---
title: Microsoft 365ネットワークインサイト
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
description: Microsoft 365ネットワークインサイト
ms.openlocfilehash: 10b1c66a8f9aae555c2841b2b290f341bec3c7ec
ms.sourcegitcommit: fb6c5e04ade1e82b26b2f911577b5ac721f1c544
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2021
ms.locfileid: "52470558"
---
# <a name="microsoft-365-network-insights"></a>Microsoft 365ネットワークインサイト

**ネットワーク分析情報は**、Microsoft 365 テナントから収集されたパフォーマンス 指標であり、テナントの管理ユーザーだけが表示できます。 インサイトは、管理センターの Microsoft 365に表示されます <https://portal.microsoft.com/adminportal/home#/networkperformance> 。

インサイトは、オフィスの場所のネットワーク境界を設計する場合に役立ちます。 各分析情報は、ユーザーがテナントにアクセスしている地理的な場所ごとに、特定の一般的な問題のパフォーマンス特性に関するライブの詳細を提供します。

各オフィスの場所に表示される可能性がある 6 つの特定のネットワーク分析情報があります。

- [バックホールされたネットワーク出力](#backhauled-network-egress)
- [ネットワーク仲介デバイス](#network-intermediary-device)
- [近くの顧客に対して検出されるパフォーマンスの向上](#better-performance-detected-for-customers-near-you)
- [サービス フロント ドアの最適Exchange Online使用](#use-of-a-non-optimal-exchange-online-service-front-door)
- [オンライン サービス フロント ドアSharePoint最適でないサービスの使用](#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [フロント ドアからのダウンロードSharePoint速度が低い](#low-download-speed-from-sharepoint-front-door)
- [中国ユーザーの最適なネットワーク出力](#china-user-optimal-network-egress)

テナントには、2 つのテナント レベルのネットワーク分析情報が表示されます。 これらは生産性スコア ページにも表示されます。

- [Exchangeの問題の影響を受け、サンプリングされた接続を確認する](#exchange-sampled-connections-impacted-by-connectivity-issues)
- [SharePointの問題の影響を受け、サンプルされた接続を確認する](#sharepoint-sampled-connections-impacted-by-connectivity-issues)

>[!IMPORTANT]
>Microsoft 365 管理センターのネットワーク分析情報、パフォーマンスの推奨事項、評価は現在プレビュー状態であり、機能プレビュー プログラムに登録されている Microsoft 365 テナントでのみ使用できます。

## <a name="backhauled-network-egress"></a>バックホールされたネットワーク出力

この分析情報は、ネットワーク インサイト サービスが、特定のユーザーの場所からネットワーク出力までの距離が 500 マイル (800 キロメートル) を超えると検出した場合に表示され、Microsoft 365 トラフィックが一般的なインターネット エッジ デバイスまたはプロキシにバックホールされたことを示します。

この分析情報は、一部の概要ビュー Egress"」と省略されます。

> [!div class="mx-imgBorder"]
> ![バックホールされたネットワーク出力](../media/m365-mac-perf/m365-mac-perf-insights-detail-backhauled.png)

### <a name="what-does-this-mean"></a>シナリオ

これは、オフィスの場所とネットワーク出力の間の距離が 500 マイル (800 キロメートル) を超える場合を識別します。 Office の場所は難読化されたクライアント コンピューターの場所によって識別され、ネットワーク出力の場所は、場所データベースへの逆 IP アドレスを使用して識別されます。 コンピューターで Location Services が無効になっている場合Windowsオフィスの場所が不正確になる可能性があります。 逆 IP アドレス データベース情報が不正確な場合、ネットワーク出力場所が不正確になる可能性があります。

この分析情報の詳細には、オフィスの場所、現在のネットワーク出力場所、出力場所の関連性、場所と現在の出力ポイント間の距離、条件が最初に検出された日付、および条件が解決された日付の合計テナント ユーザーの推定割合が含まれます。

### <a name="what-should-i-do"></a>どうすればよいですか?

この分析情報を得る場合は、ネットワーク出力をオフィスの場所に近づけて、接続を Microsoft のグローバル ネットワークと最も近いサービス フロント ドアに最適にルーティングMicrosoft 365勧めします。 また、ユーザーのオフィスの場所に近いネットワーク出力を使用すると、Microsoft が将来、プレゼンスのネットワーク ポイントと Microsoft 365 サービス フロント ドアの両方を拡張する中で、パフォーマンスが向上します。

この問題を解決する方法の詳細については、「ネットワーク[](microsoft-365-network-connectivity-principles.md#egress-network-connections-locally)接続Egress」を参照Office 365[してください](microsoft-365-network-connectivity-principles.md)。

## <a name="network-intermediary-device"></a>ネットワーク仲介デバイス

この分析情報は、ユーザーと Microsoft のネットワークの間でデバイスが検出され、ユーザー エクスペリエンスの向上に影響を与Office 365表示されます。 Microsoft データセンター宛ての特定のネットワーク トラフィックMicrosoft 365バイパスする必要があります。 この推奨事項については、「ネットワーク接続[の原則Microsoft 365」で説明します](microsoft-365-network-connectivity-principles.md)。 

Exchange、SharePoint、Teams の重要な Office 365 ネットワーク エンドポイントがネットワーク仲介デバイスによって傍受および復号化された場合の SSL ブレークとインスペクションが示されているネットワーク仲介の分析情報の 1 つです。

### <a name="what-does-this-mean"></a>シナリオ

プロキシ サーバー、VPN、データ損失防止デバイスなどのネットワーク仲介デバイスは、トラフィックが中間的な Microsoft 365 クライアントのパフォーマンスと安定性に影響を与える可能性があります。

### <a name="what-should-i-do"></a>どうすればよいですか?

ネットワーク トラフィックの処理をバイパスするために検出されたネットワーク仲介Microsoft 365構成します。

## <a name="better-performance-detected-for-customers-near-you"></a>近くの顧客に対して検出されるパフォーマンスの向上

この分析情報は、ネットワーク インサイト サービスが、このオフィスの場所にある組織内のユーザーよりも、メトロエリアのかなりの数の顧客のパフォーマンスが優れたと検出した場合に表示されます。

この分析情報は、一部の概要ビューで "Peers" と省略されます。

> [!div class="mx-imgBorder"]
> ![相対ネットワークパフォーマンス](../media/m365-mac-perf/m365-mac-perf-insights-detail-cust-near-you.png)

### <a name="what-does-this-mean"></a>シナリオ

この分析情報は、このオフィスの場所と同Microsoft 365顧客の集計パフォーマンスを調べる。 この分析情報は、ユーザーの平均待機時間が隣接テナントの平均待機時間より 10% 大きい場合に表示されます。

### <a name="what-should-i-do"></a>どうすればよいですか?

この状態には、企業ネットワークまたは ISP の待機時間、ボトルネック、アーキテクチャ設計の問題など、多くの理由が考え得る。 Office ネットワークと現在のネットワーク間のルート内の各ホップ間の待機時間をMicrosoft 365します。 詳細については、「ネットワーク接続[Microsoft 365」を参照してください](microsoft-365-network-connectivity-principles.md)。

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>サービス フロント ドアの最適Exchange Online使用

この分析情報は、ネットワーク インサイト サービスが、特定の場所のユーザーが最適なサービス フロント ドアに接続Exchange Online場合に表示されます。

この分析情報は、一部の概要ビューでは "ルーティング" と省略されます。

> [!div class="mx-imgBorder"]
> ![最適ではない EXO フロント ドア](../media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-exo.png)

### <a name="what-does-this-mean"></a>シナリオ

優れたパフォーマンスExchange Onlineオフィスの場所から使用に適したサービス フロント ドアの一覧を示します。 現在のテストで、このリストに含Exchange Onlineサービス フロント ドアの使用が示されている場合は、この推奨事項を呼び出します。

### <a name="what-should-i-do"></a>どうすればよいですか?

サービス フロント ドアに最適でない Exchange Onlineを使用すると、企業のネットワーク出力の前にネットワーク バックホールが発生する可能性があります。その場合は、ローカルおよび直接のネットワーク出力をお勧めします。 また、リモート DNS 再帰的リゾルバー サーバーを使用した場合、DNS 再帰的リゾルバー サーバーをネットワーク出力に合わせて配置することをお勧めします。

## <a name="use-of-a-non-optimal-sharepoint-online-service-front-door"></a>オンライン サービス フロント ドアSharePoint最適でないサービスの使用

この分析情報は、ネットワーク インサイト サービスが、特定の場所のユーザーが Online サービスのフロント ドアに最も近いユーザーに接続SharePoint場合に表示されます。

この分析情報は、一部の概要ビューで "Afd" と省略されます。

> [!div class="mx-imgBorder"]
> ![最適でない SPO フロント ドア](../media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-spo.png)

### <a name="what-does-this-mean"></a>シナリオ

テスト クライアントがSharePointしているオンライン サービスのフロント ドアを特定します。 次に、オフィスの場所の都市について、その都市のSharePointオンライン サービスのフロント ドアと比較します。 一致しない場合は、この推奨事項を作成します。

### <a name="what-should-i-do"></a>どうすればよいですか?

最適ではないネットワーク SharePoint サービス フロント ドアの使用は、企業のネットワーク出力の前にネットワーク バックホールが発生する可能性があります。その場合は、ローカルおよび直接のネットワーク出力をお勧めします。 また、リモート DNS 再帰的リゾルバー サーバーを使用した場合、DNS 再帰的リゾルバー サーバーをネットワーク出力に合わせて配置することをお勧めします。

## <a name="low-download-speed-from-sharepoint-front-door"></a>フロント ドアからのダウンロードSharePoint速度が低い

この分析情報は、ネットワーク インサイト サービスが、特定のオフィスの場所とオンライン間の帯域幅が 1 MBps 未満SharePoint検出した場合に表示されます。

この分析情報は、一部の概要ビューで "スループット" と省略されます。

### <a name="what-does-this-mean"></a>シナリオ

ユーザーがオンラインおよび SharePoint および OneDrive for Business から取得できるダウンロード速度は、1 秒あたりのメガバイト (MBps) 単位で測定されます。 この値が 1 MBps 未満の場合は、この分析情報を提供します。

### <a name="what-should-i-do"></a>どうすればよいですか?

ダウンロード速度を向上させるために、帯域幅を増やす必要がある場合があります。 または、オフィスの場所でユーザー コンピューターとオンライン サービスのフロント ドアSharePointネットワークの混雑が発生する可能性があります。 これは、混雑損失と呼ばれる場合があります。十分な帯域幅が利用可能な場合でも、ユーザーが利用できるダウンロード速度が制限されます。

## <a name="china-user-optimal-network-egress"></a>中国ユーザーの最適なネットワーク出力

この分析情報は、中国のユーザーが他の地理的な場所Microsoft 365に接続している場合に表示されます。 

### <a name="what-does-this-mean"></a>シナリオ

組織にプライベート WAN 接続がある場合は、次の場所でインターネットへのネットワーク出力を持つ中国のオフィスの場所からネットワーク WAN 回線を構成することをお勧めします。

- 香港特別行政区
- 日本
- 台湾
- 韓国
- シンガポール
- マレーシア

これらの場所よりもユーザーから遠く離れたインターネット出力はパフォーマンスを低下させるので、中国の出力は国境を越えた混雑のために高い遅延と接続の問題を引き起こす可能性があります。

### <a name="what-should-i-do"></a>どうすればよいですか?

この分析情報に関連するパフォーマンスの問題を軽減する方法の詳細については、「中国のユーザー Microsoft 365のパフォーマンスの最適化」を[参照してください](microsoft-365-networking-china.md)。

## <a name="exchange-sampled-connections-impacted-by-connectivity-issues"></a>Exchangeの問題の影響を受け、サンプリングされた接続を確認する

この分析情報は、サンプリングされた接続の 50% 以上が影響を受け取る場合に表示されます。 影響は、サンプルごとに 60% 未満Exchange評価によって定義されます。

### <a name="what-does-this-mean"></a>シナリオ

これは、ユーザーの大半が、ユーザーに接続するユーザーエクスペリエンスの問題が発生している可能性が高Outlook示Exchange Online。 サンプルの割合は、60 ポイントを下回るユーザーの割合を表している可能性があります。  

### <a name="what-should-i-do"></a>どうすればよいですか?

オフィスの場所ネットワーク接続の可視性を有効にする (まだ有効にしていない場合)。 Exchange に影響を与えるネットワーク接続の不十分な影響を受け、ユーザーを Microsoft のネットワークに接続する各オフィスでネットワーク境界を改善する方法を見つける必要があります。

## <a name="sharepoint-sampled-connections-impacted-by-connectivity-issues"></a>SharePointの問題の影響を受け、サンプルされた接続を確認する

この分析情報は、サンプリングされた接続の 50% 以上が影響を受け取る場合に表示されます。 影響は、各サンプルSharePoint 40% 未満の評価によって定義されます。

### <a name="what-does-this-mean"></a>シナリオ

これは、ユーザーの大半が、ユーザーエクスペリエンスの問題が発生している可能性が高SharePoint示OneDrive。 サンプルの割合は、40 ポイントを下回るユーザーの割合を表している可能性があります。  

### <a name="what-should-i-do"></a>どうすればよいですか?

オフィスの場所ネットワーク接続の可視性を有効にする (まだ有効にしていない場合)。 SharePoint に影響を与えるネットワーク接続の不十分な影響を受け、ユーザーを Microsoft のネットワークに接続する各オフィスでネットワーク境界を改善する方法を見つける必要があります。

## <a name="related-topics"></a>関連項目

[管理センターでのネットワークMicrosoft 365 (プレビュー)](office-365-network-mac-perf-overview.md)

[Microsoft 365評価 (プレビュー)](office-365-network-mac-perf-score.md)

[Microsoft 365接続テスト ツール (プレビュー)](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365ネットワーク接続位置情報サービス (プレビュー)](office-365-network-mac-location-services.md)
