---
title: 個別のユーザーのパスワードを無期限に設定する
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f493e3af-e1d8-4668-9211-230c245a0466
description: 管理者アカウントにサインインMicrosoft 365を使用して、個々のユーザー パスワードを有効期限が切れWindows PowerShell。
ms.openlocfilehash: 29d0ebcbb3f9fb197e574731e23aaa64c2fa7894
ms.sourcegitcommit: 00f001019c653269d85718d410f970887d904304
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2021
ms.locfileid: "53394257"
---
# <a name="set-an-individual-users-password-to-never-expire"></a>個別のユーザーのパスワードを無期限に設定する

この記事では、個々のユーザーのパスワードを期限切れにしない設定方法について説明します。 PowerShell を使用してこれらの手順を実行する必要があります。

## <a name="before-you-begin"></a>開始する前に

この記事は、職場、学校、または非営利団体のパスワードの有効期限ポリシーを設定する管理者を対象としています。 これらの手順を完了するには、Microsoft 365 の管理者アカウントでサインインする必要があります。 [管理者アカウントとは](../../business-video/admin-center-overview.md)。

これらの手順を実行するには [、グローバル管理者またはパスワード](about-admin-roles.md) 管理者である必要があります。

Microsoft クラウド サービスのグローバル管理者は、Azure Active Directory [PowerShell](/powershell/azure/active-directory/install-adv2)を使用して、Graphユーザーに対して有効期限が切れないパスワードを設定できます。 AzureAD コマンドレット [を使用して](/powershell/module/Azuread) 、有効期限が切れない構成を削除したり、有効期限が切れないユーザー パスワードを確認することもできます。

このガイドは、Intune や Microsoft 365 などの他のプロバイダーにも適用されます。これは、Azure AD ID およびディレクトリ サービスにも依存します。 パスワードの有効期限は、変更できるポリシーの唯一の部分です。


## <a name="how-to-check-the-expiration-policy-for-a-password"></a>パスワードの有効期限ポリシーを確認する方法

AzureAD モジュールの Get-AzureADUser コマンドの詳細については、参照記事 [Get-AzureADUser を参照してください](/powershell/module/Azuread/Get-AzureADUser)。

次のいずれかのコマンドを実行します：

- 1 人のユーザーのパスワードが有効期限が切れないに設定されている場合は *、UPN (user@contoso.onmicrosoft.com* など) または確認するユーザーのユーザー ID を使用して、次のコマンドレットを実行します。

    ```powershell
    Get-AzureADUser -ObjectId <user id or UPN> | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    }
    ```

    例:

    ```powershell
    Get-AzureADUser -ObjectId userUPN@contoso.com | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    }
    ```

- すべてのユーザーに **対して [パスワードの有効期限が切** れることはありません] 設定を表示するには、次のコマンドレットを実行します。

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
     }
    ```

- 現在のユーザーのデスクトップで PasswordNeverExpires を Html で持つすべてのユーザーのレポートを取得するには、ReportPasswordNeverExpires.htm **l**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Html | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.html
    ```

- 現在のユーザーのデスクトップで PasswordNeverExpires を CSV で持つすべてのユーザーのレポートを取得 **するには**、名前を付ReportPasswordNeverExpires.csv

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Csv -NoTypeInformation | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.csv

## Set a password to never expire

Run one of the following commands:

- To set the password of one user to never expire, run the following cmdlet by using the UPN or the user ID of the user:

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies DisablePasswordExpiration
    ```

- 組織内のすべてのユーザーのパスワードに有効期限を設定するには、次のコマンドレットを実行します。

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration
    ```

> [!WARNING]
> パラメーターを使用して構成された `-PasswordPolicies DisablePasswordExpiration` ユーザー アカウントは、属性に基づいて年齢を変更 `pwdLastSet` します。 属性に基づいて、有効期限をに変更した場合 `pwdLastSet` 、pwdLastSet が 90 日を超えるすべてのパスワードでは、次回サインイン時にパスワードを変更する必要があります `-PasswordPolicies None` 。 この変更は、多数のユーザーに影響を与える可能性があります。

### <a name="set-a-password-to-expire"></a>パスワードの有効期限を設定する

次のいずれかのコマンドを実行します：

- パスワードの有効期限が切れる 1 人のユーザーのパスワードを設定するには、UPN またはユーザーのユーザー ID を使用して次のコマンドレットを実行します。

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies None
    ```

- 組織内のすべてのユーザーのパスワードを期限切れに設定するには、次のコマンドレットを使用します。

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies None
    ```

## <a name="related-content"></a>関連コンテンツ

[ユーザーが自分でパスワードをリセットできるようにする](../add-users/let-users-reset-passwords.md) (記事)\
[パスワードをリセットする](../add-users/reset-passwords.md) (記事)\
[組織のパスワード有効期限ポリシーを設定する](../manage/set-password-expiration-policy.md) (記事)
