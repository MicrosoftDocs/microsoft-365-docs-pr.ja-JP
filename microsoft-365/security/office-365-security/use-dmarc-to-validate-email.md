---
title: DMARC を使用してメールを検証する
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
ms.assetid: 4a05898c-b8e4-4eab-bd70-ee912e349737
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Domain-based Message Authentication, Reporting, and Conformance (DMARC) を構成して、組織から送信されたメッセージを検証する方法について説明します。
ms.openlocfilehash: 9dd97b1fc60f0b6198bb6c55af291c7dd103ac5d
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "49615338"
---
# <a name="use-dmarc-to-validate-email"></a><span data-ttu-id="fec1f-103">DMARC を使用してメールを検証する</span><span class="sxs-lookup"><span data-stu-id="fec1f-103">Use DMARC to validate email</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


<span data-ttu-id="fec1f-104">Domain-based Message Authentication, Reporting, and Conformance ([DMARC](https://dmarc.org)) は、Sender Policy Framework (SPF) および DomainKeys Identified Mail (DKIM) と併用することで、メールの送信者を認証できるようになり、送信先の電子メール システムはドメインから送信されたメッセージを信頼するようになります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-104">Domain-based Message Authentication, Reporting, and Conformance ([DMARC](https://dmarc.org)) works with Sender Policy Framework (SPF) and DomainKeys Identified Mail (DKIM) to authenticate mail senders and ensure that destination email systems trust messages sent from your domain.</span></span> <span data-ttu-id="fec1f-105">SPF および DKIM と共に DMARC を実装すると、メールのスプーフィングやフィッシングに対抗する追加の保護が得られます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-105">Implementing DMARC with SPF and DKIM provides additional protection against spoofing and phishing email.</span></span> <span data-ttu-id="fec1f-106">DMARC は、電子メールを受信するシステムが、ドメインから送信された SPF チェックまたは DKIM チェックに失敗したメッセージに対して、どのように対応するかを判断する際に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-106">DMARC helps receiving mail systems determine what to do with messages sent from your domain that fail SPF or DKIM checks.</span></span>

> [!TIP]
> <span data-ttu-id="fec1f-107">Microsoft 365 用の DMARC レポートを提供しているサードパーティ ベンダーを確認するには、「[Microsoft Intelligent Security Association (MISA)](https://www.microsoft.com/misapartnercatalog)」(Microsoft インテリジェント セキュリティ アソシエーション) カタログを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fec1f-107">Visit the [Microsoft Intelligent Security Association (MISA)](https://www.microsoft.com/misapartnercatalog) catalog to view third-party vendors offering DMARC reporting for Microsoft 365.</span></span>

## <a name="how-do-spf-and-dmarc-work-together-to-protect-email-in-microsoft-365"></a><span data-ttu-id="fec1f-108">SPF と DMARC が連携して Microsoft 365 の電子メールを保護するしくみ</span><span class="sxs-lookup"><span data-stu-id="fec1f-108">How do SPF and DMARC work together to protect email in Microsoft 365?</span></span>

 <span data-ttu-id="fec1f-109">電子メール メッセージには、発信者、送信者、またはアドレスが含まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-109">An email message may contain multiple originator, or sender, addresses.</span></span> <span data-ttu-id="fec1f-110">これらのアドレスは、さまざまな目的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-110">These addresses are used for different purposes.</span></span> <span data-ttu-id="fec1f-111">たとえば、次のアドレスについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="fec1f-111">For example, consider these addresses:</span></span>

- <span data-ttu-id="fec1f-112">**「Mail From」アドレス**: 送信者を識別し、メッセージの配信に問題が発生した場合に、配信不能通知などの通知の返送先を指定します。</span><span class="sxs-lookup"><span data-stu-id="fec1f-112">**"Mail From" address**: Identifies the sender and specifies where to send return notices if any problems occur with the delivery of the message, such as non-delivery notices.</span></span> <span data-ttu-id="fec1f-113">これは電子メール メッセージのエンベロープ部分に表示されます。通常、ユーザーの電子メール アプリケーションには表示されません。</span><span class="sxs-lookup"><span data-stu-id="fec1f-113">This appears in the envelope portion of an email message and is not usually displayed by your email application.</span></span> <span data-ttu-id="fec1f-114">これは、5321.MailFrom アドレスまたはリバース パス アドレスとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-114">This is sometimes called the 5321.MailFrom address or the reverse-path address.</span></span>

- <span data-ttu-id="fec1f-115">**「From」アドレス**: From アドレスとして、ユーザーの電子メール アプリケーションに表示されるアドレス。</span><span class="sxs-lookup"><span data-stu-id="fec1f-115">**"From" address**: The address displayed as the From address by your mail application.</span></span> <span data-ttu-id="fec1f-116">このアドレスにより、電子メールの作成者を識別します。</span><span class="sxs-lookup"><span data-stu-id="fec1f-116">This address identifies the author of the email.</span></span> <span data-ttu-id="fec1f-117">つまり、メッセージを書いた個人またはシステムのメールボックスになります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-117">That is, the mailbox of the person or system responsible for writing the message.</span></span> <span data-ttu-id="fec1f-118">これは、 5322.From アドレスとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-118">This is sometimes called the 5322.From address.</span></span>

<span data-ttu-id="fec1f-p105">SPF は、DNS TXT レコードを使用して、特定のドメインに対する認証済みの送信側 IP アドレスのリストを提示します。通常、SPF チェックは 5321.MailFrom アドレスに対してのみ実行されます。つまり、単独で SPF を使用すると、5322.From アドレスは認証されないことになります。これは、SPF チェックにパスしていても、5322.From 送信者アドレスがスプーフィングされたメッセージをユーザーが受信するというシナリオの余地を残すことになります。たとえば、次のような SMTP トランスクリプトを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p105">SPF uses a DNS TXT record to provide a list of authorized sending IP addresses for a given domain. Normally, SPF checks are only performed against the 5321.MailFrom address. This means that the 5322.From address is not authenticated when you use SPF by itself. This allows for a scenario where a user can receive a message which passes an SPF check but has a spoofed 5322.From sender address. For example, consider this SMTP transcript:</span></span>

```console
S: Helo woodgrovebank.com
S: Mail from: phish@phishing.contoso.com
S: Rcpt to: astobes@tailspintoys.com
S: data
S: To: "Andrew Stobes" <astobes@tailspintoys.com>
S: From: "Woodgrove Bank Security" <security@woodgrovebank.com>
S: Subject: Woodgrove Bank - Action required
S:
S: Greetings User,
S:
S: We need to verify your banking details.
S: Please click the following link to verify that we have the right information for your account.
S:
S: https://short.url/woodgrovebank/updateaccount/12-121.aspx
S:
S: Thank you,
S: Woodgrove Bank
S: .
```

<span data-ttu-id="fec1f-124">このトランスクリプトでは、送信者のアドレスは次にようになります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-124">In this transcript, the sender addresses are as follows:</span></span>

- <span data-ttu-id="fec1f-125">Mail From アドレス (5321.MailFrom): phish@phishing.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fec1f-125">Mail from address (5321.MailFrom): phish@phishing.contoso.com</span></span>

- <span data-ttu-id="fec1f-126">From アドレス (5322.From): security@woodgrovebank.com</span><span class="sxs-lookup"><span data-stu-id="fec1f-126">From address (5322.From): security@woodgrovebank.com</span></span>

<span data-ttu-id="fec1f-p106">SPF を構成した場合、受信側サーバーは Mail From アドレス phish@phishing.contoso.com に対してチェックを実行します。メッセージがドメイン phishing.contoso.com の有効なソースから送信された場合は、SPF チェックをパスします。電子メール クライアントには差出人アドレスのみが表示されるため、ユーザーには、このメッセージが security@woodgrovebank.com から送信されたように見えます。SPF だけでは、woodgrovebank.com の有効性は認証されません。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p106">If you configured SPF, then the receiving server performs a check against the Mail from address phish@phishing.contoso.com. If the message came from a valid source for the domain phishing.contoso.com then the SPF check passes. Since the email client only displays the From address, the user sees that this message came from security@woodgrovebank.com. With SPF alone, the validity of woodgrovebank.com was never authenticated.</span></span>

<span data-ttu-id="fec1f-p107">DMARC を使用すると、From アドレスに対するチェックを受信側サーバーも実行するようになります。前述の例では、woodgrovebank.com の所定の場所に DMARC TXT レコードが存在していれば、From アドレスに対するチェックは失敗します。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p107">When you use DMARC, the receiving server also performs a check against the From address. In the example above, if there is a DMARC TXT record in place for woodgrovebank.com, then the check against the From address fails.</span></span>

## <a name="what-is-a-dmarc-txt-record"></a><span data-ttu-id="fec1f-133">DMARC TXT レコードとは</span><span class="sxs-lookup"><span data-stu-id="fec1f-133">What is a DMARC TXT record?</span></span>

<span data-ttu-id="fec1f-p108">SPF の DNS レコードと同様に、DMARC のレコードは、スプーフィングとフィッシングの防止に役立つ DNS テキスト (TXT) レコードです。DMARC TXT レコードは DNS で発行します。DMARC TXT レコードは、メール作成者の IP アドレスを、送信側ドメインの所有者とされる名前と照合して、メール メッセージの発信元を確認します。 この DMARC TXT レコードにより、承認済みの送信メール サーバーを識別します。送信先メール システムでは、メッセージが承認済みの送信メール サーバーから発信されたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p108">Like the DNS records for SPF, the record for DMARC is a DNS text (TXT) record that helps prevent spoofing and phishing. You publish DMARC TXT records in DNS. DMARC TXT records validate the origin of email messages by verifying the IP address of an email's author against the alleged owner of the sending domain. The DMARC TXT record identifies authorized outbound email servers. Destination email systems can then verify that messages they receive originate from authorized outbound email servers.</span></span>

<span data-ttu-id="fec1f-139">Microsoft の DMARC TXT レコードは、次のような内容になります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-139">Microsoft's DMARC TXT record looks something like this:</span></span>

```console
_dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.agari.com; ruf=mailto:d@ruf.agari.com; fo=1"
```

<span data-ttu-id="fec1f-140">Microsoft は、DMARC レポートをサード パーティの [Agari](https://agari.com) に送信します。</span><span class="sxs-lookup"><span data-stu-id="fec1f-140">Microsoft sends its DMARC reports to [Agari](https://agari.com), a third party.</span></span> <span data-ttu-id="fec1f-141">Agari では、DMARC レポートを収集して分析します。</span><span class="sxs-lookup"><span data-stu-id="fec1f-141">Agari collects and analyzes DMARC reports.</span></span> <span data-ttu-id="fec1f-142">Microsoft 365 用の DMARC レポートを提供している他のサードパーティ ベンダーを確認するには、[MISA カタログ](https://www.microsoft.com/misapartnercatalog)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fec1f-142">Please visit the [MISA catalog](https://www.microsoft.com/misapartnercatalog) to view more third-party vendors offering DMARC reporting for Microsoft 365.</span></span>

## <a name="implement-dmarc-for-inbound-mail"></a><span data-ttu-id="fec1f-143">受信メール用に DMARC を実装する</span><span class="sxs-lookup"><span data-stu-id="fec1f-143">Implement DMARC for inbound mail</span></span>

<span data-ttu-id="fec1f-p110">Microsoft 365 で受信するメールの DMARC を設定するために必要な手順はありません。すべて、Microsoft が手配します。DMARC チェックをパスしないメールに対する処理について知る必要がある場合は、「[Microsoft 365 が DMARC に失敗した受信メールを処理する方法](#how-microsoft-365-handles-inbound-email-that-fails-dmarc)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p110">You don't have to do a thing to set up DMARC for mail that you receive in Microsoft 365. We've taken care of everything for you. If you want to learn what happens to mail that fails to pass our DMARC checks, see [How Microsoft 365 handles inbound email that fails DMARC](#how-microsoft-365-handles-inbound-email-that-fails-dmarc).</span></span>

## <a name="implement-dmarc-for-outbound-mail-from-microsoft-365"></a><span data-ttu-id="fec1f-147">Microsoft 365 からの送信メール用に DMARC を実装する</span><span class="sxs-lookup"><span data-stu-id="fec1f-147">Implement DMARC for outbound mail from Microsoft 365</span></span>

<span data-ttu-id="fec1f-p111">Microsoft 365 を使用しているもののカスタム ドメインを使用していない場合 (つまり、onmicrosoft.com を使用する場合)、組織で DMARC を構成または実装するために、他に行わなければならないことは何もありません。SPF のセットアップは既に完了しており、Microsoft 365 により自動的に送信メールに DKIM 署名が生成されます。この署名の詳細については「[DKIM と Microsoft 365 の既定の動作](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p111">If you use Microsoft 365 but you aren't using a custom domain, that is, you use onmicrosoft.com, you don't need to do anything else to configure or implement DMARC for your organization. SPF is already set up for you and Microsoft 365 automatically generates a DKIM signature for your outgoing mail. For more information about this signature, see [Default behavior for DKIM and Microsoft 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).</span></span>

 <span data-ttu-id="fec1f-p112">カスタム ドメインを所有している場合や、Microsoft 365 に加えてオンプレミスの Exchange サーバーも使用している場合は、送信メール用に手動で DMARC を実装する必要があります。カスタム ドメイン用に DMARC を実装する手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p112">If you have a custom domain or you are using on-premises Exchange servers in addition to Microsoft 365, you need to manually implement DMARC for your outbound mail. Implementing DMARC for your custom domain includes these steps:</span></span>

- [<span data-ttu-id="fec1f-153">手順 1:ドメインに対する有効なメールのソースを特定する</span><span class="sxs-lookup"><span data-stu-id="fec1f-153">Step 1: Identify valid sources of mail for your domain</span></span>](#step-1-identify-valid-sources-of-mail-for-your-domain)

- [<span data-ttu-id="fec1f-154">手順 2: ドメイン用に SPF をセットアップする</span><span class="sxs-lookup"><span data-stu-id="fec1f-154">Step 2: Set up SPF for your domain</span></span>](#step-2-set-up-spf-for-your-domain)

- [<span data-ttu-id="fec1f-155">手順 3: カスタム ドメイン用に DKIM をセットアップする</span><span class="sxs-lookup"><span data-stu-id="fec1f-155">Step 3: Set up DKIM for your custom domain</span></span>](#step-3-set-up-dkim-for-your-custom-domain)

- [<span data-ttu-id="fec1f-156">手順 4: ドメイン用の DMARC TXT レコードを作成する</span><span class="sxs-lookup"><span data-stu-id="fec1f-156">Step 4: Form the DMARC TXT record for your domain</span></span>](#step-4-form-the-dmarc-txt-record-for-your-domain)

### <a name="step-1-identify-valid-sources-of-mail-for-your-domain"></a><span data-ttu-id="fec1f-157">手順 1:ドメインに対する有効なメールのソースを特定する</span><span class="sxs-lookup"><span data-stu-id="fec1f-157">Step 1: Identify valid sources of mail for your domain</span></span>

<span data-ttu-id="fec1f-p113">既に SPF のセットアップが済んでいる場合は、この演習を完了していることになります。ただし、DMARC には追加の考慮事項があります。ドメインに対するメールのソースを特定するときには、2 つの問いに答える必要があります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p113">If you have already set up SPF then you have already gone through this exercise. However, for DMARC, there are additional considerations. When identifying sources of mail for your domain there are two questions you need to answer:</span></span>

- <span data-ttu-id="fec1f-161">どの IP アドレスにドメインからメッセージを送信するか。</span><span class="sxs-lookup"><span data-stu-id="fec1f-161">What IP addresses send messages from my domain?</span></span>

- <span data-ttu-id="fec1f-162">自分の代わりにサード パーティから送信されるメールについて、5321.MailFrom ドメインと 5322.From ドメインが一致しているか。</span><span class="sxs-lookup"><span data-stu-id="fec1f-162">For mail sent from third parties on my behalf, will the 5321.MailFrom and 5322.From domains match?</span></span>

### <a name="step-2-set-up-spf-for-your-domain"></a><span data-ttu-id="fec1f-163">手順 2: ドメイン用に SPF をセットアップする</span><span class="sxs-lookup"><span data-stu-id="fec1f-163">Step 2: Set up SPF for your domain</span></span>

<span data-ttu-id="fec1f-164">すべての有効な送信者の一覧が用意できると、「[SPF を設定して、スプーフィングを防止する](set-up-spf-in-office-365-to-help-prevent-spoofing.md)」手順を実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-164">Now that you have a list of all your valid senders you can follow the steps to [Set up SPF to help prevent spoofing](set-up-spf-in-office-365-to-help-prevent-spoofing.md).</span></span>

<span data-ttu-id="fec1f-165">たとえば、contoso.com が Exchange Online からメールを送信するとします。このとき、オンプレミスの Exchange サーバーの IP アドレスが 192.168.0.1、Web アプリケーションの IP アドレスが 192.168.100.100 だと仮定すると、SPF TXT テキストレコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-165">For example, assuming contoso.com sends mail from Exchange Online, an on-premises Exchange server whose IP address is 192.168.0.1, and a web application whose IP address is 192.168.100.100, the SPF TXT record would look like this:</span></span>

```console
contoso.com  IN  TXT  " v=spf1 ip4:192.168.0.1 ip4:192.168.100.100 include:spf.protection.outlook.com -all"
```

<span data-ttu-id="fec1f-166">ベスト プラクティスとして、SPF TXT レコードでは、サード パーティの送信者についても考慮に入れておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-166">As a best practice, ensure that your SPF TXT record takes into account third-party senders.</span></span>

### <a name="step-3-set-up-dkim-for-your-custom-domain"></a><span data-ttu-id="fec1f-167">手順 3: カスタム ドメイン用に DKIM をセットアップする</span><span class="sxs-lookup"><span data-stu-id="fec1f-167">Step 3: Set up DKIM for your custom domain</span></span>

<span data-ttu-id="fec1f-p114">SPF のセットアップ後には、DKIM をセットアップする必要があります。DKIM では、電子メール メッセージのメッセージ ヘッダー内にデジタル署名を追加できます。DKIM をセットアップする代わりに、ドメインに対して Microsoft 365 で既定の DKIM 構成の使用を許可すると、DMARC が失敗することがあります。これは、既定の DKIM 構成が、5322.From アドレスとしてカスタム ドメインではなく初期設定の onmicrosoft.com ドメインを使用するためです。これにより、ドメインから送信されたすべてのメールの 5321.MailFrom アドレスと 5322.From アドレスとの間に不一致が生じることになります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p114">Once you have set up SPF, you need to set up DKIM. DKIM lets you add a digital signature to email messages in the message header. If you do not set up DKIM and instead allow Microsoft 365 to use the default DKIM configuration for your domain, DMARC may fail. This is because the default DKIM configuration uses your initial onmicrosoft.com domain as the 5322.From address, not your custom domain. This forces a mismatch between the 5321.MailFrom and the 5322.From addresses in all email sent from your domain.</span></span>

<span data-ttu-id="fec1f-p115">メールを代理で送信するサード パーティの送信者が存在しているときに、そのサード パーティが送信するメールの 5321.MailFrom アドレスと 5322.From アドレスが一致していないと、そのメールに対する DMARC は失敗します。これを回避するには、そのサード パーティの送信者について、具体的にドメインの DKIM をセットアップする必要があります。これにより、このサード パーティのサービスからのメールを Microsoft 365 で認証できるようになります。ただし、そのようにすると、サード パーティが送信したメールを本人が送信したメールであるかのように検証することを他者 (Yahoo、Gmail、Comcast など) にも許可するようになります。これには、顧客がどこにメールボックスを配置していてもドメインとの信頼を構築できるようになるという利点があります。それと同時に、メッセージはドメインの認証チェックをパスしているため、Microsoft 365 は偽装を理由にメッセージをスパムとしてマークしなくなります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p115">If you have third-party senders that send mail on your behalf and the mail they send has mismatched 5321.MailFrom and 5322.From addresses, DMARC will fail for that email. To avoid this, you need to set up DKIM for your domain specifically with that third-party sender. This allows Microsoft 365 to authenticate email from this 3rd-party service. However, it also allows others, for example, Yahoo, Gmail, and Comcast, to verify email sent to them by the third-party as if it was email sent by you. This is beneficial because it allows your customers to build trust with your domain no matter where their mailbox is located, and at the same time Microsoft 365 won't mark a message as spam due to spoofing because it passes authentication checks for your domain.</span></span>

<span data-ttu-id="fec1f-178">サード パーティの送信者がドメインを偽装できるように DKIM をセットアップする方法を含め、ドメインの DKIM をセットアップする手順については、「[DKIM を使用して、カスタム ドメインから送信される送信電子メールを検証する](use-dkim-to-validate-outbound-email.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fec1f-178">For instructions on setting up DKIM for your domain, including how to set up DKIM for third-party senders so they can spoof your domain, see [Use DKIM to validate outbound email sent from your custom domain](use-dkim-to-validate-outbound-email.md).</span></span>

### <a name="step-4-form-the-dmarc-txt-record-for-your-domain"></a><span data-ttu-id="fec1f-179">手順 4: ドメイン用の DMARC TXT レコードを作成する</span><span class="sxs-lookup"><span data-stu-id="fec1f-179">Step 4: Form the DMARC TXT record for your domain</span></span>

<span data-ttu-id="fec1f-p116">ここでは、Microsoft 365 で最もよく使用される構文オプションを示します。ただし、ここに記載されていない別の構文のオプションもあります。ドメイン用の DMARC TXT レコードは、次に示す形式で作成します。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p116">Although there are other syntax options that are not mentioned here, these are the most commonly used options for Microsoft 365. Form the DMARC TXT record for your domain in the format:</span></span>

```console
_dmarc.domain  TTL  IN  TXT  "v=DMARC1; p=policy; pct=100"
```

<span data-ttu-id="fec1f-182">各部分の意味は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fec1f-182">where:</span></span>

- <span data-ttu-id="fec1f-183">*domain* は、保護対象にするドメインです。</span><span class="sxs-lookup"><span data-stu-id="fec1f-183">*domain* is the domain you want to protect.</span></span> <span data-ttu-id="fec1f-184">既定では、このレコードは、ドメインとすべてのサブドメインからのメールを保護します。</span><span class="sxs-lookup"><span data-stu-id="fec1f-184">By default, the record protects mail from the domain and all subdomains.</span></span> <span data-ttu-id="fec1f-185">たとえば、\_dmarc.contoso.com を指定すると、DMARC は、このドメインとすべてのサブドメイン (housewares.contoso.com や plumbing.contoso.com など) からのメールを保護します。</span><span class="sxs-lookup"><span data-stu-id="fec1f-185">For example, if you specify \_dmarc.contoso.com, then DMARC protects mail from the domain and all subdomains, such as housewares.contoso.com or plumbing.contoso.com.</span></span>

- <span data-ttu-id="fec1f-p118">*TTL* は、常に 1 時間に相当する必要があります。TTL に使用される単位は、ドメインのレジストラーに応じて hours (1 時間)、minutes (60 分)、または seconds (3,600 秒) のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p118">*TTL* should always be the equivalent of one hour. The unit used for TTL, either hours (1 hour), minutes (60 minutes), or seconds (3600 seconds), will vary depending on the registrar for your domain.</span></span>

- <span data-ttu-id="fec1f-188">*pct=100* は、このルールがメールの 100% に使用される必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="fec1f-188">*pct=100* indicates that this rule should be used for 100% of email.</span></span>

- <span data-ttu-id="fec1f-p119">*policy* では、DMARC に失敗した場合に受信側サーバーが従う必要のあるポリシーを指定します。ポリシーは、なし (none)、検疫 (quarantine)、または拒否 (reject) に設定できます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p119">*policy* specifies what policy you want the receiving server to follow if DMARC fails. You can set the policy to none, quarantine, or reject.</span></span>

<span data-ttu-id="fec1f-191">どのオプションを使用するかについては、「[Microsoft 365 で DMARC を実装する際のベスト プラクティス](#best-practices-for-implementing-dmarc-in-microsoft-365)」の概念をよく理解してください。</span><span class="sxs-lookup"><span data-stu-id="fec1f-191">For information about which options to use, become familiar with the concepts in [Best practices for implementing DMARC in Microsoft 365](#best-practices-for-implementing-dmarc-in-microsoft-365).</span></span>

<span data-ttu-id="fec1f-192">例:</span><span class="sxs-lookup"><span data-stu-id="fec1f-192">Examples:</span></span>

- <span data-ttu-id="fec1f-193">ポリシーをなし (none) に設定する</span><span class="sxs-lookup"><span data-stu-id="fec1f-193">Policy set to none</span></span>

    ```console
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=none"
    ```

- <span data-ttu-id="fec1f-194">ポリシーを検疫 (quarantine) に設定する</span><span class="sxs-lookup"><span data-stu-id="fec1f-194">Policy set to quarantine</span></span>

    ```console
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=quarantine"
    ```

- <span data-ttu-id="fec1f-195">ポリシーを拒否 (reject) に設定する</span><span class="sxs-lookup"><span data-stu-id="fec1f-195">Policy set to reject</span></span>

    ```console
    _dmarc.contoso.com  3600 IN  TXT  "v=DMARC1; p=reject"
    ```

<span data-ttu-id="fec1f-p120">レコードの作成後には、ドメイン レジストラーでレコードを更新する必要があります。DMARC TXT レコードを Microsoft 365 の DNS レコードに追加する手順の詳細については、「[DNS レコードを管理するときに Microsoft 365 の DNS レコードを作成する](https://docs.microsoft.com/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p120">Once you have formed your record, you need to update the record at your domain registrar. For instructions on adding the DMARC TXT record to your DNS records for Microsoft 365, see [Create DNS records for Microsoft 365 when you manage your DNS records](https://docs.microsoft.com/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider).</span></span>

## <a name="best-practices-for-implementing-dmarc-in-microsoft-365"></a><span data-ttu-id="fec1f-198">Microsoft 365 で DMARC を実装する際のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="fec1f-198">Best practices for implementing DMARC in Microsoft 365</span></span>

<span data-ttu-id="fec1f-p121">DMARC は、メール フローの他の部分に影響を与えないように段階的に実装できます。ここに示す手順に従ったロール アウト計画を作成して実施してください。ここに示す各手順は、まずサブドメインに実行します。その後で、その他の各サブドメインに対して実行し、最後に組織のトップレベル ドメインに実行してから、次の手順に進みます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p121">You can implement DMARC gradually without impacting the rest of your mail flow. Create and implement a roll out plan that follows these steps. Do each of these steps first with a sub-domain, then other sub-domains, and finally with the top-level domain in your organization before moving on to the next step.</span></span>

1. <span data-ttu-id="fec1f-202">DMARC の実装による影響を監視する</span><span class="sxs-lookup"><span data-stu-id="fec1f-202">Monitor the impact of implementing DMARC</span></span>

    <span data-ttu-id="fec1f-p122">まず、サブドメインまたはドメインに単純な監視モード レコードを使用することから始めます。このレコードでは、そのドメインを使用して確認するメッセージについての統計を送信するように DMARC レシーバーに要求します。監視モード レコードとは、ポリシーをなし (p=none) に設定したDMARC TXT レコードのことです。多くの企業は、p=none の DMARC TXT レコードを発行しています。それより制限の厳しいポリシーを発行することで、どれだけのメールが失われるかについて、明確にはわからないためです。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p122">Start with a simple monitoring-mode record for a sub-domain or domain that requests that DMARC receivers send you statistics about messages that they see using that domain. A monitoring-mode record is a DMARC TXT record that has its policy set to none (p=none). Many companies publish a DMARC TXT record with p=none because they are unsure about how much email they may lose by publishing a more restrictive DMARC policy.</span></span>

    <span data-ttu-id="fec1f-p123">これは、メッセージング インフラストラクチャに SPF や DKIM を実装する前でも実行できます。ただし、SPF と DKIM を実装して併用するまでは、DMARC を使用した効果的なメールの検疫や拒否はできません。SPF と DKIM を導入すると、DMARC によって生成されるレポートには、それらのチェックをパスしたメッセージとパスしなかったメッセージの発信元と数が示されます。それらのチェックの適用対象になる (または適用対象にならない) 正当なトラフィックの量を簡単に確認できます。また、あらゆる問題のトラブルシューティングも簡単になります。さらに、どれだけの偽装メッセージが送信されているかや、偽装メッセージの送信元についても、次第にわかるようになります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p123">You can do this even before you've implemented SPF or DKIM in your messaging infrastructure. However, you won't be able to effectively quarantine or reject mail by using DMARC until you also implement SPF and DKIM. As you introduce SPF and DKIM, the reports generated through DMARC will provide the numbers and sources of messages that pass these checks, and those that don't. You can easily see how much of your legitimate traffic is or isn't covered by them, and troubleshoot any problems. You'll also begin to see how many fraudulent messages are being sent, and from where.</span></span>

2. <span data-ttu-id="fec1f-211">DMARC に失敗したメールの検疫を外部のメール システムに要求する</span><span class="sxs-lookup"><span data-stu-id="fec1f-211">Request that external mail systems quarantine mail that fails DMARC</span></span>

    <span data-ttu-id="fec1f-p124">すべて、または大部分の正当なトラフィックが SPF と DKIM で保護されるという確信が持てるようになり、DMARC の実装による影響を理解したら、検疫ポリシーを実装してください。検疫ポリシーとは、ポリシーを検疫 (p=quarantine) に設定した DMARC TXT レコードのことです。このようにすることで、DMARC レシーバーに対して、DMARC に失敗したドメインからのメッセージを顧客の受信トレイではなく、ローカルのスパム フォルダーと同等のフォルダーに入れるように指示します。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p124">When you believe that all or most of your legitimate traffic is protected by SPF and DKIM, and you understand the impact of implementing DMARC, you can implement a quarantine policy. A quarantine policy is a DMARC TXT record that has its policy set to quarantine (p=quarantine). By doing this, you are asking DMARC receivers to put messages from your domain that fail DMARC into the local equivalent of a spam folder instead of your customers' inboxes.</span></span>

3. <span data-ttu-id="fec1f-215">DMARC に失敗したメッセージを受け取らないように外部システムに要求する</span><span class="sxs-lookup"><span data-stu-id="fec1f-215">Request that external mail systems not accept messages that fail DMARC</span></span>

    <span data-ttu-id="fec1f-p125">最後の手順は、拒否ポリシーの実装です。拒否ポリシーとは、ポリシーを拒否 (p=reject) に設定した DMARC TXT レコードのことです。これにより、DMARC レシーバーに対して、DMARC チェックに失敗したメッセージを受け取らないように指示します。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p125">The final step is implementing a reject policy. A reject policy is a DMARC TXT record that has its policy set to reject (p=reject). When you do this, you're asking DMARC receivers not to accept messages that fail the DMARC checks.</span></span>

4. <span data-ttu-id="fec1f-219">サブドメイン用に DMARC を設定する方法</span><span class="sxs-lookup"><span data-stu-id="fec1f-219">How to setup DMARC for subdomain?</span></span>

<span data-ttu-id="fec1f-220">DMARC は、ポリシーを DNS の TXT レコードとして公開することで実装され、階層的です (たとえば、contoso.com に公開されたポリシーは、サブドメインに別のポリシーが明示的に定義されていない限り、sub.domain.contonos.com に適用されます)。</span><span class="sxs-lookup"><span data-stu-id="fec1f-220">DMARC is implemented by publishing a policy as a TXT record in DNS and is hierarchical (e.g. a policy published for contoso.com will apply to sub.domain.contonos.com unless a different policy is explicitly defined for the subdomain).</span></span> <span data-ttu-id="fec1f-221">これは、より広い範囲をカバーするために、より少ない数の高レベル DMARC レコードを指定できる場合があるため、便利です。</span><span class="sxs-lookup"><span data-stu-id="fec1f-221">This is useful as organizations may be able to specify a smaller number of high level DMARC records for wider coverage.</span></span> <span data-ttu-id="fec1f-222">サブドメインがトップ レベル ドメインの DMARC レコードを継承しないようにするには、明示的なサブドメイン DMARC レコードを構成するように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-222">Care should be taken to configure explicit subdomain DMARC records where you do not want the subdomains to inherit the top level domain's DMARC record.</span></span>

<span data-ttu-id="fec1f-223">また、`sp=reject` 値を追加することにより、サブドメインがメールを送信してはならないときに DMARC にワイルドカード タイプのポリシーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-223">Also, you can add a wildcard-type policy for DMARC when subdomains shouldn't be sending email, by adding the `sp=reject` value.</span></span> <span data-ttu-id="fec1f-224">例:</span><span class="sxs-lookup"><span data-stu-id="fec1f-224">For example:</span></span>

```console
_dmarc.contoso.com. TXT "v=DMARC1; p=reject; sp=reject; ruf=mailto:authfail@contoso.com; rua=mailto:aggrep@contoso.com"
```

## <a name="how-microsoft-365-handles-outbound-email-that-fails-dmarc"></a><span data-ttu-id="fec1f-225">Microsoft 365 が DMARC に失敗した送信メールを処理する方法</span><span class="sxs-lookup"><span data-stu-id="fec1f-225">How Microsoft 365 handles outbound email that fails DMARC</span></span>

<span data-ttu-id="fec1f-226">メッセージが Microsoft 365 から送信され、DMARC に失敗し、ポリシーを p=quarantine または p=reject に設定していると、メッセージは「[送信メッセージにおける危険度の高い配信プール](high-risk-delivery-pool-for-outbound-messages.md)」によってルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-226">If a message is outbound from Microsoft 365 and fails DMARC, and you have set the policy to p=quarantine or p=reject, the message is routed through the [High-risk delivery pool for outbound messages](high-risk-delivery-pool-for-outbound-messages.md).</span></span> <span data-ttu-id="fec1f-227">送信メールの上書きはありません。</span><span class="sxs-lookup"><span data-stu-id="fec1f-227">There is no override for outbound email.</span></span>

<span data-ttu-id="fec1f-p129">DMARC 拒否ポリシー (p=reject) を発行すると、どの顧客も Microsoft 365 ではドメインを偽装できなくなります。メッセージは、サービスを通じたメッセージ送信の中継時に、ドメインの SPF または DKIM をパスできないためです。ただし、DMARC 拒否ポリシーを発行していても、すべてのメールが Microsoft 365 で認証されている場合、前述の説明どおりに受信メールの一部はスパムとしてのマークが付けられます。それ以外のメールは、SPF を発行していない場合に、サービスを通じて送信を中継するようにしていると拒否されます。 これは、DMARC TXT レコードの作成時に、ドメインの代理としてメールを送信するサーバーの一部の IP アドレスとアプリを含め忘れている場合などに発生します。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p129">If you publish a DMARC reject policy (p=reject), no other customer in Microsoft 365 can spoof your domain because messages will not be able to pass SPF or DKIM for your domain when relaying a message outbound through the service. However, if you do publish a DMARC reject policy but don't have all of your email authenticated through Microsoft 365, some of it may be marked as spam for inbound email (as described above), or it will be rejected if you do not publish SPF and try to relay it outbound through the service. This happens, for example, if you forget to include some of the IP addresses for servers and apps that send mail on behalf of your domain when you form your DMARC TXT record.</span></span>

## <a name="how-microsoft-365-handles-inbound-email-that-fails-dmarc"></a><span data-ttu-id="fec1f-231">Microsoft 365 が DMARC に失敗した受信メールを処理する方法</span><span class="sxs-lookup"><span data-stu-id="fec1f-231">How Microsoft 365 handles inbound email that fails DMARC</span></span>

<span data-ttu-id="fec1f-232">送信側サーバーの DMARC ポリシーが `p=reject` の場合、[Exchange Online Protection](exchange-online-protection-overview.md) (EOP) はメッセージを拒否するのではなく、スプーフィングとしてマークを付けます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-232">If the DMARC policy of the sending server is `p=reject`, [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) marks the message as spoof instead of rejecting it.</span></span> <span data-ttu-id="fec1f-233">つまり、受信メールの場合、Microsoft 365 は `p=reject` と `p=quarantine` を同様に扱うということです。</span><span class="sxs-lookup"><span data-stu-id="fec1f-233">In other words, for inbound email, Microsoft 365 treats `p=reject` and `p=quarantine` the same way.</span></span> <span data-ttu-id="fec1f-234">管理者は、[フィッシング詐欺対策ポリシー](set-up-anti-phishing-policies.md)内のスプーフィングとして分類されたメッセージに対するアクションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-234">Admins can define the action to take on messages classified as spoof within the [anti-phishing policy](set-up-anti-phishing-policies.md).</span></span>

<span data-ttu-id="fec1f-235">このように Microsoft 365 が構成されている理由は、一部の正当なメールが DMARC に失敗することがあるためです。</span><span class="sxs-lookup"><span data-stu-id="fec1f-235">Microsoft 365 is configured like this because some legitimate email may fail DMARC.</span></span> <span data-ttu-id="fec1f-236">たとえば、メッセージがメーリング リストに送信されてから、リストのすべての参加者にメッセージが中継される場合、DMARC に失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-236">For example, a message might fail DMARC if it is sent to a mailing list that then relays the message to all list participants.</span></span> <span data-ttu-id="fec1f-237">こうしたメッセージを Microsoft 365 が拒否すると、受信者は正当なメールを失うことになり、そのメールを取得する手段がなくなります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-237">If Microsoft 365 rejected these messages, people could lose legitimate email and have no way to retrieve it.</span></span> <span data-ttu-id="fec1f-238">その代わりに、このようなメッセージは DMARC に失敗するようにしておき、スパムのマークを付けて拒否しないようにします。</span><span class="sxs-lookup"><span data-stu-id="fec1f-238">Instead, these messages will still fail DMARC but they will be marked as spam and not rejected.</span></span> <span data-ttu-id="fec1f-239">必要であれば、ユーザーは自分の受信トレイから、次の方法でメッセージを取得できます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-239">If desired, users can still get these messages in their inbox through these methods:</span></span>

- <span data-ttu-id="fec1f-240">ユーザーが、自分のメール クライアントを使用して、個別に安全な送信者を追加します。</span><span class="sxs-lookup"><span data-stu-id="fec1f-240">Users add safe senders individually by using their email client.</span></span>

- <span data-ttu-id="fec1f-241">管理者は、[スプーフィング インテリジェンス](learn-about-spoof-intelligence.md) レポートを更新して、スプーフィングを許可できます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-241">Administrators can update the [Spoof Intelligence](learn-about-spoof-intelligence.md) reporting to allow the spoof.</span></span>

- <span data-ttu-id="fec1f-242">管理者が、該当する送信者のメッセージを許可するすべてのユーザーに向けて Exchange メール フロー ルール (トランスポート ルールとも呼ばれる) を作成します。</span><span class="sxs-lookup"><span data-stu-id="fec1f-242">Administrators create an Exchange mail flow rule (also known as a transport rule) for all users that allows messages for those particular senders.</span></span>

<span data-ttu-id="fec1f-243">詳細については、「[信頼できる差出人リストの作成](create-safe-sender-lists-in-office-365.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fec1f-243">For more information, see [Create safe sender lists](create-safe-sender-lists-in-office-365.md).</span></span>

## <a name="how-microsoft-365-utilizes-authenticated-received-chain-arc"></a><span data-ttu-id="fec1f-244">Microsoft 365 でオーセンティケーテッド レシーブド チェーン (ARC) を活用する方法</span><span class="sxs-lookup"><span data-stu-id="fec1f-244">How Microsoft 365 utilizes Authenticated Received Chain (ARC)</span></span>

<span data-ttu-id="fec1f-245">Microsoft 365 でホストされているすべてのメール ボックスでは、向上したメッセージの配信率と強化されたスプーフィング対策保護と共に、ARC の利点が得られます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-245">All hosted mailboxes in Microsoft 365 will now gain the benefit of ARC with improved deliverability of messages and enhanced anti-spoofing protection.</span></span> <span data-ttu-id="fec1f-246">ARC では、元のサーバーから受信者のメールボックスへと電子メールがルーティングされると、すべての関与する仲介役、つまりホップからの電子メール認証の結果が保持されます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-246">ARC preserves the email authentication results from all participating intermediaries, or hops, when an email is routed from the originating server to the recipient mailbox.</span></span> <span data-ttu-id="fec1f-247">ARC 以前、転送ルールまたは自動署名などの電子メール ルーティングの仲介役によって実行される変更は、受信者のメールボックスで電子メールが受信される時間によって DMARC の失敗を引き起こす場合があります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-247">Before ARC, modifications performed by intermediaries in email routing, like forwarding rules or automatic signatures, could cause DMARC failures by the time the email reached the recipient mailbox.</span></span> <span data-ttu-id="fec1f-248">ARC を使用すると、認証の結果の暗号化保存により、Microsoft 365 では電子メールの送信者の真正性を検証することができます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-248">With ARC, the cryptographic preservation of the authentication results allows Microsoft 365 to verify the authenticity of an email's sender.</span></span>

<span data-ttu-id="fec1f-249">Microsoft が ARC Sealer の場合、現在、Microsoft 365 では ARC を使用して認証の結果を検証します。しかし、将来的にはサードパーティの ARC Sealer のサポートを追加する予定です。</span><span class="sxs-lookup"><span data-stu-id="fec1f-249">Microsoft 365 currently utilizes ARC to verify authentication results when Microsoft is the ARC Sealer, but plan to add support for third party ARC sealers in the future.</span></span>

## <a name="troubleshooting-your-dmarc-implementation"></a><span data-ttu-id="fec1f-250">DMARC 実装のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="fec1f-250">Troubleshooting your DMARC implementation</span></span>

<span data-ttu-id="fec1f-251">ドメインの MX レコードを構成したときに、最初のエントリを EOP 以外にすると、DMARC の失敗はドメインに強制されなくなります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-251">If you have configured your domain's MX records where EOP is not the first entry, DMARC failures will not be enforced for your domain.</span></span>

<span data-ttu-id="fec1f-252">お客様の場合でも、ドメインのプライマリ MX レコードが EOP を指していないと、DMARC による利点は得られなくなります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-252">If you're a customer, and your domain's primary MX record does not point to EOP, you will not get the benefits of DMARC.</span></span> <span data-ttu-id="fec1f-253">たとえば、MX レコードがオンプレミスのメール サーバーを指していて、コネクタを使用することで EOP にメールをルーティングしていると、DMARC は機能しなくなります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-253">For example, DMARC won't work if you point the MX record to your on-premises mail server and then route email to EOP by using a connector.</span></span> <span data-ttu-id="fec1f-254">このシナリオでは、受信側ドメインは認証済みドメインのいずれかになりますが、EOP はプライマリ MX ではありません。</span><span class="sxs-lookup"><span data-stu-id="fec1f-254">In this scenario, the receiving domain is one of your Accepted-Domains but EOP is not the primary MX.</span></span> <span data-ttu-id="fec1f-255">たとえば、contoso.com がそれ自体の MX をポイントしていて、セカンダリ MX レコードとして EOP を使用しているとすると、contoso.com の MX レコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-255">For example, suppose contoso.com points its MX at itself and uses EOP as a secondary MX record, contoso.com's MX record looks like the following:</span></span>

```console
contoso.com     3600   IN  MX  0  mail.contoso.com
contoso.com     3600   IN  MX  10 contoso-com.mail.protection.outlook.com
```

<span data-ttu-id="fec1f-256">すべて、またはほとんどのメールは、最初にプライマリ MX である mail.contoso.com にルーティングされてから、EOP にルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-256">All, or most, email will first be routed to mail.contoso.com since it's the primary MX, and then mail will get routed to EOP.</span></span> <span data-ttu-id="fec1f-257">場合によっては、MX レコードとして EOP をリストすることさえなく、単にメールをルーティングするようにコネクタを接続していることもあります。</span><span class="sxs-lookup"><span data-stu-id="fec1f-257">In some cases, you might not even list EOP as an MX record at all and simply hook up connectors to route your email.</span></span> <span data-ttu-id="fec1f-258">EOP は、DMARC 検証を行うための最初のエントリである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fec1f-258">EOP does not have to be the first entry for DMARC validation to be done.</span></span> <span data-ttu-id="fec1f-259">検証は、オンプレミスまたは O365 以外のすべてのサーバーが DMARC チェックを行うわけではないため、検証だけを行います。</span><span class="sxs-lookup"><span data-stu-id="fec1f-259">It just ensures the validation, as we cannot be certain that all on-premise/non-O365 servers will do DMARC checks.</span></span>  <span data-ttu-id="fec1f-260">DMARC TXT レコードを設定するときに顧客のドメイン (サーバーではなく) に対して DMARC を強制できますが、実際に強制するのは受信サーバーだけです。</span><span class="sxs-lookup"><span data-stu-id="fec1f-260">DMARC is eligible to be enforced for a customer's domain (not server) when you set up the DMARC TXT record, but it is up to the receiving server to actually do the enforcement.</span></span>  <span data-ttu-id="fec1f-261">EOP を受信サーバーとして設定すると、EOP は DMARC 強制を行います。</span><span class="sxs-lookup"><span data-stu-id="fec1f-261">If you set up EOP as the receiving server, then EOP does the DMARC enforcement.</span></span>

![DMARC のトラブルシューティング グラフィック、Daniel Mande 提供](../../media/Tp_DMARCTroublehoot.png)

## <a name="for-more-information"></a><span data-ttu-id="fec1f-263">詳細情報</span><span class="sxs-lookup"><span data-stu-id="fec1f-263">For more information</span></span>

<span data-ttu-id="fec1f-p135">DMARC の詳細情報が必要ですか。以下のリソースが役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="fec1f-p135">Want more information about DMARC? These resources can help.</span></span>

- <span data-ttu-id="fec1f-266">[スパム対策メッセージ ヘッダー](anti-spam-message-headers.md)には、Microsoft 365 が DMARC チェックに使用する構文とヘッダー フィールドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fec1f-266">[Anti-spam message headers](anti-spam-message-headers.md) includes the syntax and header fields used by Microsoft 365 for DMARC checks.</span></span>

- <span data-ttu-id="fec1f-267">M<sup>3</sup>AAWG (Messaging, Malware, Mobile Anti-Abuse Working Group) の「[DMARC TRAINING SERIES](https://www.m3aawg.org/activities/training/dmarc-training-series)」。</span><span class="sxs-lookup"><span data-stu-id="fec1f-267">Take the [DMARC Training Series](https://www.m3aawg.org/activities/training/dmarc-training-series) from M<sup>3</sup>AAWG (Messaging, Malware, Mobile Anti-Abuse Working Group).</span></span>

- <span data-ttu-id="fec1f-268">[dmarcian](https://space.dmarcian.com/deployment/) のチェックリストを使用する。</span><span class="sxs-lookup"><span data-stu-id="fec1f-268">Use the checklist at [dmarcian](https://space.dmarcian.com/deployment/).</span></span>

- <span data-ttu-id="fec1f-269">[DMARC.org](https://dmarc.org) のソースに直接アクセスする。</span><span class="sxs-lookup"><span data-stu-id="fec1f-269">Go directly to the source at [DMARC.org](https://dmarc.org).</span></span>

## <a name="see-also"></a><span data-ttu-id="fec1f-270">関連項目</span><span class="sxs-lookup"><span data-stu-id="fec1f-270">See also</span></span>

[<span data-ttu-id="fec1f-271">Microsoft 365 において Sender Policy Framework (SPF) を使用して、スプーフィングを防止する方法</span><span class="sxs-lookup"><span data-stu-id="fec1f-271">How Microsoft 365 uses Sender Policy Framework (SPF) to prevent spoofing</span></span>](how-office-365-uses-spf-to-prevent-spoofing.md)

[<span data-ttu-id="fec1f-272">Microsoft 365 で SPF を設定して、スプーフィングを防止する</span><span class="sxs-lookup"><span data-stu-id="fec1f-272">Set up SPF in Microsoft 365 to help prevent spoofing</span></span>](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

[<span data-ttu-id="fec1f-273">DKIM を使用して、Microsoft 365 のカスタム ドメインから送信される送信電子メールを検証する</span><span class="sxs-lookup"><span data-stu-id="fec1f-273">Use DKIM to validate outbound email sent from your custom domain in Microsoft 365</span></span>](use-dkim-to-validate-outbound-email.md)
