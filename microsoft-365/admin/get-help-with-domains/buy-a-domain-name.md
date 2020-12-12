---
title: ドメイン名を購入する
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
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- okr_smb
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 1561140a-16a9-4a02-822d-a989250e479d
description: Microsoft 365 でドメイン名を購入する方法について説明します。
ms.openlocfilehash: d8c0bac5921b5cb3efacffdfee3ab948857b8a1f
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "49658613"
---
# <a name="buy-a-domain-name"></a>ドメイン名を購入する

::: moniker range="o365-21vianet"

> [!NOTE]
> 管理センターは変更されました。 エクスペリエンスがここで説明されている詳細と一致しない場合は、「[新しい Microsoft 365 管理センターについて](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet)」を参照してください。

::: moniker-end

 *追加、変更またはドメインを削除するには、[ビジネスまたはエンタープライズ プラン](https://products.office.com/business/office)の **グローバル管理者** である **必要** があります。これらの変更は、テナント全体、*カスタマイズ管理者* または *正規ユーザー* に影響を与え、変更を加えることはできません。*  

 探している内容が見つからない場合は、**[ドメインに関する FAQ を確認Q](../setup/domains-faq.yml)** を参照してください。 
  
### <a name="sign-in-and-go-to-settings--domains--buy-a-domain"></a>サインインして [設定ドメイン] \> ドメインを購入 \> するに移動する

1. 管理センターで、**[設定]** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">[ドメイン]</a> ページの順に移動します。
    
3. On the **Domains** page, select **Buy domain**.
    
次のトップレベル ドメインからドメインを選ぶことができます。
  
- .biz
    
- .com
    
- .info
    
- .me
    
- .mobi
    
- .net
    
- .org
    
- .tv
    
- .co.uk
    
- org.uk
    

> [!NOTE]
> [ドメインの **購入**] を選択すると、テナントが Microsoft パートナーを通じて購入/管理されている場合、Microsoft パートナーの Web サイトにリダイレクトされる可能性があります。

### <a name="domain-privacy"></a>ドメインプライバシー
ドメインを購入すると、無料のドメイン プライバシー サブスクリプションが提供されます。 これにより、ICANN プライベートを使用したドメインの登録に連絡先情報が添付されます。 [詳細情報](https://whois.icann.org/en/privacy-and-proxy-services)
  
### <a name="buy-a-domain-from-another-domain-registrar"></a>別のドメイン レジストラーからドメインを購入する
[GoDaddy](https://www.godaddy.com)以外のドメイン レジストラーからドメインを購入する場合は、自動セットアップ (ドメイン接続) をサポートする以下のドメイン レジストラーを使用することをお勧めします。 
  
- [1 &amp; 1](https://www.1and1.com/)
- [WordPress](https://www.wordpress.com) 

   
### <a name="transfer-your-domain-to-a-different-domain-registrar"></a>ドメインを別のドメイン レジストラーに移行する

必要な DNS レコードの一部をサポートしていないプロバイダーがドメインを管理している場合は、ドメインを別のレジストラーに移行することができます。ドメインを移行するときには、ドメイン名の更新と保持のために支払先を変更します。
  
ドメインの移行先レジストラーに移行をリクエストします。 **DNS の移行** などのオプションについては、そのレジストラーの Web サイトでお確かめください。レジストラーでの変更後、インターネットに更新が行き渡るまでには数日かかることがあります。
 



::: moniker range="o365-21vianet"
## <a name="how-to-buy-a-domain-for-office-365-operated-by-21vianet"></a>21Vianet が運営する Office 365 のドメインを購入する方法



専用ドメインをまだ持っていない場合は、ドメイン名レジストラー、ドメイン リセラー、現在のインターネット プロバイダーなどからオンラインで簡単に購入できます。21Vianet が運営する Office 365 にサインアップすると、たとえば、contoso.partner.onmschina.cn のようなドメイン名を与えられますが、fourthcoffee.com のようなカスタム ドメイン名を使うこともできます。
  
Microsoft 365 でドメインをセットアップするには、ドメインを所有し、ドメインの DNS レコードの一部を変更する必要があります。
  
> [!CAUTION]
> 一部のドメイン レジストラーまたは DNS ホスティング プロバイダーでは、Microsoft 365 で必要なすべての DNS レコードの作成が許可されていない場合があります。 必要なすべてのレコードをサポートしているホスティング プロバイダーの一覧を次に示します。 別のホスティング プロバイダーの使用を考えている場合は、 [Service limitations when your hosting provider does not support SRV, CNAME, TXT, or redirection](https://support.microsoft.com/office/dfbb03e3-08c1-4c4e-b2f0-891665b29b77)してください。 
  
ドメインを (ドメイン レジストラーで) 登録した後、管理者として Microsoft 365 にサインインし、メール アドレスや他のサービスで使用できるようドメインを設定します。
  
> [!NOTE]
> この記事の SharePoint Online パブリック Web サイトの情報は、組織が 2015 年 3 月 9 日より前に Microsoft 365 を購入した場合にのみ適用されます。 

## <a name="domain-registrars-that-support-all-dns-records-required-for-microsoft-365"></a>Microsoft 365 に必要なすべての DNS レコードをサポートするドメイン レジストラー

- [Oray](https://oray.com/)
    
- [HiChina](https://www.hichina.com/)
    
- [east.net](http://www.east.net/)
    
- [BIZCN](https://www.bizcn.com/)
    
::: moniker-end

## <a name="related-articles"></a>関連記事

[Microsoft 365 にドメインを追加する](../setup/add-domain.md)

[ドメイン FAQ](../setup/domains-faq.yml)

[DNS レコードを更新して、Web サイトを現在のホスティング プロバイダーに維持します](https://docs.microsoft.com/microsoft-365/admin/dns/update-dns-records-to-retain-current-hosting-provider)。
