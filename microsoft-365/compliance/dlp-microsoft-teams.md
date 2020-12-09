---
title: データ損失防止と Microsoft Teams
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: これで、DLP ポリシーを Microsoft Teams のチャットおよびチャネルに適用できるようになります。 機能の詳細については、この記事を参照してください。
ms.openlocfilehash: 4903056a9a7e7ae74a8ada52bd491f2b8efe771e
ms.sourcegitcommit: d859ea36152c227699c1786ef08cda5805ecf7db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604361"
---
# <a name="data-loss-prevention-and-microsoft-teams"></a><span data-ttu-id="d936c-104">データ損失防止と Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d936c-104">Data loss prevention and Microsoft Teams</span></span>

> [!NOTE]
> <span data-ttu-id="d936c-105">データ損失防止機能は、最近、Office 365 E5/A5、Microsoft 365 E5/a5、Microsoft 365 情報保護とガバナンス、または Office 365 Advanced コンプライアンスのユーザー向けに、Microsoft Teams のチャットおよびチャネルメッセージに追加されました。</span><span class="sxs-lookup"><span data-stu-id="d936c-105">Data loss prevention capabilities were recently added to Microsoft Teams chat and channel messages for users licensed for Office 365 E5/A5, Microsoft 365 E5/A5, Microsoft 365 Information Protection and Governance or Office 365 Advanced Compliance.</span></span> <span data-ttu-id="d936c-106">Office 365 と Microsoft 365 E3 には、SharePoint Online、OneDrive、および Exchange Online の DLP 保護が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d936c-106">Office 365 and Microsoft 365 E3 include DLP protection for SharePoint Online, OneDrive, and Exchange Online.</span></span> <span data-ttu-id="d936c-107">これには、Teams が SharePoint Online と OneDrive を使用してファイルを共有するため、Teams によって共有されるファイルも含まれます。</span><span class="sxs-lookup"><span data-stu-id="d936c-107">This also includes files that are shared through Teams because Teams uses SharePoint Online and OneDrive to share files.</span></span>
<span data-ttu-id="d936c-108">Teams チャットで DLP 保護をサポートするには、E5 が必要です。</span><span class="sxs-lookup"><span data-stu-id="d936c-108">Support for DLP protection in Teams Chat requires E5.</span></span>
<span data-ttu-id="d936c-109">ライセンス要件の詳細については、「[Microsoft 365 テナントレベル サービスのライセンスに関するガイダンス](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d936c-109">To learn more about licensing requirements, see [Microsoft 365 Tenant-Level Services Licensing Guidance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance).</span></span>

## <a name="overview-of-dlp-for-microsoft-teams"></a><span data-ttu-id="d936c-110">Microsoft Teams の DLP の概要</span><span class="sxs-lookup"><span data-stu-id="d936c-110">Overview of DLP for Microsoft Teams</span></span>

<span data-ttu-id="d936c-111">最近では、 [データ損失防止](data-loss-prevention-policies.md) (DLP) 機能が、 **プライベートチャネルメッセージを含む** Microsoft Teams のチャットおよびチャネルメッセージを含むように拡張されました。</span><span class="sxs-lookup"><span data-stu-id="d936c-111">Recently, [data loss prevention](data-loss-prevention-policies.md) (DLP) capabilities were extended to include Microsoft Teams chat and channel messages, **including private channel messages**.</span></span>


<span data-ttu-id="d936c-112">組織に DLP がある場合は、Microsoft Teams チャネルまたはチャットセッションで機密情報を共有できないようにするポリシーを定義できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d936c-112">If your organization has DLP, you can now define policies that prevent people from sharing sensitive information in a Microsoft Teams channel or chat session.</span></span> <span data-ttu-id="d936c-113">この保護がどのように機能するかについて、いくつかの例を示します。</span><span class="sxs-lookup"><span data-stu-id="d936c-113">Here are some examples of how this protection works:</span></span>

- <span data-ttu-id="d936c-114">**例 1: メッセージ内の機密情報を保護** します。</span><span class="sxs-lookup"><span data-stu-id="d936c-114">**Example 1: Protecting sensitive information in messages**.</span></span> <span data-ttu-id="d936c-115">チームのチャットまたはチャネル内の機密情報をゲスト (外部ユーザー) と共有しようとするユーザーがいるとします。</span><span class="sxs-lookup"><span data-stu-id="d936c-115">Suppose that someone attempts to share sensitive information in a Teams chat or channel with guests (external users).</span></span> <span data-ttu-id="d936c-116">これを防止するように定義された DLP ポリシーがある場合、外部ユーザーに送信される機密情報を含むメッセージは削除されます。</span><span class="sxs-lookup"><span data-stu-id="d936c-116">If you have a DLP policy defined to prevent this, messages with sensitive information that are sent to external users are deleted.</span></span> <span data-ttu-id="d936c-117">これは、DLP ポリシーがどのように構成されているかに応じて、数秒で自動的に発生します。</span><span class="sxs-lookup"><span data-stu-id="d936c-117">This happens automatically, and within seconds, according to how your DLP policy is configured.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d936c-118">Microsoft Teams の DLP では、次のものを持つ Microsoft Teams ユーザーとの共有時に機密コンテンツがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="d936c-118">DLP for Microsoft Teams blocks sensitive content when shared with Microsoft Teams users who have:</span></span><br/><span data-ttu-id="d936c-119">- teams およびチャネルでの[ゲストアクセス](https://docs.microsoft.com/MicrosoftTeams/guest-access)。や</span><span class="sxs-lookup"><span data-stu-id="d936c-119">- [guest access](https://docs.microsoft.com/MicrosoftTeams/guest-access) in teams and channels; or</span></span><br/><span data-ttu-id="d936c-120">- 会議およびチャットセッションでの[外部アクセス](https://docs.microsoft.com/MicrosoftTeams/manage-external-access)。</span><span class="sxs-lookup"><span data-stu-id="d936c-120">- [external access](https://docs.microsoft.com/MicrosoftTeams/manage-external-access) in meetings and chat sessions.</span></span> <p><span data-ttu-id="d936c-121">外部チャットセッションの DLP は、送信者と受信者の両方が Teams のみのモードで、 [Microsoft teams のネイティブフェデレーション](https://docs.microsoft.com/microsoftteams/manage-external-access)を使用している場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="d936c-121">DLP for external chat sessions will only work if both the sender and the receiver are in Teams Only mode and using [Microsoft Teams native federation](https://docs.microsoft.com/microsoftteams/manage-external-access).</span></span> <span data-ttu-id="d936c-122">Teams の DLP では、Skype for Business または非ネイティブのフェデレーションチャットセッションによる [相互運用](https://docs.microsoft.com/microsoftteams/teams-and-skypeforbusiness-coexistence-and-interoperability#interoperability-of-teams-and-skype-for-business) のメッセージはブロックされません。</span><span class="sxs-lookup"><span data-stu-id="d936c-122">DLP for Teams does not block messages in [interop](https://docs.microsoft.com/microsoftteams/teams-and-skypeforbusiness-coexistence-and-interoperability#interoperability-of-teams-and-skype-for-business) with Skype for Business or non-native federated chat sessions.</span></span>

- <span data-ttu-id="d936c-123">**例 2: ドキュメント内の機密情報を保護** します。</span><span class="sxs-lookup"><span data-stu-id="d936c-123">**Example 2: Protecting sensitive information in documents**.</span></span> <span data-ttu-id="d936c-124">Microsoft Teams チャネルまたはチャットのゲストでドキュメントを共有しようとした場合に、ドキュメントに機密情報が含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="d936c-124">Suppose that someone attempts to share a document with guests in a Microsoft Teams channel or chat, and the document contains sensitive information.</span></span> <span data-ttu-id="d936c-125">これを防止するように定義された DLP ポリシーがある場合、ドキュメントはそれらのユーザーに対して開くことができません。</span><span class="sxs-lookup"><span data-stu-id="d936c-125">If you have a DLP policy defined to prevent this, the document won't open for those users.</span></span> <span data-ttu-id="d936c-126">この場合、DLP ポリシーには、保護を設定するために SharePoint と OneDrive を含める必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d936c-126">Note that in this case, your DLP policy must include SharePoint and OneDrive in order for protection to be in place.</span></span> <span data-ttu-id="d936c-127">(これは Microsoft Teams に表示される SharePoint の DLP の例であり、ユーザーは office 365 DLP (Office 365 E3 に含まれています) のライセンスが必要ですが、ユーザーに Office 365 Advanced コンプライアンスのライセンスを付与する必要はありません。)</span><span class="sxs-lookup"><span data-stu-id="d936c-127">(This is an example of DLP for SharePoint that shows up in Microsoft Teams, and therefore requires that users are licensed for Office 365 DLP (included in Office 365 E3), but does not require users to be licensed for Office 365 Advanced Compliance.)</span></span>

## <a name="policy-tips-help-educate-users"></a><span data-ttu-id="d936c-128">ユーザーを教育するためのポリシーヒント</span><span class="sxs-lookup"><span data-stu-id="d936c-128">Policy tips help educate users</span></span>

<span data-ttu-id="d936c-129">[Exchange、outlook、outlook on the web](data-loss-prevention-policies.md#policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web)、 [SharePoint Online、OneDrive for business サイト](data-loss-prevention-policies.md#policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites)、および[OFFICE デスクトップクライアント](data-loss-prevention-policies.md#policy-evaluation-in-the-office-desktop-programs)での dlp の動作と同様に、操作が dlp ポリシーと競合すると、ポリシーヒントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d936c-129">Similar to how DLP works in [Exchange, Outlook, Outlook on the web](data-loss-prevention-policies.md#policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web), [SharePoint Online, OneDrive for Business sites](data-loss-prevention-policies.md#policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites), and [Office desktop clients](data-loss-prevention-policies.md#policy-evaluation-in-the-office-desktop-programs), policy tips appear when an action conflicts with a DLP policy.</span></span> <span data-ttu-id="d936c-130">ポリシーヒントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d936c-130">Here's an example of a policy tip:</span></span>

![Teams でブロックされたメッセージ通知](../media/dlp-teams-blockedmessage-notification.png)

<span data-ttu-id="d936c-132">この場合、送信者は Microsoft Teams チャネルでソーシャルセキュリティ番号を共有しようとしました。</span><span class="sxs-lookup"><span data-stu-id="d936c-132">In this case, the sender attempted to share a social security number in a Microsoft Teams channel.</span></span> <span data-ttu-id="d936c-133">[ **何を行いますか?** ] リンクは、問題を解決するために送信者に対してオプションを提供するダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="d936c-133">The **What can I do?** link opens a dialog box that provides options for the sender to resolve the issue.</span></span> <span data-ttu-id="d936c-134">この場合、送信者はポリシーを上書きするか、管理者に通知してそれを確認して解決するかを選択することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d936c-134">Notice that in this case, the sender can opt to override the policy, or notify an admin to review and resolve it.</span></span>

![ブロックされたメッセージを解決するためのオプション](../media/dlp-teams-blockedmessage-possibleactions.png)

<span data-ttu-id="d936c-136">組織では、ユーザーが DLP ポリシーを上書きすることを許可するかどうかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="d936c-136">In your organization, you can choose to allow users to override a DLP policy.</span></span> <span data-ttu-id="d936c-137">また、DLP ポリシーを構成するときは、既定のポリシーヒントを使用するか、組織の [ポリシーヒントをカスタマイズ](#to-customize-policy-tips) できます。</span><span class="sxs-lookup"><span data-stu-id="d936c-137">And, when you configure your DLP policies, you can use the default policy tips, or [customize policy tips](#to-customize-policy-tips) for your organization.</span></span>

<span data-ttu-id="d936c-138">この例では、送信者が Teams チャネルで社会保障番号を共有している場合、受信者は次のように表示されています。</span><span class="sxs-lookup"><span data-stu-id="d936c-138">Returning to our example, where a sender shared a social security number in a Teams channel, here's what the recipient saw:</span></span>

![ブロックされたメッセージ](../media/dlp-teams-blockedmessage-notification-to-user.png)

<span data-ttu-id="d936c-140">[ **ポップヒント]** リンクによって、メッセージがブロックされた理由を説明する DLP ポリシーに関する [記事](data-loss-prevention-policies.md) が開きます。</span><span class="sxs-lookup"><span data-stu-id="d936c-140">The **What's this?** link opens an [article](data-loss-prevention-policies.md) about DLP policies, which helps explain why the message was blocked.</span></span>

### <a name="to-customize-policy-tips"></a><span data-ttu-id="d936c-141">ポリシーヒントをカスタマイズするには</span><span class="sxs-lookup"><span data-stu-id="d936c-141">To customize policy tips</span></span>

<span data-ttu-id="d936c-142">このタスクを実行するには、DLP ポリシーを編集する権限を持つ役割が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d936c-142">To perform this task, you must be assigned a role that has permissions to edit DLP policies.</span></span> <span data-ttu-id="d936c-143">詳細については、「[アクセス許可](data-loss-prevention-policies.md#permissions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d936c-143">To learn more, see [Permissions](data-loss-prevention-policies.md#permissions).</span></span>

1. <span data-ttu-id="d936c-144">セキュリティ & コンプライアンスセンター () に移動し、 [https://protection.office.com](https://protection.office.com) サインインします。</span><span class="sxs-lookup"><span data-stu-id="d936c-144">Go to the Security & Compliance Center ([https://protection.office.com](https://protection.office.com)) and sign in.</span></span>

2. <span data-ttu-id="d936c-145">[**データ損失防止** ポリシー] を選択し  >  **Policy** ます。</span><span class="sxs-lookup"><span data-stu-id="d936c-145">Choose **Data loss prevention** > **Policy**.</span></span>

3. <span data-ttu-id="d936c-146">ポリシーを選択し、[ **ポリシー設定**] の横にある [ **編集**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d936c-146">Select a policy, and next to **Policy settings**, choose **Edit**.</span></span>

4. <span data-ttu-id="d936c-147">新しいルールを作成するか、ポリシーの既存のルールを編集します。</span><span class="sxs-lookup"><span data-stu-id="d936c-147">Either create a new rule, or edit an existing rule for the policy.</span></span><br/>![ポリシーのルールを編集する](../media/dlp-teams-editrule.png)<br/>

5. <span data-ttu-id="d936c-149">[ **ユーザー通知** ] タブで、[ **電子メールテキストのカスタマイズ** ] または [ **ポリシーヒントテキストオプションのカスタマイズ** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d936c-149">On the **User notifications** tab, select **Customize the email text** and/or **Customize the policy tip text** options.</span></span><br/><span data-ttu-id="d936c-150">![ユーザー通知とポリシーヒントをカスタマイズする](../media/dlp-teams-editrule-usernotifications.png)</span><span class="sxs-lookup"><span data-stu-id="d936c-150">![Customize user notifications and policy tips](../media/dlp-teams-editrule-usernotifications.png)</span></span><br/>  

6. <span data-ttu-id="d936c-151">電子メール通知やポリシーヒントに使用するテキストを指定し、[ **保存**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d936c-151">Specify the text you want to use for email notifications and/or policy tips, and then choose **Save**.</span></span>

7. <span data-ttu-id="d936c-152">[ **ポリシー設定** ] タブで、[ **保存**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d936c-152">On the **Policy settings** tab, choose **Save**.</span></span>

<span data-ttu-id="d936c-153">変更がデータセンターを経由して、ユーザーアカウントに同期されるまで約1時間の時間を確保します。</span><span class="sxs-lookup"><span data-stu-id="d936c-153">Allow approximately one hour for your changes to work their way through your data center and sync to user accounts.</span></span>
 <!-- why are these syncing to user accounts? -->
## <a name="add-microsoft-teams-as-a-location-to-existing-dlp-policies"></a><span data-ttu-id="d936c-154">既存の DLP ポリシーに Microsoft Teams を場所として追加する</span><span class="sxs-lookup"><span data-stu-id="d936c-154">Add Microsoft Teams as a location to existing DLP policies</span></span>

<span data-ttu-id="d936c-155">このタスクを実行するには、DLP ポリシーを編集する権限を持つ役割が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d936c-155">To perform this task, you must be assigned a role that has permissions to edit DLP policies.</span></span> <span data-ttu-id="d936c-156">詳細については、「[アクセス許可](data-loss-prevention-policies.md#permissions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d936c-156">To learn more, see [Permissions](data-loss-prevention-policies.md#permissions).</span></span>

1. <span data-ttu-id="d936c-157">セキュリティ & コンプライアンスセンター () に移動し、 [https://protection.office.com](https://protection.office.com) サインインします。</span><span class="sxs-lookup"><span data-stu-id="d936c-157">Go to the Security & Compliance Center ([https://protection.office.com](https://protection.office.com)) and sign in.</span></span>

2. <span data-ttu-id="d936c-158">[**データ損失防止** ポリシー] を選択し  >  **Policy** ます。</span><span class="sxs-lookup"><span data-stu-id="d936c-158">Choose **Data loss prevention** > **Policy**.</span></span>

3. <span data-ttu-id="d936c-159">ポリシーを選択し、[ **場所**] で値を確認します。</span><span class="sxs-lookup"><span data-stu-id="d936c-159">Select a policy, and look at the values under **Locations**.</span></span> <span data-ttu-id="d936c-160">**Teams のチャットおよびチャネルメッセージ** が表示される場合は、すべて設定されています。</span><span class="sxs-lookup"><span data-stu-id="d936c-160">If you see **Teams chat and channel messages**, you're all set.</span></span> <span data-ttu-id="d936c-161">表示しない場合は、[ **編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d936c-161">If you don't, click **Edit**.</span></span><br/><span data-ttu-id="d936c-162">![既存のポリシーの場所](../media/dlp-teams-editexistingpolicy.png)</span><span class="sxs-lookup"><span data-stu-id="d936c-162">![Locations for existing policy](../media/dlp-teams-editexistingpolicy.png)</span></span><br/>

4. <span data-ttu-id="d936c-163">[ **状態** ] 列で、 **Teams のチャットおよびチャネルメッセージ** のポリシーをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d936c-163">In the **Status** column, turn the policy on for **Teams chat and channel messages**.</span></span><br/><span data-ttu-id="d936c-164">![Teams のチャットおよびチャネルの DLP](../media/dlp-teams-addteamschatschannels.png)</span><span class="sxs-lookup"><span data-stu-id="d936c-164">![DLP for Teams chats and channels](../media/dlp-teams-addteamschatschannels.png)</span></span><br/>

5. <span data-ttu-id="d936c-165">すべてのアカウントの既定の設定をそのまま使用するか、または含めるアカウントまたは除外するアカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="d936c-165">Keep the default settings of all accounts, or specify which accounts to include or exclude.</span></span>

6. <span data-ttu-id="d936c-166">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d936c-166">Click **Save**.</span></span>

<span data-ttu-id="d936c-167">変更がデータセンターを経由して、ユーザーアカウントに同期されるまで約1時間の時間を確保します。</span><span class="sxs-lookup"><span data-stu-id="d936c-167">Allow approximately one hour for your changes to work their way through your data center and sync to user accounts.</span></span>
<!-- again, why user accounts? -->
## <a name="define-a-new-dlp-policy-for-microsoft-teams"></a><span data-ttu-id="d936c-168">Microsoft Teams の新しい DLP ポリシーを定義する</span><span class="sxs-lookup"><span data-stu-id="d936c-168">Define a new DLP policy for Microsoft Teams</span></span>

<span data-ttu-id="d936c-169">このタスクを実行するには、DLP ポリシーを編集する権限を持つ役割が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d936c-169">To perform this task, you must be assigned a role that has permissions to edit DLP policies.</span></span> <span data-ttu-id="d936c-170">詳細については、「[アクセス許可](data-loss-prevention-policies.md#permissions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d936c-170">To learn more, see [Permissions](data-loss-prevention-policies.md#permissions).</span></span>

1. <span data-ttu-id="d936c-171">セキュリティ & コンプライアンスセンター () に移動し、 [https://protection.office.com](https://protection.office.com) サインインします。</span><span class="sxs-lookup"><span data-stu-id="d936c-171">Go to the Security & Compliance Center ([https://protection.office.com](https://protection.office.com)) and sign in.</span></span>

2. <span data-ttu-id="d936c-172">[**データ損失防止** ポリシー] を選択して  >  **Policy**  >  **、ポリシーを作成** します。</span><span class="sxs-lookup"><span data-stu-id="d936c-172">Choose **Data loss prevention** > **Policy** > **+ Create a policy**.</span></span>

3. <span data-ttu-id="d936c-173">[テンプレート](data-loss-prevention-policies.md#dlp-policy-templates)を選択し、[**次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d936c-173">Choose a [template](data-loss-prevention-policies.md#dlp-policy-templates), and then choose **Next**.</span></span><br/><span data-ttu-id="d936c-174">この例では、米国の個人を特定できる情報データテンプレートを選択しました。</span><span class="sxs-lookup"><span data-stu-id="d936c-174">In our example, we chose the U.S. Personally Identifiable Information Data template.</span></span><br/><span data-ttu-id="d936c-175">![DLP ポリシーのプライバシーテンプレート](../media/dlp-teams-createnewpolicy-template.png)</span><span class="sxs-lookup"><span data-stu-id="d936c-175">![Privacy template for DLP policy](../media/dlp-teams-createnewpolicy-template.png)</span></span><br/>

4. <span data-ttu-id="d936c-176">[ **ポリシーに名前** をつける] タブで、ポリシーの名前と説明を指定し、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d936c-176">On the **Name your policy** tab, specify a name and description for the policy, and then choose **Next**.</span></span>

5. <span data-ttu-id="d936c-177">[ **場所の選択** ] タブで、すべての場所の既定の設定をそのまま使用するか、[特定の **場所を選択** する] を選択して、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d936c-177">On the **Choose locations** tab, keep the default setting of all locations, or select **Let me choose specific locations**, and then choose **Next**.</span></span><br/><span data-ttu-id="d936c-178">特定の場所を選択した場合は、DLP ポリシーに対してそれらの場所を選択し、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d936c-178">If you chose specific locations, select them for your DLP policy, and then choose **Next**.</span></span><br/><span data-ttu-id="d936c-179">![DLP ポリシーの場所](../media/dlp-teams-selectlocationsnewpolicy.png)</span><span class="sxs-lookup"><span data-stu-id="d936c-179">![DLP policy locations](../media/dlp-teams-selectlocationsnewpolicy.png)</span></span><br/>
    > [!NOTE]
    > <span data-ttu-id="d936c-180">機密情報が含まれるドキュメントが Teams で不適切に共有されないようにするには、 **SharePoint サイト** と **OneDrive アカウント** が有効になっていることを、 **teams のチャットおよびチャネルメッセージ** と一緒に確認します。</span><span class="sxs-lookup"><span data-stu-id="d936c-180">If you want to make sure documents that contain sensitive information are not shared inappropriately in Teams, make sure **SharePoint sites** and **OneDrive accounts** are turned on, along with **Teams chat and channel messages**.</span></span>

<br/>

6. <span data-ttu-id="d936c-181">[ **ポリシー設定** ] タブの [ **保護するコンテンツの種類をカスタマイズ** する] で、既定の簡易設定をそのまま使用するか、[ **詳細設定**] を選択して [ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d936c-181">On the **Policy settings** tab, under **Customize the type of content you want to protect**, keep the default simple settings, or choose **Use advanced settings**, and then choose **Next**.</span></span> <span data-ttu-id="d936c-182">[詳細設定] を選択した場合は、ポリシーのルールを作成または編集することができます。</span><span class="sxs-lookup"><span data-stu-id="d936c-182">If you choose advanced settings, you can create or edit rules for your policy.</span></span> <span data-ttu-id="d936c-183">(詳細については、「 [Simple settings](data-loss-prevention-policies.md#simple-settings-vs-advanced-settings)」と「advanced settings」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="d936c-183">(To get help with this, see [Simple settings vs. advanced settings](data-loss-prevention-policies.md#simple-settings-vs-advanced-settings).)</span></span>

7.  <span data-ttu-id="d936c-184">[ **ポリシー設定** ] タブの [ **機密情報が検出された場合に実行** する操作] で、設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="d936c-184">On the **Policy settings** tab, under **What do you want to do if we detect sensitive info?**, review the settings.</span></span> <span data-ttu-id="d936c-185">(既定の [ポリシーヒントと電子メール通知](use-notifications-and-policy-tips.md)を保持するか、カスタマイズするかを選択できます)。</span><span class="sxs-lookup"><span data-stu-id="d936c-185">(Here's where you can choose to keep default [policy tips and email notifications](use-notifications-and-policy-tips.md), or customize them.)</span></span><br/><span data-ttu-id="d936c-186">![ヒントと通知を含む DLP ポリシー設定](../media/dlp-teams-policysettings-tipsemails.png)</span><span class="sxs-lookup"><span data-stu-id="d936c-186">![DLP policy settings with tips and notifications](../media/dlp-teams-policysettings-tipsemails.png)</span></span><br/><span data-ttu-id="d936c-187">設定の確認または編集が完了したら、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d936c-187">When you're finished reviewing or editing settings, choose **Next**.</span></span>

8. <span data-ttu-id="d936c-188">[ **ポリシー設定** ] タブの [ **ポリシーをオンにするか、または最初にテストしますか?**] で、ポリシーをオンにするか、 [最初にテスト](data-loss-prevention-policies.md#roll-out-dlp-policies-gradually-with-test-mode)するか、または今すぐ有効にしないかを選択し、[ **次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d936c-188">On the **Policy settings** tab, under **Do you want to turn on the policy or test things out first?**, choose whether to turn the policy on, [test it first](data-loss-prevention-policies.md#roll-out-dlp-policies-gradually-with-test-mode), or keep it turned off for now, and then choose **Next**.</span></span><br/><span data-ttu-id="d936c-189">![ポリシーを有効にするかどうかを指定する](../media/dlp-teams-policysettings-turnonnow.png)</span><span class="sxs-lookup"><span data-stu-id="d936c-189">![Specify whether to turn the policy on](../media/dlp-teams-policysettings-turnonnow.png)</span></span><br/>

9. <span data-ttu-id="d936c-190">[ **設定の確認** ] タブで、新しいポリシーの設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="d936c-190">On the **Review your settings** tab, review the settings for your new policy.</span></span> <span data-ttu-id="d936c-191">[ **編集** ] を選択して変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="d936c-191">Choose **Edit** to make changes.</span></span> <span data-ttu-id="d936c-192">完了したら、[ **作成**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d936c-192">When you're finished, choose **Create**.</span></span>

<span data-ttu-id="d936c-193">新しいポリシーがデータセンターを使用して動作し、ユーザーアカウントに同期できるようになるまで約1時間かかります。</span><span class="sxs-lookup"><span data-stu-id="d936c-193">Allow approximately one hour for your new policy to work its way through your data center and sync to user accounts.</span></span>

## <a name="prevent-external-access-to-sensitive-documents"></a><span data-ttu-id="d936c-194">機密ドキュメントへの外部アクセスを禁止する</span><span class="sxs-lookup"><span data-stu-id="d936c-194">Prevent external access to sensitive documents</span></span>

<span data-ttu-id="d936c-195">SharePoint または Teams から外部のゲストが、機密情報を含む SharePoint ドキュメントに既定でアクセスできないようにするには、次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="d936c-195">To ensure that SharePoint documents that contain sensitive information cannot be accessed by external guests either from SharePoint or Teams by default, select the following:</span></span>

- <span data-ttu-id="d936c-196">ドキュメントが DLP スキャンまで確実に保護され、[新しいファイルを既定で重要なものとし](https://docs.microsoft.com/sharepoint/sensitive-by-default)てマークすることにより、安全であるとマークされるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="d936c-196">You can ensure that documents are protected until DLP scans and marks them as safe to share by [marking new files as sensitive by default](https://docs.microsoft.com/sharepoint/sensitive-by-default)</span></span>
- <span data-ttu-id="d936c-197">推奨される DLP ポリシー構造</span><span class="sxs-lookup"><span data-stu-id="d936c-197">Recommended DLP policy structure</span></span>
    - <span data-ttu-id="d936c-198">**条件**</span><span class="sxs-lookup"><span data-stu-id="d936c-198">**Conditions**</span></span>
        - <span data-ttu-id="d936c-199">コンテンツには、次の機密情報の種類のいずれかが含まれています。 [適用するすべてを選択する]</span><span class="sxs-lookup"><span data-stu-id="d936c-199">Content contains any of these sensitive information types: [Select all that applies]</span></span>
        - <span data-ttu-id="d936c-200">コンテンツは Microsoft 365 から、自分の組織外のユーザーと共有される</span><span class="sxs-lookup"><span data-stu-id="d936c-200">Content is shared from Microsoft 365 with people outside my organization</span></span>
        <br/><span data-ttu-id="d936c-201">![機密コンテンツの外部共有を検出する DLP 条件](../media/dlp-teams-external-sharing/external-condition.png)</span><span class="sxs-lookup"><span data-stu-id="d936c-201">![DLP conditions to detect external sharing of sensitive content](../media/dlp-teams-external-sharing/external-condition.png)</span></span><br/>


    - <span data-ttu-id="d936c-202">**アクション**</span><span class="sxs-lookup"><span data-stu-id="d936c-202">**Actions**</span></span>
        - <span data-ttu-id="d936c-203">外部ユーザーのコンテンツへのアクセスを制限する</span><span class="sxs-lookup"><span data-stu-id="d936c-203">Restrict access to the content for external users</span></span>
        - <span data-ttu-id="d936c-204">ユーザーに電子メールとポリシーヒントを通知する</span><span class="sxs-lookup"><span data-stu-id="d936c-204">Notify users with email and policy tips</span></span>
        - <span data-ttu-id="d936c-205">インシデントレポートを管理者に送信する</span><span class="sxs-lookup"><span data-stu-id="d936c-205">Send incident reports to the Administrator</span></span>    
        <br/>![機密コンテンツの外部共有をブロックする DLP アクション](../media/dlp-teams-external-sharing/external-action.png)<br/>

<span data-ttu-id="d936c-207">次に示す、外部ゲストの機密情報を含む SharePoint のドキュメントを共有しようとした場合の DLP ポリシー。</span><span class="sxs-lookup"><span data-stu-id="d936c-207">DLP policy in action when attempting to share a document in SharePoint that contains sensitive information with an external guest:</span></span>
<br/><span data-ttu-id="d936c-208">![外部共有のブロック](../media/dlp-teams-external-sharing/external-sharing-blocked.png)</span><span class="sxs-lookup"><span data-stu-id="d936c-208">![External sharing blocked](../media/dlp-teams-external-sharing/external-sharing-blocked.png)</span></span><br/>


<span data-ttu-id="d936c-209">[外部ブロック] を持つ Teams でゲストがドキュメントを開こうとした場合の DLP ポリシーの動作:</span><span class="sxs-lookup"><span data-stu-id="d936c-209">DLP policy in action when guest attempts to open a document in Teams with block external:</span></span>
<br/><span data-ttu-id="d936c-210">![外部アクセスのブロック](../media/dlp-teams-external-sharing/external-access-blocked.png)</span><span class="sxs-lookup"><span data-stu-id="d936c-210">![External access blocked](../media/dlp-teams-external-sharing/external-access-blocked.png)</span></span><br/>

## <a name="related-articles"></a><span data-ttu-id="d936c-211">関連記事</span><span class="sxs-lookup"><span data-stu-id="d936c-211">Related articles</span></span>

[<span data-ttu-id="d936c-212">DLP ポリシーの作成、テスト、調整</span><span class="sxs-lookup"><span data-stu-id="d936c-212">Create, test, and tune a DLP policy</span></span>](create-test-tune-dlp-policy.md)

[<span data-ttu-id="d936c-213">メール通知を送信して、DLP ポリシーのヒントを表示する</span><span class="sxs-lookup"><span data-stu-id="d936c-213">Send email notifications and show policy tips for DLP policies</span></span>](use-notifications-and-policy-tips.md)
