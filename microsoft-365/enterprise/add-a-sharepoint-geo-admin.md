---
title: 地域管理者を追加または削除する
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
localization_priority: Normal
f1.keywords:
- NOCSH
description: 地理的な場所ごとに個別の管理者を構成する必要がありますか? Microsoft 365 Multi-Geo で地域管理者を追加または削除する方法について説明します。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 32fe5e934e6a3d6f18c802c3c427974e67c1b454
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "50905610"
---
# <a name="add-or-remove-a-geo-administrator-in-microsoft-365-multi-geo"></a><span data-ttu-id="28afb-104">Microsoft 365 Multi-Geo で地域管理者を追加または削除する</span><span class="sxs-lookup"><span data-stu-id="28afb-104">Add or remove a geo administrator in Microsoft 365 Multi-Geo</span></span>

<span data-ttu-id="28afb-105">テナント内にある地域の場所ごとに個別の管理者を構成することができます。</span><span class="sxs-lookup"><span data-stu-id="28afb-105">You can configure separate administrators for each geo location that you have in your tenant.</span></span> <span data-ttu-id="28afb-106">これらの管理者は、各自の地域の場所に固有の SharePoint Online と OneDrive の設定にアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="28afb-106">These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="28afb-107">用語ストアなどの一部のサービスは、中央の場所から管理され、サテライトの場所にレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="28afb-107">Some services - such as the term store - are administered from the central location and replicated to satellite locations.</span></span> <span data-ttu-id="28afb-108">中央の場所の地域管理者は、これらのサービスにアクセスできますが、サテライトの場所の地理管理者はアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="28afb-108">The geo admin for the central location has access to these, whereas geo admins for satellite locations don't.</span></span>

<span data-ttu-id="28afb-109">グローバル管理者と SharePoint Online 管理者は、中央の場所とすべてのサテライトの場所の設定に引き続きアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="28afb-109">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="28afb-110">地域管理者の構成</span><span class="sxs-lookup"><span data-stu-id="28afb-110">Configuring geo administrators</span></span>

<span data-ttu-id="28afb-111">地域管理者の構成には、SharePoint Online PowerShell モジュールが必要です。</span><span class="sxs-lookup"><span data-stu-id="28afb-111">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="28afb-112">[Connect-SPOService](/powershell/module/sharepoint-online/Connect-SPOService) を使用して、地域管理者を追加する地域の場所の管理センターに接続します。(例: Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="28afb-112">Use [Connect-SPOService](/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="28afb-113">場所の既存の地域管理者を表示するには、`Get-SPOGeoAdministrator` を実行します。</span><span class="sxs-lookup"><span data-stu-id="28afb-113">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="28afb-114">地域管理者としてのユーザーの追加</span><span class="sxs-lookup"><span data-stu-id="28afb-114">Adding a user as a geo admin</span></span>

<span data-ttu-id="28afb-115">地域管理者としてのユーザーを追加するには、`Add-SPOGeoAdministrator -UserPrincipalName <UPN>` を実行します。</span><span class="sxs-lookup"><span data-stu-id="28afb-115">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="28afb-116">場所の地域管理者としてのユーザーを削除するには、`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>` を実行します。</span><span class="sxs-lookup"><span data-stu-id="28afb-116">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="28afb-117">地域管理者としてのグループの追加</span><span class="sxs-lookup"><span data-stu-id="28afb-117">Adding a group as a geo admin</span></span>

<span data-ttu-id="28afb-118">地域管理者として、セキュリティ グループまたはメールが有効なセキュリティ グループを追加できます。(配布グループと Microsoft 365 グループはサポートされていません。)</span><span class="sxs-lookup"><span data-stu-id="28afb-118">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Microsoft 365 Groups are not supported.)</span></span>

<span data-ttu-id="28afb-119">地域管理者としてグループを追加するには、`Add-SPOGeoAdministrator -GroupAlias <alias>` を実行します。</span><span class="sxs-lookup"><span data-stu-id="28afb-119">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="28afb-120">地域管理者としてのグループを削除するには、`Remove-SPOGeoAdministrator -GroupAlias <alias>` を実行します。</span><span class="sxs-lookup"><span data-stu-id="28afb-120">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="28afb-121">一部のセキュリティ グループにはグループ エイリアスがないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="28afb-121">Note that not all security groups have a group alias.</span></span> <span data-ttu-id="28afb-122">エイリアスがないセキュリティ グループを追加する場合は、[Get-MsolGroup](/powershell/module/msonline/get-msolgroup) を実行して、グループの一覧を取得し、セキュリティ グループの ObjectID を検索して、次を実行します。</span><span class="sxs-lookup"><span data-stu-id="28afb-122">If you want to add a security group that does not have an alias, run [Get-MsolGroup](/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="28afb-123">ObjectID を使用してグループを削除するには、`Remove-SPOGeoAdministrator -ObjectID <ObjectID>` を実行します。</span><span class="sxs-lookup"><span data-stu-id="28afb-123">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

## <a name="related-topics"></a><span data-ttu-id="28afb-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="28afb-124">Related topics</span></span>

[<span data-ttu-id="28afb-125">Add-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="28afb-125">Add-SPOGeoAdministrator</span></span>](/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="28afb-126">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="28afb-126">Get-SPOGeoAdministrator</span></span>](/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="28afb-127">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="28afb-127">Remove-SPOGeoAdministrator</span></span>](/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="28afb-128">セキュリティ グループのエイリアス (MailNickName) を設定する</span><span class="sxs-lookup"><span data-stu-id="28afb-128">Set an alias (MailNickName) for a security group</span></span>](/powershell/module/azuread/set-azureadgroup)