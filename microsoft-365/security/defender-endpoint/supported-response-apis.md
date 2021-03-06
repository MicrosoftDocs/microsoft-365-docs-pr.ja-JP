---
title: サポートされている Microsoft Defender for Endpoint response API
description: 特定の応答関連の Microsoft Defender for Endpoint API 呼び出しについて説明します。
keywords: 応答 API、グラフ API、サポートされている API、アクター、アラート、デバイス、ユーザー、ドメイン、IP、ファイル
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.topic: conceptual
ms.openlocfilehash: 36ed1f624fda7ae413ffbbf807925cf00e0a23ca
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2021
ms.locfileid: "51933771"
---
# <a name="supported-microsoft-defender-for-endpoint-query-apis"></a>サポートされている Microsoft Defender for Endpoint クエリ API 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!TIP]
> Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-supported-response-apis-abovefoldlink) 

実行できるサポートされる応答関連 API 呼び出しと、必要な要求ヘッダー、呼び出しからの予期される応答などの詳細について説明します。

## <a name="in-this-section"></a>このセクションの内容
トピック | 説明
:---|:---
調査パッケージの収集 | この API を実行して、デバイスから調査パッケージを収集します。
デバイスの分離 | ネットワークからデバイスを分離するには、この API を実行します。
Unisolate デバイス | デバイスを分離から削除します。 
コードの実行を制限する | 悪意のあるプロセスを停止して攻撃を含めるには、この API を実行します。 デバイスをロックダウンして、悪意のある可能性のあるプログラムの後続の試行が実行されるのを防ぐことも可能です。
無制限のコード実行 | 侵害されたデバイスが修復されたと確認した後、アプリケーション ポリシーの制限を取り消す場合は、これを実行します。
ウイルス対策スキャンを実行する | ウイルス対策スキャンをリモートで開始して、侵害されたデバイスに存在する可能性のあるマルウェアを特定して修復します。
ファイルの停止と検疫 |  この呼び出しを実行して、プロセスの実行を停止し、ファイルを検疫し、レジストリ キーなどの永続性を削除します。
要求サンプル | この呼び出しを実行して、特定のデバイスからファイルのサンプルを要求します。 ファイルはデバイスから収集され、セキュリティで保護された記憶域にアップロードされます。
ブロック ファイル | この API を実行して、悪意のある可能性のあるファイルやマルウェアの疑いを禁止して、組織内の攻撃をさらに伝播防止します。 
ファイルのブロックを解除する | 組織でファイルの実行を許可するには、次のMicrosoft Defender ウイルス対策。
パッケージ SAS URI の取得 | この API を実行して、調査パッケージのダウンロードを許可する URI を取得します。
MachineAction オブジェクトの取得 | この API を実行して MachineAction オブジェクトを取得します。
MachineActions コレクションの取得 | MachineAction コレクションを取得するには、これを実行します。
Get FileActions コレクション | FileActions コレクションを取得するには、この API を実行します。
Get FileMachineAction オブジェクト | FileMachineAction オブジェクトを取得するには、この API を実行します。
Get FileMachineActions コレクション | FileMachineAction コレクションを取得するには、この API を実行します。
