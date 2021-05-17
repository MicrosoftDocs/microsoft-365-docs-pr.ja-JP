---
title: デバイス検出の構成
description: 基本または標準の検出を使用して Microsoft 365 Defender でデバイスの検出を構成する方法について説明します。
keywords: 基本、標準、エンドポイント検出の構成、デバイスの検出
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
localization_priority: normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 0d722b4f4bef5b4d178edc5f2142c887690d4c63
ms.sourcegitcommit: 7a339c9f7039825d131b39481ddf54c57b021b11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "51765253"
---
# <a name="configure-device-discovery"></a><span data-ttu-id="aa9e1-104">デバイス検出の構成</span><span class="sxs-lookup"><span data-stu-id="aa9e1-104">Configure device discovery</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

<span data-ttu-id="aa9e1-105">**適用対象:**</span><span class="sxs-lookup"><span data-stu-id="aa9e1-105">**Applies to:**</span></span>
- [<span data-ttu-id="aa9e1-106">Microsoft Defender for Endpoint</span><span class="sxs-lookup"><span data-stu-id="aa9e1-106">Microsoft Defender for Endpoint</span></span>](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [<span data-ttu-id="aa9e1-107">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="aa9e1-107">Microsoft 365 Defender</span></span>](https://go.microsoft.com/fwlink/?linkid=2118804)


[!include[Prerelease information](../../includes/prerelease.md)]

<span data-ttu-id="aa9e1-108">検出は、標準モードまたは基本モードで構成できます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-108">Discovery can be configured to be on standard or basic mode.</span></span> <span data-ttu-id="aa9e1-109">標準オプションを使用して、ネットワーク内のデバイスをアクティブに検索し、エンドポイントの検出を保証し、より豊富なデバイス分類を提供します。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-109">Use the standard option to actively find devices in your network, which will better guarantee the discovery of endpoints and provide richer device classification.</span></span> 

<span data-ttu-id="aa9e1-110">標準検出の実行に使用するデバイスの一覧をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-110">You can customize the list of devices that are used to perform standard discovery.</span></span> <span data-ttu-id="aa9e1-111">この機能をサポートしているすべてのオンボード デバイス (現在は Windows 10 デバイスのみ) で標準検出を有効にするか、デバイス タグを指定してデバイスのサブセットまたはサブセットを選択できます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-111">You can either enable standard discovery on all the onboarded devices that also support this capability (currently - Windows 10 devices only) or select a subset or subsets of your devices by specifying their device tags.</span></span> 


> [!IMPORTANT]
> <span data-ttu-id="aa9e1-112">プレビューでは、最初にプレビュー機能をオンにする必要Microsoft Defender セキュリティ センター。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-112">For preview, you'll first need to turn on the Preview features in Microsoft Defender Security Center.</span></span>
> <span data-ttu-id="aa9e1-113">その後、セキュリティ センターでデバイス検出Microsoft 365アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-113">You can then access the device discovery configuration in Microsoft 365 security center.</span></span> <span data-ttu-id="aa9e1-114">管理されていないデバイスとセキュリティに関する推奨事項の一覧は、Microsoft Defender セキュリティ センター セキュリティ センターと Microsoft 365 セキュリティ センターの両方で使用できます。ダッシュボード タイルは Microsoft 365 セキュリティ センターでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-114">The list of unmanaged devices and security recommendations will be available in both Microsoft Defender Security Center and Microsoft 365 security center, while the dashboard tiles will only be available in Microsoft 365 security center.</span></span>


<span data-ttu-id="aa9e1-115">セキュリティ センターで次の構成Microsoft 365実行します。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-115">Take the following configuration steps in Microsoft 365 security center:</span></span>

1.  <span data-ttu-id="aa9e1-116">[デバイスの検出 **設定 >に移動します**。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-116">Navigate to **Settings > Device discovery**.</span></span>
2.  <span data-ttu-id="aa9e1-117">オンボード デバイスで使用する検出モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-117">Select the discovery mode to use on your onboarded devices.</span></span> 
3.  <span data-ttu-id="aa9e1-118">標準検出を使用する場合は、アクティブなプロブに使用するデバイス (すべてのデバイスまたはデバイス タグを指定してサブセット上) を選択します。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-118">If you've selected to use standard discovery, select which devices to use for active probing: all devices or on a subset by specifying their device tags.</span></span>
4. <span data-ttu-id="aa9e1-119">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-119">Click **Save**.</span></span>


## <a name="exclude-devices-from-being-actively-probed-in-standard-discovery"></a><span data-ttu-id="aa9e1-120">デバイスが標準検出でアクティブにプローブされるのを除外する</span><span class="sxs-lookup"><span data-stu-id="aa9e1-120">Exclude devices from being actively probed in standard discovery</span></span>
<span data-ttu-id="aa9e1-121">ネットワーク上にアクティブにスキャンすべきではないデバイス (たとえば、別のセキュリティ ツールでハニーポットとして使用されるデバイス) がある場合は、除外リストを定義してスキャンを防止することもできます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-121">If there are devices on your network which should not be actively scanned (for example, devices used as honeypots for another security tool), you can also define a list of exclusions to prevent them from being scanned.</span></span> <span data-ttu-id="aa9e1-122">デバイスは、基本検出モードを使用して検出できます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-122">Note that devices can still be discovered using Basic discovery mode.</span></span> <span data-ttu-id="aa9e1-123">これらのデバイスは受動的に検出されますが、アクティブにプローブされません。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-123">Those devices will be passively discovered but won't be actively probed.</span></span> 

## <a name="select-networks-to-monitor"></a><span data-ttu-id="aa9e1-124">監視するネットワークの選択</span><span class="sxs-lookup"><span data-stu-id="aa9e1-124">Select networks to monitor</span></span>
 <span data-ttu-id="aa9e1-125">Microsoft Defender for Endpoint は、ネットワークを分析し、監視が必要な企業ネットワークか、無視できる非企業ネットワークかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-125">Microsoft Defender for Endpoint analyzes a network and determines if it is a corporate network that needs to be monitored or a non-corporate network that can be ignored.</span></span> <span data-ttu-id="aa9e1-126">通常、企業ネットワークは監視対象として選択されます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-126">Corporate networks are typically chosen to be monitored.</span></span> <span data-ttu-id="aa9e1-127">ただし、オンボードデバイスが見つかった企業以外のネットワークを監視することで、この決定を上書きできます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-127">However, you can override this decision by choosing to monitor non-corporate networks where onboarded devices are found.</span></span> 

<span data-ttu-id="aa9e1-128">監視するネットワークを指定することで、デバイスの検出を実行できる場所を構成できます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-128">You can configure where device discovery can be performed by specifying which networks to monitor.</span></span> <span data-ttu-id="aa9e1-129">ネットワークを監視すると、デバイス検出をそのネットワークで実行できます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-129">When a network is monitored, device discovery can be performed on it.</span></span> 

<span data-ttu-id="aa9e1-130">デバイス検出を実行できるネットワークの一覧が、[監視対象のネットワーク] **ページに表示** されます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-130">A list of networks where device discovery can be performed is shown in the **Monitored networks** page.</span></span> 


>[!NOTE]
> <span data-ttu-id="aa9e1-131">上位 50 のネットワーク (関連付けられているデバイスの数に応じて) だけがネットワーク リストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-131">Only top 50 networks (according to the number of associated devices) will be available in the network list.</span></span> 


<span data-ttu-id="aa9e1-132">監視対象のネットワークの一覧は、過去 7 日間にネットワークに表示されたデバイスの総数に基づいて並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-132">The list of monitored networks is sorted based upon the total number of devices seen on the network in the last 7 days.</span></span>


<span data-ttu-id="aa9e1-133">フィルターを適用して、次のネットワーク検出状態を表示できます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-133">You can apply a filter to view any of the following network discovery states:</span></span>

- <span data-ttu-id="aa9e1-134">**監視対象のネットワーク** - デバイス検出が実行されるネットワーク。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-134">**Monitored networks** - Networks where device discovery is performed.</span></span>
- <span data-ttu-id="aa9e1-135">**無視されたネットワーク** - このネットワークは無視され、デバイス検出は実行されません。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-135">**Ignored networks** - This network will be ignored and device discovery will not be performed on it.</span></span>
- <span data-ttu-id="aa9e1-136">**All** - 監視対象ネットワークと無視されたネットワークの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-136">**All** - Both monitored and ignored networks will be displayed.</span></span> 


### <a name="configure-the-network-monitor-state"></a><span data-ttu-id="aa9e1-137">ネットワーク モニターの状態を構成する</span><span class="sxs-lookup"><span data-stu-id="aa9e1-137">Configure the network monitor state</span></span>
<span data-ttu-id="aa9e1-138">デバイス検出の実行場所を制御します。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-138">You control where device discovery takes place.</span></span> <span data-ttu-id="aa9e1-139">監視対象のネットワークは、デバイスの検出が実行される場所であり、通常は企業ネットワークです。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-139">Monitored networks is where device discovery will be performed and are typically corporate networks.</span></span> <span data-ttu-id="aa9e1-140">ネットワークを無視するか、状態を変更した後の最初の検出分類を選択するように選択できます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-140">You can also choose to ignore networks or select the initial discovery classification after modifying a state.</span></span> 

<span data-ttu-id="aa9e1-141">最初の検出分類を選択すると、既定のシステムで作成されたネットワーク モニター状態が適用されます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-141">Choosing the initial discovery classification means applying the default system-made network monitor state.</span></span> <span data-ttu-id="aa9e1-142">既定のシステム製のネットワーク モニター状態を選択すると、企業として識別され、監視され、非企業として識別されたネットワークは自動的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-142">Selecting the default system-made network monitor state means that networks that were identified to be corporate, will be monitored, and ones identified as non-corporate, will be ignored automatically.</span></span>
 
1. <span data-ttu-id="aa9e1-143">[デバイス **設定 >] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-143">Select **Settings > Device discovery**.</span></span>
2. <span data-ttu-id="aa9e1-144">[監視 **対象のネットワーク] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-144">Select **Monitored networks**.</span></span> 
3. <span data-ttu-id="aa9e1-145">ネットワークの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-145">View the list of networks.</span></span> 
4. <span data-ttu-id="aa9e1-146">ネットワーク名の横にある 3 つのドットを選択します。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-146">Select the three dots next to the network name.</span></span> 
5. <span data-ttu-id="aa9e1-147">初期検出分類を監視、無視、または使用するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-147">Choose whether you want to monitor, ignore, or use the initial discovery classification.</span></span> 
    
    > [!WARNING]
    >- <span data-ttu-id="aa9e1-148">Microsoft Defender for Endpoint によって企業ネットワークとして識別されていないネットワークを監視すると、企業ネットワークの外部でデバイスの検出が発生し、自宅や他の企業以外のデバイスを検出する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-148">Choosing to monitor a network that was not identified by Microsoft Defender for Endpoint as a corporate network can cause device discovery outside of your corporate network, and may therefore detect home or other non-corporate devices.</span></span> 
    > - <span data-ttu-id="aa9e1-149">ネットワークを無視すると、そのネットワーク内のデバイスの監視と検出が停止します。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-149">Choosing to ignore a network will stop monitoring and discovering devices in that network.</span></span> <span data-ttu-id="aa9e1-150">既に検出されたデバイスはインベントリから削除されませんが、更新されなくなるので、Defender for Endpoint のデータ保持期間が経過するまで詳細が保持されます。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-150">Devices that were already discovered will not be removed from the inventory, but will no longer be updated, and details will be retained until the data retention period of the Defender for Endpoint expires.</span></span>
    > - <span data-ttu-id="aa9e1-151">企業以外のネットワークを監視する前に、その権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-151">Before choosing to monitor non-corporate networks, you must ensure you have permission to do so.</span></span> <br>


6. <span data-ttu-id="aa9e1-152">変更を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa9e1-152">Confirm that you want to make the change.</span></span> 




## <a name="see-also"></a><span data-ttu-id="aa9e1-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa9e1-153">See also</span></span>
- [<span data-ttu-id="aa9e1-154">デバイス検出の概要</span><span class="sxs-lookup"><span data-stu-id="aa9e1-154">Device discovery overview</span></span>](device-discovery.md)
- [<span data-ttu-id="aa9e1-155">デバイスの検出に関するよくある質問</span><span class="sxs-lookup"><span data-stu-id="aa9e1-155">Device discovery FAQs</span></span>](device-discovery-faq.md)