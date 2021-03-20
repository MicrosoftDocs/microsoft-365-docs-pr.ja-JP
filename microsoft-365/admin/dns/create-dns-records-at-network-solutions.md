---
title: Microsoft のネットワーク ソリューションで DNS レコードを作成する
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
ms.assetid: 1dc55f9f-5309-450f-acc3-b2b4119c8be3
description: Microsoft のネットワーク ソリューションで、ドメインを確認し、電子メール、Skype for Business Online、その他のサービスの DNS レコードを設定する方法について説明します。
ms.openlocfilehash: f25e21037695c99489adc9038bf70629a103ec7a
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "50910140"
---
# <a name="create-dns-records-at-network-solutions-for-microsoft"></a>Microsoft のネットワーク ソリューションで DNS レコードを作成する

 **探している内容が見つからない場合は、[ドメインに関する FAQ を確認](../setup/domains-faq.yml)** してください。 
  
使用している DNS ホスティング プロバイダーが Network Solutions の場合は、この記事に示す手順に従い、ドメインを確認して、メール、Skype for Business Online などの DNS レコードを設定します。
  
追加する主なレコードは次のとおりです。 次の手順を実行するか、[ビデオを参照](https://support.microsoft.com/office/c49698c2-6991-47fb-b5ac-18e49a505099)してください。 
  
- [確認のための TXT レコードを追加する](#add-a-txt-record-for-verification)
    
- [MX レコードを追加して、自分のドメインのメールが Microsoft に届くようにする](#add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft)
    
- [Microsoft に必要な CNAME レコードを追加する](#add-the-cname-records-that-are-required-for-microsoft)
    
- [迷惑メールの防止に役立つ、SPF の TXT レコードを追加する](#add-a-txt-record-for-spf-to-help-prevent-email-spam)
    
- [Microsoft で必要な 2 つの SRV レコードを追加する](#add-the-two-srv-records-that-are-required-for-microsoft)
    
ネットワーク ソリューションでこれらのレコードを追加すると、Microsoft サービスを使用するためにドメインがセットアップされます。
  

  
> [!NOTE]
>  通常、DNS の変更が有効になるのに 15 分ほどかかります。ただし、インターネットの DNS システム全体を更新する変更の場合、さらに長くかかることもあります。DNS レコードの追加でメール フローなどに問題が発生した場合は、「[ドメイン名または DNS レコードの変更後の問題に関するトラブルシューティング](../get-help-with-domains/find-and-fix-issues.md)」を参照してください。 
  
## <a name="add-a-txt-record-for-verification"></a>確認のための TXT レコードを追加する
<a name="BKMK_verify"> </a>

Microsoft のドメインを使うには、ドメインを所有していることを確認する必要があります。自分のドメイン レジストラーで自分のアカウントにログインし、DNS レコードを作成することができれば、Microsoft に対してドメインを所有していることを確認することができます。
  
> [!NOTE]
> このレコードは、ドメインを所有していることを確認するためだけに使用されます。その他には影響しません。 必要に応じて、後で削除することができます。 
  
次の手順を実行するか、[ビデオ (47 秒から開始) を参照](https://support.microsoft.com/office/c49698c2-6991-47fb-b5ac-18e49a505099)してください。
  
1. まず、[このリンク](https://www.networksolutions.com/manage-it)を使って Network Solutions でドメイン ページにアクセスします。ログインするように求められます。
    
    > [!IMPORTANT]
    > [ログイン] ボタンを **選択する前** に、[ログイン先:] ドロップダウン リストで [自分のドメイン名の管理 **]** を選択します。 
  
    ![[Manage My Domain Names] を選択して、Network Solutions にログインします](../../media/fda7d4a1-9445-4086-be9c-87c6983ef2aa.png)
  
2. 変更するドメインの名前の横にあるチェック ボックスをオンにします。
    
    ![自分のドメインのチェック ボックスを選択します](../../media/2c13d2ba-4a31-44da-812c-2cc90900a183.png)
  
3. [DNS **の編集] を選択します**。
    
    ![[DNS の編集] を選択します。](../../media/9d7c269f-48d1-442c-9d7b-63bd384a36a9.png)
  
4. [高度 **な DNS レコードの管理] を選択します**。
    
    (下へスクロールしなければならないことがあります。)
    
    ![[高度な DNS レコードの管理] を選択します。](../../media/fd2956d6-eec3-47ea-b60a-266bab14f51f.png)
  
5. [テキスト **(TXT レコード)] セクションまで** 下にスクロールし、[TXT レコードの編集 **] を選択します**。
    
    ![[TXT レコードの編集] を選択する](../../media/240a01d6-750a-4da6-8554-641b571e4b71.png)
  
6. 新規レコードのボックスに、次の表の値を入力するか、コピーして貼り付けます。
    
    |**Host**|**TTL**|**Text**|
    |:-----|:-----|:-----|
    |@  <br/> (The system will change this value to **@ (None)** when you save the record.)  <br/> |3600  <br/> |MS=ms *XXXXXXXX*  <br/> **注:** これは例です。 この表から **[宛先またはポイント先のアドレス]** の値を指定してください。  [確認する方法](../get-help-with-domains/information-for-dns-records.md)   |
       
    ![新しいレコードのボックスに値を入力または貼り付ける](../../media/8a76daab-b6ff-4c82-ba68-192b24fbb934.png)
  
7. [続行 **] を選択します**。
    
    ![[続行] を選択します。](../../media/89e7fb38-b4d9-4949-a1bb-d0dd10b361e0.png)
  
8. [変更 **の保存] を選択します**。
    
    ![[変更の保存] を選択します。](../../media/bd4d7cd0-c8a3-497a-b080-cfd5a5c60dc5.png)
  
9. 数分待つと、続行できます。この間、作成したレコードがインターネット全体で更新されます。
    
これで、ドメイン レジストラーのサイトでレコードが追加されました。Microsoft に戻り、レコードをリクエストします。
  
Microsoft で正しい TXT レコードが見つかった場合、ドメインは確認済みとなります。

1. 管理センターで、**[設定]** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">[ドメイン]</a> ページの順に移動します。
    
2. **[ドメイン]** ページで、確認するドメインを選択します。 
    
    
  
3. **[セットアップ]** ページで、**[セットアップの開始]** を選択します。
    
    
  
4. **[ドメインの確認]** ページで、**[確認]** を選択します。
    
    
  
> [!NOTE]
>  通常、DNS の変更が有効になるのに 15 分ほどかかります。ただし、インターネットの DNS システム全体を更新する変更の場合、さらに長くかかることもあります。DNS レコードの追加でメール フローなどに問題が発生した場合は、「[ドメイン名または DNS レコードの変更後の問題に関するトラブルシューティング](../get-help-with-domains/find-and-fix-issues.md)」を参照してください。 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>MX レコードを追加して、自分のドメインのメールが Microsoft に届くようにする
<a name="BKMK_add_MX"> </a>

次の手順を実行するか、[ビデオ (3 分 51 秒から開始) を参照](https://support.microsoft.com/office/c49698c2-6991-47fb-b5ac-18e49a505099)してください。
  
1. まず、[このリンク](https://www.networksolutions.com/manage-it)を使って Network Solutions でドメイン ページにアクセスします。ログインするように求められます。
    
    > [!IMPORTANT]
    > [ログイン] ボタンを **選択する前** に、[ログイン先:] ドロップダウン リストで [自分のドメイン名の管理 **]** を選択します。 
  
    ![[Manage My Domain Names] を選択して、Network Solutions にログインします](../../media/fda7d4a1-9445-4086-be9c-87c6983ef2aa.png)
  
2. 変更するドメインの名前の横にあるチェック ボックスをオンにします。
    
    ![自分のドメインのチェック ボックスを選択します](../../media/2c13d2ba-4a31-44da-812c-2cc90900a183.png)
  
3. [DNS **の編集] を選択します**。
    
    ![[DNS の編集] を選択します。](../../media/9d7c269f-48d1-442c-9d7b-63bd384a36a9.png)
  
4. [高度 **な DNS レコードの管理] を選択します**。
    
    (下へスクロールしなければならないことがあります。)
    
    ![[高度な DNS レコードの管理] を選択します。](../../media/fd2956d6-eec3-47ea-b60a-266bab14f51f.png)
  
5. [メール サーバー **(MX レコード)] セクションまで** 下にスクロールし、[MX レコードの編集 **] を選択します**。
    
    ![[MX レコードの編集] を選択する](../../media/74b4e412-9073-4d2d-8710-fe340b223798.png)
  
6. 新規レコードのボックスに、次の表の値を入力するか、コピーして貼り付けます。
    
    |**[優先度]**|**TTL**|**Mail Server**|
    |:-----|:-----|:-----|
    |10    <br/> 優先度の詳細については、「[MX 優先度とは何か](../setup/domains-faq.yml)」を参照してください。 <br/> |3600  <br/> | *\<domain-key\>*  .mail.protection.outlook.com。  <br/> **この値は、末尾がピリオド (.) でなければなりません** <br/> **注:** Microsoft アカウント  *\<domain-key\>*  からユーザーを取得します。 [確認する方法](../get-help-with-domains/information-for-dns-records.md)          |
       
    ![新しいレコードのボックスに値を入力または貼り付ける](../../media/0bb96872-cc6e-4dfa-a649-fb7efbbf0012.png)
  
7. [続行 **] を選択します**。
    
    ![[続行] を選択します。](../../media/963f758b-e79d-4452-8340-7eba8a3972c9.png)
  
8. [変更 **の保存] を選択します**。
    
    ![[変更の保存] を選択します。](../../media/7c2f784a-6dee-4364-866c-ad7202ef1fc2.png)
  
9. 他の MX レコードがある場合は、レコードごとに [ **Delete**] を選んで他の MX レコードをすべて削除します。 
    
    ![Select the Delete check box for other MX records](../../media/709d6133-9f5d-490a-a91e-95e21ca94695.png)
  
10. すべて選択されている場合は、[続行] を **選択します**。
    
    ![[続行] を選択します。](../../media/4710f988-0bbc-4ba7-bf31-ca2392b2900e.png)
  
11. [変更 **の保存] を選択します**。
    
    ![[変更の保存] を選択します。](../../media/24432ec6-666b-4612-9488-37c06437959b.png)
  
## <a name="add-the-cname-records-that-are-required-for-microsoft"></a>Microsoft に必要な CNAME レコードを追加する
<a name="BKMK_add_CNAME"> </a>

次の手順を実行するか、[ビデオ (4 分 43 秒から開始) を参照](https://support.microsoft.com/office/c49698c2-6991-47fb-b5ac-18e49a505099)してください。
  
1. まず、[このリンク](https://www.networksolutions.com/manage-it)を使って Network Solutions でドメイン ページにアクセスします。ログインするように求められます。
    
    > [!IMPORTANT]
    > [ログイン] ボタンを **選択する前** に、[ログイン先:] ドロップダウン リストで [自分のドメイン名の管理 **]** を選択します。 
  
    ![[Manage My Domain Names] を選択して、Network Solutions にログインします](../../media/fda7d4a1-9445-4086-be9c-87c6983ef2aa.png)
  
2. 変更するドメインの名前の横にあるチェック ボックスをオンにします。
    
    ![自分のドメインのチェック ボックスを選択します](../../media/2c13d2ba-4a31-44da-812c-2cc90900a183.png)
  
3. [DNS **の編集] を選択します**。
    
    ![[DNS の編集] を選択します。](../../media/9d7c269f-48d1-442c-9d7b-63bd384a36a9.png)
  
4. [高度 **な DNS レコードの管理] を選択します**。
    
    (下へスクロールしなければならないことがあります。)
    
    ![[高度な DNS レコードの管理] を選択します。](../../media/fd2956d6-eec3-47ea-b60a-266bab14f51f.png)
  
5. [ホスト エイリアス **(CNAME レコード)] セクション** まで下にスクロールし、[CNAME レコードの編集] **を選択します**。
    
    ![[ホスト エイリアス] で [CNAME レコードの編集] を選択します。](../../media/2d0a4666-8d40-48f4-886c-64a5157baaf5.png)
  
6. 4 つの新規レコードのボックスに、次の表の値を入力するか、コピーして貼り付けます。
    
    |**Alias**|**TTL**|**Refers to Host Name**|**Other Host          ([ **Other Host**] オプション ボタンを選びます)**|
    |:-----|:-----|:-----|:-----|
    |autodiscover  <br/> |3600  <br/> |(設定しない)  <br/> |autodiscover.outlook.com.  <br/> **この値は、末尾がピリオド (.) でなければなりません** <br/> |
    |sip  <br/> |3600  <br/> |(設定しない)  <br/> |sipdir.online.lync.com  <br/> **この値は、末尾がピリオド (.) でなければなりません** <br/> |
    |lyncdiscover  <br/> |3600  <br/> |(設定しない)  <br/> |webdir.online.lync.com.  <br/> **この値は、末尾がピリオド (.) でなければなりません** <br/> |
    |enterpriseregistration  <br/> |3600  <br/> |(設定しない)  <br/> |enterpriseregistration.windows.net  <br/> **この値は、末尾がピリオド (.) でなければなりません** <br/> |
    |enterpriseenrollment  <br/> |3600  <br/> |(設定しない)  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> **この値は、末尾がピリオド (.) でなければなりません** <br/> |
    
    ![新しいレコードの値を入力または貼り付ける](../../media/5ce0b30c-b46c-4778-aa5a-fb5e2f0961c1.png)
  
7. 必要なすべての CNAME レコードを追加した場合は、[続行] を **選択します**。
    
    ![[続行] を選択します。](../../media/4978bd8b-f6a6-458d-9522-ad612b301c4a.png)
  
8. [変更 **の保存] を選択します**。
    
    ![[変更の保存] を選択します。](../../media/f005c38a-0d8d-4c61-bec6-15e60c89aa5a.png)
  
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>迷惑メールの防止に役立つ、SPF の TXT レコードを追加する
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> 1 つのドメインで、SPF に複数の TXT レコードを設定することはできません。 1 つのドメインに複数の SPF レコードがあると、メール、配信の分類、迷惑メールの分類で問題が発生することがあります。 使用しているドメインに既に SPF レコードがある場合は、Microsoft 用に新しいレコードを作成しないでください。 代わりに、必要な Microsoft 値を現在のレコードに追加して、両方の値セットを含む  *1*  つの SPF レコードを作成します。 
  
次の手順を実行するか、[ビデオ (5 分 35 秒から開始) を参照](https://support.microsoft.com/office/c49698c2-6991-47fb-b5ac-18e49a505099)してください。
  
1. まず、[このリンク](https://www.networksolutions.com/manage-it)を使って Network Solutions でドメイン ページにアクセスします。ログインするように求められます。
    
    > [!IMPORTANT]
    > [ログイン] ボタンを **選択する前** に、[ログイン先:] ドロップダウン リストで [自分のドメイン名の管理 **]** を選択します。 
  
    ![[Manage My Domain Names] を選択して、Network Solutions にログインします](../../media/fda7d4a1-9445-4086-be9c-87c6983ef2aa.png)
  
2. 変更するドメインの名前の横にあるチェック ボックスをオンにします。
    
    ![自分のドメインのチェック ボックスを選択します](../../media/2c13d2ba-4a31-44da-812c-2cc90900a183.png)
  
3. [DNS **の編集] を選択します**。
    
    ![[DNS の編集] を選択します。](../../media/9d7c269f-48d1-442c-9d7b-63bd384a36a9.png)
  
4. [高度 **な DNS レコードの管理] を選択します**。
    
    (下へスクロールしなければならないことがあります。)
    
    ![[高度な DNS レコードの管理] を選択します。](../../media/fd2956d6-eec3-47ea-b60a-266bab14f51f.png)
  
5. [テキスト **(TXT レコード)] セクションまで** 下にスクロールし、[TXT レコードの編集 **] を選択します**。
    
    ![[テキスト] で [TXT レコードの編集] を選択します。](../../media/a69a2631-6da2-4e81-99ab-9a9ab9b30b07.png)
  
6. 新規レコードのボックスに次の値を入力するか、コピーして貼り付けます。
    
    |**Host**|**TTL**|**Text**|
    |:-----|:-----|:-----|
    |@  <br/> (The system will change this value to **@ (None)** when you save the record.)  <br/> |3600  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **注:** スペースも正しく入力されるように、この値をコピーして貼り付けることをお勧めします。 |
       
    ![新しいレコードの値を入力または貼り付ける](../../media/11564eca-e2ee-4f17-af2b-a00eb7c157db.png)
  
7. [続行 **] を選択します**。
    
    ![[続行] を選択します。](../../media/482a8dae-0c79-47c4-8bd8-87965683de24.png)
  
8. [変更 **の保存] を選択します**。
    
    ![[変更の保存] を選択します。](../../media/600b8c6d-184f-4213-a50e-8f119ebf3ff0.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Microsoft で必要な 2 つの SRV レコードを追加する
<a name="BKMK_add_SRV"> </a>

次の手順を実行するか、[ビデオ (6 分 18 秒から開始) を参照](https://support.microsoft.com/office/c49698c2-6991-47fb-b5ac-18e49a505099)してください。
  
1. まず、[このリンク](https://www.networksolutions.com/manage-it)を使って Network Solutions でドメイン ページにアクセスします。ログインするように求められます。
    
    > [!IMPORTANT]
    > [ログイン] ボタンを **選択する前** に、[ログイン先:] ドロップダウン リストで [自分のドメイン名の管理 **]** を選択します。 
  
    ![[Manage My Domain Names] を選択して、Network Solutions にログインします](../../media/fda7d4a1-9445-4086-be9c-87c6983ef2aa.png)
  
2. 変更するドメインの名前の横にあるチェック ボックスをオンにします。
    
    ![自分のドメインのチェック ボックスを選択します](../../media/2c13d2ba-4a31-44da-812c-2cc90900a183.png)
  
3. [DNS **の編集] を選択します**。
    
    ![[DNS の編集] を選択します。](../../media/9d7c269f-48d1-442c-9d7b-63bd384a36a9.png)
  
4. [高度 **な DNS レコードの管理] を選択します**。
    
    (下へスクロールしなければならないことがあります。)
    
    ![[高度な DNS レコードの管理] を選択します。](../../media/fd2956d6-eec3-47ea-b60a-266bab14f51f.png)
  
5. [サービス **(SRV レコード)] セクションまで下にスクロールし、[SRV** レコードの編集 **] を選択します**。
    
    ![[サービス] で [SRV レコードの編集] を選択します。](../../media/9a9248ea-5de5-4e16-9364-f7600fa371f5.png)
  
6. 2 つの新規レコードのボックスに、次の表の値を入力するか、コピーして貼り付けます。
    
    [ **Service**] と [ **Protocol**] の値をドロップダウン リストから選びます。 
    
    |**Service**|**Protocol**|**TTL**|**Priority**|**Weight**|**Port**|**Target**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip  <br/> |_tls  <br/> |3600  <br/> |100  <br/> |1  <br/> |443  <br/> |sipdir.online.lync.com  <br/> **この値は、末尾がピリオド (.) でなければなりません** <br/> |
    |_sipfederationtls  <br/> |_tcp  <br/> |3600  <br/> |100  <br/> |1  <br/> |5061  <br/> |sipfed.online.lync.com。  <br/> **この値は、末尾がピリオド (.) でなければなりません** <br/> |
       
    ![新しいレコードの値を入力または貼り付ける](../../media/86968d1c-8e43-4e61-aeaa-37fc7d7ef7a7.png)
  
7. [続行 **] を選択します**。
    
    ![[続行] を選択します。](../../media/bfe2c778-5d2b-4bb6-a79d-c3ff9caf9e1e.png)
  
8. [変更 **の保存] を選択します**。
    
    ![[変更の保存] を選択します。](../../media/6d323126-0ebe-45ab-8567-c234711d84c7.png)
  
> [!NOTE]
>  通常、DNS の変更が有効になるのに 15 分ほどかかります。ただし、インターネットの DNS システム全体を更新する変更の場合、さらに長くかかることもあります。DNS レコードの追加でメール フローなどに問題が発生した場合は、「[ドメイン名または DNS レコードの変更後の問題に関するトラブルシューティング](../get-help-with-domains/find-and-fix-issues.md)」を参照してください。 
