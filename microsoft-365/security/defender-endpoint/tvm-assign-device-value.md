---
title: デバイス値の割り当て - 脅威と脆弱性の管理
description: 低、通常、または高い値をデバイスに割り当て、資産の優先順位を区別する方法について学習します。
keywords: microsoft Defender atp デバイスの値、脅威と脆弱性管理デバイスの値、価値の高いデバイス、デバイス値の露出スコア
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: ellevin
author: levinec
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: be578158e18d55bb25d450749c3fb4373854456b
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51065996"
---
# <a name="assign-device-value---threat-and-vulnerability-management"></a>デバイス値の割り当て - 脅威と脆弱性の管理

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [脅威と脆弱性の管理](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-portaloverview-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

デバイスの値を定義すると、資産の優先順位を区別できます。 デバイスの値は、個々の資産のリスクアペタイトを脅威と脆弱性管理の露出スコアの計算に組み込むのに使用されます。 "高い値" として割り当てられたデバイスは、より多くの重みを受け取る。

デバイス値の設定 [API を使用することもできます](set-device-value.md)。

デバイス値のオプション:

- 低
- 標準 (既定値)
- 高

高い値を割り当てる必要があるデバイスの例を次に示します。

- ドメイン コントローラー、Active Directory
- インターネットに接続するデバイス
- VIP デバイス
- 内部/外部の実稼働サービスをホストするデバイス

## <a name="choose-device-value"></a>デバイスの値を選択する

1. 任意のデバイス ページに移動し、最も簡単な場所はデバイス インベントリから行います。

2. ページ **の上部にある** アクション バーの横にある 3 つのドットから [デバイス値] を選択します。

    ![デバイス値ドロップダウンの例。](images/tvm-device-value-dropdown.png)

3. 現在のデバイス値とそれが何を意味するフライアウトが表示されます。 デバイスの値を確認し、デバイスに最適な値を選択します。
![デバイス値のフライアウトの例。](images/tvm-device-value-flyout.png)

## <a name="how-device-value-impacts-your-exposure-score"></a>デバイスの値が露出スコアに与える影響

露出スコアは、すべてのデバイスの加重平均です。 デバイス グループがある場合は、デバイス グループ別にスコアをフィルター処理することもできます。

- 通常のデバイスの重み 1
- 低い値のデバイスの重み 0.75
- 高い値のデバイスには、NumberOfAssets / 10 の重みがあります。
    - デバイスが 100 台の場合、各高価値デバイスの重みは 10 (100/10) になります。

## <a name="related-topics"></a>関連項目

- [脅威と脆弱性の管理の概要](next-gen-threat-and-vuln-mgt.md)
- [露出スコア](tvm-exposure-score.md)
- [API](next-gen-threat-and-vuln-mgt.md#apis)