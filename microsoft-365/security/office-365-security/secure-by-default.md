---
title: Office 365 で既定でセキュリティ保護されている
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: Exchange Online Protection (EOP) の [既定でセキュリティ保護] の設定についての詳細情報
ms.openlocfilehash: 758d2169d80630a38c0b498e8c1848568e5ec941
ms.sourcegitcommit: 1beaf89d2faa32f11fe1613be2fa2b31c4bc4a91
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "49602043"
---
# <a name="secure-by-default-in-office-365"></a><span data-ttu-id="ffe1d-103">Office 365 で既定でセキュリティ保護されている</span><span class="sxs-lookup"><span data-stu-id="ffe1d-103">Secure by default in Office 365</span></span>

[!INCLUDE [Prerelease information](../includes/prerelease.md)]
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

<span data-ttu-id="ffe1d-104">[既定でセキュリティ保護] は、可能な限り最も安全な既定の設定を定義するために使用される用語です。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-104">"Secure by default" is a term used to define the default settings that are most secure as possible.</span></span>

<span data-ttu-id="ffe1d-105">ただし、セキュリティは生産性にバランスをとる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-105">However, security needs to be balanced with productivity.</span></span> <span data-ttu-id="ffe1d-106">これには、次のようなバランスを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-106">This can include balancing across:</span></span>

- <span data-ttu-id="ffe1d-107">**有用性**: 設定は、ユーザーの生産性を向上させることはできません。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-107">**Usability**: Settings should not get in the way of user productivity.</span></span>
- <span data-ttu-id="ffe1d-108">**リスク**: セキュリティが重要なアクティビティをブロックする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-108">**Risk**: Security might block important activities.</span></span>
- <span data-ttu-id="ffe1d-109">**従来の設定**: 新しい高度な設定が改善された場合でも、以前の製品や機能のいくつかの構成は、ビジネス上の理由から維持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-109">**Legacy settings**: Some configurations for older products and features might need to be maintained for business reasons, even if new, modern settings are improved.</span></span>

<span data-ttu-id="ffe1d-110">Exchange Online のメールボックスを使用する Microsoft 365 組織は、Exchange Online Protection (EOP) によって保護されています。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-110">Microsoft 365 organizations with mailboxes in Exchange Online are protected by Exchange Online Protection (EOP).</span></span> <span data-ttu-id="ffe1d-111">この保護には次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-111">This protection includes:</span></span>

- <span data-ttu-id="ffe1d-112">疑いのあるマルウェアを含む電子メールは自動的に検疫され、受信者に通知されます。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-112">Email with suspected malware will automatically be quarantined and recipients will be notified.</span></span> <span data-ttu-id="ffe1d-113">[EOP でマルウェア対策ポリシーを構成するを](configure-anti-malware-policies.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-113">See [Configure anti-malware policies in EOP](configure-anti-malware-policies.md).</span></span>
- <span data-ttu-id="ffe1d-114">精度の高いフィッシングとして識別されたメールは、スパム対策ポリシーアクションに従って処理されます。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-114">Email identified as high confidence phishing will be handled according to the anti-spam policy action.</span></span> <span data-ttu-id="ffe1d-115">[EOP の「スパム対策ポリシーの構成」を](configure-your-spam-filter-policies.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-115">See [Configure anti-spam policies in EOP](configure-your-spam-filter-policies.md).</span></span>

<span data-ttu-id="ffe1d-116">EOP の詳細については、「 [Exchange Online Protection の概要](exchange-online-protection-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-116">For more information about EOP, see [Exchange Online Protection overview](exchange-online-protection-overview.md).</span></span>

<span data-ttu-id="ffe1d-117">Microsoft は、お客様を既定で安全なものにすることを目的としているため、一部のテナントの上書きは、マルウェアや高精度のフィッシングには適用されません。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-117">Because Microsoft wants to keep our customers secure by default, some tenants overrides are not applied for malware or high confidence phishing.</span></span> <span data-ttu-id="ffe1d-118">これらのオーバーライドは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-118">These overrides include:</span></span>

- <span data-ttu-id="ffe1d-119">許可された送信者リストまたは許可されたドメインリスト (スパム対策ポリシー)</span><span class="sxs-lookup"><span data-stu-id="ffe1d-119">Allowed sender lists or allowed domain lists (anti-spam policies)</span></span>
- <span data-ttu-id="ffe1d-120">Outlook の差出人セーフリスト</span><span class="sxs-lookup"><span data-stu-id="ffe1d-120">Outlook Safe Senders</span></span>
- <span data-ttu-id="ffe1d-121">IP 許可一覧 (接続フィルター)</span><span class="sxs-lookup"><span data-stu-id="ffe1d-121">IP Allow List (connection filtering)</span></span>

<span data-ttu-id="ffe1d-122">これらのオーバーライドの詳細については、「 [安全な送信者リストを作成](create-safe-sender-lists-in-office-365.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-122">More information on these overrides can be found in [Create safe sender lists](create-safe-sender-lists-in-office-365.md).</span></span>

<span data-ttu-id="ffe1d-123">既定では、オンまたはオフにすることはできますが、潜在的に危険または不要なメッセージをメールボックスから保持するために、ボックスからフィルター処理を実行する方法は、セキュリティで保護されています。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-123">Secure by default is not a setting that can be turned on or off, but is the way our filtering works out of the box to keep potentially dangerous or unwanted messages out of your mailboxes.</span></span> <span data-ttu-id="ffe1d-124">マルウェアと信頼度の高いフィッシングメッセージは検疫される必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-124">Malware and high confidence phishing messages should be quarantined.</span></span> <span data-ttu-id="ffe1d-125">マルウェアまたは信頼度の高いフィッシングとして検疫されたメッセージを管理できるのは管理者のみです。また、そこから Microsoft に誤検知を報告することもできます。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-125">Only admins can manage messages that are quarantined as malware or high confidence phishing, and they can also report false positives to Microsoft from there.</span></span> <span data-ttu-id="ffe1d-126">詳細については、「 [EOP で管理者として検疫済みメッセージおよびファイルを管理する](manage-quarantined-messages-and-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-126">For more information, see [Manage quarantined messages and files as an admin in EOP](manage-quarantined-messages-and-files.md)</span></span>

## <a name="more-on-why-were-doing-this"></a><span data-ttu-id="ffe1d-127">これを実行する理由について</span><span class="sxs-lookup"><span data-stu-id="ffe1d-127">More on why we're doing this</span></span>

<span data-ttu-id="ffe1d-128">既定でセキュリティ保護されているのは、次のようになります。このメッセージが悪意のあるメッセージを受け取った場合に実行するのと同じ操作を実行しています。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-128">The spirit of being secure by default is: we're taking the same action on the message that you would take if you knew the message malicious, even if there was an allow in place.</span></span> <span data-ttu-id="ffe1d-129">これは、マルウェアに対して使用したのと同じ方法ですので、これと同じ動作を高信頼性のフィッシングメッセージにまで拡大しています。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-129">This is the same approach that we've used on malware, and now we're extending this same behavior to high confidence phishing messages.</span></span> <span data-ttu-id="ffe1d-130">このデータは、信頼度の高いフィッシングメッセージの誤検知率が非常に低いことを示しており、管理者が送信した場合には、管理者が誤検知を解決できます。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-130">Our data indicates that the false positive rate for high confidence phishing messages is very low, and admins can resolve any false positives with admin submissions.</span></span> <span data-ttu-id="ffe1d-131">また、このデータは、Outlook のスパム対策ポリシーと安全な送信者の許可された送信者の一覧および許可されるドメインの一覧が大きすぎて、正常ではなくなったことも示しています。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-131">Our data also indicates that the allowed sender lists and allowed domain lists in anti-spam policies and Safe Senders in Outlook were too broad and causing more harm than good.</span></span>

<span data-ttu-id="ffe1d-132">別の方法として、セキュリティサービスとして、ユーザーが危険にさらされないようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-132">To put it another way: as a security service, we're acting on your behalf to prevent your users from being compromised.</span></span> <span data-ttu-id="ffe1d-133">さらに、既定でのセキュリティ保護は、スパム対策ポリシーで信頼度の高いフィッシングメッセージに対して使用可能なオプションを完全に引き継ぐものではありません。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-133">In addition, secure by default is not a full takeover of your available options for high confidence phishing messages in anti-spam policies.</span></span> <span data-ttu-id="ffe1d-134">検疫は推奨されていますが、常に使用可能になっている他のアクションは引き続き利用できます ([迷惑メール] フォルダーに移動するか、電子メールアドレスにリダイレクトします)。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-134">Although we recommend Quarantine, the other actions that have always been available are still available (Move to Junk Email folder or Redirect to an email address).</span></span>

## <a name="exceptions"></a><span data-ttu-id="ffe1d-135">例外</span><span class="sxs-lookup"><span data-stu-id="ffe1d-135">Exceptions</span></span>

<span data-ttu-id="ffe1d-136">高信頼フィッシングメッセージがフィルターをバイパスすることを許可する唯一のオーバーライドは、Exchange メールフロールール (トランスポートルールとも呼ばれます) です。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-136">The only override that allows high confidence phishing message to bypass filtering is Exchange mail flow rules (also known as transport rules).</span></span> <span data-ttu-id="ffe1d-137">メールフロールールを使用してフィルター処理をバイパスするには、「 [メールフロールールを使用してメッセージに SCL を設定](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-137">To use mail flow rules to bypass filtering, see [Use mail flow rules to set the SCL in messages](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md).</span></span>

<span data-ttu-id="ffe1d-138">次のシナリオでは、オーバーライドの使用を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-138">You should only consider using overrides in the following scenarios:</span></span>

- <span data-ttu-id="ffe1d-139">フィッシングのシミュレーション: 実際の攻撃が組織に影響を与える前に、脆弱性のあるユーザーを特定するのに役立つ、シミュレートされた攻撃。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-139">Phishing simulations: Simulated attacks can help you identify vulnerable users before a real attack impacts your organization.</span></span>
- <span data-ttu-id="ffe1d-140">セキュリティ/SecOps メールボックス: セキュリティチームがフィルター処理されていないメッセージを取得するために使用する専用のメールボックス (良好および不良)。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-140">Security/SecOps mailboxes: Dedicated mailboxes used by security teams to get unfiltered messages (both good and bad).</span></span> <span data-ttu-id="ffe1d-141">チームは、悪意のあるコンテンツが含まれているかどうかを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-141">Teams can then review to see if they contain malicious content.</span></span>
- <span data-ttu-id="ffe1d-142">サードパーティ製のフィルター: サードパーティ製のフィルターによってメールフィルターが管理されるため、サードパーティベンダーによっては EOP (SCL =-1) をオフにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-142">Third-party filters: Some third-party vendors will recommend turning off EOP (SCL=-1) as the third-party filter will manage the mail filtering.</span></span> <span data-ttu-id="ffe1d-143">Microsoft [Defender For Office 365](office-365-atp.md)の EOP が必要な場合は、EOP をオフにすることはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-143">Microsoft does not recommend turning off EOP as EOP is required for [Microsoft Defender for Office 365](office-365-atp.md).</span></span> <span data-ttu-id="ffe1d-144">代わりに、 [コネクタの拡張フィルター処理](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)を有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-144">Instead, the recommendation here is to turn on [Enhanced Filtering for Connectors](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).</span></span>
- <span data-ttu-id="ffe1d-145">誤検知: Microsoft によって引き続き分析されている特定のメッセージを、 [管理者送信で](admin-submission.md)一時的に許可することができます。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-145">False positives: You might want to temporarily allow certain messages that are still being analyzed by Microsoft [via Admin submissions](admin-submission.md).</span></span> <span data-ttu-id="ffe1d-146">すべてのオーバーライドと同様に、一時的なものにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ffe1d-146">As with all overrides, it is recommended that they are temporary.</span></span>
