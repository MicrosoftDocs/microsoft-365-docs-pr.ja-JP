---
title: PowerShell で Microsoft 365を管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- O365ITProTrain
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: 932d57c0-1520-4f0f-8ec9-9966d646480f
description: Microsoft 365 のユーザーとライセンス、および PowerShell を使用した Microsoft 365 アプリを管理する方法について説明します。
ms.openlocfilehash: d0b98af9f0e8e832462468941fe39a9eb3c9ceae
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46692084"
---
# <a name="manage-microsoft-365-with-powershell"></a><span data-ttu-id="a12af-103">PowerShell で Microsoft 365を管理する</span><span class="sxs-lookup"><span data-stu-id="a12af-103">Manage Microsoft 365 with PowerShell</span></span>

<span data-ttu-id="a12af-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="a12af-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="a12af-105">Microsoft 365 の PowerShell は、Microsoft 365 管理センターを補完する強力な管理ツールです。</span><span class="sxs-lookup"><span data-stu-id="a12af-105">PowerShell for Microsoft 365 is a powerful management tool that complements the Microsoft 365 admin center.</span></span> <span data-ttu-id="a12af-106">たとえば、PowerShell オートメーションを使用して、複数のユーザーアカウントとライセンスをすばやく管理したり、レポートを作成したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="a12af-106">For example, you can use PowerShell automation to more quickly manage multiple user accounts and licenses and create reports.</span></span> <span data-ttu-id="a12af-107">Microsoft 365 ユーザーとライセンス、Skype for Business Online、SharePoint Online、Exchange Online、セキュリティ & コンプライアンスセンターで PowerShell を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a12af-107">Learn how to use PowerShell for Microsoft 365 users and licenses, Skype for Business Online, SharePoint Online, Exchange Online, and the Security & Compliance Center.</span></span>
  
<span data-ttu-id="a12af-108">以下から必要に合うトピックを選択してください。</span><span class="sxs-lookup"><span data-stu-id="a12af-108">Select the topic based on your needs:</span></span>
  
- [<span data-ttu-id="a12af-109">概要</span><span class="sxs-lookup"><span data-stu-id="a12af-109">Get started</span></span>](getting-started-with-microsoft-365-powershell.md)

    <span data-ttu-id="a12af-110">Microsoft 365 の PowerShell に精通しておらず、microsoft 365 モジュールをインストールして Microsoft 365 サブスクリプションに接続する場合は、ここから開始してください。</span><span class="sxs-lookup"><span data-stu-id="a12af-110">Start here if you are not familiar with PowerShell for Microsoft 365 and want to install the Microsoft 365 modules and connect to your Microsoft 365 subscription.</span></span>

- [<span data-ttu-id="a12af-111">ユーザーアカウント、ライセンス、およびグループ</span><span class="sxs-lookup"><span data-stu-id="a12af-111">User accounts, licenses, and groups</span></span>](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

    <span data-ttu-id="a12af-112">Microsoft 365 モジュールをインストールしてあり、オートメーションコマンドを使用してユーザーアカウント、ライセンス、グループを管理する方法について詳しく知りたい場合は、ここから開始してください。</span><span class="sxs-lookup"><span data-stu-id="a12af-112">Start here if you have installed the Microsoft 365 modules and want to learn more about using automation commands to manage user accounts, licenses, and groups.</span></span>

- [<span data-ttu-id="a12af-113">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a12af-113">SharePoint Online</span></span>](manage-sharepoint-online-with-microsoft-365-powershell.md)

    <span data-ttu-id="a12af-114">Microsoft 365 モジュールをインストールしていて、オートメーションコマンドを使用して SharePoint Online の管理を実行する場合は、ここから開始してください。</span><span class="sxs-lookup"><span data-stu-id="a12af-114">Start here if you have installed the Microsoft 365 modules and want to use automation commands to perform management of SharePoint Online.</span></span>

- [<span data-ttu-id="a12af-115">Exchange Online の PowerShell</span><span class="sxs-lookup"><span data-stu-id="a12af-115">Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)

    <span data-ttu-id="a12af-116">オートメーション コマンドを使用して Exchange Online を管理する場合は、ここから開始してください。</span><span class="sxs-lookup"><span data-stu-id="a12af-116">Start here if you want to use automation commands to manage Exchange Online.</span></span>

- [<span data-ttu-id="a12af-117">電子メールの移行</span><span class="sxs-lookup"><span data-stu-id="a12af-117">Email migration</span></span>](use-powershell-for-email-migration-to-microsoft-365.md)

    <span data-ttu-id="a12af-118">PowerShell 365 モジュールをインストールしていて、既存のシステムからメールを移行する場合は、ここから開始してください。</span><span class="sxs-lookup"><span data-stu-id="a12af-118">Start here if you have installed the PowerShell 365 modules and want to migrate your email from existing systems.</span></span>

- [<span data-ttu-id="a12af-119">セキュリティ/コンプライアンス センター</span><span class="sxs-lookup"><span data-stu-id="a12af-119">Security & Compliance Center</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell)

    <span data-ttu-id="a12af-120">オートメーション コマンドを使用してセキュリティ/コンプライアンス センターを管理する場合は、ここから開始してください。</span><span class="sxs-lookup"><span data-stu-id="a12af-120">Start here if you want to use automation commands to manage the Security & Compliance Center.</span></span>

- [<span data-ttu-id="a12af-121">代理アクセス許可 (DAP) パートナー</span><span class="sxs-lookup"><span data-stu-id="a12af-121">Delegated Access Permissions (DAP) partners</span></span>](manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-dap-p.md)

    <span data-ttu-id="a12af-122">シンジケートおよびクラウドソリューションプロバイダー (CSP) パートナーを使用して、Microsoft 365 の顧客テナントを管理する場合は、ここから開始してください。</span><span class="sxs-lookup"><span data-stu-id="a12af-122">Start here if you want to use Syndication and Cloud Solution Provider (CSP) partners to manage your Microsoft 365 customer tenants.</span></span>

- [<span data-ttu-id="a12af-123">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="a12af-123">Skype for Business Online</span></span>](manage-skype-for-business-online-with-microsoft-365-powershell.md)

    <span data-ttu-id="a12af-124">PowerShell モジュールをインストールして、Skype for Business Online の管理を実行する場合は、ここから開始してください。</span><span class="sxs-lookup"><span data-stu-id="a12af-124">Start here if you have installed the PowerShell modules and want to perform management of Skype for Business Online.</span></span>