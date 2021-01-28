---
title: ドキュメント理解とフォーム処理モデルの違い
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
localization_priority: Priority
description: ドキュメント理解とフォーム処理モデルの主な違いについて説明します
ms.openlocfilehash: f57d220eb77a783de5ac352f3cf684364252a163
ms.sourcegitcommit: 162c01dfaa2fdb3225ce4c24964c1065ce22ed5d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2021
ms.locfileid: "49975879"
---
# <a name="difference-between-document-understanding-and-form-processing-models"></a><span data-ttu-id="56ee5-103">ドキュメント理解とフォーム処理モデルの違い</span><span class="sxs-lookup"><span data-stu-id="56ee5-103">Difference between document understanding and form processing models</span></span> 


<span data-ttu-id="56ee5-104">Microsoft SharePoint Syntex のコンテンツを理解すると、SharePoint ドキュメントライブラリにアップロードされたドキュメントを識別および分類し、各ファイルから関連情報を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="56ee5-104">Content understanding in Microsoft SharePoint Syntex allows you to identify and classify documents that are uploaded to SharePoint document libraries, and extract relevant information from each file.</span></span>  <span data-ttu-id="56ee5-105">たとえば、ファイルが SharePoint ドキュメントライブラリにアップロードされると、*発注書* として識別されたすべてのファイルがそのように分類され、カスタム ドキュメント ライブラリ ビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="56ee5-105">For example, as files are uploaded to a SharePoint document library, all files that are identified as *Purchase Orders* are classified as such, and then displayed in a custom document library view.</span></span> <span data-ttu-id="56ee5-106">さらに、各ファイルから特定の情報 (*PO番号* や *合計* など) を取得して、ドキュメントライブラリビューの列として表示できます。</span><span class="sxs-lookup"><span data-stu-id="56ee5-106">Additionally, you can pull specific information from each file (for example, *PO Number* and *Total*) and display it as a column in your document library view.</span></span> 

<span data-ttu-id="56ee5-107">コンテンツの理解により、必要な情報を特定して抽出するための *モデル* を作成できます。</span><span class="sxs-lookup"><span data-stu-id="56ee5-107">Content understanding lets you create *models* to identify and extract the information you need.</span></span> <span data-ttu-id="56ee5-108">モデルは、検索、ビジネスプロセス、コンプライアンス、およびその他の多くのビジネス問題の解決を支援する上で価値があります。</span><span class="sxs-lookup"><span data-stu-id="56ee5-108">Models have value in helping to resolve business issues for search, business processes, compliance, and many others.</span></span>

<span data-ttu-id="56ee5-109">使用できるモデルタイプは次の 2 つです。</span><span class="sxs-lookup"><span data-stu-id="56ee5-109">There are two model types that you can use:</span></span>

- [<span data-ttu-id="56ee5-110">ドキュメント理解モデル</span><span class="sxs-lookup"><span data-stu-id="56ee5-110">Document understanding models</span></span>](document-understanding-overview.md)
- [<span data-ttu-id="56ee5-111">フォーム処理モデル</span><span class="sxs-lookup"><span data-stu-id="56ee5-111">Form processing models</span></span>](form-processing-overview.md)

<span data-ttu-id="56ee5-112">どちらのモデルも一般的に同じ目的で使用されますが、以下に示す主な違いは、どちらを使用できるかに影響します。</span><span class="sxs-lookup"><span data-stu-id="56ee5-112">While both models are generally used for the same purpose, the key differences listed below affect which ones you can use.</span></span>

> [!NOTE]
> <span data-ttu-id="56ee5-113">フォーム処理とドキュメント理解シナリオの例の詳細については、「[SharePoint Syntex の導入: 概要](https://docs.microsoft.com/microsoft-365/contentunderstanding/adoption-getstarted#form-processing-scenario-example)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56ee5-113">See the [SharePoint Syntex adoption: Get started guide](https://docs.microsoft.com/microsoft-365/contentunderstanding/adoption-getstarted#form-processing-scenario-example) for more information about form processing and document understanding scenario examples.</span></span>


## <a name="structured-versus-unstructured-and-semi-structured-content"></a><span data-ttu-id="56ee5-114">構造化コンテンツと非構造化コンテンツおよび半構造化コンテンツ</span><span class="sxs-lookup"><span data-stu-id="56ee5-114">Structured versus unstructured and semi-structured content</span></span>

<span data-ttu-id="56ee5-115">ドキュメント理解モデルを使用して、文字や契約書などの非構造化ドキュメントからデータを識別して抽出します。抽出するテキスト エンティティは、ドキュメントの文または特定の領域にあります。</span><span class="sxs-lookup"><span data-stu-id="56ee5-115">Use document understanding models to identify and extract data from unstructured documents, such as letters or contracts, where the text entities you want to extract is in sentences or specific regions of the document.</span></span> <span data-ttu-id="56ee5-116">たとえば、非構造化ドキュメントは、さまざまな方法で記述できる契約更新レターである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="56ee5-116">For example, an unstructured document could be a contract renewal letter that can be written in different ways.</span></span> <span data-ttu-id="56ee5-117">ただし、情報は各契約更新ドキュメントの本文に一貫して存在します。たとえば、*サービス開始日の* テキスト文字列の後に実際の日付が続きます。</span><span class="sxs-lookup"><span data-stu-id="56ee5-117">However, information exists consistently in the body of each contract renewal document, such as the text string *Service start date of* followed by an actual date.</span></span>

<span data-ttu-id="56ee5-118">フォーム処理モデルを使用してファイルを識別し、フォームや請求書などの構造化または半構造化されたドキュメントからデータを抽出します。</span><span class="sxs-lookup"><span data-stu-id="56ee5-118">Use form processing models to identify files and extract data from structured or semi-structured documents, such as forms or invoices.</span></span> <span data-ttu-id="56ee5-119">フォーム処理モデルは、サンプル ドキュメントからフォームのレイアウトを理解し、似ている場所から抽出する必要のあるデータを探すようにトレーニングされています。</span><span class="sxs-lookup"><span data-stu-id="56ee5-119">Form processing models are trained to understand the layout of your form from example documents, and learn to look for the data you need to extract from similar locations.</span></span> <span data-ttu-id="56ee5-120">フォームは通常、エンティティが同じ場所に配置されている、より構造化されたレイアウトを持っています (たとえば、納税申告での社会保障番号など)。</span><span class="sxs-lookup"><span data-stu-id="56ee5-120">Forms usually have a more structured layout where entities are in the same location (for example, a social security number in a tax form).</span></span>

> [!NOTE]
> <span data-ttu-id="56ee5-121">ドキュメント理解モデルを作成したり、SharePoint ドキュメントライブラリに適用したりするには、コンテンツ センター サイトへのアクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="56ee5-121">You must have access to a content center site to create a document understanding model or to apply one to a SharePoint document library.</span></span> 


## <a name="where-models-are-created"></a><span data-ttu-id="56ee5-122">モデルが作成された場所</span><span class="sxs-lookup"><span data-stu-id="56ee5-122">Where models are created</span></span>

<span data-ttu-id="56ee5-123">ドキュメント理解モデルは、SharePoint コンテンツ センター サイトで作成および管理されます。</span><span class="sxs-lookup"><span data-stu-id="56ee5-123">Document understanding models are created and managed in a SharePoint content center site.</span></span> 

> [!NOTE]
> <span data-ttu-id="56ee5-124">入力ドキュメントの詳細については、[フォーム処理モデルの要件と制限](https://docs.microsoft.com/ai-builder/form-processing-model-requirements)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56ee5-124">For more information about input documents, see [Form processing model requirements and limitations](https://docs.microsoft.com/ai-builder/form-processing-model-requirements).</span></span> 

<span data-ttu-id="56ee5-125">フォーム処理モデルは PowerApps [AI ビルダー](https://docs.microsoft.com/ai-builder/overview)で作成されますが、作成は SharePoint ドキュメント ライブラリから直接開始されます。</span><span class="sxs-lookup"><span data-stu-id="56ee5-125">Form processing models are created in PowerApps [AI Builder](https://docs.microsoft.com/ai-builder/overview), but the creation starts directly from a SharePoint document library.</span></span> <span data-ttu-id="56ee5-126">ドキュメント ライブラリでは、ユーザーがそのドキュメントのためにフォーム処理モデルを作成する前に、フォーム処理モデルの作成を有効にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="56ee5-126">A document library must have form processing model creation enabled before a user can create a form processing model for it.</span></span> <span data-ttu-id="56ee5-127">管理者は、コンテンツの理解の管理設定でフォーム処理モデルの作成を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="56ee5-127">Admins can enable form processing model creation in the content understanding admin settings.</span></span> <span data-ttu-id="56ee5-128">フォーム処理モデルは、ファイルがドキュメント ライブラリにアップロードされるときに、PowerAutomate フローを使用してファイルを処理します。</span><span class="sxs-lookup"><span data-stu-id="56ee5-128">Form processing models use PowerAutomate flows to process files when they're uploaded to the document library.</span></span>

<span data-ttu-id="56ee5-129">ドキュメント理解モデルを作成するときは、SharePoint コンテンツタイプギャラリーに保存される新しい [SharePoint コンテンツ タイプ](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978)を作成します。</span><span class="sxs-lookup"><span data-stu-id="56ee5-129">When you create a document understanding model, you create a new [SharePoint content type](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978) that is saved to the SharePoint Content Types gallery.</span></span> <span data-ttu-id="56ee5-130">または、必要に応じて、既存のコンテンツタイプを使用してモデルを定義できます。</span><span class="sxs-lookup"><span data-stu-id="56ee5-130">Or you can use existing content types to define your model if needed.</span></span>

<span data-ttu-id="56ee5-131">フォーム処理モデルは、新しい [SharePoint コンテンツ タイプ](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978)も作成し、SharePoint コンテンツ タイプ ギャラリーにも保存されます。</span><span class="sxs-lookup"><span data-stu-id="56ee5-131">Form processing models also create new [SharePoint content types](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978), and are also stored in the SharePoint Content Types gallery.</span></span>

## <a name="where-they-can-be-applied"></a><span data-ttu-id="56ee5-132">適用可能な場所</span><span class="sxs-lookup"><span data-stu-id="56ee5-132">Where they can be applied</span></span>

<span data-ttu-id="56ee5-133">アクセスできる SharePoint ドキュメント ライブラリにドキュメント理解モデルを適用できます。</span><span class="sxs-lookup"><span data-stu-id="56ee5-133">You can apply document understanding models to SharePoint document libraries that you have access to.</span></span> <span data-ttu-id="56ee5-134">コンテンツ センターを使用してドキュメント理解モデルを作成し、それをさまざまなドキュメント ライブラリに適用できます。</span><span class="sxs-lookup"><span data-stu-id="56ee5-134">Use the content center to create a document understanding model, and apply it to different document libraries.</span></span> <span data-ttu-id="56ee5-135">コンテンツ センターでは、ドキュメント理解モデルの使用方法と適用できる場所をより集中的に制御できます。</span><span class="sxs-lookup"><span data-stu-id="56ee5-135">The content center gives you a more central control for how document understanding models are used and where they're applied.</span></span> <span data-ttu-id="56ee5-136">この情報はコンテンツセンターにもロールアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="56ee5-136">Note this information must also roll up to a content center.</span></span>

<span data-ttu-id="56ee5-137">現在、フォーム処理モデルは、モデルを作成した SharePoint ドキュメント ライブラリにのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="56ee5-137">Form processing models can currently only be applied to the SharePoint document library from which you created them.</span></span> <span data-ttu-id="56ee5-138">これにより、サイトにアクセスできるライセンス付与済みのユーザーは、フォーム処理モデルを作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="56ee5-138">This allows licensed users with access to the site to create a form processing model.</span></span> <span data-ttu-id="56ee5-139">管理者は、SharePoint ドキュメントライブラリでフォーム処理を有効にして、ライセンス付与済みのユーザーが使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="56ee5-139">Note that an admin needs to enable form processing on a SharePoint document library for it to be available to licensed users.</span></span>

 ## <a name="see-also"></a><span data-ttu-id="56ee5-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="56ee5-140">See Also</span></span>
[<span data-ttu-id="56ee5-141">トレーニング: AI ビルダーを使用してビジネスの実績を高める</span><span class="sxs-lookup"><span data-stu-id="56ee5-141">Training: Improve business performance with AI Builder</span></span>](https://docs.microsoft.com/learn/paths/improve-business-performance-ai-builder/?source=learn)



[<span data-ttu-id="56ee5-142">ドキュメントの理解の概要</span><span class="sxs-lookup"><span data-stu-id="56ee5-142">Document understanding overview</span></span>](document-understanding-overview.md)

[<span data-ttu-id="56ee5-143">フォーム処理の概要</span><span class="sxs-lookup"><span data-stu-id="56ee5-143">Form processing overview</span></span>](form-processing-overview.md)

[<span data-ttu-id="56ee5-144">SharePoint Syntex の概要</span><span class="sxs-lookup"><span data-stu-id="56ee5-144">Introduction to SharePoint Syntex</span></span>](index.md)
