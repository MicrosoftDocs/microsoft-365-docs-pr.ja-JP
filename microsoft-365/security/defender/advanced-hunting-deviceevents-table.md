---
title: 高度な検索スキーマの DeviceEvents テーブル
description: 高度なハンティング スキーマのその他のデバイス イベント (DeviceEvents) テーブルのウイルス対策、ファイアウォール、その他のイベントの種類について説明します。
keywords: 高度な狩猟、脅威の検出、サイバー脅威の検出、Microsoft 365 Defender、microsoft 365、m365、検索、クエリ、テレメトリ、スキーマ参照、kusto、table、column、データ型、セキュリティ イベント、ウイルス対策、ファイアウォール、エクスプロイト ガード、DeviceEvents
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
ms.openlocfilehash: 63a2d41714329918192caccd384587a4e4f04112
ms.sourcegitcommit: 72795ec56a7c4db863dcaaff5e9f7c41c653fda8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2021
ms.locfileid: "52023203"
---
# <a name="deviceevents"></a>DeviceEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**適用対象:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

高度な検索スキーマのその他のデバイス イベントまたはテーブルには、セキュリティ制御によってトリガーされるイベント (Windows Defender ウイルス対策やエクスプロイト保護など) に関するさまざまなイベント `DeviceEvents` の種類に関する情報が含まれています。 [](advanced-hunting-overview.md) このテーブルの情報を返すクエリを作成するには、このリファレンスを使用します。

>[!TIP]
> テーブルでサポートされるイベントの種類 (値) の詳細については、セキュリティ センターで使用できる組み込みのスキーマ参照 `ActionType` を使用します。

高度な捜索スキーマのその他のテーブルの詳細については、「[高度な捜索のリファレンス](advanced-hunting-schema-tables.md)」 を参照してください。


| 列名 | データ型 | 説明 |
|-------------|-----------|-------------|
| `Timestamp` | 日付型 | イベントが記録された日付と時刻 |
| `DeviceId` | string | コンピューターの一意識別子 |
| `DeviceName` | string | コンピューターの完全修飾ドメイン名 (FQDN) |
| `ActionType` | string | イベントをトリガーしたアクティビティの種類。 詳細については [、ポータル内スキーマリファレンス](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) を参照してください。 |
| `FileName` | 文字列 | 記録されたアクションが適用されたファイルの名前 |
| `FolderPath` | 文字列 | 記録されたアクションが適用されたファイルを含むフォルダー |
| `SHA1` | 文字列 | 記録されたアクションが適用されたファイルの SHA-1 |
| `SHA256` | 文字列 | 記録されたアクションが適用されたファイルの SHA-256 このフィールドは通常は入力されません。使用可能な場合は、SHA1 列を使用します。 |
| `MD5` | 文字列型 | 記録されたアクションが適用されたファイルの MD5 ハッシュ |
| `FileSize` | long | ファイルのサイズ (バイト単位) |
| `AccountDomain` | string | アカウントのドメイン |
| `AccountName` | string | アカウントのユーザー名 |
| `AccountSid` | string | アカウントのセキュリティ識別子 (SID) |
| `RemoteUrl` | 文字列 | に接続されていた URL または完全修飾ドメイン名 (FQDN) |
| `RemoteDeviceName` | 文字列 | 影響を受けるコンピューターでリモート操作を実行したコンピューターの名前。 報告されるイベントに応じて、この名前には完全修飾ドメイン名 (FQDN)、NetBIOS 名、またはドメイン情報のないホスト名を指定できます。 |
| `ProcessId` | int | 新しく作成されたプロセスのプロセス ID (PID) |
| `ProcessCommandLine` | string | 新しいプロセスの作成に使用するコマンド ライン |
| `ProcessCreationTime` | 日付型 | プロセスが作成された日時 |
| `ProcessTokenElevation` | string | 新しく作成されたプロセスに適用されるユーザー アクセス制御 (UAC) 特権昇格の有無を示すトークンの種類 |
| `LogonId` | string | ログオン セッションの識別子。 この識別子は、再起動の間にのみ同じコンピューター上で一意です。 |
| `RegistryKey` | string | 記録されたアクションが適用されたレジストリ キー |
| `RegistryValueName` | string | 記録されたアクションが適用されたレジストリ値の名前 |
| `RegistryValueData` | string | 記録されたアクションが適用されたレジストリ値のデータ |
| `RemoteIP` | 文字列 | に接続されていた IP アドレス |
| `RemotePort` | int | 接続されているリモート デバイスの TCP ポート |
| `LocalIP` | string | 通信中に使用されるローカル コンピューターに割り当てられた IP アドレス |
| `LocalPort` | int | 通信中に使用されるローカル コンピューター上の TCP ポート |
| `FileOriginUrl` | string | ファイルがダウンロードされた URL |
| `FileOriginIP` | string | ファイルがダウンロードされた IP アドレス |
| `InitiatingProcessSHA1` | string | イベントを開始したプロセス (イメージ ファイル) の SHA-1 |
| `InitiatingProcessSHA256` | string | イベントを開始したプロセス (イメージ ファイル) の SHA-256。 このフィールドは通常は入力されません。使用可能な場合は、SHA1 列を使用します。 |
| `InitiatingProcessMD5` | 文字列型 | イベントを開始したプロセス (イメージ ファイル) の MD5 ハッシュ |
| `InitiatingProcessFileName` | string | イベントを開始したプロセスの名前 |
| `InitiatingProcessFileSize` | long | イベントの処理を実行したファイルのサイズ |
| `InitiatingProcessFolderPath` | string | イベントを開始したプロセス (イメージ ファイル) を含むフォルダー |
| `InitiatingProcessId` | int | イベントを開始したプロセスのプロセス ID (PID) |
| `InitiatingProcessCommandLine` | string | イベントを開始したプロセスの実行に使用されるコマンド ライン |
| `InitiatingProcessCreationTime` | 日付型 | イベントを開始したプロセスが開始された日時 |
| `InitiatingProcessAccountDomain` | string | イベントを担当するプロセスを実行したアカウントのドメイン |
| `InitiatingProcessAccountName` | string | イベントを担当するプロセスを実行したアカウントのユーザー名 |
| `InitiatingProcessAccountSid` | string | イベントを担当するプロセスを実行したアカウントのセキュリティ識別子 (SID) |
| `InitiatingProcessAccountUpn` | string | イベントを担当するプロセスを実行したアカウントのユーザー プリンシパル名 (UPN) |
| `InitiatingProcessAccountObjectId` | string | Azure ADを実行したユーザー アカウントのオブジェクト ID を指定します。 |
| `InitiatingProcessVersionInfoCompanyName` | string | イベントを担当するプロセスのバージョン情報 (イメージ ファイル) からの会社名 |
| `InitiatingProcessVersionInfoProductName` | string | イベントを担当するプロセス (イメージ ファイル) のバージョン情報からの製品名 |
| `InitiatingProcessVersionInfoProductVersion` | string | イベントを担当するプロセスのバージョン情報 (イメージ ファイル) からの製品バージョン |
|` InitiatingProcessVersionInfoInternalFileName` | string | イベントを担当するプロセスのバージョン情報 (イメージ ファイル) からの内部ファイル名 |
| `InitiatingProcessVersionInfoOriginalFileName` | string | イベントを担当するプロセスのバージョン情報 (イメージ ファイル) からの元のファイル名 |
| `InitiatingProcessVersionInfoFileDescription` | string | イベントを担当するプロセス (イメージ ファイル) のバージョン情報の説明 |
| `InitiatingProcessParentId` | int | イベントを担当するプロセスを生成した親プロセスのプロセス ID (PID) |
| `InitiatingProcessParentFileName` | string | イベントを担当するプロセスを生成した親プロセスの名前 |
| `InitiatingProcessParentCreationTime` | 日付型 | イベントを担当するプロセスの親が開始された日時 |
| `InitiatingProcessLogonId` | string | イベントを開始したプロセスのログオン セッションの識別子。 この識別子は、再起動の間にのみ同じコンピューター上で一意です。 |
| `ReportId` | long | 繰り返しカウンターに基づくイベント識別子。 一意のイベントを識別するには、この列を DeviceName 列と Timestamp 列と組み合わせて使用する必要があります。 |
| `AppGuardContainerId` | string | ブラウザーのアクティビティを分離するために Application Guard が使用する仮想化コンテナーの識別子 |
| `AdditionalFields` | string | JSON 配列形式のイベントに関する追加情報 |

## <a name="related-topics"></a>関連項目
- [高度な追求の概要](advanced-hunting-overview.md)
- [クエリ言語の説明](advanced-hunting-query-language.md)
- [共有クエリを使用する](advanced-hunting-shared-queries.md)
- [デバイス、メール、アプリ、ID 全体で探す](advanced-hunting-query-emails-devices.md)
- [スキーマを理解する](advanced-hunting-schema-tables.md)
- [クエリのベスト プラクティスを適用する](advanced-hunting-best-practices.md)
