---
title: ユーザー送信ポリシー
f1.keywords:
- NOCSH
ms.author: siosulli
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: 管理者は、ユーザーによって報告されたスパムやフィッシング電子メールを収集するようにメールボックスを構成する方法について説明します。
ms.openlocfilehash: 7064e2d26722c433d33fe2f983484a40fa33c1e6
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "49615626"
---
# <a name="user-submissions-policy"></a><span data-ttu-id="5f36d-103">ユーザー送信ポリシー</span><span class="sxs-lookup"><span data-stu-id="5f36d-103">User submissions policy</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


<span data-ttu-id="5f36d-104">Exchange Online メールボックスを使用している Microsoft 365 組織では、ユーザーが悪意のあるメールや悪意のないメッセージを受信するメールボックスを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="5f36d-104">In Microsoft 365 organizations with Exchange Online mailboxes, you can specify a mailbox to receive messages that users report as malicious or not malicious.</span></span> <span data-ttu-id="5f36d-105">ユーザーがさまざまなレポートオプションを使用してメッセージを送信する場合、このメールボックスを使用して、メッセージを傍受する (カスタムメールボックスにのみ送信する) か、メッセージのコピーを受信する (カスタムメールボックスおよび Microsoft に送信) ことができます。</span><span class="sxs-lookup"><span data-stu-id="5f36d-105">When users submit messages using the various reporting options, you can use this mailbox to intercept messages (send to the custom mailbox only) or receive copies of messages (send to the custom mailbox and Microsoft).</span></span> <span data-ttu-id="5f36d-106">この機能は、次のメッセージレポートオプションで機能します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-106">This feature works with the following message reporting options:</span></span>

- [<span data-ttu-id="5f36d-107">レポートメッセージアドイン</span><span class="sxs-lookup"><span data-stu-id="5f36d-107">The Report Message add-in</span></span>](enable-the-report-message-add-in.md)

- <span data-ttu-id="5f36d-108">[Web 上の outlook](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md) (旧称 Outlook web App) での組み込みレポート</span><span class="sxs-lookup"><span data-stu-id="5f36d-108">[Built-in reporting in Outlook on the web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md) (formerly known as Outlook Web App)</span></span>

- [<span data-ttu-id="5f36d-109">IOS および Android 用の Outlook の組み込みレポート</span><span class="sxs-lookup"><span data-stu-id="5f36d-109">Built-in reporting in Outlook for iOS and Android</span></span>](report-junk-email-and-phishing-scams-in-outlook-for-iOS-and-Android.md)

  > [!NOTE]
  > <span data-ttu-id="5f36d-110">[Web 上の outlook で](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web)レポートが無効になっている場合、ここでユーザーによる送信を有効にすると、その設定が無効になり、ユーザーは web 上の outlook でメッセージを再度レポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="5f36d-110">If reporting has been [disabled in Outlook on the web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web), enabling user submissions here will override that setting and enable users to report messages in Outlook on the web again.</span></span>

<span data-ttu-id="5f36d-111">また、指定したメールボックスにメッセージを転送するように、サードパーティ製のメッセージレポートツールを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="5f36d-111">You can also configure third-party message reporting tools to forward messages to the mailbox that you specify.</span></span>

<span data-ttu-id="5f36d-112">ユーザーが報告したメッセージを Microsoft に直接送信する代わりにカスタムメールボックスに配信することにより、管理者は、 [管理者送信](admin-submission.md)を使用してメッセージを選択的に、手動で microsoft に報告できます。</span><span class="sxs-lookup"><span data-stu-id="5f36d-112">Delivering user reported messages to a custom mailbox instead of directly to Microsoft allows your admins to selectively and manually report messages to Microsoft using [Admin submission](admin-submission.md).</span></span>

## <a name="custom-mailbox-prerequisites"></a><span data-ttu-id="5f36d-113">カスタムメールボックスの前提条件</span><span class="sxs-lookup"><span data-stu-id="5f36d-113">Custom mailbox prerequisites</span></span>

<span data-ttu-id="5f36d-114">次の記事を使用して、ユーザーがレポートされたメッセージをカスタムメールボックスに移動するために必要な前提条件を構成します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-114">Use the following articles to configure the prerequisites required so user reported messages go to your custom mailbox:</span></span>

- <span data-ttu-id="5f36d-115">スパム信頼レベルを設定する exchange メールフロールールを作成して、カスタムメールボックスでスパムフィルター処理をスキップします。</span><span class="sxs-lookup"><span data-stu-id="5f36d-115">Skip spam filtering on the custom mailbox by creating an exchange mail flow rule to set the spam confidence level.</span></span> <span data-ttu-id="5f36d-116">SCL を **-1** に設定する [メッセージの scl を設定するメールフロールールを作成するには、EAC を使用](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md#use-the-eac-to-create-a-mail-flow-rule-that-sets-the-scl-of-a-message)してください。</span><span class="sxs-lookup"><span data-stu-id="5f36d-116">See [Use the EAC to create a mail flow rule that sets the SCL of a message](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md#use-the-eac-to-create-a-mail-flow-rule-that-sets-the-scl-of-a-message) to set the SCL to **-1**.</span></span>

- <span data-ttu-id="5f36d-117">カスタムメールボックス内のマルウェアの添付ファイルのスキャンを無効にします。</span><span class="sxs-lookup"><span data-stu-id="5f36d-117">Turn off scanning attachments for malware in the custom mailbox.</span></span> <span data-ttu-id="5f36d-118">「 [Set Up Safe attachments policy In Defender In Office 365」](set-up-atp-safe-attachments-policies.md)を使用して、「**安全な添付ファイルの不明なマルウェア応答** の設定を **オフ** にした安全な添付ファイルのポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-118">Use [Set up Safe Attachments policies in Defender for Office 365](set-up-atp-safe-attachments-policies.md) to create a Safe Attachments policy with the setting **Off** for **Safe Attachments unknown malware response**.</span></span>

- <span data-ttu-id="5f36d-119">カスタムメールボックス内のメッセージに対する URL スキャンを無効にします。</span><span class="sxs-lookup"><span data-stu-id="5f36d-119">Turn off URL scanning on messages in the custom mailbox.</span></span> <span data-ttu-id="5f36d-120">「 [Set Up Safe links policy In Office 365」](set-up-atp-safe-links-policies.md)を使用して安全リンクポリシーを作成し 、 **[メッセージ内の不明な悪意のある Url に対するアクションを選択** します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-120">Use [Set up Safe Links policies in Defender for Office 365](set-up-atp-safe-links-policies.md) to create a Safe Links policy with the setting **Off** for **Select the action for unknown potentially malicious URLs in messages**.</span></span>

- <span data-ttu-id="5f36d-121">マルウェア対策ポリシーを作成して、マルウェアのゼロ時間の自動削除を無効にします。</span><span class="sxs-lookup"><span data-stu-id="5f36d-121">Create an anti-malware policy to turn off Malware Zero-hour Auto Purge.</span></span> <span data-ttu-id="5f36d-122">**マルウェアのゼロ時間自動削除** を **オフ** に設定するに [は、「セキュリティ & コンプライアンスセンターを使用してマルウェア対策ポリシーを作成する」を](configure-your-spam-filter-policies.md#use-the-security--compliance-center-to-create-anti-spam-policies)参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f36d-122">See [Use the Security & Compliance Center to create anti-malware policies](configure-your-spam-filter-policies.md#use-the-security--compliance-center-to-create-anti-spam-policies) to set **Malware Zero-hour Auto Purge** to **Off**.</span></span>

- <span data-ttu-id="5f36d-123">スパムフィルターポリシーを作成して、カスタムメールボックスでスパムおよびフィッシングのゼロ時間自動削除 (ZAP) を無効にします。</span><span class="sxs-lookup"><span data-stu-id="5f36d-123">Create a spam filter policy to disable zero-hour auto purge (ZAP) for spam and phishing in the custom mailbox.</span></span> <span data-ttu-id="5f36d-124">「[セキュリティ & コンプライアンスセンターを使用](configure-your-spam-filter-policies.md#use-the-security--compliance-center-to-create-anti-spam-policies)してスパム対策ポリシーを作成し、**スパム ZAP** および **フィッシング ZAP\*\*\*\*のチェックボックス** をオフにする」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f36d-124">See [Use the Security & Compliance Center to create anti-spam policies](configure-your-spam-filter-policies.md#use-the-security--compliance-center-to-create-anti-spam-policies) and clear the **On** checkboxes for **Spam ZAP** and **Phish ZAP**.</span></span>

- <span data-ttu-id="5f36d-125">カスタムメールボックスで迷惑メールルールを無効にします。</span><span class="sxs-lookup"><span data-stu-id="5f36d-125">Disable the junk email rule in the custom mailbox.</span></span> <span data-ttu-id="5f36d-126">迷惑メールルールを無効にするには、 [Exchange Online メールボックスで迷惑メールの設定を構成](configure-junk-email-settings-on-exo-mailboxes.md) します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-126">Use [Configure junk email settings on Exchange Online mailboxes](configure-junk-email-settings-on-exo-mailboxes.md) to disable the junk email rule.</span></span> <span data-ttu-id="5f36d-127">無効にした場合、EOP は、迷惑メールフォルダーにメッセージを移動することはできません verdict アクションによる迷惑メール **フォルダーへのメッセージの移動** またはメールボックス上のセーフリストコレクションへのメッセージの移動。</span><span class="sxs-lookup"><span data-stu-id="5f36d-127">Once disabled, EOP can't move messages to the Junk Email folder based on the spam filtering verdict action **Move message to Junk Email folder** or the safelist collection on the mailbox.</span></span>

<span data-ttu-id="5f36d-128">メールボックスが適用可能なすべての前提条件を満たしていることを確認したら、 [セキュリティ & コンプライアンスセンターを使用して、ユーザー送信メールボックスを構成](#use-the-security--compliance-center-to-configure-the-user-submissions-mailbox) します (この記事で説明します)。</span><span class="sxs-lookup"><span data-stu-id="5f36d-128">After you've verified that your mailbox meets all applicable prerequisites, [Use the Security & Compliance Center to configure the user submissions mailbox](#use-the-security--compliance-center-to-configure-the-user-submissions-mailbox) (in this article).</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="5f36d-129">はじめに把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="5f36d-129">What do you need to know before you begin?</span></span>

- <span data-ttu-id="5f36d-130"><https://protection.office.com/> でセキュリティ/コンプライアンス センターを開きます。</span><span class="sxs-lookup"><span data-stu-id="5f36d-130">You open the Security & Compliance Center at <https://protection.office.com/>.</span></span> <span data-ttu-id="5f36d-131">[ **ユーザーの送信** ] ページに直接移動するには、を使用 <https://protection.office.com/userSubmissionsReportMessage> します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-131">To go directly to the **User submissions** page, use <https://protection.office.com/userSubmissionsReportMessage>.</span></span>

- <span data-ttu-id="5f36d-132">ユーザー送信の構成を変更するには、次のいずれかの役割グループのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f36d-132">To modify the configuration for User submissions, you need to be a member of one of the following role groups:</span></span>

  - <span data-ttu-id="5f36d-133">**組織の管理** または [セキュリティ/コンプライアンス センター](permissions-in-the-security-and-compliance-center.md)の **セキュリティ管理者**。</span><span class="sxs-lookup"><span data-stu-id="5f36d-133">**Organization Management** or **Security Administrator** in the [Security & Compliance Center](permissions-in-the-security-and-compliance-center.md).</span></span>
  - <span data-ttu-id="5f36d-134">[Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups)での **組織の管理**。</span><span class="sxs-lookup"><span data-stu-id="5f36d-134">**Organization Management** in [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups).</span></span>

## <a name="use-the-security--compliance-center-to-configure-the-user-submissions-mailbox"></a><span data-ttu-id="5f36d-135">セキュリティ & コンプライアンスセンターを使用してユーザー送信メールボックスを構成する</span><span class="sxs-lookup"><span data-stu-id="5f36d-135">Use the Security & Compliance Center to configure the user submissions mailbox</span></span>

1. <span data-ttu-id="5f36d-136">[セキュリティ & コンプライアンスセンター] で、[**脅威管理** ポリシーのユーザーの送信] に移動 \>  \> します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-136">In the Security & Compliance Center, go to **Threat management** \> **Policy** \> **User submissions**.</span></span>

2. <span data-ttu-id="5f36d-137">表示される [ **ユーザーの送信** ] ページで、次のいずれかのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-137">In the **User submissions** page that appears, select one of the following options:</span></span>

   1. <span data-ttu-id="5f36d-138">**Outlook のレポートメッセージ機能を有効にする (推奨)**: レポートメッセージアドインまたは outlook on the web の組み込みのレポートを使用して、次の設定を構成する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-138">**Enable the Report Message feature for Outlook (Recommended)**: Select this option if you use the Report Message add-in or the built-in reporting in Outlook on the web, and then configure the following settings:</span></span>

      - <span data-ttu-id="5f36d-139">**エンドユーザーの確認メッセージをカスタマイズする**: このリンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f36d-139">**Customize the end-user confirmation message**: Click this link.</span></span> <span data-ttu-id="5f36d-140">[ **確認メッセージのカスタマイズ** ] ポップアップが表示されたら、次の設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-140">In the **Customize confirmation message** flyout that appears, configure the following settings:</span></span>

      - <span data-ttu-id="5f36d-141">**提出前**: **タイトル** と確認の **メッセージ** ボックスに、レポートメッセージアドインを使用してメッセージを報告する前にユーザーに表示される説明テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-141">**Before submission**: In the **Title** and **Confirmation message** boxes, enter the descriptive text that users see before they report a message using the Report Message add-in.</span></span> <span data-ttu-id="5f36d-142">変数% 型% を使用して、送信の種類 (迷惑メール、迷惑メールではない、フィッシングなど) を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="5f36d-142">You can use the variable %type% to include the submission type (junk, not junk, phish, etc.).</span></span>

        <span data-ttu-id="5f36d-143">前述したように、報告されたメッセージを Microsoft に送信するオプションを選択すると、通知に次のテキストも追加されます。</span><span class="sxs-lookup"><span data-stu-id="5f36d-143">As noted, if you select an option that sends the reported messages to Microsoft, the following text is also added to the notification:</span></span>

        > <span data-ttu-id="5f36d-144">電子メールは、のように、分析のために Microsoft に提出されます。</span><span class="sxs-lookup"><span data-stu-id="5f36d-144">Your email will be submitted as-is to Microsoft for analysis.</span></span> <span data-ttu-id="5f36d-145">メールによっては個人情報や機密情報が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5f36d-145">Some emails might contain personal or sensitive information.</span></span>

      - <span data-ttu-id="5f36d-146">**送信後**: [ ![ 展開] アイコンをクリックし ](../../media/scc-expand-icon.png) ます。</span><span class="sxs-lookup"><span data-stu-id="5f36d-146">**After submission**: Click ![Expand icon](../../media/scc-expand-icon.png).</span></span> <span data-ttu-id="5f36d-147">[ **タイトル** ] および [ **確認メッセージ** ] ボックスに、レポートメッセージアドインを使用してメッセージを報告した後にユーザーに表示される説明テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-147">In the **Title** and **Confirmation message** boxes, enter the descriptive text that users see after they report a message using the Report Message add-in.</span></span> <span data-ttu-id="5f36d-148">変数% 型% を使用して、提出の種類を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="5f36d-148">You can use the variable %type% to include the submission type.</span></span>

      <span data-ttu-id="5f36d-149">完了したら、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f36d-149">When you're finished, click **Save**.</span></span> <span data-ttu-id="5f36d-150">これらの値をクリアするには、[**ユーザーの送信**] ページの [元に **戻す**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f36d-150">To clear these values, click **Restore** back on the **User submissions** page.</span></span>

      - <span data-ttu-id="5f36d-151">**報告されたメッセージの送信先**: 次のいずれかの選択を行います。</span><span class="sxs-lookup"><span data-stu-id="5f36d-151">**Send the reported messages to**: Make one of the following selections:</span></span>

        - <span data-ttu-id="5f36d-152">**Microsoft (推奨)**: ユーザーの送信メールボックスが使用されていません (報告されたすべてのメッセージが Microsoft に送られます)。</span><span class="sxs-lookup"><span data-stu-id="5f36d-152">**Microsoft (Recommended)**: The user submissions mailbox isn't used (all reported messages go to Microsoft).</span></span>

        - <span data-ttu-id="5f36d-153">**Microsoft およびカスタムメールボックス**: 表示されるボックスに、既存の Exchange Online メールボックスの電子メールアドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-153">**Microsoft and a custom mailbox**: In the box that appears, enter the email address of an existing Exchange Online mailbox.</span></span> <span data-ttu-id="5f36d-154">配布グループは許可されていません。</span><span class="sxs-lookup"><span data-stu-id="5f36d-154">Distribution groups are not allowed.</span></span> <span data-ttu-id="5f36d-155">ユーザーによる送信は、分析のために Microsoft と Microsoft の両方に、管理者またはセキュリティ運用チームのためのカスタムメールボックスに移動します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-155">User submissions will go to both Microsoft for analysis and to the custom mailbox for your admin or security operations team to analyze.</span></span>

        - <span data-ttu-id="5f36d-156">**カスタムメールボックス**: 表示されるボックスに、既存の Exchange Online メールボックスの電子メールアドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-156">**Custom mailbox**: In the box that appears, enter the email address of an existing Exchange Online mailbox.</span></span> <span data-ttu-id="5f36d-157">配布グループは許可されていません。</span><span class="sxs-lookup"><span data-stu-id="5f36d-157">Distribution groups are not allowed.</span></span> <span data-ttu-id="5f36d-158">このオプションを使用するのは、最初に分析のために管理者またはセキュリティ操作チームのみにメッセージを移動する場合です。</span><span class="sxs-lookup"><span data-stu-id="5f36d-158">Use this option if you want the message to only go to an admin or the security operations team for analysis first.</span></span> <span data-ttu-id="5f36d-159">管理者が自分を転送しない限り、メッセージは Microsoft には送られません。</span><span class="sxs-lookup"><span data-stu-id="5f36d-159">Messages will not go to Microsoft unless the admin forwards it themselves.</span></span>

        > [!NOTE]
        > <span data-ttu-id="5f36d-160">米国政府機関 (GCC、GCC、.H、DoD) は、 **カスタムメールボックス** のみを構成できます。</span><span class="sxs-lookup"><span data-stu-id="5f36d-160">U.S. Government organizations (GCC, GCC-H, and DoD) can only configure **Custom mailbox**.</span></span> <span data-ttu-id="5f36d-161">他の2つのオプションは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="5f36d-161">The other two options are disabled.</span></span>

      <span data-ttu-id="5f36d-162">完了したら、[ **確認**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f36d-162">When you're finished, click **Confirm**.</span></span>

      > [!CAUTION]
      > <span data-ttu-id="5f36d-163">Web 上の outlook on the web メールボックスポリシーを使用して outlook の [迷惑メール報告を無効](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) にしたが、microsoft にメッセージを報告するために以前の設定のいずれかを構成した場合、ユーザーはレポートメッセージアドインを使用して、web 上の outlook でメッセージを microsoft に報告できます。</span><span class="sxs-lookup"><span data-stu-id="5f36d-163">If you have [disabled junk email reporting in Outlook on the web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) using Outlook on the web mailbox policies, but you configure either of the previous settings to report messages to Microsoft, users will be able to report messages to Microsoft in Outlook on the web using the Report Message add-in.</span></span>

   - <span data-ttu-id="5f36d-164">**Outlook のレポートメッセージ機能を無効に** する: レポートメッセージアドインまたは web 上の Outlook の組み込みレポートではなくサードパーティのレポートツールを使用し、次の設定を構成する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-164">**Disable the Report Message feature for Outlook**: Select this option if you use third-party reporting tools instead of the Report Message add-in or the built-in reporting in Outlook on the web, and then configure the following settings:</span></span>

      <span data-ttu-id="5f36d-165">[ **このカスタムメールボックスを使用して、ユーザーが報告した送信を受信する**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-165">Select **Use this custom mailbox to receive user reported submissions**.</span></span> <span data-ttu-id="5f36d-166">表示されるボックスに、Office 365 に既に存在する既存のメールボックスの電子メールアドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-166">In the box that appears, enter the email address of an existing mailbox that is already in Office 365.</span></span> <span data-ttu-id="5f36d-167">これは、電子メールを受信できる Exchange Online の既存のメールボックスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f36d-167">This has to be an existing mailbox in Exchange Online that can receive email.</span></span>

      <span data-ttu-id="5f36d-168">完了したら、[ **確認**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5f36d-168">When you're finished, click **Confirm**.</span></span>

## <a name="message-submission-format"></a><span data-ttu-id="5f36d-169">メッセージ送信形式</span><span class="sxs-lookup"><span data-stu-id="5f36d-169">Message submission format</span></span>

<span data-ttu-id="5f36d-170">カスタムメールボックスに送信されるメッセージは、特定の送信メール形式に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f36d-170">Messages sent to custom mailboxes need to follow a specific submission mail format.</span></span> <span data-ttu-id="5f36d-171">提出物の件名 (封筒のタイトル) は、次の形式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f36d-171">The Subject (Envelope Title) of the submission should be in this format:</span></span>

`SafetyAPIAction|NetworkMessageId|SenderIp|FromAddress|(Message Subject)`

<span data-ttu-id="5f36d-172">この例では、Saf Etyapiaction は次の整数値のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="5f36d-172">where SafetyAPIAction is one of the following integer values:</span></span>

- <span data-ttu-id="5f36d-173">1: 迷惑メール</span><span class="sxs-lookup"><span data-stu-id="5f36d-173">1: Junk</span></span>
- <span data-ttu-id="5f36d-174">2: 迷惑メールではない</span><span class="sxs-lookup"><span data-stu-id="5f36d-174">2: Not junk</span></span>
- <span data-ttu-id="5f36d-175">3: フィッシング</span><span class="sxs-lookup"><span data-stu-id="5f36d-175">3: Phishing</span></span>

<span data-ttu-id="5f36d-176">次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="5f36d-176">In the following example:</span></span>

- <span data-ttu-id="5f36d-177">メッセージはフィッシングとして報告されています。</span><span class="sxs-lookup"><span data-stu-id="5f36d-177">The message is being reported as phishing.</span></span>
- <span data-ttu-id="5f36d-178">ネットワークメッセージ ID は49871234-6dc6-43e8-abcd-08d797f20abe です。</span><span class="sxs-lookup"><span data-stu-id="5f36d-178">The Network Message ID is 49871234-6dc6-43e8-abcd-08d797f20abe.</span></span>
- <span data-ttu-id="5f36d-179">送信者の IP は167.220.232.101 です。</span><span class="sxs-lookup"><span data-stu-id="5f36d-179">The Sender IP is 167.220.232.101.</span></span>
- <span data-ttu-id="5f36d-180">From アドレスは test@contoso.com です。</span><span class="sxs-lookup"><span data-stu-id="5f36d-180">The From address is test@contoso.com.</span></span>
- <span data-ttu-id="5f36d-181">メッセージの件名行は "テストフィッシング発信" です。</span><span class="sxs-lookup"><span data-stu-id="5f36d-181">The message's subject line is "test phishing submission"</span></span>

`3|49871234-6dc6-43e8-abcd-08d797f20abe|167.220.232.101|test@contoso.com|(test phishing submission)`

<span data-ttu-id="5f36d-182">この形式に従っていないメッセージは、送信ポータルで適切に表示されません。</span><span class="sxs-lookup"><span data-stu-id="5f36d-182">Messages that do not follow this format will not display properly in the Submissions portal.</span></span>
