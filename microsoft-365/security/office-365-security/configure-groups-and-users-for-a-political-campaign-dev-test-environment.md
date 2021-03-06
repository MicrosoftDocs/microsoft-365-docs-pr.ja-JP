---
title: グループとユーザーを作成する - 選挙運動の開発/テスト環境用
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
localization_priority: Priority
search.appverid:
- MET150
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: '要約: 選挙運動の開発/テスト環境向けのユーザーとグループで Office 365 と Enterprise Mobility + Security (EMS) の試用版サブスクリプションを作成します。'
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2e21cdfb0aabbdb10397d6d16c879756449a498e
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "51204966"
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a>選挙運動の開発/テスト環境用にグループとユーザーを構成する

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**適用対象**
- [Microsoft Defender for Office 365 プラン 2](defender-for-office-365.md)

 **要約:** 選挙運動の開発/テスト環境向けのユーザーとグループで Office 365 と Enterprise Mobility + Security (EMS) の試用版サブスクリプションを作成します。

簡略化されたユーザー アカウントとグループを含む開発/テスト環境を「[選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)」ソリューション用に作成するには、この資料の手順を使用します。

## <a name="phase-1-create-your-office-365-devtest-environment"></a>フェーズ 1: Office 365 の開発/テスト環境を作成する

このフェーズでは、選挙運動を務める架空の組織用に Office 365 E5 と Enterprise Mobility + Security (EMS) E5 の試用版サブスクリプションを取得します。

まず、「[軽量な基本構成](../../enterprise/lightweight-base-configuration-microsoft-365-enterprise.md)」の **フェーズ 2** の指示に従います。

次に、EMS E5 試用版サブスクリプションにサインアップして、試用版サブスクリプションと同じ組織に追加します。

1. 必要に応じて、試用版サブスクリプション用の全体管理者アカウントの資格情報で管理センターにサインインします。 詳細については、「[サインインする場所](https://support.microsoft.com/office/e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。

2. **[管理者]** タイルをクリックします。

3. ブラウザーの **[Microsoft 365 管理センター]** タブの、左側のナビゲーションで **[請求] > [サービスを購入する]** の順にクリックします。

4. **[サービスを購入]** ページで、 **[Enterprise Mobility + Security E5]** 項目を探します。その項目の上にマウス ポインターを移動させ、 **[無料試用版を起動する]** をクリックします。

5. **[注文の確認]** ページで、 **[今すぐ実行]** をクリックします。

6. **[注文の受領書]** ページで、**[続行]** をクリックします。

次に、全体管理者アカウントの EMS E5 ライセンスを有効にします。

1. ブラウザーの **[Microsoft 365 管理センター]** タブの左側のナビゲーションで **[ユーザー] > [アクティブなユーザー]** の順にクリックします。

2. 全体管理者アカウントをクリックしてから、 **[製品ライセンス]** で **[編集]** をクリックします。

3. **[製品ライセンス]** ウィンドウで、 **Enterprise Mobility + Security E5** の製品ライセンスを **[オン]** にして、 **[保存]** をクリックしてから、 **[閉じる]** を 2 回クリックします。

## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a>フェーズ 2: Azure Active Directory (AD) グループを作成して構成する

このフェーズでは、選挙運動用に Azure AD グループを作成して構成します。

最初に、Azure portal で一般的な選挙運動グループのセットを作成します。

1. ブラウザーで別のタブを開き、Azure portal <https://portal.azure.com> にアクセスします。 必要に応じて、Office 365 E5 の試用版サブスクリプション用の全体管理者アカウントの資格情報でサインインします。

2. Azure portal で **[Azure Active Directory] > [ユーザーとグループ] > [すべてのグループ]** の順にクリックします。

3. このリストのグループ名ごとに、次の手順を実行します。

   - 戦略的シニア スタッフ

   - IT スタッフ

   - 分析スタッフ

   - 正規のコア スタッフ

   - 運用スタッフ

   - フィールド スタッフ

1. **[すべてのグループ]** ブレードで、**[+ 新しいグループ]** をクリックします。

2. リストにあるグループ名を **[名前]** に入力します。

3. **[メンバーシップ]** で **[動的ユーザー]** を選択します。

4. **[Office の機能を有効にする]** で **[はい]** をクリックします。

5. **[動的クエリの追加]** をクリックします。

6. **[ユーザーを追加する場所]** で、**[部署]** を選択します。

7. 次のフィールドで、**[等しい]** を選択します。

8. 次のフィールドで、リストにあるグループ名を入力します。

9. **[クエリの追加]** をクリックしてから、**[作成]** をクリックします。

10. **[ユーザーとグループ - すべてのグループ]** をクリックします。

次に、メンバーに Office 365 E5 および EMS E5 のライセンスが自動的に割り当てられるようにグループを構成します。

1. Azure portal で **[Azure Active Directory] > [ライセンス] > [すべての製品]** の順にクリックします。

2. 一覧で、**[Enterprise Mobility + Security E5]** と **[Office 365 Enterprise E5]** を選択して、**[+ 割り当て]** をクリックします。

3. **[ライセンスの割り当て]** ブレードで、**[ユーザーとグループ]** をクリックします。

4. グループの一覧で、次を選択します。

   - 分析スタッフ

   - フィールド スタッフ

   - IT スタッフ

   - 運用スタッフ

   - 正規のコア スタッフ

   - 戦略的シニア スタッフ

5. **[選択]** をクリックし、**[割り当て]** をクリックします。

6. ブラウザーの [Azure Portal] タブを閉じます。

## <a name="phase-3-add-your-user-accounts"></a>フェーズ 3:ユーザー アカウントを追加する

このフェーズでは、選挙運動のサンプル ユーザー アカウントを追加します。

まず、[Azure Active Directory PowerShell for Graph モジュールに接続](../../enterprise/connect-to-microsoft-365-powershell.md)します。

次に、組織名、場所、および共通のパスワードを入力し、PowerShell コマンド プロンプトまたは Integrated Scripting Environment (ISE) からこれらのコマンドを実行します。

```powershell
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1")
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2")
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1")
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2")
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1")
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1")
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
```

> [!IMPORTANT]
> ここでは共通のパスワードを使用することで、自動化と、開発/テスト環境の構成を容易にしています。運用サブスクリプションでの使用はお勧めしません。これらの新しいユーザー アカウントでサインインするときに、パスワードの変更を求めるダイアログが表示されます。

動的グループのメンバーシップとグループ ベースのライセンスが正常に機能していることを確認するには、次の手順を使用します。

1. ブラウザーの **[Microsoft Office Home]** タブで、 **[管理者]** タイルをクリックします。

2. ブラウザーの新しい **Microsoft 365 管理センター** のタブで、**[ユーザー]** をクリックします。

3. ユーザーの一覧で **[候補]** をクリックします。

4. **[候補]** ユーザー アカウントのプロパティを一覧表示するウィンドウで、次を確認します。

   - **[戦略的シニア スタッフ]** グループのメンバーである (**[グループ メンバーシップ]** 内)。

   - **[Enterprise Mobility + Security E5]** と **[Office 365 Enterprise E5]** のライセンスが割り当てられている (**[製品ライセンス]** 内)。

5. **[候補]** ユーザー アカウントのウィンドウを閉じます。

## <a name="record-values-for-future-reference"></a>将来の参考のために値を記録する

この開発/テスト環境で Office 365 と EMS の試用版サブスクリプションを使用するために、これらの値を記録します。

- 試用版サブスクリプションの組織名 ![下線](../../media/Common-Images/TableLine.png)

  たとえば、試用版サブスクリプションのドメイン名が contoso.onmicrosoft.com である場合、組織名は「contoso」です。

- グローバル管理者名: ![下線](../../media/Common-Images/TableLine.png).onmicrosoft.com

  このアカウントのパスワードや、その他のユーザー アカウントの共通のパスワードを安全な場所に記録します。

## <a name="next-step"></a>次の手順

[Create team sites in a political campaign dev/test environment](create-team-sites-in-a-political-campaign-dev-test-environment.md) を使用して、この開発/テスト環境で 4 つの異なる種類の SharePoint Online チーム サイトを作成します。

## <a name="see-also"></a>関連項目

[選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)

[選挙運動用の開発/テスト環境でチーム サイトを作成する](create-team-sites-in-a-political-campaign-dev-test-environment.md)

[クラウド導入のテスト ラボ ガイド (TLG)](../../enterprise/cloud-adoption-test-lab-guides-tlgs.md)

[クラウド導入およびハイブリッド ソリューション](/office365/enterprise/cloud-adoption-and-hybrid-solutions)