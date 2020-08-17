---
title: Microsoft 365 identity モデルと Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.date: 06/09/2020
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: クラウドのみまたはハイブリッドの id モデルを使用して、Microsoft 365 の Azure AD ユーザー id サービスを管理する方法について説明します。
ms.openlocfilehash: d91e14f678e487365805b024e4025e9a39db0c2c
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46692202"
---
# <a name="microsoft-365-identity-models-and-azure-active-directory"></a><span data-ttu-id="e626d-103">Microsoft 365 identity モデルと Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="e626d-103">Microsoft 365 identity models and Azure Active Directory</span></span>

<span data-ttu-id="e626d-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="e626d-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="e626d-105">Microsoft 365 では、Azure Active Directory (Azure AD) を使用して、microsoft 365 サブスクリプションに含まれているクラウドベースのユーザー id と認証サービスを使用して、Microsoft 365 の id と認証を管理しています。</span><span class="sxs-lookup"><span data-stu-id="e626d-105">Microsoft 365 uses Azure Active Directory (Azure AD), a cloud-based user identity and authentication service that is included with your Microsoft 365 subscription, to manage identities and authentication for Microsoft 365.</span></span> <span data-ttu-id="e626d-106">Id インフラストラクチャを正しく構成することは、組織の Microsoft 365 のユーザーアクセスとアクセス許可を管理するために不可欠です。</span><span class="sxs-lookup"><span data-stu-id="e626d-106">Getting your identity infrastructure configured correctly is vital to managing Microsoft 365 user access and permissions for your organization.</span></span>

<span data-ttu-id="e626d-107">開始する前に、Microsoft 365 の ID モデルと認証の概要についてこのビデオをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e626d-107">Before you begin, watch this video for an overview of identity models and authentication for Microsoft 365.</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

<span data-ttu-id="e626d-108">最初の計画の選択は、Microsoft 365 の id モデルです。</span><span class="sxs-lookup"><span data-stu-id="e626d-108">Your first planning choice is the Microsoft 365 identity model.</span></span>

## <a name="microsoft-365-identity-models"></a><span data-ttu-id="e626d-109">Microsoft 365 id モデル</span><span class="sxs-lookup"><span data-stu-id="e626d-109">Microsoft 365 identity models</span></span>

<span data-ttu-id="e626d-110">ユーザーアカウントを計画するには、まず、Microsoft 365 で2つの id モデルを理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e626d-110">To plan for user accounts, you first need to understand the two identity models in Microsoft 365.</span></span> <span data-ttu-id="e626d-111">組織の id は、クラウド内でのみ管理できます。または、オンプレミスの Active Directory ドメインサービス (AD DS) の id を維持して、ユーザーが Microsoft 365 cloud services にアクセスするときの認証に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="e626d-111">You can maintain your organization's identities only in the cloud, or you can maintain your on-premises Active Directory Domain Services (AD DS) identities and use them for authentication when users access Microsoft 365 cloud services.</span></span>  

<span data-ttu-id="e626d-112">ここでは、2種類の id と、それらのユーザーにとって最適なものと利点を示します。</span><span class="sxs-lookup"><span data-stu-id="e626d-112">Here are the two types of identity and their best fit and benefits.</span></span>

| <span data-ttu-id="e626d-113">属性</span><span class="sxs-lookup"><span data-stu-id="e626d-113">Attribute</span></span> | <span data-ttu-id="e626d-114">クラウド専用 ID</span><span class="sxs-lookup"><span data-stu-id="e626d-114">Cloud-only identity</span></span> | <span data-ttu-id="e626d-115">ハイブリッド ID</span><span class="sxs-lookup"><span data-stu-id="e626d-115">Hybrid identity</span></span> |
|:-------|:-----|:-----|
| <span data-ttu-id="e626d-116">**定義**</span><span class="sxs-lookup"><span data-stu-id="e626d-116">**Definition**</span></span> | <span data-ttu-id="e626d-117">ユーザーアカウントは、Microsoft 365 サブスクリプションの Azure AD テナントにのみ存在します。</span><span class="sxs-lookup"><span data-stu-id="e626d-117">User account only exists in the Azure AD tenant for your Microsoft 365 subscription.</span></span> | <span data-ttu-id="e626d-118">ユーザーアカウントが AD DS に存在し、Microsoft 365 サブスクリプションの Azure AD テナントにもコピーがあります。</span><span class="sxs-lookup"><span data-stu-id="e626d-118">User account exists in AD DS and a copy is also in the Azure AD tenant for your Microsoft 365 subscription.</span></span> <span data-ttu-id="e626d-119">Azure AD のユーザーアカウントには、既にハッシュされた AD DS ユーザーアカウントのパスワードが含まれている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e626d-119">The user account in Azure AD might also include a hashed version of the already hashed AD DS user account password.</span></span> |
| <span data-ttu-id="e626d-120">**Microsoft 365 でユーザー資格情報を認証する方法**</span><span class="sxs-lookup"><span data-stu-id="e626d-120">**How Microsoft 365 authenticates user credentials**</span></span> | <span data-ttu-id="e626d-121">Microsoft 365 サブスクリプションの Azure AD テナントは、クラウド id アカウントを使用して認証を実行します。</span><span class="sxs-lookup"><span data-stu-id="e626d-121">The Azure AD tenant for your Microsoft 365 subscription performs the authentication with the cloud identity account.</span></span> | <span data-ttu-id="e626d-122">Microsoft 365 サブスクリプションの Azure AD テナントは、認証プロセスを処理するか、またはユーザーを別の id プロバイダーにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="e626d-122">The Azure AD tenant for your Microsoft 365 subscription either handles the authentication process or redirects the user to another identity provider.</span></span> |
| <span data-ttu-id="e626d-123">**最適シナリオ**</span><span class="sxs-lookup"><span data-stu-id="e626d-123">**Best for**</span></span> | <span data-ttu-id="e626d-124">社内の AD DS を必要としない、または必要としない組織。</span><span class="sxs-lookup"><span data-stu-id="e626d-124">Organizations that do not have or need an on-premises AD DS.</span></span> | <span data-ttu-id="e626d-125">AD DS または別の id プロバイダーを使用している組織。</span><span class="sxs-lookup"><span data-stu-id="e626d-125">Organizations using AD DS or another identity provider.</span></span> |
| <span data-ttu-id="e626d-126">**最大のメリット**</span><span class="sxs-lookup"><span data-stu-id="e626d-126">**Greatest benefit**</span></span> | <span data-ttu-id="e626d-127">簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="e626d-127">Simple to use.</span></span> <span data-ttu-id="e626d-128">その他のディレクトリツールやサーバーは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="e626d-128">No extra directory tools or servers required.</span></span> | <span data-ttu-id="e626d-129">ユーザーは、オンプレミスまたはクラウドベースのリソースにアクセスするときに同じ資格情報を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e626d-129">Users can use the same credentials when accessing on-premises or cloud-based resources.</span></span> |
||||

## <a name="cloud-only-identity"></a><span data-ttu-id="e626d-130">クラウド専用 ID</span><span class="sxs-lookup"><span data-stu-id="e626d-130">Cloud-only identity</span></span>

<span data-ttu-id="e626d-131">クラウド専用の id は、Azure AD のみに存在するユーザーアカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="e626d-131">A cloud-only identity uses user accounts that exist only in Azure AD.</span></span> <span data-ttu-id="e626d-132">クラウド id は、通常、オンプレミスサーバーを持たない小規模な組織、または AD DS を使用してローカル id を管理しない小規模な組織で使用されます。</span><span class="sxs-lookup"><span data-stu-id="e626d-132">Cloud identity is typically used by small organizations that do not have on-premises servers or do not use AD DS to manage local identities.</span></span> 

<span data-ttu-id="e626d-133">ここでは、クラウド専用の id の基本的なコンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="e626d-133">Here are the basic components of cloud-only identity.</span></span>
 
![クラウド専用の id の基本的なコンポーネント](../media/about-microsoft-365-identity/cloud-only-identity.png)

<span data-ttu-id="e626d-135">オンプレミスとリモート (オンライン) の両方のユーザーは、Azure AD のユーザーアカウントとパスワードを使用して、Microsoft 365 クラウドサービスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="e626d-135">Both on-premises and remote (online) users use their Azure AD user accounts and passwords to access Microsoft 365 cloud services.</span></span> <span data-ttu-id="e626d-136">Azure AD は、保存されたユーザーアカウントとパスワードに基づいてユーザー資格情報を認証します。</span><span class="sxs-lookup"><span data-stu-id="e626d-136">Azure AD authenticates user credentials based on its stored user accounts and passwords.</span></span>

### <a name="administration"></a><span data-ttu-id="e626d-137">管理</span><span class="sxs-lookup"><span data-stu-id="e626d-137">Administration</span></span>
<span data-ttu-id="e626d-138">ユーザーアカウントは Azure AD にのみ格納されるので、 [Microsoft 365 管理センター](https://admin.microsoft.com) や [Windows PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)などのツールを使用してクラウド id を管理します。</span><span class="sxs-lookup"><span data-stu-id="e626d-138">Because user accounts are only stored in Azure AD, you manage cloud identities with tools such as the [Microsoft 365 admin center](https://admin.microsoft.com) and [Windows PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md).</span></span> 

## <a name="hybrid-identity"></a><span data-ttu-id="e626d-139">ハイブリッド ID</span><span class="sxs-lookup"><span data-stu-id="e626d-139">Hybrid identity</span></span>

<span data-ttu-id="e626d-140">ハイブリッド id は、オンプレミスの AD DS で開始され、Microsoft 365 サブスクリプションの Azure AD テナントにコピーを持つアカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="e626d-140">Hybrid identity uses accounts that originate in an on-premises AD DS and have a copy in the Azure AD tenant of a Microsoft 365 subscription.</span></span> <span data-ttu-id="e626d-141">ただし、ほとんどの変更は1つの方法でのみフローします。</span><span class="sxs-lookup"><span data-stu-id="e626d-141">However, most changes only flow one way.</span></span> <span data-ttu-id="e626d-142">AD DS ユーザーアカウントに加えた変更は、Azure AD のコピーと同期されます。</span><span class="sxs-lookup"><span data-stu-id="e626d-142">Changes that you make to AD DS user accounts are synchronized to their copy in Azure AD.</span></span> <span data-ttu-id="e626d-143">しかし、新しいユーザーアカウントなどの Azure AD のクラウドベースのアカウントに加えられた変更は、AD DS と同期されません。</span><span class="sxs-lookup"><span data-stu-id="e626d-143">But changes made to cloud-based accounts in Azure AD, such as new user accounts, are not synchronized with AD DS.</span></span>

<span data-ttu-id="e626d-144">Azure AD Connect は、継続的なアカウント同期を提供します。</span><span class="sxs-lookup"><span data-stu-id="e626d-144">Azure AD Connect provides the ongoing account synchronization.</span></span> <span data-ttu-id="e626d-145">オンプレミスのサーバー上で実行され、AD DS の変更を確認し、それらの変更を Azure AD に転送します。</span><span class="sxs-lookup"><span data-stu-id="e626d-145">It runs on an on-premises server, checks for changes in the AD DS, and forwards those changes to Azure AD.</span></span> <span data-ttu-id="e626d-146">Azure AD Connect は、同期されているアカウントをフィルター処理する機能と、パスワードハッシュ同期 (PHS) と呼ばれるユーザーパスワードのハッシュバージョンを同期するかどうかを指定する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="e626d-146">Azure AD Connect provides the ability to filter which accounts are synchronized and whether to synchronize a hashed version of user passwords, known as password hash synchronization (PHS).</span></span>

<span data-ttu-id="e626d-147">ハイブリッド id を実装すると、オンプレミスの AD DS が、アカウント情報の権限のあるソースになります。</span><span class="sxs-lookup"><span data-stu-id="e626d-147">When you implement hybrid identity, your on-premises AD DS is the authoritative source for account information.</span></span> <span data-ttu-id="e626d-148">これは、ほとんどがオンプレミスの管理タスクを実行することを意味します。これは、Azure AD に同期されます。</span><span class="sxs-lookup"><span data-stu-id="e626d-148">This means that you perform administration tasks mostly on-premises, which are then synchronized to Azure AD.</span></span> 

<span data-ttu-id="e626d-149">ハイブリッド id のコンポーネントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="e626d-149">Here are the components of hybrid identity.</span></span>

![ハイブリッド id のコンポーネント](../media/about-microsoft-365-identity/hybrid-identity.png)

<span data-ttu-id="e626d-151">Azure AD テナントには、AD DS アカウントのコピーがあります。</span><span class="sxs-lookup"><span data-stu-id="e626d-151">The Azure AD tenant has a copy of the AD DS accounts.</span></span> <span data-ttu-id="e626d-152">この構成では、オンプレミスのユーザーと Microsoft 365 cloud services にアクセスするリモートユーザーの両方が Azure AD に対して認証されます。</span><span class="sxs-lookup"><span data-stu-id="e626d-152">In this configuration, both on-premises and remote users accessing Microsoft 365 cloud services authenticate against Azure AD.</span></span>

>[!Note]
><span data-ttu-id="e626d-153">ハイブリッド id のユーザーアカウントを同期するには、常に Azure AD Connect を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e626d-153">You always need to use Azure AD Connect to synchronize user accounts for hybrid identity.</span></span> <span data-ttu-id="e626d-154">ライセンスの割り当てとグループ管理、アクセス許可の構成、およびユーザーアカウントに関連するその他の管理タスクを実行するには、Azure AD の同期されたユーザーアカウントが必要です。</span><span class="sxs-lookup"><span data-stu-id="e626d-154">You need the synchronized user accounts in Azure AD to perform license assignment and group management, configure permissions, and other administrative tasks that involve user accounts.</span></span>
>

### <a name="administration"></a><span data-ttu-id="e626d-155">管理</span><span class="sxs-lookup"><span data-stu-id="e626d-155">Administration</span></span>

<span data-ttu-id="e626d-156">元のユーザーアカウントと権限のあるユーザーアカウントは、オンプレミスの AD DS に格納されるので、Active Directory ユーザーおよびコンピューターツールなどの AD DS と同じツールを使用して id を管理します。</span><span class="sxs-lookup"><span data-stu-id="e626d-156">Because the original and authoritative user accounts are stored in the on-premises AD DS, you manage your identities with the same tools as AD DS, such as the Active Directory Users and Computers tool.</span></span> 

<span data-ttu-id="e626d-157">Microsoft 365 管理センターまたは Microsoft 365 の PowerShell を使用して、Azure AD で同期されたユーザーアカウントを管理することはありません。</span><span class="sxs-lookup"><span data-stu-id="e626d-157">You don't use the Microsoft 365 admin center or PowerShell for Microsoft 365 to manage synchronized user accounts in Azure AD.</span></span>

## <a name="next-step"></a><span data-ttu-id="e626d-158">次の手順</span><span class="sxs-lookup"><span data-stu-id="e626d-158">Next step</span></span>

<span data-ttu-id="e626d-159">クラウド専用の id モデルが必要な場合は、「 [cloud only identity](cloud-only-identities.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e626d-159">If you need the cloud-only identity model, see [Cloud-only identity](cloud-only-identities.md).</span></span>

<span data-ttu-id="e626d-160">ハイブリッド id モデルが必要な場合は、「 [ハイブリッド id](plan-for-directory-synchronization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e626d-160">If you need the hybrid identity model, see [Hybrid identity](plan-for-directory-synchronization.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="e626d-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="e626d-161">See also</span></span>

[<span data-ttu-id="e626d-162">Microsoft 365 Enterprise の概要</span><span class="sxs-lookup"><span data-stu-id="e626d-162">Microsoft 365 Enterprise overview</span></span>](microsoft-365-overview.md)