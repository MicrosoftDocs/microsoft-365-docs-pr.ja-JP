---
title: SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
- seo-marvel-apr2020
ms.assetid: 0d93ff4a-8fbd-42b8-9227-d817dba0046d
description: この記事では、Azure インフラストラクチャサービスでホストされている Sharepoint Server 2013 インターネットサイトを設計および実装するためのリソースを提供します。
ms.openlocfilehash: f8c2094b63f8fbd390fb904fc9d1b5798b8b814a
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46692123"
---
# <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a><span data-ttu-id="2b5f6-103">SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト</span><span class="sxs-lookup"><span data-stu-id="2b5f6-103">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>

 <span data-ttu-id="2b5f6-104">Azure インフラストラクチャサービスでホストされている SharePoint Server 2013 の利点を使用するインターネットサイト。</span><span class="sxs-lookup"><span data-stu-id="2b5f6-104">Internet sites that use SharePoint Server 2013 benefit by being hosted in Azure Infrastructure Services.</span></span> <span data-ttu-id="2b5f6-105">この記事では、このソリューションを設計し、実装するためのリソースを提供します。</span><span class="sxs-lookup"><span data-stu-id="2b5f6-105">This article provides resources for designing and implementing this solution.</span></span>
  
## <a name="using-azure-infrastructure-services-for-internet-sites"></a><span data-ttu-id="2b5f6-106">インターネット サイト向けの Azure インフラストラクチャ サービスの使用</span><span class="sxs-lookup"><span data-stu-id="2b5f6-106">Using Azure Infrastructure Services for Internet sites</span></span>

<span data-ttu-id="2b5f6-p102">Microsoft Azure は SharePoint Server 2013 に基づくインターネット サイトをホストするための強力なオプションを提供します。その利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2b5f6-p102">Microsoft Azure provides a compelling option for hosting Internet sites based on SharePoint Server 2013. Advantages include the following:</span></span>
  
- <span data-ttu-id="2b5f6-109">インフラストラクチャの構築ではなく、魅力的なサイトの開発に重点を置きます。</span><span class="sxs-lookup"><span data-stu-id="2b5f6-109">Focus on developing a great site instead of building infrastructure.</span></span>
    
- <span data-ttu-id="2b5f6-110">スケール アウトとスケール インにより、需要に基づきソリューション規模を柔軟に決めることができます。</span><span class="sxs-lookup"><span data-stu-id="2b5f6-110">Flexibility to scale your solution based on demand by scaling out and in.</span></span>
    
- <span data-ttu-id="2b5f6-111">必要で実際に使用するリソースだけに課金されます。</span><span class="sxs-lookup"><span data-stu-id="2b5f6-111">Pay only for the resources that you need and use.</span></span>
    
- <span data-ttu-id="2b5f6-112">顧客アカウントに Azure Active Directory を利用できます。</span><span class="sxs-lookup"><span data-stu-id="2b5f6-112">Take advantage of Azure Active Directory for customer accounts.</span></span>
    
- <span data-ttu-id="2b5f6-113">詳細なレポートや分析など、Microsoft 365 では現在利用できない機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="2b5f6-113">Add features that are not currently available in Microsoft 365, such as deep reporting and analytics.</span></span>
    
## <a name="resources"></a><span data-ttu-id="2b5f6-114">リソース</span><span class="sxs-lookup"><span data-stu-id="2b5f6-114">Resources</span></span>

<span data-ttu-id="2b5f6-115">次の技術説明図および記事は、SharePoint Server 2013 を使用して Azure でインターネット サイトを設計し、実装する方法に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="2b5f6-115">The following technical illustrations and articles provide information about how to design and implement Internet sites in Azure by using SharePoint Server 2013.</span></span>
  
|<span data-ttu-id="2b5f6-116">**Resource**</span><span class="sxs-lookup"><span data-stu-id="2b5f6-116">**Resource**</span></span>|<span data-ttu-id="2b5f6-117">**詳細情報**</span><span class="sxs-lookup"><span data-stu-id="2b5f6-117">**More information**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2b5f6-118">**Azure での SharePoint Server 2013 のインターネット サイト**</span><span class="sxs-lookup"><span data-stu-id="2b5f6-118">**SharePoint Server 2013 Internet sites in Azure**</span></span> <br/> <span data-ttu-id="2b5f6-119">[![SharePoint を使用した Azure のインターネット サイトのイメージ](../media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span><span class="sxs-lookup"><span data-stu-id="2b5f6-119">[![Image of Internet sites in Azure using SharePoint](../media/MS-AZ-SPInternetSites.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392552)</span></span> <br/> <span data-ttu-id="2b5f6-120">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552) \|[          ](https://go.microsoft.com/fwlink/p/?LinkId=392551) [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)  </span><span class="sxs-lookup"><span data-stu-id="2b5f6-120">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)  \| [          ](https://go.microsoft.com/fwlink/p/?LinkId=392551)[Visio](https://go.microsoft.com/fwlink/p/?LinkId=392551)</span></span> <br/> |<span data-ttu-id="2b5f6-121">このアーキテクチャ モデルは、Azure のインターネット サイトの主要な設計活動および推奨されるアーキテクチャの選択肢の概要を説明しています。</span><span class="sxs-lookup"><span data-stu-id="2b5f6-121">This architecture model outlines key design activities and recommended architecture choices for Internet sites in Azure.</span></span>  <br/> |
|<span data-ttu-id="2b5f6-122">\*\*設計サンプル: SharePoint Server 2013 用の Azure のインターネット サイト \*\*</span><span class="sxs-lookup"><span data-stu-id="2b5f6-122">**Design sample: Internet Sites in Azure for SharePoint Server 2013**</span></span> <br/> <span data-ttu-id="2b5f6-123">[![デザイン サンプルの図:SharePoint 2013 用の Microsoft Azure のインターネット サイト](../media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span><span class="sxs-lookup"><span data-stu-id="2b5f6-123">[![Image of the Design sample: Internet sites in Microsoft Azure for SharePoint 2013](../media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://go.microsoft.com/fwlink/p/?LinkId=392549)</span></span> <br/> <span data-ttu-id="2b5f6-124">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span><span class="sxs-lookup"><span data-stu-id="2b5f6-124">[PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392548)</span></span> <br/> |<span data-ttu-id="2b5f6-125">独自のアーキテクチャの開始点としてこの設計サンプルをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="2b5f6-125">Use this design sample as a starting point for your own architecture.</span></span>  <br/> |
|<span data-ttu-id="2b5f6-126">**[SharePoint 2013 用の Microsoft Azure アーキテクチャ](microsoft-azure-architectures-for-sharepoint-2013.md)**</span><span class="sxs-lookup"><span data-stu-id="2b5f6-126">**[Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)**</span></span> <br/> |<span data-ttu-id="2b5f6-127">この記事は、SharePoint ソリューションをホストするための Azure アーキテクチャの設計方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="2b5f6-127">This article describes how to design Azure architectures to host SharePoint solutions.</span></span>  <br/> |

## <a name="see-also"></a><span data-ttu-id="2b5f6-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b5f6-128">See Also</span></span>

[<span data-ttu-id="2b5f6-129">Microsoft 365 ソリューションおよびアーキテクチャ センター</span><span class="sxs-lookup"><span data-stu-id="2b5f6-129">Microsoft 365 solution and architecture center</span></span>](../solutions/solution-architecture-center.md)


