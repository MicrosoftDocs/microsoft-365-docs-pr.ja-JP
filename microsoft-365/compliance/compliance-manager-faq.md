---
title: Microsoft コンプライアンスマネージャーの FAQ
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Microsoft コンプライアンスマネージャーに関してよく寄せられる質問への回答を検索します。これにより、組織はリスク評価を簡略化および自動化できます。
ms.openlocfilehash: 3e1b6cdbcafd0cb4af4545cb258dab2ce082a2d8
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/22/2020
ms.locfileid: "48204449"
---
# <a name="compliance-manager-frequently-asked-questions"></a><span data-ttu-id="26088-103">コンプライアンスマネージャーのよく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="26088-103">Compliance Manager frequently asked questions</span></span>

## <a name="is-compliance-manager-and-compliance-score-the-same-thing-or-are-they-different"></a><span data-ttu-id="26088-104">コンプライアンスマネージャーとコンプライアンススコアが同じかどうか、または相違点</span><span class="sxs-lookup"><span data-stu-id="26088-104">Is Compliance Manager and Compliance Score the same thing, or are they different?</span></span>

<span data-ttu-id="26088-105">コンプライアンスマネージャーは、1つのソリューションだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="26088-105">There is now just one solution: Compliance Manager.</span></span> <span data-ttu-id="26088-106">このセクションでは、以下の基本的な概要から始まる移行手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="26088-106">This section walks you through the transition, starting with a basic overview below.</span></span> <span data-ttu-id="26088-107">また、次のセクションのいずれかに直接移動すると役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="26088-107">You may also find it helpful to jump directly to one of the following sections:</span></span>

- [<span data-ttu-id="26088-108">組織は、Microsoft Service Trust Portal にあるコンプライアンスマネージャー (クラシック版またはパブリックプレビュー版) を主に使用していました。</span><span class="sxs-lookup"><span data-stu-id="26088-108">Your organization primarily used Compliance Manager (either the classic or public preview versions), located in the Microsoft Service Trust Portal</span></span>](#your-organization-regularly-used-compliance-manger-in-the-service-trust-portal)

- [<span data-ttu-id="26088-109">お客様の組織では、Microsoft 365 コンプライアンスセンターにある、主にコンプライアンススコア (パブリックプレビュー) を使用していました。</span><span class="sxs-lookup"><span data-stu-id="26088-109">Your organization primarily used Compliance Score (public preview), located in the Microsoft 365 compliance center</span></span>](#your-organization-used-compliance-score-public-preview-in-the-microsoft-365-compliance-center)

- [<span data-ttu-id="26088-110">組織はコンプライアンスマネージャーを初めて使用する</span><span class="sxs-lookup"><span data-stu-id="26088-110">Your organization is new to Compliance Manager</span></span>](#youre-new-to-compliance-manager
)
#### <a name="the-basics"></a><span data-ttu-id="26088-111">基本事項</span><span class="sxs-lookup"><span data-stu-id="26088-111">The basics</span></span>

<span data-ttu-id="26088-112">Microsoft コンプライアンスマネージャーは、Microsoft Service Trust Portal の内部でコンプライアンス管理ソリューションとして開始されました。</span><span class="sxs-lookup"><span data-stu-id="26088-112">Microsoft Compliance Manager began as a compliance management solution inside the Microsoft Service Trust Portal.</span></span>  <span data-ttu-id="26088-113">コンプライアンスソリューションが Microsoft 365 コンプライアンスセンターに含まれている場合、この場所に対してよりユーザーフレンドリな設計を使用して、新しい経験を開発しました。</span><span class="sxs-lookup"><span data-stu-id="26088-113">As compliance solutions came into in the Microsoft 365 compliance center, we developed a new experience with a more user-friendly design for this location.</span></span> <span data-ttu-id="26088-114">コンプライアンススコアパブリックプレビューは、Microsoft 365 コンプライアンスセンター (2019 年11月) でリリースされました。</span><span class="sxs-lookup"><span data-stu-id="26088-114">Compliance Score public preview was released in the Microsoft 365 compliance center in November 2019.</span></span> <span data-ttu-id="26088-115">コンプライアンススコアコンプライアンスマネージャーと同じバックエンドを共有し、お客様が両方の場所で作業できるようにします。</span><span class="sxs-lookup"><span data-stu-id="26088-115">Compliance Score shared the same backend as Compliance Manager, allowing customers to work in both places.</span></span> <span data-ttu-id="26088-116">2019年11月以降、新機能を構築し、お客様からのフィードバックに応答したため、いくつかの更新プログラムをリリースしました。</span><span class="sxs-lookup"><span data-stu-id="26088-116">Since November 2019, we’ve released several updates as we built new functionality and responded to customer feedback.</span></span>

<span data-ttu-id="26088-117">Microsoft 365 コンプライアンスセンター (年 9 2020 月) のコンプライアンスマネージャーの一般的な可用性は、この進化を完了します。</span><span class="sxs-lookup"><span data-stu-id="26088-117">The general availability of Compliance Manager in the Microsoft 365 compliance center in September 2020 completes this evolution.</span></span> <span data-ttu-id="26088-118">コンプライアンスマネージャーは、統合されたエンドツーエンドのコンプライアンスソリューションです。</span><span class="sxs-lookup"><span data-stu-id="26088-118">Compliance Manager is the unified, end-to-end compliance solution.</span></span> <span data-ttu-id="26088-119">コンプライアンスのスコアは、コンプライアンスマネージャーの重要なコンポーネントとして残ります。</span><span class="sxs-lookup"><span data-stu-id="26088-119">Your compliance score remains a key component of Compliance Manager.</span></span>

<span data-ttu-id="26088-120">コンプライアンスマネージャーの GA リリースの新機能の詳細については、この [ブログ投稿](https://aka.ms/compliancemanager/GAblog) をお読みください。</span><span class="sxs-lookup"><span data-stu-id="26088-120">Read this [blog post](https://aka.ms/compliancemanager/GAblog) to learn more about what’s new with the GA release of Compliance Manager.</span></span>

#### <a name="your-organization-regularly-used-compliance-manger-in-the-service-trust-portal"></a><span data-ttu-id="26088-121">組織がサービス信頼ポータルで定期的にコンプライアンスマネージャーを使用している</span><span class="sxs-lookup"><span data-stu-id="26088-121">Your organization regularly used Compliance Manger in the Service Trust Portal</span></span>

<span data-ttu-id="26088-122">Service Trust Portal でコンプライアンスマネージャーを使用していた場合、組織のすべてのデータは、Microsoft 365 コンプライアンスセンターのコンプライアンスマネージャーに現在存在して https://compliance.microsoft.com/compliancemanager います。</span><span class="sxs-lookup"><span data-stu-id="26088-122">If you used Compliance Manager in the Service Trust Portal, all of your organization’s data now exists in Compliance Manager in the Microsoft 365 compliance center at https://compliance.microsoft.com/compliancemanager.</span></span> <span data-ttu-id="26088-123">コンプライアンスマネージャーが新しい場所で作業を再開するために必要な操作はありません。以前の場所にあるブックマークを更新する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="26088-123">There’s nothing you need to do to resume your Compliance Manager work in its new location, other than to update any bookmarks you have to its previous location.</span></span> <span data-ttu-id="26088-124">評価とその他のデータはすべてお客様に提供されています。</span><span class="sxs-lookup"><span data-stu-id="26088-124">All of your assessments and other data have been brought over for you.</span></span>

<span data-ttu-id="26088-125">コンプライアンスマネージャー (プレビュー) は、サービス信頼ポータルからはアクセスできなくなります。また、すべてのリンクが Microsoft 365 コンプライアンスセンターの新しい場所にリダイレクトされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="26088-125">Note that Compliance Manager (preview) is no longer accessible in the Service Trust Portal, and all links to it will redirect you to its new location in the Microsoft 365 compliance center.</span></span> <span data-ttu-id="26088-126">コンプライアンスマネージャー (クラシック) はサービス信頼ポータルに残りますが、使用は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="26088-126">Compliance Manager (classic) remains in the Service Trust Portal, though its use is discouraged.</span></span>

<span data-ttu-id="26088-127">以前のバージョンのコンプライアンスマネージャーで使用したもの (アクションの完了 ("改善アクション" と呼ばれました)、評価の作成など、新しいコンプライアンスマネージャーで行うことができます。</span><span class="sxs-lookup"><span data-stu-id="26088-127">Everything you used to do in previous versions of Compliance Manager, such as completing actions (now called “improvement actions”) and creating assessments, can be done in the new Compliance Manager.</span></span> <span data-ttu-id="26088-128">150を超える新しい評価テンプレートを追加し、テンプレートの作成プロセスを改善しました。</span><span class="sxs-lookup"><span data-stu-id="26088-128">We’ve added over 150 new assessment templates and improved the template creation process.</span></span> <span data-ttu-id="26088-129">今後のリリースでさらに強化された機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="26088-129">We'll add more enhancements in future releases.</span></span>

<span data-ttu-id="26088-130">役に立つリソースを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="26088-130">Below are some helpful resources:</span></span>

- [<span data-ttu-id="26088-131">新しいコンプライアンスマネージャーの経験を理解する</span><span class="sxs-lookup"><span data-stu-id="26088-131">Get familiar with your new Compliance Manger experience</span></span>](compliance-manager-setup.md#understand-the-compliance-manger-dashboard)
- [<span data-ttu-id="26088-132">新しいホームでコンプライアンスマネージャーのアクセス許可とその他のセットアップ情報を検索する</span><span class="sxs-lookup"><span data-stu-id="26088-132">Find permissions and other setup information for Compliance Manager in its new home</span></span>](compliance-manager-setup.md#who-can-access-compliance-manager)
- [<span data-ttu-id="26088-133">Microsoft 365 コンプライアンスセンターの詳細情報</span><span class="sxs-lookup"><span data-stu-id="26088-133">Learn more about the Microsoft 365 compliance center</span></span>](microsoft-365-compliance-center.md)

#### <a name="your-organization-used-compliance-score-public-preview-in-the-microsoft-365-compliance-center"></a><span data-ttu-id="26088-134">組織が Microsoft 365 コンプライアンスセンターでコンプライアンススコア (パブリックプレビュー) を使用した</span><span class="sxs-lookup"><span data-stu-id="26088-134">Your organization used Compliance Score (public preview) in the Microsoft 365 compliance center</span></span>

<span data-ttu-id="26088-135">パブリックプレビューでコンプライアンススコアを使用した場合は、コンプライアンスマネージャーがほぼ同じように表示されることがわかります。ダッシュボードでスコアが目立つようになっています。</span><span class="sxs-lookup"><span data-stu-id="26088-135">If you used Compliance Score in public preview, you’ll notice Compliance Manager looks largely the same, with your score featured prominently on your dashboard.</span></span> <span data-ttu-id="26088-136">GA リリースでは、評価のためのテンプレートの作成や変更など、特定の評価管理機能を実行するために Microsoft 365 コンプライアンスセンターを終了する必要がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="26088-136">With the GA release, you no longer need to leave the Microsoft 365 compliance center in order to perform certain assessment management functions, such as creating and modifying templates for assessments.</span></span> <span data-ttu-id="26088-137">すべての機能が1つの場所に配置されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="26088-137">All functionality now resides in one place.</span></span> <span data-ttu-id="26088-138">コンプライアンススコアのプレビューバージョンに含まれていたデータは、コンプライアンスマネージャーの GA バージョンに保持されます。</span><span class="sxs-lookup"><span data-stu-id="26088-138">Any data you had in the preview version of Compliance Score remains in the GA version of Compliance Manager.</span></span>

<span data-ttu-id="26088-139">コンプライアンススコアダッシュボードビューをフィルター処理した場合、このフィルターは、9月に新しいコンプライアンスマネージャーを展開したときにリセットされたことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="26088-139">Note that if you filtered your Compliance Score dashboard view, those filters were reset when we deployed the new Compliance Manager in September.</span></span> <span data-ttu-id="26088-140">必要なフィルターを再適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26088-140">You will need to reapply any filters you had.</span></span>

<span data-ttu-id="26088-141">コンプライアンスマネージャーにも新しいライセンス条項があります。</span><span class="sxs-lookup"><span data-stu-id="26088-141">Compliance Manager also has new licensing terms.</span></span> <span data-ttu-id="26088-142">ライセンスについては、以下の質問を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26088-142">See the question below on licensing.</span></span>

#### <a name="youre-new-to-compliance-manager"></a><span data-ttu-id="26088-143">コンプライアンスマネージャーの使用が初めての方</span><span class="sxs-lookup"><span data-stu-id="26088-143">You're new to Compliance Manager</span></span>

<span data-ttu-id="26088-144">コンプライアンスマネージャーは、コンプライアンス活動を管理および追跡するための、Microsoft 365 コンプライアンスセンターのエンドツーエンドのソリューションです。</span><span class="sxs-lookup"><span data-stu-id="26088-144">Compliance Manager is an end-to-end solution in the Microsoft 365 compliance center for managing and tracking compliance activities.</span></span> <span data-ttu-id="26088-145">初めてアクセスしたときに、コンプライアンスの状況を最初に評価することになるため、コンプライアンスへの移行を開始するのに最適な場所です。</span><span class="sxs-lookup"><span data-stu-id="26088-145">It’s a great place to begin your compliance journey because it gives you an initial assessment of your compliance posture the first time you visit.</span></span> <span data-ttu-id="26088-146">詳細な学習を開始するための適切な場所は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="26088-146">Below are good places to start learning more:</span></span>

- [<span data-ttu-id="26088-147">コンプライアンスマネージャーの概要を取得する</span><span class="sxs-lookup"><span data-stu-id="26088-147">Get an overview of Compliance Manager</span></span>](compliance-manager.md)
- [<span data-ttu-id="26088-148">クイックスタートガイドを使用して段階的に向上させる</span><span class="sxs-lookup"><span data-stu-id="26088-148">Use our quickstart guide to help ramp up in stages</span></span>](compliance-manager-quickstart.md)
- [<span data-ttu-id="26088-149">Microsoft 365 コンプライアンスセンターの詳細情報</span><span class="sxs-lookup"><span data-stu-id="26088-149">Learn more about the Microsoft 365 compliance center</span></span>](microsoft-365-compliance-center.md)

## <a name="are-there-licensing-requirements-for-using-compliance-manager"></a><span data-ttu-id="26088-150">コンプライアンスマネージャーを使用するためのライセンス要件はありますか。</span><span class="sxs-lookup"><span data-stu-id="26088-150">Are there licensing requirements for using Compliance Manager?</span></span>

<span data-ttu-id="26088-151">はい。</span><span class="sxs-lookup"><span data-stu-id="26088-151">Yes.</span></span> <span data-ttu-id="26088-152">コンプライアンスマネージャーの GA リリースには、新しいライセンス条項が含まれています。</span><span class="sxs-lookup"><span data-stu-id="26088-152">The GA release of Compliance Manager contains new licensing terms.</span></span> <span data-ttu-id="26088-153">Office 365 と Microsoft 365 のライセンスを持つすべての組織 (米国政府および DoD を除く) は、コンプライアンスマネージャーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="26088-153">All organizations with Office 365 and Microsoft 365 licenses (except for US Government and DoD) have access to Compliance Manager.</span></span> <span data-ttu-id="26088-154">ただし、組織で使用可能な評価と評価テンプレートの管理方法は、使用許諾契約によって異なります。</span><span class="sxs-lookup"><span data-stu-id="26088-154">However, the assessments available to your organization and how you manage assessment templates depends on your licensing agreement.</span></span> <span data-ttu-id="26088-155">詳細については、「 [Microsoft 365 ライセンスガイダンス」の「セキュリティとコンプライアンス」を](https://go.microsoft.com/fwlink/?linkid=2132371) 参照してください。</span><span class="sxs-lookup"><span data-stu-id="26088-155">Visit the [Microsoft 365 licensing guidance for security and compliance](https://go.microsoft.com/fwlink/?linkid=2132371) for details.</span></span>

## <a name="if-i-have-a-high-score-does-it-mean-im-fully-compliant"></a><span data-ttu-id="26088-156">スコアが高い場合は、完全に準拠していることを意味します。</span><span class="sxs-lookup"><span data-stu-id="26088-156">If I have a high score, does it mean I’m fully compliant?</span></span>

<span data-ttu-id="26088-157">いいえ。</span><span class="sxs-lookup"><span data-stu-id="26088-157">No.</span></span> <span data-ttu-id="26088-158">コンプライアンススコアは、データ保護と規制基準に関するリスクを軽減するために、推奨されるアクションを完了するための進捗状況を測定します。</span><span class="sxs-lookup"><span data-stu-id="26088-158">Your compliance score measures your progress in completing recommended actions that help reduce risks around data protection and regulatory standards.</span></span> <span data-ttu-id="26088-159">特定の標準または規制に関して、組織のコンプライアンスの絶対的な測定基準を表すものではありません。</span><span class="sxs-lookup"><span data-stu-id="26088-159">It does not express an absolute measure of organizational compliance with regard to a particular standard or regulation.</span></span> <span data-ttu-id="26088-160">コンプライアンスマネージャーおよびコンプライアンススコアは、何らかの保証として解釈されることはありません。</span><span class="sxs-lookup"><span data-stu-id="26088-160">Compliance Manager, and your compliance score, should not be interpreted as a guarantee in any way.</span></span>

## <a name="can-i-use-compliance-manager-for-non-microsoft-products"></a><span data-ttu-id="26088-161">Microsoft 以外の製品でコンプライアンスマネージャーを使用できますか。</span><span class="sxs-lookup"><span data-stu-id="26088-161">Can I use Compliance Manager for non-Microsoft products?</span></span>

<span data-ttu-id="26088-162">コンプライアンスマネージャーは、継続的な監視および推奨されるアクションを Microsoft クラウドサービスに対してのみ提供しますが、サードパーティのサービスのコンプライアンスマネージャーでカスタム評価を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="26088-162">While Compliance Manager provides continuous monitoring and recommended actions only for Microsoft cloud services, you can add custom assessments in Compliance Manager for your third-party services.</span></span> <span data-ttu-id="26088-163">この方法では、Microsoft コンプライアンスマネージャーを SaaS コンプライアンス管理ツールとして使用して、デジタルアセット全体のコントロールを管理することができます。</span><span class="sxs-lookup"><span data-stu-id="26088-163">In this way, you can use Microsoft Compliance Manager as a SaaS compliance management tool to help you manage all the controls across your digital assets.</span></span>