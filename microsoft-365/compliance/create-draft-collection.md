---
title: 下書きコレクションを作成する
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: 下書きコレクションは、コレクションの検索クエリに一致する検索見積もりを返す高度な電子情報開示ケース内の保管データ ソースと非保管データ ソースの電子情報開示検索です。 検索結果をレビュー セットにコミットする前に、検索統計を確認し、アイテムのサンプリングをプレビューし、コレクションを修正して再実行できます。
ms.openlocfilehash: 18f018a5e00f355c3f320a963135e76ecc51f086
ms.sourcegitcommit: 8f1721de52dbe3a12c11a0fa5ed0ef5972ca8196
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2021
ms.locfileid: "50838897"
---
# <a name="create-a-draft-collection-in-advanced-ediscovery"></a><span data-ttu-id="64990-104">Advanced eDiscovery で下書きコレクションを作成する</span><span class="sxs-lookup"><span data-stu-id="64990-104">Create a draft collection in Advanced eDiscovery</span></span>

<span data-ttu-id="64990-105">ケースの保管担当者と保管担当者以外のデータ ソースを特定した後、関連する一連のドキュメントを特定して見つける準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="64990-105">After you've identified custodians and any non-custodian data sources for the case, you're ready to identify and locate a set of documents that are relevant.</span></span> <span data-ttu-id="64990-106">これを行うには、コレクション ツールを使用して、関連するコンテンツのデータ ソースを検索します。</span><span class="sxs-lookup"><span data-stu-id="64990-106">You do this by using the Collections tool to search data sources for relevant content.</span></span> <span data-ttu-id="64990-107">これを行うには、検索条件に一致するコンテンツの指定されたデータ ソースを検索するコレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="64990-107">You do this by creating a collection that searches specified data sources for content that matches your search criteria.</span></span> <span data-ttu-id="64990-108">アイテムの見積もりである下書きコレクションを作成するオプションや、アイテムをレビュー セットに自動的に追加するコレクションを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="64990-108">You have the option to create a *draft collection*, which is an estimate of the items are found or you can create a collection that automatically adds the items to a review set.</span></span> <span data-ttu-id="64990-109">下書きコレクションを作成すると、検索クエリに一致した推定結果に関する情報 (見つかったアイテムの総数とサイズ、見つかったさまざまなデータ ソース、検索クエリに関する統計情報など) を表示できます。</span><span class="sxs-lookup"><span data-stu-id="64990-109">When you create a draft collection, you can views information about the estimated results that matched the search query, such as the total number and size of items found, the different data sources where they were found, and statistics about the search query.</span></span> <span data-ttu-id="64990-110">コレクションによって返されたアイテムのサンプルをプレビューできます。</span><span class="sxs-lookup"><span data-stu-id="64990-110">You can also preview a sample of items that were returned by the collection.</span></span> <span data-ttu-id="64990-111">これらの統計を使用して、検索クエリを変更し、下書きコレクションを再実行して結果を絞り込むできます。</span><span class="sxs-lookup"><span data-stu-id="64990-111">Using these statistics, you can change the search query and rerun the draft collection to narrow your results.</span></span> <span data-ttu-id="64990-112">コレクションの結果に満足したら、コレクションをレビュー セットにコミットできます。</span><span class="sxs-lookup"><span data-stu-id="64990-112">Once you're satisfied with the collection results, you can commit the collection to a review set.</span></span> <span data-ttu-id="64990-113">下書きコレクションをコミットすると、コレクションによって返されるアイテムがレビュー、分析、およびエクスポート用のレビュー セットに追加されます。</span><span class="sxs-lookup"><span data-stu-id="64990-113">When you commit a draft collection, the items returned by the collection are added to a review set for review, analysis, and export.</span></span>

## <a name="before-you-create-a-draft-collection"></a><span data-ttu-id="64990-114">下書きコレクションを作成する前に</span><span class="sxs-lookup"><span data-stu-id="64990-114">Before you create a draft collection</span></span>

- <span data-ttu-id="64990-115">下書きコレクションを作成する前に、保管担当者と非保管データ ソースをケースに追加します。</span><span class="sxs-lookup"><span data-stu-id="64990-115">Add custodians and non-custodial data sources to the case before you create a draft collection.</span></span> <span data-ttu-id="64990-116">これは、下書きコレクションの作成時にデータ ソースを選択するために必要です。</span><span class="sxs-lookup"><span data-stu-id="64990-116">This is required so that you can select the data sources when you create a draft collection.</span></span> <span data-ttu-id="64990-117">詳しくは、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64990-117">For more information, see:</span></span>

  - [<span data-ttu-id="64990-118">ケースにカストディアンを追加する</span><span class="sxs-lookup"><span data-stu-id="64990-118">Add custodians to a case</span></span>](add-custodians-to-case.md)

  - [<span data-ttu-id="64990-119">非カストディアンのデータ ソースをケースに追加する</span><span class="sxs-lookup"><span data-stu-id="64990-119">Add non-custodial data sources to a case</span></span>](non-custodial-data-sources.md)

- <span data-ttu-id="64990-120">ケースに関連する可能性のあるコンテンツの下書きコレクションで、追加のデータ ソース (ケースに保管場所または非保管場所として追加されていないデータ ソース) を検索できます。</span><span class="sxs-lookup"><span data-stu-id="64990-120">You can search additional data sources (ones that haven't been added to the case as custodial or non-custodial locations) in a draft collection for content that may be relevant to the case.</span></span> <span data-ttu-id="64990-121">これらのデータ ソースには、メールボックス、SharePoint サイト、Teams が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="64990-121">These data sources might include mailboxes, SharePoint sites, and Teams.</span></span> <span data-ttu-id="64990-122">この状況がケースに該当する場合は、これらのデータ ソースの一覧をコンパイルして、コレクションに追加できます。</span><span class="sxs-lookup"><span data-stu-id="64990-122">If this situation is applicable to your case, compile a list of these data sources so you can add them to the collection.</span></span>

## <a name="create-a-draft-collection"></a><span data-ttu-id="64990-123">下書きコレクションを作成する</span><span class="sxs-lookup"><span data-stu-id="64990-123">Create a draft collection</span></span>

1. <span data-ttu-id="64990-124">Microsoft 365 コンプライアンス センターで、高度な電子情報開示ケースを開き、[コレクション] **タブを選択** します。</span><span class="sxs-lookup"><span data-stu-id="64990-124">In the Microsoft 365 compliance center, open the Advanced eDiscovery case, and then select the **Collections** tab.</span></span>

2. <span data-ttu-id="64990-125">[コレクション **] ページで、[** 新しいコレクション **の標準コレクション**  >  **] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="64990-125">On the **Collections** page, select **New collection** > **Standard collection**.</span></span>

3. <span data-ttu-id="64990-126">コレクションの名前 (必須) と説明 (省略可能) を入力します。</span><span class="sxs-lookup"><span data-stu-id="64990-126">Type a name (required) and description (optional) for the collection.</span></span> <span data-ttu-id="64990-127">コレクションを作成した後、名前を変更することはできませんが、説明を変更できます。</span><span class="sxs-lookup"><span data-stu-id="64990-127">After the collection is created, you can't change the name, but you can modify the description.</span></span>

4. <span data-ttu-id="64990-128">[保管 **データ ソース]** ページで、次のいずれかの操作を実行して、コンテンツを収集する保管データ ソースを識別します。</span><span class="sxs-lookup"><span data-stu-id="64990-128">On the **Custodial data sources** page, do one of the following things to identify the custodial data sources to collect content from:</span></span>

   - <span data-ttu-id="64990-129">[ **保管担当者の選択] を** クリックして、ケースに追加された特定の保管担当者を検索します。</span><span class="sxs-lookup"><span data-stu-id="64990-129">Click **Select custodians** to search specific custodians that were added to the case.</span></span> <span data-ttu-id="64990-130">このオプションを使用すると、ケース保管担当者の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="64990-130">If you use this option, a list of the case custodians is displayed.</span></span> <span data-ttu-id="64990-131">1 つ以上の保管担当者を選択します。</span><span class="sxs-lookup"><span data-stu-id="64990-131">Select one or more custodians.</span></span> <span data-ttu-id="64990-132">保管担当者を選択して追加した後、各保管担当者を検索する特定のデータ ソースを選択できます。</span><span class="sxs-lookup"><span data-stu-id="64990-132">After you select and add the custodians, you can also select the specific data sources to search for each custodian.</span></span> <span data-ttu-id="64990-133">表示されるこれらのデータ ソースは、保管担当者がケースに追加されたときに指定されました。</span><span class="sxs-lookup"><span data-stu-id="64990-133">These data sources that are displayed were specified when the custodian was added to the case.</span></span>

   - <span data-ttu-id="64990-134">[すべて選択 **] トグル** をクリックして、ケースに追加されたすべての保管担当者を検索します。</span><span class="sxs-lookup"><span data-stu-id="64990-134">Click the **Select all** toggle to search all custodians that were added to the case.</span></span> <span data-ttu-id="64990-135">このオプションを選択すると、すべての保管担当者のすべてのデータ ソースが検索されます。</span><span class="sxs-lookup"><span data-stu-id="64990-135">When you select this option, all data sources for all custodians are searched.</span></span>

5. <span data-ttu-id="64990-136">[非保管 **データ** ソース] ページで、次のいずれかの操作を実行して、コンテンツを収集する非保管データ ソースを識別します。</span><span class="sxs-lookup"><span data-stu-id="64990-136">On the **Non-custodial data sources** page, do one of the following things to identify the non-custodial data sources to collect content from:</span></span>

   - <span data-ttu-id="64990-137">[ **保管されていないデータ ソースの選択** ] をクリックして、ケースに追加された特定の非保管データ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="64990-137">Click **Select non-custodial data sources** to select specific non-custodial data sources that were added to the case.</span></span> <span data-ttu-id="64990-138">このオプションを使用すると、データ ソースの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="64990-138">If you use this option, a list of data sources displayed.</span></span> <span data-ttu-id="64990-139">これらのデータ ソースの 1 つ以上を選択します。</span><span class="sxs-lookup"><span data-stu-id="64990-139">Select one or more of these data sources.</span></span>

   - <span data-ttu-id="64990-140">[すべて選択 **] トグル** をクリックして、ケースに追加された非保管データ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="64990-140">Click the **Select all** toggle to select all non-custodial data sources that were added to the case.</span></span>

6. <span data-ttu-id="64990-141">[その **他のデータ ソース] ページ** で、コレクションの一部として検索する他のメールボックスとサイトを選択できます。</span><span class="sxs-lookup"><span data-stu-id="64990-141">On the **Additional data sources** page, you can select other mailboxes and sites to search as part of the collection.</span></span> <span data-ttu-id="64990-142">このような種類のデータ ソースは、ケース内で保管または非保管データの場所として追加されません。</span><span class="sxs-lookup"><span data-stu-id="64990-142">These types of data sources weren't added as custodial or non-custodial data locations in the case.</span></span> <span data-ttu-id="64990-143">追加のデータ ソースを検索する場合は、次の 2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="64990-143">You also have two options when searching additional data sources:</span></span>

   - <span data-ttu-id="64990-144">特定のサービス (Exchange メールボックス、SharePoint および OneDrive サイト、または Exchange パブリック フォルダー) のすべてのコンテンツの場所を検索するには、[状態] 列の対応する [すべて選択] トグルを **クリック** します。</span><span class="sxs-lookup"><span data-stu-id="64990-144">To search all content locations for a specific service (Exchange mailboxes, SharePoint and OneDrive sites, or Exchange public folders), click the corresponding **Select all** toggle in the **Status** column.</span></span> <span data-ttu-id="64990-145">このオプションは、選択したサービス内のすべてのコンテンツの場所を検索します。</span><span class="sxs-lookup"><span data-stu-id="64990-145">This option will search all content locations in the selected service.</span></span>

   - <span data-ttu-id="64990-146">サービスの特定のコンテンツの場所を検索するには、対応する [状態]列の [すべて選択] トグルをクリックし、[ユーザー、グループ、またはチーム **(Exchange** メールボックスの場合) またはサイトの選択 (SharePoint および OneDrive サイト) をクリックして、特定のコンテンツの場所を検索します。</span><span class="sxs-lookup"><span data-stu-id="64990-146">To search specific content location for a service, click the corresponding **Select all** toggle in the **Status** column, and then click **Users, groups or teams** (for Exchange mailboxes) or **Choose sites** for (SharePoint and OneDrive sites) to search specific content locations.</span></span>

7. <span data-ttu-id="64990-147">[条件 **] ページ** で、前のウィザード ページで特定したデータ ソースからアイテムを収集するために使用する検索クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="64990-147">On the **Conditions** page, you can create the search query that is used to collect items from the data sources that you've identified in the previous wizard pages.</span></span> <span data-ttu-id="64990-148">キーワード、プロパティ:値のペアを検索したり、キーワード リストを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="64990-148">You can search for keywords, property:value pairs, or use a keyword list.</span></span> <span data-ttu-id="64990-149">コレクションの範囲を絞り込むさまざまな検索条件を追加できます。</span><span class="sxs-lookup"><span data-stu-id="64990-149">You can also add various search conditions to narrow the scope of the collection.</span></span> <span data-ttu-id="64990-150">詳細については、「コレクションの [検索クエリをビルドする」を参照してください](building-search-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="64990-150">For more information, see [Build search queries for collections](building-search-queries.md).</span></span>

8. <span data-ttu-id="64990-151">[下書 **きとして保存またはレビュー セットに** 追加] ページで、[コレクションを下 **書きとして保存] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="64990-151">On the **Save as draft or add to review set** page, select **Save collection as draft**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="64990-152">このページのもう 1 つのオプションでは、アイテムを収集し、レビュー セットに直接追加できます。</span><span class="sxs-lookup"><span data-stu-id="64990-152">The other option on this page lets you collect items and add them direct to a review set.</span></span> <span data-ttu-id="64990-153">コレクションの結果の統計を確認してプレビューできる下書きコレクションを作成する代わりに、このオプションは、そのプロセスをスキップし、コレクションをレビュー セットに自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="64990-153">Instead of creating a draft collection that you can review statistics for and preview a sample of the collection results, this option skips that process and automatically adds the collection to a review set.</span></span> <span data-ttu-id="64990-154">コレクションをレビュー セットに追加する 2 番目のオプションを選択した場合は、Microsoft Teams および Yammer でチャット会話スレッド全体を収集し、クラウド添付ファイル (モダン添付ファイルとも呼ばれる) を収集するなど、構成する追加の設定があります。</span><span class="sxs-lookup"><span data-stu-id="64990-154">If you select the second option to add the collection to a review set, you have additional settings to configure, such as collecting entire chat conversation threads in Microsoft Teams and Yammer and collecting cloud attachments (also called *modern attachments*).</span></span> <span data-ttu-id="64990-155">これらの設定の詳細については、「下書きコレクションをレビュー [セットにコミットする」を参照してください](commit-draft-collection.md)。</span><span class="sxs-lookup"><span data-stu-id="64990-155">For more information about these settings, see [Commit a draft collection to a review set](commit-draft-collection.md).</span></span>

9. <span data-ttu-id="64990-156">[コレクション **の確認] ページ** で、前のページで構成したコレクション設定を確認および更新できます。</span><span class="sxs-lookup"><span data-stu-id="64990-156">On the **Review your collection** page, you can review and update the collection settings that you configured on the previous pages.</span></span>

   - <span data-ttu-id="64990-157">**[概要]** タブ: コレクションの名前と説明、コレクションの検索条件、追加のデータの場所、コレクションの種類を確認および変更します。</span><span class="sxs-lookup"><span data-stu-id="64990-157">**Summary** tab:  Review and modify the name and description of the collection, the collection search criteria, additional data locations, and the collection type.</span></span>

   - <span data-ttu-id="64990-158">**[ソース]** タブ: コレクションの保管データ ソースと非保管データ ソースを確認および変更します。</span><span class="sxs-lookup"><span data-stu-id="64990-158">**Sources** tab: Review and modify the custodial and non-custodial data sources for the collection.</span></span>

10. <span data-ttu-id="64990-159">[送信 **] を** クリックして下書きコレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="64990-159">Click **Submit** to create the draft collection.</span></span> <span data-ttu-id="64990-160">コレクションが作成されたという確認ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="64990-160">A page is displayed confirming that the collection was created.</span></span>

## <a name="what-happens-after-you-create-a-draft-collection"></a><span data-ttu-id="64990-161">下書きコレクションを作成した後の実行</span><span class="sxs-lookup"><span data-stu-id="64990-161">What happens after you create a draft collection</span></span>

<span data-ttu-id="64990-162">下書きコレクションを作成すると、ケースの [コレクション] ページにリストされ、進行中の状態が示されます。</span><span class="sxs-lookup"><span data-stu-id="64990-162">After you create a draft collection, it listed on the **Collections** page in the case and the status shows that it's in progress.</span></span> <span data-ttu-id="64990-163">検索プレビューと **見積もりの準備という** 名前のジョブも作成され、ケースの **[ジョブ** ] ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="64990-163">A job named **Preparing search preview and estimates** is also created and displayed on the **Jobs** page in the case.</span></span>

<span data-ttu-id="64990-164">下書き収集プロセス中に、Advanced eDiscovery は、コレクションで指定した検索条件とデータ ソースを使用して検索見積もりを実行します。</span><span class="sxs-lookup"><span data-stu-id="64990-164">During the draft collection process, Advanced eDiscovery performs a search estimate using the search criteria and data sources that you specified in the collection.</span></span> <span data-ttu-id="64990-165">高度な電子情報開示では、プレビューできるアイテムのサンプリングも準備されます。</span><span class="sxs-lookup"><span data-stu-id="64990-165">Advanced eDiscovery also prepares a sampling of items that you can preview.</span></span> <span data-ttu-id="64990-166">コレクションが完了すると、[コレクション] ページの次の列と対応 **する** 値が更新されます。</span><span class="sxs-lookup"><span data-stu-id="64990-166">When the collection is complete, the following columns and corresponding values on the **Collection** page are updated:</span></span>

![下書きコレクションの状態](../media/DraftCollectionStatus.png)

- <span data-ttu-id="64990-168">**Status**: コレクションの状態と種類を示します。</span><span class="sxs-lookup"><span data-stu-id="64990-168">**Status**: Indicates the status and type of collection.</span></span> <span data-ttu-id="64990-169">値 Estimated は **、** 下書きコレクションが完了したかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="64990-169">A value of **Estimated** indicates that a draft collection is complete.</span></span> <span data-ttu-id="64990-170">この同じ値は、コレクションが下書きコレクションであり、レビュー セットに追加されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="64990-170">This same value also indicates that the collection is a draft collection, and that it hasn't been added to a review set.</span></span> <span data-ttu-id="64990-171">[状態]**列の [コミット\*\*\*\*済み]** の値は、コレクションがレビュー セットに追加されたかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="64990-171">A value of **Committed** in the **Status** column indicates that the collection has been added to a review set.</span></span>

- <span data-ttu-id="64990-172">**[推定状態**] : 推定検索結果の状態と、検索の見積もりと統計情報を確認する準備ができているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="64990-172">**Estimate status**: Indicates the status of the estimated search results and whether or not the search estimates and statistics are ready for review.</span></span> <span data-ttu-id="64990-173">値が **[成功] の** 場合は、下書きコレクションの結果を確認する準備ができていることを示します。</span><span class="sxs-lookup"><span data-stu-id="64990-173">A value of **Successful** indicates the results of the draft collection are ready for review.</span></span> <span data-ttu-id="64990-174">下書きコレクションを最初に送信した後、コレクションがまだ実行されている状態を示す値が [進行中] と表示されます。</span><span class="sxs-lookup"><span data-stu-id="64990-174">After you first submit a draft collection, a value of **In progress** is displayed to indicate the collection is still running</span></span>

- <span data-ttu-id="64990-175">**プレビューの状態**: プレビューできるサンプル アイテムの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="64990-175">**Preview status**: Indicates the status of the sample items that you can preview.</span></span> <span data-ttu-id="64990-176">値が **[成功] の** 場合は、アイテムがプレビューの準備ができていることを示します。</span><span class="sxs-lookup"><span data-stu-id="64990-176">A value of **Successful** indicates the items are ready for preview.</span></span> <span data-ttu-id="64990-177">最初に下書きコレクションを送信した後、コレクションがまだ実行されている状態を示す値が [進行中] と表示されます。</span><span class="sxs-lookup"><span data-stu-id="64990-177">After you first submit a draft collection, a value of **In progress** is displayed to indicate that the collection is still running.</span></span>

## <a name="next-steps-after-a-draft-collection-is-complete"></a><span data-ttu-id="64990-178">下書きコレクションの完了後の次の手順</span><span class="sxs-lookup"><span data-stu-id="64990-178">Next steps after a draft collection is complete</span></span>

<span data-ttu-id="64990-179">下書きコレクションが正常に完了したら、さまざまなタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="64990-179">After the draft collection is successfully completed, you can perform various tasks.</span></span> <span data-ttu-id="64990-180">これらのタスクのほとんどを実行するには、[コレクション]タブに移動し、下書きコレクションの名前をクリックして、フライアウト ページを表示します。</span><span class="sxs-lookup"><span data-stu-id="64990-180">To perform most of these tasks, just go the **Collections** tab and click the name of the draft collection to display the flyout page.</span></span>

![下書きコレクションのフライアウト ページ](../media/DraftCollectionFlyoutPage.png)

<span data-ttu-id="64990-182">コレクションのフライアウト ページから実行できる操作の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="64990-182">Here's a list of things you can do from the collection flyout page:</span></span>

- <span data-ttu-id="64990-183">[概要 **] タブを** 選択して、コレクションに関する概要情報と、コレクションによって返される推定検索結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="64990-183">Select the **Summary** tab to view summary information about the collection and the estimated search results returned by the collection.</span></span> <span data-ttu-id="64990-184">これには、推定検索結果のアイテム数とサイズの合計数、検索結果が含まれるメールボックスとサイトの数、およびコレクションのスコープに使用される検索条件 (使用されている場合) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="64990-184">This includes that total number of items and size of the estimated search results, the number of mailboxes and sites contained search results, and the search conditions (if used) used to scope the collection.</span></span>

- <span data-ttu-id="64990-185">[データ **ソース] タブを** 選択して、コレクション内で検索された保管担当者および非保管データ ソースの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="64990-185">Select the **Data sources** tab to view a list of custodians and non-custodial data sources) that were searched in the collection.</span></span> <span data-ttu-id="64990-186">検索されたその他のコンテンツの場所は、[概要] タブの **[場所** ] **の下に表示** されます。</span><span class="sxs-lookup"><span data-stu-id="64990-186">Any additional content locations that were search are listed under **Locations** on the **Summary** tab.</span></span>

- <span data-ttu-id="64990-187">[検索の **統計情報] タブ** を選択して、コレクションに関する統計情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="64990-187">Select the **Search statistics** tab to view statistics about the collection.</span></span> <span data-ttu-id="64990-188">これには、各サービスで見つかったアイテムの総数とサイズ (Exchange メールボックスや SharePoint サイトなど) と、コレクションで使用される検索クエリの異なるコンポーネントによって返されるアイテムの数に関する統計情報を表示する条件レポートが含まれます。</span><span class="sxs-lookup"><span data-stu-id="64990-188">This includes the total number and size of items found in each service (for example, Exchange mailboxes or SharePoint sites) and a condition report that displays statistics about the number of items returned by different components of the search query used by the collection.</span></span> <span data-ttu-id="64990-189">詳細については、「コレクションの統計情報 [とレポート」を参照してください](collection-statistics-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="64990-189">For more information, see [Collection statistics and reports](collection-statistics-reports.md).</span></span>

- <span data-ttu-id="64990-190">[ **レビュー サンプル]** (フライアウト ページの下部にある) をクリックして、コレクションから返されるアイテムのサンプルをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="64990-190">Click **Review sample** (located at the bottom of the flyout page) to preview a sample of the items returned by the collection.</span></span>

- <span data-ttu-id="64990-191">下書きコレクションをレビュー セットにコミットします ([アクションの編集]**コレクションを**  >  **クリックします**)。</span><span class="sxs-lookup"><span data-stu-id="64990-191">Commit the draft collection to a review set (by clicking **Actions** > **Edit collection**).</span></span> <span data-ttu-id="64990-192">つまり、(現在の設定を使用して) コレクションを再実行し、コレクションから返されたアイテムをレビュー セットに追加します。</span><span class="sxs-lookup"><span data-stu-id="64990-192">This means that you rerun the collection (using the current settings) and add the items returned by the collection to a review set.</span></span> <span data-ttu-id="64990-193">前に説明したように、コレクションをレビュー セットに追加するときに、追加の設定 (スレッドスレッドやクラウドベースの添付ファイルなど) を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="64990-193">As previously explained, you can also configure additional settings (such as conversation threading and cloud-based attachments) when you add the collection to a review set.</span></span> <span data-ttu-id="64990-194">詳細と手順については、「レビュー セットに下書きコレクションをコミット [する」を参照してください](commit-draft-collection.md)。</span><span class="sxs-lookup"><span data-stu-id="64990-194">For more information and step-by-step instructions, see [Commit a draft collection to a review set](commit-draft-collection.md).</span></span>

## <a name="manage-a-draft-collection"></a><span data-ttu-id="64990-195">下書きコレクションの管理</span><span class="sxs-lookup"><span data-stu-id="64990-195">Manage a draft collection</span></span>

<span data-ttu-id="64990-196">下書きコレクションのフライアウト ページの [ **アクション** ] メニューのオプションを使用して、さまざまな管理タスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="64990-196">You can use the options in the **Actions** menu on the flyout page of a draft collection to perform various management tasks.</span></span>

![下書きコレクションの [アクション] メニューのオプション](../media/DraftCollectionActionsMenu.png)

<span data-ttu-id="64990-198">管理オプションの説明を次に示します。</span><span class="sxs-lookup"><span data-stu-id="64990-198">Here's are descriptions of the management options.</span></span>

- <span data-ttu-id="64990-199">**コレクションの編集**: 下書きコレクションの設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="64990-199">**Edit collection**: Change the settings of the draft collection.</span></span> <span data-ttu-id="64990-200">変更を加えた後、コレクションを再実行し、検索の推定値と統計情報を更新できます。</span><span class="sxs-lookup"><span data-stu-id="64990-200">After you make changes, you can rerun the collection and update the search estimates and statistics.</span></span> <span data-ttu-id="64990-201">前に説明したように、このオプションを使用して下書きコレクションをレビュー セットにコミットします。</span><span class="sxs-lookup"><span data-stu-id="64990-201">As previously explained, you use this option to commit a draft collection to a review set.</span></span>  

- <span data-ttu-id="64990-202">**コレクションの削除**: 下書きコレクションを削除します。</span><span class="sxs-lookup"><span data-stu-id="64990-202">**Delete collection**: Delete a draft collection.</span></span> <span data-ttu-id="64990-203">下書きコレクションがレビュー セットにコミットされた後は、削除できない点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="64990-203">Note that after a draft collection is committed to a review set, it can't be deleted.</span></span>

- <span data-ttu-id="64990-204">**推定値の更新**: 下書きコレクションで指定されたクエリ (データ ソースに対して) を再実行して、検索の推定値と統計情報を更新します。</span><span class="sxs-lookup"><span data-stu-id="64990-204">**Refresh estimates**: Rerun the query (against the data sources) specified in the draft collection to update the search estimates and statistics.</span></span>

- <span data-ttu-id="64990-205">**レポートとしてエクスポート**: 下書きコレクションに関する情報を、ローカル コンピューターにダウンロードできる CSV ファイルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="64990-205">**Export as report**: Exports information about the draft collection to a CSV file that you can download to your local computer.</span></span> <span data-ttu-id="64990-206">エクスポート レポートには、次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="64990-206">The export report contains the following information:</span></span>

  - <span data-ttu-id="64990-207">下書きコレクション内の検索クエリに一致するアイテムを含む各コンテンツの場所の ID。</span><span class="sxs-lookup"><span data-stu-id="64990-207">The identity of each content location that contains items that match the search query in the draft collection.</span></span> <span data-ttu-id="64990-208">これらの場所は、通常、メールボックスまたはサイトです。</span><span class="sxs-lookup"><span data-stu-id="64990-208">These locations are typically mailboxes or sites.</span></span>
  
  - <span data-ttu-id="64990-209">各コンテンツの場所のアイテムの総数。</span><span class="sxs-lookup"><span data-stu-id="64990-209">The total number of items in each content location.</span></span>
  
  - <span data-ttu-id="64990-210">各コンテンツの場所にあるアイテムの合計サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="64990-210">The total size (in bytes) of the items in each content location.</span></span>

  - <span data-ttu-id="64990-211">コンテンツの場所があるサービス (Exchange や SharePoint など)。</span><span class="sxs-lookup"><span data-stu-id="64990-211">The service (such as Exchange or SharePoint) in which the content location is located.</span></span>

- <span data-ttu-id="64990-212">**Copy collection**: 既存のコレクションから設定をコピーして、新しい下書きコレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="64990-212">**Copy collection**: Create a new draft collection by copying the settings from an existing collection.</span></span> <span data-ttu-id="64990-213">新しいコレクションに別の名前を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64990-213">You have to use a different name for the new collection.</span></span> <span data-ttu-id="64990-214">また、新しいコレクションを送信する前に設定を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="64990-214">You also have the option to modify the settings before you submit the new collection.</span></span> <span data-ttu-id="64990-215">送信すると、検索クエリが実行され、新しい推定値と統計情報が生成されます。</span><span class="sxs-lookup"><span data-stu-id="64990-215">After you submit it, the search query is run and new estimates and statistics are generated.</span></span> <span data-ttu-id="64990-216">これは、追加の下書きコレクションをすばやく作成し、必要に応じて選択した設定を変更し、元のコレクション内の情報を保持する良い方法です。</span><span class="sxs-lookup"><span data-stu-id="64990-216">The is a good way to quickly create additional draft collection and then modify selected settings as necessary while still preserving information in the original collection.</span></span> <span data-ttu-id="64990-217">また、同様の 2 つのコレクションの結果を簡単に比較できます。</span><span class="sxs-lookup"><span data-stu-id="64990-217">This also lets you easily compare the results of two similar collections.</span></span>

> [!NOTE]
> <span data-ttu-id="64990-218">下書きコレクションがレビュー セットにコミットされた後は、コレクションのコピーとレポートのエクスポートのみ可能です。</span><span class="sxs-lookup"><span data-stu-id="64990-218">After a draft collection is committed to a review set, you can only copy the collection and export a report.</span></span>