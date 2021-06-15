---
title: Microsoft SharePoint Syntex のモデルに秘密度ラベルを適用する
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
localization_priority: Priority
description: 秘密度ラベルを SharePoint Syntex のモデルに適用する方法について説明します。
ms.openlocfilehash: 799ab3fa0fcdc9af9d227428056d2cd7abeaf539
ms.sourcegitcommit: a05f61a291eb4595fa9313757a3815b7f217681d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2021
ms.locfileid: "52706722"
---
# <a name="apply-a-sensitivity-label-to-a-model-in-microsoft-sharepoint-syntex"></a><span data-ttu-id="2d440-103">Microsoft SharePoint Syntex のモデルに秘密度ラベルを適用する</span><span class="sxs-lookup"><span data-stu-id="2d440-103">Apply a sensitivity label to a model in Microsoft SharePoint Syntex</span></span>

<span data-ttu-id="2d440-104">Microsoft SharePoint Syntex のドキュメント理解モデルに[秘密度ラベル](../compliance/sensitivity-labels.md)を簡単に適用できます。</span><span class="sxs-lookup"><span data-stu-id="2d440-104">You can easily apply a [sensitivity label](../compliance/sensitivity-labels.md) to document understanding models in Microsoft SharePoint Syntex.</span></span> <span data-ttu-id="2d440-105">この機能は、フォーム処理モデルではまだ利用できません。</span><span class="sxs-lookup"><span data-stu-id="2d440-105">This feature isn't available yet for form processing models.</span></span>

<span data-ttu-id="2d440-106">秘密度ラベルを使用すると、モデルが識別するドキュメントに暗号化、共有、および条件付きアクセス ポリシーを適用できます。</span><span class="sxs-lookup"><span data-stu-id="2d440-106">Sensitivity labels let you apply encryption, sharing, and conditional access policies to the documents that your models identify.</span></span> <span data-ttu-id="2d440-107">たとえば、ドキュメント ライブラリにアップロードされた銀行口座番号やクレジット カード番号を含む財務書類をモデルで識別するだけでなく、それらに *暗号化* 秘密度ラベルを適用して、そのコンテンツにアクセスできるユーザーとそのコンテンツの使用方法を制限することも必要です。</span><span class="sxs-lookup"><span data-stu-id="2d440-107">For example, you want your model to not only identify any financial documents that contain bank account numbers or credit card numbers that are uploaded to your document library, but also to apply an *Encryption* sensitivity label to them to restrict who can access that content and how it can be used.</span></span>

<span data-ttu-id="2d440-108">モデルのホーム ページのモデル設定を使用して、既存の秘密度ラベルをモデルに適用できます。</span><span class="sxs-lookup"><span data-stu-id="2d440-108">You can apply a pre-existing sensitivity label to your model through your model settings on your model's home page.</span></span> <span data-ttu-id="2d440-109">モデル設定から選択できるようにするには、ラベルがすでに公開されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d440-109">The label must already be published to be available for selection from model settings.</span></span>

> [!Important]
> <span data-ttu-id="2d440-110">秘密度ラベルをドキュメント理解モデルに適用できるようにするには、秘密度ラベルを[作成して Microsoft 365 コンプライアンス センターで公開する](../business-video/create-sensitivity-labels.md)必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d440-110">For sensitivity labels to be available to apply to your document understanding models, they need to be [created and published in the Microsoft 365 Compliance Center](../business-video/create-sensitivity-labels.md).</span></span>

## <a name="add-a-sensitivity-label-to-a-document-understanding-model"></a><span data-ttu-id="2d440-111">秘密度ラベルをドキュメント理解モデルに追加する</span><span class="sxs-lookup"><span data-stu-id="2d440-111">Add a sensitivity label to a document understanding model</span></span>

1. <span data-ttu-id="2d440-112">モデルのホーム ページから、[**モデルの設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2d440-112">From the model home page, select **Model settings**.</span></span>

   ![[モデルの設定] オプションが強調表示された [モデル] ページのスクリーンショット。](../media/content-understanding/sensitivity-model-settings.png)

2. <span data-ttu-id="2d440-114">[**モデルの設定**] ウィンドウの [**コンプライアンス**] セクションで、[**秘密度ラベル**] メニューを選択して、モデルに適用できる秘密度ラベルのリストを表示します。</span><span class="sxs-lookup"><span data-stu-id="2d440-114">On **Model settings** pane, in the **Compliance** section, select the **Sensitivity label** menu to see a list of sensitivity labels that are available for you to apply to the model.</span></span>

   ![秘密度ラベル メニューが表示されている [モデルの設定] ウィンドウのスクリーンショット。](../media/content-understanding/sensitivity-model-settings-pane.png) 

3. <span data-ttu-id="2d440-116">モデルに適用する秘密度ラベルを選択し、[**保存**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2d440-116">Select the sensitivity label you want to apply to the model, and then select **Save**.</span></span>

<span data-ttu-id="2d440-117">モデルに秘密度ラベルを適用した後、次のものに適用できます。</span><span class="sxs-lookup"><span data-stu-id="2d440-117">After you apply the sensitivity label to your model, you can apply it to a:</span></span>

- <span data-ttu-id="2d440-118">新しいドキュメント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="2d440-118">New document library</span></span>
- <span data-ttu-id="2d440-119">モデルがすでに適用されているドキュメント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="2d440-119">Document library to which the model is already applied</span></span>
 
### <a name="apply-the-sensitivity-label-to-a-document-library-to-which-the-model-is-already-applied"></a><span data-ttu-id="2d440-120">モデルがすでに適用されているドキュメント ライブラリに秘密度ラベルを適用します</span><span class="sxs-lookup"><span data-stu-id="2d440-120">Apply the sensitivity label to a document library to which the model is already applied</span></span>

<span data-ttu-id="2d440-121">ドキュメント理解モデルがすでにドキュメント ライブラリに適用されている場合は、次の手順を実行して、秘密度ラベルの更新を同期し、ドキュメント ライブラリに適用できます。</span><span class="sxs-lookup"><span data-stu-id="2d440-121">If your document understanding model has already been applied to a document library, you can do the following to sync your sensitivity label update to apply it to the document library:</span></span>

1. <span data-ttu-id="2d440-122">モデル ホーム ページの [**このモデルのあるライブラリ**] セクションで、秘密度ラベルの更新を適用するドキュメント ライブラリを選択します。</span><span class="sxs-lookup"><span data-stu-id="2d440-122">On the model home page, in the **Libraries with this model** section, select the document library to which you want to apply the sensitivity label update.</span></span>

2. <span data-ttu-id="2d440-123">[**同期**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2d440-123">Select **Sync**.</span></span>

   ![[同期] が強調表示された [このモデルのあるライブラリ] セクションを示すスクリーンショット。](../media/content-understanding/sensitivity-libraries-sync.png)

<span data-ttu-id="2d440-125">更新を適用してモデルに同期した後、次の手順を実行して、更新が適用されたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="2d440-125">After you apply the update and sync it to your model, you can confirm that it has been applied by doing the following steps:</span></span>

1. <span data-ttu-id="2d440-126">コンテンツ センターの [**このモデルのあるライブラリ**] セクションで、更新したモデルが適用されたライブラリを選択します。</span><span class="sxs-lookup"><span data-stu-id="2d440-126">In the content center, in the **Libraries with this model** section, select the library to which your updated model was applied.</span></span> 

2. <span data-ttu-id="2d440-127">ドキュメント ライブラリ ビューで、情報アイコンを選択してモデルのプロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d440-127">In your document library view, select the information icon to check the model properties.</span></span>

3. <span data-ttu-id="2d440-128">[**アクティブモデル**] リストで、更新したモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="2d440-128">In the **Active models** list, select your updated model.</span></span>

4. <span data-ttu-id="2d440-129">[**秘密度ラベル**] セクションに、適用されている秘密度ラベルの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d440-129">In the **Sensitivity label** section, you'll see the name of the applied sensitivity label.</span></span>

<span data-ttu-id="2d440-130">ドキュメント ライブラリのモデルの表示ページに、新しい [**秘密度ラベル**] 列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d440-130">On your model's view page in your document library, a new **Sensitivity label** column will display.</span></span> <span data-ttu-id="2d440-131">モデルがそのコンテンツ タイプに属するものとして識別したファイルを分類し、それらをライブラリ ビューに一覧表示すると、[**秘密度ラベル**] 列には、モデルを通じてモデルに適用された秘密度ラベルの名前も表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d440-131">As your model classifies files it identifies as belonging to its content type and lists them in the library view, the **Sensitivity label** column will also display the name of the sensitivity label that has been applied to it through the model.</span></span>

<span data-ttu-id="2d440-132">たとえば、モデルが識別するすべての財務書類にも *暗号化* 秘密度ラベルが適用され、権限のないユーザーがアクセスするのを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="2d440-132">For example, all financial documents that your model identifies also will have the *Encryption* sensitivity label applied to them, preventing them from being accessed by unauthorized people.</span></span> <span data-ttu-id="2d440-133">権限のないユーザーがドキュメント ライブラリのファイルにアクセスしようとすると、適用されている秘密度ラベルのために許可されていないというエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d440-133">If an attempt is made to access the file from the document library by an unauthorized person, an error will display saying it isn't allowed because of the applied sensitivity label.</span></span>

<!---
## Add a sensitivity label to a form processing model

> [!Important]
> For sensitivity labels to be available to apply to your form processing model, they need to be [created and published in the Microsoft 365 Compliance Center](../business-video/create-sensitivity-labels.md).

You can either apply a sensitivity label to a form processing model when you are creating a model, or apply it to an existing model.

### Add a sensitivity label when you create a form processing model

1. When you [create a new form processing model](create-a-form-processing-model.md), select **Advanced settings**.

2. In **Advanced settings**, in the **Sensitivity label** section, select the menu and then select the sensitivity label you want to apply to the model.

3.  After you've completed your remaining model settings, select **Create** to build your model.

### Add a sensitivity label to an existing form processing model

You can add a sensitivity label to an existing form processing model in different ways:

- Through the **Automate** menu in the document library
- Through the **Active model** settings in the document library 

#### Add a sensitivity label to an existing form processing model through the Automate menu

You can add a sensitivity label to an existing form processing model that you own through the **Automate** menu in the document library in which the model is applied.

1. In your document library to which the form processing model is applied, select the **Automate** menu, select **AI Builder**, and then select **View form processing model details**.

2. On the **Model details** pane, in the **Sensitivity label** section, select the sensitivity label you want to apply. Then select **Save**.

#### Add a sensitivity label to an existing form processing model in the active model settings

You can add a sensitivity label to an existing form processing model that you own through the **Active model** settings in the document library in which the model is applied.

1. In the SharePoint document library in which the model is applied, select the **View active models** icon, and then select **View active models**.

2. In **Active models**, select the form processing model to which you want to apply the sensitivity label.

3. On the **Model details** pane, in the **Sensitivity label** section, select the sensitivity label you want to apply. Then select **Save**.

   > [!NOTE]
   > You must be the model owner for the **Model settings** pane to be editable. 
--->

## <a name="see-also"></a><span data-ttu-id="2d440-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d440-134">See also</span></span>

[<span data-ttu-id="2d440-135">保持ラベルを適用する</span><span class="sxs-lookup"><span data-stu-id="2d440-135">Apply a retention label</span></span>](apply-a-retention-label-to-a-model.md)

[<span data-ttu-id="2d440-136">分類子を作成する</span><span class="sxs-lookup"><span data-stu-id="2d440-136">Create a classifier</span></span>](create-a-classifier.md)

[<span data-ttu-id="2d440-137">抽出子を作成する</span><span class="sxs-lookup"><span data-stu-id="2d440-137">Create an extractor</span></span>](create-an-extractor.md)

[<span data-ttu-id="2d440-138">ドキュメント理解の概要</span><span class="sxs-lookup"><span data-stu-id="2d440-138">Document Understanding overview</span></span>](document-understanding-overview.md)