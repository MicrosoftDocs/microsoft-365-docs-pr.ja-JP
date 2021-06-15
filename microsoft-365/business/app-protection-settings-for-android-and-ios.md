---
title: Android または iOS デバイスのアプリ保護設定を設定する
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: 6f2b80b4-81c3-4714-a7bc-ae69313e8a33
description: アプリ管理ポリシーを作成、編集、または削除し、Android デバイスまたは iOS デバイス上の作業ファイルを保護する方法について説明します。
ms.openlocfilehash: 92dce1e8761e53b85df85f2a84f30ab307f63e6d
ms.sourcegitcommit: be929f79751c0c52dfa6bd98a854432a0c63faf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2021
ms.locfileid: "52925065"
---
# <a name="set-app-protection-settings-for-android-or-ios-devices"></a><span data-ttu-id="2cc6f-103">Android または iOS デバイスのアプリ保護設定を設定する</span><span class="sxs-lookup"><span data-stu-id="2cc6f-103">Set app protection settings for Android or iOS devices</span></span>

<span data-ttu-id="2cc6f-104">この記事は、このMicrosoft 365 Business Premium。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-104">This article applies to Microsoft 365 Business Premium.</span></span>

## <a name="create-an-app-management-policy"></a><span data-ttu-id="2cc6f-105">アプリの管理ポリシーを作成する</span><span class="sxs-lookup"><span data-stu-id="2cc6f-105">Create an app management policy</span></span>

1. <span data-ttu-id="2cc6f-106"><a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a> から管理センターにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-106">Go to the admin center at <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.</span></span> 
    
2. <span data-ttu-id="2cc6f-107">左側のナビゲーションで、[デバイス ポリシー **の** \> **追加] を** \> **選択します**。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-107">In the left nav, choose **Devices** \> **Policies** \> **Add**.</span></span>
  
3. <span data-ttu-id="2cc6f-108">[ **ポリシーの追加**] ウィンドウで、このポリシーの一意の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-108">On the **Add policy** pane, enter a unique name for this policy.</span></span> 
    
4. <span data-ttu-id="2cc6f-109">[ **ポリシーの種類]** で、作成するポリシーのセットに応じて **、[Android** 用アプリケーション管理] または **[iOS** 用アプリケーション管理] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-109">Under **Policy type**, choose **Application Management for Android** or **Application Management for iOS**, depending on which set of policies you want to create.</span></span> 
    
5. <span data-ttu-id="2cc6f-110">[**デバイスが紛失または盗難された** 場合に作業ファイルを保護する] を展開し、ユーザーがモバイル デバイス上Officeファイルにアクセスする **方法を管理します**。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-110">Expand **Protect work files when devices are lost or stolen** and **Manage how users access Office files on mobile devices**.</span></span> <span data-ttu-id="2cc6f-111">必要な設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-111">Configure the settings how you would like.</span></span> <span data-ttu-id="2cc6f-112">**ユーザーがモバイル デバイスOfficeファイル** にアクセスする方法を管理するには、既定で [オフ] を選択しますが、オンにし、既定値を受け入れすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-112">**Manage how users access Office files on mobile devices** is **Off** by default, but we recommend that you turn it **On** and accept the default values.</span></span> <span data-ttu-id="2cc6f-113">詳細については、「使用可能な設定 [」を参照してください](#available-settings)。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-113">For more information, see [Available settings](#available-settings).</span></span> 
    
    <span data-ttu-id="2cc6f-114">[ **既定の設定に戻す**] リンクを使用すれば、既定の設定にいつでも戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-114">You can always use the **Reset default settings** link to return to the default setting.</span></span> 
    
    ![Screenshot of Create a policy with Application management for Android selected](../media/eabbe06d-ac0a-4f3a-8630-68c808b1e662.png)
  
6. <span data-ttu-id="2cc6f-116">Next decide **Who will get these settings?**</span><span class="sxs-lookup"><span data-stu-id="2cc6f-116">Next decide **Who will get these settings?**</span></span> <span data-ttu-id="2cc6f-117">既定の [すべてのユーザー] セキュリティグループを使用しない場合は、[変更] を選択し、これらの設定を取得するセキュリティ グループを選択 \> **します**。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-117">If you don't want to use the default **All Users** security group, choose **Change**, choose the security groups that get these settings \> **Select**.</span></span>
    
7. <span data-ttu-id="2cc6f-118">最後に、[ **完了**] を選択してポリシーを保存し、それをデバイスに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-118">Finally, choose **Done** to save the policy, and assign it to devices.</span></span> 
    
## <a name="edit-an-app-management-policy"></a><span data-ttu-id="2cc6f-119">アプリの管理ポリシーを編集する</span><span class="sxs-lookup"><span data-stu-id="2cc6f-119">Edit an app management policy</span></span>

1. <span data-ttu-id="2cc6f-120">[ポリシー] **カードで、[** ポリシーの編集] **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-120">On the **Policies** card, choose **Edit policy**.</span></span>
    
2. <span data-ttu-id="2cc6f-121">[ **ポリシーの編集**] ウィンドウで、変更するポリシーを選択します。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-121">On the **Edit policy** pane, choose the policy you want to change</span></span> 
    
3. <span data-ttu-id="2cc6f-122">各設定の横にある [ **編集**] を選び、ポリシーの値を変更します。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-122">Choose **Edit** next to each setting to change the values in the policy.</span></span> <span data-ttu-id="2cc6f-123">値を変更すると、ポリシーに自動的に保存されます。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-123">When you change a value, it's automatically saved in the policy.</span></span>
    
4. <span data-ttu-id="2cc6f-124">完了したら、[ポリシーの編集] **ウィンドウを閉** じます。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-124">When you're finished, close the **Edit policy** pane.</span></span> 
    
## <a name="delete-an-app-management-policy"></a><span data-ttu-id="2cc6f-125">アプリの管理ポリシーを削除する</span><span class="sxs-lookup"><span data-stu-id="2cc6f-125">Delete an app management policy</span></span>

1. <span data-ttu-id="2cc6f-126">[ポリシー **] ページで** ポリシーを選択し、[削除] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-126">On the **Policies** page, choose a policy and then **Delete**.</span></span>
    
2. <span data-ttu-id="2cc6f-127">[ポリシー **の削除] ウィンドウで** 、[確認] **を選択** して、選択したポリシーまたはポリシーを削除します。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-127">On the **Delete policy** pane, choose **Confirm** to delete the policy or policies you chose.</span></span> 
    
## <a name="available-settings"></a><span data-ttu-id="2cc6f-128">利用可能な設定</span><span class="sxs-lookup"><span data-stu-id="2cc6f-128">Available settings</span></span>

<span data-ttu-id="2cc6f-129">次の表に、デバイス上の作業ファイルを保護するために使用できる設定と、ユーザーがモバイル デバイスからファイルにアクセスする方法を制御するOffice詳細な情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-129">The following tables give detailed information about settings available to protect work files on devices and the settings that control how users access Office files from their mobile devices.</span></span>
  
 <span data-ttu-id="2cc6f-130">詳細については、「Intune の設定[にマップするMicrosoft 365 Business Premium方法」を参照してください](map-protection-features-to-intune-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-130">For more information, see [How do protection features in Microsoft 365 Business Premium map to Intune settings](map-protection-features-to-intune-settings.md).</span></span> 
  
### <a name="settings-that-protect-work-files"></a><span data-ttu-id="2cc6f-131">作業ファイルを保護する設定</span><span class="sxs-lookup"><span data-stu-id="2cc6f-131">Settings that protect work files</span></span>

<span data-ttu-id="2cc6f-132">次の設定は、ユーザーのデバイスが紛失したり盗難された場合に、作業ファイルを保護するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-132">The following settings are available to protect work files if a user's device is lost or stolen:</span></span>


|<span data-ttu-id="2cc6f-133">Setting</span><span class="sxs-lookup"><span data-stu-id="2cc6f-133">Setting</span></span>  <br/> |<span data-ttu-id="2cc6f-134">説明</span><span class="sxs-lookup"><span data-stu-id="2cc6f-134">Description</span></span>  <br/> |
|:-----|:-----|
|<span data-ttu-id="2cc6f-135">この日数後、非アクティブなデバイスから作業ファイルを削除する</span><span class="sxs-lookup"><span data-stu-id="2cc6f-135">Delete work files from an inactive device after this many days</span></span>  <br/> |<span data-ttu-id="2cc6f-136">ここで指定した日数のデバイスを使用しない場合、デバイスに保存されている作業ファイルは自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-136">If a device isn't used for the number of days that you specify here, any work files stored on the device will be deleted automatically.</span></span>  <br/> |
|<span data-ttu-id="2cc6f-137">ユーザーにすべての作業ファイルを OneDrive for Business に強制的に保存させる</span><span class="sxs-lookup"><span data-stu-id="2cc6f-137">Force users to save all work files to OneDrive for Business</span></span>  <br/> |<span data-ttu-id="2cc6f-138">この設定が **[オン] の場合**、作業ファイルに使用できる保存場所は、OneDrive for Business。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-138">If this setting is **On**, the only available save location for work files is OneDrive for Business.</span></span>  <br/> |
|<span data-ttu-id="2cc6f-139">作業ファイルの暗号化</span><span class="sxs-lookup"><span data-stu-id="2cc6f-139">Encrypt work files</span></span>  <br/> |<span data-ttu-id="2cc6f-140">作業ファイルが暗号化によって保護されるように、この設定は常に **オン** にします。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-140">Keep this setting **On** so that work files are protected by encryption.</span></span> <span data-ttu-id="2cc6f-141">デバイスが紛失または盗まれた場合でも、誰も会社のデータを読み取ることはありません。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-141">Even if the device is lost or stolen, no one can read your company data.</span></span>  <br/> |
   
### <a name="settings-that-control-how-users-access-office-files-on-mobile-devices"></a><span data-ttu-id="2cc6f-142">ユーザーがモバイル デバイスで Office ファイルにアクセスする方法を制御する設定</span><span class="sxs-lookup"><span data-stu-id="2cc6f-142">Settings that control how users access Office files on mobile devices</span></span>

<span data-ttu-id="2cc6f-143">次の設定は、ユーザーが Office 作業ファイルにアクセスする方法を管理するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-143">The following settings are available to manage how users access Office work files:</span></span>


|<span data-ttu-id="2cc6f-144">Setting</span><span class="sxs-lookup"><span data-stu-id="2cc6f-144">Setting</span></span>  <br/> |<span data-ttu-id="2cc6f-145">説明</span><span class="sxs-lookup"><span data-stu-id="2cc6f-145">Description</span></span>  <br/> |
|:-----|:-----|
|<span data-ttu-id="2cc6f-146">Office アプリにアクセスするのに暗証番号 (PIN) または指紋認証を使用する必要がある</span><span class="sxs-lookup"><span data-stu-id="2cc6f-146">Require a PIN or fingerprint to access Office apps</span></span>  <br/> |<span data-ttu-id="2cc6f-147">この設定が **[オン] の** 場合、ユーザーはモバイル デバイスでアプリを使用する前に、ユーザー名とパスワードに加えて、別の形式の認証Office必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-147">If this setting is **On** users must provide another form of authentication, in addition to their username and password, before they can use Office apps on their mobile devices.</span></span><br/> |
|<span data-ttu-id="2cc6f-148">ログインに指定の回数失敗した場合に PIN をリセットする</span><span class="sxs-lookup"><span data-stu-id="2cc6f-148">Reset PIN when login fails this many times</span></span>  <br/> |<span data-ttu-id="2cc6f-149">承認されていないユーザーが PIN をランダムに推測するのを防ぐため、指定した回数、エントリを間違うと、PIN がリセットされます。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-149">To prevent an unauthorized user from randomly guessing a PIN, the PIN will reset after the number of wrong entries that you specify.</span></span>  <br/> |
|<span data-ttu-id="2cc6f-150">次の時間 Office アプリのアイドル状態が続いた場合にユーザーはもう一度サインインする必要がある</span><span class="sxs-lookup"><span data-stu-id="2cc6f-150">Require users to sign in again after Office apps have been idle for</span></span>  <br/> |<span data-ttu-id="2cc6f-151">この設定は、ユーザーが再度サインインするように求めるメッセージが表示されるまでアイドル状態にできる期間を決定します。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-151">This setting determines how long a user can be idle before they're prompted to sign in again.</span></span>  <br/> |
|<span data-ttu-id="2cc6f-152">脱獄またはルート化したデバイスでの作業ファイルへのアクセスを拒否する</span><span class="sxs-lookup"><span data-stu-id="2cc6f-152">Deny access to work files on jailbroken or rooted devices</span></span>  <br/> |<span data-ttu-id="2cc6f-p105">賢いユーザーは、脱獄またはルート化されたデバイスを持っている場合があります。これは、ユーザーがオペレーティング システムを変更できるため、デバイスがマルウェアの危険にさらされる可能性が高くなることを意味します。この設定を **オン** にすると、これらのデバイスはブロックされます。  </span><span class="sxs-lookup"><span data-stu-id="2cc6f-p105">Clever users may have a device that is jailbroken or rooted. This means that the user can modify the operating system, which can make the device more subject to malware. These devices are blocked when this setting is **On**.  </span></span><br/> |
|<span data-ttu-id="2cc6f-156">ユーザーがアプリから個人用アプリにコンテンツをコピー Office許可しない</span><span class="sxs-lookup"><span data-stu-id="2cc6f-156">Don't allow users to copy content from Office apps into personal apps</span></span>  <br/> |<span data-ttu-id="2cc6f-157">これは既定で許可していますが、設定が **オン** の場合、ユーザーは作業ファイル内の情報を個人のファイルにコピーできます。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-157">We do allow this by default, but if the setting is **On**, the user could copy information in a work file to a personal file.</span></span> <span data-ttu-id="2cc6f-158">この設定が **オフ** の場合、ユーザーは職場アカウントから個人用アプリまたは個人のアカウントに情報をコピーすることはできません。</span><span class="sxs-lookup"><span data-stu-id="2cc6f-158">If the setting is **Off**, the user will be unable to copy information from a work account into a personal app or personal account.</span></span>  <br/> |
