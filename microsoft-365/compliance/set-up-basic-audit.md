---
title: Microsoft 365で基本監査を設定する
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-audit
- m365initiative-compliance
- m365solution-scenario
search.appverid:
- MOE150
- MET150
description: この記事では、組織内のユーザーおよび管理者が実行する監査アクティビティの検索を開始できるように、基本監査を設定する方法について説明します。
ms.openlocfilehash: 59b5c85003ef0e19f7d3dd7417f764f446244652
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2021
ms.locfileid: "52564831"
---
# <a name="set-up-basic-audit-in-microsoft-365"></a><span data-ttu-id="ae535-103">Microsoft 365で基本監査を設定する</span><span class="sxs-lookup"><span data-stu-id="ae535-103">Set up Basic Audit in Microsoft 365</span></span>

<span data-ttu-id="ae535-104">Microsoft 365の基本監査では、ユーザーと管理者がさまざまなMicrosoft 365サービスで実行したアクティビティの監査レコードを検索できます。</span><span class="sxs-lookup"><span data-stu-id="ae535-104">Basic Audit in Microsoft 365 lets you search for audit records for activities performed in the different Microsoft 365 services by users and admins.</span></span> <span data-ttu-id="ae535-105">基本監査は、ほとんどのMicrosoft 365およびOffice 365組織で既定で有効になっているため、組織内のユーザーが監査ログを検索する前に行う必要のある操作は、いくつかしかありません。</span><span class="sxs-lookup"><span data-stu-id="ae535-105">Because Basic Audit is enabled by default for most Microsoft 365 and Office 365 organizations, there's only a few things you need to do before you and others in your organization can search the audit log.</span></span>

<span data-ttu-id="ae535-106">この資料では、基本監査を設定するために必要な次の手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae535-106">This article discusses the following steps necessary to set up Basic Audit.</span></span>

![基本監査を設定する手順](../media/BasicAuditingWorkflow.png)

<span data-ttu-id="ae535-108">これらの手順には、監査レコードの生成と保存に必要な組織のサブスクリプションとユーザー ライセンスの確保、およびセキュリティ操作、IT、コンプライアンス、法務チームのチーム メンバーにアクセス許可を割り当てて監査ログを検索できるようにすることが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ae535-108">These steps include ensuring the proper organizational subscriptions and user licensing required to generate and preserve audit records and assigning permissions to team members of your security operations, IT, compliance, and legal teams so that can search the audit log.</span></span>

<span data-ttu-id="ae535-109">詳細については[、「Microsoft 365の基本監査](auditing-solutions-overview.md#basic-audit)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae535-109">For more information, see [Basic Audit in Microsoft 365](auditing-solutions-overview.md#basic-audit).</span></span>

## <a name="step-1-verify-organization-subscription-and-user-licensing"></a><span data-ttu-id="ae535-110">手順 1: 組織のサブスクリプションとユーザー ライセンスを確認する</span><span class="sxs-lookup"><span data-stu-id="ae535-110">Step 1: Verify organization subscription and user licensing</span></span>

<span data-ttu-id="ae535-111">基本監査のライセンスには、監査ログ検索ツールへのアクセスを提供する適切な組織のサブスクリプションと、監査レコードのログ記録と保持に必要なユーザーごとのライセンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="ae535-111">Licensing for Basic Audit requires the appropriate organization subscription that provides access to audit log search tool and per-user licensing that's required to log and retain audit records.</span></span>

<span data-ttu-id="ae535-112">監査されたアクティビティがユーザーや管理者によって実行されると、監査記録が生成され、組織の監査ログに保存されます。</span><span class="sxs-lookup"><span data-stu-id="ae535-112">When an audited activity is performed by a user or admin, an audit record is generated and stored in the audit log for your organization.</span></span> <span data-ttu-id="ae535-113">基本監査では、監査レコードは 90 日間監査ログに保存され、検索可能です。</span><span class="sxs-lookup"><span data-stu-id="ae535-113">In Basic Audit, audit records are retained and searchable in the audit log for 90 days.</span></span>

<span data-ttu-id="ae535-114">基本監査のサブスクリプションおよびライセンス要件の一覧については、「 [Microsoft 365 のソリューションの監査](auditing-solutions-overview.md#licensing-requirements)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae535-114">For a list of subscription and licensing requirements for Basic Audit, see [Auditing solutions in Microsoft 365](auditing-solutions-overview.md#licensing-requirements).</span></span>

## <a name="step-2-assign-permissions-to-search-the-audit-log"></a><span data-ttu-id="ae535-115">手順 2: 監査ログを検索するアクセス許可を割り当てる</span><span class="sxs-lookup"><span data-stu-id="ae535-115">Step 2: Assign permissions to search the audit log</span></span>

<span data-ttu-id="ae535-116">監査ログを検索するには、Exchange Onlineの管理者および調査チームのメンバーにView-Only監査ログまたは監査ログの役割が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae535-116">Admins and members of investigation teams must be assigned the View-Only Audit Logs or Audit Logs role in Exchange Online to search the audit log.</span></span> <span data-ttu-id="ae535-117">既定では、これらの役割は Exchange 管理センターの [**アクセス許可**] ページでコンプライアンス管理役割グループまたは組織管理役割グループに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="ae535-117">By default, these roles are assigned to the Compliance Management and Organization Management role groups on the **Permissions** page in the Exchange admin center.</span></span> <span data-ttu-id="ae535-118">Office 365およびMicrosoft 365のグローバル管理者は、Exchange Onlineの組織管理役割グループのメンバーとして自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="ae535-118">Global administrators in Office 365 and Microsoft 365 are automatically added as members of the Organization Management role group in Exchange Online.</span></span> <span data-ttu-id="ae535-119">最小限の特権レベルで監査ログを検索する権限をユーザーに付与するには、Exchange Online でカスタムの役割グループを作成し、閲覧限定の監査ログまたは監査ログの役割を追加し、この新しい役割グループのメンバーとしてユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="ae535-119">To give a user the ability to search the audit log with the minimum level of privileges, you can create a custom role group in Exchange Online, add the View-Only Audit Logs or Audit Logs role, and then add the user as a member of the new role group.</span></span> <span data-ttu-id="ae535-120">詳細については、「[Exchange Online で役割グループを管理する](/Exchange/permissions-exo/role-groups)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae535-120">For more information, see [Manage role groups in Exchange Online](/Exchange/permissions-exo/role-groups).</span></span>

<span data-ttu-id="ae535-121">次のスクリーンショットは、Exchange管理センターの組織管理役割グループに割り当てられた 2 つの監査関連の役割を示しています。</span><span class="sxs-lookup"><span data-stu-id="ae535-121">The following screenshot shows the two audit-related roles assigned to the Organization Management role group in the Exchange admin center.</span></span>

![Exchange Onlineの役割グループに割り当てられた役割の監査](../media/EACAuditRoles.png)

## <a name="step-3-search-the-audit-log"></a><span data-ttu-id="ae535-123">手順 3: 監査ログを検索する</span><span class="sxs-lookup"><span data-stu-id="ae535-123">Step 3: Search the audit log</span></span>

<span data-ttu-id="ae535-124">これで、Microsoft 365 コンプライアンス センターで監査ログを検索する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="ae535-124">Now you're ready to search the audit log in the Microsoft 365 compliance center.</span></span>

1. <span data-ttu-id="ae535-125"><https://compliance.microsoft.com>適切な監査アクセス許可が割り当てられているアカウントを使用して、に移動してサインインします。</span><span class="sxs-lookup"><span data-stu-id="ae535-125">Go to <https://compliance.microsoft.com> and sign in using an account that has been assigned the appropriate audit permissions.</span></span>

2. <span data-ttu-id="ae535-126">コンプライアンス センターの左側のナビゲーション ウィンドウ Microsoft 365で、[**すべて表示**] をクリックし、[**監査**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae535-126">In the left navigation pane of the Microsoft 365 compliance center, click **Show all** and then click **Audit**.</span></span>

3. <span data-ttu-id="ae535-127">[ **監査** ] ページで、[検索] タブで次の条件を使用して **検索** を構成します。</span><span class="sxs-lookup"><span data-stu-id="ae535-127">On the **Audit** page, configure the search using the following conditions on the **Search** tab.</span></span> 

   ![監査ログ検索の構成設定](../media/AuditLogSearchToolMCCCallouts.png)

   1. <span data-ttu-id="ae535-129">**日付と時刻の範囲**。</span><span class="sxs-lookup"><span data-stu-id="ae535-129">**Date and time range**.</span></span> <span data-ttu-id="ae535-130">日付と時間の範囲を選択し、その期間内に発生したイベントを表示します。</span><span class="sxs-lookup"><span data-stu-id="ae535-130">Select a date and time range to display the events that occurred within that period.</span></span> <span data-ttu-id="ae535-131">日付と時刻は、ローカル時刻で表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae535-131">The date and time are presented in local time.</span></span> <span data-ttu-id="ae535-132">デフォルトでは、過去 7 日間が選択されます。</span><span class="sxs-lookup"><span data-stu-id="ae535-132">The last seven days are selected by default.</span></span>
  
   2. <span data-ttu-id="ae535-133">**活動**:</span><span class="sxs-lookup"><span data-stu-id="ae535-133">**Activities**.</span></span> <span data-ttu-id="ae535-134">検索する活動を選択します。</span><span class="sxs-lookup"><span data-stu-id="ae535-134">Select the activities to search for.</span></span> <span data-ttu-id="ae535-135">検索ボックスを使用して、リストに追加する活動を検索します。</span><span class="sxs-lookup"><span data-stu-id="ae535-135">Use the search box to search for activities to add to the list.</span></span> <span data-ttu-id="ae535-136">監査対象アクティビティの一部については、「 [監査されたアクティビティ](search-the-audit-log-in-security-and-compliance.md#audited-activities)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae535-136">For a partial list of audited activities, see [Audited activities](search-the-audit-log-in-security-and-compliance.md#audited-activities).</span></span> <span data-ttu-id="ae535-137">このボックスを空白のままにすると、すべての監査対象アクティビティのエントリが返されます。</span><span class="sxs-lookup"><span data-stu-id="ae535-137">Leave this box blank to return entries for all audited activities.</span></span>
  
   3. <span data-ttu-id="ae535-138">**ユーザー**。</span><span class="sxs-lookup"><span data-stu-id="ae535-138">**Users**.</span></span>  <span data-ttu-id="ae535-139">このボックスをクリックして、検索結果を表示するユーザーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="ae535-139">Click in this box and start typing the name of users to display search results for.</span></span> <span data-ttu-id="ae535-140">このボックスで選択したユーザーが実行した、選択したアクティビティの監査ログ エントリが、結果の一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae535-140">The audit log entries for the selected activities performed by the users you select in this box are displayed in the list of results.</span></span> <span data-ttu-id="ae535-141">組織のすべてのユーザー (およびサービス アカウント) のエントリを返すには、このボックスを空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="ae535-141">Leave this box blank to return entries for all users (and service accounts) in your organization.</span></span>
  
   4. <span data-ttu-id="ae535-142">**ファイル、フォルダ、またはサイト**</span><span class="sxs-lookup"><span data-stu-id="ae535-142">**File, folder, or site**.</span></span> <span data-ttu-id="ae535-143">指定したキーワードを含むフォルダーのファイルに関連するアクティビティーを検索するには、ファイル名またはフォルダー名の一部またはすべてを入力します。</span><span class="sxs-lookup"><span data-stu-id="ae535-143">Type some or all of a file or folder name to search for activity related to the file of folder that contains the specified keyword.</span></span> <span data-ttu-id="ae535-144">ファイルまたはフォルダーの URL を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ae535-144">You can also specify a URL of a file or folder.</span></span> <span data-ttu-id="ae535-145">ファイルまたはフォルダの URL を使用する場合は、絶対 URL パスを入力するか、URL の一部を入力する場合は、特殊文字やスペースを含まないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="ae535-145">If you use a URL of a file or folder, be sure the type the full URL path or if you type a portion of the URL, don't include any special characters or spaces.</span></span> <span data-ttu-id="ae535-146">組織内のすべてのファイルおよびフォルダーのエントリを返すには、このボックスを空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="ae535-146">Leave this box blank to return entries for all files and folders in your organization.</span></span>

4. <span data-ttu-id="ae535-147">[ **検索** ] をクリックして検索を実行します。</span><span class="sxs-lookup"><span data-stu-id="ae535-147">Click **Search** to run the search.</span></span>

<span data-ttu-id="ae535-148">監査ログ検索が実行されていることを示す新しいページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae535-148">A new page is display that shows the audit log search is running.</span></span> <span data-ttu-id="ae535-149">検索が完了すると、ページに監査レコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae535-149">When the search is completed, audit records are displayed on the page.</span></span> <span data-ttu-id="ae535-150">詳細なプロパティを含むフライアウト ページを表示するには、レコードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae535-150">Click a record to display a flyout page with detailed properties.</span></span>

<span data-ttu-id="ae535-151">詳細な手順については、 [コンプライアンス センターで監査ログを検索するを](search-the-audit-log-in-security-and-compliance.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae535-151">For more detailed instructions, see [Search the audit log in the compliance center](search-the-audit-log-in-security-and-compliance.md).</span></span>