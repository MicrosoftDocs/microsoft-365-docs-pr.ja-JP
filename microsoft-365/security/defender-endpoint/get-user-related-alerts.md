---
title: ユーザー関連の通知 API を取得する
description: Microsoft Defender for Endpoint を使用して、特定のユーザー ID に関連するアラートのコレクションを取得します。
keywords: apis, graph api, supported apis, get, user, related, alerts
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
ms.openlocfilehash: ab0d0e97365b5ce38b29f2b0d65e3aea48d6c28c
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2021
ms.locfileid: "52769931"
---
# <a name="get-user-related-alerts-api"></a>ユーザー関連の通知 API を取得する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Defender for Endpoint を体験してみませんか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API の説明
特定のユーザー ID に関連するアラートのコレクションを取得します。


## <a name="limitations"></a>制限事項
1. この API のレート制限は、1 分あたり 100 回の呼び出しと 1 時間あたり 1500 回の呼び出しです。


## <a name="permissions"></a>アクセス許可
この API を呼び出すには、次のいずれかのアクセス許可が必要です。 アクセス許可の選択方法など、詳細については [、「Use Microsoft Defender for Endpoint API」を参照してください。](apis-intro.md)

アクセス許可の種類 |   アクセス許可  |   アクセス許可の表示名
:---|:---|:---
アプリケーション |   Alert.Read.All |    'すべてのアラートの読み取り'
アプリケーション |   Alert.ReadWrite.All |   'すべてのアラートの読み取りと書き込み'
委任 (職場または学校のアカウント) | Alert.Read | 'アラートの読み取り'
委任 (職場または学校のアカウント) | Alert.ReadWrite | 'アラートの読み取りと書き込み'

>[!Note]
> ユーザー資格情報を使用してトークンを取得する場合:
>- ユーザーには、少なくとも次の役割のアクセス許可が必要です。'データの表示' 。 詳細については、「役割の作成 [と管理」を参照してください](user-roles.md)。
>- 応答には、デバイス グループ設定に基づいて、ユーザーがアクセスできるデバイスに関連付けられたアラートだけが含まれます[](machine-groups.md)(詳細については、「デバイス グループの作成と管理」を参照してください)

## <a name="http-request"></a>HTTP 要求
```
GET /api/users/{id}/alerts
```

**ID は完全な UPN ではなく、ユーザー名のみです。(たとえば、/api/users/user1/alerts を使用 user1@contoso.com アラートを取得するには)**

## <a name="request-headers"></a>要求ヘッダー

名前 | 種類 | 説明
:---|:---|:---
Authorization | String | ベアラー {token}。 **必須**


## <a name="request-body"></a>要求本文
Empty

## <a name="response"></a>応答
成功し、ユーザーが存在する場合 - 200 OK。 ユーザーが存在しない場合 - 404 が見つかりません。 


## <a name="example"></a>例

**要求**

以下は、要求の例です。

```http
GET https://api.securitycenter.microsoft.com/api/users/user1/alerts
```
