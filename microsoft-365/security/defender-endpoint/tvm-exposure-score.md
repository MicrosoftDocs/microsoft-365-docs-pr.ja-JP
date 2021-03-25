---
title: 脅威と脆弱性の管理における露出スコア
description: 脅威と脆弱性管理の暴露スコアは、組織がサイバーセキュリティの脅威に対してどのように脆弱かを反映しています。
keywords: 露出スコア、mdatp 露出スコア、mdatp tvm 露出スコア、組織の露出スコア、tvm 組織の露出スコア、脅威と脆弱性の管理、Microsoft Defender for Endpoint
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: cc7abd678d6f2d317d02c4ed2b8028e7e270b055
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51068451"
---
# <a name="exposure-score---threat-and-vulnerability-management"></a>露出スコア - 脅威と脆弱性の管理

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [脅威と脆弱性の管理](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Microsoft Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-portaloverview-abovefoldlink)

露出スコアは、Microsoft Defender[](tvm-dashboard-insights.md)セキュリティ センターの脅威と脆弱性の管理ダッシュボードに表示されます。 これは、組織がサイバーセキュリティの脅威に対してどのように脆弱かを反映しています。 露出スコアが低いということは、デバイスが悪用の影響を受けやすいという意味です。

- 組織のセキュリティの状態に関する高レベルのテイクアウトを迅速に理解し、特定します。
- 現在の状態を改善するために調査またはアクションが必要な領域を検出して対応します。
- セキュリティの取り組みの影響について、ピアや経営陣とコミュニケーションを取る。

このカードは、時間の流れによる露出スコアの傾向を高レベルで表示します。 グラフ内のスパイクは、サイバーセキュリティの脅威に対する高い暴露を視覚的に示し、さらに調査することができます。

![露出スコア カード](images/tvm_exp_score.png)

## <a name="how-it-works"></a>メカニズム

露出スコアは、次のレベルに分割されます。

- 0 ~ 29: 低露出スコア
- 30 ~ 69: 中程度の露出スコア
- 70 ~ 100: 高い露出スコア

優先度の高いセキュリティ推奨事項に基づいて問題を修復[](tvm-security-recommendation.md)し、露出スコアを下ろします。 各ソフトウェアには、推奨事項に変換され、組織のリスクに基づいて優先順位が付けられた弱点があります。

## <a name="reduce-your-threat-and-vulnerability-exposure"></a>脅威と脆弱性の暴露を減らす

セキュリティに関する推奨事項を修正することで、脅威と脆弱性の暴露 [を削減します](tvm-security-recommendation.md)。 脅威と脆弱性の管理ダッシュボードで確認できる、セキュリティに関する上位の推奨事項を修正することで、露出スコアに最も影響 [を与えます](tvm-dashboard-insights.md)。

## <a name="related-topics"></a>関連項目

- [脅威と脆弱性の管理の概要](next-gen-threat-and-vuln-mgt.md)
- [デバイスの Microsoft Secure Score](tvm-microsoft-secure-score-devices.md)
- [セキュリティ上の推奨事項](tvm-security-recommendation.md)
- [イベントタイムライン](threat-and-vuln-mgt-event-timeline.md)