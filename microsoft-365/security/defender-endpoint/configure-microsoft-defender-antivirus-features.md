---
title: Microsoft Defender ウイルス対策機能を構成する
description: Intune、Microsoft Defender ウイルス対策、グループ ポリシー Microsoft Endpoint Configuration Manager PowerShell を使用して、これらの機能を構成できます。
keywords: Microsoft Defender ウイルス対策、マルウェア対策、セキュリティ、防御者、構成、Microsoft Endpoint Configuration Manager、SCCM、Intune、MDM、モバイル デバイス管理、GP、グループ ポリシー、PowerShell
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 06/04/2021
ms.reviewer: ''
manager: dansimp
ms.openlocfilehash: 7fa5959ede9f0c71c75cefafc0fcb0d4376a1a4f
ms.sourcegitcommit: be929f79751c0c52dfa6bd98a854432a0c63faf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2021
ms.locfileid: "52925397"
---
# <a name="configure-microsoft-defender-antivirus-features"></a>Microsoft Defender ウイルス対策機能を構成する


**適用対象:**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)

次のようなMicrosoft Defender ウイルス対策ツールを使用して、構成を構成できます。

- Microsoft エンドポイント マネージャー (これには、Microsoft IntuneとMicrosoft Endpoint Configuration Manager)
- グループ ポリシー
- PowerShell コマンドレット
- Windows Management Instrumentation (WMI)

次の広範なカテゴリの機能を構成できます。

- クラウドによる保護。 [「Cloud-delivered protection and Microsoft Defender ウイルス対策](cloud-protection-microsoft-defender-antivirus.md)
 
- 行動、ヒューリスティック、機械学習ベースの保護を含む、常時オンのリアルタイム保護。 「 [動作、ヒューリスティック、およびリアルタイム保護を構成する」を参照してください](configure-protection-features-microsoft-defender-antivirus.md)。

- エンド ユーザーが個々のエンドポイントでクライアントとやり取りする方法。 以下のリソースを参照してください。
   
   - [ユーザーがユーザー インターフェイスを表示または操作Microsoft Defender ウイルス対策防止する](prevent-end-user-interaction-microsoft-defender-antivirus.md)

   - [ユーザーがポリシー設定をローカルで変更Microsoft Defender ウイルス対策または許可する](configure-local-policy-overrides-microsoft-defender-antivirus.md) 

> [!TIP]
> 管理 [ツールと構成ツールのリファレンス トピックを確認します](configuration-management-reference-microsoft-defender-antivirus.md)。
