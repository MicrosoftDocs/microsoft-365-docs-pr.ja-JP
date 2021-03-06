---
title: Microsoft Defender のユーザー タグ (Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 04/21/2021
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: 管理者は、プラン 2 の Microsoft Defender でユーザー タグを持つユーザーの特定のグループOffice 365学習できます。 タグ フィルターは、Microsoft Defender のアラート、レポート、および調査で、タグ付けされたユーザーをすばやく識別Office 365に使用できます。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3ac53891e0eb106ab3681251cc4cb8c969b51f8a
ms.sourcegitcommit: cd55fe6abe25b1e4f5fbe8295d3a99aebd97ce66
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2021
ms.locfileid: "53083118"
---
# <a name="user-tags-in-microsoft-defender-for-office-365"></a>Microsoft Defender のユーザー タグ (Office 365

> [!NOTE]
> ユーザー タグ機能はプレビュー機能であり、すべてのユーザーが利用できるとは言え、変更される可能性があります。 リリース スケジュールの詳細については、次のロードマップ[をMicrosoft 365してください](https://www.microsoft.com/microsoft-365/roadmap)。

ユーザー タグは、Microsoft [Defender](defender-for-office-365.md)のユーザーの特定のグループの識別子Office 365。 ユーザー タグには次の 2 種類があります。

- **システム タグ**: 現在、 [優先度アカウント](../../admin/setup/priority-accounts.md) はシステム タグの唯一の種類です。
- **カスタム タグ**: これらのユーザー タグは、自分で作成します。

組織に Defender for Office 365 プラン 2 (サブスクリプションまたはアドオンとして含まれる) がある場合は、優先度アカウント タグの使用に加えて、カスタム ユーザー タグを作成できます。

> [!NOTE]
> 現時点では、メールボックス ユーザーにのみユーザー タグを適用できます。

システム タグまたはカスタム タグをユーザーに適用した後、これらのタグをアラート、レポート、調査のフィルターとして使用できます。

- [Alerts](alerts.md)
- [カスタムアラート ポリシー](../../compliance/alert-policies.md#viewing-alerts)
- [脅威エクスプローラーとリアルタイム検出](threat-explorer.md)
- [[メール エンティティ] ページ](mdo-email-entity-page.md#other-innovations)
- [脅威保護の状態レポート](view-email-security-reports.md#threat-protection-status-report)
- [キャンペーン ビュー](campaigns.md)
- 優先度アカウントの場合は、管理センター [](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report) (EAC) の [優先アカウントの電子メールExchangeレポートを使用できます。

この記事では、ポータルでユーザー タグを構成するMicrosoft 365 Defenderします。 ユーザー タグを管理するためのMicrosoft 365 Defenderポータルにはコマンドレットはありません。

影響の大きなユーザー アカウントを保護するための戦略の一部であるユーザー タグの詳細については、「セキュリティに関する推奨事項」を参照[Microsoft 365。](security-recommendations-for-priority-accounts.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a>はじめに把握しておくべき情報

- <https://security.microsoft.com/> で Microsoft 365 Defender ポータルを開きます。 [ユーザー タグ] ページに **直接移動するには** 、を開きます <https://security.microsoft.com/securitysettings/userTags> 。

- この記事の手順を実行するには、Microsoft 365 Defenderポータルでアクセス許可を割り当てる必要があります。
  - ユーザー タグを作成、変更、および削除するには、組織の管理役割グループまたはセキュリティ管理者役割グループ **のメンバーである** 必要があります。
  - 既存のユーザー タグのメンバーを追加および削除するには、組織の管理、セキュリティ管理者、またはセキュリティオペレーターの役割グループ **のメンバーである** 必要があります。
  - ユーザー タグへの読み取り専用アクセスでは、グローバル リーダーまたはセキュリティリーダーの役割グループ **のメンバーである** 必要があります。

  詳細については、「[Microsoft 365 Defender ポータルのアクセス許可](permissions-microsoft-365-security-center.md)」を参照してください。

  > [!NOTE]
  >
  > - Microsoft 365 管理センター の対応する Azure Active Directory ロールにユーザーを追加すると、Microsoft 365 Defender ポータルで必要なアクセス許可と、Microsoft 365の他の機能に対するアクセス許可が付与されます。 詳細については、[「管理者の役割について」](../../admin/add-users/about-admin-roles.md) を参照してください。
  >
  > - ユーザー タグ管理は、タグ リーダーと **タグ マネージャー** の **役割によって制御** されます。

- また、優先度アカウントを管理および監視することもできます。Microsoft 365 管理センター。 手順については、「優先度アカウントの [管理と監視」を参照してください](../../admin/setup/priority-accounts.md)。

- 特権アカウント (管理者アカウント) _のセキュリティ保護の詳細については_ 、このトピックを [参照してください](/azure/architecture/framework/security/critical-impact-accounts)。

## <a name="use-the-microsoft-365-defender-portal-to-create-user-tags"></a>ユーザー タグを作成Microsoft 365 Defenderポータルを使用する

1. ポータルで、[Microsoft 365 Defenderグループのユーザー タグ設定 \> **メール&] に** \> **移動します**。

2. [ユーザー タグ **] ページで** 、[タグの作成] ![ アイコン [タグの ](../../media/m365-cc-sc-create-icon.png) **作成] をクリックします**。

3. タグ **の作成ウィザード** が新しいフライアウトで開きます。 [タグの **定義] ページ** で、次の設定を構成します。
   - **名前**: タグの一意でわかりやすい名前を入力します。 これは、表示および使用する値です。 タグを作成した後は、名前を変更できない点に注意してください。
   - **説明**: タグのオプションの説明を入力します。

   完了したら、**[次へ]** をクリックします。

4. [メンバーの **割り当て** ] ページで、次のいずれかの手順を実行します。
   - [メンバー ![ の追加] アイコン [ ](../../media/m365-cc-sc-create-icon.png) **メンバーの追加] をクリックします**。 表示されるフライアウトで、次の手順を実行して個々のユーザーまたはグループを追加します。
     - ボックス内をクリックし、リストをスクロールしてユーザーまたはグループを選択します。
     - ボックス内をクリックし、入力を開始してリストをフィルター処理し、ユーザーまたはグループを選択します。
     - 追加の値を追加するには、ボックス内の空の領域をクリックします。
     - 個々のエントリを削除するには、 ![[エントリの削除] アイコン](../../media/m365-cc-sc-remove-selection-icon.png) ボックス内のエントリの横に表示されます。
     - すべてのエントリを削除するには、ボックスの下にある [選択された nn ユーザーと nn グループ] アイテムの [エントリの削除 ![ ](../../media/m365-cc-sc-remove-selection-icon.png) ] アイコンをクリックします。 

     完了したら、**[追加]** をクリックします。

     [メンバーの割 **り当て** ] ページに戻って、エントリの横にある [削除] アイコンをクリックしてエントリ ![ ](../../media/m365-cc-sc-delete-icon.png) を削除することもできます。

   - [ **インポート] を** クリックして、ユーザーまたはグループの電子メール アドレスを含むテキスト ファイルを選択します。 テキスト ファイルに 1 行に 1 つのエントリが含まれている必要があります。

   完了したら、**[次へ]** をクリックします。

5. 表示される **[タグの確認** ] ページで、設定を確認します。 各セクションで **[編集]** を選択して、そのセクション内の設定を変更することができます。 または、**[戻る]** をクリックするか、ウィザードで特定のページを選択します。

   完了したら、[送信] をクリック **し**、[完了] を **クリックします**。

## <a name="use-the-microsoft-365-defender-portal-to-view-user-tags"></a>ユーザー タグを表示Microsoft 365 Defenderポータルを使用する

1. ポータルで、[Microsoft 365 Defenderグループのユーザー タグ設定 \> **メール&] に** \> **移動します**。

2. [ユーザー タグ **] ページ** では、ユーザー タグの一覧に次のプロパティが表示されます。

   - **タグ**: ユーザー タグの名前。 これには、組み込みの Priority アカウント システム **タグが** 含まれます。
   - **適用 :** メンバーの数
   - **最終更新日時**
   - **作成日時**

3. 名前をクリックしてユーザー タグを選択すると、詳細がフライアウトに表示されます。

## <a name="use-the-microsoft-365-defender-portal-to-modify-user-tags"></a>ユーザー タグを変更Microsoft 365 Defenderポータルを使用する

1. ポータルで、[Microsoft 365 Defenderグループのユーザー タグ設定 \> **メール&] に** \> **移動します**。

2. [ユーザー タグ **] ページで** 、リストからユーザー タグを選択し、[タグの編集] アイコン [タグの編集] ![ ](../../media/m365-cc-sc-edit-icon.png) **をクリックします**。

3. 表示される詳細フライアウトでは、この記事の「Microsoft 365 Defender ポータルを使用してユーザー タグ[](#use-the-microsoft-365-defender-portal-to-create-user-tags)を作成する」セクションで説明したように、同じウィザードと設定を使用できます。

   **注**:

   - [ **タグの定義** ] ページは組み込みの **Priority アカウント** システム タグでは使用できないので、このタグの名前を変更したり、説明を変更したりすることはできません。
   - カスタム タグの名前は変更できますが、説明は変更できます。

## <a name="use-the-microsoft-365-defender-portal-to-remove-user-tags"></a>ユーザー タグを削除Microsoft 365 Defenderポータルを使用する

> [!NOTE]
> 組み込みの Priority アカウント システム タグ **は** 削除できません。

1. ポータルで、[Microsoft 365 Defenderグループのユーザー タグ設定 \> **メール&] に** \> **移動します**。

2. [ユーザー タグ **] ページ** で、リストからユーザー タグを選択し、[タグの削除] アイコン [タグの削除] ![ ](../../media/m365-cc-sc-delete-icon.png) **をクリックします**。

3. 表示される確認ダイアログで警告を読み、[はい、削除] **をクリックします**。
