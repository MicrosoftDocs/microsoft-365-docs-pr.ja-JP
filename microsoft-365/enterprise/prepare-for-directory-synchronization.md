---
title: Prepare for directory synchronization to Microsoft 365 (Microsoft 365 へのディレクトリ同期を準備する)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: ディレクトリ同期を使用して Microsoft 365 にユーザーをプロビジョニングするための準備方法と、この方法を使用する長期的な利点について説明します。
ms.openlocfilehash: cf5afc05b8273974c069662c2b887092fdd20b96
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46696213"
---
# <a name="prepare-for-directory-synchronization-to-microsoft-365"></a><span data-ttu-id="fcbd7-103">Prepare for directory synchronization to Microsoft 365 (Microsoft 365 へのディレクトリ同期を準備する)</span><span class="sxs-lookup"><span data-stu-id="fcbd7-103">Prepare for directory synchronization to Microsoft 365</span></span>

<span data-ttu-id="fcbd7-104">*この記事は、Microsoft 365 Enterprise と Microsoft 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="fcbd7-104">*This article applies to both Microsoft 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="fcbd7-105">組織のハイブリッド id とディレクトリ同期の利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-105">The benefits to hybrid identity and directory synchronization your organization include:</span></span>
  
- <span data-ttu-id="fcbd7-106">組織内の管理プログラムを減らす</span><span class="sxs-lookup"><span data-stu-id="fcbd7-106">Reducing the administrative programs in your organization</span></span>
- <span data-ttu-id="fcbd7-107">オプションでシングルサインオンのシナリオを有効にする</span><span class="sxs-lookup"><span data-stu-id="fcbd7-107">Optionally enabling single sign-on scenario</span></span>
- <span data-ttu-id="fcbd7-108">Microsoft 365 でのアカウントの変更の自動化</span><span class="sxs-lookup"><span data-stu-id="fcbd7-108">Automating account changes in Microsoft 365</span></span>
    
<span data-ttu-id="fcbd7-109">ディレクトリ同期を使用する利点の詳細については、「 [Microsoft 365 の](plan-for-directory-synchronization.md)[ディレクトリ同期のロードマップ]( https://go.microsoft.com/fwlink/p/?LinkId=525398)」および「ハイブリッド id」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-109">For more information about the advantages of using directory synchronization, see [Directory synchronization roadmap]( https://go.microsoft.com/fwlink/p/?LinkId=525398) and [Hybrid identity for Microsoft 365](plan-for-directory-synchronization.md).</span></span>

<span data-ttu-id="fcbd7-110">ただし、ディレクトリ同期では、Active Directory ドメインサービス (AD DS) が、少なくとも1つのエラーを含む Microsoft 365 サブスクリプションの Azure Active Directory (Azure AD) テナントに同期されるように計画と準備を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-110">However, directory synchronization requires planning and preparation to ensure that your Active Directory Domain Services (AD DS) synchronizes to the Azure Active Directory (Azure AD) tenant of your Microsoft 365 subscription with a minimum of errors.</span></span> 

<span data-ttu-id="fcbd7-111">最適な結果を得るために、以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-111">Follow these steps in order for the best results.</span></span>
  
## <a name="1-directory-cleanup-tasks"></a><span data-ttu-id="fcbd7-112">1. ディレクトリクリーンアップタスク</span><span class="sxs-lookup"><span data-stu-id="fcbd7-112">1. Directory cleanup tasks</span></span>

<span data-ttu-id="fcbd7-113">AD DS を Azure AD テナントと同期する前に、AD DS をクリーンアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-113">Before you synchronize your AD DS to your Azure AD tenant, you need to clean up your AD DS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fcbd7-114">同期する前に AD DS のクリーンアップを実行しない場合は、展開プロセスに著しい悪影響を及ぼす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-114">If you don't perform AD DS cleanup before you synchronize, there can be a significant negative effect on the deployment process.</span></span> <span data-ttu-id="fcbd7-115">ディレクトリ同期のサイクルを経て、エラーを特定し、再同期を実行するまでに、数日または数週間かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-115">It might take days, or even weeks, to go through the cycle of directory synchronization, identifying errors, and re-synchronization.</span></span> 
  
<span data-ttu-id="fcbd7-116">AD DS で、Microsoft 365 ライセンスが割り当てられる各ユーザーアカウントに対して次のクリーンアップタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-116">In your AD DS, complete the following clean-up tasks for each user account that will be assigned a Microsoft 365 license:</span></span>
  
1. <span data-ttu-id="fcbd7-117">**ProxyAddresses**属性に、有効な一意の電子メールアドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-117">Ensure a valid and unique email address in the **proxyAddresses** attribute.</span></span> 
  
2. <span data-ttu-id="fcbd7-118">**ProxyAddresses**属性の重複する値を削除します。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-118">Remove any duplicate values in the **proxyAddresses** attribute.</span></span> 
    
3.  <span data-ttu-id="fcbd7-119">可能であれば、ユーザーの**ユーザー**オブジェクトの**userPrincipalName**属性の有効な一意の値を確認してください。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-119">If possible, ensure a valid and unique value for the **userPrincipalName** attribute in the user's **user** object.</span></span> <span data-ttu-id="fcbd7-120">最適な同期処理を行うには、AD DS UPN が Azure AD UPN に一致していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-120">For the best synchronization experience, ensure that the AD DS UPN matches the Azure AD UPN.</span></span> <span data-ttu-id="fcbd7-121">ユーザーが **userPrincipalName** 属性の値を持っていない場合は、 **ユーザー** オブジェクトに **sAMAccountName** 属性の有効な一意の値が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-121">If a user does not have a value for the **userPrincipalName** attribute, then the **user** object must contain a valid and unique value for the **sAMAccountName** attribute.</span></span> <span data-ttu-id="fcbd7-122">**UserPrincipalName**属性の重複する値を削除します。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-122">Remove any duplicate values in the **userPrincipalName** attribute.</span></span> 
    
4. <span data-ttu-id="fcbd7-123">グローバルアドレス一覧 (GAL) を最適に使用するには、AD DS ユーザーアカウントの次の属性の情報が正しいことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-123">For optimal use of the global address list (GAL), ensure the information in the following attributes of the AD DS user account is correct:</span></span>
    
  - <span data-ttu-id="fcbd7-124">givenName</span><span class="sxs-lookup"><span data-stu-id="fcbd7-124">givenName</span></span>
  - <span data-ttu-id="fcbd7-125">surname</span><span class="sxs-lookup"><span data-stu-id="fcbd7-125">surname</span></span>
  - <span data-ttu-id="fcbd7-126">displayName</span><span class="sxs-lookup"><span data-stu-id="fcbd7-126">displayName</span></span>
  - <span data-ttu-id="fcbd7-127">役職</span><span class="sxs-lookup"><span data-stu-id="fcbd7-127">Job Title</span></span>
  - <span data-ttu-id="fcbd7-128">部署</span><span class="sxs-lookup"><span data-stu-id="fcbd7-128">Department</span></span>
  - <span data-ttu-id="fcbd7-129">事業所</span><span class="sxs-lookup"><span data-stu-id="fcbd7-129">Office</span></span>
  - <span data-ttu-id="fcbd7-130">事業所電話番号</span><span class="sxs-lookup"><span data-stu-id="fcbd7-130">Office Phone</span></span>
  - <span data-ttu-id="fcbd7-131">携帯電話番号</span><span class="sxs-lookup"><span data-stu-id="fcbd7-131">Mobile Phone</span></span>
  - <span data-ttu-id="fcbd7-132">FAX 番号</span><span class="sxs-lookup"><span data-stu-id="fcbd7-132">Fax Number</span></span>
  - <span data-ttu-id="fcbd7-133">番地</span><span class="sxs-lookup"><span data-stu-id="fcbd7-133">Street Address</span></span>
  - <span data-ttu-id="fcbd7-134">都市</span><span class="sxs-lookup"><span data-stu-id="fcbd7-134">City</span></span>
  - <span data-ttu-id="fcbd7-135">都道府県</span><span class="sxs-lookup"><span data-stu-id="fcbd7-135">State or Province</span></span>
  - <span data-ttu-id="fcbd7-136">郵便番号</span><span class="sxs-lookup"><span data-stu-id="fcbd7-136">Zip or Postal Code</span></span>
  - <span data-ttu-id="fcbd7-137">国または地域</span><span class="sxs-lookup"><span data-stu-id="fcbd7-137">Country or Region</span></span>
    
## <a name="2-directory-object-and-attribute-preparation"></a><span data-ttu-id="fcbd7-138">2. ディレクトリオブジェクトと属性の準備</span><span class="sxs-lookup"><span data-stu-id="fcbd7-138">2. Directory object and attribute preparation</span></span>

<span data-ttu-id="fcbd7-139">AD DS と Microsoft 365 の間のディレクトリ同期を正常に行うには、AD DS 属性が適切に準備されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-139">Successful directory synchronization between your AD DS and Microsoft 365 requires that your AD DS attributes are properly prepared.</span></span> <span data-ttu-id="fcbd7-140">たとえば、Microsoft 365 環境と同期されている特定の属性に特定の文字が使用されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-140">For example, you need to ensure that specific characters aren't used in certain attributes that are synchronized with the Microsoft 365 environment.</span></span> <span data-ttu-id="fcbd7-141">予期しない文字によってディレクトリ同期が失敗することはありませんが、警告が返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-141">Unexpected characters do not cause directory synchronization to fail but might return a warning.</span></span> <span data-ttu-id="fcbd7-142">無効な文字は、ディレクトリ同期が失敗する原因となります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-142">Invalid characters will cause directory synchronization to fail.</span></span>
  
<span data-ttu-id="fcbd7-143">一部の AD DS ユーザーが1つ以上の重複した属性を持っている場合も、ディレクトリ同期は失敗します。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-143">Directory synchronization will also fail if some of your AD DS users have one or more duplicate attributes.</span></span> <span data-ttu-id="fcbd7-144">各ユーザーは固有の属性を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-144">Each user must have unique attributes.</span></span>
  
<span data-ttu-id="fcbd7-145">準備する必要がある属性を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-145">The attributes that you need to prepare are listed here:</span></span>
  
- <span data-ttu-id="fcbd7-146">**displayName**</span><span class="sxs-lookup"><span data-stu-id="fcbd7-146">**displayName**</span></span>
    
  - <span data-ttu-id="fcbd7-147">属性が user オブジェクトに存在する場合は、Microsoft 365 と同期されます。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-147">If the attribute exists in the user object, it will be synchronized with Microsoft 365.</span></span>
  - <span data-ttu-id="fcbd7-148">この属性が user オブジェクトに存在する場合は、その値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-148">If this attribute exists in the user object, there must be a value for it.</span></span> <span data-ttu-id="fcbd7-149">つまり、属性を空白にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-149">That is, the attribute must not be blank.</span></span>
  - <span data-ttu-id="fcbd7-150">最大文字数: 256</span><span class="sxs-lookup"><span data-stu-id="fcbd7-150">Maximum number of characters: 256</span></span>
    
- <span data-ttu-id="fcbd7-151">**givenName**</span><span class="sxs-lookup"><span data-stu-id="fcbd7-151">**givenName**</span></span>
    
  - <span data-ttu-id="fcbd7-152">属性が user オブジェクトに存在する場合、その属性は Microsoft 365 と同期されますが、Microsoft 365 では要求も使用もされません。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-152">If the attribute exists in the user object, it will be synchronized with Microsoft 365, but Microsoft 365 does not require or use it.</span></span>
  - <span data-ttu-id="fcbd7-153">最大文字数:64</span><span class="sxs-lookup"><span data-stu-id="fcbd7-153">Maximum number of characters: 64</span></span>
    
- <span data-ttu-id="fcbd7-154">**mail**</span><span class="sxs-lookup"><span data-stu-id="fcbd7-154">**mail**</span></span>
    
  - <span data-ttu-id="fcbd7-155">この属性の値は、ディレクトリ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-155">The attribute value must be unique within the directory.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="fcbd7-156">重複する値がある場合、値を持つ最初のユーザーが同期されます。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-156">If there are duplicate values, the first user with the value is synchronized.</span></span> <span data-ttu-id="fcbd7-157">今後のユーザーは、Microsoft 365 に表示されません。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-157">Subsequent users will not appear in Microsoft 365.</span></span> <span data-ttu-id="fcbd7-158">Microsoft 365 の値を変更するか、両方のユーザーを Microsoft 365 に表示するために、AD DS の両方の値を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-158">You must modify either the value in Microsoft 365 or modify both of the values in AD DS in order for both users to appear in Microsoft 365.</span></span> 
  
- <span data-ttu-id="fcbd7-159">**mailNickname** (Exchange エイリアス)</span><span class="sxs-lookup"><span data-stu-id="fcbd7-159">**mailNickname** (Exchange alias)</span></span> 
    
  - <span data-ttu-id="fcbd7-160">属性値はピリオド (.) で始めることはできません。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-160">The attribute value cannot begin with a period (.).</span></span>
  - <span data-ttu-id="fcbd7-161">この属性の値は、ディレクトリ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-161">The attribute value must be unique within the directory.</span></span>
  
    > [!NOTE]
    > <span data-ttu-id="fcbd7-162">同期名のアンダスコア ("_") は、この属性の元の値に無効な文字が含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-162">Underscores ("_") in the synchronized name indicates that the original value of this attribute contains invalid characters.</span></span> <span data-ttu-id="fcbd7-163">この属性の詳細については、「 [Exchange alias attribute](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-mailbox?view=exchange-ps)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-163">For more information on this attribute, see [Exchange alias attribute](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-mailbox?view=exchange-ps).</span></span>
    >
      
- <span data-ttu-id="fcbd7-164">**proxyAddresses**</span><span class="sxs-lookup"><span data-stu-id="fcbd7-164">**proxyAddresses**</span></span>
    
  - <span data-ttu-id="fcbd7-165">複数値の属性</span><span class="sxs-lookup"><span data-stu-id="fcbd7-165">Multiple-value attribute</span></span>
  - <span data-ttu-id="fcbd7-166">値あたりの最大文字数: 256</span><span class="sxs-lookup"><span data-stu-id="fcbd7-166">Maximum number of characters per value: 256</span></span>
  - <span data-ttu-id="fcbd7-167">属性の値にスペースを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-167">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="fcbd7-168">この属性の値は、ディレクトリ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-168">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="fcbd7-169">無効な文字: \< \> ();, [] "'</span><span class="sxs-lookup"><span data-stu-id="fcbd7-169">Invalid characters: \< \> ( ) ; , [ ] " '</span></span>
    
    <span data-ttu-id="fcbd7-170">無効な文字は、SMTP:User@contso.com が許可されていても、SMTP:user:M@contoso.com は許可されていませんが、型区切り記号の後の文字と ":" に適用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-170">Note that the invalid characters apply to the characters following the type delimiter and ":", such that SMTP:User@contso.com is allowed, but SMTP:user:M@contoso.com is not.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="fcbd7-171">すべての簡易メール転送プロトコル (SMTP) アドレスは、電子メールメッセージング標準に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-171">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span> <span data-ttu-id="fcbd7-172">重複しているまたは不要なアドレスが存在する場合は、ヘルプトピックの「 [Exchange での重複および不要なプロキシアドレスの削除](https://go.microsoft.com/fwlink/?LinkId=293860)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-172">If duplicate or unwanted addresses exist, see the Help topic [Removing duplicate and unwanted proxy addresses in Exchange](https://go.microsoft.com/fwlink/?LinkId=293860).</span></span> 
  
- <span data-ttu-id="fcbd7-173">**sAMAccountName**</span><span class="sxs-lookup"><span data-stu-id="fcbd7-173">**sAMAccountName**</span></span>
    
  - <span data-ttu-id="fcbd7-174">最大文字数:20</span><span class="sxs-lookup"><span data-stu-id="fcbd7-174">Maximum number of characters: 20</span></span>
  - <span data-ttu-id="fcbd7-175">この属性の値は、ディレクトリ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-175">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="fcbd7-176">無効な文字: [\ "|,/: \< \> + =;?</span><span class="sxs-lookup"><span data-stu-id="fcbd7-176">Invalid characters: [ \ " | , / : \< \> + = ; ?</span></span> <span data-ttu-id="fcbd7-177">\* ']</span><span class="sxs-lookup"><span data-stu-id="fcbd7-177">\* ']</span></span>
  - <span data-ttu-id="fcbd7-178">ユーザーの **sAMAccountName** 属性が無効で、 **userPrincipalName** 属性が有効な場合、ユーザーアカウントは Microsoft 365 で作成されます。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-178">If a user has an invalid **sAMAccountName** attribute but has a valid **userPrincipalName** attribute, the user account is created in Microsoft 365.</span></span> 
  - <span data-ttu-id="fcbd7-179">**SAMAccountName**と**userPrincipalName**の両方が無効な場合は、AD DS **userPrincipalName**属性を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-179">If both **sAMAccountName** and **userPrincipalName** are invalid, the AD DS **userPrincipalName** attribute must be updated.</span></span> 
    
- <span data-ttu-id="fcbd7-180">**sn** (姓)</span><span class="sxs-lookup"><span data-stu-id="fcbd7-180">**sn** (surname)</span></span> 
    
  - <span data-ttu-id="fcbd7-181">属性が user オブジェクトに存在する場合、その属性は Microsoft 365 と同期されますが、Microsoft 365 では要求も使用もされません。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-181">If the attribute exists in the user object, it will be synchronized with Microsoft 365, but Microsoft 365 does not require or use it.</span></span>
    
- <span data-ttu-id="fcbd7-182">**targetAddress**</span><span class="sxs-lookup"><span data-stu-id="fcbd7-182">**targetAddress**</span></span>
    
    <span data-ttu-id="fcbd7-183">ユーザーに対して設定されている **targetAddress** 属性 (たとえば、SMTP:tom@contoso.com) を MICROSOFT 365 GAL に表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-183">It's required that the **targetAddress** attribute (for example, SMTP:tom@contoso.com) that's populated for the user must appear in the Microsoft 365 GAL.</span></span> <span data-ttu-id="fcbd7-184">サードパーティ製のメッセージング移行シナリオでは、AD DS の Microsoft 365 スキーマ拡張が必要になります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-184">In third-party messaging migration scenarios, this would require the Microsoft 365 schema extension for the AD DS.</span></span> <span data-ttu-id="fcbd7-185">また、Microsoft 365 スキーマ拡張機能は、AD DS からのディレクトリ同期ツールを使用して設定された Microsoft 365 オブジェクトを管理するための便利な属性も追加します。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-185">The Microsoft 365 schema extension would also add other useful attributes to manage Microsoft 365 objects that are populated by using a directory synchronization tool from AD DS.</span></span> <span data-ttu-id="fcbd7-186">たとえば、非表示のメールボックスまたは配布グループを管理する **msExchHideFromAddressLists** 属性が追加されます。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-186">For example, the **msExchHideFromAddressLists** attribute to manage hidden mailboxes or distribution groups would be added.</span></span> 
   
  - <span data-ttu-id="fcbd7-187">最大文字数: 256</span><span class="sxs-lookup"><span data-stu-id="fcbd7-187">Maximum number of characters: 256</span></span>
  - <span data-ttu-id="fcbd7-188">属性の値にスペースを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-188">The attribute value must not contain a space.</span></span>
  - <span data-ttu-id="fcbd7-189">この属性の値は、ディレクトリ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-189">The attribute value must be unique within the directory.</span></span>
  - <span data-ttu-id="fcbd7-190">無効な文字: \ \< \> ();, [] "</span><span class="sxs-lookup"><span data-stu-id="fcbd7-190">Invalid characters: \ \< \> ( ) ; , [ ] "</span></span>
  - <span data-ttu-id="fcbd7-191">すべての簡易メール転送プロトコル (SMTP) アドレスは、電子メールメッセージング標準に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-191">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
    
- <span data-ttu-id="fcbd7-192">**userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="fcbd7-192">**userPrincipalName**</span></span>
    
  - <span data-ttu-id="fcbd7-193">**UserPrincipalName**属性は、ユーザー名の後にアットマーク記号 (@) とドメイン名が続く、インターネットスタイルのサインイン形式にする必要があります。たとえば、user@contoso.com のようにします。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-193">The **userPrincipalName** attribute must be in the Internet-style sign-in format where the user name is followed by the at sign (@) and a domain name: for example, user@contoso.com.</span></span> <span data-ttu-id="fcbd7-194">すべての簡易メール転送プロトコル (SMTP) アドレスは、電子メールメッセージング標準に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-194">All Simple Mail Transport Protocol (SMTP) addresses should comply with email messaging standards.</span></span>
  - <span data-ttu-id="fcbd7-195">**UserPrincipalName**属性の最大文字数は113です。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-195">The maximum number of characters for the **userPrincipalName** attribute is 113.</span></span> <span data-ttu-id="fcbd7-196">アットマーク (@) の前後には、次のように特定の文字数が許可されます。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-196">A specific number of characters are permitted before and after the at sign (@), as follows:</span></span> 
  - <span data-ttu-id="fcbd7-197">アットマーク (@) の前にあるユーザー名の最大文字数:64</span><span class="sxs-lookup"><span data-stu-id="fcbd7-197">Maximum number of characters for the username that is in front of the at sign (@): 64</span></span>
  - <span data-ttu-id="fcbd7-198">アットマーク記号 (@) の後に続くドメイン名の最大文字数:48</span><span class="sxs-lookup"><span data-stu-id="fcbd7-198">Maximum number of characters for the domain name following the at sign (@): 48</span></span>
  - <span data-ttu-id="fcbd7-199">無効な文字: \% &amp; \* +/=?</span><span class="sxs-lookup"><span data-stu-id="fcbd7-199">Invalid characters: \ % &amp; \* + / = ?</span></span> <span data-ttu-id="fcbd7-200">{ } | \< \> ( ) ; : , [ ] " '</span><span class="sxs-lookup"><span data-stu-id="fcbd7-200">{ } | \< \> ( ) ; : , [ ] " '</span></span>
  - <span data-ttu-id="fcbd7-201">ウムラウトは、無効な文字でもあります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-201">An umlaut is also an invalid character.</span></span>
  - <span data-ttu-id="fcbd7-202">各 **userPrincipalName** 値には @ 文字が必要です。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-202">The @ character is required in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="fcbd7-203">各 **userPrincipalName** 値の先頭文字に @ 文字を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-203">The @ character cannot be the first character in each **userPrincipalName** value.</span></span> 
  - <span data-ttu-id="fcbd7-204">ユーザー名の末尾には、ピリオド (.)、アンパサンド ( &amp; )、スペース、アットマーク (@) を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-204">The username cannot end with a period (.), an ampersand (&amp;), a space, or an at sign (@).</span></span>
  - <span data-ttu-id="fcbd7-205">ユーザー名にスペースを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-205">The username cannot contain any spaces.</span></span>
  - <span data-ttu-id="fcbd7-206">ルーティング可能なドメインを使用する必要があります。たとえば、ローカルまたは内部のドメインを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-206">Routable domains must be used; for example, local or internal domains cannot be used.</span></span>
  - <span data-ttu-id="fcbd7-207">Unicode は、アンダースコア文字に変換されます。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-207">Unicode is converted to underscore characters.</span></span>
  - <span data-ttu-id="fcbd7-208">**userPrincipalName** には、ディレクトリ内に重複する値を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-208">**userPrincipalName** cannot contain any duplicate values in the directory.</span></span> 
    
## <a name="3-prepare-the-userprincipalname-attribute"></a><span data-ttu-id="fcbd7-209">3. userPrincipalName 属性を準備する</span><span class="sxs-lookup"><span data-stu-id="fcbd7-209">3. Prepare the userPrincipalName attribute</span></span>

<span data-ttu-id="fcbd7-210">Active Directory は、組織内のエンドユーザーが **sAMAccountName** または **userPrincipalName**のいずれかを使用してディレクトリにサインインできるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-210">Active Directory is designed to allow the end users in your organization to sign in to your directory by using either **sAMAccountName** or **userPrincipalName**.</span></span> <span data-ttu-id="fcbd7-211">同様に、エンドユーザーは、職場または学校のアカウントのユーザープリンシパル名 (UPN) を使用して、Microsoft 365 にサインインできます。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-211">Similarly, end users can sign in to Microsoft 365 by using the user principal name (UPN) of their work or school account.</span></span> <span data-ttu-id="fcbd7-212">ディレクトリ同期では、AD DS 内の同じ UPN を使用して、Azure Active Directory で新しいユーザーを作成しようとしています。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-212">Directory synchronization attempts to create new users in Azure Active Directory by using the same UPN that's in your AD DS.</span></span> <span data-ttu-id="fcbd7-213">UPN は、電子メールアドレスのように書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-213">The UPN is formatted like an email address.</span></span> 

<span data-ttu-id="fcbd7-214">Microsoft 365 では、UPN は電子メールアドレスの生成に使用される既定の属性です。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-214">In Microsoft 365, the UPN is the default attribute that's used to generate the email address.</span></span> <span data-ttu-id="fcbd7-215">**UserPrincipalName** (ad DS および Azure ad) と**proxyAddresses**のプライマリ電子メールアドレスは、異なる値に設定するのが簡単です。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-215">It's easy to get **userPrincipalName** (in AD DS and in Azure AD) and the primary email address in **proxyAddresses** set to different values.</span></span> <span data-ttu-id="fcbd7-216">複数の値が設定されている場合、管理者とエンドユーザーに混乱が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-216">When they are set to different values, there can be confusion for administrators and end users.</span></span> 
  
<span data-ttu-id="fcbd7-217">これらの属性を調整して混乱を軽減することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-217">It's best to align these attributes to reduce confusion.</span></span> <span data-ttu-id="fcbd7-218">Active Directory フェデレーションサービス (AD FS) 2.0 を使用したシングルサインオンの要件を満たすには、Azure Active Directory と AD DS の Upn が一致し、有効なドメイン名前空間を使用していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-218">To meet the requirements of single sign-on with Active Directory Federation Services (AD FS) 2.0, you need to ensure that the UPNs in Azure Active Directory and your AD DS match and are using a valid domain namespace.</span></span>
  
## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a><span data-ttu-id="fcbd7-219">4. AD DS に代替 UPN サフィックスを追加する</span><span class="sxs-lookup"><span data-stu-id="fcbd7-219">4. Add an alternative UPN suffix to AD DS</span></span>

<span data-ttu-id="fcbd7-220">ユーザーの会社の資格情報を Microsoft 365 環境に関連付けるには、代替 UPN サフィックスを追加する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-220">You may need to add an alternative UPN suffix to associate the user's corporate credentials with the Microsoft 365 environment.</span></span> <span data-ttu-id="fcbd7-221">UPN サフィックスは、@ 文字の右側の UPN の一部です。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-221">A UPN suffix is the part of a UPN to the right of the @ character.</span></span> <span data-ttu-id="fcbd7-222">シングル サインオンに使用する UPN には文字、数字、ピリオド、ダッシュ、アンダースコアを含めることができますが、その他の種類の文字を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-222">UPNs that are used for single sign-on can contain letters, numbers, periods, dashes, and underscores, but no other types of characters.</span></span>
  
<span data-ttu-id="fcbd7-223">Active Directory に代替 UPN サフィックスを追加する方法の詳細については、「 [ディレクトリ同期の準備]( https://go.microsoft.com/fwlink/p/?LinkId=525430)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-223">For more information on how to add an alternative UPN suffix to Active Directory, see [Prepare for directory synchronization]( https://go.microsoft.com/fwlink/p/?LinkId=525430).</span></span>
  
## <a name="5-match-the-ad-ds-upn-with-the-microsoft-365-upn"></a><span data-ttu-id="fcbd7-224">5. AD DS UPN と Microsoft 365 UPN を一致させる</span><span class="sxs-lookup"><span data-stu-id="fcbd7-224">5. Match the AD DS UPN with the Microsoft 365 UPN</span></span>

<span data-ttu-id="fcbd7-225">ディレクトリ同期が既にセットアップされている場合、Microsoft 365 用のユーザーの UPN は、AD DS で定義されているユーザーの AD DS UPN と一致しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-225">If you've already set up directory synchronization, the user's UPN for Microsoft 365 may not match the user's AD DS UPN that's defined in your AD DS.</span></span> <span data-ttu-id="fcbd7-226">ドメインが確認される前にユーザーにライセンスを割り当てた場合、この状況が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-226">This can occur when a user was assigned a license before the domain was verified.</span></span> <span data-ttu-id="fcbd7-227">この問題を解決するには、PowerShell を使用して重複した [upn を修正](https://go.microsoft.com/fwlink/p/?LinkId=396730) し、MICROSOFT 365 upn が企業ユーザー名とドメインと一致するようにします。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-227">To fix this, use [PowerShell to fix duplicate UPN](https://go.microsoft.com/fwlink/p/?LinkId=396730) to update the user's UPN to ensure that the Microsoft 365 UPN matches the corporate user name and domain.</span></span> <span data-ttu-id="fcbd7-228">AD DS で UPN を更新していて、Azure Active Directory id と同期する必要がある場合は、AD DS で変更を行う前に、Microsoft 365 でユーザーのライセンスを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-228">If you are updating the UPN in the AD DS and would like it to synchronize with the Azure Active Directory identity, you need to remove the user's license in Microsoft 365 prior to making the changes in AD DS.</span></span> 
  
<span data-ttu-id="fcbd7-229">また [、ディレクトリ同期にルーティング不能なドメイン (たとえば、ローカルドメイン) を準備する方法に](prepare-a-non-routable-domain-for-directory-synchronization.md)ついても説明します。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-229">Also see [How to prepare a non-routable domain (such as .local domain) for directory synchronization](prepare-a-non-routable-domain-for-directory-synchronization.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="fcbd7-230">次の手順</span><span class="sxs-lookup"><span data-stu-id="fcbd7-230">Next steps</span></span>

<span data-ttu-id="fcbd7-231">上記の手順 1 ~ 5 を実行した場合は、「 [ディレクトリ同期をセットアップ](set-up-directory-synchronization.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcbd7-231">If you have done steps 1 through 5 above, see [Set up directory synchronization](set-up-directory-synchronization.md).</span></span>