---
title: Microsoft 365 Business で Azure ADに参加しているデバイスからオンプレミスのリソースにアクセスする
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.collection: M365-subscription-management
localization_priority: Normal
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: b0f4d010-9fd1-44d0-9d20-fabad2cdbab5
description: Azure Active Directory に参加している Windows 10 デバイスから、業務アプリ、ファイル共有、プリンターなど、オンプレミスのリソースにアクセスする方法について説明します。
ms.openlocfilehash: fc02fd30f41f25f52e653e750a6bdfd1bd7f800e
ms.sourcegitcommit: a62ac3c01ba700a51b78a647e2301f27ac437c5a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2021
ms.locfileid: "50233842"
---
# <a name="access-on-premises-resources-from-an-azure-ad-joined-device-in-microsoft-365-business-premium"></a><span data-ttu-id="a09e2-103">Microsoft 365 Business Premium で Azure ADに参加しているデバイスからオンプレミスのリソースにアクセスする</span><span class="sxs-lookup"><span data-stu-id="a09e2-103">Access on-premises resources from an Azure AD-joined device in Microsoft 365 Business Premium</span></span>

<span data-ttu-id="a09e2-104">この記事は、Microsoft 365 Business Premium に適用されます。</span><span class="sxs-lookup"><span data-stu-id="a09e2-104">This article applies to Microsoft 365 Business Premium.</span></span>

<span data-ttu-id="a09e2-105">Azure Active Directory に参加しているすべての Windows 10 デバイスは、Microsoft 365 アプリなどのクラウドベースのすべてのリソースにアクセスし、Microsoft 365 Business Premium で保護できます。</span><span class="sxs-lookup"><span data-stu-id="a09e2-105">Any Windows 10 device that is Azure Active Directory joined has access to all cloud-based resources, such as your Microsoft 365 apps, and can be protected by Microsoft 365 Business Premium.</span></span> <span data-ttu-id="a09e2-106">また、業務 (LOB) アプリ、ファイル共有、プリンターなど、オンプレミスのリソースへのアクセスを許可することもできます。</span><span class="sxs-lookup"><span data-stu-id="a09e2-106">You can also allow access to on-premises resources like line of business (LOB) apps, file shares, and printers.</span></span> <span data-ttu-id="a09e2-107">アクセスを許可するには [、Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) を使用して、オンプレミスの Active Directory と Azure Active Directory を同期します。</span><span class="sxs-lookup"><span data-stu-id="a09e2-107">To allow access, use [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) to synchronize your on-premises Active Directory with Azure Active Directory.</span></span> 

<span data-ttu-id="a09e2-108">詳細については、「Azure Active Directory でのデバイス [管理の概要」を参照してください](https://docs.microsoft.com/azure/active-directory/device-management-introduction)。</span><span class="sxs-lookup"><span data-stu-id="a09e2-108">To learn more, see [Introduction to device management in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-introduction).</span></span>
<span data-ttu-id="a09e2-109">手順の概要については、次のセクションでも説明します。</span><span class="sxs-lookup"><span data-stu-id="a09e2-109">The steps are also summarized in the following sections.</span></span>
 
## <a name="run-azure-ad-connect"></a><span data-ttu-id="a09e2-110">Azure AD Connect を実行する</span><span class="sxs-lookup"><span data-stu-id="a09e2-110">Run Azure AD Connect</span></span>

<span data-ttu-id="a09e2-111">次の手順を実行して、組織の Azure ADに参加しているデバイスがオンプレミスのリソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a09e2-111">Complete the following steps to enable your organization's Azure AD joined devices to access on-premises resources.</span></span>
  
1. <span data-ttu-id="a09e2-112">ローカル Active Directory から Azure Active Directory にユーザー、グループ、連絡先を同期するには、「Office [365](https://docs.microsoft.com/microsoft-365/enterprise/set-up-directory-synchronization)のディレクトリ同期をセットアップする」の説明に従って、ディレクトリ同期ウィザードと Azure AD Connect を実行します。</span><span class="sxs-lookup"><span data-stu-id="a09e2-112">To synchronize your users, groups, and contacts from local Active Directory into Azure Active Directory, run the Directory synchronization wizard and Azure AD Connect as described in [Set up directory synchronization for Office 365](https://docs.microsoft.com/microsoft-365/enterprise/set-up-directory-synchronization).</span></span>
    
2. <span data-ttu-id="a09e2-113">ディレクトリ同期が完了したら、組織の Windows 10 デバイスが Azure に参加ADします。</span><span class="sxs-lookup"><span data-stu-id="a09e2-113">After the directory synchronization is complete, make sure your organization's Windows 10 devices are Azure AD joined.</span></span> <span data-ttu-id="a09e2-114">この手順は、各 Windows 10 デバイスで個別に実行します。</span><span class="sxs-lookup"><span data-stu-id="a09e2-114">This step is done individually on each Windows 10 device.</span></span> <span data-ttu-id="a09e2-115">詳細 [については、「Microsoft 365 Business Premium](set-up-windows-devices.md) ユーザー向け Windows デバイスのセットアップ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a09e2-115">See [Set up Windows devices for Microsoft 365 Business Premium users](set-up-windows-devices.md) for details.</span></span> 
    
3. <span data-ttu-id="a09e2-116">Windows 10 デバイスが Azure ADに参加したら、各ユーザーはデバイスを再起動し、Microsoft 365 Business Premium の資格情報でサインインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a09e2-116">Once the Windows 10 devices are Azure AD joined, each user must reboot their devices and sign in with their Microsoft 365 Business Premium credentials.</span></span> <span data-ttu-id="a09e2-117">すべてのデバイスは、オンプレミスのリソースにもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a09e2-117">All devices now have access to on-premises resources as well.</span></span>
    
<span data-ttu-id="a09e2-118">Azure または参加しているデバイスのオンプレミス リソースにアクセスするために、追加AD必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a09e2-118">No additional steps are required to get access to on-premises resources for Azure AD joined devices.</span></span> <span data-ttu-id="a09e2-119">この機能は、Windows 10 に組み込組み込みです。</span><span class="sxs-lookup"><span data-stu-id="a09e2-119">This functionality is built into Windows 10.</span></span> 

<span data-ttu-id="a09e2-120">パスワード以外の AADJ デバイスへのログインを計画している場合は、WHFB 資格情報ログインを使用して PIN/生体測定法のようにして、オンプレミスのリソース (共有、プリンターなど) にアクセスします。など) に従います。 https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-hybrid-aadj-sso-base</span><span class="sxs-lookup"><span data-stu-id="a09e2-120">If you have plans to login to the AADJ device other than password method Like PIN/Bio-metric via WHFB credential login and then access on-premise resources (shares,printers..etc), please follow https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-hybrid-aadj-sso-base</span></span>
  
<span data-ttu-id="a09e2-121">上記の Azure AD 参加デバイス構成に展開する準備ができていない場合は、ハイブリッド Azure AD 参加デバイス構成の設定 [を検討してください](manage-windows-devices.md)。</span><span class="sxs-lookup"><span data-stu-id="a09e2-121">If your organization isn't ready to deploy in the Azure AD joined device configuration described above, consider setting up [Hybrid Azure AD Joined device configuration](manage-windows-devices.md).</span></span>
  
### <a name="considerations-when-you-join-windows-devices-to-azure-ad"></a><span data-ttu-id="a09e2-122">Windows デバイスを Azure デバイスに参加AD</span><span class="sxs-lookup"><span data-stu-id="a09e2-122">Considerations when you join Windows devices to Azure AD</span></span>

<span data-ttu-id="a09e2-123">Azure-ADに参加した Windows デバイスが以前にドメインに参加しているか、ワークグループに参加している場合は、次の制限事項を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="a09e2-123">If the Windows device that you Azure-AD joined was previously domain-joined or in a workgroup, consider the following limitations:</span></span>
  
- <span data-ttu-id="a09e2-124">デバイス Azure AD参加すると、既存のプロファイルを参照せずに新しいユーザーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a09e2-124">When a device Azure AD joins, it creates a new user without referencing an existing profile.</span></span> <span data-ttu-id="a09e2-125">プロファイルは手動で移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a09e2-125">Profiles must be manually migrated.</span></span> <span data-ttu-id="a09e2-126">ユーザー プロファイルには、お気に入り、ローカル ファイル、ブラウザーの設定、スタート メニューの設定など、情報が含まれている。</span><span class="sxs-lookup"><span data-stu-id="a09e2-126">A user profile contains information like favorites, local files, browser settings, and Start menu settings.</span></span> <span data-ttu-id="a09e2-127">最善の方法は、既存のファイルと設定を新しいプロファイルにマップするサード パーティ製ツールを見つけ出す方法です。</span><span class="sxs-lookup"><span data-stu-id="a09e2-127">A best approach is to find a third-party tool to map existing files and settings to the new profile.</span></span>

- <span data-ttu-id="a09e2-128">デバイスがグループ ポリシー オブジェクト (GPO) を使用している場合、一部の GPO では Intune で同等の [構成](https://docs.microsoft.com/windows/configuration/provisioning-packages/how-it-pros-can-use-configuration-service-providers) サービス プロバイダー (CSP) を使用できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="a09e2-128">If the device is using Group Policy Objects (GPO), some GPOs may not have a comparable [Configuration Service Provider](https://docs.microsoft.com/windows/configuration/provisioning-packages/how-it-pros-can-use-configuration-service-providers) (CSP) in Intune.</span></span> <span data-ttu-id="a09e2-129">[MMAT ツールを実行して、](https://www.microsoft.com/download/details.aspx?id=45520)既存の GPO に対応する CSP を検索します。</span><span class="sxs-lookup"><span data-stu-id="a09e2-129">Run the [MMAT tool](https://www.microsoft.com/download/details.aspx?id=45520) to find comparable CSPs for existing GPOs.</span></span>

- <span data-ttu-id="a09e2-130">ユーザーは、Active Directory 認証に依存するアプリケーションに対して認証できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="a09e2-130">Users might not be able to authenticate to applications that depend on Active Directory authentication.</span></span> <span data-ttu-id="a09e2-131">レガシ アプリを評価し、可能であれば最新の認証を使用するアプリへの更新を検討します。</span><span class="sxs-lookup"><span data-stu-id="a09e2-131">Evaluate the legacy app and consider updating to an app that uses modern Auth, if possible.</span></span>

- <span data-ttu-id="a09e2-132">Active Directory プリンターの検出が機能しません。</span><span class="sxs-lookup"><span data-stu-id="a09e2-132">Active Directory printer discovery won't work.</span></span> <span data-ttu-id="a09e2-133">すべてのユーザーにプリンターの直接パスを指定するか、ユニバーサル印刷 [を使用できます](https://aka.ms/UPDocs)。</span><span class="sxs-lookup"><span data-stu-id="a09e2-133">You can provide direct printer paths for all users or use [Universal Print](https://aka.ms/UPDocs).</span></span>
