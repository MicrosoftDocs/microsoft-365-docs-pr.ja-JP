---
title: Azure に Microsoft 365 の高可用性フェデレーション認証を展開する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: '概要: Microsoft Azure で Microsoft 365 サブスクリプションの高可用性フェデレーション認証を構成します。'
ms.openlocfilehash: 3989ebb06b4ac5dfa1cded5e07c086c4778f94e7
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "50919154"
---
# <a name="deploy-high-availability-federated-authentication-for-microsoft-365-in-azure"></a><span data-ttu-id="709f7-103">Azure に Microsoft 365 の高可用性フェデレーション認証を展開する</span><span class="sxs-lookup"><span data-stu-id="709f7-103">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>

<span data-ttu-id="709f7-104">この記事では、次の仮想マシンを使用して Azure インフラストラクチャ サービスに Microsoft Microsoft 365 の高可用性フェデレーション認証を展開する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="709f7-104">This article has links to the step-by-step instructions for deploying high availability federated authentication for Microsoft Microsoft 365 in Azure infrastructure services with these virtual machines:</span></span>
  
- <span data-ttu-id="709f7-105">2 つの Web アプリケーション プロキシ サーバー</span><span class="sxs-lookup"><span data-stu-id="709f7-105">Two web application proxy servers</span></span>
    
- <span data-ttu-id="709f7-106">2 つの Active Directory フェデレーション サービス (AD FS) サーバー</span><span class="sxs-lookup"><span data-stu-id="709f7-106">Two Active Directory Federation Services (AD FS) servers</span></span>
    
- <span data-ttu-id="709f7-107">2 つのレプリカ ドメイン コントローラー</span><span class="sxs-lookup"><span data-stu-id="709f7-107">Two replica domain controllers</span></span>
    
- <span data-ttu-id="709f7-108">Azure AD Connect を実行する 1 つのディレクトリ同期サーバー</span><span class="sxs-lookup"><span data-stu-id="709f7-108">One directory synchronization server running Azure AD Connect</span></span>
    
<span data-ttu-id="709f7-109">各サーバーのプレース ホルダー名を使用した構成がこちらです。</span><span class="sxs-lookup"><span data-stu-id="709f7-109">Here is the configuration, with placeholder names for each server.</span></span>
  
<span data-ttu-id="709f7-110">**Azure の Microsoft 365 インフラストラクチャの高可用性フェデレーション認証**</span><span class="sxs-lookup"><span data-stu-id="709f7-110">**A high availability federated authentication for Microsoft 365 infrastructure in Azure**</span></span>

![Azure での高可用性 Microsoft 365 フェデレーション認証インフラストラクチャの最終的な構成](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="709f7-112">すべての仮想マシンが単一のクロスプレミス Azure 仮想ネットワーク (VNet) に入っています。</span><span class="sxs-lookup"><span data-stu-id="709f7-112">All of the virtual machines are in a single cross-premises Azure virtual network (VNet).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="709f7-p101">個々のユーザーのフェデレーション認証は、オンプレミスのリソースには依存しません。ただし、クロスプレミス接続が使用できなくなると、オンプレミスの Active Directory Domain Services (AD DS) で加えられたユーザー アカウントとグループに対する更新が VNet 内のドメイン コントローラーで受信されなくなります。これを回避するために、クロスプレミス接続で高可用性を構成できます。詳細については、「[高可用性のクロスプレミス接続および VNet 間接続](/azure/vpn-gateway/vpn-gateway-highlyavailable)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="709f7-p101">Federated authentication of individual users does not rely on any on-premises resources. However, if the cross-premises connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Active Directory Domain Services (AD DS). To ensure this does not happen, you can configure high availability for your cross-premises connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="709f7-117">特定の役割を持つ仮想マシンの各ペアが独自のサブネットと可用性セットに入っています。</span><span class="sxs-lookup"><span data-stu-id="709f7-117">Each pair of virtual machines for a specific role is in its own subnet and availability set.</span></span>
  
> [!NOTE]
> <span data-ttu-id="709f7-p102">この VNet はオンプレミスのネットワークに接続されているため、この構成に管理サブネット上の jumpbox や仮想マシンの監視は含まれません。詳細については、「[N 層のアーキテクチャで Windows VM を実行する](/azure/guidance/guidance-compute-n-tier-vm)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="709f7-p102">Because this VNet is connected to the on-premises network, this configuration does not include jumpbox or monitoring virtual machines on a management subnet. For more information, see [Running Windows VMs for an N-tier architecture](/azure/guidance/guidance-compute-n-tier-vm).</span></span> 
  
<span data-ttu-id="709f7-120">この構成の結果、すべての Microsoft 365 ユーザーに対してフェデレーション認証が行え、AD DS 資格情報を使用して Microsoft 365 アカウントではなくサインインできます。</span><span class="sxs-lookup"><span data-stu-id="709f7-120">The result of this configuration is that you will have federated authentication for all of your Microsoft 365 users, in which they can use their AD DS credentials to sign in rather than their Microsoft 365 account.</span></span> <span data-ttu-id="709f7-121">フェデレーション認証インフラストラクチャでは、オンプレミスの境界ネットワークよりも Azure インフラストラクチャ サービスでより簡単に展開できるサーバーの冗長セットが使用されます。</span><span class="sxs-lookup"><span data-stu-id="709f7-121">The federated authentication infrastructure uses a redundant set of servers that are more easily deployed in Azure infrastructure services, rather than in your on-premises edge network.</span></span>
  
## <a name="bill-of-materials"></a><span data-ttu-id="709f7-122">部品表</span><span class="sxs-lookup"><span data-stu-id="709f7-122">Bill of materials</span></span>

<span data-ttu-id="709f7-123">このベースライン構成には、Azure のサービスおよびコンポーネントの次のセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="709f7-123">This baseline configuration requires the following set of Azure services and components:</span></span>
  
- <span data-ttu-id="709f7-124">7 つの仮想マシン</span><span class="sxs-lookup"><span data-stu-id="709f7-124">Seven virtual machines</span></span>
    
- <span data-ttu-id="709f7-125">4 つのサブネットを持つ 1 つのクロスプレミス仮想ネットワーク</span><span class="sxs-lookup"><span data-stu-id="709f7-125">One cross-premises virtual network with four subnets</span></span>
    
- <span data-ttu-id="709f7-126">4 つのリソース グループ</span><span class="sxs-lookup"><span data-stu-id="709f7-126">Four resource groups</span></span>
    
- <span data-ttu-id="709f7-127">3 つの可用性セット</span><span class="sxs-lookup"><span data-stu-id="709f7-127">Three availability sets</span></span>
    
- <span data-ttu-id="709f7-128">1 つの Azure サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="709f7-128">One Azure subscription</span></span>
    
<span data-ttu-id="709f7-129">仮想マシンと、この構成用の既定サイズを次に示します。</span><span class="sxs-lookup"><span data-stu-id="709f7-129">Here are the virtual machines and their default sizes for this configuration.</span></span>
  
|<span data-ttu-id="709f7-130">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="709f7-130">**Item**</span></span>|<span data-ttu-id="709f7-131">**仮想マシンの説明**</span><span class="sxs-lookup"><span data-stu-id="709f7-131">**Virtual machine description**</span></span>|<span data-ttu-id="709f7-132">**Azure ギャラリー イメージ**</span><span class="sxs-lookup"><span data-stu-id="709f7-132">**Azure gallery image**</span></span>|<span data-ttu-id="709f7-133">**既定のサイズ**</span><span class="sxs-lookup"><span data-stu-id="709f7-133">**Default size**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="709f7-134">1.</span><span class="sxs-lookup"><span data-stu-id="709f7-134">1.</span></span>  <br/> |<span data-ttu-id="709f7-135">1 つ目のドメイン コントローラー</span><span class="sxs-lookup"><span data-stu-id="709f7-135">First domain controller</span></span>  <br/> |<span data-ttu-id="709f7-136">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="709f7-136">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="709f7-137">D2</span><span class="sxs-lookup"><span data-stu-id="709f7-137">D2</span></span>  <br/> |
|<span data-ttu-id="709f7-138">2.</span><span class="sxs-lookup"><span data-stu-id="709f7-138">2.</span></span>  <br/> |<span data-ttu-id="709f7-139">2 つ目のドメイン コントローラー</span><span class="sxs-lookup"><span data-stu-id="709f7-139">Second domain controller</span></span>  <br/> |<span data-ttu-id="709f7-140">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="709f7-140">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="709f7-141">D2</span><span class="sxs-lookup"><span data-stu-id="709f7-141">D2</span></span>  <br/> |
|<span data-ttu-id="709f7-142">3.</span><span class="sxs-lookup"><span data-stu-id="709f7-142">3.</span></span>  <br/> |<span data-ttu-id="709f7-143">Azure AD Connect サーバー</span><span class="sxs-lookup"><span data-stu-id="709f7-143">Azure AD Connect server</span></span>  <br/> |<span data-ttu-id="709f7-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="709f7-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="709f7-145">D2</span><span class="sxs-lookup"><span data-stu-id="709f7-145">D2</span></span>  <br/> |
|<span data-ttu-id="709f7-146">4.</span><span class="sxs-lookup"><span data-stu-id="709f7-146">4.</span></span>  <br/> |<span data-ttu-id="709f7-147">1 つ目の AD FS サーバー</span><span class="sxs-lookup"><span data-stu-id="709f7-147">First AD FS server</span></span>  <br/> |<span data-ttu-id="709f7-148">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="709f7-148">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="709f7-149">D2</span><span class="sxs-lookup"><span data-stu-id="709f7-149">D2</span></span>  <br/> |
|<span data-ttu-id="709f7-150">5.</span><span class="sxs-lookup"><span data-stu-id="709f7-150">5.</span></span>  <br/> |<span data-ttu-id="709f7-151">2 つ目の AD FS サーバー</span><span class="sxs-lookup"><span data-stu-id="709f7-151">Second AD FS server</span></span>  <br/> |<span data-ttu-id="709f7-152">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="709f7-152">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="709f7-153">D2</span><span class="sxs-lookup"><span data-stu-id="709f7-153">D2</span></span>  <br/> |
|<span data-ttu-id="709f7-154">6.</span><span class="sxs-lookup"><span data-stu-id="709f7-154">6.</span></span>  <br/> |<span data-ttu-id="709f7-155">1 つ目の Web アプリケーション プロキシ サーバー</span><span class="sxs-lookup"><span data-stu-id="709f7-155">First web application proxy server</span></span>  <br/> |<span data-ttu-id="709f7-156">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="709f7-156">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="709f7-157">D2</span><span class="sxs-lookup"><span data-stu-id="709f7-157">D2</span></span>  <br/> |
|<span data-ttu-id="709f7-158">7.</span><span class="sxs-lookup"><span data-stu-id="709f7-158">7.</span></span>  <br/> |<span data-ttu-id="709f7-159">2 つ目の Web アプリケーション プロキシ サーバー</span><span class="sxs-lookup"><span data-stu-id="709f7-159">Second web application proxy server</span></span>  <br/> |<span data-ttu-id="709f7-160">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="709f7-160">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="709f7-161">D2</span><span class="sxs-lookup"><span data-stu-id="709f7-161">D2</span></span>  <br/> |
   
<span data-ttu-id="709f7-162">この構成の見積もりコストを計算するには、「[料金計算ツール](https://azure.microsoft.com/pricing/calculator/)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="709f7-162">To compute the estimated costs for this configuration, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)</span></span>
  
## <a name="phases-of-deployment"></a><span data-ttu-id="709f7-163">展開のフェーズ</span><span class="sxs-lookup"><span data-stu-id="709f7-163">Phases of deployment</span></span>

<span data-ttu-id="709f7-164">次のフェーズでは、このワークロードを展開します。</span><span class="sxs-lookup"><span data-stu-id="709f7-164">You deploy this workload in the following phases:</span></span>
  
- <span data-ttu-id="709f7-p104">[フェーズ 1: Azure を構成する](high-availability-federated-authentication-phase-1-configure-azure.md)。リソース グループ、ストレージ アカウント、可用性セット、およびクロスプレミスの仮想ネットワークを作成します。</span><span class="sxs-lookup"><span data-stu-id="709f7-p104">[Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="709f7-167">[フェーズ 2: ドメイン コントローラーを構成する](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)。</span><span class="sxs-lookup"><span data-stu-id="709f7-167">[Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span></span> <span data-ttu-id="709f7-168">レプリカの AD DS ドメイン コントローラーとディレクトリ同期サーバーを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="709f7-168">Create and configure replica AD DS domain controllers and the directory synchronization server.</span></span>
    
- <span data-ttu-id="709f7-p106">[フェーズ 3: AD FS サーバーを構成する](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)。2 つの AD FS サーバーを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="709f7-p106">[Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="709f7-p107">[フェーズ 4: Web アプリケーション プロキシを構成する](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)。2 つの Web アプリケーション プロキシ サーバーを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="709f7-p107">[Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="709f7-173">[フェーズ 5: Microsoft 365 のフェデレーション認証を構成します](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)。</span><span class="sxs-lookup"><span data-stu-id="709f7-173">[Phase 5: Configure federated authentication for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md).</span></span> <span data-ttu-id="709f7-174">Microsoft 365 サブスクリプションのフェデレーション認証を構成します。</span><span class="sxs-lookup"><span data-stu-id="709f7-174">Configure federated authentication for your Microsoft 365 subscription.</span></span>
    
<span data-ttu-id="709f7-175">これらの記事では、Azure インフラストラクチャ サービスにおける Microsoft 365 の機能的で高可用性のフェデレーション認証を作成する、定義済みのアーキテクチャに関する、事前に説明された段階的なガイドを提供します。</span><span class="sxs-lookup"><span data-stu-id="709f7-175">These articles provide a prescriptive, phase-by-phase guide for a predefined architecture to create a functional, high availability federated authentication for Microsoft 365 in Azure infrastructure services.</span></span> <span data-ttu-id="709f7-176">以下の点にご注意ください。</span><span class="sxs-lookup"><span data-stu-id="709f7-176">Keep the following in mind:</span></span>
  
- <span data-ttu-id="709f7-177">経験豊富な AD FS の実行者である場合、フェーズ 3 と 4 の手順を自由に適応させて、自分のニーズに最適なサーバーのセットを構築できます。</span><span class="sxs-lookup"><span data-stu-id="709f7-177">If you are an experienced AD FS implementer, feel free to adapt the instructions in phases 3 and 4 and build the set of servers that best suits your needs.</span></span>
    
- <span data-ttu-id="709f7-178">既存のクロスプレミスの仮想ネットワークを使用した既存の Azure ハイブリッド クラウド展開がある場合は、フェーズ 1 と 2 の手順を自由に適応させるかスキップして、AD FS と Web アプリケーション プロキシ サーバーを適切なサブネットに配置できます。</span><span class="sxs-lookup"><span data-stu-id="709f7-178">If you already have an existing Azure hybrid cloud deployment with an existing cross-premises virtual network, feel free to adapt or skip the instructions in phases 1 and 2 and place the AD FS and web application proxy servers on the appropriate subnets.</span></span>
    
<span data-ttu-id="709f7-179">開発/テスト環境またはこの構成の概念実証を構築するには [、「Microsoft 365](federated-identity-for-your-microsoft-365-dev-test-environment.md)開発/テスト環境のフェデレーション ID」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="709f7-179">To build a dev/test environment or a proof-of-concept of this configuration, see [Federated identity for your Microsoft 365 dev/test environment](federated-identity-for-your-microsoft-365-dev-test-environment.md).</span></span>
  
## <a name="next-step"></a><span data-ttu-id="709f7-180">次の手順</span><span class="sxs-lookup"><span data-stu-id="709f7-180">Next step</span></span>

<span data-ttu-id="709f7-181">このワークロードの構成を「[フェーズ 1: Azure を構成する](high-availability-federated-authentication-phase-1-configure-azure.md)」から開始します。 </span><span class="sxs-lookup"><span data-stu-id="709f7-181">Start the configuration of this workload with [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span> 
