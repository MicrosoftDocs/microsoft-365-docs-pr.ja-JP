---
title: 高度な検索スキーマの EmailEvents テーブル
description: 高度な検索スキーマの emailEvents Microsoft 365メールに関連付けられているイベントについて説明します。
keywords: 高度な狩猟、脅威の検出、サイバー脅威の検出、Microsoft 365 Defender、microsoft 365、m365、検索、クエリ、テレメトリ、スキーマ参照、kusto、テーブル、列、データ型、説明、EmailEvents、ネットワーク メッセージ ID、送信者、受信者、添付ファイル ID、添付ファイル名、マルウェアの評決、フィッシングの評決、添付ファイル数、リンク数、URL カウント
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
ms.technology: m365d
ms.openlocfilehash: 18d3d768b672364f730b042239ae9fa0042f95f6
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2021
ms.locfileid: "51935487"
---
# <a name="emailevents"></a>EmailEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**適用対象:**

- Microsoft 365 Defender

高度 `EmailEvents` な検索スキーマの[表](advanced-hunting-overview.md)には、Microsoft Defender の電子メールの処理に関連するイベントに関する情報が含Office 365。 このテーブルの情報を返すクエリを作成するには、このリファレンスを使用します。

>[!TIP]
> テーブルでサポートされるイベントの種類 (値) の詳細については、セキュリティ センターで使用できる組み込みのスキーマ参照 `ActionType` を使用します。

高度な捜索スキーマのその他のテーブルの詳細については、「[高度な捜索のリファレンス](advanced-hunting-schema-tables.md)」 を参照してください。

| 列名 | データ型 | 説明 |
|-------------|-----------|-------------|
| `Timestamp` | 日付型 | イベントが記録された日付と時刻 |
| `NetworkMessageId` | string | ユーザーが生成する電子メールの一意Microsoft 365 |
| `InternetMessageId` | string | 送信メール システムにより設定された、メールの一般向けの識別子 |
| `SenderMailFromAddress` | string | MAIL FROM ヘッダーの送信者メール アドレス (エンベロープ送信者またはリターン パス アドレスとも呼ばれる) |
| `SenderFromAddress` | string | 受信者のメール クライアントで受信者に表示される、FROM ヘッダーの送信者メール アドレス |
| `SenderDisplayName` | string | アドレス帳に表示される送信者の名前(通常は、特定の名前または名、ミドル イニシャル、姓または姓の組み合わせ) |
| `SenderObjectId` | string |Azure アカウントの送信者のアカウントの一意AD |
| `SenderMailFromDomain` | string | MAIL FROM ヘッダーの送信者ドメイン (エンベロープ送信者またはリターン パス アドレスとも呼ばれる) |
| `SenderFromDomain` | string | 受信者のメール クライアントで受信者に表示される、MAIL FROM ヘッダーの送信者ドメイン |
| `SenderIPv4` | string | 検出された、最後にメッセージをリレーしたメール サーバーの IPv4 アドレス |
| `SenderIPv6` | string | 検出された、最後にメッセージをリレーしたメール サーバーの IPv6 アドレス |
| `RecipientEmailAddress` | string | 受信者のメール アドレス、または配布リストの展開後の受信者のメール アドレス |
| `RecipientObjectId` | string | Azure の電子メール受信者の一意AD |
| `Subject` | string | メールの件名 |
| `EmailClusterId` | string | コンテンツのヒューリスティック分析に基づいてまとめられた、似通ったメールのグループの識別子 |
| `EmailDirection` | string | ネットワークに対するメールの方向: Inbound、Outbound、Intra-org |
| `DeliveryAction` | string | メールの配信アクション: Delivered、Junked、Blocked、または Replaced |
| `DeliveryLocation` | string | メールの配信場所: 受信トレイ/フォルダー、オンプレミス/外部、迷惑メール、検疫、失敗、中断、削除済みアイテム |
| `ThreatTypes` | string | 電子メールにマルウェア、フィッシング、その他の脅威が含まれているかどうかに関する電子メール フィルター スタックからの評決 |
| `ThreatNames` | string |マルウェアまたは検出された他の脅威の検出名 |
| `DetectionMethods` | string | 電子メールで見つかったマルウェア、フィッシング、その他の脅威を検出するために使用される方法 |
| `ConfidenceLevel` | string | スパムまたはフィッシングの評決の信頼レベルの一覧。 スパムの場合、この列にはスパム信頼レベル (SCL) が表示され、電子メールがスキップされた (-1)、スパムではない (0,1)、中程度の信頼度を持つスパム (5,6) が検出された、または高い信頼度を持つスパムである (9) ことを示します。 フィッシングの場合、この列には信頼度が "高" か "低" かを表示します。 |
| `EmailAction` | string | フィルターの判定、ポリシー、ユーザー アクションに基づいてメールに対して実行される最終的なアクション: メッセージを迷惑メール フォルダーに移動、X-ヘッダーの追加、件名の変更、メッセージのリダイレクト、メッセージの削除、検疫フォルダーへの配信、アクションなし、Bcc メッセージ |
| `EmailActionPolicy` | string | 適用されたアクション ポリシー: 高信頼度のスパム対策、スパム対策、バルク メール スパム対策、フィッシング スパム対策、ドメイン偽装フィッシング対策、ユーザー偽装フィッシング対策、スプーフィング フィッシング対策、グラフ偽装フィッシング対策、マルウェア対策、安全な添付ファイル、Enterprise Transport Rules (ETR) |
| `EmailActionPolicyGuid` | string | メールに対する最終アクションを決定したポリシーの一意の識別子 |
| `AttachmentCount` | int | メール内の添付ファイル数 |
| `UrlCount` | int | メールに埋め込まれている URL の数 |
| `EmailLanguage` | string | 検出されたメールのコンテンツの言語 |
| `Connectors` | string | 組織のメール フローと電子メールのルーティング方法を定義するカスタム手順 |
| `OrgLevelAction` | string | 組織レベルで定義されたポリシーとの一致に対応して電子メールに対して実行されるアクション |
| `OrgLevelPolicy` | string | 電子メールで実行されたアクションをトリガーした組織ポリシー |
| `UserLevelAction` | string | 受信者によって定義されたメールボックス ポリシーとの一致に応答して電子メールに対して実行されるアクション |
| `UserLevelPolicy` | string | 電子メールで実行されたアクションをトリガーしたエンド ユーザー メールボックス ポリシー |
| `ReportId` | long | 繰り返しカウンターに基づくイベント識別子。 一意のイベントを識別するには、この列を DeviceName 列と Timestamp 列と組み合わせて使用する必要があります。 |

## <a name="related-topics"></a>関連項目

- [高度な追求の概要](advanced-hunting-overview.md)
- [クエリ言語の説明](advanced-hunting-query-language.md)
- [共有クエリを使用する](advanced-hunting-shared-queries.md)
- [デバイス、メール、アプリ、ID 全体で探す](advanced-hunting-query-emails-devices.md)
- [スキーマを理解する](advanced-hunting-schema-tables.md)
- [クエリのベスト プラクティスを適用する](advanced-hunting-best-practices.md)
