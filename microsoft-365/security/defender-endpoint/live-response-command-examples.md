---
title: ライブ応答コマンドの例
description: Microsoft Defender for Endpoint の基本的なライブ応答コマンドまたは高度なライブ応答コマンドを実行する方法と、その使用例を参照してください。
keywords: たとえば、コマンド、cli、リモート、シェル、接続、ライブ、応答、リアルタイム、コマンド、スクリプト、修復、ハント、エクスポート、ログ、ドロップ、ダウンロード、ファイル
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 82052634b79bf433731d0afdab45e3d75e6497e0
ms.sourcegitcommit: 4886457c0d4248407bddec56425dba50bb60d9c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2021
ms.locfileid: "53289333"
---
# <a name="live-response-command-examples"></a>ライブ応答コマンドの例

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Defender for Endpoint を体験してみませんか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-investigateip-abovefoldlink)

ライブ応答で使用される一般的なコマンドについて説明し、その一般的な使用例を参照してください。

付与されている役割に応じて、基本的なライブ応答コマンドまたは高度なライブ応答コマンドを実行できます。 基本的なコマンドと高度なコマンドの詳細については、「ライブ応答を使用してデバイス上のエンティティを調査 [する」を参照してください](live-response.md)。

## <a name="analyze"></a>分析

```console
# Analyze the file malware.txt
analyze file c:\Users\user\Desktop\malware.txt
```

```console
# Analyze the process by PID
analyze process 1234
```

## <a name="connections"></a>接続

```console
# List active connections in json format using parameter name
connections -output json
```

```console
# List active connections in json format without parameter name
connections json
```

## <a name="dir"></a>dir

```console
# List files and sub-folders in the current folder
dir
```

```console
# List files and sub-folders in a specific folder
dir C:\Users\user\Desktop\
```

```console
# List files and subfolders in the current folder in json format
dir -output json
```

## <a name="fileinfo"></a>fileinfo

```console
# Display information about a file
fileinfo C:\Windows\notepad.exe
```

## <a name="findfile"></a>findfile

```console
# Find file by name
findfile test.txt
```

## <a name="getfile"></a>getfile

```console
# Download a file from a machine
getfile c:\Users\user\Desktop\work.txt
```

```console
# Download a file from a machine, automatically run prerequisite commands
getfile c:\Users\user\Desktop\work.txt -auto
```

>[!NOTE]
>
> 次のファイルの種類 **は、Live** Response 内からこのコマンドを使用してダウンロードできません。
>
> - [Reparse ポイント ファイル](/windows/desktop/fileio/reparse-points/)
> - [スパース ファイル](/windows/desktop/fileio/sparse-files/)
> - 空のファイル
> - 仮想ファイル、またはローカルに完全に存在しないファイル
>
> これらのファイルの種類 **は** [PowerShell でサポートされています](/powershell/scripting/overview)。
>
> Live Response 内からこのコマンドを使用する際に問題が発生した場合は、PowerShell を代わりに使用します。

## <a name="library"></a>ライブラリ

```console
# List files in the library
library
```

```console
# Delete a file from the library
library delete script.ps1
```

## <a name="processes"></a>processes

```console
# Show all processes
processes
```

```console
# Get process by pid
processes 123
```

```console
# Get process by pid with argument name
processes -pid 123
```

```console
# Get process by name
processes -name notepad.exe
```

## <a name="putfile"></a>putfile

```console
# Upload file from library
putfile get-process-by-name.ps1
```

```console
# Upload file from library, overwrite file if it exists
putfile get-process-by-name.ps1 -overwrite
```

```console
# Upload file from library, keep it on the machine after a restart
putfile get-process-by-name.ps1 -keep
```

## <a name="registry"></a>レジストリ

```console
# Show information about the values in a registry key
registry HKEY_CURRENT_USER\Console
```

```console
# Show information about a specific registry value
registry HKEY_CURRENT_USER\Console\\ScreenBufferSize
```


## <a name="remediate"></a>remediate

```console
# Remediate file in specific path
remediate file c:\Users\user\Desktop\malware.exe
```

```console
# Remediate process with specific PID
remediate process 7960
```

```console
# See list of all remediated entities
remediate list
```

## <a name="run"></a>run

```console
# Run PowerShell script from the library without arguments
run script.ps1
```

```console
# Run PowerShell script from the library with arguments
run get-process-by-name.ps1 -parameters "-processName Registry"
```

>[!NOTE]
>
> **'** run ' や '**getfile**'などの長時間実行されているコマンドの場合は、コマンドの最後に ' ' 記号を使用して、バックグラウンドでそのアクションを **&** 実行できます。
> これにより、コンピューターの調査を続行し、'**fg**' basic コマンドを使用して実行すると、バックグラウンド コマンドに [戻る可能性があります](live-response.md#basic-commands)。

## <a name="scheduledtask"></a>scheduledtask

```console
# Get all scheduled tasks
scheduledtasks
```

```console
# Get specific scheduled task by location and name
scheduledtasks Microsoft\Windows\Subscription\LicenseAcquisition
```

```console
# Get specific scheduled task by location and name with spacing
scheduledtasks "Microsoft\Configuration Manager\Configuration Manager Health Evaluation"
```

## <a name="undo"></a>元に戻す

```console
# Restore remediated registry
undo registry HKEY_CURRENT_USER\Console\ScreenBufferSize
```

```console
# Restore remediated scheduledtask
undo scheduledtask Microsoft\Windows\Subscription\LicenseAcquisition
```

```console
# Restore remediated file
undo file c:\Users\user\Desktop\malware.exe
```
