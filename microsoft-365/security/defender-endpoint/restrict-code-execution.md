---
title: アプリの実行 API の制限
description: この API を使用して、アプリケーションの実行制限に関連する呼び出しを作成します。
keywords: apis、graph api、サポートされている API、調査パッケージの収集
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
ms.openlocfilehash: 149f3aefd963f15eafa15030a322ec588c0615ed
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51186783"
---
# <a name="restrict-app-execution-api"></a>アプリの実行 API の制限

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**適用対象:** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Microsoft Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>API の説明
定義済みのセットを除くデバイス上のすべてのアプリケーションの実行を制限します。


## <a name="limitations"></a>制限事項
1. この API のレート制限は、1 分あたり 100 回の呼び出しと 1 時間あたり 1500 回の呼び出しです。


[!include[Device actions note](../../includes/machineactionsnote.md)]

## <a name="permissions"></a>アクセス許可
この API を呼び出すには、次のいずれかのアクセス許可が必要です。 アクセス許可の選択方法など、詳細については [、「Use Microsoft Defender for Endpoint API」を参照してください。](apis-intro.md)

アクセス許可の種類 |   アクセス許可  |   アクセス許可の表示名
:---|:---|:---
アプリケーション |   Machine.RestrictExecution | 'コードの実行を制限する'
委任 (職場または学校のアカウント) | Machine.RestrictExecution | 'コードの実行を制限する'

>[!Note]
> ユーザー資格情報を使用してトークンを取得する場合:
>- ユーザーは、少なくとも次の役割のアクセス許可を持っている必要があります。 'Active 修復アクション' (詳細については、「役割の作成と管理 [」](user-roles.md) を参照してください)
>- ユーザーは、デバイス グループ設定に基づいてデバイスにアクセスする必要があります (詳細については、「 [デバイス](machine-groups.md) グループの作成と管理」を参照してください)

## <a name="http-request"></a>HTTP 要求
```
POST https://api.securitycenter.microsoft.com/api/machines/{id}/restrictCodeExecution
```

## <a name="request-headers"></a>要求ヘッダー

名前 | 種類 | 説明
:---|:---|:---
Authorization | 文字列 | ベアラー {token}。 **必須**
Content-Type | string | application/json. **必須**

## <a name="request-body"></a>要求本文
要求本文で、JSON オブジェクトに次のパラメーターを指定します。

パラメーター | 種類    | 説明
:---|:---|:---
コメント |   文字列 |    アクションに関連付けるコメント。 **必須**

## <a name="response"></a>応答
成功した場合、このメソッドは応答本文に 201 - Created response code and [Machine Action](machineaction.md) を返します。


## <a name="example"></a>例

**要求**

以下は、要求の例です。

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/restrictCodeExecution 
```

```json
{
  "Comment": "Restrict code execution due to alert 1234"
}

```

- デバイスからコード実行制限を削除するには、「アプリの制限を [削除する」を参照してください](unrestrict-code-execution.md)。