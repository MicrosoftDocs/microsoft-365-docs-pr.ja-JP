---
title: インポート インジケーター API
description: Microsoft Defender for Endpoint でインジケーター API のインポート バッチを使用する方法について説明します。
keywords: apis, サポートされている api, submit, ti, indicator, update
search.product: eADQiWindows 10XVcnh
ms.prod: w10
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
ms.openlocfilehash: b1777adf7b97083fae2daf4213a4bda742ba097d
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51198247"
---
# <a name="import-indicators-api"></a>インポート インジケーター API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>API の説明
Indicator エンティティのバッチを [送信または](ti-indicator.md) 更新します。
<br>IPs の CIDR 表記はサポートされていません。

## <a name="limitations"></a>制限事項
1. この API のレート制限は、1 分あたり 30 回の呼び出しです。
2. テナントごとに 15,000 のアクティブ [なインジケーターの制限](ti-indicator.md) があります。 
3. 1 つの API 呼び出しの最大バッチ サイズは 500 です。

## <a name="permissions"></a>アクセス許可
この API を呼び出すには、次のいずれかのアクセス許可が必要です。 アクセス許可の選択方法などの詳細については、「開始する」 [を参照してください。](apis-intro.md)

アクセス許可の種類 |   アクセス許可  |   アクセス許可の表示名
:---|:---|:---
アプリケーション |   Ti.ReadWrite |  '読み取りおよび書き込みインジケーター'
アプリケーション |   Ti.ReadWrite.All |  'すべてのインジケーターの読み取りと書き込み'
委任 (職場または学校のアカウント) |    Ti.ReadWrite |  '読み取りおよび書き込みインジケーター'


## <a name="http-request"></a>HTTP 要求
```
POST https://api.securitycenter.microsoft.com/api/indicators/import
```

## <a name="request-headers"></a>要求ヘッダー

名前 | 型 | 説明
:---|:---|:---
Authorization | String | ベアラー {token}。 **必須**
Content-Type | string | application/json. **必須**

## <a name="request-body"></a>要求本文
要求本文で、JSON オブジェクトに次のパラメーターを指定します。

パラメーター | 型    | 説明
:---|:---|:---
インジケーター | リスト<[インジケーター](ti-indicator.md)> | インジケーターの [一覧](ti-indicator.md)。 **Required**


## <a name="response"></a>応答
- 成功した場合、このメソッドは、インジケーターごとのインポート結果の一覧を含む 200 - OK 応答コードを返します。以下の例を参照してください。
- 成功しない場合: このメソッドは 400 - Bad Request を返します。 通常、不適切な要求は、不適切な本文を示します。

## <a name="example"></a>例

**要求**

以下は、要求の例です。

```http
POST https://api.securitycenter.microsoft.com/api/indicators/import
```

```json
{
    "Indicators":
    [
        {
            "indicatorValue": "220e7d15b011d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "title": "demo",
            "application": "demo-test",
            "expirationTime": "2021-12-12T00:00:00Z",
            "action": "Alert",
            "severity": "Informational",
            "description": "demo2",
            "recommendedActions": "nothing",
            "rbacGroupNames": ["group1", "group2"]
        },
        {
            "indicatorValue": "2233223322332233223322332233223322332233223322332233223322332222",
            "indicatorType": "FileSha256",
            "title": "demo2",
            "application": "demo-test2",
            "expirationTime": "2021-12-12T00:00:00Z",
            "action": "Alert",
            "severity": "Medium",
            "description": "demo2",
            "recommendedActions": "nothing",
            "rbacGroupNames": []
        }
    ]
}
```

**応答**

以下は、応答の例です。

```json
{
    "value": [
        {
            "id": "2841",
            "indicator": "220e7d15b011d7fac48f2bd61114db1022197f7f",
            "isFailed": false,
            "failureReason": null
        },
        {
            "id": "2842",
            "indicator": "2233223322332233223322332233223322332233223322332233223322332222",
            "isFailed": false,
            "failureReason": null
        }
    ]
}
```

## <a name="related-topic"></a>関連トピック
- [インジケーターの管理](manage-indicators.md)
