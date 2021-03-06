---
title: Microsoft 365接続テスト ツール
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/21/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365接続テスト ツール
ms.openlocfilehash: 8cb25dfc8d11ca28d1a3c35985d84126f0652439
ms.sourcegitcommit: fb6c5e04ade1e82b26b2f911577b5ac721f1c544
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2021
ms.locfileid: "52470594"
---
# <a name="microsoft-365-network-connectivity-test-tool"></a>Microsoft 365接続テスト ツール

ネットワークMicrosoft 365テスト ツールは、 に位置します <https://connectivity.office.com> 。 このツールは、正常性サーバーの下の Microsoft 365 管理センターで利用可能なネットワーク評価およびネットワーク分析情報の| **[接続]** メニュー。

> [!IMPORTANT]
> すべてのテスト レポートが管理者と共有され、サインイン中にテナントにアップロードされる場合は、Microsoft 365 テナントにサインインすることが重要です。

> [!div class="mx-imgBorder"]
> ![接続テスト ツール](../media/m365-mac-perf/m365-mac-perf-test-tool-page.png)

>[!NOTE]
>ネットワーク接続テスト ツールは、WW Commercial および Germany のテナントをサポートしますが、モデレート、GCC、GCC、中国ではサポートされません。

Microsoft 365 管理センターのネットワークインサイトは、Microsoft 365 テナントの定期的な製品内測定値に基づいており、毎日集計されます。 一方、ネットワーク接続テストMicrosoft 365ネットワーク分析情報は、ツール内でローカルで 1 回実行されます。 製品内で実行できるテストは制限され、ユーザーにローカルでテストを実行することで、より多くのデータを収集し、より深い分析情報を得られる可能性があります。 次に、Microsoft 365 管理センターのネットワーク分析情報に、特定のオフィスの場所で Microsoft 365を使用するネットワーク上の問題が表示されます。 接続Microsoft 365テストは、推奨されるネットワーク パフォーマンス向上アクションにつながる問題の根本原因を特定するのに役立ちます。

これらの分析情報を一緒に使用して、Microsoft 365 管理センターの各オフィスの場所についてネットワーク品質の状態を評価し、Microsoft 365 接続テストに基づくテストの展開後に詳細を確認することをお勧めします。

>[!IMPORTANT]
>Microsoft 365 管理センターのネットワーク分析情報、パフォーマンスの推奨事項、評価は現在プレビュー状態であり、機能プレビュー プログラムに登録されている Microsoft 365 テナントでのみ使用できます。

## <a name="what-happens-at-each-test-step"></a>各テスト ステップで何が起こるか

### <a name="office-location-identification"></a>Office場所の識別

[テストの実行] ボタンをクリックすると、実行中のテスト ページが表示され、オフィスの場所が特定されます。 市区町場、州、国別に場所を入力するか、Web ブラウザーから検出することができます。 検出された場合は、Web ブラウザーから緯度と経度を要求し、使用する前に精度を 300 メートルから 300 メートルに制限します。 これは、ネットワークパフォーマンスのために建物よりも正確に場所を特定する必要がないので、これを行います。 

### <a name="javascript-tests"></a>JavaScript テスト

オフィスの場所を特定した後、JavaScript で TCP 遅延テストを実行し、サービスのフロント ドア サーバーで使用および推奨されるサービスに関するデータOffice 365要求します。 これらのテストが完了すると、マップ上および詳細タブに表示され、次の手順の前に表示されます。

### <a name="download-the-advanced-tests-client-application"></a>高度なテスト クライアント アプリケーションをダウンロードする

次に、高度なテスト クライアント アプリケーションのダウンロードを開始します。 クライアント アプリケーションを起動するには、ユーザーに依存し、.NET Core もインストールされている必要があります。

ネットワーク接続テストには、web サイトMicrosoft 365高度なネットワーク接続テストを実行するダウンロード可能Windowsクライアント アプリケーションの 2 つの部分 <https://connectivity.office.com> があります。 ほとんどのテストでは、アプリケーションを実行する必要があります。 実行すると、結果が Web ページに読み込み戻されます。

Web ブラウザーのテストが完了した後、Web サイトから高度なクライアント テスト アプリケーションをダウンロードするように求めるメッセージが表示されます。 プロンプトが表示されたら、ファイルを開いて実行します。

> [!div class="mx-imgBorder"]
> ![高度なテスト クライアント アプリケーション](../media/m365-mac-perf/m365-mac-perf-open-run-file.png)

### <a name="start-the-advanced-tests-client-application"></a>高度なテスト クライアント アプリケーションを開始する

クライアント アプリケーションが起動すると、Web ページが更新され、この結果が表示されます。 テスト データは、Web ページへの受信を開始します。 新しいデータを受信する度にページが更新され、データが到着すると確認できます。

### <a name="advanced-tests-completed-and-test-report-upload"></a>高度なテストが完了し、レポートのアップロードをテストする

テストが完了すると、Web ページと高度なテスト クライアントの両方にそれが表示されます。 ユーザーがサインインしている場合、テスト レポートは顧客のテナントにアップロードされます。

## <a name="sharing-your-test-report"></a>テスト レポートの共有

テスト レポートには、ユーザーのアカウントにサインインOffice 365があります。 管理者は、テスト レポートの共有方法を選択します。

### <a name="sharing-your-report-with-your-administrator"></a>管理者とレポートを共有する

テスト レポートが発生するときにサインインしている場合、そのレポートは管理者と共有されます。

### <a name="sharing-with-your-microsoft-account-team-support-or-other-personnel"></a>Microsoft アカウント チーム、サポート、その他の担当者との共有

テスト レポート (個人識別を除く) は、Microsoft の従業員と共有されます。 この共有は既定で有効になり、正常性サーバーで管理者が **無効|管理センターの**[ネットワークMicrosoft 365] ページ。

### <a name="sharing-with-other-users-who-sign-in-to-the-same-office-365-tenant"></a>同じテナントにサインインする他のユーザー Office 365する

レポートを共有するユーザーを選択できます。 選択できる状態は既定で有効になっていますが、管理者が無効にできます。

> [!div class="mx-imgBorder"]
> ![テスト結果へのリンクをユーザーと共有する](../media/m365-mac-perf/m365-mac-perf-share-to-user.png)

### <a name="sharing-with-anyone-using-a-reportid-link"></a>ReportID リンクを使用しているユーザーとの共有

ReportID リンクへのアクセスを提供することで、テスト レポートを誰とでも共有できます。 このリンクは、サインインせずにテスト レポートを表示できるよう、誰かに送信できる URL を生成します。 この共有は既定で無効になっているので、管理者が有効にする必要があります。

> [!div class="mx-imgBorder"]
> ![テスト結果へのリンクを共有する](../media/m365-mac-perf/m365-mac-perf-share-link.png)

## <a name="network-connectivity-test-results"></a>ネットワーク接続テストの結果

結果は、[概要] タブ **と [詳細] タブ****に表示** されます。 [概要] タブには、検出されたネットワーク境界のマップと、近くの他のユーザーとのネットワーク評価Office 365表示されます。 また、テスト レポートの共有も可能です。 概要結果ビューの外観を次に示します。

> [!div class="mx-imgBorder"]
> ![ネットワーク接続テスト ツールの概要結果](../media/m365-mac-perf/m365-mac-perf-summary-page.png)

ツールに表示される詳細タブ出力の例を次に示します。 [詳細] タブに、結果がしきい値と良好に比較された場合、緑色の円のチェック マークが表示されます。 結果がネットワークインサイトを示すしきい値を超えた場合、赤い三角形の感嘆符が表示されます。 次のセクションでは、各詳細タブの結果行について説明し、ネットワークインサイトに使用されるしきい値について説明します。

> [!div class="mx-imgBorder"]
> ![ネットワーク接続テスト ツールのテスト結果の例](../media/m365-mac-perf/m365-mac-perf-all-details.png)

### <a name="your-location-information"></a>位置情報

このセクションには、場所に関連するテスト結果が表示されます。

#### <a name="your-location"></a>お客様の場所

ユーザーの場所は、ユーザー Web ブラウザーから検出されます。 また、ユーザーの選択で入力できます。 これは、エンタープライズ ネットワーク境界の特定の部分へのネットワーク距離を識別するために使用されます。 この場所検出からの都市と他のネットワーク ポイントまでの距離だけがレポートに保存されます。

ユーザーのオフィスの場所がマップ ビューに表示されます。

#### <a name="network-egress-location-the-location-where-your-network-connects-to-your-isp"></a>ネットワーク出力の場所 (ネットワークが ISP に接続する場所)

サーバー側のネットワーク出力 IP アドレスを識別します。 場所データベースは、ネットワーク出力のおおよその場所を検索するために使用されます。 これらのデータベースは通常、IP アドレスの約 90% の精度を持っています。 ネットワーク出力 IP アドレスから探した場所が正確ではない場合は、このテストで誤った結果が発生します。 特定の IP アドレスに対してこのエラーが発生している場合は、パブリックアクセス可能なネットワーク IP アドレスの場所 Web サイトを使用して、実際の場所と比較できます。

#### <a name="your-distance-from-the-network-egress-location"></a>ネットワーク出力場所からの距離

その場所からオフィスの場所までの距離を決定します。 これは、TCP 待機時間が 25 ミリ秒を超える可能性が高く、ユーザー エクスペリエンスに影響を与える可能性がある距離が **500** マイル (800 キロメートル) を超える場合のネットワーク分析情報として表示されます。

ネットワーク出力の場所がマップ ビューに表示され、エンタープライズ WAN の内部のネットワーク バックホールを示すユーザー オフィスの場所に接続されます。

ユーザーのオフィスの場所からインターネットへのローカルおよび直接ネットワーク出力の実装は、ネットワーク接続のMicrosoft 365推奨されます。 ローカル出力と直接出力の改善は、このネットワークインサイトに対処するための最良の方法です。

#### <a name="proxy-server-information"></a>プロキシ サーバー情報

ローカル コンピューターで構成されているプロキシ サーバーを識別します。 ネットワーク トラフィックを最適化するためのカテゴリをネットワーク パスで構成Microsoft 365します。 ユーザーのオフィスの場所からプロキシ サーバーまでの距離を特定します。 距離は最初に ICMP ping によってテストされ、失敗した場合は TCP ping でテストし、最後に失敗した場合は、IP アドレスの場所データベースでプロキシ サーバーの IP アドレスを確認します。 プロキシ サーバーがユーザーのオフィスの場所から **500 マイル (800** キロメートル) 以上離れた場合は、ネットワークインサイトが表示されます。

#### <a name="virtual-private-network-vpn-you-use-to-connect-to-your-organization"></a>組織への接続に使用する仮想プライベート ネットワーク (VPN)

これにより、VPN を使用してネットワークに接続Office 365。 VPN がない場合、または VPN が推奨されるスプリット トンネル構成の VPN を使用している場合は、パス結果がOffice 365。

#### <a name="vpn-split-tunnel"></a>VPN スプリット Tunnel

Exchange Online、SharePoint Online、および Microsoft Teams の各最適化されたカテゴリ ルートは、VPN でトンネリングされるのかテストされます。 分割されたワークロードは VPN を完全に回避します。 トンネル処理されたワークロードはすべて VPN を通して送信されます。 選択的なトンネリングされたワークロードには、VPN を使用して送信されるルートと分割されたルートがあります。渡す結果は、すべてのワークロードが分割または選択的トンネリングされた場合に表示されます。

#### <a name="customers-in-your-metropolitan-area-with-better-performance"></a>パフォーマンスの向上を実現する大都市圏の顧客

ユーザー オフィスの場所から Exchange Online サービスのフロント ドアへのネットワーク TCP 待機時間は、同Microsoft 365の顧客と比較されます。 同じメトロエリアの 10% 以上の顧客のパフォーマンスが向上した場合、ネットワークインサイトが表示されます。 つまり、ユーザーはユーザー インターフェイスのパフォーマンスMicrosoft 365向上します。

このネットワークインサイトは、都市内のすべてのユーザーが同じ通信インフラストラクチャにアクセスし、インターネット回線と Microsoft のネットワークに同じ近接性を持つという根拠に基づいて生成されます。

#### <a name="time-to-make-a-dns-request-on-your-network"></a>ネットワークで DNS 要求を行う時間

これは、テストを実行したクライアント コンピューターで構成された DNS サーバーを示しています。 DNS 再帰的リゾルバー サーバーである可能性があります。ただし、これは一般的ではありません。 DNS の結果をキャッシュし、キャッシュされていない DNS 要求を別の DNS サーバーに転送する DNS 転送サーバーである可能性が高い。

これは情報のみを提供し、ネットワークの洞察には貢献しない。

#### <a name="your-distance-from-andor-time-to-connect-to-a-dns-recursive-resolver"></a>DNS 再帰リゾルバーへの接続距離および/または接続時間

使用されている DNS 再帰的リゾルバーは、特定の DNS 要求を行い、同じ要求を受信した IP アドレスを DNS ネーム サーバーに要求することで識別されます。 この IP アドレスは DNS 再帰的リゾルバーであり、場所を見つけるために IP アドレスの場所データベースで検索されます。 その後、ユーザーのオフィスの場所から DNS 再帰的リゾルバー サーバーの場所までの距離が計算されます。 これは、距離が **500 マイル (800 キロ** メートル) を超える場合のネットワーク分析情報として表示されます。

ネットワーク出力 IP アドレスから見上げた場所が正確ではない可能性があります。このテストでは誤った結果が発生します。 特定の IP アドレスに対してこのエラーが発生した場合に検証するには、パブリックアクセス可能なネットワーク IP アドレスの場所 Web サイトを使用できます。

このネットワークインサイトは、サービス フロント ドアの選択Exchange Online特に影響します。 この洞察に対処するには、ローカルおよび直接のネットワーク出力が前提条件であり、DNS 再帰的リゾルバーをそのネットワーク出力の近くに位置する必要があります。

### <a name="exchange-online"></a>Exchange Online

このセクションでは、テストに関連するテスト結果をExchange Online。

#### <a name="exchange-service-front-door-location"></a>Exchangeフロント ドアの場所

Outlook がこれを行うのと同じ方法で、Exchange サービス フロント ドアの使用が識別され、ユーザーの場所からユーザーの場所へのネットワーク TCP 待機時間が測定されます。 TCP 待機時間が表示され、サービス フロント Exchangeの使用時間が、現在の場所に最適なサービス フロント ドアの一覧と比較されます。 これは、サービス フロント ドアで最もExchangeの 1 つが使用されていない場合に、ネットワーク分析情報として表示されます。

最適な Exchange サービス フロント ドアの 1 つを使用しない場合は、企業のネットワーク出力の前にネットワーク バックホールが発生する可能性があります。その場合は、ローカルおよび直接のネットワーク出力をお勧めします。 また、リモート DNS 再帰的リゾルバー サーバーを使用した場合、DNS 再帰的リゾルバー サーバーをネットワーク出力に合わせて配置することをお勧めします。

サービス フロント ドアに対する TCP 待機時間 (ms) の潜在的なExchangeを計算します。 これは、テスト済みユーザーのオフィスの場所ネットワークの待機時間を確認し、ネットワークの待機時間を現在の場所からサービス フロント ドアのExchange差し引いて行います。 違いは、改善の潜在的な機会を表します。

#### <a name="best-exchange-service-front-doors-for-your-location"></a>おExchange最適なサービス フロント ドア

このリストには、お客様Exchangeに最適なサービス フロント ドアの場所が都市別に一覧表示されます。

#### <a name="service-front-door-recorded-in-the-client-dns"></a>クライアント DNS に記録されたサービス フロント ドア

これは、指定したサービス フロント ドア サーバー Exchange DNS 名と IP アドレスを示します。 この情報は情報用に提供され、関連付けられたネットワーク分析情報はありません。

### <a name="sharepoint-online"></a>SharePoint Online

このセクションでは、オンラインとオンラインのテストに関連SharePoint結果をOneDrive。

#### <a name="the-service-front-door-location"></a>サービス フロント ドアの場所

使用している SharePoint サービス フロント ドアは、OneDrive クライアントが行うのと同じ方法で識別され、ユーザーのオフィスの場所からその場所へのネットワーク TCP 待機時間を測定します。

#### <a name="download-speed"></a>ダウンロード速度

15Mb ファイルのダウンロード速度は、サービス フロント SharePointから測定します。 結果は 1 秒あたりのメガバイト単位で表示され、1 秒に 1 mb 単位でダウンロードできるサイズ ファイルを SharePointまたはOneDrive **示します**。 この数は、1 秒あたりのメガビットの最小回線帯域幅の 10 分の 1 に似ている必要があります。 たとえば、100 mbps のインターネット接続がある場合は、1 秒あたり 10 メガバイト (10MBps) が予想されます。

#### <a name="buffer-bloat"></a>バッファーの割り当て

15Mb のダウンロード中に、サービス フロント ドアに対する TCP SharePointを測定します。 これは読み込み時の待機時間であり、負荷がかからない場合の待機時間と比較されます。 負荷が下がった場合の待機時間の増加は、多くの場合、読み込まれている (または過大化された) コンシューマー ネットワーク デバイス バッファーに起因します。 ネットワークインサイトは、1,000 以上の任意のブロートに対して表示されます。

#### <a name="service-front-door-recorded-in-the-client-dns"></a>クライアント DNS に記録されたサービス フロント ドア

これは、指定したサービス フロント ドア サーバー SharePoint DNS 名と IP アドレスを示します。 この情報は情報用に提供され、関連付けられたネットワーク分析情報はありません。

### <a name="microsoft-teams"></a>Microsoft Teams

このセクションでは、テストに関連するテスト結果をMicrosoft Teams。

#### <a name="media-connectivity-audio-video-and-application-sharing"></a>メディア接続 (オーディオ、ビデオ、およびアプリケーション共有)

このテストでは、サービス フロント ドアMicrosoft Teams UDP 接続をテストします。 これをブロックすると、TCP Microsoft Teams機能する可能性がありますが、オーディオとビデオが損なわれる可能性があります。 これらの UDP ネットワーク測定値の詳細については、「Microsoft Teams Online のメディア品質とネットワーク接続のパフォーマンス」でも[Skype for Businessしてください](/skypeforbusiness/optimizing-your-network/media-quality-and-network-connectivity-performance)。

#### <a name="packet-loss"></a>パケット損失

クライアントからサービス フロント ドアへの 10 秒間のテスト オーディオ呼び出しで測定Microsoft Teams UDP パケット損失を表示します。 これは、パスの **場合は 1.00% より** 低くする必要があります。

#### <a name="latency"></a>Latency

**100ms** より低い UDP 待機時間を示します。

#### <a name="jitter"></a>ジッター

**30ms** より低い UDP ジッターを示します。

#### <a name="connectivity"></a>接続

ユーザー オフィスの場所から必要なすべてのネットワーク エンドポイントへの HTTP 接続Microsoft 365します。 これらはで公開されています [https://aka.ms/o365ip](./urls-and-ip-address-ranges.md) 。 ネットワークインサイトは、接続できない必要なネットワーク エンドポイントに対して表示されます。

プロキシ サーバー、ファイアウォール、またはエンタープライズ ネットワーク境界上の別のネットワーク セキュリティ デバイスによって接続がブロックされる場合があります。 TCP ポート 80 への接続は HTTP 要求でテストされ、TCP ポート 443 への接続は HTTPS 要求でテストされます。 応答がない場合、FQDN はエラーとしてマークされます。 HTTP 応答コード 407 がある場合、FQDN はエラーとしてマークされます。 HTTP 応答コード 403 がある場合は、応答の Server 属性を確認し、プロキシ サーバーのように見える場合は、これをエラーとしてマークします。 コマンド ライン ツールを使用して実行Windowsをシミュレートcurl.exe。

で定義されている最適化カテゴリまたは許可カテゴリにあるMicrosoft 365ネットワーク エンドポイントで SSL 証明書をテストします [https://aka.ms/o365ip](./urls-and-ip-address-ranges.md) 。 テストで Microsoft SSL 証明書が見つからない場合は、接続されている暗号化されたネットワークが仲介ネットワーク デバイスによって傍受されている必要があります。 ネットワークインサイトは、傍受された暗号化されたネットワーク エンドポイントに表示されます。

Microsoft によって提供されていない SSL 証明書が見つかった場合は、テストの FQDN と、使用中の SSL 証明書の所有者が表示されます。 この SSL 証明書の所有者は、プロキシ サーバー ベンダーである場合や、エンタープライズ自己署名証明書である場合があります。

#### <a name="network-path"></a>ネットワーク パス

このセクションでは、Exchange Online サービス フロント ドア、SharePoint Online サービス フロント ドア、および Microsoft Teams サービス フロント ドアへの ICMP トレースルートの結果を示します。 この情報は情報用に提供され、関連付けられたネットワーク分析情報はありません。 3 つのトレース ルートが提供されています。 outlook.office365.com への _traceroute、_ 顧客への traceroute SharePoint フロントエンド、または microsoft.sharepoint.com が提供されていない場合は _microsoft.sharepoint.com_ に、traceroute は _world.tr.teams.microsoft.com。_

## <a name="connectivity-reports"></a>接続レポート

サインインすると、実行した以前のレポートを確認できます。 共有したり、リストから削除したりできます。

> [!div class="mx-imgBorder"]
> ![レポート](../media/m365-mac-perf/m365-mac-perf-reports-list.png)

## <a name="network-health-status"></a>ネットワーク正常性の状態

これは、Microsoft のグローバル ネットワークに関する重大な正常性の問題を示し、お客様のMicrosoft 365可能性があります。

> [!div class="mx-imgBorder"]
> ![ネットワーク正常性の状態](../media/m365-mac-perf/m365-mac-perf-status-page.png)

## <a name="faq"></a>FAQ

よく寄せられる質問の一部に対する回答を次に示します。

### <a name="is-this-tool-released-and-supported-by-microsoft"></a>このツールは Microsoft によってリリースされ、サポートされていますか?

現在はプレビュー版であり、Microsoft からのサポートを受け、一般提供リリースの状態に達するまで定期的に更新プログラムを提供する予定です。 改善に役立つフィードバックをお寄せください。 このツールの一部として、Office 365詳細なネットワーク オンボーディング ガイドを公開する予定です。これは、テスト結果によって組織向けにカスタマイズされます。

### <a name="what-is-required-to-run-the-advanced-test-client"></a>高度なテスト クライアントを実行するために必要な情報

高度なテスト クライアントには、.NET Core 3.1 デスクトップ ランタイムが必要です。 高度なテスト クライアントをインストールせずに実行すると [、.NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1)インストーラー ページが表示されます。 SDK ではなくデスクトップ ランタイム、またはページの上位の ASP.NET Coreランタイムをインストールしてください。 .NET Core をインストールするには、コンピューターに対する管理者のアクセス許可が必要です。

### <a name="what-is-microsoft-365-service-front-door"></a>サービス フロント Microsoft 365とは何ですか?

Microsoft 365サービス フロント ドアは、Microsoft のグローバル ネットワーク上のエントリ ポイントであり、クライアントOfficeサービスがネットワーク接続を終了します。 ネットワーク接続を最適にMicrosoft 365、都市または地下鉄の最も近いMicrosoft 365にネットワーク接続を終了する必要があります。

> [!NOTE]
> Microsoft 365フロント ドアは **、Azure マーケット** プレースで利用可能な Azure Front Door Service 製品との直接的な関係はありません。

### <a name="what-is-the-best-microsoft-365-service-front-door"></a>サービス フロント ドアでMicrosoft 365は何ですか?

ベスト Microsoft 365 サービス フロント ドア (以前は最適なサービス フロント ドアと呼ばれる) は、一般に都市または地下鉄エリアでネットワーク出力に最も近いサービスです。 ネットワーク パフォーマンス Microsoft 365ツールを使用して、サービス フロント ドアと最適Microsoft 365サービス フロント ドアの場所を特定します。 使用しているフロント ドアが最適なドアの 1 つだとツールが判断した場合は、Microsoft のグローバル ネットワークへの接続性が高い必要があります。

### <a name="what-is-an-internet-egress-location"></a>インターネットの出力場所とは何ですか?

インターネット出力場所は、ネットワーク トラフィックがエンタープライズ ネットワークから出てインターネットに接続する場所です。 これは、ネットワーク アドレス変換 (NAT) デバイスを持ち、通常はインターネット サービス プロバイダー (ISP) に接続する場所として識別されます。 場所とインターネットの出力場所との距離が長い場合は、WAN バックホールが重要な場合があります。

## <a name="related-topics"></a>関連項目

[管理センターでのネットワークMicrosoft 365 (プレビュー)](office-365-network-mac-perf-overview.md)

[Microsoft 365パフォーマンス分析情報 (プレビュー)](office-365-network-mac-perf-insights.md)

[Microsoft 365評価 (プレビュー)](office-365-network-mac-perf-score.md)

[Microsoft 365ネットワーク接続位置情報サービス (プレビュー)](office-365-network-mac-location-services.md)