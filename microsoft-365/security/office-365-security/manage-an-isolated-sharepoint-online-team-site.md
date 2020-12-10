---
title: 分離した SharePoint Online チーム サイトの管理
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 79a61003-4905-4ba8-9e8a-16def7add37c
description: 分離した SharePoint Online チームサイトを管理し、新しいユーザーとグループを追加し、ユーザーとグループを削除し、カスタムアクセス許可を持つドキュメントサブフォルダーを作成します。
ms.openlocfilehash: 1e244738071b434efd09e8fd700462bbef7e116a
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "49616766"
---
# <a name="manage-an-isolated-sharepoint-online-team-site"></a>分離した SharePoint Online チーム サイトの管理

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


 **概要:** 以下の手順を使用して、分離した SharePoint Online チーム サイトを管理します。

この記事では、分離した SharePoint Online チーム サイトの一般的な管理操作について説明します。

## <a name="add-a-new-user"></a>新しいユーザーを追加する

他のユーザーが新しいサイトに参加する場合は、サイトでの参加レベルを決定する必要があります。

- 管理:サイト管理者のアクセス グループに新しいユーザー アカウントを追加する

- アクティブ コラボレーション:サイト メンバーのアクセス グループにユーザー アカウントを追加する

- 表示:サイト ビューアーのアクセス グループにユーザー アカウントを追加する

Active Directory ドメインサービス (AD DS) を使用してユーザーアカウントとグループを管理している場合は、通常の AD DS のユーザーおよびグループ管理手順を使用して適切なアクセスグループに適切なユーザーを追加し、サブスクリプションとの同期を待機します。

Microsoft 365 を介してユーザーアカウントとグループを管理している場合は、Microsoft 365 管理センターまたは Microsoft PowerShell を使用できます。

- Microsoft 365 管理センターの場合は、ユーザーアカウント管理者または会社の管理者の役割が割り当てられているユーザーアカウントでサインインし、グループを使用して適切なアクセスグループに適切なユーザーを追加します。

- PowerShell の場合、まず、 [Azure Active Directory PowerShell For Graph モジュールに接続](https://docs.microsoft.com/microsoft-365/enterprise/connect-to-microsoft-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module)します。 ユーザー プリンシパル名 (UPN) を使ってユーザー アカウントをアクセス グループに追加するには、次の PowerShell コマンド ブロックを使用します。

```powershell
$userUPN="<UPN of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

表示名を使ってユーザー アカウントをアクセス グループに追加するには、次の PowerShell コマンド ブロックを使用します。

```powershell
$userDisplayName="<display name of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="add-a-new-group"></a>新しいグループを追加する

グループ全体にアクセスを追加するには、サイト内のグループのすべてのメンバーへの参加レベルを決定する必要があります。

- 管理:サイト管理者のアクセス グループにグループを追加する

- アクティブ コラボレーション:サイト メンバーのアクセス グループにグループを追加する

- 表示:サイト ビューアーのアクセス グループにグループを追加する

AD DS を介してユーザーアカウントとグループを管理している場合は、通常の AD DS のユーザーおよびグループ管理手順を使用して適切なグループに適切なグループを追加し、サブスクリプションとの同期を待機します。

Office 365 を介してユーザーアカウントとグループを管理している場合は、Microsoft 365 管理センターまたは PowerShell を使用できます。

- Microsoft 365 管理センターの場合は、ユーザーアカウント管理者または会社の管理者の役割が割り当てられているユーザーアカウントでサインインし、グループを使用して適切なアクセスグループに適切なグループを追加します。

- PowerShell の場合、まず、 [Azure Active Directory PowerShell For Graph モジュールに接続](https://docs.microsoft.com/microsoft-365/enterprise/connect-to-microsoft-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module)します。
 その後、次の PowerShell コマンドを使用します。

```powershell
$newGroupName="<display name of the new group to add>"
$siteGrpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $newGroupName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $siteGrpName }).ObjectID
```

## <a name="remove-a-user"></a>ユーザーを削除する

他のユーザーのアクセスをサイトから削除する必要がある場合は、サイトでの参加に基づいてそのユーザーが現在メンバーになっているアクセス グループから削除します。

- 管理:サイト管理者のアクセス グループからユーザー アカウントを削除する

- アクティブ コラボレーション:サイト メンバーのアクセス グループからユーザー アカウントを削除する

- 表示:サイト ビューアーのアクセス グループからユーザー アカウントを削除する

AD DS を介してユーザーアカウントとグループを管理している場合は、通常の AD DS のユーザーおよびグループ管理手順を使用して適切なアクセスグループから適切なユーザーを削除し、サブスクリプションとの同期を待機します。

Office 365 を介してユーザーアカウントとグループを管理している場合は、Microsoft 365 管理センターまたは PowerShell を使用できます。

- Microsoft 365 管理センターの場合は、ユーザーアカウント管理者または会社の管理者の役割が割り当てられているユーザーアカウントでサインインし、グループを使用して適切なアクセスグループから適切なユーザーを削除します。

- PowerShell の場合、まず、 [Azure Active Directory PowerShell For Graph モジュールに接続](https://docs.microsoft.com/microsoft-365/enterprise/connect-to-microsoft-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module)します。
UPN を使ってアクセス グループからユーザー アカウントを削除するには、次の PowerShell コマンド ブロックを使用します。

```powershell
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

表示名を使ってアクセス グループからユーザー アカウントを削除するには、次の PowerShell コマンド ブロックを使用します。

```powershell
$userDisplayName="<display name of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="remove-a-group"></a>グループを削除する

グループ全体のアクセスを削除する必要がある場合は、サイトでの参加に基づいてそのグループが現在メンバーになっているアクセス グループから削除します。

- 管理:サイト管理者のアクセス グループからグループを削除する

- アクティブ コラボレーション:サイト メンバーのアクセス グループからグループを削除する

- 表示:サイト ビューアーのアクセス グループからグループを削除する

Windows Server Active Directory を使用してユーザーアカウントとグループを管理している場合は、通常の AD DS ユーザーおよびグループ管理手順を使用して適切なアクセスグループから適切なグループを削除し、サブスクリプションとの同期を待機します。

Office 365 を介してユーザーアカウントとグループを管理している場合は、Microsoft 365 管理センターまたは PowerShell を使用できます。

- Microsoft 365 管理センターの場合は、ユーザーアカウント管理者または会社の管理者の役割が割り当てられているユーザーアカウントでサインインし、グループを使用して適切なアクセスグループから適切なグループを削除します。

- PowerShell の場合、まず、 [Azure Active Directory PowerShell For Graph モジュールに接続](https://docs.microsoft.com/microsoft-365/enterprise/connect-to-microsoft-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module)します。
表示名を使用してアクセス グループからグループを削除するには、次の PowerShell コマンド ブロックを使用します。

```powershell
$groupMemberName="<display name of the group to remove>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="create-a-documents-subfolder-with-custom-permissions"></a>カスタムのアクセス許可を持つドキュメントのサブフォルダーを作成します。

分離したサイト内で作業している人々のサブセットでは、コラボレーションするためにプライバシー性の高い場所が必要になることがあります。SharePoint Online サイトでは、サイトの [ドキュメント] フォルダーにサブフォルダーを作成し、カスタムのアクセス許可を割り当てることがことができます。アクセス許可を持たないユーザーはサブフォルダーを表示できません。

カスタムのアクセス許可を持つドキュメントのサブフォルダーを作成するには、以下のことを行います。

1. サイトの管理者アクセスグループのメンバーであるアカウントにサインインします。 詳細については、「[一般法人向け Microsoft 365 にサインインする場所](https://support.microsoft.com/office/e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。

2. 分離したチーム サイトに移動し、 **[ドキュメント]** をクリックします。

3. カスタムのアクセス許可を持つサブフォルダーを格納するフォルダーをドキュメントのフォルダーの中で参照し、そのフォルダーを作成して開きます。

4. [ **共有**] をクリックします。

5. **[共有相手] > [詳細]** をクリックします。

6. **[アクセス許可の継承の中止]** をクリックしてから、 **[OK]** をクリックします。

7. [ **共有**] をクリックします。

8. **[共有相手] > [詳細]** をクリックします。

9. **[アクセス許可を付与する] > [共有相手] > [詳細]** をクリックします。

10. On the permissions page, click **\<site name> Members in the list**.

11. On the **\<site name> Members** page, select the checkmark next to the site members access group, click **Actions**, click **Remove users from group**, and then click **OK**.

12. 特定のメンバーをこのサブフォルダーに追加するには、 **[新規] > [ユーザーの追加]** をクリックします。

13. **[共有]** ダイアログ ボックスで、サブフォルダー内のファイルでコラボレーションできるユーザー アカウントの名前を入力してから、 **[共有]** をクリックします。

14. Web ページを更新して新しい結果を表示します。

15. Under **Groups** in the left navigation, click the **\<site name> Visitors** group and use steps 11-14 to specify the set of user accounts that can view the files in the subfolder (as needed).

16. Under **Groups** in the left navigation, click the **\<site name> Owners** group and use steps 11-14 to specify the set of user accounts that can administer the permissions in the subfolder (as needed).

17. ブラウザーで **[ユーザーとグループ]** タブを閉じます。

## <a name="see-also"></a>関連項目

[分離した SharePoint Online チーム サイト](isolated-sharepoint-online-team-sites.md)

[分離した SharePoint Online チーム サイトの設計](design-an-isolated-sharepoint-online-team-site.md)

[分離した SharePoint Online チーム サイトの展開](deploy-an-isolated-sharepoint-online-team-site.md)
