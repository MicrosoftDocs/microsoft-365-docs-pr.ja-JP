---
title: 検疫ポリシー
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ROBOTS: NOINDEX
description: 管理者は、検疫ポリシーを使用して、検疫されたメッセージに対してユーザーが実行できる操作を制御する方法について説明します。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 96dc1e2158787457884ca6a3c6f27bf76e83a369
ms.sourcegitcommit: fa9efab24a84f71fec7d001f2ad8949125fa8eee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2021
ms.locfileid: "53055202"
---
# <a name="quarantine-policies"></a>検疫ポリシー

> [!NOTE]
> この記事で説明する機能は、現在プレビュー中であり、すべてのユーザーが利用できる機能ではなく、変更される可能性があります。

Exchange Online Protection (EOP) の検疫ポリシー (以前は検疫タグと呼ばれる) を使用すると、管理者は、メッセージが検疫に到着した方法に基づいて、検疫されたメッセージに対してユーザーが実行できる操作を制御できます。

EOP は、従来、検疫およびエンド ユーザーのスパム通知のメッセージに[](find-and-release-quarantined-messages-as-a-user.md)対して、特定のレベルの対話機能を許可または[防止しています](use-spam-notifications-to-release-and-report-quarantined-messages.md)。 たとえば、ユーザーはスパム対策フィルターによって検疫されたメッセージをスパムまたは一括として表示および解放できますが、高信頼フィッシングとして検疫されたメッセージを表示または解放できない (管理者だけが実行できます)。

サポート [されている保護機能](#step-2-assign-a-quarantine-policy-to-supported-features)の場合、検疫ポリシーは、エンドユーザーのスパム通知メッセージと検疫中の検疫済みメッセージ (ユーザーが受信者であるメッセージ) でユーザーが実行できる操作を指定します。 既定の検疫ポリシーは、検疫されたメッセージに対してユーザーの履歴機能を適用するために自動的に割り当てられます。 または、カスタム検疫ポリシーを作成して割り当て、エンド ユーザーが検疫済みメッセージに対して特定のアクションを実行を許可または防止できます。

個々のアクセス許可は、次の事前設定されたアクセス許可グループに組み合わされます。

- アクセスなし
- 制限付きアクセス
- フル アクセス

使用可能な個々のアクセス許可と、事前設定されたアクセス許可グループに含まれているか含まれていないかについて、次の表で説明します。

<br>

****

|アクセス許可|アクセスなし|制限付きアクセス|フル アクセス|
|---|:---:|:---:|:---:|
|**送信者を許可** する (_PermissionToAllowSender_)|||![チェック マーク](../../media/checkmark.png)|
|**送信者のブロック** (_PermissionToBlockSender_)||![チェック マーク](../../media/checkmark.png)|![チェック マーク](../../media/checkmark.png)|
|**Delete** (_PermissionToDelete_)||![チェック マーク](../../media/checkmark.png)|![チェック マーク](../../media/checkmark.png)|
|**プレビュー** (_PermissionToPreview_)||![チェック マーク](../../media/checkmark.png)|![チェック マーク](../../media/checkmark.png)|
|**受信者に検疫からのメッセージの解放を許可** する (_PermissionToRelease_)|||![チェック マーク](../../media/checkmark.png)|
|**受信者がメッセージを検疫から** 解放する要求を許可する (_PermissionToRequestRelease_)||![チェック マーク](../../media/checkmark.png)||
|

事前設定されたアクセス許可グループの既定のアクセス許可が気に入らない場合は、カスタム検疫ポリシーを作成または変更するときにカスタムアクセス許可を使用できます。 各アクセス許可の動作の詳細については、この記事の後半の「 [検疫ポリシーのアクセス許可の詳細](#quarantine-policy-permission-details) 」セクションを参照してください。

Microsoft 365 Defender ポータルまたは PowerShell で検疫ポリシーを作成および割り当てる (Exchange Online メールボックスを持つ Microsoft 365 組織の場合は Exchange Online PowerShell、Exchange Online メールボックスのない EOP 組織ではスタンドアロンの EOP PowerShell)。

## <a name="what-do-you-need-to-know-before-you-begin"></a>はじめに把握しておくべき情報

- <https://security.microsoft.com> で Microsoft 365 Defender ポータルを開きます。 または、[検疫ポリシー] ページに直接 **移動するには、** を開きます <https://security.microsoft.com/quarantineTags> 。

- Exchange Online PowerShell へ接続するには、「[Exchange Online PowerShell に接続する](/powershell/exchange/connect-to-exchange-online-powershell)」を参照してください。 スタンドアロンの EOP PowerShell に接続するには、「[Exchange Online Protection PowerShell への接続](/powershell/exchange/connect-to-exchange-online-protection-powershell)」を参照してください。

- 検疫ポリシーを表示、Microsoft 365 Defender 作成、変更、または削除するには、組織の管理またはセキュリティ管理者の役割のメンバーである必要があります。 詳細については、「[Microsoft 365 Defender ポータルのアクセス許可](permissions-microsoft-365-security-center.md)」を参照してください。

## <a name="step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal"></a>手順 1: セキュリティ ポータルで検疫ポリシーをMicrosoft 365 Defenderする

1. [セキュリティ ポータルMicrosoft 365 Defenderに移動し、[電子メール &**の** 脅威ポリシー] セクションの [検疫ポリシー] に移動し、[検疫ポリシー \>  \>  \>  ]**を選択します**。

2. [検疫ポリシー **] ページで** 、[カスタム ポリシーの追加] アイコン [カスタム ![ ](../../media/m365-cc-sc-create-icon.png) **ポリシーの追加] をクリックします**。

3. 新 **しいポリシー ウィザード** が開きます。 [ポリシー名 **] ページで** 、[ポリシー名] ボックスに簡単な一意の **名前を入力** します。 今後の手順では、名前で検疫ポリシーを識別して選択する必要があります。 完了したら、**[次へ]** をクリックします。

4. [受信者メッセージ **アクセス] ページ** で、次のいずれかの値を選択します。
   - **アクセスなし**
   - **制限付きアクセス**
   - **フル アクセス**

   これらのアクセス許可グループに含まれる個々のアクセス許可については、この記事の前で説明します。

   カスタムアクセス許可を指定するには、[特定のアクセス **許可を設定する (Advanced)** を選択し、表示される次の設定を構成します。

     - **[リリース アクションの基本設定]** を選択します。次のいずれかの値を選択します。
       - **リリースアクションなし**: これは既定値です。
       - **受信者が検疫からメッセージを解放するを許可する**
       - **受信者が検疫からメッセージを解放する要求を許可する**
     - **検疫済みメッセージに対して** 受信者が実行できる追加のアクションを選択する: 次の値の一部、すべて、またはなしを選択します。
       - **削除**
       - **プレビュー**
       - **送信者をブロックする**

   これらのアクセス許可と検疫済みメッセージおよびエンド ユーザースパム通知への影響については、この記事の[](#quarantine-policy-permission-details)後半の「検疫ポリシーのアクセス許可の詳細」セクションで説明します。

   完了したら、**[次へ]** をクリックします。

5. 表示される **[ポリシーの確認** ] ページで、設定を確認します。 各セクションで **[編集]** を選択して、そのセクション内の設定を変更することができます。 または、**[戻る]** をクリックするか、ウィザードで特定のページを選択します。

   完了したら、[送信] を **クリックします**。

6. 表示された [確認]ページで、**[完了]** をクリックします。

これで、手順 2 の説明に従って検疫ポリシーを検疫機能に割 [り当てる準備ができました](#step-2-assign-a-quarantine-policy-to-supported-features) 。

### <a name="create-quarantine-policies-in-powershell"></a>PowerShell で検疫ポリシーを作成する

PowerShell を使用して検疫ポリシーを作成する場合は、Exchange Online PowerShell または Exchange Online Protection PowerShell に接続し **、New-QuarantineTag コマンドレットを使用** します。 次の 2 つの方法から選択できます。

- _EndUserQuarantinePermissionsValue パラメーターを使用_ します。
- _EndUserQuarantinePermissions パラメーターを使用_ します。

これらのメソッドについては、次のセクションで説明します。

#### <a name="use-the-enduserquarantinepermissionsvalue-parameter"></a>EndUserQuarantinePermissionsValue パラメーターを使用する

_EndUserQuarantinePermissionsValue_ パラメーターを使用して検疫ポリシーを作成するには、次の構文を使用します。

```powershell
New-QuarantineTag -Name "<UniqueName>" -EndUserQuarantinePermissionsValue <0 to 236>
```

_EndUserQuarantinePermissionsValue_ パラメーターは、バイナリ値から変換される 10 進値を使用します。 バイナリ値は、特定の順序で使用可能なエンド ユーザー検疫のアクセス許可に対応します。 アクセス許可ごとに、値 1 は True、値 0 は False に等しくなります。

事前設定されたアクセス許可グループの各アクセス許可に必要な順序と値を次の表に示します。

<br>

****

|アクセス許可|アクセスなし|制限付きアクセス|フル アクセス|
|---|:---:|:---:|:---:|
|PermissionToAllowSender|0|0|1|
|PermissionToBlockSender|0|1|1|
|PermissionToDelete|0|1|1|
|PermissionToDownload<sup>\*</sup>|0|0|0|
|PermissionToPreview|0|1|1|
|PermissionToRelease<sup>\*\*</sup>|0|0|1|
|PermissionToRequestRelease<sup>\*\*</sup>|0|1|0|
|PermissionToViewHeader<sup>\*</sup>|0|0|0|
|バイナリ値|00000000|01101010|11101100|
|使用する 10 進値|0|106|236|
|

<sup>\*</sup> 現在、この値は常に 0 です。 PermissionToViewHeader の場合、値 0 は検疫済みメッセージの詳細で [メッセージ ヘッダーの表示] ボタンを非表示にできません (ボタンは常に使用できます)。

<sup>\*\*</sup> 両方の値を 1 に設定しない。 1 を 1 に、もう一方を 0 に設定するか、両方を 0 に設定します。

この例では、前の表で説明したように、アクセス許可なしを割り当てる新しい検疫ポリシー名 NoAccess を作成します。

```powershell
New-QuarantineTag -Name NoAccess -EndUserQuarantinePermissionsValue 0
```

制限付きアクセス許可の場合は、値 106 を使用します。 [完全アクセス許可] の場合は、値 236 を使用します。

カスタムアクセス許可の場合は、前の表を使用して、必要なアクセス許可に対応するバイナリ値を取得します。 バイナリ値を 10 進値に変換し _、EndUserQuarantinePermissionsValue_ パラメーターに 10 進値を使用します。

構文とパラメーターの詳細については [、「New-QuarantineTag」を参照してください](/powershell/module/exchange/new-quarantinetag)。

#### <a name="use-the-enduserquarantinepermissions-parameter"></a>EndUserQuarantinePermissions パラメーターを使用する

_EndUserQuarantinePermissionsValue_ パラメーターを使用して検疫ポリシーを作成するには、次の手順を実行します。

A. **New-QuarantinePermissions** コマンドレットを使用して、検疫アクセス許可オブジェクトを変数に格納します。

<p>

B. New-QuarantineTag コマンドの _EndUserQuarantinePermissions_ 値 **として変数を使用** します。

##### <a name="step-a-store-a-quarantine-permissions-object-in-a-variable"></a>手順 A: 検疫アクセス許可オブジェクトを変数に格納する

次の構文を使用してください。

```powershell
$<VariableName> = New-QuarantinePermissions [-PermissionToAllowSender <$true | $False>] [-PermissionToBlockSender <$true | $False>] [-PermissionToDelete <$true | $False>] [-PermissionToPreview <$true | $False>] [-PermissionToRelease <$true | $False>] [-PermissionToRequestRelease <$true | $False>]
```

未使用のパラメーターの既定値は次の値なので、値をに設定するパラメーターのみを `$false` 使用する必要があります `$true` 。

次の例は、事前設定されたアクセス許可グループに対応するアクセス許可オブジェクトを作成する方法を示しています。

- **アクセスなし**:

  ```powershell
  $NoAccess = New-QuarantinePermissions
  ```

- **制限付きアクセス**:

  ```powershell
  $LimitedAccess = New-QuarantinePermissions -PermissionToBlockSender $true -PermissionToDelete $true -PermissionToPreview $true -PermissionToRequestRelease $true
  ```

- **フル アクセス**:

  ```powershell
  $FullAccess = New-QuarantinePermissions -PermissionToAllowSender $true -PermissionToBlockSender $true -PermissionToDelete $true -PermissionToPreview $true -PermissionToRelease $true
  ```

設定した値を表示するには、変数名をコマンドとして実行します (たとえば、コマンドを実行します `$NoAccess` )。

カスタムアクセス許可の場合は _、PermissionToRelease_ パラメーターと _PermissionToRequestRelease_ パラメーターの両方をに設定しない `$true` 。 1 つを `$true` に設定し、もう一方を `$false` そのままにするか、両方をとして残します `$false` 。

作成後 **、Set-QuarantinePermissions** コマンドレットを使用して使用する前に、既存のアクセス許可オブジェクト変数を変更することもできます。

構文とパラメーターの詳細については [、「New-QuarantinePermissions」](/powershell/module/exchange/new-quarantinepermissions) および [「Set-QuarantinePermissions」を参照してください](/powershell/module/exchange/set-quarantinepermissions)。

##### <a name="step-b-use-the-variable-in-the-new-quarantinetag-command"></a>手順 B: [変数] コマンドで変数New-QuarantineTagします。

permissions オブジェクトを変数に作成して格納したら、次の **New-QuarantineTag** コマンドで _EndUserQuarantinePermission_ パラメーター値の変数を使用します。

```powershell
New-QuarantineTag -Name "<UniqueName>" -EndUserQuarantinePermissions $<VariableName>
```

次の使用例は、前の手順で説明して作成したアクセス許可オブジェクトを使用して、LimitedAccess という名前の新しい検疫 `$LimitedAccess` ポリシーを作成します。

```powershell
New-QuarantineTag -Name LimitedAccess -EndUserQuarantinePermissions $LimitedAccess
```

構文とパラメーターの詳細については [、「New-QuarantineTag」を参照してください](/powershell/module/exchange/new-quarantinetag)。

## <a name="step-2-assign-a-quarantine-policy-to-supported-features"></a>手順 2: 検疫ポリシーをサポートされている機能に割り当てる

メッセージ _またはファイルを_ 検疫するサポートされている保護機能 (自動的に、または構成可能なアクションとして) では、検疫ポリシーを使用可能な検疫アクションに割り当てることもできます。 メッセージを検疫する機能と検疫ポリシーの可用性については、次の表で説明します。

<br>

****

|機能|検疫ポリシーがサポートされていますか?|使用される既定の検疫ポリシー|
|---|:---:|---|
|[スパム対策ポリシー](configure-your-spam-filter-policies.md): <ul><li>**スパム** (_SpamAction_)</li><li>**高信頼スパム** (_HighConfidenceSpamAction_)</li><li>**フィッシング** (_PhishSpamAction_)</li><li>**高信頼フィッシング** (_HighConfidencePhishAction_)</li><li>**Bulk** (_BulkSpamAction_)</li></ul>|はい|<ul><li>DefaultSpamTag (フル アクセス)</li><li>DefaultHighConfSpamTag (フル アクセス)</li><li>DefaultPhishTag (フル アクセス)</li><li>DefaultHighConfPhishTag (アクセスなし)</li><li>DefaultBulkTag (フル アクセス)</li></ul>
|フィッシング対策ポリシー: <ul><li>[スプーフィング インテリジェンス保護](set-up-anti-phishing-policies.md#spoof-settings) (_AuthenticationFailAction_)</li><li>[偽装保護](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365):<sup>\*</sup> <ul><li>**偽装ユーザーとしてメッセージが検出された場合** (_TargetedUserProtectionAction_)</li><li>**偽装ドメインとしてメッセージが検出された場合** (_TargetedDomainProtectionAction_)</li><li>**メールボックス インテリジェンスがユーザーを検出して偽装した場合** (_MailboxIntelligenceProtectionAction_)</li></ul></li></ul></ul>|いいえ|該当なし|
|[マルウェア対策ポリシー](configure-anti-malware-policies.md): 検出されたメッセージはすべて常に検疫されます。|いいえ|該当なし|
|[SharePoint、OneDrive、Microsoft Teams 用の安全な添付ファイル](mdo-for-spo-odb-and-teams.md)|いいえ|該当なし|
|[アクションを含む](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) メール フロー ルール (トランスポート ルールとも呼ばれる): メッセージをホストされた検疫 (検疫) **に** 配信 _します_。|いいえ|該当なし|
|

<sup>\*</sup>偽装保護の設定は、Microsoft Defender のフィッシング対策ポリシーでのみOffice 365。

既定の検疫ポリシーによって提供されるエンド ユーザーのアクセス許可に満足している場合は、何もする必要はありません。 エンド ユーザーのスパム通知または検疫済みメッセージの詳細でエンド ユーザー機能 (使用可能なボタン) をカスタマイズする場合は、カスタム検疫ポリシーを割り当てできます。

### <a name="assign-quarantine-policies-in-anti-spam-policies-in-the-microsoft-365-defender-portal"></a>スパム対策ポリシーで検疫ポリシーを割り当てるには、Microsoft 365 Defenderします。

スパム対策ポリシーを作成および変更する手順の詳細については、「EOP でのスパム対策ポリシーの構成」 [を参照してください](configure-your-spam-filter-policies.md)。

1. [メール Microsoft 365 Defender] ポータルで、[メール &**ポリシー** ] &[スパム対策] \>  \>  \> **セクションに移動します**。 または、 を開きます <https://security.microsoft.com/antispam> 。

2. [スパム **対策ポリシー] ページで** 、次のいずれかの手順を実行します。
   - 既存の受信スパム対策 **ポリシーを** 検索して選択します。
   - 新しい受信 **スパム対策** ポリシーを作成します。

3. 次のいずれかの手順を実行します。
   - **既存のスパム対策ポリシーを** 編集する : ポリシーの詳細フライアウトで、[アクション] セクションに移動し、[アクションの編集]**をクリックします**。
   - **新しいスパム対策ポリシーを作成する**: 新しいポリシー ウィザードで、[アクション] ページ **に移動** します。

4. [操作 **] ページ** で。 検疫メッセージ アクションを持つすべての評決には、対応する検疫ポリシーを選択する [検疫ポリシーの選択] ボックスも表示されます。

   **注**: 新しいポリシーを作成する場合、空の **[** 検疫ポリシーの選択] の値は、その評決の既定の検疫ポリシーが使用されます。 後でポリシーを編集すると、前の表で説明したように、空白の値が実際の既定の検疫ポリシー名に置き換えられる。

   ![スパム対策ポリシーの検疫ポリシーの選択](../../media/quarantine-tags-in-anti-spam-policies.png)

5. 完了したら、**[保存]** をクリックします。

#### <a name="assign-quarantine-policies-in-anti-spam-policies-in-powershell"></a>PowerShell のスパム対策ポリシーで検疫ポリシーを割り当てる

スパム対策ポリシーで検疫ポリシーを割り当てる場合は、Exchange Online PowerShell または Exchange Online Protection PowerShell に接続し、次の構文を使用します。

```powershell
<New-HostedContentFilterPolicy -Name "<Unique name>" | Set-HostedContentFilterPolicy -Identity "<Policy name>">  [-SpamAction Quarantine] [-SpamQuarantineTag <QuarantineTagName>] [-HighConfidenceSpamAction Quarantine] [-HighConfidenceSpamQuarantineTag <QuarantineTagName>] [-PhishSpamAction Quarantine] [-PhishQuarantineTag <QuarantineTagName>] [-HighConfidencePhishQuarantineTag <QuarantineTagName>] [-BulkSpamAction Quarantine] [-BulkQuarantineTag <QuarantineTagName>] ...
```

**注**:

- _HighConfidencePhishAction_ パラメーターの既定値は [検疫] なので、新しいスパム対策ポリシーで高信頼フィッシング検出の検疫アクションを設定する必要はありません。 新しいスパム対策ポリシーまたは既存のスパム対策ポリシーの他のすべてのスパム フィルターの評決では、検疫ポリシーは、アクション値が [検疫] の場合にのみ有効です。 既存のスパム対策ポリシーのアクション値を表示するには、次のコマンドを実行します。

  ```powershell
  Get-HostedContentFilterPolicy | Format-Table Name,*SpamAction,HighConfidencePhishAction
  ```

  Standard および Strict の既定のアクション値と推奨されるアクション値については、「EOP スパム対策ポリシー設定」 [を参照してください](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)。

- 対応する検疫ポリシー パラメーターのないスパム フィルターの評決は、[](#step-2-assign-a-quarantine-policy-to-supported-features)その評決の既定の検疫ポリシーが使用されるという意味です。

  検疫済みメッセージの既定のエンド ユーザー機能を変更する場合は、既定の検疫ポリシーをカスタム検疫ポリシーに置き換える必要があります。

- PowerShell の新しいスパム対策ポリシーには **、New-HostedContentFilterPolicy** コマンドレットを使用するスパム フィルター ポリシー (設定) と **、New-HostedContentFilterRule** コマンドレットを使用する新しいスパム フィルター ルール (受信者フィルター) が必要です。 手順については [、「Use PowerShell を使用してスパム対策ポリシーを作成する」を参照してください](configure-your-spam-filter-policies.md#use-powershell-to-create-anti-spam-policies)。

この例では、次の設定を使用して、Research Department という名前の新しいスパム フィルター ポリシーを作成します。

- すべてのスパム フィルターの評決に対するアクションが [検疫] に設定されます。
- アクセス許可なしを割り当てる NoAccess という名前のカスタム検疫ポリシーは、既定でアクセス許可なしをまだ割り当てない既定の検疫ポリシーに置き換わります。 

```powershell
New-HostedContentFilterPolicy -Name Research Department -SpamAction Quarantine -SpamQuarantineTag NoAccess -HighConfidenceSpamAction Quarantine -HighConfidenceSpamQuarantineTag NoAction -PhishSpamAction Quarantine -PhishQuarantineTag NoAction -BulkSpamAction Quarantine -BulkQuarantineTag NoAccess
```

構文とパラメーターの詳細については、「[New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy)」を参照してください。

この例では、Human Resources という名前の既存のスパム フィルター ポリシーを変更します。 スパム検疫の評決のアクションは [検疫] に設定され、NoAccess という名前のカスタム検疫ポリシーが割り当てられます。

```powershell
Set-HostedContentFilterPolicy -Identity "Human Resources" -SpamAction Quarantine -SpamQuarantineTag NoAccess
```

構文とパラメーターの詳細については、「[Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy)」を参照してください。

## <a name="configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal"></a>ポータルでグローバル検疫通知設定をMicrosoft 365 Defenderする

検疫ポリシーのグローバル設定を使用すると、検疫されたメッセージの受信者に送信されるエンドユーザーのスパム通知をカスタマイズできます。 これらの通知の詳細については、「エンドユーザーの [スパム通知」を参照してください](use-spam-notifications-to-release-and-report-quarantined-messages.md)。

1. [セキュリティ ポータルMicrosoft 365 Defenderに移動し、[電子メール &**の** 脅威ポリシー] セクションの [検疫ポリシー] に移動し、[検疫ポリシー \>  \>  \>  ]**を選択します**。

2. [検疫ポリシー **] ページで、[** グローバル設定] **を選択します**。

3. 開く **検疫通知設定の** フライアウトで、次の設定の一部またはすべてを構成します。

   - **表示名**: エンド ユーザーのスパム通知で使用される送信者の表示名をカスタマイズします。

     追加した言語ごとに、2 番目の言語ボックス ([X] をクリックしない) で言語を選択し、[表示名] ボックスに必要なテキスト値 **を入力** します。

     次のスクリーンショットは、エンド ユーザーのスパム通知でカスタマイズされた表示名を示しています。

     ![エンド ユーザースパム通知のカスタマイズされた送信者の表示名](../../media/quarantine-tags-esn-customization-display-name.png)

   - **免責** 事項 : エンドユーザーのスパム通知の下部にカスタム免責事項を追加します。 ローカライズされたテキスト、 **組織からの免責事項:** は常に最初に含まれていて、その後に指定したテキストが含まれます。

     追加した言語ごとに、2 番目の言語ボックス ([X] をクリックしない) で言語を選択し、[免責事項] ボックスに必要なテキスト値 **を入力** します。

     次のスクリーンショットは、エンド ユーザーのスパム通知でカスタマイズされた免責事項を示しています。

     ![エンドユーザーのスパム通知の下部にあるカスタム免責事項](../../media/quarantine-tags-esn-customization-disclaimer.png)

   - **[言語の選択**]: エンド ユーザーのスパム通知は、受信者の言語設定に基づいて既にローカライズされています。 表示名と免責事項の値には、異なる **言語でカスタマイズ** されたテキスト **を指定** できます。

     [最初の言語] ボックスから少なくとも 1 つの言語を選択し、[追加] を **クリックします**。 複数の言語を選択するには、[追加] をクリック **します** 。 セクションの言語ボックスには、選択した言語すべてが表示されます。

     ![検疫ポリシーのグローバル検疫通知設定の [2 番目の言語] ボックスで選択した言語](../../media/quarantine-tags-esn-customization-selected-languages.png)

   - **[会社のロゴを使用** する]: エンド ユーザーのスパム通知の上部で使用される既定の Microsoft ロゴを置き換える場合は、このオプションを選択します。 これを行う前に、「カスタム ロゴをアップロードするには、組織Microsoft 365テーマをカスタマイズする」の[指示](../../admin/setup/customize-your-organization-theme.md)に従う必要があります。

     次のスクリーンショットは、エンドユーザーのスパム通知のカスタム ロゴを示しています。

     ![エンドユーザースパム通知のカスタム ロゴ](../../media/quarantine-tags-esn-customization-logo.png)

## <a name="view-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender ポータルで検疫ポリシーを表示する

1. [セキュリティ ポータルMicrosoft 365 Defenderに移動し、[電子メール &**の** 脅威ポリシー] セクションの [検疫ポリシー] に移動し、[検疫ポリシー \>  \>  \>  ]**を選択します**。

2. [**検疫ポリシー] ページ** には、[名前]と [最終更新日] のポリシー **の一覧が表示** されます。

3. 組み込みまたはカスタム検疫ポリシーの設定を表示するには、名前をクリックして、一覧から検疫ポリシーを選択します。

4. グローバル設定を表示するには、[グローバル設定] **をクリックします。**

### <a name="view-quarantine-policies-in-powershell"></a>PowerShell で検疫ポリシーを表示する

PowerShell を使用して検疫ポリシーを表示する場合は、次の手順を実行します。

- すべての組み込みポリシーまたはカスタム ポリシーの概要リストを表示するには、次のコマンドを実行します。

  ```powershell
  Get-QuarantineTag | Format-Table Name
  ```

- 組み込みまたはカスタム検疫ポリシーの設定を表示するには、検疫ポリシーの名前に置き換え、 \<QuarantinePolicyName\> 次のコマンドを実行します。

  ```powershell
  Get-QuarantineTag -Identity "<QuarantinePolicyName>"
  ```

- グローバル設定を表示するには、次のコマンドを実行します。

  ```powershell
  Get-QuarantineTag -QuarantineTagType GlobalQuarantineTag
  ```

構文とパラメーターの詳細については、「[Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy)」を参照してください。

## <a name="modify-quarantine-policies-in-the-microsoft-365-defender-portal"></a>ポータルで検疫ポリシーをMicrosoft 365 Defenderする

1. [セキュリティ ポータルMicrosoft 365 Defenderに移動し、[電子メール &**の** 脅威ポリシー] セクションの [検疫ポリシー] に移動し、[検疫ポリシー \>  \>  \>  ]**を選択します**。

2. [検疫 **ポリシー] ページで** 、名前をクリックしてポリシーを選択します。

3. ポリシーを選択した後、[ポリシーの編集] アイコン ![ ](../../media/m365-cc-sc-edit-icon.png) **が表示される [ポリシーの編集** ] アイコンをクリックします。

4. 開 **くポリシーの** 編集ウィザードは、この記事の前の「Microsoft 365 Defender ポータルの検疫ポリシーの作成」で説明したように、新しいポリシー [ウィザードと](#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal)事実上同じです。

   主な違いは、既存のポリシーの名前を変更できない点です。

5. ポリシーの変更が完了したら、[概要] ページに移動し、[送信] を **クリックします**。

### <a name="modify-quarantine-policies-in-powershell"></a>PowerShell で検疫ポリシーを変更する

PowerShell を使用してカスタム検疫ポリシーを変更する場合は、検疫ポリシーの名前に置き換え、次の \<QuarantinePolicyName\> 構文を使用します。

```powershell
Set-QuarantineTag -Identity "<QuarantinePolicyName>" [Settings]
```

使用可能な設定は、この記事で前述した検疫ポリシーの作成に関する説明と同じです。

構文とパラメーターの詳細については [、「Set-QuarantineTag」を参照してください](/powershell/module/exchange/set-quarantinetag)。

## <a name="remove-quarantine-policies-in-the-microsoft-365-defender-portal"></a>セキュリティ ポータルで検疫ポリシーをMicrosoft 365 Defenderする

**注**:

- 組み込みの検疫ポリシーを削除できない。
- カスタム検疫ポリシーを削除する前に、そのポリシーが使用されていないか確認してください。 たとえば、PowerShell で次のコマンドを実行します。

  ```powershell
  Get-HostedContentFilterPolicy | Format-List Name,*QuarantineTag
  ```

  検疫ポリシーが使用されている場合は、割 [り当てられた検疫ポリシー](#step-2-assign-a-quarantine-policy-to-supported-features) を削除する前に置き換える必要があります。

1. [セキュリティ ポータルMicrosoft 365 Defenderに移動し、[電子メール &**の** 脅威ポリシー] セクションの [検疫ポリシー] に移動し、[検疫ポリシー \>  \>  \>  ]**を選択します**。

2. [検疫 **ポリシー] ページ** で、名前をクリックして削除するカスタム検疫ポリシーを選択します。

3. ポリシーを選択した後、[ポリシーの削除] ![ アイコン ](../../media/m365-cc-sc-delete-icon.png) が表示される [ **ポリシーの** 削除] アイコンをクリックします。

4. 表示 **される確認ダイアログで** [ポリシーの削除] をクリックします。

### <a name="remove-quarantine-policies-in-powershell"></a>PowerShell で検疫ポリシーを削除する

PowerShell を使用してカスタム検疫ポリシーを削除する場合は、検疫ポリシーの名前に置き換え、 \<QuarantinePolicyName\> 次のコマンドを実行します。

```powershell
Remove-QuarantineTag -Identity "<QuarantinePolicyName>"
```

構文とパラメーターの詳細については [、「Remove-QuarantineTag」を参照してください](/powershell/module/exchange/remove-quarantinetag)。

## <a name="quarantine-policy-permission-details"></a>検疫ポリシーのアクセス許可の詳細

次のセクションでは、検疫済みメッセージの詳細およびエンドユーザーのスパム通知における事前設定されたアクセス許可グループと個々のアクセス許可の影響について説明します。

### <a name="preset-permissions-groups"></a>事前設定されたアクセス許可グループ

事前設定されたアクセス許可グループに含まれる個々のアクセス許可は、この記事の冒頭の表に示されています。

#### <a name="no-access"></a>アクセスなし

検疫ポリシーでアクセス許可なし(アクセス許可なし) が割り当て済みである場合、ユーザーは引き続きいくつかの基準機能を取得します。

- **検疫済みメッセージの詳細**: [ **メッセージ ヘッダーの表示] ボタン** は常に使用できます。

  ![検疫ポリシーでユーザーにアクセス許可がない場合、検疫済みメッセージの詳細で使用可能なボタン](../../media/quarantine-tags-quarantined-message-details-no-access.png)

- **エンドユーザーのスパム通知**: **検疫内** のメッセージにユーザーを移動する [確認] ボタンは常に使用できます。

  ![検疫ポリシーでユーザーにアクセス許可がない場合、エンド ユーザーのスパム通知で使用可能なボタン](../../media/quarantine-tags-esn-no-access.png)

#### <a name="limited-access"></a>制限付きアクセス

検疫ポリシーで制限付きアクセス許可 **が割り** 当てられている場合、ユーザーは次の機能を利用できます。

- **検疫済みメッセージの詳細**: 次のボタンを使用できます。
  - **リリースの要求**
  - **メッセージ ヘッダーの表示**
  - **プレビュー メッセージ**
  - **送信者をブロックする**
  - **検疫から削除する**

  ![検疫ポリシーがユーザーに制限付きアクセス許可を与える場合、検疫済みメッセージの詳細で使用可能なボタン](../../media/quarantine-tags-quarantined-message-details-limited-access.png)

- **エンド ユーザーのスパム通知**: 次のボタンを使用できます。
  - **送信者をブロックする**
  - **確認**

  ![検疫ポリシーがユーザーに制限付きアクセス許可を与える場合、エンド ユーザーのスパム通知で使用可能なボタン](../../media/quarantine-tags-esn-limited-access.png)

#### <a name="full-access"></a>フル アクセス

検疫ポリシーで [フル アクセス] **アクセス許可** (すべての使用可能なアクセス許可) が割り当て済みである場合、ユーザーは次の機能を利用できます。

- **検疫済みメッセージの詳細**: 次のボタンを使用できます。
  - **リリース メッセージ**
  - **メッセージ ヘッダーの表示**
  - **プレビュー メッセージ**
  - **送信者をブロックする**
  - **送信者を許可する**
  - **検疫から削除する**

  ![検疫ポリシーがユーザーにフル アクセスのアクセス許可を与える場合、検疫済みメッセージの詳細で使用可能なボタン](../../media/quarantine-tags-quarantined-message-details-full-access.png)

- **エンド ユーザーのスパム通知**: 次のボタンを使用できます。
  - **送信者をブロックする**
  - **リリース**
  - **確認**

  ![検疫ポリシーがユーザーにフル アクセスのアクセス許可を与える場合、エンド ユーザーのスパム通知で使用可能なボタン](../../media/quarantine-tags-esn-full-access.png)

### <a name="individual-permissions"></a>個々のアクセス許可

> [!NOTE]
> ユーザーは、[アクセスなし] セクションで説明されているボタンを常 [に取得](#no-access) します。 これらのボタンは、個々のアクセス許可の説明には含まれません。

#### <a name="allow-sender-permission"></a>送信者のアクセス許可を許可する

[**送信者の許可**]_(PermissionToAllowSender)_ はボタンへのアクセスを制御し、検疫済みメッセージ送信者を [送信者] リストに簡単に追加セーフします。

- **検疫済みメッセージの詳細**:
  - **[送信者のアクセス許可** を有効にする]: [送信者 **を許可する** ] ボタンを使用できます。
  - **[送信者のアクセス許可** を無効にする]: [送信者 **を許可する** ] ボタンは使用できません。

- **エンド ユーザーのスパム通知**: 無効です。

セーフ 送信者の一覧の詳細については、「信頼できる送信者が[](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379666)ブロックされるのを防ぐ」および[「use Exchange Online PowerShell](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox)を使用してメールボックスのセーフリスト コレクションを構成する」を参照してください。

#### <a name="block-sender-permission"></a>送信者のアクセス許可をブロックする

[ **送信者のブロック]** アクセス許可 _(PermissionToBlockSender)_ はボタンへのアクセスを制御し、検疫済みメッセージ送信者をブロックされた送信者リストに簡単に追加できます。

- **検疫済みメッセージの詳細**:
  - **[送信者のアクセス許可** をブロックする] を有効にする: **[送信者のブロック** ] ボタンを使用できます。
  - **[送信者のアクセス許可** を無効にする]: [ **送信者のブロック** ] ボタンは使用できません。

- **エンド ユーザーのスパム通知**:
  - **[送信者のアクセス許可** を無効にする]: [ **送信者のブロック** ] ボタンは使用できません。
  - **[送信者のアクセス許可** をブロックする] を有効にする: **[送信者のブロック** ] ボタンを使用できます。

[送信者のブロック] リストの詳細については、「他[](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379667)のユーザーからのメッセージをブロックする」および[「Use Exchange Online PowerShell](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox)を使用してメールボックスのセーフリスト コレクションを構成する」を参照してください。

#### <a name="delete-permission"></a>削除のアクセス許可

[ **削除]** アクセス許可 _(PermissionToDelete)_ は、ユーザーが検疫からメッセージ (ユーザーが受信者であるメッセージ) を削除する機能を制御します。

- **検疫済みメッセージの詳細**:
  - **アクセス許可** の削除が有効: [ **検疫から削除] ボタン** を使用できます。
  - **削除** のアクセス許可が無効: [ **検疫から削除] ボタン** は使用できません。

- **エンド ユーザーのスパム通知**: 無効です。

#### <a name="preview-permission"></a>プレビューのアクセス許可

[ **プレビュー]** アクセス許可 _(PermissionToPreview)_ は、ユーザーが検疫でメッセージをプレビューする機能を制御します。

- **検疫済みメッセージの詳細**:
  - **プレビュー** のアクセス許可が有効: **[メッセージのプレビュー] ボタン** を使用できます。
  - **プレビュー** のアクセス許可が無効: **[メッセージのプレビュー]** ボタンは使用できません。

- **エンド ユーザーのスパム通知**: 無効です。

#### <a name="allow-recipients-to-release-a-message-from-quarantine-permission"></a>受信者が検疫のアクセス許可からメッセージを解放するを許可する

[ **受信者に検疫** からのメッセージの解放を許可する] アクセス許可 _(PermissionToRelease)_ は、ユーザーが管理者の承認なしに検疫済みメッセージを直接解放する機能を制御します。

- **検疫済みメッセージの詳細**:
  - アクセス許可が有効: **[メッセージの解放] ボタン** を使用できます。
  - アクセス許可が無効: **[メッセージの解放]** ボタンは使用できません。

- **エンド ユーザーのスパム通知**:
  - アクセス許可が有効: **[リリース]** ボタンを使用できます。
  - アクセス許可が無効: **[リリース]** ボタンは使用できません。

#### <a name="allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission"></a>受信者が検疫アクセス許可からメッセージを解放する要求を許可する

[**受信者に検疫** からのメッセージの解放を要求する] アクセス許可 _(PermissionToRequestRelease)_ は、ユーザーが検疫済みメッセージのリリースを要求する機能を制御します。 メッセージは、管理者が要求を承認した後にのみ解放されます。

- **検疫済みメッセージの詳細**:
  - アクセス許可が有効: **[要求] リリース ボタン** を使用できます。
  - アクセス許可が無効: **[要求] リリース** ボタンは使用できません。

- **エンドユーザーのスパム通知**: [ **リリース] ボタン** は使用できません。
