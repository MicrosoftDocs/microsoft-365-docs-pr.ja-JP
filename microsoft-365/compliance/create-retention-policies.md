---
title: コンテンツを自動的に保持または削除するアイテム保持ポリシーを作成して構成する
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: アイテム保持ポリシーを使用して、ユーザーがメール、ドキュメント、および会話で生成するコンテンツを効率的に制御します。 必要なものを保持し、不要なものを取り除きます。
ms.openlocfilehash: 1faeae5dc145d6f908f9137387b875c890d22e14
ms.sourcegitcommit: 8e4c107e4da3a00be0511b05bc655a98fe871a54
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2021
ms.locfileid: "52280429"
---
# <a name="create-and-configure-retention-policies"></a><span data-ttu-id="b982d-104">アイテム保持ポリシーを作成して構成する</span><span class="sxs-lookup"><span data-stu-id="b982d-104">Create and configure retention policies</span></span>

><span data-ttu-id="b982d-105">*[セキュリティとコンプライアンスのための Microsoft 365 ライセンス ガイダンス](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)。*</span><span class="sxs-lookup"><span data-stu-id="b982d-105">*[Microsoft 365 licensing guidance for security & compliance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*</span></span>

<span data-ttu-id="b982d-106">アイテム保持ポリシーを使用して、コンテンツを保持するか、削除するか、あるいは保持した後に削除するかを事前に決定することにより、組織のデータを管理します。</span><span class="sxs-lookup"><span data-stu-id="b982d-106">Use a retention policy to manage the data for your organization by deciding proactively whether to retain content, delete content, or retain and then delete the content.</span></span>

<span data-ttu-id="b982d-107">アイテム保持ポリシーを使用すると、コンテナー レベルで同じ保持設定を割り当てて、そのコンテナー内のコンテンツに自動的に継承することで、この作業を非常に効率的に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b982d-107">A retention policy lets you do this very efficiently by assigning the same retention settings at the container level to be automatically inherited by content in that container.</span></span> <span data-ttu-id="b982d-108">たとえば、SharePoint サイトのすべてのアイテム、ユーザーの Exchange メールボックスのすべてのメール メッセージ、Microsoft Teams で使用するチームのすべてのチャネル メッセージなどが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="b982d-108">For example, all items in SharePoint sites, all email messages in users' Exchange mailboxes, all channel messages for teams that are used with Microsoft Teams.</span></span> <span data-ttu-id="b982d-109">アイテム保持ポリシーをコンテナー レベルで使用するべきか、保持ラベルをアイテム レベルで使用するべきかが分からない場合は、「[アイテム保持ポリシーと保持ラベル](retention.md#retention-policies-and-retention-labels)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b982d-109">If you're not sure whether to use a retention policy at the container level or a retention label at the item level, see [Retention policies and retention labels](retention.md#retention-policies-and-retention-labels).</span></span>

<span data-ttu-id="b982d-110">アイテム保持ポリシーと Microsoft 365 内のデータ保持の仕組みに関する詳細情報については、「[アイテム保持ポリシーおよび保持ラベルの詳細](retention.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b982d-110">For more information about retention policies and how retention works in Microsoft 365, see [Learn about retention policies and retention labels](retention.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b982d-111">このページの情報はコンプライアンス管理者向けです。</span><span class="sxs-lookup"><span data-stu-id="b982d-111">The information on this page is for compliance administrators.</span></span> <span data-ttu-id="b982d-112">お客様が管理者ではなく、使用するアプリに対してアイテム保持ポリシーがどのように構成されているのか理解したい場合は、ヘルプ デスク、IT 部門、または管理者にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="b982d-112">If you are not an administrator and want to understand how retention policies have been configured for the apps that you use, contact your help desk, IT department, or administrator.</span></span> <span data-ttu-id="b982d-113">Teams チャットとチャネル メッセージでアイテム保持ポリシーに関するメッセージが表示される場合は、「[アイテム保持ポリシーに関する Teams のメッセージ](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b)」から役立つ情報が得られる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b982d-113">If you're seeing messages about retention policies in Teams chats and channel messages, you might find it helpful to review [Teams messages about retention policies](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="b982d-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="b982d-114">Before you begin</span></span>

<span data-ttu-id="b982d-115">組織のグローバル管理者には、アイテム保持ポリシーを作成および編集できる完全な権限があります。</span><span class="sxs-lookup"><span data-stu-id="b982d-115">The global admin for your organization has full permissions to create and edit retention policies.</span></span> <span data-ttu-id="b982d-116">グローバル管理者としてサインインしていない場合は、「[アイテム保持ポリシーと保持ラベルを作成して管理するために必要なアクセス許可](get-started-with-retention.md#permissions-required-to-create-and-manage-retention-policies-and-retention-labels)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b982d-116">If you aren't signing in as a global admin, see [Permissions required to create and manage retention policies and retention labels](get-started-with-retention.md#permissions-required-to-create-and-manage-retention-policies-and-retention-labels).</span></span>

## <a name="create-and-configure-a-retention-policy"></a><span data-ttu-id="b982d-117">アイテム保持ポリシーを作成して構成する</span><span class="sxs-lookup"><span data-stu-id="b982d-117">Create and configure a retention policy</span></span>

<span data-ttu-id="b982d-118">アイテム保持ポリシーは、アイテム保持ポリシー内において"場所"として識別された複数のサービスをサポートすることができますが、サポートされているすべての場所を含む単一のアイテム保持ポリシーを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="b982d-118">Although a retention policy can support multiple services that are identified as "locations" in the retention policy, you can't create a single retention policy that includes all the supported locations:</span></span>

- <span data-ttu-id="b982d-119">Exchange メール</span><span class="sxs-lookup"><span data-stu-id="b982d-119">Exchange email</span></span>
- <span data-ttu-id="b982d-120">SharePoint サイト</span><span class="sxs-lookup"><span data-stu-id="b982d-120">SharePoint site</span></span>
- <span data-ttu-id="b982d-121">OneDrive アカウント</span><span class="sxs-lookup"><span data-stu-id="b982d-121">OneDrive accounts</span></span>
- <span data-ttu-id="b982d-122">Microsoft 365 グループ</span><span class="sxs-lookup"><span data-stu-id="b982d-122">Microsoft 365 groups</span></span>
- <span data-ttu-id="b982d-123">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="b982d-123">Skype for Business</span></span>
- <span data-ttu-id="b982d-124">Exchange パブリック フォルダー</span><span class="sxs-lookup"><span data-stu-id="b982d-124">Exchange public folders</span></span>
- <span data-ttu-id="b982d-125">チームのチャネル メッセージ</span><span class="sxs-lookup"><span data-stu-id="b982d-125">Teams channel messages</span></span>
- <span data-ttu-id="b982d-126">Teams のチャット</span><span class="sxs-lookup"><span data-stu-id="b982d-126">Teams chats</span></span>
- <span data-ttu-id="b982d-127">Yammer コミュニティのメッセージ</span><span class="sxs-lookup"><span data-stu-id="b982d-127">Yammer community messages</span></span>
- <span data-ttu-id="b982d-128">Yammer の個人用メッセージ</span><span class="sxs-lookup"><span data-stu-id="b982d-128">Yammer private messages</span></span>

<span data-ttu-id="b982d-129">アイテム保持ポリシーを作成するときに Teams か Yammer の場所を選択する場合、他の場所は自動的に除外されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-129">If you select the Teams or Yammer locations when you create a retention policy, the other locations are automatically excluded.</span></span> <span data-ttu-id="b982d-130">したがって、従うべき手順は、Teams か Yammer の場所を含める必要があるかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="b982d-130">This means that the instructions to follow depend on whether you need to include the Teams or Yammer locations:</span></span>

- [<span data-ttu-id="b982d-131">Teams の場所のアイテム保持ポリシーの説明</span><span class="sxs-lookup"><span data-stu-id="b982d-131">Instructions for a retention policy for Teams locations</span></span>](#retention-policy-for-teams-locations)
- [<span data-ttu-id="b982d-132">Yammer の場所のアイテム保持ポリシーの説明</span><span class="sxs-lookup"><span data-stu-id="b982d-132">Instructions for a retention policy for Yammer locations</span></span>](#retention-policy-for-yammer-locations)
- [<span data-ttu-id="b982d-133">Teams や Yammer 以外の場所のアイテム保持ポリシーの説明</span><span class="sxs-lookup"><span data-stu-id="b982d-133">Instructions for a retention policy for locations other than Teams and Yammer</span></span>](#retention-policy-for-locations-other-than-teams-and-yammer)

<span data-ttu-id="b982d-134">複数のアイテム保持ポリシーがあり、保持ラベルも使用する場合は、「[保持の原則、すなわち優先順位について](retention.md#the-principles-of-retention-or-what-takes-precedence)」を参照して、複数の保持設定が同じコンテンツに適用された場合の結果を理解してください。</span><span class="sxs-lookup"><span data-stu-id="b982d-134">When you have more than one retention policy, and when you also use retention labels, see [The principles of retention, or what takes precedence?](retention.md#the-principles-of-retention-or-what-takes-precedence) to understand the outcome when multiple retention settings apply to the same content.</span></span>

### <a name="retention-policy-for-teams-locations"></a><span data-ttu-id="b982d-135">Teams の場所のアイテム保持ポリシー</span><span class="sxs-lookup"><span data-stu-id="b982d-135">Retention policy for Teams locations</span></span>

1. <span data-ttu-id="b982d-136">[Microsoft 365 コンプライアンス センター](https://compliance.microsoft.com/)から、[**ポリシー**] > [**保持**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="b982d-136">From the [Microsoft 365 compliance center](https://compliance.microsoft.com/), select **Policies** > **Retention**.</span></span>

2. <span data-ttu-id="b982d-137">[**新しいアイテム保持ポリシー**] を選択してアイテム保持ポリシーの作成ウィザードを開始し、新しいアイテム保持ポリシーに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="b982d-137">Select **New retention policy** to start the Create retention policy wizard, and name your new retention policy.</span></span>

3. <span data-ttu-id="b982d-138">[**ポリシーを適用する場所の選択**] ページで、Teams の場所の 1 つまたは両方を選択します: [**Teams チャネル メッセージ**] と [**Teams チャット**]。</span><span class="sxs-lookup"><span data-stu-id="b982d-138">For the **Choose locations to apply the policy** page, select one or both of the locations for Teams: **Teams channel message** and **Teams chats**.</span></span>

   <span data-ttu-id="b982d-139">**Teams のチャネル メッセージ** の場合、標準チャネルからのメッセージが含まれますが、[プライベート チャネル](/microsoftteams/private-channels)は含まれません。</span><span class="sxs-lookup"><span data-stu-id="b982d-139">For **Teams channel messages**, message from standard channels but not [private channels](/microsoftteams/private-channels) are included.</span></span> <span data-ttu-id="b982d-140">現在、プライベートチャネルはアイテム保持ポリシーでサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b982d-140">Currently, private channels aren't supported by retention policies.</span></span>

   <span data-ttu-id="b982d-141">既定では、[すべてのチームとすべてのユーザーが選択されています](#a-policy-that-applies-to-entire-locations)が、[**[選択]** と **[除外]** オプション](#a-policy-with-specific-inclusions-or-exclusions)を選択することでこれを調整できます。</span><span class="sxs-lookup"><span data-stu-id="b982d-141">By default, [all teams and all users are selected](#a-policy-that-applies-to-entire-locations), but you can refine this by selecting the [**Choose** and **Exclude** options](#a-policy-with-specific-inclusions-or-exclusions).</span></span> <span data-ttu-id="b982d-142">ただし、この既定の選択を変更する前に、アイテム保持ポリシーが次を対象または除外対象とするために構成されるときに、メッセージを削除する点について注意してください。</span><span class="sxs-lookup"><span data-stu-id="b982d-142">However, before you change the default, be aware of the following consequences for a retention policy that deletes messages when it's configured for includes or excludes:</span></span>
    
    - <span data-ttu-id="b982d-143">グループ チャットでは、メッセージのコピーがチャットに含まれる各ユーザーのメールボックスに保存されるため、引き続きポリシーが割り当てられていないユーザーからの電子情報開示の結果で返されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-143">For group chats, because a copy of messages are saved in each user's mailbox who are included in the chat, copies of messages will continue to be returned in eDiscovery results from users who weren't assigned the policy.</span></span>
    - <span data-ttu-id="b982d-144">ポリシーが割り当てられていないユーザーには、削除されたメッセージが Teams の検索結果で返されますが、ユーザーに割り当てられたポリシーからの完全な削除の結果としてメッセージの内容は表示されません。</span><span class="sxs-lookup"><span data-stu-id="b982d-144">For users who weren't assigned the policy, deleted messages will be returned in their Teams search results but won't display the contents of the message as a result of the permanent deletion from the policy assigned to users.</span></span>

4. <span data-ttu-id="b982d-145">ウィザードの [**コンテンツを保持するか、削除するか、またはその両方を行うかを決定する**] ページで、コンテンツを保持および削除するための構成オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="b982d-145">For **Decide if you want to retain content, delete it, or both** page of the wizard, specify the configuration options for retaining and deleting content.</span></span>

   <span data-ttu-id="b982d-146">削除せずにコンテンツを保持するだけのアイテム保持ポリシーを作成し、指定した期間が経過した後に保持してから削除するか、指定した期間が経過した後にコンテンツを削除するだけです。</span><span class="sxs-lookup"><span data-stu-id="b982d-146">You can create a retention policy that just retains content without deleting, retains and then deletes after a specified period of time, or just deletes content after a specified period of time.</span></span> <span data-ttu-id="b982d-147">詳細については、このページの「[コンテンツを保持および削除するための設定](#settings-for-retaining-and-deleting-content)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b982d-147">For more information, see [Settings for retaining and deleting content](#settings-for-retaining-and-deleting-content) on this page.</span></span>

5. <span data-ttu-id="b982d-148">ウィザードを完了して、設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="b982d-148">Complete the wizard to save your settings.</span></span>

<span data-ttu-id="b982d-149">Teams のアイテム保持ポリシーを使用するタイミングと、エンド ユーザー エクスペリエンスを理解するためのガイダンスについては、Teams のドキュメントから「[Microsoft Teams のアイテム保持ポリシーを管理する](/microsoftteams/retention-policies)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b982d-149">For guidance when to use retention policies for Teams and understand the end user experience, see [Manage retention policies for Microsoft Teams](/microsoftteams/retention-policies) from the Teams documentation.</span></span>

<span data-ttu-id="b982d-150">アイテム保持ポリシーに対してサポートされているメッセージの要素や、タイミング情報の例を説明した手引きを含む、アイテム保持ポリシーの Teams に対する機能の技術的な詳細については、「[Microsoft Teams の保持に関する情報](retention-policies-teams.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b982d-150">For technical details about how retention works for Teams, including what elements of messages are supported for retention and timing information with example walkthroughs, see [Learn about retention for Microsoft Teams](retention-policies-teams.md).</span></span>

#### <a name="known-configuration-issues"></a><span data-ttu-id="b982d-151">既知の構成の問題</span><span class="sxs-lookup"><span data-stu-id="b982d-151">Known configuration issues</span></span>

- <span data-ttu-id="b982d-152">アイテムが最後に変更されたときに保持期間を開始するオプションを選択できますが、**アイテムが作成されたとき** の値が常に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-152">Although you can select the option to start the retention period when items were last modified, the value of **When items were created** is always used.</span></span> <span data-ttu-id="b982d-153">編集されたメッセージの場合、元のメッセージのコピーが元のタイムスタンプとともに保存され、この事前編集されたメッセージがいつ作成されたかを識別し、後編集されたメッセージのタイムスタンプが新しくなります。</span><span class="sxs-lookup"><span data-stu-id="b982d-153">For messages that are edited, a copy of the original message is saved with its original timestamp to identify when this pre-edited message was created, and the post-edited message has a newer timestamp.</span></span>

- <span data-ttu-id="b982d-154">**[Teams のチャネル メッセージ]** の場所にある **[チームの選択]** を選択した場合、チームではない Microsoft 365 グループが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="b982d-154">When you select **Choose teams** for the **Teams channel messages** location, you might see Microsoft 365 groups that aren't also teams.</span></span> <span data-ttu-id="b982d-155">これらのグループは選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="b982d-155">Don't select these groups.</span></span>

- <span data-ttu-id="b982d-156">**[Teams のチャット] の場所にある [ユーザーの選択]** を選択した場合、ゲストや、メールボックスのユーザーではないユーザーが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="b982d-156">When you select **Choose users for the Teams chats** location, you might see guests and non-mailbox users.</span></span> <span data-ttu-id="b982d-157">アイテム保持ポリシーはこれらのユーザー向けに設計されていないため、選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="b982d-157">Retention policies aren't designed for these users, so don't select them.</span></span>


#### <a name="additional-retention-policy-needed-to-support-teams"></a><span data-ttu-id="b982d-158">Teams をサポートするのに必要な追加のアイテム保持ポリシー</span><span class="sxs-lookup"><span data-stu-id="b982d-158">Additional retention policy needed to support Teams</span></span>

<span data-ttu-id="b982d-159">Teams は、単なるチャットやチャネルメッセージを送るだけのツールではありません。</span><span class="sxs-lookup"><span data-stu-id="b982d-159">Teams is more than just chats and channel messages.</span></span> <span data-ttu-id="b982d-160">Microsoft 365 グループ (以前の Office 365 グループ) から作成されたチームがある場合は、**Microsoft 365 グループ** の場所を使用して、その Microsoft 365 グループを含むアイテム保持ポリシーを追加で構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b982d-160">If you have teams that were created from a Microsoft 365 group (formerly Office 365 group), you should additionally configure a retention policy that includes that Microsoft 365 group by using the **Microsoft 365 Groups** location.</span></span> <span data-ttu-id="b982d-161">このアイテム保持ポリシーは、グループのメールボックス、サイト、およびドキュメントのコンテンツに適用されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-161">This retention policy applies to content in the group's mailbox, site, and files.</span></span>

<span data-ttu-id="b982d-162">チーム サイトが Microsoft 365 グループに接続されていない場合に、Teams 内のファイルを保持および削除するためには、**SharePoint サイト** または **OneDrive アカウント** の場所を含むアイテム保持ポリシーが必要です。</span><span class="sxs-lookup"><span data-stu-id="b982d-162">If you have team sites that aren't connected to a Microsoft 365 group, you need a retention policy that includes the **SharePoint sites** or **OneDrive accounts** locations to retain and delete files in Teams:</span></span>

- <span data-ttu-id="b982d-163">チャット内で共有されるファイルは、ファイルを共有したユーザーの OneDrive アカウントに保存されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-163">Files that are shared in chat are stored in the OneDrive account of the user who shared the file.</span></span>

- <span data-ttu-id="b982d-164">チャネルにアップロードされたファイルは、チームの SharePoint 内に保存されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-164">Files that are uploaded to channels are stored in the SharePoint site for the team.</span></span>

> [!TIP]
> <span data-ttu-id="b982d-165">チームの SharePoint サイトおよびチーム内のユーザーの OneDrive アカウントを選択すると、Microsoft 365 グループに接続されていない特定のチームのみのファイルにアイテム保持ポリシーを適用出来ます。</span><span class="sxs-lookup"><span data-stu-id="b982d-165">You can apply a retention policy to the files of just a specific team when it's not connected to a Microsoft 365 group by selecting the SharePoint site for the team, and the OneDrive accounts of users in the Team.</span></span>

<span data-ttu-id="b982d-166">Microsoft 365 グループ、SharePoint サイトや OneDrive アカウントに適用されているアイテム保持ポリシーにより、Teams のチャットやチャネル メッセージで参照されているファイルが、それらのメッセージが削除されるよりも先に削除される場合があります。</span><span class="sxs-lookup"><span data-stu-id="b982d-166">It's possible that a retention policy that's applied to Microsoft 365 groups, SharePoint sites, or OneDrive accounts could delete a file that's referenced in a Teams chat or channel message before those messages get deleted.</span></span> <span data-ttu-id="b982d-167">このような場合、そのファイルは Teams のメッセージに引き続き表示されますが、ユーザーがファイルをクリックすると、"ファイルが見つかりません" というエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-167">In this scenario, the file still displays in the Teams message, but when users select the file, they get a "File not found" error.</span></span> <span data-ttu-id="b982d-168">この動作はアイテム保持ポリシーに固有のものではなく、ユーザーが SharePoint または OneDrive から手動でファイルを削除した場合にも発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b982d-168">This behavior isn't specific to retention policies and could also happen if a user manually deletes a file from SharePoint or OneDrive.</span></span>

### <a name="retention-policy-for-yammer-locations"></a><span data-ttu-id="b982d-169">Yammer の場所のアイテム保持ポリシー</span><span class="sxs-lookup"><span data-stu-id="b982d-169">Retention policy for Yammer locations</span></span>

> [!NOTE]
> <span data-ttu-id="b982d-170">Yammer の保持ポリシーがプレビューで展開されています。</span><span class="sxs-lookup"><span data-stu-id="b982d-170">Retention policies for Yammer are rolling out in preview.</span></span> <span data-ttu-id="b982d-171">まだ Yammer の新しい場所が表示されていない場合は、数週間後にもう一度お試しください。</span><span class="sxs-lookup"><span data-stu-id="b982d-171">If you don't yet see the new locations for Yammer, try again in a few weeks.</span></span>
>
> <span data-ttu-id="b982d-172">この機能を使用するには、ご利用の Yammer ネットワークがハイブリッド モードではなく、[ネイティブ モード](/yammer/configure-your-yammer-network/overview-native-mode)になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b982d-172">To use this feature, your Yammer network must be [Native Mode](/yammer/configure-your-yammer-network/overview-native-mode), not Hybrid Mode.</span></span>

1. <span data-ttu-id="b982d-173">[Microsoft 365 コンプライアンス センター](https://compliance.microsoft.com/)から、[**ポリシー**] > [**保持**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="b982d-173">From the [Microsoft 365 compliance center](https://compliance.microsoft.com/), select **Policies** > **Retention**.</span></span>

2. <span data-ttu-id="b982d-174">新しいアイテム保持ポリシーを作成するには、[**新しいアイテム保持ポリシー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b982d-174">Select **New retention policy** to create a new retention policy.</span></span>

3. <span data-ttu-id="b982d-175">ウィザードの [**コンテンツを保持するか、削除するか、またはその両方を行うかを決定する**] ページで、コンテンツを保持および削除するための構成オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="b982d-175">For **Decide if you want to retain content, delete it, or both** page of the wizard, specify the configuration options for retaining and deleting content.</span></span> 
    
    <span data-ttu-id="b982d-176">削除せずにコンテンツを保持するだけのアイテム保持ポリシーを作成し、指定した期間が経過した後に保持してから削除するか、指定した期間が経過した後にコンテンツを削除するだけです。</span><span class="sxs-lookup"><span data-stu-id="b982d-176">You can create a retention policy that just retains content without deleting, retains and then deletes after a specified period of time, or just deletes content after a specified period of time.</span></span> <span data-ttu-id="b982d-177">詳細については、このページの「[コンテンツを保持および削除するための設定](#settings-for-retaining-and-deleting-content)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b982d-177">For more information, see [Settings for retaining and deleting content](#settings-for-retaining-and-deleting-content) on this page.</span></span>
    
    <span data-ttu-id="b982d-178">このオプションは Teams の場所ではサポートされていないため、[**保存期間の詳細設定を使用する**] を選択しないでください。</span><span class="sxs-lookup"><span data-stu-id="b982d-178">Do not select **Use advanced retention settings** because this option isn't supported for Yammer locations.</span></span> 

4. <span data-ttu-id="b982d-179">[**場所の選択**] ページで、[**特定の場所を選択**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b982d-179">For the **Choose locations** page, select **Let me choose specific locations**.</span></span> <span data-ttu-id="b982d-180">その後、Yammer の場所の 1 つまたは両方をオンに切り替えます: **Yammer コミュニティのメッセージ** と **Yammer の個人用メッセージ**。</span><span class="sxs-lookup"><span data-stu-id="b982d-180">Then toggle on one or both of the locations for Yammer: **Yammer community message** and **Yammer private messages**.</span></span>
    
    <span data-ttu-id="b982d-181">既定ではすべてのコミュニティとユーザーが選択されていますが、コミュニティやユーザーを含めるか、または除外するかを指定することで、これを絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="b982d-181">By default, all communities and users are selected, but you can refine this by specifying communities and users to be included or excluded.</span></span>
    
    <span data-ttu-id="b982d-182">Yammer の個人用メッセージの場合:</span><span class="sxs-lookup"><span data-stu-id="b982d-182">For Yammer private messages:</span></span> 
    - <span data-ttu-id="b982d-183">規定値を **すべて** のままにしておくと、Azure B2B のゲスト ユーザーは含まれません。</span><span class="sxs-lookup"><span data-stu-id="b982d-183">If you leave the default at **All**, Azure B2B guest users are not included.</span></span> 
    - <span data-ttu-id="b982d-184">[**ユーザーの選択**] を選択した場合、外部ユーザーのアカウントがわかっている場合は、外部ユーザーに保持ポリシーを適用できます。</span><span class="sxs-lookup"><span data-stu-id="b982d-184">If you select **Choose user**, you can apply a retention policy to external users if you know their account.</span></span>

5. <span data-ttu-id="b982d-185">ウィザードを完了して、設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="b982d-185">Complete the wizard to save your settings.</span></span>

<span data-ttu-id="b982d-186">Yammer 向けに機能する保持ポリシーの仕組みに関する詳細情報については、「[Yammer の保持の詳細](retention-policies-yammer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b982d-186">For more information about how retention policies work for Yammer, see [Learn about retention for Yammer](retention-policies-yammer.md).</span></span>

#### <a name="additional-retention-policies-needed-to-support-yammer"></a><span data-ttu-id="b982d-187">Yammer をサポートするのに必要な追加のアイテム保持ポリシー</span><span class="sxs-lookup"><span data-stu-id="b982d-187">Additional retention policies needed to support Yammer</span></span>

<span data-ttu-id="b982d-188">Yammer に備わっているのは、コミュニティのメッセージや個人用メッセージだけではありません。</span><span class="sxs-lookup"><span data-stu-id="b982d-188">Yammer is more than just community messages and private messages.</span></span> <span data-ttu-id="b982d-189">Yammer ネットワークのメール メッセージを保持したり削除したりするには、**Microsoft 365 グループ** の場所を使用して、Yammer で使用されている任意の Microsoft 365 グループを含む追加の保持ポリシーを構成します。</span><span class="sxs-lookup"><span data-stu-id="b982d-189">To retain and delete email messages for your Yammer network, configure an additional retention policy that includes any Microsoft 365 groups that are used for Yammer, by using the **Microsoft 365 Groups** location.</span></span> 

<span data-ttu-id="b982d-190">Yammer に保存されているファイルを保持したり削除したりするためには、**SharePoint サイト** や **OneDrive アカウント** の場所を含むアイテム保持ポリシーが必要です。</span><span class="sxs-lookup"><span data-stu-id="b982d-190">To retain and delete files that are stored in Yammer, you need a retention policy that includes the **SharePoint sites** or **OneDrive accounts** locations:</span></span>

- <span data-ttu-id="b982d-191">個人用メッセージ内で共有されるファイルは、ファイルを共有したユーザーの OneDrive アカウントに保存されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-191">Files that are shared in private messages are stored in the OneDrive account of the user who shared the file.</span></span> 

- <span data-ttu-id="b982d-192">コミュニティにアップロードされたファイルは、Yammer コミュニティの SharePoint 内に保存されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-192">Files that are uploaded to communities are stored in the SharePoint site for the Yammer community.</span></span>

<span data-ttu-id="b982d-193">SharePoint サイトや OneDrive アカウントに適用されているアイテム保持ポリシーにより、Yammer メッセージで参照されているファイルが、それらのメッセージが削除されるよりも先に削除される場合があります。</span><span class="sxs-lookup"><span data-stu-id="b982d-193">It's possible that a retention policy that's applied to SharePoint sites or OneDrive accounts could delete a file that's referenced in a Yammer message before those messages get deleted.</span></span> <span data-ttu-id="b982d-194">このような場合、そのファイルは Yammer のメッセージに引き続き表示されますが、ユーザーがファイルをクリックすると、"ファイルが見つかりません" というエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-194">In this scenario, the file still displays in the Yammer message, but when users select the file, they get a "File not found" error.</span></span> <span data-ttu-id="b982d-195">この動作はアイテム保持ポリシーに固有のものではなく、ユーザーが SharePoint または OneDrive から手動でファイルを削除した場合にも発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b982d-195">This behavior isn't specific to retention policies and could also happen if a user manually deletes a file from SharePoint or OneDrive.</span></span>

### <a name="retention-policy-for-locations-other-than-teams-and-yammer"></a><span data-ttu-id="b982d-196">Teams や Yammer 以外の場所のアイテム保持ポリシー</span><span class="sxs-lookup"><span data-stu-id="b982d-196">Retention policy for locations other than Teams and Yammer</span></span>

<span data-ttu-id="b982d-197">これらのサービスのいずれかに適用されるアイテム保持ポリシーについては、次の手順をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="b982d-197">Use the following instructions for retention policies that apply to any of these services:</span></span>

- <span data-ttu-id="b982d-198">Exchange: メールとパブリック フォルダー</span><span class="sxs-lookup"><span data-stu-id="b982d-198">Exchange: Email and public folders</span></span>
- <span data-ttu-id="b982d-199">SharePoint: サイト</span><span class="sxs-lookup"><span data-stu-id="b982d-199">SharePoint: Sites</span></span>
- <span data-ttu-id="b982d-200">OneDrive: アカウント</span><span class="sxs-lookup"><span data-stu-id="b982d-200">OneDrive: Accounts</span></span>
- <span data-ttu-id="b982d-201">Microsoft 365 グループ</span><span class="sxs-lookup"><span data-stu-id="b982d-201">Microsoft 365 groups</span></span>
- <span data-ttu-id="b982d-202">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="b982d-202">Skype for Business</span></span>

1. <span data-ttu-id="b982d-203">[Microsoft 365 コンプライアンス センター](https://compliance.microsoft.com/)から、[**ポリシー**] > [**保持**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="b982d-203">From the [Microsoft 365 compliance center](https://compliance.microsoft.com/), select **Policies** > **Retention**.</span></span>

2. <span data-ttu-id="b982d-204">[**新しいアイテム保持ポリシー**] を選択してアイテム保持ポリシーの作成ウィザードを開始し、新しいアイテム保持ポリシーに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="b982d-204">Select **New retention policy** to start the Create retention policy wizard, and name your new retention policy.</span></span>

3. <span data-ttu-id="b982d-205">**[場所の選択]** ページで、Teams の場所以外の場所のオンとオフを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b982d-205">For the **Choose locations** page, toggle on or off any of the locations except the locations for Teams.</span></span> <span data-ttu-id="b982d-206">場所ごとに、既定のままにして、[ポリシーを場所全体に適用する](#a-policy-that-applies-to-entire-locations)か、[包含と除外を指定](#a-policy-with-specific-inclusions-or-exclusions)することができます。</span><span class="sxs-lookup"><span data-stu-id="b982d-206">For each location, you can leave it at the default to [apply the policy to the entire location](#a-policy-that-applies-to-entire-locations), or [specify includes and excludes](#a-policy-with-specific-inclusions-or-exclusions).</span></span>

    <span data-ttu-id="b982d-207">場所固有の情報:</span><span class="sxs-lookup"><span data-stu-id="b982d-207">Information specific to locations:</span></span>
    - [<span data-ttu-id="b982d-208">Exchange メールと Exchange パブリック フォルダー</span><span class="sxs-lookup"><span data-stu-id="b982d-208">Exchange email and Exchange public folders</span></span>](#configuration-information-for-exchange-email-and-exchange-public-folders)
    - [<span data-ttu-id="b982d-209">SharePoint サイトと OneDrive アカウント</span><span class="sxs-lookup"><span data-stu-id="b982d-209">SharePoint sites and OneDrive accounts</span></span>](#configuration-information-for-sharepoint-sites-and-onedrive-accounts)
    - [<span data-ttu-id="b982d-210">Microsoft 365 グループ</span><span class="sxs-lookup"><span data-stu-id="b982d-210">Microsoft 365 Groups</span></span>](#configuration-information-for-microsoft-365-groups)
    - [<span data-ttu-id="b982d-211">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="b982d-211">Skype for Business</span></span>](#configuration-information-for-skype-for-business)

4. <span data-ttu-id="b982d-212">ウィザードの [**コンテンツを保持するか、削除するか、またはその両方を行うかを決定する**] ページで、コンテンツを保持および削除するための構成オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="b982d-212">For **Decide if you want to retain content, delete it, or both** page of the wizard, specify the configuration options for retaining and deleting content.</span></span>

    <span data-ttu-id="b982d-213">削除せずにコンテンツを保持するだけのアイテム保持ポリシーを作成し、指定した期間が経過した後に保持してから削除するか、指定した期間が経過した後にコンテンツを削除するだけです。</span><span class="sxs-lookup"><span data-stu-id="b982d-213">You can create a retention policy that just retains content without deleting, retains and then deletes after a specified period of time, or just deletes content after a specified period of time.</span></span> <span data-ttu-id="b982d-214">詳細については、このページの「[コンテンツを保持および削除するための設定](#settings-for-retaining-and-deleting-content)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b982d-214">For more information, see [Settings for retaining and deleting content](#settings-for-retaining-and-deleting-content) on this page.</span></span>

5. <span data-ttu-id="b982d-215">ウィザードを完了して、設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="b982d-215">Complete the wizard to save your settings.</span></span>

#### <a name="configuration-information-for-exchange-email-and-exchange-public-folders"></a><span data-ttu-id="b982d-216">Exchange メールと Exchange パブリック フォルダーの構成情報</span><span class="sxs-lookup"><span data-stu-id="b982d-216">Configuration information for Exchange email and Exchange public folders</span></span>

<span data-ttu-id="b982d-217">**Exchange メール** の場所は、メールボックスのレベルで保持設定を適用することにより、ユーザーのメール、予定表、およびその他のメールボックス アイテムの保持をサポートします。</span><span class="sxs-lookup"><span data-stu-id="b982d-217">The **Exchange email** location supports retention for users' email, calendar, and other mailbox items, by applying retention settings at the level of a mailbox.</span></span>

<span data-ttu-id="b982d-218">Exchange の保持設定を構成するときに含めるアイテムと除外するアイテムの詳細については、「[保持と削除に含めるもの](retention-policies-exchange.md#whats-included-for-retention-and-deletion)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b982d-218">For detailed information about which items are included and excluded when you configure retention settings for Exchange, see [What's included for retention and deletion](retention-policies-exchange.md#whats-included-for-retention-and-deletion)</span></span>

<span data-ttu-id="b982d-219">Microsoft 365 グループには Exchange メールボックスがありますが、**Exchange メール** の場所全体が含まれるアイテム保持ポリシーには、Microsoft 365 グループのメールボックスのコンテンツは含まれないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b982d-219">Note that even though a Microsoft 365 group has an Exchange mailbox, a retention policy that includes the entire **Exchange email** location won't include content in Microsoft 365 group mailboxes.</span></span> <span data-ttu-id="b982d-220">これらのメールボックスのコンテンツを保持するには、**Microsoft 365 グループ** の場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="b982d-220">To retain content in these mailboxes, select the **Microsoft 365 Groups** location.</span></span>

<span data-ttu-id="b982d-221">**Exchange パブリック フォルダー** の場所は保持設定をすべてのパブリック フォルダーに適用し、フォルダーまたはメールボックス レベルでは適用できません。</span><span class="sxs-lookup"><span data-stu-id="b982d-221">The **Exchange public folders** location applies retention settings to all public folders and can't be applied at the folder or mailbox level.</span></span>

#### <a name="configuration-information-for-sharepoint-sites-and-onedrive-accounts"></a><span data-ttu-id="b982d-222">SharePoint サイトと OneDrive アカウントの構成情報</span><span class="sxs-lookup"><span data-stu-id="b982d-222">Configuration information for SharePoint sites and OneDrive accounts</span></span>

<span data-ttu-id="b982d-223">[**SharePoint サイト**] の場所を選択すると、アイテム保持ポリシーでは、SharePoint​​ コミュニケーション サイト、Microsoft 365 グループによって接続されていないチーム サイト、クラシック サイトのドキュメントを保持および削除することができます。</span><span class="sxs-lookup"><span data-stu-id="b982d-223">When you choose the **SharePoint sites** location, the retention policy can retain and delete documents in SharePoint communication sites, team sites that aren't connected by Microsoft 365 groups, and classic sites.</span></span> <span data-ttu-id="b982d-224">Microsoft 365 グループによって接続されているチーム サイトは、このオプションでサポートされていないため、代わりにグループのメールボックス、サイト、ファイル内のコンテンツに適用されている [**Microsoft 365 グループ**] の場所を使用します。</span><span class="sxs-lookup"><span data-stu-id="b982d-224">Team sites connected by Microsoft 365 groups aren't supported with this option and instead, use the **Microsoft 365 Groups** location that applies to content in the group's mailbox, site, and files.</span></span>

<span data-ttu-id="b982d-225">アイテム保持ポリシーはサイト レベルで適用されますが、保持設定が適用されるのはドキュメントのみです。</span><span class="sxs-lookup"><span data-stu-id="b982d-225">Although the retention policy is applied at the site level, only documents have retention settings applied to them.</span></span> <span data-ttu-id="b982d-226">SharePoint と OneDrive の保持設定を構成するときに含めるものと除外するものの詳細については、「[保持と削除に含めるもの](retention-policies-sharepoint.md#whats-included-for-retention-and-deletion)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b982d-226">For detailed information about what's included and excluded when you configure retention settings for SharePoint and OneDrive, see [What's included for retention and deletion](retention-policies-sharepoint.md#whats-included-for-retention-and-deletion).</span></span> 

<span data-ttu-id="b982d-227">SharePoint サイトまたは OneDrive アカウントの場所を指定する場合、サイトにアクセスするためのアクセス許可は必要ありません。また、**[場所の編集]** ページで URL を指定するときに、検証は行われません。</span><span class="sxs-lookup"><span data-stu-id="b982d-227">When you specify your locations for SharePoint sites or OneDrive accounts, you don't need permissions to access the sites and no validation is done at the time you specify the URL on the **Edit locations** page.</span></span> <span data-ttu-id="b982d-228">ただし、指定した SharePoint サイトは、ウィザードの最後に存在していることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-228">However, the SharePoint sites that you specify are checked that they exist at the end of the wizard.</span></span> <span data-ttu-id="b982d-229">この確認が失敗した場合は、入力した URL の検証が失敗したことを示すメッセージが表示され、検証が成功するまで、ウィザードはアイテム保持ポリシーを作成しません。</span><span class="sxs-lookup"><span data-stu-id="b982d-229">If this check fails, you see a message that validation failed for the URL you entered, and the wizard won't create the retention policy until the validation check passes.</span></span> <span data-ttu-id="b982d-230">このメッセージが表示されたら、ウィザードに戻って URL を変更するか、アイテム保持ポリシーからサイトを削除します。</span><span class="sxs-lookup"><span data-stu-id="b982d-230">If you see this message, go back in the wizard to change the URL or remove the site from the retention policy.</span></span>

<span data-ttu-id="b982d-231">含めるまたは除外する個々の OneDrive アカウントを指定できる URL の形式は次のとおりです: `https://<tenant name>-my.sharepoint.com/personal/<user_name>_<tenant name>_com`</span><span class="sxs-lookup"><span data-stu-id="b982d-231">To specify individual OneDrive accounts to include or exclude, the URL has the following format: `https://<tenant name>-my.sharepoint.com/personal/<user_name>_<tenant name>_com`</span></span>

<span data-ttu-id="b982d-232">たとえば、「rsimone」のユーザー名を持つ contoso テナント内のユーザーの場合: `https://contoso-my.sharepoint.com/personal/rsimone_contoso_onmicrosoft_com`</span><span class="sxs-lookup"><span data-stu-id="b982d-232">For example, for a user in the contoso tenant that has a user name of "rsimone": `https://contoso-my.sharepoint.com/personal/rsimone_contoso_onmicrosoft_com`</span></span>

<span data-ttu-id="b982d-233">テナントの構文を確認し、ユーザーの URL を特定するには、「[組織内のすべてのユーザーの OneDrive URL のリストを取得する](/onedrive/list-onedrive-urls)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b982d-233">To verify the syntax for your tenant and identify URLs for users, see [Get a list of all user OneDrive URLs in your organization](/onedrive/list-onedrive-urls).</span></span>

### <a name="configuration-information-for-microsoft-365-groups"></a><span data-ttu-id="b982d-234">Microsoft 365 グループの構成情報</span><span class="sxs-lookup"><span data-stu-id="b982d-234">Configuration information for Microsoft 365 Groups</span></span>

<span data-ttu-id="b982d-235">Microsoft 365 グループ (以前の Office 365 グループ) のコンテンツを保持または削除するには、**Microsoft 365 グループ** の場所を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b982d-235">To retain or delete content for a Microsoft 365 group (formerly Office 365 group), use the **Microsoft 365 Groups** location.</span></span> <span data-ttu-id="b982d-236">Microsoft 365 グループには Exchange メールボックスがありますが、**Exchange メール** の場所全体が含まれるアイテム保持ポリシーには、Microsoft 365 グループのメールボックスのコンテンツは含まれません。</span><span class="sxs-lookup"><span data-stu-id="b982d-236">Even though a Microsoft 365 group has an Exchange mailbox, a retention policy that includes the entire **Exchange email** location won't include content in Microsoft 365 group mailboxes.</span></span> <span data-ttu-id="b982d-237">最初は **Exchange メール** の場所でグループ メールボックスを含めるか除外するかを指定できますが、アイテム保持ポリシーを保存しようとすると、Exchange の場所では「RemoteGroupMailbox」を選択できないことを示すエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-237">Although the **Exchange email** location initially allows you to specify a group mailbox to be included or excluded, when you try to save the retention policy, you'll see an error that "RemoteGroupMailbox" is not a valid selection for the Exchange location.</span></span>

<span data-ttu-id="b982d-238">既定では、Microsoft 365 グループに適用される保持ポリシーには、グループのメールボックスと SharePoint チーム サイトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b982d-238">By default, a retention policy applied to a Microsoft 365 group includes the group mailbox and SharePoint teams site.</span></span> <span data-ttu-id="b982d-239">SharePoint の Teams サイトに保存されたファイルは、場所でカバーされていますが、独自の保持ポリシーの場所を持つ Teams のチャットや Teams のチャネルはカバーされません。</span><span class="sxs-lookup"><span data-stu-id="b982d-239">Files stored in the SharePoint teams site are covered with this location, but not Teams chats or Teams channel messages that have their own retention policy locations.</span></span>

<span data-ttu-id="b982d-240">保持ポリシーを Microsoft 365 メールボックスのみ、または接続された SharePoint チーム サイトのみに適用するために既定を変更するには、次のいずれかの値を指定した *Applications* パラメーターを指定して [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) PowerShell コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="b982d-240">To change the default because you want the retention policy to apply to either just the Microsoft 365 mailboxes, or just the connected SharePoint teams sites, use the [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) PowerShell cmdlet with the *Applications* parameter with one of the following values:</span></span>

- <span data-ttu-id="b982d-241">グループに接続されている Microsoft 365 メールボックスのみの場合は `Group:Exchange`。</span><span class="sxs-lookup"><span data-stu-id="b982d-241">`Group:Exchange` for just Microsoft 365 mailboxes that are connected to the group.</span></span>
- <span data-ttu-id="b982d-242">グループに接続されている SharePoint サイトのみの場合は `Group:SharePoint`。</span><span class="sxs-lookup"><span data-stu-id="b982d-242">`Group:SharePoint` for just SharePoint sites that are connected to the group.</span></span>

<span data-ttu-id="b982d-243">選択した Microsoft 365 グループのメールボックスと SharePoint サイトの両方の既定値に戻すには、`Group:Exchange,SharePoint`を指定します。</span><span class="sxs-lookup"><span data-stu-id="b982d-243">To return to the default value of both the mailbox and SharePoint site for the selected Microsoft 365 groups, specify `Group:Exchange,SharePoint`.</span></span>

### <a name="configuration-information-for-skype-for-business"></a><span data-ttu-id="b982d-244">Skype for Business の構成情報</span><span class="sxs-lookup"><span data-stu-id="b982d-244">Configuration information for Skype for Business</span></span>

<span data-ttu-id="b982d-245">Exchange メールとは異なり Skype の場所の状態をオンに切り替えて自動的にすべてのユーザーを含めることはできませんが、そのロケーションをオンにしてから、会話を保持するユーザーを手動で選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b982d-245">Unlike Exchange email, you can't toggle the status of the Skype location on to automatically include all users, but when you turn on that location, you must then manually choose the users whose conversations you want to retain:</span></span>

![アイテム保持ポリシーの Skype の場所を選択する](../media/skype-location-retention-policies.png)

<span data-ttu-id="b982d-247">[**ユーザーの選択**] を選択すると、[**すべて選択する**] ボックスを選択して、すべてのユーザーをすばやく含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b982d-247">When you select **Choose user**, you can quickly include all users by selecting the **Select all** box.</span></span> <span data-ttu-id="b982d-248">ただし、各ユーザーはポリシーの特定のインクルージョンとしてカウントされることを理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="b982d-248">However, it's important to understand that each user counts as a specific inclusion in the policy.</span></span> <span data-ttu-id="b982d-249">したがって、[**すべて選択**] ボックスを選択して 1,000 人のユーザーを含める場合、含める 1,000 人のユーザーを手動で選択した場合と同じです。これは、Skype for Business でサポートされる最大数です。</span><span class="sxs-lookup"><span data-stu-id="b982d-249">So if you include 1,000 users by selecting the **Select all** box, it's the same as if you manually selected 1,000 users to include, which is the maximum supported for Skype for Business.</span></span>

<span data-ttu-id="b982d-250">[**会話履歴**] (Outlook のフォルダー) は、Skype のアーカイブとは関係のない機能です。</span><span class="sxs-lookup"><span data-stu-id="b982d-250">Be aware that **Conversation History**, a folder in Outlook, is a feature that has nothing to do with Skype archiving.</span></span> <span data-ttu-id="b982d-251">[**会話履歴**] は、エンドユーザーが無効にすることができます。しかし、Skype のアーカイブの場合は、ユーザーによるアクセスは不可能ですが、電子情報開示で利用できる非表示フォルダーに Skype の会話のコピーが保存されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-251">**Conversation History** can be turned off by the end user, but archiving for Skype is done by storing a copy of Skype conversations in a hidden folder that is inaccessible to the user but available to eDiscovery.</span></span>

## <a name="settings-for-retaining-and-deleting-content"></a><span data-ttu-id="b982d-252">コンテンツを保持および削除するための設定</span><span class="sxs-lookup"><span data-stu-id="b982d-252">Settings for retaining and deleting content</span></span>

<span data-ttu-id="b982d-253">アイテム保持ポリシーでコンテンツを保持および削除するための設定を選択すると、アイテム保持ポリシーは、指定された期間、次のいずれかの構成になります。</span><span class="sxs-lookup"><span data-stu-id="b982d-253">By choosing the settings for retaining and deleting content in your retention policy, your retention policy will have one of the following configurations for a specified period of time:</span></span>

- <span data-ttu-id="b982d-254">保持のみ</span><span class="sxs-lookup"><span data-stu-id="b982d-254">Retain-only</span></span>

    <span data-ttu-id="b982d-255">この構成では、[**特定の期間アイテムを保持する**] と [**保持期間の終了時: 何もしない**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b982d-255">For this configuration, choose **Retain items for a specific period** and **At end of the retention period: Do nothing**.</span></span> <span data-ttu-id="b982d-256">または、[**アイテムを無期限に保持する**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b982d-256">Or, select **Retain items forever**.</span></span>

- <span data-ttu-id="b982d-257">保持してから削除</span><span class="sxs-lookup"><span data-stu-id="b982d-257">Retain and then delete</span></span>

    <span data-ttu-id="b982d-258">この構成では、[**特定の期間アイテムを保持する**] と [**保持期間の終了時: アイテムを自動的に削除する**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b982d-258">For this configuration, choose **Retain items for a specific period** and **At end of the retention period: Delete items automatically**.</span></span>

- <span data-ttu-id="b982d-259">削除のみ</span><span class="sxs-lookup"><span data-stu-id="b982d-259">Delete-only</span></span>

    <span data-ttu-id="b982d-260">この構成では、[**アイテムが特定の年齢に達したときにのみアイテムを削除する**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b982d-260">For this configuration, choose **Only delete items when they reach a certain age**.</span></span>

### <a name="retaining-content-for-a-specific-period-of-time"></a><span data-ttu-id="b982d-261">コンテンツを特定の期間保持する</span><span class="sxs-lookup"><span data-stu-id="b982d-261">Retaining content for a specific period of time</span></span>

<span data-ttu-id="b982d-262">アイテム保持ポリシーを構成するときは、アイテムを特定の日数、月数、または年数の間保持することを選択します。</span><span class="sxs-lookup"><span data-stu-id="b982d-262">When you configure a retention policy, you choose to retain items for a specific number of days, months, or years.</span></span> <span data-ttu-id="b982d-263">または、アイテムを永久に保持します。</span><span class="sxs-lookup"><span data-stu-id="b982d-263">Or alternatively, retain the items forever.</span></span>

<span data-ttu-id="b982d-264">アイテム保持ポリシーを構成するときは、コンテンツを無期限に、または特定の日数、月数、または年数の間保持することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="b982d-264">When you configure a retention policy, you can choose to retain content indefinitely or for a specific number of days, months, or years.</span></span> <span data-ttu-id="b982d-265">保存期間は、アイテム保持ポリシーが適用された時点からではなくコンテンツの経過時間から計算されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-265">The retention period is calculated from the age of the content, not from when the retention policy is applied.</span></span>

<span data-ttu-id="b982d-266">保持期間の開始時に、コンテンツがいつ作成されたか、またはコンテンツが最後に変更されたときの、SharePoint、OneDrive、Microsoft 365 グループのファイルのみサポートされるかを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="b982d-266">For the start of the retention period, you can also choose when the content was created or, supported only for files and the SharePoint, OneDrive, and Microsoft 365 Groups, when the content was last modified.</span></span>

<span data-ttu-id="b982d-267">例:</span><span class="sxs-lookup"><span data-stu-id="b982d-267">Examples:</span></span>

- <span data-ttu-id="b982d-268">SharePoint: サイト コレクションのコンテンツを最後に変更してから 7 年間このアイテムを保持する場合に、そのサイト コレクションのドキュメントが 6 年変更されていないと、そのドキュメントが変更されなければあと 1 年間しか保持されません。</span><span class="sxs-lookup"><span data-stu-id="b982d-268">SharePoint: If you want to retain items in a site collection for seven years after this content is last modified, and a document in that site collection hasn't been modified in six years, the document will be retained for only another year if it's not modified.</span></span> <span data-ttu-id="b982d-269">そのドキュメントがもう一度編集された場合、ドキュメントの古さは最後に変更された日付から計算され、その後 7 年間保留にされます。</span><span class="sxs-lookup"><span data-stu-id="b982d-269">If the document is edited again, the age of the document is calculated from the new last modified date, and it will be retained for another seven years.</span></span>

- <span data-ttu-id="b982d-270">Exchange: メールボックスのアイテムを 7 年間保持する場合、あるメッセージが 6 年前に送信されているときは、あと 1 年間のみ保持されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-270">Exchange: If you want to retain items in a mailbox for seven years, and a message was sent six years ago, the message will be retained for only one year.</span></span> <span data-ttu-id="b982d-271">Exchange アイテムの場合、経過時間は受信メールの受信日または送信メールの送信日に基づいています。</span><span class="sxs-lookup"><span data-stu-id="b982d-271">For Exchange items, the age is based on the date received for incoming email, or the date sent for outgoing email.</span></span> <span data-ttu-id="b982d-272">最終更新日に基づいてアイテムを保持するポリシーは、OneDrive および SharePoint のコンテンツ サイトにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-272">Retaining items based on when it was last modified applies only to site content in OneDrive and SharePoint.</span></span>

<span data-ttu-id="b982d-273">保持期間の終了時にコンテンツを完全に削除するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="b982d-273">At the end of the retention period, you choose whether you want the content to be permanently deleted:</span></span>

![[アイテム保持設定] ページ](../media/b05f84e5-fc71-4717-8f7b-d06a29dc4f29.png)

### <a name="deleting-content-thats-older-than-a-specific-age"></a><span data-ttu-id="b982d-275">特定の経過時間を超えた古いコンテンツを削除する</span><span class="sxs-lookup"><span data-stu-id="b982d-275">Deleting content that's older than a specific age</span></span>

<span data-ttu-id="b982d-276">アイテム保持ポリシーは、アイテムを保持してから削除することも、古いアイテムを保持せずに削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="b982d-276">A retention policy can both retain and then delete items, or delete old items without retaining them.</span></span>

<span data-ttu-id="b982d-277">どちらの場合も、アイテム保持ポリシーによってアイテムを削除する場合、アイテム保持ポリシーに指定した期間は、ポリシーが割り当てられた時点からではなく、アイテムが作成または変更された時点から計算されることを理解しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="b982d-277">In both cases, if your retention policy deletes items, it's important to understand that the time period specified for a retention policy is calculated from the time when the item was created or modified, and not the time since the policy was assigned.</span></span>

<span data-ttu-id="b982d-p134">したがって、アイテム保持ポリシーを初めて割り当てる前に、特にそのポリシーでアイテムを削除する場合は、まず既存のコンテンツの保存期間と、ポリシーがコンテンツに与える影響を検討してください。また、新しいポリシーを割り当てる前にユーザーに伝達し、発生する可能性がある影響を評価する時間を与えます。</span><span class="sxs-lookup"><span data-stu-id="b982d-p134">So before you assign a retention policy for the first time, and especially when that policy deletes items, first consider the age of the existing content and how the policy may impact that content. You might also want to communicate the new policy to your users before assigning it, to give them time to assess the possible impact.</span></span>

### <a name="a-policy-that-applies-to-entire-locations"></a><span data-ttu-id="b982d-280">場所全体に適用されるポリシー</span><span class="sxs-lookup"><span data-stu-id="b982d-280">A policy that applies to entire locations</span></span>

<span data-ttu-id="b982d-281">場所を選択すると、Skype for Business を除き、場所の状態が [**オン**] の場合の既定の設定は [**すべて**] になります。</span><span class="sxs-lookup"><span data-stu-id="b982d-281">When you choose locations, with the exception of Skype for Business, the default setting is **All** when the status of the location is **On**.</span></span>

<span data-ttu-id="b982d-282">アイテム保持ポリシーが場所全体の任意の組み合わせに適用される場合、ポリシーに含めることができる受信者、サイト、アカウント、グループなどの数に制限はありません。</span><span class="sxs-lookup"><span data-stu-id="b982d-282">When a retention policy applies to any combination of entire locations, there is no limit to the number of recipients, sites, accounts, groups, etc., that the policy can include.</span></span>

<span data-ttu-id="b982d-283">たとえば、ポリシーにすべての Exchange メールとすべての SharePoint サイトが含まれている場合、数に関係なくすべてのサイトと受信者が含められます。</span><span class="sxs-lookup"><span data-stu-id="b982d-283">For example, if a policy includes all Exchange email and all SharePoint sites, all sites and recipients will be included, no matter how many.</span></span> <span data-ttu-id="b982d-284">また、Exchange の場合、ポリシーの適用後に作成された新しいメールボックスには、そのポリシーが自動的に継承されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-284">And for Exchange, any new mailbox created after the policy is applied will automatically inherit the policy.</span></span>

### <a name="a-policy-with-specific-inclusions-or-exclusions"></a><span data-ttu-id="b982d-285">特定の追加または除外を含むポリシー</span><span class="sxs-lookup"><span data-stu-id="b982d-285">A policy with specific inclusions or exclusions</span></span>

<span data-ttu-id="b982d-286">省略可能な構成を使用して、特定のユーザー、特定の Microsoft 365 グループ、特定のサイトに保持設定を適用する場合にのみ、ポリシーごとに注意すべき制限事項があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b982d-286">Be aware that if you use the optional configuration to scope your retention settings to specific users, specific Microsoft 365 groups, or specific sites, there are some limits per policy to be aware of.</span></span> <span data-ttu-id="b982d-287">詳細については、「[アイテム保持ポリシーと保持ラベルポリシーの制限](retention-limits.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b982d-287">For more information, see [Limits for retention policies and retention label policies](retention-limits.md).</span></span> 

<span data-ttu-id="b982d-288">省略可能な構成を使用して保持設定を適用するには、目的の場所の [**状態**] が [**オン**] であることを確認した上で、リンクを使用して特定のユーザー、Microsoft 365 グループ、またはサイトを含めたり除外したりします。</span><span class="sxs-lookup"><span data-stu-id="b982d-288">To use the optional configuration to scope your retention settings, make sure the **Status** of that location is **On**, and then use the links to include or exclude specific users, Microsoft 365 groups, or sites.</span></span>

> [!WARNING]
> <span data-ttu-id="b982d-289">含まれる内容を構成してから最後のものを削除すると、その場所の構成は **All** に戻ります。</span><span class="sxs-lookup"><span data-stu-id="b982d-289">If you configure includes and then remove the last one, the configuration reverts to **All** for the location.</span></span>  <span data-ttu-id="b982d-290">ポリシーを保存する前に、これが意図した構成であることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="b982d-290">Make sure this is the configuration that you intend before you save the policy.</span></span>
>
> <span data-ttu-id="b982d-291">たとえば、データを削除するように設定されているアイテム保持ポリシーに含める SharePoint サイトを 1 つ指定していて、そのサイトを削除した場合、既定では、すべての SharePoint サイトがデータを完全に削除するアイテム保持ポリシーの対象となります。</span><span class="sxs-lookup"><span data-stu-id="b982d-291">For example, if you specify one SharePoint site to include in your retention policy that's configured to delete data, and then remove the single site, by default all SharePoint sites will then be subject to the retention policy that permanently deletes data.</span></span> <span data-ttu-id="b982d-292">Exchange 受信者、OneDrive アカウント、Teams チャット ユーザーなどに含まれる内容にも同様に適用されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-292">The same applies to includes for Exchange recipients, OneDrive accounts, Teams chat users etc.</span></span>
>
> <span data-ttu-id="b982d-293">このシナリオでは、その場所の **All** 設定をアイテム保持ポリシーの対象にしたくない場合、場所をオフに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b982d-293">In this scenario, toggle the location off if you don't want the **All** setting for the location to be subject to the retention policy.</span></span> <span data-ttu-id="b982d-294">あるいは、ポリシーの適用から除外されるように指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="b982d-294">Alternatively, specify excludes to be exempt from the policy.</span></span>

## <a name="updating-retention-policies"></a><span data-ttu-id="b982d-295">アイテム保持ポリシーの更新</span><span class="sxs-lookup"><span data-stu-id="b982d-295">Updating retention policies</span></span>

<span data-ttu-id="b982d-296">アイテム保持ポリシーを作成して保存した後には変更できない設定があり、それらは以下のものを含みます。</span><span class="sxs-lookup"><span data-stu-id="b982d-296">Some settings can't be changed after a retention policy is created and saved, which include:</span></span>
- <span data-ttu-id="b982d-297">アイテム保持ポリシー名と保持期間を除く保持設定、および保持期間を開始するタイミング。</span><span class="sxs-lookup"><span data-stu-id="b982d-297">The retention policy name and the retention settings except the retention period and when to start the retention period.</span></span>

<span data-ttu-id="b982d-298">アイテム保持ポリシーを編集し、アイテムが既にアイテム保持ポリシーの元の設定の対象となっている場合、更新された設定は、新しく特定されたアイテムに加えて、このアイテムに自動的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="b982d-298">If you edit a retention policy and items are already subject to the original settings in your retention policy, your updated settings will be automatically applied to these items in addition to items that are newly identified.</span></span>

<span data-ttu-id="b982d-299">通常、この更新はかなり迅速ですが、数日かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b982d-299">Usually this update is fairly quick but can take several days.</span></span> <span data-ttu-id="b982d-300">Microsoft 365 の場所間でのポリシーの複製が完了すると、Microsoft 365 コンプライアンス センターの保持ポリシーの状態が [**On (保留中)**] から [**オン (成功)**] に変わります。</span><span class="sxs-lookup"><span data-stu-id="b982d-300">When the policy replication across your Microsoft 365 locations is complete, you'll see the status of the retention policy in the Microsoft 365 compliance center change from **On (Pending)** to **On (Success)**.</span></span>

## <a name="locking-the-policy-to-prevent-changes"></a><span data-ttu-id="b982d-301">変更を防止するためにポリシーをロックする</span><span class="sxs-lookup"><span data-stu-id="b982d-301">Locking the policy to prevent changes</span></span>

<span data-ttu-id="b982d-302">ポリシーをオフにしたり、ポリシーを削除したり、制限を緩和したりすることができないようにする必要がある場合は、「[保管ロックを使用して、アイテム保持ポリシーと保持ラベル ポリシーへの変更を制限する](retention-preservation-lock.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b982d-302">If you need to ensure that no one can turn off the policy, delete the policy, or make it less restrictive, see [Use Preservation Lock to restrict changes to retention policies and retention label policies](retention-preservation-lock.md).</span></span>
