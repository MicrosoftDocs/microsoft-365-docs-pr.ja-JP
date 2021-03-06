---
title: macOS で Microsoft Defender for Endpoint でスキャンをスケジュールする方法
description: 組織の資産をより保護するために、macOS の Microsoft Defender for Endpoint の自動スキャン時間をスケジュールする方法について説明します。
keywords: microsoft、defender、Microsoft Defender for Endpoint、mac、スキャン、ウイルス対策
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
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: a93ea3427c72eb5529715b92cb18d01462493cc6
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2021
ms.locfileid: "52842856"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>macOS で Microsoft Defender for Endpoint でスキャンをスケジュールする

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Defender for Endpoint を使用していつでも脅威スキャンを開始することができますが、企業はスケジュールされたスキャンや時間指定スキャンのメリットを得る可能性があります。 たとえば、すべての作業日または週の初めにスキャンを実行するスケジュールを設定できます。 

## <a name="schedule-a-scan-with-launchd"></a>起動したスキャンを *スケジュールする*

macOS デバイスで起動されたデーモンを使用 *してスキャン* スケジュールを作成できます。

1. 次のコードは、スキャンをスケジュールするために使用する必要があるスキーマを示しています。 テキスト エディターを開き、この例を独自のスケジュールされたスキャン ファイルのガイドとして使用します。

    ここで使用する *.plist ファイル* 形式の詳細については、Apple の公式開発者向け Web サイトの「 [情報プロパティ リスト](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) ファイルについて」を参照してください。

    ```XML
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
      "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
        <key>Label</key>
        <string>com.microsoft.wdav.schedquickscan</string>
        <key>ProgramArguments</key>
        <array>
            <string>sh</string>
            <string>-c</string>
            <string>/usr/local/bin/mdatp scan quick</string>
        </array>
        <key>RunAtLoad</key>
        <true/>
        <key>StartCalendarInterval</key>
        <dict>
            <key>Day</key>
            <integer>3</integer>
            <key>Hour</key>
            <integer>2</integer>
            <key>Minute</key>
            <integer>0</integer>
            <key>Weekday</key>
            <integer>5</integer>
        </dict>
        <key>WorkingDirectory</key>
        <string>/usr/local/bin/</string>
    </dict>
    </plist>
     ```

2. ファイルを *com.microsoft.wdav.schedquickscan.plist として保存します*。

    > [!TIP]
    > クイック スキャンの代わりにフル スキャンを実行するには、行 12 を変更し、(つまり) の代わりにオプションを使用し、ファイルを `<string>/usr/local/bin/mdatp scan quick</string>` `full` `quick` `<string>/usr/local/bin/mdatp scan full</string>` *com.microsoft.wdav.sched の代わりに com.microsoft.wdav.sched* full *scan.plist* として保存します。

3. ターミナルを **開きます**。
4. ファイルを読み込むには、次のコマンドを入力します。

    ```bash
    launchctl load /Library/LaunchDaemons/<your file name.plist>
    launchctl start <your file name>
    ```

5. スケジュールされたスキャンは、p リストで定義した日付、時刻、および頻度で実行されます。 この例では、スキャンは毎週金曜日の午前 2 時に実行されます。 

    値 `Weekday` は、週の 5 日目または金曜日を示すために整数 `StartCalendarInterval` を使用します。

 > [!IMPORTANT]
 > 起動済みで *実行された* エージェントは、デバイスがスリープ状態の間、スケジュールされた時刻に実行されません。 デバイスがスリープ モードから再開すると、代わりに実行されます。
 >
 > デバイスがオフになっている場合、スキャンは次のスケジュールされたスキャン時間に実行されます。

## <a name="schedule-a-scan-with-intune"></a>Intune でスキャンをスケジュールする

また、スキャンをスケジュールすることもできます。Microsoft Intune。 Microsoft [Defender](https://github.com/microsoft/shell-intune-samples/tree/master/Misc/MDATP) [for Endpoint runMDATPQuickScan.sh](https://github.com/microsoft/shell-intune-samples/tree/master/Misc/MDATP#runmdatpquickscansh)使用可能なシェル スクリプトは、デバイスがスリープ モードから再開しても保持されます。 

エンタープライズ [でこのスクリプトを使用する](/mem/intune/apps/macos-shell-scripts) 方法の詳細については、「Intune の macOS デバイスでシェル スクリプトを使用する」を参照してください。
