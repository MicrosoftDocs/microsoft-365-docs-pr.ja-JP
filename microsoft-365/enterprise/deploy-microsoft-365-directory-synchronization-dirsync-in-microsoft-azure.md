---
title: Microsoft Azure で Microsoft 365 ディレクトリ同期を展開する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/05/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: Azure の仮想マシンに Azure AD Connect を展開して、オンプレミス ディレクトリと Azure サーバー テナントの間でアカウントを同期するADします。
ms.openlocfilehash: 52c1bb2eb53cc4e6753d528e0d82822b2a0eebc5
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "50919088"
---
# <a name="deploy-microsoft-365-directory-synchronization-in-microsoft-azure"></a><span data-ttu-id="fbd08-103">Microsoft Azure で Microsoft 365 ディレクトリ同期を展開する</span><span class="sxs-lookup"><span data-stu-id="fbd08-103">Deploy Microsoft 365 Directory Synchronization in Microsoft Azure</span></span>

<span data-ttu-id="fbd08-104">Azure Active Directory (Azure AD) Connect (以前はディレクトリ同期ツール、ディレクトリ同期ツール、または DirSync.exe ツールと呼ばれる) は、ドメインに参加しているサーバーにインストールして、オンプレミスの Active Directory ドメイン サービス (AD DS) ユーザーを Microsoft 365 サブスクリプションの Azure AD テナントに同期させるアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="fbd08-104">Azure Active Directory (Azure AD) Connect (formerly known as the Directory Synchronization tool, Directory Sync tool, or the DirSync.exe tool) is an application that you install on a domain-joined server to synchronize your on-premises Active Directory Domain Services (AD DS) users to the Azure AD tenant of your Microsoft 365 subscription.</span></span> <span data-ttu-id="fbd08-105">Microsoft 365 では、Azure ADをディレクトリ サービスに使用します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-105">Microsoft 365 uses Azure AD for its directory service.</span></span> <span data-ttu-id="fbd08-106">Microsoft 365 サブスクリプションには、Azure サービス ADがあります。</span><span class="sxs-lookup"><span data-stu-id="fbd08-106">Your Microsoft 365 subscription includes an Azure AD tenant.</span></span> <span data-ttu-id="fbd08-107">このテナントは他の SaaS アプリケーションと Azure のアプリを含む、他のクラウドのワークロードで組織の ID を管理するためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbd08-107">This tenant can also be used for management of your organization's identities with other cloud workloads, including other SaaS applications and apps in Azure.</span></span>

<span data-ttu-id="fbd08-108">Azure AD Connect はオンプレミス サーバーにインストールできますが、次の理由により、Azure の仮想マシンにもインストールできます。</span><span class="sxs-lookup"><span data-stu-id="fbd08-108">You can install Azure AD Connect on a on-premises server, but you can also install it on a virtual machine in Azure for these reasons:</span></span>
  
- <span data-ttu-id="fbd08-109">クラウド ベースのサーバーをより迅速にプロビジョニングして構成でき、ユーザーがすぐにサービスを利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="fbd08-109">You can provision and configure cloud-based servers faster, making the services available to your users sooner.</span></span>
- <span data-ttu-id="fbd08-110">Azure では、より少ない労力でより良いサイト可用性が得られます。</span><span class="sxs-lookup"><span data-stu-id="fbd08-110">Azure offers better site availability with less effort.</span></span>
- <span data-ttu-id="fbd08-111">組織内のオンプレミス サーバーの数を削減できます。</span><span class="sxs-lookup"><span data-stu-id="fbd08-111">You can reduce the number of on-premises servers in your organization.</span></span>

<span data-ttu-id="fbd08-p102">このソリューションには、オンプレミス ネットワークと Azure Virtual Network 間の接続が必要です。詳しくは、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fbd08-p102">This solution requires connectivity between your on-premises network and your Azure virtual network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="fbd08-114">この記事では、1 つのフォレスト内の単一ドメインの同期について説明します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-114">This article describes synchronization of a single domain in a single forest.</span></span> <span data-ttu-id="fbd08-115">Azure AD Connect は、Active Directory フォレストAD DS ドメインのすべてのドメインを Microsoft 365 と同期します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-115">Azure AD Connect synchronizes all AD DS domains in your Active Directory forest with Microsoft 365.</span></span> <span data-ttu-id="fbd08-116">Microsoft 365 と同期する複数の Active Directory フォレストがある場合は、「Multi-forest Directory Sync with Single Sign-On [シナリオ」を参照してください](/azure/active-directory/hybrid/whatis-hybrid-identity)。</span><span class="sxs-lookup"><span data-stu-id="fbd08-116">If you have multiple Active Directory forests to synchronize with Microsoft 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](/azure/active-directory/hybrid/whatis-hybrid-identity).</span></span> 
  
## <a name="overview-of-deploying-microsoft-365-directory-synchronization-in-azure"></a><span data-ttu-id="fbd08-117">Azure での Microsoft 365 ディレクトリ同期の展開の概要</span><span class="sxs-lookup"><span data-stu-id="fbd08-117">Overview of deploying Microsoft 365 directory synchronization in Azure</span></span>

<span data-ttu-id="fbd08-118">次の図は、オンプレミスの AD DS フォレストを Microsoft 365 サブスクリプションに同期する Azure の仮想マシン (ディレクトリ同期サーバー) で実行されている Azure AD Connect を示しています。</span><span class="sxs-lookup"><span data-stu-id="fbd08-118">The following diagram shows Azure AD Connect running on a virtual machine in Azure (the directory sync server) that synchronizes an on-premises AD DS forest to a Microsoft 365 subscription.</span></span>
  
![Azure AD Microsoft 365 サブスクリプションの Azure AD テナントとトラフィック フローを同期する Azure の仮想マシン上の Azure AD Connect ツール](../media/CP-DirSyncOverview.png)
  
<span data-ttu-id="fbd08-p104">この図には、サイト間 VPN または ExpressRoute 接続で接続されている 2 つのネットワークがあります。具体的には、AD DS ドメイン コントローラーが配置されているオンプレミス ネットワークと、ディレクトリ同期サーバーとして [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) を実行している仮想マシンが含まれる Azure 仮想ネットワークの 2 つです。ディレクトリ同期サーバーを発信元とする主要なトラフィック フローは 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="fbd08-p104">In the diagram, there are two networks connected by a site-to-site VPN or ExpressRoute connection. There is an on-premises network where AD DS domain controllers are located, and there is an Azure virtual network with a directory sync server, which is a virtual machine running [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). There are two main traffic flows originating from the directory sync server:</span></span>
  
-  <span data-ttu-id="fbd08-123">Azure AD Connect は、アカウントとパスワードの変更に関してオンプレミス ネットワーク上のドメイン コントローラーにクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-123">Azure AD Connect queries a domain controller on the on-premises network for changes to accounts and passwords.</span></span>
-  <span data-ttu-id="fbd08-124">Azure AD Connect は、Microsoft 365 サブスクリプションの Azure ADインスタンスに変更を送信します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-124">Azure AD Connect sends the changes to accounts and passwords to the Azure AD instance of your Microsoft 365 subscription.</span></span> <span data-ttu-id="fbd08-125">ディレクトリ同期サーバーはオンプレミス ネットワークの拡張部分にあるため、これらの変更はオンプレミス ネットワークのプロキシ サーバーを介して送信されます。</span><span class="sxs-lookup"><span data-stu-id="fbd08-125">Because the directory sync server is in an extended portion of your on-premises network, these changes are sent through the on-premises network's proxy server.</span></span>
    
> [!NOTE]
> <span data-ttu-id="fbd08-126">このソリューションでは、1 つの Active Directory フォレスト内の単一 Active Directory ドメインの同期について説明します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-126">This solution describes synchronization of a single Active Directory domain, in a single Active Directory forest.</span></span> <span data-ttu-id="fbd08-127">Azure AD Connect は、Active Directory フォレスト内のすべての Active Directory ドメインを Microsoft 365 と同期します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-127">Azure AD Connect synchronizes all Active Directory domains in your Active Directory forest with Microsoft 365.</span></span> <span data-ttu-id="fbd08-128">Microsoft 365 と同期する複数の Active Directory フォレストがある場合は、「Multi-forest Directory Sync with Single Sign-On [シナリオ」を参照してください](/azure/active-directory/hybrid/whatis-hybrid-identity)。</span><span class="sxs-lookup"><span data-stu-id="fbd08-128">If you have multiple Active Directory forests to synchronize with Microsoft 365, see [Multi-forest Directory Sync with Single Sign-On Scenario](/azure/active-directory/hybrid/whatis-hybrid-identity).</span></span> 
  
<span data-ttu-id="fbd08-129">このソリューションをデプロイする場合には、次の 2 つの主要な手順があります。</span><span class="sxs-lookup"><span data-stu-id="fbd08-129">There are two major steps when you deploy this solution:</span></span>
  
1. <span data-ttu-id="fbd08-p107">Azure Virtual Network を作成し、オンプレミスネットワークに対するサイト間 VPN 接続を確立します。詳しくは、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fbd08-p107">Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
    
2. <span data-ttu-id="fbd08-132">[Azure AD接続](https://www.microsoft.com/download/details.aspx?id=47594)を Azure のドメインに参加している仮想マシンにインストールし、オンプレミスの DS を Microsoft 365 AD同期します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-132">Install [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) on a domain-joined virtual machine in Azure, and then synchronize the on-premises AD DS to Microsoft 365.</span></span> <span data-ttu-id="fbd08-133">これには以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-133">This involves:</span></span>
    
    <span data-ttu-id="fbd08-134">Azure AD Connect を実行するため、Azure Virtual Machine を作成します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-134">Creating an Azure Virtual Machine to run Azure AD Connect.</span></span>
    
    <span data-ttu-id="fbd08-135">[Azure AD Connect ](https://www.microsoft.com/download/details.aspx?id=47594) をインストールし、設定します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-135">Installing and configuring [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).</span></span>
    
    <span data-ttu-id="fbd08-136">Azure AD Connect を構成するには、Azure AD 管理者アカウントの資格情報 (ユーザー名とパスワード) と DS エンタープライズ管理者アカウントADが必要です。</span><span class="sxs-lookup"><span data-stu-id="fbd08-136">Configuring Azure AD Connect requires the credentials (user name and password) of an Azure AD administrator account and a AD DS enterprise administrator account.</span></span> <span data-ttu-id="fbd08-137">Azure AD Connect は直ちに継続的に実行され、オンプレミスの DS フォレストと Microsoft 365 AD同期します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-137">Azure AD Connect runs immediately and on an ongoing basis to synchronize the on-premises AD DS forest to Microsoft 365.</span></span>
    
<span data-ttu-id="fbd08-138">このソリューションを実稼働環境に展開する前に、「シミュレートされたエンタープライズ[](simulated-ent-base-configuration-microsoft-365-enterprise.md)ベース構成」の手順を使用して、この構成を概念実証、デモンストレーション、または実験用として設定できます。</span><span class="sxs-lookup"><span data-stu-id="fbd08-138">Before you deploy this solution in production, you can use the instructions in [The simulated enterprise base configuration](simulated-ent-base-configuration-microsoft-365-enterprise.md) to set this configuration up as a proof of concept, for demonstrations, or for experimentation.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="fbd08-139">Azure AD Connect の設定が完了しても、AD DS エンタープライズ管理者アカウントの資格情報は保存されません。</span><span class="sxs-lookup"><span data-stu-id="fbd08-139">When Azure AD Connect configuration completes, it does not save the AD DS enterprise administrator account credentials.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="fbd08-140">このソリューションでは、単一の DS フォレストAD Microsoft 365 への同期について説明します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-140">This solution describes synchronizing a single AD DS forest to Microsoft 365.</span></span> <span data-ttu-id="fbd08-141">この記事で取り上げられているトポロジは、このソリューションを実装する 1 つの方法に過ぎません。</span><span class="sxs-lookup"><span data-stu-id="fbd08-141">The topology discussed in this article represents only one way to implement this solution.</span></span> <span data-ttu-id="fbd08-142">組織のトポロジは、固有のネットワーク要件とセキュリティに関する考慮事項によって異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fbd08-142">Your organization's topology might differ based on your unique network requirements and security considerations.</span></span> 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-microsoft-365-in-azure"></a><span data-ttu-id="fbd08-143">Azure で Microsoft 365 のディレクトリ同期サーバーをホストする計画</span><span class="sxs-lookup"><span data-stu-id="fbd08-143">Plan for hosting a directory sync server for Microsoft 365 in Azure</span></span>
<span data-ttu-id="fbd08-144"><a name="PlanningVirtual"> </a></span><span class="sxs-lookup"><span data-stu-id="fbd08-144"><a name="PlanningVirtual"> </a></span></span>

### <a name="prerequisites"></a><span data-ttu-id="fbd08-145">前提条件</span><span class="sxs-lookup"><span data-stu-id="fbd08-145">Prerequisites</span></span>

<span data-ttu-id="fbd08-146">開始する前に、このソリューションの以下の前提条件を確認してください。</span><span class="sxs-lookup"><span data-stu-id="fbd08-146">Before you begin, review the following prerequisites for this solution:</span></span>
  
- <span data-ttu-id="fbd08-147">「[Azure 仮想ネットワークの計画](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network)」に記されている関連する計画内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-147">Review the related planning content in [Plan your Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).</span></span>
    
- <span data-ttu-id="fbd08-148">Azure Virtual Network を構成するためのすべての「[前提条件](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites)」を満たしていることを確かめます。</span><span class="sxs-lookup"><span data-stu-id="fbd08-148">Ensure that you meet all [Prerequisites](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) for configuring the Azure virtual network.</span></span>
    
- <span data-ttu-id="fbd08-149">Active Directory 統合機能を含む Microsoft 365 サブスクリプションを持っている。</span><span class="sxs-lookup"><span data-stu-id="fbd08-149">Have a Microsoft 365 subscription that includes the Active Directory integration feature.</span></span> <span data-ttu-id="fbd08-150">Microsoft 365 サブスクリプションの詳細については [、「Microsoft 365 サブスクリプション」ページを参照してください](https://products.office.com/compare-all-microsoft-office-products?tab=2)。</span><span class="sxs-lookup"><span data-stu-id="fbd08-150">For information about Microsoft 365 subscriptions, go to the [Microsoft 365 subscription page](https://products.office.com/compare-all-microsoft-office-products?tab=2).</span></span>
    
- <span data-ttu-id="fbd08-151">Azure AD Connect を実行する 1 つの Azure 仮想マシンをプロビジョニングして、オンプレミスの DS フォレストAD Microsoft 365 と同期します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-151">Provision one Azure Virtual Machine that runs Azure AD Connect to synchronize your on-premises AD DS forest with Microsoft 365.</span></span>
    
    <span data-ttu-id="fbd08-152">AD DS エンタープライズ管理者アカウントと Azure AD 管理者アカウントの資格情報 (名前とパスワード) が必要です。</span><span class="sxs-lookup"><span data-stu-id="fbd08-152">You must have the credentials (names and passwords) for a AD DS enterprise administrator account and an Azure AD Administrator account.</span></span>
    
### <a name="solution-architecture-design-assumptions"></a><span data-ttu-id="fbd08-153">ソリューション アーキテクチャ設計の前提条件</span><span class="sxs-lookup"><span data-stu-id="fbd08-153">Solution architecture design assumptions</span></span>

<span data-ttu-id="fbd08-154">次の一覧では、このソリューションで採用された設計方針について説明します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-154">The following list describes the design choices made for this solution.</span></span>
  
- <span data-ttu-id="fbd08-p112">このソリューションでは、サイト間 VPN 接続を伴う 1 つの Azure Virtual Network を使用します。Azure Virtual Network は 1 つのサブネットをホストし、このサブネットには Azure AD Connect を実行する 1 つのディレクトリ同期サーバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fbd08-p112">This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that has one server, the directory sync server that is running Azure AD Connect.</span></span> 
    
- <span data-ttu-id="fbd08-157">オンプレミス ネットワークには、ドメイン コントローラーと DNS サーバーが存在します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-157">On the on-premises network, a domain controller and DNS servers exist.</span></span>
    
- <span data-ttu-id="fbd08-p113">Azure AD Connect は、シングル サインオンではなくパスワード ハッシュ同期を実行します (Active Directory フェデレーション サービス (AD FS) インフラストラクチャを展開する必要はありません)。パスワード ハッシュ同期とシングル サインオンのオプションの詳細については、「[Azure Active Directory ハイブリッド ID ソリューションの適切な認証方法の選択](/azure/active-directory/hybrid/choose-ad-authn)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbd08-p113">Azure AD Connect performs password hash synchronization instead of single sign-on. You do not have to deploy an Active Directory Federation Services (AD FS) infrastructure. To learn more about password hash synchronization and single sign-on options, see [Choosing the right authentication method for your Azure Active Directory hybrid identity solution](/azure/active-directory/hybrid/choose-ad-authn).</span></span>
    
<span data-ttu-id="fbd08-p114">ご使用の環境でこのソリューションを展開する場合に考慮できるその他の設計に関する選択内容があります。それらには以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fbd08-p114">There are additional design choices that you might consider when you deploy this solution in your environment. These include the following:</span></span>
  
- <span data-ttu-id="fbd08-163">既存の Azure Virtual Network 内に既存の DNS サーバーがある場合、オンプレミス ネットワークの DNS サーバーではなく、それらをディレクトリ同期サーバーで使用して名前解決を行うかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-163">If there are existing DNS servers in an existing Azure virtual network, determine whether you want your directory sync server to use them for name resolution instead of DNS servers on the on-premises network.</span></span>
    
- <span data-ttu-id="fbd08-p115">既存の Azure Virtual Network にドメイン コントローラーがある場合、Active Directory サイトとサービスを構成するという方法がより有効な選択肢となるかどうかを判別します。ディレクトリ同期サーバーはアカウントとパスワードの変更内容を調べるために、オンプレミス ネットワークのドメイン コントローラーではなく、Azure Virtual Network 内のドメイン コントローラーをクエリできます。</span><span class="sxs-lookup"><span data-stu-id="fbd08-p115">If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.</span></span>
    
## <a name="deployment-roadmap"></a><span data-ttu-id="fbd08-166">展開のロードマップ</span><span class="sxs-lookup"><span data-stu-id="fbd08-166">Deployment roadmap</span></span>

<span data-ttu-id="fbd08-167">Azure の仮想マシンへの Azure AD Connect の展開には、3つのフェーズがあります。</span><span class="sxs-lookup"><span data-stu-id="fbd08-167">Deploying Azure AD Connect on a virtual machine in Azure consists of three phases:</span></span>
  
- <span data-ttu-id="fbd08-168">フェーズ 1:Azure 仮想ネットワークを作成および構成する</span><span class="sxs-lookup"><span data-stu-id="fbd08-168">Phase 1: Create and configure the Azure virtual network</span></span>
    
- <span data-ttu-id="fbd08-169">フェーズ 2:Azure 仮想マシンを作成および構成する</span><span class="sxs-lookup"><span data-stu-id="fbd08-169">Phase 2: Create and configure the Azure virtual machine</span></span>
    
- <span data-ttu-id="fbd08-170">フェーズ 3: Azure AD Connect をインストールして構成する</span><span class="sxs-lookup"><span data-stu-id="fbd08-170">Phase 3: Install and configure Azure AD Connect</span></span>
    
<span data-ttu-id="fbd08-171">展開後、Microsoft 365 の新しいユーザー アカウントの場所とライセンスも割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbd08-171">After deployment, you must also assign locations and licenses for the new user accounts in Microsoft 365.</span></span>


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a><span data-ttu-id="fbd08-172">フェーズ 1: Azure Virtual Network を作成および構成する</span><span class="sxs-lookup"><span data-stu-id="fbd08-172">Phase 1: Create and configure the Azure virtual network</span></span>

<span data-ttu-id="fbd08-173">Azure 仮想ネットワークを作成および構成するには、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」の展開ロードマップにある「[フェーズ 1: オンプレミス ネットワークの準備](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network)」および「[フェーズ 2: Azure でのクロスプレミスの仮想ネットワークの作成](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure)」を完了してください。</span><span class="sxs-lookup"><span data-stu-id="fbd08-173">To create and configure the Azure virtual network, complete [Phase 1: Prepare your on-premises network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) and [Phase 2: Create the cross-premises virtual network in Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) in the deployment roadmap of [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
<span data-ttu-id="fbd08-174">以下が最終的な構成です。</span><span class="sxs-lookup"><span data-stu-id="fbd08-174">This is your resulting configuration.</span></span>
  
![Azure でホストされる Microsoft 365 のディレクトリ同期サーバーのフェーズ 1](../media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
<span data-ttu-id="fbd08-176">この図は、サイト間 VPN や ExpressRoute 接続を介してAzure 仮想ネットワークに接続しているオンプレミスネットワークを示しています。</span><span class="sxs-lookup"><span data-stu-id="fbd08-176">This figure shows an on-premises network connected to an Azure virtual network through a site-to-site VPN or ExpressRoute connection.</span></span>
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a><span data-ttu-id="fbd08-177">フェーズ 2:Azure 仮想マシンを作成および構成する</span><span class="sxs-lookup"><span data-stu-id="fbd08-177">Phase 2: Create and configure the Azure virtual machine</span></span>

<span data-ttu-id="fbd08-p116">「[Azure ポータルで最初の Windows 仮想マシンを作成する](https://go.microsoft.com/fwlink/p/?LinkId=393098)」の説明に従い、Azure に仮想マシンを作成します。以下の設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-p116">Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:</span></span>
  
- <span data-ttu-id="fbd08-p117">**[基本]** ウィンドウで、仮想ネットワークと同じサブスクリプション、場所およびリソース グループを選択します。ユーザー名とパスワードを安全な場所に記録します。後ほど、仮想マシンに接続するときに必要になります。</span><span class="sxs-lookup"><span data-stu-id="fbd08-p117">On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.</span></span>
    
- <span data-ttu-id="fbd08-183">**[サイズの選択]** ウィンドウで、 **A2 標準** サイズを選択します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-183">On the **Choose a size** pane, choose the **A2 Standard** size.</span></span>
    
- <span data-ttu-id="fbd08-p118">**[設定]** ウィンドウの **[ストレージ]** セクションで、**[標準]** ストレージ タイプを選択します。**[ネットワーク]** セクションで、(ゲートウェイ サブネットではなく) ディレクトリ同期サーバーをホストするための仮想ネットワークの名前とサブネットを選択します。他のすべての設定は、既定値のままにします。</span><span class="sxs-lookup"><span data-stu-id="fbd08-p118">On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.</span></span>
    
<span data-ttu-id="fbd08-187">内部 DNS をチェックして、ディレクトリ同期サーバーが DNS を正しく使用していることを検証し、仮想マシンに IP アドレスのアドレス (A) レコードが追加されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-187">Verify that your directory sync server is using DNS correctly by checking your internal DNS to make sure that an Address (A) record was added for the virtual machine with its IP address.</span></span> 
  
<span data-ttu-id="fbd08-p119">「[仮想マシンへの接続とサインオン](/azure/virtual-machines/windows/connect-logon)」の説明を参照してリモートデスクトップ接続でディレクトリ同期サーバーに接続します。サインイン後、仮想マシンをオンプレミス AD DS ドメインに参加させます。</span><span class="sxs-lookup"><span data-stu-id="fbd08-p119">Use the instructions in [Connect to the virtual machine and sign on](/azure/virtual-machines/windows/connect-logon) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises AD DS domain.</span></span>
  
<span data-ttu-id="fbd08-p120">Azure AD Connect がインターネット リソースにアクセスできるようにするには、オンプレミス ネットワークのプロキシ サーバーを使用するようディレクトリ同期サーバーを構成する必要があります。実行する追加の構成手順は、ネットワーク管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="fbd08-p120">For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.</span></span>
  
<span data-ttu-id="fbd08-192">以下が最終的な構成です。</span><span class="sxs-lookup"><span data-stu-id="fbd08-192">This is your resulting configuration.</span></span>
  
![Azure でホストされる Microsoft 365 のディレクトリ同期サーバーのフェーズ 2](../media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
<span data-ttu-id="fbd08-194">この図に、クロスプレミス Azure 仮想ネットワーク内のディレクトリ同期サーバーとしての仮想マシンを示します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-194">This figure shows the directory sync server virtual machine in the cross-premises Azure virtual network.</span></span>
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a><span data-ttu-id="fbd08-195">フェーズ 3: Azure AD Connect をインストールして構成する</span><span class="sxs-lookup"><span data-stu-id="fbd08-195">Phase 3: Install and configure Azure AD Connect</span></span>

<span data-ttu-id="fbd08-196">次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-196">Complete the following procedure:</span></span>
  
1. <span data-ttu-id="fbd08-p121">ローカル管理者権限を持つ AD DS ドメイン アカウントを使用して、リモート デスクトップ接続でディレクトリ同期サーバーに接続します。「[仮想マシンへの接続とサインオン](/azure/virtual-machines/windows/connect-logon)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbd08-p121">Connect to the directory sync server using a Remote Desktop Connection with an AD DS domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](/azure/virtual-machines/windows/connect-logon).</span></span>
    
2. <span data-ttu-id="fbd08-199">ディレクトリ同期サーバーから [、「Microsoft 365](set-up-directory-synchronization.md) のディレクトリ同期のセットアップ」記事を開き、パスワード ハッシュ同期を使用したディレクトリ同期の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="fbd08-199">From the directory sync server, open the [Set up directory synchronization for Microsoft 365](set-up-directory-synchronization.md) article and follow the directions for directory synchronization with password hash synchronization.</span></span>
    
> [!CAUTION]
> <span data-ttu-id="fbd08-p122">セットアップによって、ローカル ユーザー組織単位 (OU) 内に **AAD_xxxxxxxxxxxx** というアカウントが作成されます。このアカウントは移動も削除も行わないでください。移動や削除を行うと、同期が失敗します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-p122">Setup creates the **AAD_xxxxxxxxxxxx** account in the Local Users organizational unit (OU). Do not move or remove this account or synchronization will fail.</span></span>
  
<span data-ttu-id="fbd08-202">以下が最終的な構成です。</span><span class="sxs-lookup"><span data-stu-id="fbd08-202">This is your resulting configuration.</span></span>
  
![Azure でホストされる Microsoft 365 のディレクトリ同期サーバーのフェーズ 3](../media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
<span data-ttu-id="fbd08-204">この図に、クロスプレミス Azure 仮想ネットワーク内の Azure AD Connect を使ったディレクトリ同期サーバーを示します。</span><span class="sxs-lookup"><span data-stu-id="fbd08-204">This figure shows the directory sync server with Azure AD Connect in the cross-premises Azure virtual network.</span></span>
  
### <a name="assign-locations-and-licenses-to-users-in-microsoft-365"></a><span data-ttu-id="fbd08-205">Microsoft 365 のユーザーに場所とライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="fbd08-205">Assign locations and licenses to users in Microsoft 365</span></span>

<span data-ttu-id="fbd08-206">Azure AD Connect は、オンプレミスの AD DS から Microsoft 365 サブスクリプションにアカウントを追加しますが、ユーザーが Microsoft 365 にサインインしてサービスを使用するには、アカウントを場所とライセンスで構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbd08-206">Azure AD Connect adds accounts to your Microsoft 365 subscription from the on-premises AD DS, but in order for users to sign in to Microsoft 365 and use its services, the accounts must be configured with a location and licenses.</span></span> <span data-ttu-id="fbd08-207">次の手順で、適切なユーザーアカウントに場所を追加し、ライセンス認証を行います。</span><span class="sxs-lookup"><span data-stu-id="fbd08-207">Use these steps to add the location and activate licenses for the appropriate user accounts:</span></span>
  
1. <span data-ttu-id="fbd08-208">[Microsoft 365](https://admin.microsoft.com)管理センターにサインインし、[管理] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="fbd08-208">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com), and then click **Admin**.</span></span>
    
2. <span data-ttu-id="fbd08-209">左側のナビゲーションで、 **[ユーザー] > [アクティブなユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbd08-209">In the left navigation, click **Users > Active users**.</span></span>
    
3. <span data-ttu-id="fbd08-210">ユーザーアカウントのリストで、アクティブにするユーザー名の隣にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="fbd08-210">In the list of user accounts, select the check box next to the user you want to activate.</span></span>
    
4. <span data-ttu-id="fbd08-211">ユーザーのページで、**[製品ライセンス]** の **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbd08-211">On the page for the user, click **Edit** for **Product licenses**.</span></span>
    
5. <span data-ttu-id="fbd08-212">**[製品ライセンス]** ページの **[場所]** でユーザーの場所を選択し、ユーザーの適切なライセンスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="fbd08-212">On the **Product licenses** page, select a location for the user for **Location**, and then enable the appropriate licenses for the user.</span></span>
    
6. <span data-ttu-id="fbd08-213">完了したら、**[保存]** をクリックし、2 回 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbd08-213">When complete, click **Save**, and then click **Close** twice.</span></span>
    
7. <span data-ttu-id="fbd08-214">別のユーザーについては、手順 3 に戻ります。</span><span class="sxs-lookup"><span data-stu-id="fbd08-214">Go back to step 3 for additional users.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="fbd08-215">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbd08-215">See also</span></span>

[<span data-ttu-id="fbd08-216">Microsoft 365 ソリューションおよびアーキテクチャ センター</span><span class="sxs-lookup"><span data-stu-id="fbd08-216">Microsoft 365 solution and architecture center</span></span>](../solutions/index.yml)
  
[<span data-ttu-id="fbd08-217">オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する</span><span class="sxs-lookup"><span data-stu-id="fbd08-217">Connect an on-premises network to a Microsoft Azure virtual network</span></span>](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[<span data-ttu-id="fbd08-218">Azure AD Connect をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="fbd08-218">Download Azure AD Connect</span></span>](https://www.microsoft.com/download/details.aspx?id=47594)
  
[<span data-ttu-id="fbd08-219">Microsoft 365 のディレクトリ同期を設定する</span><span class="sxs-lookup"><span data-stu-id="fbd08-219">Set up directory synchronization for Microsoft 365</span></span>](set-up-directory-synchronization.md)
