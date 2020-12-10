---
title: メンバーがグループに代わって送信または送信できるようにする
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 0ad41414-0cc6-4b97-90fb-06bec7bcf590
description: メンバーが Microsoft 365 グループとしてメールを送信できるようにする方法、または Microsoft 365 グループの代理としてメールを送信できるようにする方法について説明します。
ms.openlocfilehash: 2abf0668411ccd08db5bbd8408605dcd0aa2d832
ms.sourcegitcommit: a0cddd1f888edb940717e434cda2dbe62e5e9475
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2020
ms.locfileid: "49613574"
---
# <a name="allow-members-to-send-as-or-send-on-behalf-of-a-group"></a><span data-ttu-id="c6e22-103">メンバーがグループに代わって送信または送信できるようにする</span><span class="sxs-lookup"><span data-stu-id="c6e22-103">Allow members to send as or send on behalf of a group</span></span>

<span data-ttu-id="c6e22-104">送信者または **代理人\*\*\*\*と** して送信するアクセス許可が付与されている Microsoft 365 グループのメンバーは、グループとして、またはグループの代わりにメールを送信できます。</span><span class="sxs-lookup"><span data-stu-id="c6e22-104">A member of a Microsoft 365 group who has been granted **Send as** or **Send on behalf** permissions can send email as the group, or on behalf of the group.</span></span> <span data-ttu-id="c6e22-105">この記事では、管理者がこれらのアクセス許可を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6e22-105">This article explains how an admin can set these permissions.</span></span>
  
<span data-ttu-id="c6e22-106">たとえば、Megan Bowen が **トレーニング** の Microsoft 365 グループに含まれていて、グループに対して **送信** 者アクセス許可を持っている場合、グループとして電子メールを送信すると、その電子メールを送信した **トレーニング** グループのように表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6e22-106">For example, if Megan Bowen is part of the **Training** Microsoft 365 group, and has **Send as** permissions on the group, if she sends an email as the group, it will look like the **Training** group sent the email.</span></span> 
  
<span data-ttu-id="c6e22-107">**[代理人として送信** する] アクセス許可を使用すると、ユーザーは Microsoft 365 グループに代わって電子メールを送信できます。</span><span class="sxs-lookup"><span data-stu-id="c6e22-107">The **Send on Behalf** permission lets a user send email on behalf of a Microsoft 365 group.</span></span> <span data-ttu-id="c6e22-108">たとえば、Alex が **marketing** Microsoft 365 グループの一部であり、 **代理送信** アクセス許可を持ち、グループとして電子メールを送信する場合、電子メールは **Alex がマーケティングの代理** として送信されたように見えます。</span><span class="sxs-lookup"><span data-stu-id="c6e22-108">For example, if Alex Wilber is a part of the **Marketing** Microsoft 365 group, and has **Send on Behalf** permissions and sends an email as the group, the email looks like it was sent by **Alex Wilber on behalf of Marketing**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e22-109">特定のユーザーに対し **て [送信** ] または **[代理送信** ] を構成できますが、両方を構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="c6e22-109">You can configure **Send as** or **Send on behalf** for a given user, but not both.</span></span> <span data-ttu-id="c6e22-110">両方を構成した場合、既定では **として送信** されます。</span><span class="sxs-lookup"><span data-stu-id="c6e22-110">If you configure both, it will default to **Send as**.</span></span>

> [!TIP]
> <span data-ttu-id="c6e22-111">Outlook および Outlook on the Web を使用してグループから電子メールを送信する方法について [は、「Microsoft 365 グループの代理](https://support.microsoft.com/office/0f4964af-aec6-484b-a65c-0434df8cdb6b) としてメールを送信する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6e22-111">See [Send email from or on behalf of a Microsoft 365 group](https://support.microsoft.com/office/0f4964af-aec6-484b-a65c-0434df8cdb6b) to learn how to use Outlook and Outlook on the Web to send email from a group.</span></span>
    
## <a name="allow-members-to-send-email-as-a-group"></a><span data-ttu-id="c6e22-112">メンバーがグループとしてメールを送信できるようにする</span><span class="sxs-lookup"><span data-stu-id="c6e22-112">Allow members to send email as a group</span></span>

<span data-ttu-id="c6e22-113">このセクションでは、exchange Online の [exchange 管理センター](https://go.microsoft.com/fwlink/p/?linkid=2059104) (EAC) でユーザーがグループとしてメールを送信できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6e22-113">This section explains how to allow users to send email as a group in the [Exchange admin center](https://go.microsoft.com/fwlink/p/?linkid=2059104) (EAC) in Exchange Online.</span></span>
  
1. <span data-ttu-id="c6e22-114"><a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange 管理センター</a> で、[**受信者**]、[**グループ**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="c6e22-114">In the <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange admin center</a>, go to **Recipients** \> **Groups**.</span></span>
    
2. <span data-ttu-id="c6e22-115"> ![ ](../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) ユーザーが送信者として送信できるようにするグループの [編集グループの編集] アイコンを選択します。  </span><span class="sxs-lookup"><span data-stu-id="c6e22-115">Select **Edit**  ![Edit group icon](../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) on the group that you want to allow users to send as.</span></span> 
    
3. <span data-ttu-id="c6e22-116">[ **グループ委任**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="c6e22-116">Select **group delegation**.</span></span>
    
4. <span data-ttu-id="c6e22-117">[ **送信** ] セクションで、 **+** グループとして送信するユーザーを追加するための署名を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6e22-117">In the **Send As** section, select the **+** sign to add the users that you want to send as the Group.</span></span> 
    
    ![[送信] ダイアログボックスのスクリーンショット](../media/1df167f6-1eff-4f98-9ecd-4230fab46557.png)
  
5. <span data-ttu-id="c6e22-119">ユーザーを入力して検索するか、一覧からユーザーを選択します。</span><span class="sxs-lookup"><span data-stu-id="c6e22-119">Type to search or pick a user from the list.</span></span> <span data-ttu-id="c6e22-120">[ **OK]** を選択して、 **保存** します。</span><span class="sxs-lookup"><span data-stu-id="c6e22-120">Select **OK** and **Save**.</span></span>
    
    ![リストからユーザーを検索または選択するには、「」と入力します。](../media/522919cf-664c-4a25-8076-c51c8c9fbe43.png)
  
## <a name="allow-members-to-send-email-on-behalf-of-a-group"></a><span data-ttu-id="c6e22-122">メンバーがグループに代わって電子メールを送信することを許可する</span><span class="sxs-lookup"><span data-stu-id="c6e22-122">Allow members to send email on behalf of a group</span></span>

<span data-ttu-id="c6e22-123">このセクションでは、exchange Online の Exchange 管理センター (EAC) で、ユーザーがグループに代わって電子メールを送信できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6e22-123">This section explains how to allow users to send email on behalf of a group in the Exchange admin center (EAC) in Exchange Online.</span></span>
  
1. <span data-ttu-id="c6e22-124"><a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange 管理センター</a> で、[**受信者**]、[**グループ**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="c6e22-124">In the <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange admin center</a>, go to **Recipients** \> **Groups**.</span></span>
    
2. <span data-ttu-id="c6e22-125"> ![ ](../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) ユーザーが送信者として送信できるようにするグループの [編集グループの編集] アイコンを選択します。</span><span class="sxs-lookup"><span data-stu-id="c6e22-125">Select **Edit** ![Edit group icon](../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) on the group that you want to allow users to send as.</span></span> 
    
3. <span data-ttu-id="c6e22-126">[ **グループ委任**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="c6e22-126">Select **group delegation**.</span></span>
    
4. <span data-ttu-id="c6e22-127">[代理人として送信する] セクションで、 **+** グループとして送信するユーザーを追加するための署名を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6e22-127">In the Send on Behalf section, select the **+** sign to add the users that you want to send as the Group.</span></span> 
    
    ![[代理送信] ダイアログのスクリーンショット](../media/2bae0579-8907-4d6b-8920-ddd6555897b4.png)
  
5. <span data-ttu-id="c6e22-129">ユーザーを入力して検索するか、一覧からユーザーを選択します。</span><span class="sxs-lookup"><span data-stu-id="c6e22-129">Type to search or pick a user from the list.</span></span> <span data-ttu-id="c6e22-130">[ **OK]** を選択して、 **保存** します。</span><span class="sxs-lookup"><span data-stu-id="c6e22-130">Select **OK** and **Save**.</span></span>
    
    ![リストからユーザーを検索または選択するには、「」と入力します。](../media/522919cf-664c-4a25-8076-c51c8c9fbe43.png)

## <a name="related-articles"></a><span data-ttu-id="c6e22-132">関連記事</span><span class="sxs-lookup"><span data-stu-id="c6e22-132">Related articles</span></span>

[<span data-ttu-id="c6e22-133">コラボレーションガバナンスの計画のステップバイステップ</span><span class="sxs-lookup"><span data-stu-id="c6e22-133">Collaboration governance planning step-by-step</span></span>](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[<span data-ttu-id="c6e22-134">コラボレーションのガバナンス計画を作成する</span><span class="sxs-lookup"><span data-stu-id="c6e22-134">Create your collaboration governance plan</span></span>](collaboration-governance-first.md)

[<span data-ttu-id="c6e22-135">Microsoft 365 グループの詳細情報</span><span class="sxs-lookup"><span data-stu-id="c6e22-135">Learn more about Microsoft 365 groups</span></span>](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

<span data-ttu-id="c6e22-136">[[受信者の追加] アクセス許可](https://go.microsoft.com/fwlink/p/?LinkId=723960)</span><span class="sxs-lookup"><span data-stu-id="c6e22-136">[Add-RecipientPermission](https://go.microsoft.com/fwlink/p/?LinkId=723960)</span></span>

[<span data-ttu-id="c6e22-137">Set-UnifiedGroup</span><span class="sxs-lookup"><span data-stu-id="c6e22-137">Set-UnifiedGroup</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=616189)
