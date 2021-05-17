---
title: PowerShell Microsoft 365ユーザー アカウントを表示する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: PowerShell を使用して、さまざまな方法でユーザー アカウントMicrosoft 365表示、一覧表示、または表示する方法について説明します。
ms.openlocfilehash: de91195afeb8480bf231d9536e4b3a94502a6da1
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "50924650"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="3493e-103">PowerShell Microsoft 365ユーザー アカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="3493e-103">View Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="3493e-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="3493e-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="3493e-105">管理センターの Microsoft 365を使用して、テナントのアカウントMicrosoft 365できます。</span><span class="sxs-lookup"><span data-stu-id="3493e-105">You can use the Microsoft 365 admin center to view the accounts for your Microsoft 365 tenant.</span></span> <span data-ttu-id="3493e-106">PowerShell for Microsoft 365これを有効にし、追加の機能も提供します。</span><span class="sxs-lookup"><span data-stu-id="3493e-106">PowerShell for Microsoft 365 enables this but also provides additional functionality.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="3493e-107">Graph 用 Azure Active Directory PowerShell モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="3493e-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="3493e-108">最初に[、テナントにMicrosoft 365します](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="3493e-108">First, [connect to your Microsoft 365 tenant](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="3493e-109">すべてのアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="3493e-109">View all accounts</span></span>

<span data-ttu-id="3493e-110">ユーザー アカウントの完全な一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3493e-110">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-AzureADUser
```

<span data-ttu-id="3493e-111">次のような情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3493e-111">You should get information similar to this:</span></span>
  
```powershell
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a><span data-ttu-id="3493e-112">特定のアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="3493e-112">View a specific account</span></span>

<span data-ttu-id="3493e-113">特定のユーザー アカウントを表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3493e-113">To display a specific user account, run the following command.</span></span> <span data-ttu-id="3493e-114">ユーザー アカウントのサインイン アカウント名 (ユーザー プリンシパル名 (UPN) とも呼ばれる) を入力します。</span><span class="sxs-lookup"><span data-stu-id="3493e-114">Fill in the sign-in account name of the user account, which is also known as the user principal name (UPN).</span></span> <span data-ttu-id="3493e-115">"<" 文字と ">" 文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="3493e-115">Remove the "<" and ">" characters.</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="3493e-116">次に例を示します:</span><span class="sxs-lookup"><span data-stu-id="3493e-116">Here's an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="3493e-117">特定のアカウントの追加のプロパティ値を表示する</span><span class="sxs-lookup"><span data-stu-id="3493e-117">View additional property values for a specific account</span></span>

<span data-ttu-id="3493e-118">**既定では、Get-AzureADUser コマンドレット** は、アカウントの *ObjectID、DisplayName、* および *UserPrincipalName* プロパティのみを表示します。 </span><span class="sxs-lookup"><span data-stu-id="3493e-118">By default, the **Get-AzureADUser** cmdlet only displays the *ObjectID*, *DisplayName*, and *UserPrincipalName* properties of accounts.</span></span>

<span data-ttu-id="3493e-119">表示するプロパティの詳細を選択するには **、Select** コマンドレットを **Get-AzureADUser** コマンドレットと組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="3493e-119">To be more selective about the properties to display, use the **Select** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="3493e-120">2 つのコマンドレットを組み合わせるには、"パイプ" 文字 ("|") を使用して、Azure Active Directory PowerShell に Graph のコマンドの結果を取得し、次のコマンドに送信します。</span><span class="sxs-lookup"><span data-stu-id="3493e-120">To combine the two cmdlets, use the "pipe" character ("|"), which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="3493e-121">すべてのユーザー アカウントの DisplayName、Department、UsageLocation を表示する *コマンド* の例を次に示します。  </span><span class="sxs-lookup"><span data-stu-id="3493e-121">Here's an example command that displays the *DisplayName*, *Department*, and *UsageLocation* for every user account:</span></span>
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

<span data-ttu-id="3493e-122">このコマンドは、PowerShell に次の指示を行います。</span><span class="sxs-lookup"><span data-stu-id="3493e-122">This command instructs PowerShell to:</span></span>
  
1. <span data-ttu-id="3493e-123">ユーザー アカウント **(Get-AzureADUser)** のすべての情報を取得し、次のコマンド ( ) に送信します **|** 。</span><span class="sxs-lookup"><span data-stu-id="3493e-123">Get all the information on the user accounts (**Get-AzureADUser**) and send it to the next command (**|**).</span></span>
    
1.  <span data-ttu-id="3493e-124">ユーザー アカウント名、部署、使用状況の場所のみを表示します **([DisplayName、 Department, UsageLocation] の選択**)。</span><span class="sxs-lookup"><span data-stu-id="3493e-124">Display only the user account name, department, and usage location (**Select DisplayName, Department, UsageLocation**).</span></span>
  
<span data-ttu-id="3493e-125">特定のユーザー アカウントのすべてのプロパティを表示するには **、Select** コマンドレットとワイルドカード文字 (\*)を使用します。</span><span class="sxs-lookup"><span data-stu-id="3493e-125">To see all the properties for a specific user account, use the **Select** cmdlet and the wildcard character (\*).</span></span> <span data-ttu-id="3493e-126">次に例を示します:</span><span class="sxs-lookup"><span data-stu-id="3493e-126">Here's an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="3493e-127">別の例として、次のコマンドを実行して、特定のユーザー アカウントの有効な状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="3493e-127">As another example, run the following command to check the enabled status of a specific user account:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-account-synchronization-status"></a><span data-ttu-id="3493e-128">アカウントの同期状態の表示</span><span class="sxs-lookup"><span data-stu-id="3493e-128">View account synchronization status</span></span>

<span data-ttu-id="3493e-129">ユーザー アカウントには、次の 2 つのソースがあります。</span><span class="sxs-lookup"><span data-stu-id="3493e-129">User accounts have two sources:</span></span> 

- <span data-ttu-id="3493e-130">Windowsサーバー Active Directory (AD) は、オンプレミスのサーバーからクラウドAD同期するアカウントです。</span><span class="sxs-lookup"><span data-stu-id="3493e-130">Windows Server Active Directory (AD), which are accounts that sync from on-premises AD to the cloud.</span></span>

- <span data-ttu-id="3493e-131">Azure Active Directory (Azure AD) AD、クラウドに直接作成されるアカウントです。</span><span class="sxs-lookup"><span data-stu-id="3493e-131">Azure Active Directory (Azure AD) AD accounts, which are created directly in the cloud.</span></span>


<span data-ttu-id="3493e-132">次のコマンドは、属性 *DirSyncEnabled* を True に設定しているすべてのユーザーを取得するように PowerShell に指示 *します*。</span><span class="sxs-lookup"><span data-stu-id="3493e-132">The following command instructs PowerShell to get all users who have the attribute *DirSyncEnabled* set to *True*.</span></span> <span data-ttu-id="3493e-133">この機能を使用して、オンプレミスのアカウントから同期しているアカウントをAD。</span><span class="sxs-lookup"><span data-stu-id="3493e-133">You can use it to find accounts that are synchronizing from on-premise AD.</span></span>

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -eq $true}
```

<span data-ttu-id="3493e-134">次のコマンドは、属性 *DirSyncEnabled* を False に設定しているすべてのユーザーを取得するように PowerShell に指示 *します*。</span><span class="sxs-lookup"><span data-stu-id="3493e-134">The following command instructs PowerShell to get all users who have the attribute *DirSyncEnabled* set to *False*.</span></span> <span data-ttu-id="3493e-135">クラウド専用アカウントの検索に使用できます。</span><span class="sxs-lookup"><span data-stu-id="3493e-135">You can use it to find cloud-only accounts.</span></span>

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -ne $false}
```

### <a name="view-accounts-based-on-a-common-property"></a><span data-ttu-id="3493e-136">共通プロパティに基づいてアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="3493e-136">View accounts based on a common property</span></span>

<span data-ttu-id="3493e-137">表示するアカウントの一覧を選択するには **、Get-AzureADUser** コマンドレットと組み合わせて Where コマンドレットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3493e-137">To be more selective about the list of accounts to display, you can use the **Where** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="3493e-138">2 つのコマンドレットを組み合わせるには、"パイプ" 文字 ("|") を使用して、Azure Active Directory PowerShell に Graph のコマンドの結果を取得し、次のコマンドに送信します。</span><span class="sxs-lookup"><span data-stu-id="3493e-138">To combine the two cmdlets, use the "pipe" character ("|"), which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="3493e-139">使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3493e-139">Here's an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="3493e-140">このコマンドは、次Azure Active Directory PowerShell にGraph指示します。</span><span class="sxs-lookup"><span data-stu-id="3493e-140">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
1. <span data-ttu-id="3493e-141">ユーザー アカウント **(Get-AzureADUser)** のすべての情報を取得し、次のコマンド ( ) に送信します **|** 。</span><span class="sxs-lookup"><span data-stu-id="3493e-141">Get all the information on the user accounts (**Get-AzureADUser**) and send it to the next command (**|**).</span></span>
    
1. <span data-ttu-id="3493e-142">使用場所が指定されていないすべてのユーザー アカウントを検索します **(Where {$ \_ .UsageLocation -eq $Null}**)。</span><span class="sxs-lookup"><span data-stu-id="3493e-142">Find all the user accounts that have an unspecified usage location (**Where {$\_.UsageLocation -eq $Null}**).</span></span> <span data-ttu-id="3493e-143">中かっこ内で、このコマンドは、UsageLocation ユーザー アカウント プロパティ (**$ \_ .UsageLocation**) は指定されていません (**-eq $Null)。**</span><span class="sxs-lookup"><span data-stu-id="3493e-143">Inside the braces, the command instructs PowerShell to only find the set of accounts for which the UsageLocation user account property (**$\_.UsageLocation**) is not specified (**-eq $Null**).</span></span>
    
<span data-ttu-id="3493e-144">**UsageLocation プロパティ** は、ユーザー アカウントに関連付けられている多数のプロパティの 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="3493e-144">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="3493e-145">特定のユーザー アカウントのすべてのプロパティを表示するには **、Select** コマンドレットとワイルドカード文字 (\*)を使用します。</span><span class="sxs-lookup"><span data-stu-id="3493e-145">To display all the properties for a specific user account, use the **Select** cmdlet and the wildcard character (\*).</span></span> <span data-ttu-id="3493e-146">次に例を示します:</span><span class="sxs-lookup"><span data-stu-id="3493e-146">Here's an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="3493e-147">たとえば **、City は** ユーザー アカウント プロパティの名前です。</span><span class="sxs-lookup"><span data-stu-id="3493e-147">For example, **City** is the name of a user account property.</span></span> <span data-ttu-id="3493e-148">次のコマンドを使用して、ロンドンに住むユーザーのすべてのアカウントを一覧表示できます。</span><span class="sxs-lookup"><span data-stu-id="3493e-148">You can use the following command to list all accounts of users who live in London:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="3493e-149">これらの例の **Where コマンドレット** の構文は **、Where {$ です \_ 。**</span><span class="sxs-lookup"><span data-stu-id="3493e-149">The syntax for the **Where** cmdlet in these examples is **Where {$\_.**</span></span> <span data-ttu-id="3493e-150">[ユーザー アカウントのプロパティ名][比較演算子][value] **}**.> [比較演算子] は、等号の場合は **-eq、** 等しくない場合は **-ne、** より小さい場合は **-lt、** より大きい場合は **-gt、** その他は -gt です。</span><span class="sxs-lookup"><span data-stu-id="3493e-150">[user account property name] [comparison operator] [value] **}**.> [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="3493e-151">[value] は通常、文字列 (一連の文字、数字、その他の文字)、数値、または指定されていない$Null指定します。</span><span class="sxs-lookup"><span data-stu-id="3493e-151">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="3493e-152">詳細については [、「Where」 を参照してください](/powershell/module/microsoft.powershell.core/where-object?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="3493e-152">For more information, see [Where](/powershell/module/microsoft.powershell.core/where-object?view=powershell-7).</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="3493e-153">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="3493e-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="3493e-154">最初に[、テナントにMicrosoft 365します](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="3493e-154">First, [connect to your Microsoft 365 tenant](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="3493e-155">すべてのアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="3493e-155">View all accounts</span></span>

<span data-ttu-id="3493e-156">ユーザー アカウントの完全な一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3493e-156">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-MsolUser
```

>[!Note]
><span data-ttu-id="3493e-157">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に *Msol* が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="3493e-157">PowerShell Core doesn't support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with *Msol* in their name.</span></span> <span data-ttu-id="3493e-158">これらのコマンドレットは、Windows PowerShell から実行します。</span><span class="sxs-lookup"><span data-stu-id="3493e-158">Run these cmdlets from Windows PowerShell.</span></span>
>

<span data-ttu-id="3493e-159">次のような情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3493e-159">You should get information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="3493e-160">**Get-MsolUser** コマンドレットには、表示するユーザー アカウントのセットをフィルターにかけるための一連のパラメーターもあります。</span><span class="sxs-lookup"><span data-stu-id="3493e-160">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="3493e-161">たとえば、ライセンスのないユーザーの一覧 (Microsoft 365 に追加されたが、まだサービスを使用するライセンスが与えされていないユーザー) の場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3493e-161">For example, for the list of unlicensed users (users who have been added to Microsoft 365 but haven't yet been licensed to use any of the services), run this command:</span></span>
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="3493e-162">次のような情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3493e-162">You should get information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="3493e-163">表示されるユーザー アカウントのセットをフィルター処理する追加のパラメーターの詳細については [、「Get-MsolUser」を参照してください](/previous-versions/azure/dn194133(v=azure.100))。</span><span class="sxs-lookup"><span data-stu-id="3493e-163">For information about additional parameters to filter the set of user accounts that are displayed, see [Get-MsolUser](/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  
### <a name="view-a-specific-account"></a><span data-ttu-id="3493e-164">特定のアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="3493e-164">View a specific account</span></span>

<span data-ttu-id="3493e-165">特定のユーザー アカウントを表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3493e-165">To display a specific user account, run the following command.</span></span> <span data-ttu-id="3493e-166">ユーザー アカウントのサインイン名 (ユーザー プリンシパル名 (UPN) とも呼ばれる) を入力します。</span><span class="sxs-lookup"><span data-stu-id="3493e-166">Fill in the sign-in name of the user account, which is also known as the user principal name (UPN).</span></span> <span data-ttu-id="3493e-167">"<" 文字と ">" 文字を削除します。</span><span class="sxs-lookup"><span data-stu-id="3493e-167">Remove the "<" and ">" characters.</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-accounts-based-on-a-common-property"></a><span data-ttu-id="3493e-168">共通プロパティに基づいてアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="3493e-168">View accounts based on a common property</span></span>

<span data-ttu-id="3493e-169">表示するアカウントの一覧を選択するには **、Get-MsolUser** コマンドレットと組み合わせて **Where** コマンドレットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3493e-169">To be more selective about the list of accounts to display, you can use the **Where** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="3493e-170">2 つのコマンドレットを組み合わせるには、"pipe" 文字 ("|") を使用して、PowerShell に 1 つのコマンドの結果を取得し、次のコマンドに送信します。</span><span class="sxs-lookup"><span data-stu-id="3493e-170">To combine the two cmdlets, use the "pipe" character ("|"), which tells PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="3493e-171">使用場所が指定されていないユーザー アカウントのみを表示する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3493e-171">Here's an example that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="3493e-172">このコマンドは、PowerShell に次の指示を行います。</span><span class="sxs-lookup"><span data-stu-id="3493e-172">This command instructs PowerShell to:</span></span>
  
1. <span data-ttu-id="3493e-173">ユーザー アカウント **(Get-MsolUser)** のすべての情報を取得し、次のコマンド ( ) に送信します **|** 。</span><span class="sxs-lookup"><span data-stu-id="3493e-173">Get all the information on the user accounts (**Get-MsolUser**) and send it to the next command (**|**).</span></span>
    
1. <span data-ttu-id="3493e-174">使用場所が指定されていないすべてのユーザー アカウントを検索します **(Where {$ \_ .UsageLocation -eq $Null}**)。</span><span class="sxs-lookup"><span data-stu-id="3493e-174">Find all user accounts that have an unspecified usage location (**Where {$\_.UsageLocation -eq $Null}**).</span></span> <span data-ttu-id="3493e-175">中かっこ内で、このコマンドは、UsageLocation ユーザー アカウント プロパティ (**$ \_ .UsageLocation**) は指定されていません (**-eq $Null)。**</span><span class="sxs-lookup"><span data-stu-id="3493e-175">Inside the braces, the command instructs PowerShell to find only the set of accounts for which the UsageLocation user account property (**$\_.UsageLocation**) is not specified (**-eq $Null**).</span></span>
    
<span data-ttu-id="3493e-176">次のような情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3493e-176">You should get information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="3493e-177">*UsageLocation プロパティ* は、ユーザー アカウントに関連付けられている多数のプロパティの 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="3493e-177">The *UsageLocation* property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="3493e-178">ユーザー アカウントのすべてのプロパティを表示するには **、Select** コマンドレットとワイルドカード文字 (\*) を使用して、それらをすべて特定のユーザー アカウントに表示します。</span><span class="sxs-lookup"><span data-stu-id="3493e-178">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="3493e-179">次に例を示します:</span><span class="sxs-lookup"><span data-stu-id="3493e-179">Here's an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="3493e-180">たとえば *、City は* ユーザー アカウント プロパティの名前です。</span><span class="sxs-lookup"><span data-stu-id="3493e-180">For example, *City* is the name of a user account property.</span></span> <span data-ttu-id="3493e-181">次のコマンドを使用して、ロンドンに住むユーザーのすべてのユーザー アカウントを一覧表示できます。</span><span class="sxs-lookup"><span data-stu-id="3493e-181">You can use the following command to list all of the user accounts for users who live in London:</span></span>
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="3493e-182">これらの例の **Where コマンドレット** の構文は **、Where {$ です \_ 。**</span><span class="sxs-lookup"><span data-stu-id="3493e-182">The syntax for the **Where** cmdlet in these examples is **Where {$\_.**</span></span> <span data-ttu-id="3493e-183">[ユーザー アカウントのプロパティ名][比較演算子][value] **}**.</span><span class="sxs-lookup"><span data-stu-id="3493e-183">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="3493e-184">[比較演算子] は、等しい場合は **-eq、** 等しくない場合は **-ne、** より小さい場合は **-lt、** より大きい場合は **-gt、** その他は -gt です。</span><span class="sxs-lookup"><span data-stu-id="3493e-184">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="3493e-185">[value] は通常、文字列 (一連の文字、数字、その他の文字)、数値、または指定されていない$Null指定します。</span><span class="sxs-lookup"><span data-stu-id="3493e-185">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="3493e-186">詳細については [、「Where」 を参照してください](/powershell/module/microsoft.powershell.core/where-object?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="3493e-186">For more information, see [Where](/powershell/module/microsoft.powershell.core/where-object?view=powershell-7).</span></span>
  
<span data-ttu-id="3493e-187">ユーザー アカウントのブロックされた状態を確認するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="3493e-187">To check the blocked status of a user account, use the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="3493e-188">アカウントの追加のプロパティ値を表示する</span><span class="sxs-lookup"><span data-stu-id="3493e-188">View additional property values for accounts</span></span>

<span data-ttu-id="3493e-189">既定では **、Get-MsolUser コマンドレットは** 、ユーザー アカウントの次の 3 つのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="3493e-189">By default, the **Get-MsolUser** cmdlet displays these three properties of user accounts:</span></span>
  
- <span data-ttu-id="3493e-190">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="3493e-190">UserPrincipalName</span></span>
    
- <span data-ttu-id="3493e-191">DisplayName</span><span class="sxs-lookup"><span data-stu-id="3493e-191">DisplayName</span></span>
    
- <span data-ttu-id="3493e-192">isLicensed</span><span class="sxs-lookup"><span data-stu-id="3493e-192">isLicensed</span></span>
    
<span data-ttu-id="3493e-193">ユーザーが働く部署、Microsoft 365 サービスを使用する国/地域などの追加のプロパティが必要な場合は **、Get-MsolUser** を Select コマンドレットと組み合わせて実行して、ユーザー アカウントのプロパティの一覧を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3493e-193">If you need additional properties, such as the department where the user works and the country/region where they use Microsoft 365 services, you can run **Get-MsolUser** in combination with the **Select** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="3493e-194">次に例を示します:</span><span class="sxs-lookup"><span data-stu-id="3493e-194">Here's an example:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

<span data-ttu-id="3493e-195">このコマンドは、PowerShell に次の指示を行います。</span><span class="sxs-lookup"><span data-stu-id="3493e-195">This command instructs PowerShell to:</span></span>
  
1. <span data-ttu-id="3493e-196">ユーザー アカウント **(Get-MsolUser)** に関する情報を取得し、次のコマンド ( ) に送信します **|** 。</span><span class="sxs-lookup"><span data-stu-id="3493e-196">Get all the information about the user accounts (**Get-MsolUser**) and send it to the next command (**|**).</span></span>
    
1. <span data-ttu-id="3493e-197">ユーザー アカウント名、部署、使用状況の場所のみを表示します **([DisplayName、 Department, UsageLocation] の選択**)。</span><span class="sxs-lookup"><span data-stu-id="3493e-197">Display only the user account name, department, and usage location (**Select DisplayName, Department, UsageLocation**).</span></span>
    
<span data-ttu-id="3493e-198">次のような情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3493e-198">You should get information similar to this:</span></span>
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="3493e-199">Select **コマンドレットでは** 、表示するプロパティを選択できます。</span><span class="sxs-lookup"><span data-stu-id="3493e-199">The **Select** cmdlet lets you choose what properties to display.</span></span> <span data-ttu-id="3493e-200">特定のユーザー アカウントのすべてのプロパティを表示するには、ワイルドカード文字 (\*)を使用します。</span><span class="sxs-lookup"><span data-stu-id="3493e-200">To display all the properties for a specific user account, use the wildcard character (\*).</span></span> <span data-ttu-id="3493e-201">次に例を示します:</span><span class="sxs-lookup"><span data-stu-id="3493e-201">Here's an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="3493e-202">表示するアカウントの一覧の詳細を選択するには **、Where** コマンドレットを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="3493e-202">To be more selective about the list of accounts to display, you can also use the **Where** cmdlet.</span></span> <span data-ttu-id="3493e-203">使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3493e-203">Here's an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

<span data-ttu-id="3493e-204">このコマンドは、PowerShell に次の指示を行います。</span><span class="sxs-lookup"><span data-stu-id="3493e-204">This command instructs PowerShell to:</span></span>
  
1. <span data-ttu-id="3493e-205">ユーザー アカウント **(Get-MsolUser)** に関する情報を取得し、次のコマンド ( ) に送信します **|** 。</span><span class="sxs-lookup"><span data-stu-id="3493e-205">Get all the information about the user accounts (**Get-MsolUser**) and send it to the next command (**|**).</span></span>
    
1. <span data-ttu-id="3493e-206">使用場所が指定されていないすべてのユーザー アカウントを検索します **(Where {$ \_ .UsageLocation -eq $Null} )** をクリックし、結果の情報を次のコマンド ( ) に送信します **|** 。</span><span class="sxs-lookup"><span data-stu-id="3493e-206">Find all user accounts that have an unspecified usage location (**Where {$\_.UsageLocation -eq $Null}**), and send the resulting information to the next command (**|**).</span></span> <span data-ttu-id="3493e-207">中かっこ内で、このコマンドは、UsageLocation ユーザー アカウント プロパティ (**$ \_ .UsageLocation**) は指定されていません (**-eq $Null)。**</span><span class="sxs-lookup"><span data-stu-id="3493e-207">Inside the braces, the command instructs PowerShell to only find the set of accounts for which the UsageLocation user account property (**$\_.UsageLocation**) is not specified (**-eq $Null**).</span></span>
    
1. <span data-ttu-id="3493e-208">ユーザー アカウント名、部署、使用状況の場所のみを表示します **([DisplayName、 Department, UsageLocation] の選択**)。</span><span class="sxs-lookup"><span data-stu-id="3493e-208">Display only the user account name, department, and usage location (**Select DisplayName, Department, UsageLocation**).</span></span>
    
<span data-ttu-id="3493e-209">次のような情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3493e-209">You should get information similar to this:</span></span>
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="3493e-210">ディレクトリ同期を使用して、Microsoft 365 ユーザーを作成および管理する場合は、Microsoft 365 ユーザーが投影されたローカル アカウントを表示できます。</span><span class="sxs-lookup"><span data-stu-id="3493e-210">If you're using directory synchronization to create and manage your Microsoft 365 users, you can display the local account from which a Microsoft 365 user has been projected.</span></span> <span data-ttu-id="3493e-211">次の例では、以下を前提とします。</span><span class="sxs-lookup"><span data-stu-id="3493e-211">The following example assumes that:</span></span>

- <span data-ttu-id="3493e-212">Azure AD Connect ObjectGUID の既定のソース アンカーを使用するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="3493e-212">Azure AD Connect is configured to use the default source anchor of ObjectGUID.</span></span> <span data-ttu-id="3493e-213">(ソース アンカーの構成の詳細については[、「Azure AD Connect: デザインの概念」を参照してください](/azure/active-directory/hybrid/plan-connect-design-concepts)。</span><span class="sxs-lookup"><span data-stu-id="3493e-213">(For more information about configuring a source anchor, see [Azure AD Connect: Design concepts](/azure/active-directory/hybrid/plan-connect-design-concepts)).</span></span>
- <span data-ttu-id="3493e-214">PowerShell 用の Active Directory ドメイン サービス モジュールがインストールされています [(「RSAT ツール」を参照](https://www.microsoft.com/en-gb/download/details.aspx?id=45520))。</span><span class="sxs-lookup"><span data-stu-id="3493e-214">The Active Directory Domain Services module for PowerShell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)).</span></span>

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a><span data-ttu-id="3493e-215">関連項目</span><span class="sxs-lookup"><span data-stu-id="3493e-215">See also</span></span>

[<span data-ttu-id="3493e-216">Microsoft 365 ユーザー アカウント、ライセンス、PowerShell を使用したグループを管理する</span><span class="sxs-lookup"><span data-stu-id="3493e-216">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[<span data-ttu-id="3493e-217">PowerShell で Microsoft 365を管理する</span><span class="sxs-lookup"><span data-stu-id="3493e-217">Manage Microsoft 365 with PowerShell</span></span>](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[<span data-ttu-id="3493e-218">Microsoft 365 用 PowerShell の使用を開始する</span><span class="sxs-lookup"><span data-stu-id="3493e-218">Get started with PowerShell for Microsoft 365</span></span>](getting-started-with-microsoft-365-powershell.md)