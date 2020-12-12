---
title: Netregistry for Microsoft で DNS レコードを作成する
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
- BEA160
ms.assetid: 48e09394-2287-4b3c-9853-21eadf61277e
description: Microsoft Netregistry でドメインを確認し、メール、Skype for Business Online、その他のサービスの DNS レコードをセットアップする方法について説明します。
ms.openlocfilehash: 857645c685cce946b39a7c3dcadb0a45b43686cf
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "49657805"
---
# <a name="create-dns-records-at-netregistry-for-microsoft"></a><span data-ttu-id="94153-103">Netregistry for Microsoft で DNS レコードを作成する</span><span class="sxs-lookup"><span data-stu-id="94153-103">Create DNS records at Netregistry for Microsoft</span></span>

<span data-ttu-id="94153-104">探している内容が見つからない場合は、[ドメインに関する FAQ を確認](../setup/domains-faq.yml)してください。</span><span class="sxs-lookup"><span data-stu-id="94153-104">[Check the Domains FAQ](../setup/domains-faq.yml) if you don't find what you're looking for.</span></span> 
  
<span data-ttu-id="94153-105">使用している DNS ホスティング プロバイダーが Netregistry の場合は、この記事に記載された手順に従って、ドメインの確認とメールや Skype for Business Online などの DNS レコードのセットアップを行います。</span><span class="sxs-lookup"><span data-stu-id="94153-105">If Netregistry is your DNS hosting provider, follow the steps in this article to verify your domain and set up DNS records for email, Skype for Business Online, and so on.</span></span>
  
<span data-ttu-id="94153-106">追加する主なレコードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="94153-106">These are the main records to add.</span></span>
  
- [<span data-ttu-id="94153-107">確認のための TXT レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="94153-107">Add a TXT record for verification</span></span>](#add-a-txt-record-for-verification)
    
- [<span data-ttu-id="94153-108">MX レコードを追加して、自分のドメインのメールが Microsoft に届くようにする</span><span class="sxs-lookup"><span data-stu-id="94153-108">Add an MX record so email for your domain will come to Microsoft</span></span>](#add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft)

- [<span data-ttu-id="94153-109">Microsoft に必要な CNAME レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="94153-109">Add the CNAME records that are required for Microsoft</span></span>](#add-the-cname-records-that-are-required-for-microsoft)
    
- [<span data-ttu-id="94153-110">迷惑メールの防止に役立つ、SPF の TXT レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="94153-110">Add a TXT record for SPF to help prevent email spam</span></span>](#add-a-txt-record-for-spf-to-help-prevent-email-spam)
    
- [<span data-ttu-id="94153-111">Microsoft で必要な 2 つの SRV レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="94153-111">Add the two SRV records that are required for Microsoft</span></span>](#add-the-two-srv-records-that-are-required-for-microsoft)
    
<span data-ttu-id="94153-112">Netregistry でこれらのレコードを追加すると、ドメインは Microsoft サービスで動作する設定に設定されます。</span><span class="sxs-lookup"><span data-stu-id="94153-112">After you add these records at Netregistry, your domain will be set up to work with Microsoft services.</span></span>
  
  
> [!NOTE]
> <span data-ttu-id="94153-p101">通常、DNS の変更が有効になるのに 15 分ほどかかります。ただし、インターネットの DNS システム全体を更新する変更の場合、さらに長くかかることもあります。DNS レコードの追加でメール フローなどに問題が発生した場合は、「[ドメイン名または DNS レコードの変更後の問題に関するトラブルシューティング](../get-help-with-domains/find-and-fix-issues.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94153-p101">Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).</span></span> 
  
## <a name="add-a-txt-record-for-verification"></a><span data-ttu-id="94153-116">確認のための TXT レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="94153-116">Add a TXT record for verification</span></span>
<span data-ttu-id="94153-117"><a name="bkmk_txt"> </a></span><span class="sxs-lookup"><span data-stu-id="94153-117"><a name="bkmk_txt"> </a></span></span>

<span data-ttu-id="94153-p102">Microsoft のドメインを使うには、ドメインを所有していることを確認する必要があります。自分のドメイン レジストラーで自分のアカウントにログインし、DNS レコードを作成することができれば、Microsoft に対してドメインを所有していることを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="94153-p102">Before you use your domain with Microsoft, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft that you own the domain.</span></span>
  
> [!NOTE]
> <span data-ttu-id="94153-p103">このレコードは、ドメインを所有していることを確認するためだけに使用されます。その他には影響しません。 必要に応じて、後で削除することができます。</span><span class="sxs-lookup"><span data-stu-id="94153-p103">This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like.</span></span> 
  
1. <span data-ttu-id="94153-p104">まず、[こちらのリンク](https://theconsole.netregistry.com.au/)を使って、Netregistry のドメイン ページにアクセスします。ログインするように求められます。</span><span class="sxs-lookup"><span data-stu-id="94153-p104">To get started, go to your domains page in Netregistry by using [this link](https://theconsole.netregistry.com.au/). You'll be prompted to log in.</span></span>
    
    ![Netregistry_login](../../media/ed3c785f-01c3-49e7-affd-c04637c0ffe9.png)
  
2. <span data-ttu-id="94153-125">管理するドメインの横にある、[ **Manage** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-125">Next to the domain you want to manage, select **Manage**.</span></span>
    
    ![Netregistry_Manage](../../media/64ad542a-5ec4-4148-96f8-d6e163449352.png)
  
3. <span data-ttu-id="94153-127">[ **Zone Manager** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-127">Select **Zone Manager**.</span></span>
    
    ![Netregistry_selectZoneManager](../../media/e18c32f9-c1e7-4aa2-9aa6-8dc9c5ea44af.png)
  
4. <span data-ttu-id="94153-129">[Add **a zone record] (ゾーン レコードの** 追加) で、一覧から **[TXT Record]** を選び **、[Create new record] (** 新しいレコードの作成) を選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-129">Under **Add a zone record**, choose **TXT Record** from the list, and then select **Create new record**.</span></span>
    
    ![Netregistry_TXT_select](../../media/eb1761e6-9deb-4631-8deb-bc5d09926722.png)
  
    > [!NOTE]
    > <span data-ttu-id="94153-131">TXT ボックスのエントリの前と後に引用符を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94153-131">You must use quotation marks before and after the entry in the TXT box.</span></span> 
  
    <span data-ttu-id="94153-132">[ **New TXT Record** ] フォームに、次の表の値を入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="94153-132">In the **New TXT Record** form, type or copy and paste the values from the following table.</span></span> 
    
    |<span data-ttu-id="94153-133">**名前**</span><span class="sxs-lookup"><span data-stu-id="94153-133">**Name**</span></span>|<span data-ttu-id="94153-134">**TTL (秒)**</span><span class="sxs-lookup"><span data-stu-id="94153-134">**TTL (SEC)**</span></span>|<span data-ttu-id="94153-135">**TXT (ポイント先のアドレスまたは値)**</span><span class="sxs-lookup"><span data-stu-id="94153-135">**TXT (Points to address or value)**</span></span>|
    |:-----|:-----|:-----|
    |<span data-ttu-id="94153-136">(空白のまま)</span><span class="sxs-lookup"><span data-stu-id="94153-136">(leave blank)</span></span>  <br/> |<span data-ttu-id="94153-137">3600 (秒)</span><span class="sxs-lookup"><span data-stu-id="94153-137">3600 (seconds)</span></span>  <br/> |<span data-ttu-id="94153-138">"MS=msXXXXXXXX"</span><span class="sxs-lookup"><span data-stu-id="94153-138">"MS=msXXXXXXXX"</span></span>  <br/> <span data-ttu-id="94153-139">**注:** これは例です。</span><span class="sxs-lookup"><span data-stu-id="94153-139">**Note:** This is an example.</span></span> <span data-ttu-id="94153-140">この表から **[宛先またはポイント先のアドレス]** の値を指定してください。</span><span class="sxs-lookup"><span data-stu-id="94153-140">Use your specific **Destination or Points to Address** value here, from the table.</span></span> [<span data-ttu-id="94153-141">確認する方法</span><span class="sxs-lookup"><span data-stu-id="94153-141">How do I find this?</span></span>](../get-help-with-domains/information-for-dns-records.md)  |
       
    ![Netregistry_verificationTXTvalues](../../media/cfe8b05a-fa8b-4dba-9554-7a3466e6c012.png)
  
6. <span data-ttu-id="94153-143">Select **Add record**.</span><span class="sxs-lookup"><span data-stu-id="94153-143">Select **Add record**.</span></span>
    
<span data-ttu-id="94153-144">これで、ドメイン レジストラーのサイトでレコードが追加されました。Microsoft に戻り、レコードをリクエストします。</span><span class="sxs-lookup"><span data-stu-id="94153-144">Now that you've added the record at your domain registrar's site, you'll go back to Microsoft and request the record.</span></span>
  
<span data-ttu-id="94153-145">Microsoft で正しい TXT レコードが見つかった場合、ドメインは確認済みとなります。</span><span class="sxs-lookup"><span data-stu-id="94153-145">When Microsoft finds the correct TXT record, your domain is verified.</span></span>
  
1. <span data-ttu-id="94153-146">管理センターで、**[設定]** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">[ドメイン]</a> ページの順に移動します。</span><span class="sxs-lookup"><span data-stu-id="94153-146">In the admin center, go to the **Settings** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domains</a> page.</span></span>
    
2. <span data-ttu-id="94153-147">**[ドメイン]** ページで、確認するドメインを選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-147">On the **Domains** page, select the domain that you are verifying.</span></span> 
    
    
  
3. <span data-ttu-id="94153-148">**[セットアップ]** ページで、**[セットアップの開始]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-148">On the **Setup** page, select **Start setup**.</span></span>
    
    
  
4. <span data-ttu-id="94153-149">**[ドメインの確認]** ページで、**[確認]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-149">On the **Verify domain** page, select **Verify**.</span></span>
    
    
  
> [!NOTE]
>  <span data-ttu-id="94153-p106">通常、DNS の変更が有効になるのに 15 分ほどかかります。ただし、インターネットの DNS システム全体を更新する変更の場合、さらに長くかかることもあります。DNS レコードの追加でメール フローなどに問題が発生した場合は、「[ドメイン名または DNS レコードの変更後の問題に関するトラブルシューティング](../get-help-with-domains/find-and-fix-issues.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94153-p106">Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).</span></span> 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a><span data-ttu-id="94153-153">MX レコードを追加して、自分のドメインのメールが Microsoft に届くようにする</span><span class="sxs-lookup"><span data-stu-id="94153-153">Add an MX record so email for your domain will come to Microsoft</span></span>
<span data-ttu-id="94153-154"><a name="bkmk_mx"> </a></span><span class="sxs-lookup"><span data-stu-id="94153-154"><a name="bkmk_mx"> </a></span></span>

1. <span data-ttu-id="94153-p107">まず、[こちらのリンク](https://theconsole.netregistry.com.au/)を使って、Netregistry のドメイン ページにアクセスします。ログインするように求められます。</span><span class="sxs-lookup"><span data-stu-id="94153-p107">To get started, go to your domains page in Netregistry by using [this link](https://theconsole.netregistry.com.au/). You'll be prompted to log in.</span></span>
    
    ![Netregistry_login](../../media/80277b0e-547e-4635-aa6a-5d8ebe3fba85.png)
  
2. <span data-ttu-id="94153-158">管理するドメインの横にある、[ **Manage** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-158">Next to the domain you want to manage, select **Manage**.</span></span>
    
    ![Netregistry_Manage](../../media/96e2c6e4-21fd-4405-a4fe-b1188400b985.png)
  
3. <span data-ttu-id="94153-160">[ **Zone Manager** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-160">Select **Zone Manager**.</span></span>
    
    ![Netregistry_selectZoneManager](../../media/914021f6-dff3-4640-84d6-b83cf8f61cf1.png)
  
4. <span data-ttu-id="94153-162">[**現在のゾーンのレコード**] で、一覧の各 MX レコードの横にある [削除] を選択して、既定の MX レコードを削除します。</span><span class="sxs-lookup"><span data-stu-id="94153-162">Under **Current zone records**, remove the default MX records by selecting **Remove** next to each MX record in the list.</span></span> 
    
    ![Netregistry_MX_remove](../../media/494670a9-8b8d-46e5-8136-05e82212a115.png)
  
5. <span data-ttu-id="94153-164">[ **ゾーン レコードの追加] で**、一覧から **[MX レコード** ] を選択し、[新しいレコードの作成 **] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="94153-164">Under **Add a zone record**, choose **MX Record** from the list, and then select **Create new record**.</span></span>
    
    ![Netregistry_MX_select](../../media/29b60eb9-6c40-490f-9669-e65b65962f37.png)
  
6. <span data-ttu-id="94153-166">[New **MX Record]** フォームで、次の表の値を入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="94153-166">In the **New MX Record** form, type or copy and paste the values from the following table.</span></span> 
    
    |<span data-ttu-id="94153-167">**名前**</span><span class="sxs-lookup"><span data-stu-id="94153-167">**Name**</span></span>|<span data-ttu-id="94153-168">**TTL (秒)**</span><span class="sxs-lookup"><span data-stu-id="94153-168">**TTL (SEC)**</span></span>|<span data-ttu-id="94153-169">**Exchange (ポイント先アドレスまたは値)**</span><span class="sxs-lookup"><span data-stu-id="94153-169">**Exchange (Points to address or value)**</span></span>|<span data-ttu-id="94153-170">**ホストは完全修飾されますか?**</span><span class="sxs-lookup"><span data-stu-id="94153-170">**Is host fully qualified?**</span></span>|<span data-ttu-id="94153-171">**Preference (Priority)**</span><span class="sxs-lookup"><span data-stu-id="94153-171">**Preference (Priority)**</span></span>|
    |:-----|:-----|:-----|:-----|:-----|
    |<span data-ttu-id="94153-172">(空白のまま)</span><span class="sxs-lookup"><span data-stu-id="94153-172">(leave blank)</span></span>  <br/> |<span data-ttu-id="94153-173">3600 (秒)</span><span class="sxs-lookup"><span data-stu-id="94153-173">3600 (seconds)</span></span>  <br/> | <span data-ttu-id="94153-174">*\<domain-key\>*  .mail.protection.outlook.com</span><span class="sxs-lookup"><span data-stu-id="94153-174">*\<domain-key\>*  .mail.protection.outlook.com</span></span>  <br/> <span data-ttu-id="94153-175">**注:** Microsoft アカウント  *\<domain-key\>*  からユーザーを取得します。</span><span class="sxs-lookup"><span data-stu-id="94153-175">**Note:** Get your  *\<domain-key\>*  from your Microsoft account.</span></span>  [<span data-ttu-id="94153-176">確認する方法</span><span class="sxs-lookup"><span data-stu-id="94153-176">How do I find this?</span></span>](../get-help-with-domains/information-for-dns-records.md)      |<span data-ttu-id="94153-177">(チェック ボックスをオンにする)</span><span class="sxs-lookup"><span data-stu-id="94153-177">(select the checkbox)</span></span>  <br/> |<span data-ttu-id="94153-178">10 </span><span class="sxs-lookup"><span data-stu-id="94153-178">10</span></span>  <br/> <span data-ttu-id="94153-179">For more information about priority, see What is MX priority?</span><span class="sxs-lookup"><span data-stu-id="94153-179">For more information about priority, see What is MX priority?</span></span>  <br/> |
       
    ![Netregistry_MX_values](../../media/518b3da6-4055-4e2d-b5ce-44a0fee25419.png)
  
7. <span data-ttu-id="94153-181">[ **Add Record** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-181">Select **Add Record**.</span></span>
    
    ![Netregistry_MX_values_AddRecord](../../media/8194cb38-afa0-48ac-831c-fd34b6ad652e.png)
  
## <a name="add-the-cname-records-that-are-required-for-microsoft"></a><span data-ttu-id="94153-183">Microsoft に必要な CNAME レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="94153-183">Add the CNAME records that are required for Microsoft</span></span>
<span data-ttu-id="94153-184"><a name="bkmk_cname"> </a></span><span class="sxs-lookup"><span data-stu-id="94153-184"><a name="bkmk_cname"> </a></span></span>

1. <span data-ttu-id="94153-p109">まず、[こちらのリンク](https://theconsole.netregistry.com.au/)を使って、Netregistry のドメイン ページにアクセスします。ログインするように求められます。</span><span class="sxs-lookup"><span data-stu-id="94153-p109">To get started, go to your domains page in Netregistry by using [this link](https://theconsole.netregistry.com.au/). You'll be prompted to log in.</span></span>
    
    ![Netregistry_login](../../media/cbf83dce-86d2-4008-9400-56def4b6fcd7.png)
  
2. <span data-ttu-id="94153-188">管理するドメインの横にある、[ **Manage** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-188">Next to the domain you want to manage, select **Manage**.</span></span>
    
    ![Netregistry_Manage](../../media/7bee4b0f-2c1d-43ca-b1bb-9b889ca0c5e4.png)
  
3. <span data-ttu-id="94153-190">[ **Zone Manager** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-190">Select **Zone Manager**.</span></span>
    
    ![Netregistry_selectZoneManager](../../media/58384add-0a9d-472b-a5d0-51ec8155fd41.png)
  
4. <span data-ttu-id="94153-192">[  **ゾーン レコードの追加] で、** リストから **[CNAME レコード** ] を選択し、[新しいレコードの作成 **] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="94153-192">Under  **Add a zone record**, choose **CNAME Record** from the list, and then select **Create new record**.</span></span>
    
    ![Netregistry_CNAME_CreateNewRecord](../../media/7b4f133f-45da-48da-93c0-62f57c786165.png)
  
5. <span data-ttu-id="94153-194">新規レコードのボックスに、次の表の値を入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="94153-194">In the boxes for the new record, type or copy and paste the values from the following table.</span></span>
    
    |<span data-ttu-id="94153-195">**名前**</span><span class="sxs-lookup"><span data-stu-id="94153-195">**Name**</span></span>|<span data-ttu-id="94153-196">**Type**</span><span class="sxs-lookup"><span data-stu-id="94153-196">**Type**</span></span>|<span data-ttu-id="94153-197">**TTL**</span><span class="sxs-lookup"><span data-stu-id="94153-197">**TTL**</span></span>|<span data-ttu-id="94153-198">**HOST (ポイント先またはアドレス値)**</span><span class="sxs-lookup"><span data-stu-id="94153-198">**HOST (Points to or address value)**</span></span>|
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="94153-199">autodiscover</span><span class="sxs-lookup"><span data-stu-id="94153-199">autodiscover</span></span>  <br/> |<span data-ttu-id="94153-200">CNAME</span><span class="sxs-lookup"><span data-stu-id="94153-200">CNAME</span></span>  <br/> |<span data-ttu-id="94153-201">3600 (秒)</span><span class="sxs-lookup"><span data-stu-id="94153-201">3600 (seconds)</span></span>  <br/> |<span data-ttu-id="94153-202">autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="94153-202">autodiscover.outlook.com</span></span>  <br/> |
    |<span data-ttu-id="94153-203">sip</span><span class="sxs-lookup"><span data-stu-id="94153-203">sip</span></span>  <br/> |<span data-ttu-id="94153-204">CNAME</span><span class="sxs-lookup"><span data-stu-id="94153-204">CNAME</span></span>  <br/> |<span data-ttu-id="94153-205">3600 (秒)</span><span class="sxs-lookup"><span data-stu-id="94153-205">3600 (seconds)</span></span>  <br/> |<span data-ttu-id="94153-206">sipdir.online.lync.com</span><span class="sxs-lookup"><span data-stu-id="94153-206">sipdir.online.lync.com</span></span>  <br/> |
    |<span data-ttu-id="94153-207">lyncdiscover</span><span class="sxs-lookup"><span data-stu-id="94153-207">lyncdiscover</span></span>  <br/> |<span data-ttu-id="94153-208">CNAME</span><span class="sxs-lookup"><span data-stu-id="94153-208">CNAME</span></span>  <br/> |<span data-ttu-id="94153-209">3600 (秒)</span><span class="sxs-lookup"><span data-stu-id="94153-209">3600 (seconds)</span></span>  <br/> |<span data-ttu-id="94153-210">webdir.online.lync.com</span><span class="sxs-lookup"><span data-stu-id="94153-210">webdir.online.lync.com</span></span>  <br/> |
    |<span data-ttu-id="94153-211">enterpriseregistration</span><span class="sxs-lookup"><span data-stu-id="94153-211">enterpriseregistration</span></span>  <br/> |<span data-ttu-id="94153-212">CNAME</span><span class="sxs-lookup"><span data-stu-id="94153-212">CNAME</span></span>  <br/> |<span data-ttu-id="94153-213">3600 (秒)</span><span class="sxs-lookup"><span data-stu-id="94153-213">3600 (seconds)</span></span>  <br/> |<span data-ttu-id="94153-214">enterpriseregistration.windows.net</span><span class="sxs-lookup"><span data-stu-id="94153-214">enterpriseregistration.windows.net</span></span>  <br/> |
    |<span data-ttu-id="94153-215">enterpriseenrollment</span><span class="sxs-lookup"><span data-stu-id="94153-215">enterpriseenrollment</span></span>  <br/> |<span data-ttu-id="94153-216">CNAME</span><span class="sxs-lookup"><span data-stu-id="94153-216">CNAME</span></span>  <br/> |<span data-ttu-id="94153-217">3600 (秒)</span><span class="sxs-lookup"><span data-stu-id="94153-217">3600 (seconds)</span></span>  <br/> |<span data-ttu-id="94153-218">enterpriseenrollment-s.manage.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="94153-218">enterpriseenrollment-s.manage.microsoft.com</span></span>  <br/> |
       
    ![Netregistry_CNAME_values](../../media/93c479f0-3ce2-491a-9113-6dde1cd7131b.png)
      
6. <span data-ttu-id="94153-220">Select **Add record**.</span><span class="sxs-lookup"><span data-stu-id="94153-220">Select **Add record**.</span></span>
    
    ![Netregistry_CNAME_values_AddRecord](../../media/046c8c64-ea71-4530-9fc6-69f0c70993b6.png)
  
7. <span data-ttu-id="94153-222">前の手順を繰り返し、他の 5 つの CNAME レコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="94153-222">Repeat the previous steps to create the other five CNAME records.</span></span>
    
    <span data-ttu-id="94153-223">レコードごとに、上のテーブルの次の行の値をそのレコードのボックスに入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="94153-223">For each record, type or copy and paste the values from the next row of the table above into the boxes for that record.</span></span>
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a><span data-ttu-id="94153-224">迷惑メールの防止に役立つ、SPF の TXT レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="94153-224">Add a TXT record for SPF to help prevent email spam</span></span>
<span data-ttu-id="94153-225"><a name="bkmk_spf"> </a></span><span class="sxs-lookup"><span data-stu-id="94153-225"><a name="bkmk_spf"> </a></span></span>

> [!IMPORTANT]
> <span data-ttu-id="94153-226">1 つのドメインで、SPF に複数の TXT レコードを設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="94153-226">You cannot have more than one TXT record for SPF for a domain.</span></span> <span data-ttu-id="94153-227">1 つのドメインに複数の SPF レコードがあると、メール、配信の分類、迷惑メールの分類で問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="94153-227">If your domain has more than one SPF record, you'll get email errors, as well as delivery and spam classification issues.</span></span> <span data-ttu-id="94153-228">使用しているドメインに既に SPF レコードがある場合は、Microsoft 用に新しいレコードを作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="94153-228">If you already have an SPF record for your domain, don't create a new one for Microsoft.</span></span> <span data-ttu-id="94153-229">代わりに、必要な Microsoft の値を現在のレコードに追加して、両方の値のセットを含む  *1*  つの SPF レコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="94153-229">Instead, add the required Microsoft values to the current record so that you have a  *single*  SPF record that includes both sets of values.</span></span>
  
1. <span data-ttu-id="94153-p111">まず、[こちらのリンク](https://theconsole.netregistry.com.au/)を使って、Netregistry のドメイン ページにアクセスします。ログインするように求められます。</span><span class="sxs-lookup"><span data-stu-id="94153-p111">To get started, go to your domains page in Netregistry by using [this link](https://theconsole.netregistry.com.au/). You'll be prompted to log in.</span></span>
    
    ![Netregistry_login](../../media/a841f11f-1c0f-4926-acea-a2b8bb083984.png)
  
2. <span data-ttu-id="94153-233">管理するドメインの横にある、[ **Manage** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-233">Next to the domain you want to manage, select **Manage**.</span></span>
    
    ![Netregistry_Manage](../../media/4245bbbb-4e2d-49e7-a89c-679949aa3d18.png)
  
3. <span data-ttu-id="94153-235">[ **Zone Manager** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-235">Select **Zone Manager**.</span></span>
    
    ![Netregistry_selectZoneManager](../../media/372e5918-b6dc-4268-8f9a-0aa71d65deef.png)
  
4. <span data-ttu-id="94153-237">[Add **a zone record] (ゾーン レコードの** 追加) で、一覧から **[TXT Record]** を選び **、[Create new record] (** 新しいレコードの作成) を選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-237">Under **Add a zone record**, choose **TXT Record** from the list, and then select **Create new record**.</span></span>
    
    ![Netregistry_TXT_select](../../media/a2930d03-853a-4f1e-9205-d00f25bed35f.png)
  
5. <span data-ttu-id="94153-239">新規レコードのボックスに、次の表の値を入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="94153-239">In the boxes for the new record, type or copy and paste the values from the following table.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="94153-240">TXT ボックスのエントリの前と後に引用符を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94153-240">You must use quotation marks before and after the entry in the TXT box.</span></span> 
  
    |<span data-ttu-id="94153-241">**名前**</span><span class="sxs-lookup"><span data-stu-id="94153-241">**Name**</span></span>|<span data-ttu-id="94153-242">**Type**</span><span class="sxs-lookup"><span data-stu-id="94153-242">**Type**</span></span>|<span data-ttu-id="94153-243">**TTL**</span><span class="sxs-lookup"><span data-stu-id="94153-243">**TTL**</span></span>|<span data-ttu-id="94153-244">**TXT データ (ターゲット)**</span><span class="sxs-lookup"><span data-stu-id="94153-244">**TXT Data (Target)**</span></span>|
    |:-----|:-----|:-----|:-----|
    |<span data-ttu-id="94153-245">(空白のまま)</span><span class="sxs-lookup"><span data-stu-id="94153-245">(leave blank)</span></span>  <br/> |<span data-ttu-id="94153-246">TXT</span><span class="sxs-lookup"><span data-stu-id="94153-246">TXT</span></span>  <br/> |<span data-ttu-id="94153-247">3600 (秒)</span><span class="sxs-lookup"><span data-stu-id="94153-247">3600 (seconds)</span></span>  <br/> |<span data-ttu-id="94153-248">"v=spf1 include:spf.protection.outlook.com -all"</span><span class="sxs-lookup"><span data-stu-id="94153-248">"v=spf1 include:spf.protection.outlook.com -all"</span></span>  <br/> <span data-ttu-id="94153-249">**注:** スペースも正しく入力されるように、この値をコピーして貼り付けることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="94153-249">**Note:** We recommend copying and pasting this entry, so that all of the spacing stays correct.</span></span>           |
   
    ![Netregistry_SPF-TXTvalues](../../media/a369345a-d774-48bc-8160-b628ab8247f9.png)
  
6. <span data-ttu-id="94153-251">[ **Add Record** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-251">Select **Add Record**.</span></span>
    
    ![Netregistry_SPF-TXTvalues_AddRecord](../../media/063bfbaf-940a-489f-970f-29c026b4b312.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a><span data-ttu-id="94153-253">Microsoft で必要な 2 つの SRV レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="94153-253">Add the two SRV records that are required for Microsoft</span></span>
<span data-ttu-id="94153-254"><a name="bkmk_srv"> </a></span><span class="sxs-lookup"><span data-stu-id="94153-254"><a name="bkmk_srv"> </a></span></span>

1. <span data-ttu-id="94153-p112">まず、[こちらのリンク](https://theconsole.netregistry.com.au/)を使って、Netregistry のドメイン ページにアクセスします。ログインするように求められます。</span><span class="sxs-lookup"><span data-stu-id="94153-p112">To get started, go to your domains page in Netregistry by using [this link](https://theconsole.netregistry.com.au/). You'll be prompted to log in.</span></span>
    
    ![Netregistry_login](../../media/accf6584-e5f4-4d68-a641-0f8847f8370f.png)
  
2. <span data-ttu-id="94153-258">管理するドメインの横にある [管理] を選択  **します**。</span><span class="sxs-lookup"><span data-stu-id="94153-258">Next to the domain you want to manage, select  **Manage**.</span></span>
    
    ![Netregistry_Manage](../../media/e0ddc79e-0123-4e24-8380-9645bdb41aac.png)
  
3. <span data-ttu-id="94153-260">[ **Zone Manager** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-260">Select **Zone Manager**.</span></span>
    
    ![Netregistry_selectZoneManager](../../media/f122888b-3cc5-40ec-adac-0ede04799d9a.png)
  
4. <span data-ttu-id="94153-262">[Add  **a zone record] (ゾーン レコードの** 追加) で、一覧から **[SRV Record]** を選び、[Create new record ] (新しいレコードの作成 **) を選択します**。</span><span class="sxs-lookup"><span data-stu-id="94153-262">Under  **Add a zone record**, choose **SRV Record** from the list, and then select **Create new record**.</span></span>
    
    ![Netregistry_SRV_select](../../media/e5dab850-acd1-48b8-8b4a-e3b9777cf508.png)
  
5. <span data-ttu-id="94153-264">新規レコードのボックスに、次の表の値を入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="94153-264">In the boxes for the new record, type or copy and paste the values from the following table.</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="94153-265">Name フィールドは、サービス (_sip など) とプロトコル (たとえば、_tls) の組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="94153-265">The Name field is a combination of the service (for example, _sip) and protocol (for example, _tls).</span></span> 
  
    |<span data-ttu-id="94153-266">**Type**</span><span class="sxs-lookup"><span data-stu-id="94153-266">**Type**</span></span>|<span data-ttu-id="94153-267">**名前**</span><span class="sxs-lookup"><span data-stu-id="94153-267">**Name**</span></span>|<span data-ttu-id="94153-268">**TTL (秒)**</span><span class="sxs-lookup"><span data-stu-id="94153-268">**TTL (SEC)**</span></span>|<span data-ttu-id="94153-269">**Priority**</span><span class="sxs-lookup"><span data-stu-id="94153-269">**Priority**</span></span>|<span data-ttu-id="94153-270">**Weight**</span><span class="sxs-lookup"><span data-stu-id="94153-270">**Weight**</span></span>|<span data-ttu-id="94153-271">**Port**</span><span class="sxs-lookup"><span data-stu-id="94153-271">**Port**</span></span>|<span data-ttu-id="94153-272">**対象**</span><span class="sxs-lookup"><span data-stu-id="94153-272">**Target**</span></span>|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |<span data-ttu-id="94153-273">SRV (サービス)</span><span class="sxs-lookup"><span data-stu-id="94153-273">SRV (service)</span></span>  <br/> |<span data-ttu-id="94153-274">_sip._tls</span><span class="sxs-lookup"><span data-stu-id="94153-274">_sip._tls</span></span>  <br/> |<span data-ttu-id="94153-275">3600 (秒)</span><span class="sxs-lookup"><span data-stu-id="94153-275">3600 (seconds)</span></span>  <br/> |<span data-ttu-id="94153-276">100</span><span class="sxs-lookup"><span data-stu-id="94153-276">100</span></span>  <br/> |<span data-ttu-id="94153-277">1 </span><span class="sxs-lookup"><span data-stu-id="94153-277">1</span></span>  <br/> |<span data-ttu-id="94153-278">443</span><span class="sxs-lookup"><span data-stu-id="94153-278">443</span></span>  <br/> |<span data-ttu-id="94153-279">sipdir.online.lync.com</span><span class="sxs-lookup"><span data-stu-id="94153-279">sipdir.online.lync.com</span></span>  <br/> |
    |<span data-ttu-id="94153-280">SRV (サービス)</span><span class="sxs-lookup"><span data-stu-id="94153-280">SRV (service)</span></span>  <br/> |<span data-ttu-id="94153-281">_sipfederationtls._tcp</span><span class="sxs-lookup"><span data-stu-id="94153-281">_sipfederationtls._tcp</span></span>  <br/> |<span data-ttu-id="94153-282">3600 (秒)</span><span class="sxs-lookup"><span data-stu-id="94153-282">3600 (seconds)</span></span>  <br/> |<span data-ttu-id="94153-283">100</span><span class="sxs-lookup"><span data-stu-id="94153-283">100</span></span>  <br/> |<span data-ttu-id="94153-284">1 </span><span class="sxs-lookup"><span data-stu-id="94153-284">1</span></span>  <br/> |<span data-ttu-id="94153-285">5061</span><span class="sxs-lookup"><span data-stu-id="94153-285">5061</span></span>  <br/> |<span data-ttu-id="94153-286">sipfed.online.lync.com</span><span class="sxs-lookup"><span data-stu-id="94153-286">sipfed.online.lync.com</span></span>  <br/> |
       
    ![Netregistry_SRV_values](../../media/49292846-1598-4b8c-9940-db6e10675753.png)
  
6. <span data-ttu-id="94153-288">[ **Add Record** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="94153-288">Select **Add Record**.</span></span>
    
    ![Netregistry_SRV_values_AddRecord](../../media/abc82061-939f-4757-87e4-0e8f9e43ebcb.png)
  
7. <span data-ttu-id="94153-290">上記の手順を繰り返し、他の SRV レコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="94153-290">Repeat the previous steps to create the other SRV record.</span></span>
    
    <span data-ttu-id="94153-291">2 番目のレコードのボックスに、上の表の 2 行目の値を入力するかコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="94153-291">Type or copy and paste the values from the second row of the table above into the boxes for the second record.</span></span>
    
> [!NOTE]
> <span data-ttu-id="94153-p113">通常、DNS の変更が有効になるのに 15 分ほどかかります。ただし、インターネットの DNS システム全体を更新する変更の場合、さらに長くかかることもあります。DNS レコードの追加でメール フローなどに問題が発生した場合は、「[ドメイン名または DNS レコードの変更後の問題に関するトラブルシューティング](../get-help-with-domains/find-and-fix-issues.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94153-p113">Typically it takes about 15 minutes for DNS changes to take effect. However, it can occasionally take longer for a change you've made to update across the Internet's DNS system. If you're having trouble with mail flow or other issues after adding DNS records, see [Troubleshoot issues after changing your domain name or DNS records](../get-help-with-domains/find-and-fix-issues.md).</span></span> 
  

