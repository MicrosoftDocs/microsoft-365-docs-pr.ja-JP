---
title: SharePoint 2013 用の Microsoft Azure アーキテクチャ
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
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: Microsoft Azure 仮想マシンでホストできる SharePoint 2013 ソリューションの種類と、ホストする Azure をセットアップする方法について説明します。
ms.openlocfilehash: eed74e2dcbe383f0f63e7f6ea2fc70fe7b51b1b3
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "50924178"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a><span data-ttu-id="f64e0-103">SharePoint 2013 用の Microsoft Azure アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="f64e0-103">Microsoft Azure Architectures for SharePoint 2013</span></span>

<span data-ttu-id="f64e0-104">Azure は SharePoint Server 2013 ソリューションをホストするための優れた環境です。</span><span class="sxs-lookup"><span data-stu-id="f64e0-104">Azure is a good environment for hosting a SharePoint Server 2013 solution.</span></span> <span data-ttu-id="f64e0-105">ほとんどの場合、Microsoft 365 をお勧めしますが、Azure でホストされている SharePoint Server ファームは、特定のソリューションにとって良い選択肢になります。</span><span class="sxs-lookup"><span data-stu-id="f64e0-105">In most cases, we recommend Microsoft 365, but a SharePoint Server farm hosted in Azure can be a good option for specific solutions.</span></span> <span data-ttu-id="f64e0-106">この記事では、SharePoint ソリューションが Azure プラットフォームに適合するように設計する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f64e0-106">This article describes how to architect SharePoint solutions so they are a good fit in the Azure platform.</span></span> <span data-ttu-id="f64e0-107">次の 2 つのソリューションが例として使用されています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-107">The following two specific solutions are used as examples:</span></span>
  
- [<span data-ttu-id="f64e0-108">Microsoft Azure での SharePoint Server 2013 の障害復旧</span><span class="sxs-lookup"><span data-stu-id="f64e0-108">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [<span data-ttu-id="f64e0-109">SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト</span><span class="sxs-lookup"><span data-stu-id="f64e0-109">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a><span data-ttu-id="f64e0-110">推奨されている Azure インフラストラクチャ サービスの SharePoint ソリューション</span><span class="sxs-lookup"><span data-stu-id="f64e0-110">Recommended SharePoint solutions for Azure Infrastructure Services</span></span>

<span data-ttu-id="f64e0-p102">Azure インフラストラクチャ サービスは、SharePoint ソリューションをホストするための非常に魅力的な選択肢です。このプラットフォームでは、いくつかのソリューションが他のものと比べてより適していると言えます。以下の表では、推奨されているソリューションが示されています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p102">Azure infrastructure services is a compelling option for hosting SharePoint solutions. Some solutions are a better fit for this platform than others. The following table shows recommended solutions.</span></span>
  
|<span data-ttu-id="f64e0-114">**解決方法**</span><span class="sxs-lookup"><span data-stu-id="f64e0-114">**Solution**</span></span>|<span data-ttu-id="f64e0-115">**Azure でそのソリューションが推奨されている理由**</span><span class="sxs-lookup"><span data-stu-id="f64e0-115">**Why this solution is recommended for Azure**</span></span>|
|:-----|:-----|
|<span data-ttu-id="f64e0-116">開発環境とテスト環境</span><span class="sxs-lookup"><span data-stu-id="f64e0-116">Development and test environments</span></span>  <br/> |<span data-ttu-id="f64e0-117">これらの環境を簡単に作成して管理できます。</span><span class="sxs-lookup"><span data-stu-id="f64e0-117">It's easy to create and manage these environments.</span></span>  <br/> |
|<span data-ttu-id="f64e0-118">Azure に対するオンプレミス SharePoint ファームの障害復旧</span><span class="sxs-lookup"><span data-stu-id="f64e0-118">Disaster recovery of on-premises SharePoint farms to Azure</span></span>  <br/> |<span data-ttu-id="f64e0-119">**ホストされているセカンダリ データセンター** 別の地域にあるセカンダリ データセンターに投資するのではなく、Azure を使用します。</span><span class="sxs-lookup"><span data-stu-id="f64e0-119">**Hosted secondary datacenter** Use Azure instead of investing in a secondary datacenter in a different region.</span></span> <br/> <span data-ttu-id="f64e0-p103">**低コストの障害復旧環境** オンプレミスの障害復旧環境よりも維持するリソースが少なく、費用も低く抑えられます。リソースの数は、コールド スタンバイ、ウォーム スタンバイ、ホット スタンバイのどの障害復旧環境を選択するかに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p103">**Lower-cost disaster-recovery environments** Maintain and pay for fewer resources than an on-premises disaster recovery environment. The number of resources depends on the disaster recovery environment you choose: cold standby, warm standby, or hot standby. </span></span><br/> <span data-ttu-id="f64e0-p104">**より柔軟なプラットフォーム** 障害時には、負荷要件を満たすためにご使用の復旧 SharePoint ファームを簡単にスケールアウトできます。それらのリソースが不要になった場合にはスケールインします。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p104">**More elastic platform** In the event of a disaster, easily scale-out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources. </span></span><br/> <span data-ttu-id="f64e0-124">「[Microsoft Azure での SharePoint Server 2013 の障害復旧](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f64e0-124">See [SharePoint Server 2013 Disaster Recovery in Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).</span></span>  <br/> |
|<span data-ttu-id="f64e0-125">Microsoft 365 では利用できない機能とスケールを使用するインターネット向けサイト</span><span class="sxs-lookup"><span data-stu-id="f64e0-125">Internet-facing sites that use features and scale not available in Microsoft 365</span></span>  <br/> |<span data-ttu-id="f64e0-126">**作業の重点** インフラストラクチャの構築ではなく、魅力的なサイトの構築のほうに集中できます。</span><span class="sxs-lookup"><span data-stu-id="f64e0-126">**Focus your efforts** Concentrate on building a great site rather than building infrastructure.</span></span> <br/> <span data-ttu-id="f64e0-p105">**Azure でのサイズの柔軟性を活用** 必要に応じて新しいサーバーを追加してファームのサイズを変更し、必要なリソースに対してのみ支払いを行います。動的なマシンの割り当てはサポートされていません (自動スケール)。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p105">**Take advantage of elasticity in Azure** Size the farm for the demand by adding new servers, and pay only for resources you need. Dynamic machine allocation is not supported (auto scale). </span></span><br/> <span data-ttu-id="f64e0-129">**Azure Active Directory (AD) の使用** ユーザー アカウントに関して Azure AD を活用します。</span><span class="sxs-lookup"><span data-stu-id="f64e0-129">**Use Azure Active Directory (AD)** Take advantage of Azure AD for customer accounts.</span></span> <br/> <span data-ttu-id="f64e0-130">**Microsoft 365 で使用できない SharePoint 機能の追加** 詳細なレポートと Web 分析を追加します。</span><span class="sxs-lookup"><span data-stu-id="f64e0-130">**Add SharePoint functionality not available in Microsoft 365** Add deep reporting and web analytics.</span></span> <br/> <span data-ttu-id="f64e0-131">「[SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f64e0-131">See [Internet Sites in Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).</span></span>  <br/> |
|<span data-ttu-id="f64e0-132">Microsoft 365 またはオンプレミス環境をサポートするアプリ ファーム</span><span class="sxs-lookup"><span data-stu-id="f64e0-132">App farms to support Microsoft 365 or on-premises environments</span></span>  <br/> |<span data-ttu-id="f64e0-133">**アプリのビルド、テスト、ホスト** Azure で、オンプレミス環境とクラウド環境の両方をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="f64e0-133">**Build, test, and host apps** in Azure to support both on-premises and cloud environments.</span></span> <br/> <span data-ttu-id="f64e0-134">**このロールのホスト** オンプレミス環境用の新しいハードウェアを購入する代わりに、Azure で行います。</span><span class="sxs-lookup"><span data-stu-id="f64e0-134">**Host this role** in Azure instead of buying new hardware for on-premises environments.</span></span> <br/> |
   
<span data-ttu-id="f64e0-135">イントラネットとコラボレーションのソリューション、およびワークロードに関しては、以下の選択肢を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="f64e0-135">For intranet and collaboration solutions and workloads, consider the following options:</span></span>
  
- <span data-ttu-id="f64e0-136">Microsoft 365 がビジネス要件を満たしているのか、それともソリューションの一部になるか判断します。</span><span class="sxs-lookup"><span data-stu-id="f64e0-136">Determine if Microsoft 365 meets your business requirements or can be part of the solution.</span></span> <span data-ttu-id="f64e0-137">Microsoft 365 には、常に最新の豊富な機能セットが提供されています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-137">Microsoft 365 provides a rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="f64e0-138">Microsoft 365 がすべてのビジネス要件を満たしていない場合は、Microsoft コンサルティング サービス (MCS) からオンプレミスの SharePoint 2013 の標準実装を検討してください。</span><span class="sxs-lookup"><span data-stu-id="f64e0-138">If Microsoft 365 does not meet all your business requirements, consider a standard implementation of SharePoint 2013 on premises from Microsoft Consulting Services (MCS).</span></span> <span data-ttu-id="f64e0-139">標準のアーキテクチャは、カスタマイズされたアーキテクチャよりもソリューションの実装が迅速かつ安価で、なおかつ簡単です。</span><span class="sxs-lookup"><span data-stu-id="f64e0-139">A standard architecture can be a quicker, cheaper, and easier solution for you to support than a customized one.</span></span> 
    
- <span data-ttu-id="f64e0-140">標準実装がビジネス要件を満たさない場合には、カスタマイズされたオンプレミスのソリューションを考慮します。</span><span class="sxs-lookup"><span data-stu-id="f64e0-140">If a standard implementation doesn't meet your business requirements, consider a customized on-premises solution.</span></span>
    
- <span data-ttu-id="f64e0-p108">ビジネス要件でクラウド プラットフォームを使用することが重要な場合には、Azure インフラストラクチャ サービスでホストされている SharePoint 2013 の標準実装、またはカスタマイズ実装を考慮してください。SharePoint ソリューションは、Microsoft のネイティブ以外の他のパブリック クラウド プラットフォームよりも Azure での方が、より簡単にサポートできます。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p108">If using a cloud platform is important for your business requirements, consider a standard or customized implementation of SharePoint 2013 hosted in Azure infrastructure services. SharePoint solutions are much easier to support in Azure than other non-native Microsoft public cloud platforms.</span></span>
    
## <a name="before-you-design-the-azure-environment"></a><span data-ttu-id="f64e0-143">Azure 環境を設計する前に</span><span class="sxs-lookup"><span data-stu-id="f64e0-143">Before you design the Azure environment</span></span>

<span data-ttu-id="f64e0-p109">この記事では SharePoint トポロジの例が使用されていますが、こうした設計概念は任意の SharePoint ファーム トポロジで使用できます。Azure 環境を設計する前に、SharePoint ファームを設計するための次のトポロジ、アーキテクチャ、キャパシティ、およびパフォーマンスに関するガイダンスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p109">While this article uses example SharePoint topologies, you can use these design concepts with any SharePoint farm topology. Before you design the Azure environment, use the following topology, architecture, capacity, and performance guidance to design the SharePoint farm:</span></span>
  
- [<span data-ttu-id="f64e0-146">SharePoint 2013 の IT 担当者向けアーキテクチャ設計</span><span class="sxs-lookup"><span data-stu-id="f64e0-146">Architecture design for SharePoint 2013 IT pros</span></span>](/SharePoint/technical-reference/technical-diagrams)
    
- [<span data-ttu-id="f64e0-147">Plan for performance and capacity management in SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="f64e0-147">Plan for performance and capacity management in SharePoint Server 2013</span></span>](/SharePoint/administration/performance-planning-in-sharepoint-server-2013)
    
## <a name="determine-the-active-directory-domain-type"></a><span data-ttu-id="f64e0-148">Active Directory ドメインの種類の決定</span><span class="sxs-lookup"><span data-stu-id="f64e0-148">Determine the Active Directory domain type</span></span>

<span data-ttu-id="f64e0-p110">各 SharePoint Server ファームは、ファーム セットアップ用の管理アカウントを提供する点で Active Directory に依存しています。この時点では、Azure には SharePoint ソリューション用の 2 つの選択肢があります。それらについて、以下の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p110">Each SharePoint Server farm relies on Active Directory to provide administrative accounts for farm setup. At this time, there are two options for SharePoint solutions in Azure. These are described in the following table.</span></span>
  
|<span data-ttu-id="f64e0-152">**オプション**</span><span class="sxs-lookup"><span data-stu-id="f64e0-152">**Option**</span></span>|<span data-ttu-id="f64e0-153">**説明**</span><span class="sxs-lookup"><span data-stu-id="f64e0-153">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="f64e0-154">専用ドメイン</span><span class="sxs-lookup"><span data-stu-id="f64e0-154">Dedicated domain</span></span>  <br/> |<span data-ttu-id="f64e0-p111">Azure に対して専用で独立した Active Directory ドメインを展開し、SharePoint ファームをサポートできます。一般のインターネット サイトに適しています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p111">You can deploy a dedicated and isolated Active Directory domain to Azure to support your SharePoint farm. This is a good choice for public-facing Internet sites.</span></span>  <br/> |
|<span data-ttu-id="f64e0-157">クロスプレミス接続を使用したオンプレミス ドメインの拡張</span><span class="sxs-lookup"><span data-stu-id="f64e0-157">Extend the on-premises domain through a cross-premises connection</span></span>  <br/> |<span data-ttu-id="f64e0-p112">クロスプレミス接続を使用してオンプレミス ドメインを拡張すると、ユーザーは SharePoint ファームに、オンプレミスでホストされているのと同じようにイントラネットを介してアクセスします。オンプレミスの Active Directory と DNS 実装の利点を生かすことができます。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p112">When you extend the on-premises domain through a cross-premises connection, users access the SharePoint farm via your intranet as if it were hosted on-premises. You can take advantage of your on-premises Active Directory and DNS implementation.</span></span>  <br/> <span data-ttu-id="f64e0-160">オンプレミスのファームとの間でフェールオーバーするために Azure で障害復旧環境を構築するには、クロスプレミス接続が必要になります。</span><span class="sxs-lookup"><span data-stu-id="f64e0-160">A cross-premises connection is required for building a disaster-recovery environment in Azure to fail over to from your on-premises farm.</span></span>  <br/> |
   
<span data-ttu-id="f64e0-p113">この記事には、クロスプレミス接続を使用してオンプレミス ドメインを拡張するための設計概念も記されています。ご使用のソリューションで専用ドメインを使用する場合には、クロスプレミス接続は不要です。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p113">This article includes design concepts for extending the on-premises domain through a cross-premises connection. If your solution uses a dedicated domain, you don't need a cross-premises connection.</span></span>
  
## <a name="design-the-virtual-network"></a><span data-ttu-id="f64e0-163">仮想ネットワークの設計</span><span class="sxs-lookup"><span data-stu-id="f64e0-163">Design the virtual network</span></span>

<span data-ttu-id="f64e0-p114">最初に、仮想マシンを配置するサブネットを含む仮想ネットワークが Azure で必要になります。仮想ネットワークには、プライベート IP アドレス空間が必要です。その一部をサブネットに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p114">First you need a virtual network in Azure, which includes subnets on which you will place your virtual machines. The virtual network needs a private IP address space, portions of which you assign to the subnets.</span></span>
  
<span data-ttu-id="f64e0-166">クロスプレミス接続を使用して Azure にオンプレミス ネットワークを拡張する場合は (このことは障害回復環境で必要となります)、オンプレミス環境と他の Azure 仮想ネットワークを含む組織ネットワークの他のどの場所にも使用されていないプライベート アドレス空間を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f64e0-166">If you are extending your on-premises network to Azure through a cross-premises connection (required for a disaster recovery environment), you must choose a private address space that is not already in use elsewhere in your organization network, which can include your on-premises environment and other Azure virtual networks.</span></span> 
  
<span data-ttu-id="f64e0-167">**図 1:Azure での仮想ネットワークを使用したオンプレミス環境**</span><span class="sxs-lookup"><span data-stu-id="f64e0-167">**Figure 1: On-premises environment with a virtual network in Azure**</span></span>

![SharePoint ソリューション用の Microsoft Azure 仮想ネットワーク設計。Azure ゲートウェイ用の 1 つのサブネット。仮想マシン用の 1 つのサブネット。](../media/OPrrasconWA-AZarch.png)
  
<span data-ttu-id="f64e0-171">この図では次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-171">In this diagram:</span></span>
  
- <span data-ttu-id="f64e0-p116">Azure 内の仮想ネットワークは、オンプレミス環境と横並びに示されています。2 つの環境は、クロスプレミス接続 (サイト間 VPN 接続または ExpressRoute である場合もあります) によってまだ接続されていません。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p116">A virtual network in Azure is illustrated side-by-side to the on-premises environment. The two environments are not yet connected by a cross-premises connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="f64e0-p117">この時点では、仮想ネットワークにはサブネットのみが含まれており、他のアーキテクチャ要素は含まれていません。1 つのサブネットが Azure ゲートウェイをホストし、他のサブネットは SharePoint ファームの層をホストします。その 1 つは Active Directory と DNS 用に追加されたものです。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p117">At this point, the virtual network just includes the subnets and no other architectural elements. One subnet will host the Azure gateway and other subnets host the tiers of the SharePoint farm, with an additional one for Active Directory and DNS.</span></span>
    
## <a name="add-cross-premises-connectivity"></a><span data-ttu-id="f64e0-176">クロスプレミス接続の追加</span><span class="sxs-lookup"><span data-stu-id="f64e0-176">Add cross-premises connectivity</span></span>

<span data-ttu-id="f64e0-p118">次の展開手順では、クロスプレミス接続を作成します (ご利用のソリューションに該当する場合)。クロスプレミス接続の場合、Azure ゲートウェイを配置する別のゲートウェイ サブネットを作成して、それにアドレス スペースを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p118">The next deployment step is to create the cross-premises connection (if this applies to your solution). For cross-premises connections, a Azure gateway resides in a separate gateway subnet, which you must create and assign an address space.</span></span> 
  
<span data-ttu-id="f64e0-179">クロスプレミス接続を計画する場合は、Azure ゲートウェイと、オンプレミス ゲートウェイ デバイスへの接続を定義して作成します。</span><span class="sxs-lookup"><span data-stu-id="f64e0-179">When you plan for a cross-premises connection, you define and create an Azure gateway and connection to an on-premises gateway device.</span></span>
  
<span data-ttu-id="f64e0-180">**図 2:オンプレミス環境と Azure 間でサイト間接続を提供するための Azure ゲートウェイとオンプレミス ゲートウェイ デバイスの使用**</span><span class="sxs-lookup"><span data-stu-id="f64e0-180">**Figure 2: Using an Azure gateway and an on-premises gateway device to provide site-to-site connectivity between the on-premises environment and Azure**</span></span>

![オンプレミス環境はクロスプレミス接続 (サイト間 VPN 接続または ExpressRoute が可能) を介して Azure 仮想ネットワークに接続されています](../media/AZarch-VPNgtwyconnct.png)
  
<span data-ttu-id="f64e0-182">この図では次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-182">In this diagram:</span></span>
  
- <span data-ttu-id="f64e0-183">前述の図に加えられた点として、オンプレミス環境がクロスプレミス接続 (サイト間 VPN 接続または ExpressRoute である場合もあります) を介して Azure 仮想ネットワークに接続されています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-183">Adding to the previous diagram, the on-premises environment is connected to the Azure virtual network by a cross-premise connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="f64e0-184">Azure ゲートウェイはゲートウェイ サブネット上に配置します。</span><span class="sxs-lookup"><span data-stu-id="f64e0-184">An Azure gateway is on a gateway subnet.</span></span>
    
- <span data-ttu-id="f64e0-185">オンプレミス環境には、ルーターまたは VPN サーバーなどのゲートウェイ デバイスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f64e0-185">The on-premises environment includes a gateway device, such as a router or VPN server.</span></span>
    
<span data-ttu-id="f64e0-186">クロスプレミス仮想ネットワークの計画と作成に関する詳細については、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="f64e0-186">For additional information to plan for and create a cross-premises virtual network, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a><span data-ttu-id="f64e0-187">Active Directory ドメイン サービス (DS) AD DNS の追加</span><span class="sxs-lookup"><span data-stu-id="f64e0-187">Add Active Directory Domain Services (AD DS) and DNS</span></span>

<span data-ttu-id="f64e0-188">Azure における障害復旧の場合、Windows Server AD と DNS をハイブリッド シナリオで展開します。このとき、Windows Server AD は、オンプレミスと Azure 仮想マシンの両方に展開されます。</span><span class="sxs-lookup"><span data-stu-id="f64e0-188">For disaster recovery in Azure, you deploy Windows Server AD and DNS in a hybrid scenario where Windows Server AD is deployed both on-premises and on Azure virtual machines.</span></span>
  
<span data-ttu-id="f64e0-189">**図 3: Active Directory ドメインのハイブリッド構成**</span><span class="sxs-lookup"><span data-stu-id="f64e0-189">**Figure 3: Hybrid Active Directory domain configuration**</span></span>

![Azure の仮想ネットワークと SharePoint ファームのサブネットに配置された 2 つの仮想マシンは、レプリカ ドメイン コントローラーおよび DNS サーバーです](../media/AZarch-HyADdomainConfig.png)
  
<span data-ttu-id="f64e0-p119">この図は前の図に基づいて作成されていて、Windows Server AD と DNS のサブネットには 2 つの仮想マシンが追加されています。これらの仮想マシンは、レプリカのドメイン コントローラーと DNS サーバーです。これらは、オンプレミス Windows Server AD 環境の拡張となります。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p119">This diagram builds on the previous diagrams by adding two virtual machines to a Windows Server AD and DNS subnet. These virtual machines are replica domain controllers and DNS servers. They are an extension of the on-premises Windows Server AD environment.</span></span> 
  
<span data-ttu-id="f64e0-p120">次の表に、Azure におけるこうした仮想マシンに関して推奨されている構成を示します。これらを、ご使用の環境を設計するための開始点として使用してください。Azure 環境がオンプレミス環境と通信しない専用ドメインの場合であってもこれは当てはまります。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p120">The following table provides configuration recommendations for these virtual machines in Azure. Use these as a starting point for designing your own environment—even for a dedicated domain where your Azure environment doesn't communicate with your on-premises environment.</span></span>
  
|<span data-ttu-id="f64e0-196">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="f64e0-196">**Item**</span></span>|<span data-ttu-id="f64e0-197">**構成**</span><span class="sxs-lookup"><span data-stu-id="f64e0-197">**Configuration**</span></span>|
|:-----|:-----|
|<span data-ttu-id="f64e0-198">Azure での仮想マシンのサイズ</span><span class="sxs-lookup"><span data-stu-id="f64e0-198">Virtual machine size in Azure</span></span>  <br/> |<span data-ttu-id="f64e0-199">標準層の A1 または A2 サイズ</span><span class="sxs-lookup"><span data-stu-id="f64e0-199">A1 or A2 size in the Standard tier</span></span>  <br/> |
|<span data-ttu-id="f64e0-200">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="f64e0-200">Operating system</span></span>  <br/> |<span data-ttu-id="f64e0-201">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f64e0-201">Windows Server 2012 R2</span></span>  <br/> |
|<span data-ttu-id="f64e0-202">Active Directory ロール</span><span class="sxs-lookup"><span data-stu-id="f64e0-202">Active Directory role</span></span>  <br/> |<span data-ttu-id="f64e0-p121">グローバル カタログ サーバーとして指定された AD DS ドメイン コントローラー。この構成により、クロスプレミス接続を使用する出口トラフィックが減少します。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p121">AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the cross-premises connection.</span></span>  <br/> <span data-ttu-id="f64e0-205">変更率の高いマルチドメイン環境の場合 (一般的ではありません)、オンプレミスのドメイン コントローラーが、Azure 内のグローバル カタログ サーバーと同期しないように構成して、レプリケーション トラフィックを削減します。</span><span class="sxs-lookup"><span data-stu-id="f64e0-205">In a multidomain environment with high rates of change (this is not common), configure domain controllers on premises not to sync with the global catalog servers in Azure, to reduce replication traffic.</span></span>  <br/> |
|<span data-ttu-id="f64e0-206">DNS ロール</span><span class="sxs-lookup"><span data-stu-id="f64e0-206">DNS role</span></span>  <br/> |<span data-ttu-id="f64e0-207">ドメイン コントローラーで DNS サーバー サービスをインストールして構成します。</span><span class="sxs-lookup"><span data-stu-id="f64e0-207">Install and configure the DNS Server service on the domain controllers.</span></span>  <br/> |
|<span data-ttu-id="f64e0-208">データ ディスク</span><span class="sxs-lookup"><span data-stu-id="f64e0-208">Data disks</span></span>  <br/> |<span data-ttu-id="f64e0-p122">Active Directory データベース、ログ、SYSVOL を追加の Azure データ ディスクに配置します。オペレーティング システム ディスク、または Azure によって提供される一時ディスクには配置しないでください。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p122">Place the Active Directory database, logs, and SYSVOL on additional Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure.</span></span>  <br/> |
|<span data-ttu-id="f64e0-211">IP アドレス</span><span class="sxs-lookup"><span data-stu-id="f64e0-211">IP addresses</span></span>  <br/> |<span data-ttu-id="f64e0-212">静的 IP アドレスを使用して仮想ネットワークを構成し、ドメイン コントローラーの構成後にこれらのアドレスを仮想ネットワーク内の仮想マシンに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="f64e0-212">Use static IP addresses and configure the virtual network to assign these addresses to the virtual machines in the virtual network after the domain controllers have been configured.</span></span>  <br/> |
   
> [!IMPORTANT]
> <span data-ttu-id="f64e0-p123">Active Directory を Azure で展開する前に、「[Azure の仮想マシンでの Windows Server Active Directory のデプロイ ガイドライン](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100)」をご覧ください。ご使用のソリューションで別のアーキテクチャまたは構成設定が必要かどうかを判断するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p123">Before you deploy Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100). These help you determine if a different architecture or different configuration settings are needed for your solution.</span></span> 
  
## <a name="add-the-sharepoint-farm"></a><span data-ttu-id="f64e0-215">SharePoint ファームの追加</span><span class="sxs-lookup"><span data-stu-id="f64e0-215">Add the SharePoint farm</span></span>

<span data-ttu-id="f64e0-216">該当するサブネット上の層に SharePoint ファームの仮想マシンを配置します。</span><span class="sxs-lookup"><span data-stu-id="f64e0-216">Place the virtual machines of the SharePoint farm in tiers on the appropriate subnets.</span></span>
  
<span data-ttu-id="f64e0-217">**図 4: SharePoint 仮想マシンの配置**</span><span class="sxs-lookup"><span data-stu-id="f64e0-217">**Figure 4: Placement of SharePoint virtual machines**</span></span>

![SharePoint ファーム サブネット内の Azure 仮想ネットワークに追加された、データベース サーバーと SharePoint サーバーの役割](../media/AZarch-SPVMsinCloudSer.png)
  
<span data-ttu-id="f64e0-219">この図は前の図に基づいて作成されていて、それぞれの層で SharePoint ファーム サーバー ロールが追加されています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-219">This diagram builds on the previous diagrams by adding the SharePoint farm server roles in their respective tiers.</span></span>
  
- <span data-ttu-id="f64e0-220">SQL Server を実行する 2 つのデータベース仮想マシンによってデータベース層が作成されます。</span><span class="sxs-lookup"><span data-stu-id="f64e0-220">Two database virtual machines running SQL Server create the database tier.</span></span>
    
- <span data-ttu-id="f64e0-221">それぞれのロール (フロント エンド サーバー、分散キャッシュ サーバー、バック エンド サーバー) ごとに、SharePoint Server 2013 を実行する 2 つの仮想マシンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-221">Two virtual machines running SharePoint Server 2013 for each of the following tiers: front end servers, distributed cache servers, and back end servers.</span></span>
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a><span data-ttu-id="f64e0-222">可用性セットと障害ドメイン用のサーバー ロールの設計と調整</span><span class="sxs-lookup"><span data-stu-id="f64e0-222">Design and fine tune server roles for availability sets and fault domains</span></span>

<span data-ttu-id="f64e0-p124">障害ドメインは、ロール インスタンスを実行するハードウェアをグループ化したものです。同じ障害ドメイン内の仮想マシンは、Azure インフラストラクチャによって同時に更新できます。そうしないと、同じラックを共有しているために、同時に障害が発生する可能性があります。同じ障害ドメインに 2 つの仮想マシンが含まれるというリスクを回避するため、仮想マシンを可用性セットとして構成できます。これにより、各仮想マシンが確実に異なる障害ドメインに配置されます。3 つの仮想マシンが可用性セットとして構成されると、Azure により、同じ障害ドメインに最大で 2 つの仮想マシンしか含まれないようになります。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p124">A fault domain is a grouping of hardware in which role instances run. Virtual machines within the same fault domain can be updated by the Azure infrastructure at the same time. Or, they can fail at the same time because they share the same rack. To avoid the risk of having two virtual machines on the same fault domain, you can configure your virtual machines as an availability set, which ensures that each virtual machine is in a different fault domain. If three virtual machines are configured as an availability set, Azure guarantees that no more than two of the virtual machines are located in the same fault domain.</span></span>
  
<span data-ttu-id="f64e0-p125">SharePoint ファーム用に Azure アーキテクチャを設計する場合、可用性セットの一部となるように同じサーバー ロールを構成します。これにより、ご使用のそれぞれの仮想マシンが複数の障害ドメインに分散されます。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p125">When you design the Azure architecture for a SharePoint farm, configure identical server roles to be part of an availability set. This ensures that your virtual machines are spread across multiple fault domains.</span></span>
  
<span data-ttu-id="f64e0-230">**図 5: SharePoint ファーム層の高可用性を確保するための Azure 可用性セットの使用**</span><span class="sxs-lookup"><span data-stu-id="f64e0-230">**Figure 5: Use Azure Availability Sets to provide high availability for the SharePoint farm tiers**</span></span>

![SharePoint 2013 ソリューションのための Azure インフラストラクチャ内の可用性セットの構成](../media/AZenv-WinAzureAvailSetsHA.png)
  
<span data-ttu-id="f64e0-p126">この図は、Azure インフラストラクチャ内の可用性セットの構成を示しています。次の各ロールが、それぞれの可用性セットで共有されています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p126">This diagram calls out the configuration of availability sets within the Azure infrastructure. Each of the following roles share a separate availability set:</span></span>
  
- <span data-ttu-id="f64e0-234">Active Directory と DNS</span><span class="sxs-lookup"><span data-stu-id="f64e0-234">Active Directory and DNS</span></span>
    
- <span data-ttu-id="f64e0-235">データベース</span><span class="sxs-lookup"><span data-stu-id="f64e0-235">Database</span></span>
    
- <span data-ttu-id="f64e0-236">バック エンド</span><span class="sxs-lookup"><span data-stu-id="f64e0-236">Back end</span></span>
    
- <span data-ttu-id="f64e0-237">分散キャッシュ</span><span class="sxs-lookup"><span data-stu-id="f64e0-237">Distribute cache</span></span>
    
- <span data-ttu-id="f64e0-238">フロント エンド</span><span class="sxs-lookup"><span data-stu-id="f64e0-238">Front end</span></span>
    
<span data-ttu-id="f64e0-p127">SharePoint ファームを Azure プラットフォームで調整しなければならない場合があります。すべてのコンポーネントで高可用性を確保するには、サーバー ロールがすべて同じ構成になっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p127">The SharePoint farm might need to be fine tuned in the Azure platform. To ensure high availability of all components, ensure that the server roles are all configured identically.</span></span>
  
<span data-ttu-id="f64e0-p128">次の例は、キャパシティとパフォーマンスに関する特定の目標を達成するための標準インターネット サイト アーキテクチャを示しています。この例では次のアーキテクチャ モデルが使用されています。[SharePoint Server 2013 のインターネット サイト検索アーキテクチャ](https://go.microsoft.com/fwlink/p/?LinkId=261519)</span><span class="sxs-lookup"><span data-stu-id="f64e0-p128">Here is an example that shows a standard Internet Sites architecture that meets specific capacity and performance goals. This example is featured in the following architecture model: [Internet Sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).</span></span>
  
<span data-ttu-id="f64e0-243">**図 6: 3 層ファームにおけるキャパシティとパフォーマンスの目標に関する計画例**</span><span class="sxs-lookup"><span data-stu-id="f64e0-243">**Figure 6: Planning example for capacity and performance goals in a three-tier farm**</span></span>

![特定の容量とパフォーマンスの目標を達成するコンポーネント割り当てを含む標準的な SharePoint 2013 のインターネット サイトのアーキテクチャ](../media/AZarch-CapPerfexmpArch.png)
  
<span data-ttu-id="f64e0-245">この図では次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-245">In this diagram:</span></span>
  
- <span data-ttu-id="f64e0-246">3 層ファームは、Web サーバー、アプリケーション サーバー、データベース サーバーで表されます。</span><span class="sxs-lookup"><span data-stu-id="f64e0-246">A three-tier farm is represented: web servers, application servers, and database servers.</span></span>
    
- <span data-ttu-id="f64e0-247">3 つの Web サーバーは複数のコンポーネントを含んでおり、同一に構成されています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-247">The three web servers are configured identically with multiple components.</span></span>
    
- <span data-ttu-id="f64e0-248">2 つのデータベース サーバーは同一に構成されています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-248">The two database servers are configured identically.</span></span>
    
- <span data-ttu-id="f64e0-p129">3 つのアプリケーション サーバーの構成は同一ではありません。これらのサーバー ロールに関しては、Azure で可用性セット用に調整が必要です。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p129">The three application servers are not configured identically. These server roles require fine tuning for availability sets in Azure.</span></span>
    
<span data-ttu-id="f64e0-251">アプリケーション サーバー層について詳しく見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="f64e0-251">Let's look closer at the application server tier.</span></span>
  
<span data-ttu-id="f64e0-252">**図 7: 調整前のアプリケーション サーバー層**</span><span class="sxs-lookup"><span data-stu-id="f64e0-252">**Figure 7: Application server tier before fine tuning**</span></span>

![Microsoft Azure 可用性セットのために調整する前の SharePoint Server 2013 アプリケーション サーバー層の例](../media/AZarch-AppServtierBefore.png)
  
<span data-ttu-id="f64e0-254">この図では次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-254">In this diagram:</span></span>
  
- <span data-ttu-id="f64e0-255">3 つのサーバーがアプリケーション層に含まれています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-255">Three servers are included in the application tier.</span></span>
    
- <span data-ttu-id="f64e0-256">最初のサーバーには 4 つのコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-256">The first server includes four components.</span></span>
    
- <span data-ttu-id="f64e0-257">2　番目のサーバーには、3 つのコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-257">The second server includes three components.</span></span>
    
- <span data-ttu-id="f64e0-258">3 番目のサーバーには、2 つのコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-258">The third server includes two components.</span></span>
    
<span data-ttu-id="f64e0-p130">対象ファームのパフォーマンスとキャパシティの目標のために必要なコンポーネント数を決定します。Azure でこのアーキテクチャを採用するには、3 つすべてのサーバーで 4 つのコンポーネントのレプリカを作成します。これにより、パフォーマンスとキャパシティに関して必要とされる以上にコンポーネント数が増えます。これは、これら 3 つの仮想マシンが 1 つの可用性セットに割り当てられる場合に、この設計で Azure プラットフォームの 4 つすべてのコンポーネントの高可用性を確保するためのトレードオフとなります。</span><span class="sxs-lookup"><span data-stu-id="f64e0-p130">You determine the number of components by the performance and capacity targets for the farm. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span>
  
<span data-ttu-id="f64e0-263">**図 8: 調整後のアプリケーション サーバー層**</span><span class="sxs-lookup"><span data-stu-id="f64e0-263">**Figure 8: Application server tier after fine tuning**</span></span>

![Microsoft Azure 可用性セットのために調整した後の SharePoint Server 2013 アプリケーション サーバー層の例](../media/AZarch-AppServtierAfter.png)
  
<span data-ttu-id="f64e0-265">この図は、同じ 4 つのコンポーネントを含み、同一に構成されている 3 つのアプリケーション サーバーすべてを示しています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-265">This diagram shows all three application servers configured identically with the same four components.</span></span>
  
<span data-ttu-id="f64e0-266">SharePoint ファームの各層に可用性セットを追加すると、実装作業が完了します。</span><span class="sxs-lookup"><span data-stu-id="f64e0-266">When we add availability sets to the tiers of the SharePoint farm, the implementation is complete.</span></span>
  
<span data-ttu-id="f64e0-267">**図 9:Azure インフラストラクチャ サービスに実装された SharePoint ファーム**</span><span class="sxs-lookup"><span data-stu-id="f64e0-267">**Figure 9: The completed SharePoint farm in Azure infrastructure services**</span></span>

![仮想ネットワーク、クロスプレミス接続、サブネット、VM、および可用性の設定を含む Azure インフラストラクチャ サービスの SharePoint 2013 ファームの例](../media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
<span data-ttu-id="f64e0-269">この図は、Azure インフラストラクチャ サービスに実装された、各層内のサーバー用の障害ドメインを提供する可用性セットを備えた SharePoint ファームを示しています。</span><span class="sxs-lookup"><span data-stu-id="f64e0-269">This diagram shows the SharePoint farm implemented in Azure infrastructure services, with availability sets to provide fault domains for the servers in each tier.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f64e0-270">関連項目</span><span class="sxs-lookup"><span data-stu-id="f64e0-270">See Also</span></span>

[<span data-ttu-id="f64e0-271">Microsoft 365 ソリューションおよびアーキテクチャ センター</span><span class="sxs-lookup"><span data-stu-id="f64e0-271">Microsoft 365 solution and architecture center</span></span>](../solutions/index.yml)
  
[<span data-ttu-id="f64e0-272">SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト</span><span class="sxs-lookup"><span data-stu-id="f64e0-272">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[<span data-ttu-id="f64e0-273">Microsoft Azure での SharePoint Server 2013 の障害復旧</span><span class="sxs-lookup"><span data-stu-id="f64e0-273">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)