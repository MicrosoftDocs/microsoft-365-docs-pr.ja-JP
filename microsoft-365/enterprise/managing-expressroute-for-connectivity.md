---
title: Office 365 向け ExpressRoute の接続を管理する
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: プレフィックスフィルター、セキュリティ、コンプライアンスなど、構成する共通領域を含む Office 365 の ExpressRoute を管理する方法について説明します。
ms.openlocfilehash: 5b55150b91b68954cb7b701afb7cf46ab9b951dd
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46692223"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a><span data-ttu-id="4418d-103">Office 365 向け ExpressRoute の接続を管理する</span><span class="sxs-lookup"><span data-stu-id="4418d-103">Managing ExpressRoute for Office 365 connectivity</span></span>

<span data-ttu-id="4418d-104">Office 365 用 ExpressRoute は、インターネットに送信されるすべてのトラフィックを必要とせずに、多くの Office 365 サービスにアクセスするための代替ルーティングパスを提供します。</span><span class="sxs-lookup"><span data-stu-id="4418d-104">ExpressRoute for Office 365 offers an alternative routing path to reach many Office 365 services without needing all traffic to egress to the internet.</span></span> <span data-ttu-id="4418d-105">Office 365 へのインターネット接続は依然として必要ですが、Microsoft が BGP を使用してネットワークにアドバタイズする際には、ネットワークに他の構成が存在しない限り、直接 ExpressRoute 回線を優先させる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4418d-105">Although the internet connection to Office 365 is still needed, the specific routes that Microsoft advertises through BGP to your network make the direct ExpressRoute circuit preferred unless there are other configurations in your network.</span></span> <span data-ttu-id="4418d-106">このルーティングを管理するために構成する共通領域には、プレフィックスのフィルター、セキュリティ、コンプライアンスがあります。</span><span class="sxs-lookup"><span data-stu-id="4418d-106">The three common areas you may want to configure to manage this routing include prefix filtering, security, and compliance.</span></span>
  
> [!NOTE]
> <span data-ttu-id="4418d-107">Microsoft は、Azure ExpressRoute の Microsoft ピアリングルーティングドメインの確認方法を変更しました。</span><span class="sxs-lookup"><span data-stu-id="4418d-107">Microsoft changed how the Microsoft Peering routing domain is reviewed for Azure ExpressRoute.</span></span> <span data-ttu-id="4418d-108">2017年7月31日以降、Azure ExpressRoute のすべてのお客様は、Azure 管理コンソールまたは PowerShell を使用して、Microsoft のピアリングを直接有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="4418d-108">Starting July 31st, 2017, all Azure ExpressRoute customers can enable Microsoft Peering directly from the Azure Administrative console or via PowerShell.</span></span> <span data-ttu-id="4418d-109">Microsoft ピアリングを有効にした後は、すべてのお客様は、Dynamics 365 カスタマーエンゲージメントアプリケーション (旧称 CRM Online) の BGP route 広告を受信するルートフィルターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4418d-109">After enabling Microsoft Peering, any customer can create route filters to receive BGP route advertisements for Dynamics 365 Customer Engagement applications (Formerly known as CRM Online).</span></span> <span data-ttu-id="4418d-110">Office 365 用の Azure ExpressRoute を必要とするお客様は、Office 365 のルートフィルターを作成する前に、マイクロソフトからレビューを受ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="4418d-110">Customers needing Azure ExpressRoute for Office 365 must obtain review from Microsoft before they can create route filters for Office 365.</span></span> <span data-ttu-id="4418d-111">Office 365 ExpressRoute を有効にするためのレビューを要求する方法については、Microsoft アカウントチームにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="4418d-111">Please contact your Microsoft Account team to learn about how to request a review for enabling Office 365 ExpressRoute.</span></span> <span data-ttu-id="4418d-112">承認されていないサブスクリプション Office 365 のルートフィルターを作成しようとすると、[エラーメッセージ](https://support.microsoft.com/kb/3181709)が表示される</span><span class="sxs-lookup"><span data-stu-id="4418d-112">Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709)</span></span>
  
## <a name="prefix-filtering"></a><span data-ttu-id="4418d-113">プレフィックスフィルター</span><span class="sxs-lookup"><span data-stu-id="4418d-113">Prefix filtering</span></span>

<span data-ttu-id="4418d-114">Microsoft では、すべての BGP ルートを Microsoft から提供されたとおりにお客様が受け入れることをお勧めします。提供されるルートには、追加された精査のメリットを排除するための厳密なレビューと検証プロセス</span><span class="sxs-lookup"><span data-stu-id="4418d-114">Microsoft recommends that customers accept all BGP routes as advertised from Microsoft, the routes provided undergo a rigorous review and validation process removing any benefits to added scrutiny.</span></span> <span data-ttu-id="4418d-115">ExpressRoute はネイティブに、お客様側で受信ルートフィルターを使用せずに、IP プレフィックスの所有権、整合性、スケールなどの推奨されるコントロールを提供します。</span><span class="sxs-lookup"><span data-stu-id="4418d-115">ExpressRoute natively offers the recommended controls such as IP prefix ownership, integrity, and scale - with no inbound route filtering on the customer side.</span></span>
  
<span data-ttu-id="4418d-116">ExpressRoute のパブリックピア間でルートの所有権を追加で検証する必要がある場合は、アドバタイズされたルートを、 [Microsoft のパブリック ip 範囲](https://www.microsoft.com/download/details.aspx?id=53602)を表す IPv4 および IPv6 のすべての ip プレフィックスの一覧に対して確認できます。</span><span class="sxs-lookup"><span data-stu-id="4418d-116">If you require additional validation of route ownership across ExpressRoute public peering, you can check the advertised routes against the list of all IPv4 and IPv6 IP prefixes that represent [Microsoft's public IP ranges](https://www.microsoft.com/download/details.aspx?id=53602).</span></span> <span data-ttu-id="4418d-117">これらの範囲は、完全な Microsoft アドレススペースをカバーしており、頻繁には変更されません。また、フィルター処理する範囲の信頼性の高いセットを提供することで、Microsoft が所有していないユーザーが環境にリークしていることを懸念している顧客にも追加の保護を提供します</span><span class="sxs-lookup"><span data-stu-id="4418d-117">These ranges cover the full Microsoft address space and change infrequently, providing a reliable set of ranges to filter against that also provides additional protection to customers who are concerned about non-Microsoft owned routes leaking into their environment.</span></span> <span data-ttu-id="4418d-118">変更がある場合は、その月の1日に実行され、ページの [ **詳細** ] セクションのバージョン番号は、ファイルが更新されるたびに変更されます。</span><span class="sxs-lookup"><span data-stu-id="4418d-118">In the event there is a change, it will be made on the 1st of the month and the version number in the **details** section of the page will change every time the file is updated.</span></span>
  
<span data-ttu-id="4418d-119">プレフィックスフィルターリストを生成するために [Office 365 の url と IP アドレスの範囲](https://aka.ms/o365endpoints) を使用しないようにするには、いくつかの理由が考えられます。</span><span class="sxs-lookup"><span data-stu-id="4418d-119">There are a number of reasons to avoid the use of the [Office 365 URLs and IP address ranges](https://aka.ms/o365endpoints) for generating prefix filter lists.</span></span> <span data-ttu-id="4418d-120">次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4418d-120">Including the following:</span></span>
  
- <span data-ttu-id="4418d-121">Office 365 の IP プレフィックスは、頻繁に多くの変更を行います。</span><span class="sxs-lookup"><span data-stu-id="4418d-121">The Office 365 IP prefixes undergo lots of changes on a frequent basis.</span></span>

- <span data-ttu-id="4418d-122">Office 365 の Url と IP アドレスの範囲は、ルーティングではなく、ファイアウォールの許可リストとプロキシインフラストラクチャを管理するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="4418d-122">The Office 365 URLs and IP address ranges are designed for managing firewall allow lists and Proxy infrastructure, not routing.</span></span>

- <span data-ttu-id="4418d-123">Office 365 の Url と IP アドレスの範囲は、ExpressRoute 接続のスコープ内にある他の Microsoft サービスをカバーしていません。</span><span class="sxs-lookup"><span data-stu-id="4418d-123">The Office 365 URLs and IP address ranges do not cover other Microsoft services that may be in scope for your ExpressRoute connections.</span></span>

|<span data-ttu-id="4418d-124">**オプション**</span><span class="sxs-lookup"><span data-stu-id="4418d-124">**Option**</span></span>|<span data-ttu-id="4418d-125">**複雑さ**</span><span class="sxs-lookup"><span data-stu-id="4418d-125">**Complexity**</span></span>|<span data-ttu-id="4418d-126">**変更管理**</span><span class="sxs-lookup"><span data-stu-id="4418d-126">**Change Control**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="4418d-127">Microsoft のすべてのルートを受け入れる</span><span class="sxs-lookup"><span data-stu-id="4418d-127">Accept all Microsoft routes</span></span>  <br/> |<span data-ttu-id="4418d-128">**低:** お客様は Microsoft コントロールに依存して、すべてのルートが適切に所有されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4418d-128">**Low:** Customer relies upon Microsoft controls to ensure all routes are properly owned.</span></span>  <br/> |<span data-ttu-id="4418d-129">なし</span><span class="sxs-lookup"><span data-stu-id="4418d-129">None</span></span>  <br/> |
|<span data-ttu-id="4418d-130">Microsoft が所有するスーパーネットにフィルターを適用する</span><span class="sxs-lookup"><span data-stu-id="4418d-130">Filter Microsoft owned supernets</span></span>  <br/> |<span data-ttu-id="4418d-131">**中:** 顧客は、Microsoft が所有するルートのみを許可するように、集約されたプレフィックスフィルターリストを実装します。</span><span class="sxs-lookup"><span data-stu-id="4418d-131">**Medium:** Customer implements summarized prefix filter lists to allow only Microsoft owned routes.</span></span>  <br/> |<span data-ttu-id="4418d-132">お客様は、頻度の低い更新プログラムがルートフィルターに反映されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4418d-132">Customers must ensure the infrequent updates are reflected in route filters.</span></span>  <br/> |
|<span data-ttu-id="4418d-133">Office 365 IP 範囲のフィルター処理</span><span class="sxs-lookup"><span data-stu-id="4418d-133">Filter Office 365 IP ranges</span></span>  <br/> [!CAUTION] <span data-ttu-id="4418d-134">推奨されない</span><span class="sxs-lookup"><span data-stu-id="4418d-134">Not-Recommended</span></span> |<span data-ttu-id="4418d-135">**高:** 顧客は、定義された Office 365 IP プレフィックスに基づいてルートをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="4418d-135">**High:** Customer filters routes based on defined Office 365 IP prefixes.</span></span>  <br/> |<span data-ttu-id="4418d-136">お客様は毎月の更新プログラムに対して、堅牢な変更管理プロセスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4418d-136">Customers must implement a robust change management process for the monthly updates.</span></span>  <br/> [!CAUTION] <span data-ttu-id="4418d-137">このソリューションでは、継続的な変更が必要になります。</span><span class="sxs-lookup"><span data-stu-id="4418d-137">This solution requires significant on-going changes.</span></span> <span data-ttu-id="4418d-138">時間内に実装されていない変更は、サービスの停止につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4418d-138">Changes not implemented in time will likely result in a service outage.</span></span>   |

<span data-ttu-id="4418d-139">Azure ExpressRoute を使用した Office 365 への接続は、Office 365 エンドポイントが展開されているネットワークを表す特定の IP サブネットの BGP 広告に基づいています。</span><span class="sxs-lookup"><span data-stu-id="4418d-139">Connecting to Office 365 using Azure ExpressRoute is based on BGP advertisements of specific IP subnets that represent networks where Office 365 endpoints are deployed.</span></span> <span data-ttu-id="4418d-140">Office 365 のグローバルな性質と Office 365 を構成するサービスの数により、多くの場合、お客様はネットワークにおいて受け入れる広告を管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4418d-140">Due to the global nature of Office 365 and the number of services that make up Office 365, customers often have a need to manage the advertisements they accept on their network.</span></span> <span data-ttu-id="4418d-141">ご使用の環境にアドバタイズされているプレフィックスの数について懸念している場合は、 [BGP コミュニティ](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) 機能を使用して、特定の Office 365 サービスセットに対して広告をフィルター処理することができます。</span><span class="sxs-lookup"><span data-stu-id="4418d-141">If you're concerned with number of prefixes advertised into your environment, the [BGP community](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) feature allows you to filter the advertisements to a specific set of Office 365 services.</span></span> <span data-ttu-id="4418d-142">これで、この機能はプレビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4418d-142">This feature is now in preview.</span></span>
  
<span data-ttu-id="4418d-143">Microsoft からの BGP ルート広告を管理する方法に関係なく、インターネット回線だけ経由で Office 365 に接続するのと比較して、Office 365 サービスに特別な影響を与えることはありません。</span><span class="sxs-lookup"><span data-stu-id="4418d-143">Regardless of how you manage the BGP route advertisements coming from Microsoft, you won't gain any special exposure to Office 365 services when compared to connecting to Office 365 over an internet circuit alone.</span></span> <span data-ttu-id="4418d-144">Microsoft は、お客様が Office 365 への接続に使用する回線の種類に関係なく、同じセキュリティ、コンプライアンス、およびパフォーマンスレベルを維持します。</span><span class="sxs-lookup"><span data-stu-id="4418d-144">Microsoft maintains the same security, compliance, and performance levels regardless of the type of circuit a customer uses to connect to Office 365.</span></span>
  
### <a name="security"></a><span data-ttu-id="4418d-145">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4418d-145">Security</span></span>

<span data-ttu-id="4418d-146">Microsoft では、Office 365 サービスとの接続を含む、ExpressRoute パブリックおよび Microsoft ピアとの間で送受信される接続について、独自のネットワークおよびセキュリティ境界の制御を維持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4418d-146">Microsoft recommends that you maintain your own network and security perimeter controls for connections going to and from ExpressRoute public and Microsoft peering, which includes connections to and from Office 365 services.</span></span> <span data-ttu-id="4418d-147">ネットワークから microsoft のネットワークへの受信だけでなく、ネットワークから Microsoft のネットワークへの送信を転送するネットワーク要求には、セキュリティコントロールを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4418d-147">Security controls should be in place for network requests that travel outbound from your network to Microsoft's network as well as inbound from Microsoft's network to your network.</span></span>
  
#### <a name="outbound-from-customer-to-microsoft"></a><span data-ttu-id="4418d-148">お客様から Microsoft への送信</span><span class="sxs-lookup"><span data-stu-id="4418d-148">Outbound from Customer to Microsoft</span></span>
  
<span data-ttu-id="4418d-149">コンピューターが Office 365 に接続する場合、接続がインターネットまたは ExpressRoute のどちらで行われているかにかかわらず、同じエンドポイントに接続されます。</span><span class="sxs-lookup"><span data-stu-id="4418d-149">When computers connect to Office 365, they connect to the same set of endpoints regardless of whether the connection is made over an internet or ExpressRoute circuit.</span></span> <span data-ttu-id="4418d-150">使用されている回線に関係なく、Office 365 サービスは、一般的なインターネットの宛先よりも信頼度の高いものとして扱うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4418d-150">Regardless of the circuit being used, Microsoft recommends that you treat Office 365 services as more trusted than generic internet destinations.</span></span> <span data-ttu-id="4418d-151">送信セキュリティ制御は、ポートとプロトコルに焦点を合わせて、公開を減らし、継続的な保守を最小限に抑えます。</span><span class="sxs-lookup"><span data-stu-id="4418d-151">Your outbound security controls should focus on the ports and protocols to reduce exposure and minimize ongoing maintenance.</span></span> <span data-ttu-id="4418d-152">必要なポート情報は、「 [Office 365 エンドポイント](https://aka.ms/o365endpoints) リファレンス」の記事で参照できます。</span><span class="sxs-lookup"><span data-stu-id="4418d-152">The required port information is available in the [Office 365 endpoints](https://aka.ms/o365endpoints) reference article.</span></span>
  
<span data-ttu-id="4418d-153">追加のコントロールについては、プロキシインフラストラクチャ内で FQDN レベルフィルターを使用して、インターネットまたは Office 365 宛ての一部またはすべてのネットワーク要求を制限または検査することができます。</span><span class="sxs-lookup"><span data-stu-id="4418d-153">For added controls, you can use FQDN level filtering within your proxy infrastructure to restrict or inspect some or all network requests destined for the internet or Office 365.</span></span> <span data-ttu-id="4418d-154">機能がリリースされ、Office 365 オファーリングが進化するにつれて Fqdn のリストを維持するには、公開された [office 365 エンドポイント](https://aka.ms/o365endpoints)への変更をより強力に管理および追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4418d-154">Maintaining the list of FQDNs as features are released and the Office 365 offerings evolve requires more robust change management and tracking of changes to the published [Office 365 endpoints](https://aka.ms/o365endpoints).</span></span>
  
> [!CAUTION]
> <span data-ttu-id="4418d-155">Microsoft では、Office 365 への送信セキュリティを管理するために IP プレフィックスだけに頼ることはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="4418d-155">Microsoft recommends you don't rely solely on IP prefixes to manage outbound security to Office 365.</span></span>

|<span data-ttu-id="4418d-156">**オプション**</span><span class="sxs-lookup"><span data-stu-id="4418d-156">**Option**</span></span>|<span data-ttu-id="4418d-157">**複雑さ**</span><span class="sxs-lookup"><span data-stu-id="4418d-157">**Complexity**</span></span>|<span data-ttu-id="4418d-158">**変更管理**</span><span class="sxs-lookup"><span data-stu-id="4418d-158">**Change Control**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="4418d-159">制限なし</span><span class="sxs-lookup"><span data-stu-id="4418d-159">No restrictions</span></span>  <br/> |<span data-ttu-id="4418d-160">**低:** お客様は、Microsoft への送信アクセスを無制限に許可します。</span><span class="sxs-lookup"><span data-stu-id="4418d-160">**Low:** Customer allows unrestricted outbound access to Microsoft.</span></span>  <br/> |<span data-ttu-id="4418d-161">なし</span><span class="sxs-lookup"><span data-stu-id="4418d-161">None</span></span>  <br/> |
|<span data-ttu-id="4418d-162">ポートの制限</span><span class="sxs-lookup"><span data-stu-id="4418d-162">Port restrictions</span></span>  <br/> |<span data-ttu-id="4418d-163">**低:** お客様は、必要なポートで Microsoft への送信アクセスを制限しています。</span><span class="sxs-lookup"><span data-stu-id="4418d-163">**Low:** Customer restricts outbound access to Microsoft by the expected ports.</span></span>  <br/> |<span data-ttu-id="4418d-164">ときどき.</span><span class="sxs-lookup"><span data-stu-id="4418d-164">Infrequent.</span></span>  <br/> |
|<span data-ttu-id="4418d-165">FQDN の制限</span><span class="sxs-lookup"><span data-stu-id="4418d-165">FQDN restrictions</span></span>  <br/> |<span data-ttu-id="4418d-166">**高:** お客様は、公開された Fqdn に基づいて Office 365 への送信アクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="4418d-166">**High:** Customer restricts outbound access to Office 365 based on the published FQDNs.</span></span>  <br/> |<span data-ttu-id="4418d-167">月単位の変更。</span><span class="sxs-lookup"><span data-stu-id="4418d-167">Monthly changes.</span></span>  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a><span data-ttu-id="4418d-168">Microsoft からお客様への受信</span><span class="sxs-lookup"><span data-stu-id="4418d-168">Inbound from Microsoft to Customer</span></span>
  
<span data-ttu-id="4418d-169">Microsoft がネットワークへの接続を開始する必要がある、いくつかのオプションのシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="4418d-169">There are several optional scenarios that require Microsoft to initiate connections to your network.</span></span>
  
- <span data-ttu-id="4418d-170">サインインのパスワードの検証中に ADFS が有効になります。</span><span class="sxs-lookup"><span data-stu-id="4418d-170">ADFS during password validation for sign-in.</span></span>

- <span data-ttu-id="4418d-171">[Exchange Server のハイブリッド展開](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4418d-171">[Exchange Server Hybrid deployments](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).</span></span>

- <span data-ttu-id="4418d-172">Exchange Online テナントから社内ホストへのメール。</span><span class="sxs-lookup"><span data-stu-id="4418d-172">Mail from an Exchange Online tenant to an on-premises host.</span></span>

- <span data-ttu-id="4418d-173">Sharepoint online からオンプレミスのホストへの SharePoint online メール送信。</span><span class="sxs-lookup"><span data-stu-id="4418d-173">SharePoint Online Mail send from SharePoint Online to an on-premises host.</span></span>

- <span data-ttu-id="4418d-174">[SharePoint フェデレーションハイブリッド検索](https://technet.microsoft.com/library/dn197174.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4418d-174">[SharePoint federated hybrid search](https://technet.microsoft.com/library/dn197174.aspx).</span></span>

- <span data-ttu-id="4418d-175">[SharePoint ハイブリッド BCS](https://technet.microsoft.com/library/dn197239.aspx )。</span><span class="sxs-lookup"><span data-stu-id="4418d-175">[SharePoint hybrid BCS](https://technet.microsoft.com/library/dn197239.aspx ).</span></span>

- <span data-ttu-id="4418d-176">[Skype](https://technet.microsoft.com/library/jj205403.aspx) for business ハイブリッドおよび/または skype for business [フェデレーション](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4418d-176">[Skype for Business hybrid](https://technet.microsoft.com/library/jj205403.aspx) and/or [Skype for Business federation](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).</span></span>

- <span data-ttu-id="4418d-177">[Skype For Business Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx )。</span><span class="sxs-lookup"><span data-stu-id="4418d-177">[Skype for Business Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx ).</span></span>

<span data-ttu-id="4418d-178">このような接続は、ExpressRoute 回線ではなく、インターネット回線を介して使用して、複雑さを軽減することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4418d-178">Microsoft recommends that you accept these connections over your internet circuit instead of your ExpressRoute circuit to reduce complexity.</span></span> <span data-ttu-id="4418d-179">コンプライアンスまたはパフォーマンスによって、これらの受信接続が ExpressRoute 回線経由で受け入れられるようにするには、ファイアウォールまたはリバースプロキシを使用して、受け入れられた接続のスコープを設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4418d-179">If your compliance or performance needs dictate these inbound connections must be accepted over an ExpressRoute circuit, using a firewall or reverse proxy to scope the accepted connections is recommended.</span></span> <span data-ttu-id="4418d-180">[Office 365 エンドポイント](https://aka.ms/o365endpoints)を使用して、右側の FQDN と IP プレフィックスを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="4418d-180">You can use the [Office 365 endpoints](https://aka.ms/o365endpoints) to figure out the right FQDNs and IP prefixes.</span></span>
  
### <a name="compliance"></a><span data-ttu-id="4418d-181">コンプライアンス</span><span class="sxs-lookup"><span data-stu-id="4418d-181">Compliance</span></span>

<span data-ttu-id="4418d-182">コンプライアンスコントロールに使用するルーティングパスに依存していません。</span><span class="sxs-lookup"><span data-stu-id="4418d-182">We don't rely on the routing path you use for any of our compliance controls.</span></span> <span data-ttu-id="4418d-183">ExpressRoute またはインターネット回線経由で Office 365 サービスに接続するかどうかに関係なく、コンプライアンスコントロールは変更されません。</span><span class="sxs-lookup"><span data-stu-id="4418d-183">Regardless of whether you connect to Office 365 services over an ExpressRoute or internet circuit, our compliance controls won't change.</span></span> <span data-ttu-id="4418d-184">Office 365 のさまざまなコンプライアンスおよびセキュリティ証明レベルを確認して、組織のニーズを満たすための最適な選択を判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4418d-184">You should review the different compliance and security certification levels for Office 365 to figure out the best choice for meeting your organization's needs.</span></span>
  
<span data-ttu-id="4418d-185">ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)</span><span class="sxs-lookup"><span data-stu-id="4418d-185">Here's a short link you can use to come back: [https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="4418d-186">関連項目</span><span class="sxs-lookup"><span data-stu-id="4418d-186">Related topics</span></span>

[<span data-ttu-id="4418d-187">コンテンツ配信ネットワーク</span><span class="sxs-lookup"><span data-stu-id="4418d-187">Content delivery networks</span></span>](content-delivery-networks.md)
  
[<span data-ttu-id="4418d-188">Office 365 の URL と IP アドレスの範囲</span><span class="sxs-lookup"><span data-stu-id="4418d-188">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="4418d-189">Office 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="4418d-189">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="4418d-190">Azure ExpressRoute for Office 365 のトレーニング</span><span class="sxs-lookup"><span data-stu-id="4418d-190">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer)