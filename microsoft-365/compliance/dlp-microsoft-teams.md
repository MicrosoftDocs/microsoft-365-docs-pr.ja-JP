---
title: データ損失防止と Microsoft Teams
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: これで、DLP ポリシーを Microsoft Teams のチャットおよびチャネルに適用できるようになります。 機能の詳細については、この記事を参照してください。
ms.openlocfilehash: 4903056a9a7e7ae74a8ada52bd491f2b8efe771e
ms.sourcegitcommit: d859ea36152c227699c1786ef08cda5805ecf7db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604361"
---
# <a name="data-loss-prevention-and-microsoft-teams"></a>データ損失防止と Microsoft Teams

> [!NOTE]
> データ損失防止機能は、最近、Office 365 E5/A5、Microsoft 365 E5/a5、Microsoft 365 情報保護とガバナンス、または Office 365 Advanced コンプライアンスのユーザー向けに、Microsoft Teams のチャットおよびチャネルメッセージに追加されました。 Office 365 と Microsoft 365 E3 には、SharePoint Online、OneDrive、および Exchange Online の DLP 保護が含まれています。 これには、Teams が SharePoint Online と OneDrive を使用してファイルを共有するため、Teams によって共有されるファイルも含まれます。
Teams チャットで DLP 保護をサポートするには、E5 が必要です。
ライセンス要件の詳細については、「[Microsoft 365 テナントレベル サービスのライセンスに関するガイダンス](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance)」を参照してください。

## <a name="overview-of-dlp-for-microsoft-teams"></a>Microsoft Teams の DLP の概要

最近では、 [データ損失防止](data-loss-prevention-policies.md) (DLP) 機能が、 **プライベートチャネルメッセージを含む** Microsoft Teams のチャットおよびチャネルメッセージを含むように拡張されました。


組織に DLP がある場合は、Microsoft Teams チャネルまたはチャットセッションで機密情報を共有できないようにするポリシーを定義できるようになりました。 この保護がどのように機能するかについて、いくつかの例を示します。

- **例 1: メッセージ内の機密情報を保護** します。 チームのチャットまたはチャネル内の機密情報をゲスト (外部ユーザー) と共有しようとするユーザーがいるとします。 これを防止するように定義された DLP ポリシーがある場合、外部ユーザーに送信される機密情報を含むメッセージは削除されます。 これは、DLP ポリシーがどのように構成されているかに応じて、数秒で自動的に発生します。

    > [!NOTE]
    > Microsoft Teams の DLP では、次のものを持つ Microsoft Teams ユーザーとの共有時に機密コンテンツがブロックされます。<br/>- teams およびチャネルでの[ゲストアクセス](https://docs.microsoft.com/MicrosoftTeams/guest-access)。や<br/>- 会議およびチャットセッションでの[外部アクセス](https://docs.microsoft.com/MicrosoftTeams/manage-external-access)。 <p>外部チャットセッションの DLP は、送信者と受信者の両方が Teams のみのモードで、 [Microsoft teams のネイティブフェデレーション](https://docs.microsoft.com/microsoftteams/manage-external-access)を使用している場合にのみ機能します。 Teams の DLP では、Skype for Business または非ネイティブのフェデレーションチャットセッションによる [相互運用](https://docs.microsoft.com/microsoftteams/teams-and-skypeforbusiness-coexistence-and-interoperability#interoperability-of-teams-and-skype-for-business) のメッセージはブロックされません。

- **例 2: ドキュメント内の機密情報を保護** します。 Microsoft Teams チャネルまたはチャットのゲストでドキュメントを共有しようとした場合に、ドキュメントに機密情報が含まれているとします。 これを防止するように定義された DLP ポリシーがある場合、ドキュメントはそれらのユーザーに対して開くことができません。 この場合、DLP ポリシーには、保護を設定するために SharePoint と OneDrive を含める必要があることに注意してください。 (これは Microsoft Teams に表示される SharePoint の DLP の例であり、ユーザーは office 365 DLP (Office 365 E3 に含まれています) のライセンスが必要ですが、ユーザーに Office 365 Advanced コンプライアンスのライセンスを付与する必要はありません。)

## <a name="policy-tips-help-educate-users"></a>ユーザーを教育するためのポリシーヒント

[Exchange、outlook、outlook on the web](data-loss-prevention-policies.md#policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web)、 [SharePoint Online、OneDrive for business サイト](data-loss-prevention-policies.md#policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites)、および[OFFICE デスクトップクライアント](data-loss-prevention-policies.md#policy-evaluation-in-the-office-desktop-programs)での dlp の動作と同様に、操作が dlp ポリシーと競合すると、ポリシーヒントが表示されます。 ポリシーヒントの例を次に示します。

![Teams でブロックされたメッセージ通知](../media/dlp-teams-blockedmessage-notification.png)

この場合、送信者は Microsoft Teams チャネルでソーシャルセキュリティ番号を共有しようとしました。 [ **何を行いますか?** ] リンクは、問題を解決するために送信者に対してオプションを提供するダイアログボックスを開きます。 この場合、送信者はポリシーを上書きするか、管理者に通知してそれを確認して解決するかを選択することに注意してください。

![ブロックされたメッセージを解決するためのオプション](../media/dlp-teams-blockedmessage-possibleactions.png)

組織では、ユーザーが DLP ポリシーを上書きすることを許可するかどうかを選択できます。 また、DLP ポリシーを構成するときは、既定のポリシーヒントを使用するか、組織の [ポリシーヒントをカスタマイズ](#to-customize-policy-tips) できます。

この例では、送信者が Teams チャネルで社会保障番号を共有している場合、受信者は次のように表示されています。

![ブロックされたメッセージ](../media/dlp-teams-blockedmessage-notification-to-user.png)

[ **ポップヒント]** リンクによって、メッセージがブロックされた理由を説明する DLP ポリシーに関する [記事](data-loss-prevention-policies.md) が開きます。

### <a name="to-customize-policy-tips"></a>ポリシーヒントをカスタマイズするには

このタスクを実行するには、DLP ポリシーを編集する権限を持つ役割が割り当てられている必要があります。 詳細については、「[アクセス許可](data-loss-prevention-policies.md#permissions)」を参照してください。

1. セキュリティ & コンプライアンスセンター () に移動し、 [https://protection.office.com](https://protection.office.com) サインインします。

2. [**データ損失防止** ポリシー] を選択し  >  **Policy** ます。

3. ポリシーを選択し、[ **ポリシー設定**] の横にある [ **編集**] を選択します。

4. 新しいルールを作成するか、ポリシーの既存のルールを編集します。<br/>![ポリシーのルールを編集する](../media/dlp-teams-editrule.png)<br/>

5. [ **ユーザー通知** ] タブで、[ **電子メールテキストのカスタマイズ** ] または [ **ポリシーヒントテキストオプションのカスタマイズ** ] を選択します。<br/>![ユーザー通知とポリシーヒントをカスタマイズする](../media/dlp-teams-editrule-usernotifications.png)<br/>  

6. 電子メール通知やポリシーヒントに使用するテキストを指定し、[ **保存**] を選択します。

7. [ **ポリシー設定** ] タブで、[ **保存**] を選択します。

変更がデータセンターを経由して、ユーザーアカウントに同期されるまで約1時間の時間を確保します。
 <!-- why are these syncing to user accounts? -->
## <a name="add-microsoft-teams-as-a-location-to-existing-dlp-policies"></a>既存の DLP ポリシーに Microsoft Teams を場所として追加する

このタスクを実行するには、DLP ポリシーを編集する権限を持つ役割が割り当てられている必要があります。 詳細については、「[アクセス許可](data-loss-prevention-policies.md#permissions)」を参照してください。

1. セキュリティ & コンプライアンスセンター () に移動し、 [https://protection.office.com](https://protection.office.com) サインインします。

2. [**データ損失防止** ポリシー] を選択し  >  **Policy** ます。

3. ポリシーを選択し、[ **場所**] で値を確認します。 **Teams のチャットおよびチャネルメッセージ** が表示される場合は、すべて設定されています。 表示しない場合は、[ **編集**] をクリックします。<br/>![既存のポリシーの場所](../media/dlp-teams-editexistingpolicy.png)<br/>

4. [ **状態** ] 列で、 **Teams のチャットおよびチャネルメッセージ** のポリシーをオンにします。<br/>![Teams のチャットおよびチャネルの DLP](../media/dlp-teams-addteamschatschannels.png)<br/>

5. すべてのアカウントの既定の設定をそのまま使用するか、または含めるアカウントまたは除外するアカウントを指定します。

6. **[保存]** をクリックします。

変更がデータセンターを経由して、ユーザーアカウントに同期されるまで約1時間の時間を確保します。
<!-- again, why user accounts? -->
## <a name="define-a-new-dlp-policy-for-microsoft-teams"></a>Microsoft Teams の新しい DLP ポリシーを定義する

このタスクを実行するには、DLP ポリシーを編集する権限を持つ役割が割り当てられている必要があります。 詳細については、「[アクセス許可](data-loss-prevention-policies.md#permissions)」を参照してください。

1. セキュリティ & コンプライアンスセンター () に移動し、 [https://protection.office.com](https://protection.office.com) サインインします。

2. [**データ損失防止** ポリシー] を選択して  >  **Policy**  >  **、ポリシーを作成** します。

3. [テンプレート](data-loss-prevention-policies.md#dlp-policy-templates)を選択し、[**次へ**] を選択します。<br/>この例では、米国の個人を特定できる情報データテンプレートを選択しました。<br/>![DLP ポリシーのプライバシーテンプレート](../media/dlp-teams-createnewpolicy-template.png)<br/>

4. [ **ポリシーに名前** をつける] タブで、ポリシーの名前と説明を指定し、[ **次へ**] を選択します。

5. [ **場所の選択** ] タブで、すべての場所の既定の設定をそのまま使用するか、[特定の **場所を選択** する] を選択して、[ **次へ**] を選択します。<br/>特定の場所を選択した場合は、DLP ポリシーに対してそれらの場所を選択し、[ **次へ**] を選択します。<br/>![DLP ポリシーの場所](../media/dlp-teams-selectlocationsnewpolicy.png)<br/>
    > [!NOTE]
    > 機密情報が含まれるドキュメントが Teams で不適切に共有されないようにするには、 **SharePoint サイト** と **OneDrive アカウント** が有効になっていることを、 **teams のチャットおよびチャネルメッセージ** と一緒に確認します。

<br/>

6. [ **ポリシー設定** ] タブの [ **保護するコンテンツの種類をカスタマイズ** する] で、既定の簡易設定をそのまま使用するか、[ **詳細設定**] を選択して [ **次へ**] を選択します。 [詳細設定] を選択した場合は、ポリシーのルールを作成または編集することができます。 (詳細については、「 [Simple settings](data-loss-prevention-policies.md#simple-settings-vs-advanced-settings)」と「advanced settings」を参照してください)。

7.  [ **ポリシー設定** ] タブの [ **機密情報が検出された場合に実行** する操作] で、設定を確認します。 (既定の [ポリシーヒントと電子メール通知](use-notifications-and-policy-tips.md)を保持するか、カスタマイズするかを選択できます)。<br/>![ヒントと通知を含む DLP ポリシー設定](../media/dlp-teams-policysettings-tipsemails.png)<br/>設定の確認または編集が完了したら、[ **次へ**] を選択します。

8. [ **ポリシー設定** ] タブの [ **ポリシーをオンにするか、または最初にテストしますか?**] で、ポリシーをオンにするか、 [最初にテスト](data-loss-prevention-policies.md#roll-out-dlp-policies-gradually-with-test-mode)するか、または今すぐ有効にしないかを選択し、[ **次へ**] を選択します。<br/>![ポリシーを有効にするかどうかを指定する](../media/dlp-teams-policysettings-turnonnow.png)<br/>

9. [ **設定の確認** ] タブで、新しいポリシーの設定を確認します。 [ **編集** ] を選択して変更を加えます。 完了したら、[ **作成**] を選択します。

新しいポリシーがデータセンターを使用して動作し、ユーザーアカウントに同期できるようになるまで約1時間かかります。

## <a name="prevent-external-access-to-sensitive-documents"></a>機密ドキュメントへの外部アクセスを禁止する

SharePoint または Teams から外部のゲストが、機密情報を含む SharePoint ドキュメントに既定でアクセスできないようにするには、次のいずれかを選択します。

- ドキュメントが DLP スキャンまで確実に保護され、[新しいファイルを既定で重要なものとし](https://docs.microsoft.com/sharepoint/sensitive-by-default)てマークすることにより、安全であるとマークされるようにすることができます。
- 推奨される DLP ポリシー構造
    - **条件**
        - コンテンツには、次の機密情報の種類のいずれかが含まれています。 [適用するすべてを選択する]
        - コンテンツは Microsoft 365 から、自分の組織外のユーザーと共有される
        <br/>![機密コンテンツの外部共有を検出する DLP 条件](../media/dlp-teams-external-sharing/external-condition.png)<br/>


    - **アクション**
        - 外部ユーザーのコンテンツへのアクセスを制限する
        - ユーザーに電子メールとポリシーヒントを通知する
        - インシデントレポートを管理者に送信する    
        <br/>![機密コンテンツの外部共有をブロックする DLP アクション](../media/dlp-teams-external-sharing/external-action.png)<br/>

次に示す、外部ゲストの機密情報を含む SharePoint のドキュメントを共有しようとした場合の DLP ポリシー。
<br/>![外部共有のブロック](../media/dlp-teams-external-sharing/external-sharing-blocked.png)<br/>


[外部ブロック] を持つ Teams でゲストがドキュメントを開こうとした場合の DLP ポリシーの動作:
<br/>![外部アクセスのブロック](../media/dlp-teams-external-sharing/external-access-blocked.png)<br/>

## <a name="related-articles"></a>関連記事

[DLP ポリシーの作成、テスト、調整](create-test-tune-dlp-policy.md)

[メール通知を送信して、DLP ポリシーのヒントを表示する](use-notifications-and-policy-tips.md)
