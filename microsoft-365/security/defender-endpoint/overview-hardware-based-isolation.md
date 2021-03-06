---
title: ハードウェア ベースの分離 (Windows 10)
ms.reviewer: ''
description: マルウェア対策に役立つハードウェア ベースの分離Windows 10について学習します。
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.author: macapara
ms.date: 09/07/2018
ms.technology: mde
ms.openlocfilehash: b3babf858ac19e70119a2dc6a58b25359f1b05c1
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2021
ms.locfileid: "52842988"
---
# <a name="hardware-based-isolation-in-windows-10"></a>Windows 10 のハードウェア ベースの分離

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


ハードウェア ベースの分離は、Microsoft Defender for Endpoint と統合Windows 10システムの整合性を保護するのに役立ちます。 

| 機能 | 説明 |
|------------|-------------|
| [Windows Defender Application Guard](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview.md) | Application Guard は、生産性を維持しながら、高度な攻撃からデバイスを保護します。 独自のハードウェア ベースの分離アプローチを使用して、信頼されていない Web サイトと PDF ドキュメントを、ネイティブの Windows ハイパーバイザーを介してオペレーティング システムから分離された軽量コンテナー内で分離します。 信頼されていないサイトまたは PDF ドキュメントが悪意のあると判明した場合でも、デスクトップ PC を保護し、攻撃者をエンタープライズ データから遠く離して、Application Guard のセキュリティで保護されたコンテナーに含まれるままです。 |
| [Windows DefenderSystem Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows.md) | System Guard は、システムの開始および実行後にシステムの整合性を保護および維持し、構成証明を使用してシステムの整合性を検証します。  |

