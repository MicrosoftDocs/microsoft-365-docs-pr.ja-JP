---
title: 自動調査の詳細と結果
description: 自動調査の結果と主な検出事項は、調査の実行中および実行後に表示できます。
keywords: 自動化、調査、結果、分析、詳細、修復、autoair
search.appverid: met150
ms.prod: m365-security
ms.technology: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.date: 02/08/2021
ms.openlocfilehash: 3d278c7fd06b2dd14bd9a8c0dcbe639d3c911828
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51060718"
---
# <a name="details-and-results-of-an-automated-investigation"></a><span data-ttu-id="13bdc-104">自動調査の詳細と結果</span><span class="sxs-lookup"><span data-stu-id="13bdc-104">Details and results of an automated investigation</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

<span data-ttu-id="13bdc-105">**適用対象:**</span><span class="sxs-lookup"><span data-stu-id="13bdc-105">**Applies to:**</span></span>
- <span data-ttu-id="13bdc-106">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="13bdc-106">Microsoft 365 Defender</span></span>

<span data-ttu-id="13bdc-107">Microsoft 365 Defender では[](m365d-autoir.md)、自動調査が実行されると、その調査に関する詳細は、自動調査プロセス中と自動調査後の両方で利用できます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-107">With Microsoft 365 Defender, when an [automated investigation](m365d-autoir.md) runs, details about that investigation are available both during and after the automated investigation process.</span></span> <span data-ttu-id="13bdc-108">[必要なアクセス許可](m365d-action-center.md#required-permissions-for-action-center-tasks)を持っている場合は、調査の詳細ビューでこれらの詳細を表示できます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-108">If you have the [necessary permissions](m365d-action-center.md#required-permissions-for-action-center-tasks), you can view those details in an investigation details view.</span></span> <span data-ttu-id="13bdc-109">調査の詳細ビューでは最新の状態が表示され、保留中のアクションを承認する機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-109">The investigation details view provides you with up-to-date status and the ability to approve any pending actions.</span></span> 

![調査の詳細](../../media/mtp-air-investdetails.png)

## <a name="new-unified-investigation-page"></a><span data-ttu-id="13bdc-111">(NEW!)統合された調査ページ</span><span class="sxs-lookup"><span data-stu-id="13bdc-111">(NEW!) Unified investigation page</span></span>

<span data-ttu-id="13bdc-112">調査ページが最近更新され、デバイス、電子メール、およびコラボレーション コンテンツ全体の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-112">The investigation page has recently been updated to include information across your devices, email, and collaboration content.</span></span> <span data-ttu-id="13bdc-113">新しい統合された調査ページでは、共通言語が定義され [、Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) および Microsoft Defender for Office 365 全体で自動調査 [を行う一元的なエクスペリエンスが](../defender-365-security/defender-for-office-365.md)提供されます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-113">The new, unified investigation page defines a common language and provides a unified experience for automatic investigations across [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) and [Microsoft Defender for Office 365](../defender-365-security/defender-for-office-365.md).</span></span> <span data-ttu-id="13bdc-114">統合調査ページにアクセスするには、次の黄色のバナーにあるリンクを選択します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-114">To access the unified investigation page, select the link in the yellow banner you'll see on:</span></span>
- <span data-ttu-id="13bdc-115">コンプライアンス センター ( ) Office 365 セキュリティ &の調査ページ [https://protection.office.com](https://protection.office.com)</span><span class="sxs-lookup"><span data-stu-id="13bdc-115">Any investigation page in the Office 365 Security & Compliance Center ([https://protection.office.com](https://protection.office.com))</span></span>
- <span data-ttu-id="13bdc-116">Microsoft Defender セキュリティ センターの調査ページ ( [https://securitycenter.windows.com](https://securitycenter.windows.com) )</span><span class="sxs-lookup"><span data-stu-id="13bdc-116">Any investigation page in the Microsoft Defender Security Center ([https://securitycenter.windows.com](https://securitycenter.windows.com))</span></span>
- <span data-ttu-id="13bdc-117">強化された Microsoft 365 セキュリティ センターでのインシデントまたはアクション センターのエクスペリエンス ( [https://security.microsoft.com](https://security.microsoft.com) )</span><span class="sxs-lookup"><span data-stu-id="13bdc-117">Any incident or Action center experience in the improved Microsoft 365 security center ([https://security.microsoft.com](https://security.microsoft.com))</span></span>

## <a name="open-the-investigation-details-view"></a><span data-ttu-id="13bdc-118">調査の詳細ビューを開く</span><span class="sxs-lookup"><span data-stu-id="13bdc-118">Open the investigation details view</span></span>

<span data-ttu-id="13bdc-119">調査の詳細ビューを開くには、次のいずれかの方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-119">You can open the investigation details view by using one of the following methods:</span></span>
- [<span data-ttu-id="13bdc-120">アクション センターでアイテムを選択する</span><span class="sxs-lookup"><span data-stu-id="13bdc-120">Select an item in the Action center</span></span>](#select-an-item-in-the-action-center)
- [<span data-ttu-id="13bdc-121">インシデントの詳細ページから調査を選択する</span><span class="sxs-lookup"><span data-stu-id="13bdc-121">Select an investigation from an incident details page</span></span>](#open-an-investigation-from-an-incident-details-page)

### <a name="select-an-item-in-the-action-center"></a><span data-ttu-id="13bdc-122">アクション センターでアイテムを選択する</span><span class="sxs-lookup"><span data-stu-id="13bdc-122">Select an item in the Action center</span></span>

<span data-ttu-id="13bdc-123">改善された[アクション センター](m365d-action-center.md) ( ) は、デバイス全体の修復アクション、電子メール、コラボレーション & ID を [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) まとめます[](m365d-remediation-actions.md)。</span><span class="sxs-lookup"><span data-stu-id="13bdc-123">The improved [Action center](m365d-action-center.md) ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) brings together [remediation actions](m365d-remediation-actions.md) across your devices, email & collaboration content, and identities.</span></span> <span data-ttu-id="13bdc-124">リストされているアクションには、自動的または手動で実行された修復アクションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-124">Listed actions include remediation actions that were taken automatically or manually.</span></span> <span data-ttu-id="13bdc-125">アクション センターでは、承認を待っているアクションと、既に承認または完了したアクションを表示できます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-125">In the Action center, you can view actions that are awaiting approval and actions that were already approved or completed.</span></span> <span data-ttu-id="13bdc-126">調査ページなどの詳細に移動することもできます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-126">You can also navigate to more details, such as an investigation page.</span></span>

> [!TIP]
> <span data-ttu-id="13bdc-127">アクションを承認 [、拒否、または](m365d-action-center.md#required-permissions-for-action-center-tasks) 元に戻すには、特定のアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="13bdc-127">You must have [certain permissions](m365d-action-center.md#required-permissions-for-action-center-tasks) to approve, reject, or undo actions.</span></span>

1. <span data-ttu-id="13bdc-128">[https://security.microsoft.com](https://security.microsoft.com) に移動し、サインインします。</span><span class="sxs-lookup"><span data-stu-id="13bdc-128">Go to [https://security.microsoft.com](https://security.microsoft.com) and sign in.</span></span> 
2. <span data-ttu-id="13bdc-129">ナビゲーション ウィンドウで、[**アクション センター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-129">In the navigation pane, choose **Action center**.</span></span> 
3. <span data-ttu-id="13bdc-130">[**保留中**] タブまたは [**履歴**] タブのいずれかでアイテムを選択します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-130">On either the **Pending** or **History** tab, select an item.</span></span> <span data-ttu-id="13bdc-131">そのフライアウト ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-131">Its flyout pane opens.</span></span>
4. <span data-ttu-id="13bdc-132">フライアウト ウィンドウで情報を確認し、次のいずれかの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-132">Review the information in the flyout pane, and then take one of the following steps:</span></span>
   - <span data-ttu-id="13bdc-133">[ **調査ページを開く]** を選択して、調査の詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-133">Select **Open investigation page** to view more details about the investigation.</span></span>
   - <span data-ttu-id="13bdc-134">[承認 **] を** 選択して保留中のアクションを開始します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-134">Select **Approve** to initiate a pending action.</span></span>
   - <span data-ttu-id="13bdc-135">保留中 **のアクション** が実行されるのを防ぐには、[拒否] を選択します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-135">Select **Reject** to prevent a pending action from being taken.</span></span>
   - <span data-ttu-id="13bdc-136">[Go **hunt] を** 選択して高度な [ハンティングに入る](advanced-hunting-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="13bdc-136">Select **Go hunt** to go into [Advanced hunting](advanced-hunting-overview.md).</span></span>

### <a name="open-an-investigation-from-an-incident-details-page"></a><span data-ttu-id="13bdc-137">インシデントの詳細ページから調査を開く</span><span class="sxs-lookup"><span data-stu-id="13bdc-137">Open an investigation from an incident details page</span></span>

<span data-ttu-id="13bdc-138">インシデントの詳細ページを使用して、インシデントに関する詳細情報を表示します。これには、影響を受けたデバイス、ユーザー アカウント、またはメールボックスに関する情報がトリガーされた警告が含まれます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-138">Use an incident details page to view detailed information about an incident, including alerts that were triggered information about any affected devices, user accounts, or mailboxes.</span></span>

![インシデントの詳細](../../media/mtp-incidentdetails-tabs.png)

1. <span data-ttu-id="13bdc-140">[https://security.microsoft.com](https://security.microsoft.com) に移動し、サインインします。</span><span class="sxs-lookup"><span data-stu-id="13bdc-140">Go to [https://security.microsoft.com](https://security.microsoft.com) and sign in.</span></span> 
2. <span data-ttu-id="13bdc-141">ナビゲーション ウィンドウで、[インシデント] を選択 **し、[インシデント&通知**  >  **します**。</span><span class="sxs-lookup"><span data-stu-id="13bdc-141">In the navigation pane, choose **Incidents & alerts** > **Incidents**.</span></span> 
3. <span data-ttu-id="13bdc-142">リストでアイテムを選択し、[インシデント ページを開 **く] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="13bdc-142">Select an item in the list, and then choose **Open incident page**.</span></span>
4. <span data-ttu-id="13bdc-143">[調査 **] タブを** 選択し、一覧で調査を選択します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-143">Select the **Investigations** tab, and then select an investigation in the list.</span></span> <span data-ttu-id="13bdc-144">そのフライアウト ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-144">Its flyout pane opens.</span></span>
5. <span data-ttu-id="13bdc-145">[調査 **ページを開く] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="13bdc-145">Select **Open investigation page**.</span></span> 

## <a name="investigation-details"></a><span data-ttu-id="13bdc-146">調査の詳細</span><span class="sxs-lookup"><span data-stu-id="13bdc-146">Investigation details</span></span>

<span data-ttu-id="13bdc-147">調査の詳細ビューを使用して、調査に関連する過去、現在、保留中のアクティビティを表示します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-147">Use the investigation details view to see past, current, and pending activity pertaining to an investigation.</span></span> <span data-ttu-id="13bdc-148">調査の詳細ビューの画像は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="13bdc-148">The investigation details view resembles the following image:</span></span>

![調査の詳細](../../media/mtp-air-investdetails.png)

<span data-ttu-id="13bdc-150">調査の詳細ビューでは、次の表で説明する [**Investigation graph (調査のグラフ)**]、[**Alerts (警告)**]、[**Device (デバイス)**]、[**Identities (ID)**]、[**Key findings (主な検出事項)**]、[**Entities (エンティティ)**]、[**Log (ログ)**]、[**Pending actions (保留中のアクション)**] の各タブに情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-150">In the Investigation details view, you can see information on the **Investigation graph**, **Alerts**, **Devices**, **Identities**, **Key findings**, **Entities**, **Log**, and **Pending actions** tabs, described in the following table.</span></span>

> [!NOTE]
> <span data-ttu-id="13bdc-151">調査の詳細ページに表示される特定のタブは、サブスクリプションに含まれる内容によって異なります。</span><span class="sxs-lookup"><span data-stu-id="13bdc-151">The specific tabs you see in an investigation details page depends on what your subscription includes.</span></span> <span data-ttu-id="13bdc-152">たとえば、サブスクリプションに Microsoft Defender for Office 365 プラン 2 が含まれる場合、[メールボックス] タブ **は表示** されません。</span><span class="sxs-lookup"><span data-stu-id="13bdc-152">For example, if your subscription does not include Microsoft Defender for Office 365 Plan 2, you won't see a **Mailboxes** tab.</span></span>

| <span data-ttu-id="13bdc-153">タブ</span><span class="sxs-lookup"><span data-stu-id="13bdc-153">Tab</span></span> | <span data-ttu-id="13bdc-154">説明</span><span class="sxs-lookup"><span data-stu-id="13bdc-154">Description</span></span> |
|:--------|:--------|
| <span data-ttu-id="13bdc-155">**Investigation graph (調査グラフ)**</span><span class="sxs-lookup"><span data-stu-id="13bdc-155">**Investigation graph**</span></span>   | <span data-ttu-id="13bdc-156">調査を視覚的に表します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-156">Provides a visual representation of the investigation.</span></span> <span data-ttu-id="13bdc-157">エンティティと検出された脅威のほか、警告、承認を待っているアクションがあるかどうかが示されます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-157">Depicts entities and lists threats found, along with alerts and whether any actions are awaiting approval.</span></span><br/><span data-ttu-id="13bdc-158">グラフ上のアイテムを選択すると、詳細を表示できます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-158">You can select an item on the graph to view more details.</span></span> <span data-ttu-id="13bdc-159">たとえば、[証拠]**アイコンを** 選択すると、[証拠]タブに移動し、検出されたエンティティとその評決を確認できます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-159">For example, selecting the **Evidence** icon takes you to the **Evidence** tab, where you can see detected entities and their verdicts.</span></span> |
| <span data-ttu-id="13bdc-160">**Alerts**</span><span class="sxs-lookup"><span data-stu-id="13bdc-160">**Alerts**</span></span>    | <span data-ttu-id="13bdc-161">調査に関連する警告を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-161">Lists alerts associated with the investigation.</span></span> <span data-ttu-id="13bdc-162">アラートは、ユーザーのデバイス、Office アプリ、Cloud App Security、その他の Microsoft 365 Defender 機能の脅威保護機能から発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="13bdc-162">Alerts can come from threat protection features on a user's device, in Office apps, Cloud App Security, and other Microsoft 365 Defender features.</span></span>|
| <span data-ttu-id="13bdc-163">**デバイス**</span><span class="sxs-lookup"><span data-stu-id="13bdc-163">**Devices**</span></span> | <span data-ttu-id="13bdc-164">調査に含まれるデバイスとその修復レベルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-164">Lists devices included in the investigation along with their remediation level.</span></span> <span data-ttu-id="13bdc-165">(修復レベルは、 [デバイス グループのオートメーション レベルに対応します](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups)。)</span><span class="sxs-lookup"><span data-stu-id="13bdc-165">(Remediation levels correspond to [the automation level for device groups](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups).)</span></span> |
| <span data-ttu-id="13bdc-166">**メールボックス**</span><span class="sxs-lookup"><span data-stu-id="13bdc-166">**Mailboxes**</span></span> |<span data-ttu-id="13bdc-167">検出された脅威の影響を受けたメールボックスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-167">Lists mailboxes that are impacted by detected threats.</span></span>  |
| <span data-ttu-id="13bdc-168">**ユーザー**</span><span class="sxs-lookup"><span data-stu-id="13bdc-168">**Users**</span></span>  | <span data-ttu-id="13bdc-169">検出された脅威の影響を受けたユーザー アカウントを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-169">Lists user accounts that are impacted by detected threats.</span></span> |
| <span data-ttu-id="13bdc-170">**証拠**</span><span class="sxs-lookup"><span data-stu-id="13bdc-170">**Evidence**</span></span> | <span data-ttu-id="13bdc-171">アラート/調査によって発生した証拠の一部を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-171">Lists pieces of evidence raised by alerts/investigations.</span></span> <span data-ttu-id="13bdc-172">評決 (悪意のある、疑 *わしい、* または脅威が見 *つからない*) と修復の状態が含まれます。</span><span class="sxs-lookup"><span data-stu-id="13bdc-172">Includes verdicts (*Malicious*, *Suspicious*, or *No threats found*) and remediation status.</span></span> |
| <span data-ttu-id="13bdc-173">**Entities**</span><span class="sxs-lookup"><span data-stu-id="13bdc-173">**Entities**</span></span>  | <span data-ttu-id="13bdc-174">各エンティティの種類 (悪意のある、疑わしい、または脅威が見つからない)の評決を含む、分析された各エンティティの詳細 *を提供します*。</span><span class="sxs-lookup"><span data-stu-id="13bdc-174">Provides details about each analyzed entity, including a verdict for each entity type (*Malicious*, *Suspicious*, or *No threats found*).</span></span>|
|<span data-ttu-id="13bdc-175">**Log**</span><span class="sxs-lookup"><span data-stu-id="13bdc-175">**Log**</span></span>    | <span data-ttu-id="13bdc-176">アラートがトリガーされた後に行ったすべての調査アクションの時系列的で詳細なビューを提供します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-176">Provides a chronological, detailed view of all the investigation actions taken after an alert was triggered.</span></span>|
| <span data-ttu-id="13bdc-177">**Pending actions (保留中のアクション)**</span><span class="sxs-lookup"><span data-stu-id="13bdc-177">**Pending actions**</span></span> | <span data-ttu-id="13bdc-178">続けるには承認を必要とするアイテムを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-178">Lists items that require approval to proceed.</span></span> <span data-ttu-id="13bdc-179">アクション センター ( ) に移動 [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) して、保留中のアクションを承認します。</span><span class="sxs-lookup"><span data-stu-id="13bdc-179">Go to the Action center ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) to approve pending actions.</span></span> |

## <a name="next-steps"></a><span data-ttu-id="13bdc-180">次の手順</span><span class="sxs-lookup"><span data-stu-id="13bdc-180">Next steps</span></span>

- [<span data-ttu-id="13bdc-181">自動調査後の修復アクションを承認または拒否する</span><span class="sxs-lookup"><span data-stu-id="13bdc-181">Approve or reject remediation actions following an automated investigation</span></span>](m365d-autoir-actions.md)
- [<span data-ttu-id="13bdc-182">修復アクションの詳細</span><span class="sxs-lookup"><span data-stu-id="13bdc-182">Learn more about remediation actions</span></span>](m365d-remediation-actions.md)