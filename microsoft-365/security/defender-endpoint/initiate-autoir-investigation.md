---
title: 調査 API の開始
description: この API を使用して、デバイスの調査を開始します。
keywords: apis, graph api, サポートされている API, 調査
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
ms.openlocfilehash: b7a6a3e7f6f705f322ee3eb1c1b561bc01c55d29
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2021
ms.locfileid: "52770891"
---
# <a name="start-investigation-api"></a>調査 API の開始

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Defender for Endpoint を体験してみませんか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>API の説明
デバイスで自動調査を開始します。
<br>詳細 [については、「自動調査の概要](automated-investigations.md) 」を参照してください。


## <a name="limitations"></a>制限事項
1. この API のレート制限は、1 時間あたり 50 回の呼び出しです。


## <a name="permissions"></a>アクセス許可
この API を呼び出すには、次のいずれかのアクセス許可が必要です。 アクセス許可の選択方法など、詳細については [、「Use Microsoft Defender for Endpoint API」を参照してください。](apis-intro.md)

アクセス許可の種類 |   アクセス許可  |   アクセス許可の表示名
:---|:---|:---
アプリケーション |   Alert.ReadWrite.All |   'すべてのアラートの読み取りと書き込み'
委任 (職場または学校のアカウント) | Alert.ReadWrite | 'アラートの読み取りと書き込み'

>[!Note]
> ユーザー資格情報を使用してトークンを取得する場合:
>- ユーザーは、少なくとも次の役割のアクセス許可を持っている必要があります。 'Active 修復アクション' (詳細については、「役割の作成と管理 [」](user-roles.md) を参照してください)
>- ユーザーは、デバイス グループ設定に基づいてデバイスにアクセスする必要があります (詳細については、「 [デバイス](machine-groups.md) グループの作成と管理」を参照してください)


## <a name="http-request"></a>HTTP 要求
```
POST https://api.securitycenter.microsoft.com/api/machines/{id}/startInvestigation
```

## <a name="request-headers"></a>要求ヘッダー

名前 | 種類 | 説明
:---|:---|:---
Authorization | String | ベアラー {token}。 **必須**
Content-Type | string | application/json. **必須**

## <a name="request-body"></a>要求本文
要求本文で、JSON オブジェクトに次のパラメーターを指定します。

パラメーター | 種類    | 説明
:---|:---|:---
コメント |   文字列 |    アクションに関連付けるコメント。 **必須**


## <a name="response"></a>応答
成功した場合、このメソッドは 201 - 作成された応答コードと [応答本文の調査](investigation.md) を返します。


## <a name="example"></a>例

**要求**

以下は、要求の例です。

```https
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/startInvestigation
```

```json
{
  "Comment": "Test investigation"
}
```
