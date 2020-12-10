---
title: グループとユーザーを作成する - 選挙運動の開発/テスト環境用
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: '要約: 選挙運動の開発/テスト環境向けのユーザーとグループで Office 365 と Enterprise Mobility + Security (EMS) の試用版サブスクリプションを作成します。'
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1fac15cc0b2a512745e0538ec689bd5f17555419
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "49614908"
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a><span data-ttu-id="66af2-103">選挙運動の開発/テスト環境用にグループとユーザーを構成する</span><span class="sxs-lookup"><span data-stu-id="66af2-103">Configure groups and users for a political campaign dev/test environment</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


 <span data-ttu-id="66af2-104">**要約:** 選挙運動の開発/テスト環境向けのユーザーとグループで Office 365 と Enterprise Mobility + Security (EMS) の試用版サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="66af2-104">**Summary:** Create Office 365 and Enterprise Mobility + Security (EMS) trial subscriptions with users and groups for a political campaign dev/test environment.</span></span>

<span data-ttu-id="66af2-105">簡略化されたユーザー アカウントとグループを含む開発/テスト環境を「[選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)」ソリューション用に作成するには、この資料の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="66af2-105">Use the instructions in this article to create a dev/test environment that includes simplified user accounts and groups for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution.</span></span>

## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="66af2-106">フェーズ 1: Office 365 の開発/テスト環境を作成する</span><span class="sxs-lookup"><span data-stu-id="66af2-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="66af2-107">このフェーズでは、選挙運動を務める架空の組織用に Office 365 E5 と Enterprise Mobility + Security (EMS) E5 の試用版サブスクリプションを取得します。</span><span class="sxs-lookup"><span data-stu-id="66af2-107">In this phase, you obtain trial subscriptions for Office 365 E5 and Enterprise Mobility + Security (EMS) E5 for a fictional organization that represents a political campaign.</span></span>

<span data-ttu-id="66af2-108">まず、「[軽量な基本構成](https://docs.microsoft.com/microsoft-365/enterprise/lightweight-base-configuration-microsoft-365-enterprise)」の **フェーズ 2** の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="66af2-108">First, follow the instructions in **Phase 2** of [The lightweight base configuration](https://docs.microsoft.com/microsoft-365/enterprise/lightweight-base-configuration-microsoft-365-enterprise).</span></span>

<span data-ttu-id="66af2-109">次に、EMS E5 試用版サブスクリプションにサインアップして、試用版サブスクリプションと同じ組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="66af2-109">Next, sign up for the EMS E5 trial subscription and add it to the same organization as your trial subscription.</span></span>

1. <span data-ttu-id="66af2-110">必要に応じて、試用版サブスクリプション用の全体管理者アカウントの資格情報で管理センターにサインインします。</span><span class="sxs-lookup"><span data-stu-id="66af2-110">If needed, sign in to the admin center with the credentials of the global administrator account of your trial subscription.</span></span> <span data-ttu-id="66af2-111">詳細については、「[サインインする場所](https://support.microsoft.com/office/e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66af2-111">For help, see [Where to sign in](https://support.microsoft.com/office/e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>

2. <span data-ttu-id="66af2-112">**[管理者]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-112">Click the **Admin** tile.</span></span>

3. <span data-ttu-id="66af2-113">ブラウザーの **[Microsoft 365 管理センター]** タブの、左側のナビゲーションで **[請求] > [サービスを購入する]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-113">On the **Microsoft 365 admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>

4. <span data-ttu-id="66af2-p102">**[サービスを購入]** ページで、 **[Enterprise Mobility + Security E5]** 項目を探します。その項目の上にマウス ポインターを移動させ、 **[無料試用版を起動する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>

5. <span data-ttu-id="66af2-116">**[注文の確認]** ページで、 **[今すぐ実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-116">On the **Confirm your order** page, click **Try now**.</span></span>

6. <span data-ttu-id="66af2-117">**[注文の受領書]** ページで、**[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-117">On the **Order receipt** page, click **Continue**.</span></span>

<span data-ttu-id="66af2-118">次に、全体管理者アカウントの EMS E5 ライセンスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="66af2-118">Next, enable the EMS E5 license for your global administrator account.</span></span>

1. <span data-ttu-id="66af2-119">ブラウザーの **[Microsoft 365 管理センター]** タブの左側のナビゲーションで **[ユーザー] > [アクティブなユーザー]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-119">On the **Microsoft 365 admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>

2. <span data-ttu-id="66af2-120">全体管理者アカウントをクリックしてから、 **[製品ライセンス]** で **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-120">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>

3. <span data-ttu-id="66af2-121">**[製品ライセンス]** ウィンドウで、 **Enterprise Mobility + Security E5** の製品ライセンスを **[オン]** にして、 **[保存]** をクリックしてから、 **[閉じる]** を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-121">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>

## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a><span data-ttu-id="66af2-122">フェーズ 2: Azure Active Directory (AD) グループを作成して構成する</span><span class="sxs-lookup"><span data-stu-id="66af2-122">Phase 2: Create and configure your Azure Active Directory (AD) groups</span></span>

<span data-ttu-id="66af2-123">このフェーズでは、選挙運動用に Azure AD グループを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="66af2-123">In this phase, you create and configure the Azure AD groups for your campaign.</span></span>

<span data-ttu-id="66af2-124">最初に、Azure portal で一般的な選挙運動グループのセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="66af2-124">First, create a set of groups for a typical political campaign with the Azure portal.</span></span>

1. <span data-ttu-id="66af2-p103">ブラウザーの別タブで、Azure portal (<https://portal.azure.com>) に移動します。必要に応じて、Office 365 E5 試用版サブスクリプション用の全体管理者アカウントの資格情報でサインインします。</span><span class="sxs-lookup"><span data-stu-id="66af2-p103">On a separate tab in your browser, go to the Azure portal at <https://portal.azure.com>. If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>

2. <span data-ttu-id="66af2-127">Azure portal で **[Azure Active Directory] > [ユーザーとグループ] > [すべてのグループ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-127">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>

3. <span data-ttu-id="66af2-128">このリストのグループ名ごとに、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="66af2-128">Do the following steps for each group name in this list:</span></span>

   - <span data-ttu-id="66af2-129">戦略的シニア スタッフ</span><span class="sxs-lookup"><span data-stu-id="66af2-129">Senior and strategic staff</span></span>

   - <span data-ttu-id="66af2-130">IT スタッフ</span><span class="sxs-lookup"><span data-stu-id="66af2-130">IT staff</span></span>

   - <span data-ttu-id="66af2-131">分析スタッフ</span><span class="sxs-lookup"><span data-stu-id="66af2-131">Analytics staff</span></span>

   - <span data-ttu-id="66af2-132">正規のコア スタッフ</span><span class="sxs-lookup"><span data-stu-id="66af2-132">Regular core staff</span></span>

   - <span data-ttu-id="66af2-133">運用スタッフ</span><span class="sxs-lookup"><span data-stu-id="66af2-133">Operations staff</span></span>

   - <span data-ttu-id="66af2-134">フィールド スタッフ</span><span class="sxs-lookup"><span data-stu-id="66af2-134">Field staff</span></span>

1. <span data-ttu-id="66af2-135">**[すべてのグループ]** ブレードで、**[+ 新しいグループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-135">On the **All groups** blade, click **+ New group**.</span></span>

2. <span data-ttu-id="66af2-136">リストにあるグループ名を **[名前]** に入力します。</span><span class="sxs-lookup"><span data-stu-id="66af2-136">Type the group name from the list in **Name**.</span></span>

3. <span data-ttu-id="66af2-137">**[メンバーシップ]** で **[動的ユーザー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="66af2-137">Select **Dynamic user** in **Membership**.</span></span>

4. <span data-ttu-id="66af2-138">**[Office の機能を有効にする]** で **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-138">Click **Yes** for **Enable Office features**.</span></span>

5. <span data-ttu-id="66af2-139">**[動的クエリの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-139">Click **Add dynamic query**.</span></span>

6. <span data-ttu-id="66af2-140">**[ユーザーを追加する場所]** で、**[部署]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="66af2-140">In **Add users where**, select **department**.</span></span>

7. <span data-ttu-id="66af2-141">次のフィールドで、**[等しい]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="66af2-141">In the next field, select **Equals**.</span></span>

8. <span data-ttu-id="66af2-142">次のフィールドで、リストにあるグループ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="66af2-142">In the next field, type the group name from the list.</span></span>

9. <span data-ttu-id="66af2-143">**[クエリの追加]** をクリックしてから、**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-143">Click **Add query**, and then click **Create**.</span></span>

10. <span data-ttu-id="66af2-144">**[ユーザーとグループ - すべてのグループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-144">Click **Users and groups - All groups**.</span></span>

<span data-ttu-id="66af2-145">次に、メンバーに Office 365 E5 および EMS E5 のライセンスが自動的に割り当てられるようにグループを構成します。</span><span class="sxs-lookup"><span data-stu-id="66af2-145">Next, you configure the groups so that members are automatically assigned Office 365 E5 and EMS E5 licenses.</span></span>

1. <span data-ttu-id="66af2-146">Azure portal で **[Azure Active Directory] > [ライセンス] > [すべての製品]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-146">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>

2. <span data-ttu-id="66af2-147">一覧で、**[Enterprise Mobility + Security E5]** と **[Office 365 Enterprise E5]** を選択して、**[+ 割り当て]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-147">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **+ Assign**.</span></span>

3. <span data-ttu-id="66af2-148">**[ライセンスの割り当て]** ブレードで、**[ユーザーとグループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-148">In the **Assign license** blade, click **Users and groups**.</span></span>

4. <span data-ttu-id="66af2-149">グループの一覧で、次を選択します。</span><span class="sxs-lookup"><span data-stu-id="66af2-149">In the list of groups, select the following:</span></span>

   - <span data-ttu-id="66af2-150">分析スタッフ</span><span class="sxs-lookup"><span data-stu-id="66af2-150">Analytics staff</span></span>

   - <span data-ttu-id="66af2-151">フィールド スタッフ</span><span class="sxs-lookup"><span data-stu-id="66af2-151">Field staff</span></span>

   - <span data-ttu-id="66af2-152">IT スタッフ</span><span class="sxs-lookup"><span data-stu-id="66af2-152">IT staff</span></span>

   - <span data-ttu-id="66af2-153">運用スタッフ</span><span class="sxs-lookup"><span data-stu-id="66af2-153">Operations staff</span></span>

   - <span data-ttu-id="66af2-154">正規のコア スタッフ</span><span class="sxs-lookup"><span data-stu-id="66af2-154">Regular core staff</span></span>

   - <span data-ttu-id="66af2-155">戦略的シニア スタッフ</span><span class="sxs-lookup"><span data-stu-id="66af2-155">Senior and strategic staff</span></span>

5. <span data-ttu-id="66af2-156">**[選択]** をクリックし、**[割り当て]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-156">Click **Select**, and then click **Assign**.</span></span>

6. <span data-ttu-id="66af2-157">ブラウザーの [Azure Portal] タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="66af2-157">Close the Azure portal tab in your browser.</span></span>

## <a name="phase-3-add-your-user-accounts"></a><span data-ttu-id="66af2-158">フェーズ 3:ユーザー アカウントを追加する</span><span class="sxs-lookup"><span data-stu-id="66af2-158">Phase 3: Add your user accounts</span></span>

<span data-ttu-id="66af2-159">このフェーズでは、選挙運動のサンプル ユーザー アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="66af2-159">In this phase, you add the example user accounts for your political campaign.</span></span>

<span data-ttu-id="66af2-160">まず、[Azure Active Directory PowerShell for Graph モジュールに接続](https://docs.microsoft.com/microsoft-365/enterprise/connect-to-microsoft-365-powershell)します。</span><span class="sxs-lookup"><span data-stu-id="66af2-160">First, you [Connect with the Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/microsoft-365/enterprise/connect-to-microsoft-365-powershell).</span></span>

<span data-ttu-id="66af2-161">次に、組織名、場所、および共通のパスワードを入力し、PowerShell コマンド プロンプトまたは Integrated Scripting Environment (ISE) からこれらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="66af2-161">Next, you fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE):</span></span>

```powershell
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1")
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2")
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1")
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2")
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1")
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1")
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
```

> [!IMPORTANT]
> <span data-ttu-id="66af2-p104">ここでは共通のパスワードを使用することで、自動化と、開発/テスト環境の構成を容易にしています。運用サブスクリプションでの使用はお勧めしません。これらの新しいユーザー アカウントでサインインするときに、パスワードの変更を求めるダイアログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="66af2-p104">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions. As you sign in with each of these new user accounts, you will be prompted to change the password.</span></span>

<span data-ttu-id="66af2-165">動的グループのメンバーシップとグループ ベースのライセンスが正常に機能していることを確認するには、次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="66af2-165">Use these steps to verify that dynamic group membership and group-based licensing are working correctly.</span></span>

1. <span data-ttu-id="66af2-166">ブラウザーの **[Microsoft Office Home]** タブで、 **[管理者]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-166">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>

2. <span data-ttu-id="66af2-167">ブラウザーの新しい **Microsoft 365 管理センター** のタブで、**[ユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-167">From the new **Microsoft 365 admin center** tab of your browser, click **Users**.</span></span>

3. <span data-ttu-id="66af2-168">ユーザーの一覧で **[候補]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="66af2-168">In the list of users, click **Candidate**.</span></span>

4. <span data-ttu-id="66af2-169">**[候補]** ユーザー アカウントのプロパティを一覧表示するウィンドウで、次を確認します。</span><span class="sxs-lookup"><span data-stu-id="66af2-169">In the pane that lists the properties of the **Candidate** user account, verify that:</span></span>

   - <span data-ttu-id="66af2-170">**[戦略的シニア スタッフ]** グループのメンバーである (**[グループ メンバーシップ]** 内)。</span><span class="sxs-lookup"><span data-stu-id="66af2-170">It is a member of the **Senior and strategic staff** group (in **Group memberships**).</span></span>

   - <span data-ttu-id="66af2-171">**[Enterprise Mobility + Security E5]** と **[Office 365 Enterprise E5]** のライセンスが割り当てられている (**[製品ライセンス]** 内)。</span><span class="sxs-lookup"><span data-stu-id="66af2-171">It has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>

5. <span data-ttu-id="66af2-172">**[候補]** ユーザー アカウントのウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="66af2-172">Close the **Candidate** user account pane.</span></span>

## <a name="record-values-for-future-reference"></a><span data-ttu-id="66af2-173">将来の参考のために値を記録する</span><span class="sxs-lookup"><span data-stu-id="66af2-173">Record values for future reference</span></span>

<span data-ttu-id="66af2-174">この開発/テスト環境で Office 365 と EMS の試用版サブスクリプションを使用するために、これらの値を記録します。</span><span class="sxs-lookup"><span data-stu-id="66af2-174">Record these values for working with the Office 365 and EMS trial subscriptions for this dev/test environment:</span></span>

- <span data-ttu-id="66af2-175">試用版サブスクリプションの組織名</span><span class="sxs-lookup"><span data-stu-id="66af2-175">Your trial subscription organization name:</span></span> ![下線](../../media/Common-Images/TableLine.png)

  <span data-ttu-id="66af2-177">たとえば、試用版サブスクリプションのドメイン名が contoso.onmicrosoft.com である場合、組織名は「contoso」です。</span><span class="sxs-lookup"><span data-stu-id="66af2-177">For example, for the trial subscription domain name of contoso.onmicrosoft.com, the organization name is "contoso".</span></span>

- <span data-ttu-id="66af2-178">グローバル管理者名:</span><span class="sxs-lookup"><span data-stu-id="66af2-178">The global administrator name:</span></span> ![下線](../../media/Common-Images/TableLine.png)<span data-ttu-id="66af2-180">.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="66af2-180">.onmicrosoft.com</span></span>

  <span data-ttu-id="66af2-181">このアカウントのパスワードや、その他のユーザー アカウントの共通のパスワードを安全な場所に記録します。</span><span class="sxs-lookup"><span data-stu-id="66af2-181">Record the password for this account and the common initial password for the other user accounts in a secure location.</span></span>

## <a name="next-step"></a><span data-ttu-id="66af2-182">次の手順</span><span class="sxs-lookup"><span data-stu-id="66af2-182">Next step</span></span>

<span data-ttu-id="66af2-183">[Create team sites in a political campaign dev/test environment](create-team-sites-in-a-political-campaign-dev-test-environment.md) を使用して、この開発/テスト環境で 4 つの異なる種類の SharePoint Online チーム サイトを作成します。</span><span class="sxs-lookup"><span data-stu-id="66af2-183">Build the four different types of SharePoint Online team sites in this dev/test environment with [Create team sites in a political campaign dev/test environment](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="66af2-184">関連項目</span><span class="sxs-lookup"><span data-stu-id="66af2-184">See also</span></span>

[<span data-ttu-id="66af2-185">選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス</span><span class="sxs-lookup"><span data-stu-id="66af2-185">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)

[<span data-ttu-id="66af2-186">選挙運動用の開発/テスト環境でチーム サイトを作成する</span><span class="sxs-lookup"><span data-stu-id="66af2-186">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)

[<span data-ttu-id="66af2-187">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="66af2-187">Cloud adoption Test Lab Guides (TLGs)</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/cloud-adoption-test-lab-guides-tlgs)

[<span data-ttu-id="66af2-188">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="66af2-188">Cloud adoption and hybrid solutions</span></span>](https://docs.microsoft.com/office365/enterprise/cloud-adoption-and-hybrid-solutions)
