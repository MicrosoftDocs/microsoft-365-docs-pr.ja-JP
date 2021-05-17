---
title: MX レコードを更新してグローバル レコード サービスにExchange Onlineする
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
description: Microsoft Cloud Germany サービスからグローバル Exchange Onlineサービスに移行するExchange Onlineする
ms.openlocfilehash: 8de64e30205b07a0c20a8ae4f7cdedbf6cc6824f
ms.sourcegitcommit: 628f195cbe3c00910f7350d8b09997a675dde989
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "48644857"
---
# <a name="update-your-mx-records-to-transition-to-the-global-exchange-online-service"></a><span data-ttu-id="5c0a6-103">MX レコードを更新してグローバル レコード サービスにExchange Onlineする</span><span class="sxs-lookup"><span data-stu-id="5c0a6-103">Update your MX records to transition to the global Exchange Online service</span></span>

1. <span data-ttu-id="5c0a6-104">管理者ポータルに [サインインMicrosoft 365](https://admin.microsoft.com)し、[ドメイン] に移動設定  >  **します。**</span><span class="sxs-lookup"><span data-stu-id="5c0a6-104">Sign in to [Microsoft 365 admin portal](https://admin.microsoft.com), and go to **Settings** > **Domains**</span></span>

2. <span data-ttu-id="5c0a6-105">各ドメインの右側に状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5c0a6-105">Status will be shown on the right side for each domain.</span></span> <span data-ttu-id="5c0a6-106">組織のドメインが Microsoft Cloud Germany Exchange Onlineしている場合は、MX レコードを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c0a6-106">If your organization’s domains point to Microsoft Cloud Germany Exchange Online, you'll need to update your MX record.</span></span>

3. <span data-ttu-id="5c0a6-107">ドメインをクリックし、[DNS エラーが検出されました] **をクリックし、ここをクリックして表示します**。</span><span class="sxs-lookup"><span data-stu-id="5c0a6-107">Click the domain, then click **DNS errors detected, click here to view**.</span></span>

4. <span data-ttu-id="5c0a6-108">このページには、MX レコードを修正する方法を示す手順が記載されています。</span><span class="sxs-lookup"><span data-stu-id="5c0a6-108">This page will have instructions to show you how to fix the MX record.</span></span> <span data-ttu-id="5c0a6-109">ドメインのレジストラーが Domain Connectを使用している場合は、上部[の](../setup/add-domain.md#registrars-with-domain-connect)[レコードの修正] をクリックできます。</span><span class="sxs-lookup"><span data-stu-id="5c0a6-109">If your domain’s registrar uses [Domain Connect](../setup/add-domain.md#registrars-with-domain-connect), you can click “Fix my records” on top.</span></span> <span data-ttu-id="5c0a6-110">それ以外の場合は、ウィザードのリンクに従ってレジストラーの手順を実行できます。</span><span class="sxs-lookup"><span data-stu-id="5c0a6-110">Otherwise you can follow the link in the wizard to **step-by-step instructions** for your registrar.</span></span>