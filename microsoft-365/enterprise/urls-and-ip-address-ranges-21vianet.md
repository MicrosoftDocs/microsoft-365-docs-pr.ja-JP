---
title: 21Vianet が運営する Office 365の URL と IP アドレス範囲
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 01/04/2021
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- GMA150
- GPA150
- GEA150
ms.assetid: 5c47c07d-f9b6-4b78-a329-bfdc1b6da7a0
ms.custom: seo-marvel-apr2020
f1.keywords:
- NOCSH
description: この記事では、中国で 21Vianet が運用している場合の Office 365 の URL と IP アドレスの範囲を示します。
hideEdit: true
ms.openlocfilehash: 8a17cb9da5cf552615abf1ac20a67463e8430eb7
ms.sourcegitcommit: a76de3d1604d755b29053e7bf557c0008be6ad23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "49787811"
---
# <a name="urls-and-ip-address-ranges-for-office-365-operated-by-21vianet"></a><span data-ttu-id="5af6e-103">21Vianet が運営する Office 365の URL と IP アドレス範囲</span><span class="sxs-lookup"><span data-stu-id="5af6e-103">URLs and IP address ranges for Office 365 operated by 21Vianet</span></span>

 <span data-ttu-id="5af6e-104">*適用先: 21Vianet が運営する Office 365 の中小企業管理者、21Vianet が運営する Office 365 の管理者*</span><span class="sxs-lookup"><span data-stu-id="5af6e-104">*Applies To: Office 365 operated by 21Vianet - Small Business Admin, Office 365 operated by 21Vianet - Admin*</span></span>

<span data-ttu-id="5af6e-105">**概要**: 次のエンドポイント (FQDN、ポート、URL、IPv4、および IPv6 プレフィックス) は 21Vianet が運営する Office 365 に適用され、これらのプランだけを活用して生産性サービスを組織へ提供できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="5af6e-105">**Summary**: The following endpoints (FQDNs, ports, URLs, IPv4, and IPv6 prefixes) apply to Office 365 operated by 21 Vianet and are designed to deliver productivity services to organizations using only these plans.</span></span>
  
 <span data-ttu-id="5af6e-106">**Office 365 エンドポイント:** [(GCC を含む) 世界](urls-and-ip-address-ranges.md)  | *21Vianet が運営する Office 365* | [Office 365 ドイツ](microsoft-365-germany-endpoints.md) |  [Office 365 米国政府機関向け DoD](microsoft-365-u-s-government-dod-endpoints.md) | [Office 365 米国政府 GCC 高](microsoft-365-u-s-government-gcc-high-endpoints.md) |</span><span class="sxs-lookup"><span data-stu-id="5af6e-106">**Office 365 endpoints:** [Worldwide (including GCC)](urls-and-ip-address-ranges.md)  | *Office 365 operated by 21 Vianet* | [Office 365 Germany](microsoft-365-germany-endpoints.md) | [Office 365 U.S. Government DoD](microsoft-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md) |</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="5af6e-107">**最終更新日:** 2021 年 1 月 4 日 - ![RSS](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [ログ サブスクリプションの変更](https://endpoints.office.com/version/China?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="5af6e-107">**Last updated:** 01/04/2021 - ![RSS](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change Log subscription](https://endpoints.office.com/version/China?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>|<span data-ttu-id="5af6e-108">**ダウンロード:** 1 つの [JSON 形式](https://endpoints.office.com/endpoints/China?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)リスト内のすべての必須およびオプションの宛先。</span><span class="sxs-lookup"><span data-stu-id="5af6e-108">**Download:** all required and optional destinations in one [JSON formatted](https://endpoints.office.com/endpoints/China?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) list.</span></span>  <br/> |

<span data-ttu-id="5af6e-p101">はじめに 「[Office 365 エンドポイントを管理する](managing-office-365-endpoints.md)」を読み、以下のデータを使用してネットワーク接続を管理するための推奨事項を確認します。エンドポイント データは毎月月初めに更新され、新しい IP アドレスと URL は、それらがアクティブになる 30 日前に公開されます。これにより、お客様がまだ自動更新の設定を行っていない場合でも、新しい接続が必要になる前にプロセスを完了していただけます。サポートのエスカレーション、セキュリティ インシデント、またはその他の即時の運用要件に対応するために、月の途中にエンドポイントが更新される場合があります。このページの下に表示されるデータは、すべて REST ベースの Web サービスから生成されたものです。スクリプトやネットワーク デバイスを使用してこのデータにアクセスする場合、[[Web サービス](microsoft-365-ip-web-service.md)] に直接移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5af6e-p101">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](microsoft-365-ip-web-service.md) directly.</span></span>

<span data-ttu-id="5af6e-p102">次のエンドポイント データは、ユーザーのコンピューターを Office 365 に接続するための要件の一覧です。Microsoft からお客様のネットワークへの接続 (“ハイブリッド ネットワーク接続” や ”受信ネットワーク接続” と呼ばれる場合があります) は含まれません。</span><span class="sxs-lookup"><span data-stu-id="5af6e-p102">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="5af6e-p103">エンドポイントは 4 つのサービス領域にグループ分けされます。最初の 3 つのサービス領域は個別に接続の選択ができます。4 番目のサービス領域は共通の依存関係 ("Microsoft 365 Common および Office Online" と呼ばれる) で、常時ネットワーク接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5af6e-p103">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.</span></span>

<span data-ttu-id="5af6e-120">次のデータ列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5af6e-120">Data columns shown are:</span></span>

- <span data-ttu-id="5af6e-p104">**ID**: エンドポイントのセットとして知られる、行の ID 番号です。この ID は、エンドポイントの Web サービスによって返されるものと同じです。</span><span class="sxs-lookup"><span data-stu-id="5af6e-p104">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="5af6e-p105">**カテゴリ**: エンドポイントのセットが「最適化」、「許可」または「既定」のどれに分類されているかを示します。これらのカテゴリとその管理ガイダンスについては、[https://aka.ms/pnc](https://aka.ms/pnc) を参照してください。この列には、ネットワーク接続に必要なエンドポイントのセットが表示されます。ネットワーク接続が必要ないエンドポイントのセットの場合、このコラムには、エンドポイントのセットがブロックされた場合に使えなくなる機能に関する注意書きが書かれます。サービス領域全体を除外する場合は、ネットワーク接続が必要と記載されているエンドポイントのセットの接続は不要です。</span><span class="sxs-lookup"><span data-stu-id="5af6e-p105">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="5af6e-p106">**ER**: 「**はい**」とある場合、エンドポイントのセットは Office 365 のルート プレフィックスを使用して Azure ExpressRoute でサポートされています。表示されているルートのプレフィックスを含む BGP コミュニティは、記載されているサービス領域と整合します。ER に「**いいえ**」とある場合、ExpressRoute はそのエンドポイントのセットでサポートされていないことを意味します。ただし、ER に「**いいえ**」とある場合でも、アドバタイズされたルートが 1 つも無いとは判断しないようにします。</span><span class="sxs-lookup"><span data-stu-id="5af6e-p106">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="5af6e-p107">**アドレス**: FQDN またはワイルドカードを含むドメイン名と、エンドポイントのセットの IP アドレス範囲を一覧表示します。IP アドレスの範囲は CIDR 形式となり、指定されたネットワークの個別の IP アドレスが多数含まれる場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5af6e-p107">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="5af6e-p108">**ポート**: アドレスと組み合わさることによりネットワーク エンドポイントを形成する TCP または UDP ポートの一覧を表示します。異なるポートが記載されている場合、IP アドレス範囲が重複している場合があります。</span><span class="sxs-lookup"><span data-stu-id="5af6e-p108">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 operated by 21Vianet endpoints](../includes/office-365-operated-by-21vianet-endpoints.md)]


