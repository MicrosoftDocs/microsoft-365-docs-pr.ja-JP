---
title: ユーザーの強力なパスワード要件をオフにする
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
search.appverid:
- BCS160
- MET150
- MOE150
description: ユーザーに強力なパスワード要件を設定する方法については、Windows PowerShell。
ms.openlocfilehash: 87ba9e0323c379d8c2589dbb82c38c531dd9d047
ms.sourcegitcommit: 4886457c0d4248407bddec56425dba50bb60d9c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2021
ms.locfileid: "53286269"
---
# <a name="turn-off-strong-password-requirements-for-users"></a>ユーザーの強力なパスワード要件をオフにする

この記事では、ユーザーの強力なパスワード要件をオフにする方法について説明します。 強力なパスワード要件は、ビジネス組織向けMicrosoft 365既定で有効になっています。 組織には、強力なパスワードを無効にする必要がある場合があります。 強力なパスワード要件をオフにするには、以下の手順に従います。 PowerShell を使用してこれらの手順を実行する必要があります。

## <a name="before-you-begin"></a>はじめに

この記事は、ビジネス、学校、または非営利団体のパスワード ポリシーを管理するユーザー向けです。 これらの手順を完了するには、Microsoft 365 の管理者アカウントでサインインする必要があります。 [管理者アカウントとは](/microsoft-365/business-video/admin-center-overview) これらの手順を実行するには [、グローバル管理者またはパスワード](about-admin-roles.md) 管理者である必要があります。

PowerShell を使用して、Microsoft 365接続する必要があります。

## <a name="set-strong-passwords"></a>強力なパスワードを設定する

1. [Connect PowerShell をMicrosoft 365する方法を説明します](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

2. PowerShell を使用すると、次のコマンドを使用して、すべてのユーザーの強力なパスワード要件をオフにできます。

    ```powershell
    Get-MsolUser | Set-MsolUser -StrongPasswordRequired $false

3. You can turn of strong password requirements for specific users with this command:

    ```powershell
    Set-MsolUser –UserPrincipalName –StrongPasswordRequired  $false
    ```

> [!NOTE]
> userPrincipalName は、ユーザー名の後にアット 記号 (@) とドメイン名が続くインターネット スタイルのサインイン形式である必要があります。 たとえば、次の user@contoso.com。

## <a name="related-content"></a>関連コンテンツ

[PowerShell で Microsoft 365 に接続する方法](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

[PowerShell MsolUser コマンドの詳細情報](/powershell/azure/active-directory/install-adv2)

[パスワード ポリシーの詳細情報](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts)
