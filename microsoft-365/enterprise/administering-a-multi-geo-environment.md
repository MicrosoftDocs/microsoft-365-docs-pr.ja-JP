---
title: 複数地域環境の管理
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Normal
description: 管理者は、複数地域の環境でSharePointサービスOneDrive管理する方法について学習できます。
ms.openlocfilehash: 9ef22a34881ef5c9c2ed72835bc88c1dbfe835b5
ms.sourcegitcommit: 7dc3b4dec05299abb4290a6e3d1ebe0fdc622ed7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2021
ms.locfileid: "53363945"
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="a5259-103">複数地域環境の管理</span><span class="sxs-lookup"><span data-stu-id="a5259-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="a5259-104">ここでは、複数地域環境で Microsoft 365 のサービスが動作するしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a5259-104">Here's a look at how Microsoft 365 services work in a multi-geo environment.</span></span>

## <a name="administrator-experience"></a><span data-ttu-id="a5259-105">管理者エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="a5259-105">Administrator experience</span></span>

<span data-ttu-id="a5259-106">管理[センター SharePoint](https://admin.microsoft.com/sharepoint)左側のナビゲーションに[地域の場所] タブが表示され、地域の場所を表示および管理できる地理的位置マップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a5259-106">The [SharePoint admin center](https://admin.microsoft.com/sharepoint) has a **Geo locations** tab in the left navigation which features a geo locations map where you can view and manage your geo locations.</span></span> <span data-ttu-id="a5259-107">テナントの地理的な場所を追加または削除するには、このページを使用します。</span><span class="sxs-lookup"><span data-stu-id="a5259-107">Use this page to add or delete geo locations for your tenant.</span></span>

## <a name="audit-log-search"></a><span data-ttu-id="a5259-108">監査ログ検索</span><span class="sxs-lookup"><span data-stu-id="a5259-108">Audit log search</span></span>

<span data-ttu-id="a5259-109">すべてのサテライト地域に対して統合された[監査ログ](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)は、Microsoft 365 監査ログの検索ページから利用できます。</span><span class="sxs-lookup"><span data-stu-id="a5259-109">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your satellite locations is available from the Microsoft 365 audit log search page.</span></span> <span data-ttu-id="a5259-110">すべての地域からの監査ログのエントリを参照できます。たとえば、NAM ユーザーと EUR ユーザーのアクティビティが、1 つの組織ビューに表示され、既存のフィルターを適用することで特定のユーザーのアクティビティを確認できます。</span><span class="sxs-lookup"><span data-stu-id="a5259-110">You can see all the audit log entries from across geo locations, for example, NAM & EUR users' activities will show up in one org view and then you can apply existing filters to see specific user's activities.</span></span>

## <a name="bcs-secure-store-apps"></a><span data-ttu-id="a5259-111">BCS、Secure Store、Apps</span><span class="sxs-lookup"><span data-stu-id="a5259-111">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="a5259-112">BCS、Secure Store、およびすべての App は、各サテライトの場所に個別のインスタンスがあります。そのため、SharePoint Online 管理者は、これらのサービスを各サテライトの場所とは別に管理および構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5259-112">BCS, Secure Store, and Apps all have separate instances in each satellite location, therefore the SharePoint Online administrator should manage and configure these services separately from each satellite location.</span></span>

## <a name="compliance-admin-center"></a><span data-ttu-id="a5259-113">コンプライアンス管理センター</span><span class="sxs-lookup"><span data-stu-id="a5259-113">Compliance admin center</span></span>

<span data-ttu-id="a5259-114">複数地域テナントには、コンプライアンス管理センターとコンプライアンス管理センターの 1[つのMicrosoft 365センターがあります](https://compliance.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="a5259-114">There is one central compliance center for a multi-geo tenant: [Microsoft 365 Compliance admin center](https://compliance.microsoft.com/).</span></span>

## <a name="ediscovery"></a><span data-ttu-id="a5259-115">電子情報開示</span><span class="sxs-lookup"><span data-stu-id="a5259-115">eDiscovery</span></span>

<span data-ttu-id="a5259-116">デフォルトでは、複数地域のテナントの eDiscovery Manager またはeDiscovery Administrator が、そのテナントの中心地でのみ電子情報の開示ができるようになります。</span><span class="sxs-lookup"><span data-stu-id="a5259-116">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant.</span></span> <span data-ttu-id="a5259-117">Office 365 全体管理者は、別のユーザーが電子情報開示を実行できるように電子情報開示マネージャーのアクセス許可を割り当てる必要があります。また、サテライトの場所として電子情報開示を実施する地域を指定するために該当するコンプライアンス セキュリティ フィルターで "Region" パラメーターを割り当てる必要があります。それ以外の場合は、サテライトの場所で電子情報開示は実施されません。</span><span class="sxs-lookup"><span data-stu-id="a5259-117">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a "Region" parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span> <span data-ttu-id="a5259-118">地域のコンプライアンス セキュリティ フィルター を構成するには、[Office 365 Multi-Geo eDiscovery の構成](multi-geo-ediscovery-configuration.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5259-118">To configure the Compliance Security Filter for a Region, see [Configure Office 365 Multi-Geo eDiscovery](multi-geo-ediscovery-configuration.md).</span></span>

## <a name="exchange-mailboxes"></a><span data-ttu-id="a5259-119">Exchange メールボックス</span><span class="sxs-lookup"><span data-stu-id="a5259-119">Exchange mailboxes</span></span>

<span data-ttu-id="a5259-120">ユーザーの PDL が変更された場合、Exchange メールボックスが自動的に移動します。</span><span class="sxs-lookup"><span data-stu-id="a5259-120">Users' Exchange mailboxes are moved automatically if their PDL is changed.</span></span> <span data-ttu-id="a5259-121">新しいメールボックスが作成されたとき、ユーザーの PDL の値が設定されていない場合は、ユーザーの PDL または中心地にメールボックスがプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="a5259-121">When a new mailbox is created, it is provisioned to the user's PDL or to the central location if no value has been set for the user's PDL.</span></span>

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="a5259-122">情報保護 (IP) データ損失防止 (DLP) ポリシー</span><span class="sxs-lookup"><span data-stu-id="a5259-122">Information Protection (IP) Data Loss Prevention (DLP) policy</span></span>

<span data-ttu-id="a5259-123">必要に応じて、テナント全体または該当するユーザーにポリシーの範囲を指定するセキュリティ & コンプライアンス センターで、OneDrive for Business、SharePoint、Exchange の IP DLP ポリシーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="a5259-123">You can set your IP DLP policies for OneDrive for Business, SharePoint, and Exchange in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users.</span></span> <span data-ttu-id="a5259-124">例: サテライト地域にいるユーザーのポリシーを選択する場合は、そのポリシーを特定の OneDrive に適用し、ユーザーの OneDrive URL を入力するように選択します。</span><span class="sxs-lookup"><span data-stu-id="a5259-124">For example: If you wish to select a policy for a user in a satellite location, select to apply the policy to a specific OneDrive and enter the user's OneDrive url.</span></span> <span data-ttu-id="a5259-125">DLP ポリシーを作成する際の一般的なガイダンスについては、[データ損失防止ポリシーの概要](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5259-125">See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="a5259-126">DLP ポリシーは、そのポリシーの適用性に基づいて各地域の場所に自動的に同期されます。</span><span class="sxs-lookup"><span data-stu-id="a5259-126">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="a5259-127">地域の場所のすべてのユーザーに対する Information Protection ポリシーとデータ損失防止ポリシーの実装は、UI で使用可能なオプションではありません。その代わりに、ポリシーの適用が可能なアカウントを選択するか、すべてのアカウントにグローバルにポリシーを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5259-127">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable accounts for the policy or apply the policy globally to all accounts.</span></span>

## <a name="microsoft-powerapps"></a><span data-ttu-id="a5259-128">Microsoft PowerApps</span><span class="sxs-lookup"><span data-stu-id="a5259-128">Microsoft PowerApps</span></span>

<span data-ttu-id="a5259-129">サテライト地域に作成された PowerApps は、テナントの中心地にあるエンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="a5259-129">PowerApps created for the satellite location will use the end point located in the central location for the tenant.</span></span> <span data-ttu-id="a5259-130">Microsoft PowerApps は、Multi-Geo サービスではありません。</span><span class="sxs-lookup"><span data-stu-id="a5259-130">Microsoft PowerApps is not a Multi-Geo service.</span></span> 

## <a name="power-automate"></a><span data-ttu-id="a5259-131">Power Automate</span><span class="sxs-lookup"><span data-stu-id="a5259-131">Power Automate</span></span>

<span data-ttu-id="a5259-132">サテライト地域に作成された Flow は、テナントのデフォルトの地域にあるエンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="a5259-132">Flows created for the satellite location will use the end point located in the default geo location for the tenant.</span></span>  <span data-ttu-id="a5259-133">Power Automateは、複数地域サービスではありません。</span><span class="sxs-lookup"><span data-stu-id="a5259-133">Power Automate is not a Multi-Geo service.</span></span> 

## <a name="sharepoint-storage-quota"></a><span data-ttu-id="a5259-134">SharePoint のストレージ クォータ</span><span class="sxs-lookup"><span data-stu-id="a5259-134">SharePoint storage quota</span></span>

<span data-ttu-id="a5259-135">デフォルトでは、複数地域環境のすべての地域では、使用できるテナントの ストレージ クォータを共有します。</span><span class="sxs-lookup"><span data-stu-id="a5259-135">By default, all geo locations of a multi-geo environment share the available tenant storage quota.</span></span>  <span data-ttu-id="a5259-136">特定の地域に固有のクォータを割り当てることで、ストレージ クォータを管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="a5259-136">You can also manage the storage quota by allocating a specific quota for a particular geo location.</span></span> <span data-ttu-id="a5259-137">詳細については、[複数地域環境における SharePoint ストレージ クォータ](sharepoint-multi-geo-storage-quota.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5259-137">For more information, see [SharePoint storage quotas in multi-geo environments](sharepoint-multi-geo-storage-quota.md).</span></span>

## <a name="sharing"></a><span data-ttu-id="a5259-138">共有</span><span class="sxs-lookup"><span data-stu-id="a5259-138">Sharing</span></span>

<span data-ttu-id="a5259-139">管理者は、各地域のポリシーの共有を設定し管理できます。</span><span class="sxs-lookup"><span data-stu-id="a5259-139">Administrators can set and manage sharing policies for each of their locations.</span></span> <span data-ttu-id="a5259-140">各地域OneDriveのSharePointサイトとサイトは、対応する地域固有の共有設定のみを受け入れる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5259-140">The OneDrive and SharePoint sites in each geo location will honor only the corresponding geo-specific sharing settings.</span></span> <span data-ttu-id="a5259-141">(たとえば、中心地への[外部共有](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)は許可できますが、サテライト地域またはその逆にはできません) 共有設定は地域間の共有制限を構成できませんので注意してください。</span><span class="sxs-lookup"><span data-stu-id="a5259-141">(For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa.) Note that the sharing settings do not allow configuring sharing limitations between geo locations.</span></span>

## <a name="stream"></a><span data-ttu-id="a5259-142">Stream</span><span class="sxs-lookup"><span data-stu-id="a5259-142">Stream</span></span>

<span data-ttu-id="a5259-143">1:1 チャットで Stream にアップロードされたビデオは、アップロードするユーザーのOneDriveに保存されます。</span><span class="sxs-lookup"><span data-stu-id="a5259-143">Videos uploaded to Stream in a 1:1 chat are stored in the OneDrive of the person uploading.</span></span> <span data-ttu-id="a5259-144">会議の記録は、会議を記録OneDrive出席者のグループに保存されます。</span><span class="sxs-lookup"><span data-stu-id="a5259-144">Meeting recordings are stored in the OneDrive of each attendee who records the meeting.</span></span>

## <a name="taxonomy"></a><span data-ttu-id="a5259-145">分類</span><span class="sxs-lookup"><span data-stu-id="a5259-145">Taxonomy</span></span>

<span data-ttu-id="a5259-146">エンタープライズで管理されるメタデータ[](/sharepoint/managed-metadata)の統合分類は、地理的な場所全体でサポートされ、マスターは会社の一元的な場所でホストされます。</span><span class="sxs-lookup"><span data-stu-id="a5259-146">We support a unified [taxonomy](/sharepoint/managed-metadata) for enterprise-managed metadata across geo locations, with the master being hosted in the central location for your company.</span></span> <span data-ttu-id="a5259-147">中心地からグローバル分類を管理し、サテライト地域の分類に地域固有の用語を追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a5259-147">We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite location's Taxonomy.</span></span> <span data-ttu-id="a5259-148">グローバル分類の用語は、サテライト地域に同期されます。</span><span class="sxs-lookup"><span data-stu-id="a5259-148">Global taxonomy terms will synchronize to the satellite locations.</span></span>

<span data-ttu-id="a5259-149">詳細と開発者向けガイダンスについては、[複数地域テナントにおけるメタデータの管理](/sharepoint/dev/solution-guidance/multigeo-managedmetadata)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5259-149">See [Manage metadata in a multi-geo tenant](/sharepoint/dev/solution-guidance/multigeo-managedmetadata) for additional details and for developer guidance.</span></span>

## <a name="user-profile-application"></a><span data-ttu-id="a5259-150">ユーザー プロファイル アプリケーション</span><span class="sxs-lookup"><span data-stu-id="a5259-150">User Profile Application</span></span>

<span data-ttu-id="a5259-151">各地域に[ユーザー プロフィール アプリケーション](/sharepoint/manage-user-profiles)があります。</span><span class="sxs-lookup"><span data-stu-id="a5259-151">There is a [user profile application](/sharepoint/manage-user-profiles) in each geo location.</span></span> <span data-ttu-id="a5259-152">各ユーザーのプロフィール情報は、ユーザーの地域でホストされており、その地域の管理者が利用できます。</span><span class="sxs-lookup"><span data-stu-id="a5259-152">Each user's profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="a5259-153">カスタムのプロフィール プロパティがある場合は、すべての地域で同じプロフィール スキーマを使用して、すべての地域の場所または必要な場所のどちらかにカスタムのプロフィール プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="a5259-153">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed.</span></span> <span data-ttu-id="a5259-154">プログラムを使用したユーザー プロフィール データの設定方法に関するガイダンスは、[ユーザー プロフィールの一括更新 API](/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5259-154">For guidance regarding how to populate user profile data programmatically, please refer to the [Bulk User Profile Update API](/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).</span></span>

<span data-ttu-id="a5259-155">詳細と開発者向けガイダンスについては、[複数地域テナントのユーザー プロフィールの操作](/sharepoint/dev/solution-guidance/multigeo-userprofileexperience)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5259-155">See [Work with user profiles in a multi-geo tenant](/sharepoint/dev/solution-guidance/multigeo-userprofileexperience) for additional details and for developer guidance.</span></span>

## <a name="yammer"></a><span data-ttu-id="a5259-156">Yammer</span><span class="sxs-lookup"><span data-stu-id="a5259-156">Yammer</span></span>

<span data-ttu-id="a5259-157">Yammerは、複数地域のワークロードではありません。</span><span class="sxs-lookup"><span data-stu-id="a5259-157">Yammer is not a Multi-Geo workload.</span></span> <span data-ttu-id="a5259-158">Yammerに格納Yammerスレッドは、テナントの中央の場所に配置されます。</span><span class="sxs-lookup"><span data-stu-id="a5259-158">Yammer threads stored in Yammer will be placed in the tenant’s central location.</span></span> <span data-ttu-id="a5259-159">Yammerは、ファイルストレージの変更を展開しています。この変更により、Yammerファイルが格納SharePoint。</span><span class="sxs-lookup"><span data-stu-id="a5259-159">Yammer is rolling out a file storage change which will store Yammer files within SharePoint.</span></span> <span data-ttu-id="a5259-160">Yammerに保存SharePointファイルは、SharePointグループに関連付Yammerされます。</span><span class="sxs-lookup"><span data-stu-id="a5259-160">Yammer files stored in SharePoint will be placed the SharePoint site associated with the Yammer group.</span></span> <span data-ttu-id="a5259-161">SharePointグループ サイトは、[サイトとグループ] で説明されている PDL[ロジックSharePoint基づいて作成されます](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md#sharepoint-sites-and-groups)。</span><span class="sxs-lookup"><span data-stu-id="a5259-161">SharePoint group sites are based on PDL logic as outlined in [SharePoint Sites and Groups](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md#sharepoint-sites-and-groups).</span></span>
