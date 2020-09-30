---
title: Office 365 セキュリティ
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 08/13/2020
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- microsoft-365-docs-pr
description: Office 365 のセキュリティ。 EOP から ATP プラン1および2、標準と厳密なセキュリティ構成の比較を行い、プロパティをセキュリティで保護する方法を理解できるようにします。
ms.openlocfilehash: 680066f58850f59523ae6fb8a8168459dd813fc1
ms.sourcegitcommit: 888b9355ef7b933c55ca6c18639c12426ff3fbde
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/29/2020
ms.locfileid: "48304848"
---
# <a name="office-365-security-outline"></a><span data-ttu-id="b6701-103">Office 365 セキュリティアウトライン</span><span class="sxs-lookup"><span data-stu-id="b6701-103">Office 365 Security outline</span></span>

<span data-ttu-id="b6701-104">この記事では、クラウド内の新しいセキュリティプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b6701-104">This article will introduce you to your new security properties in the Cloud.</span></span> <span data-ttu-id="b6701-105">セキュリティ操作センターの一部であるかどうかにかかわらず、セキュリティ管理者はこのスペースを利用しているか、またはリフレッシャーを使用したいと考えています。</span><span class="sxs-lookup"><span data-stu-id="b6701-105">Whether you're part of a Security Operations Center, you're a Security Administrator new to the space, or you want a refresher, let's get started.</span></span>

> [!CAUTION]
> <span data-ttu-id="b6701-106">こんにちは。</span><span class="sxs-lookup"><span data-stu-id="b6701-106">Hi.</span></span> <span data-ttu-id="b6701-107">**Outlook.com**、 **microsoft 365 ファミリ**、または**microsoft 365 Personal**を使用していて *、安全なリンク*または安全な*添付ファイル*の情報を必要とする場合は、***このリンクをクリックし***てください。 [Microsoft 365 サブスクライバーの高度な Outlook.com セキュリティ](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2)。</span><span class="sxs-lookup"><span data-stu-id="b6701-107">If you're using **Outlook.com**, **Microsoft 365 Family**, or **Microsoft 365 Personal**, and need *Safe Links* or *Safe Attachments* info, ***click this link***: [Advanced Outlook.com security for Microsoft 365 subscribers](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).</span></span> <span data-ttu-id="b6701-108">よろしく!</span><span class="sxs-lookup"><span data-stu-id="b6701-108">Thanks!</span></span>

## <a name="office-365-security-spelled-out"></a><span data-ttu-id="b6701-109">Office 365 のセキュリティに関する綴り</span><span class="sxs-lookup"><span data-stu-id="b6701-109">Office 365 security spelled out</span></span>

<span data-ttu-id="b6701-110">すべての Office 365 サブスクリプションには、セキュリティ機能が付属しています。</span><span class="sxs-lookup"><span data-stu-id="b6701-110">Every Office 365 subscription comes with security capabilities.</span></span> <span data-ttu-id="b6701-111">実行できる目標と操作は、これらの異なるサブスクリプションの焦点に依存します。</span><span class="sxs-lookup"><span data-stu-id="b6701-111">The goals and actions that you can take depend on the focus of these different subscriptions.</span></span> <span data-ttu-id="b6701-112">Office 365 のセキュリティでは、サブスクリプションの種類に関連付けられている3つの主要なセキュリティサービス (製品) があります。</span><span class="sxs-lookup"><span data-stu-id="b6701-112">In Office 365 security, there are three main security services (or products) tied to your subscription type:</span></span>

1. <span data-ttu-id="b6701-113">Exchange Online Protection (EOP)</span><span class="sxs-lookup"><span data-stu-id="b6701-113">Exchange Online Protection (EOP)</span></span>
1. <span data-ttu-id="b6701-114">Advanced Threat Protection、Plan 1 (ATP P1)</span><span class="sxs-lookup"><span data-stu-id="b6701-114">Advanced Threat Protection, Plan 1 (ATP P1)</span></span>
1. <span data-ttu-id="b6701-115">Advanced Threat Protection、Plan 2 (ATP P2)</span><span class="sxs-lookup"><span data-stu-id="b6701-115">Advanced Threat Protection, Plan 2 (ATP P2)</span></span>

> [!NOTE]
> <span data-ttu-id="b6701-116">サブスクリプションを購入し、セキュリティ機能を *今すぐ*展開する必要がある場合は、「 [脅威から保護](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats?view=o365-worldwide) する」の手順に進んでください。</span><span class="sxs-lookup"><span data-stu-id="b6701-116">If you bought your subscription and need to roll out security features *right now*, skip to the steps in the [Protect Against Threats](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats?view=o365-worldwide) article.</span></span> <span data-ttu-id="b6701-117">ご利用のお客様がご自身のサブスクリプションを初めてご利用になる場合は、 [Microsoft 365 管理センター](https://admin.microsoft.com/AdminPortal/#/homepage)の製品 > 請求先を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6701-117">If you're new to your subscription and would like to know your license before you begin, browse Billing > Your Products in the [Microsoft 365 admin center](https://admin.microsoft.com/AdminPortal/#/homepage).</span></span>

<span data-ttu-id="b6701-118">Office 365 は、EOP によって提供される中心的な保護に基づいて構築されています。</span><span class="sxs-lookup"><span data-stu-id="b6701-118">Office 365 security builds on the core protections offered by EOP.</span></span> <span data-ttu-id="b6701-119">EOP は、Exchange Online メールボックスが存在する任意のサブスクリプションに存在します (ここで説明するすべてのセキュリティ製品はクラウドベースであることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="b6701-119">EOP is present in any subscription where Exchange Online mailboxes can be found (remember, all the security products discussed here are Cloud-based).</span></span>

<span data-ttu-id="b6701-120">この方法で説明した3つのコンポーネントについては、よく見られます。</span><span class="sxs-lookup"><span data-stu-id="b6701-120">You may be accustomed to seeing these three components discussed in this way:</span></span>

|<span data-ttu-id="b6701-121">EOP</span><span class="sxs-lookup"><span data-stu-id="b6701-121">EOP</span></span>  | <span data-ttu-id="b6701-122">ATP P1</span><span class="sxs-lookup"><span data-stu-id="b6701-122">ATP P1</span></span> | <span data-ttu-id="b6701-123">ATP P2</span><span class="sxs-lookup"><span data-stu-id="b6701-123">ATP P2</span></span>  |
|---------|---------|---------|
|<span data-ttu-id="b6701-124">ボリュームベースの広範な既知の攻撃を防止します。</span><span class="sxs-lookup"><span data-stu-id="b6701-124">Prevents broad, volume-based, known attacks.</span></span>    |  <span data-ttu-id="b6701-125">ゼロ日のマルウェア、フィッシング、およびビジネスメールの侵害から電子メールとコラボレーションを保護します。</span><span class="sxs-lookup"><span data-stu-id="b6701-125">Protects email and collaboration from zero-day malware, phish, and business email compromise.</span></span>       | <span data-ttu-id="b6701-126">事後違反の調査、探し、応答、自動化、シミュレーション (トレーニング用) を追加します。</span><span class="sxs-lookup"><span data-stu-id="b6701-126">Adds post-breach investigation, hunting, and response, as well as automation, and simulation (for training).</span></span>         |

<span data-ttu-id="b6701-127">しかし、アーキテクチャに関しては、各部分をセキュリティの累積的なレイヤーと考え、それぞれにセキュリティ上の重点を置いて始めましょう。</span><span class="sxs-lookup"><span data-stu-id="b6701-127">But in terms of architecture, let's start by thinking of each piece as cumulative layers of security, each with a security emphasis.</span></span> <span data-ttu-id="b6701-128">次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b6701-128">More like this:</span></span>

<!--:::image type="content" source="../../media/tp-EOPATPStack.PNG" alt-text="Placeholder graphic":::-->

:::image type="content" source="../../media/tp_EOPandATPGraphic.png" alt-text="Placeholder graphic":::

<span data-ttu-id="b6701-130">これらのサービスはそれぞれ、保護、検出、調査、応答の中から特定の目標を重視していますが、 ***すべて*** のサービスが、保護、検出、調査、応答の ***いずれか*** の目標を達成できます。</span><span class="sxs-lookup"><span data-stu-id="b6701-130">Though each of these services emphasizes a specific goal from among Protect, Detect, Investigate, and Respond, ***all*** the services can carry out ***any*** of the goals of protecting, detecting, investigating, and responding.</span></span>

<span data-ttu-id="b6701-131">Office 365 セキュリティの中核となるのは、EOP 保護です。</span><span class="sxs-lookup"><span data-stu-id="b6701-131">The core of Office 365 security is EOP protection.</span></span> <span data-ttu-id="b6701-132">ATP P1 には EOP が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b6701-132">ATP P1 contains EOP in it.</span></span> <span data-ttu-id="b6701-133">ATP P2 には、P1 と EOP が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b6701-133">ATP P2 contains P1 and EOP.</span></span> <span data-ttu-id="b6701-134">この構造体は累積されています。</span><span class="sxs-lookup"><span data-stu-id="b6701-134">The structure is cumulative.</span></span> <span data-ttu-id="b6701-135">そのため、ATP を構成する場合は、EOP から始めて、レイヤー全体で作業する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6701-135">That's why, when configuring ATP, you should start with EOP and work up through the layers.</span></span>

<span data-ttu-id="b6701-136">電子メール認証の構成はパブリック DNS で行われますが、この機能を構成してスプーフィングを防止することが重要です。</span><span class="sxs-lookup"><span data-stu-id="b6701-136">Though email authentication configuration takes place in public DNS, it's important to configure this feature to help defend against spoofing.</span></span> <span data-ttu-id="b6701-137">*EOP を使用している場合は、* ***[電子メール認証を構成](https://docs.microsoft.com/microsoft-365/security/office-365-security/email-validation-and-authentication?view=o365-worldwide)する必要があり***ます。</span><span class="sxs-lookup"><span data-stu-id="b6701-137">*If you have EOP,* ***you should [configure email authentication](https://docs.microsoft.com/microsoft-365/security/office-365-security/email-validation-and-authentication?view=o365-worldwide)***.</span></span>

<span data-ttu-id="b6701-138">Office 365 E3 以降がある場合は、EOP がありますが、アップグレードを通じてスタンドアロン ATP P1 を購入するオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="b6701-138">If you have an Office 365 E3, or below, you have EOP, but with the option to buy standalone ATP P1 through upgrade.</span></span> <span data-ttu-id="b6701-139">Office 365 E5 がインストールされている場合は、既に ATP P2 があります。</span><span class="sxs-lookup"><span data-stu-id="b6701-139">If you have Office 365 E5, you already have ATP P2.</span></span>

> [!TIP]
> <span data-ttu-id="b6701-140">サブスクリプションが Office 365 E3 または E5 のどちらでもない場合でも、ATP P1 にアップグレードするオプションがあるかどうかを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="b6701-140">If your subscription is neither Office 365 E3 or E5, you can still check to see if you have the option to upgrade to ATP P1.</span></span> <span data-ttu-id="b6701-141">関心がある場合は、 [この web ページ](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) に ATP P1 upgrade の対象となるサブスクリプションが一覧表示されます (詳細については、ページの最後をチェックしてください)。</span><span class="sxs-lookup"><span data-stu-id="b6701-141">If you're interested, [this webpage](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) lists subscriptions eligible for the ATP P1 upgrade (check the end of the page for the fine-print).</span></span>

## <a name="the-office-365-security-ladder-from-eop-to-atp"></a><span data-ttu-id="b6701-142">EOP から ATP への Office 365 セキュリティのはしご</span><span class="sxs-lookup"><span data-stu-id="b6701-142">The Office 365 security ladder from EOP to ATP</span></span>

:::image type="content" source="../../media/tp_EOPATPEmailAuth4.gif" alt-text="Placeholder graphic":::

> [!IMPORTANT]
> <span data-ttu-id="b6701-144">これらのページの詳細については、「 [Exchange Online protection](https://docs.microsoft.com/microsoft-365/security/office-365-security/exchange-online-protection-overview?view=o365-worldwide)」および [「Advanced Threat protection](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp?view=o365-worldwide)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6701-144">Learn the details on these pages: [Exchange Online Protection](https://docs.microsoft.com/microsoft-365/security/office-365-security/exchange-online-protection-overview?view=o365-worldwide), and [Advanced Threat Protection](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp?view=o365-worldwide).</span></span>

<span data-ttu-id="b6701-145">ATP プランを追加することによって、純粋な EOP threat management の利点が一目でわかります。</span><span class="sxs-lookup"><span data-stu-id="b6701-145">What makes adding ATP plans an advantage to pure EOP threat management can be difficult to tell at first glance.</span></span> <span data-ttu-id="b6701-146">アップグレードパスが組織に適しているかどうかを判断するには、各製品の機能を次のように確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="b6701-146">To help sort out if an upgrade path is right for your organization, let's look at the capabilities of each product when it comes to:</span></span>

 - <span data-ttu-id="b6701-147">脅威の防止と検出</span><span class="sxs-lookup"><span data-stu-id="b6701-147">preventing and detecting threats</span></span>
 - <span data-ttu-id="b6701-148">うち</span><span class="sxs-lookup"><span data-stu-id="b6701-148">investigating</span></span>
 - <span data-ttu-id="b6701-149">応答</span><span class="sxs-lookup"><span data-stu-id="b6701-149">responding</span></span>

<span data-ttu-id="b6701-150">**Exchange Online Protection**以降:</span><span class="sxs-lookup"><span data-stu-id="b6701-150">starting with **Exchange Online Protection**:</span></span>
<p>

|<span data-ttu-id="b6701-151">防止/検出</span><span class="sxs-lookup"><span data-stu-id="b6701-151">Prevent/Detect</span></span>  |<span data-ttu-id="b6701-152">調査</span><span class="sxs-lookup"><span data-stu-id="b6701-152">Investigate</span></span>  |<span data-ttu-id="b6701-153">Respond</span><span class="sxs-lookup"><span data-stu-id="b6701-153">Respond</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="b6701-154">テクノロジは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b6701-154">Technologies include:</span></span><ul><li><span data-ttu-id="b6701-155">スパム</span><span class="sxs-lookup"><span data-stu-id="b6701-155">spam</span></span></li><li><span data-ttu-id="b6701-156">フィッシング</span><span class="sxs-lookup"><span data-stu-id="b6701-156">phish</span></span></li><li><span data-ttu-id="b6701-157">ウェア</span><span class="sxs-lookup"><span data-stu-id="b6701-157">malware</span></span></li><li><span data-ttu-id="b6701-158">バルクメール</span><span class="sxs-lookup"><span data-stu-id="b6701-158">bulk mail</span></span></li><li><span data-ttu-id="b6701-159">スプーフィングインテリジェンス</span><span class="sxs-lookup"><span data-stu-id="b6701-159">spoof intelligence</span></span></li><li><span data-ttu-id="b6701-160">偽装の検出</span><span class="sxs-lookup"><span data-stu-id="b6701-160">impersonation detection</span></span></li><li><span data-ttu-id="b6701-161">管理者検疫</span><span class="sxs-lookup"><span data-stu-id="b6701-161">Admin Quarantine</span></span></li><li><span data-ttu-id="b6701-162">誤検知と誤検知の管理者およびユーザーの送信</span><span class="sxs-lookup"><span data-stu-id="b6701-162">Admin and user submissions of False Positives and False Negatives</span></span></li><li><span data-ttu-id="b6701-163">Url とファイルの許可/ブロック</span><span class="sxs-lookup"><span data-stu-id="b6701-163">Allow/Block for URLs and Files</span></span></li><li><span data-ttu-id="b6701-164">レポート</span><span class="sxs-lookup"><span data-stu-id="b6701-164">Reports</span></span></li></u1>|<li><span data-ttu-id="b6701-165">監査ログ検索</span><span class="sxs-lookup"><span data-stu-id="b6701-165">Audit log search</span></span></li><li><span data-ttu-id="b6701-166">メッセージの追跡</span><span class="sxs-lookup"><span data-stu-id="b6701-166">Message Trace</span></span></li>|<li><span data-ttu-id="b6701-167">ゼロ時間自動削除 (ZAP)</span><span class="sxs-lookup"><span data-stu-id="b6701-167">Zero-hour Auto-Purge (ZAP)</span></span></li><li><span data-ttu-id="b6701-168">許可リストと禁止リストの絞り込みとテスト</span><span class="sxs-lookup"><span data-stu-id="b6701-168">Refinement and testing of Allow and Block lists</span></span></li>|

<span data-ttu-id="b6701-169">EOP に移動する場合は、 **[この記事に移動](https://review.docs.microsoft.com/microsoft-365/security/office-365-security/exchange-online-protection-overview?view=o365-21vianet&branch=tp_EOPOverview)** してください。</span><span class="sxs-lookup"><span data-stu-id="b6701-169">If you want to dig in to EOP, **[jump to this article](https://review.docs.microsoft.com/microsoft-365/security/office-365-security/exchange-online-protection-overview?view=o365-21vianet&branch=tp_EOPOverview)**.</span></span>

<span data-ttu-id="b6701-170">これらの製品は累積的なので、ATP P1 を評価してサブスクライブする場合は、これらの機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="b6701-170">Because these products are cumulative, if you evaluate ATP P1 and decide to subscribe to it, you'll add these abilities.</span></span>

<span data-ttu-id="b6701-171">**Advanced Threat Protection**を使用した利点: プラン 1 (終了):</span><span class="sxs-lookup"><span data-stu-id="b6701-171">Gains with **Advanced Threat Protection, Plan 1** (to date):</span></span>
<p>

|<span data-ttu-id="b6701-172">防止/検出</span><span class="sxs-lookup"><span data-stu-id="b6701-172">Prevent/Detect</span></span>  |<span data-ttu-id="b6701-173">調査</span><span class="sxs-lookup"><span data-stu-id="b6701-173">Investigate</span></span>  |<span data-ttu-id="b6701-174">Respond</span><span class="sxs-lookup"><span data-stu-id="b6701-174">Respond</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="b6701-175">EOP に含まれるテクノロジには、次のようなものがあります。<u1></span><span class="sxs-lookup"><span data-stu-id="b6701-175">Technologies include everything in EOP plus:<u1></span></span><li><span data-ttu-id="b6701-176">安全な添付ファイル</span><span class="sxs-lookup"><span data-stu-id="b6701-176">Safe attachments</span></span></li><li><span data-ttu-id="b6701-177">安全なリンク</span><span class="sxs-lookup"><span data-stu-id="b6701-177">Safe links</span></span><li><span data-ttu-id="b6701-178">ワークロードの ATP 保護 (例</span><span class="sxs-lookup"><span data-stu-id="b6701-178">ATP protection for workloads (ex.</span></span> <span data-ttu-id="b6701-179">SharePoint Online、Teams、OneDrive for Business)</span><span class="sxs-lookup"><span data-stu-id="b6701-179">SharePoint Online, Teams, OneDrive for Business)</span></span></li><li><span data-ttu-id="b6701-180">電子メール、Office クライアント、および Teams でのクリック時の保護</span><span class="sxs-lookup"><span data-stu-id="b6701-180">Time-of-click protection in email, Office clients, and Teams</span></span></li><li><span data-ttu-id="b6701-181">ATP のフィッシング対策</span><span class="sxs-lookup"><span data-stu-id="b6701-181">ATP anti-phishing</span></span></li><li><span data-ttu-id="b6701-182">ユーザーおよびドメインの偽装保護</span><span class="sxs-lookup"><span data-stu-id="b6701-182">User and domain impersonation protection</span></span></li><li><span data-ttu-id="b6701-183">通知の SIEM 統合 API</span><span class="sxs-lookup"><span data-stu-id="b6701-183">Alerts, and SIEM integration API for alerts</span></span></li>|<li><span data-ttu-id="b6701-184">検出のための SIEM 統合 API</span><span class="sxs-lookup"><span data-stu-id="b6701-184">SIEM integration API for detections</span></span></li><li><span data-ttu-id="b6701-185">**リアルタイム検出ツール**</span><span class="sxs-lookup"><span data-stu-id="b6701-185">**Real-time detections tool**</span></span></li><li><span data-ttu-id="b6701-186">URL トレース</span><span class="sxs-lookup"><span data-stu-id="b6701-186">URL trace</span></span></li>|<li><span data-ttu-id="b6701-187">同じ</span><span class="sxs-lookup"><span data-stu-id="b6701-187">Same</span></span></li></u1>

<span data-ttu-id="b6701-188">そのため、ATP P1 は家の ***予防*** 側を拡張し、 ***検出***のための追加のフォームを追加します。</span><span class="sxs-lookup"><span data-stu-id="b6701-188">So, ATP P1 expands on the ***prevention*** side of the house, and adds extra forms of ***detection***.</span></span>

<span data-ttu-id="b6701-189">ATP P1 では **、調査のリアルタイム検出** も追加されています。</span><span class="sxs-lookup"><span data-stu-id="b6701-189">ATP P1 also adds **Real-time detections** for investigations.</span></span> <span data-ttu-id="b6701-190">この脅威の探すツールの名前は、ATP P1 があることを *知る* ことが明確であるため、太字になっています。</span><span class="sxs-lookup"><span data-stu-id="b6701-190">This threat hunting tool's name is in bold because having it is clear means of *knowing* you have ATP P1.</span></span> <span data-ttu-id="b6701-191">ATP P2 では表示されません。</span><span class="sxs-lookup"><span data-stu-id="b6701-191">It doesn't appear in ATP P2.</span></span>

<span data-ttu-id="b6701-192">**Advanced Threat Protection**を使用した利点: プラン 2 (終了):</span><span class="sxs-lookup"><span data-stu-id="b6701-192">Gains with **Advanced Threat Protection, Plan 2** (to date):</span></span>
<p>

|<span data-ttu-id="b6701-193">防止/検出</span><span class="sxs-lookup"><span data-stu-id="b6701-193">Prevent/Detect</span></span>  |<span data-ttu-id="b6701-194">調査</span><span class="sxs-lookup"><span data-stu-id="b6701-194">Investigate</span></span>  |<span data-ttu-id="b6701-195">Respond</span><span class="sxs-lookup"><span data-stu-id="b6701-195">Respond</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="b6701-196">EOP には、次のようなテクノロジが含まれています。<u1></span><span class="sxs-lookup"><span data-stu-id="b6701-196">Technologies include everything in EOP, and ATP P1 plus:<u1></span></span><li><span data-ttu-id="b6701-197">同じ</span><span class="sxs-lookup"><span data-stu-id="b6701-197">Same</span></span></li>|<li><span data-ttu-id="b6701-198">**脅威エクスプローラー**</span><span class="sxs-lookup"><span data-stu-id="b6701-198">**Threat Explorer**</span></span></li><li><span data-ttu-id="b6701-199">脅威トラッカー</span><span class="sxs-lookup"><span data-stu-id="b6701-199">Threat Trackers</span></span></li><li><span data-ttu-id="b6701-200">キャンペーンビュー</span><span class="sxs-lookup"><span data-stu-id="b6701-200">Campaign views</span></span></li>|<li><span data-ttu-id="b6701-201">自動化された調査と応答 (AIR)</span><span class="sxs-lookup"><span data-stu-id="b6701-201">Automated Investigation and Response (AIR)</span></span></li><li><span data-ttu-id="b6701-202">脅威エクスプローラからの空気</span><span class="sxs-lookup"><span data-stu-id="b6701-202">AIR from Threat Explorer</span></span></li><li><span data-ttu-id="b6701-203">侵害されたユーザーのための空気</span><span class="sxs-lookup"><span data-stu-id="b6701-203">AIR for compromised users</span></span></li><li><span data-ttu-id="b6701-204">自動調査用の SIEM 統合 API</span><span class="sxs-lookup"><span data-stu-id="b6701-204">SIEM Integration API for Automated Investigations</span></span></li>

<span data-ttu-id="b6701-205">そのため、ATP P2 は、住宅の ***調査と応答*** 側を拡張し、新しい探しの強さを追加します。</span><span class="sxs-lookup"><span data-stu-id="b6701-205">So, ATP P2 expands on the ***investigation and response*** side of the house, and adds a new hunting strength.</span></span> <span data-ttu-id="b6701-206">自動化。</span><span class="sxs-lookup"><span data-stu-id="b6701-206">Automation.</span></span>

<span data-ttu-id="b6701-207">ATP P2 では、プライマリの探しているツールは、リアルタイムの検出ではなく、[ **脅威エクスプローラー** ] と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="b6701-207">In ATP P2, the primary hunting tool is called **Threat Explorer** rather than Real-time detections.</span></span> <span data-ttu-id="b6701-208">セキュリティセンターに移動したときに脅威エクスプローラーが表示された場合は、ATP P2 にいます。</span><span class="sxs-lookup"><span data-stu-id="b6701-208">If you see Threat Explorer when you navigate to the Security center, you're in ATP P2.</span></span>

<span data-ttu-id="b6701-209">ATP P1 と P2 の詳細を確認するには、 **[この記事に移動](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp?view=o365-worldwide)** します。</span><span class="sxs-lookup"><span data-stu-id="b6701-209">To get into the details of ATP P1 and P2, **[jump to this article](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp?view=o365-worldwide)**.</span></span>

> [!TIP]
> <span data-ttu-id="b6701-210">また、EOP と ATP は、エンドユーザーに関しても異なります。</span><span class="sxs-lookup"><span data-stu-id="b6701-210">EOP and ATP are also different when it comes to end-users.</span></span> <span data-ttu-id="b6701-211">EOP と ATP P1 では、フォーカスは *認識*されます。この2つのサービスには、ユーザーが疑わしいと思われる電子メールを報告して詳細な分析を行うことができるようにするための *レポートメッセージ Outlook アドイン* が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b6701-211">In EOP and ATP P1, the focus is *awareness*, and so those two services include the *Report message Outlook add-in* so users can report emails they find suspicious, for further analysis.</span></span> <p> <span data-ttu-id="b6701-212">ATP P2 (EOP および P1 のすべての内容が含まれています) では、フォーカスがエンドユーザーのための *追加トレーニング* に移り、セキュリティ操作センターが強力な *脅威シミュレータ* ツールと、それが提供するエンドユーザー指標にアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="b6701-212">In ATP P2 (which contains everything in EOP and P1), the focus shifts to *further training* for end-users, and so the Security Operations Center has access to a powerful *Threat Simulator* tool, and the end-user metrics it provides.</span></span>

## <a name="office-365-atp-plan-1-vs-plan-2-cheat-sheet"></a><span data-ttu-id="b6701-213">Office 365 ATP プラン1対計画2カンニングペーパー</span><span class="sxs-lookup"><span data-stu-id="b6701-213">Office 365 ATP Plan 1 vs. Plan 2 cheat sheet</span></span>

<span data-ttu-id="b6701-214">このクイックリファレンスは、各 ATP サブスクリプションで提供される機能について理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b6701-214">This quick-reference will help you understand what capabilities come with each ATP subscription.</span></span> <span data-ttu-id="b6701-215">EOP の機能についての知識と組み合わせることにより、ビジネス意思決定者がニーズに最も適した ATP を判断できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b6701-215">When combined with your knowledge of EOP features, it can help business decision makers determine what ATP is best for their needs.</span></span>

|<span data-ttu-id="b6701-216">Office 365 ATP プラン 1</span><span class="sxs-lookup"><span data-stu-id="b6701-216">Office 365 ATP Plan 1</span></span>|<span data-ttu-id="b6701-217">Office 365 ATP プラン 2</span><span class="sxs-lookup"><span data-stu-id="b6701-217">Office 365 ATP Plan 2</span></span>|
|---|---|
|<br/><span data-ttu-id="b6701-218">構成、保護、および検出機能:</span><span class="sxs-lookup"><span data-stu-id="b6701-218">Configuration, protection, and detection capabilities:</span></span> <ul><li>[<span data-ttu-id="b6701-219">添付ファイル保護</span><span class="sxs-lookup"><span data-stu-id="b6701-219">Safe Attachments</span></span>](atp-safe-attachments.md)</li><li>[<span data-ttu-id="b6701-220">リンク保護</span><span class="sxs-lookup"><span data-stu-id="b6701-220">Safe Links</span></span>](atp-safe-links.md)</li><li>[<span data-ttu-id="b6701-221">SharePoint、OneDrive、Microsoft Teams 用の ATP</span><span class="sxs-lookup"><span data-stu-id="b6701-221">ATP for SharePoint, OneDrive, and Microsoft Teams</span></span>](atp-for-spo-odb-and-teams.md)</li><li>[<span data-ttu-id="b6701-222">ATP のフィッシング対策保護</span><span class="sxs-lookup"><span data-stu-id="b6701-222">ATP anti-phishing protection</span></span>](set-up-anti-phishing-policies.md#exclusive-settings-in-atp-anti-phishing-policies)</li><li>[<span data-ttu-id="b6701-223">リアルタイムの検出</span><span class="sxs-lookup"><span data-stu-id="b6701-223">Real-time detections</span></span>](threat-explorer.md)</li></ul>|<span data-ttu-id="b6701-224">Office 365 ATP プラン 1 の機能</span><span class="sxs-lookup"><span data-stu-id="b6701-224">Office 365 ATP Plan 1 capabilities</span></span><br/><span data-ttu-id="b6701-225">--- プラスのもの ---</span><span class="sxs-lookup"><span data-stu-id="b6701-225">--- plus ---</span></span><br/><span data-ttu-id="b6701-226">自動化、調査、修復、教育の機能:</span><span class="sxs-lookup"><span data-stu-id="b6701-226">Automation, investigation, remediation, and education capabilities:</span></span></li><li>[<span data-ttu-id="b6701-227">脅威トラッカー</span><span class="sxs-lookup"><span data-stu-id="b6701-227">Threat Trackers</span></span>](threat-trackers.md)</li><li>[<span data-ttu-id="b6701-228">脅威エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="b6701-228">Threat Explorer</span></span>](threat-explorer.md)</li><li>[<span data-ttu-id="b6701-229">自動調査および対応</span><span class="sxs-lookup"><span data-stu-id="b6701-229">Automated investigation and response</span></span>](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air)</li><li>[<span data-ttu-id="b6701-230">攻撃シミュレータ</span><span class="sxs-lookup"><span data-stu-id="b6701-230">Attack Simulator</span></span>](attack-simulator.md)</li></ul>|
|

- <span data-ttu-id="b6701-231">Office 365 ATP プラン 2 は、Office 365 E5、Office 365 A5、および Microsoft 365 E5 に含まれています。</span><span class="sxs-lookup"><span data-stu-id="b6701-231">Office 365 ATP Plan 2 is included in Office 365 E5, Office 365 A5, and Microsoft 365 E5.</span></span>

- <span data-ttu-id="b6701-232">Office 365 ATP プラン 1 は、Microsoft 365 Business Premium に含まれています。</span><span class="sxs-lookup"><span data-stu-id="b6701-232">Office 365 ATP Plan 1 is included in Microsoft 365 Business Premium.</span></span>

- <span data-ttu-id="b6701-233">Office 365 ATP プラン 1 および Office 365 ATP プラン 2 は、それぞれ特定のサブスクリプションのアドオンとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="b6701-233">Office 365 ATP Plan 1 and Office 365 ATP Plan 2 are each available as an add-on for certain subscriptions.</span></span> <span data-ttu-id="b6701-234">詳細については、次のリンク [機能が ATP プラン全体で利用可能](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans)です。</span><span class="sxs-lookup"><span data-stu-id="b6701-234">To learn more, here's another link [Feature availability across ATP plans](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).</span></span>

- <span data-ttu-id="b6701-235">[安全なドキュメント](safe-docs.md)機能は、Microsoft 365 E5 または Microsoft 365 E5 セキュリティ ライセンス (Office 365 ATP プランには含まれません) を持つユーザーのみが利用できます。</span><span class="sxs-lookup"><span data-stu-id="b6701-235">The [Safe Documents](safe-docs.md) feature is only available to users with the Microsoft 365 E5 or Microsoft 365 E5 Security licenses (not included in Office 365 ATP plans).</span></span>

- <span data-ttu-id="b6701-236">現在のサブスクリプションに Office 365 ATP が含まれておらず、これを使用する場合は、 [販売に連絡して試用版を開始](https://go.microsoft.com/fwlink/p/?LinkId=518644)し、atp が組織内でどのように動作するかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b6701-236">If your current subscription doesn't include Office 365 ATP and you want it, [contact sales to start a trial](https://go.microsoft.com/fwlink/p/?LinkId=518644), and find out how ATP can work for in your organization.</span></span>

> [!TIP]
> <span data-ttu-id="b6701-237">***Insider ヒント***。</span><span class="sxs-lookup"><span data-stu-id="b6701-237">***Insider tip***.</span></span> <span data-ttu-id="b6701-238">EOP と ATP の詳細については、docs.microsoft.com の目次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6701-238">You can use the docs.microsoft.com table of contents to learn about EOP and ATP.</span></span> <span data-ttu-id="b6701-239">[Office 365 のセキュリティ](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap?view=o365-worldwide)記事に移動すると、目次組織が評価と展開 (移行を含む) で開始され、予防、検出、調査、および応答が続くことがわかります。</span><span class="sxs-lookup"><span data-stu-id="b6701-239">Navigate to [Office 365 Security](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap?view=o365-worldwide) articles, and you'll notice that table of contents organization begins with Evaluation and Deployment (including migration) and then continues into prevention, detection, investigation, and response.</span></span> <p> <span data-ttu-id="b6701-240">この構造体は、 **セキュリティ管理** のトピックの後に **セキュリティの運用** に関するトピックが表示されるように分割されています。</span><span class="sxs-lookup"><span data-stu-id="b6701-240">This structure is divided so that **Security Administration** topics are followed by **Security Operations** topics.</span></span> <span data-ttu-id="b6701-241">いずれかのジョブロールの新しいメンバーである場合は、スペースの理解に役立つように、このヒントのリンクと目次の情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="b6701-241">If you're a new member of either job role, use the link in this tip, and your knowledge of the table of contents, to help learn the space.</span></span> <span data-ttu-id="b6701-242">*フィードバックリンク*を必ず使用し、*記事*を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6701-242">Remember to use *feedback links* and *rate articles* as you go.</span></span> <span data-ttu-id="b6701-243">フィードバックは、弊社が提供するものを改善するのに役立つ情報です。</span><span class="sxs-lookup"><span data-stu-id="b6701-243">Feedback helps us improve what we offer you.</span></span>