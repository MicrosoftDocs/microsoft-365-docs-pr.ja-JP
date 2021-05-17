---
title: Office 365 の NAT サポート
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: この記事では、NAT を使用して組織内の IP アドレスごとに使用できるクライアント数を概算する方法の詳細を示します。
ms.openlocfilehash: f48874853c3acb80927933761862b14379b6d4bd
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46691616"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="bf8a5-103">Office 365 の NAT サポート</span><span class="sxs-lookup"><span data-stu-id="bf8a5-103">NAT support with Office 365</span></span>

<span data-ttu-id="bf8a5-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="bf8a5-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="bf8a5-105">ガイダンスでは以前、Office 365 に接続するために IP アドレスごとに使用する必要がある Exchange クライアントの最大数は、ネットワーク ポート 1 つあたり約 2,000 と推奨していました。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="bf8a5-106">NAT を使用する理由は何ですか。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-106">Why use NAT?</span></span>

<span data-ttu-id="bf8a5-107">NAT の使用により、企業ネットワークの何千人ものユーザーが、少数のパブリック ルーティング可能な IP アドレスを「共有」することができます。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="bf8a5-p101">ほとんどの企業ネットワークは、プライベート (RFC1918) の IP アドレス空間を使用しています。プライベートアドレス空間は Internet Assigned Numbers Authority (IANA) によって割り当てられたもので、グローバル インターネットに直接つながっていないネットワークのみを想定しています。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-p101">Most corporate networks use private (RFC1918) IP address space. Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="bf8a5-p102">プライベート IP アドレス空間上のデバイスにインターネット アクセスを提供するには、ネットワーク アドレス変換 (NAT) またはポート アドレス変換 (PAT) サービスを提供するファイアウォールおよびプロキシのようなゲートウェイ技術を使用します。これらのゲートウェイは、内部デバイスからインターネットへのトラフィック (Office 365 など) を、1 つまたは複数のパブリック ルーティング可能な IP アドレスから来ているように見せます。内部デバイス変換から各アウトバウンド接続はパブリック IP アドレスの異なる送信元 TCP ポートに変換されます。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-p102">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services. These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses. Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="bf8a5-113">Office 365 に対して多数の接続を同時に開く必要があるのはなぜですか。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="bf8a5-114">Outlook 8 つ以上の接続を開く場合があります (アドイン、共有予定表、メールボックスなどがある場合)。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-114">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.).</span></span> <span data-ttu-id="bf8a5-115">Windows ベースの NAT デバイスで使用できるポートは最大 64,000 個なので、ポートが使い果たされる前に、IP アドレスの背後に最大 8,000 人のユーザーが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-115">Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted.</span></span> <span data-ttu-id="bf8a5-116">お客様が NAT に対して非 Windows OS ベースのデバイスを使用している場合、使用可能なポートの合計は、使用されている NAT デバイスまたはソフトウェアによって異なります。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-116">Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used.</span></span> <span data-ttu-id="bf8a5-117">このシナリオでは、ポートの最大数は 64,000 未満になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-117">In this scenario, the maximum number of ports could be less than 64,000.</span></span> <span data-ttu-id="bf8a5-118">ポートの可用性は、Windows が独自に使用するために 4,000 ポートを制限するなどの他の要因によっても影響を受け、使用可能なポートの総数は 60,000 に減少します。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-118">Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.</span></span> <span data-ttu-id="bf8a5-119">他のアプリケーション (Internet Explorerなど) が同時に接続される場合があります。追加のポートが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-119">There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="bf8a5-120">Office 365 で単一のパブリック IP アドレスにサポートされるデバイスの最大数の計算</span><span class="sxs-lookup"><span data-stu-id="bf8a5-120">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="bf8a5-p104">単一のパブリック IP アドレスにあるデバイスの最大数を決定するには、ネットワーク トラフィックを監視し、クライアントごとのピーク ポート消費量を決定する必要があります。また、ポートの使用数にピーク係数を使用する必要があります (最小は 4)。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-p104">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client. Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="bf8a5-123">**IP アドレスごとにサポートされるデバイスの数を計算するには、次の式を使用します。**</span><span class="sxs-lookup"><span data-stu-id="bf8a5-123">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="bf8a5-124">単一のパブリック IP アドレスにサポートされるデバイスの最大数 = (64,000 - 制限されたポート) / (ピーク ポート消費量 + ピーク係数)</span><span class="sxs-lookup"><span data-stu-id="bf8a5-124">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="bf8a5-125">**たとえば、次のような条件だとします。**</span><span class="sxs-lookup"><span data-stu-id="bf8a5-125">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="bf8a5-126">**制限されたポート:** オペレーティング システムで 4,000</span><span class="sxs-lookup"><span data-stu-id="bf8a5-126">**Restricted ports:** 4,000 for the operating system</span></span>

- <span data-ttu-id="bf8a5-127">**ピーク ポート消費量:** デバイスあたり 6</span><span class="sxs-lookup"><span data-stu-id="bf8a5-127">**Peak port consumption:** 6 per device</span></span>

- <span data-ttu-id="bf8a5-128">**ピーク係数:** 4</span><span class="sxs-lookup"><span data-stu-id="bf8a5-128">**Peak factor:** 4</span></span>

<span data-ttu-id="bf8a5-129">このような条件の場合、単一のパブリック IP アドレスにサポートされるデバイスの最大数 = (64,000 - 4,000) / (6 + 4) = 6,000 </span><span class="sxs-lookup"><span data-stu-id="bf8a5-129">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="bf8a5-p105">Office 365 ホスティング パック (Microsoft Office Outlook 2007 用の 2011 年 9 月の更新プログラム、Microsoft Outlook 2010 用の 2011 年 11 月の更新プログラム、またはそれ以降の更新プログラムに含まれています) のリリースでの、Outlook (Office Outlook 2007 Service Pack 2 と Outlook 2010 の両方) から Exchange への最小接続数は 2 つです。ピーク時のネットワークに必要な最小または最大のポート数を決定するには、異なるオペレーティング システムやユーザーの行動などを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-p105">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2. You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="bf8a5-132">単一のパブリック IP アドレスでより多くのデバイスをサポートする場合、サポートできるデバイスの最大数を説明した手順に従って査定します。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-132">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="bf8a5-p106">クライアントごとのピーク ポート消費量を決定するために、ネットワーク トラフィックを監視します。このデータは次の要領で収集します。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-p106">Monitor network traffic to determine peak port consumption per client. You should collect this data:</span></span>
  
- <span data-ttu-id="bf8a5-135">複数の場所から収集する</span><span class="sxs-lookup"><span data-stu-id="bf8a5-135">From multiple locations</span></span>
    
- <span data-ttu-id="bf8a5-136">複数のデバイスから収集する</span><span class="sxs-lookup"><span data-stu-id="bf8a5-136">From multiple devices</span></span>
    
- <span data-ttu-id="bf8a5-137">複数回にわたって収集する</span><span class="sxs-lookup"><span data-stu-id="bf8a5-137">At multiple times</span></span>
    
<span data-ttu-id="bf8a5-138">上記の計算式を使い、クライアントの環境でサポート可能な IP アドレスあたりの最大ユーザー数を計算します。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-138">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="bf8a5-p107">追加のパブリック IP アドレス間でクライアント負荷を分散するにはさまざまな方法があります。利用可能な方法は企業のゲートウェイ ソリューションの機能によって決まります。最も簡単な方法は、ユーザー アドレス空間をセグメントに分けて、静的に各ゲートウェイに IP アドレスの数を「割り当て」る方法です。多くのゲートウェイ デバイスでサポートされている別の方法としては、IP アドレスのプールの機能を使用できます。アドレス プールの利点は、非常に動的で、ユーザー ベースの増加に合わせて調整する必要があまりないということです。</span><span class="sxs-lookup"><span data-stu-id="bf8a5-p107">There are various methods for distributing client load across additional public IP addresses. Strategies available depend on the capabilities of the corporate gateway solution. The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway. Another alternative that many gateway devices offer is the ability to use a pool of IP addresses. The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bf8a5-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf8a5-144">See also</span></span>

[<span data-ttu-id="bf8a5-145">Office 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="bf8a5-145">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="bf8a5-146">Office 365 エンドポイントの FAQ</span><span class="sxs-lookup"><span data-stu-id="bf8a5-146">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
