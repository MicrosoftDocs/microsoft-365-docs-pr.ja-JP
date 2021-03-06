---
title: 管理者として検疫済みメッセージとファイルを管理する
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 065cc2cf-2f3a-47fd-a434-2a20b8f51d0c
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: 管理者は、ユーザー (EOP) 内のすべてのユーザーの検疫済みメッセージを表示および管理Exchange Online Protectionできます。 Microsoft Defender for Office 365組織の管理者は、SharePoint Online、OneDrive for Business、およびMicrosoft Teams。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 59bdfdaddbc091467bfd2ccddc2c40377955fab3
ms.sourcegitcommit: d904f04958a13a514ce10219ed822b9e4f74ca2d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2021
ms.locfileid: "53028993"
---
# <a name="manage-quarantined-messages-and-files-as-an-admin-in-eop"></a>EOP の管理者として検疫済みメッセージとファイルを管理する

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**適用対象**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 プラン 1 およびプラン 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online のメールボックスを使用している Microsoft 365 組織または Exchange Online のメールボックスを使用していないスタンドアロンの Exchange Online Protection (EOP) 組織では、危険な可能性があるメッセージまたは不要なメッセージは検疫済みメッセージとして保留されます。 詳細については [、「EOP の検疫済み電子メール メッセージ」を参照してください](quarantine-email-messages.md)。

管理者は、すべてのユーザーの検疫済みメッセージのすべての種類を表示、解放、および削除できます。 マルウェア、高信頼フィッシング、またはメール フロー ルール (トランスポート ルールとも呼ばれる) の結果として検疫されたメッセージを管理できるのは、管理者だけです。 管理者は、誤検知を Microsoft に報告できます。

Microsoft Defender for Office 365 組織の管理者は、SharePoint Online、OneDrive for Business、および Microsoft Teams で検疫済みファイルを表示、ダウンロード、および削除Microsoft Teams。

検疫済みメッセージは、Microsoft 365 Defender ポータルまたは PowerShell (Exchange Online PowerShell for Microsoft 365 のメールボックスを持つ Exchange Online 組織、Exchange Online メールボックスのない組織のスタンドアロン EOP PowerShell) で表示および管理します。

## <a name="what-do-you-need-to-know-before-you-begin"></a>はじめに把握しておくべき情報

- Microsoft 365 Defender ポータルを開くには、<https://security.microsoft.com> にアクセスします。 検疫ページを直接開くには、<https://security.microsoft.com/quarantine> にアクセスします。

- Exchange Online PowerShell へ接続するには、「[Exchange Online PowerShell に接続する](/powershell/exchange/connect-to-exchange-online-powershell)」を参照してください。 スタンドアロンの EOP PowerShell に接続するには、「[Exchange Online Protection PowerShell への接続](/powershell/exchange/connect-to-exchange-online-protection-powershell)」を参照してください。

- この記事の手順を実行する際には、あらかじめ **Exchange Online** でアクセス許可を割り当てる必要があります。
  - すべてのユーザーの検疫済みメッセージに対してアクションを実行するには、組織の管理、セキュリティ管理者、または検疫管理者の役割グループのメンバー **である** <sup>\*</sup> 必要があります。
  - すべてのユーザーの検疫済みメッセージへの読み取り専用アクセスには、グローバル リーダーまたはセキュリティリーダーの役割グループの **メンバーである** 必要があります。

  詳細については、「[Exchange Online のアクセス許可](/exchange/permissions-exo/permissions-exo)」を参照してください。

  **注**:

  - Microsoft 365 管理センターで、対応する Azure Active Directory の役割にユーザーを追加すると、ユーザーには、必要なアクセス許可 _および_ Microsoft 365 のその他の機能に必要なアクセス許可が付与されます。 詳細については、「[管理者の役割について](../../admin/add-users/about-admin-roles.md)」を参照してください。
  - [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) の **閲覧専用の組織管理** の役割グループが この機能への読み取り専用アクセス権も付与します。
  - <sup>\*</sup>また、検疫管理者 **役割** グループのメンバーは [、Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups)で検疫手順を実行するために、Exchange Online Exchange Online の衛生管理役割グループのメンバーである必要があります。

- 検疫済みメッセージは、自動的に削除される前に既定の期間保持されます。
  - スパム対策ポリシー (スパム、フィッシング、バルク メール) によって検疫されたメッセージの 30 日間。 これは既定値と最大値です。 この値を (低く) 構成するには、「スパム対策ポリシーを構成 [する」を参照してください](configure-your-spam-filter-policies.md)。
  - マルウェアを含むメッセージの場合は 15 日間。
  - Defender セーフ の添付ファイル、SharePoint、OneDrive、Microsoft Teamsによって検疫Office 365。

  検疫からメッセージの有効期限が切れると、メッセージを回復できません。

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-email-messages"></a>検疫済みMicrosoft 365 Defenderを管理するには、このポータルを使用します。

### <a name="view-quarantined-email"></a>検疫済みメールの表示

1. Microsoft 365 Defender ポータルで、**[メールと共同作業]** \> **[レビュー]** \> **[検疫]** に移動します。

2. [検疫 **] ページ** で、[検疫の表示] **が** 既定値の電子メールに設定されているのを確認 **します**。

3. 使用できる列見出しをクリックすると、結果を並べ替えることができます。 **[列の変更]** をクリックして、最大で 7 列まで表示できます。 既定値にはアスタリスク (<sup>\*</sup>) が付いています。

   - **[受信日時]**<sup>\*</sup>
   - **[送信者]**<sup>\*</sup>
   - **[件名]**<sup>\*</sup>
   - **[検疫の理由]**<sup>\*</sup>
   - **[解放済み?]**<sup>\*</sup>
   - **[ポリシーの種類]**<sup>\*</sup>
   - **[有効期限]**<sup>\*</sup>
   - **[受信者]**
   - **[メッセージ ID]**
   - **[ポリシー名]**
   - **[サイズ]**
   - **[方向]**

   完了したら、**[保存]** をクリックして、**[既定値に設定]** をクリックします。

4. 結果をフィルター処理するには、**[フィルター]** をクリックします。 使用できるフィルターは次のとおりです。
   - **[期限切れ日時]**: 検疫の期限が切れるタイミングでメッセージをフィルター処理します。
     - **[今日]**
     - **[今後 2 日間]**
     - **[今後 7 日間]**
     - **[カスタム]**: **[開始日]** と **[終了日]** を入力します。
   - **[受信日時]**: **[開始日]** と **[終了日]** を入力します。
   - **[検疫の理由]**:
     - **ポリシー**: メッセージは、メール フロー ルール (トランスポート ルールとも呼ばれる) の条件と一致しました。
     - **バルク**
     - **フィッシング**: スパム フィルターの評決は、フィッシングメールまたはフィッシング対策保護がメッセージ [(ス](set-up-anti-phishing-policies.md#spoof-settings)プーフィング設定または偽装保護) を [検疫しました](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)。
     - **マルウェア**
     - **スパム**
     - **高信頼フィッシング**
   - **ポリシーの種類**: 次のポリシーの種類ごとに、メッセージをフィルター処理します。
     - **マルウェア対策ポリシー**
     - **セーフ添付ファイルポリシー**
     - **フィッシング対策ポリシー**
     - **ホストされているコンテンツ フィルター ポリシー** (スパム対策ポリシー)
     - **トランスポート ルール**
   - **電子メール受信者**: すべてのユーザーまたは送信されたメッセージのみ。 エンド ユーザーは、送信された検疫済みメッセージのみを管理できます。

   フィルターをクリアするには、**[クリア]** をクリックします。 フィルターのポップアップを非表示にするには、**[フィルター]** をもう一度クリックします。

5. **[結果の並べ替え]** (既定では **[メッセージ ID]** ボタン) および対応する値を使用して、特定のメッセージを検索します。 ワイルドカードはサポートされていません。 次の値に基づいて検索できます。
   - **[メッセージ ID]**: メッセージのグローバル一意識別子。

     たとえば、メッセージ [トレースを](message-trace-scc.md) 使用して、組織内のユーザーに送信されたメッセージを探し、メッセージが配信される代わりに検疫されたと判断しました。 メッセージ ID の完全な値 (角かっこ ( ) を含む場合があります) を必ず含める \<\> 必要があります。 例: `<79239079-d95a-483a-aacf-e954f592a0f6@XYZPR00BM0200.contoso.com>`。

   - **[送信者のメール アドレス]**: 単一の送信者のメール アドレス。
   - **ポリシー名**: メッセージのポリシー名全体を使用します。 この検索では大文字と小文字は区別されません。
   - **[受信者のメール アドレス]**: 単一の受信者のメール アドレス。
   - **[件名]**: メッセージの件名全体を使用します。 この検索では大文字と小文字は区別されません。
   - **ポリシー名**: メッセージのクォーティ化を担当したポリシーの名前。

   検索条件を入力したら、![[更新] ボタン](../../media/scc-quarantine-refresh.png) **[更新]** をクリックすると、結果がフィルター処理されます。

特定の検疫済みメッセージを見つけたら、そのメッセージを選択して詳細を表示し、処理を実行します (メッセージの表示、解放、ダウンロード、または削除など)。

#### <a name="view-quarantined-message-details"></a>検疫済みメッセージの詳細を表示する

一覧で電子メール メッセージを選択すると、次のメッセージの詳細が表示される詳細フライアウトで使用できます。

- **[メッセージ ID]**: メッセージのグローバル一意識別子。
- **[送信者のアドレス]**
- **[受信日時]**: メッセージを受信した日時。
- **[件名]**
- **検疫の理由**: メッセージがスパム、バルク、フィッシング、メールフロー ルール **(トランスポート** ルール) と一致したと識別された場合、またはマルウェアが含まれていると識別された場合に表示 **されます**。
- **受信者数**
- **[受信者]**: メッセージに複数の受信者が含まれている場合は、**[メッセージのプレビュー]** か **[メッセージ ヘッダーを表示]** をクリックして受信者の完全な一覧を表示する必要があります。
- **[有効期限]**: 検疫からメッセージが自動的に完全に削除される日時。
- **[解放済み]**: メッセージが解放されたすべてのメール アドレス (ある場合)。
- **[未解放]**: メッセージがまだ解放されていないすべてのメール アドレス (ある場合)。

### <a name="take-action-on-quarantined-email"></a>検疫済みメールを処理する

メッセージを選択した後、詳細フライアウトでメッセージを処理するためのいくつかのオプションがあります。

- **リリース メッセージ**: 表示されるフライアウトで、次のオプションを選択します。
  - **分析のために Microsoft にメッセージを** 報告する : これは既定で選択され、誤って検疫されたメッセージを誤検知として Microsoft に報告します。 メッセージがスパム、バルク、フィッシング、またはマルウェアを含むとして検疫された場合、メッセージは Microsoft スパム分析チームにも報告されます。 分析によっては、サービス全体のスパム フィルター ルールが調整され、メッセージの通過が許可される場合があります。
  - 次のいずれかのオプションを選択します。
    - **すべての受信者にメッセージを解放する**
    - **特定の受信者にメッセージをリリースする**
    - **他のユーザーへのメッセージの** 解放 : 元の受信者以外のユーザーにマルウェア メッセージを解放する機能はサポートされていません。

  完了したら、**[メッセージの解放]** をクリックします。

  メッセージのリリースに関する注意事項:

  - 同じ受信者に対してメッセージを 2 回以上リリースできない。
  - メッセージを受信していない受信者だけが、潜在的な受信者の一覧に表示されます。

- **[メッセージ ヘッダーを表示]**: このリンクをクリックすると、メッセージ ヘッダー テキストが表示されます。 ヘッダー フィールドと値を詳しく分析するには、メッセージ ヘッダー テキストをクリップボードにコピーし、**[Microsoft メッセージ ヘッダー アナライザー]** を選択して、リモート接続アナライザーに移動します (このタスクを実行するために Microsoft 365 を閉じたくない場合は、右クリックして **[新しいタブで開く]** を選択します)。 メッセージ ヘッダーを [Microsoft メッセージ ヘッダー アナライザー] セクションのページに貼り付け、**[ヘッダーを分析]** を選択します。
- **プレビュー メッセージ**: 表示されるフライアウトで、次のいずれかのオプションを選択します。
  - **[ソースを表示]**: すべてのリンクが無効になったメッセージ本文の HTML バージョンを表示します。
  - **[テキスト表示]**: プレーン テキストでメッセージ本文を表示します。
- **検疫から削除**: 表示される警告 **で [は** い] をクリックすると、メッセージは元の受信者に送信されることなくすぐに削除されます。
- **ダウンロード メッセージ**: 表示されるフライアウトで、[このメッセージをダウンロードするリスクを理解する] を選択して、メッセージのローカル コピーを .eml 形式で保存します。
- **送信者のブロック**: メールボックスの [ブロックされた送信者] リストに送信者を追加します。 詳細については、「[メール送信者をブロックする](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4)」を参照してください。
- **送信メッセージ**: 表示されるフライアウトで、次のオプションを選択します。
  - **オブジェクトの種類**:**メール**(既定 **)、URL、** または **添付ファイル 。**
  - **送信形式**: **ネットワーク メッセージ ID** (既定では、[ネットワーク メッセージ **ID]** ボックスに対応する値を指定) **または** [ファイル] (ローカルの .eml ファイルまたは .msg ファイルを参照)。 [ファイル] を **選択し** 、[ネットワーク メッセージ **ID]** を選択すると、初期値は削除されます。
  - **受信者:** メッセージの元の受信者をリース時に入力するか、[すべて選択] をクリックしてすべての受信者を識別します。 [すべて選択] **をクリックし** 、個々の受信者を選択的に削除できます。
  - **申請の理由**: **ブロックされていない** (既定) または **ブロックされている必要があります**。

  完了したら、[送信] を **クリックします**。

メッセージを解放も削除もしないと、既定の検疫保持期間が経過した後に削除されます。

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>複数の検疫済みメール メッセージを処理する

リストで複数の検疫済みメッセージ (最大 100) を選択すると、[一括操作] フライアウトが表示され、次のアクションを実行できます。

- **[メッセージの解放]**: このオプションは、**[特定の受信者にメッセージを解放する]** を選択できない点以外は単一のメッセージを解放する場合と同様です。**[すべての受信者にメッセージを解放する]** か **[他のユーザーにメッセージを解放する]** のみを選択できます。

  > [!NOTE]
  > 次のシナリオを検討してください:john@gmail.com メッセージをメッセージに送信 faith@contoso.com と john@subsidiary.contoso.com。 Gmail は、このメッセージを 2 つのコピーに分割し、どちらも Microsoft でフィッシング詐欺として検疫にルーティングされます。 管理者は、これらのメッセージの両方をリリースして、admin@contoso.com。 管理メールボックスに到達した最初のリリース済みメッセージが配信されます。 2 番目にリリースされたメッセージは重複配信として識別され、スキップされます。 メッセージ ID と受信時間が同じ場合、メッセージは重複として識別されます。

- **メッセージの** 削除 : 表示される警告 **で [は** い] をクリックすると、メッセージは元の受信者に送信されることなくすぐに削除されます。

完了したら、**[閉じる]** をクリックします。

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365"></a>Defender の検疫済Microsoft 365 Defenderを管理するには、このポータルを使用Office 365
> [!NOTE]
> このセクションの検疫済みファイルの手順は、プラン 1 およびプラン 2 Office 365 Microsoft Defender でのみ使用できます。

Defender for Office 365組織では、管理者は SharePoint Online、OneDrive for Business、および Microsoft Teams で検疫済みファイルを管理できます。 これらのファイルの保護を有効にするには、「添付ファイルを有効にする[セーフ」をSharePoint、OneDrive、](turn-on-mdo-for-spo-odb-and-teams.md)およびMicrosoft Teams。

### <a name="view-quarantined-files"></a>検疫済みファイルの表示

1. Microsoft 365 Defender ポータルで、**[メールと共同作業]** \> **[レビュー]** \> **[検疫]** に移動します。


2. [検疫 **] ページ** で、[検疫済 **みビュー] を値** ファイルに変更 **します**。 使用可能な列ヘッダーをクリックすると、フィールドの並べ替えを行います。

3. 使用できる列見出しをクリックすると、結果を並べ替えることができます。 **[列の変更]** をクリックして、最大で 7 列まで表示できます。 既定の列には、アスタリスク ( ) が付いています <sup>\*</sup> 。
   - [**User**<sup>\*</sup>]
   - **場所**<sup>\*</sup>
   - **ファイル名**<sup>\*</sup>
   - **ファイル URL**<sup>\*</sup>
   - **ファイル サイズ**<sup>\*</sup>
   - **[有効期限]**<sup>\*</sup>
   - **[解放済み?]**<sup>\*</sup>
   - **によって検出される**
   - **時間による変更**

4. 結果をフィルター処理するには、**[フィルター]** をクリックします。 使用できるフィルターは次のとおりです。
   - **[期限切れ日時]**: 検疫の期限が切れるタイミングでメッセージをフィルター処理します。
     - **[今日]**
     - **[今後 2 日間]**
     - **[今後 7 日間]**
     - カスタムの日付/時刻範囲。
   - **受信時刻**
   - **検疫の理由**: 使用可能な値は Malware **のみです**。
   - **ポリシーの種類**

特定の検疫済みファイルを見つけたら、ファイルを選択して詳細を表示し、そのファイルに対してアクションを実行します (メッセージの表示、リリース、ダウンロード、削除など)。

#### <a name="view-quarantined-file-details"></a>検疫済みファイルの詳細を表示する

一覧でファイルを選択すると、開く詳細フライアウトで次のファイルの詳細が表示されます。

- **ファイル名**
- **ファイル URL**: ファイルの場所を定義する URL (たとえば、[オンライン] SharePointします)。
- **悪意のあるコンテンツが検出された** ファイルが検疫された日付/時刻。
- **有効期限**: ファイルが検疫から削除される日付。
- **Detected By**: Defender for Office 365 Microsoft のマルウェア対策エンジン。
- **[解放済み?]**
- **マルウェア名**
- **ドキュメント ID**: ドキュメントの一意の識別子。
- **ファイル サイズ**: キロバイト (KB) で指定します。
- **組織** 組織の一意の ID。
- **最終更新日時**
- **[変更者**] : ファイルを最後に変更したユーザー。
- **Secure Hash Algorithm 256-bit (SHA-256)** の値 : このハッシュ値を使用して、他の評価ストアまたは環境内の他の場所にあるファイルを識別できます。

### <a name="take-action-on-quarantined-files"></a>検疫済みファイルに対してアクションを実行する

一覧でファイルを選択すると、詳細フライアウトでファイルに対して次のアクションを実行できます。

- **ファイルを解放** する : 分析のためにMicrosoft にレポート ファイルを選択 (既定) または選択解除し、[ファイルのリリース]**をクリックします**。
- **ファイルをダウンロードする**
- **検疫からファイルを削除する**

ファイルを解放または削除しない場合、既定の検疫保持期間の有効期限が切れると、ファイルは削除されます。

#### <a name="actions-on-multiple-quarantined-files"></a>複数の検疫済みファイルに対するアクション

リストで複数の検疫済みファイル (最大 100) を選択すると、[一括操作] フライアウトが表示され、次の操作を実行できます。

- **ファイルを解放する**
- **ファイルの削除**: 表示される **警告で [は** い] をクリックすると、ファイルはすぐに削除されます。

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-view-and-manage-quarantined-messages-and-files"></a>PowerShell Exchange Onlineスタンドアロン EOP PowerShell を使用して、検疫済みメッセージとファイルを表示および管理する

検疫内のメッセージとファイルを表示および管理するコマンドレットは、次のとおりです。

- [Delete-QuarantineMessage](/powershell/module/exchange/delete-quarantinemessage)

- [Export-QuarantineMessage](/powershell/module/exchange/export-quarantinemessage)

- [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)

- [Preview-QuarantineMessage](/powershell/module/exchange/preview-quarantinemessage): このコマンドレットはメッセージ専用であり、セーフ 添付ファイルから SharePoint、OneDrive、および Microsoft Teams のファイルを検疫Microsoft Teams。

- [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)
