---
title: '脅威トラッカー - 新機能とNoteworthy 機能 '
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: a097f5ca-eac0-44a4-bbce-365f35b79ed1
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: 新しい注目すべきトラッカーを含む脅威のトラッカーについて説明します。これにより、組織はセキュリティ上の問題に常に役立てることができます。
ms.openlocfilehash: 551f5704337ef8989fd1568854822bc1d9d4c14b
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "49615458"
---
# <a name="threat-trackers---new-and-noteworthy"></a><span data-ttu-id="9c809-103">脅威トラッカー - 新機能とNoteworthy 機能 </span><span class="sxs-lookup"><span data-stu-id="9c809-103">Threat Trackers - New and Noteworthy</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


<span data-ttu-id="9c809-104">[Office 365 の脅威調査と応答](office-365-ti.md) 機能を使用すると、組織のセキュリティチームが cybersecurity の脅威を検出し、行動を取ることができます。</span><span class="sxs-lookup"><span data-stu-id="9c809-104">[Office 365 Threat Investigation and Response](office-365-ti.md) capabilities enable your organization's security team to discover and take action against cybersecurity threats.</span></span> <span data-ttu-id="9c809-105">Office 365 の脅威の調査と応答の機能には、注目すべきトラッカーを含む脅威の追跡機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9c809-105">Office 365 Threat Investigation and Response capabilities include Threat Tracker features, including Noteworthy trackers.</span></span> <span data-ttu-id="9c809-106">これらの新機能と次の手順の概要を確認するには、この記事をお読みください。</span><span class="sxs-lookup"><span data-stu-id="9c809-106">Read this article to get an overview of these new features and next steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c809-107">Office 365 の脅威インテリジェンスは、Microsoft Defender for Office 365 プラン2に加えて、追加の脅威保護機能と共に提供されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="9c809-107">Office 365 Threat Intelligence is now Microsoft Defender for Office 365 Plan 2, along with additional threat protection capabilities.</span></span> <span data-ttu-id="9c809-108">詳細については、「 [Microsoft defender For office 365 プランと料金](https://products.office.com/exchange/advance-threat-protection) 」および「 [Microsoft defender For office 365 サービスの説明](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c809-108">To learn more, see [Microsoft Defender for Office 365 plans and pricing](https://products.office.com/exchange/advance-threat-protection) and the [Microsoft Defender for Office 365 Service Description](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).</span></span>

## <a name="what-are-threat-trackers"></a><span data-ttu-id="9c809-109">脅威のトラッカーとは</span><span class="sxs-lookup"><span data-stu-id="9c809-109">What are Threat Trackers?</span></span>

<span data-ttu-id="9c809-110">脅威のトラッカーは、会社に影響を与える可能性があるさまざまな cybersecurity の問題に関するインテリジェンスを提供する、情報ウィジェットとビューです。</span><span class="sxs-lookup"><span data-stu-id="9c809-110">Threat Trackers are informative widgets and views that provide you with intelligence on different cybersecurity issues that might impact your company.</span></span> <span data-ttu-id="9c809-111">たとえば、脅威のトラッカーを使用して、トレンドマルウェアキャンペーンに関する情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="9c809-111">For example, you can view information about trending malware campaigns using Threat Trackers.</span></span>

![マルウェアキャンペーンを示す脅威の追跡ツールの例](../../media/a883b5ac-8e2b-469a-90e0-f8ad39bb63b7.png)

<span data-ttu-id="9c809-113">ほとんどのトラッカーページには、定期的に更新される傾向の数値、最も大きな問題について理解するのに役立つウィジェット、およびエクスプローラーに表示される [ **Actions** ] 列にあるクイックリンクが含まれています。これにより、より詳細な情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="9c809-113">Most tracker pages include trending numbers that are updated periodically, widgets to help you understand which issues are the biggest or have grown the most, and a quick link in the **Actions** column that takes you to Explorer, where you can view more detailed information.</span></span>

![エクスプローラーでのキャンペーン情報の例](../../media/e426f220-fdcb-4dd9-99a2-db97dbcf71d5.png)

<span data-ttu-id="9c809-115">トラッカーは、 [Microsoft Defender For Office 365 プラン 2](office-365-ti.md)で入手できる、多くの重要な機能のほんの一部に過ぎません。</span><span class="sxs-lookup"><span data-stu-id="9c809-115">Trackers are just a few of the many great features you get with [Microsoft Defender for Office 365 Plan 2](office-365-ti.md).</span></span> <span data-ttu-id="9c809-116">脅威のトラッカーには、 [注意を価値トラッカー](#noteworthy-trackers)、 [傾向分析](#trending-trackers)、 [追跡クエリ](#tracked-queries)、および [保存されたクエリ](#saved-queries)が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9c809-116">Threat Trackers include [Noteworth trackers](#noteworthy-trackers), [Trending trackers](#trending-trackers), [Tracked queries](#tracked-queries), and [Saved queries](#saved-queries).</span></span>

<span data-ttu-id="9c809-117">組織の脅威のトラッカーを表示して使用するには、セキュリティ & コンプライアンスセンター ( <https://protection.office.com> ) に移動して、[ **脅威管理** の \> **脅威の追跡ツール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9c809-117">To view and use your Threat Trackers for your organization, go to the Security & Compliance Center (<https://protection.office.com>) and choose **Threat management** \> **Threat tracker**.</span></span>

> [!NOTE]
> <span data-ttu-id="9c809-118">脅威のトラッカーを使用するには、全体管理者、セキュリティ管理者、またはセキュリティリーダーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c809-118">To use Threat Trackers, you must be a global administrator, security administrator, or security reader.</span></span> <span data-ttu-id="9c809-119">「 [セキュリティ & コンプライアンスセンター」の「アクセス許可」を](permissions-in-the-security-and-compliance-center.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c809-119">See [Permissions in the Security & Compliance Center](permissions-in-the-security-and-compliance-center.md).</span></span>

### <a name="noteworthy-trackers"></a><span data-ttu-id="9c809-120">注目すべきトラッカー</span><span class="sxs-lookup"><span data-stu-id="9c809-120">Noteworthy trackers</span></span>

<span data-ttu-id="9c809-121">注目すべき脅威とリスクについて理解していると考えられていますが、注目すべきトラッカーがあります。</span><span class="sxs-lookup"><span data-stu-id="9c809-121">Noteworthy trackers are where you'll find big and smaller threats and risks that we think you should know about.</span></span> <span data-ttu-id="9c809-122">注目すべきトラッカーは、Microsoft 365 環境にこれらの問題があるかどうかを確認するのに役立ちます。また、そのような記事へのリンクにより、何が起こっているか、またそれらがどのように Office 365 を使用しているかにどのように影響するかについての情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="9c809-122">Noteworthy trackers help you find whether these issues exist in your Microsoft 365 environment, plus link to articles (like this one) that give you more details on what is happening, and how they'll impact your organization's use of Office 365.</span></span> <span data-ttu-id="9c809-123">It が大きな新しい脅威であるかどうか (例: Wonprint Acoffice、Petya)、または既存の脅威 (他の inaugural の重要なアイテム-Nemucod など) であるかどうか。この記事では、お客様とセキュリティチームが定期的に検討して検討する必要がある重要な新しいアイテムを紹介します。</span><span class="sxs-lookup"><span data-stu-id="9c809-123">Whether it's a big new threat (e.g. Wannacry, Petya) or an existing threat that might create some new challenges (like our other inaugural Noteworthy item - Nemucod), this is where you'll find important new items you and your security team should review and examine periodically.</span></span>

<span data-ttu-id="9c809-124">通常、注目すべきトラッカーは、新しい脅威を特定し、この機能が提供する追加の可視性が必要になる可能性があると考えると、わずか数週間だけ投稿されます。</span><span class="sxs-lookup"><span data-stu-id="9c809-124">Typically Noteworthy trackers will be posted for just a couple of weeks when we identify new threats and think you might need the extra visibility that this feature provides.</span></span> <span data-ttu-id="9c809-125">脅威に対する最大のリスクが経過したら、その注目すべき項目を削除します。</span><span class="sxs-lookup"><span data-stu-id="9c809-125">Once the biggest risk for a threat has passed, we'll remove that Noteworthy item.</span></span> <span data-ttu-id="9c809-126">これにより、他の関連する新しいアイテムの一覧を最新の状態にし、最新の状態に保つことができます。</span><span class="sxs-lookup"><span data-stu-id="9c809-126">This way, we can keep the list fresh and up to date with other relevant new items.</span></span>

### <a name="trending-trackers"></a><span data-ttu-id="9c809-127">トレンド分析</span><span class="sxs-lookup"><span data-stu-id="9c809-127">Trending trackers</span></span>

<span data-ttu-id="9c809-128">過去1週間に組織のメールで受信した新しい脅威は、傾向分析 (旧称キャンペーン) によって強調されています。</span><span class="sxs-lookup"><span data-stu-id="9c809-128">Trending trackers (formerly called Campaigns) highlight new threats received in your organization's email in the past week.</span></span>

![トレンドマルウェアキャンペーンウィジェットの例](../../media/d2ccc1a0-2a1d-4e36-99b5-6766c207772f.png)

<span data-ttu-id="9c809-130">傾向分析では、より幅広い企業環境が攻撃に対して準備されていることを確認するために検討すべき新しい脅威について理解します。</span><span class="sxs-lookup"><span data-stu-id="9c809-130">Trending trackers give you an idea of new threats you should review to ensure your broader corporate environment is prepared against attacks.</span></span>

### <a name="tracked-queries"></a><span data-ttu-id="9c809-131">追跡されたクエリ</span><span class="sxs-lookup"><span data-stu-id="9c809-131">Tracked queries</span></span>

<span data-ttu-id="9c809-132">追跡されたクエリは、保存されたクエリを利用して、組織内の Microsoft 365 のアクティビティを定期的に評価します。</span><span class="sxs-lookup"><span data-stu-id="9c809-132">Tracked queries leverage your saved queries to periodically assess Microsoft 365 activity in your organization.</span></span> <span data-ttu-id="9c809-133">これにより、イベントの傾向が得られ、今後数か月になる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="9c809-133">This gives you event trending, with more to come in the coming months.</span></span> <span data-ttu-id="9c809-134">追跡されたクエリは自動的に実行され、最新の情報が得られるため、クエリを再実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9c809-134">Tracked queries run automatically, giving you up-to-date information without having to remember to re-run your queries.</span></span>

![1つが選択された状態の追跡クエリの例](../../media/0c556174-06eb-4ae5-b32a-5ff76b9e4f13.png)

### <a name="saved-queries"></a><span data-ttu-id="9c809-136">保存されたクエリ</span><span class="sxs-lookup"><span data-stu-id="9c809-136">Saved queries</span></span>

<span data-ttu-id="9c809-137">保存されたクエリは、[トラッカー] セクションにもあります。</span><span class="sxs-lookup"><span data-stu-id="9c809-137">Saved queries are also found in the Trackers section.</span></span> <span data-ttu-id="9c809-138">保存されたクエリを使用して、検索を毎回作成しなくても、すばやく繰り返して戻る必要がある一般的なエクスプローラー検索を格納できます。</span><span class="sxs-lookup"><span data-stu-id="9c809-138">You can use Saved queries to store the common Explorer searches that you want to get back to quicker and repeatedly, without having to re-create the search every time.</span></span>

![1つの選択で保存されたクエリの例](../../media/188cf3ff-58f1-41ea-81aa-76158d8f40c3.png)

<span data-ttu-id="9c809-140">エクスプローラーページの上部にある [ **クエリの保存** ] ボタンを使用して、注目すべき追跡ツールまたは独自のエクスプローラクエリをいつでも保存できます。</span><span class="sxs-lookup"><span data-stu-id="9c809-140">You can always save a Noteworthy tracker query or any of your own Explorer queries using the **Save query** button at the top of the Explorer page.</span></span> <span data-ttu-id="9c809-141">保存された内容は、[トラッカー] ページの [ **保存さ** れたクエリ] リストに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c809-141">Anything saved there will show up in the **Saved queries** list on the Tracker page.</span></span>

## <a name="trackers-and-explorer"></a><span data-ttu-id="9c809-142">トラッカーとエクスプローラー</span><span class="sxs-lookup"><span data-stu-id="9c809-142">Trackers and Explorer</span></span>

<span data-ttu-id="9c809-143">メール、コンテンツ、または Office アクティビティ (近日中) をレビューしているかどうかにかかわらず、エクスプローラーとトラッカーは連携して、セキュリティリスクと脅威を調査および追跡するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9c809-143">Whether you're reviewing email, content, or Office activities (coming soon), Explorer and Trackers work together to help you investigate and track security risks and threats.</span></span> <span data-ttu-id="9c809-144">これらのすべての機能により、新しい、注目されたよく検索される問題を強調することで、ユーザーを保護するための情報が提供されます。これにより、クラウドに移行する際のビジネスの保護が向上します。</span><span class="sxs-lookup"><span data-stu-id="9c809-144">All together, Trackers provide you with information to protect your users by highlighting new, notable, and frequently searched issues - ensuring your business is better protected as it moves to the cloud.</span></span>

<span data-ttu-id="9c809-145">また、[セキュリティ & コンプライアンスセンターの概要](https://support.microsoft.com/office/a5f2fd18-b029-4257-b5a8-ae83e7768c85)の右下にある [**フィードバック**] ボタンをクリックすることで、このまたはその他の Microsoft 365 のセキュリティ機能に関するフィードバックをいつでも提供できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9c809-145">And remember that you can always provide us feedback on this or other Microsoft 365 security features by clicking on the **Feedback** button in the lower right corner of the [Overview of the Security & Compliance Center](https://support.microsoft.com/office/a5f2fd18-b029-4257-b5a8-ae83e7768c85).</span></span>

![セキュリティ/コンプライアンス センター](../../media/86c330db-8132-4150-8475-220258fe04fb.png)

## <a name="trackers-and-microsoft-defender-for-office-365"></a><span data-ttu-id="9c809-147">トラッカーおよび Microsoft Defender for Office 365</span><span class="sxs-lookup"><span data-stu-id="9c809-147">Trackers and Microsoft Defender for Office 365</span></span>

<span data-ttu-id="9c809-148">Inaugural の注目すべき脅威から、 [安全な添付ファイル](atp-safe-attachments.md)によって検出された高度なマルウェアの脅威を強調しています。</span><span class="sxs-lookup"><span data-stu-id="9c809-148">With our inaugural Noteworthy threat, we're highlighting advanced malware threats detected by [Safe Attachments](atp-safe-attachments.md).</span></span> <span data-ttu-id="9c809-149">Office 365 Enterprise E5 のお客様で、 [Microsoft Defender For office 365](office-365-atp.md)を使用していない場合は、サブスクリプションに含まれています。</span><span class="sxs-lookup"><span data-stu-id="9c809-149">If you're an Office 365 Enterprise E5 customer and you're not using [Microsoft Defender for Office 365](office-365-atp.md), you should be - it's included in your subscription.</span></span> <span data-ttu-id="9c809-150">Office 365 の Defender には、Office 365 サービスでメールフローをフィルタリングする他のセキュリティツールがある場合でも、値が提供されます。</span><span class="sxs-lookup"><span data-stu-id="9c809-150">Defender for Office 365 provides value even if you have other security tools filtering email flow with your Office 365 services.</span></span> <span data-ttu-id="9c809-151">ただし、スパム対策機能と [安全なリンク](atp-safe-links.md) 機能は、メインの電子メールセキュリティソリューションが Office 365 を使用している場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="9c809-151">However, anti-spam and [Safe Links](atp-safe-links.md) features work best when your main email security solution is through Office 365.</span></span>

![セキュリティ & コンプライアンスセンターの Microsoft Defender for Office 365](../../media/cee70d07-f0c1-459b-843c-2d10c253349f.png)

<span data-ttu-id="9c809-153">今日の riddled world では、従来のマルウェア対策スキャンのみを実行することは、攻撃に対して十分に保護されていないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="9c809-153">In today's threat-riddled world, running only traditional anti-malware scans means you are not protected well enough against attacks.</span></span> <span data-ttu-id="9c809-154">今日の高度な攻撃者は、一般的に使用可能なツールを使用して、従来の署名ベースのマルウェア対策エンジンで認識されない新しい、難読化された、または遅延した攻撃を作成します。</span><span class="sxs-lookup"><span data-stu-id="9c809-154">Today's more sophisticated attackers use commonly available tools to create new, obfuscated, or delayed attacks that won't be recognized by traditional signature-based anti-malware engines.</span></span> <span data-ttu-id="9c809-155">安全な添付ファイル機能は、電子メールの添付ファイルを取得し、それを仮想環境で分析して、それらが安全か悪意があるかを判断します。</span><span class="sxs-lookup"><span data-stu-id="9c809-155">The Safe Attachments feature takes email attachments and detonates them in a virtual environment to determine whether they're safe or malicious.</span></span> <span data-ttu-id="9c809-156">この分析プロセスは、仮想コンピューター環境で各ファイルを開き、ファイルが開かれた後の処理を監視します。</span><span class="sxs-lookup"><span data-stu-id="9c809-156">This detonation process opens each file in a virtual computer environment, then watches what happens after the file is opened.</span></span> <span data-ttu-id="9c809-157">PDF、圧縮ファイル、または Office ドキュメントであるかどうかにかかわらず、悪意のあるコードはファイル内で非表示にすることができます。アクティブ化するには、ユーザーが自分のコンピューターでそのコードを開いている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c809-157">Whether it's a PDF, and compressed file, or an Office document, malicious code can be hidden in a file, activating only once the victim opens it on their computer.</span></span> <span data-ttu-id="9c809-158">Detonating を使用して電子メールフロー内のファイルを分析することで、Office 365 の機能に対する Defender は、動作、ファイルの評価、およびいくつかのヒューリスティックルールに基づいてこれらの脅威を検出します。</span><span class="sxs-lookup"><span data-stu-id="9c809-158">By detonating and analyzing the file in the email flow, Defender for Office 365 capabilities finds these threats based on behaviors, file reputation, and a number of heuristic rules.</span></span>

<span data-ttu-id="9c809-159">新しい注目すべき脅威フィルターは、安全な添付ファイルによって最近検出されたアイテムを強調表示します。</span><span class="sxs-lookup"><span data-stu-id="9c809-159">The new Noteworthy threat filter highlights items that were recently detected through Safe Attachments.</span></span> <span data-ttu-id="9c809-160">これらの検出は、電子メールフローまたは他のお客様の電子メールのいずれかで、Microsoft 365 によって以前検出されていない新しい悪意のあるファイルであるアイテムを表します。</span><span class="sxs-lookup"><span data-stu-id="9c809-160">These detections represent items that are new malicious files, not previously found by Microsoft 365 in either your email flow or other customers' email.</span></span> <span data-ttu-id="9c809-161">注目すべき脅威追跡ツールの項目に注目し、それらのユーザーが対象としているユーザーを確認し、[詳細な分析] タブ (エクスプローラーで電子メールの件名をクリックすると表示されます) に示されている分析の詳細を確認します。</span><span class="sxs-lookup"><span data-stu-id="9c809-161">Pay attention to the items in the Noteworthy Threat Tracker, see who was targeted by them, and review the detonation details shown on the Advanced Analysis tab (found by clicking on the subject of the email in Explorer).</span></span> <span data-ttu-id="9c809-162">メモこのタブは、安全な添付ファイル機能によって検出された電子メールにのみ表示されます。この注目すべきトラッカーには、フィルターが含まれていますが、そのフィルターをエクスプローラーで他の検索に使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="9c809-162">Note you'll only find this tab on emails detected by the Safe Attachments capability - this Noteworthy tracker includes that filter, but you can also use that filter for other searches in Explorer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9c809-163">次の手順</span><span class="sxs-lookup"><span data-stu-id="9c809-163">Next steps</span></span>

- <span data-ttu-id="9c809-164">組織にこれらの Office 365 脅威の調査および応答機能がまだない場合は、「 [office 365 の脅威の調査および応答機能を入手する方法](office-365-ti.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c809-164">If your organization doesn't already have these Office 365 Threat Investigation and Response capabilities, see [How do we get Office 365 Threat Investigation and Response capabilities?](office-365-ti.md).</span></span>

- <span data-ttu-id="9c809-165">セキュリティチームに適切な役割とアクセス許可が割り当てられていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9c809-165">Make sure that your security team has the correct roles and permissions assigned.</span></span> <span data-ttu-id="9c809-166">セキュリティ & コンプライアンスセンターでは、全体管理者であるか、セキュリティ管理者または検索および削除の役割が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c809-166">You must be a global administrator, or have the Security Administrator or Search and Purge role assigned in the Security & Compliance Center.</span></span> <span data-ttu-id="9c809-167">「 [セキュリティ & コンプライアンスセンター」の「アクセス許可」を](permissions-in-the-security-and-compliance-center.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c809-167">See [Permissions in the Security & Compliance Center](permissions-in-the-security-and-compliance-center.md).</span></span>

- <span data-ttu-id="9c809-168">新しいトラッカーが Microsoft 365 環境に表示されることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9c809-168">Watch for the new Trackers to show up in your Microsoft 365 environment.</span></span> <span data-ttu-id="9c809-169">利用可能な場合は、 [ここで](https://protection.office.com/)トラッカーを見つけてください。</span><span class="sxs-lookup"><span data-stu-id="9c809-169">When available, you'll find your Trackers [here](https://protection.office.com/).</span></span> <span data-ttu-id="9c809-170">**脅威管理** の脅威の \> **トラッカー** に移動します。</span><span class="sxs-lookup"><span data-stu-id="9c809-170">Go to **Threat management** \> **Threat trackers**.</span></span>

- <span data-ttu-id="9c809-171">お客様の組織については、「[安全なリンク](atp-safe-links.md)」や「[安全な添付ファイル](atp-safe-attachments.md)」を含む、 [Microsoft Defender for Office 365 の](office-365-atp.md)詳細と構成を行っていない場合は、こちらを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c809-171">If you haven't already done so, learn more about and configure [Microsoft Defender for Office 365](office-365-atp.md) for your organization, including [Safe links](atp-safe-links.md) and [Safe Attachments](atp-safe-attachments.md).</span></span>
