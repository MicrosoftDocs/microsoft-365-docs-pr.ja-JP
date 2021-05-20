---
title: 削除された Microsoft 365 グループを復元する
ms.reviewer: arvaradh
f1.keywords: CSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b7c66b59-657a-4e1a-8aa0-8163b1f4eb54
description: 削除されたグループは 30 日間保持され、グループを復元できます。 30 日後、グループとそのコンテンツは完全に削除されます。
ms.openlocfilehash: 285796ec45b1e6d77d46d7a0c39706f566bb8cf6
ms.sourcegitcommit: 9541d5e6720a06327dc785e3ad7e8fb11246fd72
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2021
ms.locfileid: "52582682"
---
# <a name="restore-a-deleted-microsoft-365-group"></a><span data-ttu-id="9327f-104">削除された Microsoft 365 グループを復元する</span><span class="sxs-lookup"><span data-stu-id="9327f-104">Restore a deleted Microsoft 365 group</span></span>

<span data-ttu-id="9327f-105">グループを削除した場合、既定では 30 日間保持されます。</span><span class="sxs-lookup"><span data-stu-id="9327f-105">If you've deleted a group, it will be retained for 30 days by default.</span></span> <span data-ttu-id="9327f-106">この 30 日間の期間は、グループを復元することができますので、"soft-delete" と見なされます。</span><span class="sxs-lookup"><span data-stu-id="9327f-106">This 30-day period is considered a "soft-delete" because you can still restore the group.</span></span> <span data-ttu-id="9327f-107">30 日後、グループとその関連コンテンツは完全に削除され、復元できません。</span><span class="sxs-lookup"><span data-stu-id="9327f-107">After 30 days, the group and its associated contents are permanently deleted and cannot be restored.</span></span>

<span data-ttu-id="9327f-108">グループを復元すると、次のコンテンツが復元されます。</span><span class="sxs-lookup"><span data-stu-id="9327f-108">When a group is restored, the following content is restored:</span></span>
  
- <span data-ttu-id="9327f-109">Azure Active Directory (AD) Microsoft 365 Groups オブジェクト、プロパティ、およびメンバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="9327f-109">Azure Active Directory (AD) Microsoft 365 Groups object, properties, and members.</span></span>
    
- <span data-ttu-id="9327f-110">グループの電子メール アドレス。</span><span class="sxs-lookup"><span data-stu-id="9327f-110">Group's e-mail addresses.</span></span>
    
- <span data-ttu-id="9327f-111">Exchange Online受信トレイと予定表を共有します。</span><span class="sxs-lookup"><span data-stu-id="9327f-111">Exchange Online shared Inbox and calendar.</span></span>
    
- <span data-ttu-id="9327f-112">SharePointオンライン チーム サイトとファイル。</span><span class="sxs-lookup"><span data-stu-id="9327f-112">SharePoint Online team site and files.</span></span>
    
- <span data-ttu-id="9327f-113">OneNote ノートブック</span><span class="sxs-lookup"><span data-stu-id="9327f-113">OneNote notebook</span></span>
    
- <span data-ttu-id="9327f-114">Planner</span><span class="sxs-lookup"><span data-stu-id="9327f-114">Planner</span></span>
    
- <span data-ttu-id="9327f-115">Teams</span><span class="sxs-lookup"><span data-stu-id="9327f-115">Teams</span></span>

- <span data-ttu-id="9327f-116">Yammerグループとグループ のコンテンツ (Microsoft 365グループがグループから作成されたYammer)</span><span class="sxs-lookup"><span data-stu-id="9327f-116">Yammer group and group content (If the Microsoft 365 group was created from Yammer)</span></span>

> [!NOTE]
> <span data-ttu-id="9327f-117">この記事では、グループの復元Microsoft 365説明します。</span><span class="sxs-lookup"><span data-stu-id="9327f-117">This article describes restoring only Microsoft 365 groups.</span></span> <span data-ttu-id="9327f-118">他のすべてのグループは、一度削除すると復元できません。</span><span class="sxs-lookup"><span data-stu-id="9327f-118">All other groups cannot be restored once deleted.</span></span>

## <a name="restore-a-group"></a><span data-ttu-id="9327f-119">グループの復元</span><span class="sxs-lookup"><span data-stu-id="9327f-119">Restore a group</span></span>

# <a name="outlook"></a>[<span data-ttu-id="9327f-120">Outlook</span><span class="sxs-lookup"><span data-stu-id="9327f-120">Outlook</span></span>](#tab/outlook)

<span data-ttu-id="9327f-121">ユーザーがグループグループの所有者Microsoft 365、次の手順に従って、Outlookでグループを復元できます。</span><span class="sxs-lookup"><span data-stu-id="9327f-121">If you are the owner of a Microsoft 365 group, you can restore the group yourself in Outlook on the web by following these steps:</span></span>

1. <span data-ttu-id="9327f-122">[削除された [グループ] ページで、[](https://outlook.office.com/people/group/deleted)グループ] ノードの **[** グループの管理] オプションを選択し、[削除済み]**を選択します**。</span><span class="sxs-lookup"><span data-stu-id="9327f-122">On the [deleted groups page](https://outlook.office.com/people/group/deleted), select the **Manage groups** option under the **Groups** node, and then choose **Deleted**.</span></span>

2. <span data-ttu-id="9327f-123">復元するグループ **の** 横にある [復元] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9327f-123">Click on the **Restore** tab next to the group you want to restore.</span></span>

<span data-ttu-id="9327f-124">削除されたグループがここに表示されない場合は、管理者に問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="9327f-124">If the deleted group doesn't appear here, contact an administrator.</span></span>

# <a name="admin-center"></a>[<span data-ttu-id="9327f-125">管理センター</span><span class="sxs-lookup"><span data-stu-id="9327f-125">Admin center</span></span>](#tab/admin-center)

<span data-ttu-id="9327f-126">グローバル管理者またはグループ管理者の場合は、管理センターで削除されたグループMicrosoft 365できます。</span><span class="sxs-lookup"><span data-stu-id="9327f-126">If you are a global administrator or a groups administrator, you can restore a deleted group in the Microsoft 365 admin center:</span></span>

1. <span data-ttu-id="9327f-127">[管理センター](https://admin.microsoft.com)にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9327f-127">Go to the [admin center](https://admin.microsoft.com).</span></span>
2. <span data-ttu-id="9327f-128">[グループ **] を展開** し、[削除済 **みグループ] をクリックします**。</span><span class="sxs-lookup"><span data-stu-id="9327f-128">Expand **Groups**, and then click **Deleted groups**.</span></span>
3. <span data-ttu-id="9327f-129">復元するグループを選択し、[グループの復元] **をクリックします**。</span><span class="sxs-lookup"><span data-stu-id="9327f-129">Select the group that you want to restore, and then click **Restore group**.</span></span>

> [!NOTE]
> <span data-ttu-id="9327f-130">場合によっては、グループとそのすべてのデータが復元に 24 時間かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9327f-130">In some cases, it may take as long as 24 hours for the group and all of its data to be restored.</span></span> 

---

## <a name="got-questions-about-microsoft-365-groups"></a><span data-ttu-id="9327f-131">グループに関する質問Microsoft 365しましたか?</span><span class="sxs-lookup"><span data-stu-id="9327f-131">Got questions about Microsoft 365 Groups?</span></span>

<span data-ttu-id="9327f-132">質問を[投稿し、Community](https://techcommunity.microsoft.com/t5/Office-365-Groups/ct-p/Office365Groups)グループに関する会話に参加するには、Microsoft Tech Microsoft 365をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9327f-132">Visit the [Microsoft Tech Community](https://techcommunity.microsoft.com/t5/Office-365-Groups/ct-p/Office365Groups) to post questions and participate in conversations about Microsoft 365 groups.</span></span> 
  
## <a name="related-content"></a><span data-ttu-id="9327f-133">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="9327f-133">Related content</span></span>

<span data-ttu-id="9327f-134">[PowerShell Microsoft 365グループの管理](../../enterprise/manage-microsoft-365-groups-with-powershell.md)(記事)</span><span class="sxs-lookup"><span data-stu-id="9327f-134">[Manage Microsoft 365 Groups with PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md) (article)</span></span>
  
<span data-ttu-id="9327f-135">[Remove-UnifiedGroupコマンドレットを使用してグループを](/powershell/module/exchange/remove-unifiedgroup) 削除する (記事)</span><span class="sxs-lookup"><span data-stu-id="9327f-135">[Delete groups using the Remove-UnifiedGroup cmdlet](/powershell/module/exchange/remove-unifiedgroup) (article)</span></span>
  
<span data-ttu-id="9327f-136">[グループに接続されたチーム サイトの設定を管理する](https://support.microsoft.com/office/8376034d-d0c7-446e-9178-6ab51c58df42) (記事)</span><span class="sxs-lookup"><span data-stu-id="9327f-136">[Manage your group-connected team site settings](https://support.microsoft.com/office/8376034d-d0c7-446e-9178-6ab51c58df42) (article)</span></span>
  
<span data-ttu-id="9327f-137">[グループを削除する (Outlook)](https://support.microsoft.com/office/ca7f5a9e-ae4f-4cbe-a4bc-89c469d1726f)</span><span class="sxs-lookup"><span data-stu-id="9327f-137">[Delete a group in Outlook](https://support.microsoft.com/office/ca7f5a9e-ae4f-4cbe-a4bc-89c469d1726f) (article)</span></span>