---
title: Exchange Online での暗号化の S/MIME - Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 887c710b-0ec6-4ff0-8065-5f05f74afef3
description: 管理者は、Exchange Online で S/MIME (Secure/Multipurpose Internet Mail Extensions) を使用して電子メールを暗号化し、デジタル署名する方法について学習できます。
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d189bf7f52dd6f9fb11dc360c17d5fe15729c9fa
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51061915"
---
# <a name="smime-for-message-signing-and-encryption-in-exchange-online"></a><span data-ttu-id="91f6c-103">Exchange Online でのメッセージ署名と暗号化の S/MIME</span><span class="sxs-lookup"><span data-stu-id="91f6c-103">S/MIME for message signing and encryption in Exchange Online</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


<span data-ttu-id="91f6c-104">S/MIME (Secure/Multipurpose Internet Mail Extensions) は、デジタル署名されたメッセージと暗号化されたメッセージを送信するための広く受け入れられているメソッド (より正確にはプロトコル) です。</span><span class="sxs-lookup"><span data-stu-id="91f6c-104">S/MIME (Secure/Multipurpose Internet Mail Extensions) is a widely accepted method (or more precisely, a protocol) for sending digitally signed and encrypted messages.</span></span> <span data-ttu-id="91f6c-105">S/MIME では電子メールを暗号化し、デジタル署名を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="91f6c-105">S/MIME allows you to encrypt emails and digitally sign them.</span></span> <span data-ttu-id="91f6c-106">電子メール メッセージで S/MIME を使用すると、そのメッセージを受信する人は、受信トレイにあるものが送信者によって作成されたメッセージそのものであることがわかります。</span><span class="sxs-lookup"><span data-stu-id="91f6c-106">When you use S/MIME with an email message, it helps the people who receive that message to be certain that what they see in their inbox is the exact message that started with the sender.</span></span> <span data-ttu-id="91f6c-107">また、メッセージを受信する人は、そのメッセージが確かに特定の送信者から送信されたものであり、その送信者になりすました別の誰かからのものでないこともわかります。</span><span class="sxs-lookup"><span data-stu-id="91f6c-107">It will also help people who receive messages to be certain that the message came from the specific sender and not from someone pretending to be the sender.</span></span> <span data-ttu-id="91f6c-108">このために、S/MIME には認証、メッセージの整合性、発信元の否認防止 (デジタル署名を使用) などの暗号化セキュリティ サービスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="91f6c-108">To do this, S/MIME provides for cryptographic security services such as authentication, message integrity, and non-repudiation of origin (using digital signatures).</span></span> <span data-ttu-id="91f6c-109">また、これは電子メッセージングのプライバシーとデータ セキュリティ (暗号化を使用) の強化にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="91f6c-109">It also helps enhance privacy and data security (using encryption) for electronic messaging.</span></span> <span data-ttu-id="91f6c-110">電子メール関連での S/MIME の歴史とアーキテクチャに関する詳細な背景情報については、「[S/MIME について](/previous-versions/tn-archive/aa995740(v=exchg.65))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91f6c-110">For a more complete background about the history and architecture of S/MIME in the context of email, see [Understanding S/MIME](/previous-versions/tn-archive/aa995740(v=exchg.65)).</span></span>

<span data-ttu-id="91f6c-111">Exchange Online 管理者は、組織内のメールボックスに対して S/MIME ベースのセキュリティを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="91f6c-111">As an Exchange Online admin, you can enable S/MIME-based security for the mailboxes in your organization.</span></span> <span data-ttu-id="91f6c-112">S/MIME をセットアップするには、Exchange Online PowerShell と共にここにリンクされているトピックのガイダンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="91f6c-112">Use the guidance in the topics linked here along with Exchange Online PowerShell to set up S/MIME.</span></span> <span data-ttu-id="91f6c-113">サポートされている電子メール クライアントで S/MIME を使用するには、組織内のユーザーが署名と暗号化の目的で発行された証明書と、オンプレミスの Active Directory ドメイン サービス (AD DS) に発行されたデータを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="91f6c-113">To use S/MIME in supported email clients, the users in your organization must have certificates issued for signing and encryption purposes and data published to your on-premises Active Directory Domain Service (AD DS).</span></span> <span data-ttu-id="91f6c-114">ユーザー AD DS は、インターネット上のリモート施設やクラウドベースのサービスではなく、ユーザーが制御する物理的な場所にあるコンピューター上に置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="91f6c-114">Your AD DS must be located on computers at a physical location that you control and not at a remote facility or cloud-based service somewhere on the internet.</span></span> <span data-ttu-id="91f6c-115">DS の詳細についてはAD Active Directory [ドメイン サービスの概要を参照してください](/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview)。</span><span class="sxs-lookup"><span data-stu-id="91f6c-115">For more information about AD DS, see [Active Directory Domain Services Overview](/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview).</span></span>

## <a name="supported-scenarios-and-technical-considerations"></a><span data-ttu-id="91f6c-116">サポートされるシナリオと技術的な考慮事項</span><span class="sxs-lookup"><span data-stu-id="91f6c-116">Supported scenarios and technical considerations</span></span>

<span data-ttu-id="91f6c-117">次の任意のエンドポイントで機能するように S/MIME をセットアップできます。</span><span class="sxs-lookup"><span data-stu-id="91f6c-117">You can set up S/MIME to work with any of the following end points:</span></span>

- <span data-ttu-id="91f6c-118">Outlook 2010 以降</span><span class="sxs-lookup"><span data-stu-id="91f6c-118">Outlook 2010 or later</span></span>
- <span data-ttu-id="91f6c-119">Web 上の Outlook (旧称 Outlook Web App)</span><span class="sxs-lookup"><span data-stu-id="91f6c-119">Outlook on the web (formerly known as Outlook Web App)</span></span>
- <span data-ttu-id="91f6c-120">Exchange ActiveSync (EAS)</span><span class="sxs-lookup"><span data-stu-id="91f6c-120">Exchange ActiveSync (EAS)</span></span>

<span data-ttu-id="91f6c-121">これらの各エンド ポイントで S/MIME を設定する手順は少し異なります。</span><span class="sxs-lookup"><span data-stu-id="91f6c-121">The steps that you follow to set up S/MIME with each of these end points is slightly different.</span></span> <span data-ttu-id="91f6c-122">通常、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91f6c-122">Generally, you will need to do the following steps:</span></span>

1. <span data-ttu-id="91f6c-123">Windows ベースの証明機関 (CA) をインストールし、公開キー インフラストラクチャをセットアップして S/MIME 証明書を発行します。</span><span class="sxs-lookup"><span data-stu-id="91f6c-123">Install a Windows-based Certification Authority (CA) and set up a public key infrastructure to issue S/MIME certificates.</span></span> <span data-ttu-id="91f6c-124">サードパーティの証明書プロバイダーによって発行された証明書もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="91f6c-124">Certificates issued by third-party certificate providers are also supported.</span></span> <span data-ttu-id="91f6c-125">詳細については、「[Active Directory 証明書サービスの概要](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831740(v=ws.11))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91f6c-125">For details, see [Active Directory Certificate Services Overview](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831740(v=ws.11)).</span></span>

   <span data-ttu-id="91f6c-126">**注**:</span><span class="sxs-lookup"><span data-stu-id="91f6c-126">**Notes**:</span></span>

   - <span data-ttu-id="91f6c-127">サード パーティ CA によって発行された証明書は、すべてのクライアントとデバイスによって自動的に信頼されるという利点があります。</span><span class="sxs-lookup"><span data-stu-id="91f6c-127">Certificates issued by a third-party CA have the advantage of being automatically trusted by all clients and devices.</span></span> <span data-ttu-id="91f6c-128">内部のプライベート CA によって発行された証明書は、クライアントやデバイスによって自動的に信頼されるのではなく、すべてのデバイス (電話など) がプライベート証明書を信頼するように構成できる場合ではありません。</span><span class="sxs-lookup"><span data-stu-id="91f6c-128">Certificates that are issued by an internal, private CA aren't automatically trusted by clients and devices, and not all devices (for example, phones) can be configured to trust private certificates.</span></span>

   - <span data-ttu-id="91f6c-129">ルート証明書の代わりに中間証明書を使用して、ユーザーに証明書を発行する方法を検討してください。</span><span class="sxs-lookup"><span data-stu-id="91f6c-129">Consider using an intermediate certificate instead of the root certificate to issue certificates to users.</span></span> <span data-ttu-id="91f6c-130">そうすることで、証明書を取り消して再発行する必要がある場合、ルート証明書はそのまま残ります。</span><span class="sxs-lookup"><span data-stu-id="91f6c-130">That way, if you ever need to revoke and reissue certificates, the root certificate is still intact.</span></span>

2. <span data-ttu-id="91f6c-131">**UserSMIMECertificate** 属性または **UserCertificate** 属性AD DS アカウントにユーザー証明書を発行します。</span><span class="sxs-lookup"><span data-stu-id="91f6c-131">Publish the user certificate in an on-premises AD DS account in the **UserSMIMECertificate** and/or **UserCertificate** attributes.</span></span>

3. <span data-ttu-id="91f6c-132">Exchange Online 組織の場合は、適切なバージョンの Azure AD Connect を使用して、DS から Azure Active Directory にユーザー証明書をADします。</span><span class="sxs-lookup"><span data-stu-id="91f6c-132">For Exchange Online organizations, synchronize the user certificates from AD DS to Azure Active Directory by using an appropriate version of Azure AD Connect.</span></span> <span data-ttu-id="91f6c-133">次に、これらの証明書は Azure Active Directory から Exchange Online のディレクトリに同期され、受信者へのメッセージの暗号化に使用されます。</span><span class="sxs-lookup"><span data-stu-id="91f6c-133">These certificates will then get synchronized from Azure Active Directory to Exchange Online directory and will be used when encrypting a message to a recipient.</span></span>

4. <span data-ttu-id="91f6c-p108">S/MIME を検証するためには、仮想の証明書のコレクションを設定します。この情報は、電子メールの署名を検証する際に Web 上の Outlook により使用され、そのメールが信頼される証明書により署名されたことが確認されます。</span><span class="sxs-lookup"><span data-stu-id="91f6c-p108">Set up a virtual certificate collection in order to validate S/MIME. This information is used by Outlook on the web when validating the signature of an email and ensuring that it was signed by a trusted certificate.</span></span>

5. <span data-ttu-id="91f6c-136">S/MIME を使用する Outlook エンド ポイントまたは EAS エンド ポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="91f6c-136">Set up the Outlook or EAS end point to use S/MIME.</span></span>

> [!NOTE]
> <span data-ttu-id="91f6c-137">Mac、iOS、Android、その他の Windows 以外のデバイスでは、Outlook on the web に S/MIME コントロールをインストールできません。</span><span class="sxs-lookup"><span data-stu-id="91f6c-137">You can't install S/MIME control in Outlook on the web on Mac, iOS, Android, or other non-Windows devices.</span></span> <span data-ttu-id="91f6c-138">詳細については [、「Outlook on the web で S/MIME を使用してメッセージを暗号化する」を参照してください](https://support.microsoft.com/office/878c79fc-7088-4b39-966f-14512658f480)。</span><span class="sxs-lookup"><span data-stu-id="91f6c-138">For more information, see [Encrypt messages by using S/MIME in Outlook on the web](https://support.microsoft.com/office/878c79fc-7088-4b39-966f-14512658f480).</span></span>

## <a name="set-up-smime-with-outlook-on-the-web"></a><span data-ttu-id="91f6c-139">Web 上の Outlook での S/MIME のセットアップ</span><span class="sxs-lookup"><span data-stu-id="91f6c-139">Set up S/MIME with Outlook on the web</span></span>

<span data-ttu-id="91f6c-140">Outlook on the web での Exchange Online 用 S/MIME のセットアップには、次の重要な手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="91f6c-140">Setting up S/MIME for Exchange Online with Outlook on the web involves the following key steps:</span></span>

1. [<span data-ttu-id="91f6c-141">Outlook on the web の S/MIME 設定を構成する</span><span class="sxs-lookup"><span data-stu-id="91f6c-141">Configure S/MIME settings for Outlook on the web</span></span>](configure-s-mime-settings-for-outlook-web-app.md)
2. [<span data-ttu-id="91f6c-142">S/MIME を検証するための仮想証明書コレクションを設定する</span><span class="sxs-lookup"><span data-stu-id="91f6c-142">Set up virtual certificate collection to validate S/MIME</span></span>](set-up-virtual-certificate-collection-to-validate-s-mime.md)
3. [<span data-ttu-id="91f6c-143">S/MIME 用にユーザー証明書を Office 365 に同期させる</span><span class="sxs-lookup"><span data-stu-id="91f6c-143">Sync user certificates to Office 365 for S/MIME</span></span>](sync-user-certificates-to-office-365-for-s-mime.md)

## <a name="related-message-encryption-technologies"></a><span data-ttu-id="91f6c-144">関連するメッセージ暗号化テクノロジ</span><span class="sxs-lookup"><span data-stu-id="91f6c-144">Related message encryption technologies</span></span>

<span data-ttu-id="91f6c-145">メッセージ のセキュリティが重要になると、管理者はセキュリティで保護されたメッセージングの原則と概念を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91f6c-145">As message security becomes more important, admins need to understand the principles and concepts of secure messaging.</span></span> <span data-ttu-id="91f6c-146">この理解は、利用可能な保護関連テクノロジ (S/MIME を含む) の種類が増えているため、特に重要です。</span><span class="sxs-lookup"><span data-stu-id="91f6c-146">This understanding is especially important because of the growing variety of protection-related technologies (including S/MIME) that are available.</span></span> <span data-ttu-id="91f6c-147">S/MIME と電子メールのコンテキストでの動作の詳細については [、「S/MIME について」を参照してください](/previous-versions/tn-archive/aa995740(v=exchg.65))。</span><span class="sxs-lookup"><span data-stu-id="91f6c-147">To understand more about S/MIME and how it works in context of email, see [Understanding S/MIME](/previous-versions/tn-archive/aa995740(v=exchg.65)).</span></span> <span data-ttu-id="91f6c-148">さまざまな暗号化テクノロジが連携して、保管されているメッセージと転送中のメッセージの保護を提供します。</span><span class="sxs-lookup"><span data-stu-id="91f6c-148">A variety of encryption technologies work together to provide protection for messages at rest and in-transit.</span></span> <span data-ttu-id="91f6c-149">S/MIME は次のようなテクノロジと同時に機能しますが、それらに依存してはいません。</span><span class="sxs-lookup"><span data-stu-id="91f6c-149">S/MIME can work simultaneously with the following technologies but is not dependent on them:</span></span>

- <span data-ttu-id="91f6c-150">**トランスポート層セキュリティ (TLS)** は、盗聴防止に役立てるために電子メール サーバー間のトンネルまたはルートを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="91f6c-150">**Transport Layer Security (TLS)** encrypts the tunnel or the route between email servers in order to help prevent snooping and eavesdropping.</span></span>

- <span data-ttu-id="91f6c-151">**Secure Sockets Layer (SSL) は** 、電子メール クライアントと Microsoft 365 サーバー間の接続を暗号化します。</span><span class="sxs-lookup"><span data-stu-id="91f6c-151">**Secure Sockets Layer (SSL)** encrypts the connection between email clients and Microsoft 365 servers.</span></span>

- <span data-ttu-id="91f6c-152">**BitLocker** は、データ センター内のハード ドライブ上のデータを暗号化して、誰かが承認されていないアクセスを取得した場合、データを読み取る事ができない。</span><span class="sxs-lookup"><span data-stu-id="91f6c-152">**BitLocker** encrypts the data on a hard drive in a datacenter so that if someone gets unauthorized access, they can't read it.</span></span>

### <a name="smime-compared-with-office-365-message-encryption"></a><span data-ttu-id="91f6c-153">S/MIME と Office 365 のメッセージ暗号化との比較</span><span class="sxs-lookup"><span data-stu-id="91f6c-153">S/MIME compared with Office 365 Message Encryption</span></span>

<span data-ttu-id="91f6c-154">S/MIME には B2B (企業間取引) および B2C (企業-消費者間取引) の状況でよく使用される証明書および公開のインフラストラクチャが必要です。</span><span class="sxs-lookup"><span data-stu-id="91f6c-154">S/MIME requires a certificate and publishing infrastructure that is often used in business-to-business and business-to-consumer situations.</span></span> <span data-ttu-id="91f6c-155">ユーザーは、S/MIME で暗号化キーを制御し、送信する各メッセージにキーを使用するかどうかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="91f6c-155">The user controls the cryptographic keys in S/MIME and can choose whether to use them for each message they send.</span></span> <span data-ttu-id="91f6c-156">Outlook などの電子メール プログラムはデジタル署名と署名の検証を実行するために、信頼できるルート証明機関の場所を検索します。</span><span class="sxs-lookup"><span data-stu-id="91f6c-156">Email programs such as Outlook search a trusted root certificate authority location to perform digital signing and verification of the signature.</span></span> <span data-ttu-id="91f6c-157">Office 365 のメッセージの暗号化は、組織内外の任意の受信者に送信されるメールを暗号化するための、管理者が構成できる (個々のユーザーは構成できない) ポリシー ベースの暗号化サービスです。</span><span class="sxs-lookup"><span data-stu-id="91f6c-157">Office 365 Message Encryption is a policy-based encryption service that can be configured by an administrator, and not an individual user, to encrypt mail sent to anyone inside or outside of the organization.</span></span> <span data-ttu-id="91f6c-158">これは、Azure Rights Management (RMS) 上に構築され、公開キー インフラストラクチャに依存しないオンライン サービスです。</span><span class="sxs-lookup"><span data-stu-id="91f6c-158">It's an online service that's built on Azure Rights Management (RMS) and does not rely on a public key infrastructure.</span></span> <span data-ttu-id="91f6c-159">Office 365 Message Encryption には、組織のブランドでメールをカスタマイズする機能など、追加の機能も備えています。</span><span class="sxs-lookup"><span data-stu-id="91f6c-159">Office 365 Message Encryption also provides additional capabilities, such as the capability to customize the mail with organization's brand.</span></span> <span data-ttu-id="91f6c-160">365 メッセージ暗号化のOffice詳細については、「暗号化」 [を参照Officeしてください](../../compliance/encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="91f6c-160">For more information about Office 365 Message Encryption, see [Encryption in Office 365](../../compliance/encryption.md).</span></span>

## <a name="more-information"></a><span data-ttu-id="91f6c-161">詳細情報</span><span class="sxs-lookup"><span data-stu-id="91f6c-161">More information</span></span>

[<span data-ttu-id="91f6c-162">Outlook on the web</span><span class="sxs-lookup"><span data-stu-id="91f6c-162">Outlook on the web</span></span>](/exchange/exchange-admin-center)

<span data-ttu-id="91f6c-163">[Secure Mail (2000)](/previous-versions/windows/it-pro/windows-2000-server/cc962043(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="91f6c-163">[Secure Mail (2000)](/previous-versions/windows/it-pro/windows-2000-server/cc962043(v=technet.10))</span></span>