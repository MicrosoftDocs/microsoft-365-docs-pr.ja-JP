---
title: サードパーティのフィッシング シミュレーションをユーザーに配信し、フィルター処理されていないメッセージを SecOps メールボックスに配信する構成
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: 管理者は、Exchange Online Protection (EOP) の高度な配信ポリシーを使用して、サポートされている特定のシナリオ (サード パーティのフィッシング シミュレーションとセキュリティ操作 (SecOps) メールボックスに配信されるメッセージ) でフィルター処理すべきではないメッセージを識別する方法について説明します。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 01d35c1f0c7abc7b6ce34fc9c2ec4d5fd5b228ae
ms.sourcegitcommit: 410f6e1c6cf53c3d9013b89d6e0b40a050ee9cad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2021
ms.locfileid: "53137741"
---
# <a name="configure-the-delivery-of-third-party-phishing-simulations-to-users-and-unfiltered-messages-to-secops-mailboxes"></a><span data-ttu-id="d8f99-103">サードパーティのフィッシング シミュレーションをユーザーに配信し、フィルター処理されていないメッセージを SecOps メールボックスに配信する構成</span><span class="sxs-lookup"><span data-stu-id="d8f99-103">Configure the delivery of third-party phishing simulations to users and unfiltered messages to SecOps mailboxes</span></span>

<span data-ttu-id="d8f99-104">**適用対象**</span><span class="sxs-lookup"><span data-stu-id="d8f99-104">**Applies to**</span></span>
- [<span data-ttu-id="d8f99-105">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="d8f99-105">Exchange Online Protection</span></span>](exchange-online-protection-overview.md)
- [<span data-ttu-id="d8f99-106">Microsoft Defender for Office 365 プラン 1 およびプラン 2</span><span class="sxs-lookup"><span data-stu-id="d8f99-106">Microsoft Defender for Office 365 plan 1 and plan 2</span></span>](defender-for-office-365.md)
- [<span data-ttu-id="d8f99-107">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="d8f99-107">Microsoft 365 Defender</span></span>](../defender/microsoft-365-defender.md)

> [!NOTE]
> <span data-ttu-id="d8f99-108">この記事で説明する機能はプレビューで、すべてのユーザーが利用できるとは言え、変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d8f99-108">The feature that's described in this article is in Preview, isn't available to everyone, and is subject to change.</span></span>

<span data-ttu-id="d8f99-109">既定で組織を[](secure-by-default.md)セキュリティで保護するために、Exchange Online Protection (EOP) では、マルウェアまたは高信頼フィッシングとして識別されるメッセージの安全なリストやフィルター バイパスは許可されません。</span><span class="sxs-lookup"><span data-stu-id="d8f99-109">To keep your organization [secure by default](secure-by-default.md), Exchange Online Protection (EOP) does not allow safe lists or filtering bypass for messages that are identified as malware or high confidence phishing.</span></span> <span data-ttu-id="d8f99-110">ただし、フィルター処理されていないメッセージの配信を必要とする特定のシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="d8f99-110">But, there are specific scenarios that require the delivery of unfiltered messages.</span></span> <span data-ttu-id="d8f99-111">例:</span><span class="sxs-lookup"><span data-stu-id="d8f99-111">For example:</span></span>

- <span data-ttu-id="d8f99-112">**サード パーティのフィッシング シミュレーション**: シミュレートされた攻撃は、実際の攻撃が組織に影響を与える前に、脆弱なユーザーを特定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-112">**Third-party phishing simulations**: Simulated attacks can help you identify vulnerable users before a real attack impacts your organization.</span></span>
- <span data-ttu-id="d8f99-113">**セキュリティ操作 (SecOps)** メールボックス: セキュリティ チームがフィルター処理されていないメッセージ (良いメッセージと悪いメッセージの両方) を収集および分析するために使用する専用のメールボックス。</span><span class="sxs-lookup"><span data-stu-id="d8f99-113">**Security operations (SecOps) mailboxes**: Dedicated mailboxes that are used by security teams to collect and analyze unfiltered messages (both good and bad).</span></span>

<span data-ttu-id="d8f99-114">これらの特定の _シナリオで_ これらのメッセージがフィルター Microsoft 365されるのを防ぐには、Microsoft 365の高度な _配信ポリシーを_ 使用します。 <sup>\*</sup>高度な配信ポリシーにより、これらのシナリオのメッセージで次の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-114">You use the _advanced delivery policy_ in Microsoft 365 to prevent these messages _in these specific scenarios_ from being filtered.<sup>\*</sup> The advanced delivery policy ensures that messages in these scenarios achieve the following results:</span></span>

- <span data-ttu-id="d8f99-115">EOP と Microsoft Defender のフィルターは、Office 365に対してアクションを実行しません。<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="d8f99-115">Filters in EOP and Microsoft Defender for Office 365 take no action on these messages.<sup>\*</sup></span></span>
- <span data-ttu-id="d8f99-116">[スパムとフィッシングのゼロアワー パージ (ZAP)](zero-hour-auto-purge.md) は、これらのメッセージに対して何も実行しません。<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="d8f99-116">[Zero-hour Purge (ZAP)](zero-hour-auto-purge.md) for spam and phishing take no action on these messages.<sup>\*</sup></span></span>
- <span data-ttu-id="d8f99-117">[これらのシナリオでは](alerts.md) 、既定のシステム通知はトリガーされません。</span><span class="sxs-lookup"><span data-stu-id="d8f99-117">[Default system alerts](alerts.md) aren't triggered for these scenarios.</span></span>
- <span data-ttu-id="d8f99-118">[Defender の AIR とクラスター化では、Office 365](office-365-air.md)メッセージは無視されます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-118">[AIR and clustering in Defender for Office 365](office-365-air.md) ignores these messages.</span></span>
- <span data-ttu-id="d8f99-119">特に、サード パーティ製のフィッシング シミュレーションの場合:</span><span class="sxs-lookup"><span data-stu-id="d8f99-119">Specifically for third-party phishing simulations:</span></span>
  - <span data-ttu-id="d8f99-120">[管理者の申請は](admin-submission.md) 、メッセージがフィッシング シミュレーション キャンペーンの一部であり、実際の脅威ではないという自動応答を生成します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-120">[Admin submissions](admin-submission.md) generates an automatic response saying that the message is part of a phishing simulation campaign and isn't a real threat.</span></span> <span data-ttu-id="d8f99-121">アラートと AIR はトリガーされません。</span><span class="sxs-lookup"><span data-stu-id="d8f99-121">Alerts and AIR will not be triggered.</span></span>
  - <span data-ttu-id="d8f99-122">[セーフ Defender for Office 365](safe-links.md)リンクは、これらのメッセージで特定された URL をブロックまたは削除しません。</span><span class="sxs-lookup"><span data-stu-id="d8f99-122">[Safe Links in Defender for Office 365](safe-links.md) doesn't block or detonate the specifically identified URLs in these messages.</span></span>
  - <span data-ttu-id="d8f99-123">[セーフ Defender Office 365](safe-attachments.md)添付ファイルは、これらのメッセージ内の添付ファイルを削除しません。</span><span class="sxs-lookup"><span data-stu-id="d8f99-123">[Safe Attachments in Defender for Office 365](safe-attachments.md) doesn't detonate attachments in these messages.</span></span>

<span data-ttu-id="d8f99-124"><sup>\*</sup> マルウェアのフィルター処理やマルウェアに対する ZAP をバイパスできない。</span><span class="sxs-lookup"><span data-stu-id="d8f99-124"><sup>\*</sup> You can't bypass malware filtering or ZAP for malware.</span></span>

<span data-ttu-id="d8f99-125">高度な配信ポリシーによって識別されるメッセージはセキュリティ上の脅威ではないので、メッセージはシステムオーバーライドとしてマークされます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-125">Messages that are identified by the advanced delivery policy aren't security threats, so the messages are marked as system overrides.</span></span> <span data-ttu-id="d8f99-126">管理者は、次のエクスペリエンスでこれらのシステムオーバーライドをフィルター処理して分析できます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-126">Admins can filter and analyze these system overrides in the following experiences:</span></span>

- [<span data-ttu-id="d8f99-127">ウイルス対策プラン 2 の Defender での脅威エクスプローラー/Office 365検出</span><span class="sxs-lookup"><span data-stu-id="d8f99-127">Threat Explorer/Real-time detections in Defender for Office 365 plan 2</span></span>](threat-explorer.md)
- <span data-ttu-id="d8f99-128">脅威[エクスプローラー/リアルタイム検出](mdo-email-entity-page.md)の Email エンティティ ページ</span><span class="sxs-lookup"><span data-stu-id="d8f99-128">The [Email entity Page in Threat Explorer/Real-time detections](mdo-email-entity-page.md)</span></span>
- <span data-ttu-id="d8f99-129">脅威 [保護の状態レポート](view-email-security-reports.md#threat-protection-status-report)</span><span class="sxs-lookup"><span data-stu-id="d8f99-129">The [Threat protection status report](view-email-security-reports.md#threat-protection-status-report)</span></span>
- [<span data-ttu-id="d8f99-130">エンドポイント向け Microsoft Defender での高度な検索</span><span class="sxs-lookup"><span data-stu-id="d8f99-130">Advanced hunting in Microsoft Defender for Endpoint</span></span>](../defender-endpoint/advanced-hunting-overview.md)
- [<span data-ttu-id="d8f99-131">キャンペーン ビュー</span><span class="sxs-lookup"><span data-stu-id="d8f99-131">Campaign Views</span></span>](campaigns.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="d8f99-132">はじめに把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="d8f99-132">What do you need to know before you begin?</span></span>

- <span data-ttu-id="d8f99-133"><https://security.microsoft.com> で Microsoft 365 Defender ポータルを開きます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-133">You open the Microsoft 365 Defender portal at <https://security.microsoft.com>.</span></span> <span data-ttu-id="d8f99-134">[高度な配信] ページに **直接移動するには** 、を開きます <https://security.microsoft.com/advanceddelivery> 。</span><span class="sxs-lookup"><span data-stu-id="d8f99-134">To go directly to the **Advanced delivery** page, open <https://security.microsoft.com/advanceddelivery>.</span></span>

- <span data-ttu-id="d8f99-135">Exchange Online PowerShell へ接続するには、「[Exchange Online PowerShell に接続する](/powershell/exchange/connect-to-exchange-online-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8f99-135">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).</span></span>

- <span data-ttu-id="d8f99-136">この記事の手順を実行するには、アクセス許可を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8f99-136">You need to be assigned permissions before you can do the procedures in this article:</span></span>
  - <span data-ttu-id="d8f99-137">高度な配信ポリシーで構成された設定を作成、変更、または削除するには、Microsoft 365 Defender ポータルのセキュリティ管理者役割グループのメンバーであり **、Exchange Online** の組織の管理役割グループ **のメンバーである必要があります**。</span><span class="sxs-lookup"><span data-stu-id="d8f99-137">To create, modify, or remove configured settings in the advanced delivery policy, you need to be a member of the **Security Administrator** role group in the **Microsoft 365 Defender portal** and a member of the **Organization Management** role group in **Exchange Online**.</span></span>
  - <span data-ttu-id="d8f99-138">高度な配信ポリシーへの読み取り専用アクセスでは、グローバル リーダーまたはセキュリティリーダーの役割グループの **メンバーである** 必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8f99-138">For read-only access to the advanced delivery policy, you need to be a member of the **Global Reader** or **Security Reader** role groups.</span></span>

  <span data-ttu-id="d8f99-139">詳細については、「Microsoft 365 Defender[](permissions-microsoft-365-security-center.md)ポータルのアクセス許可」および「Exchange Online」[を参照してください](/exchange/permissions-exo/permissions-exo)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-139">For more information, see [Permissions in the Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md) and [Permissions in Exchange Online](/exchange/permissions-exo/permissions-exo).</span></span>

  > [!NOTE]
  > <span data-ttu-id="d8f99-140">ユーザーを対応する Azure Active Directory ロールに追加すると、ユーザーは Microsoft 365 Defender ポータルで必要なアクセス許可と、Microsoft 365 の他の機能に対するアクセス許可を与Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="d8f99-140">Adding users to the corresponding Azure Active Directory role gives users the required permissions in the Microsoft 365 Defender portal _and_ permissions for other features in Microsoft 365.</span></span> <span data-ttu-id="d8f99-141">詳細については、「[管理者の役割について](../../admin/add-users/about-admin-roles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8f99-141">For more information, see [About admin roles](../../admin/add-users/about-admin-roles.md).</span></span>

## <a name="use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy"></a><span data-ttu-id="d8f99-142">高度な配信Microsoft 365 Defender SecOps メールボックスを構成するには、次のポータルを使用します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-142">Use the Microsoft 365 Defender portal to configure SecOps mailboxes in the advanced delivery policy</span></span>

1. <span data-ttu-id="d8f99-143">このポータルMicrosoft 365 Defender、[メールの送信] & **[** ルールの脅威ポリシー&] セクションの [詳細な配信 \>  \>  \> ] \> **に移動します**。</span><span class="sxs-lookup"><span data-stu-id="d8f99-143">In the Microsoft 365 Defender portal, go to **Email & Collaboration** \> **Policies & Rules** \> **Threat policies** page \> **Rules** section \> **Advanced delivery**.</span></span>

2. <span data-ttu-id="d8f99-144">[高度 **な配信] ページ** で **、[SecOps** メールボックス] タブが選択されていることを確認し、次のいずれかの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-144">On the **Advanced delivery** page, verify that the **SecOps mailbox** tab is selected, and then do one of the following steps:</span></span>
   - <span data-ttu-id="d8f99-145">[編集 ![ ] アイコン [ ](../../media/m365-cc-sc-edit-icon.png) **編集] をクリックします**。</span><span class="sxs-lookup"><span data-stu-id="d8f99-145">Click ![Edit icon](../../media/m365-cc-sc-edit-icon.png) **Edit**.</span></span>
   - <span data-ttu-id="d8f99-146">フィッシング シミュレーションが構成されていない場合は、[追加] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="d8f99-146">If there are no configured phishing simulations, click **Add**.</span></span>

3. <span data-ttu-id="d8f99-147">開く **[SecOps** メールボックスの編集] フライアウトで、次のいずれかの手順を実行して、SecOps メールボックスとして指定する既存の Exchange Online メールボックスを入力します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-147">On the **Edit SecOps mailboxes** flyout that opens, enter an existing Exchange Online mailbox that you want to designate as SecOps mailbox by doing one of the following steps:</span></span>
   - <span data-ttu-id="d8f99-148">ボックス内をクリックし、メールボックスの一覧を解決し、メールボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-148">Click in the box, let the list of mailboxes resolve, and then select the mailbox.</span></span>
   - <span data-ttu-id="d8f99-149">ボックス内をクリックすると、メールボックスの識別子 (名前、表示名、エイリアス、電子メール アドレス、アカウント名など) の入力を開始し、結果からメールボックス (表示名) を選択します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-149">Click in the box start typing an identifier for the mailbox (name, display name, alias, email address, account name, etc.), and select the mailbox (display name) from the results.</span></span>

     <span data-ttu-id="d8f99-150">必要な回数だけこの手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-150">Repeat this step as many times as necessary.</span></span> <span data-ttu-id="d8f99-151">配布グループは許可されません。</span><span class="sxs-lookup"><span data-stu-id="d8f99-151">Distribution groups are not allowed.</span></span>

     <span data-ttu-id="d8f99-152">既存の値を削除するには、削除をクリックします</span><span class="sxs-lookup"><span data-stu-id="d8f99-152">To remove an existing value, click remove</span></span> ![[削除] アイコン](../../media/m365-cc-sc-remove-selection-icon.png) <span data-ttu-id="d8f99-154">値の隣。</span><span class="sxs-lookup"><span data-stu-id="d8f99-154">next to the value.</span></span>

4. <span data-ttu-id="d8f99-155">完了したら、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8f99-155">When you're finished, click **Save**.</span></span>

<span data-ttu-id="d8f99-156">構成した SecOps メールボックス エントリは **、[SecOps** メールボックス] タブに表示されます。変更するには、タブの ![ [編集] ](../../media/m365-cc-sc-edit-icon.png) **アイコン [編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8f99-156">The SecOps mailbox entries that you configured are displayed on the **SecOps mailbox** tab. To make changes, click ![Edit icon](../../media/m365-cc-sc-edit-icon.png) **Edit** on the tab.</span></span>

## <a name="use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a><span data-ttu-id="d8f99-157">高度な配信Microsoft 365 Defenderでサード パーティのフィッシング シミュレーションを構成するには、Microsoft 365 Defender ポータルを使用します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-157">Use the Microsoft 365 Defender portal to configure third-party phishing simulations in the advanced delivery policy</span></span>

1. <span data-ttu-id="d8f99-158">このポータルMicrosoft 365 Defender、[メールの送信] & **[** ルールの脅威ポリシー&] セクションの [詳細な配信 \>  \>  \> ] \> **に移動します**。</span><span class="sxs-lookup"><span data-stu-id="d8f99-158">In the Microsoft 365 Defender portal, go to **Email & Collaboration** \> **Policies & Rules** \> **Threat policies** page \> **Rules** section \> **Advanced delivery**.</span></span>

2. <span data-ttu-id="d8f99-159">[高度 **な配信] ページ** で、[フィッシング シミュレーション] **タブを選択** し、次のいずれかの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-159">On the **Advanced delivery** page, select the **Phishing simulation** tab, and then do one of the following steps:</span></span>
   - <span data-ttu-id="d8f99-160">[編集 ![ ] アイコン [ ](../../media/m365-cc-sc-edit-icon.png) **編集] をクリックします**。</span><span class="sxs-lookup"><span data-stu-id="d8f99-160">Click ![Edit icon](../../media/m365-cc-sc-edit-icon.png) **Edit**.</span></span>
   - <span data-ttu-id="d8f99-161">フィッシング シミュレーションが構成されていない場合は、[追加] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="d8f99-161">If there are no configured phishing simulations, click **Add**.</span></span>

3. <span data-ttu-id="d8f99-162">開く **[サード パーティ製フィッシング シミュレーションの編集] フライ** アウトで、次の設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-162">On the **Edit third-party phishing simulation** flyout that opens, configure the following settings:</span></span>

   - <span data-ttu-id="d8f99-163">**送信ドメイン**: この設定を展開し、ボックスをクリックして値を入力し、Enter キーを押したり、ボックスの下に表示される値を選択して、少なくとも 1 つの電子メール アドレス ドメイン (contoso.com など) を入力します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-163">**Sending domain**: Expand this setting and enter at least one email address domain (for example, contoso.com) by clicking in the box, entering a value, and then pressing Enter or selecting the value that's displayed below the box.</span></span> <span data-ttu-id="d8f99-164">必要な回数だけこの手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-164">Repeat this step as many times as necessary.</span></span> <span data-ttu-id="d8f99-165">最大 10 のエントリを追加できます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-165">You can add up to 10 entries.</span></span>
   - <span data-ttu-id="d8f99-166">**送信 IP**: この設定を展開し、ボックスをクリックして値を入力し、Enter キーを押するか、ボックスの下に表示される値を選択することで、少なくとも 1 つの有効な IPv4 アドレスを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8f99-166">**Sending IP**: Expand this setting and enter at least one valid IPv4 address is required by clicking in the box, entering a value, and then pressing Enter or selecting the value that's displayed below the box.</span></span> <span data-ttu-id="d8f99-167">必要な回数だけこの手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-167">Repeat this step as many times as necessary.</span></span> <span data-ttu-id="d8f99-168">最大 10 のエントリを追加できます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-168">You can add up to 10 entries.</span></span> <span data-ttu-id="d8f99-169">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d8f99-169">Valid values are:</span></span>
     - <span data-ttu-id="d8f99-170">単一 IP: たとえば、192.168.1.1。</span><span class="sxs-lookup"><span data-stu-id="d8f99-170">Single IP: For example, 192.168.1.1.</span></span>
     - <span data-ttu-id="d8f99-171">IP 範囲: たとえば、192.168.0.1-192.168.0.254 です。</span><span class="sxs-lookup"><span data-stu-id="d8f99-171">IP range: For example, 192.168.0.1-192.168.0.254.</span></span>
     - <span data-ttu-id="d8f99-172">CIDR IP: たとえば、192.168.0.1/25。</span><span class="sxs-lookup"><span data-stu-id="d8f99-172">CIDR IP: For example, 192.168.0.1/25.</span></span>
   - <span data-ttu-id="d8f99-173">**許可** するシミュレーション URL : この設定を展開し、必要に応じて、フィッシング シミュレーション キャンペーンの一部である特定の URL を入力します。この URL は、ボックス内をクリックして値を入力し、Enter キーを押したり、ボックスの下に表示される値を選択したりしてブロックまたは削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8f99-173">**Simulation URLs to allow**: Expand this setting and optionally enter specific URLs that are part of your phishing simulation campaign that should not be blocked or detonated by clicking in the box, entering a value, and then pressing Enter or selecting the value that's displayed below the box.</span></span> <span data-ttu-id="d8f99-174">最大 10 のエントリを追加できます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-174">You can add up to 10 entries.</span></span>

   <span data-ttu-id="d8f99-175">既存の値を削除するには、削除をクリックします</span><span class="sxs-lookup"><span data-stu-id="d8f99-175">To remove an existing value, click remove</span></span> ![[削除] アイコン](../../media/m365-cc-sc-remove-selection-icon.png) <span data-ttu-id="d8f99-177">値の隣。</span><span class="sxs-lookup"><span data-stu-id="d8f99-177">next to the value.</span></span>

4. <span data-ttu-id="d8f99-178">完了したら、次のいずれかの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-178">When you're finished, do one of the following steps:</span></span>
   - <span data-ttu-id="d8f99-179">**初回:**[追加] を **クリックし**、[閉じる] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="d8f99-179">**First time**: Click **Add**, and then click **Close**.</span></span>
   - <span data-ttu-id="d8f99-180">**既存の編集 :**[保存] を **クリックし** 、[閉じる] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="d8f99-180">**Edit existing**: Click **Save** and then click **Close**.</span></span>

<span data-ttu-id="d8f99-181">構成したサード パーティのフィッシング シミュレーション エントリが [フィッシング シミュレーション] **タブに表示** されます。変更するには、タブの ![ [編集] ](../../media/m365-cc-sc-edit-icon.png) **アイコン [編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8f99-181">The third-party phishing simulation entries that you configured are displayed on the **Phishing simulation** tab. To make changes, click ![Edit icon](../../media/m365-cc-sc-edit-icon.png) **Edit** on the tab.</span></span>

## <a name="additional-scenarios-that-require-filtering-bypass"></a><span data-ttu-id="d8f99-182">フィルター バイパスが必要なその他のシナリオ</span><span class="sxs-lookup"><span data-stu-id="d8f99-182">Additional scenarios that require filtering bypass</span></span>

<span data-ttu-id="d8f99-183">高度な配信ポリシーが役立つ 2 つのシナリオに加えて、フィルター処理をバイパスする必要がある他のシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="d8f99-183">In addition to the two scenarios that the advanced delivery policy can help you with, there are other scenarios that might require you bypass filtering:</span></span>

- <span data-ttu-id="d8f99-184">**サード パーティ製フィルター**: ドメインの MXレコードが Office 365 を指していない場合 (メッセージは最初にどこか別の [](secure-by-default.md)場所にルーティングされます)、既定ではセキュリティで保護 *されません。*</span><span class="sxs-lookup"><span data-stu-id="d8f99-184">**Third-party filters**: If your domain's MX record *doesn't* point to Office 365 (messages are routed somewhere else first), [secure by default](secure-by-default.md) *is not available*.</span></span> <span data-ttu-id="d8f99-185">保護を追加する場合は、コネクタの拡張フィルター (スキップ リストとも呼ばれる) を有効にする *必要があります*。</span><span class="sxs-lookup"><span data-stu-id="d8f99-185">If you'd like to add protection, you'll need to enable Enhanced Filtering for Connectors (also known as *skip listing*).</span></span> <span data-ttu-id="d8f99-186">詳細については、「サードパーティのクラウド サービスを使用してメール フローを管理する」を参照[Exchange Online。](/exchange/mail-flow-best-practices/manage-mail-flow-using-third-party-cloud)</span><span class="sxs-lookup"><span data-stu-id="d8f99-186">For more information, see [Manage mail flow using a third-party cloud service with Exchange Online](/exchange/mail-flow-best-practices/manage-mail-flow-using-third-party-cloud).</span></span> <span data-ttu-id="d8f99-187">コネクタの拡張フィルター処理が不要な場合は、メール フロー ルール (トランスポート ルールとも呼ばれる) を使用して、サード パーティのフィルター処理によって既に評価されているメッセージに対して Microsoft フィルターをバイパスします。</span><span class="sxs-lookup"><span data-stu-id="d8f99-187">If you don't want Enhanced Filtering for Connectors,use mail flow rules (also known as transport rules) to bypass Microsoft filtering for messages that have already been evaluated by third-party filtering.</span></span> <span data-ttu-id="d8f99-188">詳細については、「メール フロー ルール [を使用してメッセージの SCL を設定する」を参照してください](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl.md)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-188">For more information, see [Use mail flow rules to set the SCL in messages](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl.md).</span></span>

- <span data-ttu-id="d8f99-189">**レビュー中** の誤検知 : 管理者の申請を通じて Microsoft によって分析中の特定の [](admin-submission.md)メッセージを一時的に許可して、Microsoft に不適切とマークされている既知の良いメッセージ (誤検知) を報告することができます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-189">**False positives under review**: You might want to temporarily allow certain messages that are still being analyzed by Microsoft via [admin submissions](admin-submission.md) to report known good messages that are incorrectly being marked as bad to Microsoft (false positives).</span></span> <span data-ttu-id="d8f99-190">すべての上書きと同様に、これらの許容量 **_は_** 一時的なものとすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d8f99-190">As with all overrides, we **_highly recommended_** that these allowances are temporary.</span></span>

## <a name="exchange-online-powershell-procedures-for-secops-mailboxes-in-the-advanced-delivery-policy"></a><span data-ttu-id="d8f99-191">Exchange Online高度な配信ポリシーの SecOps メールボックスの PowerShell の手順</span><span class="sxs-lookup"><span data-stu-id="d8f99-191">Exchange Online PowerShell procedures for SecOps mailboxes in the advanced delivery policy</span></span>

<span data-ttu-id="d8f99-192">PowerShell Exchange Online、高度な配信ポリシーの SecOps メールボックスの基本的な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d8f99-192">In Exchange Online PowerShell, the basic elements of SecOps mailboxes in the advanced delivery policy are:</span></span>

- <span data-ttu-id="d8f99-193">**SecOps オーバーライド ポリシー**: **\* -SecOpsOverridePolicy コマンドレットによって** 制御されます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-193">**The SecOps override policy**: Controlled by the **\*-SecOpsOverridePolicy** cmdlets.</span></span>
- <span data-ttu-id="d8f99-194">**SecOps オーバーライド ルール**: **\* -SecOpsOverrideRule** コマンドレットによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-194">**The SecOps override rule**: Controlled by the **\*-SecOpsOverrideRule** cmdlets.</span></span>

<span data-ttu-id="d8f99-195">この動作の結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d8f99-195">This behavior has the following results:</span></span>

- <span data-ttu-id="d8f99-196">最初にポリシーを作成してから、ルールが適用されるポリシーを識別するルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-196">You create the policy first, then you create the rule that identifies the policy that the rule applies to.</span></span>
- <span data-ttu-id="d8f99-197">PowerShell からポリシーを削除すると、対応するルールも削除されます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-197">When you remove a policy from PowerShell, the corresponding rule is also removed.</span></span>
- <span data-ttu-id="d8f99-198">PowerShell からルールを削除すると、対応するポリシーは削除されません。</span><span class="sxs-lookup"><span data-stu-id="d8f99-198">When you remove a rule from PowerShell, the corresponding policy is not removed.</span></span> <span data-ttu-id="d8f99-199">対応するポリシーを手動で削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8f99-199">You need to remove the corresponding policy manually.</span></span>

### <a name="use-powershell-to-configure-secops-mailboxes"></a><span data-ttu-id="d8f99-200">PowerShell を使用して SecOps メールボックスを構成する</span><span class="sxs-lookup"><span data-stu-id="d8f99-200">Use PowerShell to configure SecOps mailboxes</span></span>

<span data-ttu-id="d8f99-201">PowerShell の高度な配信ポリシーで SecOps メールボックスを構成するには、次の 2 つの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-201">Configuring a SecOps mailbox in the advanced delivery policy in PowerShell is a two-step process:</span></span>

1. <span data-ttu-id="d8f99-202">SecOps オーバーライド ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-202">Create the SecOps override policy.</span></span>
2. <span data-ttu-id="d8f99-203">ルールが適用されるポリシーを指定する SecOps オーバーライド ルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-203">Create the SecOps override rule that specifies the policy that the rule applies to.</span></span>

#### <a name="step-1-use-powershell-to-create-the-secops-override-policy"></a><span data-ttu-id="d8f99-204">手順 1: PowerShell を使用して SecOps オーバーライド ポリシーを作成する</span><span class="sxs-lookup"><span data-stu-id="d8f99-204">Step 1: Use PowerShell to create the SecOps override policy</span></span>

<span data-ttu-id="d8f99-205">SecOps オーバーライド ポリシーを作成するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-205">To create the SecOps override policy, use the following syntax:</span></span>

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>
```

<span data-ttu-id="d8f99-206">**注**: 指定した Name 値に関係なく、ポリシー名は SecOpsOverridePolicy なので、その値を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-206">**Note**: Regardless of the Name value you specify, the policy name will be SecOpsOverridePolicy, so you might as well use that value.</span></span>

<span data-ttu-id="d8f99-207">次の使用例は、SecOps メールボックス ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-207">This example creates the SecOps mailbox policy.</span></span>

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SendTo secops@contoso.com
```

<span data-ttu-id="d8f99-208">構文とパラメーターの詳細については [、「New-SecOpsOverridePolicy」を参照してください](/powershell/module/exchange/new-secopsoverridepolicy)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-208">For detailed syntax and parameter information, see [New-SecOpsOverridePolicy](/powershell/module/exchange/new-secopsoverridepolicy).</span></span>

#### <a name="step-2-use-powershell-to-create-the-secops-override-rule"></a><span data-ttu-id="d8f99-209">手順 2: PowerShell を使用して SecOps オーバーライド ルールを作成する</span><span class="sxs-lookup"><span data-stu-id="d8f99-209">Step 2: Use PowerShell to create the SecOps override rule</span></span>

<span data-ttu-id="d8f99-210">次の使用例は、指定した設定で SecOps メールボックス ルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-210">This example creates the SecOps mailbox rule with the specified settings.</span></span>

```powershell
New-SecOpsOverrideRule -Name SecOpsOverrideRule -Policy SecOpsOverridePolicy
```

<span data-ttu-id="d8f99-211">**注**: \*\*指定した Name 値に関係なく、ルール名は SecOpsOverrideRule になります。一意の GUID 値 \<GUID\> \<GUID\> (たとえば、6fed4b63-3563-495d-a481-b24a311f8329 など)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-211">**Note**: \*\*Regardless of the Name value you specify, the rule name will be SecOpsOverrideRule\<GUID\> where \<GUID\> is a unique GUID value (for example, 6fed4b63-3563-495d-a481-b24a311f8329).</span></span>

<span data-ttu-id="d8f99-212">構文とパラメーターの詳細については [、「New-SecOpsOverrideRule」を参照してください](/powershell/module/exchange/new-secopsoverriderule)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-212">For detailed syntax and parameter information, see [New-SecOpsOverrideRule](/powershell/module/exchange/new-secopsoverriderule).</span></span>

### <a name="use-powershell-to-view-the-secops-override-policy"></a><span data-ttu-id="d8f99-213">PowerShell を使用して SecOps オーバーライド ポリシーを表示する</span><span class="sxs-lookup"><span data-stu-id="d8f99-213">Use PowerShell to view the SecOps override policy</span></span>

<span data-ttu-id="d8f99-214">次の使用例は、1 つの SecOps メールボックス ポリシーに関する詳細情報を返します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-214">This example returns detailed information about the one and only SecOps mailbox policy.</span></span>

```powershell
Get-SecOpsOverridePolicy
```

<span data-ttu-id="d8f99-215">構文とパラメーターの詳細については [、「Get-SecOpsOverridePolicy」を参照してください](/powershell/module/exchange/get-secopsoverridepolicy)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-215">For detailed syntax and parameter information, see [Get-SecOpsOverridePolicy](/powershell/module/exchange/get-secopsoverridepolicy).</span></span>

### <a name="use-powershell-to-view-secops-override-rules"></a><span data-ttu-id="d8f99-216">PowerShell を使用して SecOps オーバーライド ルールを表示する</span><span class="sxs-lookup"><span data-stu-id="d8f99-216">Use PowerShell to view SecOps override rules</span></span>

<span data-ttu-id="d8f99-217">次の使用例は、SecOps オーバーライド ルールに関する詳細情報を返します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-217">This example returns detailed information about SecOps override rules.</span></span>

```powershell
Get-SecOpsOverrideRule
```

<span data-ttu-id="d8f99-218">前のコマンドは 1 つのルールのみを返す必要があります。削除が保留中のルールも結果に含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d8f99-218">Although the previous command should return only one rule, any rules that are pending deletion might also be included in the results.</span></span>

<span data-ttu-id="d8f99-219">次の使用例は、有効なルール (1) と無効なルールを識別します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-219">This example identifies the valid rule (one) and any invalid rules.</span></span>

```powershell
Get-SecOpsOverrideRule | Format-Table Name,Mode
```

<span data-ttu-id="d8f99-220">無効なルールを特定した後、この記事で後述するように **Remove-SecOpsOverrideRule** コマンドレットを使用して削除 [できます](#use-powershell-to-remove-secops-override-rules)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-220">After you identify the invalid rules, you can remove them by using the **Remove-SecOpsOverrideRule** cmdlet as described [later in this article](#use-powershell-to-remove-secops-override-rules).</span></span>

<span data-ttu-id="d8f99-221">構文とパラメーターの詳細については [、「Get-SecOpsOverrideRule」を参照してください。](/powershell/module/exchange/get-secopsoverriderule)</span><span class="sxs-lookup"><span data-stu-id="d8f99-221">For detailed syntax and parameter information, see [Get-SecOpsOverrideRule](/powershell/module/exchange/get-secopsoverriderule)</span></span>

### <a name="use-powershell-to-modify-the-secops-override-policy"></a><span data-ttu-id="d8f99-222">PowerShell を使用して SecOps オーバーライド ポリシーを変更する</span><span class="sxs-lookup"><span data-stu-id="d8f99-222">Use PowerShell to modify the SecOps override policy</span></span>

<span data-ttu-id="d8f99-223">SecOps オーバーライド ポリシーを変更するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-223">To modify the SecOps override policy, use the following syntax:</span></span>

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy [-AddSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>] [-RemoveSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>]
```

<span data-ttu-id="d8f99-224">次の使用例は、secops2@contoso.com ポリシーに追加します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-224">This example adds secops2@contoso.com to the SecOps override policy.</span></span>

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy -AddSentTo secops2@contoso.com
```

<span data-ttu-id="d8f99-225">**注**: 関連付けられた有効な SecOps オーバーライド ルールが存在する場合、ルール内の電子メール アドレスも更新されます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-225">**Note**: If an associated, valid SecOps override rule exists, the email addresses in the rule will also be updated.</span></span>

<span data-ttu-id="d8f99-226">構文とパラメーターの詳細については [、「Set-SecOpsOverridePolicy」を参照してください](/powershell/module/exchange/set-secopsoverridepolicy)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-226">For detailed syntax and parameter information, see [Set-SecOpsOverridePolicy](/powershell/module/exchange/set-secopsoverridepolicy).</span></span>

### <a name="use-powershell-to-modify-a-secops-override-rule"></a><span data-ttu-id="d8f99-227">PowerShell を使用して SecOps オーバーライド ルールを変更する</span><span class="sxs-lookup"><span data-stu-id="d8f99-227">Use PowerShell to modify a SecOps override rule</span></span>

<span data-ttu-id="d8f99-228">**Set-SecOpsOverrideRule** コマンドレットは、SecOps オーバーライド ルールの電子メール アドレスを変更しません。</span><span class="sxs-lookup"><span data-stu-id="d8f99-228">The **Set-SecOpsOverrideRule** cmdlet does not modify the email addresses in the SecOps override rule.</span></span> <span data-ttu-id="d8f99-229">SecOps オーバーライド ルールの電子メール アドレスを変更するには **、Set-SecOpsOverridePolicy コマンドレットを使用** します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-229">To modify the email addresses in the SecOps override rule, use the **Set-SecOpsOverridePolicy** cmdlet.</span></span>

<span data-ttu-id="d8f99-230">構文とパラメーターの詳細については [、「Set-SecOpsOverrideRule」を参照してください](/powershell/module/exchange/set-secopsoverriderule)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-230">For detailed syntax and parameter information, see [Set-SecOpsOverrideRule](/powershell/module/exchange/set-secopsoverriderule).</span></span>

### <a name="use-powershell-to-remove-the-secops-override-policy"></a><span data-ttu-id="d8f99-231">PowerShell を使用して SecOps オーバーライド ポリシーを削除する</span><span class="sxs-lookup"><span data-stu-id="d8f99-231">Use PowerShell to remove the SecOps override policy</span></span>

<span data-ttu-id="d8f99-232">次の使用例は、SecOps メールボックス ポリシーと対応するルールを削除します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-232">This example removes the SecOps Mailbox policy and the corresponding rule.</span></span>

```powershell
Remove-SecOpsOverridePolicy -Identity SecOpsOverridePolicy
```

<span data-ttu-id="d8f99-233">構文とパラメーターの詳細については [、「Remove-SecOpsOverridePolicy」を参照してください](/powershell/module/exchange/remove-secopsoverridepolicy)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-233">For detailed syntax and parameter information, see [Remove-SecOpsOverridePolicy](/powershell/module/exchange/remove-secopsoverridepolicy).</span></span>

### <a name="use-powershell-to-remove-secops-override-rules"></a><span data-ttu-id="d8f99-234">PowerShell を使用して SecOps オーバーライド ルールを削除する</span><span class="sxs-lookup"><span data-stu-id="d8f99-234">Use PowerShell to remove SecOps override rules</span></span>

<span data-ttu-id="d8f99-235">SecOps オーバーライド ルールを削除するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-235">To remove a SecOps override rule, use the following syntax:</span></span>

```powershell
Remove-SecOpsOverrideRule -Identity <RuleIdentity>
```

<span data-ttu-id="d8f99-236">次の使用例は、指定した SecOps オーバーライド ルールを削除します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-236">This example removes the specified SecOps override rule.</span></span>

```powershell
Remove-SecOpsOverrideRule -Identity SecOpsOverrideRule6fed4b63-3563-495d-a481-b24a311f8329
```

<span data-ttu-id="d8f99-237">構文とパラメーターの詳細については [、「Remove-SecOpsOverrideRule」を参照してください](/powershell/module/exchange/remove-secopsoverriderule)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-237">For detailed syntax and parameter information, see [Remove-SecOpsOverrideRule](/powershell/module/exchange/remove-secopsoverriderule).</span></span>

## <a name="exchange-online-powershell-procedures-for-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a><span data-ttu-id="d8f99-238">Exchange Online高度な配信ポリシーでのサード パーティのフィッシング シミュレーションの PowerShell 手順</span><span class="sxs-lookup"><span data-stu-id="d8f99-238">Exchange Online PowerShell procedures for third-party phishing simulations in the advanced delivery policy</span></span>

<span data-ttu-id="d8f99-239">PowerShell Exchange Online、高度な配信ポリシーのサード パーティフィッシング シミュレーションの基本的な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d8f99-239">In Exchange Online PowerShell, the basic elements of third-party phishing simulations in the advanced delivery policy are:</span></span>

- <span data-ttu-id="d8f99-240">**フィッシング シミュレーションの上書きポリシー**: **\* -PhishSimOverridePolicy** コマンドレットによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-240">**The phishing simulation override policy**: Controlled by the **\*-PhishSimOverridePolicy** cmdlets.</span></span>
- <span data-ttu-id="d8f99-241">**フィッシング シミュレーションの上書きルール**: **\* -PhishSimOverrideRule** コマンドレットによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-241">**The phishing simulation override rule**: Controlled by the **\*-PhishSimOverrideRule** cmdlets.</span></span>

<span data-ttu-id="d8f99-242">この動作の結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d8f99-242">This behavior has the following results:</span></span>

- <span data-ttu-id="d8f99-243">最初にポリシーを作成してから、ルールが適用されるポリシーを識別するルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-243">You create the policy first, then you create the rule that identifies the policy that the rule applies to.</span></span>
- <span data-ttu-id="d8f99-244">ポリシーとルールの設定は個別に変更します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-244">You modify the settings in the policy and the rule separately.</span></span>
- <span data-ttu-id="d8f99-245">PowerShell からポリシーを削除すると、対応するルールも削除されます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-245">When you remove a policy from PowerShell, the corresponding rule is also removed.</span></span>
- <span data-ttu-id="d8f99-246">PowerShell からルールを削除すると、対応するポリシーは削除されません。</span><span class="sxs-lookup"><span data-stu-id="d8f99-246">When you remove a rule from PowerShell, the corresponding policy is not removed.</span></span> <span data-ttu-id="d8f99-247">対応するポリシーを手動で削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8f99-247">You need to remove the corresponding policy manually.</span></span>

### <a name="use-powershell-to-configure-third-party-phishing-simulations"></a><span data-ttu-id="d8f99-248">PowerShell を使用してサード パーティのフィッシング シミュレーションを構成する</span><span class="sxs-lookup"><span data-stu-id="d8f99-248">Use PowerShell to configure third-party phishing simulations</span></span>

<span data-ttu-id="d8f99-249">PowerShell の高度な配信ポリシーでサード パーティ製のフィッシング シミュレーションを構成するには、次の 2 つの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-249">Configuring a third-party phishing simulation in the advanced delivery policy in PowerShell is a two-step process:</span></span>

1. <span data-ttu-id="d8f99-250">フィッシング シミュレーションオーバーライド ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-250">Create the phishing simulation override policy.</span></span>
2. <span data-ttu-id="d8f99-251">ルールが適用されるポリシーを指定するフィッシング シミュレーション オーバーライド ルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-251">Create the phishing simulation override rule that specifies the policy that the rule applies to.</span></span>

#### <a name="step-1-use-powershell-to-create-the-phishing-simulation-override-policy"></a><span data-ttu-id="d8f99-252">手順 1: PowerShell を使用してフィッシング シミュレーションオーバーライド ポリシーを作成する</span><span class="sxs-lookup"><span data-stu-id="d8f99-252">Step 1: Use PowerShell to create the phishing simulation override policy</span></span>

<span data-ttu-id="d8f99-253">この例では、フィッシング シミュレーションオーバーライド ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-253">This example creates the phishing simulation override policy.</span></span>

```powershell
New-PhishSimOverridePolicy -Name PhishSimOverridePolicy
```

<span data-ttu-id="d8f99-254">**注**: 指定した Name 値に関係なく、ポリシー名は PhishSimOverridePolicy なので、その値を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d8f99-254">**Note**: Regardless of the Name value you specify, the policy name will be PhishSimOverridePolicy, so you might as well use that value.</span></span>

<span data-ttu-id="d8f99-255">構文とパラメーターの詳細については [、「New-PhishSimOverridePolicy」を参照してください](/powershell/module/exchange/new-phishsimoverridepolicy)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-255">For detailed syntax and parameter information, see [New-PhishSimOverridePolicy](/powershell/module/exchange/new-phishsimoverridepolicy).</span></span>

#### <a name="step-2-use-powershell-to-create-the-phishing-simulation-override-rule"></a><span data-ttu-id="d8f99-256">手順 2: PowerShell を使用してフィッシング シミュレーションオーバーライド ルールを作成する</span><span class="sxs-lookup"><span data-stu-id="d8f99-256">Step 2: Use PowerShell to create the phishing simulation override rule</span></span>

<span data-ttu-id="d8f99-257">次の構文を使用してください。</span><span class="sxs-lookup"><span data-stu-id="d8f99-257">Use the following syntax:</span></span>

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -SenderDomainIs <Domain1>,<Domain2>,...<DomainN> -SenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>
```

<span data-ttu-id="d8f99-258">指定した Name 値に関係なく、ルール名は、一意の GUID 値である PhishSimOverrideRule \<GUID\> \<GUID\> になります (たとえば、a0eae53e-d755-4a42-9320-b9c6b55c5011 など)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-258">Regardless of the Name value you specify, the rule name will be PhishSimOverrideRule\<GUID\> where \<GUID\> is a unique GUID value (for example, a0eae53e-d755-4a42-9320-b9c6b55c5011).</span></span>

<span data-ttu-id="d8f99-259">有効な IP アドレス エントリは、次のいずれかの値です。</span><span class="sxs-lookup"><span data-stu-id="d8f99-259">A valid IP address entry is one of the following values:</span></span>

- <span data-ttu-id="d8f99-260">単一 IP: たとえば、192.168.1.1。</span><span class="sxs-lookup"><span data-stu-id="d8f99-260">Single IP: For example, 192.168.1.1.</span></span>
- <span data-ttu-id="d8f99-261">IP 範囲: たとえば、192.168.0.1-192.168.0.254 です。</span><span class="sxs-lookup"><span data-stu-id="d8f99-261">IP range: For example, 192.168.0.1-192.168.0.254.</span></span>
- <span data-ttu-id="d8f99-262">CIDR IP: たとえば、192.168.0.1/25。</span><span class="sxs-lookup"><span data-stu-id="d8f99-262">CIDR IP: For example, 192.168.0.1/25.</span></span>

<span data-ttu-id="d8f99-263">次の使用例は、指定した設定でフィッシング シミュレーションオーバーライド ルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-263">This example creates the phishing simulation override rule with the specified settings.</span></span>

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -SenderDomainIs fabrikam.com,wingtiptoys.com -SenderIpRanges 192.168.1.55
```

<span data-ttu-id="d8f99-264">構文とパラメーターの詳細については [、「New-PhishSimOverrideRule」を参照してください](/powershell/module/exchange/new-phishsimoverriderule)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-264">For detailed syntax and parameter information, see [New-PhishSimOverrideRule](/powershell/module/exchange/new-phishsimoverriderule).</span></span>

### <a name="use-powershell-to-view-the-phishing-simulation-override-policy"></a><span data-ttu-id="d8f99-265">PowerShell を使用してフィッシング シミュレーションオーバーライド ポリシーを表示する</span><span class="sxs-lookup"><span data-stu-id="d8f99-265">Use PowerShell to view the phishing simulation override policy</span></span>

<span data-ttu-id="d8f99-266">この例では、唯一のフィッシング シミュレーションオーバーライド ポリシーに関する詳細情報を返します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-266">This example returns detailed information about the one and only phishing simulation override policy.</span></span>

```powershell
Get-PhishSimOverridePolicy
```

<span data-ttu-id="d8f99-267">構文とパラメーターの詳細については [、「Get-PhishSimOverridePolicy」を参照してください](/powershell/module/exchange/get-phishsimoverridepolicy)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-267">For detailed syntax and parameter information, see [Get-PhishSimOverridePolicy](/powershell/module/exchange/get-phishsimoverridepolicy).</span></span>

### <a name="use-powershell-to-view-phishing-simulation-override-rules"></a><span data-ttu-id="d8f99-268">PowerShell を使用してフィッシング シミュレーションの上書きルールを表示する</span><span class="sxs-lookup"><span data-stu-id="d8f99-268">Use PowerShell to view phishing simulation override rules</span></span>

<span data-ttu-id="d8f99-269">この例では、フィッシング シミュレーションの上書きルールに関する詳細情報を返します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-269">This example returns detailed information about phishing simulation override rules.</span></span>

```powershell
Get-PhishSimOverrideRule
```

<span data-ttu-id="d8f99-270">前のコマンドは 1 つのルールのみを返す必要があります。削除が保留中のルールも結果に含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d8f99-270">Although the previous command should return only one rule, any rules that are pending deletion might also be included in the results.</span></span>

<span data-ttu-id="d8f99-271">次の使用例は、有効なルール (1) と無効なルールを識別します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-271">This example identifies the valid rule (one) and any invalid rules.</span></span>

```powershell
Get-PhishSimOverrideRule | Format-Table Name,Mode
```

<span data-ttu-id="d8f99-272">無効なルールを特定した後、この記事で後述するように **Remove-PhisSimOverrideRule** コマンドレットを使用して削除 [できます](#use-powershell-to-remove-phishing-simulation-override-rules)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-272">After you identify the invalid rules, you can remove them by using the **Remove-PhisSimOverrideRule** cmdlet as described [later in this article](#use-powershell-to-remove-phishing-simulation-override-rules).</span></span>

<span data-ttu-id="d8f99-273">構文とパラメーターの詳細については [、「Get-PhishSimOverrideRule」を参照してください](/powershell/module/exchange/get-phishsimoverriderule)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-273">For detailed syntax and parameter information, see [Get-PhishSimOverrideRule](/powershell/module/exchange/get-phishsimoverriderule).</span></span>

### <a name="use-powershell-to-modify-the-phishing-simulation-override-policy"></a><span data-ttu-id="d8f99-274">PowerShell を使用してフィッシング シミュレーションオーバーライド ポリシーを変更する</span><span class="sxs-lookup"><span data-stu-id="d8f99-274">Use PowerShell to modify the phishing simulation override policy</span></span>

<span data-ttu-id="d8f99-275">フィッシング シミュレーションオーバーライド ポリシーを変更するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-275">To modify the phishing simulation override policy, use the following syntax:</span></span>

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy [-Comment "<DescriptiveText>"] [-Enabled <$true | $false>]
```

<span data-ttu-id="d8f99-276">この例では、フィッシング シミュレーションオーバーライド ポリシーを無効にします。</span><span class="sxs-lookup"><span data-stu-id="d8f99-276">This example disables the phishing simulation override policy.</span></span>

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy -Enabled $false
```

<span data-ttu-id="d8f99-277">構文とパラメーターの詳細については [、「Set-PhishSimOverridePolicy」を参照してください](/powershell/module/exchange/set-phishsimoverridepolicy)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-277">For detailed syntax and parameter information, see [Set-PhishSimOverridePolicy](/powershell/module/exchange/set-phishsimoverridepolicy).</span></span>

### <a name="use-powershell-to-modify-a-phishing-simulation-override-rule"></a><span data-ttu-id="d8f99-278">PowerShell を使用してフィッシング シミュレーションオーバーライド ルールを変更する</span><span class="sxs-lookup"><span data-stu-id="d8f99-278">Use PowerShell to modify a phishing simulation override rule</span></span>

<span data-ttu-id="d8f99-279">フィッシング シミュレーションオーバーライド ルールを変更するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-279">To modify the phishing simulation override rule, use the following syntax:</span></span>

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 [-Comment "<DescriptiveText>"] [-AddSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-RemoveSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-AddSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>] [-RemoveSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>]
```

<span data-ttu-id="d8f99-280">次の使用例は、次の設定を使用して、指定したフィッシング シミュレーションオーバーライド ルールを変更します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-280">This example modifies the specified phishing simulation override rule with the following settings:</span></span>

- <span data-ttu-id="d8f99-281">ドメイン エントリを追加 blueyonderairlines.com。</span><span class="sxs-lookup"><span data-stu-id="d8f99-281">Add the domain entry blueyonderairlines.com.</span></span>
- <span data-ttu-id="d8f99-282">IP アドレス エントリ 192.168.1.55 を削除します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-282">Remove the IP address entry 192.168.1.55.</span></span>

<span data-ttu-id="d8f99-283">これらの変更は既存のエントリには影響しない点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="d8f99-283">Note that these changes don't affect existing entries.</span></span>

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 -AddSenderDomainIs blueyonderairlines.com -RemoveSenderIpRanges 192.168.1.55
```

<span data-ttu-id="d8f99-284">構文とパラメーターの詳細については [、「Set-PhishSimOverrideRule」を参照してください](/powershell/module/exchange/set-phishsimoverriderule)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-284">For detailed syntax and parameter information, see [Set-PhishSimOverrideRule](/powershell/module/exchange/set-phishsimoverriderule).</span></span>

### <a name="use-powershell-to-remove-a-phishing-simulation-override-policy"></a><span data-ttu-id="d8f99-285">PowerShell を使用してフィッシング シミュレーションオーバーライド ポリシーを削除する</span><span class="sxs-lookup"><span data-stu-id="d8f99-285">Use PowerShell to remove a phishing simulation override policy</span></span>

<span data-ttu-id="d8f99-286">次の使用例は、フィッシング シミュレーションオーバーライド ポリシーと対応するルールを削除します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-286">This example removes the phishing simulation override policy and the corresponding rule.</span></span>

```powershell
Remove-PhishSimOverridePolicy -Identity PhishSimOverridePolicy
```

<span data-ttu-id="d8f99-287">構文とパラメーターの詳細については [、「Remove-PhishSimOverridePolicy」を参照してください](/powershell/module/exchange/remove-phishsimoverridepolicy)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-287">For detailed syntax and parameter information, see [Remove-PhishSimOverridePolicy](/powershell/module/exchange/remove-phishsimoverridepolicy).</span></span>

### <a name="use-powershell-to-remove-phishing-simulation-override-rules"></a><span data-ttu-id="d8f99-288">PowerShell を使用してフィッシング シミュレーションの上書きルールを削除する</span><span class="sxs-lookup"><span data-stu-id="d8f99-288">Use PowerShell to remove phishing simulation override rules</span></span>

<span data-ttu-id="d8f99-289">フィッシング シミュレーションオーバーライド ルールを削除するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-289">To remove a phishing simulation override rule, use the following syntax:</span></span>

```powershell
Remove-PhishSimOverrideRule -Identity <RuleIdentity>
```

<span data-ttu-id="d8f99-290">次の使用例は、指定したフィッシング シミュレーションオーバーライド ルールを削除します。</span><span class="sxs-lookup"><span data-stu-id="d8f99-290">This example removes the specified phishing simulation override rule.</span></span>

```powershell
Remove-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011
```

<span data-ttu-id="d8f99-291">構文とパラメーターの詳細については [、「Remove-PhishSimOverrideRule」を参照してください](/powershell/module/exchange/remove-phishsimoverriderule)。</span><span class="sxs-lookup"><span data-stu-id="d8f99-291">For detailed syntax and parameter information, see [Remove-PhishSimOverrideRule](/powershell/module/exchange/remove-phishsimoverriderule).</span></span>
