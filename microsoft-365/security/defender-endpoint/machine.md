---
title: コンピューター リソースの種類
description: Microsoft Defender for Endpoint の Machine リソースタイプのメソッドとプロパティについて説明します。
keywords: apis、サポートされている api、get、コンピューター
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 5ca147c9e69168b2f15aa69bba8728567b782fa9
ms.sourcegitcommit: 34c06715e036255faa75c66ebf95c12a85f8ef42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2021
ms.locfileid: "52984462"
---
# <a name="machine-resource-type"></a>コンピューター リソースの種類

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>メソッド

メソッド|戻り値の型 |説明
:---|:---|:---
[マシンの一覧表示](get-machines.md) | [machine](machine.md) コレクション | 組織のコンピューター [エンティティ](machine.md) のセットを一覧表示します。
[コンピューターの取得](get-machine-by-id.md) | [コンピューター](machine.md) | コンピューターの [ID を](machine.md) 使用してコンピューターを取得します。
[ログオンしているユーザーを取得する](get-machine-log-on-users.md) | [user](user.md) コレクション | コンピューターにログオン [したユーザー](user.md) のセットを取得 [します](machine.md)。
[関連するアラートを取得する](get-machine-related-alerts.md) | [alert](alerts.md) コレクション | コンピューターで発生 [した](alerts.md) アラート エンティティのセットを取得 [します](machine.md)。
[インストールされたソフトウェアを取得する](get-installed-software.md) | [ソフトウェア](software.md) コレクション | 特定のコンピューター ID に関連するインストール済みソフトウェアのコレクションを取得します。
[検出された脆弱性を取得する](get-discovered-vulnerabilities.md) | [脆弱性の](vulnerability.md) コレクション | 特定のコンピューター ID に関連する検出された脆弱性のコレクションを取得します。
[セキュリティ上の推奨事項を取得する](get-security-recommendations.md) | [おすすめ](recommendation.md) コレクション | 特定のコンピューター ID に関連するセキュリティ推奨事項のコレクションを取得します。
[マシン タグの追加または削除](add-or-remove-machine-tags.md) | [コンピューター](machine.md) | 特定のコンピューターにタグを追加または削除します。
[IP でマシンを検出する](find-machines-by-ip.md) | [machine](machine.md) コレクション | IP で見られるコンピューターを検索します。
[タグでマシンを検出する](find-machines-by-tag.md) | [machine](machine.md) コレクション | タグでコンピューターを [検索します](machine-tags.md)。
[不足している KB を取得する](get-missing-kbs-machine.md) | KB コレクション | コンピューター ID に関連付けられている不足している KB の一覧を取得する
[デバイス値の設定](set-device-value.md)| [machine](machine.md) コレクション | デバイスの [値を設定します](tvm-assign-device-value.md)。
[コンピューターの更新](update-machine-method.md) |[machine](machine.md) コレクション | コンピューターの更新状態を取得します。

## <a name="properties"></a>プロパティ

プロパティ |   種類   |   説明
:---|:---|:---
id | String | [マシン](machine.md) ID。
computerDnsName | String | [コンピューター](machine.md) の完全修飾名。
firstSeen | DateTimeOffset | Microsoft Defender for [](machine.md) Endpoint によってコンピューターが観測された最初の日付と時刻。
lastSeen | DateTimeOffset |最後に受信した完全なデバイス レポートの時刻と日付。 通常、デバイスは 24 時間ごとに完全なレポートを送信します。
osPlatform | String | オペレーティング システム プラットフォーム。
osProcessor | String | オペレーティング システム プロセッサ。 代わりに osArchitecture プロパティを使用します。
version | String | オペレーティング システムのバージョン。
osBuild | Null 許容長 | オペレーティング システムのビルド番号。
lastIpAddress | String | コンピューター上のローカル NIC の最後の[IP。](machine.md)
lastExternalIpAddress | String | コンピューターがインターネットに [アクセスした](machine.md) 最後の IP。
healthStatus | 列挙 | [マシンの](machine.md) 正常性状態。 指定できる値は、"Active"、"Inactive"、"ImpairedCommunication"、"NoSensorData"、"NoSensorDataImpairedCommunication"、"Unknown" です。 
rbacGroupName | String | コンピューター グループ名。
riskScore | Null 許容列挙 | Microsoft Defender for Endpoint によって評価されるリスク スコア。 指定できる値は、'None'、'Informational'、'Low'、'Medium'、および 'High' です。
exposureScore | Null 許容列挙 | [Microsoft](tvm-exposure-score.md) Defender for Endpoint によって評価される露出スコア。 指定できる値は、'None'、'Low'、'Medium'、および 'High' です。
aadDeviceId | Null 許容表現 Guid | AAD デバイス ID ( [コンピューターが](machine.md) AAD 参加している場合)。
machineTags | String コレクション | コンピューター タグ [の](machine.md) セット。
exposureLevel | Null 許容列挙 | Microsoft Defender for Endpoint によって評価される露出レベル。 指定できる値は、'None'、'Low'、'Medium'、および 'High' です。
deviceValue | Null 許容列挙 | デバイス [の値](tvm-assign-device-value.md)です。 指定できる値は、'Normal'、'Low'、および 'High' です。
ipAddresses | IpAddress コレクション | ***IpAddress オブジェクトの*** セット。 「Get [machines API」を参照してください](get-machines.md)。
osArchitecture | String | オペレーティング システムのアーキテクチャ。 指定できる値は、"32 ビット"、"64 ビット" です。 osProcessor の代わりにこのプロパティを使用します。


