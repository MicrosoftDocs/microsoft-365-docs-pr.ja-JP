---
title: Microsoft 365 エンドポイント
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/07/2018
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
description: Microsoft 365 のトラフィックの宛先 IP アドレスおよび Url については、Microsoft 365 クラウドごとのインターネットエンドポイントに関する記事の一覧を使用します。
ms.openlocfilehash: b0d8468eaa1b56d1151e54d8e05e6ada51845118
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46691964"
---
# <a name="microsoft-365-endpoints"></a><span data-ttu-id="274f1-103">Microsoft 365 エンドポイント</span><span class="sxs-lookup"><span data-stu-id="274f1-103">Microsoft 365 endpoints</span></span>

<span data-ttu-id="274f1-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="274f1-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="274f1-105">エンドポイントとは、インターネット上の Microsoft 365 トラフィックの宛先 IP アドレス、DNS ドメイン名、Url のセットのことです。</span><span class="sxs-lookup"><span data-stu-id="274f1-105">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Microsoft 365 traffic on the Internet.</span></span> 

<span data-ttu-id="274f1-106">Microsoft 365 のクラウドベースのサービスのパフォーマンスを最適化するために、これらのエンドポイントにはクライアントブラウザーとエッジネットワーク内のデバイスによる特別な処理が必要です。</span><span class="sxs-lookup"><span data-stu-id="274f1-106">To optimize performance to Microsoft 365 cloud-based services, these endpoints need special handling by your client browsers and the devices in your edge network.</span></span> <span data-ttu-id="274f1-107">これらのデバイスには、ファイアウォール、SSL ブレークと検査、パケット検査デバイス、データ損失防止システムなどがあります。</span><span class="sxs-lookup"><span data-stu-id="274f1-107">These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="274f1-108">詳細については、「 [Microsoft 365 エンドポイントの管理](managing-office-365-endpoints.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="274f1-108">See [Managing Microsoft 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="274f1-109">現在、5つの異なる Microsoft 365 クラウドがあります。</span><span class="sxs-lookup"><span data-stu-id="274f1-109">There are currently five different Microsoft 365 clouds.</span></span> <span data-ttu-id="274f1-110">次の表は、それぞれのエンドポイントの一覧を示しています。</span><span class="sxs-lookup"><span data-stu-id="274f1-110">This table takes you to the list of endpoints for each one.</span></span>

| <span data-ttu-id="274f1-111">クラウド</span><span class="sxs-lookup"><span data-stu-id="274f1-111">Cloud</span></span> | <span data-ttu-id="274f1-112">説明</span><span class="sxs-lookup"><span data-stu-id="274f1-112">Description</span></span> |
|:-------|:-----|
| [<span data-ttu-id="274f1-113">世界中のエンドポイント</span><span class="sxs-lookup"><span data-stu-id="274f1-113">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="274f1-114">米国政府機関向けコミュニティクラウド (GCC) を含む、世界中の Microsoft 365 サブスクリプションのエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="274f1-114">The endpoints for worldwide Microsoft 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="274f1-115">米国政府の DoD エンドポイント</span><span class="sxs-lookup"><span data-stu-id="274f1-115">U.S. Government DoD endpoints</span></span>](microsoft-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="274f1-116">米国国防総省 (DoD) のサブスクリプションのエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="274f1-116">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="274f1-117">米国政府の GCC High エンドポイント</span><span class="sxs-lookup"><span data-stu-id="274f1-117">U.S. Government GCC High endpoints</span></span>](microsoft-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="274f1-118">米国政府機関向けコミュニティ クラウド High (GCC High) サブスクリプションのエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="274f1-118">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="274f1-119">21Vianet が運用している Microsoft 365 のエンドポイント</span><span class="sxs-lookup"><span data-stu-id="274f1-119">Microsoft 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="274f1-120">21Vianet が運用している Microsoft 365 のエンドポイント。中国での Microsoft 365 のニーズを満たすように設計されています。</span><span class="sxs-lookup"><span data-stu-id="274f1-120">The endpoints for Microsoft 365 operated by 21Vianet, which is designed to meet the needs for Microsoft 365 in China.</span></span> |
| [<span data-ttu-id="274f1-121">Microsoft 365 ドイツエンドポイント</span><span class="sxs-lookup"><span data-stu-id="274f1-121">Microsoft 365 Germany endpoints</span></span>](microsoft-365-germany-endpoints.md) | <span data-ttu-id="274f1-122">ヨーロッパにある、規制が最も厳しいドイツ、欧州連合 (EU)、および欧州自由貿易連合 (EFTA) のお客様向けの特別なクラウドのエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="274f1-122">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="274f1-123">Microsoft 365 cloud のエンドポイントの最新の一覧を自動的に取得するには、「 [Office 365 の IP アドレスと URL Web サービス](microsoft-365-ip-web-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="274f1-123">To automate getting the latest list of endpoints for your Microsoft 365 cloud, see the [Office 365 IP Address and URL Web service](microsoft-365-ip-web-service.md).</span></span>

<span data-ttu-id="274f1-124">その他のエンドポイントについては次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="274f1-124">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="274f1-125">Web サービスに含まれていないその他のエンドポイント</span><span class="sxs-lookup"><span data-stu-id="274f1-125">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="274f1-126">Office 2016 for Mac でのネットワーク要求</span><span class="sxs-lookup"><span data-stu-id="274f1-126">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)

<span data-ttu-id="274f1-127">ネットワーク機器ベンダーの場合は、 [Office 365 ネットワークパートナープログラム](microsoft-365-networking-partner-program.md)に参加してください。</span><span class="sxs-lookup"><span data-stu-id="274f1-127">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](microsoft-365-networking-partner-program.md).</span></span> <span data-ttu-id="274f1-128">Microsoft 365 ネットワーク接続の原則を製品とソリューションに構築するために、プログラムに登録します。</span><span class="sxs-lookup"><span data-stu-id="274f1-128">Enroll in the program to build Microsoft 365 network connectivity principles into your products and solutions.</span></span> 