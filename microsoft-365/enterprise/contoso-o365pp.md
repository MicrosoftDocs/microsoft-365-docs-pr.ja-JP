---
title: Contoso 社の Microsoft 365 Apps for enterprise の展開
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: Contoso 社が Microsoft Endpoint Configuration Manager を使用して Microsoft 365 Apps for enterprise を展開する方法について説明します。
ms.openlocfilehash: 71958b2e87882e478a852db1f906f61207837854
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "50907676"
---
# <a name="microsoft-365-apps-for-enterprise-deployment-for-contoso"></a><span data-ttu-id="4b954-103">Contoso 社の Microsoft 365 Apps for enterprise の展開</span><span class="sxs-lookup"><span data-stu-id="4b954-103">Microsoft 365 Apps for enterprise deployment for Contoso</span></span>

<span data-ttu-id="4b954-104">Contoso 社は、Pc を Windows 10 Enterprise および Microsoft 365 Apps for enterprise にアップグレードし、より効果的なコラボレーション、より優れたセキュリティ、よりモダンなデスクトップ エクスペリエンスを実現しました。</span><span class="sxs-lookup"><span data-stu-id="4b954-104">Contoso upgraded their PCs to Windows 10 Enterprise and Microsoft 365 Apps for enterprise to enable more effective collaboration, better security, and a more modern desktop experience.</span></span> <span data-ttu-id="4b954-105">インフラストラクチャとビジネス ニーズを評価した後、Contoso 社は展開に関する次の重要な要件を特定しました。</span><span class="sxs-lookup"><span data-stu-id="4b954-105">After they assessed their infrastructure and business needs, Contoso identified these key requirements for the deployment:</span></span>

- <span data-ttu-id="4b954-106">すべての PC で Microsoft 365 Apps for enterprise を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b954-106">All PCs should run Microsoft 365 Apps for enterprise.</span></span>
- <span data-ttu-id="4b954-107">展開では、可能な場合は既存の管理ツールとインフラストラクチャを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b954-107">Deployment should use existing management tools and infrastructure when possible.</span></span>
- <span data-ttu-id="4b954-108">展開では、ユーザーのデバイスで複数の言語と既存のアーキテクチャをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b954-108">Deployment must support multiple languages and existing architectures on users' devices.</span></span>
- <span data-ttu-id="4b954-109">PC は、IT 管理コストを最小限に抑え、ユーザーに与える影響を最小限に抑え、最新のセキュリティを維持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b954-109">PCs should stay up-to-date and secure with minimal IT administrative costs and minimal impact to users.</span></span>

## <a name="deployment-tools"></a><span data-ttu-id="4b954-110">展開ツール</span><span class="sxs-lookup"><span data-stu-id="4b954-110">Deployment tools</span></span>

<span data-ttu-id="4b954-111">Contoso 社は、要件に基づいて、Configuration Manager (Current Branch) を通じて Windows 10 Enterprise および Microsoft 365 Apps for enterprise を展開することを選択しました。</span><span class="sxs-lookup"><span data-stu-id="4b954-111">Based on their requirements, Contoso chose to deploy Windows 10 Enterprise and Microsoft 365 Apps for enterprise through Configuration Manager (Current Branch).</span></span> <span data-ttu-id="4b954-112">Configuration Manager は、大規模な環境向けに調整されていて、インストール、更新、設定についての詳細な制御を実現します。</span><span class="sxs-lookup"><span data-stu-id="4b954-112">Configuration Manager scales for large environments and provides extensive control over installation, updates, and settings.</span></span> <span data-ttu-id="4b954-113">さらに、次に示す組み込みの機能により、Office の展開および管理が簡単で効率的になります。</span><span class="sxs-lookup"><span data-stu-id="4b954-113">It also has built-in features to make it easier and more efficient to deploy and manage Office, including:</span></span>

- <span data-ttu-id="4b954-114">ピア キャッシュ: リモートの場所のデバイスに展開する際にネットワーク容量が制限される場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4b954-114">Peer cache, which can help with limited network capacity when deploying to devices in remote locations.</span></span>
- <span data-ttu-id="4b954-115">クライアントOffice管理ダッシュボードを使用すると、更新プログラムの展開と監視が容易Office、管理者は最新の展開および管理機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="4b954-115">The Office Client Management dashboard, which makes it easy to deploy Office and monitor updates and gives administrators access to the latest deployment and management features.</span></span>
- <span data-ttu-id="4b954-116">オペレーティング システムと同じ言語を自動的に展開するなどのインテリジェントな言語パックの展開。</span><span class="sxs-lookup"><span data-stu-id="4b954-116">Intelligent language pack deployment, including automatically deploying the same language as the operating system.</span></span>
- <span data-ttu-id="4b954-117">展開中にクライアントから既存のバージョンのファイルを削除する完全にサポートされ、使いやすいOffice方法です。</span><span class="sxs-lookup"><span data-stu-id="4b954-117">A fully supported and easy-to-use method of removing existing versions of Office from a client during deployment.</span></span>

<span data-ttu-id="4b954-118">Configuration Manager に加えて、Contoso 社は Office アドインの準備 Toolkit と [、Microsoft](/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps)の無料ツールである VBA を使用して、Office マクロとアドインとの互換性の問題を評価しました。</span><span class="sxs-lookup"><span data-stu-id="4b954-118">In addition to Configuration Manager, Contoso used the [Readiness Toolkit for Office add-ins and VBA](/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps), a free tool from Microsoft, to assess compatibility issues with their Office macros and add-ins.</span></span>

## <a name="managing-deployment-and-updates"></a><span data-ttu-id="4b954-119">展開と更新プログラムの管理</span><span class="sxs-lookup"><span data-stu-id="4b954-119">Managing deployment and updates</span></span>

<span data-ttu-id="4b954-120">Microsoft 365 Apps for enterprise には、サービスとしての新しいOfficeモデルがあります。</span><span class="sxs-lookup"><span data-stu-id="4b954-120">Microsoft 365 Apps for enterprise has a new release model: Office as a service.</span></span> <span data-ttu-id="4b954-121">サービス モデルを使用すると、新しい機能を簡単に最新の情報に更新できます。</span><span class="sxs-lookup"><span data-stu-id="4b954-121">The service model makes it easy to stay up to date with new features.</span></span> <span data-ttu-id="4b954-122">しかし、多くの場合、IT 部門は新しいリリースの展開方法とテスト方法を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b954-122">But it often requires IT departments to change how they deploy and test new releases.</span></span> <span data-ttu-id="4b954-123">互換性の問題を最小限に抑え、コンピューターを最新の情報に保つには、次の 2 つのOffice展開しました。</span><span class="sxs-lookup"><span data-stu-id="4b954-123">To minimize compatibility issues and to ensure their computers stay up to date, Contoso deployed Windows and Office in two stages:</span></span>

- <span data-ttu-id="4b954-124">最初に、Microsoft 365 Apps for enterprise を組織全体の一部の代表的なデバイスに展開しました。</span><span class="sxs-lookup"><span data-stu-id="4b954-124">First, they deployed Microsoft 365 Apps for enterprise to a small set of representative devices across the organization.</span></span> <span data-ttu-id="4b954-125">このパイロット グループは、Microsoft 365 Apps for enterprise でアプリ、アドイン、ハードウェアをテストするために使用しました。</span><span class="sxs-lookup"><span data-stu-id="4b954-125">This pilot group was used to test apps, add-ins, and hardware with Microsoft 365 Apps for enterprise.</span></span>
- <span data-ttu-id="4b954-126">4 か月後、パイロット グループのアプリ、アドイン、ハードウェアに関する重要な問題を解決した後、Contoso 社では Microsoft 365 Apps for enterprise を組織内の残り (広範グループ) のデバイスに展開しました。</span><span class="sxs-lookup"><span data-stu-id="4b954-126">Four months later, after addressing all critical issues with apps, add-ins, and hardware in the pilot group, Contoso deployed Microsoft 365 Apps for enterprise to the rest of the devices in the organization (the broad group).</span></span>

<span data-ttu-id="4b954-127">Contoso 社は、Configuration Manager を使用してOffice更新プログラムを管理する代わりに、クラウドからの自動更新を有効にしました。</span><span class="sxs-lookup"><span data-stu-id="4b954-127">Instead of managing updates to Office by using Configuration Manager, Contoso enabled automatic updates from the cloud.</span></span> <span data-ttu-id="4b954-128">クラウドベースの更新プログラムを使用すると、管理上のオーバーヘッドが軽減され、デバイスが最新の情報に更新されます。</span><span class="sxs-lookup"><span data-stu-id="4b954-128">Cloud-based updates reduce administrative overhead while ensuring that devices stay up to date.</span></span>

<span data-ttu-id="4b954-129">Contoso は、Office の展開に使用した機能更新プログラムと同じ 2 段階のアプローチに従いました。パイロット グループ内のデバイスは、組織の他のデバイス (広範なグループ) よりも 4 か月前に機能更新プログラムを受け取りました。</span><span class="sxs-lookup"><span data-stu-id="4b954-129">Contoso followed the same two-stage approach for feature updates as they used for deploying Office: Devices in the pilot group received feature updates four months earlier than devices in the rest of the organization (the broad group).</span></span> <span data-ttu-id="4b954-130">これを Office で可能にするために、Contoso 社では 2 つの推奨される[更新チャネル](/DeployOffice/overview-update-channels)を使用しました。</span><span class="sxs-lookup"><span data-stu-id="4b954-130">To enable this for Office, Contoso used two recommended [update channels](/DeployOffice/overview-update-channels):</span></span>

- <span data-ttu-id="4b954-131">パイロット グループへの更新向け半期エンタープライズ チャネル (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="4b954-131">Semi-Annual Enterprise Channel (Preview) for updates to the pilot group</span></span>
- <span data-ttu-id="4b954-132">Semi-Annualグループの更新プログラムをエンタープライズ チャネルに追加する</span><span class="sxs-lookup"><span data-stu-id="4b954-132">Semi-Annual Enterprise Channel for updates to the broad group</span></span>

<span data-ttu-id="4b954-133">エンタープライズ チャネル (プレビュー) は半期エンタープライズ チャネルよりも 4 か月早いバージョンの Microsoft 365 Apps for enterprise をリリースするため、Contoso 社は更新プログラムを管理する必要なしに、それらを検証する時間があります。</span><span class="sxs-lookup"><span data-stu-id="4b954-133">Because the Semi-Annual Enterprise Channel (Preview) releases a version of Microsoft 365 Apps for enterprise four months earlier than the Semi-Annual Enterprise Channel, Contoso has time to validate the updates without having to manage them.</span></span>

## <a name="deployment-process"></a><span data-ttu-id="4b954-134">展開プロセス</span><span class="sxs-lookup"><span data-stu-id="4b954-134">Deployment process</span></span>

<span data-ttu-id="4b954-135">Office の展開を完了するために、Contoso 社では Microsoft のベスト プラクティスの推奨事項を含む次のプロセスを実装しました。</span><span class="sxs-lookup"><span data-stu-id="4b954-135">To complete the deployment of Office, Contoso implemented the following process, which includes best practice recommendations from Microsoft:</span></span>

1. <span data-ttu-id="4b954-136">展開の前に、Contoso は Office アドインと VBA の準備 Toolkit を使用してアプリと Office アドインをテストし、Microsoft 365 Apps for enterprise との互換性を評価しました。</span><span class="sxs-lookup"><span data-stu-id="4b954-136">Before deployment, Contoso used the Readiness Toolkit for Office add-in and VBA to test their apps and Office Add-ins to assess their compatibility with Microsoft 365 Apps for enterprise.</span></span>
1. <span data-ttu-id="4b954-137">Configuration Manager では、クライアント デバイスでピア キャッシュを有効にし、リモートの場所にクライアント デバイスを展開する際のネットワーク容量の制限に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4b954-137">In Configuration Manager, they enabled peer cache on their client devices, which helps with limited network capacity when deploying to client devices in remote locations.</span></span> 
1. <span data-ttu-id="4b954-138">Contoso 社は、Configuration Manager で 2 つの展開グループをデバイス コレクションとして定義しました。パイロット グループと広範なグループ。</span><span class="sxs-lookup"><span data-stu-id="4b954-138">Contoso defined two deployment groups as device collections in Configuration Manager: a pilot group and a broad group.</span></span> <span data-ttu-id="4b954-139">組織全体の代表的なデバイスの小さなセットを含むパイロット グループは、Windows 10 Enterprise および Microsoft 365 Apps for enterprise を使用したアプリ、アドイン、ハードウェアの追加テストに使用されました。</span><span class="sxs-lookup"><span data-stu-id="4b954-139">The pilot group, which included a small set of representative devices across the organization, was used for additional testing of apps, add-ins, and hardware with Windows 10 Enterprise and Microsoft 365 Apps for enterprise.</span></span>
1. <span data-ttu-id="4b954-140">Office クライアント管理ダッシュボードと Office 365 インストーラー ウィザード (どちらも Configuration Manager コンソールの一部) を使用して、Office 用の展開パッケージを作成しました。</span><span class="sxs-lookup"><span data-stu-id="4b954-140">They created deployment packages for Office by using the Office Client Management dashboard and the Office 365 Installer wizard, which are both part of the Configuration Manager console.</span></span> <span data-ttu-id="4b954-141">エンタープライズ パッケージ用の Microsoft 365 Apps を 2 つ構築しました。1 つは Semi-Annual エンタープライズ チャネル (プレビュー) のパイロット グループ用、1 つは Semi-Annual Enterprise チャネルの広範なグループ用です。</span><span class="sxs-lookup"><span data-stu-id="4b954-141">They built two Microsoft 365 Apps for enterprise packages, one for the pilot group on the Semi-Annual Enterprise Channel (Preview) and one for the broad group on the Semi-Annual Enterprise Channel.</span></span>
2. <span data-ttu-id="4b954-142">各Officeには、英語、フランス語、ドイツ語の言語パックが含まれていました。</span><span class="sxs-lookup"><span data-stu-id="4b954-142">Each Office package included English, French, and German Language packs.</span></span> <span data-ttu-id="4b954-143">デバイスで、Office パッケージに含まれていない言語が必要な場合、その言語パックは Office コンテンツ配信ネットワーク (CDN) から自動的にダウンロードされました。</span><span class="sxs-lookup"><span data-stu-id="4b954-143">If a device required a language that wasn't included in the Office package, that language pack was automatically downloaded from the Office Content Delivery Network (CDN).</span></span>
3. <span data-ttu-id="4b954-144">Office パッケージの組み込み機能を使用して、Microsoft 365 Apps for enterprise のインストール前に既存の MSI バージョンの Office をすべて自動的に削除しました。</span><span class="sxs-lookup"><span data-stu-id="4b954-144">They used the built-in feature in the Office package to automatically remove all existing MSI versions of Office before installing Microsoft 365 Apps for enterprise.</span></span>
4. <span data-ttu-id="4b954-145">Configuration Manager では、ネットワーク全体の配布ポイントに Windows Officeパッケージを展開しました。</span><span class="sxs-lookup"><span data-stu-id="4b954-145">In Configuration Manager, they deployed the Windows and Office packages to distribution points across their network.</span></span> <span data-ttu-id="4b954-146">次に、Configuration Manager 展開タスク シーケンスを実行して、パイロット Microsoft 365 Apps for enterprise パッケージをパイロット グループに展開しました。</span><span class="sxs-lookup"><span data-stu-id="4b954-146">Then they ran the Configuration Manager deployment task sequences to deploy the pilot Microsoft 365 Apps for enterprise package to the pilot group.</span></span>
5. <span data-ttu-id="4b954-147">パイロット グループとの互換性の問題に対処した後、Contoso はタスク シーケンスを実行して、Microsoft 365 Apps for enterprise パッケージを広範なグループに展開しました。</span><span class="sxs-lookup"><span data-stu-id="4b954-147">After they addressed compatibility issues with the pilot group, Contoso ran the task sequences to deploy the Microsoft 365 Apps for enterprise package to the broad group.</span></span>

<span data-ttu-id="4b954-148">Contoso 社ではクラウドからデバイスを自動的に更新するよう選択しているため、Configuration Manger でプロセスを管理する必要はありませんでした。</span><span class="sxs-lookup"><span data-stu-id="4b954-148">Because Contoso chose to automatically update devices from the cloud, there was no need to manage the process in Configuration Manager.</span></span> <span data-ttu-id="4b954-149">デバイスは、最初の展開で定義された更新チャネルに基づいて、クラウドベースから直接自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="4b954-149">Their devices are automatically updated directly from the cloud-based on the update channel that was defined in the initial deployment.</span></span>

<span data-ttu-id="4b954-150">Contoso Microsoft 365 Apps for enterprise インストールと継続的な更新プログラムの展開アーキテクチャを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4b954-150">Here is the Contoso Microsoft 365 Apps for enterprise installation and ongoing updates deployment architecture.</span></span>

![エンタープライズ向け Microsoft 365 Apps の Contoso 展開インフラストラクチャ](../media/contoso-o365pp/contoso-o365pp-fig1.png)
 
## <a name="next-step"></a><span data-ttu-id="4b954-152">次の手順</span><span class="sxs-lookup"><span data-stu-id="4b954-152">Next step</span></span>

<span data-ttu-id="4b954-153">Contoso 社が Microsoft 365 for enterprise で [Microsoft Intune](contoso-mdm.md) を使用してデバイスと組織全体で実行するアプリを管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b954-153">Learn how Contoso is [using Microsoft Intune](contoso-mdm.md) in Microsoft 365 for enterprise to manage its devices and the apps that they run across the organization.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b954-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b954-154">See also</span></span>

[<span data-ttu-id="4b954-155">Microsoft 365 Apps for enterprise</span><span class="sxs-lookup"><span data-stu-id="4b954-155">Microsoft 365 Apps for enterprise</span></span>](/deployoffice/deployment-guide-microsoft-365-apps)

[<span data-ttu-id="4b954-156">Microsoft 365 for enterprise の概要</span><span class="sxs-lookup"><span data-stu-id="4b954-156">Microsoft 365 for enterprise overview</span></span>](microsoft-365-overview.md)

[<span data-ttu-id="4b954-157">テスト ラボ ガイド</span><span class="sxs-lookup"><span data-stu-id="4b954-157">Test lab guides</span></span>](m365-enterprise-test-lab-guides.md)