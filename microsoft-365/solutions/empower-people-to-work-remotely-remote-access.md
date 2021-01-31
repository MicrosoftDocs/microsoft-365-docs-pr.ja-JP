---
title: 手順 2.  オンプレミスのアプリとサービスへのリモート アクセスを提供します。
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: laurawi
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Priority
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: Microsoft 365 クラウド サービスへのアクセスを最適化しながら、リモート ワーカーがオンプレミスのリソースにアクセスできることを確認します。
ms.openlocfilehash: 43000ce27fc24dbc6c2db3782b0ed40aa66b7fd2
ms.sourcegitcommit: 1ac884d8470b2f2a58b6f79e324fd91e4d11dceb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2021
ms.locfileid: "50055533"
---
# <a name="step-2-provide-remote-access-to-on-premises-apps-and-services"></a><span data-ttu-id="09a72-104">手順 2. </span><span class="sxs-lookup"><span data-stu-id="09a72-104">Step 2.</span></span> <span data-ttu-id="09a72-105">オンプレミスのアプリとサービスへのリモート アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="09a72-105">Provide remote access to on-premises apps and services</span></span>

<span data-ttu-id="09a72-106">組織でリモートアクセス VPN ソリューションを使用している場合 (通常、ネットワークのエッジに VPN サーバー、ユーザーのデバイスにインストールされた VPN クライアントがある場合)、ユーザーはリモートアクセス VPN 接続を使用してオンプレミスのアプリやサーバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="09a72-106">If your organization uses a remote access VPN solution, typically with VPN servers on the edge of your network and VPN clients installed on your users' devices, your users can use remote access VPN connections to access on-premises apps and servers.</span></span> <span data-ttu-id="09a72-107">ただし、Microsoft 365 クラウドベース サービスへのトラフィックを最適化することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="09a72-107">But you may need to optimize traffic to Microsoft 365 cloud-based services.</span></span>

<span data-ttu-id="09a72-108">ユーザーが VPN ソリューションを使用していない場合は、すべてのアプリが Web ベースであるかどうかに応じて、Azure Active Directory (Azure AD) アプリケーション プロキシと Azure Point-to-Site (P2S) VPN を使用してアクセスを提供できます。</span><span class="sxs-lookup"><span data-stu-id="09a72-108">If your users do not use a VPN solution, you can use Azure Active Directory (Azure AD) Application Proxy and Azure Point-to-Site (P2S) VPN to provide access, depending on whether all your apps are web-based.</span></span>

<span data-ttu-id="09a72-109">リモート アクセスのプライマリ構成は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="09a72-109">Here are the primary configurations for remote access:</span></span>

- <span data-ttu-id="09a72-110">既にリモート アクセス VPN ソリューションを使用しています。</span><span class="sxs-lookup"><span data-stu-id="09a72-110">You are already using a remote access VPN solution.</span></span>
- <span data-ttu-id="09a72-111">リモートアクセス VPN ソリューションを使用していない場合、リモートワーカーに個人用コンピューターを使用したい。</span><span class="sxs-lookup"><span data-stu-id="09a72-111">You are not using a remote access VPN solution and you want your remote workers to use their personal computers.</span></span>
- <span data-ttu-id="09a72-112">リモート アクセス VPN ソリューションを使用しておらず、ハイブリッド ID があり、オンプレミスの Web ベースのアプリへのリモート アクセスのみが必要です。</span><span class="sxs-lookup"><span data-stu-id="09a72-112">You are not using a remote access VPN solution, you have hybrid identity, and you need remote access only to on-premises web-based apps.</span></span>
- <span data-ttu-id="09a72-113">リモート アクセス VPN ソリューションを使用しておらず、オンプレミス アプリへのアクセスが必要であり、その一部は Web ベースではありません。</span><span class="sxs-lookup"><span data-stu-id="09a72-113">You are not using a remote access VPN solution and you need access to on-premises apps, some of which are not web-based.</span></span>

<span data-ttu-id="09a72-114">この記事で説明するリモート アクセス構成オプションについては、このフローチャートを参照してください。</span><span class="sxs-lookup"><span data-stu-id="09a72-114">See this flowchart for the remote access configuration options discussed in this article.</span></span>

![リモート アクセス構成フローチャート](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-flowchart.png)

<span data-ttu-id="09a72-116">リモート アクセス接続では、[リモート デスクトップ](https://support.microsoft.com/help/4028379/windows-10-how-to-use-remote-desktop)を使用して、ユーザーをオンプレミス PC に接続することもできます。</span><span class="sxs-lookup"><span data-stu-id="09a72-116">With remote access connections, you can also use [Remote Desktop](https://support.microsoft.com/help/4028379/windows-10-how-to-use-remote-desktop) to connect your users to an on-premises PC.</span></span> <span data-ttu-id="09a72-117">たとえば、リモート ワーカーはリモート デスクトップを使用して、Windows、iOS、または Android デバイスからオフィスの PC に接続できます。</span><span class="sxs-lookup"><span data-stu-id="09a72-117">For example, a remote worker can use Remote Desktop to connect to the PC in their office from their Windows, iOS, or Android device.</span></span> <span data-ttu-id="09a72-118">リモートで接続すると、目の前に座っているかのように使用できます。</span><span class="sxs-lookup"><span data-stu-id="09a72-118">Once they are remotely connected, they can use it as if they were sitting in front of it.</span></span>

## <a name="optimize-performance-for-remote-access-vpn-clients-to-microsoft-365-cloud-services"></a><span data-ttu-id="09a72-119">Microsoft 365 クラウド サービスへのリモート アクセス VPN クライアントのパフォーマンスを最適化する</span><span class="sxs-lookup"><span data-stu-id="09a72-119">Optimize performance for remote access VPN clients to Microsoft 365 cloud services</span></span>

<span data-ttu-id="09a72-120">リモート ワーカーが従来の VPN クライアントを使用して組織ネットワークへのリモート アクセスを取得している場合は、VPN クライアントがスプリット トンネリング サポートを備えていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="09a72-120">If your remote workers are using a traditional VPN client to obtain remote access to your organization network, verify that the VPN client has split tunneling support.</span></span>

<span data-ttu-id="09a72-121">スプリット トンネリングを使用しない場合、すべてのリモート作業トラフィックは VPN 接続を介して送信され、そこで組織のエッジ デバイスに転送されて処理され、インターネット上で送信される必要があります。</span><span class="sxs-lookup"><span data-stu-id="09a72-121">Without split tunneling, all of your remote work traffic gets sent across the VPN connection, where it must be forwarded to your organization’s edge devices, get processed, and then sent on the Internet.</span></span>

![トンネリングのない VPN クライアントからのネットワーク トラフィック](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-before-tunneling.png)

<span data-ttu-id="09a72-123">Microsoft 365 トラフィックは、組織を経由して間接的にルーティングする必要があります。これは、VPN クライアントの物理的な場所から遠く離れた Microsoft ネットワーク エントリ ポイントに転送される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="09a72-123">Microsoft 365 traffic must take an indirect route through your organization, which could be forwarded to a Microsoft network entry point far away from the VPN client’s physical location.</span></span> <span data-ttu-id="09a72-124">この間接パスにより、ネットワーク トラフィックが遅延し、全体的なパフォーマンスを低下させます。</span><span class="sxs-lookup"><span data-stu-id="09a72-124">This indirect path adds latency to the network traffic and decreases overall performance.</span></span> 

<span data-ttu-id="09a72-125">スプリッ トトンネリングを使用すると、VPN クライアントを構成して、特定の種類のトラフィックが VPN 接続を介して、組織ネットワークに送信されることを除外できます。</span><span class="sxs-lookup"><span data-stu-id="09a72-125">With split tunneling, you can configure your VPN client to exclude specific types of traffic from being sent over the VPN connection to the organization network.</span></span>

<span data-ttu-id="09a72-126">Microsoft 365 クラウドリソースへのアクセスを最適化するには、VPN 接続を介して、**最適化** カテゴリの Microsoft 365 エンドポイントへのトラフィックを除外するようにスプリット トンネリング VPN クライアントを構成します。</span><span class="sxs-lookup"><span data-stu-id="09a72-126">To optimize access to Microsoft 365 cloud resources, configure your split tunneling VPN clients to exclude traffic to the **Optimize** category Microsoft 365 endpoints over the VPN connection.</span></span> <span data-ttu-id="09a72-127">詳細については、「[Office 365 エンドポイントのカテゴリ](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-network-connectivity-principles#new-office-365-endpoint-categories)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="09a72-127">For more information, see [Office 365 endpoint categories](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-network-connectivity-principles#new-office-365-endpoint-categories).</span></span> <span data-ttu-id="09a72-128">最適化カテゴリのエンドポイントについては、[こちらのリスト](https://docs.microsoft.com/microsoft-365/enterprise/urls-and-ip-address-ranges)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="09a72-128">See [this list](https://docs.microsoft.com/microsoft-365/enterprise/urls-and-ip-address-ranges) of Optimize category endpoints.</span></span>

<span data-ttu-id="09a72-129">Microsoft 365 クラウド アプリへのほとんどのトラフィックが VPN 接続をバイパスした結果としてのトラフィック フローは、以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="09a72-129">Here is the resulting traffic flow, in which most of the traffic to Microsoft 365 cloud apps bypass the VPN connection.</span></span>

![トンネリングのある VPN クライアントからのネットワーク トラフィック](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-after-tunneling.png)

<span data-ttu-id="09a72-131">これにより、VPN クライアントは、インターネット経由で、または Microsoft ネットワークへの最も近いエントリポイントに、重要な Microsoft 365 クラウド サービスのトラッフィックを送受信できます。</span><span class="sxs-lookup"><span data-stu-id="09a72-131">This allows the VPN client to send and receive crucial Microsoft 365 cloud service traffic directly over the Internet and to the nearest entry point into the Microsoft network.</span></span>

<span data-ttu-id="09a72-132">詳細とガイダンスについては、「[VPN スプリット トンネリングを使用してリモート ユーザーの Office 365 の接続を最適化する](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-vpn-split-tunnel??)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="09a72-132">For more information and guidance, see [Optimize Office 365 connectivity for remote users using VPN split tunneling](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-vpn-split-tunnel??).</span></span>

## <a name="deploy-remote-access-when-all-your-apps-are-web-apps-and-you-have-hybrid-identity"></a><span data-ttu-id="09a72-133">すべてのアプリが Web アプリであり、ハイブリッド ID がある場合にリモート アクセスを展開する</span><span class="sxs-lookup"><span data-stu-id="09a72-133">Deploy remote access when all your apps are web apps and you have hybrid identity</span></span>

<span data-ttu-id="09a72-134">リモート ワーカーが従来の VPN クライアントを使用しておらず、オンプレミスのユーザー アカウントとグループが Azure AD と同期している場合は、Azure AD アプリケーション プロキシを使用して、オンプレミスのサーバーでホストされている Web ベースのアプリケーションに対して安全なリモート アクセスを提供できます。</span><span class="sxs-lookup"><span data-stu-id="09a72-134">If your remote workers are not using a traditional VPN client and your on-premises user accounts and groups are synchronized with Azure AD, you can use Azure AD Application Proxy to provide secure remote access for web-based applications hosted on on-premises servers.</span></span> <span data-ttu-id="09a72-135">Web ベースのアプリケーションには、SharePoint Server サイト、Outlook Web Access サーバー、またはその他の Web ベースの基幹業務アプリケーションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="09a72-135">Web-based applications include SharePoint Server sites, Outlook Web Access servers, or any other web-based line of business applications.</span></span> 

<span data-ttu-id="09a72-136">ここでは、Azure AD アプリケーション プロキシのコンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="09a72-136">Here are the components of Azure AD Application Proxy.</span></span>

![Azure AD アプリケーション プロキシのコンポーネント](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-application-proxy.png)

<span data-ttu-id="09a72-138">詳細については、この「[Azure AD アプリケーション プロキシの概要](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="09a72-138">For more information, see this [overview of Azure AD Application Proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).</span></span>

>[!Note]
><span data-ttu-id="09a72-139">Azure AD アプリケーションプロキシは、Microsoft 365 のサブスクリプションには含まれていません。</span><span class="sxs-lookup"><span data-stu-id="09a72-139">Azure AD Application Proxy is not included with a Microsoft 365 subscription.</span></span> <span data-ttu-id="09a72-140">別の Azure サブスクリプションで使用する場合は、支払う必要があります。</span><span class="sxs-lookup"><span data-stu-id="09a72-140">You must pay for usage with a separate Azure subscription.</span></span>
>

## <a name="deploy-remote-access-when-not-all-your-apps-are-web-apps"></a><span data-ttu-id="09a72-141">すべてのアプリが Web アプリではない場合にリモート アクセスを展開する</span><span class="sxs-lookup"><span data-stu-id="09a72-141">Deploy remote access when not all your apps are web apps</span></span>

<span data-ttu-id="09a72-142">リモート ワーカーが従来の VPN クライアントを使用しておらず、お使いのアプリが Web ベースではない場合は、Azure Point-to-Site (P2S) VPN を使用できます。</span><span class="sxs-lookup"><span data-stu-id="09a72-142">If your remote workers are not using a traditional VPN client and you have apps that are not web-based, you can use an Azure Point-to-Site (P2S) VPN.</span></span>

<span data-ttu-id="09a72-143">P2S VPN 接続は、Azure 仮想ネットワークを介してリモート ワーカーのデバイスから組織ネットワークへの安全な接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="09a72-143">A P2S VPN connection creates a secure connection from a remote worker’s device to your organization network through an Azure virtual network.</span></span> 

![Azure P2S VPN のコンポーネント](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-p2s-vpn.png)

<span data-ttu-id="09a72-145">詳細については、この「[P2S VPN の概要](https://docs.microsoft.com/azure/vpn-gateway/point-to-site-about)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="09a72-145">For more information, see this [overview of P2S VPN](https://docs.microsoft.com/azure/vpn-gateway/point-to-site-about).</span></span>

>[!Note]
><span data-ttu-id="09a72-146">Azure P2S VPN は、Microsoft 365 のサブスクリプションには含まれていません。</span><span class="sxs-lookup"><span data-stu-id="09a72-146">Azure P2S VPN is not included with a Microsoft 365 subscription.</span></span> <span data-ttu-id="09a72-147">別の Azure サブスクリプションで使用する場合は、支払う必要があります。</span><span class="sxs-lookup"><span data-stu-id="09a72-147">You must pay for usage with a separate Azure subscription.</span></span>
>

## <a name="deploy-windows-virtual-desktop-to-provide-remote-access-for-remote-workers-using-personal-devices"></a><span data-ttu-id="09a72-148">リモート ワーカーが個人用デバイスを使用してリモート アクセスできるように、Windows Virtual Desktop を展開する</span><span class="sxs-lookup"><span data-stu-id="09a72-148">Deploy Windows Virtual Desktop to provide remote access for remote workers using personal devices</span></span> 

<span data-ttu-id="09a72-149">個人用デバイスや管理されていないデバイスのみを使用できるリモート ワーカーをサポートするには、Azure の Windows Virtual Desktop を使用して、ユーザーが自宅から使用する仮想デスクトップを作成して割り当てます。</span><span class="sxs-lookup"><span data-stu-id="09a72-149">To support remote workers who can only use their personal and unmanaged devices, use Windows Virtual Desktop in Azure to create and allocate virtual desktops for your users to use from home.</span></span> <span data-ttu-id="09a72-150">仮想化された PC は、組織のネットワークに接続されている PC と同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="09a72-150">Virtualized PCs can act just like PCs connected to your organization network.</span></span>

![Azure Windows Virtual Desktop のコンポーネント](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-windows-virtual-desktop.png)

<span data-ttu-id="09a72-152">詳細については、「[Windows Virtual Desktop の概要](https://docs.microsoft.com/azure/virtual-desktop/overview)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="09a72-152">For more information, see this [overview of Windows Virtual Desktop](https://docs.microsoft.com/azure/virtual-desktop/overview).</span></span> 

>[!Note]
><span data-ttu-id="09a72-153">Windows Virtual Desktop は、Microsoft 365 のサブスクリプションには含まれていません。</span><span class="sxs-lookup"><span data-stu-id="09a72-153">Windows Virtual Desktop is not included with a Microsoft 365 subscription.</span></span> <span data-ttu-id="09a72-154">別の Azure サブスクリプションで使用する場合は、支払う必要があります。</span><span class="sxs-lookup"><span data-stu-id="09a72-154">You must pay for usage with a separate Azure subscription.</span></span>
>

## <a name="protect-your-remote-desktop-services-connections-with-the-remote-desktop-services-gateway"></a><span data-ttu-id="09a72-155">リモートデスクトップサービスゲートウェイを使用して、リモートデスクトップサービス接続を保護する</span><span class="sxs-lookup"><span data-stu-id="09a72-155">Protect your Remote Desktop Services connections with the Remote Desktop Services Gateway</span></span>

<span data-ttu-id="09a72-156">リモートデスクトップサービス (RDS) を使用している場合、従業員がオンプレミスのネットワーク上の Windows ベースのコンピューターに接続できるようにするには、エッジネットワークの Microsoft リモートデスクトップサービスゲートウェイを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09a72-156">If you are using Remote Desktop Services (RDS) to allow employees to connect into Windows-based computers on your on-premises network, you should use a Microsoft Remote Desktop Services gateway in your edge network.</span></span> <span data-ttu-id="09a72-157">ゲートウェイはトランスポート層セキュリティ (TLS) を使用してトラフィックを暗号化し、RDS をホストしているオンプレミス コンピューターがインターネットに直接公開されるのを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="09a72-157">The gateway uses Transport Layer Security (TLS) to encrypt traffic and prevents the on-premises computer hosting RDS from being directly exposed to the Internet.</span></span>

![リモートデスクトップサービスゲートウェイを使用して、リモートデスクトップサービス接続する。](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-remote-desktop.png)

<span data-ttu-id="09a72-159">詳細については、[こちらの記事](https://www.microsoft.com/security/blog/2020/04/16/security-guidance-remote-desktop-adoption/)を参照してください。 </span><span class="sxs-lookup"><span data-stu-id="09a72-159">See [this article](https://www.microsoft.com/security/blog/2020/04/16/security-guidance-remote-desktop-adoption/) for more information.</span></span>

## <a name="admin-technical-resources-for-remote-access"></a><span data-ttu-id="09a72-160">リモート アクセスのための管理技術リソース</span><span class="sxs-lookup"><span data-stu-id="09a72-160">Admin technical resources for remote access</span></span>

- [<span data-ttu-id="09a72-161">リモート社員の Office 365 トラフィックをすぐに最適化し、インフラストラクチャの負担を軽減する方法</span><span class="sxs-lookup"><span data-stu-id="09a72-161">How to quickly optimize Office 365 traffic for remote staff & reduce the load on your infrastructure</span></span>](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571)
- [<span data-ttu-id="09a72-162">VPN スプリット トンネリングを使用してリモート ユーザーの Office 365 の接続を最適化する</span><span class="sxs-lookup"><span data-stu-id="09a72-162">Optimize Office 365 connectivity for remote users using VPN split tunneling</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-vpn-split-tunnel?)

## <a name="results-of-step-2"></a><span data-ttu-id="09a72-163">手順 2 の結果</span><span class="sxs-lookup"><span data-stu-id="09a72-163">Results of Step 2</span></span>

<span data-ttu-id="09a72-164">リモート アクセス ソリューションをリモート ワーカーに展開した後、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="09a72-164">After deployment of a remote access solution for your remote workers:</span></span>

| <span data-ttu-id="09a72-165">リモート アクセス構成</span><span class="sxs-lookup"><span data-stu-id="09a72-165">Remote access configuration</span></span> | <span data-ttu-id="09a72-166">結果</span><span class="sxs-lookup"><span data-stu-id="09a72-166">Results</span></span> |
|:-------|:-----|
| <span data-ttu-id="09a72-167">リモート アクセス VPN ソリューションが導入されている</span><span class="sxs-lookup"><span data-stu-id="09a72-167">A remote access VPN solution is in place</span></span> | <span data-ttu-id="09a72-168">リモート アクセス VPN クライアントをスプリット トンネリング用と Microsoft 365 エンドポイントの最適化カテゴリ用に構成しました。</span><span class="sxs-lookup"><span data-stu-id="09a72-168">You have configured your remote access VPN client for split tunneling and for the Optimize category of Microsoft 365 endpoints.</span></span> |
| <span data-ttu-id="09a72-169">リモート アクセス VPN ソリューションはなく、オンプレミスの Web ベースのアプリへのリモート アクセスのみが必要です</span><span class="sxs-lookup"><span data-stu-id="09a72-169">No remote access VPN solution and you need remote access only to on-premises web-based apps</span></span> | <span data-ttu-id="09a72-170">Azure アプリケーション プロキシを構成しました。</span><span class="sxs-lookup"><span data-stu-id="09a72-170">You have configured Azure Application Proxy.</span></span> |
| <span data-ttu-id="09a72-171">リモート アクセス VPN ソリューションはなく、オンプレミス アプリへのアクセスが必要であり、その一部は Web ベースではありません</span><span class="sxs-lookup"><span data-stu-id="09a72-171">No remote access VPN solution and you need access to on-premises apps, some of which are not web-based</span></span> | <span data-ttu-id="09a72-172">Azure P2S VPN を構成しました。</span><span class="sxs-lookup"><span data-stu-id="09a72-172">You have configured Azure P2S VPN.</span></span> |
| <span data-ttu-id="09a72-173">リモート ワーカーは自宅から個人用デバイスを使用しています</span><span class="sxs-lookup"><span data-stu-id="09a72-173">Remote workers are using their personal devices from home</span></span> | <span data-ttu-id="09a72-174">Windows Virtual Desktop を構成しました。</span><span class="sxs-lookup"><span data-stu-id="09a72-174">You have configured Windows Virtual Desktop.</span></span> |
| <span data-ttu-id="09a72-175">リモートワーカーがオンプレミスシステムへの RDS 接続を使用している</span><span class="sxs-lookup"><span data-stu-id="09a72-175">Remote workers are using RDS connections to on-premises systems</span></span> | <span data-ttu-id="09a72-176">境界ネットワークにリモートデスクトップサービスゲートウェイを展開しました。</span><span class="sxs-lookup"><span data-stu-id="09a72-176">You have deployed a Remote Desktop Services gateway in your edge network.</span></span> |
|||

## <a name="next-step"></a><span data-ttu-id="09a72-177">次の手順</span><span class="sxs-lookup"><span data-stu-id="09a72-177">Next step</span></span>

<span data-ttu-id="09a72-178">[![手順 3: Microsoft 365 のセキュリティとコンプライアンスのサービスを展開する](../media/empower-people-to-work-remotely/remote-workers-step-grid-3.png)](empower-people-to-work-remotely-security-compliance.md)</span><span class="sxs-lookup"><span data-stu-id="09a72-178">[![Step 3: Deploy Microsoft 365 security and compliance services](../media/empower-people-to-work-remotely/remote-workers-step-grid-3.png)](empower-people-to-work-remotely-security-compliance.md)</span></span>

<span data-ttu-id="09a72-179">Microsoft 365 のセキュリティとコンプライアンスのサービスを展開して、お客様のアプリケーション、データ、およびデバイスを保護するには [手順 3](empower-people-to-work-remotely-security-compliance.md) に進んでください。</span><span class="sxs-lookup"><span data-stu-id="09a72-179">Continue with [Step 3](empower-people-to-work-remotely-security-compliance.md) to deploy Microsoft 365 security and compliance services to protect your apps, data, and devices.</span></span>

