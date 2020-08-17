---
title: Office 365 コンテンツ配信ネットワーク (CDN) クイックスタート
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 06/04/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
description: Office 365 コンテンツ配信ネットワーク (CDN) クイックスタート
ms.openlocfilehash: 8a8152c749306ed5247e92d4bc2c6a58e7a1c6cd
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46696178"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a><span data-ttu-id="e99f9-103">Office 365 コンテンツ配信ネットワーク (CDN) クイックスタート</span><span class="sxs-lookup"><span data-stu-id="e99f9-103">Office 365 Content Delivery Network (CDN) Quickstart</span></span>

<span data-ttu-id="e99f9-104">組み込みの **Office 365 コンテンツ配信ネットワーク (CDN)** を使用して、静的なアセット (画像、JavaScript、スタイルシート、woff ファイル) をホストし、SharePoint Online ページのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="e99f9-104">You can use the built-in **Office 365 Content Delivery Network (CDN)** to host static assets (images, JavaScript, Stylesheets, WOFF files) to provide better performance for your SharePoint Online pages.</span></span> <span data-ttu-id="e99f9-105">Office 365 CDN では、静的資産を要求しているブラウザーの近くに静的資産をキャッシュするとパフォーマンスが向上します。これにより、ダウンロードが速くなり、待ち時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="e99f9-105">The Office 365 CDN improves performance by caching static assets closer to the browsers requesting them, which helps to speed up downloads and reduce latency.</span></span> <span data-ttu-id="e99f9-106">また、Office 365 CDN は、強化された圧縮と HTTP パイプライン処理に HTTP/2 プロトコルを使用します。</span><span class="sxs-lookup"><span data-stu-id="e99f9-106">Also, the Office 365 CDN uses the HTTP/2 protocol for improved compression and HTTP pipelining.</span></span> <span data-ttu-id="e99f9-107">Office 365 CDN サービスは、SharePoint Online サブスクリプションの一部として含まれます。</span><span class="sxs-lookup"><span data-stu-id="e99f9-107">The Office 365 CDN service is included as part of your SharePoint Online subscription.</span></span>

<span data-ttu-id="e99f9-108">詳細については [、「SharePoint Online で Office 365 コンテンツ配信ネットワーク (CDN) を使用する](use-microsoft-365-cdn-with-spo.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e99f9-108">For more detailed information guidance see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-microsoft-365-cdn-with-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="e99f9-109">Office 365 CDN は、運用環境 (世界規模) のクラウドのテナントでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e99f9-109">The Office 365 CDN is only available to tenants in the production (worldwide) cloud.</span></span> <span data-ttu-id="e99f9-110">米国政府機関のテナント、中国およびドイツのクラウドでは、現在 Office 365 CDN をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e99f9-110">Tenants in the US Government, China and Germany clouds do not currently support the Office 365 CDN.</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a><span data-ttu-id="e99f9-111">SharePoint 用ページ診断ツールを使用して CDN に含まれていないアイテムを識別する</span><span class="sxs-lookup"><span data-stu-id="e99f9-111">Use the Page Diagnostics for SharePoint tool to identify items not in CDN</span></span>

<span data-ttu-id="e99f9-112">SharePoint ツールブラウザー拡張機能 **のページ診断** を使用して、CDN の配信元に追加できる sharepoint Online ページのアセットを簡単に一覧表示できます。</span><span class="sxs-lookup"><span data-stu-id="e99f9-112">You can use the **Page Diagnostics for SharePoint tool** browser extension to easily list assets in your SharePoint Online pages that can be added to a CDN origin.</span></span>

<span data-ttu-id="e99f9-113">**Sharepoint 用ページ診断ツール**は、新しい Microsoft Edge ( https://www.microsoft.com/edge) および sharepoint Online モダンポータルと従来の発行サイトページの両方を分析する Chrome ブラウザー) 用のブラウザー拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="e99f9-113">The **Page Diagnostics for SharePoint tool** is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="e99f9-114">このツールでは、定義されている一連のパフォーマンス条件に対するページのパフォーマンスを示す分析済みの各ページのレポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e99f9-114">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="e99f9-115">SharePoint 用ページ診断ツールのインストール方法と詳細については、「[SharePoint Online 用ページ診断ツールを使用する](https://aka.ms/perftool)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e99f9-115">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](https://aka.ms/perftool).</span></span>

<span data-ttu-id="e99f9-116">SharePoint Online ページで SharePoint ツールのページ診断ツールを実行すると、[ **診断テスト** ] タブをクリックして、CDN によってホストされていないアセットの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="e99f9-116">When you run the Page Diagnostics for SharePoint tool on a SharePoint Online page, you can click the **Diagnostic Tests** tab to see a list of assets not being hosted by the CDN.</span></span> <span data-ttu-id="e99f9-117">これらのアセットは、以下のスクリーンショットに示されているように、[見出し **コンテンツ配信ネットワーク (CDN)] チェック** の下に一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="e99f9-117">These assets will be listed under the heading **Content Delivery Network (CDN) check** as shown in the screenshot below.</span></span>

![ページ診断](../media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
><span data-ttu-id="e99f9-119">ページ診断ツールは SharePoint Online でのみ機能し、SharePoint システム ページでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="e99f9-119">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

## <a name="cdn-overview"></a><span data-ttu-id="e99f9-120">CDN の概要</span><span class="sxs-lookup"><span data-stu-id="e99f9-120">CDN Overview</span></span>

<span data-ttu-id="e99f9-121">Office 365 CDN は、画像や javascript ファイルなど、頻繁にアクセスされるオブジェクトを高速なグローバルネットワーク経由で分散することによって、ユーザーのパフォーマンスを最適化するように設計されています。これにより、ページの読み込み時間が短縮され、ホストされたオブジェクトへのアクセスがユーザーにできるだけ近づけることができます。</span><span class="sxs-lookup"><span data-stu-id="e99f9-121">The Office 365 CDN is designed to optimize performance for users by distributing frequently accessed objects like images and javascript files over a high-speed global network, reducing page load time and providing access to hosted objects as close as possible to the user.</span></span> <span data-ttu-id="e99f9-122">CDN は、 _送信元_と呼ばれる場所からアセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="e99f9-122">The CDN fetches your assets from a location called an _origin_.</span></span> <span data-ttu-id="e99f9-123">起点として、URL でアクセスできる SharePoint サイト、ドキュメントライブラリ、またはフォルダーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e99f9-123">An origin can be a SharePoint site, document library or folder that is accessible by a URL.</span></span>

<span data-ttu-id="e99f9-124">Office 365 CDN は、次の2つの基本的な種類に分けられます。</span><span class="sxs-lookup"><span data-stu-id="e99f9-124">The Office 365 CDN is separated into two basic types:</span></span>

- <span data-ttu-id="e99f9-125">**パブリック CDN** は、JS (JavaScript)、CSS (スタイルシート)、Web フォントファイル (woff、WOFF2)、会社のロゴなどの非所有の画像に使用するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="e99f9-125">**Public CDN** is designed to be used for JS (JavaScript), CSS (StyleSheets), Web Font File (WOFF, WOFF2) and non-proprietary images like company logos.</span></span>
- <span data-ttu-id="e99f9-126">**プライベート CDN** は、画像 (PNG、JPG、JPEG など) に使用するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="e99f9-126">**Private CDN** is designed to be used for images (PNG, JPG, JPEG, etc.).</span></span>

<span data-ttu-id="e99f9-127">組織にパブリックまたはプライベートのどちらを使用するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="e99f9-127">You can choose to have both public or private origins for your organization.</span></span> <span data-ttu-id="e99f9-128">大部分の組織では、2つの組み合わせを実装することを選択します。</span><span class="sxs-lookup"><span data-stu-id="e99f9-128">Most organizations will choose to implement a combination of the two.</span></span> <span data-ttu-id="e99f9-129">パブリックおよびプライベートのどちらのオプションもパフォーマンスの向上に似ていますが、それぞれに固有の属性と利点があります。</span><span class="sxs-lookup"><span data-stu-id="e99f9-129">Both public and private options provide similar performance gains, but each has unique attributes and advantages.</span></span> <span data-ttu-id="e99f9-130">パブリックおよびプライベート CDN オリジンの詳細については、「 [各配信元をパブリックまたはプライベートにする必要があるかどうかを選択](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e99f9-130">For more information about public and private CDN origins, see [Choose whether each origin should be public or private](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span></span>

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a><span data-ttu-id="e99f9-131">既定の構成を使用してパブリック CDN とプライベート CDN を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="e99f9-131">How to enable Public and Private CDN with the default configuration</span></span>
<span data-ttu-id="e99f9-132">テナントの CDN 設定に変更を加える前に、組織のコンプライアンス、セキュリティ、プライバシーポリシーを満たしていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e99f9-132">Before you make changes to the tenant CDN settings, you should verify that it meets compliance, security and privacy policies of your organization.</span></span>

<span data-ttu-id="e99f9-133">構成設定の詳細については、または既に CDN を有効にしていて、別の場所 (出所) を追加する場合は、「 [SharePoint Online 管理シェルを使用して Office 365 CDN をセットアップおよび構成](use-microsoft-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e99f9-133">For more detailed configuration settings, or if you have already enabled CDN and want to add additional locations (origins), please see the section [Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell](use-microsoft-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell)</span></span>

<span data-ttu-id="e99f9-134">SharePoint Online 管理シェルを使用して、テナントに接続します。</span><span class="sxs-lookup"><span data-stu-id="e99f9-134">Connect to your tenant using the SharePoint Online Management Shell:</span></span>

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

<span data-ttu-id="e99f9-135">既定の構成でパブリックとプライベートの両方のオリジンを組織で使用できるようにするには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="e99f9-135">To enable your organization to use both public and private origins with the default configuration, type the following command:</span></span>

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="e99f9-136">これらのコマンドレットの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e99f9-136">Output of these cmdlets should look like the following:</span></span>

![SPOTenantCdnEnabled の出力](../media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a><span data-ttu-id="e99f9-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="e99f9-138">See also</span></span>

[<span data-ttu-id="e99f9-139">SharePoint Online のページ診断ツールを使用する</span><span class="sxs-lookup"><span data-stu-id="e99f9-139">Use the Page Diagnostics tool for SharePoint Online</span></span>](https://aka.ms/perftool)

[<span data-ttu-id="e99f9-140">SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用</span><span class="sxs-lookup"><span data-stu-id="e99f9-140">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-microsoft-365-cdn-with-spo.md)

[<span data-ttu-id="e99f9-141">Content Delivery Network</span><span class="sxs-lookup"><span data-stu-id="e99f9-141">Content Delivery Networks</span></span>](https://aka.ms/o365cdns)

[<span data-ttu-id="e99f9-142">Office 365 のネットワーク計画とパフォーマンス チューニング</span><span class="sxs-lookup"><span data-stu-id="e99f9-142">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

[<span data-ttu-id="e99f9-143">SharePoint パフォーマンスシリーズ-Office 365 CDN ビデオシリーズ</span><span class="sxs-lookup"><span data-stu-id="e99f9-143">SharePoint Performance Series - Office 365 CDN video series</span></span>](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)