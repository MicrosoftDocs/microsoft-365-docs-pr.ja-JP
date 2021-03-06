---
title: machineAction リソースの種類
description: Microsoft Defender for Endpoint の MachineAction リソースタイプのメソッドとプロパティについて説明します。
keywords: apis, サポートされている api, get, machineaction, recent
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
ms.technology: mde
ms.openlocfilehash: a3b017a9a05964c15411668787b035f1052c68cf
ms.sourcegitcommit: 337e8d8a2fee112d799edd8a0e04b3a2f124f900
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/10/2021
ms.locfileid: "52878282"
---
# <a name="machineaction-resource-type"></a>MachineAction リソースの種類

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


- 詳細については、「応答アクション [」を参照してください](respond-machine-alerts.md)。 

| メソッド                                                            | 戻り値の型                        | 説明                                                 |
|:------------------------------------------------------------------|:-----------------------------------|:------------------------------------------------------------|
| [MachineActions の一覧表示](get-machineactions-collection.md)           | [マシン アクション](machineaction.md) | [ [マシン アクション] エンティティを](machineaction.md) 一覧表示します。           |
| [MachineAction の取得](get-machineaction-object.md)                  | [マシン アクション](machineaction.md) | 単一の [Machine Action エンティティを取得](machineaction.md) します。     |
| [調査パッケージの収集](collect-investigation-package.md) | [マシン アクション](machineaction.md) | コンピューターから調査パッケージを収集 [します](machine.md)。 |
| [調査パッケージ SAS URI の取得](get-package-sas-uri.md)       | [マシン アクション](machineaction.md) | 調査パッケージをダウンロードするための URI を取得します。          |
| [マシンの隔離](isolate-machine.md)                             | [マシン アクション](machineaction.md) | ネットワーク [からコンピューター](machine.md) を分離します。                 |
| [マシンを隔離から解放する](unisolate-machine.md)            | [マシン アクション](machineaction.md) | 分離 [からコンピューター](machine.md) を解放します。               |
| [アプリの実行を制限する](restrict-code-execution.md)              | [マシン アクション](machineaction.md) | アプリケーションの実行を制限します。                             |
| [アプリの制限を削除する](unrestrict-code-execution.md)            | [マシン アクション](machineaction.md) | アプリケーションの実行制限を削除します。                   |
| [ウイルス対策スキャンを実行する](run-av-scan.md)                              | [マシン アクション](machineaction.md) | アプリケーションを使用して AV スキャンWindows Defender実行します (該当する場合)。    |
| [マシンのオフボード](offboard-machine-api.md)                       | [マシン アクション](machineaction.md) | Microsoft [Defender](machine.md) for Endpoint のオフボード マシン。 |
| [ファイルの停止と検疫](stop-and-quarantine-file.md)           | [マシン アクション](machineaction.md) | コンピューター上のファイルの実行を停止し、削除します。        |
| [ライブ応答の実行](run-live-response.md)                     | [マシン アクション](machineaction.md)  | デバイスで一連のライブ応答コマンドを実行する                       |
| [ライブ応答の結果を取得する](get-live-response-result.md) | URL エンティティ      | インデックスによって特定のライブ応答コマンドの結果ダウンロード リンクを取得します。 |
|[コンピューターの操作をキャンセルする](cancel-machine-action.md)                                | [マシン アクション](machineaction.md)  | アクティブなコンピューターの操作を取り消します。                                            |

<br>

## <a name="properties"></a>プロパティ

| プロパティ            | 型           | 説明                                                                                                                                                                                                    |
|:--------------------|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID                  | Guid           | Machine [Action エンティティの](machineaction.md) ID。                                                                                                                                                     |
| type                | 列挙           | アクションの種類。 指定できる値は、"RunAntiVirusScan"、"Offboard"、"CollectInvestigationPackage"、"Isolate"、"Unisolate"、"StopAndQuarantineFile"、"RestrictCodeExecution"、"UnrestrictCodeExecution" です。 |
| scope               | string         | アクションのスコープ。 "Full" または "Selective" for Isolation, "Quick" or "Full" for Anti-Virus scan.                                                                                                   |
| requestor           | String         | アクションを実行したユーザーの ID。                                                                                                                                                               |
| requestorComment    | String         | アクションを発行するときに書き込まれたコメント。                                                                                                                                                              |
| status              | 列挙           | コマンドの現在の状態。 指定できる値は、"Pending"、"InProgress"、"Succeeded"、"Failed"、"TimeOut"、"Canceled" です。                                                                                 |
| machineId           | String         | アクションが [実行](machine.md) されたコンピューターの ID。                                                                                                                                              |
| machineId           | String         | アクションが [実行](machine.md) されたコンピューターの名前。                                                                                                                                            |
| creationDateTimeUtc | DateTimeOffset | アクションが作成された日時。                                                                                                                                                                 |
| lastUpdateTimeUtc   | DateTimeOffset | アクションの状態が更新された最後の日付と時刻。                                                                                                                                                     |
| relatedFileInfo     | クラス          | 2 つのプロパティが含まれる。 string 、 Enum と指定できる値 ```fileIdentifier``` : ```fileIdentifierType``` "Sha1"、"Sha256" および "Md5" 。                                                                         |



## <a name="json-representation"></a>Json 表記

```json
{
        "id": "5382f7ea-7557-4ab7-9782-d50480024a4e",
        "type": "Isolate",
        "scope": "Selective",
        "requestor": "Analyst@TestPrd.onmicrosoft.com",
        "requestorComment": "test for docs",
        "status": "Succeeded",
        "machineId": "7b1f4967d9728e5aa3c06a9e617a22a4a5a17378",
        "computerDnsName": "desktop-test",
        "creationDateTimeUtc": "2019-01-02T14:39:38.2262283Z",
        "lastUpdateDateTimeUtc": "2019-01-02T14:40:44.6596267Z",
        "relatedFileInfo": null
}
```
