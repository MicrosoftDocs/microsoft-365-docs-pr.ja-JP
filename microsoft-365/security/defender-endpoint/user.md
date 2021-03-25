---
title: ユーザー リソースの種類
description: ユーザーに関連する最近の Microsoft Defender for Endpoint アラートを取得します。
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
ms.technology: mde
ms.openlocfilehash: e3b2a567a953883d1d0ecd062159bfee4135dc85
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51197959"
---
# <a name="user-resource-type"></a>ユーザー リソースの種類

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


メソッド|戻り値の型 |説明
:---|:---|:---
[ユーザー関連のアラートの一覧表示](get-user-related-alerts.md) | [alert](alerts.md) コレクション |  ユーザーに関連付けられているすべてのアラートを一覧表示 [します](user.md)。
[リスト ユーザー関連のデバイス](get-user-related-machines.md) | [machine](machine.md) コレクション | ユーザーがログオンしていたすべてのデバイスを一覧表示 [します](user.md)。