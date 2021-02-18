---
title: 分離した SharePoint Online チーム サイトの展開
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/30/2019
audience: ITPro
ms.topic: article
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 3033614b-e23b-4f68-9701-f62525eafaab
description: このステップ バイ ステップ展開ガイドを使用して、SharePoint Online の独立したチーム サイトを Microsoft Office 365 で作成および構成します。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d226a545c3f8dc274f02e5d54d39739fe5d981ea
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/18/2021
ms.locfileid: "50288349"
---
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a>分離した SharePoint Online チーム サイトの展開

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**適用対象**
- [Microsoft Defender for Office 365 プラン 1 およびプラン 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

 **概要:** ステップごとの手順を使用して、分離した新しい SharePoint Online チーム サイトを展開します。

この記事は、分離した SharePoint Online チーム サイトを Microsoft Office 365 で作成および構成するためのステップごとの展開ガイドです。これらの手順は、アクセス レベルごとに 1 つの Azure Active Directory (AD) ベースのアクセス グループが含まれる、3 つの既定の SharePoint グループとそれに対応するアクセス許可レベルの使用を前提としています。

## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a>フェーズ 1:チーム サイト アクセス グループの作成と設定

このフェーズでは、3 つの既定の SharePoint グループに対して 3 つの Azure AD ベースのアクセス グループを作成し、それらに適切なユーザー アカウントを設定します。

> [!NOTE]
> 次の手順は、すべての必要なユーザー アカウントが既に存在し、適切なライセンスが割り当てられていることを前提としています。そうでない場合は、それらを追加して、手順 1 に進む前にライセンスを割り当てます。

### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a>手順 1:サイトの SharePoint Online 管理者を一覧表示する

分離したチーム サイトの SharePoint Online 管理者に対応するユーザー アカウントのセットを決定します。

Microsoft 365 を使用してユーザー アカウントとグループを管理し、Windows PowerShell を使用する場合は、ユーザー プリンシパル名 (UPN) の一覧 (UPN: belindan@contoso.com など) を作成します。

### <a name="step-2-list-the-members-for-the-site"></a>手順 2: サイトのメンバーを一覧表示する

分離したチーム サイトのメンバーに対応するユーザー アカウントのセットを決定します。メンバーはサイト内に格納されているリソースで共同作業を行います。

Microsoft 365 を使用してユーザー アカウントとグループを管理し、PowerShell を使用する場合は、UPN の一覧を作成します。 サイト メンバーが数多く存在する場合は、UPN の一覧をテキスト ファイルに格納し、PowerShell コマンドを 1 回実行することですべて追加できます。

### <a name="step-3-list-the-viewers-for-the-site"></a>手順 3:サイトのビューアーを一覧表示する

分離したチーム サイトのビューアーに対応するユーザー アカウントのセットを決定します。ビューアーは、サイトに格納されているリソースを表示できますが、リソースを変更したり、そのコンテンツで直接共同作業を行ったりすることはできません。

Microsoft 365 を使用してユーザー アカウントとグループを管理し、PowerShell を使用する場合は、UPN の一覧を作成します。 サイト メンバーが数多く存在する場合は、UPN の一覧をテキスト ファイルに格納し、PowerShell コマンドを 1 回実行することですべて追加できます。

サイトのビューアーには、経営幹部、弁護士、または部門間の利害関係者などが含まれます。

### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a>手順 4:Azure AD でサイト用の 3 つのアクセス グループを作成する

Azure AD で次のアクセス グループを作成する必要があります。

- サイト管理者 (手順 1 のリストが含まれます)
- サイト メンバー (手順 2 のリストが含まれます)
- サイト ビューアー (手順 3 のリストが含まれます)

1. お使いのブラウザーで、Azure Portal (<https://portal.azure.com>) に移動し、ユーザー管理の管理者または会社管理者のロールに割り当てられたアカウントの資格情報でサインインします。

2. Azure Portal で **[Azure Active Directory] > [グループ]** の順にクリックします。

3. **[グループ] - [すべてのグループ]** ブレードで、**[+ 新しいグループ]** をクリックします。

4. [新しい **グループ] ブレードで、次の設定を** 行います。

   - **[グループの種類]** で **[セキュリティ]** を選択します。

   - **[名前]** にグループ名を入力します。

   - **[グループの説明]** にグループの説明を入力します。

   - **[メンバーシップの種類]** で **[割り当て済み]** を選択します。

5. **[作成]** をクリックして、 **[グループ]** ブレードを閉じます。

6. 追加グループについて手順 3 から 5 を繰り返します。

> [!NOTE]
> Office の機能を有効にできるグループを作成するには、Azure Portal を使用する必要があります。 SharePoint Online の分離サイトが後で Azure Information Protection ラベルを持つ高機密サイトとして構成され、ファイルを暗号化し、特定のグループにアクセス許可を割り当てる場合、許可されたグループは Office 機能を有効にした上で作成されている必要があります。 Azure AD グループが作成された後は、その Office の機能の設定は変更できません。

これで 3 つのサイトのアクセス グループの構成が完了します。

![独立した SharePoint Online サイトの展開用の 3 つのアクセス グループ。](../../media/c2557f61-478b-4494-95e9-d79fe5909e8b.png)

### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a>手順 5:アクセス グループにユーザー アカウントを追加する

この手順では、次の操作を行います。

1. 手順 1 のユーザーの一覧をサイト管理者アクセス グループに追加します。
2. 手順 2 のユーザーの一覧をサイト メンバーのアクセス グループに追加します。
3. 手順 3 のユーザーの一覧をサイト閲覧者のアクセス グループに追加します。

Active Directory ドメイン サービス (AD DS) を使用してユーザー アカウントとグループを管理している場合は、通常の AD DS ユーザーおよびグループ管理手順を使用して適切なアクセス グループにユーザーを追加し、Microsoft 365 サブスクリプションとの同期を待ちます。

Office 365 を使用してユーザー アカウントとグループを管理している場合は、Microsoft 365 管理センターまたは PowerShell を使用できます。 すべてのアクセス グループに重複するグループ名がある場合は、Microsoft 365 管理センターを使用する必要があります。

Microsoft 365 管理センターでは、ユーザー アカウント管理者または会社管理者の役割が割り当てられているユーザー アカウントでサインインし、グループを使用して適切なユーザー アカウントとグループを適切なアクセス グループに追加します。

PowerShell の場合は、 [最初に Graph 用 Azure Active Directory PowerShell モジュールを使用して接続します](../../enterprise/connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。

次に、以下のコマンド ブロックを使用して、個々のユーザー アカウントをアクセス グループに追加します。

```powershell
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

いずれかのアクセス グループのユーザー アカウントの UPN をテキスト ファイルに格納した場合は、次の PowerShell コマンド ブロックを使用して、それらすべてのユーザー アカウントを一度に追加します。

```powershell
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

PowerShell の場合、次のコマンド ブロックを使用して、個々のグループをアクセス グループに追加します。

```powershell
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

次のような結果が表示されます。

- サイト管理者の Azure AD グループには、サイト管理者のユーザー アカウントまたはグループが含まれる
- サイト メンバーの Azure AD グループには、サイト メンバーのユーザー アカウントまたはグループが含まれる
- サイト ビューアーの Azure AD グループには、サイトのコンテンツを表示できるユーザー アカウントまたはグループのみが含まれる

Microsoft 365 管理センターまたは次の PowerShell コマンド ブロックを使用して、各アクセス グループのグループ メンバーの一覧を検証します。

```powershell
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

以下に示すのが、でき上がった構成で、この構成にはユーザー アカウントとグループが設定された3 つのサイトのアクセス グループが含まれます。

![ユーザー アカウントが設定された 3 つのアクセス グループ。](../../media/2320107c-dad6-4c8f-94e5-f6427c125e71.png)

## <a name="phase-2-create-and-configure-the-isolated-team-site"></a>フェーズ 2:分離したチーム サイトを作成し構成する

このフェーズでは、分離した SharePoint Online サイトを作成し、新しい Azure AD ベースのアクセス グループを使用するために既定の SharePoint Online アクセス許可レベルのアクセス許可を構成します。 既定では、新しいチーム サイトには Microsoft 365 グループと他の関連リソースが含まれますが、この場合は、Microsoft 365 グループなしでチーム サイトを作成します。 これにより、SharePoint を通じてアクセス許可を完全に維持できます。

最初に、次の手順で SharePoint Online チーム サイトを作成します。

1. SharePoint Online チーム サイト (SharePoint Online 管理者) の管理にも使用されるアカウントを使用して、Microsoft 365 管理センターにサインインします。 詳細については、「[一般法人向け Office 365 にサインインする場所](https://support.microsoft.com/office/e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。

2. Microsoft 365 管理センターの[管理センター] で **、[SharePoint] をクリックします**。

3. SharePoint 管理センターで、[サイト] **を展開し** 、[アクティブなサイト] **をクリックします**。

4. [作成 **] を** クリックし、[その他のオプション] **を選択します**。

5. [テンプレートの **選択] ボックスの一覧** で、[チーム サイト] **を選択します**。

6. **[サイト名]** にチーム サイトの名前を入力します。

7. プライマリ **管理者で**、ログインに使用するアカウントを入力します。

8. **[完了]** をクリックします。

次に、新しい SharePoint Online チーム サイトから、アクセス許可を構成します。

1. ツールバーで、設定アイコンをクリックしてから、**[サイトの権限]** をクリックします。

2. [ **サイトの共有] で**、[メンバー **が共有する方法の変更] をクリックします**。

3. Choose the **Only site owners can share files, folders, and the site**.

4. [ **アクセス要求を許可する] を [オフ]** に **設定します**。

5. [**保存**] をクリックします。

6. [アクセス許可 **] ウィンドウで、[** 高度なアクセス許可 **の設定] をクリックします**。

7. On the **Permissions** tab of your browser, click **\<site name> Members** in the list.

8. **[ユーザーとグループ]** で、 **[新規]** をクリックします。

9. **[共有]** ダイアログ ボックスで、サイト メンバーのアクセス グループの名前を入力し、それを選択してから、**[共有]** をクリックします。

10. ブラウザーの戻るボタンをクリックします。

11. Click **\<site name> Owners** in the list.

12. **[ユーザーとグループ]** で、 **[新規]** をクリックします。

13. **[共有]** ダイアログ ボックスで、サイト管理者のアクセス グループの名前を入力し、それを選択してから、**[共有]** をクリックします。

14. ブラウザーの戻るボタンをクリックします。

15. Click **\<site name> Visitors** in the list.

16. **[ユーザーとグループ]** で、 **[新規]** をクリックします。

17. **[共有]** ダイアログ ボックスで、サイト ビューアーのアクセス グループの名前を入力し、それを選択してから、**[共有]** をクリックします。

18. ブラウザーの **[アクセス権]** タブを閉じます。

これらのアクセス権の設定の結果は次のとおりです。

- The **\<site name> Owners** SharePoint group contains the site admins access group, in which all the members have the **Full control** permission level.
- The **\<site name> Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.
- The **\<site name> Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.
- メンバーが他のメンバーを招待したり、メンバー以外のユーザーがアクセス権を要求したりする機能は無効です。

以下に示すのができ上がった構成で、この構成にはユーザー アカウントと Azure AD グループが設定された 3 つのアクセス グループを使用するように構成されたサイト用の 3 つの SharePoint グループ含まれます。

![アクセス グループおよびユーザー アカウントが設定された、独立した SharePoint Online サイトの最終的な構成。](../../media/e7618971-06ab-447b-90ff-d8be3790fe63.png)

いずれかのアクセス グループのグループ メンバーシップを介して、サイトのメンバーとともにサイトのリソースを使用して共同作業を行えるようになります。

## <a name="next-step"></a>次の手順

サイト アクセス グループ メンバーシップを変更したり、カスタム アクセス許可を持つドキュメント フォルダーを作成したりする必要がある場合は、「[分離した SharePoint Online チーム サイトの管理](manage-an-isolated-sharepoint-online-team-site.md)」を参照してください。

## <a name="see-also"></a>関連項目

[分離した SharePoint Online チーム サイト](isolated-sharepoint-online-team-sites.md)

[分離した SharePoint Online チーム サイトの設計](design-an-isolated-sharepoint-online-team-site.md)

[分離した SharePoint Online チーム サイトの管理](manage-an-isolated-sharepoint-online-team-site.md)
