---
title: SharePoint Online でのオブジェクトキャッシュの使用
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: この記事では、SharePoint Server 2013 オンプレミスと SharePoint Online でのオブジェクトキャッシュの使用との違いについて説明します。
ms.openlocfilehash: 279d156a941aad6fbe7adbcf052c57f5b58c652f
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46696239"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a><span data-ttu-id="e798e-103">SharePoint Online でのオブジェクトキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="e798e-103">Using the object cache with SharePoint Online</span></span>

<span data-ttu-id="e798e-104">この記事では、SharePoint Server 2013 オンプレミスと SharePoint Online でのオブジェクトキャッシュの使用との違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e798e-104">This article explains the difference between using the object cache in SharePoint Server 2013 on-premises and SharePoint Online.</span></span>
  
<span data-ttu-id="e798e-105">SharePoint Online 展開のオブジェクトキャッシュに依存することによって、重大な悪影響があります。</span><span class="sxs-lookup"><span data-stu-id="e798e-105">There is significant negative impact of relying on the object cache in SharePoint Online deployment.</span></span> <span data-ttu-id="e798e-106">SharePoint Online のオブジェクトキャッシュに依存している場合は、ページの信頼性が低下します。</span><span class="sxs-lookup"><span data-stu-id="e798e-106">Any dependency on object cache in SharePoint Online will reduce the reliability of your page.</span></span> 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a><span data-ttu-id="e798e-107">SharePoint Online と SharePoint Server 2013 のオブジェクトキャッシュのしくみ</span><span class="sxs-lookup"><span data-stu-id="e798e-107">How the SharePoint Online and SharePoint Server 2013 object cache works</span></span>

<span data-ttu-id="e798e-108">SharePoint Server 2013 がオンプレミスでホストされている場合、お客様は、オブジェクトキャッシュをホストする独自のフロントエンド web サーバーを備えています。</span><span class="sxs-lookup"><span data-stu-id="e798e-108">When SharePoint Server 2013 is hosted on-premises, the customer has private front-end web servers that host the object cache.</span></span> <span data-ttu-id="e798e-109">これは、キャッシュが1つの顧客専用となり、使用可能なメモリ容量によって制限されるだけで、オブジェクトキャッシュに割り当てることができることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e798e-109">This means the cache is dedicated to one customer and is only limited by how much memory is available and allocated to the object cache.</span></span> <span data-ttu-id="e798e-110">オンプレミスのシナリオでは1人の顧客のみが提供されるので、通常、フロントエンド web サーバーでは、同じサイトに対してユーザーが繰り返し要求を行うことになります。</span><span class="sxs-lookup"><span data-stu-id="e798e-110">Because only one customer is served in the on-premises scenario the front-end web servers typically have users making requests to the same sites over and over.</span></span> <span data-ttu-id="e798e-111">これは、キャッシュが短時間でいっぱいになり、ユーザーが定期的に要求しているリストクエリの結果と SharePoint オブジェクトを完全に保持することを意味します。</span><span class="sxs-lookup"><span data-stu-id="e798e-111">This means that the cache gets full quickly and remains full of the list query results and SharePoint objects that your users are requesting on a regular basis.</span></span>
  
![オンプレミスのフロントエンド Web サーバーへのトラフィックと負荷を示しています](../media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
<span data-ttu-id="e798e-113">その結果、ユーザーがページを訪問すると、ページの読み込み時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="e798e-113">As a result, the second time a user visits a page, the page load time improves.</span></span> <span data-ttu-id="e798e-114">同じページの少なくとも4つの負荷の後、ページはすべてのフロントエンド web サーバーにキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="e798e-114">After a minimum of four loads of the same page, the page is cached on all of the front-end web servers.</span></span>
  
<span data-ttu-id="e798e-115">一方、SharePoint Online では、多くのサーバーがありますが、さらに多くのサイトもあります。</span><span class="sxs-lookup"><span data-stu-id="e798e-115">In contrast, in SharePoint Online there are many more servers but also many more sites.</span></span> <span data-ttu-id="e798e-116">各ユーザーは、キャッシュが設定されていない別のフロントエンド web サーバーに接続することができます。</span><span class="sxs-lookup"><span data-stu-id="e798e-116">Each user may connect to a different front-end web server that doesn't have the cache populated.</span></span> <span data-ttu-id="e798e-117">また、キャッシュがサーバーに対して設定されている場合もありますが、そのフロントエンド web サーバーの次のユーザーは別のサイトからページを要求します。</span><span class="sxs-lookup"><span data-stu-id="e798e-117">Or, perhaps the cache does get populated for a server, but the next user to that front-end web server requests a page from a different site.</span></span> <span data-ttu-id="e798e-118">または、次のユーザーが前の訪問と同じページを要求した場合でも、そのページがキャッシュ内にない別のフロントエンド web サーバーに負荷分散されます。</span><span class="sxs-lookup"><span data-stu-id="e798e-118">Or, even if the next user requests the same page as on their previous visit, they are load-balanced to a different front-end web server that doesn't have that page in its cache.</span></span> <span data-ttu-id="e798e-119">この最後のケースでは、キャッシュを使用してユーザーをまったくサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e798e-119">In this last case, caching doesn't help the users at all.</span></span>
  
<span data-ttu-id="e798e-120">次の図では、各ドットは、ユーザーが要求しているページと、キャッシュされた場所を表しています。</span><span class="sxs-lookup"><span data-stu-id="e798e-120">In the following figure, each dot represents a page that a user is requesting and where it cached.</span></span> <span data-ttu-id="e798e-121">さまざまな色は、SaaS インフラストラクチャを共有するために使用するさまざまな顧客を表します。</span><span class="sxs-lookup"><span data-stu-id="e798e-121">Different colors represent different customers making shared use of the SaaS infrastructure.</span></span>
  
![SharePoint Online におけるオブジェクト キャッシュの結果を示します](../media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
<span data-ttu-id="e798e-123">図からわかるように、特定のユーザーがキャッシュされたページを使用してサーバーにヒットする可能性はスリムです。</span><span class="sxs-lookup"><span data-stu-id="e798e-123">As you can see from the diagram, the chances of any given user hitting a server with the cached version of their page are slim.</span></span> <span data-ttu-id="e798e-124">また、スループットが大きく、サーバーが多数のサイト間で共有されているため、キャッシュが使用可能な領域が1つしかないため、キャッシュが最後まで長くなっているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="e798e-124">Also, due to the large throughput and fact that the servers are shared between many sites, the cache doesn't last long since there is only so much space for caching available.</span></span>
  
<span data-ttu-id="e798e-125">これらのすべての理由から、ユーザーにキャッシュされたオブジェクトを取得することは、SharePoint Online でユーザーの品質を向上させるための効果的な方法ではありません。</span><span class="sxs-lookup"><span data-stu-id="e798e-125">For all of these reasons, relying on users getting cached objects is not an effective way to ensure a quality user experience and page load times in SharePoint Online.</span></span>
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a><span data-ttu-id="e798e-126">SharePoint Online のパフォーマンスを向上させるためにオブジェクトキャッシュを使用できない場合は、どうすればよいでしょうか。</span><span class="sxs-lookup"><span data-stu-id="e798e-126">If we can't rely on the object cache to improve performance in SharePoint Online, what do we use instead?</span></span>

<span data-ttu-id="e798e-127">SharePoint Online ではキャッシュを使用しないようにする必要があるため、オブジェクトキャッシュを使用する SharePoint カスタマイズの代替デザイン方法を評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e798e-127">Since you shouldn't rely on caching in SharePoint Online, you should evaluate alternative design approaches for SharePoint customizations that use the object cache.</span></span> <span data-ttu-id="e798e-128">これは、ユーザーにとって適切な結果を得るために、オブジェクトキャッシュに依存しないパフォーマンスの問題を解決する手法を使用することを意味します。</span><span class="sxs-lookup"><span data-stu-id="e798e-128">This means using approaches for performance issues which do not rely on the object caching in order to produce good results for users.</span></span> <span data-ttu-id="e798e-129">これについては、このシリーズの他の記事に記載されている内容を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e798e-129">This is described in some of the other articles in this series and include:</span></span>
  
- [<span data-ttu-id="e798e-130">SharePoint Online のナビゲーション オプション</span><span class="sxs-lookup"><span data-stu-id="e798e-130">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="e798e-131">SharePoint Online での縮小とバンドル</span><span class="sxs-lookup"><span data-stu-id="e798e-131">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="e798e-132">SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用</span><span class="sxs-lookup"><span data-stu-id="e798e-132">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-microsoft-365-cdn-with-spo.md)
    
- [<span data-ttu-id="e798e-133">SharePoint Online での画像の読み込み遅延と JavaScript</span><span class="sxs-lookup"><span data-stu-id="e798e-133">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
