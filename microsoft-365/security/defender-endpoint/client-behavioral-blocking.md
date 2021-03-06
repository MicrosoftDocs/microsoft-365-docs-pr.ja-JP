---
title: クライアントの動作ブロック
description: クライアントの動作ブロックは、Microsoft Defender for Endpoint の動作ブロックと格納機能の一部です。
keywords: 動作のブロック、迅速な保護、クライアントの動作、Microsoft Defender for Endpoint
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
localization_priority: Normal
ms.custom:
- next-gen
- edr
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.technology: mde
ms.openlocfilehash: 83f269a13a54ee38b7e7a464d794d87ddbd7b520
ms.sourcegitcommit: 4886457c0d4248407bddec56425dba50bb60d9c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2021
ms.locfileid: "53289933"
---
# <a name="client-behavioral-blocking"></a>クライアントの動作ブロック

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Defender for Endpoint を体験してみませんか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>概要

クライアントの動作ブロックは、Defender [](behavioral-blocking-containment.md) for Endpoint の動作ブロックと格納機能のコンポーネントです。 デバイス (クライアントまたはエンドポイントとも呼ばれます) で疑わしい動作が検出されると、アーティファクト (ファイルやアプリケーションなど) が自動的にブロック、チェック、修復されます。 

:::image type="content" source="images/pre-execution-and-post-execution-detection-engines.png" alt-text="クラウドとクライアントの保護":::

ウイルス対策保護は、クラウド保護と組み合わせた場合に最適です。

## <a name="how-client-behavioral-blocking-works"></a>クライアントの動作のブロックのしくみ

[Microsoft Defender ウイルス対策、](microsoft-defender-antivirus-in-windows-10.md)不審な動作、悪意のあるコード、ファイルレス攻撃やメモリ内攻撃など、デバイスで検出できます。 疑わしい動作が検出されると、Microsoft Defender ウイルス対策動作とそのプロセス ツリーを監視し、クラウド保護サービスに送信します。 機械学習は、悪意のあるアプリケーションと適切な動作をミリ秒単位で区別し、各成果物を分類します。 ほぼリアルタイムで、アーティファクトが悪意のあると判明すると、デバイス上でブロックされます。 

疑わしい動作が検出されると、アラートが生成[](alerts-queue.md)され、Microsoft 365 Defender ポータル[(以前](microsoft-defender-security-center.md)は Microsoft Defender セキュリティ センター) に表示されます。

クライアントの動作ブロックは、攻撃の開始を防ぐだけでなく、実行を開始した攻撃を停止するのに役立つため、効果的です。 また、フィードバック [ループブロック](feedback-loop-blocking.md) (別の動作ブロックと格納機能) を使用すると、組織内の他のデバイスに対する攻撃が防止されます。

## <a name="behavior-based-detections"></a>動作ベースの検出

動作ベースの検出の名前は[、MITRE ATT](https://attack.mitre.org/matrices/enterprise)&CK マトリックスに従Enterprise。 名前付け規則は、悪意のある動作が観察された攻撃段階を特定するのに役立ちます。

|戦術 | 検出の脅威名 |
|----|----|
|初期アクセス | `Behavior:Win32/InitialAccess.*!ml` |
|実行 | `Behavior:Win32/Execution.*!ml` |
|永続性 | `Behavior:Win32/Persistence.*!ml` |
|特権エスカレーション | `Behavior:Win32/PrivilegeEscalation.*!ml` |
|Defense Evasion | `Behavior:Win32/DefenseEvasion.*!ml` |
|資格情報アクセス | `Behavior:Win32/CredentialAccess.*!ml` |
|Discovery | `Behavior:Win32/Discovery.*!ml` |
|横方向の動き | `Behavior:Win32/LateralMovement.*!ml` |
|Collection | `Behavior:Win32/Collection.*!ml` |
|コマンドとコントロール | `Behavior:Win32/CommandAndControl.*!ml` |
|Exfiltration | `Behavior:Win32/Exfiltration.*!ml` |
|影響 | `Behavior:Win32/Impact.*!ml` |
|未分類 | `Behavior:Win32/Generic.*!ml` |

> [!TIP]
> 特定の脅威の詳細については、「最近のグローバル脅威 **[アクティビティ」を参照してください](https://www.microsoft.com/wdsi/threats)**。

## <a name="configuring-client-behavioral-blocking"></a>クライアントの動作ブロックの構成

組織で Defender for Endpoint を使用している場合、クライアントの動作ブロックは既定で有効になっています。 ただし、動作ブロックや格納を含むすべての Defender [](behavioral-blocking-containment.md)for Endpoint 機能を利用するには、Defender for Endpoint の次の機能が有効で構成されていることを確認してください。

- [Defender for Endpoint baselines](configure-machines-security-baseline.md)

- [Defender for Endpoint にオンボードされているデバイス](onboard-configure.md)

- [ブロック モードの EDR](edr-in-block-mode.md)

- [攻撃面の減少](attack-surface-reduction.md)

- [次世代保護](configure-microsoft-defender-antivirus-features.md) (ウイルス対策、マルウェア対策、その他の脅威保護機能)
