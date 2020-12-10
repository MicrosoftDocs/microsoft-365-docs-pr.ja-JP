---
title: 許可または禁止する Url をテナントの許可/ブロックリストで管理する
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: 管理者は、セキュリティ & コンプライアンスセンターのテナントの許可/ブロックリストで URL エントリを構成する方法について説明します。
ms.openlocfilehash: 0fdfa23ba22b240032e7a6888948de180aa0f6ae
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "49614966"
---
# <a name="manage-urls-in-the-tenant-allowblock-list"></a><span data-ttu-id="19b9e-103">テナントの許可/禁止リストの URL を管理する</span><span class="sxs-lookup"><span data-stu-id="19b9e-103">Manage URLs in the Tenant Allow/Block List</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


> [!NOTE]
> <span data-ttu-id="19b9e-104">このトピックで説明する機能はプレビュー段階にあり、変更される可能性があり、組織によっては利用できません。</span><span class="sxs-lookup"><span data-stu-id="19b9e-104">The features described in this topic are in Preview, are subject to change, and are not available in all organizations.</span></span>

<span data-ttu-id="19b9e-105">Exchange online または exchange online メールボックスを使用しない exchange online またはスタンドアロンの Exchange Online Protection (EOP) 組織内にメールボックスを持つ Microsoft 365 組織では、EOP フィルター verdict の使用に同意しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="19b9e-105">In Microsoft 365 organizations with mailboxes in Exchange Online or standalone Exchange Online Protection (EOP) organizations without Exchange Online mailboxes, you might disagree with the EOP filtering verdict.</span></span> <span data-ttu-id="19b9e-106">たとえば、良好なメッセージが不良 (誤検知) としてマークされている場合や、無効なメッセージが表示される場合があります (誤検知)。</span><span class="sxs-lookup"><span data-stu-id="19b9e-106">For example, a good message might be marked as bad (a false positive), or a bad message might be allowed through (a false negative).</span></span>

<span data-ttu-id="19b9e-107">セキュリティ & コンプライアンスセンターのテナントの許可/禁止リストにより、Microsoft 365 filtering verdicts を手動で上書きすることができます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-107">The Tenant Allow/Block List in the Security & Compliance Center gives you a way to manually override the Microsoft 365 filtering verdicts.</span></span> <span data-ttu-id="19b9e-108">テナントの許可/ブロックリストは、メールフローおよびユーザークリック時に使用されます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-108">The Tenant Allow/Block List is used during mail flow and at the time of user clicks.</span></span> <span data-ttu-id="19b9e-109">テナントの許可/ブロックリストで許可またはブロックする Url を指定できます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-109">You can specify URLs to allow or block in the Tenant Allow/Block List.</span></span>

<span data-ttu-id="19b9e-110">このトピックでは、セキュリティ & コンプライアンスセンターまたは PowerShell (exchange online にメールボックスがある Microsoft 365 組織の場合は exchange Online PowerShell、exchange online メールボックスを使用しない組織の場合は、スタンドアロン EOP PowerShell) で、テナントの許可/ブロックリストのエントリを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-110">This topic describes how to configure entries in the Tenant Allow/Block List in the Security & Compliance Center or in PowerShell (Exchange Online PowerShell for Microsoft 365 organizations with mailboxes in Exchange Online; standalone EOP PowerShell for organizations without Exchange Online mailboxes).</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="19b9e-111">はじめに把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="19b9e-111">What do you need to know before you begin?</span></span>

- <span data-ttu-id="19b9e-112"><https://protection.office.com/> でセキュリティ/コンプライアンス センターを開きます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-112">You open the Security & Compliance Center at <https://protection.office.com/>.</span></span> <span data-ttu-id="19b9e-113">[ **テナントの許可/ブロックリスト** ] ページに直接移動するには、を使用 <https://protection.office.com/tenantAllowBlockList> します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-113">To go directly to the **Tenant Allow/Block List** page, use <https://protection.office.com/tenantAllowBlockList>.</span></span>

- <span data-ttu-id="19b9e-114">使用可能な URL 値については、このトピックで後述する「 [テナントの許可/ブロックリスト」セクションの url 構文](#url-syntax-for-the-tenant-allowblock-list) で説明されています。</span><span class="sxs-lookup"><span data-stu-id="19b9e-114">The available URL values are described in the [URL syntax for the Tenant Allow/Block List](#url-syntax-for-the-tenant-allowblock-list) section later in this topic.</span></span>

- <span data-ttu-id="19b9e-115">テナントの許可/ブロックリストでは、Url に対して最大500エントリが許可されます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-115">The Tenant Allow/Block List allows a maximum of 500 entries for URLs.</span></span>

- <span data-ttu-id="19b9e-116">エントリは15分以内にアクティブである必要があります。</span><span class="sxs-lookup"><span data-stu-id="19b9e-116">An entry should be active within 15 minutes.</span></span>

- <span data-ttu-id="19b9e-117">禁止エントリは、許可エントリよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-117">Block entries take precedence over allow entries.</span></span>

- <span data-ttu-id="19b9e-118">既定では、テナントの許可/ブロックリストのエントリは30日後に期限切れになります。</span><span class="sxs-lookup"><span data-stu-id="19b9e-118">By default, entries in the Tenant Allow/Block List will expire after 30 days.</span></span> <span data-ttu-id="19b9e-119">日付を指定するか、期限切れにならないように設定できます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-119">You can specify a date or set them to never expire.</span></span>

- <span data-ttu-id="19b9e-120">Exchange Online PowerShell へ接続するには、「[Exchange Online PowerShell に接続する](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19b9e-120">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).</span></span> <span data-ttu-id="19b9e-121">スタンドアロンの EOP PowerShell に接続するには、「[Exchange Online Protection PowerShell への接続](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19b9e-121">To connect to standalone EOP PowerShell, see [Connect to Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).</span></span>

- <span data-ttu-id="19b9e-122">この記事の手順を実行する前に、セキュリティ & コンプライアンスセンターでアクセス許可を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="19b9e-122">You need to be assigned permissions in the Security & Compliance Center before you can do the procedures in this article:</span></span>
  - <span data-ttu-id="19b9e-123">テナントの許可/禁止リストに値を追加したり、削除したりするには、 **組織の管理** または **セキュリティ管理者** の役割グループのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="19b9e-123">To add and remove values from the Tenant Allow/Block List, you need to be a member of the **Organization Management** or **Security Administrator** role groups.</span></span>
  - <span data-ttu-id="19b9e-124">テナントの許可/禁止リストへの読み取り専用アクセスでは、 **グローバル閲覧** 者または **セキュリティ閲覧** 者の役割グループのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="19b9e-124">For read-only access to the Tenant Allow/Block List, you need to be a member of the **Global Reader** or **Security Reader** role groups.</span></span>

  <span data-ttu-id="19b9e-125">詳細については、「[セキュリティ/コンプライアンス センターのアクセス許可](permissions-in-the-security-and-compliance-center.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19b9e-125">For more information, see [Permissions in the Security & Compliance Center](permissions-in-the-security-and-compliance-center.md).</span></span>

  <span data-ttu-id="19b9e-126">**注**:</span><span class="sxs-lookup"><span data-stu-id="19b9e-126">**Notes**:</span></span>

  - <span data-ttu-id="19b9e-127">Microsoft 365 管理センターで、対応する Azure Active Directory の役割にユーザーを追加すると、ユーザーには、セキュリティ/コンプライアンス センター の必要なアクセス許可 _および_ Microsoft 365 のその他の機能に必要なアクセス許可が付与されます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-127">Adding users to the corresponding Azure Active Directory role in the Microsoft 365 admin center gives users the required permissions in the Security & Compliance Center _and_ permissions for other features in Microsoft 365.</span></span> <span data-ttu-id="19b9e-128">詳細については、「[管理者の役割について](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19b9e-128">For more information, see [About admin roles](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).</span></span>
  - <span data-ttu-id="19b9e-129">[Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups) の **閲覧専用の組織管理** の役割グループが この機能への読み取り専用アクセス権も付与します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-129">The **View-Only Organization Management** role group in [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups) also gives read-only access to the feature.</span></span>

## <a name="use-the-security--compliance-center-to-create-url-entries-in-the-tenant-allowblock-list"></a><span data-ttu-id="19b9e-130">セキュリティ & コンプライアンスセンターを使用して、テナントの許可/ブロックリストで URL エントリを作成する</span><span class="sxs-lookup"><span data-stu-id="19b9e-130">Use the Security & Compliance Center to create URL entries in the Tenant Allow/Block List</span></span>

<span data-ttu-id="19b9e-131">URL エントリの構文の詳細については、このトピックで後述する「 [テナントの許可/ブロックリスト」セクションの url 構文](#url-syntax-for-the-tenant-allowblock-list) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19b9e-131">For details about the syntax for URL entries, see the [URL syntax for the Tenant Allow/Block List](#url-syntax-for-the-tenant-allowblock-list) section later in this topic.</span></span>

1. <span data-ttu-id="19b9e-132">[セキュリティ & コンプライアンスセンター] で、[ **脅威管理** \> **ポリシー** の \> **テナントの許可/ブロックリスト**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-132">In the Security & Compliance Center, go to **Threat management** \> **Policy** \> **Tenant Allow/Block Lists**.</span></span>

2. <span data-ttu-id="19b9e-133">[**テナントの許可/ブロックリスト**] ページで、[ **url** ] タブが選択されていることを確認し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19b9e-133">On the **Tenant Allow/Block List** page, verify that the **URLs** tab is selected, and then click **Add**</span></span>

3. <span data-ttu-id="19b9e-134">表示される [ **新しい url の追加** ] ポップアップで、次の設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-134">In the **Add new URLs** flyout that appears, configure the following settings:</span></span>

   - <span data-ttu-id="19b9e-135">**ワイルドカードを使用して url を追加** します。1行に1つの url を入力します。最大値は20です。</span><span class="sxs-lookup"><span data-stu-id="19b9e-135">**Add URLs with wildcards**: Enter one URL per line, up to a maximum of 20.</span></span>

   - <span data-ttu-id="19b9e-136">[**ブロック/許可**]: 指定した Url を **許可** または **ブロック** するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-136">**Block/Allow**: Select whether you want to **Allow** or **Block** the specified URLs.</span></span>

   - <span data-ttu-id="19b9e-137">**無期限: 次** のいずれかの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-137">**Never expire**: Do one of the following steps:</span></span>

     - <span data-ttu-id="19b9e-138">設定がオフ (トグルオフ) になっていることを確認 ![ ](../../media/scc-toggle-off.png) し、 **[有効期限** ] ボックスを使用して、エントリの有効期限を指定します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-138">Verify the setting is turned off (![Toggle off](../../media/scc-toggle-off.png)) and use the **Expires on** box to specify the expiration date for the entries.</span></span>

     <span data-ttu-id="19b9e-139">または</span><span class="sxs-lookup"><span data-stu-id="19b9e-139">or</span></span>

     - <span data-ttu-id="19b9e-140">右にトグルを移動して、期限切れにならないようにエントリを構成します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-140">Move the toggle to the right to configure the entries to never expire:</span></span> ![オンに切り替え](../../media/963dfcd0-1765-4306-bcce-c3008c4406b9.png)<span data-ttu-id="19b9e-142">.</span><span class="sxs-lookup"><span data-stu-id="19b9e-142">.</span></span>

   - <span data-ttu-id="19b9e-143">**オプションのメモ**: エントリの説明テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-143">**Optional note**: Enter descriptive text for the entries.</span></span>

4. <span data-ttu-id="19b9e-144">完了したら、[ **追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19b9e-144">When you're finished, click **Add**.</span></span>

## <a name="use-the-security--compliance-center-to-view-entries-in-the-tenant-allowblock-list"></a><span data-ttu-id="19b9e-145">セキュリティ & コンプライアンスセンターを使用して、テナントの許可/ブロックリストのエントリを表示する</span><span class="sxs-lookup"><span data-stu-id="19b9e-145">Use the Security & Compliance Center to view entries in the Tenant Allow/Block List</span></span>

1. <span data-ttu-id="19b9e-146">[セキュリティ & コンプライアンスセンター] で、[ **脅威管理** \> **ポリシー** の \> **テナントの許可/ブロックリスト**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-146">In the Security & Compliance Center, go to **Threat management** \> **Policy** \> **Tenant Allow/Block Lists**.</span></span>

2. <span data-ttu-id="19b9e-147">[ **Url** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-147">Select the **URLs** tab.</span></span>

<span data-ttu-id="19b9e-148">次の列見出しをクリックすると、昇順または降順で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-148">Click on the following column headings to sort in ascending or descending order:</span></span>

- <span data-ttu-id="19b9e-149">**値**</span><span class="sxs-lookup"><span data-stu-id="19b9e-149">**Value**</span></span>
- <span data-ttu-id="19b9e-150">**アクション**: **ブロック** または **許可**。</span><span class="sxs-lookup"><span data-stu-id="19b9e-150">**Action**: **Block** or **Allow**.</span></span>
- <span data-ttu-id="19b9e-151">**最終更新日**</span><span class="sxs-lookup"><span data-stu-id="19b9e-151">**Last updated date**</span></span>
- <span data-ttu-id="19b9e-152">**有効期限**</span><span class="sxs-lookup"><span data-stu-id="19b9e-152">**Expiration date**</span></span>
- <span data-ttu-id="19b9e-153">**注**</span><span class="sxs-lookup"><span data-stu-id="19b9e-153">**Note**</span></span>

<span data-ttu-id="19b9e-154">[ **グループ化** ] をクリックして、エントリを **アクション** (**ブロック** または **許可**) または **なし** とグループ化します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-154">Click **Group** to group the entries by **Action** (**Block** or **Allow**) or **None**.</span></span>

<span data-ttu-id="19b9e-155">[ **検索**] をクリックして、値の全体または一部を入力し、enter キーを押して特定の値を検索します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-155">Click **Search**, enter all or part of a value, and then press ENTER to find a specific value.</span></span> <span data-ttu-id="19b9e-156">完了したら、[検索のクリア検索の **クリア**] をクリックし ![ ](../../media/b6512677-5e7b-42b0-a8a3-3be1d7fa23ee.gif) ます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-156">When you're finished, click **Clear search** ![Clear search icon](../../media/b6512677-5e7b-42b0-a8a3-3be1d7fa23ee.gif).</span></span>

<span data-ttu-id="19b9e-157">[ **フィルター**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19b9e-157">Click **Filter**.</span></span> <span data-ttu-id="19b9e-158">表示される **フィルター** のポップアップで、次のいずれかの設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-158">In the **Filter** flyout that appears, configure any of the following settings:</span></span>

- <span data-ttu-id="19b9e-159">**アクション**: **Allow**、 **Block** 、または both を選択します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-159">**Action**: Select **Allow**, **Block** or both.</span></span>

- <span data-ttu-id="19b9e-160">**無期限: オフ**(オフ ![ ](../../media/scc-toggle-off.png) ) またはオン ( ![ トグルオン ](../../media/963dfcd0-1765-4306-bcce-c3008c4406b9.png) )。</span><span class="sxs-lookup"><span data-stu-id="19b9e-160">**Never expire**: Select off (![Toggle off](../../media/scc-toggle-off.png)) or on (![Toggle on](../../media/963dfcd0-1765-4306-bcce-c3008c4406b9.png)).</span></span>

- <span data-ttu-id="19b9e-161">**最終更新** 日時: 開始日 (開始 **日)、** 終了日 (**To**)、またはその両方を選択します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-161">**Last updated**: Select a start date (**From**), an end date (**To**) or both.</span></span>

- <span data-ttu-id="19b9e-162">[**有効期限**]: 開始日 (開始 **日)、** 終了日 (**To**)、またはその両方を選択します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-162">**Expiration date**: Select a start date (**From**), an end date (**To**) or both.</span></span>

<span data-ttu-id="19b9e-163">完了したら、[ **適用**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19b9e-163">When you're finished, click **Apply**.</span></span>

<span data-ttu-id="19b9e-164">既存のフィルターをクリアするには、[ **フィルター**] をクリックし、表示される **フィルター** のポップアップで [ **フィルターのクリア**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19b9e-164">To clear existing filters, click **Filter**, and in the **Filter** flyout that appears, click **Clear filters**.</span></span>

## <a name="use-the-security--compliance-center-to-modify-entries-in-the-tenant-allowblock-list"></a><span data-ttu-id="19b9e-165">セキュリティ & コンプライアンスセンターを使用して、テナントの許可/ブロックリストのエントリを変更する</span><span class="sxs-lookup"><span data-stu-id="19b9e-165">Use the Security & Compliance Center to modify entries in the Tenant Allow/Block List</span></span>

<span data-ttu-id="19b9e-166">URL の値自体を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="19b9e-166">You can't modify the URL value itself.</span></span> <span data-ttu-id="19b9e-167">代わりに、エントリを削除して再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19b9e-167">Instead, you need to delete the entry and recreate it.</span></span>

1. <span data-ttu-id="19b9e-168">[セキュリティ & コンプライアンスセンター] で、[ **脅威管理** \> **ポリシー** の \> **テナントの許可/ブロックリスト**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-168">In the Security & Compliance Center, go to **Threat management** \> **Policy** \> **Tenant Allow/Block Lists**.</span></span>

2. <span data-ttu-id="19b9e-169">[ **Url** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-169">Select the **URLs** tab.</span></span>

3. <span data-ttu-id="19b9e-170">変更するエントリを選択し、[編集アイコンの **編集**] をクリックし ![ ](../../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png) ます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-170">Select the entry that you want to modify, and then click **Edit** ![Edit icon](../../media/0cfcb590-dc51-4b4f-9276-bb2ce300d87e.png).</span></span>

4. <span data-ttu-id="19b9e-171">表示されたポップアップで、次の設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-171">In the flyout that appears, configure the following settings:</span></span>

   - <span data-ttu-id="19b9e-172">[**ブロック/許可**]: [**許可**] または [**ブロック**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-172">**Block/Allow**: Select **Allow** or **Block**.</span></span>

   - <span data-ttu-id="19b9e-173">**無期限: 次** のいずれかの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-173">**Never expire**: Do one of the following steps:</span></span>

     - <span data-ttu-id="19b9e-174">設定がオフ (トグルオフ) になっていることを確認 ![ ](../../media/scc-toggle-off.png) し、 **[有効期限** ] ボックスを使用して、エントリの有効期限を指定します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-174">Verify the setting is turned off (![Toggle off](../../media/scc-toggle-off.png)) and use the **Expires on** box to specify the expiration date for the entry.</span></span>

     <span data-ttu-id="19b9e-175">または</span><span class="sxs-lookup"><span data-stu-id="19b9e-175">or</span></span>

     - <span data-ttu-id="19b9e-176">この設定を右に移動して、期限切れにならないようにエントリを構成します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-176">Move the toggle to the right to configure the entry to never expire:</span></span> ![オンに切り替え](../../media/963dfcd0-1765-4306-bcce-c3008c4406b9.png)<span data-ttu-id="19b9e-178">.</span><span class="sxs-lookup"><span data-stu-id="19b9e-178">.</span></span>

   - <span data-ttu-id="19b9e-179">**オプションのメモ**: エントリの説明テキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-179">**Optional note**: Enter descriptive text for the entry.</span></span>

5. <span data-ttu-id="19b9e-180">完了したら、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19b9e-180">When you're finished, click **Save**.</span></span>

## <a name="use-the-security--compliance-center-to-remove-entries-from-the-tenant-allowblock-list"></a><span data-ttu-id="19b9e-181">セキュリティ & コンプライアンスセンターを使用して、テナントの許可/ブロックリストからエントリを削除する</span><span class="sxs-lookup"><span data-stu-id="19b9e-181">Use the Security & Compliance Center to remove entries from the Tenant Allow/Block List</span></span>

1. <span data-ttu-id="19b9e-182">[セキュリティ & コンプライアンスセンター] で、[ **脅威管理** \> **ポリシー** の \> **テナントの許可/ブロックリスト**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-182">In the Security & Compliance Center, go to **Threat management** \> **Policy** \> **Tenant Allow/Block Lists**.</span></span>

2. <span data-ttu-id="19b9e-183">[ **Url** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-183">Select the **URLs** tab.</span></span>

3. <span data-ttu-id="19b9e-184">削除するエントリを選択し、[削除] [削除] アイコン **をクリックし** ![ ](../../media/87565fbb-5147-4f22-9ed7-1c18ce664392.png) ます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-184">Select the entry that you want to remove, and then click **Delete** ![Delete icon](../../media/87565fbb-5147-4f22-9ed7-1c18ce664392.png).</span></span>

4. <span data-ttu-id="19b9e-185">表示される警告ダイアログで、[ **削除**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19b9e-185">In the warning dialog that appears, click **Delete**.</span></span>

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-the-tenant-allowblock-list"></a><span data-ttu-id="19b9e-186">Exchange Online PowerShell またはスタンドアロンの EOP PowerShell を使用して、テナントの許可/ブロックリストを構成する</span><span class="sxs-lookup"><span data-stu-id="19b9e-186">Use Exchange Online PowerShell or standalone EOP PowerShell to configure the Tenant Allow/Block List</span></span>

### <a name="use-powershell-to-add-entries-in-the-tenant-allowblock-list"></a><span data-ttu-id="19b9e-187">PowerShell を使用して、テナントの許可/ブロックリストにエントリを追加する</span><span class="sxs-lookup"><span data-stu-id="19b9e-187">Use PowerShell to add entries in the Tenant Allow/Block List</span></span>

<span data-ttu-id="19b9e-188">テナントの許可/ブロックリストにエントリを追加するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-188">To add entries in the Tenant Allow/Block List, use the following syntax:</span></span>

```powershell
New-TenantAllowBlockListItems -ListType Url -Action <Allow | Block> -Entries <String[]> [-ExpirationDate <DateTime>] [-NoExpiration] [-Notes <String>]
```

<span data-ttu-id="19b9e-189">この例では、contoso.com およびすべてのサブドメイン (たとえば、contoso.com、www.contoso.com、および xyz.abc.contoso.com) の URL ブロックエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-189">This example adds a URL block entry for contoso.com and all subdomains (for example, contoso.com, www.contoso.com, and xyz.abc.contoso.com).</span></span> <span data-ttu-id="19b9e-190">ExpirationDate パラメーターまたは NoExpiration パラメーターを使用していなかったため、エントリは30日後に有効期限が切れます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-190">Because we didn't use the ExpirationDate or NoExpiration parameters, the entry expires after 30 days.</span></span>

```powershell
New-TenantAllowBlockListItem -ListType Url -Action Block -Entries ~contoso.com
```

<span data-ttu-id="19b9e-191">構文およびパラメーターの詳細については、「 [TenantAllowBlockListItems](https://docs.microsoft.com/powershell/module/exchange/new-tenantallowblocklistitems)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19b9e-191">For detailed syntax and parameter information, see [New-TenantAllowBlockListItems](https://docs.microsoft.com/powershell/module/exchange/new-tenantallowblocklistitems).</span></span>

### <a name="use-powershell-to-view-entries-in-the-tenant-allowblock-list"></a><span data-ttu-id="19b9e-192">PowerShell を使用して、テナントの許可/ブロックリストのエントリを表示する</span><span class="sxs-lookup"><span data-stu-id="19b9e-192">Use PowerShell to view entries in the Tenant Allow/Block List</span></span>

<span data-ttu-id="19b9e-193">テナントの許可/ブロックリストのエントリを表示するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-193">To view entries in the Tenant Allow/Block List, use the following syntax:</span></span>

```powershell
Get-TenantAllowBlockListItems -ListType Url [-Entry <URLValue>] [-Action <Allow | Block>] [-ExpirationDate <DateTime>] [-NoExpiration]
```

<span data-ttu-id="19b9e-194">この例では、すべてのブロックされた Url を返します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-194">This example returns all blocked URLs.</span></span>

```powershell
Get-TenantAllowBlockListItems -ListType Url -Action Block
```

<span data-ttu-id="19b9e-195">構文およびパラメーターの詳細については、「 [TenantAllowBlockListItems](https://docs.microsoft.com/powershell/module/exchange/get-tenantallowblocklistitems)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19b9e-195">For detailed syntax and parameter information, see [Get-TenantAllowBlockListItems](https://docs.microsoft.com/powershell/module/exchange/get-tenantallowblocklistitems).</span></span>

### <a name="use-powershell-to-modify-entries-in-the-tenant-allowblock-list"></a><span data-ttu-id="19b9e-196">PowerShell を使用して、テナントの許可/ブロックリストのエントリを変更する</span><span class="sxs-lookup"><span data-stu-id="19b9e-196">Use PowerShell to modify entries in the Tenant Allow/Block List</span></span>

<span data-ttu-id="19b9e-197">URL の値自体を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="19b9e-197">You can't modify the URL value itself.</span></span> <span data-ttu-id="19b9e-198">代わりに、エントリを削除して再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19b9e-198">Instead, you need to delete the entry and recreate it.</span></span>

<span data-ttu-id="19b9e-199">テナントの許可/ブロックリストのエントリを変更するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-199">To modify entries in the Tenant Allow/Block List, use the following syntax:</span></span>

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids <"Id1","Id2",..."IdN"> [-Action <Allow | Block>] [-ExpirationDate <DateTime>] [-NoExpiration] [-Notes <String>]
```

<span data-ttu-id="19b9e-200">次の使用例は、指定された項目の有効期限を変更します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-200">This example changes the expiration date of the specified entry.</span></span>

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -ExpirationDate (Get-Date "5/30/2020 9:30 AM").ToUniversalTime()
```

<span data-ttu-id="19b9e-201">構文およびパラメーターの詳細については、「 [TenantAllowBlockListItems](https://docs.microsoft.com/powershell/module/exchange/set-tenantallowblocklistitems)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19b9e-201">For detailed syntax and parameter information, see [Set-TenantAllowBlockListItems](https://docs.microsoft.com/powershell/module/exchange/set-tenantallowblocklistitems).</span></span>

### <a name="use-powershell-to-remove-entries-from-the-tenant-allowblock-list"></a><span data-ttu-id="19b9e-202">PowerShell を使用して、テナントの許可/ブロックリストからエントリを削除する</span><span class="sxs-lookup"><span data-stu-id="19b9e-202">Use PowerShell to remove entries from the Tenant Allow/Block List</span></span>

<span data-ttu-id="19b9e-203">テナントの許可/禁止リストからエントリを削除するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-203">To remove entries from the Tenant Allow/Block List, use the following syntax:</span></span>

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids <"Id1","Id2",..."IdN">
```

<span data-ttu-id="19b9e-204">この例では、指定した URL エントリをテナントの許可/禁止リストから削除します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-204">This example removes the specified URL entry from the Tenant Allow/Block List.</span></span>

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSPAAAA0"
```

<span data-ttu-id="19b9e-205">構文およびパラメーターの詳細については、「 [TenantAllowBlockListItems](https://docs.microsoft.com/powershell/module/exchange/remove-tenantallowblocklistitems)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19b9e-205">For detailed syntax and parameter information, see [Remove-TenantAllowBlockListItems](https://docs.microsoft.com/powershell/module/exchange/remove-tenantallowblocklistitems).</span></span>

## <a name="url-syntax-for-the-tenant-allowblock-list"></a><span data-ttu-id="19b9e-206">テナントの許可/ブロックリストの URL 構文</span><span class="sxs-lookup"><span data-stu-id="19b9e-206">URL syntax for the Tenant Allow/Block List</span></span>

- <span data-ttu-id="19b9e-207">IP4v および IPv6 アドレスは許可されますが、TCP/UDP ポートは許可されません。</span><span class="sxs-lookup"><span data-stu-id="19b9e-207">IP4v and IPv6 addresses are allowed, but TCP/UDP ports are not.</span></span>

- <span data-ttu-id="19b9e-208">ファイル名拡張子を使用することはできません (test.pdf など)。</span><span class="sxs-lookup"><span data-stu-id="19b9e-208">Filename extensions are not allowed (for example, test.pdf).</span></span>

- <span data-ttu-id="19b9e-209">Unicode はサポートされていませんが、Punycode はです。</span><span class="sxs-lookup"><span data-stu-id="19b9e-209">Unicode is not supported, but Punycode is.</span></span>

- <span data-ttu-id="19b9e-210">次のすべてのステートメントが true の場合、ホスト名が許可されます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-210">Hostnames are allowed if all of the following statements are true:</span></span>

  - <span data-ttu-id="19b9e-211">ホスト名にはピリオドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="19b9e-211">The hostname contains a period.</span></span>
  - <span data-ttu-id="19b9e-212">ピリオドの左側には、少なくとも1つの文字があります。</span><span class="sxs-lookup"><span data-stu-id="19b9e-212">There is at least one character to the left of the period.</span></span>
  - <span data-ttu-id="19b9e-213">ピリオドの右側には、少なくとも2つの文字があります。</span><span class="sxs-lookup"><span data-stu-id="19b9e-213">There are at least two characters to the right of the period.</span></span>

  <span data-ttu-id="19b9e-214">たとえば、は許可されて `t.co` `.com` いるか、許可され `contoso.` ていません。</span><span class="sxs-lookup"><span data-stu-id="19b9e-214">For example, `t.co` is allowed; `.com` or `contoso.` are not allowed.</span></span>

- <span data-ttu-id="19b9e-215">サブパスは黙示的ではありません。</span><span class="sxs-lookup"><span data-stu-id="19b9e-215">Subpaths are not implied.</span></span>

  <span data-ttu-id="19b9e-216">たとえば、にはを `contoso.com` 含めません `contoso.com/a` 。</span><span class="sxs-lookup"><span data-stu-id="19b9e-216">For example, `contoso.com` does not include `contoso.com/a`.</span></span>

- <span data-ttu-id="19b9e-217">次のシナリオでは、ワイルドカード (\*) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-217">Wildcards (\*) are allowed in the following scenarios:</span></span>

  - <span data-ttu-id="19b9e-218">サブドメインを指定するには、左のワイルドカードの後にピリオドを置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="19b9e-218">A left wildcard must be followed by a period to specify a subdomain.</span></span>

    <span data-ttu-id="19b9e-219">たとえば、 `*.contoso.com` は許可され `*contoso.com` ていません。許可されていません。</span><span class="sxs-lookup"><span data-stu-id="19b9e-219">For example, `*.contoso.com` is allowed; `*contoso.com` is not allowed.</span></span>

  - <span data-ttu-id="19b9e-220">右のワイルドカードは、スラッシュ (/) に続けてパスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19b9e-220">A right wildcard must follow a forward slash (/) to specify a path.</span></span>

    <span data-ttu-id="19b9e-221">たとえば、は許可されて `contoso.com/*` `contoso.com*` いるか、許可され `contoso.com/ab*` ていません。</span><span class="sxs-lookup"><span data-stu-id="19b9e-221">For example, `contoso.com/*` is allowed; `contoso.com*` or `contoso.com/ab*` are not allowed.</span></span>

  - <span data-ttu-id="19b9e-222">すべてのサブパスは、右のワイルドカードでは暗黙的には含まれません。</span><span class="sxs-lookup"><span data-stu-id="19b9e-222">All subpaths are not implied by a right wildcard.</span></span>

    <span data-ttu-id="19b9e-223">たとえば、にはを `contoso.com/*` 含めません `contoso.com/a` 。</span><span class="sxs-lookup"><span data-stu-id="19b9e-223">For example, `contoso.com/*` does not include `contoso.com/a`.</span></span>

  - <span data-ttu-id="19b9e-224">`*.com*` は無効です (解決可能なドメインではなく、右のワイルドカードはスラッシュに従っていません)。</span><span class="sxs-lookup"><span data-stu-id="19b9e-224">`*.com*` is invalid (not a resolvable domain and the right wildcard does not follow a forward slash).</span></span>

  - <span data-ttu-id="19b9e-225">IP アドレスにワイルドカードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="19b9e-225">Wildcards are not allowed in IP addresses.</span></span>

- <span data-ttu-id="19b9e-226">チルダ (~) 文字は、次のシナリオで使用できます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-226">The tilde (~) character is available in the following scenarios:</span></span>

  - <span data-ttu-id="19b9e-227">左チルダは、1つのドメインとすべてのサブドメインを意味します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-227">A left tilde implies a domain and all subdomains.</span></span>

    <span data-ttu-id="19b9e-228">たとえば `~contoso.com` `contoso.com` 、とを含み `*.contoso.com` ます。</span><span class="sxs-lookup"><span data-stu-id="19b9e-228">For example `~contoso.com` includes `contoso.com` and `*.contoso.com`.</span></span>

- <span data-ttu-id="19b9e-229">`http://` `https://` Url エントリはすべてのプロトコルに適用されるため、プロトコル (たとえば、など) を含む url エントリ `ftp://` は失敗します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-229">URL entries that contain protocols (for example, `http://`, `https://`, or `ftp://`) will fail, because URL entries apply to all protocols.</span></span>

- <span data-ttu-id="19b9e-230">ユーザー名またはパスワードがサポートされていないか、または必要です。</span><span class="sxs-lookup"><span data-stu-id="19b9e-230">A username or password aren't supported or required.</span></span>

- <span data-ttu-id="19b9e-231">引用符 (' または ") は無効な文字です。</span><span class="sxs-lookup"><span data-stu-id="19b9e-231">Quotes (' or ") are invalid characters.</span></span>

- <span data-ttu-id="19b9e-232">可能な場合は、URL にすべてのリダイレクトを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="19b9e-232">A URL should include all redirects where possible.</span></span>

### <a name="url-entry-scenarios"></a><span data-ttu-id="19b9e-233">URL エントリのシナリオ</span><span class="sxs-lookup"><span data-stu-id="19b9e-233">URL entry scenarios</span></span>

<span data-ttu-id="19b9e-234">次のセクションでは、有効な URL エントリとその結果について説明します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-234">Valid URL entries and their results are described in the following sections.</span></span>

#### <a name="scenario-no-wildcards"></a><span data-ttu-id="19b9e-235">シナリオ: ワイルドカードがありません</span><span class="sxs-lookup"><span data-stu-id="19b9e-235">Scenario: No wildcards</span></span>

<span data-ttu-id="19b9e-236">**Entry**: `contoso.com`</span><span class="sxs-lookup"><span data-stu-id="19b9e-236">**Entry**: `contoso.com`</span></span>

- <span data-ttu-id="19b9e-237">**Match の許可**: contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-237">**Allow match**: contoso.com</span></span>

- <span data-ttu-id="19b9e-238">**許可しない**:</span><span class="sxs-lookup"><span data-stu-id="19b9e-238">**Allow not matched**:</span></span>

  - <span data-ttu-id="19b9e-239">abc-contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-239">abc-contoso.com</span></span>
  - <span data-ttu-id="19b9e-240">contoso.com/a</span><span class="sxs-lookup"><span data-stu-id="19b9e-240">contoso.com/a</span></span>
  - <span data-ttu-id="19b9e-241">payroll.contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-241">payroll.contoso.com</span></span>
  - <span data-ttu-id="19b9e-242">test.com/contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-242">test.com/contoso.com</span></span>
  - <span data-ttu-id="19b9e-243">test.com/q=contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-243">test.com/q=contoso.com</span></span>
  - <span data-ttu-id="19b9e-244">www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-244">www.contoso.com</span></span>
  - <span data-ttu-id="19b9e-245">www. .com/q = a@contoso</span><span class="sxs-lookup"><span data-stu-id="19b9e-245">www.contoso.com/q=a@contoso.com</span></span>

- <span data-ttu-id="19b9e-246">**ブロック一致**:</span><span class="sxs-lookup"><span data-stu-id="19b9e-246">**Block match**:</span></span>

  - <span data-ttu-id="19b9e-247">contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-247">contoso.com</span></span>
  - <span data-ttu-id="19b9e-248">contoso.com/a</span><span class="sxs-lookup"><span data-stu-id="19b9e-248">contoso.com/a</span></span>
  - <span data-ttu-id="19b9e-249">payroll.contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-249">payroll.contoso.com</span></span>
  - <span data-ttu-id="19b9e-250">test.com/contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-250">test.com/contoso.com</span></span>
  - <span data-ttu-id="19b9e-251">test.com/q=contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-251">test.com/q=contoso.com</span></span>
  - <span data-ttu-id="19b9e-252">www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-252">www.contoso.com</span></span>
  - <span data-ttu-id="19b9e-253">www. .com/q = a@contoso</span><span class="sxs-lookup"><span data-stu-id="19b9e-253">www.contoso.com/q=a@contoso.com</span></span>

- <span data-ttu-id="19b9e-254">**ブロックが一致しません**: abc-contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-254">**Block not matched**: abc-contoso.com</span></span>

#### <a name="scenario-left-wildcard-subdomain"></a><span data-ttu-id="19b9e-255">シナリオ: 左ワイルドカード (サブドメイン)</span><span class="sxs-lookup"><span data-stu-id="19b9e-255">Scenario: Left wildcard (subdomain)</span></span>

<span data-ttu-id="19b9e-256">**Entry**: `*.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="19b9e-256">**Entry**: `*.contoso.com`</span></span>

- <span data-ttu-id="19b9e-257">一致と **ブロックの一致** を **許可する**:</span><span class="sxs-lookup"><span data-stu-id="19b9e-257">**Allow match** and **Block match**:</span></span>

  - <span data-ttu-id="19b9e-258">www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-258">www.contoso.com</span></span>
  - <span data-ttu-id="19b9e-259">xyz.abc.contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-259">xyz.abc.contoso.com</span></span>

- <span data-ttu-id="19b9e-260">[一致しない] と [**ブロックが一致** し **ません**] を許可します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-260">**Allow not matched** and **Block not matched**:</span></span>

  - <span data-ttu-id="19b9e-261">123contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-261">123contoso.com</span></span>
  - <span data-ttu-id="19b9e-262">contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-262">contoso.com</span></span>
  - <span data-ttu-id="19b9e-263">test.com/contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-263">test.com/contoso.com</span></span>
  - <span data-ttu-id="19b9e-264">www.contoso.com/abc</span><span class="sxs-lookup"><span data-stu-id="19b9e-264">www.contoso.com/abc</span></span>

#### <a name="scenario-right-wildcard-at-top-of-path"></a><span data-ttu-id="19b9e-265">シナリオ: パスの上部にあるワイルドカード (右)</span><span class="sxs-lookup"><span data-stu-id="19b9e-265">Scenario: Right wildcard at top of path</span></span>

<span data-ttu-id="19b9e-266">**Entry**: `contoso.com/a/*`</span><span class="sxs-lookup"><span data-stu-id="19b9e-266">**Entry**: `contoso.com/a/*`</span></span>

- <span data-ttu-id="19b9e-267">一致と **ブロックの一致** を **許可する**:</span><span class="sxs-lookup"><span data-stu-id="19b9e-267">**Allow match** and **Block match**:</span></span>

  - <span data-ttu-id="19b9e-268">contoso.com/a/b</span><span class="sxs-lookup"><span data-stu-id="19b9e-268">contoso.com/a/b</span></span>
  - <span data-ttu-id="19b9e-269">contoso.com/a/b/c</span><span class="sxs-lookup"><span data-stu-id="19b9e-269">contoso.com/a/b/c</span></span>
  - <span data-ttu-id="19b9e-270">contoso .com/a/? q = joe@t</span><span class="sxs-lookup"><span data-stu-id="19b9e-270">contoso.com/a/?q=joe@t.com</span></span>

- <span data-ttu-id="19b9e-271">[一致しない] と [**ブロックが一致** し **ません**] を許可します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-271">**Allow not matched** and **Block not matched**:</span></span>

  - <span data-ttu-id="19b9e-272">contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-272">contoso.com</span></span>
  - <span data-ttu-id="19b9e-273">contoso.com/a</span><span class="sxs-lookup"><span data-stu-id="19b9e-273">contoso.com/a</span></span>
  - <span data-ttu-id="19b9e-274">www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-274">www.contoso.com</span></span>
  - <span data-ttu-id="19b9e-275">www. .com/q = a@contoso</span><span class="sxs-lookup"><span data-stu-id="19b9e-275">www.contoso.com/q=a@contoso.com</span></span>

#### <a name="scenario-left-tilde"></a><span data-ttu-id="19b9e-276">シナリオ: 左チルダ</span><span class="sxs-lookup"><span data-stu-id="19b9e-276">Scenario: Left tilde</span></span>

<span data-ttu-id="19b9e-277">**Entry**: `~contoso.com`</span><span class="sxs-lookup"><span data-stu-id="19b9e-277">**Entry**: `~contoso.com`</span></span>

- <span data-ttu-id="19b9e-278">一致と **ブロックの一致** を **許可する**:</span><span class="sxs-lookup"><span data-stu-id="19b9e-278">**Allow match** and **Block match**:</span></span>

  - <span data-ttu-id="19b9e-279">contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-279">contoso.com</span></span>
  - <span data-ttu-id="19b9e-280">www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-280">www.contoso.com</span></span>
  - <span data-ttu-id="19b9e-281">xyz.abc.contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-281">xyz.abc.contoso.com</span></span>

- <span data-ttu-id="19b9e-282">[一致しない] と [**ブロックが一致** し **ません**] を許可します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-282">**Allow not matched** and **Block not matched**:</span></span>

  - <span data-ttu-id="19b9e-283">123contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-283">123contoso.com</span></span>
  - <span data-ttu-id="19b9e-284">contoso.com/abc</span><span class="sxs-lookup"><span data-stu-id="19b9e-284">contoso.com/abc</span></span>
  - <span data-ttu-id="19b9e-285">www.contoso.com/abc</span><span class="sxs-lookup"><span data-stu-id="19b9e-285">www.contoso.com/abc</span></span>

#### <a name="scenario-right-wildcard-suffix"></a><span data-ttu-id="19b9e-286">シナリオ: 右ワイルドカードサフィックス</span><span class="sxs-lookup"><span data-stu-id="19b9e-286">Scenario: Right wildcard suffix</span></span>

<span data-ttu-id="19b9e-287">**Entry**: `contoso.com/*`</span><span class="sxs-lookup"><span data-stu-id="19b9e-287">**Entry**: `contoso.com/*`</span></span>

- <span data-ttu-id="19b9e-288">一致と **ブロックの一致** を **許可する**:</span><span class="sxs-lookup"><span data-stu-id="19b9e-288">**Allow match** and **Block match**:</span></span>

  - <span data-ttu-id="19b9e-289">contoso .com/? q = whatever@fabrikam</span><span class="sxs-lookup"><span data-stu-id="19b9e-289">contoso.com/?q=whatever@fabrikam.com</span></span>
  - <span data-ttu-id="19b9e-290">contoso.com/a</span><span class="sxs-lookup"><span data-stu-id="19b9e-290">contoso.com/a</span></span>
  - <span data-ttu-id="19b9e-291">contoso.com/a/b/c</span><span class="sxs-lookup"><span data-stu-id="19b9e-291">contoso.com/a/b/c</span></span>
  - <span data-ttu-id="19b9e-292">contoso.com/ab</span><span class="sxs-lookup"><span data-stu-id="19b9e-292">contoso.com/ab</span></span>
  - <span data-ttu-id="19b9e-293">contoso.com/b</span><span class="sxs-lookup"><span data-stu-id="19b9e-293">contoso.com/b</span></span>
  - <span data-ttu-id="19b9e-294">contoso.com/b/a/c</span><span class="sxs-lookup"><span data-stu-id="19b9e-294">contoso.com/b/a/c</span></span>
  - <span data-ttu-id="19b9e-295">contoso.com/ba</span><span class="sxs-lookup"><span data-stu-id="19b9e-295">contoso.com/ba</span></span>

- <span data-ttu-id="19b9e-296">**Allow not 一致** と **ブロック not 一致**: contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-296">**Allow not matched** and **Block not matched**: contoso.com</span></span>

#### <a name="scenario-left-wildcard-subdomain-and-right-wildcard-suffix"></a><span data-ttu-id="19b9e-297">シナリオ: 左ワイルドカードサブドメインと右ワイルドカードサフィックス</span><span class="sxs-lookup"><span data-stu-id="19b9e-297">Scenario: Left wildcard subdomain and right wildcard suffix</span></span>

<span data-ttu-id="19b9e-298">**Entry**: `*.contoso.com/*`</span><span class="sxs-lookup"><span data-stu-id="19b9e-298">**Entry**: `*.contoso.com/*`</span></span>

- <span data-ttu-id="19b9e-299">一致と **ブロックの一致** を **許可する**:</span><span class="sxs-lookup"><span data-stu-id="19b9e-299">**Allow match** and **Block match**:</span></span>

  - <span data-ttu-id="19b9e-300">abc.contoso.com/ab</span><span class="sxs-lookup"><span data-stu-id="19b9e-300">abc.contoso.com/ab</span></span>
  - <span data-ttu-id="19b9e-301">abc.xyz.contoso.com/a/b/c</span><span class="sxs-lookup"><span data-stu-id="19b9e-301">abc.xyz.contoso.com/a/b/c</span></span>
  - <span data-ttu-id="19b9e-302">www.contoso.com/a</span><span class="sxs-lookup"><span data-stu-id="19b9e-302">www.contoso.com/a</span></span>
  - <span data-ttu-id="19b9e-303">www.contoso.com/b/a/c</span><span class="sxs-lookup"><span data-stu-id="19b9e-303">www.contoso.com/b/a/c</span></span>
  - <span data-ttu-id="19b9e-304">xyz.contoso.com/ba</span><span class="sxs-lookup"><span data-stu-id="19b9e-304">xyz.contoso.com/ba</span></span>

- <span data-ttu-id="19b9e-305">**Allow not 一致** と **ブロック not 一致**: contoso.com/b</span><span class="sxs-lookup"><span data-stu-id="19b9e-305">**Allow not matched** and **Block not matched**: contoso.com/b</span></span>

#### <a name="scenario-left-and-right-tilde"></a><span data-ttu-id="19b9e-306">シナリオ: 左と右のチルダ</span><span class="sxs-lookup"><span data-stu-id="19b9e-306">Scenario: Left and right tilde</span></span>

<span data-ttu-id="19b9e-307">**Entry**: `~contoso.com~`</span><span class="sxs-lookup"><span data-stu-id="19b9e-307">**Entry**: `~contoso.com~`</span></span>

- <span data-ttu-id="19b9e-308">一致と **ブロックの一致** を **許可する**:</span><span class="sxs-lookup"><span data-stu-id="19b9e-308">**Allow match** and **Block match**:</span></span>

  - <span data-ttu-id="19b9e-309">contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-309">contoso.com</span></span>
  - <span data-ttu-id="19b9e-310">contoso.com/a</span><span class="sxs-lookup"><span data-stu-id="19b9e-310">contoso.com/a</span></span>
  - <span data-ttu-id="19b9e-311">www.contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-311">www.contoso.com</span></span>
  - <span data-ttu-id="19b9e-312">www.contoso.com/b</span><span class="sxs-lookup"><span data-stu-id="19b9e-312">www.contoso.com/b</span></span>
  - <span data-ttu-id="19b9e-313">xyz.abc.contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-313">xyz.abc.contoso.com</span></span>

- <span data-ttu-id="19b9e-314">[一致しない] と [**ブロックが一致** し **ません**] を許可します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-314">**Allow not matched** and **Block not matched**:</span></span>

  - <span data-ttu-id="19b9e-315">123contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-315">123contoso.com</span></span>
  - <span data-ttu-id="19b9e-316">contoso.org</span><span class="sxs-lookup"><span data-stu-id="19b9e-316">contoso.org</span></span>

#### <a name="scenario-ip-address"></a><span data-ttu-id="19b9e-317">シナリオ: IP アドレス</span><span class="sxs-lookup"><span data-stu-id="19b9e-317">Scenario: IP address</span></span>

<span data-ttu-id="19b9e-318">**Entry**: `1.2.3.4`</span><span class="sxs-lookup"><span data-stu-id="19b9e-318">**Entry**: `1.2.3.4`</span></span>

- <span data-ttu-id="19b9e-319">Match と **Block match** を **許可する**: 1.2.3.4</span><span class="sxs-lookup"><span data-stu-id="19b9e-319">**Allow match** and **Block match**: 1.2.3.4</span></span>

- <span data-ttu-id="19b9e-320">[一致しない] と [**ブロックが一致** し **ません**] を許可します。</span><span class="sxs-lookup"><span data-stu-id="19b9e-320">**Allow not matched** and **Block not matched**:</span></span>

  - <span data-ttu-id="19b9e-321">1.2.3.4/a</span><span class="sxs-lookup"><span data-stu-id="19b9e-321">1.2.3.4/a</span></span>
  - <span data-ttu-id="19b9e-322">11.2.3.4/a</span><span class="sxs-lookup"><span data-stu-id="19b9e-322">11.2.3.4/a</span></span>

#### <a name="ip-address-with-right-wildcard"></a><span data-ttu-id="19b9e-323">右ワイルドカードを使用した IP アドレス</span><span class="sxs-lookup"><span data-stu-id="19b9e-323">IP address with right wildcard</span></span>

<span data-ttu-id="19b9e-324">**Entry**: `1.2.3.4/*`</span><span class="sxs-lookup"><span data-stu-id="19b9e-324">**Entry**: `1.2.3.4/*`</span></span>

- <span data-ttu-id="19b9e-325">一致と **ブロックの一致** を **許可する**:</span><span class="sxs-lookup"><span data-stu-id="19b9e-325">**Allow match** and **Block match**:</span></span>

  - <span data-ttu-id="19b9e-326">1.2.3.4/b</span><span class="sxs-lookup"><span data-stu-id="19b9e-326">1.2.3.4/b</span></span>
  - <span data-ttu-id="19b9e-327">1.2.3.4/baaaa</span><span class="sxs-lookup"><span data-stu-id="19b9e-327">1.2.3.4/baaaa</span></span>

### <a name="examples-of-invalid-entries"></a><span data-ttu-id="19b9e-328">無効なエントリの例</span><span class="sxs-lookup"><span data-stu-id="19b9e-328">Examples of invalid entries</span></span>

<span data-ttu-id="19b9e-329">次のエントリは無効です。</span><span class="sxs-lookup"><span data-stu-id="19b9e-329">The following entries are invalid:</span></span>

- <span data-ttu-id="19b9e-330">**ドメイン値がないか、または無効** です。</span><span class="sxs-lookup"><span data-stu-id="19b9e-330">**Missing or invalid domain values**:</span></span>

  - <span data-ttu-id="19b9e-331">拠点</span><span class="sxs-lookup"><span data-stu-id="19b9e-331">contoso</span></span>
  - <span data-ttu-id="19b9e-332">\*拠点.\*</span><span class="sxs-lookup"><span data-stu-id="19b9e-332">\*.contoso.\*</span></span>
  - <span data-ttu-id="19b9e-333">\*.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-333">\*.com</span></span>
  - <span data-ttu-id="19b9e-334">\*.pdf</span><span class="sxs-lookup"><span data-stu-id="19b9e-334">\*.pdf</span></span>

- <span data-ttu-id="19b9e-335">**文字列の場合はワイルドカード、文字間隔は使用しませ** ん。</span><span class="sxs-lookup"><span data-stu-id="19b9e-335">**Wildcard on text or without spacing characters**:</span></span>

  - <span data-ttu-id="19b9e-336">\*contoso.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-336">\*contoso.com</span></span>
  - <span data-ttu-id="19b9e-337">contoso.com\*</span><span class="sxs-lookup"><span data-stu-id="19b9e-337">contoso.com\*</span></span>
  - <span data-ttu-id="19b9e-338">\*1.2.3.4</span><span class="sxs-lookup"><span data-stu-id="19b9e-338">\*1.2.3.4</span></span>
  - <span data-ttu-id="19b9e-339">1.2.3.4\*</span><span class="sxs-lookup"><span data-stu-id="19b9e-339">1.2.3.4\*</span></span>
  - <span data-ttu-id="19b9e-340">contoso.com/a\*</span><span class="sxs-lookup"><span data-stu-id="19b9e-340">contoso.com/a\*</span></span>
  - <span data-ttu-id="19b9e-341">contoso.com/ab\*</span><span class="sxs-lookup"><span data-stu-id="19b9e-341">contoso.com/ab\*</span></span>

- <span data-ttu-id="19b9e-342">**ポートを使用した IP アドレス**:</span><span class="sxs-lookup"><span data-stu-id="19b9e-342">**IP addresses with ports**:</span></span>

  - <span data-ttu-id="19b9e-343">contoso.com:443</span><span class="sxs-lookup"><span data-stu-id="19b9e-343">contoso.com:443</span></span>
  - <span data-ttu-id="19b9e-344">abc.contoso.com:25</span><span class="sxs-lookup"><span data-stu-id="19b9e-344">abc.contoso.com:25</span></span>

- <span data-ttu-id="19b9e-345">**説明のないワイルドカード**:</span><span class="sxs-lookup"><span data-stu-id="19b9e-345">**Non-descriptive wildcards**:</span></span>

  - \*
  - <span data-ttu-id="19b9e-346">\*.\*</span><span class="sxs-lookup"><span data-stu-id="19b9e-346">\*.\*</span></span>

- <span data-ttu-id="19b9e-347">**中央のワイルドカード**:</span><span class="sxs-lookup"><span data-stu-id="19b9e-347">**Middle wildcards**:</span></span>

  - <span data-ttu-id="19b9e-348">conto \* so.com</span><span class="sxs-lookup"><span data-stu-id="19b9e-348">conto\*so.com</span></span>
  - <span data-ttu-id="19b9e-349">~ so ~ .com</span><span class="sxs-lookup"><span data-stu-id="19b9e-349">conto~so.com</span></span>

- <span data-ttu-id="19b9e-350">**2文字のワイルドカード**</span><span class="sxs-lookup"><span data-stu-id="19b9e-350">**Double wildcards**</span></span>

  - <span data-ttu-id="19b9e-351">contoso.com/\*\*</span><span class="sxs-lookup"><span data-stu-id="19b9e-351">contoso.com/\*\*</span></span>
  - <span data-ttu-id="19b9e-352">contoso.com/\*/\*</span><span class="sxs-lookup"><span data-stu-id="19b9e-352">contoso.com/\*/\*</span></span>
