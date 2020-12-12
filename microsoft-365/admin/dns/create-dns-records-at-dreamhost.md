---
title: Dreamhost で Microsoft 用の DNS レコードを作成する
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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9c0812e0-908b-4b41-a64b-77f0dbd3db7a
description: ドメインを確認し、Dreamhost for Microsoft でメール、Skype for Business Online、その他のサービスの DNS レコードをセットアップする方法について説明します。
ms.openlocfilehash: 2faf7cae1fd9a0f9308e303c0588958e56b223e1
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "49658125"
---
# <a name="create-dns-records-at-dreamhost-for-microsoft"></a><span data-ttu-id="6b1bb-103">Dreamhost で Microsoft 用の DNS レコードを作成する</span><span class="sxs-lookup"><span data-stu-id="6b1bb-103">Create DNS records at Dreamhost for Microsoft</span></span>

 <span data-ttu-id="6b1bb-104">探している内容が見つからない場合は、**[ドメインに関する FAQ を確認Q](../setup/domains-faq.yml)** を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-104">**[Check the Domains FAQ](../setup/domains-faq.yml)** if you don't find what you're looking for.</span></span> 
  
<span data-ttu-id="6b1bb-105">使用している DNS ホスティング プロバイダーが DreamHost の場合は、この記事に示す手順に従い、ドメインを確認して、メールや Lync などの DNS レコードを設定します。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-105">If DreamHost is your DNS hosting provider, follow the steps in this article to verify your domain and set up DNS records for email, Lync, and so on.</span></span>
 
<span data-ttu-id="6b1bb-106">DreamHost でこれらのレコードを追加すると、ドメインは Microsoft サービスで動作する設定に設定されます。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-106">After you add these records at DreamHost, your domain will be set up to work with Microsoft services.</span></span>
  
  
> [!NOTE]
> <span data-ttu-id="6b1bb-p101">通常、DNS の変更が有効になるのに 15 分ほどかかります。ただし、インターネットの DNS システム全体を更新する変更の場合、さらに長くかかることもあります。DNS レコードの追加でメール フローなどに問題が発生した場合は、「[ドメイン名または DNS レコードの変更後の問題に関するトラブルシューティング](../get-help-with-domains/find-and-fix-issues.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-p101">Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).</span></span> 
  
## <a name="add-a-txt-record-for-verification"></a><span data-ttu-id="6b1bb-110">確認のための TXT レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="6b1bb-110">Add a TXT record for verification</span></span>
<span data-ttu-id="6b1bb-111"><a name="BKMK_verify"> </a></span><span class="sxs-lookup"><span data-stu-id="6b1bb-111"><a name="BKMK_verify"> </a></span></span>

<span data-ttu-id="6b1bb-p102">Microsoft のドメインを使うには、ドメインを所有していることを確認する必要があります。自分のドメイン レジストラーで自分のアカウントにログインし、DNS レコードを作成することができれば、Microsoft に対してドメインを所有していることを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-p102">Before you use your domain with Microsoft, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.</span></span>
  
> [!NOTE]
> <span data-ttu-id="6b1bb-p103">このレコードは、ドメインを所有していることを確認するためだけに使用されます。その他には影響しません。 必要に応じて、後で削除することができます。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-p103">This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.</span></span> 
  
1. <span data-ttu-id="6b1bb-p104">まず、[このリンク](https://panel.dreamhost.com/)を使って DreamHost でドメイン ページにアクセスします。サインインするように求められます。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-p104">To get started, go to your domains page at DreamHost by using [this link](https://panel.dreamhost.com/). You'll be prompted to Sign in.</span></span>
    
    ![Dreamhost-BP-Configure-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. <span data-ttu-id="6b1bb-119">[ダッシュボード **] ページで\*\*\*\*、[ドメイン]** を選択し、[ドメインの管理]**を選択します**。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-119">On the **Dashboard** page, select **Domains**, and then **Manage Domains**.</span></span>
    
    ![Dreamhost-BP-Configure-1-2](../../media/ab05c16a-79f6-491f-ad07-9a2e6674671d.png)
  
3. <span data-ttu-id="6b1bb-121">[ドメイン **の管理] ページ** の[ドメイン] セクションで、編集するドメインの **DNS** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-121">On the **Manage Domains** page, in the **Domain** section, select **DNS** for the domain that you want to edit.</span></span> 
    
    ![Dreamhost-BP-Configure-1-3](../../media/1a8723a0-54bc-40ff-bc30-5fc3e8cd219b.png)
  
4. <span data-ttu-id="6b1bb-123">In the **Add a custom DNS record** section, in the boxes for the new record, type or copy and paste the values from the following table.</span><span class="sxs-lookup"><span data-stu-id="6b1bb-123">In the **Add a custom DNS record** section, in the boxes for the new record, type or copy and paste the values from the following table.</span></span> 
    
    <span data-ttu-id="6b1bb-124">(You may have to scroll down.)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-124">(You may have to scroll down.)</span></span>
    
    <span data-ttu-id="6b1bb-125">(ドロップダウン リストから [**Type**] の値を選びます。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-125">(Choose the **Type** value from the drop-down list.)</span></span> 
    
    |<span data-ttu-id="6b1bb-126">**名前**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-126">**Name**</span></span>|<span data-ttu-id="6b1bb-127">**Type**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-127">**Type**</span></span>|<span data-ttu-id="6b1bb-128">**値**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-128">**Value**</span></span>|<span data-ttu-id="6b1bb-129">**コメント**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-129">**Comment**</span></span>|
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="6b1bb-130">(Leave this field empty.)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-130">(Leave this field empty.)</span></span>  <br/> |<span data-ttu-id="6b1bb-131">TXT</span><span class="sxs-lookup"><span data-stu-id="6b1bb-131">TXT</span></span>  <br/> |<span data-ttu-id="6b1bb-132">MS=ms *XXXXXXXX*</span><span class="sxs-lookup"><span data-stu-id="6b1bb-132">MS=ms *XXXXXXXX*</span></span>  <br/> <span data-ttu-id="6b1bb-133">**注:** これは例です。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-133">**Note:** This is an example.</span></span> <span data-ttu-id="6b1bb-134">この表から **[宛先またはポイント先のアドレス]** の値を指定してください。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-134">Use your specific **Destination or Points to Address** value here, from the table.</span></span>           [<span data-ttu-id="6b1bb-135">確認する方法</span><span class="sxs-lookup"><span data-stu-id="6b1bb-135">How do I find this?</span></span>](../get-help-with-domains/information-for-dns-records.md)          |<span data-ttu-id="6b1bb-136">(このフィールドは省略可能です。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-136">(This field is optional.)</span></span>  <br/> |
   
   ![Dreamhost-BP-Verify-1-1](../../media/ed4a7d43-eeeb-4ec8-849c-37f81315dc69.png)
  
5. <span data-ttu-id="6b1bb-138">[Add **Record Now] (今すぐレコードの追加) を選択します。**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-138">Select **Add Record Now!**</span></span>
    
    ![Dreamhost-BP-Verify-1-2](../../media/5b89c89b-3a8e-4624-895a-86f3cc4638f6.png)
  
6. <span data-ttu-id="6b1bb-140">数分待つと、続行できます。この間、作成したレコードがインターネット全体で更新されます。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-140">Wait a few minutes before you continue, so that the record you just created can update across the Internet.</span></span>
    
<span data-ttu-id="6b1bb-141">これで、ドメイン レジストラーのサイトでレコードが追加されました。Microsoft に戻り、レコードをリクエストします。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-141">Now that you've added the record at your domain registrar's site, you'll go back to Microsoft and request the record.</span></span>
  
<span data-ttu-id="6b1bb-142">Microsoft で正しい TXT レコードが見つかった場合、ドメインは確認済みとなります。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-142">When Microsoft finds the correct TXT record, your domain is verified.</span></span>
  
1. <span data-ttu-id="6b1bb-143">Microsoft 管理センターで、**[設定]** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">[ドメイン]</a> ページの順に移動します。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-143">In the Microsoft admin center, go to the **Settings** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domains</a> page.</span></span>

    
2. <span data-ttu-id="6b1bb-144">**[ドメイン]** ページで、確認するドメインを選択します。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-144">On the **Domains** page, select the domain that you are verifying.</span></span> 
    
    
  
3. <span data-ttu-id="6b1bb-145">**[セットアップ]** ページで、**[セットアップの開始]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-145">On the **Setup** page, select **Start setup**.</span></span>
    
    
  
4. <span data-ttu-id="6b1bb-146">**[ドメインの確認]** ページで、**[確認]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-146">On the **Verify domain** page, select **Verify**.</span></span>
    
    
  
> [!NOTE]
>  <span data-ttu-id="6b1bb-p106">通常、DNS の変更が有効になるのに 15 分ほどかかります。ただし、インターネットの DNS システム全体を更新する変更の場合、さらに長くかかることもあります。DNS レコードの追加でメール フローなどに問題が発生した場合は、「[ドメイン名または DNS レコードの変更後の問題に関するトラブルシューティング](../get-help-with-domains/find-and-fix-issues.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-p106">Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).</span></span> 
  

  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a><span data-ttu-id="6b1bb-150">MX レコードを追加して、自分のドメインのメールが Microsoft に届くようにする</span><span class="sxs-lookup"><span data-stu-id="6b1bb-150">Add an MX record so email for your domain will come to Microsoft</span></span>
<span data-ttu-id="6b1bb-151"><a name="BKMK_add_MX"> </a></span><span class="sxs-lookup"><span data-stu-id="6b1bb-151"><a name="BKMK_add_MX"> </a></span></span>

<span data-ttu-id="6b1bb-152">以下の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-152">Follow the steps below.</span></span>
  
1. <span data-ttu-id="6b1bb-p107">まず、[このリンク](https://panel.dreamhost.com/)を使って DreamHost でドメイン ページにアクセスします。サインインするように求められます。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-p107">To get started, go to your domains page at DreamHost by using [this link](https://panel.dreamhost.com/). You'll be prompted to Sign in.</span></span>
    
    ![Dreamhost-BP-Configure-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. <span data-ttu-id="6b1bb-156">[ダッシュボード **] ページで** 、[メール] を選択 **し**、[カスタム **MX] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-156">On the **Dashboard** page, select **Mail**, and then **Custom MX**.</span></span>
    
    ![Dreamhost-BP-Configure-2-1](../../media/58478679-4018-49cc-9d83-371dc5fa4a22.png)
  
3. <span data-ttu-id="6b1bb-158">[メール **配信の管理**] セクションの [操作]**列で**、編集するドメインの [編集] を選択します。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-158">In the **Manage Mail Delivery** section, in the **Actions** column, select **Edit** for the domain that you want to edit.</span></span> 
    
    ![Dreamhost-BP-Configure-2-2](../../media/6eed0be2-6477-4f49-9f90-39e190499a53.png)
  
4. <span data-ttu-id="6b1bb-160">[ **Custom MX Record**] セクションにある新規レコードのボックスに、次の表から次の値を入力するかコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-160">In the **Custom MX Record** section, in the boxes for the new record, type or copy and paste the following values from the following table.</span></span> 
    
    <span data-ttu-id="6b1bb-161">(下へスクロールしなければならないことがあります。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-161">(You may have to scroll down.)</span></span>
    
    <span data-ttu-id="6b1bb-162">(MX レコードが他にもある場合は、それらのレコードが削除されるようにマーク付けします。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-162">(If there are any other existing MX records, mark those records to be deleted.)</span></span>
    
    |<span data-ttu-id="6b1bb-163">**MX レコード (必須)**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-163">**MX Record (required)**</span></span>|
    |:-----|
    |<span data-ttu-id="6b1bb-164">0  *\<domain-key\>*  .mail.protection.outlook.com.</span><span class="sxs-lookup"><span data-stu-id="6b1bb-164">0  *\<domain-key\>*  .mail.protection.outlook.com.</span></span>  <br/> <span data-ttu-id="6b1bb-165">**この値は、末尾がピリオド (.) でなければなりません**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-165">**This value MUST end with a period (.)**</span></span> <br/> <span data-ttu-id="6b1bb-p108">0 は、MX 優先度の値です。 この値を MX 値の先頭に追加して、スペースで他の値から分離します。  </span><span class="sxs-lookup"><span data-stu-id="6b1bb-p108">The 0 is the MX priority value. Add it to the beginning of the MX value, separated from the remainder of the value by a space.  </span></span><br/> <span data-ttu-id="6b1bb-168">**注:** Microsoft アカウント  *\<domain-key\>*  からユーザーを取得します。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-168">**Note:** Get your  *\<domain-key\>*  from your Microsoft account.</span></span>           [<span data-ttu-id="6b1bb-169">確認する方法</span><span class="sxs-lookup"><span data-stu-id="6b1bb-169">How do I find this?</span></span>](../get-help-with-domains/information-for-dns-records.md)          |
   
    ![Dreamhost-BP-Configure-2-3](../../media/90da1816-e186-4016-ab22-7962f8b86add.png)
  
5. <span data-ttu-id="6b1bb-171">Select **Change this domain to use custom MX records now!**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-171">Select **Change this domain to use custom MX records now!**</span></span>
    
    ![Dreamhost-BP-Configure-2-4](../../media/3221c767-83d3-4f30-9d08-dc998772d2a3.png)
  
6. <span data-ttu-id="6b1bb-173">他の MX レコードが既にある場合は、エントリを選択し、キーボードの **Delete** キーを押して、各レコードを削除します。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-173">If there are any other existing MX records, delete each record by selecting the entry and then pressing the **Delete** key on your keyboard.</span></span> 
    
    ![Dreamhost-BP-Configure-2-5](../../media/1827733c-3609-4b0f-bba1-531ab090da91.png)
  
7. <span data-ttu-id="6b1bb-175">レコードを削除した場合は、[今すぐカスタム MX レコード **を更新する] を選択します。**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-175">If you have deleted any records, select **Update your custom MX records now!**</span></span>
    
    ![Dreamhost-BP-Configure-2-6](../../media/177462be-0686-47b7-a389-025dfc8d6526.png)

  
## <a name="add-the-six-cname-records-that-are-required-for-microsoft"></a><span data-ttu-id="6b1bb-177">Microsoft に必要な 6 つの CNAME レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="6b1bb-177">Add the six CNAME records that are required for Microsoft</span></span>
<span data-ttu-id="6b1bb-178"><a name="BKMK_add_CNAME"> </a></span><span class="sxs-lookup"><span data-stu-id="6b1bb-178"><a name="BKMK_add_CNAME"> </a></span></span>

<span data-ttu-id="6b1bb-179">以下の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-179">Follow the steps below.</span></span>
  
1. <span data-ttu-id="6b1bb-p110">まず、[このリンク](https://panel.dreamhost.com/)を使って DreamHost でドメイン ページにアクセスします。サインインするように求められます。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-p110">To get started, go to your domains page at DreamHost by using [this link](https://panel.dreamhost.com/). You'll be prompted to Sign in.</span></span>
    
    ![Dreamhost-BP-Configure-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. <span data-ttu-id="6b1bb-183">[ダッシュボード **] ページで\*\*\*\*、[ドメイン]** を選択し、[ドメインの管理]**を選択します**。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-183">On the **Dashboard** page, select **Domains**, and then **Manage Domains**.</span></span>
    
    ![Dreamhost-BP-Configure-1-2](../../media/ab05c16a-79f6-491f-ad07-9a2e6674671d.png)
  
3. <span data-ttu-id="6b1bb-185">[ドメイン **の管理] ページ** の[ドメイン] セクションで、編集するドメインの **DNS** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-185">On the **Manage Domains** page, in the **Domain** section, select **DNS** for the domain that you want to edit.</span></span> 
    
    ![Dreamhost-BP-Configure-1-3](../../media/1a8723a0-54bc-40ff-bc30-5fc3e8cd219b.png)
  
4. <span data-ttu-id="6b1bb-187">[ **Add a custom DNS record**] セクションにある新規レコードのボックスに、次の表の最初の行の値を入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-187">In the **Add a custom DNS record** section, in the boxes for the new record, type or copy and paste the values from the first row in the following table.</span></span> 
    
    <span data-ttu-id="6b1bb-188">(下へスクロールしなければならないことがあります。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-188">(You may have to scroll down.)</span></span>
    
    <span data-ttu-id="6b1bb-189">(ドロップダウン リストから [**Type**] の値を選びます。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-189">(Choose the **Type** value from the drop-down list.)</span></span> 
    
    |<span data-ttu-id="6b1bb-190">**名前**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-190">**Name**</span></span>|<span data-ttu-id="6b1bb-191">**Type**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-191">**Type**</span></span>|<span data-ttu-id="6b1bb-192">**値**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-192">**Value**</span></span>|<span data-ttu-id="6b1bb-193">**コメント**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-193">**Comment**</span></span>|
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="6b1bb-194">autodiscover</span><span class="sxs-lookup"><span data-stu-id="6b1bb-194">autodiscover</span></span>  <br/> |<span data-ttu-id="6b1bb-195">CNAME</span><span class="sxs-lookup"><span data-stu-id="6b1bb-195">CNAME</span></span>  <br/> |<span data-ttu-id="6b1bb-196">autodiscover.outlook.com.</span><span class="sxs-lookup"><span data-stu-id="6b1bb-196">autodiscover.outlook.com.</span></span>  <br/> <span data-ttu-id="6b1bb-197">**この値は、末尾がピリオド (.) でなければなりません**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-197">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="6b1bb-198">(このフィールドは省略可能です。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-198">(This field is optional.)</span></span>  <br/> |
    |<span data-ttu-id="6b1bb-199">sip</span><span class="sxs-lookup"><span data-stu-id="6b1bb-199">sip</span></span>  <br/> |<span data-ttu-id="6b1bb-200">CNAME</span><span class="sxs-lookup"><span data-stu-id="6b1bb-200">CNAME</span></span>  <br/> |<span data-ttu-id="6b1bb-201">sipdir.online.lync.com</span><span class="sxs-lookup"><span data-stu-id="6b1bb-201">sipdir.online.lync.com.</span></span>  <br/> <span data-ttu-id="6b1bb-202">**この値は、末尾がピリオド (.) でなければなりません**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-202">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="6b1bb-203">(このフィールドは省略可能です。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-203">(This field is optional.)</span></span>  <br/> |
    |<span data-ttu-id="6b1bb-204">lyncdiscover</span><span class="sxs-lookup"><span data-stu-id="6b1bb-204">lyncdiscover</span></span>  <br/> |<span data-ttu-id="6b1bb-205">CNAME</span><span class="sxs-lookup"><span data-stu-id="6b1bb-205">CNAME</span></span>  <br/> |<span data-ttu-id="6b1bb-206">webdir.online.lync.com.</span><span class="sxs-lookup"><span data-stu-id="6b1bb-206">webdir.online.lync.com.</span></span>  <br/> <span data-ttu-id="6b1bb-207">**この値は、末尾がピリオド (.) でなければなりません**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-207">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="6b1bb-208">(このフィールドは省略可能です。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-208">(This field is optional.)</span></span>  <br/> |
    |<span data-ttu-id="6b1bb-209">enterpriseregistration</span><span class="sxs-lookup"><span data-stu-id="6b1bb-209">enterpriseregistration</span></span>  <br/> |<span data-ttu-id="6b1bb-210">CNAME</span><span class="sxs-lookup"><span data-stu-id="6b1bb-210">CNAME</span></span>  <br/> |<span data-ttu-id="6b1bb-211">enterpriseregistration.windows.net.</span><span class="sxs-lookup"><span data-stu-id="6b1bb-211">enterpriseregistration.windows.net.</span></span>  <br/> <span data-ttu-id="6b1bb-212">**この値は、末尾がピリオド (.) でなければなりません**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-212">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="6b1bb-213">(このフィールドは省略可能です。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-213">(This field is optional.)</span></span>  <br/> |
    |<span data-ttu-id="6b1bb-214">enterpriseenrollment</span><span class="sxs-lookup"><span data-stu-id="6b1bb-214">enterpriseenrollment</span></span>  <br/> |<span data-ttu-id="6b1bb-215">CNAME</span><span class="sxs-lookup"><span data-stu-id="6b1bb-215">CNAME</span></span>  <br/> |<span data-ttu-id="6b1bb-216">enterpriseenrollment-s.manage.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="6b1bb-216">enterpriseenrollment-s.manage.microsoft.com.</span></span>  <br/> <span data-ttu-id="6b1bb-217">**この値は、末尾がピリオド (.) でなければなりません**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-217">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="6b1bb-218">(このフィールドは省略可能です。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-218">(This field is optional.)</span></span>  <br/> |
   
    ![Dreamhost-BP-Configure-3-1](../../media/0c4cc587-ea24-47f2-8dc6-a35735b250e6.png)
  
5. <span data-ttu-id="6b1bb-220">[Add **Record Now] (今すぐレコードの追加) を選択します。**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-220">Select **Add Record Now!**</span></span>
    
    ![Dreamhost-BP-Configure-3-2](../../media/b5d4f939-de6d-4d1f-a20a-4eb5fe715281.png)
  
6. <span data-ttu-id="6b1bb-222">前の 2 つの手順と表の他の 5 行の値を使用して、他の 5 つの CNAME レコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-222">Using the preceding two steps and the values from the other five rows in the table, add each of the other five CNAME records.</span></span>

  
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a><span data-ttu-id="6b1bb-223">迷惑メールの防止に役立つ、SPF の TXT レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="6b1bb-223">Add a TXT record for SPF to help prevent email spam</span></span>
<span data-ttu-id="6b1bb-224"><a name="BKMK_add_TXT"> </a></span><span class="sxs-lookup"><span data-stu-id="6b1bb-224"><a name="BKMK_add_TXT"> </a></span></span>

> [!IMPORTANT]
> <span data-ttu-id="6b1bb-225">1 つのドメインで、SPF に複数の TXT レコードを設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-225">You cannot have more than one TXT record for SPF for a domain.</span></span> <span data-ttu-id="6b1bb-226">1 つのドメインに複数の SPF レコードがあると、メール、配信の分類、迷惑メールの分類で問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-226">If your domain has more than one SPF record, you'll get email errors, as well as delivery and spam classification issues.</span></span> <span data-ttu-id="6b1bb-227">使用しているドメインに既に SPF レコードがある場合は、Microsoft 用に新しいレコードを作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-227">If you already have an SPF record for your domain, don't create a new one for Microsoft.</span></span> <span data-ttu-id="6b1bb-228">代わりに、必要な Microsoft の値を現在のレコードに追加して、両方の値のセットを含む  *1*  つの SPF レコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-228">Instead, add the required Microsoft values to the current record so that you have a  *single*  SPF record that includes both sets of values.</span></span>
  
<span data-ttu-id="6b1bb-229">以下の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-229">Follow the steps below.</span></span>
  
1. <span data-ttu-id="6b1bb-p112">まず、[このリンク](https://panel.dreamhost.com/)を使って DreamHost でドメイン ページにアクセスします。サインインするように求められます。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-p112">To get started, go to your domains page at DreamHost by using [this link](https://panel.dreamhost.com/). You'll be prompted to Sign in.</span></span>
    
    ![Dreamhost-BP-Configure-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. <span data-ttu-id="6b1bb-233">[ダッシュボード **] ページで\*\*\*\*、[ドメイン]** を選択し、[ドメインの管理]**を選択します**。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-233">On the **Dashboard** page, select **Domains**, and then **Manage Domains**.</span></span>
    
    ![Dreamhost-BP-Configure-1-2](../../media/ab05c16a-79f6-491f-ad07-9a2e6674671d.png)
  
3. <span data-ttu-id="6b1bb-235">[ドメイン **の管理] ページ** の[ドメイン] セクションで、編集するドメインの **DNS** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-235">On the **Manage Domains** page, in the **Domain** section, select **DNS** for the domain that you want to edit.</span></span> 
    
    ![Dreamhost-BP-Configure-1-3](../../media/1a8723a0-54bc-40ff-bc30-5fc3e8cd219b.png)
  
4. <span data-ttu-id="6b1bb-237">[ **Add a custom DNS record**] セクションにある新規レコードのボックスに、次の表の最初の行の値を入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-237">In the **Add a custom DNS record** section, in the boxes for the new record, type or copy and paste the values from the first row in the following table.</span></span> 
    
    <span data-ttu-id="6b1bb-238">(下へスクロールしなければならないことがあります。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-238">(You may have to scroll down.)</span></span>
    
    <span data-ttu-id="6b1bb-239">(ドロップダウン リストから [**Type**] の値を選びます。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-239">(Choose the **Type** value from the drop-down list.)</span></span> 
    
    |<span data-ttu-id="6b1bb-240">**名前**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-240">**Name**</span></span>|<span data-ttu-id="6b1bb-241">**Type**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-241">**Type**</span></span>|<span data-ttu-id="6b1bb-242">**値**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-242">**Value**</span></span>|<span data-ttu-id="6b1bb-243">**コメント**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-243">**Comment**</span></span>|
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="6b1bb-244">(Leave this field empty.)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-244">(Leave this field empty.)</span></span>  <br/> |<span data-ttu-id="6b1bb-245">TXT</span><span class="sxs-lookup"><span data-stu-id="6b1bb-245">TXT</span></span>  <br/> |<span data-ttu-id="6b1bb-246">v=spf1 include:spf.protection.outlook.com -all</span><span class="sxs-lookup"><span data-stu-id="6b1bb-246">v=spf1 include:spf.protection.outlook.com -all</span></span>  <br/> <span data-ttu-id="6b1bb-247">**注:** スペースも正しく入力されるように、この値をコピーして貼り付けることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-247">**Note:** We recommend copying and pasting this entry, so that all of the spacing stays correct.</span></span>           |<span data-ttu-id="6b1bb-248">(このフィールドは省略可能です。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-248">(This field is optional.)</span></span>  <br/> |
   
   ![Dreamhost-BP-Configure-4-1](../../media/cbc4bbca-bdbc-4dc9-b1b7-b55491eb1e53.png)
  
5. <span data-ttu-id="6b1bb-250">[Add **Record Now] (今すぐレコードの追加) を選択します。**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-250">Select **Add Record Now!**</span></span>
    
    ![Dreamhost-BP-Configure-4-2](../../media/2bd7cae8-1fbc-4407-8dfa-06ce37c586c0.png)
  
6. <span data-ttu-id="6b1bb-252">上の 2 つの手順に従って、表の 2 行目の値を使って、別の SRV レコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-252">Using the preceding two steps and the values from the second row in the table, add the other SRV record.</span></span>
    
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a><span data-ttu-id="6b1bb-253">Microsoft で必要な 2 つの SRV レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="6b1bb-253">Add the two SRV records that are required for Microsoft</span></span>
<span data-ttu-id="6b1bb-254"><a name="BKMK_add_SRV"> </a></span><span class="sxs-lookup"><span data-stu-id="6b1bb-254"><a name="BKMK_add_SRV"> </a></span></span>

<span data-ttu-id="6b1bb-255">以下の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-255">Follow the steps below.</span></span>
  
1. <span data-ttu-id="6b1bb-p113">まず、[このリンク](https://panel.dreamhost.com/)を使って DreamHost でドメイン ページにアクセスします。サインインするように求められます。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-p113">To get started, go to your domains page at DreamHost by using [this link](https://panel.dreamhost.com/). You'll be prompted to Sign in.</span></span>
    
    ![Dreamhost-BP-Configure-1-1](../../media/1919b810-b6ba-4e29-a774-de1e7c67d078.png)
  
2. <span data-ttu-id="6b1bb-259">[ダッシュボード **] ページで\*\*\*\*、[ドメイン]** を選択し、[ドメインの管理]**を選択します**。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-259">On the **Dashboard** page, select **Domains**, and then **Manage Domains**.</span></span>
    
    ![Dreamhost-BP-Configure-1-2](../../media/ab05c16a-79f6-491f-ad07-9a2e6674671d.png)
  
3. <span data-ttu-id="6b1bb-261">[ドメイン **の管理] ページ** の[ドメイン] セクションで、編集するドメインの **DNS** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-261">On the **Manage Domains** page, in the **Domain** section, select **DNS** for the domain that you want to edit.</span></span> 
    
    ![Dreamhost-BP-Configure-1-3](../../media/1a8723a0-54bc-40ff-bc30-5fc3e8cd219b.png)
  
4. <span data-ttu-id="6b1bb-263">[ **Add a custom DNS record**] セクションにある新規レコードのボックスに、次の表の最初の行の値を入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-263">In the **Add a custom DNS record** section, in the boxes for the new record, type or copy and paste the values from the first row in the following table.</span></span> 
    
    <span data-ttu-id="6b1bb-264">(下へスクロールしなければならないことがあります。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-264">(You may have to scroll down.)</span></span>
    
    <span data-ttu-id="6b1bb-265">(ドロップダウン リストから [**Type**] の値を選びます。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-265">(Choose the **Type** value from the drop-down list.)</span></span> 
    
    |<span data-ttu-id="6b1bb-266">**名前**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-266">**Name**</span></span>|<span data-ttu-id="6b1bb-267">**Type**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-267">**Type**</span></span>|<span data-ttu-id="6b1bb-268">**値**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-268">**Value**</span></span>|<span data-ttu-id="6b1bb-269">**コメント**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-269">**Comment**</span></span>|
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="6b1bb-270">_sip._tls</span><span class="sxs-lookup"><span data-stu-id="6b1bb-270">_sip._tls</span></span>  <br/> |<span data-ttu-id="6b1bb-271">SRV</span><span class="sxs-lookup"><span data-stu-id="6b1bb-271">SRV</span></span>  <br/> |<span data-ttu-id="6b1bb-272">100 1 443</span><span class="sxs-lookup"><span data-stu-id="6b1bb-272">100 1 443</span></span>  <br/> <span data-ttu-id="6b1bb-273">sipdir.online.lync.com</span><span class="sxs-lookup"><span data-stu-id="6b1bb-273">sipdir.online.lync.com.</span></span>  <br/> <span data-ttu-id="6b1bb-274">**この値は、末尾がピリオド (.) でなければなりません**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-274">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="6b1bb-275">(このフィールドは省略可能です。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-275">(This field is optional.)</span></span>  <br/> |
    |<span data-ttu-id="6b1bb-276">_sipfederationtls._tcp</span><span class="sxs-lookup"><span data-stu-id="6b1bb-276">_sipfederationtls._tcp</span></span>  <br/> |<span data-ttu-id="6b1bb-277">SRV</span><span class="sxs-lookup"><span data-stu-id="6b1bb-277">SRV</span></span>  <br/> |<span data-ttu-id="6b1bb-278">100 1 5061</span><span class="sxs-lookup"><span data-stu-id="6b1bb-278">100 1 5061</span></span>  <br/> <span data-ttu-id="6b1bb-279">sipfed.online.lync.com。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-279">sipfed.online.lync.com.</span></span>  <br/> <span data-ttu-id="6b1bb-280">**この値は、末尾がピリオド (.) でなければなりません**</span><span class="sxs-lookup"><span data-stu-id="6b1bb-280">**This value MUST end with a period (.)**</span></span> <br/> |<span data-ttu-id="6b1bb-281">(このフィールドは省略可能です。)</span><span class="sxs-lookup"><span data-stu-id="6b1bb-281">(This field is optional.)</span></span>  <br/> |
   
    ![Dreamhost-BP-Configure-5-1](../../media/934eb79f-3617-4b72-802c-c42c7d165283.png)
  
5. <span data-ttu-id="6b1bb-283">[Add **Record Now! ] (今すぐレコードの追加) を選択します**。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-283">Select **Add Record Now!**.</span></span>
    
    ![Dreamhost-BP-Configure-5-2](../../media/015bc73c-8f88-49ce-87f9-e5a6ea3e10a8.png)
  
6. <span data-ttu-id="6b1bb-285">上の 2 つの手順に従って、表の 2 行目の値を使って、別の SRV レコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-285">Using the preceding two steps and the values from the second row in the table, add the other SRV record.</span></span>
    
> [!NOTE]
>  <span data-ttu-id="6b1bb-p114">通常、DNS の変更が有効になるのに 15 分ほどかかります。ただし、インターネットの DNS システム全体を更新する変更の場合、さらに長くかかることもあります。DNS レコードの追加でメール フローなどに問題が発生した場合は、「[ドメイン名または DNS レコードの変更後の問題に関するトラブルシューティング](../get-help-with-domains/find-and-fix-issues.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b1bb-p114">Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).</span></span> 

  
