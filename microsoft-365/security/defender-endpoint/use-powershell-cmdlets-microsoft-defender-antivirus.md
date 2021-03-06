---
title: PowerShell コマンドレットを使用して Microsoft Defender AV を構成および実行する
description: このWindows 10 PowerShell コマンドレットを使用して、スキャンの実行、セキュリティ インテリジェンスの更新、および設定の変更を行Microsoft Defender ウイルス対策。
keywords: scan, コマンドライン, mpcmdrun, defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 07/23/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.openlocfilehash: d6fb8dc510e004fa88bf99583cc2cc33ae8c63bb
ms.sourcegitcommit: 7a339c9f7039825d131b39481ddf54c57b021b11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "51765301"
---
# <a name="use-powershell-cmdlets-to-configure-and-manage-microsoft-defender-antivirus"></a>PowerShell コマンドレットを使用して、サーバーの構成とMicrosoft Defender ウイルス対策

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)

PowerShell を使用して、さまざまな機能を実行Windows Defender。 コマンド プロンプトやコマンド ラインと同様に、PowerShell はタスク ベースのコマンド ライン シェルであり、特にシステム管理用に設計されたスクリプト言語です。 詳細については [、MSDN の PowerShell ハブで確認できます](/previous-versions/msdn10/mt173057(v=msdn.10))。

コマンドレットとその機能と使用可能なパラメーターの一覧については、「Defender コマンドレット」 [を参照](/powershell/module/defender) してください。

PowerShell コマンドレットは、ソフトウェアWindowsグラフィカル ユーザー インターフェイス (GUI) に依存しないサーバー環境で最も役立ちます。

> [!NOTE]
> PowerShell コマンドレットは[、Microsoft Endpoint Configuration Manager、](/configmgr)グループ ポリシー管理コンソール、または Microsoft Defender ウイルス対策 グループ ポリシー ADMX テンプレート[](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))などの完全なネットワーク ポリシー管理インフラストラクチャの代[わりとして使用する必要があります](https://www.microsoft.com/download/101445)。

PowerShell で行われた変更は、変更が展開または行われたエンドポイントのローカル設定に影響します。 つまり、グループ ポリシー、グループ ポリシー、Microsoft Endpoint Configuration Manager、Microsoft Intuneを使用してポリシーを展開すると、PowerShell で行われた変更が上書きされる可能性があります。

ローカル ポリシー [の上書きを使用してローカルで上書きできる設定を構成できます](configure-local-policy-overrides-microsoft-defender-antivirus.md)。

PowerShell は通常、フォルダーの下にインストールされます `%SystemRoot%\system32\WindowsPowerShell` 。

## <a name="use-microsoft-defender-antivirus-powershell-cmdlets"></a>PowerShell Microsoft Defender ウイルス対策を使用する

1. [検索] Windowsに **、「powershell」と入力します**。
2. 結果 **Windows PowerShell** を選択してインターフェイスを開きます。
3. PowerShell コマンドとパラメーターを入力します。

> [!NOTE]
> 管理者モードで PowerShell を開く必要がある場合があります。 [スタート] メニューのアイテムを右クリックし、[管理者として実行] をクリック **し、アクセス** 許可のプロンプト **で [は** い] をクリックします。

コマンドレットのオンライン ヘルプを開く場合は、次を入力します。

```PowerShell
Get-Help <cmdlet> -Online
```

ローカルに `-online` キャッシュされたヘルプを取得するには、パラメーターを省略します。

## <a name="related-topics"></a>関連項目

- [管理および構成ツールのリファレンス トピック](configuration-management-reference-microsoft-defender-antivirus.md)
- [Microsoft Defender ウイルス対策 (Windows 10)](microsoft-defender-antivirus-in-windows-10.md)
- [Microsoft Defender ウイルス対策コマンドレット](/powershell/module/defender)