---
title: 電子メール保護の順序と優先順位
keywords: セキュリティ, マルウェア, Microsoft 365, M365, security center, ATP, Microsoft Defender ATP, Office 365 ATP, Azure ATP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: 管理者は、Exchange Online Protection (EOP) の保護のアプリケーションの順序と、保護ポリシーの優先度の値によって適用されるポリシーがどのように決定されるのかについて説明します。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b2a72420340993c027ec99820dcd3edddab1a304
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51063355"
---
# <a name="order-and-precedence-of-email-protection"></a><span data-ttu-id="7bcff-104">電子メール保護の順序と優先順位</span><span class="sxs-lookup"><span data-stu-id="7bcff-104">Order and precedence of email protection</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

<span data-ttu-id="7bcff-105">**適用対象**</span><span class="sxs-lookup"><span data-stu-id="7bcff-105">**Applies to**</span></span>
- [<span data-ttu-id="7bcff-106">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="7bcff-106">Exchange Online Protection</span></span>](exchange-online-protection-overview.md)
- [<span data-ttu-id="7bcff-107">Microsoft Defender for Office 365 プラン 1 およびプラン 2</span><span class="sxs-lookup"><span data-stu-id="7bcff-107">Microsoft Defender for Office 365 plan 1 and plan 2</span></span>](defender-for-office-365.md)
- [<span data-ttu-id="7bcff-108">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="7bcff-108">Microsoft 365 Defender</span></span>](../defender/microsoft-365-defender.md)

<span data-ttu-id="7bcff-109">Exchange Online またはスタンドアロンの Exchange Online Protection (EOP) 組織に Exchange Online メールボックスがない Microsoft 365 組織では、受信メールに複数の形式の保護のフラグが設定されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="7bcff-109">In Microsoft 365 organizations with mailboxes in Exchange Online or standalone Exchange Online Protection (EOP) organizations without Exchange Online mailboxes, inbound email may be flagged by multiple forms of protection.</span></span> <span data-ttu-id="7bcff-110">たとえば、すべての Microsoft 365 のお客様が利用できる EOP に組み込みのフィッシング対策ポリシーや、Office 365 のお客様に対して Microsoft Defender で利用できるより堅牢なフィッシング対策ポリシーなどです。</span><span class="sxs-lookup"><span data-stu-id="7bcff-110">For example, the built-in anti-phishing policies in EOP that are available to all Microsoft 365 customers, and the more robust anti-phishing policies that are available to Microsoft Defender for Office 365 customers.</span></span> <span data-ttu-id="7bcff-111">メッセージは、マルウェア、スパム、フィッシングなどの複数の検出スキャンも通過します。このすべてのアクティビティを考えると、どのポリシーが適用されるのかという混乱が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7bcff-111">Messages also pass through multiple detection scans for malware, spam, phishing, etc. Given all this activity, there may be some confusion as to which policy is applied.</span></span>

<span data-ttu-id="7bcff-112">一般に、メッセージに適用されるポリシーは **、CAT (Category)** プロパティの **X-Forefront-Antispam-Report** ヘッダーで識別されます。</span><span class="sxs-lookup"><span data-stu-id="7bcff-112">In general, a policy that's applied to a message is identified in the **X-Forefront-Antispam-Report** header in the **CAT (Category)** property.</span></span> <span data-ttu-id="7bcff-113">詳細については、「[スパム対策メッセージ ヘッダー](anti-spam-message-headers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7bcff-113">For more information, see [Anti-spam message headers](anti-spam-message-headers.md).</span></span>

<span data-ttu-id="7bcff-114">メッセージに適用されるポリシーを決定する主な要因は次の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="7bcff-114">There are two major factors that determine which policy is applied to a message:</span></span>

- <span data-ttu-id="7bcff-115">**電子メール保護の種類の優先度**: この順序は構成できません。次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="7bcff-115">**The priority of the email protection type**: This order is not configurable, and is described in the following table:</span></span>

  ****

  |<span data-ttu-id="7bcff-116">Priority</span><span class="sxs-lookup"><span data-stu-id="7bcff-116">Priority</span></span>|<span data-ttu-id="7bcff-117">電子メールの保護</span><span class="sxs-lookup"><span data-stu-id="7bcff-117">Email protection</span></span>|<span data-ttu-id="7bcff-118">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="7bcff-118">Category</span></span>|<span data-ttu-id="7bcff-119">管理する場所</span><span class="sxs-lookup"><span data-stu-id="7bcff-119">Where to manage</span></span>|
  |---|---|---|---|
  |<span data-ttu-id="7bcff-120">1</span><span class="sxs-lookup"><span data-stu-id="7bcff-120">1</span></span>|<span data-ttu-id="7bcff-121">マルウェア</span><span class="sxs-lookup"><span data-stu-id="7bcff-121">Malware</span></span>|<span data-ttu-id="7bcff-122">CAT:MALW</span><span class="sxs-lookup"><span data-stu-id="7bcff-122">CAT:MALW</span></span>|[<span data-ttu-id="7bcff-123">EOP でマルウェア対策ポリシーを構成する</span><span class="sxs-lookup"><span data-stu-id="7bcff-123">Configure anti-malware policies in EOP</span></span>](configure-anti-malware-policies.md)|
  |<span data-ttu-id="7bcff-124">2</span><span class="sxs-lookup"><span data-stu-id="7bcff-124">2</span></span>|<span data-ttu-id="7bcff-125">フィッシング</span><span class="sxs-lookup"><span data-stu-id="7bcff-125">Phishing</span></span>|<span data-ttu-id="7bcff-126">CAT:PHSH</span><span class="sxs-lookup"><span data-stu-id="7bcff-126">CAT:PHSH</span></span>|[<span data-ttu-id="7bcff-127">EOP でのスパム対策ポリシーの構成</span><span class="sxs-lookup"><span data-stu-id="7bcff-127">Configure anti-spam policies in EOP</span></span>](configure-your-spam-filter-policies.md)|
  |<span data-ttu-id="7bcff-128">3</span><span class="sxs-lookup"><span data-stu-id="7bcff-128">3</span></span>|<span data-ttu-id="7bcff-129">高確度スパム</span><span class="sxs-lookup"><span data-stu-id="7bcff-129">High confidence spam</span></span>|<span data-ttu-id="7bcff-130">CAT:HSPM</span><span class="sxs-lookup"><span data-stu-id="7bcff-130">CAT:HSPM</span></span>|[<span data-ttu-id="7bcff-131">EOP でのスパム対策ポリシーの構成</span><span class="sxs-lookup"><span data-stu-id="7bcff-131">Configure anti-spam policies in EOP</span></span>](configure-your-spam-filter-policies.md)|
  |<span data-ttu-id="7bcff-132">4</span><span class="sxs-lookup"><span data-stu-id="7bcff-132">4</span></span>|<span data-ttu-id="7bcff-133">スプーフィング</span><span class="sxs-lookup"><span data-stu-id="7bcff-133">Spoofing</span></span>|<span data-ttu-id="7bcff-134">CAT:スプーフィング</span><span class="sxs-lookup"><span data-stu-id="7bcff-134">CAT:SPOOF</span></span>|[<span data-ttu-id="7bcff-135">EOP でスプーフィング インテリジェンスを構成する</span><span class="sxs-lookup"><span data-stu-id="7bcff-135">Configure spoof intelligence in EOP</span></span>](learn-about-spoof-intelligence.md)|
  |<span data-ttu-id="7bcff-136">5<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="7bcff-136">5<sup>\*</sup></span></span>|<span data-ttu-id="7bcff-137">ユーザー偽装 (保護されたユーザー)</span><span class="sxs-lookup"><span data-stu-id="7bcff-137">User impersonation (protected users)</span></span>|<span data-ttu-id="7bcff-138">UIMP</span><span class="sxs-lookup"><span data-stu-id="7bcff-138">UIMP</span></span>|[<span data-ttu-id="7bcff-139">Microsoft Defender でフィッシング対策ポリシーを構成する (Office 365)</span><span class="sxs-lookup"><span data-stu-id="7bcff-139">Configure anti-phishing policies in Microsoft Defender for Office 365</span></span>](configure-atp-anti-phishing-policies.md)|
  |<span data-ttu-id="7bcff-140">6<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="7bcff-140">6<sup>\*</sup></span></span>|<span data-ttu-id="7bcff-141">ドメイン偽装 (保護されたドメイン)</span><span class="sxs-lookup"><span data-stu-id="7bcff-141">Domain impersonation (protected domains)</span></span>|<span data-ttu-id="7bcff-142">DIMP</span><span class="sxs-lookup"><span data-stu-id="7bcff-142">DIMP</span></span>|[<span data-ttu-id="7bcff-143">Microsoft Defender でフィッシング対策ポリシーを構成する (Office 365)</span><span class="sxs-lookup"><span data-stu-id="7bcff-143">Configure anti-phishing policies in Microsoft Defender for Office 365</span></span>](configure-atp-anti-phishing-policies.md)|
  |<span data-ttu-id="7bcff-144">7</span><span class="sxs-lookup"><span data-stu-id="7bcff-144">7</span></span>|<span data-ttu-id="7bcff-145">スパム</span><span class="sxs-lookup"><span data-stu-id="7bcff-145">Spam</span></span>|<span data-ttu-id="7bcff-146">CAT:SPM</span><span class="sxs-lookup"><span data-stu-id="7bcff-146">CAT:SPM</span></span>|[<span data-ttu-id="7bcff-147">EOP でのスパム対策ポリシーの構成</span><span class="sxs-lookup"><span data-stu-id="7bcff-147">Configure anti-spam policies in EOP</span></span>](configure-your-spam-filter-policies.md)|
  |<span data-ttu-id="7bcff-148">8</span><span class="sxs-lookup"><span data-stu-id="7bcff-148">8</span></span>|<span data-ttu-id="7bcff-149">バルク</span><span class="sxs-lookup"><span data-stu-id="7bcff-149">Bulk</span></span>|<span data-ttu-id="7bcff-150">CAT:BULK</span><span class="sxs-lookup"><span data-stu-id="7bcff-150">CAT:BULK</span></span>|[<span data-ttu-id="7bcff-151">EOP でのスパム対策ポリシーの構成</span><span class="sxs-lookup"><span data-stu-id="7bcff-151">Configure anti-spam policies in EOP</span></span>](configure-your-spam-filter-policies.md)|
  |

  <span data-ttu-id="7bcff-152"><sup>\*</sup> これらの機能は、365 の Microsoft Defender のフィッシング対策Officeです。</span><span class="sxs-lookup"><span data-stu-id="7bcff-152"><sup>\*</sup> These features are only available in anti-phishing policies in Microsoft Defender for Office 365.</span></span>

- <span data-ttu-id="7bcff-153">**ポリシー** の優先度 : 保護の種類 (スパム対策、マルウェア対策、フィッシング対策など) ごとに、すべてのユーザーに適用される既定のポリシーがありますが、特定のユーザーに適用されるカスタム ポリシーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7bcff-153">**The priority of the policy**: For each protection type (anti-spam, anti-malware, anti-phishing, etc.), there's a default policy that applies to everyone, but you can create custom policies that apply to specific users.</span></span> <span data-ttu-id="7bcff-154">各カスタム ポリシーには、ポリシーが適用される順序を決定する優先度の値があります。</span><span class="sxs-lookup"><span data-stu-id="7bcff-154">Each custom policy has a priority value that determines the order that the policies are applied in.</span></span> <span data-ttu-id="7bcff-155">既定のポリシーは常に最後に適用されます。</span><span class="sxs-lookup"><span data-stu-id="7bcff-155">The default policy is always applied last.</span></span>

  <span data-ttu-id="7bcff-156">ユーザーが同じ種類の複数のポリシーで定義されている場合、優先度が最も高いポリシーだけが適用されます。</span><span class="sxs-lookup"><span data-stu-id="7bcff-156">If a user is defined in multiple policies of the same type, only the policy with the highest priority is applied to them.</span></span> <span data-ttu-id="7bcff-157">その種類の残りのポリシーは、ユーザーに対して評価されません (既定のポリシーを含む)。</span><span class="sxs-lookup"><span data-stu-id="7bcff-157">Any remaining policies of that type are not evaluated for the user (including the default policy).</span></span>

<span data-ttu-id="7bcff-158">たとえば、同じユーザーに適用される Office 365 の Microsoft Defender の次のフィッシング対策ポリシーと、ユーザー偽装とスプーフィングの両方として識別されるメッセージを検討します。</span><span class="sxs-lookup"><span data-stu-id="7bcff-158">For example, consider the following anti-phishing policies in Microsoft Defender for Office 365 **that apply to the same users**, and a message that's identified as both user impersonation and spoofing:</span></span>

  ****

  |<span data-ttu-id="7bcff-159">ポリシー名</span><span class="sxs-lookup"><span data-stu-id="7bcff-159">Policy name</span></span>|<span data-ttu-id="7bcff-160">Priority</span><span class="sxs-lookup"><span data-stu-id="7bcff-160">Priority</span></span>|<span data-ttu-id="7bcff-161">ユーザー偽装</span><span class="sxs-lookup"><span data-stu-id="7bcff-161">User impersonation</span></span>|<span data-ttu-id="7bcff-162">スプーフィング対策</span><span class="sxs-lookup"><span data-stu-id="7bcff-162">Anti-spoofing</span></span>|
  |---|---|---|---|
  |<span data-ttu-id="7bcff-163">ポリシー A</span><span class="sxs-lookup"><span data-stu-id="7bcff-163">Policy A</span></span>|<span data-ttu-id="7bcff-164">1</span><span class="sxs-lookup"><span data-stu-id="7bcff-164">1</span></span>|<span data-ttu-id="7bcff-165">オン</span><span class="sxs-lookup"><span data-stu-id="7bcff-165">On</span></span>|<span data-ttu-id="7bcff-166">オフ</span><span class="sxs-lookup"><span data-stu-id="7bcff-166">Off</span></span>|
  |<span data-ttu-id="7bcff-167">ポリシー B</span><span class="sxs-lookup"><span data-stu-id="7bcff-167">Policy B</span></span>|<span data-ttu-id="7bcff-168">2</span><span class="sxs-lookup"><span data-stu-id="7bcff-168">2</span></span>|<span data-ttu-id="7bcff-169">オフ</span><span class="sxs-lookup"><span data-stu-id="7bcff-169">Off</span></span>|<span data-ttu-id="7bcff-170">オン</span><span class="sxs-lookup"><span data-stu-id="7bcff-170">On</span></span>|
  |

1. <span data-ttu-id="7bcff-171">スプーフィングの優先度がユーザー偽装 (5) よりも高い (4) ため、メッセージはスプーフィングとしてマークされ、処理されます。</span><span class="sxs-lookup"><span data-stu-id="7bcff-171">The message is marked and treated as spoof, because spoofing has a higher priority (4) than user impersonation (5).</span></span>
2. <span data-ttu-id="7bcff-172">ポリシー A はポリシー B よりも優先度が高いので、ユーザーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="7bcff-172">Policy A is applied to the users because it has a higher priority than Policy B.</span></span>
3. <span data-ttu-id="7bcff-173">ポリシー A の設定に基づいて、ポリシーでスプーフィング対策がオフになっているため、メッセージに対してアクションは実行されません。</span><span class="sxs-lookup"><span data-stu-id="7bcff-173">Based on the settings in Policy A, no action is taken on the message, because anti-spoofing is turned off in the policy.</span></span>
4. <span data-ttu-id="7bcff-174">ポリシー処理が停止し、ポリシー B はユーザーに適用されません。</span><span class="sxs-lookup"><span data-stu-id="7bcff-174">Policy processing stops, so Policy B is never applied to the users.</span></span>

<span data-ttu-id="7bcff-175">同じユーザーが意図的または意図せずに同じ種類の複数のカスタム ポリシーに含まれている可能性がある場合は、カスタム ポリシーに次の設計ガイドラインを使用します。</span><span class="sxs-lookup"><span data-stu-id="7bcff-175">Because it's possible that the same users are intentionally or unintentionally included in multiple custom policies of the same type, use the following design guidelines for custom policies:</span></span>

- <span data-ttu-id="7bcff-176">少人数のユーザーに適用されるポリシーに高い優先度を割り当て、多数のユーザーに適用されるポリシーに対する優先度を低くします。</span><span class="sxs-lookup"><span data-stu-id="7bcff-176">Assign a higher priority to policies that apply to a small number of users, and a lower priority to policies that apply to a large number of users.</span></span> <span data-ttu-id="7bcff-177">既定のポリシーは常に最後に適用されます。</span><span class="sxs-lookup"><span data-stu-id="7bcff-177">Remember, the default policy is always applied last.</span></span>
- <span data-ttu-id="7bcff-178">優先度の高いポリシーを構成して、優先度の低いポリシーよりも厳密な設定またはより特殊な設定を設定します。</span><span class="sxs-lookup"><span data-stu-id="7bcff-178">Configure your higher priority policies to have stricter or more specialized settings than lower priority policies.</span></span>
- <span data-ttu-id="7bcff-179">使用するカスタム ポリシーの数を少なくします (より厳密な設定またはより特殊な設定が必要なユーザーに対してカスタム ポリシーのみを使用してください)。</span><span class="sxs-lookup"><span data-stu-id="7bcff-179">Consider using fewer custom policies (only use custom policies for users who require stricter or more specialized settings).</span></span>