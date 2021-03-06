---
title: Microsoft Defender for Endpoint から高度なハンティング クエリを移行する
description: Microsoft Defender for Endpoint クエリを調整して、Microsoft Defender で使用する方法Microsoft 365する
keywords: 高度な狩猟、脅威の検出、サイバー脅威の検出、Microsoft 365 Defender、microsoft 365、m365、Microsoft Defender for Endpoint、検索、クエリ、テレメトリ、カスタム検出、スキーマ、kusto、マッピング
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.technology: m365d
ms.openlocfilehash: ba6f84f9f08d0635dab6ac65eaa697b8e0e73df7
ms.sourcegitcommit: fb6c5e04ade1e82b26b2f911577b5ac721f1c544
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2021
ms.locfileid: "52470690"
---
# <a name="migrate-advanced-hunting-queries-from-microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpoint から高度なハンティング クエリを移行する

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**適用対象:**
- Microsoft 365 Defender

高度なハンティング ワークフローを Microsoft Defender for Endpoint から移動して、より広範なデータセットを使用して脅威を積極的に検出します。 Defender Microsoft 365、次を含む他のセキュリティ ソリューションMicrosoft 365データにアクセスできます。

- Microsoft Defender for Endpoint
- Microsoft Defender for Office 365
- Microsoft Cloud App Security
- Microsoft Defender for Identity

>[!NOTE]
>ほとんどの Microsoft Defender for Endpoint のお客様は、追加のライセンスなしで Microsoft 365 [Defender を使用できます](prerequisites.md#licensing-requirements)。 Defender for Endpoint から高度なハンティング ワークフローの移行を開始するには、Defender のMicrosoft 365[します](m365d-enable.md)。

既存の Defender for Endpoint ワークフローに影響を与えることなく移行できます。 保存されたクエリはそのまま残り、カスタム検出ルールは引き続き実行され、アラートが生成されます。 ただし、Defender で表示Microsoft 365されます。 

## <a name="schema-tables-in-microsoft-365-defender-only"></a>Defender のスキーマ テーブルMicrosoft 365のみ
Defender [Microsoft 365高度な検索スキーマには、](advanced-hunting-schema-tables.md)さまざまなセキュリティ ソリューションのデータを含むMicrosoft 365があります。 次の表は、Defender のMicrosoft 365です。

| テーブル名 | 説明 |
|------------|-------------|
| [AlertEvidence](advanced-hunting-alertevidence-table.md) | アラートに関連付けられたファイル、IP アドレス、URL、ユーザー、またはデバイス |
| [AlertInfo](advanced-hunting-alertinfo-table.md) | Microsoft Defender for Endpoint、Microsoft Defender for Office 365、Microsoft Cloud App Security、Microsoft Defender for Identity からのアラート (重大度情報と脅威カテゴリを含む)  |
| [EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) | メールに添付されているファイルに関する情報 |
| [EmailEvents](advanced-hunting-emailevents-table.md) | Microsoft 365配信イベントやブロック イベントを含む電子メール イベントの管理 |
| [EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md) | 受信者メールボックスに電子メールを配信した後Microsoft 365配信後に発生するセキュリティ イベント |
| [EmailUrlInfo](advanced-hunting-emailurlinfo-table.md) | メールの URL に関する情報 |
| [IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md) | Active Directory を実行しているオンプレミスのドメイン コントローラーに関連するイベント (AD)。 次の表では、ドメイン コントローラー上の ID 関連イベントとシステム イベントの範囲について説明します。 |
| [IdentityInfo](advanced-hunting-identityinfo-table.md) | さまざまなソースからのアカウント情報 (Azure Active Directory |
| [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) | Active Directory および Microsoft オンライン サービスでの認証イベント |
| [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md) | ユーザー、グループ、デバイス、ドメインなどの Active Directory オブジェクトのクエリ |

>[!IMPORTANT]
> Defender でしか使用できないスキーマ テーブルを使用するクエリとカスタム検出Microsoft 365 Defender でのみMicrosoft 365できます。

## <a name="map-devicealertevents-table"></a>DeviceAlertEvents テーブルのマップ
テーブル `AlertInfo` と `AlertEvidence` テーブルは `DeviceAlertEvents` 、Microsoft Defender for Endpoint スキーマのテーブルを置き換える。 デバイス通知に関するデータに加えて、これら 2 つのテーブルには、ID、アプリ、および電子メールのアラートに関するデータが含まれます。

次の表を使用して、列 `DeviceAlertEvents` が列とテーブルの列にマップされる方法 `AlertInfo` を確認 `AlertEvidence` します。

>[!TIP]
>次の表の列に加えて、さまざまなソースからのアラートの全体的な画像を提供する他の多くの列 `AlertEvidence` も含まれています。 [すべての AlertEvidence 列を表示する](advanced-hunting-alertevidence-table.md) 

| DeviceAlertEvents 列 | Defender で同じデータをMicrosoft 365する |
|-------------|-----------|-------------|-------------|
| `AlertId` | `AlertInfo` テーブル  `AlertEvidence` とテーブル |
| `Timestamp` | `AlertInfo` テーブル  `AlertEvidence` とテーブル |
| `DeviceId` | `AlertEvidence` table |
| `DeviceName` | `AlertEvidence` table |
| `Severity` | `AlertInfo` table |
| `Category` | `AlertInfo` table |
| `Title` | `AlertInfo` table |
| `FileName` | `AlertEvidence` table |
| `SHA1` | `AlertEvidence` table |
| `RemoteUrl` | `AlertEvidence` table |
| `RemoteIP` | `AlertEvidence` table |
| `AttackTechniques` | `AlertInfo` table |
| `ReportId` | この列は、通常、Microsoft Defender for Endpoint で他のテーブル内の関連レコードを検索するために使用されます。 Defender Microsoft 365、関連するデータをテーブルから直接取得 `AlertEvidence` できます。 |
| `Table` | この列は、通常、Microsoft Defender for Endpoint で他のテーブルの追加イベント情報として使用されます。 Defender Microsoft 365、関連するデータをテーブルから直接取得 `AlertEvidence` できます。 |

## <a name="adjust-existing-microsoft-defender-for-endpoint-queries"></a>既存の Microsoft Defender for Endpoint クエリを調整する
Microsoft Defender for Endpoint クエリは、テーブルを参照しない限り、現在通り動作 `DeviceAlertEvents` します。 Defender でこれらのクエリを使用するにはMicrosoft 365変更を適用します。

- に `DeviceAlertEvents` 置き換える `AlertInfo` 。
- テーブルとテーブル `AlertInfo` を `AlertEvidence` 結合して `AlertId` 同等のデータを取得します。

### <a name="original-query"></a>元のクエリ
次のクエリは `DeviceAlertEvents` 、Microsoft Defender for Endpoint で使用して、エンドポイントに関連するアラートをpowershell.exe。

```kusto
DeviceAlertEvents
| where Timestamp > ago(7d) 
| where AttackTechniques has "PowerShell (T1086)" and FileName == "powershell.exe"
```
### <a name="modified-query"></a>変更されたクエリ
次のクエリは、Defender で使用Microsoft 365されています。 ファイル名を直接からチェックする代わりに、そのテーブル内のファイル名を結合 `DeviceAlertEvents` `AlertEvidence` してチェックします。

```kusto
AlertInfo 
| where Timestamp > ago(7d) 
| where AttackTechniques has "PowerShell (T1086)" 
| join AlertEvidence on AlertId
| where FileName == "powershell.exe"
```

## <a name="migrate-custom-detection-rules"></a>カスタム検出ルールの移行

Microsoft Defender for Endpoint ルールが Defender で編集Microsoft 365、結果のクエリがデバイス テーブルのみを参照する場合と同様に機能し続ける。 

たとえば、デバイス テーブルのみをクエリするカスタム検出ルールによって生成されたアラートは、Microsoft Defender for Endpoint での構成方法に応じて、引き続き SIEM に配信され、電子メール通知を生成します。 Defender for Endpoint の既存の抑制ルールも引き続き適用されます。

エンドポイントの Defender ルールを編集して、Microsoft 365 Defender でのみ使用可能な ID テーブルと電子メール テーブルを照会すると、そのルールは自動的に Microsoft 365 Defender に移動されます。 

移行されたルールによって生成されるアラート:

- Defender for Endpoint ポータルに表示されなくなりました (Microsoft Defender セキュリティ センター)
- SIEM への配信を停止するか、電子メール通知を生成します。 この変更を回避するには、アラートを取得するために、Microsoft 365 Defender 経由で通知を構成します。 Defender API のMicrosoft 365[を](api-incident.md)使用して、顧客検出アラートまたは関連インシデントに関する通知を受信できます。
- Microsoft Defender for Endpoint 抑制ルールでは抑制されません。 特定のユーザー、デバイス、またはメールボックスに対してアラートが生成されるのを防ぐために、対応するクエリを変更して、それらのエンティティを明示的に除外します。

この方法でルールを編集すると、そのような変更が適用される前に確認を求めるメッセージが表示されます。

Defender ポータル内のカスタム検出ルールによってMicrosoft 365新しいアラートは、次の情報を提供するアラート ページに表示されます。

- アラートのタイトルと説明 
- 影響を受け取ったアセット
- アラートに応答して実行されるアクション
- アラートをトリガーしたクエリ結果 
- カスタム検出ルールに関する情報 
 
> [!div class="mx-imgBorder"]
> ![新しいアラート ページのイメージ](../../media/new-alert-page.png)

## <a name="write-queries-without-devicealertevents"></a>DeviceAlertEvents を使用せずにクエリを書き込む

Defender スキーマMicrosoft 365では、さまざまなソースからのアラートに付随するさまざまな情報のセットに対応するために、テーブル `AlertInfo` `AlertEvidence` とテーブルが提供されます。 

Microsoft Defender for Endpoint スキーマのテーブルから取得したのと同じアラート情報を取得するには、テーブルをフィルター処理し、各一意 `DeviceAlertEvents` `AlertInfo` の `ServiceSource` ID `AlertEvidence` をテーブルに結合して、詳細なイベントとエンティティ情報を提供します。 

以下のサンプル クエリを参照してください。

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
| join AlertEvidence on AlertId
```

このクエリは、Microsoft Defender for Endpoint スキーマよりも `DeviceAlertEvents` 多くの列を生成します。 結果を管理し続けるには、関心 `project` のある列のみを取得します。 次の例では、調査で PowerShell アクティビティが検出された場合に関心のある列をプロジェクトします。

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
    and AttackTechniques has "powershell"
| join AlertEvidence on AlertId
| project Timestamp, Title, AlertId, DeviceName, FileName, ProcessCommandLine 
```

アラートに関連する特定のエンティティをフィルター処理する場合は、エンティティの種類とフィルター処理する値を指定します `EntityType` 。 次の例では、特定の IP アドレスを検索します。

```kusto
AlertInfo
| where Title == "Insert_your_alert_title"
| join AlertEvidence on AlertId 
| where EntityType == "Ip" and RemoteIP == "192.88.99.01" 
```

## <a name="see-also"></a>関連項目
- [Microsoft 365 Defender を有効にする](advanced-hunting-query-language.md)
- [高度な追求の概要](advanced-hunting-overview.md)
- [スキーマを理解する](advanced-hunting-schema-tables.md)
- [エンドポイント向け Microsoft Defender での高度な検索](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)