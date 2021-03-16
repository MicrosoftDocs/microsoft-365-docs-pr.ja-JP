---
title: Exact Data Match アクティビティの通知を作成する (プレビュー)
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Exact Data Match アクティビティの通知を作成する方法について説明します。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a537cffe253fa20cf6838ddf3fd9a51ec440fe76
ms.sourcegitcommit: 89095172c9c4793d56645b4c885ac8e30936bd0a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2021
ms.locfileid: "50766695"
---
# <a name="create-notifications-for-exact-data-match-activities-preview"></a><span data-ttu-id="7ddab-103">Exact Data Match アクティビティの通知を作成する (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="7ddab-103">Create notifications for exact data match activities (preview)</span></span>

<span data-ttu-id="7ddab-104">[Exact Data Match (EDM) を使用してカスタムの機密情報の種類を作成する](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md)と、[監査ログ](search-the-audit-log-in-security-and-compliance.md#requirements-to-search-the-audit-log)に作成されるアクティビティが多数あります。</span><span class="sxs-lookup"><span data-stu-id="7ddab-104">When you [create custom sensitive information types with exact data match (EDM)](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md) there are a number of activities that are created in the [audit log](search-the-audit-log-in-security-and-compliance.md#requirements-to-search-the-audit-log).</span></span> <span data-ttu-id="7ddab-105">[New-ProtectionAlert](https://docs.microsoft.com/powershell/module/exchange/new-protectionalert?view=exchange-ps) PowerShell コマンドレットを使用して、次のアクティビティが発生したときに知らせる通知を作成できます。</span><span class="sxs-lookup"><span data-stu-id="7ddab-105">You can use the [New-ProtectionAlert](https://docs.microsoft.com/powershell/module/exchange/new-protectionalert?view=exchange-ps) PowerShell cmdlet to create notifications that let you know when these activities occur:</span></span>

- <span data-ttu-id="7ddab-106">CreateSchema</span><span class="sxs-lookup"><span data-stu-id="7ddab-106">CreateSchema</span></span>
- <span data-ttu-id="7ddab-107">EditSchema</span><span class="sxs-lookup"><span data-stu-id="7ddab-107">EditSchema</span></span>
- <span data-ttu-id="7ddab-108">RemoveSchema</span><span class="sxs-lookup"><span data-stu-id="7ddab-108">RemoveSchema</span></span>
- <span data-ttu-id="7ddab-109">UploadDataFailed</span><span class="sxs-lookup"><span data-stu-id="7ddab-109">UploadDataFailed</span></span>
- <span data-ttu-id="7ddab-110">UploadDataCompleted</span><span class="sxs-lookup"><span data-stu-id="7ddab-110">UploadDataCompleted</span></span>

> [!NOTE]
> <span data-ttu-id="7ddab-111">EDM アクティビティの通知を作成できるのは、World Wide クラウドと GCC クラウドだけです。</span><span class="sxs-lookup"><span data-stu-id="7ddab-111">The ability to create notifications for EDM activities is only available for the World Wide and GCC clouds only.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="7ddab-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="7ddab-112">Pre-requisites</span></span>

<span data-ttu-id="7ddab-113">使用するアカウントは、次のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ddab-113">The account you use must be one of the following:</span></span>

- <span data-ttu-id="7ddab-114">グローバル管理者</span><span class="sxs-lookup"><span data-stu-id="7ddab-114">a global admin</span></span>
- <span data-ttu-id="7ddab-115">コンプライアンス管理者</span><span class="sxs-lookup"><span data-stu-id="7ddab-115">compliance administrator</span></span>
- <span data-ttu-id="7ddab-116">Exchange Online 管理者</span><span class="sxs-lookup"><span data-stu-id="7ddab-116">Exchange Online administrator</span></span>

<span data-ttu-id="7ddab-117">DLP アクセス許可の詳細については、「[アクセス許可](data-loss-prevention-policies.md#permissions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ddab-117">To learn more about DLP permissions, see [Permissions](data-loss-prevention-policies.md#permissions).</span></span>

<span data-ttu-id="7ddab-118">これらのサブスクリプションには、EDM ベースの分類が含まれています</span><span class="sxs-lookup"><span data-stu-id="7ddab-118">EDM-based classification is included in these subscriptions</span></span>

- <span data-ttu-id="7ddab-119">Office 365 E5</span><span class="sxs-lookup"><span data-stu-id="7ddab-119">Office 365 E5</span></span>
- <span data-ttu-id="7ddab-120">Microsoft 365 E5</span><span class="sxs-lookup"><span data-stu-id="7ddab-120">Microsoft 365 E5</span></span>
- <span data-ttu-id="7ddab-121">Microsoft 365 E5 Compliance </span><span class="sxs-lookup"><span data-stu-id="7ddab-121">Microsoft 365 E5 Compliance</span></span>
- <span data-ttu-id="7ddab-122">Microsoft E5/A5 Information Protection and Governance</span><span class="sxs-lookup"><span data-stu-id="7ddab-122">Microsoft E5/A5 Information Protection and Governance</span></span>

<span data-ttu-id="7ddab-123">DLP ライセンスの詳細については、「[セキュリティとコンプライアンスのための Microsoft 365 ライセンス ガイダンス](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ddab-123">To learn more about DLP licensing, see [Microsoft 365 licensing guidance for security & compliance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)</span></span>

## <a name="configure-notifications-for-edm-activities"></a><span data-ttu-id="7ddab-124">EDM アクティビティの通知を構成する</span><span class="sxs-lookup"><span data-stu-id="7ddab-124">Configure notifications for EDM activities</span></span>

1. <span data-ttu-id="7ddab-125">[セキュリティ/コンプライアンス センターの PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell?view=exchange-ps) に接続する</span><span class="sxs-lookup"><span data-stu-id="7ddab-125">Connect to the [Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell?view=exchange-ps)</span></span> 

2. <span data-ttu-id="7ddab-126">通知を作成するアクティビティを使用して、`New-ProtectionAlert` コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="7ddab-126">Run the `New-ProtectionAlert` cmdlet using the activity that you want to create the notification for.</span></span>  <span data-ttu-id="7ddab-127">たとえば、**UploadDataCompleted** 操作が発生したときに通知を受け取りたい場合は、実行できる</span><span class="sxs-lookup"><span data-stu-id="7ddab-127">For example, if you want to be notified when the **UploadDataCompleted** action occured, run</span></span>

```powershell
New-ProtectionAlert -Name "EdmUploadCompleteAlertPolicy" -Category Others -NotifyUser <***address to send  notification to***> -ThreatType Activity -Operation UploadDataCompleted -Description "Custom alert policy to track when EDM upload Completed" -AggregationType None
```

<span data-ttu-id="7ddab-128">**UploadDataFailed** に対して実行します</span><span class="sxs-lookup"><span data-stu-id="7ddab-128">for the **UploadDataFailed** you can run</span></span>

```powershell
New-ProtectionAlert -Name "EdmUploadFailAlertPolicy" -Category Others -NotifyUser <***SMTP address to send notification to***> -ThreatType Activity -Operation UploadDataFailed -Description "Custom alert policy to track when EDM upload Failed" -AggregationType None -Severity High
```

## <a name="related-articles"></a><span data-ttu-id="7ddab-129">関連記事</span><span class="sxs-lookup"><span data-stu-id="7ddab-129">Related articles</span></span>

- [<span data-ttu-id="7ddab-130">Exact Data Match (EDM) によりカスタムの機密情報の種類を作成する</span><span class="sxs-lookup"><span data-stu-id="7ddab-130">Create custom sensitive information types with exact data match (EDM)</span></span>](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md)
- [<span data-ttu-id="7ddab-131">New-ProtectionAlert</span><span class="sxs-lookup"><span data-stu-id="7ddab-131">New-ProtectionAlert</span></span>](https://docs.microsoft.com/powershell/module/exchange/new-protectionalert?view=exchange-ps) 