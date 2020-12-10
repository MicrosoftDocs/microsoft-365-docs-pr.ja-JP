---
title: Office 365 開発/テスト環境での分離した SharePoint Online チーム サイト
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
- TLG
- Ent_TLGs
ms.assetid: d1795031-beef-49ea-a6fc-5da5450d320d
description: '概要: Microsoft 365 開発/テスト環境で、組織の他の部分とは分離した SharePoint Online チームサイトを構成します。'
ms.openlocfilehash: 6e056cd1d930d13e1ae20f8f8d0cdc9aa886f17e
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "49616490"
---
# <a name="isolated-sharepoint-online-team-site-devtest-environment"></a>分離した SharePoint Online チーム サイト開発/テスト環境

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


 **概要:** Microsoft 365 開発/テスト環境で、組織の他の部分とは分離した SharePoint Online チームサイトを構成します。

Microsoft 365 の SharePoint Online チームサイトは、一般的なドキュメントライブラリ、OneNote ノートブック、その他のサービスを使用したコラボレーションの場所です。 多くの場合、部門または組織全体での幅広いアクセスやコラボレーションが望まれます。 しかし、小さなユーザー グループでコラボレーションを行うためにアクセスとアクセス許可を厳しく制御したい場合もあります。

SharePoint Online チーム サイトへのアクセスとユーザーが実行できる操作は、SharePoint グループとアクセス許可レベルによって制御されます。既定では、SharePoint Online サイトには、3 つのアクセス レベルがあります。

- **メンバー** 。サイトでリソースを表示、作成、変更できるユーザー。
- **所有者** 。権限の変更を含め、サイトを完全に制御できるユーザー。
- **訪問者** 。サイトのリソースの表示のみが可能なユーザー。

この記事では、ProjectX という秘密調査プロジェクトのための、分離した SharePoint Online チーム サイトの構成について順を追って説明します。アクセス要件は、次のとおりです。

- グループ メンバーシップによって制御される SharePoint の編集と表示の権限レベルを持つプロジェクトのメンバーだけがサイトとそのコンテンツ (ドキュメント、OneNote ノートブック、ページ) にアクセスできます。

- サイトの管理 (サイト レベルの権限の変更を含む) を実行できるのは、サイトの作成者とサイトの管理者グループのメンバーだけです。

Microsoft 365 開発/テスト環境で分離した SharePoint Online チームサイトを設定するには、3つのフェーズがあります。

1. Microsoft 365 開発/テスト環境を作成します。

2. ProjectX のユーザーとグループを作成する。

3. 新しい ProjectX SharePoint Online チーム サイトを作成して分離させる。

> [!TIP]
> 
            [ここ](https://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。

## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-microsoft-365-devtest-environment"></a>フェーズ 1: 軽量またはシミュレートされたエンタープライズ Microsoft 365 開発/テスト環境を構築する

最小要件での軽量な方法で分離した SharePoint Online チームサイトを作成する場合は、 [軽量な基本構成](https://docs.microsoft.com/microsoft-365/enterprise/lightweight-base-configuration-microsoft-365-enterprise)のフェーズ2とフェーズ3の手順に従ってください。

シミュレートされたエンタープライズ構成で分離した SharePoint Online チームサイトを作成する場合は、「 [Microsoft 365 テスト環境のパスワードハッシュ同期](https://docs.microsoft.com/microsoft-365/enterprise/password-hash-sync-m365-ent-test-environment)」の手順に従ってください。

> [!NOTE]
> 分離した SharePoint Online サイトを作成する場合は、シミュレートされたエンタープライズ開発/テスト環境を必要としません。これには、インターネットに接続されたシミュレートされたイントラネットと Active Directory ドメインサービス (AD DS) フォレストのディレクトリ同期が含まれます。 この記事は、分離した SharePoint Online サイトをテストして、一般的な組織を表す環境で試してみることができるオプションとして提供されています。

## <a name="phase-2-create-user-accounts-and-access-groups"></a>フェーズ 2: ユーザー アカウントとアクセス グループを作成する

「 [Office 365 PowerShell に接続](https://docs.microsoft.com/microsoft-365/enterprise/connect-to-microsoft-365-powershell) する」の手順を使用して、全体管理者アカウントを使用して試用版サブスクリプションに接続します。

- お使いのコンピューター (ライトウェイトの Microsoft 365 開発/テスト環境)。

- CLIENT1 仮想マシン (シミュレートされたエンタープライズ Microsoft 365 開発/テスト環境の場合)。

ProjectX の SharePoint Online チーム サイト用に新しいアクセス グループを作成するには、Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから次のコマンドを実行します。

```powershell
$groupName="ProjectX-Members"
$groupDesc="People allowed to collaborate for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Admins"
$groupDesc="People allowed to administer SharePoint for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Viewers"
$groupDesc="People allowed to view the SharePoint resources for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
```

組織名 (例: contosotoycompany)、所属地域に該当する 2 文字の国別コードを入力して、Windows PowerShell 用 Windows Azure Active Directory モジュールのプロンプトから次のコマンドを実行します。

```powershell
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "designer@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Designer" -FirstName Lead -LastName Designer -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

**New-MsolUser** コマンドの表示から、デザイナーのリーダーのアカウント用に生成されたパスワードを見つけて、安全な場所に記録しておきます。

次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。

```powershell
$userName= "researcher@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Researcher" -FirstName Lead -LastName Researcher -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

**New-MsolUser** コマンドの表示から、リサーチのリーダーのアカウント用に生成されたパスワードを見つけて、安全な場所に記録しておきます。

次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。

```powershell
$userName= "devvp@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Development VP" -FirstName Development -LastName VP -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

**New-MsolUser** コマンドの表示から、開発 VP 用に生成されたパスワードを見つけて、安全な場所に記録しておきます。

次に、新しいアクセス グループに新しいアカウントを追加するには、Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから次のコマンドを実行します。

```powershell
$grpName="ProjectX-Members"
$userUPN="designer@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$userUPN="researcher@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Admins"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userCredential.UserName }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Viewers"
$userUPN="devvp@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
```

結果:

- ProjectX-Members アクセス グループには、デザイナーのリーダーとリサーチのリーダーのユーザー アカウントが含まれます

- ProjectX-Admins アクセス グループには、試用版サブスクリプションの全体管理者アカウントが含まれます

- ProjectX-Viewers アクセス グループには、開発 VP のユーザー アカウントが含まれます

図 1 は、アクセス グループとそのメンバーシップを示しています。

**図 1**:

![分離した SharePoint Online グループサイトの Microsoft 365 グループとそのメンバーシップ](../../media/5b7373b9-2a80-4880-afe5-63ffb17237e6.png)

## <a name="phase-3-create-a-new-projectx-sharepoint-online-team-site-and-isolate-it"></a>フェーズ 3: 新しい ProjectX SharePoint Online チーム サイトを作成して分離させる

ProjectX 用の SharePoint Online チーム サイトを作成するには、次の操作を行います。

1. ローカルコンピューター (軽量構成) または CLIENT1 (シミュレートされたエンタープライズ構成) のどちらかでブラウザーを使用して、 <https://admin.microsoft.com> 全体管理者アカウントを使用して Microsoft 365 管理センター () にサインインします。

2. タイルのリストで、 **[SharePoint]** をクリックします。

3. ブラウザーの新しい SharePoint タブで、 **[+ サイトの作成]** をクリックします。

4. **[チーム サイト名]** に「 **ProjectX**」と入力します。 **[プライバシーの設定]** で、 **[非公開 - メンバーのみがこのサイトにアクセス可能]** を選択します。

5. **[チーム サイトの説明]** に、「 **ProjectX 用の SharePoint サイト**」と入力し、 **[次へ]** をクリックします。

6. **[誰を追加しますか]** ウィンドウで、 **[完了]** をクリックします。

7. ブラウザーの新しい **[ProjectX-Home]** タブのツールバーで、設定アイコンをクリックし、 **[サイトの権限]** をクリックします。

8. **[サイトの権限]** ウィンドウで、 **[高度な権限の設定]** をクリックします。

9. ブラウザーの新しい **[権限:Project X]** タブで、 **[アクセス要求の設定]** をクリックします。

10. **[アクセス要求の設定]** ダイアログ ボックスの **[サイトと個別のファイルおよびフォルダーの共有をメンバーに許可します]** と **[アクセス要求の許可]** をクリアし (これによって、3 つのチェック ボックスがすべてクリアされる)、 **[OK]** をクリックします。

11. リストの **[ProjectX のメンバー]** をクリックします。

12. **[ユーザーとグループ]** ページで、 **[新規]** をクリックします。

13. **[共有]** ダイアログ ボックスに「 **ProjectX-Members**」と入力し、それを選択して、 **[共有]** をクリックします。

14. ブラウザーの戻るボタンをクリックします。

15. リストの **[ProjectX の所有者]** をクリックします。

16. **[ユーザーとグループ]** ページで、 **[新規]** をクリックします。

17. **[共有]** ダイアログ ボックスに「 **ProjectX-Admins**」と入力し、それを選択して、 **[共有]** をクリックします。

18. ブラウザーの戻るボタンをクリックします。

19. リストの **[ProjectX の訪問者]** をクリックします。

20. **[ユーザーとグループ]** ページで、 **[新規]** をクリックします。

21. **[共有]** ダイアログ ボックスに「 **ProjectX-Viewers**」と入力し、それを選択して、 **[共有]** をクリックします。

22. ブラウザーの **[ユーザーとグループ]** タブを閉じ、ブラウザーの **[ProjectX-Home]** タブをクリックし、 **[サイトの権限]** ウィンドウを閉じます。

権限を構成した結果を以下に示します。

- ProjectX Members SharePoint グループに含まれるのは、ProjectX-Members アクセス グループ (デザイナーのリーダーとリサーチのリーダーのユーザー アカウントのみを含む) と ProjectX グループ (全体管理者のユーザー アカウントのみを含む) だけです。

- ProjectX Owners SharePoint グループに含まれるのは、ProjectX-Admins アクセス グループ (全体管理者のユーザー アカウントのみを含む) だけです。

- ProjectX Visitors SharePoint グループに含まれるのは、ProjectX-Viewers アクセス グループ (開発 VP のユーザー アカウントのみを含む) だけです。

- メンバーはサイト レベルの権限を変更できません (これを実行できるのは、ProjectX-Admins グループのメンバーだけです)。

- その他のユーザー アカウントは、サイトやそのリソースにアクセスすることも、そのサイトへのアクセスを要求することもできません。

図 2 は、SharePoint グループとそのメンバーシップを示しています。

**図 2**

![分離 SharePoint Online グループ サイトの SharePoint Online グループおよびそのメンバーシップ](../../media/595abff4-64f9-49de-a37a-c70c6856936b.png)

デザイナーのリーダーのユーザー アカウントを使用したアクセスをデモンストレーションします。

1. ブラウザーの **[ProjectX-Home]** タブを閉じ、ブラウザーの **[Microsoft Office Home]** タブをクリックします。

2. 全体管理者の名前をクリックし、 **[サインアウト]** をクリックします。

3. <https://admin.microsoft.com>デザイナーのリーダーのアカウント名とパスワードを使用して、Microsoft 365 管理センター () にサインインします。

4. タイルのリストで、 **[SharePoint]** をクリックします。

5. ブラウザーの新しい **[SharePoint]** タブの検索ボックスに「 **ProjectX**」と入力し、検索をアクティブ化した後、 **[ProjectX]** チーム サイトをクリックします。ProjectX チーム サイトのブラウザーに新しいタブが表示されます。

6. 設定アイコンをクリックします。 **[サイトの権限]** にオプションがありません。サイトの権限を変更できるのは ProjectX-Admins グループのメンバーだけなので、これは正常です。

7. お好きなメモ帳やテキスト エディターを開きます。

8. ProjectX チーム サイトの URL をコピーし、メモ帳やテキスト エディターの新しい行に貼り付けます。

9. ブラウザーの新しい **[ProjectX-Home]** タブで、 **[ドキュメント]** をクリックします。

10. ProjectX ドキュメント フォルダーの URL をコピーし、メモ帳やテキスト エディターの新しい行に貼り付けます。

11. ブラウザーの **[ProjectX-Documents]** タブで、 **[新規] > [Word 文書]** の順にクリックします。

12. ページに何らかのテキストを入力し、状態が [ **保存済み**] になっていることを待ってから、ブラウザーの [戻る] ボタンをクリックし、ページを更新します。 **ドキュメント** フォルダーに新しい **Document.docx** が表示されます。

13. **[Document.docx]** ドキュメントの省略記号をクリックし、 **[リンクの取得]** をクリックします。

14. **['Document.docx' の共有]** ダイアログ ボックスの URL をコピーし、メモ帳かテキスト エディターの新しい行に貼り付けた後、 **['Document.docx' の共有]** ダイアログ ボックスを閉じます。

15. ブラウザーの **[ProjectX-Documents]** タブと **[SharePoint]** タブを閉じ、 **[Microsoft Office Home]** タブをクリックします。

16. **[デザイナーのリーダー]** の名前をクリックし、 **[サインアウト]** をクリックします。

開発 VP のユーザー アカウントを使用したアクセスをデモンストレーションします。

1. <https://admin.microsoft.com>開発 VP のアカウント名とパスワードを使用して、Microsoft 365 管理センター () にサインインします。

2. タイルのリストで、 **[SharePoint]** をクリックします。

3. ブラウザーの新しい **[SharePoint]** タブの検索ボックスに「 **ProjectX**」と入力し、検索をアクティブ化した後、 **[ProjectX]** チーム サイトをクリックします。ProjectX チーム サイトのブラウザーに新しいタブが表示されます。

4. **[ドキュメント]** をクリックし、 **[Document.docx]** ファイルをクリックします。

5. ブラウザーの **[Document.docx]** タブで、テキストの変更を試みます。" **このドキュメントは読み取り専用です。**" というメッセージが表示されます。開発 VP のユーザー アカウントにはサイトの表示権限しかないため、これは正常です。

6. ブラウザーの **[Document.docx]** タブ、 **[ProjectX-Documents]** タブ、 **[SharePoint]** タブを閉じます。

7. **[Microsoft Office Home]** タブをクリックし、 **[開発 VP]** の名前をクリックした後、 **[サインアウト]** をクリックします。

権限を持たないユーザー アカウントでのアクセスをデモンストレーションします。

1. <https://admin.microsoft.com>User 3 のアカウント名とパスワードを使用して、Microsoft 365 管理センター () にサインインします。

2. タイルのリストで、 **[SharePoint]** をクリックします。

3. ブラウザーの新しい **[SharePoint]** タブの検索ボックスに「 **ProjectX**」と入力し、検索をアクティブ化します。" **検索に一致するものがここにありません。**" というメッセージが表示されます。

4. メモ帳またはテキスト エディターで開いたインスタンスから、ProjectX サイトの URL を、ブラウザーのアドレス バーにコピーし、 **Enter** キーを押します。 **[アクセスは拒否されました]** というページが表示されます。

5. メモ帳またはテキスト エディターから、ProjectX Documents フォルダーの URL を、ブラウザーのアドレス バーにコピーし、 **Enter** キーを押します。 **[アクセスは拒否されました]** というページが表示されます。

6. メモ帳またはテキスト エディターから、Documents.docx ファイルの URL を、ブラウザーのアドレス バーにコピーし、 **Enter** キーを押します。 **[アクセスは拒否されました]** というページが表示されます。

7. ブラウザーの **[SharePoint]** タブを閉じ、 **[Microsoft Office Home]** タブをクリックし、 **[User 3]** の名前をクリックし、 **[サインアウト]** をクリックします。

これで、分離した SharePoint Online サイトをさらにお試しいただけます。

## <a name="next-step"></a>次のステップ

分離した SharePoint Online チーム サイトを実稼働に展開する準備ができたら、「[分離した SharePoint Online チーム サイトの設計](design-an-isolated-sharepoint-online-team-site.md)」にある設計に関するステップバイステップの考慮事項を参照してください。

## <a name="see-also"></a>関連項目

[分離した SharePoint Online チーム サイト](isolated-sharepoint-online-team-sites.md)

[クラウド導入のテスト ラボ ガイド (TLG)](https://docs.microsoft.com/microsoft-365/enterprise/cloud-adoption-test-lab-guides-tlgs)

[シミュレートされたエンタープライズ基本構成](https://docs.microsoft.com/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise)

[軽量な基本構成](https://docs.microsoft.com/microsoft-365/enterprise/lightweight-base-configuration-microsoft-365-enterprise)

[クラウド導入およびハイブリッド ソリューション](https://docs.microsoft.com/office365/enterprise/cloud-adoption-and-hybrid-solutions)
