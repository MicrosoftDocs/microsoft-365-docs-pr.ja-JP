---
title: Microsoft 365 にドメインを接続する
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
search.appverid:
- MET150
ROBOTS: NOINDEX, NOFOLLOW
description: ドメインを確認し、Microsoft 365 で DNS レコードを作成する方法を学びます。
ms.custom:
- okr_smb
- AdminSurgePortfolio
ms.openlocfilehash: 206b435130e8e77ed1540432e3bbeff7f16463bf
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "49658203"
---
# <a name="connect-your-domain-to-microsoft-365"></a><span data-ttu-id="00304-103">Microsoft 365 にドメインを接続する</span><span class="sxs-lookup"><span data-stu-id="00304-103">Connect your domain to Microsoft 365</span></span>

> [!NOTE]
> <span data-ttu-id="00304-104">ドメインを追加しない場合、組織内のユーザーは、メール アドレスに onmicrosoft.com ドメインを使用します。</span><span class="sxs-lookup"><span data-stu-id="00304-104">If you don't add a domain, people in your organization will use the onmicrosoft.com domain for their email addresses until you do.</span></span> <span data-ttu-id="00304-105">ユーザーを追加する前にドメインを追加することが重要です。それにより、ユーザーを再度セットアップする必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="00304-105">It's important to add your domain before you add users, so you don't have to set them up twice.</span></span>

<span data-ttu-id="00304-106">探している内容が見つからない場合は、[ドメインに関する FAQ](../setup/domains-faq.yml) を確認してください。</span><span class="sxs-lookup"><span data-stu-id="00304-106">[Check the Domains FAQ](../setup/domains-faq.yml) if you don't find what you're looking for below.</span></span>

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a><span data-ttu-id="00304-107">MX レコードを追加して、自分のドメインのメールが Microsoft に届くようにする</span><span class="sxs-lookup"><span data-stu-id="00304-107">Add an MX record so email for your domain will come to Microsoft</span></span>

<span data-ttu-id="00304-108">MX レコードの情報は、管理センターのドメイン セットアップ ウィザードから取得されます。</span><span class="sxs-lookup"><span data-stu-id="00304-108">You'll get the information for the MX record from the admin center domain setup wizard.</span></span>

<span data-ttu-id="00304-109">ホスティング プロバイダーの Web サイトで、新しい MX レコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="00304-109">On your hosting provider's website, add a new MX record.</span></span>
<span data-ttu-id="00304-110">フィールドが次の値に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="00304-110">Make sure that the fields are set to the following values:</span></span>

- <span data-ttu-id="00304-111">Record Type: `MX`</span><span class="sxs-lookup"><span data-stu-id="00304-111">Record Type: `MX`</span></span>
- <span data-ttu-id="00304-112">Priority: 使用可能な最高の値を設定します。通常は `0` です。</span><span class="sxs-lookup"><span data-stu-id="00304-112">Priority: Set to the highest value available, typically `0`.</span></span>
- <span data-ttu-id="00304-113">Host Name: `@`</span><span class="sxs-lookup"><span data-stu-id="00304-113">Host Name: `@`</span></span>
- <span data-ttu-id="00304-114">Points to address: 管理センターから値をコピーし、ここに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="00304-114">Points to address: Copy the value from the admin center and paste it here.</span></span>
- <span data-ttu-id="00304-115">TTL: `3600‎` (またはプロバイダーの既定値)</span><span class="sxs-lookup"><span data-stu-id="00304-115">TTL: `3600‎` (or your provider default)</span></span>

<span data-ttu-id="00304-116">レコードを保存して、他の MX レコードを削除します。</span><span class="sxs-lookup"><span data-stu-id="00304-116">Save the record, and then remove any other MX records.</span></span>

## <a name="add-a-cname-record-to-connect-users-to-their-mailboxes"></a><span data-ttu-id="00304-117">CNAME レコードを追加して、ユーザーをメールボックスに接続します</span><span class="sxs-lookup"><span data-stu-id="00304-117">Add a CNAME record to connect users to their mailboxes</span></span>
<span data-ttu-id="00304-118">CNAME レコードの情報は、管理センターのドメイン セットアップ ウィザードから取得されます。</span><span class="sxs-lookup"><span data-stu-id="00304-118">You'll get the information for the CNAME records from the admin center domain setup wizard.</span></span>

<span data-ttu-id="00304-119">ホスティング プロバイダーの Web サイトで、以下の CNAME レコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="00304-119">On your hosting provider's website, add the following CNAME record.</span></span> <span data-ttu-id="00304-120">フィールドが次の値に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="00304-120">Make sure that the fields are set to the following values for each:</span></span>

- <span data-ttu-id="00304-121">Record Type: `CNAME (Alias)`</span><span class="sxs-lookup"><span data-stu-id="00304-121">Record Type: `CNAME (Alias)`</span></span>
- <span data-ttu-id="00304-122">Host: 管理センターからコピーした値をここに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="00304-122">Host: Paste the values you copy from the admin center here.</span></span>
- <span data-ttu-id="00304-123">Points to address: 管理センターから値をコピーし、ここに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="00304-123">Points to address: Copy the value from the admin center and paste it here.</span></span>
- <span data-ttu-id="00304-124">TTL: `3600‎` (またはプロバイダーの既定値)</span><span class="sxs-lookup"><span data-stu-id="00304-124">TTL: `3600‎` (or your provider default)</span></span>

## <a name="add-a-txt-record-to-help-prevent-spam"></a><span data-ttu-id="00304-125">迷惑メールの防止に役立つ SPF の TXT レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="00304-125">Add a TXT record to help prevent spam</span></span>
<span data-ttu-id="00304-126">**開始する前に:** 使用しているドメインに既に SPF レコードがある場合は、Microsoft 365 用に新しいレコードを作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="00304-126">**Before you begin:** If you already have an SPF record for your domain, don't create a new one for Microsoft 365.</span></span> <span data-ttu-id="00304-127">代わりに、ホスティング プロバイダーの Web サイトの現在のレコードに Microsoft 365 で必要になる値を追加して、元々の値と追加する値の組み合わせが *1 つ* の SPF レコードに含まれるようにします。</span><span class="sxs-lookup"><span data-stu-id="00304-127">Instead, add the required Microsoft 365 values to the current record on your hosting providers website so that you have a *single* SPF record that includes both sets of values.</span></span>

<span data-ttu-id="00304-128">ホスティング プロバイダーの Web サイトで、既存の SPF レコードを編集するか、SPF レコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="00304-128">On your hosting provider's website, edit the existing SPF record or create an SPF record.</span></span>
<span data-ttu-id="00304-129">フィールドが次の値に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="00304-129">Make sure that the fields are set to the following values:</span></span>

- <span data-ttu-id="00304-130">Record Type: `TXT (Text)`</span><span class="sxs-lookup"><span data-stu-id="00304-130">Record Type: `TXT (Text)`</span></span>
- <span data-ttu-id="00304-131">Host: `@`</span><span class="sxs-lookup"><span data-stu-id="00304-131">Host: `@`</span></span>
- <span data-ttu-id="00304-132">TXT Value: `v=spf1 include:spf.protection.outlook.com -all`</span><span class="sxs-lookup"><span data-stu-id="00304-132">TXT Value: `v=spf1 include:spf.protection.outlook.com -all`</span></span>
- <span data-ttu-id="00304-133">TTL: `3600‎` (またはプロバイダーの既定値)</span><span class="sxs-lookup"><span data-stu-id="00304-133">TTL: `3600‎` (or your provider default)</span></span>

<span data-ttu-id="00304-134">レコードを保存します。</span><span class="sxs-lookup"><span data-stu-id="00304-134">Save the record.</span></span>

<span data-ttu-id="00304-135">SPF レコードを検証するには、[SPF 検証ツール](https://docs.microsoft.com/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain)のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="00304-135">Validate your SPF record by using one of these [SPF validation tools](https://docs.microsoft.com/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain)</span></span>

<span data-ttu-id="00304-136">SPF はスプーフィングの防止に役立ちますが、SPF では保護できないスプーフィング方法があります。</span><span class="sxs-lookup"><span data-stu-id="00304-136">SPF is designed to help prevent spoofing, but there are spoofing techniques that SPF cannot protect against.</span></span> <span data-ttu-id="00304-137">これらから保護するために、SPF をセットアップした後、Microsoft 365 のために DKIM と DMARC も構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00304-137">To protect against these, once you've set up SPF, you should also set up DKIM and DMARC for Microsoft 365.</span></span>

<span data-ttu-id="00304-138">使用を開始する場合は、「[DKIM を使用して、Microsoft 365 のドメインから送信される送信電子メールを検証する](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx)」、「[DMARC を使用して Microsoft 365 のメールを検証する](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00304-138">To get started, see [Use DKIM to validate outbound email sent from your domain in Microsoft 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx) and [Use DMARC to validate email in Microsoft 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx).</span></span>

<span data-ttu-id="00304-139">最後に、管理センターのドメイン セットアップ ウィザードに戻って設定を完了します。</span><span class="sxs-lookup"><span data-stu-id="00304-139">Finally, head back to the admin center domain setup wizard to complete your setup.</span></span>