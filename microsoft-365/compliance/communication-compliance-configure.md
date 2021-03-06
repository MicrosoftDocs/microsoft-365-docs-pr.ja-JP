---
title: コミュニケーション コンプライアンスの使用を開始する
description: 確認のためにユーザー通信を構成する通信コンプライアンス ポリシーを設定します。
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: f099d7bd180843530d23d0bbcee89dc8ae35cdbb
ms.sourcegitcommit: a4c93a4c7d7db08fe3b032b58d5c7dbbb9476e90
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2021
ms.locfileid: "53256737"
---
# <a name="get-started-with-communication-compliance"></a>通信コンプライアンスを使用して開始する

コミュニケーション コンプライアンス ポリシーを使用して、内部または外部のレビュー担当者によるユーザー通信の審査を識別します。 通信コンプライアンス ポリシーが組織内の通信の監視に役立つ方法の詳細については、「コミュニケーション コンプライアンス ポリシー」を参照[Microsoft 365。](communication-compliance.md) Microsoft Teams、Exchange Online、および Yammer の通信で不快な言語を監視する通信コンプライアンス ポリシーを Contoso が迅速に構成した方法を確認する場合は、このケース スタディを[参照してください](communication-compliance-case-study.md)。

## <a name="subscriptions-and-licensing"></a>サブスクリプションとライセンス

通信コンプライアンスを開始する前に、サブスクリプションとMicrosoft 365[を](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans)確認する必要があります。 通信コンプライアンスにアクセスして使用するには、組織に次のいずれかのサブスクリプションまたはアドオンが必要です。

- Microsoft 365 E5 サブスクリプション (有料または試用版)
- Microsoft 365 E5 コンプライアンス アドオンが含まれている Microsoft 365 E3 サブスクリプション。
- Microsoft 365 E5 インサイダー リスク管理アドオンが含まれている Microsoft 365 E3 サブスクリプション。
- Microsoft 365 A5 サブスクリプション (有料または試用版)
- Microsoft 365 A5 コンプライアンス アドオンが含まれている Microsoft 365 A3 サブスクリプション。
- Microsoft 365 A5 インサイダー リスク管理アドオンが含まれている Microsoft 365 A3 サブスクリプション。
- Microsoft 365 G5 サブスクリプション (有料または試用版)
- Microsoft 365 G5 コンプライアンス アドオンが含まれている Microsoft 365 G5 サブスクリプション。
- Microsoft 365 G5 インサイダー リスク管理アドオンが含まれている Microsoft 365 G5 サブスクリプション。
- Office 365 Enterprise E5 サブスクリプション (有料または試用版)
- Office 365 A5サブスクリプション (有料版または試用版)
- Office 365 Advanced Compliance アドオンが含まれている Office 365 Enterprise E3 サブスクリプション (新しいサブスクリプションでは利用できなくなりました。注を参照してください)

通信コンプライアンス ポリシーに含まれるユーザーには、上記のいずれかのライセンスが割り当てられている必要があります。

> [!IMPORTANT]
> Office 365 Advanced Complianceスタンドアロン サブスクリプションとして販売されなくなりました。 現在のサブスクリプションの有効期限が切れると、お客様は上記のサブスクリプションの 1 つ (同じコンプライアンス機能または追加のコンプライアンス機能を含む) に移行する必要があります。

既存の Office 365 Enterprise E5 プランをお持ちで、通信コンプライアンスを試す場合は、Microsoft 365 を既存のサブスクリプションに追加するか[、Office 365 Enterprise](/office365/admin/try-or-buy-microsoft-365) E5 の試用版にサインアップできます。 [](https://www.microsoft.com/microsoft-365/enterprise)

## <a name="step-1-required-enable-permissions-for-communication-compliance"></a>手順 1 (必須): 通信コンプライアンスのアクセス許可を有効にする

> [!IMPORTANT]
> 既定では、グローバル管理者は通信コンプライアンス機能にアクセスできます。 この手順で割り当てられた役割は、通信コンプライアンス機能にアクセスする前に必要です。 役割グループを構成した後、役割グループのアクセス許可が組織全体の割り当てられたユーザーに適用されるのに最大 30 分かかる場合があります。

通信コンプライアンス機能を管理するためのアクセス許可を構成するために使用される 5 つの役割グループがあります。 Microsoft 365 コンプライアンス センターのメニュー オプションとして通信コンプライアンスを使用し、これらの構成手順を続行するには、通信コンプライアンスまたは通信コンプライアンス *管理者* の役割グループに割り当てる必要があります。 初期構成後に通信コンプライアンス機能にアクセスして管理するには、ユーザーが少なくとも 1 つの通信コンプライアンス役割グループのメンバーである必要があります。

通信ポリシーとアラートの管理方法に応じて、ユーザーを特定の役割グループに割り当てる必要があります。 通信コンプライアンス機能の異なる領域を管理するために、さまざまなコンプライアンス責任を持つユーザーを特定の役割グループに割り当てるオプションがあります。 または、指定された管理者、アナリスト、調査者、閲覧者のすべてのユーザー アカウントをコミュニケーション コンプライアンス役割グループに割 *り当てる* 場合があります。 コンプライアンス管理要件に最適な 1 つの役割グループまたは複数の役割グループを使用します。

通信コンプライアンスを構成する場合は、次の役割グループ オプションから選択します。

| 役割 | ロール権限 |
|:-----|:-----|
| **通信コンプライアンス** | この役割グループを使用して、1 つのグループで組織の通信コンプライアンスを管理します。 指定された管理者、アナリスト、調査者、閲覧者のすべてのユーザー アカウントを追加することで、1 つのグループで通信コンプライアンスのアクセス許可を構成できます。 この役割グループには、すべての通信コンプライアンスアクセス許可の役割が含まれる。 この構成は、通信コンプライアンスを迅速に開始する最も簡単な方法であり、個別のユーザー グループに対して個別のアクセス許可を定義する必要がない組織に適しています。 |
| **コミュニケーション コンプライアンスの管理者** | この役割グループを使用して、通信コンプライアンスを最初に構成し、後で通信コンプライアンス管理者を定義されたグループに分離します。 この役割グループに割り当てられたユーザーは、通信コンプライアンス ポリシー、グローバル設定、および役割グループの割り当てを作成、読み取り、更新、および削除できます。 この役割グループに割り当てられたユーザーは、メッセージ通知を表示できません。 |
| **コミュニケーション コンプライアンス アナリスト** | コミュニケーション コンプライアンス アナリストとして機能するユーザーにアクセス許可を割り当てるには、このグループを使用します。 この役割グループに割り当てられたユーザーは、レビュー担当者として割り当てられているポリシーを表示したり、メッセージ メタデータ (メッセージ コンテンツではなく) を表示したり、追加のレビュー担当者にエスカレートしたり、ユーザーに通知を送信したりできます。 アナリストは保留中のアラートを解決できません。 |
| **コミュニケーション コンプライアンス調査員** | このグループを使用して、通信コンプライアンス調査員として機能するユーザーにアクセス許可を割り当てる。 この役割グループに割り当てられたユーザーは、メッセージのメタデータとコンテンツを表示し、追加のレビュー担当者にエスカレートし、Advanced eDiscovery ケースにエスカレートし、ユーザーに通知を送信し、アラートを解決できます。 |
| **コミュニケーション コンプライアンスの閲覧者** | このグループを使用して、通信レポートを管理するユーザーにアクセス許可を割り当てる。 この役割グループに割り当てられたユーザーは、通信コンプライアンス ホーム ページのすべてのレポート ウィジェットにアクセスし、すべての通信コンプライアンス レポートを表示できます。 |

### <a name="option-1-assign-all-compliance-users-to-the-communication-compliance-role-group"></a>オプション 1: すべてのコンプライアンス ユーザーを [コミュニケーション コンプライアンス] 役割グループに割り当てる

1. 組織の [https://compliance.microsoft.com/permissions](https://compliance.microsoft.com/permissions) 管理者アカウントの資格情報を使用してサインインMicrosoft 365します。

2. セキュリティ コンプライアンス センター &amp; で、[アクセス許可] **に移動します**。 リンクを選択して、ロールを表示および管理Office 365。

3. [通信コンプライアンス *] 役割グループを* 選択し、[役割グループの **編集] を選択します**。

4. 左側 **のナビゲーション ウィンドウから** [メンバーの選択] を選択し、[編集] を **選択します**。

5. [ **追加]** を選択し、[通信コンプライアンス] 役割グループに追加するすべてのユーザーのチェック *ボックスを* オンにします。

6. [**追加**] を選択し、[**完了**] を選択します。

7. [保存 **] を** 選択して、ユーザーを役割グループに追加します。 [閉 **じる] を** 選択して手順を完了します。

### <a name="option-2-assign-users-to-specific-communication-compliance-role-groups"></a>オプション 2: 特定の通信コンプライアンス役割グループにユーザーを割り当てる

このオプションを使用して、ユーザーを特定の役割グループに割り当て、組織内の異なるユーザー間で通信コンプライアンス アクセスと責任をセグメント化します。

1. 組織の [https://compliance.microsoft.com/permissions](https://compliance.microsoft.com/permissions) 管理者アカウントの資格情報を使用してサインインMicrosoft 365します。

2. セキュリティ コンプライアンス センター &amp; で、[アクセス許可] **に移動します**。 リンクを選択して、ロールを表示および管理Office 365。

3. 通信コンプライアンス役割グループのいずれかを選択し、[役割グループの編集 **] を選択します**。

4. 左側 **のナビゲーション ウィンドウから** [メンバーの選択] を選択し、[編集] を **選択します**。

5. [ **追加] を** 選択し、役割グループに追加するすべてのユーザーのチェック ボックスをオンにします。

6. [**追加**] を選択し、[**完了**] を選択します。

7. [保存 **] を** 選択して、ユーザーを役割グループに追加します。

8. 次の通信コンプライアンス役割グループを選択し、必要な役割グループごとに手順 4 ~ 7 を繰り返します。

9. [閉 **じる] を** 選択して手順を完了します。

役割グループとアクセス許可の詳細については、「[Permissions in the Compliance Center (コンプライアンス センターのアクセス許可)](../security/office-365-security/protect-against-threats.md)」を参照してください。 

## <a name="step-2-required-enable-the-audit-log"></a>手順 2 (必須): 監査ログを有効にする

通信コンプライアンスには、警告を表示し、レビュー担当者が行った修復処置を追跡するための監査ログが必要です。 監査ログは、定義済みの組織ポリシーに関連付けられているすべてのアクティビティの概要です。また、コミュニケーション コンプライアンス ポリシーに変更があった場合はいつでもその概要を示します。

監査を有効にする手順については、「監査ログ検索を有効またはオフにする」 [を参照してください](turn-audit-log-search-on-or-off.md)。 監査を有効にすると、監査ログの準備中で、準備が完了してから数時間で検索を実行できるというメッセージが表示されます。 このアクションを行う必要があるのは 1 回だけです。 監査ログの使用の詳細については、「監査ログの検索 [」を参照してください](search-the-audit-log-in-security-and-compliance.md)。

## <a name="step-3-optional-set-up-groups-for-communication-compliance"></a>手順 3 (オプション): 通信コンプライアンス用にグループを設定する

 コミュニケーション コンプライアンス ポリシーを作成するときには、コミュニケーションが確認されるユーザーおよびレビューを実行するユーザーを定義します。 ポリシーでは、メール アドレスを使って、個人または複数人のグループを指定します。 設定を簡単にするために、コミュニケーションを確認されるユーザーのグループと、それらのコミュニケーションをレビューするユーザーのグループを作成することもできます。 グループを使用している場合は、複数必要になる場合があります。 たとえば、2 つの異なるユーザー グループ間の通信を監視する場合や、監視対象ではないグループを指定する場合などです。

次のグラフを使用して、コミュニケーション コンプライアンス ポリシー用に組織内のグループを構成できます。

| **ポリシー メンバー** | **サポートされているグループ** | **サポートされていないグループ** |
|:-----|:-----|:-----|
|監督対象ユーザー <br> 除外されたユーザー | 配布グループ <br> Microsoft 365 グループ | 動的配布グループ <br> 入れ子になった配布グループ <br> メールが有効なセキュリティ グループ <br> Microsoft 365メンバーシップを持つグループ |
| レビュー担当者 | なし | 配布グループ <br> 動的配布グループ <br> 入れ子になった配布グループ <br> メールが有効なセキュリティ グループ |

ポリシーで配布グループを割り当てると、ポリシーは配布グループ内Teamsのすべての電子メールとチャットを監視します。 ポリシーで Microsoft 365 グループを割り当てると、ポリシーは、各グループ メンバーが受信した個々の電子メールやチャットではなく、そのグループに送信された電子メールと Teams チャットを監視します。

Exchange オンプレミス展開または外部メール プロバイダーを持つ組織で、ユーザーの Microsoft Teams チャットを監視する場合は、監視するオンプレミスまたは外部メールボックスを持つユーザーの配布グループを作成する必要があります。 これらの手順の後半では、ポリシー ウィザードでこの配布グループを **[監視** 対象ユーザーとグループ] の選択として割り当てる必要があります。 クラウドベースのストレージと Teams のオンプレミス ユーザーのサポートを有効にするための要件と制限の詳細については、「オンプレミス ユーザー向け[Teams](search-cloud-based-mailboxes-for-on-premises-users.md)チャット データの検索」を参照してください。

大規模な企業組織の監督対象ユーザーを管理するには、大規模なグループ全体のユーザーすべてを監視する必要がある場合があります。 PowerShell を使用して、割り当てられたグループのグローバル通信コンプライアンス ポリシーの配布グループを構成できます。 これにより、1 つのポリシーで何千人ものユーザーを監視し、新入社員が組織に参加するに従って通信コンプライアンス ポリシーを更新できます。

1. 次のプロパティを[使用](/powershell/module/exchange/new-distributiongroup)して、グローバル通信コンプライアンス ポリシー用の専用配布グループを作成します。この配布グループは、他の目的や他のサービスOffice 365してください。

    - **MemberDepartRestriction = Closed**。 ユーザーが配布グループから自分自身を削除できないようにします。
    - **MemberJoinRestriction = Closed**。 ユーザーが配布グループに自分自身を追加できないようにします。
    - **ModerationEnabled = True**。 このグループに送信されるメッセージはすべて承認の対象であり、グループが通信コンプライアンス ポリシー構成の外部で通信するために使用されていないか確認します。

    ```PowerShell
    New-DistributionGroup -Name <your group name> -Alias <your group alias> -MemberDepartRestriction 'Closed' -MemberJoinRestriction 'Closed' -ModerationEnabled $true
    ```

2. 組織の通信[コンプライアンス ポリシー Exchange](/Exchange/recipients/mailbox-custom-attributes)ユーザーを追跡するには、未使用のカスタム 属性を選択します。

3. 定期的なスケジュールで次の PowerShell スクリプトを実行して、通信コンプライアンス ポリシーにユーザーを追加します。

    ```PowerShell
    $Mbx = (Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited -Filter {CustomAttribute9 -eq $Null})
    $i = 0
    ForEach ($M in $Mbx)
    {
      Write-Host "Adding" $M.DisplayName
      Add-DistributionGroupMember -Identity <your group name> -Member $M.DistinguishedName -ErrorAction SilentlyContinue
      Set-Mailbox -Identity $M.Alias -<your custom attribute name> SRAdded
      $i++
    }
    Write-Host $i "Mailboxes added to supervisory review distribution group."
    ```

グループの設定の詳細については、次の記事を参照してください。

- [配布グループを作成して管理する](/Exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups)
- [グループMicrosoft 365の概要](/office365/admin/create-groups/office-365-groups)

## <a name="step-4-optional-verify-your-yammer-tenant-is-in-native-mode"></a>手順 4 (オプション): テナントがネイティブ モードYammerを確認する

ネイティブ モードでは、すべての Yammer ユーザーが Azure Active Directory (Azure AD)、すべてのグループが Office 365 グループであり、すべてのファイルが SharePoint Online に保存されます。 プライベート Yammerのプライベート メッセージとコミュニティの会話で危険な会話をスキャンして識別するには、コミュニケーション コンプライアンス ポリシーのネイティブ モードにテナントがYammer。

ネイティブ モードでのアプリケーション の構成Yammer詳細については、以下を参照してください。

- [ネイティブ モードYammerの概要Microsoft 365](/yammer/configure-your-yammer-network/overview-native-mode)
- [Microsoft 365 のネイティブ モードで Yammer ネットワークを構成する](/yammer/configure-your-yammer-network/native-mode)

## <a name="step-5-required-create-a-communication-compliance-policy"></a>手順 5 (必須): 通信コンプライアンス ポリシーを作成する

> [!IMPORTANT]
> PowerShell を使用してコミュニケーション コンプライアンス ポリシーを作成し、管理することはできません。 これらのポリシーを作成および管理するには、通信コンプライアンス ソリューションのポリシー管理Microsoft 365[必要があります](https://compliance.microsoft.com/supervisoryreview)。

1. 組織の <https://compliance.microsoft.com> 管理者アカウントの資格情報を使用してサインインMicrosoft 365します。

2. [コンプライアンス] Microsoft 365 コンプライアンス センター[通信コンプライアンス **] を選択します**。

3. **[ポリシー]** タブを選択します。

4. **[ポリシーの作成]** を選択して、テンプレートから新しいポリシーを作成して構成するか、カスタム ポリシーを作成して構成します。

    ポリシーテンプレートを選択してポリシーを作成する場合は、次の方法を実行します。

    - ポリシー名を確認または更新します。 ポリシーが作成されると、ポリシー名を変更できません。

    - 除外するユーザーやグループの選択などを含めて、監督するユーザーまたはグループを選択します。 利益相反テンプレートを使用する場合は、内部通信を監視する 2 つのグループまたは 2 人のユーザーを選択します。

    - ポリシーのレビュー担当者を選択します。 レビュー担当者は個々のユーザーであり、すべてのレビュー担当者は、ユーザーに対してホストされているメールボックスExchange Online。 ここで追加されたレビュー担当者は、調査と修復ワークフローでアラートをエスカレートするときに選択できるレビュー担当者です。 レビュー担当者は、ポリシーに追加すると、ポリシーへの割り当てを通知し、レビュー プロセスに関する情報へのリンクを提供する電子メール メッセージを自動的に受信します。

    - ポリシーに適用する限られた条件フィールド (通常は機密情報の種類またはキーワード 辞書) を選択します。

    > [!NOTE]
    > 光学式文字認識[(OCR)](communication-compliance-feature-reference.md#optical-character-recognition-ocr)を有効にして、ポリシー条件に一致する印刷テキストまたは手書きテキストのメッセージに埋め込まれた画像または添付画像をスキャンする場合は、[ポリシーの条件と割合をカスタマイズする] を選択し、[評価のために画像から印刷または手書きのテキストを抽出する] を有効にするを選択します。  >   

    ポリシー ウィザードを使用してカスタム ポリシーを作成する場合は、次の手順を実行します。

    - ポリシーに名前と説明を付けます。 ポリシーを作成したら、ポリシー名は変更できません。

    - 監督するユーザーまたはグループ (組織内のすべてのユーザー、特定のユーザーとグループ、除外する他のユーザーとグループなど) を選択します。

    - ポリシーのレビュー担当者を選択します。 レビュー担当者は個々のユーザーであり、すべてのレビュー担当者は、ユーザーに対してホストされているメールボックスExchange Online。 ここで追加されたレビュー担当者は、調査と修復ワークフローでアラートをエスカレートするときに選択できるレビュー担当者です。 レビュー担当者は、ポリシーに追加すると、ポリシーへの割り当てを通知し、レビュー プロセスに関する情報へのリンクを提供する電子メール メッセージを自動的に受信します。

    - スキャンする通信チャネルを選択します (Exchange、Microsoft Teams、Yammer、Skype for Business。 Microsoft 365 でコネクタを構成した場合は、サードパーティのソースをスキャンすることも選択します。

    - 受信、送信、内部通信など、監視する通信方向を選択します。

    - 通信コンプライアンス ポリシーの条件を [定義します](communication-compliance-feature-reference.md#ConditionalSettings)。 [メッセージ アドレス]、[キーワード]、[ファイルの種類]、および [サイズの一致条件] の中から選ぶことができます。

    - 機密情報の種類を含めるかどうかを選択します。 この手順では、既定の機密情報の種類とカスタムの機密情報の種類を選択できます。 通信コンプライアンス ポリシー ウィザードで、既存のカスタム機密情報の種類またはカスタム キーワード 辞書から選択します。 必要に応じて、ウィザードを実行する前に、これらのアイテムを作成できます。 また、通信コンプライアンス ポリシー ウィザード内から新しい機密情報の種類を作成することもできます。

    - 分類子を有効にする場合に選択します。 分類子は、電子メール メッセージまたは他の種類のテキストの本文で送信または受信した不適切な言語や画像を検出できます。 次の組み込みの分類子を選択 *できます**。*    

    - 光学 [式文字認識 (OCR)](communication-compliance-feature-reference.md#optical-character-recognition-ocr) を有効にして、メッセージ内の埋め込みまたは添付された画像をスキャンして、ポリシー条件に一致する印刷または手書きのテキストを検索します。 カスタム ポリシーの場合、光学式文字認識スキャンの選択を有効にするには、ポリシーでテキスト、キーワード、分類子、または機密情報の種類に関連付けられた 1 つ以上の条件付き設定を構成する必要があります。

    - レビューする通信の割合を定義します。

    - 選択したポリシーを確認し、ポリシーを作成します。

5. テンプレートを **使用する場合は** [ポリシーの作成] を選択し、カスタム ポリシー ウィザード **を** 使用する場合は [送信] を選択します。

6. **[ポリシーが作成されました]** ページには、ポリシーがアクティブ化される時期とキャプチャされる通信に関するガイドラインが表示されます。

## <a name="step-6-optional-create-notice-templates-and-configure-user-anonymization"></a>手順 6 (オプション): 通知テンプレートを作成し、ユーザーの匿名化を構成する

関連付けられたユーザーにリマインダー通知を送信してポリシーアラートに応答するオプションを選択する場合は、組織に少なくとも 1 つの通知テンプレートを作成する必要があります。 通知テンプレート フィールドは、アラート修復プロセスの一部として送信される前に編集可能であり、通信コンプライアンス ポリシーごとにカスタマイズされた通知テンプレートを作成する必要があります。

ポリシーの一致を調査し、メッセージに対してアクションを実行するときに、表示されるユーザー名の匿名化を有効にすることもできます。

1. 組織の [https://compliance.microsoft.com](https://compliance.microsoft.com) 管理者アカウントの資格情報を使用してサインインMicrosoft 365します。

2. [コンプライアンス] Microsoft 365 コンプライアンス センター[通信コンプライアンス]**に移動します**。

3. ユーザー名の匿名化を構成するには、[プライバシー] タブ **を選択** します。

4. 匿名化を有効にするには、[匿名化 **されたバージョンのユーザー名を表示する] を選択します**。

5. **[保存]** を選択します。

6. [通知テンプレート] **タブに移動し** 、[通知テンプレートの作成 **] を選択します**。

7. [通知 **テンプレートの変更] ページで** 、次のフィールドに入力します。

    - テンプレート名 (必須)
    - から送信する (必須)
    - Cc と Bcc (オプション)
    - 件名 (必須)
    - メッセージ本文 (必須)

8. [保存 **] を** 選択して通知テンプレートを作成して保存します。

## <a name="step-7-optional-test-your-communication-compliance-policy"></a>手順 7 (オプション): 通信コンプライアンス ポリシーをテストする

コミュニケーション コンプライアンス ポリシーを作成したら、定義した条件がポリシーによって適切に実施されていることを確認するためのテストの実施をお勧めします。 通信コンプライアンス ポリシーに機密情報の種類が含まれる場合は、データ損失防止 [(DLP)](create-test-tune-dlp-policy.md) ポリシーをテストすることもできます。 テストする通信をキャプチャするために、ポリシーをアクティブ化する時間を与える必要があります。

次の手順に従って、通信コンプライアンス ポリシーをテストします。

1. テストするポリシーで定義Microsoft Teams監視Yammerサインインしている間に、電子メール クライアント、メール クライアント、メール サーバー、またはメール クライアントを開きます。

2. 通信コンプライアンス ポリシーで定義Microsoft Teamsを満たすYammer、電子メール、チャット、またはメッセージを送信します。 このテストには、キーワード、添付ファイルのサイズ、ドメインなどを指定できます。ポリシーの構成済みの条件付き設定が制限的すぎるか、寛大すぎるか確認してください。

    > [!NOTE]
    > 電子メール メッセージは、ポリシーで完全に処理するために最大 24 時間かかる場合があります。 Microsoft Teams、Yammer、サードパーティ製プラットフォームでのコミュニケーションは、ポリシーで完全に処理されるには最大 48 時間かかる可能性があります。

3. コミュニケーション コンプライアンス ポリシー Microsoft 365レビューアーとしてサインインします。 [通信コンプライアンス **通知]**  >  **に移動** して、ポリシーのアラートを表示します。

4. 修復コントロールを使用してアラートを修復し、アラートが適切に解決されていることを確認します。

## <a name="next-steps"></a>次の手順

最初の通信コンプライアンス ポリシーを作成するためにこれらの手順を完了すると、24 ~ 48 時間後にアクティビティ インジケーターからアラートの受信を開始します。 この記事の手順 5 のガイダンスを使用して、必要に応じて追加のポリシーを構成します。

通信コンプライアンスアラートの調査の詳細については、「通信コンプライアンスアラートの調査と修復 [」を参照してください](communication-compliance-investigate-remediate.md)。
