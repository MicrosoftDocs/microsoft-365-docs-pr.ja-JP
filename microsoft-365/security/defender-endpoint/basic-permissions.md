---
title: 基本的なアクセス許可を使用して Microsoft Defender セキュリティ センターにアクセスする
description: 基本的なアクセス許可を使用して Microsoft Defender for Endpoint ポータルにアクセスする方法について説明します。
keywords: ユーザー ロールの割り当て、読み取りおよび書き込みアクセスの割り当て、読み取り専用アクセスの割り当て、ユーザー、ユーザー の役割、役割
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: cb5762d2a9e4b62432aba6dacd1033ddc3c7daf2
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51163673"
---
# <a name="use-basic-permissions-to-access-the-portal"></a>基本的なアクセス許可を使用してポータルにアクセスする

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- Azure Active Directory
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-basicaccess-abovefoldlink)

基本的なアクセス許可管理を使用するには、以下の手順を参照してください。

次のいずれかのソリューションを使用できます。
- Azure PowerShell
- Azure portal

アクセス許可を詳細に制御するには [、役割ベースのアクセス制御に切り替えます](rbac.md)。

## <a name="assign-user-access-using-azure-powershell"></a>Azure PowerShell を使用してユーザー アクセスを割り当てる
次のいずれかのレベルのアクセス許可を持つユーザーを割り当てできます。
- フル アクセス (読み取りおよび書き込み)
- 読み取り専用アクセス

### <a name="before-you-begin"></a>はじめに

- Azure PowerShell をインストールします。 詳細については [、「Azure PowerShell をインストールして構成する方法」を参照してください](https://azure.microsoft.com/documentation/articles/powershell-install-configure/)。<br>

    > [!NOTE]
    > 管理者特権のコマンド ラインで PowerShell コマンドレットを実行する必要があります。

- Azure Active Directory に接続します。 詳細については [、「Connect-MsolService」を参照してください](https://docs.microsoft.com/powershell/module/msonline/connect-msolservice?view=azureadps-1.0&preserve-view=true)。

**フル アクセス** <br>
フル アクセスのユーザーは、ログインし、すべてのシステム情報を表示し、アラートを解決し、ファイルを送信して詳細な分析を行い、オンボーディング パッケージをダウンロードできます。
フル アクセス権を割り当てるには、ユーザーを "セキュリティ管理者" または "グローバル管理者" AAD 組み込みロールに追加する必要があります。

**読み取り専用アクセス** <br>
読み取り専用アクセス権を持つユーザーは、ログイン、すべての通知、および関連情報を表示できます。
アラートの状態を変更したり、詳細な分析のためにファイルを送信したり、状態の変更操作を実行したりできない。
読み取り専用アクセス権を割り当てるには、ユーザーを "Security Reader" Azure AD組み込みロールに追加する必要があります。

セキュリティ ロールを割り当てるには、次の手順を使用します。

- 読 **み取りおよび書き込** みアクセスの場合は、次のコマンドを使用してセキュリティ管理者の役割にユーザーを割り当てる必要があります。

  ```PowerShell
  Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress "secadmin@Contoso.onmicrosoft.com"
  ```
  
- 読 **み取り専用アクセスの** 場合は、次のコマンドを使用してユーザーをセキュリティ リーダー ロールに割り当てる必要があります。

  ```PowerShell
  Add-MsolRoleMember -RoleName "Security Reader" -RoleMemberEmailAddress "reader@Contoso.onmicrosoft.com"
  ```

詳細については [、「Azure Active Directory を使用してグループ メンバーを追加または削除する」を参照してください](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-members-azure-portal)。

## <a name="assign-user-access-using-the-azure-portal"></a>Azure portal を使用してユーザー アクセスを割り当てる

詳細については、「Azure Active Directory を使用して管理者と管理者以外の役割をユーザーに割り [当てる」を参照してください](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal)。

## <a name="related-topic"></a>関連トピック

- [RBAC を使用してポータル アクセスを管理する](rbac.md)