---
title: Microsoft Defender for Endpoint のホスト ファイアウォール レポート
description: セキュリティ センターでファイアウォールレポートをホストMicrosoft 365表示します。
keywords: Windows Defender, ファイアウォール
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
audience: ITPro
ms.topic: article
author: dansimp
ms.author: dansimp
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 0289d6f920fd6ff35fd446f9c2b8c5516883a4d2
ms.sourcegitcommit: e1e275eb88153bafddf93327adf8f82318913a8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2021
ms.locfileid: "52809306"
---
# <a name="host-firewall-reporting-in-microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpoint のホスト ファイアウォール レポート

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

管理者の場合は、ファイアウォール レポートをセキュリティ センターにホストMicrosoft 365[できます](https://security.microsoft.com)。 この機能を使用すると、サーバー 2019 Windows 10とWindowsレポートを一元的な場所から表示できます。 

## <a name="what-do-you-need-to-know-before-you-begin"></a>はじめに把握しておくべき情報 

- サーバー 2019 Windows 10またはWindowsする必要があります。
- デバイスを Microsoft Defender for Endpoint サービスにオンボードするには、こちらを参照 [してください](onboard-configure.md)。 
- セキュリティ センター Microsoft 365データの受信を開始するには、Advanced Security を使用して監査イベントを **有効Windows Defender ファイアウォール必要** があります。 
    - [監査フィルター プラットフォーム のパケット ドロップ](/windows/security/threat-protection/auditing/audit-filtering-platform-packet-drop)
    - [監査フィルター プラットフォーム接続](/windows/security/threat-protection/auditing/audit-filtering-platform-connection) 
- グループ ポリシー オブジェクト エディター、ローカル セキュリティ ポリシー、またはグループ ポリシー コマンドを使用して、これらのイベントauditpol.exeします。 詳細については、こちらを参照 [してください](/windows/win32/fwp/auditing-and-logging)。 
    - 2 つの PowerShell コマンドは次のとおりです。
        - **auditpol /set /subcategory:"Filtering Platform Packet Drop" /failure:enable** 
        - **auditpol /set /subcategory:"Filtering Platform Connection" /failure:enable** 

## <a name="the-process"></a>プロセス
> [!NOTE]
> 上記のセクションの指示に従い、早期プレビュー参加のためにデバイスを適切に構成してください。

- イベントを有効にすると、Microsoft 365センターがデータの監視を開始します。
    - リモート IP、リモート ポート、ローカル ポート、ローカル IP、コンピューター名、受信接続と送信接続間のプロセス。
- 管理者は、ここでホストWindowsアクティビティを確認[できます](https://security.microsoft.com/firewall)。
    - カスタム レポート スクリプトをダウンロードして、[](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall)カスタム レポートを使用してアクティビティのWindows Defender ファイアウォールを監視することで、Power BI。 
    - データが反映されるまで最大 12 時間かかる場合があります。

## <a name="supported-scenarios"></a>サポートされるシナリオ
Ring0 Preview では、次のシナリオがサポートされています。 

### <a name="firewall-reporting-in-security-center"></a>セキュリティ センターでのファイアウォールレポート

ファイアウォール レポート ページの例を次に示します。 ここでは、受信、送信、およびアプリケーションアクティビティの概要を示します。 に移動すると、このページに直接アクセスできます https://security.microsoft.com/firewall 。 

> [!div class="mx-imgBorder"]
> ![[ホスト ファイアウォールのレポート] ページ](\images\host-firewall-reporting-page.png)

これらのレポートには、ファイアウォールブロックされた受信接続カードの下部にある [セキュリティ レポート デバイスのレポート] (セクション) にアクセス  >    >  することもできます。 

### <a name="from-computers-with-a-blocked-connection-to-device"></a>"接続がブロックされているコンピューター" からデバイスへ

カードは対話型オブジェクトをサポートします。 新しいタブで起動するデバイス名をクリックして、デバイスのアクティビティをドリル インし、[デバイス タイムライン] タブ https://securitycenter.microsoft.com **に直接移動** できます。 

> [!div class="mx-imgBorder"]
> ![接続がブロックされているコンピューター](\images\firewall-reporting-blocked-connection.png)

[タイムライン] タブ **を選択** すると、そのデバイスに関連付けられたイベントの一覧が表示されます。 

表示ウィンドウの右上隅にある **[フィルター** ] ボタンをクリックした後、目的のイベントの種類を選択します。 この場合、[ファイアウォール イベント] **を選択** すると、ウィンドウはファイアウォール イベントにフィルター処理されます。 

> [!div class="mx-imgBorder"]
> ![[フィルター] ボタン](\images\firewall-reporting-filters-button.png)

### <a name="drill-into-advanced-hunting-preview-refresh"></a>高度な検索 (プレビュー更新) の詳細を確認する

ファイアウォール レポートでは、[高度な検索を開く] ボタンをクリックして、カードから高度なハンティングに直接 **ドリルを実行** できます。 クエリは事前に設定されます。 

> [!div class="mx-imgBorder"]
> ![高度な検索ボタンを開く](\images\firewall-reporting-advanced-hunting.png)

クエリを実行し、過去 30 日間のすべての関連ファイアウォール イベントを確認できます。 

追加のレポート、またはカスタムの変更については、クエリをレポートにエクスポートしてPower BI分析できます。 カスタム レポートは、カスタム レポート[](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall)スクリプトをダウンロードして、カスタム レポート を使用してWindows Defender ファイアウォールアクティビティをPower BI。 

 