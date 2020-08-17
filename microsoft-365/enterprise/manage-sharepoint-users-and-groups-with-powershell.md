---
title: PowerShell を使用して SharePoint Online のユーザーとグループを管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
- seo-marvel-apr2020
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: この記事では、Microsoft 365 の PowerShell を使用して SharePoint Online ユーザー、グループ、およびサイトを管理する方法について説明します。
ms.openlocfilehash: 5252ecc950e5f26d6ad60cd871910a67bf50f187
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46692077"
---
# <a name="manage-sharepoint-online-users-and-groups-with-powershell"></a><span data-ttu-id="f7e10-103">PowerShell を使用して SharePoint Online のユーザーとグループを管理する</span><span class="sxs-lookup"><span data-stu-id="f7e10-103">Manage SharePoint Online users and groups with PowerShell</span></span>

<span data-ttu-id="f7e10-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="f7e10-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="f7e10-105">ユーザーアカウントまたはグループの大規模なリストで作業を行う SharePoint Online 管理者は、Microsoft 365 の PowerShell を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f7e10-105">If you are a SharePoint Online administrator who works with large lists of user accounts or groups and wants an easier way to manage them, you can use PowerShell for Microsoft 365.</span></span> 

<span data-ttu-id="f7e10-106">開始する前に、このトピックの手順で SharePoint Online に接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7e10-106">Before you begin, the procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="f7e10-107">手順については、「 [SharePoint Online PowerShell への接続](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7e10-107">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="f7e10-108">サイト、グループ、ユーザーの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="f7e10-108">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="f7e10-p102">ユーザーとグループを管理する前に、サイト、グループ、ユーザーの一覧を取得する必要があります。この情報は、この記事の例全体を通して使用できます。</span><span class="sxs-lookup"><span data-stu-id="f7e10-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

<span data-ttu-id="f7e10-111">次のコマンドを使用して、テナント内のサイトの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-111">Get a list of the sites in your tenant with this command:</span></span>

```powershell
Get-SPOSite
```

<span data-ttu-id="f7e10-112">次のコマンドを使用して、テナント内のグループの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-112">Get a list of the groups in your tenant with this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

<span data-ttu-id="f7e10-113">次のコマンドを使用して、テナント内のユーザーの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-113">Get a list of the users in your tenant with this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="f7e10-114">サイト コレクション管理者グループにユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="f7e10-114">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="f7e10-115">コマンドレットを使用して、 `Set-SPOUser` サイトコレクションのサイトコレクション管理者のリストにユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-115">You use the `Set-SPOUser` cmdlet to add a user to the list of Site Collection Administrators on a site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="f7e10-116">これらのコマンドを使用するには、引用符で囲まれたすべての内容 (< と > の文字を含む) を正しい名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f7e10-116">To use these commands, replace everything within the quotes, including the < and > characters, with the correct names.</span></span>

<span data-ttu-id="f7e10-117">たとえば、次のコマンドを使用すると、Opal Castillo (user name opalc) が Contoso テナント内の ContosoTest サイトコレクションのサイトコレクション管理者の一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="f7e10-117">For example, this set of commands adds Opal Castillo (user name opalc) to the list of Site Collection Administrators on the ContosoTest site collection in the Contoso tenancy:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="f7e10-118">これらのコマンドをメモ帳にコピーして貼り付けることができます。 $tenant、$site、および $user の変数値を環境から実際の値に変更し、それを SharePoint Online 管理シェルウィンドウに貼り付けて実行します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-118">You can copy and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window to run them.</span></span>

## <a name="add-a-user-to-other-site-collection-groups"></a><span data-ttu-id="f7e10-119">他のサイトコレクショングループにユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="f7e10-119">Add a user to other site collection groups</span></span>

<span data-ttu-id="f7e10-120">この作業では、コマンドレットを使用して、 `Add-SPOUser` サイトコレクションの SharePoint グループにユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-120">In this task, we'll use the `Add-SPOUser` cmdlet to add a user to a SharePoint group on a site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="f7e10-121">たとえば、「Glen Rife (ユーザー名 glenr)」を「contoso テナント内の ContosoTest サイトコレクションの監査者グループに追加してみましょう。</span><span class="sxs-lookup"><span data-stu-id="f7e10-121">For example, let's add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso tenancy:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="f7e10-122">サイト コレクション グループを作成する</span><span class="sxs-lookup"><span data-stu-id="f7e10-122">Create a site collection group</span></span>

<span data-ttu-id="f7e10-123">`New-SPOSiteGroup`このコマンドレットを使用して、新しい SharePoint グループを作成し、それをサイトコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-123">You use the `New-SPOSiteGroup` cmdlet to create a new SharePoint group and add it to a site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
<span data-ttu-id="f7e10-124">アクセス許可レベルなどのグループのプロパティは、後でコマンドレットを使用して更新でき `Set-SPOSiteGroup` ます。</span><span class="sxs-lookup"><span data-stu-id="f7e10-124">Group properties, such as permission levels, can be updated later by using the `Set-SPOSiteGroup` cmdlet.</span></span>

<span data-ttu-id="f7e10-125">たとえば、contoso テナント内の contosotest サイトコレクションに対する表示のみのアクセス許可を持つ監査グループを追加してみましょう。</span><span class="sxs-lookup"><span data-stu-id="f7e10-125">For example, let's add the Auditors group with View Only permissions to the contosotest site collection in the contoso tenancy:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="f7e10-126">グループからユーザーを削除する</span><span class="sxs-lookup"><span data-stu-id="f7e10-126">Remove users from a group</span></span>

<span data-ttu-id="f7e10-p103">場合によっては、あるサイトまたはすべてのサイトからユーザーを削除する必要があります。たとえば、従業員がある部署から別の部署に異動した場合や、退職した場合などが該当します。対象の従業員が 1 人のみの場合は UI で簡単に削除できますが、部署全体をあるサイトから別のサイトに移動する場合は容易ではありません。</span><span class="sxs-lookup"><span data-stu-id="f7e10-p103">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="f7e10-130">ただし、SharePoint Online 管理シェルと CSV ファイルを使用することで、これは迅速かつ簡単になります。</span><span class="sxs-lookup"><span data-stu-id="f7e10-130">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy.</span></span> <span data-ttu-id="f7e10-131">このタスクでは、まず、Windows PowerShell を使用して、サイト コレクションのセキュリティ グループから 1 人のユーザーを削除します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-131">In this task, you'll use Windows PowerShell to remove a user from a site collection security group.</span></span> <span data-ttu-id="f7e10-132">次に、CSV ファイルを使用して、複数の異なるサイトから多数のユーザーを削除します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-132">Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="f7e10-133">コマンド構文を確認できるように、' Remove-SPOUser ' コマンドレットを使用して、1つの Microsoft 365 ユーザーをサイトコレクショングループから削除します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-133">We'll be using the 'Remove-SPOUser' cmdlet to remove a single Microsoft 365 user from a site collection group just so we can see the command syntax.</span></span> <span data-ttu-id="f7e10-134">以下に、構文の一例を示します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-134">Here is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
<span data-ttu-id="f7e10-135">たとえば、contoso テナントの contosotest サイトコレクションのサイトコレクション監査グループから、[村中 Overby を削除しましょう。</span><span class="sxs-lookup"><span data-stu-id="f7e10-135">For example, let's remove Bobby Overby from the site collection Auditors group in the contosotest site collection in the contoso tenancy:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="f7e10-136">ユーザーが現在所属しているすべてのグループから、村中を削除するとします。</span><span class="sxs-lookup"><span data-stu-id="f7e10-136">Suppose we wanted to remove Bobby from all the groups he is currently in.</span></span> <span data-ttu-id="f7e10-137">これを行う方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-137">Here is how we would do that:</span></span>

```powershell
$tenant = "contoso"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="f7e10-138">これは1つの例にすぎません。</span><span class="sxs-lookup"><span data-stu-id="f7e10-138">This is just an example.</span></span> <span data-ttu-id="f7e10-139">たとえば、ユーザーが退職した場合など、ユーザーをすべてのグループから実際に削除しなければならないのでない限り、このコマンドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f7e10-139">You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="f7e10-140">ユーザーおよびグループの大規模なリストの管理を自動化する</span><span class="sxs-lookup"><span data-stu-id="f7e10-140">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="f7e10-141">多数のアカウントを SharePoint サイトに追加してアクセス許可を付与するには、Microsoft 365 管理センター、個々の PowerShell コマンド、または PowerShell を CSV ファイルとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="f7e10-141">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Microsoft 365 admin center, individual PowerShell commands, or PowerShell an a CSV file.</span></span> <span data-ttu-id="f7e10-142">これらの選択肢の中では、CSV ファイルがこのタスクを自動化する最も簡単な方法になります。</span><span class="sxs-lookup"><span data-stu-id="f7e10-142">Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="f7e10-143">基本的なプロセスは、CSV を作成し、ヘッダー (列) を Windows PowerShell スクリプトに必要なパラメーターに対応させることです。</span><span class="sxs-lookup"><span data-stu-id="f7e10-143">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs.</span></span> <span data-ttu-id="f7e10-144">このようなリストは、Excel で簡単に作成して、それを CSV ファイルとしてエクスポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="f7e10-144">You can easily create such a list in Excel and then export it as a CSV file.</span></span> <span data-ttu-id="f7e10-145">次に、Windows PowerShell スクリプトを使用して、CSV ファイルのレコード (行) を反復処理し、ユーザーをグループに、グループをサイトに追加します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-145">Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="f7e10-146">たとえば、サイトコレクション、グループ、およびアクセス許可のグループを定義する CSV ファイルを作成してみましょう。</span><span class="sxs-lookup"><span data-stu-id="f7e10-146">For example, let's create a CSV file to define a group of site collections, groups, and permissions.</span></span> <span data-ttu-id="f7e10-147">次に、グループにユーザーを取り込むための CSV ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-147">Next, we will create a CSV file to populate the groups with users.</span></span> <span data-ttu-id="f7e10-148">最後に、グループを作成してユーザーを取り込む単純な Windows PowerShell スクリプトを作成して実行します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-148">Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="f7e10-149">最初の CSV ファイルは、1 つ以上のグループを 1 つ以上のサイト コレクションに追加します。このファイルの構造は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f7e10-149">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

<span data-ttu-id="f7e10-150">見出し</span><span class="sxs-lookup"><span data-stu-id="f7e10-150">Header:</span></span>

```powershell
Site,Group,PermissionLevels
```

<span data-ttu-id="f7e10-151">部分</span><span class="sxs-lookup"><span data-stu-id="f7e10-151">Item:</span></span>

```powershell
https://tenant.sharepoint.com/sites/site,group,level
```

<span data-ttu-id="f7e10-152">以下は、サンプル ファイルです。</span><span class="sxs-lookup"><span data-stu-id="f7e10-152">Here is an example file:</span></span>

```powershell
Site,Group,PermissionLevels
https://contoso.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

<span data-ttu-id="f7e10-153">2 番目の CSV ファイルは、1 つ以上のユーザーを 1 つ以上のグループに追加します。このファイルの構造は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f7e10-153">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

<span data-ttu-id="f7e10-154">見出し</span><span class="sxs-lookup"><span data-stu-id="f7e10-154">Header:</span></span>

```powershell
Group,LoginName,Site
```

<span data-ttu-id="f7e10-155">部分</span><span class="sxs-lookup"><span data-stu-id="f7e10-155">Item:</span></span>

```powershell
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="f7e10-156">以下は、サンプル ファイルです。</span><span class="sxs-lookup"><span data-stu-id="f7e10-156">Here is an example file:</span></span>

```powershell
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso.com,https://contoso.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso.com,https://contoso.sharepoint.com/sites/Project01
```

<span data-ttu-id="f7e10-157">次の手順では、2 つの CSV ファイルをドライブに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7e10-157">For the next step, you must have the two CSV files saved to your drive.</span></span> <span data-ttu-id="f7e10-158">次に、両方の CSV ファイルを使用してアクセス許可とグループメンバーシップを追加するコマンドの例を示します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-158">Here are example commands that use both CSV files and to add permissions and group membership:</span></span>

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="f7e10-159">このスクリプトは、CSV ファイルの内容をインポートし、列の値を使用して、 **remove-spositegroup** および **Add-spouser** コマンドのパラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-159">The script imports the CSV file contents and uses the values in the columns to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands.</span></span> <span data-ttu-id="f7e10-160">この例では、ドライブ C の theO365Admin フォルダーに保存していますが、任意の場所に保存できます。</span><span class="sxs-lookup"><span data-stu-id="f7e10-160">In our example, we are saving this to theO365Admin folder on drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="f7e10-161">次に、同じ CSV ファイルを使用して、複数のサイトにある複数のグループの一連のユーザーを削除してみましょう。</span><span class="sxs-lookup"><span data-stu-id="f7e10-161">Now, let's remove a bunch of people for several groups in different sites using the same CSV file.</span></span> <span data-ttu-id="f7e10-162">コマンド例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-162">Here is an example command:</span></span>

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="f7e10-163">ユーザー レポートを生成する</span><span class="sxs-lookup"><span data-stu-id="f7e10-163">Generate user reports</span></span>

<span data-ttu-id="f7e10-p114">いくつかのサイトに関する単純なレポートを取得して、該当するサイトのユーザーと各ユーザーのアクセス許可レベルやその他のプロパティを表示しなければならない場合があります。以下に、構文の一例を示します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-p114">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="f7e10-166">上記のコードは、3 つのサイトのデータを取得して、ローカル ドライブ上のテキスト ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="f7e10-166">This will grab the data for these three sites and write them to a text file on your local drive.</span></span> <span data-ttu-id="f7e10-167">パラメーター –Append は、既存のファイルに新しいコンテンツを追加することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f7e10-167">Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="f7e10-168">たとえば、Contoso1 テナントの ContosoTest サイト、TeamSite01 サイト、および Project01 サイトでレポートを実行します。</span><span class="sxs-lookup"><span data-stu-id="f7e10-168">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="f7e10-169">**$Site**変数のみを変更する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f7e10-169">Note that we had to change only the **$site** variable.</span></span> <span data-ttu-id="f7e10-170">**$Tenant**変数の値は、コマンドの3つの実行によって保持されます。</span><span class="sxs-lookup"><span data-stu-id="f7e10-170">The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="f7e10-p117">一方、この操作をすべてのサイトに対して行うとしたら、どうなるでしょうか。以下のコードを使用すれば、すべての Web サイトを入力することなく、このコマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f7e10-p117">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="f7e10-173">このレポートはかなり単純ですが、コードを追加すれば、より具体的なレポートや、その他の詳細情報が含まれるレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f7e10-173">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information.</span></span> <span data-ttu-id="f7e10-174">しかし、sharepoint online 管理シェルを使用して SharePoint Online 環境のユーザーを管理する方法についての理解が得られます。</span><span class="sxs-lookup"><span data-stu-id="f7e10-174">But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="f7e10-175">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7e10-175">See also</span></span>

[<span data-ttu-id="f7e10-176">SharePoint Online PowerShell に接続する</span><span class="sxs-lookup"><span data-stu-id="f7e10-176">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="f7e10-177">PowerShell を使用して SharePoint Online を管理する</span><span class="sxs-lookup"><span data-stu-id="f7e10-177">Manage SharePoint Online with PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="f7e10-178">PowerShell で Microsoft 365を管理する</span><span class="sxs-lookup"><span data-stu-id="f7e10-178">Manage Microsoft 365 with PowerShell</span></span>](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[<span data-ttu-id="f7e10-179">Microsoft 365 用 PowerShell の使用を開始する</span><span class="sxs-lookup"><span data-stu-id="f7e10-179">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-microsoft-365-powershell.md)