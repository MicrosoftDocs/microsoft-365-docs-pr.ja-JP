---
title: ネットワーク保護に関する問題のトラブルシューティング
description: Microsoft Defender for Endpoint のネットワーク保護に関する問題のトラブルシューティングを行うリソースとサンプル コード。
keywords: トラブルシューティング、エラー、修正、Windows Defender 例、asr、ルール、ヒップ、トラブルシューティング、監査、除外、誤検知、破損、ブロック、エンドポイント用 Microsoft Defender、Microsoft Defender Advanced Threat Protection
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
audience: ITPro
author: dansimp
ms.author: dansimp
ms.date: 01/26/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 34bebddcf052a643529f1d2b8a8a869a0ffe4a91
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51183823"
---
# <a name="troubleshoot-network-protection"></a>ネットワーク保護のトラブルシューティング

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-pullalerts-abovefoldlink) 


ネットワーク保護を [使用すると、](network-protection.md) 次のような問題が発生する可能性があります。

- ネットワーク保護は、安全な Web サイトをブロックします (誤検知)
- ネットワーク保護で疑わしい Web サイトまたは既知の悪意のある Web サイトをブロックできない (false negative)

これらの問題のトラブルシューティングには、次の 4 つの手順があります。

1. 前提条件の確認
2. 監査モードを使用してルールをテストする
3. 指定したルールの除外を追加する (誤検知の場合)
4. サポート ログの送信

## <a name="confirm-prerequisites"></a>前提条件の確認

ネットワーク保護は、次の条件を持つデバイスでのみ機能します。

>[!div class="checklist"]
> - エンドポイントは、Windows 10 Pro または Enterprise Edition バージョン 1709 以上を実行しています。
> - エンドポイントは、Microsoft Defender Antivirus を唯一のウイルス対策保護アプリとして使用しています。 [Microsoft 以外のウイルス対策ソリューションを使用している場合の問題を確認します](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility)。
> - [リアルタイム保護が](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) 有効になっています。
> - [クラウド配信の保護が](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) 有効になっています。
> - 監査モードが有効になっていません。 グループ [ポリシーを使用して](enable-network-protection.md#group-policy) ルールを無効 **(値** : **0) に設定します**。

## <a name="use-audit-mode"></a>監査モードの使用

監査モードでネットワーク保護を有効にしてから、作成した Web サイトにアクセスして機能をデモできます。 すべての Web サイト接続はネットワーク保護によって許可されますが、ネットワーク保護が有効になっている場合にブロックされた接続を示すイベントがログに記録されます。

1. ネットワーク保護を監査モード **に設定します**。

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection AuditMode
   ```

2. 問題の原因となっている接続アクティビティを実行します (たとえば、サイトにアクセスしようとしたり、ブロックしたりしない IP アドレスに接続したりします)。

3. [ネットワーク保護イベント ログを確認](network-protection.md#review-network-protection-events-in-windows-event-viewer) して、機能が [有効] に設定されている場合に接続がブロックされた可能性を確認 **します**。
   
   ネットワーク保護がブロックする必要がある接続をブロックしていない場合は、この機能を有効にします。

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection Enabled
   ```

## <a name="report-a-false-positive-or-false-negative"></a>誤検知または偽陰性を報告する

デモ サイトと監査モードで機能をテストし、ネットワーク保護が事前構成されたシナリオで動作しているが、特定の接続で期待通りには機能しない場合は [、Windows Defender Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) Web ベースの申請フォームを使用して、ネットワーク保護に対して誤検知または誤検知を報告します。 E5 サブスクリプションを使用すると、関連 [付けられたアラートへのリンクを提供できます](alerts-queue.md)。

「Address [false positives/negatives in Microsoft Defender for Endpoint」を参照してください](defender-endpoint-false-positives-negatives.md)。

## <a name="exclude-website-from-network-protection-scope"></a>ネットワーク保護スコープから Web サイトを除外する

ブロックされている Web サイト (誤検知) を許可するには、信頼できるサイトの一覧に URL [を追加します](https://blogs.msdn.microsoft.com/asiatech/2014/08/19/how-to-add-web-sites-to-trusted-sites-via-gpo-from-dc-installed-ie10-or-higher-ie-version/)。 このリストの Web リソースは、ネットワーク保護チェックをバイパスします。

## <a name="collect-diagnostic-data-for-file-submissions"></a>ファイル提出の診断データを収集する

ネットワーク保護に関する問題を報告する場合は、Microsoft のサポートチームとエンジニアリング チームが問題のトラブルシューティングに役立つ診断データを収集して提出する必要があります。

1. 管理者特権のコマンド プロンプトを開き、次のディレクトリWindows Defenderします。

   ```console
   cd c:\program files\windows defender
   ```

2. 次のコマンドを実行して、診断ログを生成します。

   ```console
   mpcmdrun -getfiles
   ```

3. 既定では、C:\ProgramData\Microsoft\Windows ファイルにDefender\Support\MpSupportFiles.cab。 提出フォームにファイルを添付します。

## <a name="related-topics"></a>関連項目

- [ネットワーク保護](network-protection.md)
- [ネットワーク保護を評価する](evaluate-network-protection.md)
- [ネットワーク保護を有効にする](enable-network-protection.md)
- [Defender for Endpoint で誤検知/負のアドレスを指定する](defender-endpoint-false-positives-negatives.md)