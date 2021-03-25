---
title: Get domain related machines API
description: Get domain related machines API を使用して、Microsoft Defender for Endpoint のドメインと通信するコンピューターを取得する方法について説明します。
keywords: apis, graph api, supported apis, get, domain, related, devices
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
ms.openlocfilehash: 3fffb87c486e8b6b89b5e868b96d02dfae496e0b
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51166876"
---
# <a name="get-domain-related-machines-api"></a>Get domain related machines API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>API の説明
特定のドメイン アドレスと通信した [コンピューター](machine.md) のコレクションを取得します。


## <a name="limitations"></a>制限事項
1. 構成済みの保持期間に従って、最後に更新されたデバイスに対してクエリを実行できます。
2. この API のレート制限は、1 分あたり 100 回の呼び出しと 1 時間あたり 1500 回の呼び出しです。


## <a name="permissions"></a>アクセス許可
この API を呼び出すには、次のいずれかのアクセス許可が必要です。 アクセス許可の選択方法など、詳細については [、「Use Microsoft Defender for Endpoint API」を参照してください。](apis-intro.md)

アクセス許可の種類 |   アクセス許可  |   アクセス許可の表示名
:---|:---|:---
アプリケーション |   Machine.Read.All |  'すべてのコンピューター プロファイルを読み取る'
アプリケーション |   Machine.ReadWrite.All | 'すべてのコンピューター情報の読み取りと書き込み'
委任 (職場または学校のアカウント) | Machine.Read | 'コンピューター情報の読み取り'
委任 (職場または学校のアカウント) | Machine.ReadWrite | 'コンピューター情報の読み取りおよび書き込み'

>[!Note]
> ユーザー資格情報を使用してトークンを取得する場合:
>- ユーザーは、少なくとも次の役割のアクセス許可を持っている必要があります。 'データの表示' (詳細については、「 [役割](user-roles.md) の作成と管理」を参照してください)
>- 応答には、デバイス グループの設定に基づいて、ユーザーがアクセスできるデバイスだけが含まれます (詳細については、「 [デバイス](machine-groups.md) グループの作成と管理」を参照してください)

## <a name="http-request"></a>HTTP 要求
```http
GET /api/domains/{domain}/machines
```

## <a name="request-headers"></a>要求ヘッダー

名前 | 種類 | 説明
:---|:---|:---
Authorization | 文字列 | ベアラー {token}。 **必須**


## <a name="request-body"></a>要求本文
Empty

## <a name="response"></a>応答
成功した場合とドメインが存在する場合 - コンピューター[](machine.md)エンティティの一覧で 200 OK。 ドメインが存在しない場合 - 404 が見つかりません。


## <a name="example"></a>例

**要求**

以下は、要求の例です。

```http
GET https://api.securitycenter.microsoft.com/api/domains/api.securitycenter.microsoft.com/machines
```