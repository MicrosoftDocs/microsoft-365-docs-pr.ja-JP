---
title: GoDaddy で Microsoft 用の DNS レコードを作成する
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
- Adm_O365
- Adm_NonTOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f40a9185-b6d5-4a80-bb31-aa3bb0cab48a
description: ドメインを確認し、GoDaddy for Microsoft でメール、Skype for Business Online、その他のサービスの DNS レコードを設定する方法について説明します。
ms.openlocfilehash: 2b53985dc17f3d124ec2b37dbf0047bce229385c
ms.sourcegitcommit: eac5d9f759f290d3c51cafaf335a1a1c43ded927
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "50126451"
---
# <a name="create-dns-records-at-godaddy-for-microsoft"></a><span data-ttu-id="6f9c1-103">GoDaddy で Microsoft 用の DNS レコードを作成する</span><span class="sxs-lookup"><span data-stu-id="6f9c1-103">Create DNS records at GoDaddy for Microsoft</span></span>

 <span data-ttu-id="6f9c1-104">**探している内容が見つからない場合は、[ドメインに関する FAQ を確認](../setup/domains-faq.yml)** してください。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-104">**[Check the Domains FAQ](../setup/domains-faq.yml)** if you don't find what you're looking for.</span></span>

<span data-ttu-id="6f9c1-105">使用している DNS ホスティング プロバイダーが GoDaddy の場合は、この記事に示す手順に従い、ドメインを確認して、メールや Skype for Business Online などの DNS レコードを設定します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-105">If GoDaddy is your DNS hosting provider, follow the steps in this article to verify your domain and set up DNS records for email, Skype for Business Online, and so on.</span></span>

<span data-ttu-id="6f9c1-106">これらのレコードを GoDaddy で追加すると、ドメインは Microsoft サービスで動作する設定に設定されます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-106">After you add these records at GoDaddy, your domain will be set up to work with Microsoft services.</span></span>

> [!NOTE]
> <span data-ttu-id="6f9c1-p101">通常、DNS の変更が有効になるのに 15 分ほどかかります。ただし、インターネットの DNS システム全体を更新する変更の場合、さらに長くかかることもあります。DNS レコードの追加でメール フローなどに問題が発生した場合は、「[ドメイン名または DNS レコードの変更後の問題に関するトラブルシューティング](../get-help-with-domains/find-and-fix-issues.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-p101">Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).</span></span>

## <a name="add-a-txt-record-for-verification"></a><span data-ttu-id="6f9c1-110">確認のための TXT レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="6f9c1-110">Add a TXT record for verification</span></span>
<span data-ttu-id="6f9c1-111"><a name="BKMK_verify"> </a></span><span class="sxs-lookup"><span data-stu-id="6f9c1-111"><a name="BKMK_verify"> </a></span></span>

<span data-ttu-id="6f9c1-p102">Microsoft のドメインを使うには、ドメインを所有していることを確認する必要があります。自分のドメイン レジストラーで自分のアカウントにログインし、DNS レコードを作成することができれば、Microsoft に対してドメインを所有していることを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-p102">Before you use your domain with Microsoft, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.</span></span>

> [!NOTE]
> <span data-ttu-id="6f9c1-p103">このレコードは、ドメインを所有していることを確認するためだけに使用されます。その他には影響しません。 必要に応じて、後で削除することができます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-p103">This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.</span></span>

<span data-ttu-id="6f9c1-116">以下の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-116">Follow the steps below.</span></span>

1. <span data-ttu-id="6f9c1-p104">まず、[このリンク](https://account.godaddy.com/products/?go_redirect=disabled)を使って GoDaddy でドメイン ページにアクセスします。ログインするように求められます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-p104">To get started, go to your domains page at GoDaddy by using [this link](https://account.godaddy.com/products/?go_redirect=disabled). You'll be prompted to log in.</span></span>

    ![GoDaddy-BP-Configure-1-1](../../media/d6833ec7-9904-43fd-a877-7c663e5f5c25.png)

2. <span data-ttu-id="6f9c1-120">[ **ドメイン] で**、編集するドメインの下の DNS を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-120">Under **Domains**, select DNS under the domain that you want to edit.</span></span>

    ![GoDaddy-BP-Configure-1-2](../../media/dns/56528038-94b6ac00-651c-11e9-8874-12db60cc7ea6.png)

3. <span data-ttu-id="6f9c1-122">**[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-122">Select **Add**.</span></span>

    ![GoDaddy-BP-Configure-1-4](../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png)

4. <span data-ttu-id="6f9c1-124">ドロップダウン リストから [ **TXT (Text)**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-124">Choose **TXT (Text)** from the drop-down list.</span></span> <span data-ttu-id="6f9c1-125">新規レコードのボックスに、次の表の値を入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-125">In the boxes for the new record, type or copy and paste the values from the following table.</span></span>

    |<span data-ttu-id="6f9c1-126">**Record type**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-126">**Record type**</span></span> |<span data-ttu-id="6f9c1-127">**Host**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-127">**Host**</span></span>|<span data-ttu-id="6f9c1-128">**TXT Value**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-128">**TXT Value**</span></span>|<span data-ttu-id="6f9c1-129">**TTL**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-129">**TTL**</span></span> |
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="6f9c1-130">TXT (テキスト)</span><span class="sxs-lookup"><span data-stu-id="6f9c1-130">TXT (Text)</span></span>|@|<span data-ttu-id="6f9c1-131">MS=ms *XXXXXXXX*</span><span class="sxs-lookup"><span data-stu-id="6f9c1-131">MS=ms *XXXXXXXX*</span></span><br><span data-ttu-id="6f9c1-132">**注**: これは例です。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-132">**Note**: This is an example.</span></span> <span data-ttu-id="6f9c1-133">この表から **[宛先またはポイント先のアドレス]** の値を指定してください。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-133">Use your specific **Destination or Points to Address** value here, from the table.</span></span> [<span data-ttu-id="6f9c1-134">確認する方法</span><span class="sxs-lookup"><span data-stu-id="6f9c1-134">How do I find this?</span></span>](../get-help-with-domains/information-for-dns-records.md)|<span data-ttu-id="6f9c1-135">1 hour</span><span class="sxs-lookup"><span data-stu-id="6f9c1-135">1 hour</span></span>  <br><span data-ttu-id="6f9c1-136">(ドロップダウン リストから値を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-136">(Select a value from the drop-down list.)</span></span>|

      ![GoDaddy-BP-Verify-1-0](../../media/dns/56526870-d6465780-651a-11e9-9cf0-d6fff71e2f62.png)

5. <span data-ttu-id="6f9c1-138">**[保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-138">Select **Save**.</span></span>

6. <span data-ttu-id="6f9c1-139">数分待つと、続行できます。この間、作成したレコードがインターネット全体で更新されます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-139">Wait a few minutes before you continue, so that the record you just created can update across the Internet.</span></span>

<span data-ttu-id="6f9c1-140">これで、ドメイン レジストラーのサイトでレコードが追加されました。Microsoft に戻り、レコードをリクエストします。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-140">Now that you've added the record at your domain registrar's site, you'll go back to Microsoft and request the record.</span></span>

<span data-ttu-id="6f9c1-141">Microsoft で正しい TXT レコードが見つかった場合、ドメインは確認済みとなります。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-141">When Microsoft finds the correct TXT record, your domain is verified.</span></span>
  
1. <span data-ttu-id="6f9c1-142">Microsoft 管理センターで、**[設定]** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">[ドメイン]</a> ページの順に移動します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-142">In the Microsoft admin center, go to the **Settings** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domains</a> page.</span></span>

    
2. <span data-ttu-id="6f9c1-143">**[ドメイン]** ページで、確認するドメインを選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-143">On the **Domains** page, select the domain that you are verifying.</span></span> 
    
    
  
3. <span data-ttu-id="6f9c1-144">**[セットアップ]** ページで、**[セットアップの開始]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-144">On the **Setup** page, select **Start setup**.</span></span>



4. <span data-ttu-id="6f9c1-145">**[ドメインの確認]** ページで、**[確認]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-145">On the **Verify domain** page, select **Verify**.</span></span>



> [!NOTE]
>  <span data-ttu-id="6f9c1-p107">通常、DNS の変更が有効になるのに 15 分ほどかかります。ただし、インターネットの DNS システム全体を更新する変更の場合、さらに長くかかることもあります。DNS レコードの追加でメール フローなどに問題が発生した場合は、「[ドメイン名または DNS レコードの変更後の問題に関するトラブルシューティング](../get-help-with-domains/find-and-fix-issues.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-p107">Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).</span></span>

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a><span data-ttu-id="6f9c1-149">MX レコードを追加して、自分のドメインのメールが Microsoft に届くようにする</span><span class="sxs-lookup"><span data-stu-id="6f9c1-149">Add an MX record so email for your domain will come to Microsoft</span></span>
<span data-ttu-id="6f9c1-150"><a name="BKMK_add_MX"> </a></span><span class="sxs-lookup"><span data-stu-id="6f9c1-150"><a name="BKMK_add_MX"> </a></span></span>

<span data-ttu-id="6f9c1-151">以下の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-151">Follow the steps below.</span></span>

1. <span data-ttu-id="6f9c1-p108">まず、[このリンク](https://account.godaddy.com/products/?go_redirect=disabled)を使って GoDaddy でドメイン ページにアクセスします。ログインするように求められます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-p108">To get started, go to your domains page at GoDaddy by using [this link](https://account.godaddy.com/products/?go_redirect=disabled). You'll be prompted to log in.</span></span>

    ![GoDaddy-BP-Configure-1-1](../../media/d6833ec7-9904-43fd-a877-7c663e5f5c25.png)

2. <span data-ttu-id="6f9c1-155">[ **ドメイン] で**、編集するドメインの下の DNS を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-155">Under **Domains**, select DNS under the domain that you want to edit.</span></span>

    ![GoDaddy-BP-Configure-1-2](../../media/dns/56528038-94b6ac00-651c-11e9-8874-12db60cc7ea6.png)

3. <span data-ttu-id="6f9c1-157">**[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-157">Select **Add**.</span></span>

    ![GoDaddy-BP-Configure-1-4](../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png)

4. <span data-ttu-id="6f9c1-159">ドロップダウン リストから [ **MX (Mail Exchanger)**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-159">Choose **MX (Mail Exchanger)** from the drop-down list.</span></span>

    ![GoDaddy-BP-Configure-2-0](../../media/dns/56528642-85842e00-651d-11e9-8dd8-217f468f9a18.png)

5. <span data-ttu-id="6f9c1-161">新規レコードのボックスに、次の表の値を入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-161">In the boxes for the new record, type or copy and paste the values from the following table.</span></span>

    <span data-ttu-id="6f9c1-162">(ドロップダウン リスト **から TTL** 値を選択します)。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-162">(Choose the **TTL** value from the drop-down list.)</span></span>

    |<span data-ttu-id="6f9c1-163">**Record type**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-163">**Record type**</span></span>|<span data-ttu-id="6f9c1-164">**Host**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-164">**Host**</span></span>|<span data-ttu-id="6f9c1-165">**Points to**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-165">**Points to**</span></span>|<span data-ttu-id="6f9c1-166">**Priority**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-166">**Priority**</span></span>|<span data-ttu-id="6f9c1-167">**TTL**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-167">**TTL**</span></span>|
    |:-----|:-----|:-----|:-----|:-----|
    |<span data-ttu-id="6f9c1-168">MX (Mail Exchanger)</span><span class="sxs-lookup"><span data-stu-id="6f9c1-168">MX (Mail Exchanger)</span></span>  <br/> |@  <br/> | <span data-ttu-id="6f9c1-169">*\<domain-key\>*  .mail.protection.outlook.com</span><span class="sxs-lookup"><span data-stu-id="6f9c1-169">*\<domain-key\>*  .mail.protection.outlook.com</span></span>  <br/> <span data-ttu-id="6f9c1-170">**注:** Microsoft アカウント  *\<domain-key\>*  からユーザーを取得します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-170">**Note:** Get your  *\<domain-key\>*  from your Microsoft account.</span></span>           [<span data-ttu-id="6f9c1-171">確認する方法</span><span class="sxs-lookup"><span data-stu-id="6f9c1-171">How do I find this?</span></span>](../get-help-with-domains/information-for-dns-records.md)          |<span data-ttu-id="6f9c1-172">10 </span><span class="sxs-lookup"><span data-stu-id="6f9c1-172">10</span></span>  <br/> <span data-ttu-id="6f9c1-173">優先度の詳細については、「[MX 優先度とは何か](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-173">For more information about priority, see [What is MX priority?](https://docs.microsoft.com/microsoft-365/admin/setup/domains-faq)</span></span> <br/> |<span data-ttu-id="6f9c1-174">1 hour</span><span class="sxs-lookup"><span data-stu-id="6f9c1-174">1 hour</span></span>  <br/> |

6. <span data-ttu-id="6f9c1-175">**[保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-175">Select **Save**.</span></span>

## <a name="add-the-cname-records-that-are-required-for-microsoft"></a><span data-ttu-id="6f9c1-176">Microsoft に必要な CNAME レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="6f9c1-176">Add the CNAME records that are required for Microsoft</span></span>
<span data-ttu-id="6f9c1-177"><a name="BKMK_add_CNAME"> </a></span><span class="sxs-lookup"><span data-stu-id="6f9c1-177"><a name="BKMK_add_CNAME"> </a></span></span>

<span data-ttu-id="6f9c1-178">以下の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-178">Follow the steps below.</span></span>

1. <span data-ttu-id="6f9c1-p110">まず、[このリンク](https://account.godaddy.com/products/?go_redirect=disabled)を使って GoDaddy でドメイン ページにアクセスします。ログインするように求められます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-p110">To get started, go to your domains page at GoDaddy by using [this link](https://account.godaddy.com/products/?go_redirect=disabled). You'll be prompted to log in.</span></span>

    ![GoDaddy-BP-Configure-1-1](../../media/d6833ec7-9904-43fd-a877-7c663e5f5c25.png)

2. <span data-ttu-id="6f9c1-182">[ **ドメイン] で**、編集するドメインの下の DNS を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-182">Under **Domains**, select DNS under the domain that you want to edit.</span></span>

    ![GoDaddy-BP-Configure-1-2](../../media/dns/56528038-94b6ac00-651c-11e9-8874-12db60cc7ea6.png)

3. <span data-ttu-id="6f9c1-184">**[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-184">Select **Add**.</span></span>

    ![GoDaddy-BP-Configure-1-4](../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png)


4. <span data-ttu-id="6f9c1-186">ドロップダウン リストから [ **CNAME (Alias)**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-186">Choose **CNAME (Alias)** from the drop-down list.</span></span>

    ![GoDaddy-BP-Configure-3-0](../../media/dns/56528891-e7449800-651d-11e9-8eac-112285b8e38c.png)

5. <span data-ttu-id="6f9c1-188">1 番目の CNAME レコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-188">Create the first CNAME record.</span></span>

    <span data-ttu-id="6f9c1-189">新規レコードのボックスに、次の表の 1 行目の値を入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-189">In the boxes for the new record, type or copy and paste the values from the first row of the following table.</span></span>

    <span data-ttu-id="6f9c1-190">(ドロップダウン リスト **から TTL** 値を選択します)。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-190">(Choose the **TTL** value from the drop-down list.)</span></span>

    |<span data-ttu-id="6f9c1-191">**Record type**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-191">**Record type**</span></span>|<span data-ttu-id="6f9c1-192">**Host**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-192">**Host**</span></span>|<span data-ttu-id="6f9c1-193">**Points to**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-193">**Points to**</span></span>|<span data-ttu-id="6f9c1-194">**TTL**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-194">**TTL**</span></span>|
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="6f9c1-195">CNAME (Alias)</span><span class="sxs-lookup"><span data-stu-id="6f9c1-195">CNAME (Alias)</span></span>  <br/> |<span data-ttu-id="6f9c1-196">autodiscover</span><span class="sxs-lookup"><span data-stu-id="6f9c1-196">autodiscover</span></span>  <br/> |<span data-ttu-id="6f9c1-197">autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="6f9c1-197">autodiscover.outlook.com</span></span>  <br/> |<span data-ttu-id="6f9c1-198">1 hour</span><span class="sxs-lookup"><span data-stu-id="6f9c1-198">1 hour</span></span>  <br/> |
    |<span data-ttu-id="6f9c1-199">CNAME (Alias)</span><span class="sxs-lookup"><span data-stu-id="6f9c1-199">CNAME (Alias)</span></span>  <br/> |<span data-ttu-id="6f9c1-200">sip</span><span class="sxs-lookup"><span data-stu-id="6f9c1-200">sip</span></span>  <br/> |<span data-ttu-id="6f9c1-201">sipdir.online.lync.com</span><span class="sxs-lookup"><span data-stu-id="6f9c1-201">sipdir.online.lync.com</span></span>  <br/> |<span data-ttu-id="6f9c1-202">1 時間</span><span class="sxs-lookup"><span data-stu-id="6f9c1-202">1 hour</span></span>  <br/> |
    |<span data-ttu-id="6f9c1-203">CNAME (Alias)</span><span class="sxs-lookup"><span data-stu-id="6f9c1-203">CNAME (Alias)</span></span>  <br/> |<span data-ttu-id="6f9c1-204">lyncdiscover</span><span class="sxs-lookup"><span data-stu-id="6f9c1-204">lyncdiscover</span></span>  <br/> |<span data-ttu-id="6f9c1-205">webdir.online.lync.com</span><span class="sxs-lookup"><span data-stu-id="6f9c1-205">webdir.online.lync.com</span></span>  <br/> |<span data-ttu-id="6f9c1-206">1 hour</span><span class="sxs-lookup"><span data-stu-id="6f9c1-206">1 hour</span></span>  <br/> |
    |<span data-ttu-id="6f9c1-207">CNAME (Alias)</span><span class="sxs-lookup"><span data-stu-id="6f9c1-207">CNAME (Alias)</span></span>  <br/> |<span data-ttu-id="6f9c1-208">enterpriseregistration</span><span class="sxs-lookup"><span data-stu-id="6f9c1-208">enterpriseregistration</span></span>  <br/> |<span data-ttu-id="6f9c1-209">enterpriseregistration.windows.net</span><span class="sxs-lookup"><span data-stu-id="6f9c1-209">enterpriseregistration.windows.net</span></span>  <br/> |<span data-ttu-id="6f9c1-210">1 hour</span><span class="sxs-lookup"><span data-stu-id="6f9c1-210">1 hour</span></span>  <br/> |
    |<span data-ttu-id="6f9c1-211">CNAME (Alias)</span><span class="sxs-lookup"><span data-stu-id="6f9c1-211">CNAME (Alias)</span></span>  <br/> |<span data-ttu-id="6f9c1-212">enterpriseenrollment</span><span class="sxs-lookup"><span data-stu-id="6f9c1-212">enterpriseenrollment</span></span>  <br/> |<span data-ttu-id="6f9c1-213">enterpriseenrollment.manage.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="6f9c1-213">enterpriseenrollment.manage.microsoft.com</span></span>  <br/> |<span data-ttu-id="6f9c1-214">1 時間</span><span class="sxs-lookup"><span data-stu-id="6f9c1-214">1 hour</span></span>  <br/> |



6. <span data-ttu-id="6f9c1-215">6 つの CNAME レコードすべてが作成されるまで、この手順を繰り返して次の CNAME レコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-215">Repeat these steps to add the next CNAME record until you have created all six of the CNAME records.</span></span>

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a><span data-ttu-id="6f9c1-216">迷惑メールの防止に役立つ、SPF の TXT レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="6f9c1-216">Add a TXT record for SPF to help prevent email spam</span></span>
<span data-ttu-id="6f9c1-217"><a name="BKMK_add_TXT"> </a></span><span class="sxs-lookup"><span data-stu-id="6f9c1-217"><a name="BKMK_add_TXT"> </a></span></span>

> [!IMPORTANT]
> <span data-ttu-id="6f9c1-218">1 つのドメインで、SPF に複数の TXT レコードを設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-218">You cannot have more than one TXT record for SPF for a domain.</span></span> <span data-ttu-id="6f9c1-219">1 つのドメインに複数の SPF レコードがあると、メール、配信の分類、迷惑メールの分類で問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-219">If your domain has more than one SPF record, you'll get email errors, as well as delivery and spam classification issues.</span></span> <span data-ttu-id="6f9c1-220">使用しているドメインに既に SPF レコードがある場合は、Microsoft 用に新しいレコードを作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-220">If you already have an SPF record for your domain, don't create a new one for Microsoft.</span></span> <span data-ttu-id="6f9c1-221">代わりに、必要な Microsoft の値を現在のレコードに追加して、両方の値のセットを含む  *1*  つの SPF レコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-221">Instead, add the required Microsoft values to the current record so that you have a  *single*  SPF record that includes both sets of values.</span></span>

<span data-ttu-id="6f9c1-222">以下の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-222">Follow the steps below.</span></span>

1. <span data-ttu-id="6f9c1-p112">まず、[このリンク](https://account.godaddy.com/products/?go_redirect=disabled)を使って GoDaddy でドメイン ページにアクセスします。ログインするように求められます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-p112">To get started, go to your domains page at GoDaddy by using [this link](https://account.godaddy.com/products/?go_redirect=disabled). You'll be prompted to log in.</span></span>

    ![GoDaddy-BP-Configure-1-1](../../media/d6833ec7-9904-43fd-a877-7c663e5f5c25.png)

2. <span data-ttu-id="6f9c1-226">[ **ドメイン] で**、編集するドメインの下の DNS を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-226">Under **Domains**, select DNS under the domain that you want to edit.</span></span>

    ![GoDaddy-BP-Configure-1-2](../../media/dns/56528038-94b6ac00-651c-11e9-8874-12db60cc7ea6.png)

3. <span data-ttu-id="6f9c1-228">**[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-228">Select **Add**.</span></span>

    ![GoDaddy-BP-Configure-1-4](../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png)

4. <span data-ttu-id="6f9c1-230">ドロップダウン リストから [ **TXT (Text)**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-230">Choose **TXT (Text)** from the drop-down list.</span></span>

    ![GoDaddy-BP-Configure-4-0](../../media/dns/56529449-c0d32c80-651e-11e9-90e9-895aa1c4bbf1.png)

5. <span data-ttu-id="6f9c1-232">新規レコードのボックスに次の値を入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-232">In the boxes for the new record, type or copy and paste the following values.</span></span>

    <span data-ttu-id="6f9c1-233">(ドロップダウン リスト **から TTL** 値を選択します)。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-233">(Choose the **TTL** value from the drop-down lists.)</span></span>

    |<span data-ttu-id="6f9c1-234">**Record type**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-234">**Record type**</span></span>|<span data-ttu-id="6f9c1-235">**Host**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-235">**Host**</span></span>|<span data-ttu-id="6f9c1-236">**TXT Value**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-236">**TXT Value**</span></span>|<span data-ttu-id="6f9c1-237">**TTL**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-237">**TTL**</span></span>|
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="6f9c1-238">TXT (テキスト)</span><span class="sxs-lookup"><span data-stu-id="6f9c1-238">TXT (Text)</span></span>  <br/> |@  <br/> |<span data-ttu-id="6f9c1-239">v=spf1 include:spf.protection.outlook.com -all</span><span class="sxs-lookup"><span data-stu-id="6f9c1-239">v=spf1 include:spf.protection.outlook.com -all</span></span>  <br/> <span data-ttu-id="6f9c1-240">**注:** スペースも正しく入力されるように、この値をコピーして貼り付けることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-240">**Note:** We recommend copying and pasting this entry, so that all of the spacing stays correct.</span></span>           |<span data-ttu-id="6f9c1-241">1 時間</span><span class="sxs-lookup"><span data-stu-id="6f9c1-241">1 hour</span></span>  <br/> |

    ![GoDaddy-BP-Configure-4-1](../../media/7c724f02-c9b3-42ab-b9c0-78959fa6ffad.png)

6. <span data-ttu-id="6f9c1-243">**[保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-243">Select **Save**.</span></span>


## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a><span data-ttu-id="6f9c1-244">Microsoft で必要な 2 つの SRV レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="6f9c1-244">Add the two SRV records that are required for Microsoft</span></span>
<span data-ttu-id="6f9c1-245"><a name="BKMK_add_SRV"> </a></span><span class="sxs-lookup"><span data-stu-id="6f9c1-245"><a name="BKMK_add_SRV"> </a></span></span>

<span data-ttu-id="6f9c1-246">以下の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-246">Follow the steps below.</span></span>

1. <span data-ttu-id="6f9c1-p113">まず、[このリンク](https://account.godaddy.com/products/?go_redirect=disabled)を使って GoDaddy でドメイン ページにアクセスします。ログインするように求められます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-p113">To get started, go to your domains page at GoDaddy by using [this link](https://account.godaddy.com/products/?go_redirect=disabled). You'll be prompted to log in.</span></span>

    ![GoDaddy-BP-Configure-1-1](../../media/d6833ec7-9904-43fd-a877-7c663e5f5c25.png)

2. <span data-ttu-id="6f9c1-250">[ **ドメイン] で**、編集するドメインの下の DNS を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-250">Under **Domains**, select DNS under the domain that you want to edit.</span></span>

    ![GoDaddy-BP-Configure-1-2](../../media/dns/56528038-94b6ac00-651c-11e9-8874-12db60cc7ea6.png)

3. <span data-ttu-id="6f9c1-252">**[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-252">Select **Add**.</span></span>

    ![GoDaddy-BP-Configure-1-4](../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png)

4. <span data-ttu-id="6f9c1-254">ドロップダウン リストから [ **SRV (Service)**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-254">Choose **SRV (Service)** from the drop-down list.</span></span>

    ![GoDaddy-BP-Configure-5-0](../../media/dns/56529669-1dcee280-651f-11e9-8ba2-ecf4fc2f6dca.png)

5. <span data-ttu-id="6f9c1-256">1 番目の SRV レコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-256">Create the first SRV record.</span></span>

    <span data-ttu-id="6f9c1-257">新規レコードのボックスに、次の表の 1 行目の値を入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-257">In the boxes for the new record, type or copy and paste the values from the first row of the following table.</span></span>

    <span data-ttu-id="6f9c1-258">(Choose the **Record type** and **TTL** values from the drop-down lists.)</span><span class="sxs-lookup"><span data-stu-id="6f9c1-258">(Choose the **Record type** and **TTL** values from the drop-down lists.)</span></span>

    |<span data-ttu-id="6f9c1-259">**Record type**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-259">**Record type**</span></span>|<span data-ttu-id="6f9c1-260">**Name**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-260">**Name**</span></span>|<span data-ttu-id="6f9c1-261">**Target**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-261">**Target**</span></span>|<span data-ttu-id="6f9c1-262">**Protocol**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-262">**Protocol**</span></span>|<span data-ttu-id="6f9c1-263">**Service**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-263">**Service**</span></span>|<span data-ttu-id="6f9c1-264">**Priority**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-264">**Priority**</span></span>|<span data-ttu-id="6f9c1-265">**Weight**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-265">**Weight**</span></span>|<span data-ttu-id="6f9c1-266">**Port**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-266">**Port**</span></span>|<span data-ttu-id="6f9c1-267">**TTL**</span><span class="sxs-lookup"><span data-stu-id="6f9c1-267">**TTL**</span></span>|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |<span data-ttu-id="6f9c1-268">SRV (Service)</span><span class="sxs-lookup"><span data-stu-id="6f9c1-268">SRV (Service)</span></span>  <br/> |@  <br/> |<span data-ttu-id="6f9c1-269">sipdir.online.lync.com</span><span class="sxs-lookup"><span data-stu-id="6f9c1-269">sipdir.online.lync.com</span></span>  <br/> |<span data-ttu-id="6f9c1-270">_tls</span><span class="sxs-lookup"><span data-stu-id="6f9c1-270">_tls</span></span>  <br/> |<span data-ttu-id="6f9c1-271">_sip</span><span class="sxs-lookup"><span data-stu-id="6f9c1-271">_sip</span></span>  <br/> |<span data-ttu-id="6f9c1-272">100</span><span class="sxs-lookup"><span data-stu-id="6f9c1-272">100</span></span>  <br/> |<span data-ttu-id="6f9c1-273">1 </span><span class="sxs-lookup"><span data-stu-id="6f9c1-273">1</span></span>  <br/> |<span data-ttu-id="6f9c1-274">443</span><span class="sxs-lookup"><span data-stu-id="6f9c1-274">443</span></span>  <br/> |<span data-ttu-id="6f9c1-275">1 hour</span><span class="sxs-lookup"><span data-stu-id="6f9c1-275">1 hour</span></span>  <br/> |
    |<span data-ttu-id="6f9c1-276">SRV (Service)</span><span class="sxs-lookup"><span data-stu-id="6f9c1-276">SRV (Service)</span></span>  <br/> |@  <br/> |<span data-ttu-id="6f9c1-277">sipfed.online.lync.com</span><span class="sxs-lookup"><span data-stu-id="6f9c1-277">sipfed.online.lync.com</span></span>  <br/> |<span data-ttu-id="6f9c1-278">_tcp</span><span class="sxs-lookup"><span data-stu-id="6f9c1-278">_tcp</span></span>  <br/> |<span data-ttu-id="6f9c1-279">_sipfederationtls</span><span class="sxs-lookup"><span data-stu-id="6f9c1-279">_sipfederationtls</span></span>  <br/> |<span data-ttu-id="6f9c1-280">100</span><span class="sxs-lookup"><span data-stu-id="6f9c1-280">100</span></span>  <br/> |<span data-ttu-id="6f9c1-281">1 </span><span class="sxs-lookup"><span data-stu-id="6f9c1-281">1</span></span>  <br/> |<span data-ttu-id="6f9c1-282">5061</span><span class="sxs-lookup"><span data-stu-id="6f9c1-282">5061</span></span>  <br/> |<span data-ttu-id="6f9c1-283">1 時間</span><span class="sxs-lookup"><span data-stu-id="6f9c1-283">1 hour</span></span>  <br/> |

    ![GoDaddy-BP-Configure-5-1](../../media/a1b15ab1-eb6a-4672-90d1-7ac3e0beb223.png)


6. <span data-ttu-id="6f9c1-285">手順 **5 を繰り返** して、他の SRV レコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-285">Repeat **Step 5** to Create the other SRV record.</span></span>

7. <span data-ttu-id="6f9c1-286">**[保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-286">Select **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="6f9c1-p114">通常、DNS の変更が有効になるのに 15 分ほどかかります。ただし、インターネットの DNS システム全体を更新する変更の場合、さらに長くかかることもあります。DNS レコードの追加でメール フローなどに問題が発生した場合は、「[ドメイン名または DNS レコードの変更後の問題に関するトラブルシューティング](../get-help-with-domains/find-and-fix-issues.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f9c1-p114">Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).</span></span>
