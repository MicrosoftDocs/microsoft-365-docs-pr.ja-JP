---
title: 'Microsoft SharePoint の同期のための導入: 作業の開始'
description: 組織で SharePoint の同期 Tex を使用して実装する方法について説明します。ビジネス上の問題を解決するのに役立ちます。
ms.author: samanro
author: samanro
manager: pamgreen
ms.date: 7/20/2020
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.custom: Adopt
search.appverid: ''
localization_priority: Normal
ms.openlocfilehash: f6bb4f5e09adcb1be6323a5d3d182cc3d1bc6017
ms.sourcegitcommit: 3f8e573244bc082518125e339a385c41ef6ee800
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2020
ms.locfileid: "48337231"
---
# <a name="microsoft-sharepoint-syntex-adoption-get-started"></a><span data-ttu-id="ff4a9-103">Microsoft SharePoint の同期のための導入: 作業の開始</span><span class="sxs-lookup"><span data-stu-id="ff4a9-103">Microsoft SharePoint Syntex adoption: Get started</span></span>

<span data-ttu-id="ff4a9-104">SharePoint の同期 Tex で利用可能なインテリジェントコンテンツサービスは3つの部分で構成されています。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-104">Think of the intelligent content services available in SharePoint Syntex as having three parts:</span></span>

- <span data-ttu-id="ff4a9-105">**コンテンツの理解:** コードなしの AI モデルを作成してコンテンツから情報を分類および抽出して、ナレッジの検出と再利用のためにメタデータを自動的に適用します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-105">**Content understanding:** create no-code AI models to classify and extract information from content to automatically apply metadata for knowledge discovery and reuse.</span></span> <span data-ttu-id="ff4a9-106">詳細については、 [コンテンツの理解](document-understanding-overview.md)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-106">Learn more about [content understanding](document-understanding-overview.md).</span></span>
- <span data-ttu-id="ff4a9-107">**コンテンツ処理:** 電力の自動処理を使用して、コンテンツのキャプチャ、取り込み、分類を自動化し、コンテンツ中心のプロセスを効率化します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-107">**Content processing:** Automate capture, ingestion and categorization of content and streamline content-centric processes using Power Automate.</span></span> <span data-ttu-id="ff4a9-108">[コンテンツ処理](form-processing-overview.md)の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-108">Learn more about [content processing](form-processing-overview.md).</span></span>
- <span data-ttu-id="ff4a9-109">**コンテンツコンプライアンス:** Microsoft Information Protection との統合により、セキュリティとガバナンスを向上させるためのコンテンツの管理と管理を行います。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-109">**Content compliance:** Control and manage content to improve security and governance with integration to Microsoft Information Protection.</span></span>

<span data-ttu-id="ff4a9-110">新しい AI サービスと機能を使用すると、SharePoint の Syntex を使用してコンテンツの理解と分類のアプリをコンテンツ管理フローに直接作成できます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-110">With new AI services and capabilities, you can build content understanding and classification apps directly into the content management flow using SharePoint Syntex:</span></span>

|<span data-ttu-id="ff4a9-111">手動入力</span><span class="sxs-lookup"><span data-stu-id="ff4a9-111">Manual entry</span></span>| <span data-ttu-id="ff4a9-112">フォームの処理</span><span class="sxs-lookup"><span data-stu-id="ff4a9-112">Form processing</span></span> | <span data-ttu-id="ff4a9-113">ドキュメントについて</span><span class="sxs-lookup"><span data-stu-id="ff4a9-113">Document understanding</span></span> |
|:-------|:--------|:--------|
| <span data-ttu-id="ff4a9-114">コンテンツによるデータ入力と労力の浪費</span><span class="sxs-lookup"><span data-stu-id="ff4a9-114">Data entry and labor-intensive on any content</span></span> | <span data-ttu-id="ff4a9-115">デジタルコンテンツ-写真、スキャン、領収書、名刺、OCR & のビデオを処理する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-115">Process digital content - photos, scans, receipts, business cards, videos with OCR & text</span></span> |  <span data-ttu-id="ff4a9-116">契約、履歴書、およびその他の構造化されたドキュメントからコンテンツタイプとメタデータを取得する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-116">Capture content types and  metadata from contracts, resumes, and other structured documents</span></span> |
| <span data-ttu-id="ff4a9-117">Interactive</span><span class="sxs-lookup"><span data-stu-id="ff4a9-117">Interactive</span></span>   | <span data-ttu-id="ff4a9-118">事前に作成された自動</span><span class="sxs-lookup"><span data-stu-id="ff4a9-118">Pre-built, automated</span></span>   | <span data-ttu-id="ff4a9-119">カスタム、支援</span><span class="sxs-lookup"><span data-stu-id="ff4a9-119">Custom, assisted</span></span>   | <span data-ttu-id="ff4a9-120">カスタム、準拠</span><span class="sxs-lookup"><span data-stu-id="ff4a9-120">Custom, compliant</span></span> |
| <span data-ttu-id="ff4a9-121">作業を行うユーザー</span><span class="sxs-lookup"><span data-stu-id="ff4a9-121">People doing the work</span></span> | <span data-ttu-id="ff4a9-122">該当分野の専門家 (Sme) による学習。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-122">Taught by your subject matter experts (SMEs).</span></span> <span data-ttu-id="ff4a9-123">コントラクト、履歴書、その他の非構造化ドキュメントからコンテンツタイプとメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-123">Capture content types and  metadata from contracts, resumes, other unstructured documents.</span></span> | <span data-ttu-id="ff4a9-124">Sme の関与は少なくなります。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-124">SMEs are less involved.</span></span> <span data-ttu-id="ff4a9-125">発注書、アプリケーション、その他の半構造化ドキュメント、構造化ドキュメント</span><span class="sxs-lookup"><span data-stu-id="ff4a9-125">from purchase orders, applications, other semi structured and structured documents</span></span> |

<span data-ttu-id="ff4a9-126">次の表では、SharePoint の同期 Tex を使用する際に得られることを説明します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-126">The following table explains what you get when you use SharePoint Syntex:</span></span>

| <span data-ttu-id="ff4a9-127">フォームの処理</span><span class="sxs-lookup"><span data-stu-id="ff4a9-127">Form processing</span></span> | <span data-ttu-id="ff4a9-128">ドキュメントについて</span><span class="sxs-lookup"><span data-stu-id="ff4a9-128">Document understanding</span></span> |
|:-------|:-------|
| <span data-ttu-id="ff4a9-129">APAC、オーストラリア、カナダ、EU、JP、LATAM、英国、US で利用可能</span><span class="sxs-lookup"><span data-stu-id="ff4a9-129">Available in APAC, Australia, Canada, EU, JP, LATAM, UK, US</span></span> | <span data-ttu-id="ff4a9-130">すべての地域で利用可能</span><span class="sxs-lookup"><span data-stu-id="ff4a9-130">Available in all regions</span></span> |
| <span data-ttu-id="ff4a9-131">AI ビルダークレジットを使用して、2000ページを使用します。消費は約2000請求書 = 2 単位です。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-131">Uses AI Builder credits - 1M credits = 2000 pages; Consumption is about 2000 invoices=2 units.</span></span> <span data-ttu-id="ff4a9-132">電力の自動化が必要な場合は、追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-132">Power Automate is required - if you need more you can add it.</span></span> <span data-ttu-id="ff4a9-133">300以上のライセンスを購入した場合は、1M のクレジットが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-133">1M credits allocated for 300+ licenses purchased.</span></span> <span data-ttu-id="ff4a9-134">クレジットを個別に購入することもできます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-134">You can also purchase credits separately.</span></span> | <span data-ttu-id="ff4a9-135">モデルは、すべてのラテン系言語で動作します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-135">Models work on all latin alphabet languages.</span></span> <span data-ttu-id="ff4a9-136">英語に加えて、ドイツ語、スウェーデン語、フランス語、スペイン語、イタリア語、ポルトガル語に加えています。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-136">In addition to English: German, Swedish, French, Spanish, Italian, and Portuguese.</span></span> |
| <span data-ttu-id="ff4a9-137">既定の共通データサービス環境に対してプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-137">Provisioned against the default common data service environment</span></span>| <span data-ttu-id="ff4a9-138">容量制限がありません。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-138">Does not have capacity restrictions.</span></span> |

<span data-ttu-id="ff4a9-139">コンテンツを理解するには、2つの異なる方法があります。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-139">There are two different ways of understanding your content.</span></span> <span data-ttu-id="ff4a9-140">使用するモデルの種類は、ファイル形式とユースケースに基づいています。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-140">The model type you use is based on file format and use case:</span></span>

| <span data-ttu-id="ff4a9-141">フォームの処理</span><span class="sxs-lookup"><span data-stu-id="ff4a9-141">Form processing</span></span> | <span data-ttu-id="ff4a9-142">ドキュメントについて</span><span class="sxs-lookup"><span data-stu-id="ff4a9-142">Document understanding</span></span> |
|:-------|:-------|
| <span data-ttu-id="ff4a9-143">ドキュメントライブラリから作成</span><span class="sxs-lookup"><span data-stu-id="ff4a9-143">Created from document library</span></span> | <span data-ttu-id="ff4a9-144">コンテンツセンターで作成された SharePoint の同期の一部</span><span class="sxs-lookup"><span data-stu-id="ff4a9-144">Created in the content center, part of SharePoint Syntex</span></span> |
| <span data-ttu-id="ff4a9-145">AI ビルダーで作成されたモデル</span><span class="sxs-lookup"><span data-stu-id="ff4a9-145">Model created in AI builder</span></span> | <span data-ttu-id="ff4a9-146">ネイティブインターフェイスで作成されたモデル</span><span class="sxs-lookup"><span data-stu-id="ff4a9-146">Model created in native interface</span></span> |
| <span data-ttu-id="ff4a9-147">半構造化ファイル形式に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-147">Used for semi-structured file formats</span></span> | <span data-ttu-id="ff4a9-148">非構造化ファイル形式で使用されます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-148">Used for unstructured file formats</span></span> |
| <span data-ttu-id="ff4a9-149">設定可能分類子</span><span class="sxs-lookup"><span data-stu-id="ff4a9-149">Settable classifier</span></span> | <span data-ttu-id="ff4a9-150">オプションの抽出機能を備えた Trainable クラシファイア</span><span class="sxs-lookup"><span data-stu-id="ff4a9-150">Trainable classifier with optional extractors</span></span> |
| <span data-ttu-id="ff4a9-151">1つのライブラリに制限</span><span class="sxs-lookup"><span data-stu-id="ff4a9-151">Restricted to a single library</span></span> | <span data-ttu-id="ff4a9-152">複数のライブラリに適用できます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-152">Can be applied to multiple libraries</span></span> |
| <span data-ttu-id="ff4a9-153">PDF、JPG、PNG 形式、合計 50 MB/500 ページをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="ff4a9-153">Train on PDF, JPG, PNG format, total 50 MB/500 pp</span></span> | <span data-ttu-id="ff4a9-154">5-10 PDF、Office、または電子メールファイル (負の例を含む) をトレーニングする</span><span class="sxs-lookup"><span data-stu-id="ff4a9-154">Train on 5-10 PDF, Office, or email files, including negative examples</span></span> |

<span data-ttu-id="ff4a9-155">SharePoint の同期 Tex は、次のような Microsoft 365 のコンプライアンス機能と統合されるようになります。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-155">SharePoint Syntex integrates with Microsoft 365 compliance features like:</span></span>

- <span data-ttu-id="ff4a9-156">ドキュメントの保存期間または外部イベントに基づいてレコードポリシーを定義する保持ラベル。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-156">Retention labels that define records policy based on document age or external events.</span></span>
- <span data-ttu-id="ff4a9-157">DLP、暗号化、共有、および条件付きアクセスポリシーを設定する機密ラベル。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-157">Sensitivity labels that set DLP, encryption, sharing, and conditional access policies.</span></span>

<span data-ttu-id="ff4a9-158">ユーザーはラベルを適用することも、SharePoint の Syntex AI モデルによって自動的に適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-158">Users can apply labels, or they can be applied automatically by SharePoint Syntex AI models.</span></span> <span data-ttu-id="ff4a9-159">分析およびファイルプランは、ラベル使用法とポリシーの拡張管理を提供します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-159">Analytics and file plans provide scaled management of label usage and policies.</span></span>

## <a name="identify-pilot-business-scenarios-to-optimize"></a><span data-ttu-id="ff4a9-160">最適化のためのパイロットビジネスシナリオを特定する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-160">Identify pilot business scenarios to optimize</span></span>

<span data-ttu-id="ff4a9-161">組織で SharePoint の同期 Tex を使用するための準備をするには、まず、それが役に立つシナリオを理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-161">To prepare for using SharePoint Syntex in your organization, you first need to understand the scenarios in which it will be useful.</span></span> <span data-ttu-id="ff4a9-162">必要なモデルを決定するのに役立つ理由と、モデルが適用される場所に基づいて組織を構造化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-162">The why helps determine what model will be needed, and how to structure your org based on where the model will be applied.</span></span> <span data-ttu-id="ff4a9-163">次のシナリオでは、組織のためにドキュメントを理解することができます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-163">Here are a few scenarios where document understanding can help your organization:</span></span>

- <span data-ttu-id="ff4a9-164">コンテンツ処理: 契約、作業ステートメント、およびその他のフォーム形式のドキュメントを処理します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-164">Content processing: Process contracts, statements of work, and other form-like documents.</span></span> <span data-ttu-id="ff4a9-165">フォームを使い、フィールドを理解してマップするためのモデルを学習し、データを自動的に収集するためにフォームを実行します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-165">Intake the forms, train the model to understand and map the fields, and then run your forms through to automatically collect the data.</span></span> <span data-ttu-id="ff4a9-166">詳細については、「 [フォーム処理の概要](form-processing-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-166">For more information, see [Form processing overview](form-processing-overview.md).</span></span>
- <span data-ttu-id="ff4a9-167">請求書の分析: 請求書から関連する詳細を取得し、ポリシーに準拠しているか、または適切に処理されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-167">Invoice analysis: Pull out the relevant details from your invoices and make sure they're complying with policy or are being processed appropriately.</span></span>

<span data-ttu-id="ff4a9-168">SharePoint の Syntex が組織を支援する方法について考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-168">Think about ways that SharePoint Syntex can help your organization:</span></span>

- <span data-ttu-id="ff4a9-169">ビジネスプロセスを自動化する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-169">Automate business processes</span></span>
- <span data-ttu-id="ff4a9-170">検索精度を向上させる</span><span class="sxs-lookup"><span data-stu-id="ff4a9-170">Improve search accuracy</span></span>
- <span data-ttu-id="ff4a9-171">コンプライアンスリスクを管理する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-171">Manage compliance risk</span></span>

### <a name="form-processing-scenario-example"></a><span data-ttu-id="ff4a9-172">フォーム処理シナリオの例</span><span class="sxs-lookup"><span data-stu-id="ff4a9-172">Form processing scenario example</span></span>

<span data-ttu-id="ff4a9-173">たとえば、SharePoint の Syntex および Power 自動化機能を使用して、請求書を追跡および監視するプロセスをセットアップできます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-173">For example, you can set up a process using SharePoint Syntex and Power Automate features to track and monitor invoices.</span></span>

1. <span data-ttu-id="ff4a9-174">請求書ドキュメントを格納するライブラリを設定します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-174">Set up a library to store the invoice documents.</span></span>
1. <span data-ttu-id="ff4a9-175">ドキュメント内のフィールドを認識するようにモデルをトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-175">Train the model to recognize fields in the documents.</span></span>
1. <span data-ttu-id="ff4a9-176">追跡するフィールドをリストに抽出します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-176">Extract the fields you want to track into a list.</span></span>
1. <span data-ttu-id="ff4a9-177">次のような特定のイベントについて通知するフローを設定します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-177">Set up a flow to notify you for specific events, such as:</span></span>
    - <span data-ttu-id="ff4a9-178">新しい請求書が追加されます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-178">A new invoice is added.</span></span>
    - <span data-ttu-id="ff4a9-179">請求書が期日を過ぎています。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-179">An invoice is past its due date.</span></span>
    - <span data-ttu-id="ff4a9-180">請求書は、自動承認金額より大きい金額を対象としています。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-180">An invoice is for an amount that's larger than your automatic approval amount.</span></span>

![SharePoint の同期を追跡および監視する (請求書とパワー自動化)](../media/content-understanding/process-invoices-flow.png)

<span data-ttu-id="ff4a9-182">このシナリオを自動化すると、次のことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-182">When you automate this scenario, you can:</span></span>

- <span data-ttu-id="ff4a9-183">手動で実行するのではなく、請求書からデータを自動的に抽出して、時間とコストを節約できます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-183">Save time and money by automatically extracting data from the invoices instead of doing it manually.</span></span>
- <span data-ttu-id="ff4a9-184">潜在的なエラーを軽減し、ワークフローを使用して請求書を処理し、問題があるかどうかを通知することにより、コンプライアンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-184">Reduce potential errors and ensure better compliance by using workflows to act on the invoices and notify you of any issues.</span></span>

### <a name="document-understanding-scenario-example"></a><span data-ttu-id="ff4a9-185">ドキュメントについて理解しているシナリオの例</span><span class="sxs-lookup"><span data-stu-id="ff4a9-185">Document understanding scenario example</span></span>

<span data-ttu-id="ff4a9-186">別の例として、会社が他の会社または個人として持っている契約を識別するプロセスを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-186">As another example, you can set up a process to identify contracts that your company has with other companies or individuals.</span></span> <span data-ttu-id="ff4a9-187">クライアント名、料金、日付、その他の重要な情報など、これらの契約から重要な情報を抽出するためのモデルを設定し、表示できるフィールドとしてライブラリに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-187">You can set up a model to extract key information from those contracts, such as the client name, fees, dates, or other important information, and add that to the library as fields you can quickly view.</span></span> <span data-ttu-id="ff4a9-188">また、ドキュメントライブラリに保持ラベルを適用することにより、特定の時間が経過した後に、業務上の規制に準拠するために契約を削除できないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-188">And you can apply a retention label on the document library to ensure that contracts cannot be deleted before a specific length of time for appropriate compliance with your business regulations.</span></span>

1. <span data-ttu-id="ff4a9-189">コンテンツセンターから始めて、新しいドキュメントを作成します。契約に関する理解モデル。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-189">Start at the content center and create a new document understanding model for contracts.</span></span>
1. <span data-ttu-id="ff4a9-190">サンプルドキュメントをアップロードして、正および負の例を見つけ、トレーニングを実行して契約書を特定し、結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-190">Upload sample documents for positive and negative examples, then run the training to identify contract documents and review the results.</span></span>
1. <span data-ttu-id="ff4a9-191">クライアント名、手数料、日付などの契約のフィールドを特定するための抽出器をトレーニングし、抽出器をテストします。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-191">Train the extractor to identify fields in the contracts, such as the client name, fee, and date, and then test the extractor.</span></span>
1. <span data-ttu-id="ff4a9-192">モデルが完成したら、コントラクトをアップロードできるライブラリにモデルを適用します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-192">When the model is complete, apply the model to a library where you can upload contracts.</span></span>
1. <span data-ttu-id="ff4a9-193">保持ラベルを日付フィールドに適用して、組織が契約に必要とする時間の期間、ライブラリ内に契約が保持されるようにします。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-193">Apply a retention label to the date field, so that contracts are retained in the library for the length of time your organization requires for contracts.</span></span>

![SharePoint の同期 Tex および保持ラベルを使用して、コントラクトを追跡および監視する](../media/content-understanding/process-contracts-flow.png)

<span data-ttu-id="ff4a9-195">このシナリオを自動化すると、次のことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-195">When you automate this scenario, you can:</span></span>

- <span data-ttu-id="ff4a9-196">手動で行う代わりに、契約のデータを自動的に抽出して、時間とコストを節約できます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-196">Save time and money by automatically extracting data from the contracts instead of doing it manually.</span></span>
- <span data-ttu-id="ff4a9-197">保持ラベルを使用して、契約が適切に保持されるようにすることで、コンプライアンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-197">Ensure better compliance by using retention labels to ensure that the contracts are retained appropriately.</span></span>

### <a name="tips-for-identifying-scenarios"></a><span data-ttu-id="ff4a9-198">シナリオを識別するためのヒント</span><span class="sxs-lookup"><span data-stu-id="ff4a9-198">Tips for identifying scenarios</span></span>

<span data-ttu-id="ff4a9-199">考慮すべきビジネスシナリオについて検討する場合は、次の点を確認してください。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-199">When thinking about which business scenarios to consider, ask yourself the following questions:</span></span>

- <span data-ttu-id="ff4a9-200">実際の問題は解決しますか?</span><span class="sxs-lookup"><span data-stu-id="ff4a9-200">Does it solve a real problem?</span></span>
- <span data-ttu-id="ff4a9-201">広く使用されているか、広範な影響があるか。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-201">Will it be widely used or have broad impact?</span></span>
- <span data-ttu-id="ff4a9-202">入手ができますか?</span><span class="sxs-lookup"><span data-stu-id="ff4a9-202">Is it obtainable?</span></span>
- <span data-ttu-id="ff4a9-203">成功を測定できますか。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-203">Can you measure success?</span></span>

<span data-ttu-id="ff4a9-204">影響と実装の容易さに基づいてシナリオの優先度を設定します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-204">Prioritize scenarios based on impact and ease of implementation.</span></span> <span data-ttu-id="ff4a9-205">初期のフォーカス領域を、簡単に実装できる、より大きな影響を与えるシナリオにします。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-205">Make your initial focus area higher impact scenarios that can also be easily implemented.</span></span> <span data-ttu-id="ff4a9-206">実装が困難な影響度の低いシナリオに優先順位を付けないでください。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-206">De-prioritize lower impact scenarios that are hard to implement.</span></span>

## <a name="identify-roles--responsibilities"></a><span data-ttu-id="ff4a9-207">役割 & 責任を特定する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-207">Identify roles & responsibilities</span></span>

<span data-ttu-id="ff4a9-208">組織内のどのユーザーがモデルを構築して管理するかを決定する。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-208">Determine who in your organization will build and manage the models?</span></span> <span data-ttu-id="ff4a9-209">次の役割が関係している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-209">The following roles might be involved:</span></span>

| <span data-ttu-id="ff4a9-210">SharePoint/ナレッジ管理者</span><span class="sxs-lookup"><span data-stu-id="ff4a9-210">SharePoint/Knowledge admin</span></span> | <span data-ttu-id="ff4a9-211">電源プラットフォーム管理者</span><span class="sxs-lookup"><span data-stu-id="ff4a9-211">Power Platform admin</span></span> | <span data-ttu-id="ff4a9-212">ナレッジマネージャー</span><span class="sxs-lookup"><span data-stu-id="ff4a9-212">Knowledge manager</span></span> | <span data-ttu-id="ff4a9-213">モデルの所有者</span><span class="sxs-lookup"><span data-stu-id="ff4a9-213">Model owner</span></span> |
|:-------|:-------|:-------|:-------|
| <span data-ttu-id="ff4a9-214">AAD の役割</span><span class="sxs-lookup"><span data-stu-id="ff4a9-214">AAD role</span></span>| <span data-ttu-id="ff4a9-215">役割の追加</span><span class="sxs-lookup"><span data-stu-id="ff4a9-215">ADD role</span></span> | <span data-ttu-id="ff4a9-216">AAD の役割</span><span class="sxs-lookup"><span data-stu-id="ff4a9-216">AAD role</span></span> | <span data-ttu-id="ff4a9-217">チャンピオン</span><span class="sxs-lookup"><span data-stu-id="ff4a9-217">Champions</span></span> |
| <span data-ttu-id="ff4a9-218">フォーム処理を構成する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-218">Configure form processing</span></span> | <span data-ttu-id="ff4a9-219">フォーム処理のための共通データサービス環境を構成する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-219">Configure Common data service environment for form processing</span></span> | <span data-ttu-id="ff4a9-220">ユースケースを収集する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-220">Gather use cases</span></span> | <span data-ttu-id="ff4a9-221">ビジネスユースケースを収集する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-221">Gather business use cases</span></span> |
| <span data-ttu-id="ff4a9-222">コンテンツセンターとアクセス許可を管理する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-222">Manage content centers and permissions</span></span>| <span data-ttu-id="ff4a9-223">AIB クレジットの購入と割り当て</span><span class="sxs-lookup"><span data-stu-id="ff4a9-223">Purchase and allocate AIB credits</span></span> | <span data-ttu-id="ff4a9-224">ベストプラクティスを確立し、モデル分析をレビューする</span><span class="sxs-lookup"><span data-stu-id="ff4a9-224">Establish best practices and review model analytics</span></span> | <span data-ttu-id="ff4a9-225">モデルを作成および適用する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-225">Create and apply models</span></span> |

<span data-ttu-id="ff4a9-226">ナレッジマネージャー、ビジネスプロセスの所有者、およびコンテンツモデルの所有者は、サンプルモデルと組織内での支持者の採用を作成します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-226">Knowledge manager, Business Process Owner and Content model owner create sample models and champion adoption in the organization.</span></span>
<span data-ttu-id="ff4a9-227">関係のある他のユーザー: コンプライアンス管理者、分類マネージャー。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-227">Others who may be involved: Compliance admin, Taxonomy managers.</span></span>

<span data-ttu-id="ff4a9-228">モデルはどこで構築し適用しますか?</span><span class="sxs-lookup"><span data-stu-id="ff4a9-228">Where will they build and apply the models?</span></span> <span data-ttu-id="ff4a9-229">拡張できる既存のプロセスまたはリポジトリがあるかどうか。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-229">Are there existing processes or repositories that could be enhanced?</span></span>

- <span data-ttu-id="ff4a9-230">フォーム処理: フォーム処理アクションを取得するサイトを決定します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-230">Form processing: Decide which sites will get Form processing action.</span></span>
- <span data-ttu-id="ff4a9-231">ドキュメントの理解: さまざまなビジネス領域に対して複数のコンテンツセンターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-231">Document understanding: You can create multiple content centers for different business areas.</span></span>

## <a name="strategic-positioning"></a><span data-ttu-id="ff4a9-232">戦略的ポジショニング</span><span class="sxs-lookup"><span data-stu-id="ff4a9-232">Strategic positioning</span></span>

<span data-ttu-id="ff4a9-233">ステークホルダーと協力して、SharePoint の同期 Tex を使用するための戦略に沿っていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-233">Work with stakeholders to make sure they are aligned on the strategy for using SharePoint Syntex.</span></span> <span data-ttu-id="ff4a9-234">この位置付けを支援するために、以下のリソースを調査して提供します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-234">Research and provide the following resources to help with this positioning:</span></span>

- <span data-ttu-id="ff4a9-235">ビジネスの成果:</span><span class="sxs-lookup"><span data-stu-id="ff4a9-235">Business outcomes:</span></span>
  - <span data-ttu-id="ff4a9-236">考えられる会計成果</span><span class="sxs-lookup"><span data-stu-id="ff4a9-236">Potential fiscal outcomes</span></span>
  - <span data-ttu-id="ff4a9-237">アジリティの潜在的な結果</span><span class="sxs-lookup"><span data-stu-id="ff4a9-237">Potential agility outcomes</span></span>
  - <span data-ttu-id="ff4a9-238">ビジネス成果テンプレート</span><span class="sxs-lookup"><span data-stu-id="ff4a9-238">Business outcome template</span></span>
- <span data-ttu-id="ff4a9-239">ステークホルダー/Exec スポンサーの購入/配置</span><span class="sxs-lookup"><span data-stu-id="ff4a9-239">Stakeholders/Exec sponsor buy-in/alignment</span></span>
  - <span data-ttu-id="ff4a9-240">ビジネスケースのデッキ</span><span class="sxs-lookup"><span data-stu-id="ff4a9-240">Business case decks</span></span>
  - <span data-ttu-id="ff4a9-241">財務モデル</span><span class="sxs-lookup"><span data-stu-id="ff4a9-241">Financial models</span></span>
  - <span data-ttu-id="ff4a9-242">会社の準備-カルチャ</span><span class="sxs-lookup"><span data-stu-id="ff4a9-242">Company readiness - culture</span></span>

## <a name="identify-stakeholders"></a><span data-ttu-id="ff4a9-243">関係者の特定</span><span class="sxs-lookup"><span data-stu-id="ff4a9-243">Identify stakeholders</span></span>

<span data-ttu-id="ff4a9-244">プロジェクトの関係者を特定します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-244">Identify the stakeholders for your project.</span></span>

|<span data-ttu-id="ff4a9-245">ロール</span><span class="sxs-lookup"><span data-stu-id="ff4a9-245">Role</span></span> |<span data-ttu-id="ff4a9-246">責任</span><span class="sxs-lookup"><span data-stu-id="ff4a9-246">Responsibilities</span></span> |<span data-ttu-id="ff4a9-247">部門</span><span class="sxs-lookup"><span data-stu-id="ff4a9-247">Department</span></span> |
|:-------|:-------|:--------|
| <span data-ttu-id="ff4a9-248">エグゼクティブスポンサー</span><span class="sxs-lookup"><span data-stu-id="ff4a9-248">Executive sponsor(s)</span></span>   | <span data-ttu-id="ff4a9-249">高レベルのビジョンと価値を企業に伝える</span><span class="sxs-lookup"><span data-stu-id="ff4a9-249">Communicate high-level vision and values to the company</span></span>   |  <span data-ttu-id="ff4a9-250">経営幹部のリーダー</span><span class="sxs-lookup"><span data-stu-id="ff4a9-250">Executive leadership</span></span>   |
| <span data-ttu-id="ff4a9-251">プロジェクトリード (s)</span><span class="sxs-lookup"><span data-stu-id="ff4a9-251">Project lead(s)</span></span> | <span data-ttu-id="ff4a9-252">起動実行とロールアウトプロセス全体を監督します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-252">Oversee the entire launch execution and rollout process</span></span> | <span data-ttu-id="ff4a9-253">プロジェクト管理</span><span class="sxs-lookup"><span data-stu-id="ff4a9-253">Project management</span></span> |
| <span data-ttu-id="ff4a9-254">ナレッジ管理者</span><span class="sxs-lookup"><span data-stu-id="ff4a9-254">Knowledge administrators</span></span>| <span data-ttu-id="ff4a9-255">コンテンツセンターを作成および管理する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-255">Create and manage the content centers</span></span> | <span data-ttu-id="ff4a9-256">IT 部門またはその他の部署</span><span class="sxs-lookup"><span data-stu-id="ff4a9-256">IT or other department</span></span>|
| <span data-ttu-id="ff4a9-257">コンテンツ管理者とモデルの所有者</span><span class="sxs-lookup"><span data-stu-id="ff4a9-257">Content managers and model owners</span></span>| <span data-ttu-id="ff4a9-258">ユースケースを収集し、モデルを作成および適用する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-258">Gather use cases and create and apply models</span></span> | <span data-ttu-id="ff4a9-259">任意の部署</span><span class="sxs-lookup"><span data-stu-id="ff4a9-259">Any department</span></span>|
| <span data-ttu-id="ff4a9-260">チャンピオン</span><span class="sxs-lookup"><span data-stu-id="ff4a9-260">Champions</span></span> | <span data-ttu-id="ff4a9-261">啓発のヘルプとオブジェクションの処理の管理</span><span class="sxs-lookup"><span data-stu-id="ff4a9-261">Help evangelize and manage objection handling</span></span> | <span data-ttu-id="ff4a9-262">任意の部署 (スタッフ)</span><span class="sxs-lookup"><span data-stu-id="ff4a9-262">Any department (staff)</span></span> |
| <span data-ttu-id="ff4a9-263">テナント管理者</span><span class="sxs-lookup"><span data-stu-id="ff4a9-263">Tenant administrator</span></span> | <span data-ttu-id="ff4a9-264">テナントレベルの設定を構成する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-264">Configure tenant-level settings</span></span> | <span data-ttu-id="ff4a9-265">IT 部門</span><span class="sxs-lookup"><span data-stu-id="ff4a9-265">IT department</span></span>|
| <span data-ttu-id="ff4a9-266">電源プラットフォーム管理者</span><span class="sxs-lookup"><span data-stu-id="ff4a9-266">Power Platform administrator</span></span>| <span data-ttu-id="ff4a9-267">Common data services 環境を構成する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-267">Configure common data services environment</span></span> | <span data-ttu-id="ff4a9-268">IT 部門</span><span class="sxs-lookup"><span data-stu-id="ff4a9-268">IT department</span></span>|

> [!Note]
> <span data-ttu-id="ff4a9-269">これらの各役割が展開中に満たされるようにすることをお勧めしますが、特定のソリューションの作業を開始するために、すべての役割が必要になるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-269">Though we recommend having each of these roles fulfilled throughout your rollout, you may find that you don't require them all to get started with your identified solution.</span></span>

## <a name="readiness-checklist"></a><span data-ttu-id="ff4a9-270">準備チェックリスト</span><span class="sxs-lookup"><span data-stu-id="ff4a9-270">Readiness checklist</span></span>

<span data-ttu-id="ff4a9-271">SharePoint の同期を実装するための準備をするには、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-271">To get ready for implementing SharePoint Syntex, you need to:</span></span>

![コンテンツを理解するための準備](../media/content-understanding/cu-adoption-readinesschecklist.png)

1. <span data-ttu-id="ff4a9-273">終了状態を計画する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-273">Plan the end state</span></span>
    - <span data-ttu-id="ff4a9-274">ドキュメントは、モデルを理解するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-274">Document understanding models are the means, not the end.</span></span>
    - <span data-ttu-id="ff4a9-275">抽出されたメタデータの価値を活用するための計画は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-275">Plan for harnessing the value of extracted metadata with:</span></span>
      - <span data-ttu-id="ff4a9-276">検索</span><span class="sxs-lookup"><span data-stu-id="ff4a9-276">Search</span></span>
      - <span data-ttu-id="ff4a9-277">フィルター処理と表示の書式設定</span><span class="sxs-lookup"><span data-stu-id="ff4a9-277">Filtering and view formatting</span></span>
      - <span data-ttu-id="ff4a9-278">コンプライアンス</span><span class="sxs-lookup"><span data-stu-id="ff4a9-278">Compliance</span></span>
      - <span data-ttu-id="ff4a9-279">オートメーション</span><span class="sxs-lookup"><span data-stu-id="ff4a9-279">Automation</span></span>
2. <span data-ttu-id="ff4a9-280">検出</span><span class="sxs-lookup"><span data-stu-id="ff4a9-280">Identify</span></span>
    - <span data-ttu-id="ff4a9-281">既存の情報アーキテクチャとコンテンツ管理機能の使用について理解します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-281">Understand existing information architecture and content management feature use.</span></span>
    - <span data-ttu-id="ff4a9-282">既存のコンテンツタイプはモデルの適切な候補ですか。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-282">Are any existing content types good candidates for models?</span></span>
    - <span data-ttu-id="ff4a9-283">メタデータによってどのような既存のプロセスが改善されますか。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-283">What existing processes would be improved by metadata?</span></span>
3. <span data-ttu-id="ff4a9-284">デザイン</span><span class="sxs-lookup"><span data-stu-id="ff4a9-284">Design</span></span>
    - <span data-ttu-id="ff4a9-285">情報アーキテクチャ、管理されたメタデータ、およびコンテンツタイプへのアプローチを設計する</span><span class="sxs-lookup"><span data-stu-id="ff4a9-285">Design your approach to information architecture, managed metadata and content types</span></span>
    - <span data-ttu-id="ff4a9-286">定義、作成、管理のプロセスを設計します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-286">Design the process for definition, creation, management.</span></span>

## <a name="engage-your-organization"></a><span data-ttu-id="ff4a9-287">組織の参加</span><span class="sxs-lookup"><span data-stu-id="ff4a9-287">Engage your organization</span></span>

1. <span data-ttu-id="ff4a9-288">利害関係者を特定し、シナリオを確認し、プロジェクト計画を策定します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-288">Identify stake holders, confirm scenarios, and develop project plan.</span></span>
1. <span data-ttu-id="ff4a9-289">設定を構成し、ライセンスを適用します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-289">Configure settings and apply licenses.</span></span>
1. <span data-ttu-id="ff4a9-290">認識とトレーニングを開始し、採用エキスパートを開始します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-290">Begin awareness and training – Recruit Champions.</span></span>
1. <span data-ttu-id="ff4a9-291">段階的にロールアウトします。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-291">Roll out in stages.</span></span>  
1. <span data-ttu-id="ff4a9-292">フィードバックを収集し、反復処理を行います。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-292">Gather feedback and iterate.</span></span>
1. <span data-ttu-id="ff4a9-293">必要に応じて、AI ビルダークレジットについては、使用量が増加します。</span><span class="sxs-lookup"><span data-stu-id="ff4a9-293">As usage grows plan for any AI Builder credits as needed.</span></span>