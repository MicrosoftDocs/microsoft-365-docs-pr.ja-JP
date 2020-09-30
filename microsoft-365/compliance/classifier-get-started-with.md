---
title: トレーニング可能な分類子の使用を開始する (プレビュー)
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Microsoft 365 の分類子は、さまざまな種類のコンテンツを認識するためにトレーニングできるツールです。そのためのサンプルを参照してください。 この記事では、カスタム分類子を作成してトレーニングする方法と、それらを再トレーニングして精度を向上させる方法について説明します。
ms.openlocfilehash: fd6bc68a8bc373d9d02e23b73971b28ce8761cd9
ms.sourcegitcommit: fdb5f9d865037c0ae23aae34a5c0f06b625b2f69
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2020
ms.locfileid: "48132371"
---
# <a name="get-started-with-trainable-classifiers-preview"></a><span data-ttu-id="1f4d6-104">トレーニング可能な分類子の使用を開始する (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="1f4d6-104">Get started with trainable classifiers (preview)</span></span>

<span data-ttu-id="1f4d6-105">Microsoft 365 trainable クラシファイアは、さまざまな種類のコンテンツを認識するためにトレーニングできるツールです。このツールを使用して、さまざまな種類のコンテンツを確認できます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-105">A Microsoft 365 trainable classifier is a tool you can train to recognize various types of content by giving it samples to look at.</span></span> <span data-ttu-id="1f4d6-106">トレーニングを受けた後、それを使用して、Office の秘密度ラベル、通信コンプライアンスポリシー、および保持ラベルポリシーのアプリケーションの項目を識別できます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-106">Once trained, you can use it to identify item for application of Office sensitivity labels, Communications compliance policies, and retention label policies.</span></span>

<span data-ttu-id="1f4d6-107">最初にカスタム trainable 分類子を作成するには、人間が選択され、カテゴリに対して明確に一致するサンプルを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-107">Creating a custom trainable classifier first involves giving it samples that are human picked and positively match the category.</span></span> <span data-ttu-id="1f4d6-108">その後、それらを処理した後で、正と負の両方のサンプルを混在させて予測する分類子機能をテストします。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-108">Then, after it has processed those, you test the classifiers ability to predict by giving it a mix of positive and negative samples.</span></span> <span data-ttu-id="1f4d6-109">この記事では、ユーザー設定の分類子を作成してトレーニングする方法、およびユーザー設定の trainable 分類子と事前に分類された分類子のパフォーマンスを改善する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-109">This article shows you how to create and train a custom classifier and how to improve the performance of custom trainable classifiers and pre-trained classifiers over their lifetime through retraining.</span></span>

<span data-ttu-id="1f4d6-110">分類子のさまざまな種類の詳細については、「 [trainable 分類子の概要 (プレビュー)](classifier-learn-about.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-110">To learn more about the different types of classifiers, see [Learn about trainable classifiers (preview)](classifier-learn-about.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1f4d6-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="1f4d6-111">Prerequisites</span></span>

### <a name="licensing-requirements"></a><span data-ttu-id="1f4d6-112">ライセンスの要件</span><span class="sxs-lookup"><span data-stu-id="1f4d6-112">Licensing requirements</span></span>

<span data-ttu-id="1f4d6-113">分類子は、Microsoft 365 E5 または E5 準拠の機能です。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-113">Classifiers are a Microsoft 365 E5, or E5 Compliance feature.</span></span> <span data-ttu-id="1f4d6-114">それらを使用するには、これらのサブスクリプションのいずれかが必要です。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-114">You must have one of these subscriptions to make use of them.</span></span>

### <a name="permissions"></a><span data-ttu-id="1f4d6-115">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="1f4d6-115">Permissions</span></span>

<span data-ttu-id="1f4d6-116">UI の分類子にアクセスするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-116">To access classifiers in the UI:</span></span> 

- <span data-ttu-id="1f4d6-117">グローバル管理者は、カスタム分類子を作成するためにテナントを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-117">the Global admin needs to opt in for the tenant to create custom classifiers</span></span>
- <span data-ttu-id="1f4d6-118">分類子を教育するには、コンプライアンス管理者ロールまたはコンプライアンスデータ管理者が必要です。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-118">the Compliance admin role or Compliance Data Administrator is required to train a classifier</span></span>

<span data-ttu-id="1f4d6-119">次のシナリオでは、分類子を使用するために、以下のアクセス許可を持つアカウントが必要になります。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-119">You'll need accounts with these permissions to use classifiers in these scenarios:</span></span>

- <span data-ttu-id="1f4d6-120">保持ラベルポリシーシナリオ: レコード管理および保持管理の役割</span><span class="sxs-lookup"><span data-stu-id="1f4d6-120">Retention label policy scenario: Record Management and Retention Management roles</span></span> 
- <span data-ttu-id="1f4d6-121">機密ラベルポリシーのシナリオ: セキュリティ管理者、コンプライアンス管理者、コンプライアンスデータ管理者</span><span class="sxs-lookup"><span data-stu-id="1f4d6-121">Sensitivity label policy scenario: Security Administrator, Compliance Administrator, Compliance Data Administrator</span></span>
- <span data-ttu-id="1f4d6-122">コミュニケーションコンプライアンスポリシーのシナリオ: Insider リスク管理管理者、監督レビュー管理者</span><span class="sxs-lookup"><span data-stu-id="1f4d6-122">Communication compliance policy scenario: Insider Risk Management Admin, Supervisory Review Administrator</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="1f4d6-123">既定では、カスタムの分類子を作成したユーザーのみが、その分類子によって行われた予測を教育およびレビューすることができます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-123">By default, only the user who creates a custom classifier can train and review predictions made by that classifier.</span></span> <span data-ttu-id="1f4d6-124">他のユーザーが分類子予測をトレーニングおよびレビューできるようにする場合は、「 [他のユーザーにトレーニングとレビューの権限を付与](#give-others-train-and-review-rights)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-124">If you want others to be able to train and review classifier predictions, see [Give others train and review rights](#give-others-train-and-review-rights).</span></span>

## <a name="prepare-for-a-custom-trainable-classifier"></a><span data-ttu-id="1f4d6-125">カスタム trainable 分類子の準備</span><span class="sxs-lookup"><span data-stu-id="1f4d6-125">Prepare for a custom trainable classifier</span></span> 

<span data-ttu-id="1f4d6-126">事前に説明する前に、カスタムの trainable 分類子を作成するために必要なことを理解しておくと役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-126">It's helpful to understand what's involved in creating a custom trainable classifier before you dive in.</span></span> 

### <a name="timeline"></a><span data-ttu-id="1f4d6-127">タイムライン</span><span class="sxs-lookup"><span data-stu-id="1f4d6-127">Timeline</span></span>

<span data-ttu-id="1f4d6-128">このタイムラインには、trainable 分類子の展開サンプルが反映されています。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-128">This timeline reflects a sample deployment of trainable classifiers.</span></span>

![trainable-クラシファイア-タイムライン](../media/trainable-classifier-deployment-timeline_border.png)

> [!TIP]
> <span data-ttu-id="1f4d6-130">Trainable 分類子では、最初にオプトインが必要です。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-130">Opt-in is required the first time for trainable classifiers.</span></span> <span data-ttu-id="1f4d6-131">Microsoft 365 で組織のコンテンツのベースライン評価を完了するには、12日間かかります。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-131">It takes twelve days for Microsoft 365 to complete a baseline evaluation of your organizations content.</span></span> <span data-ttu-id="1f4d6-132">グローバル管理者に連絡して、オプトインプロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-132">Contact your global administrator to kick off the opt-in process.</span></span>

### <a name="overall-workflow"></a><span data-ttu-id="1f4d6-133">全体的なワークフロー</span><span class="sxs-lookup"><span data-stu-id="1f4d6-133">Overall workflow</span></span>

<span data-ttu-id="1f4d6-134">カスタム trainable 分類子を作成する全体的なワークフローの詳細については、「 [customer trainable 分類子を作成するためのプロセスフロー](classifier-learn-about.md#process-flow-for-creating-custom-classifiers) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-134">To understand more about the overall workflow of creating custom trainable classifiers, see [Process flow for creating customer trainable classifiers](classifier-learn-about.md#process-flow-for-creating-custom-classifiers)</span></span>

### <a name="seed-content"></a><span data-ttu-id="1f4d6-135">Seed コンテンツ</span><span class="sxs-lookup"><span data-stu-id="1f4d6-135">Seed content</span></span>

<span data-ttu-id="1f4d6-136">Trainable 分類子を個別に特定のカテゴリのコンテンツにする必要がある場合は、まず、カテゴリに含まれるコンテンツの種類の多くのサンプルを提示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-136">When you want a trainable classifier to independently and accurately identify an item as being in particular category of content, you first have to present it with many samples of the type of content that are in the category.</span></span> <span data-ttu-id="1f4d6-137">Trainable 分類子へのこのサンプルのフィードは、 *シード*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-137">This feeding of samples to the trainable classifier is known as *seeding*.</span></span> <span data-ttu-id="1f4d6-138">Seed コンテンツは人間が選択し、コンテンツのカテゴリを表すことを判断します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-138">Seed content is selected by a human and is judged to represent the category of content.</span></span>

> [!TIP]
> <span data-ttu-id="1f4d6-139">少なくとも50の正のサンプルと最大500が必要です。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-139">You need to have at least 50 positive samples and as many as 500.</span></span> <span data-ttu-id="1f4d6-140">Trainable 分類子は、最新の作成済みサンプル (ファイル作成日時スタンプ) を500まで処理します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-140">The trainable classifier will process up to the 500 most recent created samples (by file created date/time stamp).</span></span> <span data-ttu-id="1f4d6-141">指定したサンプル数が多いほど、分類子が実行する予測がより正確になります。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-141">The more samples you provide, the more accurate the predictions the classifier will make.</span></span>

### <a name="testing-content"></a><span data-ttu-id="1f4d6-142">コンテンツのテスト</span><span class="sxs-lookup"><span data-stu-id="1f4d6-142">Testing content</span></span>

<span data-ttu-id="1f4d6-143">Trainable クラシファイアが、予測モデルを構築するのに十分な正のサンプルを処理したら、その分類をテストして、分類項目に一致する項目と、それに一致しないアイテムを正しく区別できるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-143">Once the trainable classifier has processed enough positive samples to build a prediction model, you need to test the predictions it makes to see if the classifier can correctly distinguish between items that match the category and items that don't.</span></span> <span data-ttu-id="1f4d6-144">これを行うには、より大きなユーザーが選択したコンテンツセットを別のものにします。これは、カテゴリとサンプルに分類される必要のあるサンプルで構成されます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-144">You do this by feeding it another, hopefully larger, set of human picked content that consists of samples that should fall into the category and samples that won't.</span></span> <span data-ttu-id="1f4d6-145">それらを処理した後、結果を手動で調べ、各予測が正しいかどうか、または確認できないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-145">Once it processes those, you manually go through the results and verify whether each prediction is correct, incorrect, or you aren't sure.</span></span> <span data-ttu-id="1f4d6-146">Trainable 分類子は、このフィードバックを使用して予測モデルを改善します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-146">The trainable classifier uses this feedback to improve its prediction model.</span></span>

> [!TIP]
> <span data-ttu-id="1f4d6-147">最良の結果を得るには、正と負の一致が均等に分配されたテストサンプルセットに、少なくとも200のアイテムが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-147">For best results, have at least 200 items in your test sample set with an even distribution of positive and negative matches.</span></span>

## <a name="how-to-create-a-trainable-classifier"></a><span data-ttu-id="1f4d6-148">Trainable 分類子を作成する方法</span><span class="sxs-lookup"><span data-stu-id="1f4d6-148">How to create a trainable classifier</span></span>

1. <span data-ttu-id="1f4d6-149">50-500 の seed コンテンツ項目の間で収集します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-149">Collect between 50-500 seed content items.</span></span> <span data-ttu-id="1f4d6-150">これらは、trainable 分類子が分類カテゴリに含まれるコンテンツの種類を厳密に表すサンプルである必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-150">These must be only samples that strongly represent the type of content you want the trainable classifier to positively identify as being in the classification category.</span></span> <span data-ttu-id="1f4d6-151">サポートされているファイルの種類については、「 [SharePoint Server での既定のクロール対象ファイル名拡張子および解析済みファイルの種類](https://docs.microsoft.com/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-151">See, [Default crawled file name extensions and parsed file types in SharePoint Server](https://docs.microsoft.com/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) for the supported file types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1f4d6-152">シードおよびテストサンプルアイテムは、暗号化する必要があり、英語である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-152">The seed and test sample items must not be encrypted and they must be in English.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1f4d6-153">Seed セット内のアイテムがカテゴリの **強力な** 例であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-153">Make sure the items in your seed set are **strong** examples of the category.</span></span> <span data-ttu-id="1f4d6-154">Trainable 分類子は、最初にそのモデルをシードしたものに基づいてモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-154">The trainable classifier initially builds its model based on what you seed it with.</span></span> <span data-ttu-id="1f4d6-155">この分類子は、すべてのシードサンプルが強力なものであることを前提としていますが、サンプルがカテゴリに対して弱いまたは否定的一致であるかどうかを知ることはできません。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-155">The classifier assumes all seed samples are strong positives and has no way of knowing if a sample is a weak or negative match to the category.</span></span>

2. <span data-ttu-id="1f4d6-156">Seed *コンテンツを保持する*専用の SharePoint Online フォルダーにシードコンテンツを配置します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-156">Place the seed content in a SharePoint Online folder that is dedicated to holding *the seed content only*.</span></span> <span data-ttu-id="1f4d6-157">サイト、ライブラリ、およびフォルダーの URL をメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-157">Make note of the site, library, and folder URL.</span></span>

> [!TIP]
> <span data-ttu-id="1f4d6-158">Seed データ用の新しいサイトとフォルダーを作成する場合は、そのシードデータを使用する trainable 分類子を作成する前に、少なくとも1時間、その場所にインデックスを作成するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-158">If you create a new site and folder for your seed data, allow at least an hour for that location to be indexed before creating the trainable classifier that will use that seed data.</span></span>

3. <span data-ttu-id="1f4d6-159">コンプライアンス管理者またはセキュリティ管理者の役割アクセスを使用して microsoft 365 コンプライアンスセンターにサインインし、 **microsoft 365 コンプライアンスセンター**または**microsoft 365 セキュリティセンター**の  >  **データ分類**を開く</span><span class="sxs-lookup"><span data-stu-id="1f4d6-159">Sign in to Microsoft 365 compliance center with compliance admin or security admin role access and open **Microsoft 365 compliance center** or **Microsoft 365 security center** > **Data classification**</span></span>

4. <span data-ttu-id="1f4d6-160">[ **Trainable 分類子** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-160">Choose the **Trainable classifiers** tab.</span></span>

5. <span data-ttu-id="1f4d6-161">[ **Create trainable クラシファイア**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-161">Choose **Create trainable classifier**.</span></span>

6. <span data-ttu-id="1f4d6-162">`Name` `Description` この trainable 分類子で識別するアイテムのカテゴリのフィールドに適切な値を入力します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-162">Fill in appropriate values for the `Name`, and `Description` fields of the category of items you want this trainable classifier to identify.</span></span>

7. <span data-ttu-id="1f4d6-163">手順2で、seed コンテンツサイトの SharePoint Online サイト、ライブラリ、およびフォルダーの URL を選択します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-163">Pick the SharePoint Online site, library, and folder URL for the seed content site from step 2.</span></span> <span data-ttu-id="1f4d6-164">[] を選択 `Add` します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-164">Choose `Add`.</span></span>

8. <span data-ttu-id="1f4d6-165">設定を確認し、[] を選択し `Create trainable classifier` ます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-165">Review the settings and choose `Create trainable classifier`.</span></span>

9. <span data-ttu-id="1f4d6-166">24時間以内、trainable クラシファイアはシードデータを処理し、予測モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-166">Within 24 hours the trainable classifier will process the seed data and build a prediction model.</span></span> <span data-ttu-id="1f4d6-167">分類子の状態は、 `In progress` シードデータを処理している間になります。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-167">The classifier status is `In progress` while it processes the seed data.</span></span> <span data-ttu-id="1f4d6-168">分類子がシードデータの処理を完了すると、状態はに変わり `Need test items` ます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-168">When the classifier is finished processing the seed data, the status changes to `Need test items`.</span></span>

10. <span data-ttu-id="1f4d6-169">分類子を選択することによって、[詳細] ページを表示できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-169">You can now view the details page by choosing the classifier.</span></span>


![テストの準備が整った trainable クラシファイア](../media/classifier-trainable-ready-to-test-detail.png)

11. <span data-ttu-id="1f4d6-171">最良の結果を得るために、少なくとも200のテストコンテンツ項目 (1万 max) を収集します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-171">Collect at least 200 test content items (10,000 max) for best results.</span></span> <span data-ttu-id="1f4d6-172">これらのアイテムは、強力な陽性、強力なネガ、およびそれらの性質上の明確にわかりにくい項目を組み合わせたものにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-172">These should be a mix of items that are strong positives, strong negatives and some that are a little less obvious in their nature.</span></span> <span data-ttu-id="1f4d6-173">サポートされているファイルの種類については、「 [SharePoint Server での既定のクロール対象ファイル名拡張子および解析済みファイルの種類](https://docs.microsoft.com/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-173">See, [Default crawled file name extensions and parsed file types in SharePoint Server](https://docs.microsoft.com/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) for the supported file types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1f4d6-174">サンプルアイテムは、暗号化する必要がなく、英語でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-174">The sample items must not be encrypted and they must be in English.</span></span>

12. <span data-ttu-id="1f4d6-175">テストコンテンツ *のみ*を保持する専用の SharePoint Online フォルダーにテストコンテンツを配置します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-175">Place the test content in a SharePoint Online folder that is dedicated to holding *the test content only*.</span></span> <span data-ttu-id="1f4d6-176">SharePoint Online のサイト、ライブラリ、およびフォルダーの URL をメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-176">Make note of the SharePoint Online site, library, and folder URL.</span></span>

> [!TIP]
> <span data-ttu-id="1f4d6-177">テストデータ用に新しいサイトとフォルダーを作成する場合は、そのシードデータを使用する trainable 分類子を作成する前に、少なくとも1時間、その場所にインデックスを設定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-177">If you create a new site and folder for your test data, allow at least an hour for that location to be indexed before creating the trainable classifier that will use that seed data.</span></span>

13. <span data-ttu-id="1f4d6-178">[] を選択 `Add items to test` します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-178">Choose `Add items to test`.</span></span>

14. <span data-ttu-id="1f4d6-179">手順12からテストコンテンツサイトの SharePoint Online サイト、ライブラリ、およびフォルダーの URL を選びます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-179">Pick the SharePoint Online site, library, and folder URL for the test content site from step 12.</span></span> <span data-ttu-id="1f4d6-180">[] を選択 `Add` します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-180">Choose `Add`.</span></span>

15. <span data-ttu-id="1f4d6-181">を選択してウィザードを終了し `Done` ます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-181">Finish the wizard by choosing `Done`.</span></span> <span data-ttu-id="1f4d6-182">Trainable の分類子は、テストファイルの処理に最大1時間かかります。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-182">Your trainable classifier will take up to an hour to process the test files.</span></span>

16. <span data-ttu-id="1f4d6-183">Trainable クラシファイアがテストファイルの処理を完了すると、詳細ページの状態はに変わり `Ready to review` ます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-183">When the trainable classifier is done processing your test files, the status on the details page will change to `Ready to review`.</span></span> <span data-ttu-id="1f4d6-184">テストサンプルサイズを増やす必要がある場合は、 `Add items to test` trainable クラシファイアが追加のアイテムを処理することを選択して許可します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-184">If you need to increase the test sample size, choose `Add items to test` and allow the trainable classifier to process the additional items.</span></span>

![スクリーンショットを確認する準備ができました](../media/classifier-trainable-ready-to-review-detail.png)

17. <span data-ttu-id="1f4d6-186">[ `Tested items to review` タブ] を選択してアイテムを確認します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-186">Choose `Tested items to review` tab to review items.</span></span>

18. <span data-ttu-id="1f4d6-187">Microsoft 365 は、一度に30個のアイテムを提示します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-187">Microsoft 365 will present 30 items at a time.</span></span> <span data-ttu-id="1f4d6-188">それらを確認し、 `We predict this item is "Relevant". Do you agree?` ボックスで、またはのどちらかを選択し `Yes` `No` `Not sure, skip to next item` ます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-188">Review them and in the `We predict this item is "Relevant". Do you agree?` box choose either `Yes` or `No` or `Not sure, skip to next item`.</span></span> <span data-ttu-id="1f4d6-189">モデル精度は30アイテムごとに自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-189">Model accuracy is automatically updated after every 30 items.</span></span>

![[アイテムの確認] ボックス](../media/classifier-trainable-review-detail.png)

19. <span data-ttu-id="1f4d6-191">*少なく*とも200のアイテムを確認します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-191">Review *at least* 200 items.</span></span> <span data-ttu-id="1f4d6-192">精度スコアが安定すると、[ **発行** ] オプションが使用可能になり、分類子の状態が表示され `Ready to use` ます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-192">Once the accuracy score has stabilized, the **publish** option will become available and the classifier status will say `Ready to use`.</span></span>

![精度スコアと発行の準備ができている](../media/classifier-trainable-review-ready-to-publish.png)

20. <span data-ttu-id="1f4d6-194">分類子を発行します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-194">Publish the classifier.</span></span>

21. <span data-ttu-id="1f4d6-195">公開されると、分類子は、[条件に基づいて、条件に基づいて [自動適用の保持ラベルポリシー](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) ] を使用して[Office の自動ラベル](apply-sensitivity-label-automatically.md)付けの条件として使用できるようになり[ます。](communication-compliance.md)</span><span class="sxs-lookup"><span data-stu-id="1f4d6-195">Once published your classifier will be available as a condition in [Office auto-labeling with sensitivity labels](apply-sensitivity-label-automatically.md), [auto-apply retention label policy based on a condition](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels) and in [Communication compliance](communication-compliance.md).</span></span>

## <a name="give-others-train-and-review-rights"></a><span data-ttu-id="1f4d6-196">他のユーザーにトレーニングおよびレビュー権限を付与する</span><span class="sxs-lookup"><span data-stu-id="1f4d6-196">Give others train and review rights</span></span>

<span data-ttu-id="1f4d6-197">この手順を使用して、ユーザー設定の trainable 分類子をトレーニング、レビュー、調整する権限を他のユーザーに付与します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-197">Use this procedure to give others permissions to train, review and tune your custom trainable classifier.</span></span>  
 
1. <span data-ttu-id="1f4d6-198">グローバル管理者または電子情報開示管理者は、分類子の作成者として、「 [connect To Security & コンプライアンスセンター PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell?view=exchange-ps&preserve-view=true)」の手順に従って、PowerShell を使用してコンプライアンスセンターに接続します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-198">As the creator of the classifier, a global admin or eDiscovery admin connect to the Compliance center using PowerShell using the procedures in [Connect to Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell?view=exchange-ps&preserve-view=true).</span></span>
2. <span data-ttu-id="1f4d6-199">次に示すコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-199">Run this command:</span></span>
```powershell
Add-ComplianceCaseMember -Case "<classifier name>" -Member "<user or role group>"
```
<span data-ttu-id="1f4d6-200">例: `Add-ComplianceCaseMember -Case "Financial Contract Classifier" -Member johnevans@contoso.com`</span><span class="sxs-lookup"><span data-stu-id="1f4d6-200">For example: `Add-ComplianceCaseMember -Case "Financial Contract Classifier" -Member johnevans@contoso.com`</span></span>

<span data-ttu-id="1f4d6-201">このコマンドは複数回実行して複数のユーザーを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-201">You can run this command multiple times to add multiple users.</span></span> <span data-ttu-id="1f4d6-202">Exchange Online Protection (EOP) の役割グループのみを追加でき、Azure の役割グループは追加できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1f4d6-202">Note that you can only add Exchange Online Protection (EOP) Role Groups and not Azure Role Groups.</span></span>