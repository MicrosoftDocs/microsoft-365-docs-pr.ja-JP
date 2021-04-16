---
title: Microsoft Defender for Endpoint for Mac のインストールに関する問題のトラブルシューティング
description: Microsoft Defender for Endpoint for Mac のインストールに関する問題のトラブルシューティングを行います。
keywords: microsoft, defender, atp, mac, install
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
ms.openlocfilehash: d2ad3160c9f36a27dc98f44365433de5f8b26bb2
ms.sourcegitcommit: 22505ce322f68a2d0ce70d71caf3b0a657fa838a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "51861433"
---
# <a name="troubleshoot-installation-issues-for-microsoft-defender-for-endpoint-on-macos"></a>macOS での Microsoft Defender for Endpoint のインストールの問題のトラブルシューティング

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**

- [macOS 用 Microsoft Defender for Endpoint](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="installation-failed"></a>インストールに失敗しました

手動インストールの場合、インストール ウィザードの [概要] ページには、「インストール中にエラーが発生しました。 インストーラーでエラーが発生し、インストールに失敗しました。 ソフトウェア製造元にお問い合わせください。" MDM の展開では、一般的なインストールエラーとして表示されます。

エンド ユーザーに正確なエラーは表示されませんが、インストールの進行状況を示すログ ファイルを保持します `/Library/Logs/Microsoft/mdatp/install.log` 。 このログ ファイルには、各インストール セッションが追加されます。 最後のインストール `sed` セッションのみを出力するために使用できます。

```bash
sed -n 'H; /^preinstall com.microsoft.wdav begin/h; ${g;p;}' /Library/Logs/Microsoft/mdatp/install.log
```
```Output
preinstall com.microsoft.wdav begin [2020-03-11 13:08:49 -0700] 804
INSTALLER_SECURE_TEMP=/Library/InstallerSandboxes/.PKInstallSandboxManager/CB509765-70FC-4679-866D-8A14AD3F13CC.activeSandbox/89FA879B-971B-42BF-B4EA-7F5BB7CB5695
correlation id=CB509765-70FC-4679-866D-8A14AD3F13CC
[ERROR] Downgrade from 100.88.54 to 100.87.80 is not permitted
preinstall com.microsoft.wdav end [2020-03-11 13:08:49 -0700] 804 => 1
```

この例では、実際の理由の先頭に . が付く `[ERROR]` 。
これらのバージョン間のダウングレードがサポートされていないため、インストールに失敗しました。

## <a name="mdatp-install-log-missing-or-not-updated"></a>MDATP インストール ログが見つからないか更新されない

まれに、インストールは MDATP の /Library/Logs/Microsoft/mdatp/install.log ファイルにトレースを残しません。
macOS ログを照会することで、インストールが発生したことを確認し、考えられるエラーを分析できます (これは、クライアント UI がない場合、MDM の展開に役立ちます)。 細いタイム ウィンドウを使用してクエリを実行し、膨大な量の情報が含むので、ログ プロセス名でフィルター処理することをお勧めします。

```bash
grep '^2020-03-11 13:08' /var/log/install.log
```
```Output
log show --start '2020-03-11 13:00:00' --end '2020-03-11 13:08:50' --info --debug --source --predicate 'processImagePath CONTAINS[C] "install"' --style syslog
```
