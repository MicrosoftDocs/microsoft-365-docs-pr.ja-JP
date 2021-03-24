---
title: 管理者の申請
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: 管理者は、セキュリティ & コンプライアンス センターの Submits ポータルを使用して、疑わしいメール、フィッシングメール、スパム、その他有害な可能性のあるメッセージ、URL、ファイルを Microsoft に送信してスキャンする方法について説明します。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3dd566de3ba4b4281b19c423b8623f081c378bca
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51065651"
---
# <a name="use-admin-submission-to-submit-suspected-spam-phish-urls-and-files-to-microsoft"></a><span data-ttu-id="c6fe7-103">管理者送信を使用して、疑いがあるスパム、フィッシング、URL、ファイルを Microsoft に提出する</span><span class="sxs-lookup"><span data-stu-id="c6fe7-103">Use Admin Submission to submit suspected spam, phish, URLs, and files to Microsoft</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

<span data-ttu-id="c6fe7-104">**適用対象**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-104">**Applies to**</span></span>
- [<span data-ttu-id="c6fe7-105">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="c6fe7-105">Exchange Online Protection</span></span>](exchange-online-protection-overview.md)
- [<span data-ttu-id="c6fe7-106">Microsoft Defender for Office 365 プラン 1 およびプラン 2</span><span class="sxs-lookup"><span data-stu-id="c6fe7-106">Microsoft Defender for Office 365 plan 1 and plan 2</span></span>](defender-for-office-365.md)


<span data-ttu-id="c6fe7-107">Exchange Online のメールボックスを持つ Microsoft 365 組織では、管理者はセキュリティ & コンプライアンス センターの Submits ポータルを使用して、電子メール メッセージ、URL、添付ファイルをスキャンのために Microsoft に送信できます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-107">In Microsoft 365 organizations with mailboxes in Exchange Online, admins can use the Submissions portal in the Security & Compliance Center to submit email messages, URLs, and attachments to Microsoft for scanning.</span></span>

<span data-ttu-id="c6fe7-108">電子メール メッセージを送信すると、次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-108">When you submit an email message, you will get:</span></span>

1. <span data-ttu-id="c6fe7-109">**電子メール認証チェック**: 電子メール認証が配信された際に合格または失敗したかどうかの詳細。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-109">**Email authentication check**: Details on whether email authentication passed or failed when it was delivered.</span></span>
2. <span data-ttu-id="c6fe7-110">**ポリシーヒット**: テナントへの受信メールを許可またはブロックした可能性があるポリシーに関する情報で、サービス フィルターの評決を上書きします。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-110">**Policy hits**: Information about any policies that may have allowed or blocked the incoming email into your tenant, overriding our service filter verdicts.</span></span>
3. <span data-ttu-id="c6fe7-111">**ペイロード評価/デトレーション**: メッセージ内の URL と添付ファイルの検査。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-111">**Payload reputation/detonation**: Examination of any URLs and attachments in the message.</span></span>
4. <span data-ttu-id="c6fe7-112">**Grader 分析**: メッセージが悪意のあるかどうかを確認するために、人間の採点者が行うレビュー。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-112">**Grader analysis**: Review done by human graders in order to confirm whether or not messages are malicious.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6fe7-113">ペイロード評価/デトナレーションおよび採点者分析は、すべてのテナントで行われるという問題ではありません。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-113">Payload reputation/detonation and grader analysis are not done in all tenants.</span></span> <span data-ttu-id="c6fe7-114">データがコンプライアンスの目的でテナント境界から離れるはずではない場合、情報は組織外に出るのをブロックされます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-114">Information is blocked from going outside the organization when data is not supposed to leave the tenant boundary for compliance purposes.</span></span>

<span data-ttu-id="c6fe7-115">電子メール メッセージ、URL、添付ファイルを Microsoft に送信するその他の方法については、「メッセージとファイルを Microsoft に報告する」 [を参照してください](report-junk-email-messages-to-microsoft.md)。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-115">For other ways to submit email messages, URLs, and attachments to Microsoft, see [Report messages and files to Microsoft](report-junk-email-messages-to-microsoft.md).</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="c6fe7-116">はじめに把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="c6fe7-116">What do you need to know before you begin?</span></span>

- <span data-ttu-id="c6fe7-117"><https://protection.office.com/> でセキュリティ/コンプライアンス センターを開きます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-117">You open the Security & Compliance Center at <https://protection.office.com/>.</span></span> <span data-ttu-id="c6fe7-118">[申請] ページに直接 **移動するには** 、 を使用します <https://protection.office.com/reportsubmission> 。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-118">To go directly to the **Submission** page, use <https://protection.office.com/reportsubmission>.</span></span>

- <span data-ttu-id="c6fe7-119">メッセージとファイルを Microsoft に送信するには、次のいずれかの役割グループのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-119">To submit messages and files to Microsoft, you need to be a member of one of the following role groups:</span></span>

  - <span data-ttu-id="c6fe7-120">**組織の管理** または [セキュリティ/コンプライアンス センター](permissions-in-the-security-and-compliance-center.md)の **セキュリティ管理者**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-120">**Organization Management** or **Security Administrator** in the [Security & Compliance Center](permissions-in-the-security-and-compliance-center.md).</span></span>

  - <span data-ttu-id="c6fe7-121">Exchange **Online の**[組織の管理](/Exchange/permissions-exo/permissions-exo#role-groups)。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-121">**Organization Management** in [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups).</span></span>

    <span data-ttu-id="c6fe7-122">この記事で後述するように、カスタム メールボックスへの[](#view-user-submissions-to-the-custom-mailbox)ユーザー申請を表示するには、この役割グループのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-122">Note that membership in this role group is required to [View user submissions to the custom mailbox](#view-user-submissions-to-the-custom-mailbox) as described later in this article.</span></span>

- <span data-ttu-id="c6fe7-123">ユーザーがメッセージとファイルを Microsoft に送信する方法の詳細については、「メッセージとファイルを Microsoft に報告する」 [を参照してください](report-junk-email-messages-to-microsoft.md)。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-123">For more information about how users can submit messages and files to Microsoft, see [Report messages and files to Microsoft](report-junk-email-messages-to-microsoft.md).</span></span>

## <a name="report-suspicious-content-to-microsoft"></a><span data-ttu-id="c6fe7-124">疑わしいコンテンツを Microsoft に報告する</span><span class="sxs-lookup"><span data-stu-id="c6fe7-124">Report suspicious content to Microsoft</span></span>

1. <span data-ttu-id="c6fe7-125">[セキュリティ & コンプライアンス センター] で、[脅威管理の申請] に移動し、[管理者の申請] タブで [新しい申請] をクリックします \> 。  </span><span class="sxs-lookup"><span data-stu-id="c6fe7-125">In the Security & Compliance Center, go to **Threat management** \> **Submissions**, verify that you're on the **Admin submissions** tab, and then click **New submission**.</span></span>

2. <span data-ttu-id="c6fe7-126">次 **のセクションで** 説明するように、メッセージ、URL、または添付ファイルを送信するために表示される新しい申請フライアウトを使用します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-126">Use **New submission** flyout that appears to submit the message, URL, or attachment as described in the following sections.</span></span>

### <a name="submit-a-questionable-email-to-microsoft"></a><span data-ttu-id="c6fe7-127">疑いがある電子メールを Microsoft に送信する</span><span class="sxs-lookup"><span data-stu-id="c6fe7-127">Submit a questionable email to Microsoft</span></span>

1. <span data-ttu-id="c6fe7-128">[オブジェクトの **種類] セクションで** 、[メール] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-128">In the **Object type** section, select **Email**.</span></span> <span data-ttu-id="c6fe7-129">[提出 **形式] セクション** で、次のいずれかのオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-129">In the **Submission format** section, use one of the following options:</span></span>

   - <span data-ttu-id="c6fe7-130">**ネットワーク メッセージ ID**: これは、メッセージの **X-MS-Exchange-Organization-Network-Message-Id** ヘッダー、または検疫済みメッセージの **X-MS-Office365-Filtering-Correlation-Id** ヘッダーで使用できる GUID 値です。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-130">**Network Message ID**: This is a GUID value that's available in the **X-MS-Exchange-Organization-Network-Message-Id** header in the message, or in the **X-MS-Office365-Filtering-Correlation-Id** header in quarantined messages.</span></span>

   - <span data-ttu-id="c6fe7-131">**ファイル**: [ファイルの **選択] をクリックします**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-131">**File**: Click **Choose file**.</span></span> <span data-ttu-id="c6fe7-132">開いたダイアログで、.eml ファイルまたは .msg ファイルを見つけて選択し、[開く] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-132">In the dialog that opens, find and select the .eml or .msg file, and then click **Open**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="c6fe7-133">365 プラン 1 またはプラン 2 Office Defender を使用する管理者は、30 日間の古いメッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-133">Admins with Defender for Office 365 Plan 1 or Plan 2 are able to submit messages as old as 30 days.</span></span> <span data-ttu-id="c6fe7-134">他の管理者は、7 日間だけ戻って行くことができます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-134">Other admins will only be able to go back 7 days.</span></span>

2. <span data-ttu-id="c6fe7-135">[受信者 **] セクション** で、ポリシー チェックを実行する 1 つ以上の受信者を指定します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-135">In the **Recipients** section, specify one or more recipients that you would like to run a policy check against.</span></span> <span data-ttu-id="c6fe7-136">ポリシー チェックは、ユーザーまたは組織のポリシーが原因で電子メールがスキャンをバイパスしたかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-136">The policy check will determine if the email bypassed scanning due to user or organization policies.</span></span>

3. <span data-ttu-id="c6fe7-137">[申請 **の理由] セクション** で、次のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-137">In the **Reason for submission** section, select one of the following options:</span></span>

   - <span data-ttu-id="c6fe7-138">**ブロックされていない必要があります**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-138">**Should not have been blocked**</span></span>

   - <span data-ttu-id="c6fe7-139">**ブロックされている必要があります**: [スパム **]、[\*\*\*\*フィッシング]、または [マルウェア]** を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-139">**Should have been blocked**: Select **Spam**, **Phishing**, or **Malware**.</span></span> <span data-ttu-id="c6fe7-140">不明な場合は、最善の判断を下してください。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-140">If you're not sure, use your best judgment.</span></span>

4. <span data-ttu-id="c6fe7-141">完了したら、[送信] ボタン **をクリック** します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-141">When you're finished, click the **Submit** button.</span></span>

   ![URL 申請の例](../../media/submission-flyout-email.PNG)

### <a name="send-a-suspect-url-to-microsoft"></a><span data-ttu-id="c6fe7-143">疑わしい URL を Microsoft に送信する</span><span class="sxs-lookup"><span data-stu-id="c6fe7-143">Send a suspect URL to Microsoft</span></span>

1. <span data-ttu-id="c6fe7-144">[オブジェクトの **種類] セクションで\*\*\*\*、[URL] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-144">In the **Object type** section, select **URL**.</span></span> <span data-ttu-id="c6fe7-145">表示されるボックスに、完全な URL (たとえば) を入力 `https://www.fabrikam.com/marketing.html` します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-145">In the box that appears, enter the full URL (for example, `https://www.fabrikam.com/marketing.html`).</span></span>

2. <span data-ttu-id="c6fe7-146">[申請 **の理由] セクション** で、次のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-146">In the **Reason for submission** section, select one of the following options:</span></span>

   - <span data-ttu-id="c6fe7-147">**ブロックされていない必要があります**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-147">**Should not have been blocked**</span></span>

   - <span data-ttu-id="c6fe7-148">**ブロックされている必要があります**: [フィッシング] または [**マルウェア] を\*\*\*\*選択します**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-148">**Should have been blocked**: Select **Phishing** or **Malware**.</span></span>

3. <span data-ttu-id="c6fe7-149">完了したら、[送信] ボタン **をクリック** します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-149">When you're finished, click the **Submit** button.</span></span>

   ![電子メール送信の例](../../media/submission-url-flyout.png)

### <a name="submit-a-suspected-file-to-microsoft"></a><span data-ttu-id="c6fe7-151">疑わしいファイルを Microsoft に提出する</span><span class="sxs-lookup"><span data-stu-id="c6fe7-151">Submit a suspected file to Microsoft</span></span>

1. <span data-ttu-id="c6fe7-152">[オブジェクトの **種類] セクションで** 、[添付ファイル] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-152">In the **Object type** section, select **Attachment**.</span></span>

2. <span data-ttu-id="c6fe7-153">[ファイル **の選択] をクリックします**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-153">Click **Choose File**.</span></span> <span data-ttu-id="c6fe7-154">開いたダイアログで、ファイルを見つけて選択し、[開く] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-154">In the dialog that opens, find and select the file, and then click **Open**.</span></span>

3. <span data-ttu-id="c6fe7-155">[申請 **の理由] セクション** で、次のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-155">In the **Reason for submission** section, select one of the following options:</span></span>

   - <span data-ttu-id="c6fe7-156">**ブロックされていない必要があります**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-156">**Should not have been blocked**</span></span>

   - <span data-ttu-id="c6fe7-157">**ブロックされている必要があります:\*\*\*\*マルウェア** だけが選択され、自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-157">**Should have been blocked**: **Malware** is the only choice, and is automatically selected..</span></span>

4. <span data-ttu-id="c6fe7-158">完了したら、[送信] ボタン **をクリック** します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-158">When you're finished, click the **Submit** button.</span></span>

   ![添付ファイルの提出例](../../media/submission-file-flyout.PNG)

## <a name="view-admin-submissions"></a><span data-ttu-id="c6fe7-160">管理者の申請を表示する</span><span class="sxs-lookup"><span data-stu-id="c6fe7-160">View admin submissions</span></span>

<span data-ttu-id="c6fe7-161">[セキュリティ & コンプライアンス センター] で、[脅威管理の申請] に移動し、[管理者の申請] タブで [新しい申請] をクリックします \> 。  </span><span class="sxs-lookup"><span data-stu-id="c6fe7-161">In the Security & Compliance Center, go to **Threat management** \> **Submissions**, verify that you're on the **Admin submissions** tab, and then click **New submission**.</span></span>

<span data-ttu-id="c6fe7-162">ページの上部付近では、開始日、終了日、および (既定で) ボックスに値を入力し、[更新] ボタンをクリックして、申請 **ID** (すべての申請に割り当てられている GUID 値) でフィルター処理できます。 ![ ](../../media/scc-quarantine-refresh.png)</span><span class="sxs-lookup"><span data-stu-id="c6fe7-162">Near the top of the page, you can enter a start date, an end date, and (by default) you can filter by **Submission ID** (a GUID value that's assigned to every submission) by entering a value in the box and clicking ![Refresh button](../../media/scc-quarantine-refresh.png).</span></span> <span data-ttu-id="c6fe7-163">Update</span><span class="sxs-lookup"><span data-stu-id="c6fe7-163">You can enter multiple values separated by commas.</span></span>

<span data-ttu-id="c6fe7-164">フィルター条件を変更するには、[申請 **ID]** ボタンをクリックし、次のいずれかの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-164">To change the filter criteria, click the **Submission ID** button and choose one of the following values:</span></span>

- <span data-ttu-id="c6fe7-165">**Sender**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-165">**Sender**</span></span>
- <span data-ttu-id="c6fe7-166">**件名/URL/ファイル名**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-166">**Subject/URL/File name**</span></span>
- <span data-ttu-id="c6fe7-167">**提出者**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-167">**Submitted by**</span></span>
- <span data-ttu-id="c6fe7-168">**申請の種類**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-168">**Submission type**</span></span>
- <span data-ttu-id="c6fe7-169">**状態**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-169">**Status**</span></span>

![管理者申請のフィルター オプション](../../media/admin-submission-email-filter-options.png)

<span data-ttu-id="c6fe7-171">結果をエクスポートするには、ページの上部 **にある [エクスポート** ] をクリックし、[グラフ データ] または [ **テーブル** ] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-171">To export the results, click **Export** near the top of the page and select **Chart data** or **Table**.</span></span> <span data-ttu-id="c6fe7-172">表示されるダイアログで、.csv ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-172">In the dialog that appears, save the .csv file.</span></span>

<span data-ttu-id="c6fe7-173">グラフの下には、メール **(既定\*\*\*\*)、URL、** 添付ファイルの 3 つのタブ **があります**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-173">Below the graph, there are three tabs: **Email** (default), **URL**, and **Attachment**.</span></span>

### <a name="view-admin-email-submissions"></a><span data-ttu-id="c6fe7-174">管理メールの送信を表示する</span><span class="sxs-lookup"><span data-stu-id="c6fe7-174">View admin email submissions</span></span>

<span data-ttu-id="c6fe7-175">[メール] **タブをクリック** します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-175">Click the **Email** tab.</span></span>

<span data-ttu-id="c6fe7-176">ページの下部にある **[列のオプション** ] ボタンをクリックすると、ビューに列を追加または削除できます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-176">You can click the **Column options** button near the bottom of the page to add or remove columns from the view:</span></span>

- <span data-ttu-id="c6fe7-177">**日付**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-177">**Date**</span></span>
- <span data-ttu-id="c6fe7-178">**申請 ID**: すべての申請に割り当てられている GUID 値。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-178">**Submission ID**: A GUID value that's assigned to every submission.</span></span>
- <span data-ttu-id="c6fe7-179">**提出者**<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="c6fe7-179">**Submitted by**<sup>\*</sup></span></span>
- <span data-ttu-id="c6fe7-180">**[件名]**<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="c6fe7-180">**Subject**<sup>\*</sup></span></span>
- <span data-ttu-id="c6fe7-181">**Sender**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-181">**Sender**</span></span>
- <span data-ttu-id="c6fe7-182">[**Sender IP (送信者の IP)**<sup>\*</sup>]</span><span class="sxs-lookup"><span data-stu-id="c6fe7-182">**Sender IP**<sup>\*</sup></span></span>
- <span data-ttu-id="c6fe7-183">**申請の種類**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-183">**Submission type**</span></span>
- <span data-ttu-id="c6fe7-184">**配信理由**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-184">**Delivery reason**</span></span>
- <span data-ttu-id="c6fe7-185">**状態**<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="c6fe7-185">**Status**<sup>\*</sup></span></span>

  <span data-ttu-id="c6fe7-186"><sup>\*</sup> この値をクリックすると、詳細情報がフライアウトに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-186"><sup>\*</sup> If you click this value, detailed information is displayed in a flyout.</span></span>

#### <a name="admin-submission-rescan-details"></a><span data-ttu-id="c6fe7-187">管理者申請の再スキャンの詳細</span><span class="sxs-lookup"><span data-stu-id="c6fe7-187">Admin submission rescan details</span></span>

<span data-ttu-id="c6fe7-188">管理者の申請で送信されたメッセージは再スキャンされ、詳細フライアウトに結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-188">Messages that are submitted in admin submissions are rescanned and results shown in the details flyout:</span></span>

- <span data-ttu-id="c6fe7-189">配信時に送信者のメール認証に失敗した場合。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-189">If there was a failure in the sender's email authentication at the time of delivery.</span></span>
- <span data-ttu-id="c6fe7-190">メッセージのセキュリティ判定に影響を与える、または上書きされる可能性があるポリシー ヒットに関する情報。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-190">Information about any policy hits that could have affected or overridden the verdict of a message.</span></span>
- <span data-ttu-id="c6fe7-191">現在の爆発的な結果により、メッセージに含まれる URL またはファイルが悪意のあるものかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-191">Current detonation results to see if the URLs or files contained in the message were malicious or not.</span></span>
- <span data-ttu-id="c6fe7-192">成績者からのフィードバック。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-192">Feedback from graders.</span></span>

<span data-ttu-id="c6fe7-193">上書きが見つかった場合、再スキャンは数分で完了します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-193">If an override was found, the rescan should complete in several minutes.</span></span> <span data-ttu-id="c6fe7-194">メール認証や配信に問題が発生しない場合は、上書きによって影響を受けなかった場合、採点者からのフィードバックは最大で 1 日かかる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-194">If there wasn't a problem in email authentication or delivery wasn't affected by an override, then the feedback from graders could take up to a day.</span></span>

### <a name="view-admin-url-submissions"></a><span data-ttu-id="c6fe7-195">管理者 URL の申請を表示する</span><span class="sxs-lookup"><span data-stu-id="c6fe7-195">View admin URL submissions</span></span>

<span data-ttu-id="c6fe7-196">**[URL] タブをクリック** します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-196">Click the **URL** tab.</span></span>

<span data-ttu-id="c6fe7-197">ページの下部にある **[列のオプション** ] ボタンをクリックすると、ビューに列を追加または削除できます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-197">You can click the **Column options** button near the bottom of the page to add or remove columns from the view:</span></span>

- <span data-ttu-id="c6fe7-198">**日付**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-198">**Date**</span></span>
- <span data-ttu-id="c6fe7-199">**申請 ID**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-199">**Submission ID**</span></span>
- <span data-ttu-id="c6fe7-200">**提出者**<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="c6fe7-200">**Submitted by**<sup>\*</sup></span></span>
- <span data-ttu-id="c6fe7-201">[**URL**<sup>\*</sup>]</span><span class="sxs-lookup"><span data-stu-id="c6fe7-201">**URL**<sup>\*</sup></span></span>
- <span data-ttu-id="c6fe7-202">**申請の種類**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-202">**Submission type**</span></span>
- <span data-ttu-id="c6fe7-203">**状態**<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="c6fe7-203">**Status**<sup>\*</sup></span></span>

  <span data-ttu-id="c6fe7-204"><sup>\*</sup> この値をクリックすると、詳細情報がフライアウトに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-204"><sup>\*</sup> If you click this value, detailed information is displayed in a flyout.</span></span>

### <a name="view-admin-attachment-submissions"></a><span data-ttu-id="c6fe7-205">管理者の添付ファイルの申請を表示する</span><span class="sxs-lookup"><span data-stu-id="c6fe7-205">View admin attachment submissions</span></span>

<span data-ttu-id="c6fe7-206">[添付ファイル **] タブを** クリックします。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-206">Click the **Attachments** tab.</span></span>

<span data-ttu-id="c6fe7-207">ページの下部にある **[列のオプション** ] ボタンをクリックすると、ビューに列を追加または削除できます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-207">You can click the **Column options** button near the bottom of the page to add or remove columns from the view:</span></span>

- <span data-ttu-id="c6fe7-208">**日付**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-208">**Date**</span></span>
- <span data-ttu-id="c6fe7-209">**申請 ID**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-209">**Submission ID**</span></span>
- <span data-ttu-id="c6fe7-210">**提出者**<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="c6fe7-210">**Submitted by**<sup>\*</sup></span></span>
- <span data-ttu-id="c6fe7-211">**ファイル名**<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="c6fe7-211">**File name**<sup>\*</sup></span></span>
- <span data-ttu-id="c6fe7-212">**申請の種類**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-212">**Submission type**</span></span>
- <span data-ttu-id="c6fe7-213">**状態**<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="c6fe7-213">**Status**<sup>\*</sup></span></span>

  <span data-ttu-id="c6fe7-214"><sup>\*</sup> この値をクリックすると、詳細情報がフライアウトに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-214"><sup>\*</sup> If you click this value, detailed information is displayed in a flyout.</span></span>

## <a name="view-user-submissions-to-microsoft"></a><span data-ttu-id="c6fe7-215">Microsoft へのユーザー申請の表示</span><span class="sxs-lookup"><span data-stu-id="c6fe7-215">View user submissions to Microsoft</span></span>

<span data-ttu-id="c6fe7-216">レポート メッセージ アドイン、レポート[](enable-the-report-message-add-in.md)フィッシング アドイン、またはユーザー[](enable-the-report-phish-add-in.md)が[Outlook on the web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md)で組み込みのレポートを使用している場合は、[ユーザーの申請] タブでユーザーが報告している情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-216">If you've deployed the [Report Message add-in](enable-the-report-message-add-in.md), the [Report Phishing add-in](enable-the-report-phish-add-in.md), or people use the [built-in reporting in Outlook on the web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md), you can see what users are reporting on the **User submissions** tab.</span></span>

1. <span data-ttu-id="c6fe7-217">セキュリティ 管理コンプライアンス センター&、脅威管理 **の申請に** \> **移動します**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-217">In the Security & Compliance Center, go to **Threat management** \> **Submissions**.</span></span>

2. <span data-ttu-id="c6fe7-218">[ユーザー申請 **] タブを選択** し、[新しい申請] **をクリックします**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-218">Select the **User submissions** tab, and then click **New submission**.</span></span>

<span data-ttu-id="c6fe7-219">ページの下部にある **[列のオプション** ] ボタンをクリックすると、ビューに列を追加または削除できます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-219">You can click the **Column options** button near the bottom of the page to add or remove columns from the view:</span></span>

- <span data-ttu-id="c6fe7-220">**送信済み**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-220">**Submitted on**</span></span>
- <span data-ttu-id="c6fe7-221">**提出者**<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="c6fe7-221">**Submitted by**<sup>\*</sup></span></span>
- <span data-ttu-id="c6fe7-222">**[件名]**<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="c6fe7-222">**Subject**<sup>\*</sup></span></span>
- <span data-ttu-id="c6fe7-223">**Sender**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-223">**Sender**</span></span>
- <span data-ttu-id="c6fe7-224">[**Sender IP (送信者の IP)**<sup>\*</sup>]</span><span class="sxs-lookup"><span data-stu-id="c6fe7-224">**Sender IP**<sup>\*</sup></span></span>
- <span data-ttu-id="c6fe7-225">**申請の種類**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-225">**Submission type**</span></span>

<span data-ttu-id="c6fe7-226"><sup>\*</sup> この値をクリックすると、詳細情報がフライアウトに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-226"><sup>\*</sup> If you click this value, detailed information is displayed in a flyout.</span></span>

<span data-ttu-id="c6fe7-227">ページの上部付近では、開始日、終了日、および (既定で) ボックスに値を入力し、[更新]ボタンをクリックして Sender でフィルター ![ 処理できます ](../../media/scc-quarantine-refresh.png) 。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-227">Near the top of the page, you can enter a start date, an end date, and (by default) you can filter by **Sender** by entering a value in the box and clicking ![Refresh button](../../media/scc-quarantine-refresh.png).</span></span> <span data-ttu-id="c6fe7-228">Update</span><span class="sxs-lookup"><span data-stu-id="c6fe7-228">You can enter multiple values separated by commas.</span></span>

<span data-ttu-id="c6fe7-229">フィルター条件を変更するには、[送信者] ボタン **を** クリックし、次のいずれかの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-229">To change the filter criteria, click the **Sender** button and choose one of the following values:</span></span>

- <span data-ttu-id="c6fe7-230">**送信元ドメイン**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-230">**Sender domain**</span></span>
- <span data-ttu-id="c6fe7-231">**件名**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-231">**Subject**</span></span>
- <span data-ttu-id="c6fe7-232">**提出者**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-232">**Submitted by**</span></span>
- <span data-ttu-id="c6fe7-233">**申請の種類**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-233">**Submission type**</span></span>
- <span data-ttu-id="c6fe7-234">[**Sender IP (送信者の IP)**]</span><span class="sxs-lookup"><span data-stu-id="c6fe7-234">**Sender IP**</span></span>

![ユーザー申請のフィルター オプション](../../media/user-submissions-filter-options.png)

<span data-ttu-id="c6fe7-236">結果をエクスポートするには、ページの上部 **にある [エクスポート** ] をクリックし、[グラフ データ] または [ **テーブル** ] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-236">To export the results, click **Export** near the top of the page and select **Chart data** or **Table**.</span></span> <span data-ttu-id="c6fe7-237">表示されるダイアログで、.csv ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-237">In the dialog that appears, save the .csv file.</span></span>

## <a name="view-user-submissions-to-the-custom-mailbox"></a><span data-ttu-id="c6fe7-238">カスタム メールボックスへのユーザー申請の表示</span><span class="sxs-lookup"><span data-stu-id="c6fe7-238">View user submissions to the custom mailbox</span></span>

<span data-ttu-id="c6fe7-239">**ユーザー** が報告した [メッセージを](user-submission.md) 受信するようにカスタム メールボックスを構成している場合は、レポート メールボックスに配信されたメッセージを表示および送信できます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-239">**If** you've [configured a custom mailbox](user-submission.md) to receive user reported messages, you can view and also submit messages that were delivered to the reporting mailbox.</span></span>

1. <span data-ttu-id="c6fe7-240">セキュリティ 管理コンプライアンス センター&、脅威管理 **の申請に** \> **移動します**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-240">In the Security & Compliance Center, go to **Threat management** \> **Submissions**.</span></span>

2. <span data-ttu-id="c6fe7-241">[カスタム メールボックス **] タブを** 選択します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-241">Select the **Custom mailbox** tab.</span></span>

<span data-ttu-id="c6fe7-242">ページの下部にある **[列のオプション** ] ボタンをクリックすると、ビューに列を追加または削除できます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-242">You can click the **Column options** button near the bottom of the page to add or remove columns from the view:</span></span>

- <span data-ttu-id="c6fe7-243">**送信済み**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-243">**Submitted on**</span></span>
- <span data-ttu-id="c6fe7-244">**提出者**<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="c6fe7-244">**Submitted by**<sup>\*</sup></span></span>
- <span data-ttu-id="c6fe7-245">**[件名]**<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="c6fe7-245">**Subject**<sup>\*</sup></span></span>
- <span data-ttu-id="c6fe7-246">**Sender**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-246">**Sender**</span></span>
- <span data-ttu-id="c6fe7-247">[**Sender IP (送信者の IP)**<sup>\*</sup>]</span><span class="sxs-lookup"><span data-stu-id="c6fe7-247">**Sender IP**<sup>\*</sup></span></span>
- <span data-ttu-id="c6fe7-248">**申請の種類**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-248">**Submission type**</span></span>

<span data-ttu-id="c6fe7-249">ページの上部の近くに開始日、終了日を入力し、ボックスに値を入力し、[更新]ボタンをクリックして[送信済み] でフィルター ![ 処理できます ](../../media/scc-quarantine-refresh.png) 。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-249">Near the top of the page, you can enter a start date, an end date, and you can filter by **Submitted by** by entering a value in the box and clicking ![Refresh button](../../media/scc-quarantine-refresh.png).</span></span> <span data-ttu-id="c6fe7-250">Update</span><span class="sxs-lookup"><span data-stu-id="c6fe7-250">You can enter multiple values separated by commas.</span></span>

<span data-ttu-id="c6fe7-251">結果をエクスポートするには、ページの上部 **にある [エクスポート** ] をクリックし、[グラフ データ] または [ **テーブル** ] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-251">To export the results, click **Export** near the top of the page and select **Chart data** or **Table**.</span></span> <span data-ttu-id="c6fe7-252">表示されるダイアログで、.csv ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-252">In the dialog that appears, save the .csv file.</span></span>

## <a name="undo-user-submissions"></a><span data-ttu-id="c6fe7-253">ユーザー申請の元に戻す</span><span class="sxs-lookup"><span data-stu-id="c6fe7-253">Undo user submissions</span></span>

<span data-ttu-id="c6fe7-254">ユーザーが不審なメールをカスタム メールボックスに送信すると、ユーザーと管理者は申請を元に戻すオプションを使用できません。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-254">Once a user submits a suspicious email to the custom mailbox, the user and admin don't have an option to undo the submission.</span></span> <span data-ttu-id="c6fe7-255">ユーザーが電子メールを回復する場合は、削除済みアイテムまたは迷惑メール フォルダーで回復できます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-255">If the user would like to recover the email, it will be available for recovery in the Deleted Items or Junk Email folders.</span></span>

### <a name="submit-messages-to-microsoft-from-the-custom-mailbox"></a><span data-ttu-id="c6fe7-256">カスタム メールボックスから Microsoft にメッセージを送信する</span><span class="sxs-lookup"><span data-stu-id="c6fe7-256">Submit messages to Microsoft from the custom mailbox</span></span>

<span data-ttu-id="c6fe7-257">Microsoft にメッセージを送信せずにユーザーが報告したメッセージを傍受するようにカスタム メールボックスを構成している場合は、特定のメッセージを見つけて分析のために Microsoft に送信できます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-257">If you've configured the custom mailbox to intercept user-reported messages without sending the messages to Microsoft, you can find and send specific messages to Microsoft for analysis.</span></span> <span data-ttu-id="c6fe7-258">これにより、ユーザーの申請が管理者申請に効果的に移動されます。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-258">This effectively moves a user submission to an admin submission.</span></span>

<span data-ttu-id="c6fe7-259">[カスタム **メールボックス] タブ** で、一覧でメッセージを選択し、[アクション] ボタンをクリックして、次のいずれかの選択を行います。</span><span class="sxs-lookup"><span data-stu-id="c6fe7-259">On the **Custom mailbox** tab, select a message in the list, click the **Action** button, and make one of the following selections:</span></span>

- <span data-ttu-id="c6fe7-260">**クリーンレポート**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-260">**Report clean**</span></span>
- <span data-ttu-id="c6fe7-261">**フィッシングの報告**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-261">**Report phishing**</span></span>
- <span data-ttu-id="c6fe7-262">**マルウェアの報告**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-262">**Report malware**</span></span>
- <span data-ttu-id="c6fe7-263">**スパムを報告する**</span><span class="sxs-lookup"><span data-stu-id="c6fe7-263">**Report spam**</span></span>

![[操作] ボタンのオプション](../../media/user-submission-custom-mailbox-action-button.png)