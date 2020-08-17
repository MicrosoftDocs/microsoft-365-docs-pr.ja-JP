---
title: マイクロソフトのクラウド プランのサブスクリプション、ライセンス、アカウント、およびテナント
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/25/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
ms.custom:
- seo-marvel-apr2020
- Ent_Architecture
description: Microsoft のクラウドプランの組織、サブスクリプション、ライセンス、ユーザー アカウント、およびテナントの関係について理解する。
ms.openlocfilehash: 7b19c2d6a870f53642d37ee98276f7b6a9e1febf
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46691739"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a><span data-ttu-id="aff6b-103">マイクロソフトのクラウド プランのサブスクリプション、ライセンス、アカウント、およびテナント</span><span class="sxs-lookup"><span data-stu-id="aff6b-103">Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings</span></span>

<span data-ttu-id="aff6b-104">Microsoft は、クラウド プラン全体で ID の使用と課金の一貫性を維持するために、組織、サブスクリプション、ライセンス、ユーザー アカウントなどの階層を提供しています。</span><span class="sxs-lookup"><span data-stu-id="aff6b-104">Microsoft provides a hierarchy of organizations, subscriptions, licenses, and user accounts for consistent use of identities and billing across its cloud offerings:</span></span>
  
- <span data-ttu-id="aff6b-105">Microsoft 365 および Microsoft Office 365</span><span class="sxs-lookup"><span data-stu-id="aff6b-105">Microsoft 365 and Microsoft Office 365</span></span>
- <span data-ttu-id="aff6b-106">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="aff6b-106">Microsoft Azure</span></span>
- <span data-ttu-id="aff6b-107">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="aff6b-107">Microsoft Dynamics 365</span></span>

## <a name="elements-of-the-hierarchy"></a><span data-ttu-id="aff6b-108">階層の要素</span><span class="sxs-lookup"><span data-stu-id="aff6b-108">Elements of the hierarchy</span></span>

<span data-ttu-id="aff6b-109">階層の要素を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="aff6b-109">Here are the elements of the hierarchy:</span></span>
  
### <a name="organization"></a><span data-ttu-id="aff6b-110">組織</span><span class="sxs-lookup"><span data-stu-id="aff6b-110">Organization</span></span>

<span data-ttu-id="aff6b-p101">組織は、Microsoft クラウド製品を使用しているビジネス エンティティを表します。通常は、1 つ以上のパブリック ドメイン ネーム システム (DNS) のドメイン名 (例: contoso.com) で識別されます。組織は、サブスクリプションのコンテナーになります。</span><span class="sxs-lookup"><span data-stu-id="aff6b-p101">An organization represents a business entity that is using Microsoft cloud offerings, typically identified by one or more public Domain Name System (DNS) domain names, such as contoso.com. The organization is a container for subscriptions.</span></span>
  
### <a name="subscriptions"></a><span data-ttu-id="aff6b-113">サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="aff6b-113">Subscriptions</span></span>

<span data-ttu-id="aff6b-114">サブスクリプションとは、1 つ以上の Microsoft クラウドのプラットフォームやサービスを使用するための Microsoft との契約のことです。この契約では、ユーザー単位のライセンス料またはクラウドベースのリソース消費量に基づいて請求されます。</span><span class="sxs-lookup"><span data-stu-id="aff6b-114">A subscription is an agreement with Microsoft to use one or more Microsoft cloud platforms or services, for which charges accrue based on either a per-user license fee or on cloud-based resource consumption.</span></span> 

- <span data-ttu-id="aff6b-115">サービス (SaaS) ベースのクラウドプラン (Office 365および Dynamics 365)としてのMicrosoft ソフトウェアは、ユーザーごとにライセンス料金を請求します。</span><span class="sxs-lookup"><span data-stu-id="aff6b-115">Microsoft's Software as a Service (SaaS)-based cloud offerings (Microsoft 365 and Dynamics 365) charge per-user license fees.</span></span> 
- <span data-ttu-id="aff6b-116">Microsoft のサービスとしてのプラットフォーム (PaaS) およびサービスとしてのインフラストラクチャ (IaaS) のクラウド サービス (Azure) では、クラウド リソースの消費量に基づいて請求されます。</span><span class="sxs-lookup"><span data-stu-id="aff6b-116">Microsoft's Platform as a Service (PaaS) and Infrastructure as a Service (IaaS) cloud offerings (Azure) charge based on cloud resource consumption.</span></span>
 
<span data-ttu-id="aff6b-p102">試用版サブスクリプションを使用することもできます。ただし、このサブスクリプションは、特定の期間を過ぎるか、特定の消費料金を超えると失効します。試用版サブスクリプションは、有料サブスクリプションに変更できます。</span><span class="sxs-lookup"><span data-stu-id="aff6b-p102">You can also use a trial subscription, but the subscription expires after a specific amount of time or consumption charges. You can convert a trial subscription to a paid subscription.</span></span>
  
<span data-ttu-id="aff6b-119">組織は、Microsoft のクラウド商品の複数のサブスクリプションを所有できます。</span><span class="sxs-lookup"><span data-stu-id="aff6b-119">Organizations can have multiple subscriptions for Microsoft's cloud offerings.</span></span> <span data-ttu-id="aff6b-120">図 1 は、複数の Microsoft 365 サブスクリプション、1 つの Dynamics 365 サブスクリプション、複数の Azure サブスクリプションを持つ 1 つの組織を示しています。</span><span class="sxs-lookup"><span data-stu-id="aff6b-120">Figure 1 shows a single organization that has multiple Microsoft 365 subscriptions, a Dynamics 365 subscription, and multiple Azure subscriptions.</span></span>

<span data-ttu-id="aff6b-121">**図 1: 1 つの組織に複数のサブスクリプションの例**</span><span class="sxs-lookup"><span data-stu-id="aff6b-121">**Figure 1: Example of multiple subscriptions for an organization**</span></span>

![Microsoft のクラウド プランの複数のサブスクリプションのある組織の例。](../media/Subscriptions/Subscriptions-Fig1.png)
  
### <a name="licenses"></a><span data-ttu-id="aff6b-123">ライセンス</span><span class="sxs-lookup"><span data-stu-id="aff6b-123">Licenses</span></span>

<span data-ttu-id="aff6b-124">Microsoft の SaaS クラウド商品の場合、1 つのライセンスで、1 つの特定のユーザー アカウントがクラウド商品のサービスを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="aff6b-124">For Microsoft's SaaS cloud offerings, a license allows a specific user account to use the services of the cloud offering.</span></span> <span data-ttu-id="aff6b-125">サブスクリプションの一環として、月間の固定料金が課金されます。</span><span class="sxs-lookup"><span data-stu-id="aff6b-125">You are charged a fixed monthly fee as part of your subscription.</span></span> <span data-ttu-id="aff6b-126">管理者は、サブスクリプション内で個別のユーザー アカウントにライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="aff6b-126">Administrators assign licenses to individual user accounts in the subscription.</span></span> <span data-ttu-id="aff6b-127">図 2 の例では、Contoso Corporation が 100 ライセンスの Microsoft 365 E5 サブスクリプションを所有しています。このサブスクリプションにより、最大 100 件の個別のユーザー アカウントが Microsoft 365 E5 の機能とサービスを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="aff6b-127">For the example in Figure 2, the Contoso Corporation has a Microsoft 365 E5 subscription with 100 licenses, which allows to up to 100 individual user accounts to use Microsoft 365 E5 features and services.</span></span>
  
<span data-ttu-id="aff6b-128">**図 2:1 つの組織の SaaS ベースのサブスクリプションに含まれるライセンス**</span><span class="sxs-lookup"><span data-stu-id="aff6b-128">**Figure 2: Licenses within the SaaS-based subscriptions for an organization**</span></span>

![Microsoft の SaaS ベース クラウド プランのサブスクリプション内の複数ライセンスの例。](../media/Subscriptions/Subscriptions-Fig2.png)
  
<span data-ttu-id="aff6b-130">Azure PaaS ベースのクラウド サービスの場合、サービス料金にソフトウェア ライセンスが組み込まれています。  </span><span class="sxs-lookup"><span data-stu-id="aff6b-130">For Azure PaaS-based cloud services, software licenses are built into the service pricing.</span></span>
  
<span data-ttu-id="aff6b-p105">Azure IaaS ベースの仮想マシン場合、仮想マシン イメージにインストールしたソフトウェアまたはアプリケーションを使用するために、追加ライセンスが必要になることがあります。一部の仮想マシン イメージにはライセンス付きバージョンのソフトウェアがインストールされていて、サーバーに対する分単位の料金が費用に含まれます。その例として、SQL Server 2014 および SQL Server 2016 の仮想マシン イメージが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="aff6b-p105">For Azure IaaS-based virtual machines, additional licenses to use the software or application installed on a virtual machine image might be required. Some virtual machine images have licensed versions of software installed and the cost is included in the per-minute rate for the server. Examples are the virtual machine images for SQL Server 2014 and SQL Server 2016.</span></span> 
  
<span data-ttu-id="aff6b-p106">一部の仮想マシン イメージには、アプリケーションの試用版がインストールされていて、試用期間の経過後も使用する場合は追加のソフトウェア アプリケーション ライセンスが必要になります。たとえば、SharePoint Server 2016 試用版仮想マシン イメージには、プレインストールされた試用版の SharePoint Server 2016 が含まれています。試用期間後に SharePoint Server 2016 の使用を続けるには、SharePoint Server 2016 のライセンスとクライアントのライセンスを Microsoft から購入する必要があります。こうした課金は Azure サブスクリプションとは別であり、仮想マシンを実行する分単位の料金がそのまま適用されます。</span><span class="sxs-lookup"><span data-stu-id="aff6b-p106">Some virtual machine images have trial versions of applications installed and need additional software application licenses for use beyond the trial period. For example, the SharePoint Server 2016 Trial virtual machine image includes a trial version of SharePoint Server 2016 pre-installed. To continue using SharePoint Server 2016 after the trial expiration date, you must purchase a SharePoint Server 2016 license and client licenses from Microsoft. These charges are separate from the Azure subscription and the per-minute rate to run the virtual machine still applies.</span></span>
  
### <a name="user-accounts"></a><span data-ttu-id="aff6b-138">ユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="aff6b-138">User accounts</span></span>

<span data-ttu-id="aff6b-139">すべての Microsoft のクラウド商品のユーザー アカウントは、Azure Active Directory (Azure AD) テナントに保存されます。これには、ユーザー アカウントとグループが含まれます。</span><span class="sxs-lookup"><span data-stu-id="aff6b-139">User accounts for all of Microsoft's cloud offerings are stored in an Azure Active Directory (Azure AD) tenant, which contains user accounts and groups.</span></span> <span data-ttu-id="aff6b-140">Azure AD テナントは、Windows サーバーベースのサービスである Azure AD Connect を使用して、既存の Active Directory Domain Services (AD DS) アカウントと同期できます。</span><span class="sxs-lookup"><span data-stu-id="aff6b-140">An Azure AD tenant can be synchronized with your existing Active Directory Domain Services (AD DS) accounts using Azure AD Connect, a Windows server-based service.</span></span> <span data-ttu-id="aff6b-141">これはディレクトリ同期と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="aff6b-141">This is known as directory synchronization.</span></span>
  
<span data-ttu-id="aff6b-142">図 3 は、共通の Azure AD テナントを使用する組織の複数サブスクリプションの例を示しています。このテナントに組織のアカウントが格納されています。</span><span class="sxs-lookup"><span data-stu-id="aff6b-142">Figure 3 shows an example of multiple subscriptions of an organization using a common Azure AD tenant that contains the organization's accounts.</span></span>
  
<span data-ttu-id="aff6b-143">**図 3:同じ Azure AD テナントを使用する組織の複数のサブスクリプション**</span><span class="sxs-lookup"><span data-stu-id="aff6b-143">**Figure 3: Multiple subscriptions of an organization that use the same Azure AD tenant**</span></span>

![すべてのサブスクリプションが同じ Azure AD テナントを使用する、複数のサブスクリプションのある組織の例。](../media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a><span data-ttu-id="aff6b-145">テナント</span><span class="sxs-lookup"><span data-stu-id="aff6b-145">Tenants</span></span>

<span data-ttu-id="aff6b-146">SaaS クラウド商品の場合、テナントとはクラウド サービスを提供しているサーバーが収容された地域の場所のことです。</span><span class="sxs-lookup"><span data-stu-id="aff6b-146">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services.</span></span> <span data-ttu-id="aff6b-147">たとえば、Contoso Corporation は、パリ本社の 15,000 人の従業員用の Office 365、EMS、および Dynamics 365 テナントのホストに欧州地域を選択しています。</span><span class="sxs-lookup"><span data-stu-id="aff6b-147">For example, the Contoso Corporation chose the European region to host its Microsoft 365, EMS, and Dynamics 365 tenants for the 15,000 workers in their Paris headquarters.</span></span>
  
<span data-ttu-id="aff6b-p109">Azure PaaS サービスと、Azure IaaS でホストされる仮想マシン ベースのワークロードは、世界中の Azure データセンターのテナントを持つことができます。場所と呼ばれる Azure データセンターは、Azure PaaS のアプリやサービスまたは IaaS ワークロードの要素を作成するときに、ユーザーが指定します。</span><span class="sxs-lookup"><span data-stu-id="aff6b-p109">Azure PaaS services and virtual machine-based workloads hosted in Azure IaaS can have tenancy in any Azure datacenter across the world. You specify the Azure datacenter, known as the location, when you create the Azure PaaS app or service or element of an IaaS workload.</span></span>
  
<span data-ttu-id="aff6b-150">Azure AD テナントは、アカウントおよびグループを含む Azure AD の特定のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="aff6b-150">An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span> <span data-ttu-id="aff6b-151">Microsoft 365 または Dynamics 365 の有料または試用版サブスクリプションには、無料の Azure AD テナントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="aff6b-151">Paid or trial subscriptions of Microsoft 365 or Dynamics 365 include a free Azure AD tenant.</span></span> <span data-ttu-id="aff6b-152">この Azure AD テナントには、その他の Azure サービスは含まれていません。これは、Azure の試用版または有料のサブスクリプションと同じものではありません。</span><span class="sxs-lookup"><span data-stu-id="aff6b-152">This Azure AD tenant does not include other Azure services and is not the same as an Azure trial or paid subscription.</span></span>
  
### <a name="summary-of-the-hierarchy"></a><span data-ttu-id="aff6b-153">階層の概要</span><span class="sxs-lookup"><span data-stu-id="aff6b-153">Summary of the hierarchy</span></span>

<span data-ttu-id="aff6b-154">ここに、簡単なまとめを示します。</span><span class="sxs-lookup"><span data-stu-id="aff6b-154">Here is a quick recap:</span></span>
  
- <span data-ttu-id="aff6b-155">1 つの組織には複数のサブスクリプションを含めることができる</span><span class="sxs-lookup"><span data-stu-id="aff6b-155">An organization can have multiple subscriptions</span></span>
    
  - <span data-ttu-id="aff6b-156">1 つのサブスクリプションには複数のライセンスを含めることができる</span><span class="sxs-lookup"><span data-stu-id="aff6b-156">A subscription can have multiple licenses</span></span>
    
  - <span data-ttu-id="aff6b-157">ライセンスは個別のユーザー アカウントに割り当てできる</span><span class="sxs-lookup"><span data-stu-id="aff6b-157">Licenses can be assigned to individual user accounts</span></span>
    
  - <span data-ttu-id="aff6b-158">ユーザー アカウントは Azure AD テナントに保存できる</span><span class="sxs-lookup"><span data-stu-id="aff6b-158">User accounts are stored in an Azure AD tenant</span></span>
    
<span data-ttu-id="aff6b-159">組織、サブスクリプション、ライセンス、ユーザー アカウントの関係の例を示します。</span><span class="sxs-lookup"><span data-stu-id="aff6b-159">Here is an example of the relationship of organizations, subscriptions, licenses, and user accounts:</span></span>
  
- <span data-ttu-id="aff6b-160">パブリック ドメイン名によって識別される組織。</span><span class="sxs-lookup"><span data-stu-id="aff6b-160">An organization identified by its public domain name.</span></span>
    
  - <span data-ttu-id="aff6b-161">ユーザーライセンスのある Microsoft 365 E3 サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="aff6b-161">A Microsoft 365 E3 subscription with user licenses.</span></span>
    
    <span data-ttu-id="aff6b-162">ユーザーライセンスのある Microsoft 365 E5 サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="aff6b-162">A Microsoft 365 E5 subscription with user licenses.</span></span>
    
    <span data-ttu-id="aff6b-163">ユーザー ライセンスがある Dynamics 365 サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="aff6b-163">A Dynamics 365 subscription with user licenses.</span></span>
    
    <span data-ttu-id="aff6b-164">複数の Azure サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="aff6b-164">Multiple Azure subscriptions.</span></span>
    
  - <span data-ttu-id="aff6b-165">共通の Azure AD テナントにある組織のユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="aff6b-165">The organization's user accounts in a common Azure AD tenant.</span></span>
    
<span data-ttu-id="aff6b-166">複数の Microsoft クラウド商品のサブスクリプションは、同じ Azure AD テナントを使用できます。このテナントは、共通の ID プロバイダーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="aff6b-166">Multiple Microsoft cloud offering subscriptions can use the same Azure AD tenant that acts as a common identity provider.</span></span> <span data-ttu-id="aff6b-167">オンプレミスの AD DS の同期されたユーザー アカウントを収容しているセントラル Azure AD テナントを使用することで、組織にサービス (IDaaS) としてのクラウドベース ID が提供されます。</span><span class="sxs-lookup"><span data-stu-id="aff6b-167">A central Azure AD tenant that contains the synchronized accounts of your on-premises AD DS provides cloud-based Identity as a Service (IDaaS) for your organization.</span></span> 
  
<span data-ttu-id="aff6b-168">**図 4: 同期されたオンプレミスのアカウントと組織の IDaaS**</span><span class="sxs-lookup"><span data-stu-id="aff6b-168">**Figure 4: Synchronized on-premises accounts and IDaaS for an organization**</span></span>

![組織のサービスとしての ID (IaaS) IDaaS。](../media/Subscriptions/Subscriptions-Fig4.png)
  
<span data-ttu-id="aff6b-p112">図 4 は、Microsoft の SaaS クラウド プラン、Azure PaaS アプリ、Azure AD Domain Services を使用する Azure IaaS の仮想マシンにより、共通の Azure AD テナントがどのように使用されるかを示します。Azure AD Connect は、オンプレミスの AD DS フォレストを Azure AD テナントと同期します。</span><span class="sxs-lookup"><span data-stu-id="aff6b-p112">Figure 4 shows how a common Azure AD tenant is used by Microsoft's SaaS cloud offerings, Azure PaaS apps, and virtual machines in Azure IaaS that use Azure AD Domain Services. Azure AD Connect synchronizes the on-premises AD DS forest with the Azure AD tenant.</span></span>
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a><span data-ttu-id="aff6b-172">複数の Microsoft クラウド プランのサブスクリプションの組み合わせ</span><span class="sxs-lookup"><span data-stu-id="aff6b-172">Combining subscriptions for multiple Microsoft cloud offerings</span></span>

<span data-ttu-id="aff6b-173">次の表では、既に所有している 1 つの種類のクラウド商品のサブスクリプション (最初の列に列挙したラベル) と、追加する別の種類のクラウド商品のサブスクリプション (列間を横切る) に基づいた、複数の Microsoft クラウド商品の可能な組み合わせ方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="aff6b-173">The following table describes how you can combine multiple Microsoft cloud offerings based on already having a subscription for one type of cloud offering (the labels going down the first column) and adding a subscription for a different cloud offering (going across the columns).</span></span>
  
||<span data-ttu-id="aff6b-174">**Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="aff6b-174">**Microsoft 365**</span></span>|<span data-ttu-id="aff6b-175">**Azure**</span><span class="sxs-lookup"><span data-stu-id="aff6b-175">**Azure**</span></span>|<span data-ttu-id="aff6b-176">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="aff6b-176">**Dynamics 365**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="aff6b-177">**Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="aff6b-177">**Microsoft 365**</span></span> <br/> |<span data-ttu-id="aff6b-178">該当なし</span><span class="sxs-lookup"><span data-stu-id="aff6b-178">NA</span></span>  <br/> |<span data-ttu-id="aff6b-179">Azure ポータルから Azure のサブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="aff6b-179">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="aff6b-180">Microsoft 365 管理センターから Dynamics 365 のサブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="aff6b-180">You add a Dynamics 365 subscription to your organization from the Microsoft 365 admin center.</span></span>  <br/> |
|<span data-ttu-id="aff6b-181">**Azure**</span><span class="sxs-lookup"><span data-stu-id="aff6b-181">**Azure**</span></span> <br/> |<span data-ttu-id="aff6b-182">Microsoft 365 サブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="aff6b-182">You add a Microsoft 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="aff6b-183">該当なし</span><span class="sxs-lookup"><span data-stu-id="aff6b-183">NA</span></span>  <br/> |<span data-ttu-id="aff6b-184">Dynamics 365 サブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="aff6b-184">You add a Dynamics 365 subscription to your organization.</span></span>  <br/> |
|<span data-ttu-id="aff6b-185">**Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="aff6b-185">**Dynamics 365**</span></span> <br/> |<span data-ttu-id="aff6b-186">Microsoft 365 サブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="aff6b-186">You add a Microsoft 365 subscription to your organization.</span></span>  <br/> |<span data-ttu-id="aff6b-187">Azure ポータルから Azure のサブスクリプションを組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="aff6b-187">You add an Azure subscription to your organization from the Azure portal.</span></span>  <br/> |<span data-ttu-id="aff6b-188">該当なし</span><span class="sxs-lookup"><span data-stu-id="aff6b-188">NA</span></span>  <br/> |
   
<span data-ttu-id="aff6b-189">Microsoft SaaS ベース サービスの場合は、管理センターを使用すると、組織にサブスクリプションを簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="aff6b-189">An easy way to add subscriptions to your organization for Microsoft SaaS-based services is through the admin center:</span></span>
  
1. <span data-ttu-id="aff6b-190">全体管理者アカウントを使用して、Microsoft 365 管理センター ([https://admin.microsoft.com](https://admin.microsoft.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="aff6b-190">Sign in to the Microsoft 365 admin center ([https://admin.microsoft.com](https://admin.microsoft.com)) with your global administrator account.</span></span>
    
2. <span data-ttu-id="aff6b-191">**管理センター**のホームページ左側にあるナビゲーションで、**[課金]**、**[サービスを購入する]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="aff6b-191">From the left navigation of the **Admin center** home page, click **Billing**, and then **Purchase services**.</span></span>
    
3. <span data-ttu-id="aff6b-192">**[サービスを購入する]** ページで、新しいサブスクリプションを購入します。</span><span class="sxs-lookup"><span data-stu-id="aff6b-192">On the **Purchase services** page, purchase your new subscriptions.</span></span>
    
<span data-ttu-id="aff6b-193">管理センターは、Microsoft 365 サブスクリプションの組織と Azure AD テナントを SaaS ベースのクラウドプランの新しいサブスクリプションに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="aff6b-193">The admin center assigns the organization and Azure AD tenant of your Microsoft 365 subscription to the new subscriptions for SaaS-based cloud offerings.</span></span>
  
<span data-ttu-id="aff6b-194">Microsoft 365 サブスクリプションと同じ組織および Azure AD テナントの Azure サブスクリプションを追加する方法</span><span class="sxs-lookup"><span data-stu-id="aff6b-194">To add an Azure subscription with the same organization and Azure AD tenant as your Microsoft 365 subscription:</span></span>
  
1. <span data-ttu-id="aff6b-195">Microsoft 365 全体管理者アカウントを使用して、Azureポータル ([https://portal.azure.com](https://portal.azure.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="aff6b-195">Sign in to the Azure portal ([https://portal.azure.com](https://portal.azure.com)) with your Microsoft 365 global administrator account.</span></span>
    
2. <span data-ttu-id="aff6b-196">左側のナビゲーションで、**[サブスクリプション]**、**[追加]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="aff6b-196">In the left navigation, click **Subscriptions**, and then click **Add**.</span></span>
    
3. <span data-ttu-id="aff6b-197">**[サブスクリプションの追加]** ページでプランを選択し、支払情報を記入して契約します。</span><span class="sxs-lookup"><span data-stu-id="aff6b-197">On the **Add subscription** page, select an offer and complete the payment information and agreement.</span></span>
    
<span data-ttu-id="aff6b-198">Azure と Microsoft 365 のサブスクリプションを個別に購入済みで、Azure サブスクリプションから Microsoft 365 の Azure AD テナントへのアクセスを希望する場合は、「[既存の Azure サブスクリプションを Azure Active Directory テナントに追加する](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory)」の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aff6b-198">If you purchased Azure and Microsoft 365 subscriptions separately and want to access the Microsoft 365 Azure AD tenant from your Azure subscription, see the instructions in [Add an existing Azure subscription to your Azure Active Directory tenant](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).</span></span>
 
## <a name="see-also"></a><span data-ttu-id="aff6b-199">関連項目</span><span class="sxs-lookup"><span data-stu-id="aff6b-199">See also</span></span>

[<span data-ttu-id="aff6b-200">エンタープライズ アーキテクト向け Microsoft クラウドのイラスト</span><span class="sxs-lookup"><span data-stu-id="aff6b-200">Microsoft cloud for enterprise architects illustrations</span></span>](../solutions/cloud-architecture-models.md)
  
[<span data-ttu-id="aff6b-201">SharePoint、Exchange、Skype for Business、Lync のアーキテクチャ モデル</span><span class="sxs-lookup"><span data-stu-id="aff6b-201">Architectural models for SharePoint, Exchange, Skype for Business, and Lync</span></span>](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[<span data-ttu-id="aff6b-202">ハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="aff6b-202">Hybrid solutions</span></span>](hybrid-solutions.md)

## <a name="next-step"></a><span data-ttu-id="aff6b-203">次の手順</span><span class="sxs-lookup"><span data-stu-id="aff6b-203">Next step</span></span>

[<span data-ttu-id="aff6b-204">Microsoft 365 ネットワーク接続の評価</span><span class="sxs-lookup"><span data-stu-id="aff6b-204">Assessing Microsoft 365 network connectivity</span></span>](assessing-network-connectivity.md)
  