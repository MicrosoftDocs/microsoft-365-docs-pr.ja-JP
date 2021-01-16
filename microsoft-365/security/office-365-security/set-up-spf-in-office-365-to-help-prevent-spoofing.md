---
title: SPF を設定して、スプーフィングを防止する
f1.keywords:
- CSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/21/2019
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
ms.assetid: 71373291-83d2-466f-86ea-fc61493743a6
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Office 365 で Sender Policy Framework (SPF) をカスタム ドメインと併用できるように、ドメイン ネーム サービス (DNS) レコードを更新する方法について説明します。
ms.openlocfilehash: a6cd2a0cf60812bb874c1be63fb2d294cda6d6aa
ms.sourcegitcommit: 31be333178b934c519f419656f4c3a53e1beffdc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2021
ms.locfileid: "49881719"
---
# <a name="set-up-spf-to-help-prevent-spoofing"></a>SPF を設定して、スプーフィングを防止する

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

- [前提条件<a name="UpdateSPFTXT"></a>](#updating-your-spf-txt-record-for-office-365-a-nameUpdateSPFTXT)
- [Office 365 のための SPF TXT レコードの作成 /更新<a name="CreateUpdateSPFTXT"></a>](#to-create-or-update-your-spf-txt-record-a-namecreateupdatespftxta)
    - [サブドメインの処理方法とは?<a name="SPFandSubdomains"></a>](#how-to-handle-subdomains-a-namespfandsubdomainsa)
- [SPF のトラブルシューティングとベスト プラクティス <a name="TshootingSPF"></a>](#next-steps-after-you-set-up-spf-for-office-365-a-nametshootingspfa)
- [Advanced SPF の例 <a name="AdvancedSPFexs"></a>](#more-information-about-spf-a-nameadvancedspfexsa)

この記事では、Office 365 で Sender Policy Framework (SPF) のメール認証をカスタム ドメインと併用できるように、ドメイン ネーム サービス (DNS) レコードを更新する方法について説明します。

SPF を使うと、カスタム ドメインから送信される送信電子メールを検証できます。 推奨されているメール認証方法のDMARC と DKIM (Office 365 でサポートされている他の 2 つのメール認証方法) を設定する最初の手順です。

## <a name="updating-your-spf-txt-record-for-office-365"></a>Office 365 の SPF TXT レコードを更新する<a name="UpdateSPFTXT"></a>

> [!IMPORTANT]
> **中小企業のビジネス** または IP アドレスまたは DNS の構成に慣れていない場合は、インターネット ドメイン レジストラーに電話してください (例: GoDaddy、Bluehost、web.com)。SPF の DNS 構成 (および他のメール認証方法) に関するヘルプを求めることができます。 *また*、ユーザー設定の URL (つまり、ユーザーと顧客が Office 365 にアクセスする URL が **onmicrosoft.com** で終了の場合) を購入していない場合、またはカスタム URL を使用していない場合は、Office 365 サービスで SPF が設定されています。 その場合は、それ以上の手順は必要ありません。 ご確認ありがとうございます。

DNS で TXT レコードを更新する前に、レコード作成に必要な情報を収集する必要があります。 サポートされている SPF 構文の高度な例や詳細については、「[Office 365 において SPF がスプーフィングとフィッシングを防ぐしくみ](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks)」をご覧ください。

次の情報を収集します。

- もしあれば、カスタム ドメインの現在の SPF TXT レコード。 手順に関しては、「[Office 365 の DNS レコードの作成に必要な情報を収集する](https://docs.microsoft.com/microsoft-365/admin/get-help-with-domains/information-for-dns-records)」をご覧ください。

- メッセージング サーバーに移動して、(すべてのオンプレミス メッセージング サーバーからの必要な) 外部 IP アドレスを発見します。 たとえば、**131.107.2.200** などです。

- SPF TXT レコードに含める必要があるサードパーティ製のすべてのドメインに使用するドメイン名。一部のバルク メール プロバイダーは、顧客用のサブドメインを設定しています。たとえば、会社 MailChimp に **servers.mcsv.net** を設定するなどです。

- SPF TXT レコードで使う強制ルールを決定します。 **-all** ルールが推奨されます。 その他の構文オプションについて詳しくは、「[Office 365 用の SPF TXT レコードの構文](how-office-365-uses-spf-to-prevent-spoofing.md#SPFSyntaxO365)」をご覧ください。

> [!IMPORTANT]
> カスタム ドメインを使用するには、Office 365 では、Sender Policy Framework (SPF) TXT レコードを DNS レコードに追加してスプーフィングを防止する必要があります。

## <a name="create-or-update-your-spf-txt-record"></a>SPF TXT レコードを作成または更新する<a name="CreateUpdateSPFTXT"></a>

1. 以下の表の SFP 構文について、十分に理解しておいてください。

   ****

   |要素|もし今使っているとしたら...|お客様に共通のことでは?|追加対象|
   |---|---|---|---|
   |1|いずれかの電子メール システム (必須)|共通。この値で始まるすべての SPF レコード|`v=spf1`|
   |2|Exchange Online|共通|`include:spf.protection.outlook.com`|
   |3|Exchange Online 専用のみ|共通ではない|`ip4:23.103.224.0/19` <br> `ip4:206.191.224.0/19` <br> `ip4:40.103.0.0/16` <br> `include:spf.protection.outlook.com`|
   |4|Office 365 Germany、Microsoft Cloud Germany のみ|共通ではない|`include:spf.protection.outlook.de`|
   |5|サード パーティ製の電子メール システム|共通ではない|`include:<domain_name>` <p> \<domain_name\> は、サード パーティ製の電子メール システムのドメインです。|
   |6|オンプレミスの電子メール システム。たとえば、Exchange Online Protection と別のメール システム|共通ではない|各追加メール システムで次のいずれかを使用します。 <p> `ip4:<IP_address>` <br> `ip6:<IP_address>` <br> `include:<domain_name>` <p> \<IP_address\> と \<domain_name\> は、ドメインの代理としてメールを送信する他のメールシステムの IP アドレスとドメインです。|
   |7|いずれかの電子メール システム (必須)|共通。この値で終わるすべての SPF レコード|`<enforcement rule>` <p> これは、いくつかの値のどれか 1 つかもしれません。 値 `-all` をお勧めします。|
   |

2. まだ行っていない場合は、表の構文を使用して SPF TXT レコードを作成します。

   たとえば、Office 365 で完全にホストされている場合、つまり、オンプレミスのメール サーバーを使っていない場合は、SPF TXT レコードには、次のように 1 行目、2 行目、7 行目が含まれます。

   ```text
   v=spf1 include:spf.protection.outlook.com -all
   ```

   これは、最も一般的な SPF TXT レコードです。 このレコードは、Microsoft データセンターが米国、ヨーロッパ (ドイツを含む)、または他の場所にあっても、ほぼすべてのユーザーに対して機能します。

   ただし、Microsoft Cloud Germany の一部である Office 365 Germany を購入している場合は、2 行目ではなく 4 行目から include ステートメントを使用してください。たとえば、Office 365 Germany で完全にホストされている場合、つまり、オンプレミスのメール サーバーを使っていない場合は、SPF TXT レコードには、次のように 1 行目、4 行目、7 行目が含まれます。

   ```text
   v=spf1 include:spf.protection.outlook.de -all
   ```

   Office 365 で既に展開し、カスタム ドメインの SPF TXT レコードをセットアップしている状態で Office 365 Germany に移行する場合は、SPF TXT レコードを更新する必要があります。 これを行うには、`include:spf.protection.outlook.com` を`include:spf.protection.outlook.de`に変更します。

3. SPF TXT レコードを構成した後、DNS でレコードを更新する必要があります。 ドメインに配置できる SPF TXT レコードは 1 つのみです。 SPF TXT レコードが存在する場合、新しいレコードを追加するのではなく、既存のレコードを更新しなければなりません。 「[Office 365 の DNS レコードを作成する](https://docs.microsoft.com/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider)」に移動し、DNS ホストのリンクをクリックします。

4. SPF TXT レコードをテストします。

## <a name="how-to-handle-subdomains"></a>サブドメインの処理方法とは? <a name="SPFandSubdomains"></a>

*サブドメインは、トップ レベル ドメインの SPF レコードを継承しないので、サブドメインごとに、別々のレコードを作成する必要がある* ことに注意してください。

存在しないサブドメインからのメールを、攻撃者が送信することを防ぐために、すべてのドメインとサブドメインに対して追加のワイルドカード SPF レコード (`*.`) が必要です。 例:

```text
*.subdomain.contoso.com. IN TXT "v=spf1 -all"
```

## <a name="next-steps"></a>次の手順<a name="TshootingSPF"></a>

SPF TXT レコードで問題が発生していますか? [「トラブルシューティング: Office 365 における SPF のベスト プラクティス」](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot)をお読みください。


## <a name="what-does-spf-email-authentication-actually-do"></a>SPF メール認証は、実際に何を行いますか?

SPF は、ユーザーのためにメールを送信できるメール サーバーを識別します。 基本的には、SPF を DKIM、DMARC、その他の Office 365 でサポートされているテクノロジと併用することによって、スプーフィングとフィッシング詐欺を防止できます。 SPF は TXT レコードとして追加され、DNS はこのレコードを使って、カスタム ドメインの代わりにメールを送信できるメール サーバーを識別します。 受信側のメール システムは、この SPF TXT レコードを参照して、カスタム ドメインからのメッセージが、承認されたメッセージング サーバーからのものであるかどうかを判別します。

たとえば、カスタム ドメイン contoso.com が Office 365 を使用しているとします。ユーザーのドメインの正当なメール サーバーとして Office 365 メッセージング サーバーを一覧表示する SPF TXT レコードを追加します。受信メッセージング サーバーが joe@contoso.com からのメッセージを取得すると、サーバーによって contoso.com の SPF TXT レコードが検索され、適切なメッセージであるかどうかが検出されます。受信サーバーで、SPF レコードに一覧表示されている Office 365 メッセージング サーバー以外のサーバーからメッセージを取得していることが検出された場合、受信メール サーバーはそのメッセージを迷惑メールとして拒否できます。

また、カスタム ドメインに SPF TXT レコードが含まれていないと、一部の受信サーバーはメッセージを完全に拒否することがあります。これは、受信サーバーが、承認されたメッセージング サーバーからのメッセージであることを検証できないためです。

既に Office 365 のメールを設定している場合、SPF TXT レコードとして Microsoft のメッセージング サーバーが DNS に含まれています。ただし、場合によっては DNS で SPF TXT レコードを更新する必要があります。たとえば、次のような場合です。

- 以前は、SharePoint Online を使用している場合、カスタム ドメインに別の SPF TXT レコードを追加する必要がありました。この作業を行う必要はなくなりました。この変更により、SharePoint Online の通知メッセージが [迷惑メール] フォルダーに振り分けられるリスクが軽減されます。参照の制限数である 10 に達し、"参照制限を超えました"、"ホップが多すぎます" などのメッセージを示すエラーが表示される場合は、SPF TXT レコードを更新します。

- Office 365 とオンプレミスの Exchange を使用したハイブリッド環境の場合。

- DKIM と DMARC をセットアップする場合 (推奨)。

## <a name="more-information-about-spf"></a>SPF の詳細情報<a name="AdvancedSPFexs"></a>

サポートされている SPF 構文、スプーフィング、トラブルシューティング、Office 365 が SPF をサポートする方法の高度な例や詳細については、「[Office 365 において SPF がスプーフィングとフィッシングを防ぐしくみ](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks)」をご覧ください。

## <a name="links-to-configure-dkim-and-dmarc"></a>DKIM と DMARC を構成するリンク

 SPF はスプーフィングの防止に役立ちますが、SPF では保護できないスプーフィング テクニックがあります。 それらから保護するには、SPF のセットアップ後に、DKIM と DMARC を Office 365 用に構成する必要があります。

[DKIM](https://docs.microsoft.com/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email?view=o365-worldwide) メール認証の目標は、メールの内容が改ざんされていないと証明することです。

[DMARC](https://docs.microsoft.com/microsoft-365/security/office-365-security/use-dmarc-to-validate-email?view=o365-worldwide) メール認証の目標は、SPF と DKIM の情報が From アドレスと確実に一致していることを確認することです。