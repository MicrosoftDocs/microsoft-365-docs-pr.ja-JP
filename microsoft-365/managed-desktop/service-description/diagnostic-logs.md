---
title: 診断ログ
description: トラブルシューティング中にデバイスから収集される可能性があるログと、デバイスの保存方法
keywords: Microsoft マネージド デスクトップ、Microsoft 365、サービス、ドキュメント
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: ef7d19fef989610c10323c2a9820a5314d5e1641
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2021
ms.locfileid: "52272897"
---
# <a name="diagnostic-logs"></a>診断ログ

Microsoft Managed Desktop が管理するデバイスに関する問題のトラブルシューティングを行う場合は、報告したデバイスか、サービスによって識別されたデバイスかを問わずに、ユーザーの介入なしにデバイスから特定の診断ログを収集する必要があります。 ユーザーが生成したコンテンツや情報をユーザー ディレクトリから収集しません。 デバイスの正常性と状態に関する診断データとログ データのみを収集します。

収集されたログは 28 日間保存され、削除されます。 データ処理標準に従ってデバイスから収集されたログ [を処理します](privacy-personal-data.md)。

## <a name="data-collected"></a>収集されるデータ

この一覧には、Microsoft Managed Desktop が診断ログを収集する可能性があるすべてのフォルダー、イベント ログ、実行可能ファイル、またはレジストリの場所が含まれます。 収集される実際のデータは、このリストのサブセットであり、特定された問題に依存します。

### <a name="registry-keys"></a>レジストリ キー

- HKLM \\ SYSTEM \\ CurrentControlSet \\ Services
- HKLM \\ SOFTWARE \\ Microsoft \\ Surface
- HKLM \\ ソフトウェア ポリシー Microsoft Windows \\ \\ \\ \\ WindowsUpdate
- HKLM \\ SYSTEM \\ CurrentControlSet \\ Control \\ MUI \\ UILanguages
- HKLM \\ ソフトウェア ポリシー Microsoft \\ \\ \\ WindowsStore
- HKLM \\ ソフトウェア Microsoft Windows \\ \\ \\ CurrentVersion \\ WindowsStore \\ WindowsUpdate
- HKLM \\ SOFTWARE \\ Microsoft \\ Windows NT \\ CurrentVersion
- HKLM \\ SOFTWARE \\ Microsoft \\ Windows NT \\ CurrentVersion
- HKLM \\ SOFTWARE \\ Microsoft \\ Windows \\ CurrentVersion \\ AppModel
- HKLM \\ SYSTEM \\ CurrentControlSet \\ Control \\ FirmwareResources
- HKLM \\ SOFTWARE \\ Microsoft \\ WindowsSelfhost
- HKLM \\ ソフトウェア \\ Microsoft \\ WindowsUpdate
- HKLM \\ SOFTWARE \\ Microsoft \\ Windows \\ CurrentVersion \\ Appx
- HKLM \\ SOFTWARE \\ Microsoft \\ Windows NT \\ CurrentVersion \\ Superfetch
- HKLM \\ SYSTEM \\ Setup
- HKLM \\ ソフトウェア \\ Microsoft \\ IntuneManagementExtension
- HKLM \\ SOFTWARE \\ Microsoft \\ SystemCertificates \\ AuthRoot
- HKLM \\ SOFTWARE \\ Microsoft \\ Windows Advanced Threat Protection
- HKLM \\ SOFTWARE \\ Microsoft \\ Windows \\ CurrentVersion \\ Authentication \\ LogonUI
- HKLM \\ SOFTWARE \\ Microsoft \\ Windows \\ CurrentVersion \\ Internet Settings
- HKLM \\ ソフトウェア Microsoft Windows \\ \\ \\ CurrentVersion \\ アンインストール
- HKLM \\ ソフトウェア \\ ポリシー
- HKLM \\ SOFTWARE \\ Policies \\ Microsoft \\ Cryptography \\ Configuration \\ SSL
- HKLM \\ ソフトウェア ポリシー Microsoft Windows Advanced Threat \\ \\ \\ Protection
- HKLM \\ SOFTWARE \\ WOW6432Node \\ Microsoft \\ Windows \\ CurrentVersion \\ Uninstall
- HKLM \\ SYSTEM \\ CurrentControlSet \\ Control \\ SecurityProviders \\ SCHANNEL

### <a name="commands"></a>コマンド

- %programfiles% \\ windows defendermpcmdrun.exe \\ -GetFiles
- %windir% \\ system32 \\certutil.exe -store
- %windir% \\ system32 \\certutil.exe -store -user my
- %windir% \\ system32 \\Dsregcmd.exe /status
- %windir% \\ system32 \\ipconfig.exe /all
- %windir% \\ system32 \\ipconfig.exe/displaydns
- %windir% \\ system32 \\mdmdiagnosticstool.exe
- %windir% \\ system32msinfo32.exe \\ /report %temp% \\ MDMDiagnostics \\ msinfo32.log
- %windir% \\ system32 \\netsh.exe advfirewall show allprofiles
- %windir% \\ system32netsh.exe \\ advfirewall show global
- %windir% \\ system32 \\netsh.exe LAN ショー プロファイル
- %windir% \\ system32 \\netsh.exe winhttp show proxy
- %windir% \\ system32 \\netsh.exe wlan show profiles
- %windir% \\ system32 \\netsh.exe wlan show wlanreport
- %windir% \\ system32 \\ping.exe -n 50 localhost
- %windir% \\ system32powercfg.exe \\ /batteryreport /output %temp% \\ MDMDiagnosticsbattery-report.htm\\ l
- %windir% \\ system32powercfg.exe \\ /energy/output %temp% \\ MDMDiagnosticsenergy-report.htm\\ l
- bitsadmin /list /allusers /verbose
- fltMC.exe
- bcdedit /enum all /v
- manage-bde -protectors -get
- Windows PowerShellコマンド:
    - Get-appxpackage -allusers
    - Get-appxpackage -packagetype バンドル
    - Get-Service wuauserv
    - Get-NetFirewallRule
    - Get-WmiObject -Class win32 \_ 製品
    - Get-ComputerInfo
    - Get-Service
    - Get-Process
    - Get-WmiObject Win32 \_ PnPSignedDriver

### <a name="event-logs"></a>イベント ログ

- アプリケーション
- Microsoft-Windows-AppLocker/EXE および DLL
- Microsoft-Windows-AppLocker/MSI とスクリプト
- Microsoft-Windows-AppLocker/Packaged app-Deployment
- Microsoft-Windows-AppLocker/Packaged app-Execution
- Microsoft-Windows-Bitlocker/Bitlocker 管理
- Microsoft-Windows-SENSE/Operational
- Microsoft-Windows-SenseIR/Operational
- セットアップ
- System

### <a name="files"></a>ファイル

- %ProgramData% \\ Microsoft \\ DiagnosticLogCSP \\ コレクター \\ \* .etl
- %ProgramData% \\ \\ Microsoft IntuneManagementExtension \\ Logs \\ \* .\*
- %ProgramData% \\ Microsoft Windows Defender サポート \\ \\ \\MpSupportFiles.cab
- %ProgramData% \\ \\ Microsoft Windows \\ WlanReport \\wlan-report-latest.html
- %ProgramData% \\ \\ Microsoft Windows \\ WlanReport -SourceFileName wlan-report-latest.html
- %windir% \\ ccm \\ ログ \* .log
- %windir% \\ ccmsetup \\ ログ \* .log
- %windir% \\ ログ \\ CBS \\ cbs.log
- %windir% \\ logs \\ measuredboot \* .\*
- %windir% \\ Logs \\ WindowsUpdate \* .etl
- %windir% \\ inf \\ \* .log
- %windir% \\ サービス \\ \\ セッションActionList.xml
- %windir% \\ サービス \\ \\ セッションSessions.xml
- %windir% \\ SoftwareDistribution \\ DataStore \\ Logs \\ edb.log
- %windir% \\ SoftwareDistribution \\ DataStore \\ DataStore.edb
- %windir% \\ ログ \\ \\ dism dism.log
- %SystemRoot% \\ System32 \\ Winevt \\ ログ\\
- %appdata% \\ Microsoft Teams メディア スタック \\ \\ \\ \* .blog
- %appdata% \\ Microsoft \\ Teams \\ skylib \\ \* .blog
- %appdata% \\ Microsoft Teams メディア スタック \\ \\ \\ \* .etl
- %appdata% \\ Microsoft \\ Teams \\logs.txt
- %windir% \\ Windows \\ System32 \\ winevt \\ \* .\*