---
title: デバイス プロキシとインターネット接続の設定を構成する
description: クラウド サービスとの通信を有効にするには、Microsoft Defender ATP プロキシとインターネット設定を構成します。
keywords: configure, proxy, internet, internet connectivity, settings, proxy settings, netsh, winhttp, proxy server
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
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: ce8599556b1d0c8efbd020d525b30ed2cedaa9cb
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51165467"
---
# <a name="configure-device-proxy-and-internet-connectivity-settings"></a>デバイス プロキシとインターネット接続の設定を構成する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/en-us/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Defender for Endpoint センサーでは、センサー データを報告し、Defender for Endpoint サービスと通信するために Microsoft Windows HTTP (WinHTTP) が必要です。

埋め込み Defender for Endpoint センサーは、LocalSystem アカウントを使用してシステム コンテキストで実行されます。 センサーは、Microsoft Windows HTTP Services (WinHTTP) を使用して、Defender for Endpoint クラウド サービスとの通信を有効にしています。

>[!TIP]
>インターネットへのゲートウェイとして転送プロキシを使用する組織では、ネットワーク保護を使用してプロキシの背後を調査できます。 詳細については、「[転送プロキシの背後で発生する接続イベントの調査](investigate-behind-proxy.md)」を参照してください。

WinHTTP 構成設定は、Windows Internet (WinINet) インターネット ブラウズ プロキシ設定とは独立し、次の検出方法を使用してのみプロキシ サーバーを検出できます。

- 自動検出の方法:
  - 透過プロキシ
  - Web プロキシ自動発見プロトコル (WPAD)

    > [!NOTE]
    > ネットワーク トポロジで透過プロキシまたは WPAD を使用している場合は、特別な構成設定は必要ない。 プロキシの Defender for Endpoint URL 除外の詳細については、「プロキシ サーバーで Defender for Endpoint Service URL へのアクセスを有効にする」 [を参照してください](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)。

- 手動の静的プロキシの構成:
  - レジストリ ベースの構成
  - netsh コマンドを使用して構成された WinHTTP – 安定したトポロジのデスクトップ (同じプロキシの背後にある企業ネットワークのデスクトップなど) だけに適しています。

## <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>レジストリ ベースの静的プロキシを使用して、プロキシ サーバーを手動で構成します。

コンピューターがインターネットへの接続を許可されていない場合、Defender for Endpoint センサーだけが診断データを報告し、Defender for Endpoint サービスと通信できるレジストリ ベースの静的プロキシを構成します。

静的プロキシは、グループ ポリシー (GP) を使用して構成できます。 グループ ポリシーは次の場所にあります。

- 管理用> Windows コンポーネント>データ収集とプレビュー ビルド> 接続されたユーザー エクスペリエンスとテレメトリ サービスの認証プロキシの使用を構成する
  - [有効] **に設定し** 、[ **認証されたプロキシの使用を** 無効にする: ![ グループ ポリシーのイメージ設定 1] を選択します。](images/atp-gpo-proxy1.png)
- **管理用テンプレート > Windows コンポーネント**>データ収集とプレビュー ビルド>接続されたユーザー エクスペリエンスと利用統計情報を構成する:
  - プロキシを構成します。<br>
    ![グループ ポリシー設定 2 のイメージ](images/atp-gpo-proxy2.png)

    このポリシーは、レジストリ キー `HKLM\Software\Policies\Microsoft\Windows\DataCollection` の下に 2 つのレジストリ値 `TelemetryProxyServer` を REG_SZ として、`DisableEnterpriseAuthProxy` を REG_DWORD として設定します。

    レジストリ値は、 `TelemetryProxyServer` 次の文字列形式を取ります。

    ```text
    <server name or ip>:<port>
    ```

    例: 10.0.0.6:8080

    レジストリ値 `DisableEnterpriseAuthProxy` を 1に設定する必要があります。

## <a name="configure-the-proxy-server-manually-using-netsh-command"></a>netsh コマンドを使用してプロキシ サーバーを手動で構成する

netsh を使用して、システム全体の静的プロキシを構成します。

> [!NOTE]
> - これは、既定のプロキシで WinHTTP を使用する Windows サービスを含むすべてのアプリケーションに影響します。</br>
> - トポロジを変更しているラップトップ (たとえば、オフィスから自宅) は netsh に誤動作します。 レジストリ ベースの静的プロキシの構成を使用します。

1. 管理者特権でのコマンド ラインを開きます。

    a. **[スタート]** をクリックし、「**cmd**」と入力します。

    b. **[コマンド プロンプト]** を右クリックして **[管理者として実行]** を選択します。

2. 次のコマンドを入力して、**Enter** キーを押します。

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   例: netsh winhttp set proxy 10.0.0.6:8080

winhttp プロキシをリセットするには、次のコマンドを入力して Enter キーを押 **します。**

```PowerShell
netsh winhttp reset proxy
```

詳細については、「[Netsh コマンドの構文、コンテキスト、およびフォーマット](https://docs.microsoft.com/windows-server/networking/technologies/netsh/netsh-contexts)」を参照してください。

## <a name="enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server"></a>プロキシ サーバーで Microsoft Defender for Endpoint サービス URL へのアクセスを有効にする

プロキシまたはファイアウォールが既定ですべてのトラフィックをブロックし、特定のドメインの通過だけを許可している場合は、ダウンロード可能シートに記載されているドメインを許可ドメインのリストに追加します。

次のダウンロード可能なスプレッドシートには、ネットワークが接続できる必要があるサービスと関連付けられている URL が一覧表示されます。 これらの URL へのアクセスを拒否するファイアウォールまたはネットワーク フィルター ルールが存在しないか、許可ルールを作成する必要があります。 


|**ドメインリストのスプレッドシート**|**説明**|
|:-----|:-----|
|![Microsoft Defender for Endpoint URL スプレッドシートのサム イメージ](images/mdatp-urls.png)<br/>  | サービスの場所、地理的な場所、および OS の特定の DNS レコードのスプレッドシート。 <br><br>[ここにスプレッドシートをダウンロードします。](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx) 


プロキシまたはファイアウォールで HTTPS スキャン (SSL 検査) が有効になっている場合は、上記の表に示されているドメインを HTTPS スキャンから除外します。

> [!NOTE]
> settings-win.data.microsoft.com は、バージョン 1803 以前を実行している Windows 10 デバイスがある場合にのみ必要です。<br>


> [!NOTE]
> v20 を含む URL は、バージョン 1803 以降を実行している Windows 10 デバイスがある場合にのみ必要です。 たとえば、バージョン 1803 以降を実行し、米国のデータ ストレージ領域にオンボードされている ```us-v20.events.data.microsoft.com``` Windows 10 デバイスに必要です。


> [!NOTE]
> 環境で Microsoft Defender ウイルス対策を使用している場合は、「Microsoft Defender ウイルス対策クラウド サービスへのネットワーク接続を構成する」 [を参照してください](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/configure-network-connections-microsoft-defender-antivirus)。

Defender for Endpoint センサーがシステム コンテキストから接続している場合、プロキシまたはファイアウォールが匿名トラフィックをブロックしている場合は、以前にリストした URL で匿名トラフィックが許可されている必要があります。

### <a name="microsoft-monitoring-agent-mma---proxy-and-firewall-requirements-for-older-versions-of-windows-client-or-windows-server"></a>Microsoft Monitoring Agent (MMA) - 以前のバージョンの Windows クライアントまたは Windows Server のプロキシとファイアウォールの要件

以下の情報は、Windows 7 SP1、Windows 8.1、Windows Server 2008 R2、Windows Server 2012 R2、Windows Server 2016 などの以前のバージョンの Windows の Log Analytics エージェント (Microsoft Monitoring Agent と呼ばれます) との通信に必要なプロキシおよびファイアウォール構成情報を示しています。

|エージェント リソース|ポート |Direction |HTTPS 検査のバイパス|
|------|---------|--------|--------|   
|*.ods.opinsights.azure.com |ポート 443 |送信|はい |  
|*.oms.opinsights.azure.com |ポート 443 |送信|はい |  
|*.blob.core.windows.net |ポート 443 |送信|はい |
|*.azure-automation.net |ポート 443 |送信|はい |  


> [!NOTE]
> クラウドベースのソリューションとして、IP 範囲が変更される可能性があります。 DNS 解決設定に移動する必要があります。

## <a name="confirm-microsoft-monitoring-agent-mma-service-url-requirements"></a>Microsoft 監視エージェント (MMA) サービス URL の要件を確認する 

以前のバージョンの Windows で Microsoft Monitoring Agent (MMA) を使用する場合、特定の環境のワイルドカード (*) 要件を排除するには、次のガイダンスを参照してください。

1.  Microsoft Monitoring Agent (MMA) を使用して以前のオペレーティング システムを Defender for Endpoint にオンボードします (詳細については、「Defender [on Defender](https://go.microsoft.com/fwlink/p/?linkid=2010326) およびオンボード Windows サーバーの以前のバージョンの Windows のオンボード」を [参照してください](configure-server-endpoints.md#windows-server-2008-r2-sp1-windows-server-2012-r2-and-windows-server-2016)。

2.  コンピューターが Microsoft Defender セキュリティ センター ポータルに正常に報告されたことを確認します。

3.  "C:\Program Files\Microsoft Monitoring Agent\Agent" の TestCloudConnection.exe ツールを実行して、接続を検証し、特定のワークスペースに必要な URL を確認します。

4.  Microsoft Defender for Endpoint URL リストで、地域の要件の完全な一覧を確認します (「サービス URL スプレッドシート」を参照 [してください](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx))。

![管理者のWindows PowerShell](images/admin-powershell.png)

*.ods.opinsights.azure.com、*.oms.opinsights.azure.com、および *.agentsvc.azure-automation.net URL エンドポイントで使用されるワイルドカード (*) は、特定の Workspace ID に置き換えます。 ワークスペース ID は環境とワークスペースに固有の ID で、Microsoft Defender セキュリティ センター ポータル内のテナントの [オンボーディング] セクションにあります。

*.blob.core.windows.net URL エンドポイントは、テスト結果の 「ファイアウォール ルール: *.blob.core.windows.net」セクションに示されている URL に置き換え可能です。 

> [!NOTE]
> Azure Security Center (ASC) 経由でオンボーディングを行う場合、複数のワークスペースが使用される可能性があります。 上記の TestCloudConnection.exe 手順を、各ワークスペースのオンボード コンピューターで実行する必要があります (ワークスペース間で *.blob.core.windows.net URL に変更が加わるかどうかを判断するには)。

## <a name="verify-client-connectivity-to-microsoft-defender-atp-service-urls"></a>Microsoft Defender ATP サービス URL へのクライアント接続を確認する

プロキシ構成が正常に完了したことを確認します。WinHTTP は環境内のプロキシ サーバーを介して検出および通信でき、プロキシ サーバーは Defender for Endpoint サービス URL へのトラフィックを許可します。

1. エンドポイント センサーの Defender が実行されている PC に [MDATP](https://aka.ms/mdatpanalyzer) クライアント アナライザー ツールをダウンロードします。

2. デバイス上に MDATPClientAnalyzer.zip のコンテンツを抽出します。

3. 管理者特権でのコマンド ラインを開きます。

    a. **[スタート]** をクリックし、「**cmd**」と入力します。

    b.  **[コマンド プロンプト]** を右クリックして **[管理者として実行]** を選択します。

4. 次のコマンドを入力して、**Enter** キーを押します。

    ```PowerShell
    HardDrivePath\MDATPClientAnalyzer.cmd
    ```

    *HardDrivePath* を、たとえば MDATPClientAnalyzer ツールがダウンロードされたパスに置き換えます

    ```PowerShell
    C:\Work\tools\MDATPClientAnalyzer\MDATPClientAnalyzer.cmd
    ```

5. *HardDrivePath**でMDATPClientAnalyzerResult.zip* フォルダーにツールによって作成されたファイルを抽出します。

6. *MDATPClientAnalyzerResult.txt* を開き、プロキシ構成の手順を実行して、サーバーの検出とサービス URL へのアクセスを有効にしたことを確認します。 <br><br>
   このツールは、Defender for Endpoint クライアントが相互作用するように構成されている Defender for Endpoint サービス URL の接続を確認します。 次に、Defender for Endpoint サービスとの通信に使用できる URL ごとに、結果を *MDATPClientAnalyzerResult.txt* ファイルに出力します。 次に例を示します。

   ```text
   Testing URL : https://xxx.microsoft.com/xxx
   1 - Default proxy: Succeeded (200)
   2 - Proxy auto discovery (WPAD): Succeeded (200)
   3 - Proxy disabled: Succeeded (200)
   4 - Named proxy: Doesn't exist
   5 - Command line proxy: Doesn't exist
   ```

少なくとも 1 つの接続オプションが (200) ステータスを返した場合、Defender for Endpoint クライアントはこの接続方法を使用してテスト済み URL と正しく通信できます。 <br><br>

ただし、接続を確認した結果が失敗を示している場合は、HTTP エラーが表示されます (「HTTP ステータス コード」を参照)。 次に、「プロキシ サーバーの Defender for Endpoint サービス URL へのアクセスを有効にする」に示されている表の [URL を使用できます](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)。 使用する URL は、オンボーディング手順で選択された地域によって異なります。

> [!NOTE]
>  接続アナライザー ツールは、ASR ルールと互換性がありません [PSExec および WMI コマンドから発生するプロセスの作成をブロックします](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction#attack-surface-reduction-rules)。 接続ツールを実行するには、この規則を一時的に無効にする必要があります。


> [!NOTE]
> TelemetryProxyServer がレジストリまたはグループ ポリシーを介して設定されている場合、Defender for Endpoint は、定義されたプロキシにアクセスできない場合、直接に戻されます。

## <a name="related-topics"></a>関連項目

- [オンボード Windows 10 デバイス](configure-endpoints.md)
- [Microsoft Defender for Endpoint オンボーディングの問題のトラブルシューティング](troubleshoot-onboarding.md)