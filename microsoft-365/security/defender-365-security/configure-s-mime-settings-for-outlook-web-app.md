---
title: S/MIME 設定を構成する - Exchange Online for Outlook on web
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: c7dee22c-9b5b-425c-91a9-d093204ff84e
ms.collection:
- M365-security-compliance
description: Exchange Online の Outlook on the Web で S/MIME 設定を表示および構成するために Exchange Online 管理者が行う必要がある操作の簡単な説明。
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6eacc6a264682474054d0d3546b831039bee9a0c
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51065371"
---
# <a name="configure-smime-settings-in-exchange-online-for-outlook-on-the-web"></a><span data-ttu-id="4f98a-103">Exchange Online for Outlook on the web で S/MIME 設定を構成する</span><span class="sxs-lookup"><span data-stu-id="4f98a-103">Configure S/MIME settings in Exchange Online for Outlook on the web</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

<span data-ttu-id="4f98a-104">**適用対象**</span><span class="sxs-lookup"><span data-stu-id="4f98a-104">**Applies to**</span></span>
- [<span data-ttu-id="4f98a-105">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="4f98a-105">Exchange Online Protection</span></span>](exchange-online-protection-overview.md)
- [<span data-ttu-id="4f98a-106">Microsoft Defender for Office 365 プラン 1 およびプラン 2</span><span class="sxs-lookup"><span data-stu-id="4f98a-106">Microsoft Defender for Office 365 plan 1 and plan 2</span></span>](defender-for-office-365.md)
- [<span data-ttu-id="4f98a-107">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="4f98a-107">Microsoft 365 Defender</span></span>](../defender/microsoft-365-defender.md)

<span data-ttu-id="4f98a-108">Exchange Online の管理者として、Outlook on the web (以前は Outlook Web App) をセットアップして、S/MIME で保護されたメッセージの送受信を許可できます。</span><span class="sxs-lookup"><span data-stu-id="4f98a-108">As an admin for Exchange Online, you can set up Outlook on the web (formerly known as Outlook Web App) to allow sending and receiving S/MIME-protected messages.</span></span> <span data-ttu-id="4f98a-109">**Get-SmimeConfig コマンドレット** と **Set-SmimeConfig** コマンドレットを使用して、Exchange Online PowerShell でこの機能を表示および管理します。</span><span class="sxs-lookup"><span data-stu-id="4f98a-109">Use the **Get-SmimeConfig** and **Set-SmimeConfig** cmdlets to view and manage this feature in Exchange Online PowerShell.</span></span> <span data-ttu-id="4f98a-110">Exchange Online PowerShell へ接続するには、「[Exchange Online PowerShell に接続する](/powershell/exchange/connect-to-exchange-online-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f98a-110">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).</span></span>

<span data-ttu-id="4f98a-111">構文とパラメーターの詳細については [、「Get-SmimeConfig」](/powershell/module/exchange/get-smimeconfig) および [「Set-SmimeConfig」を参照してください](/powershell/module/exchange/set-smimeconfig)。</span><span class="sxs-lookup"><span data-stu-id="4f98a-111">For detailed syntax and parameter information, see [Get-SmimeConfig](/powershell/module/exchange/get-smimeconfig) and [Set-SmimeConfig](/powershell/module/exchange/set-smimeconfig).</span></span>

## <a name="considerations-for-new-microsoft-edge-chromium-based"></a><span data-ttu-id="4f98a-112">新しい Microsoft Edge (クロム ベース) の考慮事項</span><span class="sxs-lookup"><span data-stu-id="4f98a-112">Considerations for new Microsoft Edge (Chromium-based)</span></span>

<span data-ttu-id="4f98a-113">新しい Microsoft [Edge](https://www.microsoft.com/windows/microsoft-edge) Web ブラウザーで Outlook on the web で S/MIME を使用するには **、ExtensionInstallForcelist** という名前の Microsoft Edge ブラウザー ポリシーを設定して構成し、Microsoft S/MIME 拡張機能を新しい Microsoft Edge にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f98a-113">To use S/MIME in Outlook on the web in the new [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge) web browser, you (or another admin) must set and configure the Microsoft Edge browser policy named **ExtensionInstallForcelist** to install the Microsoft S/MIME extension in the new Microsoft Edge.</span></span> <span data-ttu-id="4f98a-114">ポリシー値はです `maafgiompdekodanheihhgilkjchcakm;https://outlook.office.com/owa/SmimeCrxUpdate.ashx` 。</span><span class="sxs-lookup"><span data-stu-id="4f98a-114">The policy value is `maafgiompdekodanheihhgilkjchcakm;https://outlook.office.com/owa/SmimeCrxUpdate.ashx`.</span></span> <span data-ttu-id="4f98a-115">また、このポリシーを適用するには、ドメインに参加しているデバイスまたは Azure AD に参加しているデバイスが必要なので、新しい Microsoft Edge ブラウザーで S/MIME を使用するには、ドメインに参加しているデバイスまたは Azure AD に参加しているデバイスが効果的に必要です。</span><span class="sxs-lookup"><span data-stu-id="4f98a-115">And note that applying this policy requires domain-joined or Azure AD-joined devices, so using S/MIME in the new Microsoft Edge browser effectively requires domain-joined or Azure AD-joined devices.</span></span>

<span data-ttu-id="4f98a-116">**ExtensionInstallForcelist ポリシーの詳細については**[、「ExtensionInstallForcelist」を参照してください](/DeployEdge/microsoft-edge-policies#extensioninstallforcelist)。</span><span class="sxs-lookup"><span data-stu-id="4f98a-116">For details about the **ExtensionInstallForcelist** policy, see [ExtensionInstallForcelist](/DeployEdge/microsoft-edge-policies#extensioninstallforcelist).</span></span>

<span data-ttu-id="4f98a-117">この手順は、新しい Microsoft Edge を使用する前提条件です。ユーザーがインストールした S/MIME コントロールは置き換えされません。</span><span class="sxs-lookup"><span data-stu-id="4f98a-117">This step is a prerequisite for using new Microsoft Edge; it does not replace the S/MIME control that's installed by users.</span></span> <span data-ttu-id="4f98a-118">ユーザーは、S/MIME の最初の使用時に Outlook on the web で S/MIME コントロールをダウンロードしてインストールするように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f98a-118">Users are prompted to download and install the S/MIME control in Outlook on the web during their first use of S/MIME.</span></span> <span data-ttu-id="4f98a-119">または、ユーザーは Outlook on the Web 設定で積極的に **S/MIME** に移動して、コントロールのダウンロード リンクを取得できます。</span><span class="sxs-lookup"><span data-stu-id="4f98a-119">Or, users can proactively go to **S/MIME** in their Outlook on the web settings to get the download link for the control.</span></span>

## <a name="considerations-for-chrome"></a><span data-ttu-id="4f98a-120">Chrome の考慮事項</span><span class="sxs-lookup"><span data-stu-id="4f98a-120">Considerations for Chrome</span></span>

<span data-ttu-id="4f98a-121">Google Chrome Web ブラウザーの Outlook on the web で S/MIME を使用するには、Chrome に Microsoft S/MIME 拡張機能をインストールするように **ExtensionInstallForcelist** という名前のクロム ポリシーを設定および構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f98a-121">To use S/MIME in Outlook on the web in the Google Chrome web browser, you (or another admin) must set and configure the Chromium policy named **ExtensionInstallForcelist** to install the Microsoft S/MIME extension in Chrome.</span></span> <span data-ttu-id="4f98a-122">ポリシー値はです `maafgiompdekodanheihhgilkjchcakm;https://outlook.office.com/owa/SmimeCrxUpdate.ashx` 。</span><span class="sxs-lookup"><span data-stu-id="4f98a-122">The policy value is `maafgiompdekodanheihhgilkjchcakm;https://outlook.office.com/owa/SmimeCrxUpdate.ashx`.</span></span> <span data-ttu-id="4f98a-123">また、このポリシーを適用するにはドメインに参加しているコンピューターが必要なので、Chrome で S/MIME を使用するには、ドメインに参加しているコンピューターが効果的に必要です。</span><span class="sxs-lookup"><span data-stu-id="4f98a-123">And note that applying this policy requires domain-joined computers, so using S/MIME in Chrome effectively requires domain-joined computers.</span></span>

<span data-ttu-id="4f98a-124">**ExtensionInstallForcelist ポリシーの詳細については**[、「ExtensionInstallForcelist」を参照してください](https://cloud.google.com/docs/chrome-enterprise/policies/?policy=ExtensionInstallForcelist)。</span><span class="sxs-lookup"><span data-stu-id="4f98a-124">For details about the **ExtensionInstallForcelist** policy, see [ExtensionInstallForcelist](https://cloud.google.com/docs/chrome-enterprise/policies/?policy=ExtensionInstallForcelist).</span></span>

<span data-ttu-id="4f98a-125">この手順は、Chrome を使用する前提条件です。ユーザーがインストールした S/MIME コントロールは置き換えされません。</span><span class="sxs-lookup"><span data-stu-id="4f98a-125">This step is a prerequisite for using Chrome; it does not replace the S/MIME control that's installed by users.</span></span> <span data-ttu-id="4f98a-126">ユーザーは、S/MIME の最初の使用時に Outlook on the web で S/MIME コントロールをダウンロードしてインストールするように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f98a-126">Users are prompted to download and install the S/MIME control in Outlook on the web during their first use of S/MIME.</span></span> <span data-ttu-id="4f98a-127">または、ユーザーは Outlook on the Web 設定で積極的に **S/MIME** に移動して、コントロールのダウンロード リンクを取得できます。</span><span class="sxs-lookup"><span data-stu-id="4f98a-127">Or, users can proactively go to **S/MIME** in their Outlook on the web settings to get the download link for the control.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="4f98a-128">詳細情報</span><span class="sxs-lookup"><span data-stu-id="4f98a-128">For more information</span></span>

[<span data-ttu-id="4f98a-129">S/MIME によるメッセージの署名と暗号化</span><span class="sxs-lookup"><span data-stu-id="4f98a-129">S/MIME for message signing and encryption</span></span>](s-mime-for-message-signing-and-encryption.md)