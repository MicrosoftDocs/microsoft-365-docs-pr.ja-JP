---
title: Microsoft 365 サービス正常性を確認する方法
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: サポートを呼び出す前に Microsoft 365 サービスの正常性の状態を表示して、アクティブなサービスが中断していないかどうかを確認します。
ms.openlocfilehash: 49f7d3afd3c19cd4e9b6486db580082fe933b997
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46692147"
---
# <a name="how-to-check-microsoft-365-service-health"></a><span data-ttu-id="77618-103">Microsoft 365 サービス正常性を確認する方法</span><span class="sxs-lookup"><span data-stu-id="77618-103">How to check Microsoft 365 service health</span></span>

<span data-ttu-id="77618-104">[![管理センターについて知らせるラベルが変更されていますので、詳細については、aka.ms/aboutM365preview を参照してください。](../media/O365-Admin-AdminCenterChanging.png)](https://docs.microsoft.com/office365/admin/microsoft-365-admin-center-preview?view=o365-worldwide)</span><span class="sxs-lookup"><span data-stu-id="77618-104">[![Label to let you know the admin center is changing and you can find more details at aka.ms/aboutM365preview.](../media/O365-Admin-AdminCenterChanging.png)](https://docs.microsoft.com/office365/admin/microsoft-365-admin-center-preview?view=o365-worldwide)</span></span>

<span data-ttu-id="77618-105">Microsoft サービスの正常性 (web 上の Office、Yammer、Microsoft Dynamics CRM、およびモバイルデバイス管理クラウドサービス) は、 [microsoft 365 管理センター](https://go.microsoft.com/fwlink/p/?linkid=2024339)の [**サービス正常性**] ページで確認できます。</span><span class="sxs-lookup"><span data-stu-id="77618-105">You can view the health of your Microsoft services, including Office on the web, Yammer, Microsoft Dynamics CRM, and mobile device management cloud services, on the **Service health** page in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).</span></span> <span data-ttu-id="77618-106">クラウド サービスの問題が発生している場合は、サポートに連絡するかトラブルシューティングに時間を費やす前に、サービス正常性を確認することで、解決に向けて取り組み中の既知の問題であるかどうかを判別できます。</span><span class="sxs-lookup"><span data-stu-id="77618-106">If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span>

<span data-ttu-id="77618-107">サービス ポータルにサインインできない場合は、[[サービスの状態] ページ](https://status.office365.com)を使用して、テナントへのログインを妨げている既知の問題を確認できます。</span><span class="sxs-lookup"><span data-stu-id="77618-107">If you are unable to sign in to the service portal, you can use the [service status page](https://status.office365.com) to check for known issues preventing you from logging into your tenant.</span></span>
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="77618-108">サービス正常性の確認方法</span><span class="sxs-lookup"><span data-stu-id="77618-108">How to check service health</span></span>

1. <span data-ttu-id="77618-109">Microsoft 365 管理センターに移動し、 [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339) 管理者アカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="77618-109">Go to the Microsoft 365 admin center at [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339), and sign in with an admin account.</span></span>

    > [!NOTE]
    > <span data-ttu-id="77618-110">全体管理者またはサービス管理者の役割を割り当てられているユーザーは、サービス正常性を表示できます。</span><span class="sxs-lookup"><span data-stu-id="77618-110">People who are assigned the global admin or service administrator role can view service health.</span></span> <span data-ttu-id="77618-111">Exchange、SharePoint、および Skype for Business の管理者がサービス正常性を表示できるようにする場合も、ユーザーにはサービス管理者の役割が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="77618-111">To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span> <span data-ttu-id="77618-112">サービス正常性を表示できる役割の詳細については、「[管理者の役割について](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide#roles-available-in-the-microsoft-365-admin-center)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77618-112">For more information about roles that can view service health, see [About admin roles](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide#roles-available-in-the-microsoft-365-admin-center).</span></span>
  
2. <span data-ttu-id="77618-113">新しい管理センターを使用していない場合は、 **ホーム** ページで、右上隅にある [ **新しい管理センターの** 切り替えを試みる] を選択します。</span><span class="sxs-lookup"><span data-stu-id="77618-113">If you are not using the new admin center, on the **Home** page, select the **Try the new admin center** toggle in the upper-right corner.</span></span>

3. <span data-ttu-id="77618-114">サービス正常性を開くには、管理センターで [**正常性**]  >  [**サービス正常性**] の順に移動するか、[**ホーム ダッシュボード**] の [**サービス正常性**] カードを選択します。</span><span class="sxs-lookup"><span data-stu-id="77618-114">To view service health, in the admin center, go to **Health** > **Service health**, or select the **Service health** card on the **Home dashboard**.</span></span> <span data-ttu-id="77618-115">[ダッシュボード] カードでは、アクティブなサービスの問題があるかどうかが示され、詳細な [**サービス正常性**] ページへのリンクが提供されます。</span><span class="sxs-lookup"><span data-stu-id="77618-115">The dashboard card indicates whether there is an active service issue and links to the detailed **Service health** page.</span></span>
  
4. <span data-ttu-id="77618-116">[**サービス正常性**] ページでは、それぞれのクラウド サービスの正常性の状態は表形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="77618-116">On the **Service health** page, the health state of each cloud service is shown in a table format.</span></span>

   ![サービス正常性の現在の問題のビュー](../media/service-health-all-services.png)

<span data-ttu-id="77618-118">[**すべてのサービス**] タブ (既定のビュー) に、すべてのサービスとその現在の正常性の状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="77618-118">The **All services** tab (the default view) shows all services and their current health state.</span></span> <span data-ttu-id="77618-119">アイコンと [**状態**] 列は、各サービスの状態を示しています。</span><span class="sxs-lookup"><span data-stu-id="77618-119">An icon and the **Status** column indicate the state of each service.</span></span> 

<span data-ttu-id="77618-120">ビューをフィルタリングして、現在インシデントが発生しているサービスに絞り込むには、ページ上部の [**インシデント**] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="77618-120">To filter your view to services currently experiencing an incident, select the **Incidents** tab at the top of the page.</span></span> <span data-ttu-id="77618-121">[**勧告**] タブを選択すると、現在、勧告が投稿されているサービスのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="77618-121">Selecting the **Advisories** tab will show only services that currently have an advisory posted.</span></span> 

<span data-ttu-id="77618-122">[**履歴**] タブには、解決されたインシデントおよび勧告の履歴が表示されます。</span><span class="sxs-lookup"><span data-stu-id="77618-122">The **History** tab shows the history of incidents and advisories that have been resolved.</span></span>

<span data-ttu-id="77618-123">Microsoft 365 サービスで問題が発生し、[ **サービス正常性** ] ページに表示されていない場合は、[ **問題を報告**する] を選択して、省略形を完了します。</span><span class="sxs-lookup"><span data-stu-id="77618-123">If you're experiencing an issue with a Microsoft 365 service and you don’t see it listed on the **Service health** page, tell us about it by selecting **Report an issue**, and completing the short form.</span></span> <span data-ttu-id="77618-124">他の組織からの関連データとレポートを調べて、問題がどの程度広がっているか、およびそれがサービスに起因しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="77618-124">We’ll look at related data and reports from other organizations to see how widespread the issue is, and if it originated with our service.</span></span> <span data-ttu-id="77618-125">該当する場合、[**サービス正常性**] ページに新しいインシデントまたは勧告として追加し、その解決を追跡できます。</span><span class="sxs-lookup"><span data-stu-id="77618-125">If it did, we’ll add it as a new incident or advisory on the **Service health** page, where you can track its resolution.</span></span> <span data-ttu-id="77618-126">約 30 分以内に一覧に表示されない場合は、問題を解決するためにサポートに連絡することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="77618-126">If you don’t see it appear on the list within about 30 minutes, consider contacting support to resolve the issue.</span></span>

<span data-ttu-id="77618-127">アクティブなインシデントのテナントと状態の変更に影響を与える新しいインシデントの電子メール通知にサインアップするには、[ **ユーザー設定**] を選択し、[ **メールでサービス**の正常性通知を送信する] をクリックして、次の情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="77618-127">To sign up for email notifications of new incidents that affect your tenant and status changes for an active incident, select **Preferences**, click **Send me service heath notifications in email**, and then specify:</span></span>

- <span data-ttu-id="77618-128">最大2つの電子メールアドレス。</span><span class="sxs-lookup"><span data-stu-id="77618-128">Up to two email addresses.</span></span>
- <span data-ttu-id="77618-129">インシデントまたはアドバイザリの通知が必要かどうか</span><span class="sxs-lookup"><span data-stu-id="77618-129">Whether you want notifications for incidents or advisories</span></span>
- <span data-ttu-id="77618-130">通知を必要とするサービス</span><span class="sxs-lookup"><span data-stu-id="77618-130">The services for which you want notification</span></span>

> [!NOTE]
> <span data-ttu-id="77618-131">各管理者は、それぞれの設定を行うことができ、上記の2つの電子メールアドレスは管理者アカウントごとに制限されます。</span><span class="sxs-lookup"><span data-stu-id="77618-131">Each admin can have their Preferences set and the above limit of two email address is per admin account.</span></span>

> [!TIP]
> <span data-ttu-id="77618-132">また、モバイルデバイスで [Microsoft 365 Admin アプリケーション](https://go.microsoft.com/fwlink/p/?linkid=627216) を使用して、サービスの正常性を確認することもできます。これは、プッシュ通知を最新の状態に保つための最適な方法です。</span><span class="sxs-lookup"><span data-stu-id="77618-132">You can also use the [Microsoft 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="77618-133">投稿されたサービス正常性の詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="77618-133">View details of posted service health</span></span>

<span data-ttu-id="77618-134">[**すべてのサービス**] ビューで、[サービスの状態] を選択すると、勧告またはインシデントの概要ビューが開きます。</span><span class="sxs-lookup"><span data-stu-id="77618-134">On the **All services** view, selecting the service status will open a summary view of advisories or incidents.</span></span>
  
![サービスの勧告を表示するスクリーンショット](../media/service-health-advisory.png)

<span data-ttu-id="77618-136">勧告またはインシデントの概要では、以下の情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="77618-136">The advisory or incident summary provides the following information:</span></span>

- <span data-ttu-id="77618-137">**タイトル** - 問題の概要。</span><span class="sxs-lookup"><span data-stu-id="77618-137">**Title** - A summary of the problem.</span></span>
- <span data-ttu-id="77618-138">**サービス** - 影響を受けるサービスの名前。</span><span class="sxs-lookup"><span data-stu-id="77618-138">**Service** - The name of the affected service.</span></span>
- <span data-ttu-id="77618-139">**ID** - 問題の数値識別子。</span><span class="sxs-lookup"><span data-stu-id="77618-139">**ID** - A numeric identifier for the problem.</span></span>
- <span data-ttu-id="77618-140">**状態** - この問題がサービスに与える影響。</span><span class="sxs-lookup"><span data-stu-id="77618-140">**Status** - How this problem affects the service.</span></span>
- <span data-ttu-id="77618-141">**開始時刻** - 問題が始まった時刻。</span><span class="sxs-lookup"><span data-stu-id="77618-141">**Start time** - The time when the issue started.</span></span>
- <span data-ttu-id="77618-142">**最終更新時刻** - サービス正常性メッセージの最後の更新時刻。</span><span class="sxs-lookup"><span data-stu-id="77618-142">**Last updated** - The last time that the service health message was updated.</span></span> <span data-ttu-id="77618-143">頻繁にメッセージを投稿して、解決策の適用についての進捗状況をお知らせします。</span><span class="sxs-lookup"><span data-stu-id="77618-143">We post frequent messages to let you know the progress that we're making in applying a solution.</span></span>

<span data-ttu-id="77618-144">問題のタイトルを選択すると、[問題の詳細] ページが表示されます。このページには、解決策の取り組み中に投稿されるすべてのメッセージの[履歴](#history)を含む、問題の詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="77618-144">Select the issue title to see the issue detail page, which shows more information about the issue, including the [history](#history) of all messages posted while we work on a solution.</span></span>

![[問題の詳細] を表示するスクリーンショット](../media/service-health-advisory-detail.png)

### <a name="translate-service-health-details"></a><span data-ttu-id="77618-146">サービス正常性の詳細を翻訳する</span><span class="sxs-lookup"><span data-stu-id="77618-146">Translate service health details</span></span>

<span data-ttu-id="77618-p108">サービス正常性の説明はリアルタイムで投稿されるため、各国語に自動的には翻訳されず、サービス イベントの詳細は英語のみとなります。説明を翻訳するには、次の手順に従います</span><span class="sxs-lookup"><span data-stu-id="77618-p108">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="77618-149">1.[翻訳ツール](https://www.bing.com/translator/)に移動します。</span><span class="sxs-lookup"><span data-stu-id="77618-149">Go to [Translator](https://www.bing.com/translator/).</span></span>

2. <span data-ttu-id="77618-p109">[**サービス正常性**] ページで、インシデントまたは勧告を選択します。[**詳細の表示**] で、問題に関するテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="77618-p109">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>

3. <span data-ttu-id="77618-152">翻訳ツールで、テキストを貼り付けて、[**翻訳**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="77618-152">In Translator, paste the text and choose **Translate**.</span></span>

### <a name="definitions"></a><span data-ttu-id="77618-153">定義</span><span class="sxs-lookup"><span data-stu-id="77618-153">Definitions</span></span>

<span data-ttu-id="77618-154">ほとんどの場合、サービスは正常として表示され、それ以上の情報は示されません。</span><span class="sxs-lookup"><span data-stu-id="77618-154">Most of the time, services will appear as healthy with no further information.</span></span> <span data-ttu-id="77618-155">サービスに問題がある場合、問題は勧告またはインシデントとして認識され、現在の状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="77618-155">When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="77618-156">計画済みメンテナンス イベントはサービス正常性には表示されません。</span><span class="sxs-lookup"><span data-stu-id="77618-156">Planned maintenance events aren't shown in service health.</span></span> <span data-ttu-id="77618-157">常に **メッセージ センター**を確認することで、計画済みメンテナンス イベントを追跡できます。</span><span class="sxs-lookup"><span data-stu-id="77618-157">You can track planned maintenance events by staying up to date with the **Message center**.</span></span> <span data-ttu-id="77618-158">フィルタリングして [変更の計画] として分類されたメッセージに絞り込み、変更が発生する時期、その影響、およびそのための準備方法を確認します。</span><span class="sxs-lookup"><span data-stu-id="77618-158">Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it.</span></span> <span data-ttu-id="77618-159">詳細については [、「Microsoft 365 のメッセージセンター](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77618-159">See [Message center in Microsoft 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span>
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="77618-160">インシデントおよび勧告</span><span class="sxs-lookup"><span data-stu-id="77618-160">Incidents and advisories</span></span>

| <span data-ttu-id="77618-161">アイコン</span><span class="sxs-lookup"><span data-stu-id="77618-161">Icon</span></span> | <span data-ttu-id="77618-162">説明</span><span class="sxs-lookup"><span data-stu-id="77618-162">Description</span></span> |
|:-----|:-----|
|![勧告の情報アイコン](../media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="77618-p112">サービスが勧告と示された場合、一部のユーザーに影響する問題が認識されています。ただし、サービスは引き続き使用可能です。勧告では、多くの場合、回避策があり、問題は一時的なものである可能性があるか、または範囲およびユーザーへの影響は限られます。</span><span class="sxs-lookup"><span data-stu-id="77618-p112">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![インシデントの感嘆符アイコン](../media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="77618-p113">サービスがアクティブ インシデントと示された場合、重大な問題であり、サービスまたはサービスの主な機能は使用できません。たとえば、ユーザーはメールの送受信やサインインができない可能性があります。インシデントはユーザーに顕著な影響を与えます。進行中にインシデントが発生した場合は、サービス正常性ダッシュボードで調査、軽減への取り組み、解決策の確認に関する更新プログラムを提供します。</span><span class="sxs-lookup"><span data-stu-id="77618-p113">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |

### <a name="status-definitions"></a><span data-ttu-id="77618-171">状態の定義</span><span class="sxs-lookup"><span data-stu-id="77618-171">Status definitions</span></span>

| <span data-ttu-id="77618-172">状態</span><span class="sxs-lookup"><span data-stu-id="77618-172">Status</span></span> | <span data-ttu-id="77618-173">定義</span><span class="sxs-lookup"><span data-stu-id="77618-173">Definition</span></span> |
|:-----|:-----|
|<span data-ttu-id="77618-174">**調査中**</span><span class="sxs-lookup"><span data-stu-id="77618-174">**Investigating**</span></span> | <span data-ttu-id="77618-175">潜在的な問題は認識されており、現状と影響範囲に関する詳細情報を収集中です。</span><span class="sxs-lookup"><span data-stu-id="77618-175">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span> |
|<span data-ttu-id="77618-176">**サービスの低下**</span><span class="sxs-lookup"><span data-stu-id="77618-176">**Service degradation**</span></span> | <span data-ttu-id="77618-p114">サービスまたは機能の使用に影響する可能性のある問題があることが確認されています。サービスの実行に通常より長い時間がかかる場合、一時的に中断している場合、機能が動作していない場合などにこの状態が示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="77618-p114">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span> |
|<span data-ttu-id="77618-179">**サービスの中断**</span><span class="sxs-lookup"><span data-stu-id="77618-179">**Service interruption**</span></span> | <span data-ttu-id="77618-p115">問題がサービスへのアクセスを妨げると判断された場合にこの状態が示されます。この場合、問題は重要なものであり、常に再現できます。</span><span class="sxs-lookup"><span data-stu-id="77618-p115">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span> |
|<span data-ttu-id="77618-182">**サービスの復元**</span><span class="sxs-lookup"><span data-stu-id="77618-182">**Restoring service**</span></span> | <span data-ttu-id="77618-183">問題の原因は特定されており、対応策はわかっています。また、サービスを正常な状態に戻している段階です。</span><span class="sxs-lookup"><span data-stu-id="77618-183">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span> |
|<span data-ttu-id="77618-184">**拡張復旧**</span><span class="sxs-lookup"><span data-stu-id="77618-184">**Extended recovery**</span></span> | <span data-ttu-id="77618-p116">この状態は、ほとんどのユーザーに対するサービスを復元するための対応策が進行中ですが、影響を受けるすべてのシステムに適用されるまでは時間がかかることを示します。また、永続的な修正プログラムが適用されるのを待機する間に、一時的な修正プログラムで影響を減らした場合、この状態が表示されることもあります。</span><span class="sxs-lookup"><span data-stu-id="77618-p116">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span> |
|<span data-ttu-id="77618-187">**調査の中断**</span><span class="sxs-lookup"><span data-stu-id="77618-187">**Investigation suspended**</span></span> | <span data-ttu-id="77618-p117">潜在的な問題の詳細な調査で、さらに調査できるようにお客様からの追加情報を要求する場合は、この状態が示されます。お客様にアクションを求める場合は、必要なデータまたはログをお知らせします。</span><span class="sxs-lookup"><span data-stu-id="77618-p117">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span> |
|<span data-ttu-id="77618-190">**サービスが復元されました**</span><span class="sxs-lookup"><span data-stu-id="77618-190">**Service restored**</span></span> | <span data-ttu-id="77618-p118">対応策によって根本的な問題が解決され、サービスが正常な状態に復元されたことが確認されています。原因を確認するには、問題の詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="77618-p118">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span> |
|<span data-ttu-id="77618-193">**誤検知**</span><span class="sxs-lookup"><span data-stu-id="77618-193">**False positive**</span></span> | <span data-ttu-id="77618-194">詳細な調査の結果、サービスが正常であり、設計どおりに動作していることを確認しました。</span><span class="sxs-lookup"><span data-stu-id="77618-194">After a detailed investigation, we’ve confirmed the service is healthy and operating as designed.</span></span> <span data-ttu-id="77618-195">サービスへの影響が観察されなかったか、インシデントの原因がサービス外に起因するものでした。</span><span class="sxs-lookup"><span data-stu-id="77618-195">No impact to the service was observed or the cause of the incident originated outside of the service.</span></span> |
|<span data-ttu-id="77618-196">**インシデントの事後レポートを発行済み**</span><span class="sxs-lookup"><span data-stu-id="77618-196">**Post-incident report published**</span></span> | <span data-ttu-id="77618-197">根本原因情報および同様の問題が再発しないようにするための次の手順を含む特定の問題についてのインシデントの事後レポートを発行しました。</span><span class="sxs-lookup"><span data-stu-id="77618-197">We’ve published a Post Incident Report for a specific issue that includes root cause information and next steps to ensure a similar issue doesn’t reoccur.</span></span> |

### <a name="history"></a><span data-ttu-id="77618-198">履歴</span><span class="sxs-lookup"><span data-stu-id="77618-198">History</span></span>

<span data-ttu-id="77618-199">サービス正常性では現在の正常性の状態を確認し、過去 30 日間のサービスの勧告およびテナントに影響を与えたインシデントの履歴を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="77618-199">Service health lets you look at current health status and view the history of any service advisories and incidents that have affected your tenant in the past 30 days.</span></span> <span data-ttu-id="77618-200">すべてのサービスの過去の正常性を表示するには、[問題の詳細] ページで [**履歴の表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="77618-200">To view the past health of all services, select **View history** on the issue detail page.</span></span>
  
![正常性の履歴へのリンクの表示](../media/service-health-view-history.png)
  
<span data-ttu-id="77618-202">選択した期間に投稿されたすべての正常性メッセージのリストは、以下のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="77618-202">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![サービス正常性の履歴の表示](../media/service-health-history.png)
  
<span data-ttu-id="77618-204">問題の詳細を表示するには、いずれかの行を展開します。</span><span class="sxs-lookup"><span data-stu-id="77618-204">Expand any row to view more details about the issue.</span></span>
  
<span data-ttu-id="77618-205">稼働時間に対するコミットメントの詳細については、「 [Microsoft 365 からの透過的な運用](https://go.microsoft.com/fwlink/?linkid=848695)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77618-205">For more information about our commitment to uptime, see [Transparent operations from Microsoft 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>

## <a name="related-topics"></a><span data-ttu-id="77618-206">関連項目</span><span class="sxs-lookup"><span data-stu-id="77618-206">Related topics</span></span>

<span data-ttu-id="77618-207">[Microsoft 365 管理センター](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263) 
 のアクティビティレポート[メッセージセンターの設定](https://docs.microsoft.com/microsoft-365/admin/manage/message-center?view=o365-worldwide#preferences11)</span><span class="sxs-lookup"><span data-stu-id="77618-207">[Activity Reports in the Microsoft 365 admin center](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)
[Message center Preferences](https://docs.microsoft.com/microsoft-365/admin/manage/message-center?view=o365-worldwide#preferences11)</span></span>