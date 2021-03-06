---
title: Defender REST API Microsoft 365コードの一般的な説明
description: Defender REST API エラー コードMicrosoft 365一般的な方法について説明します。
keywords: api、 error, codes, common error, Microsoft 365 Defender, API エラー コード
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: de24856e8ea7555a96de18cabca5ccadfe71b431
ms.sourcegitcommit: 3d30ec03628870a22c54b6ec5d865cbe94f34245
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2021
ms.locfileid: "52930273"
---
# <a name="common-microsoft-365-defender-rest-api-error-codes"></a>Defender REST API Microsoft 365コードの一般的な説明

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**適用対象:**

- Microsoft 365 Defender

> [!IMPORTANT]
> 一部の情報は、市販される前に大幅に変更される可能性があるプレリリース製品に関するものです。 Microsoft は、ここに記載された情報に関して、明示または黙示を問わず、いかなる保証も行いません。

エラー コードは、任意の Defender API 上の操作Microsoft 365返される場合があります。 すべてのエラー応答にエラー メッセージが含まれるので、問題の解決に役立ちます。 テーブル セクションのエラー メッセージ列には、いくつかのサンプル メッセージが表示されます。 実際のメッセージの内容は、応答をトリガーした要因によって異なります。 変数の内容は、表に角かっこで示されます。

## <a name="error-codes"></a>エラー コード

エラー コード | HTTP ステータス コード | メッセージ
-|-|-
BadRequest | BadRequest (400) | 一般的な不良要求エラー メッセージ。
ODataError | BadRequest (400) | OData URI クエリが無効です \<the specific error is specified\> 。
InvalidInput | BadRequest (400) | 入力が無効です \<the invalid input\> 。
InvalidRequestBody | BadRequest (400) | 要求本文が無効です。
InvalidHashValue | BadRequest (400) | ハッシュ値 \<the invalid hash\> が無効です。
InvalidDomainName | BadRequest (400) | ドメイン名 \<the invalid domain\> が無効です。
InvalidIpAddress | BadRequest (400) | IP アドレス \<the invalid IP\> が無効です。
InvalidUrl | BadRequest (400) | URL \<the invalid URL\> が無効です。
MaximumBatchSizeExceeded | BadRequest (400) | 最大バッチ サイズを超えました。 受信: \<batch size received\> 、許可: {batch size allowed}。
MissingRequiredParameter | BadRequest (400) | パラメーター \<the missing parameter\> がありません。
OsPlatformNotSupported | BadRequest (400) | OS プラットフォーム \<the client OS Platform\> は、このアクションではサポートされていません。
ClientVersionNotSupported | BadRequest (400) | \<The requested action\> はクライアント バージョン以上 \<supported client version\> でサポートされています。
権限がありません (Unauthorized) | 承認されていない (401) | 権限がありません (Unauthorized) <br /><br />*注: 通常、無効または期限切れの承認ヘッダーが原因です。*
禁止されています | 禁止 (403) | 禁止されています <br /><br />*注: 有効なトークンですが、アクションに対するアクセス許可が不十分です*。
DisabledFeature | 禁止 (403) | テナント機能が有効になっていません。
DisallowedOperation | 禁止 (403) | \<the disallowed operation and the reason\>.
NotFound | 見つかりません (404) | 一般的なエラー メッセージが見つかりません。
ResourceNotFound | 見つかりません (404) | リソース \<the requested resource\> が見つかりませんでした。
InternalServerError | 内部サーバー エラー (500) | *注: エラー メッセージが表示されない場合は、操作を再試行するか、解決されない場合は [Microsoft](/microsoft-365/business-video/get-help-support) にお問い合わせください。*

## <a name="examples"></a>例

```json
{
    "error": {
        "code": "ResourceNotFound",
        "message": "Machine 123123123 was not found",
        "target": "43f4cb08-8fac-4b65-9db1-745c2ae65f3a"
    }
}
```

```json
{
    "error": {
        "code": "InvalidRequestBody",
        "message": "Request body is incorrect",
        "target": "1fa66c0f-18bd-4133-b378-36d76f3a2ba0"
    }
}
```

## <a name="body-parameters"></a>本文パラメーター

> [!IMPORTANT]
> 本文パラメーターでは、大文字と小文字が区別されます。

*InvalidRequestBody エラーまたは* *MissingRequiredParameter* エラーが発生した場合は、入力ミスが原因である可能性があります。 API のドキュメントを確認し、送信されたパラメーターが関連する例と一致する点を確認します。

## <a name="tracking-id"></a>追跡 ID

各エラー応答には、追跡用の一意の ID パラメーターが含まれる。 このパラメーターのプロパティ名は target *です*。 エラーについてお問い合わせの際に、この ID を添付すると、問題の根本原因を見つけるのに役立ちます。

## <a name="related-articles"></a>関連資料

- [Microsoft 365Defender API の概要](api-overview.md)
- [サポートされている Microsoft 365 Defender API](api-supported.md)
- [Defender API Microsoft 365アクセスする](api-access.md)
- [API の制限とライセンスの詳細](api-terms.md)
