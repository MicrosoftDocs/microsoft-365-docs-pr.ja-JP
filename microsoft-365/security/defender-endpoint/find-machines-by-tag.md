---
title: タグ API でデバイスを検索する
description: specifc タグを含むすべてのデバイスを検索する
keywords: apis, サポートされている api, get, device, find, find device, by tag, tag
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
ms.openlocfilehash: 6460860828acd5ea0c3509e9eb06061d2a9a0cc2
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51200151"
---
# <a name="find-devices-by-tag-api"></a>タグ API でデバイスを検索する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Microsoft Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>API の説明
タグ[でコンピューターを](machine.md)[検索します](machine-tags.md)。
<br>```startswith``` クエリがサポートされています。 

## <a name="limitations"></a>制限事項
1. この API のレート制限は、1 分あたり 100 回の呼び出しと 1 時間あたり 1500 回の呼び出しです。


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
> - 応答には、ユーザーがデバイス グループ設定に基づいてアクセスできるデバイスだけが含まれます (詳細については、「 [デバイス](machine-groups.md) グループの作成と管理」を参照してください)
> - ユーザーは、少なくとも次の役割のアクセス許可を持っている必要があります。 'データの表示' (詳細については、「 [役割](user-roles.md) の作成と管理」を参照してください)
> - 応答には、ユーザーがデバイス グループ設定に基づいてアクセスできるデバイスだけが含まれます (詳細については、「 [デバイス](machine-groups.md) グループの作成と管理」を参照してください)

## <a name="http-request"></a>HTTP 要求
```
GET /api/machines/findbytag?tag={tag}&useStartsWithFilter={true/false}
```

## <a name="request-headers"></a>要求ヘッダー

名前 | 種類 | 説明
:---|:---|:---
Authorization | 文字列 | ベアラー {token}。 **必須**

## <a name="request-uri-parameters"></a>要求 URI パラメーター

Name | 種類 | 説明
:---|:---|:---
tag | 文字列 | タグ名。 **必須**
useStartsWithFilter | Boolean | true に設定すると、クエリ内の指定されたタグで始まるタグ名を持つすべてのデバイスが検索されます。 既定は false です。 **オプション**。

## <a name="request-body"></a>要求本文
Empty

## <a name="response"></a>応答
成功した場合 - 応答本文のコンピューターの一覧で 200 OK。

## <a name="example"></a>例

**要求**

以下は、要求の例です。

```http
GET https://api.securitycenter.microsoft.com/api/machines/findbytag?tag=testTag&useStartsWithFilter=true
```