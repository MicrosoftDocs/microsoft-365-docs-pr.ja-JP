---
title: DAP Microsoft 365を使用してWindows PowerShellテナントを管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: この記事では、PowerShell を使用して顧客のテナンシー Microsoft 365管理する方法について説明します。
ms.openlocfilehash: 96c2c148b64d638ea977922f6a0ae3d5e23a8ace
ms.sourcegitcommit: 4886457c0d4248407bddec56425dba50bb60d9c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2021
ms.locfileid: "53289105"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="850fd-103">委任Microsoft 365アクセス許可 (DAP) パートナー Windows PowerShellを使用してテナントを管理する</span><span class="sxs-lookup"><span data-stu-id="850fd-103">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="850fd-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="850fd-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="850fd-105">Windows PowerShell、Syndication および クラウド ソリューション プロバイダー (CSP) パートナーは、顧客のテナント設定を管理し、レポートを簡単に行うことができます。この設定は、Microsoft 365 管理センター。</span><span class="sxs-lookup"><span data-stu-id="850fd-105">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="850fd-106">パートナー管理者アカウントが顧客テナンシーに接続するためには、「代理で管理」(AOBO) のアクセス許可が必要であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="850fd-106">Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>

<span data-ttu-id="850fd-107">委任アクセス許可 (DAP) パートナー とは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。</span><span class="sxs-lookup"><span data-stu-id="850fd-107">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="850fd-108">他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。</span><span class="sxs-lookup"><span data-stu-id="850fd-108">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="850fd-109">ユーザーは、Microsoft 365サービスサービスにサブスクリプションをバンドルします。</span><span class="sxs-lookup"><span data-stu-id="850fd-109">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="850fd-110">Microsoft 365 サブスクリプションを販売すると、顧客テナンシーに対する管理 (AOBO) アクセス許可が自動的に付与され、顧客テナンシーの管理と報告が可能になります。</span><span class="sxs-lookup"><span data-stu-id="850fd-110">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="850fd-111">始める前に把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="850fd-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="850fd-112">このトピックの手順では、PowerShell を使用してConnect[にMicrosoft 365する必要があります](connect-to-microsoft-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="850fd-112">The procedures in this topic require you to connect to [Connect to Microsoft 365 with PowerShell](connect-to-microsoft-365-powershell.md).</span></span>

<span data-ttu-id="850fd-113">また、パートナーのテナント管理者の資格情報も必要です。</span><span class="sxs-lookup"><span data-stu-id="850fd-113">You also need your partner tenant administrator credentials.</span></span>

## <a name="what-do-you-want-to-do"></a><span data-ttu-id="850fd-114">必要な作業</span><span class="sxs-lookup"><span data-stu-id="850fd-114">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="850fd-115">すべてのテナント ID を一覧表示する</span><span class="sxs-lookup"><span data-stu-id="850fd-115">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="850fd-p103">テナントが 500 を超える場合は、コマンドレット構文のスコープを  _-All_ または _-MaxResultsParameter_ に設定します。これは、 **Get-MsolUser** など、出力のサイズが大きいコマンドレットに適用されます。</span><span class="sxs-lookup"><span data-stu-id="850fd-p103">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>

<span data-ttu-id="850fd-118">アクセスできるすべての顧客テナント ID を一覧表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="850fd-118">To list all customer tenant Ids that you have access to, run this command.</span></span>

```powershell
Get-MsolPartnerContract -All | Select-Object TenantId
```

<span data-ttu-id="850fd-119">これにより、 **テナント ID** 順にすべての顧客テナントが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="850fd-119">This will display a listing of all your customer tenants by **TenantId**.</span></span>

>[!Note]
><span data-ttu-id="850fd-120">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="850fd-120">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="850fd-121">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="850fd-121">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="850fd-122">ドメイン名を使用してテナント ID を取得する</span><span class="sxs-lookup"><span data-stu-id="850fd-122">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="850fd-p105">ドメイン名によって特定の顧客テナントの **テナント ID** を取得するには、次のコマンドを実行します。 _<domainname.onmicrosoft.com>_ を、目的の顧客テナントの実際のドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="850fd-p105">To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>

```powershell
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="850fd-125">テナントのすべてのドメインを一覧表示する</span><span class="sxs-lookup"><span data-stu-id="850fd-125">List all domains for a tenant</span></span>

<span data-ttu-id="850fd-p106">任意の 1 つの顧客テナントの全ドメインを取得するには、次のコマンドを実行します。_<customer TenantId value>_ を実際の値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="850fd-p106">To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.</span></span>

```powershell
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="850fd-128">追加のドメインを登録した場合、顧客の **テナント ID** と関連付けられたすべてのドメインが返されます。</span><span class="sxs-lookup"><span data-stu-id="850fd-128">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>

### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="850fd-129">すべてのテナントと登録済みドメインのマッピングを取得する</span><span class="sxs-lookup"><span data-stu-id="850fd-129">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="850fd-130">Microsoft 365 コマンドの前の PowerShell では、テナント ID またはドメインを取得する方法が示されましたが、両方を同時に取得する方法は示していません。また、両者の間に明確なマッピングはありません。</span><span class="sxs-lookup"><span data-stu-id="850fd-130">The previous PowerShell for Microsoft 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all.</span></span> <span data-ttu-id="850fd-131">このコマンドは、すべての顧客テナント ID とそのドメインの一覧を生成します。</span><span class="sxs-lookup"><span data-stu-id="850fd-131">This command generates a listing of all your customer tenant IDs and their domains.</span></span>

```powershell
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="850fd-132">テナントの全ユーザーを取得する</span><span class="sxs-lookup"><span data-stu-id="850fd-132">Get all users for a tenant</span></span>

<span data-ttu-id="850fd-p108">これにより、特定のテナントの全ユーザーの **UserPrincipalName**、**DisplayName**、および **isLicensed** の状態が表示されます。_<customer TenantId value>_ を実際の値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="850fd-p108">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.</span></span>

```powershell
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="850fd-135">ユーザーに関するすべての詳細を取得する</span><span class="sxs-lookup"><span data-stu-id="850fd-135">Get all details about a user</span></span>

<span data-ttu-id="850fd-p109">特定のユーザーのすべてのプロパティを表示する場合は、次のコマンドを実行します。_<customer TenantId value>_ と _<user principal name value>_ を実際の値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="850fd-p109">If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span></span>

```powershell
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="850fd-138">ユーザーの追加、オプションの設定、およびライセンスの割り当てを行う</span><span class="sxs-lookup"><span data-stu-id="850fd-138">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="850fd-139">ユーザーの一括作成、構成、およびライセンスは、Microsoft 365に PowerShell を使用することで特にMicrosoft 365。</span><span class="sxs-lookup"><span data-stu-id="850fd-139">The bulk creation, configuration, and licensing of Microsoft 365 users is particularly efficient by using PowerShell for Microsoft 365.</span></span> <span data-ttu-id="850fd-140">この 2 段階のプロセスでは、最初にコンマ区切り値 (CSV) ファイルに追加するすべてのユーザーのエントリを作成し、次に powerShell for Microsoft 365 を使用してそのファイルをインポートします。</span><span class="sxs-lookup"><span data-stu-id="850fd-140">In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using PowerShell for Microsoft 365.</span></span>

#### <a name="create-a-csv-file"></a><span data-ttu-id="850fd-141">CSV ファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="850fd-141">Create a CSV file</span></span>

<span data-ttu-id="850fd-142">次の形式を使用して、CSV ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="850fd-142">Create a CSV file by using this format:</span></span>

`UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`

<span data-ttu-id="850fd-143">各部分の意味は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="850fd-143">where:</span></span>

- <span data-ttu-id="850fd-p111">**UsageLocation**: この値は、ユーザーの 2 文字の ISO の国や地域コードです。国や地域コードは、[ISO オンライン参照プラットフォーム](https://go.microsoft.com/fwlink/p/?LinkId=532703)で調べることができます。たとえば、米国のコードは US、ブラジルのコードは BR です。</span><span class="sxs-lookup"><span data-stu-id="850fd-p111">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR.</span></span>

- <span data-ttu-id="850fd-p112">**LicenseAssignment**:この値には、次の形式を使用します。 `syndication-account:<PROVISIONING_ID>`。たとえば、顧客テナントのユーザーに O365_Business_Premium ライセンスを割り当てている場合、 **LicenseAssignment** の値は **syndication-account:O365_Business_Premium** のようになります。PROVISIONING_ID は、シンジケートまたは CSP パートナーとしてアクセスできるシンジケート パートナー ポータルで確認できます。</span><span class="sxs-lookup"><span data-stu-id="850fd-p112">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>

#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="850fd-150">CSV ファイルをインポートしてユーザーを作成する</span><span class="sxs-lookup"><span data-stu-id="850fd-150">Import the CSV file and create the users</span></span>

<span data-ttu-id="850fd-p113">CSV ファイルを作成したら、次のコマンドを実行して、無期限のパスワード付きユーザー アカウントを作成します。このパスワードは、ユーザーが初回サインイン時に変更する必要があり、指定したライセンスを割り当てる必要があります。必ず、正しい CSV ファイル名に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="850fd-p113">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.</span></span>

```powershell
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="850fd-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="850fd-153">See also</span></span>

[<span data-ttu-id="850fd-154">パートナーのヘルプ</span><span class="sxs-lookup"><span data-stu-id="850fd-154">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)
