---
title: Microsoft Defender ATP for Linux のパフォーマンスの問題のトラブルシューティング
description: Microsoft Defender ATP for Linux のパフォーマンスの問題をトラブルシューティングします。
keywords: microsoft、Defender、atp、Linux、パフォーマンス
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
mms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: dea52da1952c3fbde8951457caf44232e9d258b7
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51187735"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-for-linux"></a>Microsoft Defender for Endpoint for Linux のパフォーマンスの問題のトラブルシューティング

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
> Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-investigateip-abovefoldlink)

この記事では、Defender for Endpoint for Linux に関連するパフォーマンスの問題を絞り込む一般的な手順について説明します。

リアルタイム保護 (RTP) は、デバイスを継続的に監視し、脅威から保護する Defender for Endpoint for Linux の機能です。 ファイルとプロセスの監視、その他のヒューリスティックで構成されます。

実行中のアプリケーションとデバイスの特性によっては、Defender for Endpoint for Linux を実行するときに最適でないパフォーマンスが発生する場合があります。 特に、短時間で多くのリソースにアクセスするアプリケーションまたはシステム プロセスは、Defender for Endpoint for Linux のパフォーマンスの問題につながる可能性があります。

開始する前に、 **他のセキュリティ製品がデバイスで現在実行されていないか確認してください**。 複数のセキュリティ製品が競合し、ホストのパフォーマンスに影響を与える可能性があります。

次の手順を使用して、これらの問題のトラブルシューティングと軽減を行います。

1. 次のいずれかの方法を使用してリアルタイム保護を無効にし、パフォーマンスが向上するかどうかを確認します。 この方法は、Defender for Endpoint for Linux がパフォーマンスの問題に貢献するかどうかを絞り込むのに役立ちます。

    デバイスが組織によって管理されていない場合は、コマンド ラインからリアルタイム保護を無効にすることができます。

    ```bash
    mdatp config real-time-protection --value disabled
    ```
    ```Output
    Configuration property updated
    ```

    デバイスが組織によって管理されている場合は [、「Defender for Endpoint for Linux](linux-preferences.md)の設定」の手順に従って、管理者がリアルタイム保護を無効にすることができます。

    リアルタイム保護がオフの間にパフォーマンスの問題が解決しない場合、問題の発生源はエンドポイント検出および応答コンポーネントである可能性があります。 この場合、詳細な手順と軽減策については、カスタマー サポートにお問い合わせください。

2. 最も多くのスキャンをトリガーしているアプリケーションを見つけるには、Defender for Endpoint for Linux によって収集されたリアルタイム統計を使用できます。

    > [!NOTE]
    > この機能は、バージョン 100.90.70 以降で使用できます。

    この機能は、既定で and チャネル `Dogfood` で有効 `InsiderFast` になっています。 別の更新チャネルを使用している場合は、コマンド ラインからこの機能を有効にできます。
    ```bash
    mdatp config real-time-protection-statistics --value enabled
    ```

    この機能では、リアルタイム保護を有効にする必要があります。 リアルタイム保護の状態を確認するには、次のコマンドを実行します。

    ```bash
    mdatp health --field real_time_protection_enabled
    ```

    エントリが `real_time_protection_enabled` . `true` それ以外の場合は、次のコマンドを実行して有効にしてください。

    ```bash
    mdatp config real-time-protection --value enabled
    ```
    ```Output
    Configuration property updated
    ```

    現在の統計情報を収集するには、次のコマンドを実行します。

    ```bash
    mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
    ```

    > [!NOTE]
    > 使用 ```--output json``` (ダブル ダッシュに注意してください) を使用すると、出力形式が解析の準備ができていることを確認します。

    このコマンドの出力には、すべてのプロセスと関連するスキャン アクティビティが表示されます。

3. Linux システムで、次のコマンドを使用して **python パーサー high_cpu_parser.py の** サンプルをダウンロードします。

    ```bash
    wget -c https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```
    このコマンドの出力は、次のようになります。

    ```Output
    --2020-11-14 11:27:27-- https://raw.githubusercontent.com/microsoft.mdatp-xplat/master/linus/diagnostic/high_cpu_parser.py
    Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.xxx.xxx
    Connecting to raw.githubusercontent.com (raw.githubusercontent.com)| 151.101.xxx.xxx| :443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1020 [text/plain]
    Saving to: 'high_cpu_parser.py'

    100%[===========================================>] 1,020    --.-K/s   in 0s
    ```

4. 次に、次のコマンドを入力します。

    ```bash
    chmod +x high_cpu_parser.py
    ```

    ```bash
    cat real_time_protection.json | python high_cpu_parser.py  > real_time_protection.log
    ```

      上記の出力は、パフォーマンスの問題に対する上位の投稿者の一覧です。 最初の列はプロセス識別子 (PID)、2 番目の列は te プロセス名、最後の列はスキャンされたファイルの数で、影響順に並べ替えます。
    たとえば、コマンドの出力は次のようになります。 

    ```Output
    ... > python ~/repo/mdatp-xplat/linux/diagnostic/high_cpu_parser.py <~Downloads/output.json | head -n 10
    27432 None 76703
    73467 actool     1249
    73914 xcodebuild 1081
    73873 bash 1050
    27475 None 836
    1    launchd    407
    73468 ibtool     344
    549  telemetryd_v1   325
    4764 None 228
    125  CrashPlanService 164
    ```

    Defender for Endpoint for Linux のパフォーマンスを向上させるために、行の下に数値が最も高いディフェンダーを見つけて除外 `Total files scanned` を追加します。 詳細については、「Defender for Endpoint for Linux の除外の構成と検証 [」を参照してください](linux-exclusions.md)。

    >[!NOTE]
    > アプリケーションは、統計をメモリに格納し、ファイルのアクティビティが開始され、リアルタイム保護が有効にされた後にのみ追跡します。 リアルタイム保護がオフの前または期間中に起動されたプロセスはカウントされません。 さらに、トリガーされたスキャンがカウントされるイベントのみ。

5. パフォーマンスの問題に寄与するプロセスまたはディスクの場所を除外して、Microsoft Defender ATP for Linux を構成し、リアルタイム保護を再び有効にしてください。

    詳細については、「Linux 用 Microsoft Defender ATP の除外の構成と検証 [」を参照してください](linux-exclusions.md)。