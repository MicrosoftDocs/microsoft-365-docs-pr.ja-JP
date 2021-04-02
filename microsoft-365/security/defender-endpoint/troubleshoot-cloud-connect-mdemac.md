---
title: Microsoft Defender for Endpoint for Mac のクラウド接続の問題のトラブルシューティング
description: このトピックでは、Microsoft Defender for Endpoint for Mac のクラウド接続の問題をトラブルシューティングする方法について説明します。
keywords: microsoft、 defender, atp, mac, installation, deploy, uninstallation, intune, jamf, macos, catalina, mojave, high sierra
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-lsaldanha
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: e522495fa86b5a71faa9f25cc863c29cc5d124c0
ms.sourcegitcommit: 7b8104015a76e02bc215e1cf08069979c70650ae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/31/2021
ms.locfileid: "51476687"
---
# <a name="troubleshoot-cloud-connectivity-issues-for-microsoft-defender-for-endpoint-for-mac"></a>Microsoft Defender for Endpoint for Mac のクラウド接続の問題のトラブルシューティング

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**プラットフォーム** macOS

このトピックでは、Microsoft Defender for Endpoint for Mac のクラウド接続の問題をトラブルシューティングする方法について説明します。

## <a name="run-the-connectivity-test"></a>接続テストの実行
Defender for Endpoint for Mac が現在のネットワーク設定とクラウドと通信できる場合にテストするには、コマンド ラインから接続テストを実行します。

```Bash
mdatp connectivity test
```

予期される出力:
```Bash
Testing connection with https://cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://eu-cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://wu-cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://x.cp.wd.microsoft.com/api/report ... [OK]
Testing connection with https://winatp-gw-cus.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-eus.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-weu.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-neu.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-ukw.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-uks.microsoft.com/test ... [OK]
Testing connection with https://eu-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://us-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://uk-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://v20.events.data.microsoft.com/ping ... [OK]
```

接続テストに失敗した場合は、デバイスにインターネット アクセス権が設定[](microsoft-defender-endpoint-mac.md#network-connections)されているのか、製品で必要なエンドポイントがプロキシまたはファイアウォールによってブロックされているのか確認します。

カール エラー 35 または 60 のエラーは、証明書のピン留め拒否を示し、SSL または HTTPS 検査の潜在的な問題を示します。 SSL 検査の構成については、以下の手順を参照してください。

## <a name="troubleshooting-steps-for-environments-without-proxy-or-with-proxy-autoconfig-pac-or-with-web-proxy-autodiscovery-protocol-wpad"></a>プロキシのない環境、またはプロキシ自動構成 (PAC) または Web プロキシ自動検出プロトコル (WPAD) を使用した環境のトラブルシューティング手順
次の手順を使用して、プロキシのない環境、またはプロキシ自動構成 (PAC) または Web プロキシ自動検出プロトコル (WPAD) を使用して接続がブロックされていないとテストします。

プロキシまたはファイアウォールが匿名トラフィックをブロックしている場合は、以前にリストした URL で匿名トラフィックが許可されている必要があります。

> [!WARNING]
> 認証されたプロキシはサポートされていません。 PAC、WPAD、または静的プロキシだけが使用されている必要があります。 SSL 検査および代行受信プロキシも、セキュリティ上の理由からサポートされていません。 SSL インスペクションとプロキシ サーバーが、Microsoft Defender for Endpoint for Mac からインターセプトなしで関連する URL にデータを直接渡す例外を構成します。 インターセプト証明書をグローバル ストアに追加すると、傍受は許可されない。
接続がブロックされていないとテストするには:Microsoft Edge for Mac や Safari などのブラウザーで開き https://x.cp.wd.microsoft.com/api/report 、 を開きます https://cdn.x.cp.wd.microsoft.com/ping 。

必要に応じて、ターミナルで次のコマンドを実行します。

```Bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping' 
```

このコマンドの出力は、次の値に似ている必要があります。
```bash
OK https://x.cp.wd.microsoft.com/api/report
OK https://cdn.x.cp.wd.microsoft.com/ping
```