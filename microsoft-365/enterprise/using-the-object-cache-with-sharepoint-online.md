---
title: Online でオブジェクト キャッシュをSharePointする
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
description: この記事では、オンプレミスのサーバー 2013 および SharePoint Online でオブジェクト キャッシュを使用するSharePoint説明します。
ms.openlocfilehash: 279d156a941aad6fbe7adbcf052c57f5b58c652f
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46696239"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a><span data-ttu-id="0b690-103">Online でオブジェクト キャッシュをSharePointする</span><span class="sxs-lookup"><span data-stu-id="0b690-103">Using the object cache with SharePoint Online</span></span>

<span data-ttu-id="0b690-104">この記事では、オンプレミスのサーバー 2013 および SharePoint Online でオブジェクト キャッシュを使用するSharePoint説明します。</span><span class="sxs-lookup"><span data-stu-id="0b690-104">This article explains the difference between using the object cache in SharePoint Server 2013 on-premises and SharePoint Online.</span></span>
  
<span data-ttu-id="0b690-105">オンライン展開のオブジェクト キャッシュに依存すると、重大な悪影響SharePointがあります。</span><span class="sxs-lookup"><span data-stu-id="0b690-105">There is significant negative impact of relying on the object cache in SharePoint Online deployment.</span></span> <span data-ttu-id="0b690-106">オンラインでのオブジェクト キャッシュへのSharePointは、ページの信頼性を低下します。</span><span class="sxs-lookup"><span data-stu-id="0b690-106">Any dependency on object cache in SharePoint Online will reduce the reliability of your page.</span></span> 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a><span data-ttu-id="0b690-107">SharePoint Server 2013 SharePoint キャッシュのしくみ</span><span class="sxs-lookup"><span data-stu-id="0b690-107">How the SharePoint Online and SharePoint Server 2013 object cache works</span></span>

<span data-ttu-id="0b690-108">サーバー 2013 SharePointオンプレミスでホストされている場合、顧客はオブジェクト キャッシュをホストするプライベート フロントエンド Web サーバーを持っています。</span><span class="sxs-lookup"><span data-stu-id="0b690-108">When SharePoint Server 2013 is hosted on-premises, the customer has private front-end web servers that host the object cache.</span></span> <span data-ttu-id="0b690-109">つまり、キャッシュは 1 人の顧客専用であり、使用可能なメモリ量とオブジェクト キャッシュへの割り当て量によってのみ制限されます。</span><span class="sxs-lookup"><span data-stu-id="0b690-109">This means the cache is dedicated to one customer and is only limited by how much memory is available and allocated to the object cache.</span></span> <span data-ttu-id="0b690-110">オンプレミスのシナリオでは、1 人の顧客だけがサービスを受け取るので、フロントエンド Web サーバーは通常、同じサイトに対して要求を行うユーザーを持っています。</span><span class="sxs-lookup"><span data-stu-id="0b690-110">Because only one customer is served in the on-premises scenario the front-end web servers typically have users making requests to the same sites over and over.</span></span> <span data-ttu-id="0b690-111">つまり、キャッシュはすばやく完全に取得され、リスト クエリの結果と、ユーザーが定期的に要求しているSharePointオブジェクトの完全な状態を維持します。</span><span class="sxs-lookup"><span data-stu-id="0b690-111">This means that the cache gets full quickly and remains full of the list query results and SharePoint objects that your users are requesting on a regular basis.</span></span>
  
![オンプレミスのフロントエンド Web サーバーへのトラフィックと負荷を示しています](../media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
<span data-ttu-id="0b690-113">その結果、ユーザーが 2 回目にページにアクセスすると、ページの読み込み時間が向上します。</span><span class="sxs-lookup"><span data-stu-id="0b690-113">As a result, the second time a user visits a page, the page load time improves.</span></span> <span data-ttu-id="0b690-114">同じページを少なくとも 4 回読み込むと、すべてのフロントエンド Web サーバーにページがキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="0b690-114">After a minimum of four loads of the same page, the page is cached on all of the front-end web servers.</span></span>
  
<span data-ttu-id="0b690-115">対照的に、オンラインではSharePointサーバーが多数あるだけでなく、サイトも多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="0b690-115">In contrast, in SharePoint Online there are many more servers but also many more sites.</span></span> <span data-ttu-id="0b690-116">各ユーザーは、キャッシュが設定された別のフロントエンド Web サーバーに接続できます。</span><span class="sxs-lookup"><span data-stu-id="0b690-116">Each user may connect to a different front-end web server that doesn't have the cache populated.</span></span> <span data-ttu-id="0b690-117">または、おそらくキャッシュはサーバーに対して設定されますが、そのフロントエンド Web サーバーの次のユーザーが別のサイトからページを要求します。</span><span class="sxs-lookup"><span data-stu-id="0b690-117">Or, perhaps the cache does get populated for a server, but the next user to that front-end web server requests a page from a different site.</span></span> <span data-ttu-id="0b690-118">または、次のユーザーが前回の訪問時と同じページを要求した場合でも、そのページをキャッシュに含めなかった別のフロントエンド Web サーバーに負荷分散されます。</span><span class="sxs-lookup"><span data-stu-id="0b690-118">Or, even if the next user requests the same page as on their previous visit, they are load-balanced to a different front-end web server that doesn't have that page in its cache.</span></span> <span data-ttu-id="0b690-119">この最後のケースでは、キャッシュはユーザーの助けにはなってこない。</span><span class="sxs-lookup"><span data-stu-id="0b690-119">In this last case, caching doesn't help the users at all.</span></span>
  
<span data-ttu-id="0b690-120">次の図では、各ドットは、ユーザーが要求しているページと、そのページがキャッシュされた場所を表しています。</span><span class="sxs-lookup"><span data-stu-id="0b690-120">In the following figure, each dot represents a page that a user is requesting and where it cached.</span></span> <span data-ttu-id="0b690-121">色が異なると、SaaS インフラストラクチャを共有して利用する顧客が異なります。</span><span class="sxs-lookup"><span data-stu-id="0b690-121">Different colors represent different customers making shared use of the SaaS infrastructure.</span></span>
  
![SharePoint Online におけるオブジェクト キャッシュの結果を示します](../media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
<span data-ttu-id="0b690-123">図から分かっている通り、キャッシュされたバージョンのページでサーバーにアクセスする可能性は薄いです。</span><span class="sxs-lookup"><span data-stu-id="0b690-123">As you can see from the diagram, the chances of any given user hitting a server with the cached version of their page are slim.</span></span> <span data-ttu-id="0b690-124">また、スループットが大きく、サーバーが多くのサイト間で共有されているという事実により、キャッシュに使用できる領域が非常に多いので、キャッシュは長持ちしません。</span><span class="sxs-lookup"><span data-stu-id="0b690-124">Also, due to the large throughput and fact that the servers are shared between many sites, the cache doesn't last long since there is only so much space for caching available.</span></span>
  
<span data-ttu-id="0b690-125">これらのすべての理由から、キャッシュされたオブジェクトを取得するユーザーに依存する方法は、SharePoint Online で高品質のユーザー エクスペリエンスとページ読み込み時間を確保する効果的な方法ではありません。</span><span class="sxs-lookup"><span data-stu-id="0b690-125">For all of these reasons, relying on users getting cached objects is not an effective way to ensure a quality user experience and page load times in SharePoint Online.</span></span>
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a><span data-ttu-id="0b690-126">オブジェクト キャッシュを使用してオンラインのパフォーマンスを向上SharePoint場合、代わりに何を使用しますか?</span><span class="sxs-lookup"><span data-stu-id="0b690-126">If we can't rely on the object cache to improve performance in SharePoint Online, what do we use instead?</span></span>

<span data-ttu-id="0b690-127">SharePoint Online でのキャッシュに依存してはならないので、オブジェクト キャッシュを使用するカスタマイズのSharePoint設計方法を評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0b690-127">Since you shouldn't rely on caching in SharePoint Online, you should evaluate alternative design approaches for SharePoint customizations that use the object cache.</span></span> <span data-ttu-id="0b690-128">つまり、ユーザーに良い結果を生み出すには、オブジェクト キャッシュに依存しないパフォーマンスの問題に対するアプローチを使用します。</span><span class="sxs-lookup"><span data-stu-id="0b690-128">This means using approaches for performance issues which do not rely on the object caching in order to produce good results for users.</span></span> <span data-ttu-id="0b690-129">これは、このシリーズの他の記事の一部で説明され、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0b690-129">This is described in some of the other articles in this series and include:</span></span>
  
- [<span data-ttu-id="0b690-130">SharePoint Online のナビゲーション オプション</span><span class="sxs-lookup"><span data-stu-id="0b690-130">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="0b690-131">SharePoint Online での縮小とバンドル</span><span class="sxs-lookup"><span data-stu-id="0b690-131">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="0b690-132">SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用</span><span class="sxs-lookup"><span data-stu-id="0b690-132">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-microsoft-365-cdn-with-spo.md)
    
- [<span data-ttu-id="0b690-133">SharePoint Online での画像の読み込み遅延と JavaScript</span><span class="sxs-lookup"><span data-stu-id="0b690-133">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

