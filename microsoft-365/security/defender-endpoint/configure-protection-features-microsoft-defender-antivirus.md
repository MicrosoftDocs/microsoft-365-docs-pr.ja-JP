---
title: Microsoft Defender ウイルス対策の機能を有効にして構成する
description: Microsoft Defender AV で動作ベース、ヒューリスティック、およびリアルタイム保護を有効にする。
keywords: ヒューリスティック、機械学習、動作モニター、リアルタイム保護、Always-on、Microsoft Defender Antivirus、マルウェア対策、セキュリティ、防御
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 9fc51682b659670a21c3c293ea8996beb228802a
ms.sourcegitcommit: 7a339c9f7039825d131b39481ddf54c57b021b11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "51765073"
---
# <a name="configure-behavioral-heuristic-and-real-time-protection"></a>動作、ヒューリスティック、およびリアルタイムの保護を構成する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)

Microsoft Defender ウイルス対策は、脅威保護を提供するためにいくつかの方法を使用します。

- 新しい脅威や新しい脅威のほぼ瞬時の検出とブロックのためのクラウドによる保護
- ファイルとプロセスの動作の監視、その他のヒューリスティックを使用した常時スキャン ("リアルタイム保護" とも呼ばれる)
- 機械学習、手動および自動のビッグデータ分析、徹底した脅威耐性調査に基づいた専用の保護の更新

グループ ポリシー、System Center Configuration Manage、PowerShell コマンドレット、および Windows 管理インストルメンテーション (WMI) を使用して、Microsoft Defender Antivirus がこれらのメソッドを使用する方法を構成できます。

このセクションでは、安全ではないと見なされるがマルウェアとして検出されない可能性があるアプリを検出およびブロックする方法など、常時スキャンの構成について説明します。

Microsoft Defender ウイルス [対策クラウド配信](cloud-protection-microsoft-defender-antivirus.md) 保護を有効にして構成する方法については、「クラウド提供の保護を通じて次世代の Microsoft Defender ウイルス対策テクノロジを使用する」を参照してください。

## <a name="in-this-section"></a>このセクションの内容

 トピック | 説明
---|---
[望ましくない可能性のあるアプリケーションの検出とブロック](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) | アドウェア、ブラウザー修飾子、ツール バー、不正なウイルス対策アプリや偽のウイルス対策アプリなど、ネットワークで望ましくない可能性があるアプリを検出してブロックする
[Microsoft Defender ウイルス対策保護機能を有効にして構成する](configure-real-time-protection-microsoft-defender-antivirus.md) | リアルタイム保護、ヒューリスティック、その他の常時オンの Microsoft Defender ウイルス対策監視機能を有効にして構成する