---
title: 組織内の電子メールメッセージの検索と削除
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 3526fd06-b45f-445b-aed4-5ebd37b3762a
description: セキュリティ/コンプライアンス センターの検索と消去機能を使って、組織のすべてのメールボックスからメール メッセージを検索し、削除できます。
ms.openlocfilehash: 52871fc85a4d5aec1754c1957f2087552b442daf
ms.sourcegitcommit: 355bd51ab6a79d5c36a4e4f57df74ae6873eba19
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "50423698"
---
# <a name="search-for-and-delete-email-messages"></a><span data-ttu-id="c34ef-103">メール メッセージを検索して削除する</span><span class="sxs-lookup"><span data-stu-id="c34ef-103">Search for and delete email messages</span></span>

<span data-ttu-id="c34ef-104">**この記事は管理者向けです。メールボックスで削除するアイテムを探している場合は、「[クイック検索を使ってメッセージまたはアイテムを検索する](https://support.office.com/article/69748862-5976-47b9-98e8-ed179f1b9e4d)**」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c34ef-104">**This article is for administrators. Are you trying to find items in your mailbox that you want to delete? See [Find a message or item with Instant Search](https://support.office.com/article/69748862-5976-47b9-98e8-ed179f1b9e4d)**.</span></span>

<span data-ttu-id="c34ef-105">コンテンツ検索機能を使用すると、組織のすべてのメールボックスからメール メッセージを検索し、削除することができます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-105">You can use the Content Search feature to search for and delete an email message from all mailboxes in your organization.</span></span> <span data-ttu-id="c34ef-106">この機能を使用して、次のように有害な、またはリスクが高い可能性があるメールを検索し、削除することができます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-106">This can help you find and remove potentially harmful or high-risk email, such as:</span></span>

- <span data-ttu-id="c34ef-107">危険性のある添付ファイルやウイルスを含むメッセージ</span><span class="sxs-lookup"><span data-stu-id="c34ef-107">Messages that contain dangerous attachments or viruses</span></span>

- <span data-ttu-id="c34ef-108">フィッシング メッセージ</span><span class="sxs-lookup"><span data-stu-id="c34ef-108">Phishing messages</span></span>

- <span data-ttu-id="c34ef-109">機密データを含むメッセージ</span><span class="sxs-lookup"><span data-stu-id="c34ef-109">Messages that contain sensitive data</span></span>

> [!CAUTION]
> <span data-ttu-id="c34ef-110">検索と消去は、必要なアクセス許可が割り当てられていれば、誰でも組織のメールボックスからメール メッセージを削除できる強力な機能です。</span><span class="sxs-lookup"><span data-stu-id="c34ef-110">Search and purge is a powerful feature that allows anyone that is assigned the necessary permissions to delete email messages from mailboxes in your organization.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="c34ef-111">始める前に</span><span class="sxs-lookup"><span data-stu-id="c34ef-111">Before you begin</span></span>

- <span data-ttu-id="c34ef-112">コンテンツ検索を作成して実行するには、**電子情報開示管理者** 役割グループのメンバーであるか、**コンプライアンス検索** の管理役割が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c34ef-112">To create and run a Content Search, you have to be a member of the **eDiscovery Manager** role group or be assigned the **Compliance Search** management role.</span></span> <span data-ttu-id="c34ef-113">メッセージを削除するには、**Organization Management** 役割グループのメンバーであるか、**検索と消去** の管理役割が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c34ef-113">To delete messages, you have to be a member of the **Organization Management** role group or be assigned the **Search And Purge** management role.</span></span> <span data-ttu-id="c34ef-114">ユーザーを役割グループに追加する方法の詳細については、「[セキュリティ/コンプライアンス センターの電子情報開示のアクセス許可を割り当てる](assign-ediscovery-permissions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c34ef-114">For information about adding users to a role group, see [Assign eDiscovery permissions in the Security & Compliance Center](assign-ediscovery-permissions.md).</span></span>

- <span data-ttu-id="c34ef-115">メッセージを削除するには、セキュリティ/コンプライアンス センターの PowerShell を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c34ef-115">You have to use Security & Compliance Center PowerShell to delete messages.</span></span> <span data-ttu-id="c34ef-116">接続方法については、「[手順 2](#step-2-connect-to-security--compliance-center-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c34ef-116">See [Step 2](#step-2-connect-to-security--compliance-center-powershell) for instructions about how to connect.</span></span>

- <span data-ttu-id="c34ef-117">メールボックスごとに最大 10 個のアイテムを一度に削除できます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-117">A maximum of 10 items per mailbox can be removed at one time.</span></span> <span data-ttu-id="c34ef-118">メッセージを検索し削除するための機能はインシデント対応ツールを意図したものなので、この制限により、メールボックスからすばやくかつ確実にメッセージを削除できます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-118">Because the capability to search for and remove messages is intended to be an incident-response tool, this limit helps ensure that messages are quickly removed from mailboxes.</span></span> <span data-ttu-id="c34ef-119">これは、ユーザーのメールボックスをクリーンアップするための機能ではありません。</span><span class="sxs-lookup"><span data-stu-id="c34ef-119">This feature isn't intended to clean up user mailboxes.</span></span>

- <span data-ttu-id="c34ef-120">コンテンツ検索で検索と削除アクションを実行してアイテムを削除するために使用できるメールボックスの最大数は 50,000 個です。</span><span class="sxs-lookup"><span data-stu-id="c34ef-120">The maximum number of mailboxes in a content search that you can use to delete items by doing a search and purge action is 50,000.</span></span> <span data-ttu-id="c34ef-121">検索 ([手順 1](#step-1-create-a-content-search-to-find-the-message-to-delete) で作成) で 50,000 個を超えるメールボックスを検索する場合、削除アクション (手順 3 で作成) は失敗します。</span><span class="sxs-lookup"><span data-stu-id="c34ef-121">If the search (that you create in [Step 1](#step-1-create-a-content-search-to-find-the-message-to-delete)) searches more than 50,000 mailboxes, the purge action (that you create in Step 3) will fail.</span></span> <span data-ttu-id="c34ef-122">1 回の検索で 50,000 個を超えるメールボックスを検索するのは、通常、組織内のすべてのメールボックスを検索に含めるように構成した場合です。</span><span class="sxs-lookup"><span data-stu-id="c34ef-122">Searching more than 50,000 mailbox in a single search might typically happen when you configure the search to include all mailboxes in your organization.</span></span> <span data-ttu-id="c34ef-123">この制限は、検索クエリに一致するアイテムが 50,000 個未満のメールボックスに含まれている場合でも適用されます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-123">This restriction still applies even when less than 50,000 mailboxes contain items that match the search query.</span></span> <span data-ttu-id="c34ef-124">検索のアクセス許可を使用して 50,000 個を超えるメールボックスからアイテムを検索および消去する方法については、「[詳細情報](#more-information)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c34ef-124">See the [More information](#more-information) section for guidance about using search permissions filters to search for and purge items from more than 50,000 mailboxes.</span></span>

- <span data-ttu-id="c34ef-125">この記事の手順は、Exchange Online のメールボックスとパブリック フォルダーにあるアイテムを削除する場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-125">The procedure in this article can only be used to delete items in Exchange Online mailboxes and public folders.</span></span> <span data-ttu-id="c34ef-126">SharePoint や OneDrive for Business のサイトからコンテンツを削除する場合には使用できません。</span><span class="sxs-lookup"><span data-stu-id="c34ef-126">You can't use it to delete content from SharePoint or OneDrive for Business sites.</span></span>

- <span data-ttu-id="c34ef-127">Advanced eDiscovery ケースのレビュー セット内のメール アイテムは、この記事の手順で削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="c34ef-127">Email items in a review set in an Advanced eDiscovery case can't be deleted by using the procedures in this article.</span></span> <span data-ttu-id="c34ef-128">これは、レビュー セット内のアイテムはライブ サービスではなく、Azure ストレージの場所に保存されるからです。</span><span class="sxs-lookup"><span data-stu-id="c34ef-128">That's because items in a review set are stored in an Azure Storage location, and not in the live service.</span></span> <span data-ttu-id="c34ef-129">これは、手順 1 で作成したコンテンツ検索では返されないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="c34ef-129">This means they won't be returned by the content search that you create in Step 1.</span></span> <span data-ttu-id="c34ef-130">レビュー セット内のアイテムを削除するには、レビュー セットが含まれている Advanced eDiscovery ケースを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c34ef-130">To delete items in a review set, you have to delete the Advanced eDiscovery case that contains the review set.</span></span> <span data-ttu-id="c34ef-131">詳細については、「[Close or delete an Advanced eDiscovery case (Advanced eDiscovery ケースを閉じるか、または削除する)](close-or-delete-case.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c34ef-131">For more information, see [Close or delete an Advanced eDiscovery case](close-or-delete-case.md).</span></span>

## <a name="step-1-create-a-content-search-to-find-the-message-to-delete"></a><span data-ttu-id="c34ef-132">手順 1: コンテンツ検索を作成して、削除するメッセージを探す</span><span class="sxs-lookup"><span data-stu-id="c34ef-132">Step 1: Create a Content Search to find the message to delete</span></span>

<span data-ttu-id="c34ef-133">最初の手順は、組織のメールボックスから削除するメッセージを見つけるコンテンツ検索を作成し、実行することです。</span><span class="sxs-lookup"><span data-stu-id="c34ef-133">The first step is to create and run a Content Search to find the message that you want to remove from mailboxes in your organization.</span></span> <span data-ttu-id="c34ef-134">セキュリティ/コンプライアンス センターを使用するか、**New-ComplianceSearch** コマンドレットと **Start-ComplianceSearch** コマンドレットを実行すると、検索を作成できます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-134">You can create the search by using the Security & Compliance Center or by running the **New-ComplianceSearch** and **Start-ComplianceSearch** cmdlets.</span></span> <span data-ttu-id="c34ef-135">[手順 3](#step-3-delete-the-message) で **New-ComplianceSearchAction -Purge** コマンドを実行すると、この検索のクエリに一致するメッセージは削除されます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-135">The messages that match the query for this search will be deleted by running the **New-ComplianceSearchAction -Purge** command in [Step 3](#step-3-delete-the-message).</span></span> <span data-ttu-id="c34ef-136">コンテンツ検索を作成し、検索クエリを構成する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c34ef-136">For information about creating a Content Search and configuring search queries, see the following topics:</span></span>

- [<span data-ttu-id="c34ef-137">Office 365 のコンテンツ検索</span><span class="sxs-lookup"><span data-stu-id="c34ef-137">Content Search in Office 365</span></span>](content-search.md)

- [<span data-ttu-id="c34ef-138">コンテンツ検索のキーワード クエリ</span><span class="sxs-lookup"><span data-stu-id="c34ef-138">Keyword queries for Content Search</span></span>](keyword-queries-and-search-conditions.md)

- [<span data-ttu-id="c34ef-139">New-ComplianceSearch</span><span class="sxs-lookup"><span data-stu-id="c34ef-139">New-ComplianceSearch</span></span>](https://docs.microsoft.com/powershell/module/exchange/New-ComplianceSearch)

- [<span data-ttu-id="c34ef-140">Start-ComplianceSearch</span><span class="sxs-lookup"><span data-stu-id="c34ef-140">Start-ComplianceSearch</span></span>](https://docs.microsoft.com/powershell/module/exchange/Start-ComplianceSearch)

> [!NOTE]
> <span data-ttu-id="c34ef-141">この手順で作成するコンテンツ検索で検索されるコンテンツの場所に、SharePoint や OneDrive for Business のサイトを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="c34ef-141">The content locations that are searched in the Content Search that you create in this step can't include SharePoint or OneDrive for Business sites.</span></span> <span data-ttu-id="c34ef-142">メール メッセージに使われるコンテンツ検索には、メールボックスとパブリック フォルダーのみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-142">You can include only mailboxes and public folders in a Content Search that will be used to email messages.</span></span> <span data-ttu-id="c34ef-143">コンテンツ検索にサイトが含まれる場合、**New-ComplianceSearchAction** コマンドレットを実行すると、手順 3 でエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="c34ef-143">If the Content Search includes sites, you'll receive an error in Step 3 when you run the **New-ComplianceSearchAction** cmdlet.</span></span>

### <a name="tips-for-finding-messages-to-remove"></a><span data-ttu-id="c34ef-144">削除するメッセージを見つけるためのヒント</span><span class="sxs-lookup"><span data-stu-id="c34ef-144">Tips for finding messages to remove</span></span>

<span data-ttu-id="c34ef-p110">検索クエリの目標は、削除するメッセージだけに検索結果を絞り込むことです。次にヒントを示します。</span><span class="sxs-lookup"><span data-stu-id="c34ef-p110">The goal of the search query is to narrow the results of the search to only the message or messages that you want to remove. Here are some tips:</span></span>

- <span data-ttu-id="c34ef-147">メッセージの件名に使われているテキストまたはフレーズを正確に記憶している場合は、検索クエリの **Subject** プロパティをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="c34ef-147">If you know the exact text or phrase used in the subject line of the message, use the **Subject** property in the search query.</span></span>

- <span data-ttu-id="c34ef-148">メッセージの正確な日付 (または期間) がわかる場合は、検索クエリに **Received** プロパティを含めます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-148">If you know that exact date (or date range) of the message, include the **Received** property in the search query.</span></span>

- <span data-ttu-id="c34ef-149">メッセージの送信者がわかる場合は、検索クエリに **From** プロパティを含めます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-149">If you know who sent the message, include the **From** property in the search query.</span></span>

- <span data-ttu-id="c34ef-150">検索結果をプレビューして、検索が、削除を希望するメッセージだけを返したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c34ef-150">Preview the search results to verify that the search returned only the message (or messages) that you want to delete.</span></span>

- <span data-ttu-id="c34ef-151">検索見積もりの統計情報 (セキュリティ/コンプライアンス センターの検索の詳細ウィンドウや、[Get-ComplianceSearch](https://go.microsoft.com/fwlink/p/?LinkId=517934) コマンドレットを使用して表示される情報) を使用して、結果の合計数のカウントを取得します。</span><span class="sxs-lookup"><span data-stu-id="c34ef-151">Use the search estimate statistics (displayed in the details pane of the search in the Security & Compliance Center or by using the [Get-ComplianceSearch](https://go.microsoft.com/fwlink/p/?LinkId=517934) cmdlet) to get a count of the total number of results.</span></span>

<span data-ttu-id="c34ef-152">不審な電子メール メッセージを検索するクエリの 2 つの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c34ef-152">Here are two examples of queries to find suspicious email messages.</span></span>

- <span data-ttu-id="c34ef-153">このクエリは、2016 年 4 月 13 日から 2016 年 4 月 14 日までの間にユーザーが受信し、単語 "action" と "required" が件名に含まれるメッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="c34ef-153">This query returns messages that were received by users between April 13, 2016 and April 14, 2016 and that contain the words "action" and "required" in the subject line.</span></span>

  ```powershell
  (Received:4/13/2016..4/14/2016) AND (Subject:'Action required')
  ```

- <span data-ttu-id="c34ef-154">このクエリは、chatsuwloginsset12345@outlook.com から送信され、完全に一致する語句 "Update your account information" (アカウント情報を更新してください) が件名に含まれているメッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="c34ef-154">This query returns messages that were sent by chatsuwloginsset12345@outlook.com and that contain the exact phrase "Update your account information" in the subject line.</span></span>

  ```powershell
  (From:chatsuwloginsset12345@outlook.com) AND (Subject:"Update your account information")
  ```

<span data-ttu-id="c34ef-155">次に示す例では、**New-ComplianceSearch** コマンドレットと **Start-ComplianceSearch** コマンドレットを実行することにより、クエリを使用して検索を作成して開始し、組織内のすべてのメールボックスを検索します。</span><span class="sxs-lookup"><span data-stu-id="c34ef-155">Here's an example of using a query to create and start a search by running the **New-ComplianceSearch** and **Start-ComplianceSearch** cmdlets to search all mailboxes in the organization:</span></span>

```powershell
$Search=New-ComplianceSearch -Name "Remove Phishing Message" -ExchangeLocation All -ContentMatchQuery '(Received:4/13/2016..4/14/2016) AND (Subject:"Action required")'
Start-ComplianceSearch -Identity $Search.Identity
```

## <a name="step-2-connect-to-security--compliance-center-powershell"></a><span data-ttu-id="c34ef-156">手順 2: セキュリティ/コンプライアンス センターの PowerShell に接続する</span><span class="sxs-lookup"><span data-stu-id="c34ef-156">Step 2: Connect to Security & Compliance Center PowerShell</span></span>

<span data-ttu-id="c34ef-157">次に、組織のセキュリティ/コンプライアンス センターの PowerShell に接続します。</span><span class="sxs-lookup"><span data-stu-id="c34ef-157">The next step is to connect to Security & Compliance Center PowerShell for your organization.</span></span> <span data-ttu-id="c34ef-158">詳細な手順については、「[セキュリティ/コンプライアンス センターの PowerShell への接続](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c34ef-158">For step-by-step instructions, see [Connect to Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell).</span></span>

<span data-ttu-id="c34ef-159">セキュリティ/コンプライアンス センターの PowerShell に接続したら、前の手順で準備した **New-ComplianceSearch** コマンドレットおよび **Start-ComplianceSearch** コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="c34ef-159">After you've connected to Security & Compliance Center PowerShell, run the **New-ComplianceSearch** and **Start-ComplianceSearch** cmdlets that you prepared in the previous step.</span></span>

## <a name="step-3-delete-the-message"></a><span data-ttu-id="c34ef-160">手順 3:メッセージを削除する</span><span class="sxs-lookup"><span data-stu-id="c34ef-160">Step 3: Delete the message</span></span>

<span data-ttu-id="c34ef-161">削除するメッセージを返すコンテンツ検索を作成して検索条件を絞り、セキュリティ/コンプライアンス センターの PowerShell に接続したら、最後に **New-ComplianceSearchAction** コマンドレットを実行して、メッセージを削除します。</span><span class="sxs-lookup"><span data-stu-id="c34ef-161">After you've created and refined a Content Search to return the message that you want to remove and are connected to Security & Compliance Center PowerShell, the final step is to run the **New-ComplianceSearchAction** cmdlet to delete the message.</span></span> <span data-ttu-id="c34ef-162">メッセージは、論理的に削除することも、物理的に削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-162">You can soft- or hard-delete the message.</span></span> <span data-ttu-id="c34ef-163">論理的に削除したアイテムは、ユーザーの [回復可能なアイテム] フォルダーに移動され、削除済みアイテムの保持期間が切れるまで保持されます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-163">A soft-deleted message is moved to a user's Recoverable Items folder and retained until the deleted item retention period expires.</span></span> <span data-ttu-id="c34ef-164">物理的に削除したメッセージは、メールボックスから完全に削除するようにマークされ、管理フォルダー用アシスタントによって次回そのメールボックスが処理される際に完全に削除されます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-164">Hard-deleted messages are marked for permanent removal from the mailbox and will be permanently removed the next time the mailbox is processed by the Managed Folder Assistant.</span></span> <span data-ttu-id="c34ef-165">そのメールボックスで単一アイテムの回復が有効になっている場合、物理的に削除したアイテムは、削除済みアイテムの保持期間が切れると完全に削除されます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-165">If single item recovery is enabled for the mailbox, hard-deleted items will be permanently removed after the deleted item retention period expires.</span></span> <span data-ttu-id="c34ef-166">メールボックスが保留中になっている場合は、削除したメッセージは、そのアイテムの保留期間が切れるか、その保留がメールボックスから削除されるまで保持されます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-166">If a mailbox is placed on hold, deleted messages are preserved until the hold duration for the item expires or until the hold is removed from the mailbox.</span></span>

<span data-ttu-id="c34ef-167">次の例では、"Remove Phishing Message"(フィッシング メッセージの削除) という名前のコンテンツ検索によって返された検索結果がコマンドによって論理的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-167">In the following example, the command soft-deletes the search results returned by a Content Search named "Remove Phishing Message".</span></span>

```powershell
New-ComplianceSearchAction -SearchName "Remove Phishing Message" -Purge -PurgeType SoftDelete
```

<span data-ttu-id="c34ef-168">Remove Phishing Message コンテンツ検索によって返されたアイテムを物理的に削除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c34ef-168">To hard-delete the items returned by the "Remove Phishing Message" content search, you would run this command:</span></span>

```powershell
New-ComplianceSearchAction -SearchName "Remove Phishing Message" -Purge -PurgeType HardDelete
```

<span data-ttu-id="c34ef-169">前のコマンドを実行してメッセージを論理的または物理的に削除する場合、*SearchName* パラメーターで指定される検索は、手順 1 で作成したコンテンツ検索になります。</span><span class="sxs-lookup"><span data-stu-id="c34ef-169">When you run the previous command to soft- or hard-delete messages, the search specified by the  *SearchName*  parameter is the Content Search that you created in Step 1.</span></span>

<span data-ttu-id="c34ef-170">詳細については、「[New-ComplianceSearchAction](https://docs.microsoft.com/powershell/module/exchange/New-ComplianceSearchAction)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c34ef-170">For more information, see [New-ComplianceSearchAction](https://docs.microsoft.com/powershell/module/exchange/New-ComplianceSearchAction).</span></span>

## <a name="more-information"></a><span data-ttu-id="c34ef-171">詳細情報</span><span class="sxs-lookup"><span data-stu-id="c34ef-171">More information</span></span>

- <span data-ttu-id="c34ef-172">**検索と削除の操作の状態を取得するにはどうすればよいですか?**</span><span class="sxs-lookup"><span data-stu-id="c34ef-172">**How do you get status on the search and remove operation?**</span></span>

  <span data-ttu-id="c34ef-173">**Get-ComplianceSearchAction** を実行すると、その削除操作の状態を取得できます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-173">Run the **Get-ComplianceSearchAction** to get the status on the delete operation.</span></span> <span data-ttu-id="c34ef-174">**New-ComplianceSearchAction** コマンドレットを実行したときに作成されるオブジェクトは、`<name of Content Search>_Purge` という形式で名前付けされます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-174">The object that is created when you run the **New-ComplianceSearchAction** cmdlet is named using this format:  `<name of Content Search>_Purge`.</span></span>

- <span data-ttu-id="c34ef-175">**メッセージを削除するとどうなりますか?**</span><span class="sxs-lookup"><span data-stu-id="c34ef-175">**What happens after you delete a message?**</span></span>

  <span data-ttu-id="c34ef-176">`New-ComplianceSearchAction -Purge -PurgeType HardDelete` コマンドを使用して削除されたメッセージは、Purges フォルダーに移動され、ユーザーはアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="c34ef-176">A message that's deleted with the  `New-ComplianceSearchAction -Purge -PurgeType HardDelete` command is moved to the Purges folder and can't be accessed by the user.</span></span> <span data-ttu-id="c34ef-177">Purges フォルダーに移動されたメッセージは、そのメールボックスで単一アイテムの回復が有効になっている場合、削除済みアイテムの保持期間が切れるまで保持されます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-177">After the message is moved to the Purges folder, the message is retained for the duration of the deleted item retention period if single item recovery is enabled for the mailbox.</span></span> <span data-ttu-id="c34ef-178">(Microsoft 365 では、新しいメールボックスを作成すると、既定で単一アイテムの回復が有効になります)。削除済みアイテムの保持期間を過ぎると、そのメッセージは完全に削除するようにマークされ、管理フォルダー用アシスタントによって次回そのメールボックスが処理される際に Microsoft 365 から消去されます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-178">(In Microsoft 365, single item recovery is enabled by default when a new mailbox is created.) After the deleted item retention period expires, the message is marked for permanent deletion and will be purged from Microsoft 365 the next time the mailbox is processed by the Managed Folder assistant.</span></span>

  <span data-ttu-id="c34ef-179">`New-ComplianceSearchAction -Purge -PurgeType SoftDelete` コマンドを使用すると、メッセージは、ユーザーの回復可能なアイテム フォルダーの Deletions フォルダーに移動されます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-179">If you use the `New-ComplianceSearchAction -Purge -PurgeType SoftDelete` command, messages are moved to the Deletions folder in the user's Recoverable Items folder.</span></span> <span data-ttu-id="c34ef-180">Microsoft 365 から直ちに削除されることはありません。</span><span class="sxs-lookup"><span data-stu-id="c34ef-180">It isn't immediately purged from Microsoft 365.</span></span> <span data-ttu-id="c34ef-181">ユーザーは、メールボックスに構成されている削除したアイテムの保持期間に基づき、その期間は削除済みアイテム フォルダーのメッセージを復元できます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-181">The user can recover messages in the Deleted Items folder for the duration based on the deleted item retention period configured for the mailbox.</span></span> <span data-ttu-id="c34ef-182">この保持期間を過ぎるか、過ぎる前にユーザーがメッセージを消去すると、メッセージは Purges フォルダーに移動され、ユーザーはアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="c34ef-182">After this retention period expires (or if user purges the message before it expires), the message is moved to the Purges folder and can no longer be accessed by the user.</span></span> <span data-ttu-id="c34ef-183">Purges フォルダーに移動されたメッセージは、そのメールボックスで単一アイテムの回復が有効になっている場合、メールボックスに構成されている削除済みアイテムの保持期間が切れるまで保持されます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-183">Once in the Purges folder, the message is retained for the duration based on the deleted item retention period configured for the mailbox if single items recovery is enabled for the mailbox.</span></span> <span data-ttu-id="c34ef-184">(Microsoft 365 では、新しいメールボックスを作成すると、既定で単一アイテムの回復が有効になります)。削除済みアイテムの保持期間を過ぎると、そのメッセージは完全に削除するようにマークされ、管理フォルダー用アシスタントによって次回そのメールボックスが処理される際に Microsoft 365 から消去されます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-184">(In Microsoft 365, single item recovery is enabled by default when a new mailbox is created.) After the deleted item retention period expires, the message is marked for permanent deletion and will be purged from Microsoft 365 the next time that the mailbox is processed by the Managed Folder assistant.</span></span>

- <span data-ttu-id="c34ef-185">**50,000 を超えるメールボックスからメッセージを削除するにはどうすればよいですか?**</span><span class="sxs-lookup"><span data-stu-id="c34ef-185">**What if you have to delete a message from more than 50,000 mailboxes?**</span></span>

  <span data-ttu-id="c34ef-186">前述のとおり、検索と削除の操作を実行できるメールボックスの上限は 50,000 です (検索クエリに一致するアイテムが 50,000 個未満の場合でも)。</span><span class="sxs-lookup"><span data-stu-id="c34ef-186">As previously stated, you can perform a search and purge operation on a maximum of 50,000 mailboxes (even if less than 50,000 contain items that match the search query).</span></span> <span data-ttu-id="c34ef-187">50,000 を超えるメールボックスに対して検索と削除の操作を実行する必要がある場合は、検索対象となるメールボックスの数を 50,000 未満に減らす一時的な検索権限フィルターを作成することをご検討ください。</span><span class="sxs-lookup"><span data-stu-id="c34ef-187">If you have to do a search and purge operation on more than 50,000 mailboxes, consider creating temporary search permissions filters that reduce the number of mailboxes that would be searched to less than 50,000 mailboxes.</span></span> <span data-ttu-id="c34ef-188">たとえば、異なる部署、都道府県、国のメールボックスが組織内にある場合、そのようなメールボックスのプロパティのいずれかを基にメールボックスの検索権限フィルターを作成して、組織のメールボックスのサブセットを検索できます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-188">For example, if your organization contains mailboxes in different departments, states, or countries, you can create a mailbox search permissions filter based on one of those mailbox properties to search a subset of mailboxes in your organization.</span></span> <span data-ttu-id="c34ef-189">検索権限フィルターを作成したら、検索を作成 (手順 1 を参照) し、メッセージを削除 (手順 3 を参照) します。</span><span class="sxs-lookup"><span data-stu-id="c34ef-189">After you create the search permissions filter, you would create the search (described in Step 1) and then delete the message (described in Step 3).</span></span> <span data-ttu-id="c34ef-190">その後、フィルターを編集し、別のメールボックスのセット内のメッセージを検索して削除できます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-190">Then you can edit the filter to search for and purge messages in a different set of mailboxes.</span></span> <span data-ttu-id="c34ef-191">検索権限フィルターの作成の詳細については、「[コンテンツ検索用にアクセス許可フィルターを設定する](permissions-filtering-for-content-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c34ef-191">For more information about creating search permissions filters, see [Configure permissions filtering for Content Search](permissions-filtering-for-content-search.md).</span></span>

- <span data-ttu-id="c34ef-192">**検索結果に含まれるインデックスのないアイテムも削除されますか?**</span><span class="sxs-lookup"><span data-stu-id="c34ef-192">**Will unindexed items included in the search results be deleted?**</span></span>

  <span data-ttu-id="c34ef-193">いいえ。\`New-ComplianceSearchAction -Purge コマンドでは、インデックスのないアイテムは削除されません。</span><span class="sxs-lookup"><span data-stu-id="c34ef-193">No, the  \`New-ComplianceSearchAction -Purge command doesn't delete unindexed items.</span></span>

- <span data-ttu-id="c34ef-194">**メッセージが、インプレース ホールドまたは訴訟ホールドが設定されたメールボックスから削除されたり、Microsoft 365 の保持ポリシーに割り当てられたりするとどうなりますか?**</span><span class="sxs-lookup"><span data-stu-id="c34ef-194">**What happens if a message is deleted from a mailbox that has been placed on In-Place Hold or Litigation Hold or is assigned to an Microsoft 365 retention policy?**</span></span>

  <span data-ttu-id="c34ef-195">消去されて Purges フォルダーに移動されたメッセージは、保持期間が切れるまで保持されます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-195">After the message is purged and moved to the Purges folder, the message is retained until the hold duration expires.</span></span> <span data-ttu-id="c34ef-196">保持期間が無期限である場合は、ホールドが解除されるか、または保持期間が変更されるまで、アイテムは保持されます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-196">If the hold duration is unlimited, then items are retained until the hold is removed or the hold duration is changed.</span></span>

- <span data-ttu-id="c34ef-197">**検索と削除のワークフローが、セキュリティ/コンプライアンス センターのさまざまな役割グループに分けられているのはなぜですか?**</span><span class="sxs-lookup"><span data-stu-id="c34ef-197">**Why is the search and remove workflow divided among different security and compliance center role groups?**</span></span>

  <span data-ttu-id="c34ef-198">前述したように、メールボックスを検索するには、電子情報開示管理者役割グループのメンバーであるか、コンプライアンス検索の管理の役割が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c34ef-198">As previously explained, a person has to be a member of the eDiscovery Manager role group or be assigned the Compliance Search management role to search mailboxes.</span></span> <span data-ttu-id="c34ef-199">メッセージを削除するには、組織管理役割グループのメンバーであるか、検索と消去の管理の役割が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c34ef-199">To delete messages, a person has to be a member of the Organization Management role group or be assigned the Search And Purge management role.</span></span> <span data-ttu-id="c34ef-200">この制限によって、組織のメールボックスを検索できるユーザーとメッセージを削除できるユーザーを制御できます。</span><span class="sxs-lookup"><span data-stu-id="c34ef-200">This makes it possible to control who can search mailboxes in the organization and who can delete messages.</span></span>
