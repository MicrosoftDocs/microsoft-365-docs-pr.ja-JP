---
title: Advanced eDiscovery のコレクションの概要
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: nickrob
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Advanced eDiscovery のコレクションを使用して、ケースまたは調査に関連するコンテンツを検索して収集します。
ms.openlocfilehash: e3f383fab31ec39f22bd781fc84644e3eeee57bb
ms.sourcegitcommit: 8f1721de52dbe3a12c11a0fa5ed0ef5972ca8196
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2021
ms.locfileid: "50838936"
---
# <a name="learn-about-collections-in-advanced-ediscovery"></a><span data-ttu-id="079ba-103">Advanced eDiscovery のコレクションの詳細</span><span class="sxs-lookup"><span data-stu-id="079ba-103">Learn about collections in Advanced eDiscovery</span></span>

> [!NOTE]
> <span data-ttu-id="079ba-104">この記事で説明する Advanced eDiscovery では、新しいコレクション エクスペリエンスを展開しています。</span><span class="sxs-lookup"><span data-stu-id="079ba-104">We're rolling out a new collections experience in Advanced eDiscovery, which is described in this article.</span></span> <span data-ttu-id="079ba-105">このロールアウトには、すべての組織が利用できるまで、数週間かかります。</span><span class="sxs-lookup"><span data-stu-id="079ba-105">This rollout will take a number of weeks before it's available to all organizations.</span></span> <span data-ttu-id="079ba-106">組織で新しいコレクション エクスペリエンスを使用できない場合でも、高度な電子情報開示検索ツールを使用してケース コンテンツ [を収集できます](create-search-to-collect-data.md)。</span><span class="sxs-lookup"><span data-stu-id="079ba-106">If the new collections experience isn't available in your organization, you can still collect case content with the [Advanced eDiscovery search tool](create-search-to-collect-data.md).</span></span>

<span data-ttu-id="079ba-107">組織が調査や潜在的な訴訟に関連する可能性のあるコミュニケーションとコンテンツの収集に直面した場合、最高の状況下で大きな課題に直面します。</span><span class="sxs-lookup"><span data-stu-id="079ba-107">When organizations are faced with gathering the communications and content that may be relevant to an investigation or potential litigation, they face a significant challenge under the best of circumstances.</span></span> <span data-ttu-id="079ba-108">今日の最新の職場では、コンテンツの量、多様性、速度が革新とリモート作業を可能にし、電子情報開示調査のコレクションを管理するための要件とプロセスも拡大しています。</span><span class="sxs-lookup"><span data-stu-id="079ba-108">In today’s modern workplace, the volume, variety, and velocity of content is enabling innovation and remote work, while also expanding the requirements and process for managing collections for eDiscovery investigations.</span></span>

<span data-ttu-id="079ba-109">コレクション ワークフローは、ネイティブの場所とソースからコンテンツを抽出する上で、技術的に大きな課題を抱えています。</span><span class="sxs-lookup"><span data-stu-id="079ba-109">The collection workflow poses significant technical challenges around extracting content from native locations and sources.</span></span> <span data-ttu-id="079ba-110">また、一般的な訴訟や調査シナリオの評価と戦略の重要なポイントです。</span><span class="sxs-lookup"><span data-stu-id="079ba-110">It's also a critical point in the assessment and strategy for common litigation or investigations scenarios.</span></span> <span data-ttu-id="079ba-111">組織が調査の評価を開始すると、最初に質問されたのは、誰が関与していたかです。</span><span class="sxs-lookup"><span data-stu-id="079ba-111">As organizations begin to assess an investigation, the first questions asked are who was involved?</span></span> <span data-ttu-id="079ba-112">関係者を特定した後、これらの保管担当者を迅速に保留にし、関連するコンテンツを保持できます。</span><span class="sxs-lookup"><span data-stu-id="079ba-112">After identifying who was involved, these custodians can quickly be placed on hold to preserve relevant content.</span></span> <span data-ttu-id="079ba-113">次の質問は、何が起こったかです。</span><span class="sxs-lookup"><span data-stu-id="079ba-113">The next question is what took place?</span></span> <span data-ttu-id="079ba-114">調査に関するこの 2 つ目の基本的な質問に答えるには、管理者がデータに目を向けなければならない。</span><span class="sxs-lookup"><span data-stu-id="079ba-114">To answer this second fundamental question of any investigation, managers must turn to the data.</span></span> <span data-ttu-id="079ba-115">何が起こったのかという問題に最も関連性の高いコンテンツをすばやく評価するために、管理者は質問のターゲットを絞り込み、コレクションの結果が広すぎることなく包括的に行われることを確認します。</span><span class="sxs-lookup"><span data-stu-id="079ba-115">To quickly assess the most relevant content to the question of what took place, managers start to refine the target of the question to ensure that the collection results are comprehensive without being too broad.</span></span>

<span data-ttu-id="079ba-116">高度な電子情報開示のコレクションは、電子情報開示管理者が Microsoft 365 の電子メール、ドキュメント、その他のコンテンツ間でコンテンツの検索をすばやく範囲指定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="079ba-116">Collections in Advanced eDiscovery help eDiscovery managers quickly scope a search for content across email, documents, and other content in Microsoft 365.</span></span> <span data-ttu-id="079ba-117">コレクションは、ケースに関連する可能性のあるコンテンツの見積もりを管理者に提供します。</span><span class="sxs-lookup"><span data-stu-id="079ba-117">Collections provide managers with an estimate of the content that may be relevant to the case.</span></span> <span data-ttu-id="079ba-118">これにより、管理者は、ケースに関連するコンテンツのサイズと範囲について、情報に基づいた迅速な意思決定を行う事が可能になります。</span><span class="sxs-lookup"><span data-stu-id="079ba-118">This allows managers to make quick, informed decisions about the size and scope of content relevant to a case.</span></span> <span data-ttu-id="079ba-119">電子情報開示管理者は、保管データ ソース (メールボックスや SharePoint サイトなど) を検索するコレクションを作成し、特定の検索条件 (キーワードや日付範囲など) を使用してコレクションの範囲をすばやく定義できます。</span><span class="sxs-lookup"><span data-stu-id="079ba-119">eDiscovery managers can create a collection to search custodial data sources (such as mailboxes and SharePoint sites) and by using specific search criteria (such as keywords and date ranges) to quickly define the scope of their collection.</span></span>

<span data-ttu-id="079ba-120">コレクションが定義された後、電子情報開示管理者はコレクションを下書きとして保存し、データ ボリュームの見積もり、結果を含むコンテンツの場所、および検索クエリ条件のヒット数などの見積もりを取得できます。</span><span class="sxs-lookup"><span data-stu-id="079ba-120">After the collection is defined, eDiscovery managers can save the collection as a draft and get estimates, including estimates for data volume, the content locations that contain results, and the number of hits for search query condition.</span></span> <span data-ttu-id="079ba-121">これらの分析情報は、コレクションを変更してコレクションの範囲を絞り込むか拡大する必要がある場合に、電子情報開示ワークフローのレビューと分析の段階に進む前に知らせるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="079ba-121">These insights can help to inform if the collection should be revised to narrow or expand the scope of the collection before moving on the review and analyze stages in the eDiscovery workflow.</span></span>

<span data-ttu-id="079ba-122">マネージャーがコレクションの範囲と、応答性が高いコンテンツの推定量に満足したら、管理者はコンテンツをレビュー セットに追加またはコミットできます。 </span><span class="sxs-lookup"><span data-stu-id="079ba-122">When the manager is satisfied with the scope of the collection and the estimated amount of content that's likely to be responsive, the manager can add or *commit* the content to a review set.</span></span> <span data-ttu-id="079ba-123">コレクションをレビュー セットにコミットする場合、そのマネージャーには、チャットの会話、クラウド添付ファイル、ドキュメントバージョンを含めるオプションも用意されています。</span><span class="sxs-lookup"><span data-stu-id="079ba-123">When committing a collection to a review set, that manager also has the options to include chat conversations, cloud attachments, and document versions.</span></span> <span data-ttu-id="079ba-124">コレクション内のコンテンツは、レビュー セットへの取り込み中に別のレベルの処理も行います。</span><span class="sxs-lookup"><span data-stu-id="079ba-124">The content in the collection also goes through another level of processing during ingestion into the review set.</span></span> <span data-ttu-id="079ba-125">コレクションは最終的なコレクションの概要で更新されます。</span><span class="sxs-lookup"><span data-stu-id="079ba-125">and the collection will be updated with the final collection summary.</span></span> <span data-ttu-id="079ba-126">コンテンツがレビュー セットに追加された後、電子情報開示管理者は、最小化とレビューに役立つコンテンツのクエリ、グループ化、絞り込み作業を続行できます。</span><span class="sxs-lookup"><span data-stu-id="079ba-126">After content is added to the review set, eDiscovery managers can continue to query, group, and refine the content in to help with minimization and review.</span></span> <span data-ttu-id="079ba-127">さらに、コレクションは、レビュー セットにコミットされたコンテンツに関する情報と統計情報で更新されます。</span><span class="sxs-lookup"><span data-stu-id="079ba-127">Additionally, the collection is updated with information and statistics about the content committed to the review set.</span></span> <span data-ttu-id="079ba-128">これにより、コレクション内のコンテンツに関する履歴参照が提供されます。</span><span class="sxs-lookup"><span data-stu-id="079ba-128">This provides a historical reference about the content in the collection.</span></span>

<span data-ttu-id="079ba-129">高度な電子情報開示のコレクションのリリースによって、[検索]タブの名前が Microsoft 365 コンプライアンス センターの高度な電子情報開示ケースのコレクションに変更されました。 </span><span class="sxs-lookup"><span data-stu-id="079ba-129">With the release of collections in an Advanced eDiscovery, the **Searches** tab has been renamed to **Collections** in an Advanced eDiscovery case in the Microsoft 365 compliance center.</span></span> <span data-ttu-id="079ba-130">コレクションの範囲とサイズを定義する手順は、検索と同じプロセスに従って場所と条件を定義します。</span><span class="sxs-lookup"><span data-stu-id="079ba-130">The steps to define the scope and size of the collection follow the same process as search to define locations and conditions.</span></span> <span data-ttu-id="079ba-131">下書きとして保存し、プレビュー見積もりを取得すると、完全な検索とコレクションをレビュー セットにコミットする前に、対象範囲のコレクションを迅速に検証できます。</span><span class="sxs-lookup"><span data-stu-id="079ba-131">Save as draft and get preview estimates enables quick validation of targeted scope of collections prior to committing a full search and collection into the review set.</span></span> <span data-ttu-id="079ba-132">これにより、ジョブ管理が改善され、検索および収集プロセス中にコンテンツを最小限に抑えるためのターゲット反復が可能になります。</span><span class="sxs-lookup"><span data-stu-id="079ba-132">This enables improved job management, and targeted iterations for starting to minimize content during the search and collection process.</span></span>

## <a name="collections-workflow"></a><span data-ttu-id="079ba-133">コレクションのワークフロー</span><span class="sxs-lookup"><span data-stu-id="079ba-133">Collections workflow</span></span>

<span data-ttu-id="079ba-134">Advanced eDiscovery のコレクションの使用を開始するには、基本的なワークフローとプロセス内の各ステップの説明を次に示します。</span><span class="sxs-lookup"><span data-stu-id="079ba-134">To get started using collections in Advanced eDiscovery, here's a basic workflow and descriptions of each step in the process.</span></span>

![Advanced eDiscovery のコレクション ワークフロー](../media/CollectionsWorkflow.png)

1. <span data-ttu-id="079ba-136">**下書きコレクションを作成して実行します**。</span><span class="sxs-lookup"><span data-stu-id="079ba-136">**Create and run a draft collection**.</span></span> <span data-ttu-id="079ba-137">最初の手順は、下書きコレクションを作成し、検索する保管データ ソースと非保管データ ソースを定義することです。</span><span class="sxs-lookup"><span data-stu-id="079ba-137">The first step is to create a draft collection and define the custodial and non-custodial data sources to search.</span></span> <span data-ttu-id="079ba-138">ケースに追加されていない他のデータ ソースを検索できます。</span><span class="sxs-lookup"><span data-stu-id="079ba-138">You can also search other data sources that haven't been added to the case.</span></span> <span data-ttu-id="079ba-139">データ ソースを追加した後、ケースに関連するコンテンツのデータ ソースを検索する検索クエリを構成します。</span><span class="sxs-lookup"><span data-stu-id="079ba-139">After you add the data sources, you configure the search query to search the data sources for content relevant to the case.</span></span> <span data-ttu-id="079ba-140">キーワード、プロパティ、および条件を使用して、ケースに最も関連性の高いコンテンツを返す検索クエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="079ba-140">You can keywords, properties, and conditions to build search queries that return content that's likely most relevant to the case.</span></span> <span data-ttu-id="079ba-141">詳細については、「下書き [コレクションを作成する」を参照してください](create-draft-collection.md)。</span><span class="sxs-lookup"><span data-stu-id="079ba-141">For more information, see [Create a draft collection](create-draft-collection.md).</span></span>

2. <span data-ttu-id="079ba-142">**推定値と統計を確認します**。</span><span class="sxs-lookup"><span data-stu-id="079ba-142">**Review estimates and statistics**.</span></span> <span data-ttu-id="079ba-143">下書きコレクションを作成して実行した後、次の手順では、関連するコンテンツが見つかるかどうかを確認し、ヒット数が最も多いコンテンツの場所を確認するためにコレクションの統計情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="079ba-143">After you create a draft collection and run it, the next step is to view collection statistics to help you verify whether relevant content is being found and the content locations with the most hits.</span></span> <span data-ttu-id="079ba-144">また、検索結果のサンプルをプレビューして、コンテンツが調査の範囲内にあるかどうかを判断するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="079ba-144">You can also preview a sample of the search results to further help you determine if the content is within scope of your investigation.</span></span> <span data-ttu-id="079ba-145">詳細については、「下書き [コレクションの統計とレポート」を参照してください](collection-statistics-reports.md#statistics-and-reports-for-draft-collections)。</span><span class="sxs-lookup"><span data-stu-id="079ba-145">For more information, see [Statistics and reports for draft collections](collection-statistics-reports.md#statistics-and-reports-for-draft-collections).</span></span>

3. <span data-ttu-id="079ba-146">**下書きコレクションを修正して再実行します**。</span><span class="sxs-lookup"><span data-stu-id="079ba-146">**Revise and rerun a draft collection**.</span></span> <span data-ttu-id="079ba-147">コレクションから返される推定値と統計情報に基づいて、検索するデータ ソースと検索クエリを変更してコレクションを展開または絞り込みすることで、下書きコレクションを編集できます。</span><span class="sxs-lookup"><span data-stu-id="079ba-147">Based on the estimates and statistics returned by the collection, you can edit the draft collection by changing the data sources that are searched and the search query to expand or narrow the collection.</span></span> <span data-ttu-id="079ba-148">ケースに最も関連性の高いコンテンツがコレクションに含まれていると確信するまで、下書きコレクションを更新して再実行できます。</span><span class="sxs-lookup"><span data-stu-id="079ba-148">You can update and rerun the draft collection until you're confident that collection contains the content that's most relevant to your case.</span></span>

4. <span data-ttu-id="079ba-149">**下書きコレクションをレビュー セットにコミットします**。</span><span class="sxs-lookup"><span data-stu-id="079ba-149">**Commit a draft collection to a review set**.</span></span> <span data-ttu-id="079ba-150">コレクションがケースに関連する種類のコンテンツを返すのに満足したら、コレクションをレビュー セットにコミットできます。</span><span class="sxs-lookup"><span data-stu-id="079ba-150">When you're satisfied that the collection returns the type content that is relevant to the case, you can commit the collection to the review set.</span></span> <span data-ttu-id="079ba-151">コレクションをコミットすると、会話スレッド、クラウド添付ファイル、ドキュメント バージョンをレビュー セットに追加できます。そのすべてがケースに関連している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="079ba-151">When you commit a collection, you have the option to add conversation threads, cloud attachments, and document versions to the review set, all of which might be relevant to the case.</span></span> <span data-ttu-id="079ba-152">コレクションをコミットすると、次のことが発生します。</span><span class="sxs-lookup"><span data-stu-id="079ba-152">The following things happen when you commit a collection:</span></span>

   - <span data-ttu-id="079ba-153">子アイテム (メールの添付ファイル、電子メール署名、画像など) は、親アイテム (電子メール メッセージ、チャット メッセージ、ドキュメントなど) から抽出され、インデックスが作成され (ディープ インデックス処理と呼ばれるプロセスで)、レビュー セットに個別のファイルとして追加されます。</span><span class="sxs-lookup"><span data-stu-id="079ba-153">Child items (such as email attachments, email signatures, and images) are extracted from a parent item (such as an email message, chat message, or document), indexed (in a process called *deep indexing*), and added to the review set as separate files.</span></span>

   - <span data-ttu-id="079ba-154">ディープ インデックスは、追加のデータ ソースから収集されたアイテムに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="079ba-154">Deep indexing is performed on items collected from additional data sources.</span></span> <span data-ttu-id="079ba-155">これらの種類のデータ ソースは、以前にケースに追加された保管データ ソースおよび非保管データ ソース以外のコンテンツの場所です。</span><span class="sxs-lookup"><span data-stu-id="079ba-155">These types of data sources are content locations other than the custodial and non-custodial data sources previously added to the case.</span></span>

   <span data-ttu-id="079ba-156">詳細については、「下書き [コレクションをレビュー セットにコミットする」を参照してください](commit-draft-collection.md)。</span><span class="sxs-lookup"><span data-stu-id="079ba-156">For more information, see [Commit a draft collection to a review set](commit-draft-collection.md).</span></span>

5. <span data-ttu-id="079ba-157">**コレクションの概要と統計情報を確認します**。</span><span class="sxs-lookup"><span data-stu-id="079ba-157">**Review collection summary and statistics**.</span></span> <span data-ttu-id="079ba-158">コレクションをレビュー セットにコミットすると、抽出されたアイテムに関する統計情報、ディープ インデックス作成、コレクションに使用される検索クエリ、アイテムが収集されたコンテンツの場所など、コレクションに関する情報が保持されます。</span><span class="sxs-lookup"><span data-stu-id="079ba-158">After you commit a collection to a review set, information about the collection is retained, such as statistics about extracted items, deep indexing, the search query used for the collection, and the content locations that items were collected from.</span></span> <span data-ttu-id="079ba-159">また、コミットされたコレクションを編集したり再実行したりもできない。</span><span class="sxs-lookup"><span data-stu-id="079ba-159">Also, committed collections can't be edited or rerun.</span></span> <span data-ttu-id="079ba-160">コピーまたは削除のみ可能です。</span><span class="sxs-lookup"><span data-stu-id="079ba-160">You can only copy or delete them.</span></span> <span data-ttu-id="079ba-161">コレクションを保持すると、レビュー セットに追加された収集されたアイテムの履歴レコードが提供されます。</span><span class="sxs-lookup"><span data-stu-id="079ba-161">Preserving collections provides a historical record of the collected items that were added to a review set.</span></span> <span data-ttu-id="079ba-162">詳細については、「コミットされたコレクション [の統計とレポート」を参照してください](collection-statistics-reports.md#statistics-and-reports-for-committed-collections)。</span><span class="sxs-lookup"><span data-stu-id="079ba-162">For more information, see [Statistics and reports for committed collections](collection-statistics-reports.md#statistics-and-reports-for-committed-collections).</span></span>