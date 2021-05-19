---
title: Microsoft 365 にドメインを追加する
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365_Setup
- Adm_O365
- Adm_TOC
ms.custom:
- TopSMBIssues
- SaRA
- MSStore_Link
- okr_smb
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 6383f56d-3d09-4dcb-9b41-b5f5a5efd611
description: セットアップ ウィザードを使用して、DNS ホストに DNS レコードMicrosoft 365追加Microsoft 365管理センターにドメインを追加します。
ms.openlocfilehash: 96849e90a420dc31dbde8c55d5a1108f73f85978
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2021
ms.locfileid: "52535832"
---
# <a name="add-a-domain-to-microsoft-365"></a><span data-ttu-id="8f06e-103">Microsoft 365 にドメインを追加する</span><span class="sxs-lookup"><span data-stu-id="8f06e-103">Add a domain to Microsoft 365</span></span>

 <span data-ttu-id="8f06e-104">探している内容が見つからない場合は、**[ドメインに関する FAQ を確認Q](domains-faq.yml)** を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f06e-104">**[Check the Domains FAQ](domains-faq.yml)** if you don't find what you're looking for.</span></span> 
  
 <span data-ttu-id="8f06e-105">*追加、変更またはドメインを削除するには、[ビジネスまたはエンタープライズ プラン](https://products.office.com/business/office)の **グローバル管理者** である **必要** があります。これらの変更は、テナント全体、*カスタマイズ管理者\* または *正規ユーザー* に影響を与え、変更を加えることはできません。\*</span><span class="sxs-lookup"><span data-stu-id="8f06e-105">*To Add, modify or remove domains you **must** be a **Global Administrator** of a [business or enterprise plan](https://products.office.com/business/office). These changes affect the whole tenant, *Customized administrators* or *regular users* won't be able to make these changes.*</span></span>  

 ## <a name="add-a-domain"></a><span data-ttu-id="8f06e-106">ドメインの追加</span><span class="sxs-lookup"><span data-stu-id="8f06e-106">Add a domain</span></span>

<span data-ttu-id="8f06e-107">以下の手順に従って、ドメインの追加、セットアップ、またはセットアップの続行を行います。</span><span class="sxs-lookup"><span data-stu-id="8f06e-107">Follow these steps to add, set up, or continue setting up a domain.</span></span> 

::: moniker range="o365-worldwide"

1. <span data-ttu-id="8f06e-108"><a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> の管理センターにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="8f06e-108">Go to the admin center at <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.</span></span>

::: moniker-end
::: moniker range="o365-germany"

1. <span data-ttu-id="8f06e-109"><a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">https://portal.office.de/adminportal</a> から管理センターにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="8f06e-109">Go to the admin center at <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">https://portal.office.de/adminportal</a>.</span></span>

::: moniker-end

::: moniker range="o365-21vianet"

1. <span data-ttu-id="8f06e-110"><a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a> から管理センターにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="8f06e-110">Go to the admin center at <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.</span></span>

::: moniker-end
    
2. <span data-ttu-id="8f06e-111">[**設定**]  >  [**ドメイン**] ページの順に移動します。</span><span class="sxs-lookup"><span data-stu-id="8f06e-111">Go to the **Settings** > **Domains** page.</span></span> 

3. <span data-ttu-id="8f06e-112">[**ドメインの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8f06e-112">Select **Add domain**.</span></span>
    
4. <span data-ttu-id="8f06e-113">追加するドメインの名前を入力し、**[次へ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8f06e-113">Enter the name of the domain you want to add, then select **Next**.</span></span>
    
5. <span data-ttu-id="8f06e-114">ドメインの所有を確認する方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="8f06e-114">Choose how you want to verify that you own the domain.</span></span>
    
    1. <span data-ttu-id="8f06e-115">ドメイン レジストラーが[ドメイン接続](#domain-connect-registrars-integrating-with-microsoft-365)を使用している場合、Microsoft は、レジストラーにサインインして Microsoft 365への接続を確認することにより、[レコードを自動的に設定します](../get-help-with-domains/domain-connect.md)。</span><span class="sxs-lookup"><span data-stu-id="8f06e-115">If your domain registrar uses [Domain Connect](#domain-connect-registrars-integrating-with-microsoft-365), Microsoft [will set up your records automatically](../get-help-with-domains/domain-connect.md) by having you sign in to your registrar and confirm the connection to Microsoft 365.</span></span> <span data-ttu-id="8f06e-116">管理センターに戻り、Microsoft がドメインを自動的に確認します。</span><span class="sxs-lookup"><span data-stu-id="8f06e-116">You'll be returned to the admin center and Microsoft will then automatically verify your domain.</span></span>
    2. <span data-ttu-id="8f06e-117">TXT レコードを使用し、ドメインを検証できます。</span><span class="sxs-lookup"><span data-stu-id="8f06e-117">You can use a TXT record to verify your domain.</span></span> <span data-ttu-id="8f06e-118">これを選択し、**[次へ]** を選択すると、この DNS レコードをレジストラーの Web サイトに追加する方法が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8f06e-118">Select this and select **Next** to see instructions for how to add this DNS record to your registrar's website.</span></span> <span data-ttu-id="8f06e-119">レコードを追加すると、検証に最大 30 分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="8f06e-119">This can take up to 30 minutes to verify after you've added the record.</span></span> 
    3. <span data-ttu-id="8f06e-120">ドメインの Web サイトにテキスト ファイルを追加できます。</span><span class="sxs-lookup"><span data-stu-id="8f06e-120">You can add a text file to your domain's website.</span></span> <span data-ttu-id="8f06e-121">セットアップ ウィザードから .txt ファイルを選択してダウンロードし、そのファイルを Web サイトの最上位フォルダーにアップロードします。</span><span class="sxs-lookup"><span data-stu-id="8f06e-121">Select and download the .txt file from the setup wizard, then upload the file to your website's top level folder.</span></span> <span data-ttu-id="8f06e-122">ファイルへのサーバー相対パスは、次のようになります: `http://mydomain.com/ms39978200.txt`。</span><span class="sxs-lookup"><span data-stu-id="8f06e-122">The path to the file should look similar to: `http://mydomain.com/ms39978200.txt`.</span></span> <span data-ttu-id="8f06e-123">Web サイトでファイルを検索して、ドメインを所有していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8f06e-123">We'll confirm you own the domain by finding the file on your website.</span></span>
    
6. <span data-ttu-id="8f06e-124">Microsoft でドメインを使用するために必要な DNS 変更の方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="8f06e-124">Choose how you want to make the DNS changes required for Microsoft to use your domain.</span></span>
    
    1. <span data-ttu-id="8f06e-125">レジストラーが [ドメイン接続](#domain-connect-registrars-integrating-with-microsoft-365)をサポートしている場合は、**[DNS レコードの追加]** を選択します。Microsoft は、レジストラーにサインインしてMicrosoft 365 への接続を確認することにより、[レコードを自動的に設定します](../get-help-with-domains/domain-connect.md)。</span><span class="sxs-lookup"><span data-stu-id="8f06e-125">Choose **Add the DNS records for me** if your registrar supports [Domain Connect](#domain-connect-registrars-integrating-with-microsoft-365), and Microsoft [will set up your records automatically](../get-help-with-domains/domain-connect.md) by having you sign in to your registrar and confirm the connection to Microsoft 365.</span></span>
    2. <span data-ttu-id="8f06e-126">特定の Microsoft 365 サービスのみをドメインに追加する場合、またはここではこの手順をスキップして後で行う場合、**[DNS レコードを自分で追加する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8f06e-126">Choose **I'll add the DNS records myself** if you want to attach only specific Microsoft 365 services to your domain or if you want to skip this for now and do this later.</span></span> <span data-ttu-id="8f06e-127">**次のように、操作内容を正確に把握している場合に、このオプションを選択します。**</span><span class="sxs-lookup"><span data-stu-id="8f06e-127">**Choose this option if you know exactly what you're doing.**</span></span>

7. <span data-ttu-id="8f06e-128">*[DNS レコードを自分で追加する]* を選択した場合、**[次へ]** を選択します。そして、ドメインを設定するために、レジストラー Web サイトに追加する必要があるすべてのレコードが含まれるページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8f06e-128">If you chose to *add DNS records yourself*  , select **Next** and you'll see a page with all the records that you need to add to your registrars website to set up your domain.</span></span> 

    <span data-ttu-id="8f06e-129">ポータルでレジストラーが認識されない場合、[一般的な方法に従うことができます](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="8f06e-129">If the portal doesn't recognize your registrar, you can [follow these general instructions.](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md)</span></span>
    
    <span data-ttu-id="8f06e-130">[ホスト固有の命令](../get-help-with-domains/set-up-your-domain-host-specific-instructions.md)の一覧からお使いのホストを見つけ、手順に従って必要なすべてのレコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="8f06e-130">Check our list of [host-specific instructions](../get-help-with-domains/set-up-your-domain-host-specific-instructions.md) to find your host and follow the steps to add all the records you need.</span></span> 
    
    <span data-ttu-id="8f06e-131">ドメインの DNS ホスティング プロバイダーまたはドメイン レジストラーがわからない場合は、「[ドメイン レジストラーまたは DNS ホスティング プロバイダーを探す](../get-help-with-domains/find-your-domain-registrar.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f06e-131">If you don't know the DNS hosting provider or domain registrar for your domain, see [Find your domain registrar or DNS hosting provider](../get-help-with-domains/find-your-domain-registrar.md).</span></span>
    
    <span data-ttu-id="8f06e-132">しばらく待つ場合は、すべてのサービスの選択を解除して **[続行]** をクリックするか、前のドメイン接続手順で **[その他のオプション]** を選択して **[今はスキップ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8f06e-132">If you want to wait for later, either unselect all the services and click **Continue**, or in the previous domain connection step choose **More Options** and select **Skip this for now**.</span></span>
    
8. <span data-ttu-id="8f06e-133">**[完了]** を選択します。これで完了です!</span><span class="sxs-lookup"><span data-stu-id="8f06e-133">Select **Finish** - you're done!</span></span>

## <a name="add-or-edit-custom-dns-records"></a><span data-ttu-id="8f06e-134">カスタムの DNS レコードを追加または編集する</span><span class="sxs-lookup"><span data-stu-id="8f06e-134">Add or edit custom DNS records</span></span>

<span data-ttu-id="8f06e-135">以下の手順に従って、Web サイトまたはサード パーティ サービスのカスタム レコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="8f06e-135">Follow the steps below to add a custom record for a website or 3rd party service.</span></span>

1. <span data-ttu-id="8f06e-136"><a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>で Microsoft 365 管理センターにサインインします。</span><span class="sxs-lookup"><span data-stu-id="8f06e-136">Sign in to the Microsoft admin center at <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.</span></span>

2. <span data-ttu-id="8f06e-137">[**設定**]   >  [**ドメイン**] ページの順に移動します。</span><span class="sxs-lookup"><span data-stu-id="8f06e-137">Go to the **Settings**  > **Domains** page.</span></span>

3. <span data-ttu-id="8f06e-138">[**ドメイン**] ページで、ドメインを選びます。</span><span class="sxs-lookup"><span data-stu-id="8f06e-138">On the **Domains** page, select a domain.</span></span> 
    
4. <span data-ttu-id="8f06e-139">**[DNS 設定]** で、**[カスタム レコード]** を選択します。 次に、**[新しいカスタム レコード]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8f06e-139">Under **DNS settings**, select **Custom Records**; then select **New custom record**.</span></span>

5. <span data-ttu-id="8f06e-140">追加する DNS レコードの種類を選択し、新しいレコードの情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="8f06e-140">Select the type of DNS record you want to add and type the information for the new record.</span></span>
    
6. <span data-ttu-id="8f06e-141">**[保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="8f06e-141">Select **Save**.</span></span>

## <a name="registrars-with-domain-connect"></a><span data-ttu-id="8f06e-142">ドメイン接続を使用するレジストラ</span><span class="sxs-lookup"><span data-stu-id="8f06e-142">Registrars with Domain Connect</span></span>

<span data-ttu-id="8f06e-143">[ドメイン接続](https://www.domainconnect.org/) 対応のレジストラを使用すると、3 ステップの手順を使って、数分でドメインを Microsoft 365 に追加できます。</span><span class="sxs-lookup"><span data-stu-id="8f06e-143">[Domain Connect](https://www.domainconnect.org/) enabled registrars let you add your domain to Microsoft 365 in a three-step process that takes minutes.</span></span> 
  
<span data-ttu-id="8f06e-144">ウィザードでは、ドメインを所有していることを確認してから、ドメインのレコードを自動的に設定するため、Microsoft 365 にメールが送信されます。Teams などの他の Microsoft 365 サービスはドメインを操作します。</span><span class="sxs-lookup"><span data-stu-id="8f06e-144">In the wizard, we'll just confirm that you own the domain, and then automatically set up your domain's records, so email comes to Microsoft 365 and other Microsoft 365 services, like Teams, work with your domain.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8f06e-145">セットアップ ウィザードを開始する前に、ブラウザーのポップアップ ブロック機能が無効になっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8f06e-145">Make sure you disable any popup blockers in your browser before you start the setup wizard.</span></span>
  
### <a name="domain-connect-registrars-integrating-with-microsoft-365"></a><span data-ttu-id="8f06e-146">Microsoft 365 と統合するドメイン接続レジストラ</span><span class="sxs-lookup"><span data-stu-id="8f06e-146">Domain Connect registrars integrating with Microsoft 365</span></span>

- [<span data-ttu-id="8f06e-147">1&amp;1 IONOS</span><span class="sxs-lookup"><span data-stu-id="8f06e-147">1&amp;1 IONOS</span></span>](https://www.1and1.com/)
- [<span data-ttu-id="8f06e-148">EuroDNS</span><span class="sxs-lookup"><span data-stu-id="8f06e-148">EuroDNS</span></span>](https://www.eurodns.com/)
- [<span data-ttu-id="8f06e-149">Cloudflare</span><span class="sxs-lookup"><span data-stu-id="8f06e-149">Cloudflare</span></span>](https://www.cloudflare.com/)
- [<span data-ttu-id="8f06e-150">Go Daddy</span><span class="sxs-lookup"><span data-stu-id="8f06e-150">GoDaddy</span></span>](https://www.godaddy.com/)
- [<span data-ttu-id="8f06e-151">WordPress.com</span><span class="sxs-lookup"><span data-stu-id="8f06e-151">WordPress.com</span></span>](https://wordpress.com/)
- [<span data-ttu-id="8f06e-152">Plesk</span><span class="sxs-lookup"><span data-stu-id="8f06e-152">Plesk</span></span>](https://www.plesk.com/)
- [<span data-ttu-id="8f06e-153">MediaTemple</span><span class="sxs-lookup"><span data-stu-id="8f06e-153">MediaTemple</span></span>](https://mediatemple.net/)
- <span data-ttu-id="8f06e-154">SecureServer または WildWestDomains (SecureServer DNS ホスティングを使用する GoDaddy リセラー)</span><span class="sxs-lookup"><span data-stu-id="8f06e-154">SecureServer or WildWestDomains (GoDaddy resellers using SecureServer DNS hosting)</span></span>
    - <span data-ttu-id="8f06e-155">例:</span><span class="sxs-lookup"><span data-stu-id="8f06e-155">Examples:</span></span>
        - [<span data-ttu-id="8f06e-156">DomainsPricedRight</span><span class="sxs-lookup"><span data-stu-id="8f06e-156">DomainsPricedRight</span></span>](https://www.domainspricedright.com/products/domain-registration)
        - [<span data-ttu-id="8f06e-157">DomainRightNow</span><span class="sxs-lookup"><span data-stu-id="8f06e-157">DomainRightNow</span></span>](https://www.domainrightnow.com/)

### <a name="what-happens-to-my-email-and-website"></a><span data-ttu-id="8f06e-158">メールと Web サイトはどうなりますか?</span><span class="sxs-lookup"><span data-stu-id="8f06e-158">What happens to my email and website?</span></span>

<span data-ttu-id="8f06e-159">セットアップを終了すると、ユーザーのドメインの MX レコードが Microsoft 365 を指定されるように更新され、そのドメイン宛てのすべてのメールが Microsoft 365 に送信されるようになります。</span><span class="sxs-lookup"><span data-stu-id="8f06e-159">After you finish setup, the MX record for your domain is updated to point to Microsoft 365 and all email for your domain will start coming to Microsoft 365.</span></span> <span data-ttu-id="8f06e-160">ユーザーのドメインにメールを持つすべてのユーザーが Microsoft 365 に追加され、メールボックスが設定されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8f06e-160">Make sure you've added users and set up mailboxes in Microsoft 365 for everyone who gets email on your domain!</span></span>
  
<span data-ttu-id="8f06e-161">ビジネスで使用している Web サイトがある場合は、そのままの場所で稼働し続けます。</span><span class="sxs-lookup"><span data-stu-id="8f06e-161">If you have a website that you use with your business, it will keep working where it is.</span></span> <span data-ttu-id="8f06e-162">ドメイン接続 のセットアップ手順は、自分の Web サイトには影響しません。</span><span class="sxs-lookup"><span data-stu-id="8f06e-162">The Domain Connect setup steps don't affect your website.</span></span>

## <a name="related-content"></a><span data-ttu-id="8f06e-163">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="8f06e-163">Related content</span></span>

<span data-ttu-id="8f06e-164">[ドメインに関する FAQ](domains-faq.yml) (記事)</span><span class="sxs-lookup"><span data-stu-id="8f06e-164">[Domains FAQ](domains-faq.yml) (article)</span></span>

[<span data-ttu-id="8f06e-165">ドメインとは</span><span class="sxs-lookup"><span data-stu-id="8f06e-165">What is a domain?</span></span>](../get-help-with-domains/what-is-a-domain.md) <span data-ttu-id="8f06e-166">(記事)</span><span class="sxs-lookup"><span data-stu-id="8f06e-166">(article)</span></span>

<span data-ttu-id="8f06e-167">[ドメイン名を購入する (Microsoft 365)](../get-help-with-domains/buy-a-domain-name.md)</span><span class="sxs-lookup"><span data-stu-id="8f06e-167">[Buy a domain name in Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (article)</span></span>

<span data-ttu-id="8f06e-168">[ドメインを設定する](../get-help-with-domains/set-up-your-domain-host-specific-instructions.md) (記事)</span><span class="sxs-lookup"><span data-stu-id="8f06e-168">[Set up your domain](../get-help-with-domains/set-up-your-domain-host-specific-instructions.md) (article)</span></span>