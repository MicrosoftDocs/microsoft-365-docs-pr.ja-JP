---
title: 機密ラベルをコンテンツに自動的に適用する
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.service: O365-seccomp
ms.date: ''
localization_priority: Priority
ms.collection:
- M365-security-compliance
ms.topic: article
search.appverid:
- MOE150
- MET150
description: 機密ラベルを作成する場合、ドキュメントまたは電子メールにラベルを自動的に割り当てるか、あるいは推奨するラベルを選択するようにユーザーに求めることができます。
ms.openlocfilehash: 705752a63d3cd1ca5f6950643648ba5c3dd50336
ms.sourcegitcommit: 38d828ae8d4350ae774a939c8decf30cb36c3bea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2020
ms.locfileid: "49551348"
---
# <a name="apply-a-sensitivity-label-to-content-automatically"></a><span data-ttu-id="52dc8-103">機密ラベルをコンテンツに自動的に適用する</span><span class="sxs-lookup"><span data-stu-id="52dc8-103">Apply a sensitivity label to content automatically</span></span>

><span data-ttu-id="52dc8-104">*[セキュリティとコンプライアンスのための Microsoft 365 ライセンス ガイダンス](https://aka.ms/ComplianceSD)。*</span><span class="sxs-lookup"><span data-stu-id="52dc8-104">*[Microsoft 365 licensing guidance for security & compliance](https://aka.ms/ComplianceSD).*</span></span>

<span data-ttu-id="52dc8-105">機密ラベルを作成する場合、指定した条件に一致したときに、そのラベルをコンテンツに自動的に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-105">When you create a sensitivity label, you can automatically assign that label to content when it matches conditions that you specify.</span></span>

<span data-ttu-id="52dc8-106">機密ラベルを自動的にコンテンツに適用する機能が重要である理由は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="52dc8-106">The ability to apply sensitivity labels to content automatically is important because:</span></span>

- <span data-ttu-id="52dc8-107">ユーザーのトレーニングは、一部の分類方法をいつ使用するかについてのみ必要。</span><span class="sxs-lookup"><span data-stu-id="52dc8-107">You don't need to train your users when to use each of your classifications.</span></span>

- <span data-ttu-id="52dc8-108">ユーザーへの依存は、一部のコンテンツを正しく分類するためにのみ必要。</span><span class="sxs-lookup"><span data-stu-id="52dc8-108">You don't need to rely on users to classify all content correctly.</span></span>

- <span data-ttu-id="52dc8-109">ユーザーはポリシーについて把握する必要がなくなり、自分たちの仕事に集中できます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-109">Users no longer need to know about your policies—they can instead focus on their work.</span></span>

<span data-ttu-id="52dc8-110">コンテンツが手動でラベル付けされている場合、そのラベルが自動ラベル付けで置き換えられることはありません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-110">When content has been manually labeled, that label will never be replaced by automatic labeling.</span></span> <span data-ttu-id="52dc8-111">ただし、自動ラベル付けは、自動的に適用された[優先度が低いラベル](sensitivity-labels.md#label-priority-order-matters)を置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-111">However, automatic labeling can replace a [lower priority label](sensitivity-labels.md#label-priority-order-matters) that was automatically applied.</span></span>

<span data-ttu-id="52dc8-112">機密ラベルを自動的に適用するには、次の 2 つの異なる方法があります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-112">There are two different methods for automatically applying a sensitivity label:</span></span>

- <span data-ttu-id="52dc8-113">**ユーザーがドキュメントを編集したり、メールを作成 (返信または転送) するときのクライアント側のラベル付け**: Office アプリ (Word、Excel、PowerPoint、Outlook) の自動ラベル付け用に構成されたラベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-113">**Client-side labeling when users edit documents or compose (also reply or forward) emails**: Use a label that's configured for auto-labeling for Office apps (Word, Excel, PowerPoint, and Outlook).</span></span> 
    
    <span data-ttu-id="52dc8-114">この方法は、ユーザーへのラベルの推奨と、ラベルの自動適用をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="52dc8-114">This method supports recommending a label to users, as well as automatically applying a label.</span></span> <span data-ttu-id="52dc8-115">ただし、どちらの場合も、ユーザーはラベルを承諾または拒否するかどうかを決定し、コンテンツの正しいラベル付けを行います。</span><span class="sxs-lookup"><span data-stu-id="52dc8-115">But in both cases, the user decides whether to accept or reject the label, to help ensure the correct labeling of content.</span></span> <span data-ttu-id="52dc8-116">このクライアント側のラベル付けでは、ドキュメントを保存する前であってもラベルを適用できるため、ドキュメントの遅延が最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-116">This client-side labeling has minimal delay for documents because the label can be applied even before the document is saved.</span></span> <span data-ttu-id="52dc8-117">ただし、すべてのクライアント アプリが自動ラベル付けをサポートしているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-117">However, not all client apps support auto-labeling.</span></span> <span data-ttu-id="52dc8-118">この機能は、Azure Information Protection 統合ラベル付けクライアント、および [Office の一部のバージョン](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps)でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="52dc8-118">This capability is supported by the Azure Information Protection unified labeling client, and [some versions of Office](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).</span></span> 
    
    <span data-ttu-id="52dc8-119">構成手順については、このページの「[Office アプリの自動ラベル付けを構成する方法](#how-to-configure-auto-labeling-for-office-apps)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-119">For configuration instructions, see [How to configure auto-labeling for Office apps](#how-to-configure-auto-labeling-for-office-apps) on this page.</span></span>

- <span data-ttu-id="52dc8-120">**コンテンツが既に保存されている (SharePoint または OneDrive で) またはメールで送信された (Exchange Online によって処理される) サービス側のラベル付け**: 自動ラベル付けポリシーを使用します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-120">**Service-side labeling when content is already saved (in SharePoint or OneDrive) or emailed (processed by Exchange Online)**: Use an auto-labeling policy.</span></span> 
    
    <span data-ttu-id="52dc8-121">この方法は、保存データ (SharePoint および OneDrive のドキュメント) や転送中のデータ (Exchange によって送信または受信されたメール) の自動ラベル付けと呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-121">You might also hear this method referred to as auto-labeling for data at rest (documents in SharePoint and OneDrive) and data in transit (email that is sent or received by Exchange).</span></span> <span data-ttu-id="52dc8-122">Exchange の場合、保存されているメール (メールボックス) は含まれません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-122">For Exchange, it doesn't include emails at rest (mailboxes).</span></span> 
    
    <span data-ttu-id="52dc8-123">このラベル付けはアプリケーションではなくサービスによって適用されるため、ユーザーが使用しているアプリやバージョンを気にする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-123">Because this labeling is applied by services rather than by applications, you don't need to worry about what apps users have and what version.</span></span> <span data-ttu-id="52dc8-124">その結果、この機能は、組織全体ですぐに使用できるようになります。また、規模に応じたラベル付けに適しています。</span><span class="sxs-lookup"><span data-stu-id="52dc8-124">As a result, this capability is immediately available throughout your organization and suitable for labeling at scale.</span></span> <span data-ttu-id="52dc8-125">自動ラベル付けポリシーでは、ユーザーがラベル付けプロセスを操作しないので、推奨されるラベル付けをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-125">Auto-labeling policies don't support recommended labeling because the user doesn't interact with the labeling process.</span></span> <span data-ttu-id="52dc8-126">代わりに、管理者は、実際にラベルを適用する前に、コンテンツの正しいラベル付けを行うために、シミュレーション モードでポリシーを実行します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-126">Instead, the administrator runs the policies in simulation mode to help ensure the correct labeling of content before actually applying the label.</span></span>
    
    <span data-ttu-id="52dc8-127">構成手順については、このページの「[SharePoint、OneDrive、Exchange の自動ラベル付けポリシーを構成する方法](#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-127">For configuration instructions, see [How to configure auto-labeling policies for SharePoint, OneDrive, and Exchange](#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) on this page.</span></span>
    
    <span data-ttu-id="52dc8-128">SharePoint と OneDrive の自動ラベル付けに固有:</span><span class="sxs-lookup"><span data-stu-id="52dc8-128">Specific to auto-labeling for SharePoint and OneDrive:</span></span>
    - <span data-ttu-id="52dc8-129">Word、PowerPoint、Excel の Office ファイルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="52dc8-129">Office files for Word, PowerPoint, and Excel are supported.</span></span> <span data-ttu-id="52dc8-130">Open XML 形式 (.docx や .xlsx など) はサポートされていますが、Microsoft Office 97-2003 形式 (.doc や .xls など) はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-130">Open XML format is supported (such as .docx and .xlsx) but not Microsoft Office 97-2003 format (such as .doc and .xls).</span></span>
    - <span data-ttu-id="52dc8-131">テナント内で 1 日あたり最大 25,000 個の自動的にラベル付けされたファイル。</span><span class="sxs-lookup"><span data-stu-id="52dc8-131">Maximum of 25,000 automatically labeled files in your tenant per day.</span></span>
    - <span data-ttu-id="52dc8-132">テナントあたり最大 10 個の自動ラベル付けポリシーが作成されます。各ポリシーは、最大 10 サイト (SharePoint サイトまたは OneDrive サイト) を対象としています。</span><span class="sxs-lookup"><span data-stu-id="52dc8-132">Maximum of 10 auto-labeling policies per tenant, each targeting up to 10 sites (SharePoint or OneDrive).</span></span>
    - <span data-ttu-id="52dc8-133">シミュレーション モードの場合、およびラベルが適用される場合、自動ラベル付けポリシーの結果として、変更、変更者、変更日の既存の値は変更されません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-133">Existing values for modified, modified by, and the date are not changed as a result of auto-labeling policies—for both simulation mode and when labels are applied.</span></span>
    - <span data-ttu-id="52dc8-134">ラベルが暗号化を適用する場合、[Rights Management 発行者と Rights Management 所有者](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) は、ファイルを最後に変更したアカウントです。</span><span class="sxs-lookup"><span data-stu-id="52dc8-134">When the label applies encryption, the [Rights Management issuer and Rights Management owner](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) is the account that last modified the file.</span></span>

    <span data-ttu-id="52dc8-135">Exchange の自動ラベル付けに固有:</span><span class="sxs-lookup"><span data-stu-id="52dc8-135">Specific to auto-labeling for Exchange:</span></span>
    - <span data-ttu-id="52dc8-136">手動でのラベル付けや Office アプリを使用した自動ラベル付けとは異なり、Office の添付ファイル (Word、Excel、PowerPoint ファイル) および PDF の添付ファイルも自動ラベル付けポリシーで指定した条件に合わせてスキャンされます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-136">Unlike manual labeling or auto-labeling with Office apps, Office attachments (Word, Excel, and PowerPoint files) and PDF attachments are also scanned for the conditions you specify in your auto-labeling policy.</span></span> <span data-ttu-id="52dc8-137">一致がある場合、メールにはラベルが付けられますが、添付ファイルにはラベルが付けられません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-137">When there is a match, the email is labeled but not the attachment.</span></span>
        - <span data-ttu-id="52dc8-138">Office ファイルの場合、Open XML 形式 (.docx や .xlsx など) はサポートされていますが、Microsoft Office 97-2003 形式 (.doc や .xls など) はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-138">For these Office files, Open XML format is supported (such as .docx and .xlsx) but not Microsoft Office 97-2003 format (such as .doc and .xls).</span></span>
    - <span data-ttu-id="52dc8-139">IRM 暗号化を適用する Exchange メール フロー ルールまたはデータ損失防止 (DLP) ポリシーがある場合: これらのルールやポリシーおよび自動ラベル付けポリシーによってコンテンツが識別されると、ラベルが適用されます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-139">If you have Exchange mail flow rules or data loss prevention (DLP) policies that apply IRM encryption: When content is identified by these rules or policies and an auto-labeling policy, the label is applied.</span></span> <span data-ttu-id="52dc8-140">このラベルが暗号化を適用すると、Exchange メール フロー ルールまたは DLP ポリシーの IRM 設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-140">If that label applies encryption, the IRM settings from the Exchange mail flow rules or DLP policies are ignored.</span></span> <span data-ttu-id="52dc8-141">ただし、そのラベルが暗号化を適用しない場合、メール フロー ルールまたは DLP ポリシーの IRM 設定がラベルに加えて適用されます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-141">However, if that label doesn't apply encryption, the IRM settings from the mail flow rules or DLP policies are applied in addition to the label.</span></span>
    - <span data-ttu-id="52dc8-142">ラベルが表示されない IRM 暗号化を使用しているメールは、自動ラベル付けを使用すると一致する場合は、暗号化設定のあるラベルに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-142">Email that has IRM encryption with no label will be replaced by a label with any encryption settings when there is a match by using auto-labeling.</span></span>
    - <span data-ttu-id="52dc8-143">自動ラベル付け条件と一致すると、受信メールにラベルが付けられます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-143">Incoming email is labeled when there is a match with your auto-labeling conditions.</span></span> <span data-ttu-id="52dc8-144">ただし、ラベルが暗号化用に構成されている場合、その暗号化は適用されません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-144">However, if the label is configured for encryption, that encryption isn't applied.</span></span>
    - <span data-ttu-id="52dc8-145">ラベルが暗号化を適用する場合、[Rights Management 発行者と Rights Management 所有者](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) は、メールを送信するユーザーです。</span><span class="sxs-lookup"><span data-stu-id="52dc8-145">When the label applies encryption, the [Rights Management issuer and Rights Management owner](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) is the person who sends the email.</span></span>
    

## <a name="compare-auto-labeling-for-office-apps-with-auto-labeling-policies"></a><span data-ttu-id="52dc8-146">Office アプリの自動ラベル付けと自動ラベル付けポリシーを比較する</span><span class="sxs-lookup"><span data-stu-id="52dc8-146">Compare auto-labeling for Office apps with auto-labeling policies</span></span>

<span data-ttu-id="52dc8-147">次の表は、2 つの相補的な自動ラベル付け方法の違いを特定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-147">Use the following table to help you identify the differences in behavior for the two complementary automatic labeling methods:</span></span>

|<span data-ttu-id="52dc8-148">機能または動作</span><span class="sxs-lookup"><span data-stu-id="52dc8-148">Feature or behavior</span></span>|<span data-ttu-id="52dc8-149">ラベル設定: Office アプリの自動ラベル付け</span><span class="sxs-lookup"><span data-stu-id="52dc8-149">Label setting: Auto-labeling for Office apps</span></span> |<span data-ttu-id="52dc8-150">ポリシー: 自動ラベル付け</span><span class="sxs-lookup"><span data-stu-id="52dc8-150">Policy: Auto-labeling</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="52dc8-151">アプリの依存関係</span><span class="sxs-lookup"><span data-stu-id="52dc8-151">App dependency</span></span>|[<span data-ttu-id="52dc8-152">はい</span><span class="sxs-lookup"><span data-stu-id="52dc8-152">Yes</span></span>](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) |<span data-ttu-id="52dc8-153">いいえ \*</span><span class="sxs-lookup"><span data-stu-id="52dc8-153">No \*</span></span> |
|<span data-ttu-id="52dc8-154">場所による制限</span><span class="sxs-lookup"><span data-stu-id="52dc8-154">Restrict by location</span></span>|<span data-ttu-id="52dc8-155">いいえ</span><span class="sxs-lookup"><span data-stu-id="52dc8-155">No</span></span> |<span data-ttu-id="52dc8-156">はい</span><span class="sxs-lookup"><span data-stu-id="52dc8-156">Yes</span></span> |
|<span data-ttu-id="52dc8-157">条件: トレーニング可能な分類子</span><span class="sxs-lookup"><span data-stu-id="52dc8-157">Conditions: Trainable classifiers</span></span>|<span data-ttu-id="52dc8-158">はい</span><span class="sxs-lookup"><span data-stu-id="52dc8-158">Yes</span></span> |<span data-ttu-id="52dc8-159">いいえ</span><span class="sxs-lookup"><span data-stu-id="52dc8-159">No</span></span> |
|<span data-ttu-id="52dc8-160">条件: メールの共有オプションと追加オプション</span><span class="sxs-lookup"><span data-stu-id="52dc8-160">Conditions: Sharing options and additional options for email</span></span>|<span data-ttu-id="52dc8-161">いいえ</span><span class="sxs-lookup"><span data-stu-id="52dc8-161">No</span></span> |<span data-ttu-id="52dc8-162">はい</span><span class="sxs-lookup"><span data-stu-id="52dc8-162">Yes</span></span> |
|<span data-ttu-id="52dc8-163">推奨事項、ポリシーのヒント、ユーザー上書き</span><span class="sxs-lookup"><span data-stu-id="52dc8-163">Recommendations, policy tooltip, and user overrides</span></span>|<span data-ttu-id="52dc8-164">はい</span><span class="sxs-lookup"><span data-stu-id="52dc8-164">Yes</span></span> |<span data-ttu-id="52dc8-165">いいえ</span><span class="sxs-lookup"><span data-stu-id="52dc8-165">No</span></span> |
|<span data-ttu-id="52dc8-166">シミュレーション モード</span><span class="sxs-lookup"><span data-stu-id="52dc8-166">Simulation mode</span></span>|<span data-ttu-id="52dc8-167">いいえ</span><span class="sxs-lookup"><span data-stu-id="52dc8-167">No</span></span> |<span data-ttu-id="52dc8-168">はい</span><span class="sxs-lookup"><span data-stu-id="52dc8-168">Yes</span></span> |
|<span data-ttu-id="52dc8-169">条件についてチェックされた Exchange 添付ファイル</span><span class="sxs-lookup"><span data-stu-id="52dc8-169">Exchange attachments checked for conditions</span></span>|<span data-ttu-id="52dc8-170">いいえ</span><span class="sxs-lookup"><span data-stu-id="52dc8-170">No</span></span> | <span data-ttu-id="52dc8-171">はい</span><span class="sxs-lookup"><span data-stu-id="52dc8-171">Yes</span></span>|
|<span data-ttu-id="52dc8-172">視覚的なマーキングの適用</span><span class="sxs-lookup"><span data-stu-id="52dc8-172">Apply visual markings</span></span> |<span data-ttu-id="52dc8-173">はい</span><span class="sxs-lookup"><span data-stu-id="52dc8-173">Yes</span></span> |<span data-ttu-id="52dc8-174">はい (メール専用)</span><span class="sxs-lookup"><span data-stu-id="52dc8-174">Yes (email only)</span></span> |
|<span data-ttu-id="52dc8-175">ラベルなしで適用された IRM 暗号化の上書き</span><span class="sxs-lookup"><span data-stu-id="52dc8-175">Override IRM encryption applied without a label</span></span>|<span data-ttu-id="52dc8-176">はい (ユーザーがエクスポートの最小使用権を持っている場合)</span><span class="sxs-lookup"><span data-stu-id="52dc8-176">Yes if the user has the minimum usage right of Export</span></span> |<span data-ttu-id="52dc8-177">はい (メール専用)</span><span class="sxs-lookup"><span data-stu-id="52dc8-177">Yes (email only)</span></span> |
|<span data-ttu-id="52dc8-178">受信メールのラベル付け</span><span class="sxs-lookup"><span data-stu-id="52dc8-178">Label incoming email</span></span>|<span data-ttu-id="52dc8-179">いいえ</span><span class="sxs-lookup"><span data-stu-id="52dc8-179">No</span></span> |<span data-ttu-id="52dc8-180">はい (暗号化は適用されません)</span><span class="sxs-lookup"><span data-stu-id="52dc8-180">Yes (encryption not applied)</span></span> |

<span data-ttu-id="52dc8-181">\* 自動ラベル付けは、現在、一部の地域では利用できません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-181">\* Auto-labeling isn't currently available in all regions.</span></span> <span data-ttu-id="52dc8-182">テナントがこの機能をサポートできない場合、自動ラベル付けタブは管理ラベル センターに表示されません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-182">If your tenant can't support this functionality, the Auto-labeling tab isn't visible in the admin labeling center.</span></span>

## <a name="how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label"></a><span data-ttu-id="52dc8-183">複数のラベルに適用するときの複数の条件の評価方法</span><span class="sxs-lookup"><span data-stu-id="52dc8-183">How multiple conditions are evaluated when they apply to more than one label</span></span>

<span data-ttu-id="52dc8-p110">ラベルは、ポリシー内で指定した位置に従って評価の順序を決められます。先頭に配置したラベルが最下位 (機密性が最も低い) になり、最後に配置したラベルが最上位 (機密性が最も高い) になります。優先度に関する詳細については、「[ラベルの優先度 (順序の問題)](sensitivity-labels.md#label-priority-order-matters)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-p110">The labels are ordered for evaluation according to their position that you specify in the policy: The label positioned first has the lowest position (least sensitive) and the label positioned last has the highest position (most sensitive). For more information on priority, see [Label priority (order matters)](sensitivity-labels.md#label-priority-order-matters).</span></span>

## <a name="dont-configure-a-parent-label-to-be-applied-automatically-or-recommended"></a><span data-ttu-id="52dc8-186">自動適用または推奨されるように親ラベルを構成しない</span><span class="sxs-lookup"><span data-stu-id="52dc8-186">Don't configure a parent label to be applied automatically or recommended</span></span>

<span data-ttu-id="52dc8-187">親ラベル (サブラベルのあるラベル) はコンテンツに適用できません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-187">Remember, you can't apply a parent label (a label with sublabels) to content.</span></span> <span data-ttu-id="52dc8-188">Office アプリで親ラベルが自動適用または自動推奨されるように構成されていないこと、自動ラベル ポリシーで親ラベルが選択されていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-188">Make sure that you don't configure a parent label to be auto-applied or recommended in Office apps, and don't select a parent label for an auto-labeling policy.</span></span> <span data-ttu-id="52dc8-189">その場合、親ラベルをコンテンツに適用できなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-189">If you do, the parent label won't be applied to content.</span></span>

<span data-ttu-id="52dc8-190">自動ラベルでサブラベルも使用するには、必ず親ラベルとサブラベルの両方を発行してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-190">To use automatic labeling with sublabels, make sure you publish both the parent label and the sublabel.</span></span>

<span data-ttu-id="52dc8-191">親ラベルとサブラベルの詳細については、「[サブラベル (ラベルのグループ化)](sensitivity-labels.md#sublabels-grouping-labels)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-191">For more information on parent labels and sublabels, see [Sublabels (grouping labels)](sensitivity-labels.md#sublabels-grouping-labels).</span></span>

## <a name="how-to-configure-auto-labeling-for-office-apps"></a><span data-ttu-id="52dc8-192">Office アプリの自動ラベル付けを構成する方法</span><span class="sxs-lookup"><span data-stu-id="52dc8-192">How to configure auto-labeling for Office apps</span></span>

<span data-ttu-id="52dc8-193">Windows 用 Office アプリの自動ラベル付けは、Azure Information Protection 統合ラベル付けクライアントでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="52dc8-193">Automatic labeling in Office apps for Windows is supported by the Azure Information Protection unified labeling client.</span></span> <span data-ttu-id="52dc8-194">Office アプリのラベルが内蔵されている場合、この機能は、[さまざまなアプリの可用性のさまざまな段階にあります](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps)。</span><span class="sxs-lookup"><span data-stu-id="52dc8-194">For built-in labeling in Office apps, this capability is in [different stages of availability for different apps](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).</span></span>

<span data-ttu-id="52dc8-195">Office アプリの自動ラベル付け設定は、[機密ラベルを作成または編集する](create-sensitivity-labels.md)ときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-195">The auto-labeling settings for Office apps are available when you [create or edit a sensitivity label](create-sensitivity-labels.md).</span></span> <span data-ttu-id="52dc8-196">ラベルのスコープとして **[ファイルとメール]** が選択されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-196">Make sure **Files & emails** is selected for the label's scope:</span></span> 

![ファイルとメールの秘密度レベル スコープ オプション](../media/filesandemails-scope-options-sensitivity-label.png)

<span data-ttu-id="52dc8-198">ウィザードを移動すると、**[Office アプリの自動ラベル付け]** ページが表示されます。このページでは、機密情報の種類またはトレーニング可能な分類子のリストから選択できます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-198">As you move through the wizard, you see the **Auto-labeling for Office apps** page where you can choose from a list of sensitive info types or trainable classifiers:</span></span>

![Office アプリの自動ラベル付けのラベル条件](../media/sensitivity-labels-conditions.png)

<span data-ttu-id="52dc8-200">この機密ラベルが自動的に適用されると、ユーザーの Office アプリに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-200">When this sensitivity label is automatically applied, the user sees a notification in their Office app.</span></span> <span data-ttu-id="52dc8-201">例:</span><span class="sxs-lookup"><span data-stu-id="52dc8-201">For example:</span></span>

![ドキュメントにラベルが自動適用されたという通知](../media/sensitivity-labels-msg-doc-was-auto-labeled.PNG)

### <a name="configuring-sensitive-info-types-for-a-label"></a><span data-ttu-id="52dc8-203">ラベルの機密情報の種類の構成</span><span class="sxs-lookup"><span data-stu-id="52dc8-203">Configuring sensitive info types for a label</span></span>

<span data-ttu-id="52dc8-204">**機密情報の種類** オプションを選択すると、データ損失防止 (DLP) ポリシーを作成するときと同じ機密情報の種類の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-204">When you select the **Sensitive info types** option, you see the same list of sensitive information types as when you create a data loss prevention (DLP) policy.</span></span> <span data-ttu-id="52dc8-205">そのため、たとえば、クレジットカード番号、社会保障番号、またはパスポート番号など、お客様の個人情報を含むコンテンツに極秘ラベルを自動的に適用できます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-205">So you can, for example, automatically apply a Highly Confidential label to any content that contains customers' personal information, such as credit card numbers, social security numbers, or passport numbers:</span></span>

![Officeアプリの自動ラベル付け用の機密情報の種類](../media/sensitivity-labels-sensitive-info-types.png)

<span data-ttu-id="52dc8-207">機密情報の種類を選択した後は、インスタンス数または一致精度を変更して条件を絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-207">After you select your sensitive information types, you can refine your condition by changing the instance count or match accuracy.</span></span> <span data-ttu-id="52dc8-208">詳細については、「[一致の難易度を設定するためのルールの調整](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-208">For more information, see [Tuning rules to make them easier or harder to match](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match).</span></span>

<span data-ttu-id="52dc8-209">さらに、条件で検知する必要があるのは、機密情報の種類のすべてか、またはそのうちの 1 つだけかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-209">Further, you can choose whether a condition must detect all sensitive information types, or just one of them.</span></span> <span data-ttu-id="52dc8-210">また、条件をより柔軟または複雑にするには、グループを追加し、グループ間で論理演算子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-210">And to make your conditions more flexible or complex, you can add groups and use logical operators between the groups.</span></span> <span data-ttu-id="52dc8-211">詳細については、「[グループ化および論理演算子](data-loss-prevention-policies.md#grouping-and-logical-operators)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-211">For more information, see [Grouping and logical operators](data-loss-prevention-policies.md#grouping-and-logical-operators).</span></span>

![インスタンス数と一致精度のオプション](../media/Sensitivity-labels-instance-count-match-accuracy.png)

### <a name="configuring-trainable-classifiers-for-a-label"></a><span data-ttu-id="52dc8-213">ラベルのトレーニング可能な分類子を構成する</span><span class="sxs-lookup"><span data-stu-id="52dc8-213">Configuring trainable classifiers for a label</span></span>

<span data-ttu-id="52dc8-214">このオプションは現在プレビューの段階です。</span><span class="sxs-lookup"><span data-stu-id="52dc8-214">This option is currently in preview.</span></span>

<span data-ttu-id="52dc8-215">**トレーニング可能な分類子** のオプションを選択する場合、Microsoft から 1 つ以上のトレーニング可能な組み込み分類子を選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-215">When you select the **Trainable classifiers** option, select one or more of the built-in trainable classifiers from Microsoft.</span></span> <span data-ttu-id="52dc8-216">独自のトレーニング可能なカスタム分類子を作成している場合は、以下を選択できます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-216">If you've created your own custom trainable classifiers, these are also available to select:</span></span>

![トレーニング可能な分類子と秘密度ラベルのオプション](../media/sensitivity-labels-classifers.png)

> [!CAUTION]
> <span data-ttu-id="52dc8-218">組み込みの [**不快な言葉**] は、誤検知の数が多いため、廃止予定です。</span><span class="sxs-lookup"><span data-stu-id="52dc8-218">We are deprecating the **Offensive Language** built-in classifier because it has been producing a high number of false positives.</span></span> <span data-ttu-id="52dc8-219">この組み込み分類子を使用しないでください。現在使用している場合は、ビジネス プロセスを移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-219">Don't use this built-in classifier and if you are currently using it, you should move your business processes off it.</span></span> <span data-ttu-id="52dc8-220">代わりに、[**個人を標的にしたハラスメント**]、[**冒涜的表現**]、および [**脅威**] の組み込み分類子を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="52dc8-220">We recommend using the **Targeted Harassment**, **Profanity**, and **Threat** built-in classifiers instead.</span></span>

<span data-ttu-id="52dc8-221">これらの分類子の詳細については、「[トレーニング可能な分類子 (プレビュー) の詳細](classifier-learn-about.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-221">For more information about these classifiers, see [Learn about trainable classifiers (preview)](classifier-learn-about.md).</span></span>

<span data-ttu-id="52dc8-222">このオプションのプレビュー期間中は、次のアプリが秘密度ラベルのトレーニング可能な分類子をサポートします。</span><span class="sxs-lookup"><span data-stu-id="52dc8-222">During the preview period for this option, the following apps support trainable classifiers for sensitivity labels:</span></span>

- <span data-ttu-id="52dc8-223">Microsoft 365 Apps for enterprise ([以前の Office 365 ProPlus](https://docs.microsoft.com/deployoffice/name-change)) for Windows は、現在、バージョン 2006 以降で[最新機能提供チャネル](https://docs.microsoft.com/deployoffice/overview-update-channels#current-channel-overview) に展開中です。</span><span class="sxs-lookup"><span data-stu-id="52dc8-223">Microsoft 365 Apps for enterprise ([formerly Office 365 ProPlus](https://docs.microsoft.com/deployoffice/name-change)) for Windows, now rolling out to the [Current Channel](https://docs.microsoft.com/deployoffice/overview-update-channels#current-channel-overview) in version 2006 and later:</span></span>
    - <span data-ttu-id="52dc8-224">Word</span><span class="sxs-lookup"><span data-stu-id="52dc8-224">Word</span></span>
    - <span data-ttu-id="52dc8-225">Excel</span><span class="sxs-lookup"><span data-stu-id="52dc8-225">Excel</span></span>
    - <span data-ttu-id="52dc8-226">PowerPoint</span><span class="sxs-lookup"><span data-stu-id="52dc8-226">PowerPoint</span></span>

- <span data-ttu-id="52dc8-227">[SharePoint および OneDrive で Office ファイルの秘密度ラベルを有効にする機能 (パブリック プレビュー)](sensitivity-labels-sharepoint-onedrive-files.md) が有効になっている場合の Web アプリ用の Office:</span><span class="sxs-lookup"><span data-stu-id="52dc8-227">Office for the web apps, when you have [enabled sensitivity labels for Office files in SharePoint and OneDrive](sensitivity-labels-sharepoint-onedrive-files.md):</span></span>
    - <span data-ttu-id="52dc8-228">Word</span><span class="sxs-lookup"><span data-stu-id="52dc8-228">Word</span></span>
    - <span data-ttu-id="52dc8-229">Excel</span><span class="sxs-lookup"><span data-stu-id="52dc8-229">Excel</span></span>
    - <span data-ttu-id="52dc8-230">PowerPoint</span><span class="sxs-lookup"><span data-stu-id="52dc8-230">PowerPoint</span></span>
    - <span data-ttu-id="52dc8-231">Outlook</span><span class="sxs-lookup"><span data-stu-id="52dc8-231">Outlook</span></span>

### <a name="recommend-that-the-user-applies-a-sensitivity-label"></a><span data-ttu-id="52dc8-232">ユーザーが秘密度ラベルを適用することを推奨</span><span class="sxs-lookup"><span data-stu-id="52dc8-232">Recommend that the user applies a sensitivity label</span></span>

<span data-ttu-id="52dc8-233">状況に応じて、ユーザーがラベルを適用することを推奨できます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-233">If you prefer, you can recommend to your users that they apply the label.</span></span> <span data-ttu-id="52dc8-234">このオプションでは、分類および関連する保護を受け入れるか、またはラベルがそのコンテンツに適していない場合、推奨事項を無視するかをユーザーが選択できます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-234">With this option, your users can accept the classification and any associated protection, or dismiss the recommendation if the label isn't suitable for their content.</span></span>

![機密ラベルをユーザーに推奨するためのオプション](../media/Sensitivity-labels-Recommended-label-option.png)

<span data-ttu-id="52dc8-p121">ラベルを推奨される操作として適用するように条件を構成したときの、Azure Information Protection の統合ラベル付けクライアントからのプロンプトの例を、カスタム ポリシー ヒントと共に示します。ポリシー ヒントに表示するテキストを選択できます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-p121">Here's an example of a prompt from the Azure Information Protection unified labeling client when you configure a condition to apply a label as a recommended action, with a custom policy tip. You can choose what text is displayed in the policy tip.</span></span>

![推奨ラベルを適用するためのプロンプト](../media/Sensitivity-label-Prompt-for-required-label.png)

### <a name="when-automatic-or-recommended-labels-are-applied"></a><span data-ttu-id="52dc8-239">自動ラベルまたは推奨ラベルが適用されている場合</span><span class="sxs-lookup"><span data-stu-id="52dc8-239">When automatic or recommended labels are applied</span></span>

<span data-ttu-id="52dc8-240">Office アプリでの自動ラベル付けと推奨ラベル付けの実装は、Office に組み込まれているラベル付けを使用しているか、または Azure Information Protection の統合ラベル付けクライアントを使用しているかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-240">The implementation of automatic and recommended labeling in Office apps depend on whether you're using labeling that's built into Office, or the Azure Information Protection unified labeling client.</span></span> <span data-ttu-id="52dc8-241">ただし、どちらの場合も次のようになります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-241">In both cases, however:</span></span>

- <span data-ttu-id="52dc8-242">以前に手動でラベルが付けられているか、以前に上位の機密度で自動的にラベルが付けられているドキュメントと電子メールには自動ラベル付けを使用できません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-242">You can't use automatic labeling for documents and emails that were previously manually labeled, or previously automatically labeled with a higher sensitivity.</span></span> <span data-ttu-id="52dc8-243">ドキュメントや電子メールに適用できる機密ラベルは (1 つの保持ラベルに加えて) 1 つだけであることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-243">Remember, you can only apply a single sensitivity label to a document or email (in addition to a single retention label).</span></span>

- <span data-ttu-id="52dc8-244">以前に上位の秘密度でラベルが付けられているドキュメントまたはメールには推奨ラベル付けを使用できません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-244">You can't use recommended labeling for documents or emails that were previously labeled with a higher sensitivity.</span></span> <span data-ttu-id="52dc8-245">コンテンツに既に上位の秘密度でラベルが付けられている場合、推奨事項とポリシー ヒントに関するプロンプトは、ユーザーに表示されません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-245">When the content's already labeled with a higher sensitivity, the user won't see the prompt with the recommendation and policy tip.</span></span>

<span data-ttu-id="52dc8-246">組み込みのラベル付けに関してのみ以下の点が当てはまります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-246">Specific to built-in labeling:</span></span>

- <span data-ttu-id="52dc8-247">必ずしもすべての Office アプリで自動 (および推奨) ラベル付けがサポートされるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-247">Not all Office apps support automatic (and recommended) labeling.</span></span> <span data-ttu-id="52dc8-248">詳しくは、「[アプリでの秘密度ラベル機能のサポート](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-248">For more information, see [Support for sensitivity label capabilities in apps](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).</span></span>

- <span data-ttu-id="52dc8-249">Word のデスクトップ バージョンにおける推奨ラベルでは、推奨をトリガーした機密コンテンツにフラグが付けられるので、ユーザーが確認して、推奨されている秘密度ラベルを適用しないで機密コンテンツを削除できます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-249">For recommended labels in the desktop versions of Word, the sensitive content that triggered the recommendation is flagged so that users can review and remove the sensitive content instead of applying the recommended sensitivity label.</span></span>

- <span data-ttu-id="52dc8-250">こうしたラベルが Office アプリで適用される方法、スクリーンショット例、機密情報の検出方法について詳しくは、「[Office のファイルとメールに秘密度ラベルを自動的に適用、または推奨する](https://support.office.com/ja-JP/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-250">For details about how these labels are applied in Office apps, example screenshots, and how sensitive information is detected, see [Automatically apply or recommend sensitivity labels to your files and emails in Office](https://support.office.com/ja-JP/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1).</span></span>

<span data-ttu-id="52dc8-251">Azure Information Protection 統合ラベル付けクライアントに関してのみ以下の点が当てはまります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-251">Specific to the Azure Information Protection unified labeling client:</span></span>

-  <span data-ttu-id="52dc8-252">自動ラベル付けと推奨ラベル付けは、Word、Excel、PowerPoint でドキュメントが保存されるときと、Outlook でメールが送信されるときに適用されます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-252">Automatic and recommended labeling applies to Word, Excel, and PowerPoint when you save a document, and to Outlook when you send an email.</span></span>

- <span data-ttu-id="52dc8-253">Outlook で推奨ラベル付けをサポートするには、最初に[詳細なポリシー設定](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations#enable-recommended-classification-in-outlook)を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-253">For Outlook to support recommended labeling, you must first configure an [advanced policy setting](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations#enable-recommended-classification-in-outlook).</span></span>

- <span data-ttu-id="52dc8-254">ドキュメントやメール内の本文、およびヘッダーとフッターに含まれる機密情報が検出されますが、件名やメールの添付ファイルのものは検知されません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-254">Sensitive information can be detected in the body text in documents and emails, and to headers and footers—but not in the subject line or attachments of email.</span></span>

## <a name="how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange"></a><span data-ttu-id="52dc8-255">SharePoint、OneDrive、Exchange の自動ラベル付けポリシーを構成する方法</span><span class="sxs-lookup"><span data-stu-id="52dc8-255">How to configure auto-labeling policies for SharePoint, OneDrive, and Exchange</span></span>

<span data-ttu-id="52dc8-256">自動ラベル付けポリシーを構成する前に、前提条件を必ずご確認ください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-256">Make sure you're aware of the prerequisites before you configure auto-labeling policies.</span></span> 

### <a name="prerequisites-for-auto-labeling-policies"></a><span data-ttu-id="52dc8-257">自動ラベル付けポリシーの前提条件</span><span class="sxs-lookup"><span data-stu-id="52dc8-257">Prerequisites for auto-labeling policies</span></span>

- <span data-ttu-id="52dc8-258">シミュレーション モード:</span><span class="sxs-lookup"><span data-stu-id="52dc8-258">Simulation mode:</span></span>
    - <span data-ttu-id="52dc8-259">Microsoft 365 の監査を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-259">Auditing for Microsoft 365 must be turned on.</span></span> <span data-ttu-id="52dc8-260">監査を有効にする必要がある場合、または監査が既に有効になっているかどうかが不明の場合は、「[監査ログの検索を有効または無効にする](turn-audit-log-search-on-or-off.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-260">If you need to turn on auditing or you're not sure whether auditing is already on, see [Turn audit log search on or off](turn-audit-log-search-on-or-off.md).</span></span>
    - <span data-ttu-id="52dc8-261">ソース ビューでファイルの内容を表示するには、**コンテンツ エクスプローラーのコンテンツ閲覧者** の役割が必要です。</span><span class="sxs-lookup"><span data-stu-id="52dc8-261">To view file contents in the source view, you must have the **Content Explorer Content Viewer** role.</span></span> <span data-ttu-id="52dc8-262">既定では、全体管理者にはこの役割はありません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-262">Global admins don't have this role by default.</span></span> <span data-ttu-id="52dc8-263">このアクセス許可がない場合、[**一致したアイテム**] タブからアイテムを選択してもプレビュー ウィンドウは表示されません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-263">If you don't have this permission, you don't see the preview pane when you select an item from the **Matched Items** tab.</span></span>

- <span data-ttu-id="52dc8-264">SharePoint および OneDrive にあるファイルに自動でラベルを付けるには:</span><span class="sxs-lookup"><span data-stu-id="52dc8-264">To auto-label files in SharePoint and OneDrive:</span></span>
    - <span data-ttu-id="52dc8-265">[SharePoint および OneDrive で Office ファイルの機密度ラベルを有効にしています](sensitivity-labels-sharepoint-onedrive-files.md)。</span><span class="sxs-lookup"><span data-stu-id="52dc8-265">You have [enabled sensitivity labels for Office files in SharePoint and OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).</span></span>
    - <span data-ttu-id="52dc8-266">自動ラベル付けポリシーの実行時に、別のプロセスまたはユーザーがファイルを開いておくことはできません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-266">At the time the auto-labeling policy runs, the file mustn't be open by another process or user.</span></span> <span data-ttu-id="52dc8-267">編集用にチェックアウトされたファイルは、このカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-267">A file that's checked out for editing falls into this category.</span></span>

- <span data-ttu-id="52dc8-268">組み込みの機密度の種類ではなく、[カスタムの機密情報の種類](custom-sensitive-info-types.md)を使用する場合は、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="52dc8-268">If you plan to use [custom sensitive information types](custom-sensitive-info-types.md) rather than the built-in sensitivity types:</span></span> 
    - <span data-ttu-id="52dc8-269">カスタム機密情報の種類は、カスタム機密情報の種類が保存された後に SharePoint または OneDrive に追加されたコンテンツに対して評価されます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-269">Custom sensitivity information types are evaluated for content that is added to SharePoint or OneDrive after the custom sensitivity information types are saved.</span></span> 
    - <span data-ttu-id="52dc8-270">新しいカスタムの機密情報の種類をテストするには、自動ラベル付けポリシーを作成する前に作成してから、テスト用のサンプル データを使用して新しいドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-270">To test new custom sensitive information types, create them before you create your auto-labeling policy, and then create new documents with sample data for testing.</span></span>

- <span data-ttu-id="52dc8-271">自動ラベル付けポリシー用に選択できる、[作成および公開された](create-sensitivity-labels.md) (少なくとも 1 人のユーザーに対して) 1 つ以上の秘密度ラベル。</span><span class="sxs-lookup"><span data-stu-id="52dc8-271">One or more sensitivity labels [created and published](create-sensitivity-labels.md) (to at least one user) that you can select for your auto-labeling policies.</span></span> <span data-ttu-id="52dc8-272">これらのラベルの場合:</span><span class="sxs-lookup"><span data-stu-id="52dc8-272">For these labels:</span></span>
    - <span data-ttu-id="52dc8-273">概要で説明したように、ラベル設定は自動ラベル付けポリシーを補完するため、Office アプリのラベル設定の自動ラベル付けがオンかオフかは関係ありません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-273">It doesn't matter if the auto-labeling in Office apps label setting is turned on or off, because that label setting supplements auto-labeling policies, as explained in the introduction.</span></span>
    - <span data-ttu-id="52dc8-274">自動ラベル付けに使用するラベルが視覚的なマーキング (ヘッダー、フッター、透かし) を使用するように構成されている場合、これらはドキュメントに適用されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-274">If the labels you want to use for auto-labeling are configured to use visual markings (headers, footers, watermarks), note that these are not applied to documents.</span></span>
    - <span data-ttu-id="52dc8-275">ラベルに [暗号化](encryption-sensitivity-labels.md)を適用する場合は、**[今すぐアクセス許可を適用する]** の設定を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-275">If the labels apply [encryption](encryption-sensitivity-labels.md), they must be configured for the **Assign permissions now** setting.</span></span>

### <a name="learn-about-simulation-mode"></a><span data-ttu-id="52dc8-276">シミュレーション モードの詳細</span><span class="sxs-lookup"><span data-stu-id="52dc8-276">Learn about simulation mode</span></span>

<span data-ttu-id="52dc8-277">シミュレーション モードは、自動ラベル付けポリシーに固有であり、ワークフローに組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="52dc8-277">Simulation mode is unique to auto-labeling policies and woven into the workflow.</span></span> <span data-ttu-id="52dc8-278">ポリシーによって少なくとも 1 つのシミュレーションが実行されるまで、ドキュメントとメールに自動的にラベルを付けることはできません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-278">You can't automatically label documents and emails until your policy has run at least one simulation.</span></span>

<span data-ttu-id="52dc8-279">自動ラベル付けポリシーのワークフロー:</span><span class="sxs-lookup"><span data-stu-id="52dc8-279">Workflow for an auto-labeling policy:</span></span>

1. <span data-ttu-id="52dc8-280">自動ラベル付けポリシーを作成して構成する。</span><span class="sxs-lookup"><span data-stu-id="52dc8-280">Create and configure an auto-labeling policy.</span></span>

2. <span data-ttu-id="52dc8-281">ポリシーをシミュレーション モードで実行し、24時間後、またはシミュレーションが完了するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-281">Run the policy in simulation mode and wait 24 hours, or until the simulation is complete.</span></span>

3. <span data-ttu-id="52dc8-282">結果を確認し、必要に応じてポリシーを調整します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-282">Review the results, and if necessary, refine your policy.</span></span> <span data-ttu-id="52dc8-283">シミュレーション モードを再実行し、24時間後、またはシミュレーションが完了するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-283">Rerun simulation mode and wait another 24 hours, or until the simulation is complete.</span></span>

4. <span data-ttu-id="52dc8-284">必要に応じて、手順 3 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-284">Repeat step 3 as needed.</span></span>

5. <span data-ttu-id="52dc8-285">実稼働環境に展開する。</span><span class="sxs-lookup"><span data-stu-id="52dc8-285">Deploy in production.</span></span>

<span data-ttu-id="52dc8-286">シミュレーションされた展開は、PowerShell の WhatIf パラメーターのように動作します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-286">The simulated deployment runs like the WhatIf parameter for PowerShell.</span></span> <span data-ttu-id="52dc8-287">定義したルールを使用して、自動ラベル付けポリシーが選択したラベルを適用したかのようにレポートされた結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-287">You see results reported as if the auto-labeling policy had applied your selected label, using the rules that you defined.</span></span> <span data-ttu-id="52dc8-288">その後、必要に応じてルールの精度を高め、シミュレーションを再実行できます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-288">You can then refine your rules for accuracy if needed, and rerun the simulation.</span></span> <span data-ttu-id="52dc8-289">ただし、Exchange の自動ラベル付けは、メールボックスに保存されたメールではなく、送受信されるメールに適用されるため、完全に同じメール メッセージを送受信することができなければ、シミュレーションのメールの結果に一貫性があるとは期待できません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-289">However, because auto-labeling for Exchange applies to emails that are sent and received, rather than emails stored in mailboxes, don't expect results for email in a simulation to be consistent unless you're able to send and receive the exact same email messages.</span></span>

<span data-ttu-id="52dc8-290">シミュレーション モードでは、展開前に自動ラベル付けポリシーの範囲を徐々に広げることもできます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-290">Simulation mode also lets you gradually increase the scope of your auto-labeling policy before deployment.</span></span> <span data-ttu-id="52dc8-291">たとえば、1 つのドキュメント ライブラリを持った SharePoint サイトなどの 1 つの場所から始めることができます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-291">For example, you might start with a single location, such as a SharePoint site, with a single document library.</span></span> <span data-ttu-id="52dc8-292">次に、反復的な変更を加えて、範囲を複数のサイトに拡大し、次に OneDrive などの別の場所に拡大します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-292">Then, with iterative changes, increase the scope to multiple sites, and then to another location, such as OneDrive.</span></span>

<span data-ttu-id="52dc8-293">最後に、シミュレーション モードを使用して、自動ラベル付けポリシーの実行に必要な時間の概算を提供し、シミュレーション モードを使用せずに実行するタイミングを計画してスケジュールすることができます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-293">Finally, you can use simulation mode to provide an approximation of the time needed to run your auto-labeling policy, to help you plan and schedule when to run it without simulation mode.</span></span>

### <a name="creating-an-auto-labeling-policy"></a><span data-ttu-id="52dc8-294">自動ラベル付けポリシーの作成</span><span class="sxs-lookup"><span data-stu-id="52dc8-294">Creating an auto-labeling policy</span></span>

1. <span data-ttu-id="52dc8-295">[Microsoft 365 コンプライアンス センター](https://compliance.microsoft.com/)で、機密ラベルに移動します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-295">In the [Microsoft 365 compliance center](https://compliance.microsoft.com/), navigate to sensitivity labels:</span></span>
    
    - <span data-ttu-id="52dc8-296">[**ソリューション**]  >  [**Information Protection**]</span><span class="sxs-lookup"><span data-stu-id="52dc8-296">**Solutions** > **Information protection**</span></span>
    
    <span data-ttu-id="52dc8-297">このオプションがすぐに表示されない場合は、まず [**すべてを表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-297">If you don't immediately see this option, first select **Show all**.</span></span>

2. <span data-ttu-id="52dc8-298">[**自動ラベル付け**] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-298">Select the **Auto-labeling** tab:</span></span>
    
    ![自動ラベル付け](../media/auto-labeling-tab.png)
    
    > [!NOTE]
    > <span data-ttu-id="52dc8-300">**[自動ラベル付け]** タブが表示されない場合、この機能は現在お住まいの地域ではご利用いただけません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-300">If you don't see the **Auto-labeling** tab, this functionality isn't currently available in your region.</span></span>

3. <span data-ttu-id="52dc8-301">[**+自動ラベル付けポリシーの作成**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-301">Select **+ Create auto-labeling policy**.</span></span> <span data-ttu-id="52dc8-302">これにより、新しいポリシー ウィザードが起動します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-302">This starts the New policy wizard:</span></span>
    
    ![<span data-ttu-id="52dc8-303">自動ラベル付け用の新しいポリシー ウィザード</span><span class="sxs-lookup"><span data-stu-id="52dc8-303">New policy wizard for auto-labeling</span></span> ](../media/auto-labeling-wizard.png)

4. <span data-ttu-id="52dc8-304">[**このラベルを適用する情報を選択する**] ページの場合: [**財務**] または [**プライバシー**] などのテンプレートのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-304">For the page **Choose info you want this label applied to**: Select one of the templates, such as **Financial** or **Privacy**.</span></span> <span data-ttu-id="52dc8-305">ドロップダウンの **表示オプション** を使用して、検索を絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-305">You can refine your search by using the **Show options for** dropdown.</span></span> <span data-ttu-id="52dc8-306">または、テンプレートが要件を満たしていない場合は、[**カスタム ポリシー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-306">Or, select **Custom policy** if the templates don't meet your requirements.</span></span> <span data-ttu-id="52dc8-307">[**次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-307">Select **Next**.</span></span>

5. <span data-ttu-id="52dc8-308">[**自動ラベル ポリシーに名前を付ける**] ページの場合: 一意の名前を入力し、必要に応じて説明を入力して、自動的に適用されるラベル、場所、ラベル付けするコンテンツを識別する条件を識別します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-308">For the page **Name your auto-labeling policy**: Provide a unique name, and optionally a description to help identify the automatically applied label, locations, and conditions that identify the content to label.</span></span>

6. <span data-ttu-id="52dc8-309">[**ラベルを適用する場所を選択する**] ページの場合: Exchange、SharePoint サイト、OneDrive の場所を選択して指定します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-309">For the page **Choose locations where you want to apply the label**: Select and specify locations for Exchange, SharePoint sites, and OneDrive.</span></span> <span data-ttu-id="52dc8-310">[**次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-310">Then select **Next**.</span></span>
    
    ![<span data-ttu-id="52dc8-311">[場所の選択] ページの自動ラベル付けウィザード</span><span class="sxs-lookup"><span data-stu-id="52dc8-311">Choose locations page auto-labelingwizard</span></span> ](../media/locations-auto-labeling-wizard.png)
    
    <span data-ttu-id="52dc8-312">個々の SharePoint サイトと OneDrive アカウントを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-312">You must specify individual SharePoint sites and OneDrive accounts.</span></span> <span data-ttu-id="52dc8-313">OneDrive の場合、ユーザーの OneDrive アカウントの URL は次の形式になります。`https://<tenant name>-my.sharepoint.com/personal/<user_name>_<tenant name>_com`</span><span class="sxs-lookup"><span data-stu-id="52dc8-313">For OneDrive, the URL for a user's OneDrive account is in the following format: `https://<tenant name>-my.sharepoint.com/personal/<user_name>_<tenant name>_com`</span></span>
    
    <span data-ttu-id="52dc8-314">たとえば、「rsimone」のユーザー名を持つ contoso テナント内のユーザーの場合: `https://contoso-my.sharepoint.com/personal/rsimone_contoso_onmicrosoft_com`</span><span class="sxs-lookup"><span data-stu-id="52dc8-314">For example, for a user in the contoso tenant that has a user name of "rsimone": `https://contoso-my.sharepoint.com/personal/rsimone_contoso_onmicrosoft_com`</span></span>
    
    <span data-ttu-id="52dc8-315">テナントの構文を確認し、ユーザーの URL を特定するには、「[組織内のすべてのユーザーの OneDrive URL のリストを取得する](https://docs.microsoft.com/onedrive/list-onedrive-urls)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-315">To verify the syntax for your tenant and identify URLs for users, see [Get a list of all user OneDrive URLs in your organization](https://docs.microsoft.com/onedrive/list-onedrive-urls).</span></span>

7. <span data-ttu-id="52dc8-316">[**一般または詳細ルールの設定**] ページの場合: 既定の [**一般的なルール**] のままにして、選択したすべての場所でラベル付けするコンテンツを識別するルールを定義します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-316">For the **Set up common or advanced rules** page: Keep the default of **Common rules** to define rules that identify content to label across all your selected locations.</span></span> <span data-ttu-id="52dc8-317">場所ごとに異なるルールが必要な場合は、[**詳細ルール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-317">If you need different rules per location, select **Advanced rules**.</span></span> <span data-ttu-id="52dc8-318">[**次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-318">Then select **Next**.</span></span>
    
    <span data-ttu-id="52dc8-319">ルールでは、機密情報の種類と共有オプションを含む条件を使用します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-319">The rules use conditions that include sensitive information types and sharing options:</span></span>
    - <span data-ttu-id="52dc8-320">機密情報の種類については、組み込みとカスタムの両方の機密情報の種類を選択できます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-320">For sensitive information types, you can select both built-in and custom sensitive information types.</span></span>
    - <span data-ttu-id="52dc8-321">共有オプションについては、[**組織内の連絡先のみ**] または [**組織外の連絡先**] を選択できます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-321">For the shared options, you can choose **only with people inside my organization** or **with people outside my organization**.</span></span>
    
    <span data-ttu-id="52dc8-322">唯一の場所が **Exchange** である場合、または [**詳細ルール**] を選択した場合、次のような選択ができる追加の条件があります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-322">If your only location is **Exchange**, or if you select **Advanced rules**, there are additional conditions that you can select:</span></span>
    - <span data-ttu-id="52dc8-323">送信者の IP アドレスが</span><span class="sxs-lookup"><span data-stu-id="52dc8-323">Sender IP address is</span></span>
    - <span data-ttu-id="52dc8-324">受信者ドメインが</span><span class="sxs-lookup"><span data-stu-id="52dc8-324">Recipient domain is</span></span>
    - <span data-ttu-id="52dc8-325">受信者が</span><span class="sxs-lookup"><span data-stu-id="52dc8-325">Recipient is</span></span>
    - <span data-ttu-id="52dc8-326">添付ファイルの拡張子が</span><span class="sxs-lookup"><span data-stu-id="52dc8-326">Attachment's file extension is</span></span>
    - <span data-ttu-id="52dc8-327">添付ファイルがパスワードで保護されている</span><span class="sxs-lookup"><span data-stu-id="52dc8-327">Attachment is password protected</span></span>
    - <span data-ttu-id="52dc8-328">メールの添付ファイルのコンテンツをスキャンできなかった</span><span class="sxs-lookup"><span data-stu-id="52dc8-328">Any email attachment's content could not be scanned</span></span>
    - <span data-ttu-id="52dc8-329">メールの添付ファイルのコンテンツのスキャンが完了しなかった</span><span class="sxs-lookup"><span data-stu-id="52dc8-329">Any email attachment's content didn't complete scanning</span></span>

8. <span data-ttu-id="52dc8-330">以前の選択に応じて、条件と例外を使用して新しいルールを作成する機会があります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-330">Depending on your previous choices, you'll now have an opportunity to create new rules by using conditions and exceptions.</span></span>
    
    <span data-ttu-id="52dc8-331">機密情報の種類の構成オプションは、Office アプリの自動ラベル付けに選択したものと同じです。</span><span class="sxs-lookup"><span data-stu-id="52dc8-331">The configuration options for sensitive information types are the same as those you select for auto-labeling for Office apps.</span></span> <span data-ttu-id="52dc8-332">詳細情報が必要な場合は、「[ラベルの機密情報の種類の構成](#configuring-sensitive-info-types-for-a-label)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-332">If you need more information, see [Configuring sensitive info types for a label](#configuring-sensitive-info-types-for-a-label).</span></span>
    
    <span data-ttu-id="52dc8-333">必要なすべてのルールを定義し、状態が [オン] になっていることを確認したら、[**次へ**] を選択して、自動適用するラベルの選択に進みます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-333">When you have defined all the rules you need, and confirmed their status is on, select **Next** to move on to choosing a label to auto-apply.</span></span>

11. <span data-ttu-id="52dc8-334">[**自動適用するラベルを選択する**] ページの場合: [**+ ラベルの選択**] を選択し、[**機密ラベルの選択**] ウィンドウのラベルを選択し、[**次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-334">For the **Choose a label to auto-apply** page: Select **+ Choose a label**, select a label from the **Choose a sensitivity label** pane, and then select **Next**.</span></span>

12. <span data-ttu-id="52dc8-335">**[ポリシーを今すぐテストするか後でテストするかを決定する]** ページの場合: シミュレーション モードで、今すぐ自動ラベル付けポリシーを実行する準備が整っている場合は、**[シミュレーション モードでポリシーを実行する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-335">For the **Decide if you want to test out the policy now or later** page: Select **Run policy in simulation mode** if you're ready to run the auto-labeling policy now, in simulation mode.</span></span> <span data-ttu-id="52dc8-336">それ以外の場合は、**[ポリシーをオフのままにする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-336">Otherwise, select **Leave policy turned off**.</span></span> <span data-ttu-id="52dc8-337">[**次へ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-337">Select **Next**:</span></span> 
    
    ![ポリシーの自動ラベル付けウィザードをテストする](../media/simulation-mode-auto-labeling-wizard.png)

13. <span data-ttu-id="52dc8-339">**[概要]** ページの場合: 自動ラベル付けポリシーの構成を確認し、必要な変更を行い、ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-339">For the **Summary** page: Review the configuration of your auto-labeling policy and make any changes that needed, and complete the wizard.</span></span>
    
    <span data-ttu-id="52dc8-340">Office アプリの自動ラベル付けとは異なり、個別の公開オプションはありません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-340">Unlike auto-labeling for Office apps, there's no separate publish option.</span></span> <span data-ttu-id="52dc8-341">ただし、ラベルの公開と同様に、自動ラベル付けポリシーが組織全体に複製されるまでに最大 24 時間かかります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-341">However, as with publishing labels, allow up to 24 hours for the auto-labeling policy to replicate throughout your organization.</span></span>

<span data-ttu-id="52dc8-342">**[情報保護]** > **[自動ラベル付け]** ページでは、自動ラベル付けポリシーを **[シミュレーション]** または **[オフ]** セクションのどちらかで確認できます。これは、シミュレーション モードで実行することを選択したかどうかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-342">Now on the **Information protection** > **Auto-labeling** page, you see your auto-labeling policy in the **Simulation** or **Off** section, depending on whether you chose to run it in simulation mode or not.</span></span> <span data-ttu-id="52dc8-343">ポリシーを選択して、構成と状態の詳細 (**[ポリシー シミュレーションの実行中]** など) を確認します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-343">Select your policy to see the details of the configuration and status (for example, **Policy simulation is still running**).</span></span> <span data-ttu-id="52dc8-344">シミュレーション モードのポリシーの場合は、**[一致したアイテム]** タブを選択して、指定したルールに一致した電子メールまたはドキュメントを確認します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-344">For policies in simulation mode, select the **Matched items** tab to see which emails or documents matched the rules that you specified.</span></span>

<span data-ttu-id="52dc8-345">このインターフェイスからは、次のようにポリシーを直接変更できます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-345">You can modify your policy directly from this interface:</span></span>

- <span data-ttu-id="52dc8-346">**[オフ]** セクションのポリシーの場合は、**[ポリシーの編集]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-346">For a policy in the **Off** section, select the **Edit policy** button.</span></span>

- <span data-ttu-id="52dc8-347">**[シミュレーション]** セクションのポリシーの場合は、いずれかのタブからページの上部にある **[ポリシーの編集]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-347">For policy in the **Simulation** section, select the **Edit policy** option at the top of the page, from either tab:</span></span>
    
    ![自動ラベル付けポリシーの編集オプション](../media/auto-labeling-edit.png)
    
    <span data-ttu-id="52dc8-349">シミュレーションなしでポリシーを実行する準備が整っているときには、**[ポリシーを有効にする]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-349">When you're ready to run the policy without simulation, select the **Turn on policy** option.</span></span>

<span data-ttu-id="52dc8-350">自動ポリシーは、削除されるまで継続的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-350">Your auto-policies run continuously until they are deleted.</span></span> <span data-ttu-id="52dc8-351">たとえば、新しいドキュメントや変更されたドキュメントは、現在のポリシー設定に含まれます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-351">For example, new and modified documents will be included with the current policy settings.</span></span>

<span data-ttu-id="52dc8-352">また、適切な[アクセス許可](data-classification-content-explorer.md#permissions)がある場合は、[コンテンツ エクスプローラー](data-classification-content-explorer.md)を使用して、自動ラベル付けポリシーの結果を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-352">You can also see the results of your auto-labeling policy by using [content explorer](data-classification-content-explorer.md) when you have the appropriate [permissions](data-classification-content-explorer.md#permissions):</span></span>
- <span data-ttu-id="52dc8-353">**コンテンツ エクスプローラーのリスト閲覧者** では、ファイルのラベルは表示できますが、ファイルのコンテンツは表示できません。</span><span class="sxs-lookup"><span data-stu-id="52dc8-353">**Content Explorer List Viewer** lets you see a file's label but not the file's contents.</span></span>
- <span data-ttu-id="52dc8-354">**コンテンツ エクスプローラーのコンテンツ閲覧者** では、ファイルの内容を表示できます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-354">**Content Explorer Content Viewer** lets you see the file's contents.</span></span>

> [!TIP]
> <span data-ttu-id="52dc8-355">コンテンツ エクスプローラーを使用して、機密情報を含むラベルの付いていないドキュメントがある場所を特定することもできます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-355">You can also use content explorer to identify locations that have documents with sensitive information, but are unlabeled.</span></span> <span data-ttu-id="52dc8-356">この情報を使用して、自動ラベル付けポリシーにこれらの場所を追加することを検討し、識別された機密情報の種類をルールとして含めます。</span><span class="sxs-lookup"><span data-stu-id="52dc8-356">Using this information, consider adding these locations to your auto-labeling policy, and include the identified sensitive information types as rules.</span></span>

### <a name="use-powershell-for-auto-labeling-policies"></a><span data-ttu-id="52dc8-357">自動ラベル付けポリシーに PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="52dc8-357">Use PowerShell for auto-labeling policies</span></span>

<span data-ttu-id="52dc8-358">[セキュリティ/コンプライアンス センターの PowerShell](https://docs.microsoft.com/powershell/exchange/scc-powershell) を使用して、自動ラベル付けポリシーを作成し、構成できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="52dc8-358">You can now use [Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/scc-powershell) to create and configure auto-labeling policies.</span></span> <span data-ttu-id="52dc8-359">これにより、自動ラベル付けポリシーの作成やメンテナンスを完全にスクリプト化できるようになり、OneDrive や SharePoint の場所に複数の URL を指定する効率的な方法も提供されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="52dc8-359">This means you can now fully script the creation and maintenance of your auto-labeling policies, which also provides a more efficient method of specifying multiple URLs for OneDrive and SharePoint locations.</span></span>

<span data-ttu-id="52dc8-360">PowerShell でコマンドを実行する前に、最初に[セキュリティ/コンプライアンス センターの PowerShell に接続](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52dc8-360">Before you run the commands in PowerShell, you must first [connect to Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell).</span></span>

<span data-ttu-id="52dc8-361">新しい自動ラベル付けポリシーを作成するには:</span><span class="sxs-lookup"><span data-stu-id="52dc8-361">To create a new auto-labeling policy:</span></span> 

```powershell
New-AutoSensitivityLabelPolicy -Name <AutoLabelingPolicyName> -SharePointLocation "<SharePointSiteLocation>" -ApplySensitivityLabel <Label> -Mode TestWithoutNotifications
```
<span data-ttu-id="52dc8-362">このコマンドは、指定した SharePoint サイトの自動ラベル付けポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-362">This command creates an auto-labeling policy for a SharePoint site that you specify.</span></span> <span data-ttu-id="52dc8-363">OneDrive の場所については、代わりに *OneDriveLocation* パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-363">For a OneDrive location, use the *OneDriveLocation* parameter, instead.</span></span> 

<span data-ttu-id="52dc8-364">既存の自動ラベル付けポリシーにサイトを追加するには:</span><span class="sxs-lookup"><span data-stu-id="52dc8-364">To add additional sites to an existing auto-labeling policy:</span></span>

```powershell
$spoLocations = @("<SharePointSiteLocation1>","<SharePointSiteLocation2>")
Set-AutoSensitivityLabelPolicy -Identity <AutoLabelingPolicyName> -AddSharePointLocation $spoLocations -ApplySensitivityLabel <Label> -Mode TestWithoutNotifications
```

<span data-ttu-id="52dc8-365">このコマンドは、追加の SharePoint URL を変数に指定し、既存の自動ラベル付けポリシーに追加します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-365">This command specifies the additional SharePoint URLs in a variable that is then added to an existing auto-labeling policy.</span></span> <span data-ttu-id="52dc8-366">代わりに OneDrive の場所を追加するには、*AddOneDriveLocation* パラメーターに *$OneDriveLocations* のような別の変数を指定して使用します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-366">To add OneDrive locations instead, use the *AddOneDriveLocation* parameter with a different variable, such as *$OneDriveLocations*.</span></span>

<span data-ttu-id="52dc8-367">新しい自動ラベル付けポリシー ルールを作成するには:</span><span class="sxs-lookup"><span data-stu-id="52dc8-367">To create a new auto-labeling policy rule:</span></span>

```powershell
New-AutoSensitivityLabelRule -Policy <AutoLabelingPolicyName> -Name <AutoLabelingRuleName> -ContentContainsSensitiveInformation @{"name"= "a44669fe-0d48-453d-a9b1-2cc83f2cba77"; "mincount" = "2"} -Workload SharePoint
```

<span data-ttu-id="52dc8-368">既存の自動ラベル付けポリシーについては、このコマンドはエンティティ ID が a44669fe-0d48-453d-a9b1-2cc83f2cba77 である **米国の社会保障番号 (SSN)** の機密情報の種類を検出するための新しいポリシー ルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="52dc8-368">For an existing auto-labeling policy, this command creates a new policy rule to detect the sensitive information type of **U.S. social security number (SSN)**, which has an entity ID of a44669fe-0d48-453d-a9b1-2cc83f2cba77.</span></span> <span data-ttu-id="52dc8-369">その他の機密情報の種類のエンティティ ID を検索するには、「[機密情報の種類のエンティティ定義](sensitive-information-type-entity-definitions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-369">To find the entity IDs for other sensitive information types, refer to [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md).</span></span>

<span data-ttu-id="52dc8-370">自動ラベル付けポリシーをサポートする PowerShell コマンドレット、使用可能なパラメーター、そしていくつかの例の詳細については、次のコマンドレットのヘルプを参照してください。</span><span class="sxs-lookup"><span data-stu-id="52dc8-370">For more information about the PowerShell cmdlets that support auto-labeling policies, their available parameters and some examples, see the following cmdlet help:</span></span>

- [<span data-ttu-id="52dc8-371">Get-AutoSensitivityLabelPolicy</span><span class="sxs-lookup"><span data-stu-id="52dc8-371">Get-AutoSensitivityLabelPolicy</span></span>](https://docs.microsoft.com/powershell/module/exchange/get-autosensitivitylabelpolicy)
- [<span data-ttu-id="52dc8-372">New-AutoSensitivityLabelPolicy</span><span class="sxs-lookup"><span data-stu-id="52dc8-372">New-AutoSensitivityLabelPolicy</span></span>](https://docs.microsoft.com/powershell/module/exchange/new-autosensitivitylabelpolicy)
- [<span data-ttu-id="52dc8-373">New-AutoSensitivityLabelRule</span><span class="sxs-lookup"><span data-stu-id="52dc8-373">New-AutoSensitivityLabelRule</span></span>](https://docs.microsoft.com/powershell/module/exchange/new-autosensitivitylabelrule)
- [<span data-ttu-id="52dc8-374">Remove-AutoSensitivityLabelPolicy</span><span class="sxs-lookup"><span data-stu-id="52dc8-374">Remove-AutoSensitivityLabelPolicy</span></span>](https://docs.microsoft.com/powershell/module/exchange/remove-autosensitivitylabelpolicy)
- [<span data-ttu-id="52dc8-375">Remove-AutoSensitivityLabelRule</span><span class="sxs-lookup"><span data-stu-id="52dc8-375">Remove-AutoSensitivityLabelRule</span></span>](https://docs.microsoft.com/powershell/module/exchange/remove-autosensitivitylabelrule)
- [<span data-ttu-id="52dc8-376">Set-AutoSensitivityLabelPolicy</span><span class="sxs-lookup"><span data-stu-id="52dc8-376">Set-AutoSensitivityLabelPolicy</span></span>](https://docs.microsoft.com/powershell/module/exchange/set-autosensitivitylabelpolicy)
- [<span data-ttu-id="52dc8-377">Set-AutoSensitivityLabelRule</span><span class="sxs-lookup"><span data-stu-id="52dc8-377">Set-AutoSensitivityLabelRule</span></span>](https://docs.microsoft.com/powershell/module/exchange/set-autosensitivitylabelrule)

