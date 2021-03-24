---
title: iOS 機能用に Microsoft Defender ATP を構成する
description: iOS 機能用に Microsoft Defender ATP を展開する方法について説明します。
keywords: microsoft、 defender, atp, ios, configure, features, ios
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 8b9f4372321bfa17ce5c11081ca274a3360e18dd
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51064276"
---
# <a name="configure-microsoft-defender-for-endpoint-for-ios-features"></a><span data-ttu-id="5e8bf-104">iOS 機能用に Microsoft Defender for Endpoint を構成する</span><span class="sxs-lookup"><span data-stu-id="5e8bf-104">Configure Microsoft Defender for Endpoint for iOS features</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

<span data-ttu-id="5e8bf-105">**適用対象:**</span><span class="sxs-lookup"><span data-stu-id="5e8bf-105">**Applies to:**</span></span>
- [<span data-ttu-id="5e8bf-106">Microsoft Defender for Endpoint</span><span class="sxs-lookup"><span data-stu-id="5e8bf-106">Microsoft Defender for Endpoint</span></span>](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [<span data-ttu-id="5e8bf-107">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="5e8bf-107">Microsoft 365 Defender</span></span>](https://go.microsoft.com/fwlink/?linkid=2118804)

> <span data-ttu-id="5e8bf-108">Defender for Endpoint を体験してみませんか?</span><span class="sxs-lookup"><span data-stu-id="5e8bf-108">Want to experience Defender for Endpoint?</span></span> [<span data-ttu-id="5e8bf-109">無料試用版にサインアップします。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-109">Sign up for a free trial.</span></span>](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

> [!NOTE]
> <span data-ttu-id="5e8bf-110">IOS 用エンドポイントの Defender は、Web Protection 機能を提供するために VPN を使用します。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-110">Defender for Endpoint for iOS would use a VPN in order to provide the Web Protection feature.</span></span> <span data-ttu-id="5e8bf-111">これは通常の VPN ではなく、デバイス外のトラフィックを受け取らないローカル/自己ループ VPN です。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-111">This is not a regular VPN and is a local/self-looping VPN that does not take traffic outside the device.</span></span>

## <a name="conditional-access-with-defender-for-endpoint-for-ios"></a><span data-ttu-id="5e8bf-112">iOS 用エンドポイントの Defender を使用した条件付きアクセス</span><span class="sxs-lookup"><span data-stu-id="5e8bf-112">Conditional Access with Defender for Endpoint for iOS</span></span>  
<span data-ttu-id="5e8bf-113">Microsoft Defender for Endpoint for iOS および Microsoft Intune および Azure Active Directory を使用すると、デバイスのリスク レベルに基づいてデバイスコンプライアンスと条件付きアクセス ポリシーを適用できます。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-113">Microsoft Defender for Endpoint for iOS along with Microsoft Intune and Azure Active Directory enables enforcing Device compliance and Conditional Access policies based on device risk levels.</span></span> <span data-ttu-id="5e8bf-114">Defender for Endpoint は、Intune を介してこの機能を活用するために展開できるモバイル脅威防御 (MTD) ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-114">Defender for Endpoint is a Mobile Threat Defense (MTD) solution that you can deploy to leverage this capability via Intune.</span></span>

<span data-ttu-id="5e8bf-115">IOS 用 Defender for Endpoint を使用して条件付きアクセスを設定する方法の詳細については [、「Defender for Endpoint and Intune」を参照してください](https://docs.microsoft.com/mem/intune/protect/advanced-threat-protection)。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-115">For more information about how to set up Conditional Access with Defender for Endpoint for iOS, see [Defender for Endpoint and Intune](https://docs.microsoft.com/mem/intune/protect/advanced-threat-protection).</span></span>

## <a name="web-protection-and-vpn"></a><span data-ttu-id="5e8bf-116">Web 保護と VPN</span><span class="sxs-lookup"><span data-stu-id="5e8bf-116">Web Protection and VPN</span></span>

<span data-ttu-id="5e8bf-117">既定では、Defender for Endpoint for iOS には Web 保護機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-117">By default, Defender for Endpoint for iOS includes and enables the web protection feature.</span></span> <span data-ttu-id="5e8bf-118">[Web 保護は](web-protection-overview.md) 、Web の脅威からデバイスを保護し、ユーザーをフィッシング攻撃から保護するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-118">[Web protection](web-protection-overview.md) helps to secure devices against web threats and protect users from phishing attacks.</span></span> <span data-ttu-id="5e8bf-119">IOS 用エンドポイントの Defender は、この保護を提供するために VPN を使用します。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-119">Defender for Endpoint for iOS uses a VPN in order to provide this protection.</span></span> <span data-ttu-id="5e8bf-120">これはローカル VPN であり、従来の VPN とは異なり、ネットワーク トラフィックはデバイスの外部に送信されません。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-120">Please note this is a local VPN and unlike traditional VPN, network traffic is not sent outside the device.</span></span>

<span data-ttu-id="5e8bf-121">既定で有効になっている場合は、VPN を無効にする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-121">While enabled by default, there might be some cases that require you to disable VPN.</span></span> <span data-ttu-id="5e8bf-122">たとえば、VPN が構成されているときに動作しないアプリを実行する場合です。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-122">For example, you want to run some apps that do not work when a VPN is configured.</span></span> <span data-ttu-id="5e8bf-123">このような場合は、次の手順に従って、デバイス上のアプリから VPN を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-123">In such cases, you can choose to disable VPN from the app on the device by following the steps below:</span></span>

1. <span data-ttu-id="5e8bf-124">iOS デバイスで、[設定]**アプリを開** き、[全般] をクリックまたはタップ **し\*\*\*\*、[VPN] をタップします**。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-124">On your iOS device, open the **Settings** app, click or tap **General** and then **VPN**.</span></span>
1. <span data-ttu-id="5e8bf-125">Microsoft Defender ATP の [i] ボタンをクリックまたはタップします。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-125">Click or tap the "i" button for Microsoft Defender ATP.</span></span>
1. <span data-ttu-id="5e8bf-126">[オンデマンド接続 **] をオフにして** VPN を無効にします。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-126">Toggle off **Connect On Demand** to disable VPN.</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="5e8bf-127">![VPN 構成はオンデマンドで接続します](images/ios-vpn-config.png)</span><span class="sxs-lookup"><span data-stu-id="5e8bf-127">![VPN config connect on demand](images/ios-vpn-config.png)</span></span>

> [!NOTE]
> <span data-ttu-id="5e8bf-128">VPN が無効になっている場合、Web 保護は使用できません。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-128">Web Protection will not be available when VPN is disabled.</span></span> <span data-ttu-id="5e8bf-129">Web Protection を再び有効にするには、デバイスで Microsoft Defender for Endpoint アプリを開き、[VPN の開始] をクリックまたは **タップします**。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-129">To re-enable Web Protection, open the Microsoft Defender for Endpoint app on the device and click or tap **Start VPN**.</span></span>

## <a name="co-existence-of-multiple-vpn-profiles"></a><span data-ttu-id="5e8bf-130">複数の VPN プロファイルの共存在</span><span class="sxs-lookup"><span data-stu-id="5e8bf-130">Co-existence of multiple VPN profiles</span></span>

<span data-ttu-id="5e8bf-131">Apple iOS では、同時にアクティブになる複数のデバイス全体の VPN はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-131">Apple iOS does not support multiple device-wide VPNs to be active simultaneously.</span></span> <span data-ttu-id="5e8bf-132">デバイスに複数の VPN プロファイルを存在することができますが、一度にアクティブにできる VPN は 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-132">While multiple VPN profiles can exist on the device, only one VPN can be active at a time.</span></span>


## <a name="configure-compliance-policy-against-jailbroken-devices"></a><span data-ttu-id="5e8bf-133">脱獄されたデバイスに対するコンプライアンス ポリシーの構成</span><span class="sxs-lookup"><span data-stu-id="5e8bf-133">Configure compliance policy against jailbroken devices</span></span>

<span data-ttu-id="5e8bf-134">企業データが脱獄された iOS デバイスでアクセスされるのを保護するには、Intune で次のコンプライアンス ポリシーを設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-134">To protect corporate data from being accessed on jailbroken iOS devices, we recommend that you set up the following compliance policy on Intune.</span></span>

> [!NOTE]
> <span data-ttu-id="5e8bf-135">現時点では、Microsoft Defender for Endpoint for iOS は脱獄シナリオに対する保護を提供しません。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-135">At this time Microsoft Defender for Endpoint for iOS does not provide protection against jailbreak scenarios.</span></span> <span data-ttu-id="5e8bf-136">脱獄されたデバイスで使用する場合、特定のシナリオで、企業の電子メール ID や企業プロファイル画像 (利用可能な場合) など、アプリケーションで使用されるデータをローカルで公開できます</span><span class="sxs-lookup"><span data-stu-id="5e8bf-136">If used on a jailbroken device, then in specific scenarios data that is used by the application like your corporate email id and corporate profile picture (if available) can be exposed locally</span></span>

<span data-ttu-id="5e8bf-137">以下の手順に従って、脱獄されたデバイスに対するコンプライアンス ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-137">Follow the steps below to create a compliance policy against jailbroken devices.</span></span>

1. <span data-ttu-id="5e8bf-138">[Microsoft Endpoint Manager 管理センターで、[](https://go.microsoft.com/fwlink/?linkid=2109431)デバイス コンプライアンス ポリシー  ->  **の作成ポリシー**  ->  **] に移動します**。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-138">In [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** -> **Compliance policies** -> **Create Policy**.</span></span> <span data-ttu-id="5e8bf-139">プラットフォームとして [iOS/iPadOS] を選択し、[作成] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-139">Select "iOS/iPadOS" as platform and click **Create**.</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="5e8bf-140">![ポリシーの作成](images/ios-jb-policy.png)</span><span class="sxs-lookup"><span data-stu-id="5e8bf-140">![Create Policy](images/ios-jb-policy.png)</span></span>

2. <span data-ttu-id="5e8bf-141">ポリシーの名前を指定します 。たとえば、「脱獄のコンプライアンス ポリシー」などです。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-141">Specify a name of the policy, for example "Compliance Policy for Jailbreak".</span></span>
3. <span data-ttu-id="5e8bf-142">[コンプライアンス設定] ページで、[デバイスの正常性] セクションをクリック **し、[脱** 獄デバイスのブロック **] フィールドをクリック** します。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-142">In the compliance settings page, click to expand **Device Health** section and click **Block** for **Jailbroken devices** field.</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="5e8bf-143">![ポリシー設定](images/ios-jb-settings.png)</span><span class="sxs-lookup"><span data-stu-id="5e8bf-143">![Policy Settings](images/ios-jb-settings.png)</span></span>

4. <span data-ttu-id="5e8bf-144">[非 *準拠のアクション] セクションで* 、要件に従ってアクションを選択し、[次へ] を選択 **します**。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-144">In the *Action for noncompliance* section, select the actions as per your requirements and select **Next**.</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="5e8bf-145">![ポリシーアクション](images/ios-jb-actions.png)</span><span class="sxs-lookup"><span data-stu-id="5e8bf-145">![Policy Actions](images/ios-jb-actions.png)</span></span>

5. <span data-ttu-id="5e8bf-146">[割 *り当て* ] セクションで、このポリシーに含めるユーザー グループを選択し、[次へ] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-146">In the *Assignments* section, select the user groups that you want to include for this policy and then select **Next**.</span></span>
6. <span data-ttu-id="5e8bf-147">[レビュー **+ 作成] セクション** で、入力した情報が正しいか確認し、[作成] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-147">In the **Review+Create** section, verify that all the information entered is correct and then select **Create**.</span></span>

## <a name="configure-custom-indicators"></a><span data-ttu-id="5e8bf-148">カスタム インジケーターの構成</span><span class="sxs-lookup"><span data-stu-id="5e8bf-148">Configure custom indicators</span></span>

<span data-ttu-id="5e8bf-149">Defender for Endpoint for iOS を使用すると、管理者は iOS デバイスでもカスタム インジケーターを構成できます。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-149">Defender for Endpoint for iOS enables admins to configure custom indicators on iOS devices as well.</span></span> <span data-ttu-id="5e8bf-150">カスタム インジケーターを構成する方法の詳細については、「指標の管理」 [を参照してください](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/manage-indicators)。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-150">For more information on how to configure custom indicators, see [Manage indicators](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/manage-indicators).</span></span>

> [!NOTE]
> <span data-ttu-id="5e8bf-151">Defender for Endpoint for iOS では、IP アドレスと URL/ドメインのカスタム インジケーターの作成のみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-151">Defender for Endpoint for iOS supports creating custom indicators only for IP addresses and URLs/domains.</span></span>

## <a name="report-unsafe-site"></a><span data-ttu-id="5e8bf-152">安全でないサイトを報告する</span><span class="sxs-lookup"><span data-stu-id="5e8bf-152">Report unsafe site</span></span>

<span data-ttu-id="5e8bf-153">フィッシング Web サイトは、お客様の個人情報または財務情報を取得する目的で信頼できる Web サイトになりすます。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-153">Phishing websites impersonate trustworthy websites for the purpose of obtaining your personal or financial information.</span></span> <span data-ttu-id="5e8bf-154">フィッシング サイト [の可能性がある Web サイトを報告](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) する場合は、[ネットワーク保護に関するフィードバックを提供する] ページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5e8bf-154">Visit the [Provide feedback about network protection](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) page if you want to report a website that could be a phishing site.</span></span>