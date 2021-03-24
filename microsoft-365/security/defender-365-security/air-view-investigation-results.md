---
title: Microsoft 365 での自動調査の結果を表示する
keywords: AIR、autoIR、ATP、自動化、調査、修復、アクション
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Microsoft 365 の自動調査中および後に、結果と主要な結果を表示できます。
ms.date: 01/29/2021
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8bf18a9fb80805581a1439b3965a664fd0868248
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51065612"
---
# <a name="details-and-results-of-an-automated-investigation-in-microsoft-365"></a><span data-ttu-id="41c19-104">Microsoft 365 での自動調査の詳細と結果</span><span class="sxs-lookup"><span data-stu-id="41c19-104">Details and results of an automated investigation in Microsoft 365</span></span>

<span data-ttu-id="41c19-105">**適用対象**</span><span class="sxs-lookup"><span data-stu-id="41c19-105">**Applies to**</span></span>
- [<span data-ttu-id="41c19-106">Microsoft Defender for Office 365 プラン 2</span><span class="sxs-lookup"><span data-stu-id="41c19-106">Microsoft Defender for Office 365 plan 2</span></span>](defender-for-office-365.md)
- [<span data-ttu-id="41c19-107">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="41c19-107">Microsoft 365 Defender</span></span>](../defender/microsoft-365-defender.md)

<span data-ttu-id="41c19-108">Microsoft Defender [for](office-365-air.md) Office [365](defender-for-office-365.md)で自動調査が行われる場合、その調査に関する詳細は、自動調査プロセスの中および後で利用できます。</span><span class="sxs-lookup"><span data-stu-id="41c19-108">When an [automated investigation](office-365-air.md) occurs in [Microsoft Defender for Office 365](defender-for-office-365.md), details about that investigation are available during and after the automated investigation process.</span></span> <span data-ttu-id="41c19-109">必要なアクセス許可がある場合は、Microsoft 365 セキュリティ センターでこれらの詳細を表示できます。</span><span class="sxs-lookup"><span data-stu-id="41c19-109">If you have the necessary permissions, you can view those details in the Microsoft 365 security center.</span></span> <span data-ttu-id="41c19-110">調査の詳細は、最新の状態と、保留中のアクションを承認する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="41c19-110">Investigation details provide you with up-to-date status, and the ability to approve any pending actions.</span></span>

> [!TIP]
> <span data-ttu-id="41c19-111">Microsoft 365 セキュリティ センターの新しい統合調査ページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="41c19-111">Check out the new, unified investigation page in the Microsoft 365 security center.</span></span> <span data-ttu-id="41c19-112">詳細については [、「(NEW!)」を参照してください。統合された調査ページ](../defender/m365d-autoir-results.md#new-unified-investigation-page)。</span><span class="sxs-lookup"><span data-stu-id="41c19-112">To learn more, see [(NEW!) Unified investigation page](../defender/m365d-autoir-results.md#new-unified-investigation-page).</span></span>

## <a name="investigation-status"></a><span data-ttu-id="41c19-113">調査の状態</span><span class="sxs-lookup"><span data-stu-id="41c19-113">Investigation status</span></span>

<span data-ttu-id="41c19-114">調査の状態は、分析と処理の進捗状況を示します。</span><span class="sxs-lookup"><span data-stu-id="41c19-114">The investigation status indicates the progress of the analysis and actions.</span></span> <span data-ttu-id="41c19-115">調査が実行されると、状態の表示が変わり、脅威が検出されたかどうかと、処理が承認されているかどうかが示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="41c19-115">As the investigation runs, status changes to indicate whether threats were found, and whether actions have been approved.</span></span>

|<span data-ttu-id="41c19-116">状態</span><span class="sxs-lookup"><span data-stu-id="41c19-116">Status</span></span>|<span data-ttu-id="41c19-117">説明</span><span class="sxs-lookup"><span data-stu-id="41c19-117">Description</span></span>|
|:---|:---|
|<span data-ttu-id="41c19-118">**開始中**</span><span class="sxs-lookup"><span data-stu-id="41c19-118">**Starting**</span></span>|<span data-ttu-id="41c19-119">調査がトリガーされ、実行の開始を待っています。</span><span class="sxs-lookup"><span data-stu-id="41c19-119">The investigation has been triggered and waiting to start running.</span></span>|
|<span data-ttu-id="41c19-120">**実行中**</span><span class="sxs-lookup"><span data-stu-id="41c19-120">**Running**</span></span>|<span data-ttu-id="41c19-121">調査プロセスが開始され、進行中です。</span><span class="sxs-lookup"><span data-stu-id="41c19-121">The investigation process has started and is underway.</span></span> <span data-ttu-id="41c19-122">この状態は、保留中の [アクションが承認された場合](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions) にも発生します。</span><span class="sxs-lookup"><span data-stu-id="41c19-122">This state also occurs when [pending actions](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions) are approved.</span></span>|
|<span data-ttu-id="41c19-123">**脅威が見つかりません**</span><span class="sxs-lookup"><span data-stu-id="41c19-123">**No Threats Found**</span></span>|<span data-ttu-id="41c19-124">調査が完了し、脅威 (ユーザー アカウント、電子メール メッセージ、URL、またはファイル) が特定されていない。</span><span class="sxs-lookup"><span data-stu-id="41c19-124">The investigation has finished and no threats (user account, email message, URL, or file) were identified.</span></span> <p> <span data-ttu-id="41c19-125">**ヒント**: 何かが見つからないと思われる場合 (偽陰性など)、Threat Explorer を使用して [アクションを実行できます](threat-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="41c19-125">**TIP**: If you suspect something was missed (such as a false negative), you can take action using [Threat Explorer](threat-explorer.md).</span></span>|
|<span data-ttu-id="41c19-126">**脅威が検出されました**</span><span class="sxs-lookup"><span data-stu-id="41c19-126">**Threats Found**</span></span>|<span data-ttu-id="41c19-127">自動調査で問題が見つかりましたが、これらの問題を解決するための特定の修復アクションはありません。</span><span class="sxs-lookup"><span data-stu-id="41c19-127">The automated investigation found issues, but there are no specific remediation actions to resolve those issues.</span></span> <p> <span data-ttu-id="41c19-128">脅威 **が見つかった状態** は、何らかの種類のユーザー アクティビティが特定されたが、クリーンアップアクションが利用できない場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="41c19-128">The **Threats Found** status can occur when some type of user activity was identified but no cleanup actions are available.</span></span> <span data-ttu-id="41c19-129">例としては、次のユーザー アクティビティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="41c19-129">Examples include any of the following user activities:</span></span> <br/><span data-ttu-id="41c19-130">- データ [損失防止](../../compliance/data-loss-prevention-policies.md) (DLP) イベント</span><span class="sxs-lookup"><span data-stu-id="41c19-130">- A [data loss prevention](../../compliance/data-loss-prevention-policies.md) (DLP) event</span></span><br/><span data-ttu-id="41c19-131">- 異常を送信する電子メール</span><span class="sxs-lookup"><span data-stu-id="41c19-131">- An email sending anomaly</span></span><br/><span data-ttu-id="41c19-132">- 送信されたマルウェア</span><span class="sxs-lookup"><span data-stu-id="41c19-132">- Sent malware</span></span><br/><span data-ttu-id="41c19-133">- 送信されたフィッシング</span><span class="sxs-lookup"><span data-stu-id="41c19-133">- Sent phish</span></span> <p> <span data-ttu-id="41c19-134">調査では、修復する悪意のある URL、ファイル、または電子メール メッセージが見つかりませんでした。また、転送ルールや委任をオフにするなどのメールボックスアクティビティも修正されませんでした。</span><span class="sxs-lookup"><span data-stu-id="41c19-134">The investigation found no malicious URLs, files, or email messages to remediate, and no mailbox activity to fix, such as turning off forwarding rules or delegation.</span></span> <p> <span data-ttu-id="41c19-135">**ヒント**: 何かが見つからない (偽陰性など) 疑われる場合は、Threat Explorer を使用して調査して [アクションを実行できます](threat-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="41c19-135">**TIP**: If you suspect something was missed (such as a false negative), you can investigate and take action using [Threat Explorer](threat-explorer.md).</span></span>|
|<span data-ttu-id="41c19-136">**システムによって終了**</span><span class="sxs-lookup"><span data-stu-id="41c19-136">**Terminated By System**</span></span>|<span data-ttu-id="41c19-137">調査が停止しました。</span><span class="sxs-lookup"><span data-stu-id="41c19-137">The investigation stopped.</span></span> <span data-ttu-id="41c19-138">調査は、いくつかの理由で停止する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="41c19-138">An investigation can stop for several reasons:</span></span> <br/><span data-ttu-id="41c19-139">- 調査の保留中のアクションの有効期限が切れています。</span><span class="sxs-lookup"><span data-stu-id="41c19-139">- The investigation's pending actions expired.</span></span> <span data-ttu-id="41c19-140">保留中のアクションは、承認を 1 週間待った後にタイム アウトします。</span><span class="sxs-lookup"><span data-stu-id="41c19-140">Pending actions time out after awaiting approval for one week.</span></span><br/><span data-ttu-id="41c19-141">- アクションが多すぎます。</span><span class="sxs-lookup"><span data-stu-id="41c19-141">- There are too many actions.</span></span> <span data-ttu-id="41c19-142">たとえば、悪意のある URL をクリックするユーザーが多すぎると、すべてのアナライザーを実行する調査の機能を超える可能性があります。そのため、調査は停止します。</span><span class="sxs-lookup"><span data-stu-id="41c19-142">For example, if there are too many users clicking on malicious URLs, it can exceed the investigation's ability to run all the analyzers, so the investigation halts.</span></span><p> <span data-ttu-id="41c19-143">**ヒント**: アクションが実行される前に調査が停止した場合は [、Threat Explorer](threat-explorer.md) を使用して脅威を見つけて対処してみてください。</span><span class="sxs-lookup"><span data-stu-id="41c19-143">**TIP**: If an investigation halts before actions were taken, try using [Threat Explorer](threat-explorer.md) to find and address threats.</span></span>|
|<span data-ttu-id="41c19-144">**保留中のアクション**</span><span class="sxs-lookup"><span data-stu-id="41c19-144">**Pending Action**</span></span>|<span data-ttu-id="41c19-145">調査では、悪意のある電子メール、悪意のある URL、危険なメールボックス設定などの脅威、および承認を待っている脅威を修復するアクションが [検出されました](air-review-approve-pending-completed-actions.md)。</span><span class="sxs-lookup"><span data-stu-id="41c19-145">The investigation has found a threat, such as a malicious email, a malicious URL, or a risky mailbox setting, and an action to remediate that threat is [awaiting approval](air-review-approve-pending-completed-actions.md).</span></span> <p> <span data-ttu-id="41c19-146">保留中 **のアクション状態は** 、対応するアクションを持つ脅威が見つかったときにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="41c19-146">The **Pending Action** state is triggered when any threat with a corresponding action is found.</span></span> <span data-ttu-id="41c19-147">ただし、保留中のアクションの一覧は、調査の実行に合って増加する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="41c19-147">However, the list of pending actions can increase as an investigation runs.</span></span> <span data-ttu-id="41c19-148">調査の詳細を表示して、他のアイテムがまだ保留中の完了を確認します。</span><span class="sxs-lookup"><span data-stu-id="41c19-148">View investigation details to see if other items are still pending completion.</span></span>|
|<span data-ttu-id="41c19-149">**修復済み**</span><span class="sxs-lookup"><span data-stu-id="41c19-149">**Remediated**</span></span>|<span data-ttu-id="41c19-150">調査が完了し、すべての修復アクションが承認されました (完全に修復されたと示されています)。</span><span class="sxs-lookup"><span data-stu-id="41c19-150">The investigation finished and all remediation actions were approved (noted as fully remediated).</span></span> <p> <span data-ttu-id="41c19-151">**メモ**: 承認済みの修復アクションには、アクションが実行されるのを妨げるエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="41c19-151">**NOTE**: Approved remediation actions can have errors that prevent the actions from being taken.</span></span> <span data-ttu-id="41c19-152">修復アクションが正常に完了したかどうかに関係なく、調査の状態は変更されません。</span><span class="sxs-lookup"><span data-stu-id="41c19-152">Regardless of whether remediation actions are successfully completed, the investigation status does not change.</span></span> <span data-ttu-id="41c19-153">調査の詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="41c19-153">View investigation details.</span></span>|
|<span data-ttu-id="41c19-154">**部分的に修復**</span><span class="sxs-lookup"><span data-stu-id="41c19-154">**Partially Remediated**</span></span>|<span data-ttu-id="41c19-155">調査の結果、修復アクションが発生し、一部は承認され、完了しました。</span><span class="sxs-lookup"><span data-stu-id="41c19-155">The investigation resulted in remediation actions, and some were approved and completed.</span></span> <span data-ttu-id="41c19-156">他のアクションはまだ [保留中です](air-review-approve-pending-completed-actions.md)。</span><span class="sxs-lookup"><span data-stu-id="41c19-156">Other actions are still [pending](air-review-approve-pending-completed-actions.md).</span></span>|
|<span data-ttu-id="41c19-157">**Failed**</span><span class="sxs-lookup"><span data-stu-id="41c19-157">**Failed**</span></span>|<span data-ttu-id="41c19-158">少なくとも 1 つの調査アナライザーで、正しく完了できない問題が発生しました。</span><span class="sxs-lookup"><span data-stu-id="41c19-158">At least one investigation analyzer ran into a problem where it could not complete properly.</span></span> <p> <span data-ttu-id="41c19-159">**注**: 修復アクションが承認された後に調査が失敗した場合、修復アクションは引き続き成功している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="41c19-159">**NOTE**: If an investigation fails after remediation actions were approved, the remediation actions might still have succeeded.</span></span> <span data-ttu-id="41c19-160">調査の詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="41c19-160">View the investigation details.</span></span> |
|<span data-ttu-id="41c19-161">**調整によってキューに入れられます**</span><span class="sxs-lookup"><span data-stu-id="41c19-161">**Queued By Throttling**</span></span>|<span data-ttu-id="41c19-162">調査がキューに保持されている。</span><span class="sxs-lookup"><span data-stu-id="41c19-162">An investigation is being held in a queue.</span></span> <span data-ttu-id="41c19-163">他の調査が完了すると、キューに入った調査が開始されます。</span><span class="sxs-lookup"><span data-stu-id="41c19-163">When other investigations complete, queued investigations begin.</span></span> <span data-ttu-id="41c19-164">調整は、サービスパフォーマンスの低下を回避するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="41c19-164">Throttling helps avoid poor service performance.</span></span>  <p> <span data-ttu-id="41c19-165">**ヒント**: 保留中のアクションでは、実行できる新しい調査の数を制限できます。</span><span class="sxs-lookup"><span data-stu-id="41c19-165">**TIP**: Pending actions can limit how many new investigations can run.</span></span> <span data-ttu-id="41c19-166">保留中のアクション [を承認 (または拒否) することを確認します](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions)。</span><span class="sxs-lookup"><span data-stu-id="41c19-166">Make sure to [approve (or reject) pending actions](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions).</span></span>|
|<span data-ttu-id="41c19-167">**調整によって終了**</span><span class="sxs-lookup"><span data-stu-id="41c19-167">**Terminated By Throttling**</span></span>|<span data-ttu-id="41c19-168">調査がキューに保持されている時間が長すぎると、停止します。</span><span class="sxs-lookup"><span data-stu-id="41c19-168">If an investigation is held in the queue too long, it stops.</span></span> <p> <span data-ttu-id="41c19-169">**ヒント**: 脅威エクスプローラー [から調査を開始できます](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)。</span><span class="sxs-lookup"><span data-stu-id="41c19-169">**TIP**: You can [start an investigation from Threat Explorer](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).</span></span>|
|

## <a name="view-details-of-an-investigation"></a><span data-ttu-id="41c19-170">調査の詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="41c19-170">View details of an investigation</span></span>

1. <span data-ttu-id="41c19-171">Microsoft 365 セキュリティ センター ( ) に移動し <https://security.microsoft.com> 、サインインします。</span><span class="sxs-lookup"><span data-stu-id="41c19-171">Go to the Microsoft 365 security center (<https://security.microsoft.com>) and sign in.</span></span>
2. <span data-ttu-id="41c19-172">ナビゲーション ウィンドウで、[アクション センター] **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="41c19-172">In the navigation pane, select **Action center**.</span></span>
3. <span data-ttu-id="41c19-173">[保留中] **タブまたは [履歴** ] **タブで** 、アクションを選択します。</span><span class="sxs-lookup"><span data-stu-id="41c19-173">On either the **Pending** or **History** tabs, select an action.</span></span> <span data-ttu-id="41c19-174">そのフライアウト ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="41c19-174">Its flyout pane opens.</span></span>
4. <span data-ttu-id="41c19-175">フライアウト ウィンドウで、[調査ページを開 **く] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="41c19-175">In the flyout pane, select **Open investigation page**.</span></span> 
5. <span data-ttu-id="41c19-176">調査の詳細については、さまざまなタブを使用します。</span><span class="sxs-lookup"><span data-stu-id="41c19-176">Use the various tabs to learn more about the investigation.</span></span>

## <a name="view-details-about-an-alert-related-to-an-investigation"></a><span data-ttu-id="41c19-177">調査に関連するアラートの詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="41c19-177">View details about an alert related to an investigation</span></span>

<span data-ttu-id="41c19-178">特定の種類のアラートは、Microsoft 365 で自動調査をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="41c19-178">Certain kinds of alerts trigger automated investigation in Microsoft 365.</span></span> <span data-ttu-id="41c19-179">詳細については、「自動調査 [をトリガーするアラート ポリシー」を参照してください](office-365-air.md#which-alert-policies-trigger-automated-investigations)。</span><span class="sxs-lookup"><span data-stu-id="41c19-179">To learn more, see [alert policies that trigger automated investigations](office-365-air.md#which-alert-policies-trigger-automated-investigations).</span></span>

1. <span data-ttu-id="41c19-180">Microsoft 365 セキュリティ センター ( ) に移動し <https://security.microsoft.com> 、サインインします。</span><span class="sxs-lookup"><span data-stu-id="41c19-180">Go to the Microsoft 365 security center (<https://security.microsoft.com>) and sign in.</span></span>
2. <span data-ttu-id="41c19-181">ナビゲーション ウィンドウで、[アクション センター] **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="41c19-181">In the navigation pane, select **Action center**.</span></span>
3. <span data-ttu-id="41c19-182">[保留中] **タブまたは [履歴** ] **タブで** 、アクションを選択します。</span><span class="sxs-lookup"><span data-stu-id="41c19-182">On either the **Pending** or **History** tabs, select an action.</span></span> <span data-ttu-id="41c19-183">そのフライアウト ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="41c19-183">Its flyout pane opens.</span></span>
4. <span data-ttu-id="41c19-184">フライアウト ウィンドウで、[調査ページを開 **く] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="41c19-184">In the flyout pane, select **Open investigation page**.</span></span> 
5. <span data-ttu-id="41c19-185">[アラート] **タブ** を選択して、その調査に関連付けられているすべてのアラートの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="41c19-185">Select the **Alerts** tab to view a list of all of the alerts associated with that investigation.</span></span>
6. <span data-ttu-id="41c19-186">リスト内のアイテムを選択して、そのフライアウト ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="41c19-186">Select an item in the list to open its flyout pane.</span></span> <span data-ttu-id="41c19-187">そこで、アラートの詳細を表示できます。</span><span class="sxs-lookup"><span data-stu-id="41c19-187">There, you can view more information about the alert.</span></span>

## <a name="keep-the-following-points-in-mind"></a><span data-ttu-id="41c19-188">以下の点に気を付ける</span><span class="sxs-lookup"><span data-stu-id="41c19-188">Keep the following points in mind</span></span>

- <span data-ttu-id="41c19-189">電子メールの数は調査時に計算され、調査のフライアウトを開く (基になるクエリに基づいて) いくつかのカウントが再計算されます。</span><span class="sxs-lookup"><span data-stu-id="41c19-189">Email counts are calculated at the time of the investigation, and some counts are recalculated when you open investigation flyouts (based on an underlying query).</span></span>

- <span data-ttu-id="41c19-190">[電子メール] タブの電子メール クラスターに対して表示される電子メールの数と、クラスター のフライアウトに表示される電子メールの量の値は、調査時に計算され、変更されません。</span><span class="sxs-lookup"><span data-stu-id="41c19-190">The email counts shown for the email clusters on the **Email** tab and the email quantity value shown on cluster flyout are calculated at the time of investigation, and do not change.</span></span>

- <span data-ttu-id="41c19-191">電子メール クラスターのフライアウトの[電子メール] タブの下部に表示される電子メール数と、エクスプローラーに表示される電子メール メッセージの数は、調査の最初の分析後に受信した電子メール メッセージを反映します。</span><span class="sxs-lookup"><span data-stu-id="41c19-191">The email count shown at the bottom of the **Email** tab of the email cluster flyout and the count of email messages shown in Explorer reflect email messages received after the investigation's initial analysis.</span></span>

  <span data-ttu-id="41c19-192">したがって、元の数が 10 個の電子メール メッセージを示す電子メール クラスターは、調査分析フェーズと管理者が調査をレビューする間に、さらに 5 つの電子メール メッセージが到着すると、合計 15 の電子メール リストを表示します。</span><span class="sxs-lookup"><span data-stu-id="41c19-192">Thus, an email cluster that shows an original quantity of 10 email messages would show an email list total of 15 when five more email messages arrive between the investigation analysis phase and when the admin reviews the investigation.</span></span> <span data-ttu-id="41c19-193">同様に、Office 365 プラン 2 の Microsoft Defender のデータは、試用版で 7 日後、有料ライセンスの場合は 30 日後に期限切れになるので、古い調査ではエクスプローラー クエリが示す数よりも多く表示され始める可能性があります。</span><span class="sxs-lookup"><span data-stu-id="41c19-193">Likewise, old investigations might start showing higher counts than Explorer queries show, because data in Microsoft Defender for Office 365 Plan 2 expires after seven days for trials and after 30 days for paid licenses.</span></span>

  <span data-ttu-id="41c19-194">調査時のメールの影響と、修復が実行されるまでの現在の影響を示すために、さまざまなビューでカウント履歴と現在のカウントの両方を表示します。</span><span class="sxs-lookup"><span data-stu-id="41c19-194">Showing both count historical and current counts in different views is done to indicate the email impact at the time of investigation and the current impact up until the time that remediation is run.</span></span>

- <span data-ttu-id="41c19-195">電子メールのコンテキストでは、調査の一環としてボリューム異常の脅威の表面が表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="41c19-195">In the context of email, you might see a volume anomaly threat surface as part of the investigation.</span></span> <span data-ttu-id="41c19-196">異常な量の発生は、以前のタイムフレームと比べて、調査イベントの時間の前後に似たようなメール メッセージのスパイクがあったことを示します。</span><span class="sxs-lookup"><span data-stu-id="41c19-196">A volume anomaly indicates a spike in similar email messages around the investigation event time compared to earlier timeframes.</span></span> <span data-ttu-id="41c19-197">メール トラフィックの急増と特定の特性 (件名と送信者のドメイン、本文の類似性、送信者 IP など) は、電子メール キャンペーンや攻撃の開始に典型的です。</span><span class="sxs-lookup"><span data-stu-id="41c19-197">A spike in email traffic together with certain characteristics (for example, subject and sender domain, body similarity, and sender IP) is typical of the start of email campaigns or attacks.</span></span> <span data-ttu-id="41c19-198">ただし、これらの特徴は多くの場合、バルク、スパム、および正当なメール キャンペーンでも同様にみられます。</span><span class="sxs-lookup"><span data-stu-id="41c19-198">However, bulk, spam, and legitimate email campaigns commonly share these characteristics.</span></span>

- <span data-ttu-id="41c19-199">ボリューム異常は潜在的な脅威を表し、それに応じて、ウイルス対策エンジン、発起、または悪意のある評判を使用して識別されるマルウェアやフィッシングの脅威と比較して、それほど深刻ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="41c19-199">Volume anomalies represent a potential threat, and accordingly could be less severe compared to malware or phish threats that are identified using anti-virus engines, detonation, or malicious reputation.</span></span>

- <span data-ttu-id="41c19-200">すべてのアクションを承認する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="41c19-200">You do not have to approve every action.</span></span> <span data-ttu-id="41c19-201">推奨されるアクションに同意しない場合、または組織が特定の種類のアクションを選択しない場合は、アクションを拒否するか、単にアクションを無視して何も実行しないか選択できます。</span><span class="sxs-lookup"><span data-stu-id="41c19-201">If you do not agree with the recommended action or your organization does not choose certain types of actions, then you can choose to **Reject** the actions or simply ignore them and take no action.</span></span>

- <span data-ttu-id="41c19-202">すべてのアクションを承認および/または拒否すると、調査を完全に終了 (状態が修復される) ことができますが、一部のアクションが不完全な場合は、調査の状態が部分的に修復された状態に変更されます。</span><span class="sxs-lookup"><span data-stu-id="41c19-202">Approving and/or rejecting all actions lets the investigation fully close (status becomes remediated), while leaving some actions incomplete results in the investigation status changing to a partially remediated state.</span></span>

## <a name="next-steps"></a><span data-ttu-id="41c19-203">次の手順</span><span class="sxs-lookup"><span data-stu-id="41c19-203">Next steps</span></span>

- [<span data-ttu-id="41c19-204">保留中のアクションの確認と承認</span><span class="sxs-lookup"><span data-stu-id="41c19-204">Review and approve pending actions</span></span>](air-review-approve-pending-completed-actions.md#approve-or-reject-pending-actions)