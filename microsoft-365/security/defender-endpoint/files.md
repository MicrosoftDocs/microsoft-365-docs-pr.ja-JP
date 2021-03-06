---
title: ファイル リソースの種類
description: ファイルに関連する最近の Microsoft Defender for Endpoint アラートを取得します。
keywords: apis, graph api, supported apis, get, alerts, recent
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
ms.openlocfilehash: 83a011e649a7289f62acd6a8d985f020b27b1e10
ms.sourcegitcommit: 4886457c0d4248407bddec56425dba50bb60d9c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2021
ms.locfileid: "53290017"
---
# <a name="file-resource-type"></a>ファイル リソースの種類

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Defender for Endpoint のファイル エンティティを表します。

## <a name="methods"></a>メソッド

メソッド|戻り値の型 |説明
:---|:---|:---
[ファイルの取得](get-file-information.md) | [file](files.md) | 1 つのファイルを取得する 
[ファイル関連のアラートを一覧表示する](get-file-related-alerts.md) | [alert](alerts.md) コレクション | ファイルに [関連](alerts.md) 付けられているアラート エンティティを取得します。
[ファイル関連のコンピューターを一覧表示する](get-file-related-machines.md) | [machine](machine.md) コレクション | アラートに [関連付](machine.md) けられたコンピューター エンティティを取得します。
[ファイルの統計情報](get-file-statistics.md) | 統計情報の概要 | 指定したファイルの有病率を取得します。


## <a name="properties"></a>プロパティ

|プロパティ | 種類 | 説明 |
|:---|:---|:---|
|sha1 | String | ファイル コンテンツの Sha1 ハッシュ |
|sha256 | String | ファイル コンテンツの Sha256 ハッシュ |
|globalPrevalence | Null 許容長 | 組織全体でのファイルの普及率 |
|globalFirstObserved | DateTimeOffset | ファイルが初めて観察された場合 |
|globalLastObserved | DateTimeOffset | ファイルが最後に観察された時刻 |
|size | Null 許容長 | ファイルのサイズ |
|fileType | String | ファイルの種類 |
|isPeFile | ブール型 | ファイルが移植可能な実行可能ファイルの場合は true ("DLL"、"EXE"など) |
|filePublisher | String | ファイル発行元 |
|fileProductName | String | 製品名 |
|署名者 | String | ファイル署名者 |
|issuer | String | ファイル発行者 |
|signerHash | String | 署名証明書のハッシュ |
|isValidCertificate | ブール型 | Microsoft Defender for Endpoint エージェントによって証明書の署名が正常に確認されました |
|determinationType | String | ファイルの決定の種類 |
|determinationValue | String | 判定値 |

## <a name="json-representation"></a>Json 表記

```json
{
    "sha1": "4388963aaa83afe2042a46a3c017ad50bdcdafb3",
    "sha256": "413c58c8267d2c8648d8f6384bacc2ae9c929b2b96578b6860b5087cd1bd6462",
    "globalPrevalence": 180022,
    "globalFirstObserved": "2017-09-19T03:51:27.6785431Z",
    "globalLastObserved": "2020-01-06T03:59:21.3229314Z",
    "size": 22139496,
    "fileType": "APP",
    "isPeFile": true,
    "filePublisher": "CHENGDU YIWO Tech Development Co., Ltd.",
    "fileProductName": "EaseUS MobiSaver for Android",
    "signer": "CHENGDU YIWO Tech Development Co., Ltd.",
    "issuer": "VeriSign Class 3 Code Signing 2010 CA",
    "signerHash": "6c3245d4a9bc0244d99dff27af259cbbae2e2d16",
    "isValidCertificate": false,
    "determinationType": "Pua",
    "determinationValue": "PUA:Win32/FusionCore"
}
```
