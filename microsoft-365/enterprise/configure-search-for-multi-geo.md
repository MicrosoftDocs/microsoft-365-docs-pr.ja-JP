---
title: Office 365 Multi-Geo ために検索を構成する
ms.reviewer: adwood
ms.author: tlarsen
author: tklarsen
manager: arnek
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: seo-marvel-mar2020
ms.collection: Strat_SP_gtc
localization_priority: Normal
f1.keywords:
- NOCSH
description: 複数地域環境で検索を構成する方法について学習します。 OneDrive for Business などの一部のクライアントだけが、複数地域環境で結果を返す可能性があります。
ms.openlocfilehash: b3a96b1d0652cb954c58ae410583befa078460d9
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "50911164"
---
# <a name="configure-search-for-microsoft-365-multi-geo"></a><span data-ttu-id="7d81c-104">Office 365 Multi-Geo ために検索を構成する</span><span class="sxs-lookup"><span data-stu-id="7d81c-104">Configure Search for Microsoft 365 Multi-Geo</span></span>

<span data-ttu-id="7d81c-105">Multi-Geo 環境では、それぞれの地域の場所にはその場所固有の検索インデックスと検索センターがあります。</span><span class="sxs-lookup"><span data-stu-id="7d81c-105">In a multi-geo environment, each geo location has its own search index and Search Center.</span></span> <span data-ttu-id="7d81c-106">ユーザーが検索すると、クエリはすべてのインデックスに対して展開され、返された結果は結合されます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-106">When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="7d81c-107">たとえば、ある地域の場所にいるユーザーが、別の地域の場所に格納されているコンテンツを検索したり、別の地域の場所に限定された SharePoint サイトのコンテンツを検索したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-107">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that's restricted to a different geo location.</span></span> <span data-ttu-id="7d81c-108">ユーザーにそのコンテンツへのアクセス権がある場合は、検索結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-108">If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="7d81c-109">Multi-Geo 環境で動作する検索クライアントについて</span><span class="sxs-lookup"><span data-stu-id="7d81c-109">Which search clients work in a multi-geo environment?</span></span>

<span data-ttu-id="7d81c-110">次のクライアントは、すべての地域の場所からの結果を返します。</span><span class="sxs-lookup"><span data-stu-id="7d81c-110">These clients can return results from all geo locations:</span></span>

- <span data-ttu-id="7d81c-111">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="7d81c-111">OneDrive for Business</span></span>
- <span data-ttu-id="7d81c-112">Delve</span><span class="sxs-lookup"><span data-stu-id="7d81c-112">Delve</span></span>
- <span data-ttu-id="7d81c-113">SharePoint ホーム ページ</span><span class="sxs-lookup"><span data-stu-id="7d81c-113">The SharePoint home page</span></span>
- <span data-ttu-id="7d81c-114">検索センター</span><span class="sxs-lookup"><span data-stu-id="7d81c-114">The Search Center</span></span>
- <span data-ttu-id="7d81c-115">SharePoint 検索 API を使用するカスタムの検索アプリケーション</span><span class="sxs-lookup"><span data-stu-id="7d81c-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="7d81c-116">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="7d81c-116">OneDrive for Business</span></span>

<span data-ttu-id="7d81c-117">Multi-Geo 環境の設定が完了した直後に、OneDrive で検索を実行するユーザーには、すべての地域の場所からの結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-117">As soon as the multi-geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="7d81c-118">Delve</span><span class="sxs-lookup"><span data-stu-id="7d81c-118">Delve</span></span>

<span data-ttu-id="7d81c-119">Multi-Geo 環境の設定が完了した直後に、Delve で検索するユーザーには、すべての地域の場所からの結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-119">As soon as the multi-geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="7d81c-120">Delve フィードとプロファイル カードでは、中央の場所に保存されているファイルのプレビューのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-120">The Delve feed and the profile card only show previews of files that are stored in the central location.</span></span> <span data-ttu-id="7d81c-121">サテライトの場所に保存されているファイルの場合は、ファイルの種類のアイコンのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-121">For files that are stored in satellite locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="7d81c-122">SharePoint ホーム ページ</span><span class="sxs-lookup"><span data-stu-id="7d81c-122">The SharePoint home page</span></span>

<span data-ttu-id="7d81c-p105">Multi-Geo 環境の設定が完了した直後に、ユーザーには、複数地域の場所からのニュース、最近のサイトおよびフォローしているサイトが示された SharePoint ホーム ページが表示されます。ユーザーが SharePoint ホーム ページの検索ボックスを使用すると、複数地域の場所からの結果がマージされて返されます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-p105">As soon as the multi-geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="7d81c-125">検索センター</span><span class="sxs-lookup"><span data-stu-id="7d81c-125">The Search Center</span></span>

<span data-ttu-id="7d81c-p106">Multi-Geo 環境の設定完了後、それぞれの検索センターには、それらの地域の場所からの結果のみが引き続き表示されます。管理者は、[それぞれの検索センターの設定を変更](#_Set_up_a_1)して、すべての地域の場所からの結果が得られるようにする必要があります。その後、検索センターで検索したユーザーには、すべての地域の場所からの結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-p106">After the multi-geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="7d81c-129">カスタムの検索アプリケーション</span><span class="sxs-lookup"><span data-stu-id="7d81c-129">Custom search applications</span></span>

<span data-ttu-id="7d81c-p107">通常のように、カスタムの検索アプリケーションは、検索インデックスとの対話型操作に既存の SharePoint 検索 REST API を使用します。すべてまたは一部の地域の場所からの結果を取得するために、アプリケーションでは、要求で [API を呼び出して新しい複数地域クエリ パラメーターを含める](#_Get_custom_search)必要があります。これにより、すべての地域の場所へのクエリのファンアウトがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-p107">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="7d81c-133">Multi-Geo 環境での検索の相違点について</span><span class="sxs-lookup"><span data-stu-id="7d81c-133">What's different about search in a multi-geo environment?</span></span>

<span data-ttu-id="7d81c-134">Multi-Geo 環境では、従来の検索機能の一部の動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="7d81c-134">Some search features you might be familiar with, work differently in a multi-geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="7d81c-135"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="7d81c-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="7d81c-136"><strong>動作のしくみ</strong></span><span class="sxs-lookup"><span data-stu-id="7d81c-136"><strong>How it works</strong></span></span></th>
<th align="left"><span data-ttu-id="7d81c-137"><strong>回避策</strong></span><span class="sxs-lookup"><span data-stu-id="7d81c-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="7d81c-138">昇格結果</span><span class="sxs-lookup"><span data-stu-id="7d81c-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="7d81c-139">昇格結果を使用するクエリ ルールは、異なるレベル (テナント全体、サイト コレクション、またはサイト) ので作成できます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-139">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site.</span></span> <span data-ttu-id="7d81c-140">Multi-Geo 環境では、すべての地域の場所の検索センターに結果を昇格する場合、テナント レベルで昇格結果を定義します。</span><span class="sxs-lookup"><span data-stu-id="7d81c-140">In a multi-geo environment, define promoted results at the tenant level to promote the results to the Search Centers in all geo locations.</span></span> <span data-ttu-id="7d81c-141">サイト コレクションまたはサイトの地域の場所にある検索センターでのみ結果を昇格する場合は、サイト コレクションまたはサイト レベルで結果を定義します。</span><span class="sxs-lookup"><span data-stu-id="7d81c-141">If you only want to promote results in the Search Center that's in the geo location of the site collection or site, define the promoted results at the site collection or site level.</span></span> <span data-ttu-id="7d81c-142">これらの検索結果は、他の地域の場所では昇格されません。</span><span class="sxs-lookup"><span data-stu-id="7d81c-142">These results are not promoted in other geo locations.</span></span></td>
<td align="left"><span data-ttu-id="7d81c-143">地域の場所ごとに異なる昇格結果を必要としない場合は (出張の場合の異なるルールなど)、テナント レベルで昇格結果を定義することをお薦めします。</span><span class="sxs-lookup"><span data-stu-id="7d81c-143">If you don't need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="7d81c-144">絞り込み検索</span><span class="sxs-lookup"><span data-stu-id="7d81c-144">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="7d81c-p109">検索は、テナントのすべての地域の場所からの絞り込み条件を返して、それらを集約します。この集約は、最善努力型であるため、絞り込み条件のカウントが 100% の精度にならないことがあります。ほとんどの検索型シナリオの場合は、この精度で十分です。 </span><span class="sxs-lookup"><span data-stu-id="7d81c-p109">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient. </span></span></td>
<td align="left"><span data-ttu-id="7d81c-148">絞り込み条件の完全性に依存する検索型アプリケーションの場合は、それぞれの地域の場所を個別にクエリします。</span><span class="sxs-lookup"><span data-stu-id="7d81c-148">For search-driven applications that depend on refiner completeness, query each geo location independently.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="7d81c-149">Multi-Geo 検索では、数値の絞り込み条件の動的バケットはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="7d81c-149">Multi-geo search doesn't support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="7d81c-150">数値絞 <a href="/sharepoint/dev/general-development/query-refinement-in-sharepoint">り込み条件には"Discretize"</a> パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="7d81c-150">Use the <a href="/sharepoint/dev/general-development/query-refinement-in-sharepoint">"Discretize" parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="7d81c-151">ドキュメント ID</span><span class="sxs-lookup"><span data-stu-id="7d81c-151">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="7d81c-152">ドキュメント ID に依存する検索型アプリケーションを開発する場合、Multi-Geo 環境のドキュメント ID は地域の場所ごとに一意ですが、複数の地域の場所にわたって一意でない点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="7d81c-152">If you're developing a search-driven application that depends on document IDs, note that document IDs in a multi-geo environment aren't unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="7d81c-153">地域の場所を示す列が追加されました。</span><span class="sxs-lookup"><span data-stu-id="7d81c-153">We've added a column that identifies the geo location.</span></span> <span data-ttu-id="7d81c-154">この列を使用して、一意性を確保してください。</span><span class="sxs-lookup"><span data-stu-id="7d81c-154">Use this column to achieve uniqueness.</span></span> <span data-ttu-id="7d81c-155">この列の名前は "GeoLocationSource" です。</span><span class="sxs-lookup"><span data-stu-id="7d81c-155">This column is named "GeoLocationSource".</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="7d81c-156">結果の数</span><span class="sxs-lookup"><span data-stu-id="7d81c-156">Number of results</span></span></td>
<td align="left"><span data-ttu-id="7d81c-157">検索結果ページには、複数の地域の場所からの結果がまとめて表示されますが、500 件を超える結果をページにまとめることはできません。</span><span class="sxs-lookup"><span data-stu-id="7d81c-157">The search results page shows combined results from the geo locations, but it's not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="7d81c-158">ハイブリッド検索</span><span class="sxs-lookup"><span data-stu-id="7d81c-158">Hybrid search</span></span></td>
<td align="left"><span data-ttu-id="7d81c-159"><a href="/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint">クラウド ハイブリッド検索</a>を使用するハイブリッド SharePoint 環境では、オンプレミス コンテンツが中央の場所の Office 365 インデックスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-159">In a hybrid SharePoint environment with <a href="/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint">cloud hybrid search</a>,  on-premises content is added to the Microsoft 365 index of the central location.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="7d81c-160">Multi-Geo 環境の検索でサポートされない内容</span><span class="sxs-lookup"><span data-stu-id="7d81c-160">What's not supported for search in a multi-geo environment?</span></span>

<span data-ttu-id="7d81c-161">Multi-Geo 環境では、従来の検索機能一部のがサポートされません。</span><span class="sxs-lookup"><span data-stu-id="7d81c-161">Some of the search features you might be familiar with, aren't supported in a multi-geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="7d81c-162"><strong>検索機能</strong></span><span class="sxs-lookup"><span data-stu-id="7d81c-162"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="7d81c-163"><strong>注</strong></span><span class="sxs-lookup"><span data-stu-id="7d81c-163"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="7d81c-164">アプリ専用の認証</span><span class="sxs-lookup"><span data-stu-id="7d81c-164">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="7d81c-165">Multi-Geo 検索では、アプリ専用の認証 (サービスからの特権アクセス) がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="7d81c-165">App-only authentication (privileged access from services) isn't supported in multi-geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="7d81c-166">ゲスト ユーザー</span><span class="sxs-lookup"><span data-stu-id="7d81c-166">Guest users</span></span></td>
<td align="left"><span data-ttu-id="7d81c-167">ゲスト ユーザーは、検索を行う際にいる地域の場所からの結果のみを取得できます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-167">Guest users only get results from the geo location that they're searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="7d81c-168">Multi-Geo 環境での検索の動作について</span><span class="sxs-lookup"><span data-stu-id="7d81c-168">How does search work in a multi-geo environment?</span></span>

<span data-ttu-id="7d81c-169">すべての検索クライアントは、既存の SharePoint 検索 REST API を使用して検索インデックスとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="7d81c-169">All the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>

![SharePoint Search REST API が検索インデックスとやり取りする方法を示す図](../media/configure-search-for-multi-geo-image1-1.png)

1. <span data-ttu-id="7d81c-171">検索クライアントは、クエリ プロパティ EnableMultiGeoSearch = true を設定して、検索 REST エンドポイントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7d81c-171">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="7d81c-172">クエリは、テナント内のすべての地域の場所に送信されます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-172">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="7d81c-173">それぞれの地域の場所からの検索結果はマージされ、ランク付けされます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-173">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="7d81c-174">クライアントは、統一された検索結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="7d81c-174">The client gets unified search results.</span></span>

<span data-ttu-id="7d81c-175"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>すべての地域の場所から結果を受け取るまでは、検索結果が結合されない点にご注意ください。</span><span class="sxs-lookup"><span data-stu-id="7d81c-175"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don't merge the search results until we've received results from all the geo locations.</span></span> <span data-ttu-id="7d81c-176">したがって、地域の場所が 1 つのみの環境での検索に比べ、複数地域検索では遅延が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="7d81c-176">This means that multi-geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="7d81c-177">検索センターにすべての地域の場所からの結果を表示する</span><span class="sxs-lookup"><span data-stu-id="7d81c-177">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="7d81c-178">それぞれの検索センターには、複数のバーティカルがあり、それぞれのバーティカルを個別に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d81c-178">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1. <span data-ttu-id="7d81c-179">ここに示す手順は、検索結果ページと検索結果 Web パーツを編集するためのアクセス許可があるアカウントで実行してください。</span><span class="sxs-lookup"><span data-stu-id="7d81c-179">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2. <span data-ttu-id="7d81c-180">検索結果ページに移動します (検索結果ページの[一覧](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213)を参照してください)</span><span class="sxs-lookup"><span data-stu-id="7d81c-180">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3. <span data-ttu-id="7d81c-p112">設定するバーティカルを選択し、右上の **[設定]** ギア アイコンをクリックして、**[ページの編集]** をクリックします。編集モードで、検索結果ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-p112">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

   ![[設定] でページ選択を編集する](../media/configure-search-for-multi-geo-image2.png)

4. <span data-ttu-id="7d81c-184">検索結果 Web パーツで、マウス ポインターを Web パーツの右上に移動させ、矢印をクリックし、メニューから [**Web パーツの編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d81c-184">In the Search Results Web Part, move the pointer to the upper, right corner of the web part, click the arrow, and then click **Edit Web Part** on the menu.</span></span> <span data-ttu-id="7d81c-185">ページの右上のリボンの下に検索結果 Web パーツのツール ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-185">The Search Results Web Part tool pane opens under the ribbon in the top right of the page.</span></span>

   ![Web パーツの選択を編集する](../media/configure-search-for-multi-geo-image3.png)

5. <span data-ttu-id="7d81c-187">Web パーツ ツール ウィンドウの **[設定]** セクションで、**[結果コントロールの設定]** から **[複数地域の検索結果を表示する]** を選択して、検索結果 Web パーツに、すべての地域の場所からの結果が表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="7d81c-187">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

6. <span data-ttu-id="7d81c-188">**[OK]** をクリックして変更内容を保存して、Web パーツ ツール ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-188">Click **OK** to save your change and close the Web Part tool pane.</span></span>

7. <span data-ttu-id="7d81c-189">検索結果 Web パーツに対する変更内容を確認するには、メイン メニューの [ページ] タブで **[チェックイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d81c-189">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

8. <span data-ttu-id="7d81c-190">ページの上部にあるメモで示されるリンクを使用して、変更内容を公開します。</span><span class="sxs-lookup"><span data-stu-id="7d81c-190">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="7d81c-191">カスタムの検索アプリケーションにすべてまたは一部の地域の場所からの結果を表示する</span><span class="sxs-lookup"><span data-stu-id="7d81c-191">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="7d81c-192">カスタム検索アプリケーションは、SharePoint Search REST API への要求でクエリ パラメーターを指定することで、すべての場所または一部の地域の場所から結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="7d81c-192">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API.</span></span> <span data-ttu-id="7d81c-193">クエリ パラメーターに応じて、クエリは、すべての地域の場所、または一部の地域の場所に対してファンアウトされます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-193">Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations.</span></span> <span data-ttu-id="7d81c-194">たとえば、関連する情報を見つけるために地域の場所のサブセットのみを照会する必要がある場合は、ファンをこれらの場所にのみ制御できます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-194">For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these.</span></span> <span data-ttu-id="7d81c-195">要求が成功すると、SharePoint Search REST API は応答データを返します。</span><span class="sxs-lookup"><span data-stu-id="7d81c-195">If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="requirement"></a><span data-ttu-id="7d81c-196">要件</span><span class="sxs-lookup"><span data-stu-id="7d81c-196">Requirement</span></span>

<span data-ttu-id="7d81c-p115">地域的位置ごとに、組織内のすべてのユーザーにルート Web サイトの **読み取り** アクセス許可レベルが付与されていることを確認する必要があります (たとえば、contoso **APAC**.sharepoint.com/ および contoso **EU**.sharepoint.com/)。[アクセス許可について](https://support.office.com/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848)。</span><span class="sxs-lookup"><span data-stu-id="7d81c-p115">For each geo location, you must ensure that all users in the organization have been granted the **Read** permission level for the root website (for example contoso **APAC**.sharepoint.com/ and contoso **EU**.sharepoint.com/). [Learn about permissions](https://support.office.com/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848).</span></span>

### <a name="query-parameters"></a><span data-ttu-id="7d81c-199">クエリ パラメーター</span><span class="sxs-lookup"><span data-stu-id="7d81c-199">Query parameters</span></span>

<span data-ttu-id="7d81c-200">EnableMultiGeoSearch - Multi-Geo テナントの他の地域の場所のインデックスへクエリをファンアウトすべきかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="7d81c-200">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the multi-geo tenant.</span></span> <span data-ttu-id="7d81c-201">クエリをファンアウトする場合は **true** と設定し、クエリをファンアウトしない場合は **false** と設定します。</span><span class="sxs-lookup"><span data-stu-id="7d81c-201">Set it to **true** to fan out the query; **false** to not fan out the query.</span></span> <span data-ttu-id="7d81c-202">このパラメータを含めない場合、既定値は **false** です。ただし、エンタープライズ検索センター テンプレートを使用するサイトに対して REST API 呼び出しを行う場合は、この既定値は **true** になります。</span><span class="sxs-lookup"><span data-stu-id="7d81c-202">If you don't include this parameter, the default value is **false**, except when making a REST API call against a site which uses the Enterprise Search Center template, in this case the default value is **true**.</span></span> <span data-ttu-id="7d81c-203">Multi-Geo ではない環境でこのパラメーターを使用する場合、パラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-203">If you use the parameter in an environment that isn't multi-geo, the parameter is ignored.</span></span>

<span data-ttu-id="7d81c-204">ClientType - これは文字列です。</span><span class="sxs-lookup"><span data-stu-id="7d81c-204">ClientType - This is a string.</span></span> <span data-ttu-id="7d81c-205">検索アプリケーションごとに一意のクライアント名を入力します。</span><span class="sxs-lookup"><span data-stu-id="7d81c-205">Enter a unique client name for each search application.</span></span> <span data-ttu-id="7d81c-206">このパラメーターを指定しない場合は、クエリは他の地域の場所へファンアウトされません。</span><span class="sxs-lookup"><span data-stu-id="7d81c-206">If you don't include this parameter, the query is not fanned out to other geo locations.</span></span>

<span data-ttu-id="7d81c-207">MultiGeoSearchConfiguration - **EnableMultiGeoSearch** が **true** に設定されている場合に、Multi-Geo テナントの他の地域の場所へファンアウトに使用するリスト (省略可能) です。</span><span class="sxs-lookup"><span data-stu-id="7d81c-207">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the multi-geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**.</span></span> <span data-ttu-id="7d81c-208">このパラメーターを指定しない場合、または空白のままにする場合は、クエリはすべての地域の場所へファンアウトされます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-208">If you don't include this parameter, or leave it blank, the query is fanned out to all geo locations.</span></span> <span data-ttu-id="7d81c-209">それぞれの地域の場所について、次の項目を JSON 形式で入力します。</span><span class="sxs-lookup"><span data-stu-id="7d81c-209">For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="7d81c-210">項目</span><span class="sxs-lookup"><span data-stu-id="7d81c-210">Item</span></span></th>
<th align="left"><span data-ttu-id="7d81c-211">説明</span><span class="sxs-lookup"><span data-stu-id="7d81c-211">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="7d81c-212">DataLocation</span><span class="sxs-lookup"><span data-stu-id="7d81c-212">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="7d81c-213">地域の場所 (例: NAM)。</span><span class="sxs-lookup"><span data-stu-id="7d81c-213">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="7d81c-214">EndPoint</span><span class="sxs-lookup"><span data-stu-id="7d81c-214">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="7d81c-215">接続先のエンドポイント (例: https://contoso.sharepoint.com)。</span><span class="sxs-lookup"><span data-stu-id="7d81c-215">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="7d81c-216">SourceId</span><span class="sxs-lookup"><span data-stu-id="7d81c-216">SourceId</span></span></td>
<td align="left"><span data-ttu-id="7d81c-217">検索先の GUID (例: B81EAB55-3140-4312-B0F4-9459D1B4FFEE)。</span><span class="sxs-lookup"><span data-stu-id="7d81c-217">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="7d81c-p119">DataLocation または EndPoint を省略した場合や DataLocation が重複している場合、要求は失敗します。[テナントの地域の場所のエンドポイントに関する情報は、Microsoft Graph を使用することで取得できます](/sharepoint/dev/solution-guidance/multigeo-discovery)。</span><span class="sxs-lookup"><span data-stu-id="7d81c-p119">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="7d81c-220">応答データ</span><span class="sxs-lookup"><span data-stu-id="7d81c-220">Response data</span></span>

<span data-ttu-id="7d81c-p120">MultiGeoSearchStatus: 要求に対する応答で SharePoint 検索 API が返すプロパティです。このプロパティの値は文字列であり、SharePoint 検索 API が返す結果について次の情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="7d81c-p120">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="7d81c-223">値</span><span class="sxs-lookup"><span data-stu-id="7d81c-223">Value</span></span></th>
<th align="left"><span data-ttu-id="7d81c-224">説明</span><span class="sxs-lookup"><span data-stu-id="7d81c-224">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="7d81c-225">Full</span><span class="sxs-lookup"><span data-stu-id="7d81c-225">Full</span></span></td>
<td align="left"><span data-ttu-id="7d81c-226"><strong>すべて</strong>の地域の場所からの完全な結果。</span><span class="sxs-lookup"><span data-stu-id="7d81c-226">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="7d81c-227">Partial</span><span class="sxs-lookup"><span data-stu-id="7d81c-227">Partial</span></span></td>
<td align="left"><span data-ttu-id="7d81c-p121">1 つ以上の地域の場所からの部分的な結果。この結果は一時的なエラーによって不完全なものになります。</span><span class="sxs-lookup"><span data-stu-id="7d81c-p121">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>
</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="7d81c-230">REST サービスを使用したクエリ</span><span class="sxs-lookup"><span data-stu-id="7d81c-230">Query using the REST service</span></span>

<span data-ttu-id="7d81c-p122">GET 要求の場合は、URL でクエリ パラメーターを指定します。POST 要求の場合は、JavaScript Object Notation (JSON) 形式のクエリ パラメーターを本文で渡します。</span><span class="sxs-lookup"><span data-stu-id="7d81c-p122">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>

#### <a name="request-headers"></a><span data-ttu-id="7d81c-233">要求ヘッダー</span><span class="sxs-lookup"><span data-stu-id="7d81c-233">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="7d81c-234">名前</span><span class="sxs-lookup"><span data-stu-id="7d81c-234">Name</span></span></th>
<th align="left"><span data-ttu-id="7d81c-235">値</span><span class="sxs-lookup"><span data-stu-id="7d81c-235">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="7d81c-236">Content-Type</span><span class="sxs-lookup"><span data-stu-id="7d81c-236">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="7d81c-237">application/json;odata=verbose</span><span class="sxs-lookup"><span data-stu-id="7d81c-237">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="7d81c-238">**すべて** の地域の場所にファンアウトされる GET 要求の例</span><span class="sxs-lookup"><span data-stu-id="7d81c-238">Sample GET request that's fanned out to **all** geo locations</span></span>

<span data-ttu-id="7d81c-239"> https:// \<tenant\> / \_ api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my client \_ \_ id'</span><span class="sxs-lookup"><span data-stu-id="7d81c-239">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="7d81c-240">**一部** の地域の場所にファンアウトする GET 要求の例</span><span class="sxs-lookup"><span data-stu-id="7d81c-240">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="7d81c-241"> https:// \<tenant\> / \_ api/search/query?querytext='site'&ClientType=''my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation \\ :"NAM" \\ ,Endpoint \\ :"https \\ ://contosoNAM.sharepoint.com" \\ ,SourceId \\ :"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"} \\ \\ ,{DataLocation :"CAN" ,Endpoint :"https \\ \\ \\ ://contosoCAN.sharepoint-df.com"}'</span><span class="sxs-lookup"><span data-stu-id="7d81c-241">https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span></span>

> [!NOTE]
> <span data-ttu-id="7d81c-242">MultiGeoSearchConfiguration プロパティの地域の場所の一覧内のコンマとコロンの前に **バックスラッシュ** 記号が先行します。</span><span class="sxs-lookup"><span data-stu-id="7d81c-242">Commas and colons in the list of geo locations for the MultiGeoSearchConfiguration property are preceded by the **backslash** character.</span></span> <span data-ttu-id="7d81c-243">これは、GET 要求では複数のプロパティの区切りにはコロンが、複数のプロパティの引数の区切りにはコンマが使用されるためです。</span><span class="sxs-lookup"><span data-stu-id="7d81c-243">This is because GET requests use colons to separate properties and commas to separate arguments of properties.</span></span> <span data-ttu-id="7d81c-244">エスケープ文字としてバックスラッシュ記号を使わない場合、MultiGeoSearchConfiguration プロパティは正確に解釈されません。</span><span class="sxs-lookup"><span data-stu-id="7d81c-244">Without the backslash as an escape character, the MultiGeoSearchConfiguration property is interpreted wrongly.</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="7d81c-245">**すべて** の地域の場所にファンアウトされる POST 要求の例</span><span class="sxs-lookup"><span data-stu-id="7d81c-245">Sample POST request that's fanned out to **all** geo locations</span></span>

```text
    {
    "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }
```

#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="7d81c-246">**一部** の地域の場所にファンアウトされる POST 要求の例</span><span class="sxs-lookup"><span data-stu-id="7d81c-246">Sample POST request that's fanned out to **some** geo locations</span></span>

```text
    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }
```

### <a name="query-using-csom"></a><span data-ttu-id="7d81c-247">CSOM を使用したクエリ</span><span class="sxs-lookup"><span data-stu-id="7d81c-247">Query using CSOM</span></span>

<span data-ttu-id="7d81c-248">次に、**すべて** の地域の場所にファアウトされる CSOM クエリの例を示します。</span><span class="sxs-lookup"><span data-stu-id="7d81c-248">Here's a sample CSOM query that's fanned out to **all** geo locations:</span></span>

```text
var keywordQuery = new KeywordQuery(ctx);
keywordQuery.QueryText = query.SearchQueryText;
keywordQuery.ClientType = <enter a string here>;
keywordQuery["EnableMultiGeoSearch"] = true;
```