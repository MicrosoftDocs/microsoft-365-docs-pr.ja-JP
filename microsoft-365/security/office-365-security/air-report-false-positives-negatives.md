---
title: Microsoft Defender for Office 365 で自動調査を行った後の誤検知または誤否定を報告する方法
description: Office 365 の Microsoft Defender で、何らかの問題があるか、空軍によって誤って検出されましたか? 分析のために誤検知または誤検知を Microsoft に送信する方法について説明します。
keywords: 自動化、調査、警告、トリガー、アクション、修復、誤検知、false 負
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
ms.date: 09/29/2020
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.topic: conceptual
ms.custom:
- autoir
ms.openlocfilehash: 0fe8891f5ea6af215791c5f4321a93667a9d58f0
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "49616178"
---
# <a name="how-to-report-false-positivesnegatives-in-automated-investigation-and-response-capabilities"></a><span data-ttu-id="e45c5-105">自動調査および応答機能の誤検知/ネガを報告する方法</span><span class="sxs-lookup"><span data-stu-id="e45c5-105">How to report false positives/negatives in automated investigation and response capabilities</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


<span data-ttu-id="e45c5-106">**適用対象:**</span><span class="sxs-lookup"><span data-stu-id="e45c5-106">**Applies to:**</span></span>
- <span data-ttu-id="e45c5-107">Microsoft Defender for Office 365</span><span class="sxs-lookup"><span data-stu-id="e45c5-107">Microsoft Defender for Office 365</span></span>

<span data-ttu-id="e45c5-108">[Office 365 ミスの自動化された調査と応答 (AIR) 機能](automated-investigation-response-office.md)が、誤って検出されたのでしょうか。</span><span class="sxs-lookup"><span data-stu-id="e45c5-108">Did [automated investigation and response (AIR) capabilities in Office 365](automated-investigation-response-office.md) miss or wrongly detect something?</span></span> <span data-ttu-id="e45c5-109">この問題を解決するには、以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e45c5-109">There are steps you can take to fix it.</span></span> <span data-ttu-id="e45c5-110">以下のことを実行できます。</span><span class="sxs-lookup"><span data-stu-id="e45c5-110">You can:</span></span>

- <span data-ttu-id="e45c5-111">[False 正/負の値を Microsoft に報告し](#report-a-false-positivenegative-to-microsoft-for-analysis)ます。</span><span class="sxs-lookup"><span data-stu-id="e45c5-111">[Report a false positive/negative to Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis);</span></span>
- <span data-ttu-id="e45c5-112">[通知を調整し](#adjust-an-alert-to-prevent-false-positives-from-recurring) ます (必要な場合)。そして</span><span class="sxs-lookup"><span data-stu-id="e45c5-112">[Adjust your alerts](#adjust-an-alert-to-prevent-false-positives-from-recurring) (if needed); and</span></span>
- <span data-ttu-id="e45c5-113">[実行された修復操作を元に戻し](#undo-a-remediation-action)ます。</span><span class="sxs-lookup"><span data-stu-id="e45c5-113">[Undo remediation actions that were taken](#undo-a-remediation-action).</span></span>

<span data-ttu-id="e45c5-114">この記事をガイドとして使用します。</span><span class="sxs-lookup"><span data-stu-id="e45c5-114">Use this article as a guide.</span></span>

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a><span data-ttu-id="e45c5-115">False 正/負の値を分析のために Microsoft に報告する</span><span class="sxs-lookup"><span data-stu-id="e45c5-115">Report a false positive/negative to Microsoft for analysis</span></span>

<span data-ttu-id="e45c5-116">Microsoft Defender for Office 365 で、電子メールメッセージ、電子メールの添付ファイル、電子メールメッセージ内の URL、または Office ファイルの URL のいずれかが失われた場合は、 [フィッシング、url、およびファイルを microsoft For office 365 のスキャンに送信](admin-submission.md)できます。</span><span class="sxs-lookup"><span data-stu-id="e45c5-116">If AIR in Microsoft Defender for Office 365 missed an email message, an email attachment, a URL in an email message, or a URL in an Office file, you can [submit suspected spam, phish, URLs, and files to Microsoft for Office 365 scanning](admin-submission.md).</span></span>

<span data-ttu-id="e45c5-117">また [、マルウェア分析のために Microsoft にファイルを送信](https://www.microsoft.com/wdsi/filesubmission)することもできます。</span><span class="sxs-lookup"><span data-stu-id="e45c5-117">You can also [Submit a file to Microsoft for malware analysis](https://www.microsoft.com/wdsi/filesubmission).</span></span>

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a><span data-ttu-id="e45c5-118">警告を調整して誤検知が繰り返されないようにする</span><span class="sxs-lookup"><span data-stu-id="e45c5-118">Adjust an alert to prevent false positives from recurring</span></span>

<span data-ttu-id="e45c5-119">正当な使用によって警告がトリガーされた場合、または警告が不正確な場合は、 [Cloud App Security ポータルで通知を管理](https://docs.microsoft.com/cloud-app-security/managing-alerts)できます。</span><span class="sxs-lookup"><span data-stu-id="e45c5-119">If an alert is triggered by legitimate use, or the alert is inaccurate, you can [Manage alerts in the Cloud App Security portal](https://docs.microsoft.com/cloud-app-security/managing-alerts).</span></span>

<span data-ttu-id="e45c5-120">Office 365 に加えて、 [エンドポイントに Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection) を使用している組織で、ファイル、IP アドレス、URL、またはドメインがデバイスでマルウェアとして扱われている場合は、そのデバイス [の "許可" アクションを使用してカスタムインジケーターを作成](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/manage-indicators)できます。</span><span class="sxs-lookup"><span data-stu-id="e45c5-120">If your organization is using [Microsoft Defender for Endpoint](https://docs.microsoft.com/windows/security/threat-protection) in addition to Office 365, and a file, IP address, URL, or domain is treated as malware on a device, even though it's safe, you can [create a custom indicator with an "Allow" action for your device](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/manage-indicators).</span></span>

## <a name="undo-a-remediation-action"></a><span data-ttu-id="e45c5-121">修復アクションを元に戻す</span><span class="sxs-lookup"><span data-stu-id="e45c5-121">Undo a remediation action</span></span>

<span data-ttu-id="e45c5-122">ほとんどの場合、ウイルス対策アクションが電子メールメッセージ、電子メールの添付ファイル、または URL に対して実行され、そのアイテムが実際には脅威ではない場合、セキュリティ操作チームは修復アクションを取り消すことができ、誤検知が定期的に行われないようにするための手順を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="e45c5-122">In most cases, if a remediation action was taken on an email message, email attachment, or URL, and the item is actually not a threat, your security operations team can undo the remediation action and take steps to prevent the false positive from recurring.</span></span> <span data-ttu-id="e45c5-123">操作を取り消すには、 [脅威エクスプローラー](#undo-an-action-using-threat-explorer) または [ [操作] タブ](#undo-an-action-using-the-actions-tab-for-an-investigation) を使用して調査を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e45c5-123">You can either use [Threat Explorer](#undo-an-action-using-threat-explorer) or the [Actions tab for an investigation](#undo-an-action-using-the-actions-tab-for-an-investigation) to undo an action.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e45c5-124">次のタスクを実行する前に、必要なアクセス許可があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e45c5-124">Make sure you have the necessary permissions before attempting to perform the following tasks.</span></span>

### <a name="undo-an-action-using-threat-explorer"></a><span data-ttu-id="e45c5-125">脅威エクスプローラーを使用してアクションを元に戻す</span><span class="sxs-lookup"><span data-stu-id="e45c5-125">Undo an action using Threat Explorer</span></span>

<span data-ttu-id="e45c5-126">脅威エクスプローラーを使用すると、セキュリティ運用チームは、アクションによって影響を受ける電子メールを検索し、アクションを元に戻す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e45c5-126">With Threat Explorer, your security operations team can find an email affected by an action and potentially undo the action.</span></span>

****

|<span data-ttu-id="e45c5-127">シナリオ</span><span class="sxs-lookup"><span data-stu-id="e45c5-127">Scenario</span></span>|<span data-ttu-id="e45c5-128">元に戻すオプション</span><span class="sxs-lookup"><span data-stu-id="e45c5-128">Undo Options</span></span>|<span data-ttu-id="e45c5-129">詳細情報</span><span class="sxs-lookup"><span data-stu-id="e45c5-129">Learn more</span></span>|
|---|---|---|
|<span data-ttu-id="e45c5-130">電子メールメッセージがユーザーの迷惑メールフォルダーにルーティングされた</span><span class="sxs-lookup"><span data-stu-id="e45c5-130">An email message was routed to a user's Junk Email folder</span></span>|<ul><li><span data-ttu-id="e45c5-131">メッセージをユーザーの削除済みアイテムフォルダーに移動する</span><span class="sxs-lookup"><span data-stu-id="e45c5-131">Move the message to the user's Deleted Items folder</span></span></li><li><span data-ttu-id="e45c5-132">ユーザーの受信トレイにメッセージを移動する</span><span class="sxs-lookup"><span data-stu-id="e45c5-132">Move the message to the user's Inbox</span></span></li><li><span data-ttu-id="e45c5-133">メッセージを削除</span><span class="sxs-lookup"><span data-stu-id="e45c5-133">Delete the message</span></span></li></ul>|[<span data-ttu-id="e45c5-134">Office 365 で配信された悪意のある電子メールを検索して調査する</span><span class="sxs-lookup"><span data-stu-id="e45c5-134">Find and investigate malicious email that was delivered in Office 365</span></span>](investigate-malicious-email-that-was-delivered.md)|
|<span data-ttu-id="e45c5-135">電子メールメッセージまたはファイルが検疫された</span><span class="sxs-lookup"><span data-stu-id="e45c5-135">An email message or a file was quarantined</span></span>|<ul><li><span data-ttu-id="e45c5-136">メールまたはファイルを解放する</span><span class="sxs-lookup"><span data-stu-id="e45c5-136">Release the email or file</span></span></li><li><span data-ttu-id="e45c5-137">メールまたはファイルを削除する</span><span class="sxs-lookup"><span data-stu-id="e45c5-137">Delete the email or file</span></span></li></ul>|[<span data-ttu-id="e45c5-138">管理者として検疫済みメッセージを管理する</span><span class="sxs-lookup"><span data-stu-id="e45c5-138">Manage quarantined messages as an admin</span></span>](manage-quarantined-messages-and-files.md)|
|

### <a name="undo-an-action-using-the-actions-tab-for-an-investigation"></a><span data-ttu-id="e45c5-139">[操作] タブを使用して、調査を行うアクションを元に戻す</span><span class="sxs-lookup"><span data-stu-id="e45c5-139">Undo an action using the Actions tab for an investigation</span></span>

<span data-ttu-id="e45c5-140">アクションセンターでは、実行された修復アクションを確認し、アクションを元に戻す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e45c5-140">In the Action center, you can see remediation actions that were taken and potentially undo the action.</span></span>

1. <span data-ttu-id="e45c5-141"><https://protection.office.com> に移動し、サインインします。</span><span class="sxs-lookup"><span data-stu-id="e45c5-141">Go to <https://protection.office.com> and sign in.</span></span> <span data-ttu-id="e45c5-142">これにより、セキュリティ & コンプライアンスセンターに移動できます。</span><span class="sxs-lookup"><span data-stu-id="e45c5-142">This takes you to the Security & Compliance Center.</span></span>

2. <span data-ttu-id="e45c5-143">[ **脅威管理** \> の **調査**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="e45c5-143">Go to **Threat management** \> **Investigations**.</span></span>

3. <span data-ttu-id="e45c5-144">調査の一覧で、アイテムの ID の横にある [ **新しいウィンドウで開く** ] アイコンを選択します。</span><span class="sxs-lookup"><span data-stu-id="e45c5-144">In the list of investigations, select the **Open in new window** icon next to an item's ID.</span></span>

4. <span data-ttu-id="e45c5-145">[ **操作** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="e45c5-145">Select the **Actions** tab.</span></span>

5. <span data-ttu-id="e45c5-146">状態が [**完了**] であるアイテムを選択し、[**判断**] 列で [**承認済み**] などのリンクを探します。</span><span class="sxs-lookup"><span data-stu-id="e45c5-146">Select an item that has status of **Completed**, and look for a link, such as **Approved**, in the **Decision** column.</span></span> <span data-ttu-id="e45c5-147">これにより、アクションの詳細を含むフライアウトが開きます。</span><span class="sxs-lookup"><span data-stu-id="e45c5-147">This opens a flyout with more details about the action.</span></span>

6. <span data-ttu-id="e45c5-148">アクションを元に戻すには、[ **修復の削除**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e45c5-148">To undo the action, select **Delete remediation**.</span></span>

## <a name="related-articles"></a><span data-ttu-id="e45c5-149">関連記事</span><span class="sxs-lookup"><span data-stu-id="e45c5-149">Related articles</span></span>

[<span data-ttu-id="e45c5-150">Microsoft Defender for Office 365</span><span class="sxs-lookup"><span data-stu-id="e45c5-150">Microsoft Defender for Office 365</span></span>](office-365-atp.md)

[<span data-ttu-id="e45c5-151">Microsoft Defender for Office 365 の空気</span><span class="sxs-lookup"><span data-stu-id="e45c5-151">AIR in Microsoft Defender for Office 365</span></span>](office-365-air.md)
