---
title: ネットワークをセットアップMicrosoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: ''
description: ネットワーク接続の概要やエンドポイントの一覧など、Microsoft 365の設定に役立つ情報を含む記事へのリンクを検索します。
ms.openlocfilehash: f0e0499c70745d31399240372c190758285408aa
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46691678"
---
# <a name="set-up-your-network-for-microsoft-365"></a>ネットワークをセットアップMicrosoft 365

*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*

オンボーディングの重要なMicrosoft 365は、ネットワークとインターネット接続が最適化されたアクセス用にセットアップされている点です。 グローバルに分散された Software-as-a-Service (SaaS) クラウドにアクセスするためのオンプレミス ネットワークの構成は、オンプレミスデータセンターへのトラフィックと中央インターネット接続用に最適化された従来のネットワークとは異なります。 

以下の記事を活用して主な違いを理解し、エッジ デバイス、クライアント コンピューター、オンプレミス ネットワークを変更して、オンプレミス ユーザーの最高のパフォーマンスを引き出します。

## <a name="how-microsoft-365-networking-works"></a>ネットワークMicrosoft 365のしくみ

次の記事を参照して、接続の概要を確認Microsoft 365。

- [Microsoft 365 ネットワーク接続の概要](microsoft-365-networking-overview.md)
- [Microsoft 365接続の原則](microsoft-365-network-connectivity-principles.md)
- [Microsoft 365 ネットワーク接続の評価](assessing-network-connectivity.md)

パフォーマンスの向上に関するアドバイスについては、「ネットワークの計画とパフォーマンスの調整」[を参照Microsoft 365。](network-planning-and-performance.md)

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a>ネットワークMicrosoft 365ベンダーとしてのネットワークのサポート

ネットワーク機器業者のお客様は、[Office 365 ネットワーク パートナー プログラム](microsoft-365-networking-partner-program.md)にぜひご参加ください。ご参加いただくと、Office 365 のネットワーク接続の基本原則をお客様の会社の製品とソリューションに組み込んでいただけます。 

## <a name="office-365-endpoints"></a>Office 365 エンドポイント

エンドポイントとは、インターネット上の Office 365 トラフィックの宛先 IP アドレス、DNS ドメイン名、URL のセットのことです。 

Office 365 のクラウドベース サービスのパフォーマンスを最適化するには、クライアント ブラウザーと境界ネットワーク内のデバイスを使用し、一部のエンドポイントに対して特別な処理を行う必要があります。これらのデバイスには、ファイアウォール、SSL 中断/検査とパケット検査デバイス、およびデータ損失防止システムが含まれます。

詳細については、「[Office 365 エンドポイントの管理](managing-office-365-endpoints.md)」を参照してください。

現在、5 つの異なる Office 365 クラウドがあります。この表からそれぞれのクラウドのエンドポイント一覧へ移動できます。

| エンドポイント | 説明 |
|:-------|:-----|
| [世界中のエンドポイント](urls-and-ip-address-ranges.md) | 米国政府機関向けコミュニティ クラウド (GCC) を含む、世界中の Office 365 サブスクリプションのエンドポイント。 |
| [米国政府の DoD エンドポイント](microsoft-365-u-s-government-dod-endpoints.md) | 米国国防総省 (DoD) のサブスクリプションのエンドポイント。 |
| [米国政府の GCC High エンドポイント](microsoft-365-u-s-government-gcc-high-endpoints.md) | 米国政府機関向けコミュニティ クラウド High (GCC High) サブスクリプションのエンドポイント。 |
| [21Vianet エンドポイントが運用している Office 365](urls-and-ip-address-ranges-21vianet.md) | 中国での Office 365 のニーズを満たすために設計された、21Vianet が運用する Office 365 のエンドポイント。 |
| [Office 365 Germany エンドポイント](microsoft-365-germany-endpoints.md) | ヨーロッパにある、規制が最も厳しいドイツ、欧州連合 (EU)、および欧州自由貿易連合 (EFTA) のお客様向けの特別なクラウドのエンドポイント。 |
|||

Office 365 クラウドのエンドポイントの最新の一覧を自動的に取得するには、「[Office 365 IP アドレスと URL の Web サービス](microsoft-365-ip-web-service.md)」を参照してください。

その他のエンドポイントについては次の記事を参照してください。

- [Web サービスに含まれていないその他のエンドポイント](additional-office365-ip-addresses-and-urls.md)
- [Office 2016 for Mac でのネットワーク要求](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a>ネットワークに関するMicrosoft 365トピック

ネットワークに関する特別なトピックについては、以下のMicrosoft 365参照してください。

- [コンテンツ配信ネットワーク](content-delivery-networks.md)
- [Office 365 サービスでの IPv6 サポート](ipv6-support.md)
- [Office 365 の NAT サポート](nat-support-with-microsoft-365.md)

## <a name="expressroute-for-microsoft-365"></a>Microsoft 365 向け ExpressRoute

Office 365 トラフィック向け ExpressRoute の使用についての詳細は、次の記事を参照してください。

- [Office 365 向け Azure ExpressRoute](azure-expressroute.md)
- [Office 365 向け ExpressRoute の実装](implementing-expressroute.md)
- [Office 365 向け ExpressRoute でのネットワーク計画](network-planning-with-expressroute.md)
- [Office 365 向け ExpressRoute でのルーティング](routing-with-expressroute.md)
