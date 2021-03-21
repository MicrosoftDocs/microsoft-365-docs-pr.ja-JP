---
title: 高可用性フェデレーション認証 フェーズ 4 Web アプリケーション プロキシの構成
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: '概要: Microsoft Azure の Microsoft 365 の高可用性フェデレーション認証用に Web アプリケーション プロキシ サーバーを構成します。'
ms.openlocfilehash: 95d73d05f2eef087e606df14db180b24c69d5932
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "50929074"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a><span data-ttu-id="31967-103">高可用性フェデレーション認証のフェーズ 4: Web アプリケーション プロキシを構成する</span><span class="sxs-lookup"><span data-stu-id="31967-103">High availability federated authentication Phase 4: Configure web application proxies</span></span>

<span data-ttu-id="31967-104">Azure インフラストラクチャ サービスで Microsoft 365 フェデレーション認証の高可用性を展開するこのフェーズでは、内部ロード バランサーと 2 台の FS サーバーをADします。</span><span class="sxs-lookup"><span data-stu-id="31967-104">In this phase of deploying high availability for Microsoft 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="31967-105">[フェーズ [5: Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)のフェデレーション認証を構成する] に進む前に、このフェーズを完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31967-105">You must complete this phase before moving on to [Phase 5: Configure federated authentication for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md).</span></span> <span data-ttu-id="31967-106">すべての [フェーズについては、「Azure での Microsoft 365](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) の高可用性フェデレーション認証の展開」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31967-106">See [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a><span data-ttu-id="31967-107">Azure でインターネット接続ロード バランサーを作成する</span><span class="sxs-lookup"><span data-stu-id="31967-107">Create the Internet-facing load balancer in Azure</span></span>

<span data-ttu-id="31967-108">Azure がインターネットからの着信クライアント認証トラフィックを 2 つの Web アプリケーション プロキシ サーバーに均等に分散するように、インターネット接続ロード バランサーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31967-108">You must create an Internet-facing load balancer so that Azure distributes the incoming client authentication traffic from the Internet evenly among the two web application proxy servers.</span></span>
  
> [!NOTE]
> <span data-ttu-id="31967-109">次のコマンド セットは、Azure PowerShell の最新版を使用します。</span><span class="sxs-lookup"><span data-stu-id="31967-109">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="31967-110">「Azure [PowerShell の使用を開始する」を参照してください](/powershell/azure/get-started-azureps)。</span><span class="sxs-lookup"><span data-stu-id="31967-110">See [Get started with Azure PowerShell](/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="31967-111">場所とリソース グループの値を指定したら、その結果のブロックを Azure PowerShell コマンド プロンプトまたは PowerShell ISE で実行します。</span><span class="sxs-lookup"><span data-stu-id="31967-111">When you have supplied location and resource group values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="31967-112">カスタム設定に基づいてすぐに実行できる PowerShell コマンド ブロックを生成するには、この Microsoft Excel 構成ブック [を使用します](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx)。</span><span class="sxs-lookup"><span data-stu-id="31967-112">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx).</span></span> 

```powershell
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="31967-113">インターネット接続ロード バランサーに割り当てられたパブリック IP アドレスを表示するには、ローカル コンピューターの Azure PowerShell コマンド プロンプトで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="31967-113">To display the public IP address assigned to your Internet-facing load balancer, run these commands at the Azure PowerShell command prompt on your local computer:</span></span>
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a><span data-ttu-id="31967-114">フェデレーション サービス FQDN を決定してて、DNS レコードを作成する</span><span class="sxs-lookup"><span data-stu-id="31967-114">Determine your federation service FQDN and create DNS records</span></span>

<span data-ttu-id="31967-115">インターネット上のフェデレーション サービス名を識別するには、DNS 名を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31967-115">You need to determine the DNS name to identify your federation service name on the Internet.</span></span> <span data-ttu-id="31967-116">Azure AD Connect はフェーズ 5 でこの名前で Microsoft 365 を構成します。これは、Microsoft 365 が接続クライアントに送信してセキュリティ トークンを取得するための URL の一部になります。</span><span class="sxs-lookup"><span data-stu-id="31967-116">Azure AD Connect will configure Microsoft 365 with this name in Phase 5, which will become part of the URL that Microsoft 365 sends to connecting clients to get a security token.</span></span> <span data-ttu-id="31967-117">たとえば、fs.contoso.com (fs はフェデレーション サービスを表します)。</span><span class="sxs-lookup"><span data-stu-id="31967-117">An example is fs.contoso.com (fs stands for federation service).</span></span>
  
<span data-ttu-id="31967-118">フェデレーション サービス FDQN を取得後、Azure インターネット接続ロード バランサーのパブリック IP アドレスに解決される、フェデレーション サービス FDQN のパブリック DNS ドメイン A レコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="31967-118">Once you have your federation service FDQN, create a public DNS domain A record for the federation service FDQN that resolves to the public IP address of the Azure Internet-facing load balancer.</span></span>
  
|<span data-ttu-id="31967-119">**名前**</span><span class="sxs-lookup"><span data-stu-id="31967-119">**Name**</span></span>|<span data-ttu-id="31967-120">**Type**</span><span class="sxs-lookup"><span data-stu-id="31967-120">**Type**</span></span>|<span data-ttu-id="31967-121">**TTL**</span><span class="sxs-lookup"><span data-stu-id="31967-121">**TTL**</span></span>|<span data-ttu-id="31967-122">**値**</span><span class="sxs-lookup"><span data-stu-id="31967-122">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="31967-123">フェデレーション サービス FDQN</span><span class="sxs-lookup"><span data-stu-id="31967-123">federation service FDQN</span></span>  <br/> |<span data-ttu-id="31967-124">A</span><span class="sxs-lookup"><span data-stu-id="31967-124">A</span></span>  <br/> |<span data-ttu-id="31967-125">3600</span><span class="sxs-lookup"><span data-stu-id="31967-125">3600</span></span>  <br/> |<span data-ttu-id="31967-126">Azure インターネット接続ロード バランサーのパブリック IP アドレス (前のセクションの **Write-Host** コマンドで表示されます)</span><span class="sxs-lookup"><span data-stu-id="31967-126">public IP address of the Azure Internet-facing load balancer (displayed by the **Write-Host** command in the previous section)</span></span> <br/> |
   
<span data-ttu-id="31967-127">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="31967-127">Here is an example:</span></span>
  
|<span data-ttu-id="31967-128">**名前**</span><span class="sxs-lookup"><span data-stu-id="31967-128">**Name**</span></span>|<span data-ttu-id="31967-129">**Type**</span><span class="sxs-lookup"><span data-stu-id="31967-129">**Type**</span></span>|<span data-ttu-id="31967-130">**TTL**</span><span class="sxs-lookup"><span data-stu-id="31967-130">**TTL**</span></span>|<span data-ttu-id="31967-131">**値**</span><span class="sxs-lookup"><span data-stu-id="31967-131">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="31967-132">fs.contoso.com</span><span class="sxs-lookup"><span data-stu-id="31967-132">fs.contoso.com</span></span>  <br/> |<span data-ttu-id="31967-133">A</span><span class="sxs-lookup"><span data-stu-id="31967-133">A</span></span>  <br/> |<span data-ttu-id="31967-134">3600</span><span class="sxs-lookup"><span data-stu-id="31967-134">3600</span></span>  <br/> |<span data-ttu-id="31967-135">131.107.249.117</span><span class="sxs-lookup"><span data-stu-id="31967-135">131.107.249.117</span></span>  <br/> |
   
<span data-ttu-id="31967-136">次に、フェデレーション サービス FQDN を AD FS サーバーの内部ロード バランサーに割り当てられたプライベート IP アドレスに解決する、組織のプライベート DNS 名前空間に DNS アドレス レコードを追加します (「表 I」、「項目 4」、「値」列)。</span><span class="sxs-lookup"><span data-stu-id="31967-136">Next, add a DNS address record to your organization's private DNS namespace that resolves your federation service FQDN to the private IP address assigned to the internal load balancer for the AD FS servers (Table I, item 4, Value column).</span></span>
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a><span data-ttu-id="31967-137">Azure に Web アプリケーション プロキシ サーバーの仮想マシンを作成する</span><span class="sxs-lookup"><span data-stu-id="31967-137">Create the web application proxy server virtual machines in Azure</span></span>

<span data-ttu-id="31967-138">次に示す Azure PowerShell コマンドのブロックを使用して、2 つの Web アプリケーション プロキシ サーバーの仮想マシンを作成します。 </span><span class="sxs-lookup"><span data-stu-id="31967-138">Use the following block of Azure PowerShell commands to create the virtual machines for the two web application proxy servers.</span></span> 
  
<span data-ttu-id="31967-139">次に示す Azure PowerShell コマンド セットには、次の表の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="31967-139">Note that the following Azure PowerShell command sets use values from the following tables:</span></span>
  
- <span data-ttu-id="31967-140">表 M: 仮想マシン用</span><span class="sxs-lookup"><span data-stu-id="31967-140">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="31967-141">表 R: リソース グループ用</span><span class="sxs-lookup"><span data-stu-id="31967-141">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="31967-142">表 V: 仮想ネットワークの設定用</span><span class="sxs-lookup"><span data-stu-id="31967-142">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="31967-143">表 S: サブネット用</span><span class="sxs-lookup"><span data-stu-id="31967-143">Table S, for your subnets</span></span>
    
- <span data-ttu-id="31967-144">表 I: 静的 IP アドレス用</span><span class="sxs-lookup"><span data-stu-id="31967-144">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="31967-145">表 A: 可用性セット用</span><span class="sxs-lookup"><span data-stu-id="31967-145">Table A, for your availability sets</span></span>
    
<span data-ttu-id="31967-146">フェーズ 2 でテーブル M を定義した [場合:フェーズ 1:](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) Configure Azure でドメイン コントローラーとテーブル R、V、S、I、および A を [構成します](high-availability-federated-authentication-phase-1-configure-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="31967-146">Recall that you defined Table M in [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
<span data-ttu-id="31967-147">適切な値をすべて指定したら、その結果のブロックを Azure PowerShell コマンド プロンプトまたは PowerShell ISE で実行します。</span><span class="sxs-lookup"><span data-stu-id="31967-147">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="31967-p104">これらの仮想マシンはイントラネット アプリケーション向けのため、パブリック IP アドレスや DNS ドメイン名のラベルが割り当てられていません。また、インターネットに公開もされていません。ただし、これは Azure ポータルから接続できないことを意味します。仮想マシンのプロパティを表示したときに、**接続** オプションは使用できない状態になります。リモート デスクトップ接続アクセサリなどのリモート デスクトップ ツールを使用して、仮想マシンのプライベート IP アドレスやイントラネット DNS 名、ローカル管理者アカウントの資格情報で仮想マシンに接続します。</span><span class="sxs-lookup"><span data-stu-id="31967-p104">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="31967-152">次に、このフェーズが正常に完了した結果の構成を示します。コンピューター名にはプレース ホルダーを使用しています。</span><span class="sxs-lookup"><span data-stu-id="31967-152">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="31967-153">**フェーズ 4:Azure での高可用性フェデレーション認証インフラストラクチャ用のインターネット接続ロード バランサーと Web アプリケーション プロキシ サーバー**</span><span class="sxs-lookup"><span data-stu-id="31967-153">**Phase 4: The Internet-facing load balancer and web application proxy servers for your high availability federated authentication infrastructure in Azure**</span></span>

![Azure の高可用性 Microsoft 365 フェデレーション認証インフラストラクチャと Web アプリケーション プロキシ サーバーのフェーズ 4](../media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a><span data-ttu-id="31967-155">次の手順</span><span class="sxs-lookup"><span data-stu-id="31967-155">Next step</span></span>

<span data-ttu-id="31967-156">[ [フェーズ 5: Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) のフェデレーション認証を構成する] を使用して、このワークロードの構成を続行します。</span><span class="sxs-lookup"><span data-stu-id="31967-156">Use [Phase 5: Configure federated authentication for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="31967-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="31967-157">See Also</span></span>

[<span data-ttu-id="31967-158">Azure に Microsoft 365 の高可用性フェデレーション認証を展開する</span><span class="sxs-lookup"><span data-stu-id="31967-158">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[<span data-ttu-id="31967-159">Microsoft 365 開発/テスト環境のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="31967-159">Federated identity for your Microsoft 365 dev/test environment</span></span>](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[<span data-ttu-id="31967-160">Microsoft 365 ソリューションおよびアーキテクチャ センター</span><span class="sxs-lookup"><span data-stu-id="31967-160">Microsoft 365 solution and architecture center</span></span>](../solutions/index.yml)