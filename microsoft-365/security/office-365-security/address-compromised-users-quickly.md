---
title: 自動調査と応答によって侵害されたユーザーアカウントに対処する
keywords: AIR、自動赤外線、ATP、自動化、調査、応答、修復、脅威、高度、脅威、保護、侵害
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
ms.date: 02/25/2020
description: Microsoft Defender for Office 365 プラン2で自動調査および応答機能を使用して、侵害されたユーザーアカウントを検出して対処するプロセスを高速化する方法について説明します。
ms.openlocfilehash: 19c9bad33263178f92c6fe523b44497cf38ebd53
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "49616739"
---
# <a name="address-compromised-user-accounts-with-automated-investigation-and-response"></a><span data-ttu-id="09b3f-104">自動調査と応答によって侵害されたユーザーアカウントに対処する</span><span class="sxs-lookup"><span data-stu-id="09b3f-104">Address compromised user accounts with automated investigation and response</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


<span data-ttu-id="09b3f-105">[Microsoft Defender For Office 365 プラン2に](office-365-atp.md#microsoft-defender-for-office-365-plan-1-and-plan-2) は [、強力な自動調査と応答](office-365-air.md) (AIR) 機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="09b3f-105">[Microsoft Defender for Office 365 Plan 2](office-365-atp.md#microsoft-defender-for-office-365-plan-1-and-plan-2) includes powerful [automated investigation and response](office-365-air.md) (AIR) capabilities.</span></span> <span data-ttu-id="09b3f-106">このような機能を使用すると、セキュリティ運用チームに大きな脅威に対処するための時間と労力を大幅に節約できます。</span><span class="sxs-lookup"><span data-stu-id="09b3f-106">Such capabilities can save your security operations team a lot of time and effort dealing with threats.</span></span> <span data-ttu-id="09b3f-107">Microsoft は、セキュリティ機能を引き続き強化しています。</span><span class="sxs-lookup"><span data-stu-id="09b3f-107">Microsoft continues to improve security capabilities.</span></span> <span data-ttu-id="09b3f-108">最近では、安全なユーザーセキュリティプレイブックを含めるように、空気機能が強化されています (現在プレビュー中)。</span><span class="sxs-lookup"><span data-stu-id="09b3f-108">Recently, AIR capabilities were enhanced to include a compromised user security playbook (currently in preview).</span></span> <span data-ttu-id="09b3f-109">侵害されたユーザーセキュリティのプレイブックの詳細については、この記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09b3f-109">Read this article to learn more about the compromised user security playbook.</span></span> <span data-ttu-id="09b3f-110">さらに、ブログの投稿速度を確認して、 [Microsoft Defender For Office 365 を使用して、ユーザーの侵害範囲と制限違反の範囲を検出して応答する](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Speed-up-time-to-detect-and-respond-to-user-compromise-and-limit/ba-p/977053) ことができます。</span><span class="sxs-lookup"><span data-stu-id="09b3f-110">And see the blog post [Speed up time to detect and respond to user compromise and limit breach scope with Microsoft Defender for Office 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Speed-up-time-to-detect-and-respond-to-user-compromise-and-limit/ba-p/977053) for additional details.</span></span>

![侵害されたユーザーの自動化された調査](/microsoft-365/media/office365atp-compduserinvestigation.jpg)

<span data-ttu-id="09b3f-112">侵害されたユーザーセキュリティのプレイブックにより、組織のセキュリティチームは次のことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="09b3f-112">The compromised user security playbook enables your organization's security team to:</span></span>

- <span data-ttu-id="09b3f-113">侵害されたユーザーアカウントの検出を高速化します。</span><span class="sxs-lookup"><span data-stu-id="09b3f-113">Speed up detection of compromised user accounts;</span></span>

- <span data-ttu-id="09b3f-114">アカウントが侵害された場合に、違反の範囲を制限します。そして</span><span class="sxs-lookup"><span data-stu-id="09b3f-114">Limit the scope of a breach when an account is compromised; and</span></span>

- <span data-ttu-id="09b3f-115">侵害されたユーザーにより効果的かつ効率的に対応します。</span><span class="sxs-lookup"><span data-stu-id="09b3f-115">Respond to compromised users more effectively and efficiently.</span></span>

## <a name="compromised-user-alerts"></a><span data-ttu-id="09b3f-116">侵害されたユーザー通知</span><span class="sxs-lookup"><span data-stu-id="09b3f-116">Compromised user alerts</span></span>

<span data-ttu-id="09b3f-117">ユーザーアカウントが侵害されると、例外的または異常な動作が発生します。</span><span class="sxs-lookup"><span data-stu-id="09b3f-117">When a user account is compromised, atypical or anomalous behaviors occur.</span></span> <span data-ttu-id="09b3f-118">たとえば、フィッシングおよびスパムメッセージは、信頼できるユーザーアカウントから内部で送信される場合があります。</span><span class="sxs-lookup"><span data-stu-id="09b3f-118">For example, phishing and spam messages might be sent internally from a trusted user account.</span></span> <span data-ttu-id="09b3f-119">Office 365 の Defender では、Office 365 の電子メールパターンやコラボレーション作業でこのような異常を検出することができます。</span><span class="sxs-lookup"><span data-stu-id="09b3f-119">Defender for Office 365 can detect such anomalies in email patterns and collaboration activity within Office 365.</span></span> <span data-ttu-id="09b3f-120">これが発生すると、アラートがトリガーされ、脅威の軽減プロセスが開始されます。</span><span class="sxs-lookup"><span data-stu-id="09b3f-120">When this happens, alerts are triggered, and the threat mitigation process begins.</span></span>

<span data-ttu-id="09b3f-121">たとえば、不審な電子メールの送信によってトリガーされた警告は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="09b3f-121">For example, here's an alert that was triggered because of suspicious email sending:</span></span>

![疑わしい電子メールの送信によってトリガーされたアラート](/microsoft-365/media/office365atp-suspiciousemailsendalert.jpg)

<span data-ttu-id="09b3f-123">また、ユーザーの送信の制限に達したときにトリガーされた警告の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="09b3f-123">And here's an example of an alert that was triggered when a sending limit was reached for a user:</span></span>

![送信制限に達したときにトリガーされるアラート](/microsoft-365/media/office365atp-sendinglimitreached.jpg)

## <a name="investigate-and-respond-to-a-compromised-user"></a><span data-ttu-id="09b3f-125">侵害されたユーザーの調査と対応</span><span class="sxs-lookup"><span data-stu-id="09b3f-125">Investigate and respond to a compromised user</span></span>

<span data-ttu-id="09b3f-126">ユーザーアカウントが侵害されると、警告がトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="09b3f-126">When a user account is compromised, alerts are triggered.</span></span> <span data-ttu-id="09b3f-127">場合によっては、ユーザーアカウントがブロックされ、組織のセキュリティ運用チームによって問題が解決されるまで、以降の電子メールメッセージを送信できなくなります。</span><span class="sxs-lookup"><span data-stu-id="09b3f-127">And in some cases, that user account is blocked and prevented from sending any further email messages until the issue is resolved by your organization's security operations team.</span></span> <span data-ttu-id="09b3f-128">その他の場合は、自動化された調査が開始され、セキュリティチームにとって推奨されるアクションが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="09b3f-128">In other cases, an automated investigation begins which can result in recommended actions that your security team should take.</span></span>

- [<span data-ttu-id="09b3f-129">制限されたユーザーの表示と調査</span><span class="sxs-lookup"><span data-stu-id="09b3f-129">View and investigate restricted users</span></span>](#view-and-investigate-restricted-users)

- [<span data-ttu-id="09b3f-130">自動調査に関する詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="09b3f-130">View details about automated investigations</span></span>](#view-details-about-automated-investigations)

> [!IMPORTANT]
> <span data-ttu-id="09b3f-131">次のタスクを実行するには、適切なアクセス許可を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="09b3f-131">You must have appropriate permissions to perform the following tasks.</span></span> <span data-ttu-id="09b3f-132">[AIR 機能を使用するには、必要なアクセス許可を](office-365-air.md#required-permissions-to-use-air-capabilities)参照してください。</span><span class="sxs-lookup"><span data-stu-id="09b3f-132">See [Required permissions to use AIR capabilities](office-365-air.md#required-permissions-to-use-air-capabilities).</span></span>

### <a name="view-and-investigate-restricted-users"></a><span data-ttu-id="09b3f-133">制限されたユーザーの表示と調査</span><span class="sxs-lookup"><span data-stu-id="09b3f-133">View and investigate restricted users</span></span>

<span data-ttu-id="09b3f-134">制限されたユーザーのリストに移動するためのいくつかのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="09b3f-134">You have a few options for navigating to a list of restricted users.</span></span> <span data-ttu-id="09b3f-135">たとえば、セキュリティ & コンプライアンスセンターでは、[**脅威の管理**] [ \>  \> **制限付きユーザー** のレビュー] に移動できます。</span><span class="sxs-lookup"><span data-stu-id="09b3f-135">For example, in the Security & Compliance Center, you can go to **Threat management** \> **Review** \> **Restricted Users**.</span></span> <span data-ttu-id="09b3f-136">次の手順では、 **通知** ダッシュボードを使用したナビゲーションについて説明します。これは、トリガーされた可能性のあるさまざまな種類の通知を確認するための適切な方法です。</span><span class="sxs-lookup"><span data-stu-id="09b3f-136">The following procedure describes navigation using the **Alerts** dashboard, which is a good way to see various kinds of alerts that might have been triggered.</span></span>

1. <span data-ttu-id="09b3f-137"><https://protection.office.com> に移動し、サインインします。</span><span class="sxs-lookup"><span data-stu-id="09b3f-137">Go to <https://protection.office.com> and sign in.</span></span>

2. <span data-ttu-id="09b3f-138">ナビゲーションウィンドウで、[**通知** ダッシュボード] を選択し \> ます。</span><span class="sxs-lookup"><span data-stu-id="09b3f-138">In the navigation pane, choose **Alerts** \> **Dashboard**.</span></span>

3. <span data-ttu-id="09b3f-139">[ **その他の通知** ] ウィジェットで、[制限された **ユーザー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="09b3f-139">In the **Other alerts** widget, choose **Restricted Users**.</span></span>

   ![その他の通知ウィジェット](/microsoft-365/media/office365atp-otheralertswidget.jpg)

   <span data-ttu-id="09b3f-141">これにより、制限されたユーザーの一覧が開きます。</span><span class="sxs-lookup"><span data-stu-id="09b3f-141">This opens the list of restricted users.</span></span>

   ![Office 365 で制限されたユーザー](/microsoft-365/media/office365atp-restrictedusers.jpg)

4. <span data-ttu-id="09b3f-143">リストでユーザーアカウントを選択して、制限され [たユーザーを解放](removing-user-from-restricted-users-portal-after-spam.md)するなどの詳細情報を表示し、アクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="09b3f-143">Select a user account in the list to view details and take action, such as [releasing the restricted user](removing-user-from-restricted-users-portal-after-spam.md).</span></span>

### <a name="view-details-about-automated-investigations"></a><span data-ttu-id="09b3f-144">自動調査に関する詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="09b3f-144">View details about automated investigations</span></span>

<span data-ttu-id="09b3f-145">自動調査が開始されたら、セキュリティ & コンプライアンスセンターでその詳細と結果を確認できます。</span><span class="sxs-lookup"><span data-stu-id="09b3f-145">When an automated investigation has begun, you can see its details and results in the Security & Compliance Center.</span></span> <span data-ttu-id="09b3f-146">[ **脅威管理** \> の **調査**] に移動し、詳細を表示する調査を選択します。</span><span class="sxs-lookup"><span data-stu-id="09b3f-146">Go to **Threat management** \> **Investigations**, and then select an investigation to view its details.</span></span>

<span data-ttu-id="09b3f-147">詳細については、「 [調査の詳細を表示](air-view-investigation-results.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09b3f-147">To learn more, see [View details of an investigation](air-view-investigation-results.md).</span></span>

## <a name="keep-the-following-points-in-mind"></a><span data-ttu-id="09b3f-148">次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="09b3f-148">Keep the following points in mind</span></span>

- <span data-ttu-id="09b3f-149">**通知を常に手前に** 移動します。</span><span class="sxs-lookup"><span data-stu-id="09b3f-149">**Stay on top of your alerts**.</span></span> <span data-ttu-id="09b3f-150">ご存知のように、危険にさらされている時間が長くなるほど、組織、顧客、パートナーに対して広範な影響とコストが発生する可能性が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="09b3f-150">As you know, the longer a compromise goes undetected, the larger the potential for widespread impact and cost to your organization, customers, and partners.</span></span> <span data-ttu-id="09b3f-151">事前の検出と適時の応答は、脅威を軽減するために重要であり、特にユーザーのアカウントが侵害された場合に非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="09b3f-151">Early detection and timely response are critical to mitigate threats, and especially when a user's account is compromised.</span></span>

- <span data-ttu-id="09b3f-152">**自動化は、セキュリティ運用チームを支援しますが、置き換えはしません**。</span><span class="sxs-lookup"><span data-stu-id="09b3f-152">**Automation assists, but does not replace, your security operations team**.</span></span> <span data-ttu-id="09b3f-153">自動化された調査および応答機能により、危険にさらされているユーザーが早いうちに検出されることがありますが、セキュリティ運用チームは、多くの場合、調査と修復を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="09b3f-153">Automated investigation and response capabilities can detect a compromised user early on, but your security operations team will likely need to engage and do some investigation and remediation.</span></span> <span data-ttu-id="09b3f-154">この点については、いくつかのヘルプが必要ですか?</span><span class="sxs-lookup"><span data-stu-id="09b3f-154">Need some help with this?</span></span> <span data-ttu-id="09b3f-155">「 [レビューと承認のアクション」を](air-review-approve-pending-completed-actions.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="09b3f-155">See [Review and approve actions](air-review-approve-pending-completed-actions.md).</span></span>

- <span data-ttu-id="09b3f-156">**疑わしいログインの警告は、唯一の指標としては利用しないで** ください。</span><span class="sxs-lookup"><span data-stu-id="09b3f-156">**Don't rely on a suspicious login alert as your only indicator**.</span></span> <span data-ttu-id="09b3f-157">ユーザーアカウントが侵害された場合、疑わしいログイン警告が発生するか、またはトリガーされない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="09b3f-157">When a user account is compromised, it might or might not trigger a suspicious login alert.</span></span> <span data-ttu-id="09b3f-158">場合によっては、警告をトリガーするアカウントが侵害された後に発生する一連のアクティビティになることがあります。</span><span class="sxs-lookup"><span data-stu-id="09b3f-158">Sometimes it's the series of activities that occur after an account is compromised that triggers an alert.</span></span> <span data-ttu-id="09b3f-159">アラートの詳細を知りたいですか。</span><span class="sxs-lookup"><span data-stu-id="09b3f-159">Want to know more about alerts?</span></span> <span data-ttu-id="09b3f-160">「 [Alert policies](https://docs.microsoft.com/microsoft-365/compliance/alert-policies)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09b3f-160">See [Alert policies](https://docs.microsoft.com/microsoft-365/compliance/alert-policies).</span></span>

## <a name="next-steps"></a><span data-ttu-id="09b3f-161">次の手順</span><span class="sxs-lookup"><span data-stu-id="09b3f-161">Next steps</span></span>

- [<span data-ttu-id="09b3f-162">空気機能を使用するために必要なアクセス許可を確認する</span><span class="sxs-lookup"><span data-stu-id="09b3f-162">Review the required permissions to use AIR capabilities</span></span>](office-365-air.md#required-permissions-to-use-air-capabilities)

- [<span data-ttu-id="09b3f-163">Office 365 で悪意のある電子メールを検索して調査する</span><span class="sxs-lookup"><span data-stu-id="09b3f-163">Find and investigate malicious email in Office 365</span></span>](investigate-malicious-email-that-was-delivered.md)

- [<span data-ttu-id="09b3f-164">エンドポイントの Microsoft Defender での空気について説明します。</span><span class="sxs-lookup"><span data-stu-id="09b3f-164">Learn about AIR in Microsoft Defender for Endpoint</span></span>](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [<span data-ttu-id="09b3f-165">Microsoft 365 ロードマップにアクセスして、近日公開予定の機能を確認する</span><span class="sxs-lookup"><span data-stu-id="09b3f-165">Visit the Microsoft 365 Roadmap to see what's coming soon and rolling out</span></span>](https://www.microsoft.com/microsoft-365/roadmap?filters=)
