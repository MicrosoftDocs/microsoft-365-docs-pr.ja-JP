---
title: メール フロー ルールを使用してバルク メールをフィルター処理する
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 2889c82e-fab0-4e85-87b0-b001b2ccd4f7
ms.collection:
- M365-security-compliance
description: 管理者は、Exchange Online Protection (EOP) でメール フロー ルール (トランスポート ルール) を使用してバルク メール (グレー メール) を識別してフィルター処理する方法について学習できます。
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c86f229d6c7371854878a67937cc38374ed00961
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "51206070"
---
# <a name="use-mail-flow-rules-to-filter-bulk-email-in-eop"></a><span data-ttu-id="f0d27-103">メール フロー ルールを使用して EOP でバルク メールをフィルタリングする</span><span class="sxs-lookup"><span data-stu-id="f0d27-103">Use mail flow rules to filter bulk email in EOP</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

<span data-ttu-id="f0d27-104">**適用対象**</span><span class="sxs-lookup"><span data-stu-id="f0d27-104">**Applies to**</span></span>
- [<span data-ttu-id="f0d27-105">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="f0d27-105">Exchange Online Protection</span></span>](exchange-online-protection-overview.md)
- [<span data-ttu-id="f0d27-106">Microsoft Defender for Office 365 プラン 1 およびプラン 2</span><span class="sxs-lookup"><span data-stu-id="f0d27-106">Microsoft Defender for Office 365 plan 1 and plan 2</span></span>](defender-for-office-365.md)
- [<span data-ttu-id="f0d27-107">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="f0d27-107">Microsoft 365 Defender</span></span>](../defender/microsoft-365-defender.md)

<span data-ttu-id="f0d27-108">Exchange Online または Exchange Online メールボックスのないスタンドアロン Exchange Online Protection (EOP) 組織のメールボックスを持つ Microsoft 365 組織では、EOP はスパム対策ポリシー (スパム フィルター ポリシーまたはコンテンツ フィルター ポリシーとも呼ばれる) を使用して、受信メッセージをスキャンしてスパムやバルク メール (グレー メールとも呼ばれる) をスキャンします。</span><span class="sxs-lookup"><span data-stu-id="f0d27-108">In Microsoft 365 organizations with mailboxes in Exchange Online or standalone Exchange Online Protection (EOP) organizations without Exchange Online mailboxes, EOP uses anti-spam policies (also known as spam filter policies or content filter policies) to scan inbound messages for spam and bulk mail (also known as gray mail).</span></span> <span data-ttu-id="f0d27-109">詳細については、「[EOP でのスパム対策ポリシーの構成](configure-your-spam-filter-policies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0d27-109">For more information, see [Configure anti-spam policies in EOP](configure-your-spam-filter-policies.md).</span></span>

<span data-ttu-id="f0d27-110">バルク メールをフィルター処理するオプションを増やしたい場合は、メール フロー ルール (トランスポート ルールとも呼ばれる) を作成して、バルク メールで頻繁に見られるテキスト パターンや語句を検索し、それらのメッセージをスパムとしてマークできます。</span><span class="sxs-lookup"><span data-stu-id="f0d27-110">If you want more options to filter bulk mail, you can create mail flow rules (also known as transport rules) to search for text patterns or phrases that are frequently found in bulk mail, and mark those messages as spam.</span></span> <span data-ttu-id="f0d27-111">バルク メールの詳細については [、「EOP](what-s-the-difference-between-junk-email-and-bulk-email.md) の迷惑メールとバルク メールの違い」および「バルク 苦情レベル [(BCL)」を参照してください](bulk-complaint-level-values.md)。</span><span class="sxs-lookup"><span data-stu-id="f0d27-111">For more information about bulk mail, see [What's the difference between junk email and bulk email?](what-s-the-difference-between-junk-email-and-bulk-email.md) and [Bulk complaint level (BCL) in EOP](bulk-complaint-level-values.md).</span></span>

<span data-ttu-id="f0d27-112">このトピックでは、Exchange 管理センター (EAC) および PowerShell (Exchange Online のメールボックスを持つ Microsoft 365 組織向け Exchange Online PowerShell、Exchange Online メールボックスのない組織のスタンドアロン EOP PowerShell) でこれらのメール フロー ルールを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f0d27-112">This topic explains how create these mail flow rules in the Exchange admin center (EAC) and PowerShell (Exchange Online PowerShell for Microsoft 365 organizations with mailboxes in Exchange Online; standalone EOP PowerShell for organizations without Exchange Online mailboxes).</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="f0d27-113">始める前に把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="f0d27-113">What do you need to know before you begin?</span></span>

- <span data-ttu-id="f0d27-114">この記事の手順を実行するには、Exchange Online または Exchange Online Protection でアクセス許可を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0d27-114">You need to be assigned permissions in Exchange Online or Exchange Online Protection before you can do the procedures in this article.</span></span> <span data-ttu-id="f0d27-115">具体的には、既定では、組織の管理、コンプライアンス管理 **(グローバル** 管理者)、レコード管理の役割グループに割り当てられているトランスポート ルールの役割が必要です。 </span><span class="sxs-lookup"><span data-stu-id="f0d27-115">Specifically, you need the **Transport Rules** role, which is assigned to the **Organization Management**, **Compliance Management** (global admins), and **Records Management** role groups by default.</span></span>

  <span data-ttu-id="f0d27-116">詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f0d27-116">For more information, see the following topics:</span></span>

  - [<span data-ttu-id="f0d27-117">Exchange Online のアクセス許可</span><span class="sxs-lookup"><span data-stu-id="f0d27-117">Permissions in Exchange Online</span></span>](/exchange/permissions-exo/permissions-exo)
  - [<span data-ttu-id="f0d27-118">スタンドアロン EOP のアクセス許可</span><span class="sxs-lookup"><span data-stu-id="f0d27-118">Permissions in standalone EOP</span></span>](feature-permissions-in-eop.md)
  - [<span data-ttu-id="f0d27-119">役割グループ内のメンバーの一覧を変更する EAC を使用する</span><span class="sxs-lookup"><span data-stu-id="f0d27-119">Use the EAC modify the list of members in role groups</span></span>](manage-admin-role-group-permissions-in-eop.md#use-the-eac-modify-the-list-of-members-in-role-groups)

- <span data-ttu-id="f0d27-120">Exchange Online で EAC を開く方法については、「Exchange Online [の Exchange 管理センター」を参照してください](/Exchange/exchange-admin-center)。</span><span class="sxs-lookup"><span data-stu-id="f0d27-120">To open the EAC in Exchange Online, see [Exchange admin center in Exchange Online](/Exchange/exchange-admin-center).</span></span> <span data-ttu-id="f0d27-121">スタンドアロン EOP で EAC を開く方法については、「 [スタンドアロン EOP の Exchange 管理センター」を参照してください](exchange-admin-center-in-exchange-online-protection-eop.md)。</span><span class="sxs-lookup"><span data-stu-id="f0d27-121">To open the EAC in standalone EOP, see [Exchange admin center in standalone EOP](exchange-admin-center-in-exchange-online-protection-eop.md).</span></span>

- <span data-ttu-id="f0d27-122">Exchange Online PowerShell へ接続するには、「[Exchange Online PowerShell に接続する](/powershell/exchange/connect-to-exchange-online-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0d27-122">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).</span></span> <span data-ttu-id="f0d27-123">スタンドアロンの EOP PowerShell に接続するには、「[Exchange Online Protection PowerShell への接続](/powershell/exchange/connect-to-exchange-online-protection-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0d27-123">To connect to standalone EOP PowerShell, see [Connect to Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).</span></span>

- <span data-ttu-id="f0d27-124">Exchange Online およびスタンドアロン EOP のメール フロー ルールの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0d27-124">For more information about mail flow rules in Exchange Online and standalone EOP, see the following topics:</span></span>

  - [<span data-ttu-id="f0d27-125">Exchange Online のメール フロー ルール (トランスポート ルール)</span><span class="sxs-lookup"><span data-stu-id="f0d27-125">Mail flow rules (transport rules) in Exchange Online</span></span>](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)

  - [<span data-ttu-id="f0d27-126">Exchange Online のメール フロー ルールでの条件と例外 (述語)</span><span class="sxs-lookup"><span data-stu-id="f0d27-126">Mail flow rule conditions and exceptions (predicates) in Exchange Online</span></span>](/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions)

  - [<span data-ttu-id="f0d27-127">Exchange Online でのメール フロー ルールの処理</span><span class="sxs-lookup"><span data-stu-id="f0d27-127">Mail flow rule actions in Exchange Online</span></span>](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions)

- <span data-ttu-id="f0d27-128">例のバルク メールを識別するために使用される単語とテキスト パターンの一覧は、網羅的ではありません。必要に応じてエントリを追加および削除できます。</span><span class="sxs-lookup"><span data-stu-id="f0d27-128">The list of words and text patterns that are used to identify bulk mail in the examples aren't exhaustive; you can add and remove entries as necessary.</span></span> <span data-ttu-id="f0d27-129">ただし、これらは良い開始点です。</span><span class="sxs-lookup"><span data-stu-id="f0d27-129">However, they are a good starting point.</span></span>

- <span data-ttu-id="f0d27-p107">メッセージ内の件名または他のヘッダー フィールドでの単語またはテキスト パターンの検索は、SMTP サーバー間で ASCII テキスト内のバイナリ メッセージ送信に使用された MIME コンテンツ転送エンコーディング方式に基づいてメッセージがデコードされた *後* に行われます。条件または例外を使用して、メッセージ内の件名または他のヘッダー フィールドの未加工 (通常は Base64) のエンコード値を検索することはできません。</span><span class="sxs-lookup"><span data-stu-id="f0d27-p107">The search for words or text patterns in the subject or other header fields in the message occurs *after* the message has been decoded from the MIME content transfer encoding method that was used to transmit the binary message between SMTP servers in ASCII text. You can't use conditions or exceptions to search for the raw (typically, Base64) encoded values of the subject or other header fields in messages.</span></span>

- <span data-ttu-id="f0d27-132">次の手順では、バルク メッセージを組織全体のスパムとしてマークします。</span><span class="sxs-lookup"><span data-stu-id="f0d27-132">The following procedures mark a bulk message as spam for your entire organization.</span></span> <span data-ttu-id="f0d27-133">ただし、別の条件を追加して、これらのルールを特定の受信者にのみ適用できます。そのため、ターゲットが高い少数のユーザーに対して積極的なフィルター処理を使用できます。残りのユーザー (主にサインアップした一括メールを取得するユーザー) は影響を受け取らない。</span><span class="sxs-lookup"><span data-stu-id="f0d27-133">However, you can add another condition to apply these rules only to specific recipients, so you can use aggressive filtering on a few, highly targeted users, while the rest of your users (who mostly get the bulk email they signed up for) aren't impacted.</span></span>

## <a name="use-the-eac-to-create-mail-flow-rules-that-filter-bulk-email"></a><span data-ttu-id="f0d27-134">EAC を使用して、バルク メールをフィルター処理するメール フロー ルールを作成する</span><span class="sxs-lookup"><span data-stu-id="f0d27-134">Use the EAC to create mail flow rules that filter bulk email</span></span>

1. <span data-ttu-id="f0d27-135">EAC で、 **[メール フロー]** \> **[ルール]** に移動します。</span><span class="sxs-lookup"><span data-stu-id="f0d27-135">In the EAC, go to **Mail flow** \> **Rules**.</span></span>

2. <span data-ttu-id="f0d27-136">[追加 **] アイコン** ![ をクリックし ](../../media/ITPro-EAC-AddIcon.png) 、[新しいルール **の作成] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="f0d27-136">Click **Add** ![Add icon](../../media/ITPro-EAC-AddIcon.png) and then select **Create a new rule**.</span></span>

3. <span data-ttu-id="f0d27-137">**[新しいルール]** のページが開いたら、以下の設定を行ってください:</span><span class="sxs-lookup"><span data-stu-id="f0d27-137">In the **New rule** page that opens, configure the following settings:</span></span>

   - <span data-ttu-id="f0d27-138">**名前**: ルールの一意でわかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f0d27-138">**Name**: Enter a unique, descriptive name for the rule.</span></span>

   - <span data-ttu-id="f0d27-139">[**その他のオプション**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d27-139">Click **More Options**.</span></span>

   - <span data-ttu-id="f0d27-140">**正規表現**(RegEx) または単語または語句を使用してメッセージ内のコンテンツを検索するには、次のいずれかの設定を構成する場合に、このルールを適用します。</span><span class="sxs-lookup"><span data-stu-id="f0d27-140">**Apply this rule if**: Configure one of the following settings to look for content in messages using regular expressions (RegEx) or words or phrases:</span></span>

     - <span data-ttu-id="f0d27-141">**件名または本文** \>**件名または本文は**、これらのテキスト パターンと一致します:表示される [単語または語句の指定] ダイアログで、次のいずれかの値を入力し、[アイコンの追加] をクリックし、すべての値を入力するまで繰り返します。 ![ ](../../media/ITPro-EAC-AddIcon.png)</span><span class="sxs-lookup"><span data-stu-id="f0d27-141">**The subject or body** \> **subject or body matches these text patterns**: In the **Specify words or phrases** dialog that appears, enter one of the following values, click **Add** ![Add Icon](../../media/ITPro-EAC-AddIcon.png), and repeat until you've entered all the values.</span></span>

       - `If you are unable to view the content of this email\, please`
       - `\>(safe )?unsubscribe( here)?\</a\>`
       - `If you do not wish to receive further communications like this\, please`
       - `<img height="?1"? width="?1"? src=.?http\://`
       - `To stop receiving these+emails\:http\://`
       - `To unsubscribe from \w+ (e\-?letter|e?-?mail|newsletter)`
       - `no longer (wish )?(to )?(be sent|receive) w+ email`
       - `If you are unable to view the content of this email\, please click here`
       - `To ensure you receive (your daily deals|our e-?mails)\, add`
       - `If you no longer wish to receive these emails`
       - `to change your (subscription preferences|preferences or unsubscribe)`
       - `click (here to|the) unsubscribe`

      <span data-ttu-id="f0d27-142">エントリを編集するには、エントリを選択し、[編集] **アイコンを** ![ クリックします ](../../media/ITPro-EAC-EditIcon.png) 。</span><span class="sxs-lookup"><span data-stu-id="f0d27-142">To edit an entry, select it and click **Edit** ![Edit icon](../../media/ITPro-EAC-EditIcon.png).</span></span> <span data-ttu-id="f0d27-143">エントリを削除するには、そのエントリを選択し、[削除] **アイコンを** ![ クリックします ](../../media/ITPro-EAC-DeleteIcon.png) 。</span><span class="sxs-lookup"><span data-stu-id="f0d27-143">To remove an entry, select it and click **Remove** ![Remove icon](../../media/ITPro-EAC-DeleteIcon.png).</span></span>

       <span data-ttu-id="f0d27-144">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d27-144">When you're finished, click **OK**.</span></span>

     - <span data-ttu-id="f0d27-145">**件名または本文** \>**件名または本文には**、これらの単語が含まれます:表示される [単語または語句の指定] ダイアログで、次のいずれかの値を入力し、[アイコンの追加] をクリックし、すべての値を入力するまで繰り返します。 ![ ](../../media/ITPro-EAC-AddIcon.png)</span><span class="sxs-lookup"><span data-stu-id="f0d27-145">**The subject or body** \> **subject or body includes any of these words**: In the **Specify words or phrases** dialog that appears, enter one of the following values, click **Add** ![Add Icon](../../media/ITPro-EAC-AddIcon.png), and repeat until you've entered all the values.</span></span>

       - `to change your preferences or unsubscribe`
       - `Modify email preferences or unsubscribe`
       - `This is a promotional email`
       - `You are receiving this email because you requested a subscription`
       - `click here to unsubscribe`
       - `You have received this email because you are subscribed`
       - `If you no longer wish to receive our email newsletter`
       - `to unsubscribe from this newsletter`
       - `If you have trouble viewing this email`
       - `This is an advertisement`
       - `you would like to unsubscribe or change your`
       - `view this email as a webpage`
       - `You are receiving this email because you are subscribed`

      <span data-ttu-id="f0d27-146">エントリを編集するには、エントリを選択し、[編集] **アイコンを** ![ クリックします ](../../media/ITPro-EAC-EditIcon.png) 。</span><span class="sxs-lookup"><span data-stu-id="f0d27-146">To edit an entry, select it and click **Edit** ![Edit icon](../../media/ITPro-EAC-EditIcon.png).</span></span> <span data-ttu-id="f0d27-147">エントリを削除するには、そのエントリを選択し、[削除] **アイコンを** ![ クリックします ](../../media/ITPro-EAC-DeleteIcon.png) 。</span><span class="sxs-lookup"><span data-stu-id="f0d27-147">To remove an entry, select it and click **Remove** ![Remove icon](../../media/ITPro-EAC-DeleteIcon.png).</span></span>

       <span data-ttu-id="f0d27-148">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0d27-148">When you're finished, click **OK**.</span></span>

   - <span data-ttu-id="f0d27-149">**[メッセージのプロパティを** 変更 **する] を選択** \> **して、スパム信頼レベル (SCL) を設定します**。</span><span class="sxs-lookup"><span data-stu-id="f0d27-149">**Do the following**: Select **Modify the message properties** \> **set the spam confidence level (SCL)**.</span></span> <span data-ttu-id="f0d27-150">表示される **[SCL の指定** ] ダイアログで、次のいずれかの設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="f0d27-150">In the **Specify SCL** dialog that appears, configure one of the following settings:</span></span>

     - <span data-ttu-id="f0d27-151">メッセージをスパムとしてマーク **するには\*\*\*\*、[6] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="f0d27-151">To mark messages as **Spam**, select **6**.</span></span> <span data-ttu-id="f0d27-152">スパム対策ポリシーでスパム フィルターの評決に対して構成したアクションがメッセージに適用されます (既定値は [メッセージを迷惑メール フォルダーに移動する]**です**)。</span><span class="sxs-lookup"><span data-stu-id="f0d27-152">The action that you've configured for **Spam** filtering verdicts in your anti-spam policies is applied to the messages (the default value is **Move message to Junk Email folder**).</span></span>

     - <span data-ttu-id="f0d27-153">メッセージを高信頼スパム **としてマークするには\*\*\*\*、9 を選択します**。</span><span class="sxs-lookup"><span data-stu-id="f0d27-153">To mark messages as **High confidence spam** select **9**.</span></span> <span data-ttu-id="f0d27-154">スパム対策ポリシーで信頼度の高いスパム フィルターの評決を構成したアクションは、メッセージに適用されます (既定値は [メッセージを迷惑メール フォルダーに移動 **する]** です)。</span><span class="sxs-lookup"><span data-stu-id="f0d27-154">The action that you've configured for **High confidence spam** filtering verdicts in your anti-spam policies is applied to the messages (the default value is **Move message to Junk Email folder**).</span></span>

    <span data-ttu-id="f0d27-155">SCL 値の詳細については、「EOP の [スパム信頼度 (SCL)」を参照してください](spam-confidence-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="f0d27-155">For more information about SCL values, see [Spam confidence level (SCL) in EOP](spam-confidence-levels.md).</span></span>

   <span data-ttu-id="f0d27-156">完了したら、[保存] を **クリックします。**</span><span class="sxs-lookup"><span data-stu-id="f0d27-156">When you're finished, click **Save**</span></span>

## <a name="use-powershell-to-create-mail-flow-rules-that-filter-bulk-email"></a><span data-ttu-id="f0d27-157">PowerShell を使用して、バルク メールをフィルター処理するメール フロー ルールを作成する</span><span class="sxs-lookup"><span data-stu-id="f0d27-157">Use PowerShell to create mail flow rules that filter bulk email</span></span>

<span data-ttu-id="f0d27-158">メール フロー ルールの 1 つまたは両方 (正規表現と単語) を作成するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="f0d27-158">Use the following syntax to create one or both of the mail flow rules (regular expressions vs. words):</span></span>

```powershell
New-TransportRule -Name "<UniqueName>" [-SubjectOrBodyMatchesPatterns "<RegEx1>","<RegEx2>"...] [-SubjectOrBodyContainsWords "<WordOrPhrase1>","<WordOrPhrase2>"...] -SetSCL <6 | 9>
```

<span data-ttu-id="f0d27-159">この例では、トピックの前の正規表現の同じリストを使用してメッセージをスパムとして設定する "バルク メール フィルター - RegEx" という名前の新しいルールを作成 **します**。</span><span class="sxs-lookup"><span data-stu-id="f0d27-159">This example creates a new rule named "Bulk email filtering - RegEx" that uses the same list of regular expressions from earlier in the topic to set messages as **Spam**.</span></span>

```powershell
New-TransportRule -Name "Bulk email filtering - RegEx" -SubjectOrBodyMatchesPatterns "If you are unable to view the content of this email\, please","\>(safe )?unsubscribe( here)?\</a\>","If you do not wish to receive further communications like this\, please","\<img height\="?1"? width\="?1"? src=.?http\://","To stop receiving these+emails\:http\://","To unsubscribe from \w+ (e\-?letter|e?-?mail|newsletter)","no longer (wish )?(to )?(be sent|receive) w+ email","If you are unable to view the content of this email\, please click here","To ensure you receive (your daily deals|our e-?mails)\, add","If you no longer wish to receive these emails","to change your (subscription preferences|preferences or unsubscribe)","click (here to|the) unsubscribe"... -SetSCL 6
```

<span data-ttu-id="f0d27-160">この例では、トピックの前の単語の同じリストを使用してメッセージを高信頼スパムとして設定する"バルク メール フィルター - 単語" という名前の新しいルール **を作成します**。</span><span class="sxs-lookup"><span data-stu-id="f0d27-160">This example creates a new rule named "Bulk email filtering - Words" that uses the same list of words from earlier in the topic to set messages as **High confidence spam**.</span></span>

```powershell
New-TransportRule -Name "Bulk email filtering - Words" -SubjectOrBodyContainsWords "to change your preferences or unsubscribe","Modify email preferences or unsubscribe","This is a promotional email","You are receiving this email because you requested a subscription","click here to unsubscribe","You have received this email because you are subscribed","If you no longer wish to receive our email newsletter","to unsubscribe from this newsletter","If you have trouble viewing this email","This is an advertisement","you would like to unsubscribe or change your","view this email as a webpage","You are receiving this email because you are subscribed" -SetSCL 9
```

<span data-ttu-id="f0d27-161">詳細な構文とパラメーターについては、「[New-TransportRule](/powershell/module/exchange/new-transportrule)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0d27-161">For detailed syntax and parameter information, see [New-TransportRule](/powershell/module/exchange/new-transportrule).</span></span>

## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="f0d27-162">正常な動作を確認する方法</span><span class="sxs-lookup"><span data-stu-id="f0d27-162">How do you know this worked?</span></span>

<span data-ttu-id="f0d27-163">バルク メールをフィルター処理するようにメール フロー ルールが構成されていることを確認するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f0d27-163">To verify that you've configured mail flow rules to filter bulk email, do any of the following steps:</span></span>

- <span data-ttu-id="f0d27-164">EAC で、[メールフロールール] に移動し、[編集] アイコンをクリックして、 \>  \> \>  ![ ](../../media/ITPro-EAC-EditIcon.png) 設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="f0d27-164">In the EAC, go to **Mail flow** \> **Rules** \> select the rule \> click **Edit** ![Edit icon](../../media/ITPro-EAC-EditIcon.png), and verify the settings.</span></span>

- <span data-ttu-id="f0d27-165">PowerShell で、ルールの名前に置き換え、次のコマンドを \<Rule Name\> 実行して設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="f0d27-165">In PowerShell, replace \<Rule Name\> with the name of the rule, and run the following command to verify the settings:</span></span>

  ```powershell
  Get-TransportRule -Identity "<Rule Name>" | Format-List
  ```

- <span data-ttu-id="f0d27-166">外部アカウントから、影響を受ける受信者に、語句またはテキスト パターンのいずれかを含むテスト メッセージを送信し、結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="f0d27-166">From an external account, send a test messages to an affected recipient that contains one of the phrases or text patterns, and verify the results.</span></span>