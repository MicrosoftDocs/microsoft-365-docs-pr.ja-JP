---
title: コンピューター API の分離
description: 分離マシン API を使用して、Microsoft Defender for Endpoint の外部ネットワークへのアクセスからデバイスを分離する方法について説明します。
keywords: apis、graph api、サポートされている API、デバイスの分離
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
ms.openlocfilehash: 9f3313a08b072f4fb2f699148ab801207e56fc09
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2021
ms.locfileid: "52772115"
---
# <a name="isolate-machine-api"></a>コンピューター API の分離

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Defender for Endpoint を体験してみませんか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>API の説明
デバイスが外部ネットワークにアクセスするのを分離します。


## <a name="limitations"></a>制限事項
1. この API のレート制限は、1 分あたり 100 回の呼び出しと 1 時間あたり 1500 回の呼び出しです。


[!include[Device actions note](../../includes/machineactionsnote.md)]

## <a name="permissions"></a>アクセス許可
この API を呼び出すには、次のいずれかのアクセス許可が必要です。 アクセス許可の選択方法など、詳細については [、「Use Microsoft Defender for Endpoint API」を参照してください。](apis-intro.md)

アクセス許可の種類 |   アクセス許可  |   アクセス許可の表示名
:---|:---|:---
アプリケーション |   Machine.Isolate |   '分離マシン'
委任 (職場または学校のアカウント) | Machine.Isolate |  '分離マシン'

>[!Note]
> ユーザー資格情報を使用してトークンを取得する場合:
>- ユーザーは、少なくとも次の役割のアクセス許可を持っている必要があります。 'Active 修復アクション' (詳細については、「役割の作成と管理 [」](user-roles.md) を参照してください)
>- ユーザーは、デバイス グループ設定に基づいてデバイスにアクセスする必要があります (詳細については、「 [デバイス](machine-groups.md) グループの作成と管理」を参照してください)


## <a name="http-request"></a>HTTP 要求
```
POST https://api.securitycenter.microsoft.com/api/machines/{id}/isolate
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
IsolationType   | String |  分離の種類。 使用できる値は、'Full' または '選択的' です。

**IsolationType** は、実行する分離の種類を制御し、次のいずれかを指定できます。
- 完全 – 完全分離
- 選択的 – 制限された一連のアプリケーションだけがネットワークにアクセスを制限します (詳細については、「 [デバイス](respond-machine-alerts.md#isolate-devices-from-the-network) をネットワークから分離する」を参照してください)


## <a name="response"></a>応答
成功した場合、このメソッドは応答本文に 201 - Created response code and [Machine Action](machineaction.md) を返します。


## <a name="example"></a>例

**要求**

以下は、要求の例です。

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/isolate
```

```json
{
  "Comment": "Isolate machine due to alert 1234",
  "IsolationType": "Full" 
}
```

- デバイスを分離から解放するには、「デバイスを分離 [から解放する」を参照してください](unisolate-machine.md)。
