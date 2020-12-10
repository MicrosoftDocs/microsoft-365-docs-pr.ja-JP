---
title: 脅威エクスプローラーとリアルタイム検出
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 82ac9922-939c-41be-9c8a-7c75b0a4e27d
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: セキュリティ & コンプライアンスセンターでエクスプローラおよびリアルタイム検出を使用して、効果的かつ効率的に脅威を調査して対応する方法について説明します。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 4328bfc52497f911c57256f8366b3742523b17b0
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "49615566"
---
# <a name="threat-explorer-and-real-time-detections"></a><span data-ttu-id="cf931-103">脅威エクスプローラーとリアルタイム検出</span><span class="sxs-lookup"><span data-stu-id="cf931-103">Threat Explorer and Real-time detections</span></span>

<span data-ttu-id="cf931-104">組織が [Microsoft Defender For Office 365](office-365-atp.md)を所有していて、 [必要なアクセス許可](#required-licenses-and-permissions)を持っている場合は、 **Explorer** または **リアルタイムの検出** (以前の *リアルタイムのレポート* - [新機能を参照してください](#new-features-in-threat-explorer-and-real-time-detections)) があります。</span><span class="sxs-lookup"><span data-stu-id="cf931-104">If your organization has [Microsoft Defender for Office 365](office-365-atp.md), and you have the [necessary permissions](#required-licenses-and-permissions), you have either **Explorer** or **Real-time detections** (formerly *Real-time reports* — [see what's new](#new-features-in-threat-explorer-and-real-time-detections)!).</span></span> <span data-ttu-id="cf931-105">[セキュリティ & コンプライアンスセンター] で、[ **脅威の管理**] に移動してから、[ **エクスプローラー** ] _または_[ **リアルタイムの検出**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cf931-105">In the Security & Compliance Center, go to **Threat management**, and then choose **Explorer** _or_ **Real-time detections**.</span></span>

|<span data-ttu-id="cf931-106">Microsoft Defender for Office 365 プラン2については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf931-106">With Microsoft Defender for Office 365 Plan 2, you see:</span></span>|<span data-ttu-id="cf931-107">Microsoft Defender for Office 365 プラン1を使用すると、次のように表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="cf931-107">With Microsoft Defender for Office 365 Plan 1, you see:</span></span>|
|---|---|
|![脅威エクスプローラー](../../media/threatmgmt-explorer.png)|![リアルタイムの検出](../../media/threatmgmt-realtimedetections.png)|
|

<span data-ttu-id="cf931-110">エクスプローラー (リアルタイム検出) を使用すると、強力なレポートが得られます。これにより、セキュリティ運用チームは脅威を調査して効果的かつ効率的に対処することができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-110">With Explorer (or Real-time detections), you have a powerful report that enables your Security Operations team to investigate and respond to threats effectively and efficiently.</span></span> <span data-ttu-id="cf931-111">このレポートは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="cf931-111">The report resembles the following image:</span></span>

![[脅威管理エクスプローラー] に移動します。 \>](../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png)

<span data-ttu-id="cf931-113">このレポートでは、次のことができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-113">With this report, you can:</span></span>

- [<span data-ttu-id="cf931-114">Microsoft 365 セキュリティ機能によって検出されたマルウェアを参照</span><span class="sxs-lookup"><span data-stu-id="cf931-114">See malware detected by Microsoft 365 security features</span></span>](#see-malware-detected-in-email-by-technology)
- <span data-ttu-id="cf931-115">[フィッシング Url に関するデータを表示し、[verdict] をクリックします。](#view-data-about-phishing-urls-and-click-verdict)</span><span class="sxs-lookup"><span data-stu-id="cf931-115">[View data about phishing URLs and click verdict](#view-data-about-phishing-urls-and-click-verdict)</span></span>
- <span data-ttu-id="cf931-116">[エクスプローラーのビューから自動化された調査と応答プロセスを開始](#start-automated-investigation-and-response) する (Defender for Office 365 プラン2のみ)</span><span class="sxs-lookup"><span data-stu-id="cf931-116">[Start an automated investigation and response process from a view in Explorer](#start-automated-investigation-and-response) (Defender for Office 365 Plan 2 only)</span></span>
- <span data-ttu-id="cf931-117">...[悪意のある電子メールの調査など](#more-ways-to-use-explorer-or-real-time-detections)</span><span class="sxs-lookup"><span data-stu-id="cf931-117">... [Investigate malicious email, and more](#more-ways-to-use-explorer-or-real-time-detections)!</span></span>

## <a name="experience-improvements-to-threat-explorer-and-real-time-detections"></a><span data-ttu-id="cf931-118">脅威エクスプローラーおよびリアルタイム検出の機能が向上しました。</span><span class="sxs-lookup"><span data-stu-id="cf931-118">Experience Improvements to Threat Explorer and Real-time detections</span></span>

### <a name="tags-in-threat-explorer"></a><span data-ttu-id="cf931-119">脅威エクスプローラーのタグ</span><span class="sxs-lookup"><span data-stu-id="cf931-119">Tags in Threat Explorer</span></span>

> [!NOTE]
> <span data-ttu-id="cf931-120">ユーザータグ機能はプレビューでは、すべてのユーザーが利用できるわけではなく、変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cf931-120">The user tags feature is in Preview, isn't available to everyone, and is subject to change.</span></span> <span data-ttu-id="cf931-121">リリーススケジュールの詳細については、Microsoft 365 ロードマップをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cf931-121">For information about the release schedule, check out the Microsoft 365 roadmap.</span></span>

<span data-ttu-id="cf931-122">ユーザータグとは、Office 365 の Microsoft Defender で特定のユーザーグループの識別子です。</span><span class="sxs-lookup"><span data-stu-id="cf931-122">User tags are identifiers for specific groups of users in Microsoft Defender for Office 365.</span></span> <span data-ttu-id="cf931-123">タグの詳細については、「 [ユーザータグ](user-tags.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf931-123">For more information around tags, licensing and configuring tags, see [User tags](user-tags.md).</span></span>

<span data-ttu-id="cf931-124">脅威エクスプローラーでは、次のような場合に、ユーザータグに関する情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="cf931-124">Within Threat Explorer, you can see information around user tags in the following experiences:</span></span>

#### <a name="email-grid-view"></a><span data-ttu-id="cf931-125">メールグリッドビュー</span><span class="sxs-lookup"><span data-stu-id="cf931-125">Email Grid View</span></span>

<span data-ttu-id="cf931-126">[電子メール] グリッドに表示される [タグ] 列には、送信者または受信者のメールボックスに適用されているすべてのタグが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cf931-126">The Tags column shown in the email grid would contain all the tags that have been applied to the sender or recipient mailboxes.</span></span> <span data-ttu-id="cf931-127">既定では、優先度のアカウントなどのシステムタグが最初に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-127">By default, system tags like priority accounts are shown first.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-128">![メールグリッドビューでのタグのフィルター処理](../../media/tags-grid.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-128">![Filter tags in email grid view](../../media/tags-grid.png)</span></span>

#### <a name="filtering"></a><span data-ttu-id="cf931-129">フィルター処理</span><span class="sxs-lookup"><span data-stu-id="cf931-129">Filtering</span></span>

<span data-ttu-id="cf931-130">これで、優先度の高いアカウント、または特定のユーザータグシナリオにわたってタグが表示されるようになりました。また、この環境の一部として特定のタグを含む結果を除外することもできます。</span><span class="sxs-lookup"><span data-stu-id="cf931-130">We now have Tags as a filter so you can hunt just across priority accounts, or specific User tags scenarios (and even exclude results with certain tags as part of this experience).</span></span> <span data-ttu-id="cf931-131">このような他の複数のフィルターを組み合わせて使用することで、調査の範囲を絞ることができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-131">Combining these with the multiple other filters that we provide, would help you to narrow down your scope of investigation</span></span>

<span data-ttu-id="cf931-132">[![タグのフィルター](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="cf931-132">[![Filter tags](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-133">![非フィルタータグ](../../media/tags-filter-not.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-133">![Not filter tags](../../media/tags-filter-not.png)</span></span>

#### <a name="email-detail-flyout"></a><span data-ttu-id="cf931-134">電子メール詳細ポップアップ</span><span class="sxs-lookup"><span data-stu-id="cf931-134">Email Detail Flyout</span></span>
<span data-ttu-id="cf931-135">送信者と受信者の個々のタグを表示するには、件名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf931-135">To view the individual tags for sender and Recipient, click on the subject.</span></span> <span data-ttu-id="cf931-136">メッセージ詳細のポップアップを開きます。</span><span class="sxs-lookup"><span data-stu-id="cf931-136">It opens the message details flyout.</span></span> <span data-ttu-id="cf931-137">[概要] タブでは、送信者と受信者のタグが電子メールに指定されている場合は個別に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-137">In the summary tab, sender and recipient tags are shown separately, if they are present for an email.</span></span>
<span data-ttu-id="cf931-138">送信者と受信者の個々のタグに関する情報は、エクスポートされた CSV にも拡張されており、これらの詳細を2つの別個の列に表示できます。</span><span class="sxs-lookup"><span data-stu-id="cf931-138">The information about individual tags for sender and Recipient, also extends to exported CSV, where you can see these details in 2 separate columns.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-139">![メール詳細タグ](../../media/tags-flyout.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-139">![Email Details Tags](../../media/tags-flyout.png)</span></span>

<span data-ttu-id="cf931-140">タグ情報は、URL クリックのポップアップにも表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-140">Tags information is also shown in URL clicks flyout.</span></span> <span data-ttu-id="cf931-141">URL クリックのポップアップを表示するには、フィッシングまたは [すべての電子メール] ビューに移動し、[url] または [URL] をクリックする必要があります。個々の URL ポップアップをクリックすると、その URL のクリックに関する詳細が表示され、そのクリックに関連付けられたタグが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-141">To get to the URL clicks flyout, you would need to go to Phish or All Email view, and then to URLs or URL Clicks Tab. Clicking on an individual URL flyout would show more details about Clicks for that URL, and would have Tags associated with that click.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-142">![URL タグ](../../media/tags-urls.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-142">![URL Tags](../../media/tags-urls.png)</span></span>

## <a name="improvements-to-threat-hunting-experience-upcoming"></a><span data-ttu-id="cf931-143">脅威の探し方の向上 (近日予定)</span><span class="sxs-lookup"><span data-stu-id="cf931-143">Improvements to Threat Hunting Experience (upcoming)</span></span>

### <a name="updated-threat-information-for-emails"></a><span data-ttu-id="cf931-144">電子メールの脅威情報の更新</span><span class="sxs-lookup"><span data-stu-id="cf931-144">Updated Threat Information for Emails</span></span>

<span data-ttu-id="cf931-145">メールレコードのデータの正確性と一貫性を向上させるために、プラットフォームとデータ品質の向上に重点を置いています。</span><span class="sxs-lookup"><span data-stu-id="cf931-145">We have focused on platform and data quality improvements to increase data accuracy and consistency for email records.</span></span> <span data-ttu-id="cf931-146">これらの更新のセットには、配信前および配布後の情報 (ZAP プロセスの一部として実行されるアクションの例) が、スパム verdict、エンティティレベルの脅威 (悪意のある URL など)、および最新の配信場所と共に1つのレコードに統合されています。</span><span class="sxs-lookup"><span data-stu-id="cf931-146">These set of updates includes consolidation of pre-delivery and post-delivery information (example action executed on an email as part of ZAP process) into a single record  along with added richness like Spam verdict, Entity level threats (e.g., which URL was malicious) and latest delivery locations.</span></span>

<span data-ttu-id="cf931-147">これらの更新プログラムを適用すると、メッセージに対して実行されたさまざまな配信後イベントに関係なく、各メッセージに対して1つのエントリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-147">After these updates, you'll see a single entry for each message, regardless of the different post-delivery events that have taken place on the message.</span></span> <span data-ttu-id="cf931-148">アクションには、ZAP、手動による修復 (管理者のアクションを意味する)、動的配信などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cf931-148">Actions can include ZAP, Manual Remediation (which means admin action), Dynamic Delivery etc.</span></span>

<span data-ttu-id="cf931-149">マルウェアとフィッシングの脅威を示すだけでなく、電子メールに関連付けられているスパム verdict を表示できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="cf931-149">In addition to showing malware and phish threats, you'll now be able to see spam verdict associated with an email.</span></span> <span data-ttu-id="cf931-150">電子メール内では、電子メールに関連付けられているすべての脅威と対応する検出テクノロジが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-150">Within the email, you will be able to see all the threats associated with the email along with the corresponding detection technologies.</span></span> <span data-ttu-id="cf931-151">各電子メールには、0、1、または複数の脅威を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-151">Each email can have 0, 1, or multiple threats.</span></span> <span data-ttu-id="cf931-152">現在の脅威が、電子メールのポップアップの [詳細] セクションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-152">You'll see the current Threats in the Details section of the Email flyout.</span></span> <span data-ttu-id="cf931-153">さらに、複数の脅威 (マルウェアとフィッシングの両方を持つ電子メールなど) については、検出技術フィールドは Threat-Detection マッピングを提供します。つまり、どの検出技術が脅威の識別につながったかを示します。</span><span class="sxs-lookup"><span data-stu-id="cf931-153">Additionally, for multiple threats (e.g., an email having both Malware and Phish), Detection tech field would give the Threat-Detection mapping, meaning which detection tech led to the identification of the Threat.</span></span>

<span data-ttu-id="cf931-154">検出テクノロジのセットは、新しい検出方法、スパム検出テクノロジ、およびあらゆる種類の電子メールビュー (マルウェア、フィッシング、すべての電子メール) にわたって更新されました。結果をフィルター処理するには、同じ一貫性のある検出テクノロジを使用してください。</span><span class="sxs-lookup"><span data-stu-id="cf931-154">The set of detection technologies has been updated to include new detection methods, as well as spam detection technologies, and across all the different email views (Malware, Phish, All Email), you'll have the same, consistent set of Detection technologies to filter the results.</span></span>

> [!NOTE]
> <span data-ttu-id="cf931-155">Verdict 分析は、必ずしもエンティティに関連付けられているとは限りません。</span><span class="sxs-lookup"><span data-stu-id="cf931-155">Verdict analysis might not necessarily be tied to entities.</span></span> <span data-ttu-id="cf931-156">例として、電子メールがフィッシングまたはスパムとして分類される場合がありますが、フィッシング/スパム verdict がスタンプされている Url はありません。</span><span class="sxs-lookup"><span data-stu-id="cf931-156">As an example, an email might be classified as Phish or Spam, but there are no URLs which have any Phish/Spam verdict stamped on them.</span></span> <span data-ttu-id="cf931-157">これは、フィルターによって、verdict を割り当てる前に、電子メールのコンテンツやその他の詳細を評価するからです。</span><span class="sxs-lookup"><span data-stu-id="cf931-157">This is because our filters also evaluate content and other details for an email, before assigning a verdict.</span></span>

#### <a name="threats-in-urls"></a><span data-ttu-id="cf931-158">Url での脅威</span><span class="sxs-lookup"><span data-stu-id="cf931-158">Threats in URLs</span></span>

<span data-ttu-id="cf931-159">[電子メール] ポップアップ-> Details] タブでは、URL に関する特定の脅威を表示できるようになりました (URL がマルウェア、フィッシング、スパム、または None になる可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="cf931-159">Within email flyout-> Details tab, you would now be able to see the specific threat for a URL (Threat for a URL can be Malware, Phish, Spam or None)</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-160">![URL の脅威](../../media/URL_Threats.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-160">![URL Threats](../../media/URL_Threats.png)</span></span>

### <a name="updated-timeline-view-upcoming"></a><span data-ttu-id="cf931-161">タイムラインビューが更新されました (予定あり)</span><span class="sxs-lookup"><span data-stu-id="cf931-161">Updated Timeline View (upcoming)</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-162">![タイムラインビューの更新](../../media/Email_Timeline.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-162">![Updated Timeline View](../../media/Email_Timeline.png)</span></span>

<span data-ttu-id="cf931-163">すべての配信イベントと配信後イベントを識別するだけでなく、タイムラインビューには、その時点で識別された、これらのイベントのサブセットがある脅威に関する情報も表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-163">In addition to identifying all delivery and post-delivery events, timeline view also gives information about the Threat identified at that point of time for a subset of these events.</span></span> <span data-ttu-id="cf931-164">また、その操作の結果と共に、追加のアクション (ZAP、手動による修復など) に関する情報も提供します。</span><span class="sxs-lookup"><span data-stu-id="cf931-164">It also gives you more information about Additional Actions (e.g., ZAP, Manual Remediation) along with the Result of that action.</span></span> <span data-ttu-id="cf931-165">[タイムライン] ビューには、元の配信に関する情報と、その後、電子メールに対して実行された配信後イベントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cf931-165">Timeline view contains information about the Original delivery and subsequently any post-delivery events performed on an email.</span></span>

- <span data-ttu-id="cf931-166">ソース: イベントのソースに基づいて、管理/システム/ユーザーになることができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-166">Source: This can be Admin/System/user based on what was the source of the event.</span></span>
- <span data-ttu-id="cf931-167">イベント: これには、元の配信、手動による修復、ZAP、送信、動的配信などの最上位レベルのイベントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cf931-167">Event: This includes top-level events like Original Delivery, Manual Remediation, ZAP, Submissions, and Dynamic Delivery.</span></span>
- <span data-ttu-id="cf931-168">アクション: ZAP または管理操作 (たとえば、ソフト削除) の一部として実行された特定のアクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cf931-168">Action: This covers the specific action that was taken either as part of ZAP or Admin Action (e.g., Soft Delete).</span></span>
- <span data-ttu-id="cf931-169">脅威: その時点で特定された脅威 (マルウェア、フィッシング、スパム) について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf931-169">Threats: Covers the threats (Malware, Phish, Spam) identified at that point of time.</span></span>
- <span data-ttu-id="cf931-170">結果/詳細: アクションの結果に関する詳細情報を、ZAP/管理アクションの一部として実行されたかどうかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cf931-170">Result/Details: Covers more information about the Result of the Action, whether it was performed as part of ZAP/Admin Action.</span></span>

### <a name="original-and-latest-delivery-location"></a><span data-ttu-id="cf931-171">元の配信場所と最新の配信場所</span><span class="sxs-lookup"><span data-stu-id="cf931-171">Original and Latest Delivery location</span></span>

<span data-ttu-id="cf931-172">今日では、電子メールのグリッドとメールのポップアップに、配信場所を公開しています。</span><span class="sxs-lookup"><span data-stu-id="cf931-172">Today, we surface delivery Location within email grid and email flyout.</span></span> <span data-ttu-id="cf931-173">今後は、配信場所フィールドの名前が元の配信場所に変更されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-173">Going forward, the Delivery Location field will be renamed to Original Delivery Location.</span></span> <span data-ttu-id="cf931-174">さらに、最新の配信場所と呼ばれる別のフィールドも導入しています。</span><span class="sxs-lookup"><span data-stu-id="cf931-174">Additionally, we're also introducing another field called Latest delivery location.</span></span>

<span data-ttu-id="cf931-175">元の配信場所には、最初にメールが配信された場所に関する詳細情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-175">The original delivery location would give more information about where an email was delivered initially.</span></span> <span data-ttu-id="cf931-176">最新の配信場所には、ZAP または [ **削除済みアイテムに移動する** などの管理者アクションのようなシステムアクションの後にメールが追加される場所が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cf931-176">The latest delivery location would include location where an email may have landed after system actions like ZAP or admin actions like **Move to Deleted Items**.</span></span> <span data-ttu-id="cf931-177">最新の配信場所は、メッセージの最後の既知の場所の配信後、またはシステムまたは管理アクションを管理者に通知することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="cf931-177">Latest delivery location is intended to inform admins of the message's last known location post-delivery or any system/admin actions.</span></span> <span data-ttu-id="cf931-178">設計上、電子メールにはエンドユーザー関連のアクションは含まれません。</span><span class="sxs-lookup"><span data-stu-id="cf931-178">By design, it doesn't include any end-user-related actions on the email.</span></span> <span data-ttu-id="cf931-179">たとえば、ユーザーがメッセージを削除したり、メッセージをアーカイブ/pst に移動したりした場合、メッセージ "配信" の場所は更新されません。</span><span class="sxs-lookup"><span data-stu-id="cf931-179">For example: if a user deletes a message or moves the message to archive/pst, the message "delivery" location will not be updated.</span></span> <span data-ttu-id="cf931-180">ただし、システムアクションによって場所が更新された場合 (たとえば、電子メールの検疫の移動中に ZAP が発生した場合)、最新の配信場所が検疫として表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-180">However, if a system action updated the location (e.g., ZAP resulting in an email moving to Quarantine), you would see the Latest delivery location as Quarantine.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-181">![更新された配信場所](../../media/Updated_Delivery_Location.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-181">![Updated Delivery Locations](../../media/Updated_Delivery_Location.png)</span></span>

> [!NOTE]
> <span data-ttu-id="cf931-182">配信場所と配信アクションが値として ' Unknown ' を表示する場合があります。</span><span class="sxs-lookup"><span data-stu-id="cf931-182">There are few cases where Delivery Location and Delivery Action may show 'Unknown' as the value:</span></span>
>
> - <span data-ttu-id="cf931-183">配信場所が配信され、配信場所が不明として表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="cf931-183">You might see Delivery location as Delivered, and Delivery Location as Unknown.</span></span> <span data-ttu-id="cf931-184">これはメッセージが配信されたときに、受信トレイルールによって、受信トレイまたは迷惑メールフォルダーではなく、既定のフォルダー (下書き、アーカイブなど) にメッセージが移動されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="cf931-184">This happens when the message was delivered, but an Inbox rule moved the message to a default folder (Draft, Archive, etc.) instead of the Inbox or Junk Email folders.</span></span>
>
> - <span data-ttu-id="cf931-185">管理者/システムアクション (ZAP、管理アクションなど) が試行されても、メッセージが見つからない場合、最新の配信場所が不明になることがあります。</span><span class="sxs-lookup"><span data-stu-id="cf931-185">Latest Delivery Location can be unknown if an admin/system action (e.g., ZAP, Admin Action) is attempted, but the message isn't found.</span></span> <span data-ttu-id="cf931-186">通常、このアクションは、ユーザーがメッセージを移動または削除した後に発生します。</span><span class="sxs-lookup"><span data-stu-id="cf931-186">Typically, the action happens after the user has moved or deleted the Message.</span></span> <span data-ttu-id="cf931-187">そのような場合は、タイムラインビューの [結果/詳細] 列を確認します。</span><span class="sxs-lookup"><span data-stu-id="cf931-187">In such cases, verify the Result/Details Column in timeline view.</span></span> <span data-ttu-id="cf931-188">メッセージ: ユーザーによって移動または削除されたメッセージを探します。</span><span class="sxs-lookup"><span data-stu-id="cf931-188">Look for the message: Message moved or deleted by the user.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-189">![タイムラインの配信場所](../../media/Updated_Timeline_Delivery_Location.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-189">![Delivery Locations for Timeline](../../media/Updated_Timeline_Delivery_Location.png)</span></span>

### <a name="additional-actions"></a><span data-ttu-id="cf931-190">追加のアクション</span><span class="sxs-lookup"><span data-stu-id="cf931-190">Additional Actions</span></span>

<span data-ttu-id="cf931-191">追加のアクションは、電子メールの配信を投稿した後のアクションによって構成されます。また、ZAP、手動による修復 (管理者によって実行されたアクションなど)、動的配信、および再処理 (メールが遡及的に有効として検出された場合) を含むことができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-191">Additional Actions consist of the actions that were applied post the delivery of the Email, and can include ZAP, Manual Remediation (action taken by an Admin e.g., Soft Delete), Dynamic Delivery, and Reprocessed (an email was retroactively detected as good).</span></span>

> [!NOTE]
>
> - <span data-ttu-id="cf931-192">この変更の一環として、配信アクションフィルターに現在表示されていた削除済みの ZAP 値が消えることがあります。</span><span class="sxs-lookup"><span data-stu-id="cf931-192">As part of this change, the Removed by ZAP value currently surfaced in the Delivery Action filter is going away.</span></span> <span data-ttu-id="cf931-193">追加のアクションを通じて、ZAP によるすべての電子メールを検索する方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="cf931-193">You'll have a way to search for all email with the ZAP attempt through the Additional Actions.</span></span>
>
> - <span data-ttu-id="cf931-194">検出テクノロジとその他のアクションについては、新しいフィールドと値が追加されています (特に ZAP シナリオの場合)。</span><span class="sxs-lookup"><span data-stu-id="cf931-194">There will be new fields and values for Detection technologies and Additional actions (especially for ZAP scenarios).</span></span> <span data-ttu-id="cf931-195">既存の保存済みのクエリと追跡されたクエリを評価して、新しい値で動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="cf931-195">Evaluate your existing Saved Queries and Tracked queries to make sure they work with the new values.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-196">![エクスプローラーでの追加のアクション](../../media/Additional_Actions.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-196">![Additional Actions in Explorer](../../media/Additional_Actions.png)</span></span>

### <a name="system-overrides"></a><span data-ttu-id="cf931-197">システムの上書き</span><span class="sxs-lookup"><span data-stu-id="cf931-197">System overrides</span></span>

<span data-ttu-id="cf931-198">システムのオーバーライドは、システムによって提供される配信場所 (フィルター処理スタックによって識別された脅威やその他の検出に基づいて) をオーバーライドすることによって、メッセージの目的の配信場所に例外を持たせる方法です。</span><span class="sxs-lookup"><span data-stu-id="cf931-198">System overrides are a method of making exceptions to the intended delivery location of a message by overriding the delivery location provided by system (based on the threats and other detections identified by our filtering stack).</span></span> <span data-ttu-id="cf931-199">ポリシーによって提案されたとおりにメッセージを配信するには、テナントポリシーまたはユーザーポリシーを使用してシステムのオーバーライドを設定できます。</span><span class="sxs-lookup"><span data-stu-id="cf931-199">System overrides can be set through tenant or user policy to deliver the message as suggested by the policy.</span></span> <span data-ttu-id="cf931-200">上書きは、構成のギャップ (たとえば、ユーザーが設定した非常に幅広い安全な送信者ポリシー) によって、悪意のあるメッセージの不要な配信を識別するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="cf931-200">Overrides are useful in identifying any unintentional delivery of malicious messages due to configurations gaps (for example, a very broad Safe Sender policy set by a user).</span></span> <span data-ttu-id="cf931-201">オーバーライドする値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cf931-201">These override values can be:</span></span>

- <span data-ttu-id="cf931-202">ユーザーポリシーによって許可: これは、ユーザーがメールボックスレベルでポリシーを作成してドメインまたは送信者を許可する場合です。</span><span class="sxs-lookup"><span data-stu-id="cf931-202">Allowed by user policy: This is when a user allows domains or senders by creating policies at the mailbox level.</span></span>
- <span data-ttu-id="cf931-203">ユーザーポリシーによってブロック: これは、ユーザーがメールボックスレベルでポリシーを作成してドメインまたは送信者をブロックする場合です。</span><span class="sxs-lookup"><span data-stu-id="cf931-203">Blocked by user policy: This is when a user blocks domains or senders by creating policies at the mailbox level.</span></span>
- <span data-ttu-id="cf931-204">組織のポリシーによって許可: 組織のセキュリティチームがポリシーまたは Exchange メールフロールール (トランスポートルールとも呼ばれます) を設定して、組織内のユーザーに送信者とドメインを許可する場合。</span><span class="sxs-lookup"><span data-stu-id="cf931-204">Allowed by org policy: This is when the organization's security teams set policies or Exchange mail flow rules (also known as transport rules) to allow senders and domains for users in their organization.</span></span> <span data-ttu-id="cf931-205">これは、一連のユーザーまたは組織全体に対して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-205">This can be for a set of users or the entire organization.</span></span>
- <span data-ttu-id="cf931-206">組織のポリシーによってブロックされます。これは、組織のセキュリティチームが、組織内のユーザーに対して送信者、ドメイン、メッセージの言語、または送信元の Ip アドレスをブロックするポリシーまたはメールフロールールを設定する場合です。</span><span class="sxs-lookup"><span data-stu-id="cf931-206">Blocked by org policy: This is when the organization's security teams set policies or mail flow rules to block senders, domains, message languages, or source IPs for users in their organization.</span></span> <span data-ttu-id="cf931-207">これは、一連のユーザーまたは組織全体に対しても可能です。</span><span class="sxs-lookup"><span data-stu-id="cf931-207">This can also be for a set of users or the entire organization.</span></span>
- <span data-ttu-id="cf931-208">組織のポリシーによってブロックされているファイル拡張子: これは、ファイルの種類の拡張子がマルウェア対策ポリシー設定を使用して組織のセキュリティチームによってブロックされる場合です。</span><span class="sxs-lookup"><span data-stu-id="cf931-208">File extension blocked by org policy: This is when a file type extension is blocked by the security teams of an organization through the anti-malware policy settings.</span></span> <span data-ttu-id="cf931-209">これらの値は、調査に役立つように、メールの詳細に表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="cf931-209">These values will now be displayed in email details to help with investigations.</span></span> <span data-ttu-id="cf931-210">Secops teams では、リッチフィルター処理機能を使用して、ブロックするファイル拡張子に対してフィルターを適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="cf931-210">Secops teams can also filter on blocked file extensions using the rich filtering capability.</span></span>

<span data-ttu-id="cf931-211">[![エクスプローラーでのシステムのオーバーライド](../../media/System_Overrides.png)](../../media/System_Overrides.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="cf931-211">[![System Overrides in Explorer](../../media/System_Overrides.png)](../../media/System_Overrides.png#lightbox)</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-212">![エクスプローラーでのシステムオーバーライドグリッド](../../media/System_Overrides_Grid.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-212">![System Overrides Grid in Explorer](../../media/System_Overrides_Grid.png)</span></span>

### <a name="improvements-around-url-and-clicks-experience"></a><span data-ttu-id="cf931-213">URL とクリックの動作に関する機能強化</span><span class="sxs-lookup"><span data-stu-id="cf931-213">Improvements around URL and Clicks Experience</span></span>

<span data-ttu-id="cf931-214">URL と URL をクリックすると、次のような機能が強化されました。</span><span class="sxs-lookup"><span data-stu-id="cf931-214">The set of improvements focused towards URL and URL clicks data include:</span></span>

- <span data-ttu-id="cf931-215">Url のポップアップセクションのクリックセクション内に、完全にクリックされた URL (URL の一部であるすべてのクエリパラメーターを含む) を表示します。</span><span class="sxs-lookup"><span data-stu-id="cf931-215">Showing full Clicked URL (including any query Parameters which are part of URL) within the Clicks Section in URL Flyout.</span></span> <span data-ttu-id="cf931-216">現在、URL ドメインとパスがタイトルバーに表示されています。</span><span class="sxs-lookup"><span data-stu-id="cf931-216">Currently we show the URL domain and path in title bar.</span></span> <span data-ttu-id="cf931-217">この情報を拡張して、完全な URL を表示しています。</span><span class="sxs-lookup"><span data-stu-id="cf931-217">We're extending that information to show the full URL.</span></span>

- <span data-ttu-id="cf931-218">Url フィルター (url、url ドメイン、URL ドメイン、パス) にわたる修正: URL を含むメッセージを検索し、[verdict] をクリックして更新を行いました。</span><span class="sxs-lookup"><span data-stu-id="cf931-218">Fixes across URL filters (URL vs URL domain vs URL Domain and path): We've made updates around searching for messages that contain a URL/Click verdict.</span></span> <span data-ttu-id="cf931-219">その一環として、プロトコルに依存しない検索のサポートが有効になっています (つまり、http を使用せずに URL を直接検索できます)。</span><span class="sxs-lookup"><span data-stu-id="cf931-219">As part of that, we've enabled support for protocol agnostic searches (meaning, you can directly search for a URL without http).</span></span> <span data-ttu-id="cf931-220">既定では、URL 検索は明示的に指定されていない限り、http にマップされます。</span><span class="sxs-lookup"><span data-stu-id="cf931-220">By default, the URL search maps to http, unless explicitly specified.</span></span> <span data-ttu-id="cf931-221">例:</span><span class="sxs-lookup"><span data-stu-id="cf931-221">For example:</span></span>

  1. <span data-ttu-id="cf931-222">`http://`"Url"、"URL ドメイン"、および "url のドメインとパス" の各フィルターフィールドで、プレフィックスの有無にかかわらず検索します。</span><span class="sxs-lookup"><span data-stu-id="cf931-222">Search with and without the `http://` prefix in "URL", "URL Domain", and "URL Domain and Path" filter fields.</span></span> <span data-ttu-id="cf931-223">この動作は一貫しており、同じ結果を表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf931-223">This behavior is consistent, and should show the same result.</span></span>

  1. <span data-ttu-id="cf931-224">`https://`"URL" でプレフィックスを検索します。</span><span class="sxs-lookup"><span data-stu-id="cf931-224">Search for the `https://` prefix in "URL".</span></span> <span data-ttu-id="cf931-225">指定しない場合、 `http://` プレフィックスが想定されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-225">When not present, the `http://` prefix is assumed.</span></span>

  1. <span data-ttu-id="cf931-226">`/` "URL パス"、"URL ドメイン"、"URL のドメインとパス" の各フィールドは無視されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-226">`/` in beginning and end of the "URL path", "URL Domain", "URL domain and path" fields is ignored.</span></span> <span data-ttu-id="cf931-227">`/` "URL" フィールドの最後は無視されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-227">`/` at the end of the "URL" field is ignored.</span></span>

### <a name="phish-confidence-level"></a><span data-ttu-id="cf931-228">フィッシングの信頼度</span><span class="sxs-lookup"><span data-stu-id="cf931-228">Phish Confidence Level</span></span>

<span data-ttu-id="cf931-229">フィッシング信頼度は、電子メールがフィッシングとして分類された信頼度を識別するのに役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="cf931-229">Phish confidence level helps to identify the degree of confidence, with which an email was categorized as Phish.</span></span> <span data-ttu-id="cf931-230">2つの値は、High と Normal です。</span><span class="sxs-lookup"><span data-stu-id="cf931-230">The two possible values are High and Normal.</span></span> <span data-ttu-id="cf931-231">初期段階では、このフィルターは、脅威エクスプローラーのフィッシングビューでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="cf931-231">In the initial stages, this filter will be available only in the Phish view of Threat Explorer.</span></span>

<span data-ttu-id="cf931-232">[![エクスプローラーでのフィッシング信頼レベル](../../media/Phish_Confidence_Level.png)](../../media/Phish_Confidence_Level.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="cf931-232">[![Phish Confidence Level in Explorer](../../media/Phish_Confidence_Level.png)](../../media/Phish_Confidence_Level.png#lightbox)</span></span>

### <a name="zap-url-signal"></a><span data-ttu-id="cf931-233">ZAP URL 信号</span><span class="sxs-lookup"><span data-stu-id="cf931-233">ZAP URL Signal</span></span>

<span data-ttu-id="cf931-234">通常、電子メールがフィッシングと識別され、配信後に削除された ZAP フィッシング Alert シナリオに使用されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-234">Typically used for ZAP Phish Alert scenarios where an email was identified as Phish and removed after delivery.</span></span> <span data-ttu-id="cf931-235">これは、通知をエクスプローラーで対応する結果に接続するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-235">This is used to connect the alert with the corresponding results in Explorer.</span></span> <span data-ttu-id="cf931-236">通知の IOCs の1つです。</span><span class="sxs-lookup"><span data-stu-id="cf931-236">It is one of the IOCs for the alert.</span></span>

<span data-ttu-id="cf931-237">探しているプロセスの改善の一環として、脅威エクスプローラーとリアルタイム検出にいくつかの更新プログラムを適用しました。</span><span class="sxs-lookup"><span data-stu-id="cf931-237">As part of improving the hunting process, we have made a few updates to Threat Explorer and Real-time detections.</span></span> <span data-ttu-id="cf931-238">これらの機能が向上しており、探し方がより一貫しています。</span><span class="sxs-lookup"><span data-stu-id="cf931-238">These are 'experience' improvements, with the focus on making the hunting experience more consistent.</span></span> <span data-ttu-id="cf931-239">これらの変更について、以下に説明します。</span><span class="sxs-lookup"><span data-stu-id="cf931-239">These changes are outlined below:</span></span>

- [<span data-ttu-id="cf931-240">タイムゾーンの向上</span><span class="sxs-lookup"><span data-stu-id="cf931-240">Timezone improvements</span></span>](#timezone-improvements)
- [<span data-ttu-id="cf931-241">更新プロセスでの更新</span><span class="sxs-lookup"><span data-stu-id="cf931-241">Update in the Refresh process</span></span>](#update-in-the-refresh-process)
- [<span data-ttu-id="cf931-242">フィルターに追加するグラフのドリルダウン</span><span class="sxs-lookup"><span data-stu-id="cf931-242">Chart drilldown to add to filters</span></span>](#chart-drilldown-to-add-to-filters)
- [<span data-ttu-id="cf931-243">製品情報の更新</span><span class="sxs-lookup"><span data-stu-id="cf931-243">In product information updates</span></span>](#in-product-information-updates)

### <a name="filter-by-user-tags"></a><span data-ttu-id="cf931-244">ユーザータグによるフィルター</span><span class="sxs-lookup"><span data-stu-id="cf931-244">Filter by user tags</span></span>

<span data-ttu-id="cf931-245">システムまたはカスタムユーザータグを使用して並べ替えとフィルター処理を行うことで、脅威の範囲をすばやく把握できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="cf931-245">You can now sort and filter by either system or custom user tags, to quickly grasp the scope of threats.</span></span> <span data-ttu-id="cf931-246">詳細については、「 [ユーザータグ](user-tags.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf931-246">See [User tags](user-tags.md) to learn more.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf931-247">ユーザータグによるフィルター処理と並べ替えは、現在、パブリックプレビュー表示されています。</span><span class="sxs-lookup"><span data-stu-id="cf931-247">Filtering and sorting by user tags is currently in public preview.</span></span>
> <span data-ttu-id="cf931-248">商用リリース前に大幅に変更されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cf931-248">It may be substantially modified before it's commercially released.</span></span> <span data-ttu-id="cf931-249">Microsoft は、提供された情報に関して、明示的または黙示的な保証を行いません。</span><span class="sxs-lookup"><span data-stu-id="cf931-249">Microsoft makes no warranties, express or implied, with respect to the information provided about it.</span></span>

![Explorer の [Tags] 列](../../media/threat-explorer-tags.png)

### <a name="timezone-improvements"></a><span data-ttu-id="cf931-251">タイムゾーンの向上</span><span class="sxs-lookup"><span data-stu-id="cf931-251">Timezone improvements</span></span>

<span data-ttu-id="cf931-252">ポータル内の電子メールレコードのタイムゾーン、およびエクスポートされたデータのタイムゾーンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-252">You will see the timezone for the email records within the Portal, as well as for Exported data.</span></span> <span data-ttu-id="cf931-253">タイムゾーンは、電子メールグリッド、詳細ポップアップ、電子メールのタイムライン、類似の電子メールなどのエクスペリエンス間で表示されるので、結果セットのタイムゾーンはユーザーに対してクリアされます。</span><span class="sxs-lookup"><span data-stu-id="cf931-253">The timezone will be visible across experiences like Email Grid, Details Flyout, Email Timeline, and Similar Emails, so that the timezone for the result set is clear to the user.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-254">![エクスプローラーでのタイムゾーンの表示](../../media/TimezoneImprovements.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-254">![View Timezone in Explorer](../../media/TimezoneImprovements.png)</span></span>

### <a name="update-in-the-refresh-process"></a><span data-ttu-id="cf931-255">更新プロセスでの更新</span><span class="sxs-lookup"><span data-stu-id="cf931-255">Update in the Refresh process</span></span>

<span data-ttu-id="cf931-256">自動更新 (日付の変更、ページの更新)、手動更新 (他のフィルターの場合) との混同に関するフィードバックをお寄せください。</span><span class="sxs-lookup"><span data-stu-id="cf931-256">We have heard feedback around confusion with automatic refresh (e.g. for date, as soon as you change the date, the page would refresh) and manual refresh (for other filters).</span></span> <span data-ttu-id="cf931-257">同様に、フィルターを削除すると自動更新になるため、クエリを変更している間に異なるフィルターを変更すると、検索に一貫性がないことがあります。</span><span class="sxs-lookup"><span data-stu-id="cf931-257">Similarly, removing filters leads to automatic refresh, this causes situations where changing the different filters while modifying the query can cause inconsistent search experiences.</span></span> <span data-ttu-id="cf931-258">この問題を解決するには、手動のフィルターメカニズムに移行します。</span><span class="sxs-lookup"><span data-stu-id="cf931-258">To solve this, we are moving to a manual filtering mechanism.</span></span>

<span data-ttu-id="cf931-259">経験の観点から見ると、ユーザーはさまざまなフィルター範囲 (フィルタセット、日付) を適用および削除し、[refresh] ボタンを押して、クエリの定義によって結果をフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="cf931-259">From an experience standpoint, the user can apply and remove the different range of filters (from the filter set, and date), and press the refresh button to filter the results once they are done with defining the query.</span></span> <span data-ttu-id="cf931-260">[更新] ボタンも、画面上で明確に呼び出されるように更新されています。</span><span class="sxs-lookup"><span data-stu-id="cf931-260">The refresh button has also been updated to call it out clearly on the screen.</span></span> <span data-ttu-id="cf931-261">また、この変更に関するツールヒントと製品内のドキュメントも更新しました。</span><span class="sxs-lookup"><span data-stu-id="cf931-261">We have also updated tooltips and in-product documentation around this change.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-262">![[更新] をクリックして結果をフィルター処理する](../../media/ManualRefresh.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-262">![Click on Refresh to filter results](../../media/ManualRefresh.png)</span></span>

### <a name="chart-drilldown-to-add-to-filters"></a><span data-ttu-id="cf931-263">フィルターに追加するグラフのドリルダウン</span><span class="sxs-lookup"><span data-stu-id="cf931-263">Chart drilldown to add to filters</span></span>

<span data-ttu-id="cf931-264">グラフの凡例値をクリックして、その値をフィルターとして追加できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cf931-264">You will now be able to click on the chart legend values to add that value as a filter.</span></span> <span data-ttu-id="cf931-265">なお、上記で説明した変更の一部として結果をフィルター処理するには、[更新] ボタンをクリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf931-265">Note that you will still have to click on the refresh button to filter the results as part of the change described above.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-266">![グラフからフィルター処理するドリルダウン](../../media/ChartDrilldown.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-266">![Drilldown through charts to Filter](../../media/ChartDrilldown.png)</span></span>

### <a name="in-product-information-updates"></a><span data-ttu-id="cf931-267">製品情報の更新</span><span class="sxs-lookup"><span data-stu-id="cf931-267">In product information updates</span></span>

<span data-ttu-id="cf931-268">また、製品内の追加の詳細も表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf931-268">You should also see additional details within the product.</span></span> <span data-ttu-id="cf931-269">たとえば、グリッド内の検索結果の合計数 (下を参照) に加えて、ラベル、エラーメッセージ、および結果セットについての詳細情報を提供するために、ラベルを中心とした改良が行われました。</span><span class="sxs-lookup"><span data-stu-id="cf931-269">For example, the total number of search results within grid (see below), as well as improvements around labels, error messages and tooltips, to give more information around filters, search experience, and result set.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-270">![製品情報の表示](../../media/ProductInfo.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-270">![View In-product Info](../../media/ProductInfo.png)</span></span>

## <a name="extended-capabilities-in-threat-explorer"></a><span data-ttu-id="cf931-271">脅威エクスプローラーの拡張機能</span><span class="sxs-lookup"><span data-stu-id="cf931-271">Extended capabilities in Threat Explorer</span></span>

### <a name="top-targeted-users"></a><span data-ttu-id="cf931-272">上位の対象ユーザー</span><span class="sxs-lookup"><span data-stu-id="cf931-272">Top targeted users</span></span>

<span data-ttu-id="cf931-273">今日は、上位の対象ユーザーの一覧を電子メール用のマルウェアビュー ([上位のマルウェアファミリ] セクション内) に公開しています。</span><span class="sxs-lookup"><span data-stu-id="cf931-273">Today we expose the list of the top targeted users in the Malware View for Emails (within the Top Malware Families section).</span></span> <span data-ttu-id="cf931-274">フィッシングおよびすべての電子メールビューでこのビューを拡張します。上位5つの対象ユーザーと、対応するビューの各ユーザーの試行回数 (たとえば、フィッシングビューの場合はフィッシング試行回数を表示できます) を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-274">We will be extending this view within Phish and All Email views as well, where you will be able to see the top five targeted users along with the number of attempts for each user for the corresponding view (for example, for Phish view you will be able to see the number of Phish attempts).</span></span>
<span data-ttu-id="cf931-275">また、対象ユーザーの一覧を、各電子メールビューのオフライン分析の試行回数に合わせて、3000の制限までエクスポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-275">You will also be able to export the list of targeted users up to a limit of 3000 along with the number of attempts for offline analysis for each email view.</span></span> <span data-ttu-id="cf931-276">それに加えて、[いいえ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cf931-276">In addition to that, selecting No.</span></span> <span data-ttu-id="cf931-277">試行回数 (たとえば、13回以下の場合) では、脅威エクスプローラーでフィルター処理されたビューが開き、電子メールとそのユーザーの脅威の詳細を確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cf931-277">of attempts (for example, 13 attempts below) would open a filtered view in Threat Explorer, so that you can look at more details across emails and threats for that user.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-278">![上位の対象ユーザー](../../media/Top_Targeted_Users.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-278">![Top Targeted Users](../../media/Top_Targeted_Users.png)</span></span>

### <a name="exchange-transport-rules"></a><span data-ttu-id="cf931-279">Exchange トランスポートルール</span><span class="sxs-lookup"><span data-stu-id="cf931-279">Exchange transport rules</span></span>

<span data-ttu-id="cf931-280">データエンリッチメントの一部として、メッセージに適用されたさまざまなトランスポートルールを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="cf931-280">As part of data enrichment, you should also be able to see all the different transport rules which were applied to a message.</span></span> <span data-ttu-id="cf931-281">この情報は、電子メールのグリッドビュー内に表示されます (これを表示するには、グリッドの [列] オプションから [列のオプション] を選択します)、および電子メールの詳細ポップアップを表示します。</span><span class="sxs-lookup"><span data-stu-id="cf931-281">This information will be present within the Email grid view (to view this, select Column options in the grid and add Exchange Transport Rule from the Column options in the grid) as well as Details flyout in the email.</span></span>
<span data-ttu-id="cf931-282">GUID だけでなく、メッセージに適用されたトランスポートルールの名前も表示できます。</span><span class="sxs-lookup"><span data-stu-id="cf931-282">You would be able to see both the GUID as well as the name of the transport rules which were applied to the message.</span></span> <span data-ttu-id="cf931-283">また、トランスポートルールの名前を使用してメッセージを検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="cf931-283">Additionally, you would be able to search for the messages using the name of the transport rule.</span></span> <span data-ttu-id="cf931-284">これは、「Contains」検索であり、部分的な検索を使用して検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="cf931-284">This would be a 'Contains' search which means you will be able to search using partial searches as well.</span></span>

#### <a name="important-note"></a><span data-ttu-id="cf931-285">重要な注意事項:</span><span class="sxs-lookup"><span data-stu-id="cf931-285">Important Note:</span></span>

<span data-ttu-id="cf931-286">ETR の検索と名前の可用性は、自分に割り当てられている特定の役割によって異なります。</span><span class="sxs-lookup"><span data-stu-id="cf931-286">ETR search and name availability would depend on the specific role that has been assigned to you.</span></span> <span data-ttu-id="cf931-287">ETR の名前と検索を表示するには、次の役割/アクセス許可のいずれかを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf931-287">You will need to have one of the following roles/permissions in order to view the ETR names and search.</span></span>  <span data-ttu-id="cf931-288">次の役割が割り当てられていない場合は、トランスポートルールの名前を表示することはできません。また、ETR 名を使用してメッセージを検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="cf931-288">If you do not have any of the following roles assigned to you, you will not be able to see the names of the transport rules, and search for the messages using the ETR names.</span></span> <span data-ttu-id="cf931-289">ただし、電子メールの詳細内に ETR ラベルと GUID 情報が表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="cf931-289">However, you will be able to see the ETR label and GUID information within the Email Details.</span></span> <span data-ttu-id="cf931-290">電子メールのグリッド、電子メールの flyouts、フィルター、エクスポートには影響しません。</span><span class="sxs-lookup"><span data-stu-id="cf931-290">Your other experiences around viewing records in Email Grids, Email flyouts, Filters, and Export are not impacted.</span></span>

- <span data-ttu-id="cf931-291">EXO Only-データ損失防止: すべて</span><span class="sxs-lookup"><span data-stu-id="cf931-291">EXO Only - Data Loss Prevention: All</span></span>
- <span data-ttu-id="cf931-292">EXO Only-O365SupportViewConfig: All</span><span class="sxs-lookup"><span data-stu-id="cf931-292">EXO Only - O365SupportViewConfig: All</span></span>
- <span data-ttu-id="cf931-293">AAD または EXO-Security Admin: All</span><span class="sxs-lookup"><span data-stu-id="cf931-293">AAD or EXO - Security Admin: All</span></span>
- <span data-ttu-id="cf931-294">AAD または EXO-Security Reader: All</span><span class="sxs-lookup"><span data-stu-id="cf931-294">AAD or EXO - Security Reader: All</span></span>
- <span data-ttu-id="cf931-295">EXO Only-トランスポートルール: すべて</span><span class="sxs-lookup"><span data-stu-id="cf931-295">EXO Only - Transport Rules: All</span></span>
- <span data-ttu-id="cf931-296">EXO Only-View-Only 構成: すべて</span><span class="sxs-lookup"><span data-stu-id="cf931-296">EXO Only - View-Only Configuration: All</span></span>

<span data-ttu-id="cf931-297">次に示すように、電子メールグリッド、詳細ポップアップ、およびエクスポートされた CSV 内で、Etr に Name/GUID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-297">Within the email grid, Details flyout, and Exported CSV, the ETRs are presented with a Name/GUID as shown below.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-298">![Exchange トランスポートルール](../../media/ETR_Details.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-298">![Exchange Transport Rules](../../media/ETR_Details.png)</span></span>

### <a name="inbound-connectors"></a><span data-ttu-id="cf931-299">受信コネクタ</span><span class="sxs-lookup"><span data-stu-id="cf931-299">Inbound connectors</span></span>

<span data-ttu-id="cf931-300">コネクタは、Microsoft 365 または Office 365 組織からの電子メールの流れをカスタマイズし、任意のセキュリティ制限または制御を適用できるようにする命令の集合です。</span><span class="sxs-lookup"><span data-stu-id="cf931-300">Connectors are a collection of instructions that customize the way your email flows to and from your Microsoft 365 or Office 365 organization, with the ability to apply any security restriction or controls.</span></span> <span data-ttu-id="cf931-301">脅威エクスプローラーで、メールに関連付けられているコネクタを表示したり、コネクタ名を使用してメールを検索したりすることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="cf931-301">Within Threat Explorer, you will now have the ability to view the connectors which are related to an email as well as search for emails using the connector names.</span></span>
<span data-ttu-id="cf931-302">コネクタの検索は、部分的なキーワード検索でも同様に機能するという点で、' Contains ' です。</span><span class="sxs-lookup"><span data-stu-id="cf931-302">The search for connectors is 'Contains' in nature which means partial keyword searches should work as well.</span></span>
<span data-ttu-id="cf931-303">次に示すように、メインのグリッドビュー、詳細のポップアップ、およびエクスポートされた CSV の中で、名前/GUID 形式でコネクタを表示します。</span><span class="sxs-lookup"><span data-stu-id="cf931-303">Within the Main grid view, the Details flyout, and the Exported CSV, the connectors are shown in the Name/GUID format as shown below:</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-304">![コネクタの詳細](../../media/Connector_Details.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-304">![Connector Details](../../media/Connector_Details.png)</span></span>

## <a name="new-features-in-threat-explorer-and-real-time-detections"></a><span data-ttu-id="cf931-305">脅威エクスプローラおよびリアルタイム検出の新機能</span><span class="sxs-lookup"><span data-stu-id="cf931-305">New features in Threat Explorer and Real-time detections</span></span>

<span data-ttu-id="cf931-306">脅威エクスプローラーとリアルタイム検出に追加された3つの新機能:</span><span class="sxs-lookup"><span data-stu-id="cf931-306">Three new features added into Threat Explorer and Real-time detections:</span></span>

- [<span data-ttu-id="cf931-307">メールヘッダーのプレビューとメール本文のダウンロード</span><span class="sxs-lookup"><span data-stu-id="cf931-307">Preview email header and download email body</span></span>](#preview-email-header-and-download-email-body)
- [<span data-ttu-id="cf931-308">電子メールのタイムライン</span><span class="sxs-lookup"><span data-stu-id="cf931-308">Email timeline</span></span>](#email-timeline)
- [<span data-ttu-id="cf931-309">URL のエクスポートクリックデータ</span><span class="sxs-lookup"><span data-stu-id="cf931-309">Export URL click data</span></span>](#export-url-click-data)

<span data-ttu-id="cf931-310">これらの新機能について、以下に説明します。</span><span class="sxs-lookup"><span data-stu-id="cf931-310">These new features are outlined below.</span></span>

### <a name="preview-email-header-and-download-email-body"></a><span data-ttu-id="cf931-311">メールヘッダーのプレビューとメール本文のダウンロード</span><span class="sxs-lookup"><span data-stu-id="cf931-311">Preview email header and download email body</span></span>

<span data-ttu-id="cf931-312">電子メールヘッダーをプレビューして電子メール本文をダウンロードする機能は、脅威エクスプローラーで利用できる新機能です。</span><span class="sxs-lookup"><span data-stu-id="cf931-312">The ability to preview an email header and download the email body are new features available in Threat Explorer.</span></span> <span data-ttu-id="cf931-313">管理者は、ダウンロードしたヘッダーや電子メールメッセージを分析して脅威を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-313">Admins will be able to analyze downloaded headers/email messages for threats.</span></span> <span data-ttu-id="cf931-314">電子メールメッセージをダウンロードすると情報の公開が危険になる可能性があるため、このプロセスは、役割ベースのアクセス制御 (RBAC) によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-314">Because downloading email messages can risk the exposure of information, this process is controlled by roles-based access control (RBAC).</span></span> <span data-ttu-id="cf931-315">新しい役割である [ *プレビュー*] を別の役割グループ (セキュリティ操作やセキュリティ管理者など) に追加して、すべての電子メールメッセージビューでメールのダウンロードとヘッダーのプレビューを許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf931-315">A new role, *Preview*, must be added to another role group (such as Security Operations or Security Administrator) to grant the ability to download mails and preview headers in all-email messages view.</span></span>

<span data-ttu-id="cf931-316">しかし、エクスプローラー (およびリアルタイム検出) によって新しい新しいフィールドも追加され、電子メールメッセージがどこにいるかをより完全に把握することができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-316">But Explorer (and Real-time detections) also adds fresh new fields designed to give you a more complete picture of where your email messages land.</span></span> <span data-ttu-id="cf931-317">この変更の目的の一環として、セキュリティを確保したユーザーを探しやすくしていますが、最終的に問題の電子メールメッセージの場所がひとめでわかることになります。</span><span class="sxs-lookup"><span data-stu-id="cf931-317">Part of the goal of this change is to make hunting easier for Security Ops people, but the net result is knowing the location of problem email messages at a glance.</span></span>

<span data-ttu-id="cf931-318">実行方法</span><span class="sxs-lookup"><span data-stu-id="cf931-318">How is this done?</span></span> <span data-ttu-id="cf931-319">配信状態は、次の2つの列に分けられました。</span><span class="sxs-lookup"><span data-stu-id="cf931-319">Delivery Status is now broken out into two columns:</span></span>

- <span data-ttu-id="cf931-320">**配信アクション** -この電子メールの状態は何ですか。</span><span class="sxs-lookup"><span data-stu-id="cf931-320">**Delivery Action** - What is the status of this email?</span></span>
- <span data-ttu-id="cf931-321">**配信場所** -この電子メールは、結果としてルーティングされましたか?</span><span class="sxs-lookup"><span data-stu-id="cf931-321">**Delivery Location** - Where was this email routed as a result?</span></span>

<span data-ttu-id="cf931-322">配信アクションは、既存のポリシーまたは検出のために電子メールに対して実行されたアクションです。</span><span class="sxs-lookup"><span data-stu-id="cf931-322">Delivery Action is the action taken on an email due to existing policies or detections.</span></span> <span data-ttu-id="cf931-323">電子メールで実行可能なアクションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cf931-323">Here are the possible actions an email can take:</span></span>

|<span data-ttu-id="cf931-324">届け</span><span class="sxs-lookup"><span data-stu-id="cf931-324">Delivered</span></span>|<span data-ttu-id="cf931-325">Junked</span><span class="sxs-lookup"><span data-stu-id="cf931-325">Junked</span></span>|<span data-ttu-id="cf931-326">Blocked</span><span class="sxs-lookup"><span data-stu-id="cf931-326">Blocked</span></span>|<span data-ttu-id="cf931-327">換わり</span><span class="sxs-lookup"><span data-stu-id="cf931-327">Replaced</span></span>|
|---|---|---|---|
|<span data-ttu-id="cf931-328">電子メールがユーザーの受信トレイまたはフォルダーに配信され、ユーザーが直接アクセスできる。</span><span class="sxs-lookup"><span data-stu-id="cf931-328">Email was delivered to Inbox or folder of a user and the user can directly access it.</span></span>|<span data-ttu-id="cf931-329">電子メールは、ユーザーの迷惑メールフォルダーまたは削除されたフォルダーに送信され、ユーザーはそのフォルダー内のメールにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cf931-329">Email was sent to either user's Junk folder or Deleted folder, and the user has access to emails in those folders.</span></span>|<span data-ttu-id="cf931-330">検疫済み、失敗した、または削除されたメール。</span><span class="sxs-lookup"><span data-stu-id="cf931-330">Any emails that are quarantined, that  failed, or were dropped.</span></span> <span data-ttu-id="cf931-331">ユーザーが完全にアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="cf931-331">This is completely inaccessible by the user!</span></span>|<span data-ttu-id="cf931-332">悪意のある添付ファイルが存在するという悪意のある添付ファイルが .txt ファイルに置き換えられる電子メール。</span><span class="sxs-lookup"><span data-stu-id="cf931-332">Any email where malicious attachments are replaced by .txt files that state the attachment was malicious.</span></span>|

|<span data-ttu-id="cf931-333">届け</span><span class="sxs-lookup"><span data-stu-id="cf931-333">Delivered</span></span>|<span data-ttu-id="cf931-334">Junked</span><span class="sxs-lookup"><span data-stu-id="cf931-334">Junked</span></span>|<span data-ttu-id="cf931-335">Blocked</span><span class="sxs-lookup"><span data-stu-id="cf931-335">Blocked</span></span>|<span data-ttu-id="cf931-336">換わり</span><span class="sxs-lookup"><span data-stu-id="cf931-336">Replaced</span></span>|
|---|---|---|---|
|<span data-ttu-id="cf931-337">電子メールがユーザーの受信トレイまたは別のフォルダーに配信され、ユーザーが直接アクセスできる。</span><span class="sxs-lookup"><span data-stu-id="cf931-337">Email was delivered to the user's inbox or another folder, and the user can directly access it.</span></span>|<span data-ttu-id="cf931-338">電子メールは、ユーザーの迷惑メールフォルダーまたは削除されたフォルダーに送信され、ユーザーはそのフォルダー内の電子メールメッセージにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cf931-338">Email was sent to either user's Junk folder or Deleted folder, and the user has access to email messages in those folders.</span></span>|<span data-ttu-id="cf931-339">検疫された、失敗した、または削除された電子メールメッセージで、ユーザーがアクセスできないメッセージ。</span><span class="sxs-lookup"><span data-stu-id="cf931-339">Any email messages that are quarantined, that failed, or were dropped, and are not accessible by the user.</span></span>|<span data-ttu-id="cf931-340">添付ファイルが悪意のある添付ファイルであることを示す、悪意のある添付ファイルが .txt ファイルに置き換えられた電子メールメッセージ。</span><span class="sxs-lookup"><span data-stu-id="cf931-340">Any email messages where malicious attachments were replaced by .txt files that state the attachments were malicious.</span></span>|
|

<span data-ttu-id="cf931-341">次に、ユーザーが表示できる機能と、それができないことを示します。</span><span class="sxs-lookup"><span data-stu-id="cf931-341">And here is what the user can see, and what they can't:</span></span>

|<span data-ttu-id="cf931-342">エンドユーザーがアクセス可能</span><span class="sxs-lookup"><span data-stu-id="cf931-342">Accessible to end users</span></span>|<span data-ttu-id="cf931-343">エンドユーザーがアクセスできない</span><span class="sxs-lookup"><span data-stu-id="cf931-343">Inaccessible to end users</span></span>|
|---|---|
|<span data-ttu-id="cf931-344">届け</span><span class="sxs-lookup"><span data-stu-id="cf931-344">Delivered</span></span>|<span data-ttu-id="cf931-345">Blocked</span><span class="sxs-lookup"><span data-stu-id="cf931-345">Blocked</span></span>|
|<span data-ttu-id="cf931-346">Junked</span><span class="sxs-lookup"><span data-stu-id="cf931-346">Junked</span></span>|<span data-ttu-id="cf931-347">換わり</span><span class="sxs-lookup"><span data-stu-id="cf931-347">Replaced</span></span>|

<span data-ttu-id="cf931-348">[配信場所] には、配信後に実行されるポリシーと検出の結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-348">Delivery location shows the results of policies and detections that run post-delivery.</span></span> <span data-ttu-id="cf931-349">配信アクションにリンクされています。</span><span class="sxs-lookup"><span data-stu-id="cf931-349">It's linked to a Delivery Action.</span></span> <span data-ttu-id="cf931-350">このフィールドは、問題のメールが検出されたときに実行される処理を把握するために追加されました。</span><span class="sxs-lookup"><span data-stu-id="cf931-350">This field was added to give insight into the action taken when a problem mail is found.</span></span> <span data-ttu-id="cf931-351">配信場所の指定可能な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cf931-351">Here are the possible values of delivery location:</span></span>

- <span data-ttu-id="cf931-352">**受信トレイまたはフォルダー**: 電子メールは、受信トレイまたはフォルダー (メールルールに従って) にあります。</span><span class="sxs-lookup"><span data-stu-id="cf931-352">**Inbox or folder**: The email is in inbox or a folder (according to your email rules).</span></span>
- <span data-ttu-id="cf931-353">**オンプレミスまたは外部**: メールボックスはクラウド上に存在していますが、オンプレミスになっています。</span><span class="sxs-lookup"><span data-stu-id="cf931-353">**On-prem or external**: The mailbox doesn't exist on cloud but is on-premises.</span></span>
- <span data-ttu-id="cf931-354">**迷惑メールフォルダー**: メールはユーザーの [迷惑メール] フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="cf931-354">**Junk folder**: The email is in the Junk folder of a user.</span></span>
- <span data-ttu-id="cf931-355">**削除済みアイテムフォルダー**: ユーザーの [削除済みアイテム] フォルダー内の電子メール。</span><span class="sxs-lookup"><span data-stu-id="cf931-355">**Deleted items folder**: The email in the Deleted items folder of a user.</span></span>
- <span data-ttu-id="cf931-356">**検疫**: 検疫内の電子メールは、ユーザーのメールボックスには含まれません。</span><span class="sxs-lookup"><span data-stu-id="cf931-356">**Quarantine**: The email in quarantine, and is not in a user's mailbox.</span></span>
- <span data-ttu-id="cf931-357">**失敗**: メールがメールボックスに到達できませんでした。</span><span class="sxs-lookup"><span data-stu-id="cf931-357">**Failed**: The email failed to reach the mailbox.</span></span>
- <span data-ttu-id="cf931-358">**削除**: メールフロー内の任意の場所に電子メールが失われます。</span><span class="sxs-lookup"><span data-stu-id="cf931-358">**Dropped**: The email gets lost somewhere in the mail flow.</span></span>

### <a name="email-timeline"></a><span data-ttu-id="cf931-359">電子メールのタイムライン</span><span class="sxs-lookup"><span data-stu-id="cf931-359">Email timeline</span></span>

<span data-ttu-id="cf931-360">**電子メールのタイムライン** は、管理者にとって、探しやすさを向上させるための別の新しいエクスプローラー機能です。</span><span class="sxs-lookup"><span data-stu-id="cf931-360">The **Email Timeline** is another new Explorer feature aimed at making the hunting experience better for admins.</span></span> <span data-ttu-id="cf931-361">イベントを理解するためにさまざまな場所をチェックするのにかかる時間が短くなるため、ランダム化が減少します。</span><span class="sxs-lookup"><span data-stu-id="cf931-361">It cuts down on randomization because there is less time spent checking different locations to try to understand the event.</span></span> <span data-ttu-id="cf931-362">複数のイベントが電子メールで同時に発生するか、または同じ時刻に終了すると、これらのイベントがタイムラインビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-362">When multiple events happen at, or close to, the same time on an email, those events will show up in a timeline view.</span></span> <span data-ttu-id="cf931-363">実際、メールへの配信の後に発生する一部のイベントは、[特殊な操作] 列に記録されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-363">In fact, some events that happen post-delivery to your mail will be captured in the 'Special action' column.</span></span> <span data-ttu-id="cf931-364">メールのタイムラインからの情報をメールの送信後の特別なアクションと組み合わせることにより、管理者は、ポリシーがどのように機能するか、メールが最後にルーティングされたか、場合によっては最終的な評価がどのようなものかを把握できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cf931-364">Combining the information from the timeline of that mail with the special action taken on the mail post-delivery will give admins insight into how their policies work, where the mail was finally routed, and, in some cases, what the final assessment was.</span></span>

<span data-ttu-id="cf931-365">悪意のある電子メールメッセージの調査の詳細については、「 [Office 365 で配信された悪意のある電子メールを調査および修復する](investigate-malicious-email-that-was-delivered.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf931-365">For more discussion about investigating malicious email messages, see [Investigate and remediate malicious email that was delivered in Office 365](investigate-malicious-email-that-was-delivered.md).</span></span>

### <a name="export-url-click-data"></a><span data-ttu-id="cf931-366">URL のエクスポートクリックデータ</span><span class="sxs-lookup"><span data-stu-id="cf931-366">Export URL click data</span></span>

<span data-ttu-id="cf931-367">また、ネットワークメッセージ ID とそのクリック Verdict の両方を表示するために、URL クリックのレポートを Microsoft Excel にエクスポートできるようになりました。これにより、URL のクリック時のトラフィックが簡単になることを理解することができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-367">Also, you will now be able to export reports for URL clicks to Microsoft Excel in order to view both their Network Message ID, and their Click Verdict, making the task of understanding where your URL click traffic originated easier.</span></span> <span data-ttu-id="cf931-368">そのしくみは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cf931-368">Here's how it works.</span></span> <span data-ttu-id="cf931-369">Office 365 のクイック起動での脅威管理の開始で、次のチェーンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf931-369">Starting in Threat Management on the Office 365 quick-launch, click through this chain:</span></span>

<span data-ttu-id="cf931-370">**エクスプローラー** \>**フィッシング** \> の表示 **クリック** \>**上位の url または url の先頭クリック** \>**任意のレコードをクリックして URL フライアウトを開く**</span><span class="sxs-lookup"><span data-stu-id="cf931-370">**Explorer** \> **View Phish** \> **Clicks** \> **Top URLs or URL Top Clicks** \> **Click on any record to open URL flyout**</span></span>

<span data-ttu-id="cf931-371">一覧の URL をクリックすると、フライアウトパネルに新しい [エクスポート] ボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-371">When you click on a URL in the list, you'll see a new Export button on the fly-out panel.</span></span> <span data-ttu-id="cf931-372">このボタンを使用して、レポートを容易にするために、データを Excel スプレッドシートに移動します。</span><span class="sxs-lookup"><span data-stu-id="cf931-372">Use this button to move data to an Excel spreadsheet for easier reporting.</span></span>

<span data-ttu-id="cf931-373">リアルタイムの検出レポートでは、次のように同じ場所にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cf931-373">You can get to the same location in the Real-time detections report as follows:</span></span>

<span data-ttu-id="cf931-374">**エクスプローラー** \>**リアルタイムの検出** \>**フィッシング** \> の表示 **Url** \>**トップの url またはクリック** \>**任意のレコードをクリックして URL フライアウト** \> を開く[**クリック] タブに移動します。**</span><span class="sxs-lookup"><span data-stu-id="cf931-374">**Explorer** \> **Real-time detections** \> **View Phish** \> **URLs** \> **Top URLs or Top Clicks** \> **Click on any record to open URL flyout** \> **Navigate to the Clicks Tab.**</span></span>

> [!TIP]
> <span data-ttu-id="cf931-375">ネットワークメッセージ ID エクスプローラーまたは関連付けられたサードパーティ製のツールでネットワークメッセージ ID を使用して検索したときに、クリックしたを特定のメールにマップします。</span><span class="sxs-lookup"><span data-stu-id="cf931-375">Network Message ID maps the click back to specific mails when you search through Explorer or associated third-party tools via Network Message ID.</span></span> <span data-ttu-id="cf931-376">ネットワークのメッセージ ID を検索すると、クリックの結果に関連付けられた特定の電子メールが管理者に付与されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-376">Searching through the Network Message ID will give admins the specific email associated with a click result.</span></span> <span data-ttu-id="cf931-377">エクスポートでは、ネットワークメッセージ ID の関連付けを識別することによって、より迅速かつ強力な分析を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-377">On export, having the correlating identification of Network Message ID makes for quicker and more powerful analysis.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="cf931-378">![エクスプローラーの [タブ] をクリックします。](../../media/tp_ExportClickResultAndNetworkID.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-378">![Clicks tab in Explorer](../../media/tp_ExportClickResultAndNetworkID.png)</span></span>

## <a name="see-malware-detected-in-email-by-technology"></a><span data-ttu-id="cf931-379">テクノロジによる電子メールで検出されたマルウェアを参照</span><span class="sxs-lookup"><span data-stu-id="cf931-379">See malware detected in email by technology</span></span>

<span data-ttu-id="cf931-380">Microsoft 365 テクノロジを使用して、電子メールで検出されたマルウェアを確認するとします。</span><span class="sxs-lookup"><span data-stu-id="cf931-380">Suppose you want to see malware detected in email, by Microsoft 365 technology.</span></span> <span data-ttu-id="cf931-381">これを行うには、エクスプローラーの [ [電子メール > マルウェア](threat-explorer-views.md#email--malware) ] ビュー (またはリアルタイムの検出) を使用します。</span><span class="sxs-lookup"><span data-stu-id="cf931-381">To do this, use the [Email > Malware](threat-explorer-views.md#email--malware) view of Explorer (or Real-time detections).</span></span>

1. <span data-ttu-id="cf931-382">セキュリティ & コンプライアンスセンター () で <https://protection.office.com> 、[ **脅威管理** \> **エクスプローラー** (または **リアルタイムの検出**)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cf931-382">In the Security & Compliance Center (<https://protection.office.com>), choose **Threat management** \> **Explorer** (or **Real-time detections**).</span></span> <span data-ttu-id="cf931-383">(この例ではエクスプローラーを使用しています)。</span><span class="sxs-lookup"><span data-stu-id="cf931-383">(This example uses Explorer.)</span></span>

2. <span data-ttu-id="cf931-384">[ **表示** ] メニューで、[ **電子メール** \> **マルウェア**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cf931-384">In the **View** menu, choose **Email** \> **Malware**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="cf931-385">![エクスプローラーの [表示] メニュー](../../media/ExplorerViewEmailMalwareMenu.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-385">![View menu for Explorer](../../media/ExplorerViewEmailMalwareMenu.png)</span></span>

3. <span data-ttu-id="cf931-386">[ **送信者**] をクリックし、[ **基本** \> **検出テクノロジ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cf931-386">Click **Sender**, and then choose **Basic** \> **Detection technology**.</span></span>

   <span data-ttu-id="cf931-387">これで、検出テクノロジがレポートのフィルターとして使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cf931-387">Your detection technologies are now available as filters for the report.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="cf931-388">![マルウェア検出テクノロジ](../../media/ExplorerEmailMalwareDetectionTech.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-388">![Malware detection technologies](../../media/ExplorerEmailMalwareDetectionTech.png)</span></span>

4. <span data-ttu-id="cf931-389">オプションを選択し、[ **更新** ] ボタンをクリックしてそのフィルターを適用します。</span><span class="sxs-lookup"><span data-stu-id="cf931-389">Select an option, and then click the **Refresh** button to apply that filter.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="cf931-390">![選択されている検出テクノロジ](../../media/ExplorerEmailMalwareDetectionTechATP.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-390">![Selected detection technology](../../media/ExplorerEmailMalwareDetectionTechATP.png)</span></span>

<span data-ttu-id="cf931-391">レポートが更新され、選択した [テクノロジ] オプションを使用して、電子メールで検出された結果のマルウェアが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-391">The report refreshes to show the results malware detected in email, using the technology option you selected.</span></span> <span data-ttu-id="cf931-392">ここから、さらに分析を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-392">From here, you can conduct further analysis.</span></span>

## <a name="view-data-about-phishing-urls-and-click-verdict"></a><span data-ttu-id="cf931-393">フィッシング Url に関するデータを表示し、[verdict] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf931-393">View data about phishing URLs and click verdict</span></span>

<span data-ttu-id="cf931-394">許可された Url の一覧を含む、電子メール内の Url によるフィッシングの試行、禁止、および上書きを確認するとします。</span><span class="sxs-lookup"><span data-stu-id="cf931-394">Suppose that you want to see phishing attempts through URLs in email, including a list of URLs that were allowed, blocked, and overridden.</span></span> <span data-ttu-id="cf931-395">クリックされた Url を識別するには、 [安全なリンク](atp-safe-links.md) を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf931-395">Identifying URLs that were clicked requires [Safe Links](atp-safe-links.md) to be configured.</span></span> <span data-ttu-id="cf931-396">[安全なリンクを使用して verdicts] をクリックしたときに、 [安全なリンクポリシー](set-up-atp-safe-links-policies.md) が設定されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="cf931-396">Make sure that you have set up [Safe Links policies](set-up-atp-safe-links-policies.md) for time-of-click protection and logging of click verdicts by Safe Links.</span></span>

<span data-ttu-id="cf931-397">メッセージ内のフィッシング Url を確認し、フィッシングメッセージで Url をクリックするには、Explorer の [電子メール > フィッシング](threat-explorer-views.md#email--phish) ビュー (またはリアルタイムの検出) を使用します。</span><span class="sxs-lookup"><span data-stu-id="cf931-397">To review phish URLs in messages and clicks on URLs in phish messages, use the [Email > Phish](threat-explorer-views.md#email--phish) view of Explorer (or Real-time detections).</span></span>

1. <span data-ttu-id="cf931-398">セキュリティ & コンプライアンスセンター () で <https://protection.office.com> 、[ **脅威管理** \> **エクスプローラー** (または **リアルタイムの検出**)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cf931-398">In the Security & Compliance Center (<https://protection.office.com>), choose **Threat management** \> **Explorer** (or **Real-time detections**).</span></span> <span data-ttu-id="cf931-399">(この例ではエクスプローラーを使用しています)。</span><span class="sxs-lookup"><span data-stu-id="cf931-399">(This example uses Explorer.)</span></span>

2. <span data-ttu-id="cf931-400">[**表示**] メニューの [**電子メール** フィッシング] をクリックし \> **Phish** ます。</span><span class="sxs-lookup"><span data-stu-id="cf931-400">In the **View** menu, choose **Email** \> **Phish**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="cf931-401">![フィッシングコンテキストでのエクスプローラーの [表示] メニュー](../../media/ExplorerViewEmailPhishMenu.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-401">![View menu for Explorer in phishing context](../../media/ExplorerViewEmailPhishMenu.png)</span></span>

3. <span data-ttu-id="cf931-402">[ **送信者**] をクリックし、[ **url** ] を選択して、 \> **[verdict] をクリック** します。</span><span class="sxs-lookup"><span data-stu-id="cf931-402">Click **Sender**, and then choose **URLs** \> **Click verdict**.</span></span>

4. <span data-ttu-id="cf931-403">1つまたは複数のオプション ([ **ブロック** されて **ブロック** する] など) を選択し、[ **更新** ] ボタンをクリックして、そのフィルターを適用するオプションと同じ行にあるものをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf931-403">Select one or more options, such as **Blocked** and **Block overridden**, and then click the **Refresh** button that is on the same line as the options to apply that filter.</span></span> <span data-ttu-id="cf931-404">(ブラウザーウィンドウを更新しないでください)。</span><span class="sxs-lookup"><span data-stu-id="cf931-404">(Don't refresh your browser window.)</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="cf931-405">![Url および [verdicts] をクリックします。](../../media/ThreatExplorerEmailPhishClickVerdictOptions.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-405">![URLs and click verdicts](../../media/ThreatExplorerEmailPhishClickVerdictOptions.png)</span></span>

   <span data-ttu-id="cf931-406">レポートが更新され、[URL] タブにレポートの下に2つの異なる URL テーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-406">The report refreshes to show two different URL tables on the URL tab under the report:</span></span>

   - <span data-ttu-id="cf931-407">**トップ url** は、フィルター処理されたメッセージに含まれる url と、各 url の電子メール配信アクション数を示します。</span><span class="sxs-lookup"><span data-stu-id="cf931-407">**Top URLs** are the URLs contained in the messages you have filtered down to, and the email delivery action counts for each URL.</span></span> <span data-ttu-id="cf931-408">[フィッシング email] ビューには、通常、正当な Url が含まれています。</span><span class="sxs-lookup"><span data-stu-id="cf931-408">In the phish email view, this list typically will contain legitimate URLs.</span></span> <span data-ttu-id="cf931-409">攻撃者は、適切な Url と正しくない Url をメッセージに混在させて配信を試みることができますが、ユーザーがクリックすると、悪意のあるリンクがより興味深いものになります。</span><span class="sxs-lookup"><span data-stu-id="cf931-409">Attackers include a mix of good and bad URLs in their messages to try to get them delivered, but they will make the malicious links more interesting for the user to click.</span></span> <span data-ttu-id="cf931-410">Url の表は、電子メールの合計数によって並べ替えられます (ただし、ビューを簡略化するため、この列は非表示になっていることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="cf931-410">The table of URLs is sorted by total email count (but note that this column is hidden to simplify the view).</span></span>

   - <span data-ttu-id="cf931-411">**トップクリック** は、クリックされた url をラップした安全なリンクです。 [合計] をクリックします (この列はビューを簡略化するためにも表示されません)。</span><span class="sxs-lookup"><span data-stu-id="cf931-411">**Top clicks** are the Safe Links wrapped URLs that were clicked, sorted by total click count (this column is also not shown to simplify the view).</span></span> <span data-ttu-id="cf931-412">列別の合計カウント [セーフリンク] は、クリックされた各 URL の [verdict count] を示します。</span><span class="sxs-lookup"><span data-stu-id="cf931-412">Total counts by column indicate the Safe Links click verdict count for each clicked URL.</span></span> <span data-ttu-id="cf931-413">フィッシングの電子メール表示では、多くの場合、疑わしいまたは悪意のある Url になりますが、脅威ではないがフィッシングメッセージ内にある Url を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-413">In the phish email view, these are more often suspicious or malicious URLs, but could include URLs that are not threats but are in phish messages.</span></span> <span data-ttu-id="cf931-414">ラップされていないリンクの URL クリックは表示されません。</span><span class="sxs-lookup"><span data-stu-id="cf931-414">URL clicks on unwrapped links will not show up here.</span></span>

   <span data-ttu-id="cf931-415">2つの URL 表は、配信アクションと場所によって、フィッシング電子メールメッセージの上位の Url を示しています。また、ブロックされた (または警告によってアクセスされた) URL クリックが表示されるので、ユーザーがどのような潜在的なリンクを受信し、ユーザーが操作したかを把握できます。</span><span class="sxs-lookup"><span data-stu-id="cf931-415">The two URL tables show top URLs in phishing email messages by delivery action and location, and they show URL clicks that were blocked (or visited despite a warning) so that you can understand what potential bad links were received by users and interacted with by users.</span></span> <span data-ttu-id="cf931-416">ここから、さらに分析を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-416">From here, you can conduct further analysis.</span></span> <span data-ttu-id="cf931-417">たとえば、グラフの下に、組織の環境でブロックされた電子メールメッセージ内の上位の Url が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-417">For example, below the chart, you can see the top URLs in email messages that were blocked in your organization's environment.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="cf931-418">![ブロックされたエクスプローラーの Url](../../media/ExplorerPhishClickVerdictURLs.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-418">![Explorer URLs that were blocked](../../media/ExplorerPhishClickVerdictURLs.png)</span></span>

   <span data-ttu-id="cf931-419">URL を選択して、詳細情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="cf931-419">Select a URL to view more detailed information.</span></span>

   > [!NOTE]
   > <span data-ttu-id="cf931-420">URL のポップアップダイアログで、電子メールメッセージのフィルター処理が削除され、環境内の URL の公開が完全に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-420">In the URL flyout dialog, the filtering on email messages is removed to show you the full view of the URL's exposure in your environment.</span></span> <span data-ttu-id="cf931-421">これにより、関心のあるメールメッセージをエクスプローラーでフィルター処理し、潜在的な脅威である特定の Url を見つけ、URL フィルターをエクスプローラービュー自体に追加することなく、環境内の URL の公開について理解を深めることができます (URL の詳細ダイアログを使用)。</span><span class="sxs-lookup"><span data-stu-id="cf931-421">This lets you filter down email messages in Explorer to ones you are concerned about, find specific URLs that are potential threats, then expand your understanding of the URL exposure in your environment (via the URL details dialog) without having to add URL filters to the Explorer view itself.</span></span>

### <a name="interpretation-of-different-click-verdicts"></a><span data-ttu-id="cf931-422">さまざまなクリック verdicts の解釈</span><span class="sxs-lookup"><span data-stu-id="cf931-422">Interpretation of different click verdicts</span></span>

<span data-ttu-id="cf931-423">電子メールまたは URL flyouts 内でのトップクリックとフィルタリングエクスペリエンスの範囲内で、お探しのエクスペリエンスの一部として異なるクリック値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-423">Within the Email or URL flyouts, Top Clicks as well as within our filtering experiences, you will see different click values as part of your hunting experience.</span></span> <span data-ttu-id="cf931-424">次に、クリック Verdicts に指定できる値とその解釈を示します。</span><span class="sxs-lookup"><span data-stu-id="cf931-424">Below are the possible values of Click Verdicts and their interpretation:</span></span>

- <span data-ttu-id="cf931-425">**None**: URL の verdict をキャプチャできませんでした。</span><span class="sxs-lookup"><span data-stu-id="cf931-425">**None**: We were unable to capture the verdict for the URL.</span></span> <span data-ttu-id="cf931-426">ユーザーが URL をクリックした可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cf931-426">The user might have clicked through the URL.</span></span>
- <span data-ttu-id="cf931-427">**許可**: ユーザーは URL への移動を許可されました。</span><span class="sxs-lookup"><span data-stu-id="cf931-427">**Allowed**: The user was allowed to navigate to the URL.</span></span>
- <span data-ttu-id="cf931-428">[**ブロック** 済み: ユーザーが URL への移動をブロックされました。</span><span class="sxs-lookup"><span data-stu-id="cf931-428">**Blocked**: The User was blocked from navigating to the URL.</span></span>
- <span data-ttu-id="cf931-429">**保留中の verdict**: ユーザーに分析保留中ページが表示されました。</span><span class="sxs-lookup"><span data-stu-id="cf931-429">**Pending verdict**: The user was presented with the detonation pending page.</span></span>
- <span data-ttu-id="cf931-430">**ブロック** されたオーバーライド: ユーザーは URL への移動をブロックされました。ただし、ユーザーはオーバーライドをブロックして、URL に移動します。</span><span class="sxs-lookup"><span data-stu-id="cf931-430">**Blocked overridden**: The user was blocked from navigating to the URL; however, the user overrode the block to navigate to the URL.</span></span>
- <span data-ttu-id="cf931-431">**Pending verdict バイパス**: ユーザーが分析ページで表示されました。ただし、ユーザーはページをオーバーライドして URL に移動します。</span><span class="sxs-lookup"><span data-stu-id="cf931-431">**Pending verdict bypassed**: The user was presented with the detonation page; however, the user overrode the page to navigate to the URL.</span></span>
- <span data-ttu-id="cf931-432">**エラー**: ユーザーにエラーページが表示されました。</span><span class="sxs-lookup"><span data-stu-id="cf931-432">**Error**: The user was presented with the error page.</span></span> <span data-ttu-id="cf931-433">これは、verdict のキャプチャでエラーが発生したことも意味します。</span><span class="sxs-lookup"><span data-stu-id="cf931-433">This can also mean there was an error in capturing the verdict.</span></span>
- <span data-ttu-id="cf931-434">**失敗**: verdict のキャプチャ中に不明な例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="cf931-434">**Failure**: There was unknown exception while capturing the verdict.</span></span> <span data-ttu-id="cf931-435">ユーザーが URL をクリックした可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cf931-435">The user might have clicked through the URL.</span></span>

## <a name="review-email-messages-reported-by-users"></a><span data-ttu-id="cf931-436">ユーザーが報告した電子メールメッセージを確認する</span><span class="sxs-lookup"><span data-stu-id="cf931-436">Review email messages reported by users</span></span>

<span data-ttu-id="cf931-437">組織内のユーザーが、 [outlook 用のレポートメッセージアドインと web 上の outlook](enable-the-report-message-add-in.md)を使用して、迷惑メールではなく迷惑メールとして報告した電子メールメッセージを表示したいとします。</span><span class="sxs-lookup"><span data-stu-id="cf931-437">Suppose that you want to see email messages that users in your organization have reported as Junk, Not Junk, or Phishing by using the [Report Message add-in for Outlook and Outlook on the web](enable-the-report-message-add-in.md).</span></span> <span data-ttu-id="cf931-438">これを行うには、エクスプローラー (またはリアルタイムの検出) の [電子メール > 提出](threat-explorer-views.md#email--submissions) の表示] を使用します。</span><span class="sxs-lookup"><span data-stu-id="cf931-438">To do this, use the [Email > Submissions](threat-explorer-views.md#email--submissions) view of Explorer (or Real-time detections).</span></span>

1. <span data-ttu-id="cf931-439">セキュリティ & コンプライアンスセンター () で <https://protection.office.com> 、[ **脅威管理** \> **エクスプローラー** (または **リアルタイムの検出**)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="cf931-439">In the Security & Compliance Center (<https://protection.office.com>), choose **Threat management** \> **Explorer** (or **Real-time detections**).</span></span> <span data-ttu-id="cf931-440">(この例ではエクスプローラーを使用しています)。</span><span class="sxs-lookup"><span data-stu-id="cf931-440">(This example uses Explorer.)</span></span>

2. <span data-ttu-id="cf931-441">[**表示**] メニューの [**電子メール** の送信] を選択し \> **Submissions** ます。</span><span class="sxs-lookup"><span data-stu-id="cf931-441">In the **View** menu, choose **Email** \> **Submissions**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="cf931-442">![エクスプローラーの電子メール用の [表示] メニュー](../../media/explorer-view-menu-email-user-reported.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-442">![View menu for Explorer for emails](../../media/explorer-view-menu-email-user-reported.png)</span></span>

3. <span data-ttu-id="cf931-443">[**送信者**] をクリックし、[**基本** レポートの種類] を選択し \> **Report type** ます。</span><span class="sxs-lookup"><span data-stu-id="cf931-443">Click **Sender**, and then choose **Basic** \> **Report type**.</span></span>

4. <span data-ttu-id="cf931-444">オプション ( **フィッシング** など) を選択し、[ **更新** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cf931-444">Select an option, such as **Phish**, and then click the **Refresh** button.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="cf931-445">![ユーザーによって報告されるフィッシング](../../media/EmailUserReportedReportType.png)</span><span class="sxs-lookup"><span data-stu-id="cf931-445">![User-reported phish](../../media/EmailUserReportedReportType.png)</span></span>

<span data-ttu-id="cf931-446">レポートが更新され、組織内のユーザーがフィッシングとして報告した電子メールメッセージに関するデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-446">The report refreshes to show data about email messages that people in your organization have reported as a phishing attempt.</span></span> <span data-ttu-id="cf931-447">この情報を使用してさらに分析を行い、必要に応じて、 [Microsoft Defender For Office 365 のフィッシング対策ポリシー](configure-atp-anti-phishing-policies.md)を調整することができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-447">You can use this information to conduct further analysis, and if necessary, adjust your [anti-phishing policies in Microsoft Defender for Office 365](configure-atp-anti-phishing-policies.md).</span></span>

## <a name="start-automated-investigation-and-response"></a><span data-ttu-id="cf931-448">自動調査と応答の開始</span><span class="sxs-lookup"><span data-stu-id="cf931-448">Start automated investigation and response</span></span>

> [!NOTE]
> <span data-ttu-id="cf931-449">自動調査および応答機能は、 **Microsoft Defender For office 365 プラン 2** および **office 365 E5** で利用できます。</span><span class="sxs-lookup"><span data-stu-id="cf931-449">Automated investigation and response capabilities are available in **Microsoft Defender for Office 365 Plan 2** and **Office 365 E5**.</span></span>

<span data-ttu-id="cf931-450">(新)自動化された [調査と応答](automated-investigation-response-office.md) によって、セキュリティ運用チームの時間と労力を節約し、cyberattacks を調査および軽減することができます。</span><span class="sxs-lookup"><span data-stu-id="cf931-450">(NEW!) [Automated investigation and response](automated-investigation-response-office.md) can save your security operations team much time and effort in investigating and mitigating cyberattacks.</span></span> <span data-ttu-id="cf931-451">セキュリティプレイブックをトリガーできる通知を構成するだけでなく、エクスプローラーのビューから自動化された調査および応答プロセスを開始できます。</span><span class="sxs-lookup"><span data-stu-id="cf931-451">In addition to configuring alerts that can trigger a security playbook, you can start an automated investigation and response process from a view in Explorer.</span></span>

<span data-ttu-id="cf931-452">詳細については、「 [例: セキュリティ管理者がエクスプローラーから調査を開始する](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf931-452">For details on this, see [Example: A security administrator triggers an investigation from Explorer](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).</span></span>

## <a name="more-ways-to-use-explorer-or-real-time-detections"></a><span data-ttu-id="cf931-453">エクスプローラーを使用するその他の方法 (またはリアルタイムの検出)</span><span class="sxs-lookup"><span data-stu-id="cf931-453">More ways to use Explorer (or Real-time detections)</span></span>

<span data-ttu-id="cf931-454">この記事で説明されているシナリオに加えて、エクスプローラー (またはリアルタイムの検出) で利用できるレポートオプションが他にも多数あります。</span><span class="sxs-lookup"><span data-stu-id="cf931-454">In addition to the scenarios outlined in this article, you have many more reporting options available with Explorer (or Real-time detections).</span></span>

- [<span data-ttu-id="cf931-455">配信された悪意のあるメールの検索と調査</span><span class="sxs-lookup"><span data-stu-id="cf931-455">Find and investigate malicious email that was delivered</span></span>](investigate-malicious-email-that-was-delivered.md)
- [<span data-ttu-id="cf931-456">SharePoint Online、OneDrive、Microsoft Teams で検出された悪意のあるファイルを表示する</span><span class="sxs-lookup"><span data-stu-id="cf931-456">View malicious files detected in SharePoint Online, OneDrive, and Microsoft Teams</span></span>](malicious-files-detected-in-spo-odb-or-teams.md)
- [<span data-ttu-id="cf931-457">脅威エクスプローラーのビューの概要 (およびリアルタイムの検出) を取得する</span><span class="sxs-lookup"><span data-stu-id="cf931-457">Get an overview of the views in Threat Explorer (and Real-time detections)</span></span>](threat-explorer-views.md)
- [<span data-ttu-id="cf931-458">脅威保護の状態レポート</span><span class="sxs-lookup"><span data-stu-id="cf931-458">Threat protection status report</span></span>](view-email-security-reports.md#threat-protection-status-report)
- [<span data-ttu-id="cf931-459">Microsoft Threat Protection での自動調査および対応</span><span class="sxs-lookup"><span data-stu-id="cf931-459">Automated investigation and response in Microsoft Threat Protection</span></span>](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)

## <a name="required-licenses-and-permissions"></a><span data-ttu-id="cf931-460">必要なライセンスとアクセス許可</span><span class="sxs-lookup"><span data-stu-id="cf931-460">Required licenses and permissions</span></span>

<span data-ttu-id="cf931-461">エクスプローラーまたはリアルタイムの検出を取得するには、 [Microsoft Defender For Office 365](office-365-atp.md) が必要です。</span><span class="sxs-lookup"><span data-stu-id="cf931-461">You must have [Microsoft Defender for Office 365](office-365-atp.md) to get Explorer or Real-time detections.</span></span>

- <span data-ttu-id="cf931-462">Explorer は、Office 365 プラン2の Defender に含まれています。</span><span class="sxs-lookup"><span data-stu-id="cf931-462">Explorer is included in Defender for Office 365 Plan 2.</span></span>
- <span data-ttu-id="cf931-463">リアルタイムの検出レポートは、Office 365 プラン1の Defender に含まれています。</span><span class="sxs-lookup"><span data-stu-id="cf931-463">The Real-time detections report is included in Defender for Office 365 Plan 1.</span></span>
- <span data-ttu-id="cf931-464">Office 365 の Defender で保護する必要があるすべてのユーザーにライセンスを割り当てることを計画します。</span><span class="sxs-lookup"><span data-stu-id="cf931-464">Plan to assign licenses for all users who should be protected by Defender for Office 365.</span></span> <span data-ttu-id="cf931-465">(エクスプローラーまたはリアルタイムの検出は、ライセンスが付与されたユーザーの検出データを示します)。</span><span class="sxs-lookup"><span data-stu-id="cf931-465">(Explorer or Real-time detections shows detection data for licensed users.)</span></span>

<span data-ttu-id="cf931-466">エクスプローラーまたはリアルタイム検出を表示して使用するには、セキュリティ管理者やセキュリティリーダーに付与されている権限など、適切なアクセス許可を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf931-466">To view and use Explorer or Real-time detections, you must have appropriate permissions, such as those granted to a security administrator or security reader.</span></span>

- <span data-ttu-id="cf931-467">セキュリティ & コンプライアンスセンターでは、次の役割のいずれかが割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf931-467">For the Security & Compliance Center, you must have one of the following roles assigned:</span></span>

  - <span data-ttu-id="cf931-468">組織管理</span><span class="sxs-lookup"><span data-stu-id="cf931-468">Organization Management</span></span>
  - <span data-ttu-id="cf931-469">セキュリティ管理者 (Azure Active Directory 管理センターで割り当てることができます ( <https://aad.portal.azure.com> )</span><span class="sxs-lookup"><span data-stu-id="cf931-469">Security Administrator (this can be assigned in the Azure Active Directory admin center (<https://aad.portal.azure.com>)</span></span>
  - <span data-ttu-id="cf931-470">セキュリティ閲覧者</span><span class="sxs-lookup"><span data-stu-id="cf931-470">Security Reader</span></span>

- <span data-ttu-id="cf931-471">Exchange Online の場合は、Exchange 管理センター ( <https://admin.protection.outlook.com/ecp/> ) または [Exchange online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell)で次のいずれかの役割が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf931-471">For Exchange Online, you must have one of the following roles assigned in either the Exchange admin center (<https://admin.protection.outlook.com/ecp/>) or [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell):</span></span>

  - <span data-ttu-id="cf931-472">組織の管理</span><span class="sxs-lookup"><span data-stu-id="cf931-472">Organization Management</span></span>
  - <span data-ttu-id="cf931-473">表示専用組織の管理</span><span class="sxs-lookup"><span data-stu-id="cf931-473">View-Only Organization Management</span></span>
  - <span data-ttu-id="cf931-474">"View-Only Recipients/表示専用受信者"</span><span class="sxs-lookup"><span data-stu-id="cf931-474">View-Only Recipients</span></span>
  - <span data-ttu-id="cf931-475">コンプライアンス管理</span><span class="sxs-lookup"><span data-stu-id="cf931-475">Compliance Management</span></span>

<span data-ttu-id="cf931-476">役割とアクセス許可の詳細については、以下のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf931-476">To learn more about roles and permissions, see the following resources:</span></span>

- [<span data-ttu-id="cf931-477">セキュリティ/コンプライアンス センターのアクセス許可</span><span class="sxs-lookup"><span data-stu-id="cf931-477">Permissions in the Security & Compliance Center</span></span>](permissions-in-the-security-and-compliance-center.md)
- [<span data-ttu-id="cf931-478">Exchange Online の機能アクセス許可</span><span class="sxs-lookup"><span data-stu-id="cf931-478">Feature permissions in Exchange Online</span></span>](https://docs.microsoft.com/exchange/permissions-exo/feature-permissions)

## <a name="some-differences-between-threat-explorer-and-real-time-detections"></a><span data-ttu-id="cf931-479">脅威エクスプローラーとリアルタイム検出の相違点</span><span class="sxs-lookup"><span data-stu-id="cf931-479">Some differences between Threat Explorer and Real-time detections</span></span>

- <span data-ttu-id="cf931-480">**リアルタイムの検出** レポートは、Office 365 プラン1の defender で利用できますが、**脅威エクスプローラー** は office 365 プラン2の defender で利用できます。</span><span class="sxs-lookup"><span data-stu-id="cf931-480">The **Real-time detections** report is available in Defender for Office 365 Plan 1, whereas **Threat Explorer** is available in Defender for Office 365 Plan 2.</span></span>
- <span data-ttu-id="cf931-481">**リアルタイムの検出** レポートを使用すると、検出がリアルタイムで表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf931-481">The **Real-time detections** report allows you to view detections in real-time.</span></span> <span data-ttu-id="cf931-482">**脅威エクスプローラー** も同様ですが、特定の攻撃に関する追加の詳細を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="cf931-482">**Threat Explorer** does this as well, but also allows you to view additional details for a given attack.</span></span>
- <span data-ttu-id="cf931-483">**すべての電子メール** ビューは、**脅威エクスプローラー** で使用できます (**リアルタイムの検出** レポートには含まれません)。</span><span class="sxs-lookup"><span data-stu-id="cf931-483">An **All email** view is available in **Threat Explorer** (and is not in the **Real-time detections** report).</span></span>
- <span data-ttu-id="cf931-484">他のフィルター処理機能および使用可能なアクションは、 **脅威エクスプローラー** に含まれています。</span><span class="sxs-lookup"><span data-stu-id="cf931-484">More filtering capabilities and available actions are included in **Threat Explorer**.</span></span>

<span data-ttu-id="cf931-485">詳細については、「 [Microsoft defender For office 365 Service Description: defender For office 365 プランの機能の可用性](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf931-485">For more details, see [Microsoft Defender for Office 365 Service Description: Feature availability across Defender for Office 365 plans](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).</span></span>
