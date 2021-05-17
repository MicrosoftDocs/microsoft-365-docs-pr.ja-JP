---
title: コンテンツ検索を使用してサードパーティのインポートされたデータを検索する
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection: M365-security-compliance
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: ec2677ff-c4d7-4363-a9e7-22c80e015688
description: コンテンツ検索電子情報開示ツールを使用して、クエリを作成して、Microsoft 365データ ソースからメールボックスにインポートされたアイテムを検索します。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 24ca63cf78b85f7b8b5181d5babd16058b641128
ms.sourcegitcommit: 25afc0c34edc7f8a5eb389d8c701175256c58ec8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2020
ms.locfileid: "47324573"
---
# <a name="use-content-search-to-search-third-party-data-imported-by-a-custom-partner-connector"></a><span data-ttu-id="8623b-103">コンテンツ検索を使用して、カスタム パートナー コネクタによってインポートされたサードパーティのデータを検索する</span><span class="sxs-lookup"><span data-stu-id="8623b-103">Use Content Search to search third-party data imported by a custom partner connector</span></span>

<span data-ttu-id="8623b-104">セキュリティ &[](content-search.md)コンプライアンス センターのコンテンツ検索電子情報開示ツールを使用して、サードパーティのデータ ソースから Microsoft 365 内のメールボックスにインポートされたアイテムを検索できます。</span><span class="sxs-lookup"><span data-stu-id="8623b-104">You can use the [Content Search eDiscovery tool](content-search.md) in the Security & Compliance Center to search for items imported to mailboxes in Microsoft 365 from a third-party data source.</span></span> <span data-ttu-id="8623b-105">インポートされたサード パーティのすべてのデータ アイテムを検索するクエリを作成するか、特定のサード パーティのデータ アイテムを検索するクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8623b-105">You can create a query to search all imported third-party data items or you can create a query to search specific third-party data items.</span></span> <span data-ttu-id="8623b-106">また、クエリ ベースのアイテム保持ポリシーまたはクエリ ベースの電子情報開示保持を作成して、サード パーティのデータを保持することもできます。</span><span class="sxs-lookup"><span data-stu-id="8623b-106">Also, you can also create a query-based retention policy or a query-based eDiscovery hold to preserve third-party data.</span></span>
  
<span data-ttu-id="8623b-107">パートナーと一緒にサード パーティ データをインポートする方法と、Microsoft 365 にインポートできるサード パーティのデータ型の一覧の詳細については、「パートナーと一緒に作業して Office 365 でサード パーティのデータをアーカイブする」[を参照してください](work-with-partner-to-archive-third-party-data.md)。</span><span class="sxs-lookup"><span data-stu-id="8623b-107">For more information about working with a partner to import third-party data and a list of the third-party data types that you can import to Microsoft 365, see [Work with a partner to archive third-party data in Office 365](work-with-partner-to-archive-third-party-data.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8623b-108">この記事のガイダンスは、カスタム パートナー コネクタによってインポートされたサードパーティのデータにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8623b-108">The guidance in this article only applies to third-party data that was imported by a custom partner connector.</span></span> <span data-ttu-id="8623b-109">この記事は、Microsoft コンプライアンス センターでサード パーティのデータ コネクタ[](archiving-third-party-data.md#third-party-data-connectors)を使用してインポートされるサード パーティのデータには適用されません。</span><span class="sxs-lookup"><span data-stu-id="8623b-109">This article doesn't apply to third-party data that is imported by using the [third-party data connectors](archiving-third-party-data.md#third-party-data-connectors) in the Microsoft compliance center.</span></span>
  
## <a name="creating-a-query-to-search-all-third-party-data"></a><span data-ttu-id="8623b-110">すべてのサード パーティのデータを検索するためのクエリの作成</span><span class="sxs-lookup"><span data-stu-id="8623b-110">Creating a query to search all third-party data</span></span>

<span data-ttu-id="8623b-111">Office 365 にインポートした任意の種類のサードパーティ データを検索 (または保留) するには、コンテンツ検索のキーワード ボックスまたはクエリ ベースの保留リストを作成するときに、メッセージ プロパティと値のペアを使用できます。 `kind:externaldata`</span><span class="sxs-lookup"><span data-stu-id="8623b-111">To search (or place on hold) any type of third-party data that you've imported to Office 365, you can use the  `kind:externaldata` message property-value pair in the keyword box for a Content Search or when creating a query-based hold.</span></span> <span data-ttu-id="8623b-112">たとえば、サードパーティのデータ ソースからインポートされたアイテムを検索し、インポートしたアイテムの Subject プロパティに "contoso" という単語を含むには、次のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="8623b-112">For example, to search for items imported from any third-party data source and contain the word "contoso" in the Subject property of the imported item, you would use the following query:</span></span> 
  
```powershell
kind:externaldata AND subject:contoso
```

<span data-ttu-id="8623b-113">前のキーワード クエリの例には、subject プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8623b-113">The previous keyword query example includes the subject property.</span></span> <span data-ttu-id="8623b-114">キーワード クエリに含めるサードパーティのデータ アイテムのその他のプロパティの一覧については、「パートナーと一緒に作業して、Office 365 でサード パーティのデータをアーカイブする」の「詳細[」セクションを参照してください](work-with-partner-to-archive-third-party-data.md#more-information)。</span><span class="sxs-lookup"><span data-stu-id="8623b-114">For a list of other properties for third-party data items that can include in a keyword query, see the "More information" section in [Work with a partner to archive third-party data in Office 365](work-with-partner-to-archive-third-party-data.md#more-information).</span></span>
  
<span data-ttu-id="8623b-115">サードパーティのデータを検索および保持するためのクエリを作成する場合は、条件を使用して検索結果を絞り込む方法も使用できます。</span><span class="sxs-lookup"><span data-stu-id="8623b-115">When creating queries to search and hold third-party data, you can also use conditions to narrow the search results.</span></span> <span data-ttu-id="8623b-116">コンテンツ検索クエリの作成の詳細については、「コンテンツ検索のキーワード クエリと [検索条件」を参照してください](keyword-queries-and-search-conditions.md)。</span><span class="sxs-lookup"><span data-stu-id="8623b-116">For more information about creating Content Search queries, see [Keyword queries and search conditions for Content Search](keyword-queries-and-search-conditions.md).</span></span>
  
## <a name="creating-a-query-to-search-specific-types-of-third-party-data"></a><span data-ttu-id="8623b-117">特定の種類のサード パーティ製データを検索するためのクエリの作成</span><span class="sxs-lookup"><span data-stu-id="8623b-117">Creating a query to search specific types of third-party data</span></span>

<span data-ttu-id="8623b-118">すべての種類のサード パーティ製データを検索する代わりに、コンテンツ検索のキーワード ボックスの値ペアというメッセージ プロパティを使用して、指定した種類のサードパーティ データのみを検索するクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8623b-118">Instead of searching all types of third-party data, you can create queries that only search for a specify type of third-party data by using the following message *property: value* pair in the keyword box for a Content Search:</span></span>
  
```powershell
itemclass:ipm.externaldata.<third-party data type>* 
```

<span data-ttu-id="8623b-119">たとえば、Subject プロパティの "contoso" という単語を含む Facebook データを検索するには、次のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="8623b-119">For example, to search Facebook data that contains the word "contoso" in the Subject property, you would use the following query:</span></span>
  
```powershell
itemclass:ipm.externaldata.Facebook* AND subject:contoso
```

<span data-ttu-id="8623b-120">次の表に、検索できるサード パーティのデータ型と、その種類のサード パーティ データを具体的に検索する message プロパティに使用する値  `itemclass:` を示します。</span><span class="sxs-lookup"><span data-stu-id="8623b-120">The following table lists the third-party data types that you can search, and the value to use for the  `itemclass:` message property to specifically search for that type of third-party data.</span></span> <span data-ttu-id="8623b-121">クエリ構文では大文字と小文字が区別されません。</span><span class="sxs-lookup"><span data-stu-id="8623b-121">The query syntax isn't case-sensitive.</span></span> 
  
|<span data-ttu-id="8623b-122">**サード パーティ製のデータ型**</span><span class="sxs-lookup"><span data-stu-id="8623b-122">**Third-party data type**</span></span>|<span data-ttu-id="8623b-123">**プロパティの  `itemclass:` 値**</span><span class="sxs-lookup"><span data-stu-id="8623b-123">**Value for  `itemclass:` property**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8623b-124">AIM</span><span class="sxs-lookup"><span data-stu-id="8623b-124">AIM</span></span>  <br/> | `ipm.externaldata.AIM*` <br/> |
|<span data-ttu-id="8623b-125">American Idol</span><span class="sxs-lookup"><span data-stu-id="8623b-125">American Idol</span></span>  <br/> | `ipm.externaldata.AmericanIdol*` <br/> |
|<span data-ttu-id="8623b-126">AOL with Pivot クライアント</span><span class="sxs-lookup"><span data-stu-id="8623b-126">AOL with Pivot Client</span></span>  <br/> | `ipm.externaldata.Pivot.IM` <br/> |
|<span data-ttu-id="8623b-127">Apple Juice</span><span class="sxs-lookup"><span data-stu-id="8623b-127">Apple Juice</span></span>  <br/> | `ipm.externaldata.AppleJuice*` <br/> |
|<span data-ttu-id="8623b-128">Ares</span><span class="sxs-lookup"><span data-stu-id="8623b-128">Ares</span></span>  <br/> | `ipm.externaldata.Ares*` <br/> |
|<span data-ttu-id="8623b-129">Axs Encrypted</span><span class="sxs-lookup"><span data-stu-id="8623b-129">Axs Encrypted</span></span>  <br/> | `ipm.externaldata.AxsEncrypted*` <br/> |
|<span data-ttu-id="8623b-130">Axs Exchange</span><span class="sxs-lookup"><span data-stu-id="8623b-130">Axs Exchange</span></span>  <br/> | `ipm.externaldata.AxsExchange*` <br/> |
|<span data-ttu-id="8623b-131">Axs Local Archive</span><span class="sxs-lookup"><span data-stu-id="8623b-131">Axs Local Archive</span></span>  <br/> | `ipm.externaldata.AxsLocalArchive*` <br/> |
|<span data-ttu-id="8623b-132">Axs プレースホルダー</span><span class="sxs-lookup"><span data-stu-id="8623b-132">Axs Placeholder</span></span>  <br/> | `ipm.externaldata.AxsPlaceHolder*` <br/> |
|<span data-ttu-id="8623b-133">Axs Signed</span><span class="sxs-lookup"><span data-stu-id="8623b-133">Axs Signed</span></span>  <br/> | `ipm.externaldata.AxsSigned*` <br/> |
|<span data-ttu-id="8623b-134">Bazaarvoice</span><span class="sxs-lookup"><span data-stu-id="8623b-134">Bazaarvoice</span></span>  <br/> | `ipm.externaldata.Bazaarvoice*` <br/> |
|<span data-ttu-id="8623b-135">Bearshare</span><span class="sxs-lookup"><span data-stu-id="8623b-135">Bearshare</span></span>  <br/> | `ipm.externaldata.Bearshare*` <br/> |
|<span data-ttu-id="8623b-136">BitTorrent</span><span class="sxs-lookup"><span data-stu-id="8623b-136">BitTorrent</span></span>  <br/> | `ipm.externaldata.BitTorrent*` <br/> |
|<span data-ttu-id="8623b-137">Blackberry</span><span class="sxs-lookup"><span data-stu-id="8623b-137">Blackberry</span></span>  <br/> | `ipm.externaldata.Blackberry*` <br/> |
|<span data-ttu-id="8623b-138">BlackBerry 通話ログ</span><span class="sxs-lookup"><span data-stu-id="8623b-138">BlackBerry Call Logs</span></span>  <br/> | `ipm.externaldata.BlackBerryCall*` <br/> |
|<span data-ttu-id="8623b-139">BlackBerry Messenger</span><span class="sxs-lookup"><span data-stu-id="8623b-139">BlackBerry Messenger</span></span>  <br/> | `ipm.externaldata.BlackBerryMessenger*` <br/> |
|<span data-ttu-id="8623b-140">BlackBerry PIN</span><span class="sxs-lookup"><span data-stu-id="8623b-140">BlackBerry PIN</span></span>  <br/> | `ipm.externaldata.BlackBerryPIN*` <br/> |
|<span data-ttu-id="8623b-141">BlackBerry 携帯ショートメール</span><span class="sxs-lookup"><span data-stu-id="8623b-141">BlackBerry SMS</span></span>  <br/> | `ipm.externaldata.BlackBerrySMS*` <br/> |
|<span data-ttu-id="8623b-142">ブルームバーグ</span><span class="sxs-lookup"><span data-stu-id="8623b-142">Bloomberg</span></span>  <br/> | `ipm.externaldata.Bloomberg*` <br/> |
|<span data-ttu-id="8623b-143">Bloomberg メッセージ</span><span class="sxs-lookup"><span data-stu-id="8623b-143">Bloomberg Message</span></span>  <br/> | `ipm.externaldata.conversation.Bloomberg Message*` <br/> |
|<span data-ttu-id="8623b-144">ブルームバーグ メッセージング</span><span class="sxs-lookup"><span data-stu-id="8623b-144">Bloomberg Messaging</span></span>  <br/> | `ipm.externaldata.BloombergMessaging*` <br/> |
|<span data-ttu-id="8623b-145">検索ボックス</span><span class="sxs-lookup"><span data-stu-id="8623b-145">Box</span></span>  <br/> | `ipm.externaldata.Box*` <br/> |
|<span data-ttu-id="8623b-146">Cisco IM &amp; Presence Server</span><span class="sxs-lookup"><span data-stu-id="8623b-146">Cisco IM &amp; Presence Server</span></span>  <br/> | `ipm.externaldata.Jabber.IM` <br/> |
|<span data-ttu-id="8623b-147">Cisco Jabber</span><span class="sxs-lookup"><span data-stu-id="8623b-147">Cisco Jabber</span></span>  <br/> | `ipm.externaldata.Jabber*` <br/> |
|<span data-ttu-id="8623b-148">CipherCloud for Salesforce Chatter</span><span class="sxs-lookup"><span data-stu-id="8623b-148">CipherCloud for Salesforce Chatter</span></span>  <br/> | `ipm.externaldata.Chatter.Post` <br/>  `ipm.externaldata.Chatter.Comment` <br/> |
|<span data-ttu-id="8623b-149">Direct Connect</span><span class="sxs-lookup"><span data-stu-id="8623b-149">Direct Connect</span></span>  <br/> | `ipm.externaldata.DirectConnect*` <br/> |
|<span data-ttu-id="8623b-150">Facebook</span><span class="sxs-lookup"><span data-stu-id="8623b-150">Facebook</span></span>  <br/> | `ipm.externaldata.Facebook*` <br/> |
|<span data-ttu-id="8623b-151">FastTrack</span><span class="sxs-lookup"><span data-stu-id="8623b-151">FastTrack</span></span>  <br/> | `ipm.externaldata.FastTrack*` <br/> |
|<span data-ttu-id="8623b-152">FXConnect</span><span class="sxs-lookup"><span data-stu-id="8623b-152">FXConnect</span></span>  <br/> | `ipm.externaldata.FXConnect.chat` <br/> |
|<span data-ttu-id="8623b-153">Flickr</span><span class="sxs-lookup"><span data-stu-id="8623b-153">Flickr</span></span>  <br/> | `ipm.externaldata.Flickr*` <br/> |
|<span data-ttu-id="8623b-154">Gnutella</span><span class="sxs-lookup"><span data-stu-id="8623b-154">Gnutella</span></span>  <br/> | `ipm.externaldata.Gnutella*` <br/> |
|<span data-ttu-id="8623b-155">Google+</span><span class="sxs-lookup"><span data-stu-id="8623b-155">Google+</span></span>  <br/> | `ipm.externaldata.GooglePlus*` <br/> |
|<span data-ttu-id="8623b-156">Google Talk</span><span class="sxs-lookup"><span data-stu-id="8623b-156">Google Talk</span></span>  <br/> | `ipm.externaldata.GoogleTalk*` <br/> |
|<span data-ttu-id="8623b-157">GoToMyPC</span><span class="sxs-lookup"><span data-stu-id="8623b-157">GoToMyPC</span></span>  <br/> | `ipm.externaldata.GoToMyPC*` <br/> |
|<span data-ttu-id="8623b-158">HipChat</span><span class="sxs-lookup"><span data-stu-id="8623b-158">HipChat</span></span>  <br/> | `ipm.externaldata.HipChat*` <br/> |
|<span data-ttu-id="8623b-159">Hopster</span><span class="sxs-lookup"><span data-stu-id="8623b-159">Hopster</span></span>  <br/> | `ipm.externaldata.Hopster*` <br/> |
|<span data-ttu-id="8623b-160">HubConnex</span><span class="sxs-lookup"><span data-stu-id="8623b-160">HubConnex</span></span>  <br/> | `ipm.externaldata.HubConnex*` <br/> |
|<span data-ttu-id="8623b-161">IBM Connections</span><span class="sxs-lookup"><span data-stu-id="8623b-161">IBM Connections</span></span>  <br/> | `ipm.externaldata.Connections*` <br/> |
|<span data-ttu-id="8623b-162">IBM SameTime</span><span class="sxs-lookup"><span data-stu-id="8623b-162">IBM SameTime</span></span>  <br/> | `ipm.externaldata.Sametime*` <br/> |
|<span data-ttu-id="8623b-163">IceChat</span><span class="sxs-lookup"><span data-stu-id="8623b-163">ICE Chat</span></span>  <br/> | `ipm.externaldata.conversation.Ice Chat*` <br/> |
|<span data-ttu-id="8623b-164">Indii Messenger</span><span class="sxs-lookup"><span data-stu-id="8623b-164">Indii Messenger</span></span>  <br/> | `ipm.externaldata.Indii*` <br/> |
|<span data-ttu-id="8623b-165">Instagram</span><span class="sxs-lookup"><span data-stu-id="8623b-165">Instagram</span></span>  <br/> | `ipm.externaldata.Instagram*` <br/> |
|<span data-ttu-id="8623b-166">Instant Bloomberg</span><span class="sxs-lookup"><span data-stu-id="8623b-166">Instant Bloomberg</span></span>  <br/> | `ipm.externaldata.InstantBloomberg*` <br/> |
|<span data-ttu-id="8623b-167">InvestEdge</span><span class="sxs-lookup"><span data-stu-id="8623b-167">InvestEdge</span></span>  <br/> | `ipm.externaldata.InvestEdge*` <br/> |
|<span data-ttu-id="8623b-168">IRC</span><span class="sxs-lookup"><span data-stu-id="8623b-168">IRC</span></span>  <br/> | `ipm.externaldata.IRC*` <br/> |
|<span data-ttu-id="8623b-169">Jive</span><span class="sxs-lookup"><span data-stu-id="8623b-169">Jive</span></span>  <br/> | `ipm.externaldata.Jive*` <br/> |
|<span data-ttu-id="8623b-170">JiveApiRetention</span><span class="sxs-lookup"><span data-stu-id="8623b-170">JiveApiRetention</span></span>  <br/> | `ipm.externaldata.JiveApiRetention*` <br/> |
|<span data-ttu-id="8623b-171">JXTA</span><span class="sxs-lookup"><span data-stu-id="8623b-171">JXTA</span></span>  <br/> | `ipm.externaldata.JXTA*` <br/> |
|<span data-ttu-id="8623b-172">LinkedIn</span><span class="sxs-lookup"><span data-stu-id="8623b-172">LinkedIn</span></span>  <br/> | `ipm.externaldata.LinkedIn*` <br/> |
|<span data-ttu-id="8623b-173">MFTP</span><span class="sxs-lookup"><span data-stu-id="8623b-173">MFTP</span></span>  <br/> | `ipm.externaldata.MFTP*` <br/> |
|<span data-ttu-id="8623b-174">Microsoft UC</span><span class="sxs-lookup"><span data-stu-id="8623b-174">Microsoft UC</span></span>  <br/> | `ipm.externaldata.MicrosoftUC*` <br/> |
|<span data-ttu-id="8623b-175">Mind Align</span><span class="sxs-lookup"><span data-stu-id="8623b-175">Mind Align</span></span>  <br/> | `ipm.externaldata.MindAlign*` <br/> |
|<span data-ttu-id="8623b-176">Mobile Guard</span><span class="sxs-lookup"><span data-stu-id="8623b-176">Mobile Guard</span></span>  <br/> | `ipm.externaldata.MobileGuard*` <br/> |
|<span data-ttu-id="8623b-177">MSN</span><span class="sxs-lookup"><span data-stu-id="8623b-177">MSN</span></span>  <br/> | `ipm.externaldata.MSN*` <br/> |
|<span data-ttu-id="8623b-178">MySpace</span><span class="sxs-lookup"><span data-stu-id="8623b-178">MySpace</span></span>  <br/> | `ipm.externaldata.MySpace*` <br/> |
|<span data-ttu-id="8623b-179">NEONetwork</span><span class="sxs-lookup"><span data-stu-id="8623b-179">NEONetwork</span></span>  <br/> | `ipm.externaldata.NEONetwork*` <br/> |
|<span data-ttu-id="8623b-180">OpenNap</span><span class="sxs-lookup"><span data-stu-id="8623b-180">OpenNap</span></span>  <br/> | `ipm.externaldata.OpenNap*` <br/> |
|<span data-ttu-id="8623b-181">Pinterest</span><span class="sxs-lookup"><span data-stu-id="8623b-181">Pinterest</span></span>  <br/> | `ipm.externaldata.Pinterest*` <br/> |
|<span data-ttu-id="8623b-182">ピボット</span><span class="sxs-lookup"><span data-stu-id="8623b-182">Pivot</span></span>  <br/> | `ipm.externaldata.Pivot*` <br/> |
|<span data-ttu-id="8623b-183">QQ</span><span class="sxs-lookup"><span data-stu-id="8623b-183">QQ</span></span>  <br/> | `ipm.externaldata.QQ*` <br/> |
|<span data-ttu-id="8623b-184">Microsoft SharePoint</span><span class="sxs-lookup"><span data-stu-id="8623b-184">Microsoft SharePoint</span></span>  <br/> | `ipm.externaldata.SharePoint*` <br/> |
|<span data-ttu-id="8623b-185">Salesforce Chatter</span><span class="sxs-lookup"><span data-stu-id="8623b-185">Salesforce Chatter</span></span>  <br/> | `ipm.externaldata.Chatter*` <br/> |
|<span data-ttu-id="8623b-186">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="8623b-186">Skype for Business</span></span>  <br/> | `ipm.externaldata.Skype*` <br/> |
|<span data-ttu-id="8623b-187">Slack Enterprise Grid</span><span class="sxs-lookup"><span data-stu-id="8623b-187">Slack Enterprise Grid</span></span>  <br/> | `ipm.externaldata.Slack.IM` <br/> |
|<span data-ttu-id="8623b-188">SoftEther</span><span class="sxs-lookup"><span data-stu-id="8623b-188">SoftEther</span></span>  <br/> | `ipm.externaldata.SoftEther*` <br/> |
|<span data-ttu-id="8623b-189">Squawker</span><span class="sxs-lookup"><span data-stu-id="8623b-189">Squawker</span></span>  <br/> | `ipm.externaldata.Squawker*` <br/> |
|<span data-ttu-id="8623b-190">Symphony</span><span class="sxs-lookup"><span data-stu-id="8623b-190">Symphony</span></span>  <br/> | `ipm.externaldata.Symphony*` <br/> |
|<span data-ttu-id="8623b-191">Thomson Reuters</span><span class="sxs-lookup"><span data-stu-id="8623b-191">Thomson Reuters</span></span>  <br/> | `ipm.externaldata.Reuters*` <br/> |
| <span data-ttu-id="8623b-192">Thomson Reuters Eikon Messenger</span><span class="sxs-lookup"><span data-stu-id="8623b-192">Thomson Reuters Eikon Messenger</span></span>  <br/> | `ipm.externaldata.ReutersEikon*` <br/> |
|<span data-ttu-id="8623b-193">Tor</span><span class="sxs-lookup"><span data-stu-id="8623b-193">Tor</span></span>  <br/> | `ipm.externaldata.Tor*` <br/> |
|<span data-ttu-id="8623b-194">TTT</span><span class="sxs-lookup"><span data-stu-id="8623b-194">TTT</span></span>  <br/> | `ipm.externaldata.TTT*` <br/> |
|<span data-ttu-id="8623b-195">Twitter</span><span class="sxs-lookup"><span data-stu-id="8623b-195">Twitter</span></span>  <br/> | `ipm.externaldata.Twitter*` <br/> |
|<span data-ttu-id="8623b-196">UBS チャット</span><span class="sxs-lookup"><span data-stu-id="8623b-196">UBS Chat</span></span>  <br/> | `ipm.externaldata.UBS*` <br/> |
|<span data-ttu-id="8623b-197">Vimeo</span><span class="sxs-lookup"><span data-stu-id="8623b-197">Vimeo</span></span>  <br/> | `ipm.externaldata.Vimeo*` <br/> |
|<span data-ttu-id="8623b-198">WinMX</span><span class="sxs-lookup"><span data-stu-id="8623b-198">WinMX</span></span>  <br/> | `ipm.externaldata.WinMX*` <br/> |
|<span data-ttu-id="8623b-199">Winny</span><span class="sxs-lookup"><span data-stu-id="8623b-199">Winny</span></span>  <br/> | `ipm.externaldata.Winny*` <br/> |
|<span data-ttu-id="8623b-200">Yahoo!</span><span class="sxs-lookup"><span data-stu-id="8623b-200">Yahoo!</span></span>  <br/> | `ipm.externaldata.Yahoo!*` <br/> |
|<span data-ttu-id="8623b-201">Yammer</span><span class="sxs-lookup"><span data-stu-id="8623b-201">Yammer</span></span>  <br/> | `ipm.externaldata.Yammer*` <br/> |
|<span data-ttu-id="8623b-202">YellowJacket</span><span class="sxs-lookup"><span data-stu-id="8623b-202">YellowJacket</span></span>  <br/> | `ipm.externaldata.YellowJacket*` <br/> |
|<span data-ttu-id="8623b-203">YouTube</span><span class="sxs-lookup"><span data-stu-id="8623b-203">YouTube</span></span>  <br/> | `ipm.externaldata.YouTube*` <br/> |
