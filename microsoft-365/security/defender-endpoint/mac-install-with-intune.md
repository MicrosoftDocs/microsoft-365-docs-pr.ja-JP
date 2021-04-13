---
title: MacOS での Microsoft Defender for Endpoint の Intune ベースの展開
description: Microsoft Intune を使用して、macOS に Microsoft Defender for Endpoint をインストールします。
keywords: microsoft、 defender, atp, mac, installation, deploy, uninstallation, intune, jamf, macos, catalina, mojave, high sierra
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 7486bde0886506a5966a95cdb0b85fc009858801
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2021
ms.locfileid: "51689751"
---
# <a name="intune-based-deployment-for-microsoft-defender-for-endpoint-on-macos"></a><span data-ttu-id="ed9fe-104">MacOS での Microsoft Defender for Endpoint の Intune ベースの展開</span><span class="sxs-lookup"><span data-stu-id="ed9fe-104">Intune-based deployment for Microsoft Defender for Endpoint on macOS</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


> [!NOTE]
> <span data-ttu-id="ed9fe-105">このドキュメントでは、macOS デバイスで Microsoft Defender for Endpoint を展開および構成するための従来の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-105">This documentation explains the legacy method for deploying and configuring Microsoft Defender for Endpoint on macOS devices.</span></span> <span data-ttu-id="ed9fe-106">ネイティブ エクスペリエンスは MEM コンソールで利用できます。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-106">The native experience is now available in the MEM console.</span></span> <span data-ttu-id="ed9fe-107">MEM コンソールでネイティブ UI をリリースすると、管理者はアプリケーションを構成して展開し、macOS デバイスに送信する方法がはるかに簡単になります。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-107">The release of the native UI in the MEM console provide admins with a much simpler way to configure and deploy the application and send it down to macOS devices.</span></span> <br> <br>
><span data-ttu-id="ed9fe-108">ブログ投稿 [MEM は、Microsoft Defender for Endpoint for macOS](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/microsoft-endpoint-manager-simplifies-deployment-of-microsoft/ba-p/1322995) の展開を簡略化し、新機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-108">The blog post [MEM simplifies deployment of Microsoft Defender for Endpoint for macOS](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/microsoft-endpoint-manager-simplifies-deployment-of-microsoft/ba-p/1322995) explains the new features.</span></span> <span data-ttu-id="ed9fe-109">アプリを構成するには [、「Microsoft InTune](https://docs.microsoft.com/mem/intune/protect/antivirus-microsoft-defender-settings-macos)の macOS 上の Microsoft Defender for Endpoint の設定」に移動します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-109">To configure the app, go to [Settings for Microsoft Defender for Endpoint on macOS in Microsoft InTune](https://docs.microsoft.com/mem/intune/protect/antivirus-microsoft-defender-settings-macos).</span></span> <span data-ttu-id="ed9fe-110">アプリを展開するには、「Microsoft Intune を使用して [Microsoft Defender for Endpoint を macOS デバイスに追加する」に移動します](https://docs.microsoft.com/mem/intune/apps/apps-advanced-threat-protection-macos)。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-110">To deploy the app, go to [Add Microsoft Defender for Endpoint to macOS devices using Microsoft Intune](https://docs.microsoft.com/mem/intune/apps/apps-advanced-threat-protection-macos).</span></span>

<span data-ttu-id="ed9fe-111">**適用対象:**</span><span class="sxs-lookup"><span data-stu-id="ed9fe-111">**Applies to:**</span></span>

- [<span data-ttu-id="ed9fe-112">macOS 上のエンドポイント用 Microsoft Defender</span><span class="sxs-lookup"><span data-stu-id="ed9fe-112">Microsoft Defender for Endpoint on macOS</span></span>](microsoft-defender-endpoint-mac.md)

<span data-ttu-id="ed9fe-113">このトピックでは、Intune を介して macOS に Microsoft Defender for Endpoint を展開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-113">This topic describes how to deploy Microsoft Defender for Endpoint on macOS through Intune.</span></span> <span data-ttu-id="ed9fe-114">展開が成功するには、次のすべての手順を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-114">A successful deployment requires the completion of all of the following steps:</span></span>

1. [<span data-ttu-id="ed9fe-115">インストール パッケージとオンボーディング パッケージのダウンロード</span><span class="sxs-lookup"><span data-stu-id="ed9fe-115">Download installation and onboarding packages</span></span>](#download-installation-and-onboarding-packages)
1. [<span data-ttu-id="ed9fe-116">クライアント デバイスのセットアップ</span><span class="sxs-lookup"><span data-stu-id="ed9fe-116">Client device setup</span></span>](#client-device-setup)
1. [<span data-ttu-id="ed9fe-117">システム拡張機能の承認</span><span class="sxs-lookup"><span data-stu-id="ed9fe-117">Approve system extensions</span></span>](#approve-system-extensions)
1. [<span data-ttu-id="ed9fe-118">システム構成プロファイルの作成</span><span class="sxs-lookup"><span data-stu-id="ed9fe-118">Create System Configuration profiles</span></span>](#create-system-configuration-profiles)
1. [<span data-ttu-id="ed9fe-119">アプリケーションの発行</span><span class="sxs-lookup"><span data-stu-id="ed9fe-119">Publish application</span></span>](#publish-application)

## <a name="prerequisites-and-system-requirements"></a><span data-ttu-id="ed9fe-120">前提条件とシステム要件</span><span class="sxs-lookup"><span data-stu-id="ed9fe-120">Prerequisites and system requirements</span></span>

<span data-ttu-id="ed9fe-121">開始する前に、現在のソフトウェア バージョンの前提条件とシステム要件の説明については、メインの [Microsoft Defender for Endpoint on macOS](microsoft-defender-endpoint-mac.md) ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-121">Before you get started, see [the main Microsoft Defender for Endpoint on macOS page](microsoft-defender-endpoint-mac.md) for a description of prerequisites and system requirements for the current software version.</span></span>

## <a name="overview"></a><span data-ttu-id="ed9fe-122">概要</span><span class="sxs-lookup"><span data-stu-id="ed9fe-122">Overview</span></span>

<span data-ttu-id="ed9fe-123">次の表に、Intune 経由で Microsoft Defender for Endpoint for Mac を展開および管理するために必要な手順を示します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-123">The following table summarizes the steps you would need to take to deploy and manage Microsoft Defender for Endpoint for Macs, via Intune.</span></span> <span data-ttu-id="ed9fe-124">詳細な手順については、以下をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-124">More detailed steps are available below.</span></span>

| <span data-ttu-id="ed9fe-125">手順</span><span class="sxs-lookup"><span data-stu-id="ed9fe-125">Step</span></span> | <span data-ttu-id="ed9fe-126">サンプル ファイル名</span><span class="sxs-lookup"><span data-stu-id="ed9fe-126">Sample file names</span></span> | <span data-ttu-id="ed9fe-127">BundleIdentifier</span><span class="sxs-lookup"><span data-stu-id="ed9fe-127">BundleIdentifier</span></span> |
|-|-|-|
| [<span data-ttu-id="ed9fe-128">インストール パッケージとオンボーディング パッケージのダウンロード</span><span class="sxs-lookup"><span data-stu-id="ed9fe-128">Download installation and onboarding packages</span></span>](#download-installation-and-onboarding-packages) | <span data-ttu-id="ed9fe-129">WindowsDefenderATPOnboarding__MDATP_wdav.atp.xml</span><span class="sxs-lookup"><span data-stu-id="ed9fe-129">WindowsDefenderATPOnboarding__MDATP_wdav.atp.xml</span></span> | <span data-ttu-id="ed9fe-130">com.microsoft.wdav.atp</span><span class="sxs-lookup"><span data-stu-id="ed9fe-130">com.microsoft.wdav.atp</span></span> |
| [<span data-ttu-id="ed9fe-131">エンドポイント用 Microsoft Defender のシステム拡張機能を承認する</span><span class="sxs-lookup"><span data-stu-id="ed9fe-131">Approve System Extension for Microsoft Defender for Endpoint</span></span>](#approve-system-extensions) | <span data-ttu-id="ed9fe-132">MDATP_SysExt.xml</span><span class="sxs-lookup"><span data-stu-id="ed9fe-132">MDATP_SysExt.xml</span></span> | <span data-ttu-id="ed9fe-133">該当なし</span><span class="sxs-lookup"><span data-stu-id="ed9fe-133">N/A</span></span> |
| [<span data-ttu-id="ed9fe-134">Microsoft Defender for Endpoint のカーネル拡張機能の承認</span><span class="sxs-lookup"><span data-stu-id="ed9fe-134">Approve Kernel Extension for Microsoft Defender for Endpoint</span></span>](#download-installation-and-onboarding-packages) | <span data-ttu-id="ed9fe-135">MDATP_KExt.xml</span><span class="sxs-lookup"><span data-stu-id="ed9fe-135">MDATP_KExt.xml</span></span> | <span data-ttu-id="ed9fe-136">該当なし</span><span class="sxs-lookup"><span data-stu-id="ed9fe-136">N/A</span></span> |
| [<span data-ttu-id="ed9fe-137">Microsoft Defender for Endpoint へのフル ディスク アクセスを許可する</span><span class="sxs-lookup"><span data-stu-id="ed9fe-137">Grant full disk access to Microsoft Defender for Endpoint</span></span>](#create-system-configuration-profiles-step-8) | <span data-ttu-id="ed9fe-138">MDATP_tcc_Catalina_or_newer.xml</span><span class="sxs-lookup"><span data-stu-id="ed9fe-138">MDATP_tcc_Catalina_or_newer.xml</span></span> | <span data-ttu-id="ed9fe-139">com.microsoft.wdav.tcc</span><span class="sxs-lookup"><span data-stu-id="ed9fe-139">com.microsoft.wdav.tcc</span></span> |
| [<span data-ttu-id="ed9fe-140">ネットワーク拡張ポリシー</span><span class="sxs-lookup"><span data-stu-id="ed9fe-140">Network Extension policy</span></span>](#create-system-configuration-profiles-step-9) | <span data-ttu-id="ed9fe-141">MDATP_NetExt.xml</span><span class="sxs-lookup"><span data-stu-id="ed9fe-141">MDATP_NetExt.xml</span></span> | <span data-ttu-id="ed9fe-142">該当なし</span><span class="sxs-lookup"><span data-stu-id="ed9fe-142">N/A</span></span> |
| [<span data-ttu-id="ed9fe-143">Microsoft AutoUpdate (MAU) の構成</span><span class="sxs-lookup"><span data-stu-id="ed9fe-143">Configure Microsoft AutoUpdate (MAU)</span></span>](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/mac-updates#intune) | <span data-ttu-id="ed9fe-144">MDATP_Microsoft_AutoUpdate.xml</span><span class="sxs-lookup"><span data-stu-id="ed9fe-144">MDATP_Microsoft_AutoUpdate.xml</span></span> | <span data-ttu-id="ed9fe-145">com.microsoft.autoupdate2</span><span class="sxs-lookup"><span data-stu-id="ed9fe-145">com.microsoft.autoupdate2</span></span> |
| [<span data-ttu-id="ed9fe-146">Microsoft Defender for Endpoint 構成設定</span><span class="sxs-lookup"><span data-stu-id="ed9fe-146">Microsoft Defender for Endpoint configuration settings</span></span>](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/mac-preferences#intune-profile-1)<br/><br/> <span data-ttu-id="ed9fe-147">**注:** macOS 用のサード パーティ製 AV の実行を計画している場合は、 に設定 `passiveMode` します `true` 。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-147">**Note:** If you're planning to run a third-party AV for macOS, set `passiveMode` to `true`.</span></span> | <span data-ttu-id="ed9fe-148">MDATP_WDAV_and_exclusion_settings_Preferences.xml</span><span class="sxs-lookup"><span data-stu-id="ed9fe-148">MDATP_WDAV_and_exclusion_settings_Preferences.xml</span></span> | <span data-ttu-id="ed9fe-149">com.microsoft.wdav</span><span class="sxs-lookup"><span data-stu-id="ed9fe-149">com.microsoft.wdav</span></span> |
| [<span data-ttu-id="ed9fe-150">エンドポイントおよび MS AutoUpdate (MAU) 通知の Microsoft Defender の構成</span><span class="sxs-lookup"><span data-stu-id="ed9fe-150">Configure Microsoft Defender for Endpoint and MS AutoUpdate (MAU) notifications</span></span>](#create-system-configuration-profiles-step-10) | <span data-ttu-id="ed9fe-151">MDATP_MDAV_Tray_and_AutoUpdate2.mobileconfig</span><span class="sxs-lookup"><span data-stu-id="ed9fe-151">MDATP_MDAV_Tray_and_AutoUpdate2.mobileconfig</span></span> | <span data-ttu-id="ed9fe-152">com.microsoft.autoupdate2 または com.microsoft.wdav.tray</span><span class="sxs-lookup"><span data-stu-id="ed9fe-152">com.microsoft.autoupdate2 or com.microsoft.wdav.tray</span></span> |

## <a name="download-installation-and-onboarding-packages"></a><span data-ttu-id="ed9fe-153">インストール パッケージとオンボーディング パッケージのダウンロード</span><span class="sxs-lookup"><span data-stu-id="ed9fe-153">Download installation and onboarding packages</span></span>

<span data-ttu-id="ed9fe-154">Microsoft Defender セキュリティ センターからインストールパッケージとオンボーディング パッケージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-154">Download the installation and onboarding packages from Microsoft Defender Security Center:</span></span>

1. <span data-ttu-id="ed9fe-155">Microsoft Defender セキュリティ センターで、[設定] **[デバイス** 管理  >  **オンボーディング]**  >  **に移動します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-155">In Microsoft Defender Security Center, go to **Settings** > **Device Management** > **Onboarding**.</span></span>

2. <span data-ttu-id="ed9fe-156">オペレーティング システムを **macOS** に設定し、展開方法を **[モバイル デバイス管理] / [Microsoft Intune] に設定します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-156">Set the operating system to **macOS** and the deployment method to **Mobile Device Management / Microsoft Intune**.</span></span>

    ![オンボーディング設定のスクリーンショット](images/atp-mac-install.png)

3. <span data-ttu-id="ed9fe-158">[インストール **パッケージのダウンロード] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-158">Select **Download installation package**.</span></span> <span data-ttu-id="ed9fe-159">_wdav.pkg としてローカル ディレクトリ_ に保存します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-159">Save it as _wdav.pkg_ to a local directory.</span></span>

4. <span data-ttu-id="ed9fe-160">[オンボード **パッケージのダウンロード] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-160">Select **Download onboarding package**.</span></span> <span data-ttu-id="ed9fe-161">同 _じディレクトリWindowsDefenderATPOnboardingPackage.zip_ として保存します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-161">Save it as _WindowsDefenderATPOnboardingPackage.zip_ to the same directory.</span></span>

5. <span data-ttu-id="ed9fe-162">**IntuneAppUtil を** ダウンロードします [https://docs.microsoft.com/intune/lob-apps-macos](https://docs.microsoft.com/intune/lob-apps-macos) 。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-162">Download **IntuneAppUtil** from [https://docs.microsoft.com/intune/lob-apps-macos](https://docs.microsoft.com/intune/lob-apps-macos).</span></span>

6. <span data-ttu-id="ed9fe-163">コマンド プロンプトから、3 つのファイルが存在するように確認します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-163">From a command prompt, verify that you have the three files.</span></span>
  

    ```bash
    ls -l
    ```

    ```Output
    total 721688
    -rw-r--r--  1 test  staff     269280 Mar 15 11:25 IntuneAppUtil
    -rw-r--r--  1 test  staff      11821 Mar 15 09:23 WindowsDefenderATPOnboardingPackage.zip
    -rw-r--r--  1 test  staff  354531845 Mar 13 08:57 wdav.pkg
    ```
7. <span data-ttu-id="ed9fe-164">.zip ファイルの内容を抽出します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-164">Extract the contents of the .zip files:</span></span>

    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```
    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    warning:  WindowsDefenderATPOnboardingPackage.zip appears to use backslashes as path separators
      inflating: intune/kext.xml
      inflating: intune/WindowsDefenderATPOnboarding.xml
      inflating: jamf/WindowsDefenderATPOnboarding.plist
    ```

8. <span data-ttu-id="ed9fe-165">IntuneAppUtil を実行可能にする:</span><span class="sxs-lookup"><span data-stu-id="ed9fe-165">Make IntuneAppUtil an executable:</span></span>

    ```bash
    chmod +x IntuneAppUtil
    ```

9. <span data-ttu-id="ed9fe-166">wdav.pkg から wdav.pkg.intunemac パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-166">Create the wdav.pkg.intunemac package from wdav.pkg:</span></span>

    ```bash
    ./IntuneAppUtil -c wdav.pkg -o . -i "com.microsoft.wdav" -n "1.0.0"
    ```
    ```Output
    Microsoft Intune Application Utility for Mac OS X
    Version: 1.0.0.0
    Copyright 2018 Microsoft Corporation

    Creating intunemac file for /Users/test/Downloads/wdav.pkg
    Composing the intunemac file output
    Output written to ./wdav.pkg.intunemac.

    IntuneAppUtil successfully processed "wdav.pkg",
    to deploy refer to the product documentation.
    ```

## <a name="client-device-setup"></a><span data-ttu-id="ed9fe-167">クライアント デバイスのセットアップ</span><span class="sxs-lookup"><span data-stu-id="ed9fe-167">Client device setup</span></span>

<span data-ttu-id="ed9fe-168">標準のポータル サイトインストールを超えて Mac デバイスに対する特別なプロビジョニング [は必要ない](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp)。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-168">You don't need any special provisioning for a Mac device beyond a standard [Company Portal installation](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp).</span></span>

1. <span data-ttu-id="ed9fe-169">デバイスの管理を確認します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-169">Confirm device management.</span></span>

   ![デバイス管理のスクリーンショットを確認する](images/mdatp-3-confirmdevicemgmt.png)

    <span data-ttu-id="ed9fe-171">[ **システム環境設定を開く]** を選択し、一 **覧で [管理プロファイル** ] を探し、[ **承認...] を選択します**。管理プロファイルが [確認済み] **と表示されます**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-171">Select **Open System Preferences**, locate **Management Profile** on the list, and select **Approve...**. Your Management Profile would be displayed as **Verified**:</span></span>

    ![管理プロファイルのスクリーンショット](images/mdatp-4-managementprofile.png)

2. <span data-ttu-id="ed9fe-173">[続行 **] を** 選択し、登録を完了します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-173">Select **Continue** and complete the enrollment.</span></span>

   <span data-ttu-id="ed9fe-174">これで、より多くのデバイスを登録できます。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-174">You may now enroll more devices.</span></span> <span data-ttu-id="ed9fe-175">システム構成とアプリケーション パッケージのプロビジョニングが完了したら、後で登録することもできます。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-175">You can also enroll them later, after you have finished provisioning system configuration and application packages.</span></span>

3. <span data-ttu-id="ed9fe-176">Intune で、[デバイスの管理 **] [**  >  **すべての**  >  **デバイス] を開きます**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-176">In Intune, open **Manage** > **Devices** > **All devices**.</span></span> <span data-ttu-id="ed9fe-177">ここにリストされているデバイスの中からデバイスを確認できます。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-177">Here you can see your device among those listed:</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="ed9fe-178">![デバイスの追加スクリーンショット](images/mdatp-5-alldevices.png)</span><span class="sxs-lookup"><span data-stu-id="ed9fe-178">![Add Devices screenshot](images/mdatp-5-alldevices.png)</span></span>

## <a name="approve-system-extensions"></a><span data-ttu-id="ed9fe-179">システム拡張機能の承認</span><span class="sxs-lookup"><span data-stu-id="ed9fe-179">Approve System Extensions</span></span>

<span data-ttu-id="ed9fe-180">システム拡張機能を承認するには、次の方法を実行します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-180">To approve the system extensions:</span></span>

1. <span data-ttu-id="ed9fe-181">Intune で、[デバイス構成の **管理**  >  **] を開きます**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-181">In Intune, open **Manage** > **Device configuration**.</span></span> <span data-ttu-id="ed9fe-182">[プロファイル **の**  >  **管理] [プロファイルの**  >  **作成] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-182">Select **Manage** > **Profiles** > **Create Profile**.</span></span>

2. <span data-ttu-id="ed9fe-183">プロファイルの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-183">Choose a name for the profile.</span></span> <span data-ttu-id="ed9fe-184">**Platform=macOS を Profile** **type=Extensions に変更します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-184">Change **Platform=macOS** to **Profile type=Extensions**.</span></span> <span data-ttu-id="ed9fe-185">**[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-185">Select **Create**.</span></span>

3. <span data-ttu-id="ed9fe-186">[基本 **] タブ** で、この新しいプロファイルに名前を付きます。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-186">In the **Basics** tab, give a name to this new profile.</span></span>

4. <span data-ttu-id="ed9fe-187">[構成 **設定] タブ** で、[許可されたシステム拡張機能] セクションに次 **のエントリを追加** します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-187">In the **Configuration settings** tab, add the following entries in the **Allowed system extensions** section:</span></span>

    <span data-ttu-id="ed9fe-188">バンドル識別子</span><span class="sxs-lookup"><span data-stu-id="ed9fe-188">Bundle identifier</span></span>         | <span data-ttu-id="ed9fe-189">チーム識別子</span><span class="sxs-lookup"><span data-stu-id="ed9fe-189">Team identifier</span></span>
    --------------------------|----------------
    <span data-ttu-id="ed9fe-190">com.microsoft.wdav.epsext</span><span class="sxs-lookup"><span data-stu-id="ed9fe-190">com.microsoft.wdav.epsext</span></span> | <span data-ttu-id="ed9fe-191">UBF8T346G9</span><span class="sxs-lookup"><span data-stu-id="ed9fe-191">UBF8T346G9</span></span>
    <span data-ttu-id="ed9fe-192">com.microsoft.wdav.netext</span><span class="sxs-lookup"><span data-stu-id="ed9fe-192">com.microsoft.wdav.netext</span></span> | <span data-ttu-id="ed9fe-193">UBF8T346G9</span><span class="sxs-lookup"><span data-stu-id="ed9fe-193">UBF8T346G9</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="ed9fe-194">![[基本] タブの [構成設定] の拡張機能設定のスクリーンショット](images/mac-system-extension-intune2.png)</span><span class="sxs-lookup"><span data-stu-id="ed9fe-194">![Screenshot of the extension settings in Configuration settings on the Basics tab](images/mac-system-extension-intune2.png)</span></span>

5. <span data-ttu-id="ed9fe-195">[割り **当て] タブ** で、このプロファイルを [すべてのユーザー] または **[すべての&に割り当てる] をクリックします**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-195">In the **Assignments** tab, assign this profile to **All Users & All devices**.</span></span>

6. <span data-ttu-id="ed9fe-196">この構成プロファイルを確認して作成します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-196">Review and create this configuration profile.</span></span>

## <a name="create-system-configuration-profiles"></a><span data-ttu-id="ed9fe-197">システム構成プロファイルの作成</span><span class="sxs-lookup"><span data-stu-id="ed9fe-197">Create System Configuration profiles</span></span>

1. <span data-ttu-id="ed9fe-198">Intune で、[デバイス構成の **管理**  >  **] を開きます**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-198">In Intune, open **Manage** > **Device configuration**.</span></span> <span data-ttu-id="ed9fe-199">[プロファイル **の**  >  **管理] [プロファイルの**  >  **作成] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-199">Select **Manage** > **Profiles** > **Create Profile**.</span></span>

2. <span data-ttu-id="ed9fe-200">プロファイルの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-200">Choose a name for the profile.</span></span> <span data-ttu-id="ed9fe-201">**Platform=macOS をプロファイル\*\*\*\*の種類=カスタム に変更します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-201">Change **Platform=macOS** to **Profile type=Custom**.</span></span> <span data-ttu-id="ed9fe-202">[構成 **] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-202">Select **Configure**.</span></span>

3. <span data-ttu-id="ed9fe-203">構成プロファイルを開き、intune/kext.xml。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-203">Open the configuration profile and upload intune/kext.xml.</span></span> <span data-ttu-id="ed9fe-204">このファイルは、前のセクションの 1 つで作成されました。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-204">This file was created in one of the preceding sections.</span></span>

4. <span data-ttu-id="ed9fe-205">**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-205">Select **OK**.</span></span>

    ![カスタム構成プロファイルのファイルから構成をインポートする](images/mdatp-6-systemconfigurationprofiles.png)

5. <span data-ttu-id="ed9fe-207">[割 **り当**  >  **ての管理] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-207">Select **Manage** > **Assignments**.</span></span> <span data-ttu-id="ed9fe-208">[含める **] タブ** で、[すべてのユーザーに割り当てる] & **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-208">In the **Include** tab, select **Assign to All Users & All devices**.</span></span>

6. <span data-ttu-id="ed9fe-209">その他のプロファイルについては、手順 1 ~ 5 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-209">Repeat steps 1 through 5 for more profiles.</span></span>

7. <span data-ttu-id="ed9fe-210">別のプロファイルを作成し、名前を付け、intune/WindowsDefenderATPOnboarding.xmlファイルをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-210">Create another profile, give it a name, and upload the intune/WindowsDefenderATPOnboarding.xml file.</span></span>

8. <span data-ttu-id="ed9fe-211">**GitHub リポジトリから fulldisk.mobileconfig** を [ダウンロードし](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)、そのリポジトリ **としてtcc.xml。**</span><span class="sxs-lookup"><span data-stu-id="ed9fe-211">Download **fulldisk.mobileconfig** from [our GitHub repository](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) and save it as **tcc.xml**.</span></span> <span data-ttu-id="ed9fe-212">別のプロファイルを作成し、任意の名前を付け、このファイルをアップロードします。<a name="create-system-configuration-profiles-step-8" id = "create-system-configuration-profiles-step-8"></a></span><span class="sxs-lookup"><span data-stu-id="ed9fe-212">Create another profile, give it any name and upload this file to it.<a name="create-system-configuration-profiles-step-8" id = "create-system-configuration-profiles-step-8"></a></span></span>

   > [!CAUTION]
   > <span data-ttu-id="ed9fe-213">macOS 10.15 (Catalina) には、新しいセキュリティとプライバシーの強化が含まれている。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-213">macOS 10.15 (Catalina) contains new security and privacy enhancements.</span></span> <span data-ttu-id="ed9fe-214">このバージョンでは、既定では、アプリケーションは明示的な同意なしにディスク上の特定の場所 (ドキュメント、ダウンロード、デスクトップなど) にアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-214">Beginning with this version, by default, applications are not able to access certain locations on disk (such as Documents, Downloads, Desktop, etc.) without explicit consent.</span></span> <span data-ttu-id="ed9fe-215">この同意がない場合、Microsoft Defender for Endpoint はデバイスを完全に保護できません。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-215">In the absence of this consent, Microsoft Defender for Endpoint is not able to fully protect your device.</span></span>
   >
   > <span data-ttu-id="ed9fe-216">この構成プロファイルは、エンドポイント用 Microsoft Defender へのフル ディスク アクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-216">This configuration profile grants Full Disk Access to Microsoft Defender for Endpoint.</span></span> <span data-ttu-id="ed9fe-217">以前に Intune を使用して Microsoft Defender for Endpoint を構成した場合は、この構成プロファイルを使用して展開を更新することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-217">If you previously configured Microsoft Defender for Endpoint through Intune, we recommend you update the deployment with this configuration profile.</span></span>

9. <span data-ttu-id="ed9fe-218">エンドポイント検出および応答機能の一環として、macOS 上の Microsoft Defender for Endpoint はソケット トラフィックを検査し、この情報を Microsoft Defender セキュリティ センター ポータルに報告します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-218">As part of the Endpoint Detection and Response capabilities, Microsoft Defender for Endpoint on macOS inspects socket traffic and reports this information to the Microsoft Defender Security Center portal.</span></span> <span data-ttu-id="ed9fe-219">次のポリシーでは、ネットワーク拡張機能でこの機能を実行できます。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-219">The following policy allows the network extension to perform this functionality.</span></span> <span data-ttu-id="ed9fe-220">[GitHub](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/netfilter.mobileconfig)リポジトリから **netfilter.mobileconfig** をダウンロードし、netext.xmlとして保存し、前のセクションと同じ手順で展開します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-220">Download **netfilter.mobileconfig** from [our GitHub repository](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/netfilter.mobileconfig), save it as netext.xml and deploy it using the same steps as in the previous sections.</span></span> <a name = "create-system-configuration-profiles-step-9" id = "create-system-configuration-profiles-step-9"></a>

10. <span data-ttu-id="ed9fe-221">microsoft Defender for Endpoint on macOS および Microsoft Auto Update が macOS 10.15 (Catalina) の UI に通知を表示するには `notif.mobileconfig` [、GitHub](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/notif.mobileconfig) リポジトリからダウンロードし、カスタム ペイロードとしてインポートします。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-221">To allow Microsoft Defender for Endpoint on macOS and Microsoft Auto Update to display notifications in UI on macOS 10.15 (Catalina), download `notif.mobileconfig` from [our GitHub repository](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/notif.mobileconfig) and import it as a custom payload.</span></span> <a name = "create-system-configuration-profiles-step-10" id = "create-system-configuration-profiles-step-10"></a>

11. <span data-ttu-id="ed9fe-222">[ **割り当ての>する] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-222">Select **Manage > Assignments**.</span></span>  <span data-ttu-id="ed9fe-223">[含める **] タブ** で、[すべてのユーザーに割り当てる] & **を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-223">In the **Include** tab, select **Assign to All Users & All devices**.</span></span>

<span data-ttu-id="ed9fe-224">Intune の変更が登録済みデバイスに反映された後は、[デバイスの状態の監視]の下に表示  >  **されます**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-224">Once the Intune changes are propagated to the enrolled devices, you can see them listed under **Monitor** > **Device status**:</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="ed9fe-225">![モニターでのデバイスの状態の表示](images/mdatp-7-devicestatusblade.png)</span><span class="sxs-lookup"><span data-stu-id="ed9fe-225">![View of Device Status in Monitor](images/mdatp-7-devicestatusblade.png)</span></span>

## <a name="publish-application"></a><span data-ttu-id="ed9fe-226">アプリケーションの発行</span><span class="sxs-lookup"><span data-stu-id="ed9fe-226">Publish application</span></span>

1. <span data-ttu-id="ed9fe-227">Intune で、[クライアント アプリの **管理] ブレード>開** きます。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-227">In Intune, open the **Manage > Client apps** blade.</span></span> <span data-ttu-id="ed9fe-228">[アプリ **と追加>を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-228">Select **Apps > Add**.</span></span>

2. <span data-ttu-id="ed9fe-229">[ **アプリの種類]=[その他]/[Line-of-business アプリ]を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-229">Select **App type=Other/Line-of-business app**.</span></span>

3. <span data-ttu-id="ed9fe-230">**file=wdav.pkg.intunemac を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-230">Select **file=wdav.pkg.intunemac**.</span></span> <span data-ttu-id="ed9fe-231">**[OK] を選択** してアップロードします。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-231">Select **OK** to upload.</span></span>

4. <span data-ttu-id="ed9fe-232">[構成 **] を** 選択し、必要な情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-232">Select **Configure** and add the required information.</span></span>

5. <span data-ttu-id="ed9fe-233">**最小 OS として macOS High Sierra 10.14** を使用します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-233">Use **macOS High Sierra 10.14** as the minimum OS.</span></span>

6. <span data-ttu-id="ed9fe-234">[アプリ *のバージョンを無視する] を* [はい] **に設定します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-234">Set *Ignore app version* to **Yes**.</span></span> <span data-ttu-id="ed9fe-235">その他の設定には任意の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-235">Other settings can be any arbitrary value.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="ed9fe-236">[ *アプリのバージョンを無視する* ] **を [いいえ** ] に設定すると、アプリケーションが Microsoft AutoUpdate を通じて更新プログラムを受け取る機能に影響します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-236">Setting *Ignore app version* to **No** impacts the ability of the application to receive updates through Microsoft AutoUpdate.</span></span> <span data-ttu-id="ed9fe-237">製品 [の更新方法の詳細については、「MacOS](mac-updates.md) での Microsoft Defender for Endpoint の更新プログラムの展開」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-237">See [Deploy updates for Microsoft Defender for Endpoint on macOS](mac-updates.md) for additional information about how the product is updated.</span></span>
    >
    > <span data-ttu-id="ed9fe-238">Intune によってアップロードされたバージョンがデバイスのバージョンより低い場合は、下位バージョンがインストールされ、Microsoft Defender for Endpoint が効果的にダウングレードされます。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-238">If the version uploaded by Intune is lower than the version on the device, then the lower version will be installed, effectively downgrading Microsoft Defender for Endpoint.</span></span> <span data-ttu-id="ed9fe-239">これにより、機能しないアプリケーションが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-239">This could result in a non-functioning application.</span></span> <span data-ttu-id="ed9fe-240">製品 [の更新方法の詳細については、「MacOS](mac-updates.md) での Microsoft Defender for Endpoint の更新プログラムの展開」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-240">See [Deploy updates for Microsoft Defender for Endpoint on macOS](mac-updates.md) for additional information about how the product is updated.</span></span> <span data-ttu-id="ed9fe-241">[アプリのバージョンを無視する] が [いいえ] に設定 *されている* Microsoft Defender for Endpoint を展開した場合 **は、[は** い] に変更 **してください**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-241">If you deployed Microsoft Defender for Endpoint with *Ignore app version* set to **No**, please change it to **Yes**.</span></span> <span data-ttu-id="ed9fe-242">Microsoft Defender for Endpoint がまだクライアント デバイスにインストールできない場合は、Microsoft Defender for Endpoint をアンインストールし、更新されたポリシーをプッシュします。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-242">If Microsoft Defender for Endpoint still cannot be installed on a client device, then uninstall Microsoft Defender for Endpoint and push the updated policy.</span></span>
     
    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="ed9fe-243">![アプリの追加でのアプリ情報の表示](images/mdatp-8-intuneappinfo.png)</span><span class="sxs-lookup"><span data-stu-id="ed9fe-243">![Display of App information in App add](images/mdatp-8-intuneappinfo.png)</span></span>

7. <span data-ttu-id="ed9fe-244">**[OK] と [** 追加]**を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-244">Select **OK** and **Add**.</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="ed9fe-245">![[通知] ウィンドウに表示されるデバイスの状態](images/mdatp-9-intunepkginfo.png)</span><span class="sxs-lookup"><span data-stu-id="ed9fe-245">![Device status shown in Notifications window](images/mdatp-9-intunepkginfo.png)</span></span>

8. <span data-ttu-id="ed9fe-246">パッケージのアップロードに少し時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-246">It may take a few moments to upload the package.</span></span> <span data-ttu-id="ed9fe-247">完了したら、一覧からパッケージを選択し、[割り当て] と [ **グループの追加** ] **に移動します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-247">After it's done, select the package from the list and go to **Assignments** and **Add group**.</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="ed9fe-248">![クライアント アプリのスクリーンショット](images/mdatp-10-clientapps.png)</span><span class="sxs-lookup"><span data-stu-id="ed9fe-248">![Client apps screenshot](images/mdatp-10-clientapps.png)</span></span>

9. <span data-ttu-id="ed9fe-249">[割 **り当ての種類] を [** 必須] **に変更します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-249">Change **Assignment type** to **Required**.</span></span>

10. <span data-ttu-id="ed9fe-250">[含 **まれるグループ] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-250">Select **Included Groups**.</span></span> <span data-ttu-id="ed9fe-251">[すべての **デバイスにこのアプリを必須にする]=[はい]を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-251">Select **Make this app required for all devices=Yes**.</span></span> <span data-ttu-id="ed9fe-252">[ **グループの選択] を選択** して、対象とするユーザーを含むグループを追加します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-252">Select **Select group to include** and add a group that contains the users you want to target.</span></span> <span data-ttu-id="ed9fe-253">**[OK] と [** 保存]**を選択します**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-253">Select **OK** and **Save**.</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="ed9fe-254">![Intune の割り当て情報のスクリーンショット](images/mdatp-11-assignments.png)</span><span class="sxs-lookup"><span data-stu-id="ed9fe-254">![Intune assignments info screenshot](images/mdatp-11-assignments.png)</span></span>

11. <span data-ttu-id="ed9fe-255">しばらくすると、アプリケーションは登録済みのすべてのデバイスに公開されます。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-255">After some time the application will be published to all enrolled devices.</span></span> <span data-ttu-id="ed9fe-256">[デバイスの監視] の [**デバイスのインストール** 状態]  >  **に表示されます**。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-256">You can see it listed in **Monitor** > **Device**, under **Device install status**:</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="ed9fe-257">![Intune デバイスの状態のスクリーンショット](images/mdatp-12-deviceinstall.png)</span><span class="sxs-lookup"><span data-stu-id="ed9fe-257">![Intune device status screenshot](images/mdatp-12-deviceinstall.png)</span></span>

## <a name="verify-client-device-state"></a><span data-ttu-id="ed9fe-258">クライアント デバイスの状態を確認する</span><span class="sxs-lookup"><span data-stu-id="ed9fe-258">Verify client device state</span></span>

1. <span data-ttu-id="ed9fe-259">構成プロファイルをデバイスに展開した後、Mac デバイス **で [System Preferences**  >  **Profiles]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-259">After the configuration profiles are deployed to your devices, open **System Preferences** > **Profiles** on your Mac device.</span></span>

    <span data-ttu-id="ed9fe-260">![System Preferences のスクリーンショット](images/mdatp-13-systempreferences.png)</span><span class="sxs-lookup"><span data-stu-id="ed9fe-260">![System Preferences screenshot](images/mdatp-13-systempreferences.png)</span></span><br/>
    <span data-ttu-id="ed9fe-261">![System Preferences Profiles スクリーンショット](images/mdatp-14-systempreferencesprofiles.png)</span><span class="sxs-lookup"><span data-stu-id="ed9fe-261">![System Preferences Profiles screenshot](images/mdatp-14-systempreferencesprofiles.png)</span></span>

2. <span data-ttu-id="ed9fe-262">次の構成プロファイルが存在し、インストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-262">Verify that the following configuration profiles are present and installed.</span></span> <span data-ttu-id="ed9fe-263">管理 **プロファイルは** Intune システム プロファイルである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-263">The **Management Profile** should be the Intune system profile.</span></span> <span data-ttu-id="ed9fe-264">_Wdav-config_ と _wdav-kext_ は、Intune で追加されたシステム構成プロファイルです。 ![ プロファイルのスクリーンショット](images/mdatp-15-managementprofileconfig.png)</span><span class="sxs-lookup"><span data-stu-id="ed9fe-264">_Wdav-config_ and _wdav-kext_ are system configuration profiles that were added in Intune: ![Profiles screenshot](images/mdatp-15-managementprofileconfig.png)</span></span>

3. <span data-ttu-id="ed9fe-265">右上隅に Microsoft Defender アイコンも表示されます。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-265">You should also see the Microsoft Defender icon in the top-right corner:</span></span>

    > [!div class="mx-imgBorder"]
    > <span data-ttu-id="ed9fe-266">![ステータス バーのスクリーンショットの Microsoft Defender アイコン](images/mdatp-icon-bar.png)</span><span class="sxs-lookup"><span data-stu-id="ed9fe-266">![Microsoft Defender icon in status bar screenshot](images/mdatp-icon-bar.png)</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="ed9fe-267">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ed9fe-267">Troubleshooting</span></span>

<span data-ttu-id="ed9fe-268">問題: ライセンスが見つかりません</span><span class="sxs-lookup"><span data-stu-id="ed9fe-268">Issue: No license found</span></span>

<span data-ttu-id="ed9fe-269">解決策: 上記の手順に従って、デバイス プロファイルを作成しますWindowsDefenderATPOnboarding.xml</span><span class="sxs-lookup"><span data-stu-id="ed9fe-269">Solution: Follow the steps above to create a device profile using WindowsDefenderATPOnboarding.xml</span></span>

## <a name="logging-installation-issues"></a><span data-ttu-id="ed9fe-270">インストールの問題をログに記録する</span><span class="sxs-lookup"><span data-stu-id="ed9fe-270">Logging installation issues</span></span>

<span data-ttu-id="ed9fe-271">エラーが発生した場合にインストーラーによって作成される自動的に生成されたログを検索する方法の詳細については、「Logging [installation issues」を参照してください](mac-resources.md#logging-installation-issues)。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-271">For more information on how to find the automatically generated log that is created by the installer when an error occurs, see [Logging installation issues](mac-resources.md#logging-installation-issues).</span></span>

## <a name="uninstallation"></a><span data-ttu-id="ed9fe-272">アンインストール</span><span class="sxs-lookup"><span data-stu-id="ed9fe-272">Uninstallation</span></span>

<span data-ttu-id="ed9fe-273">クライアント デバイス [から](mac-resources.md#uninstalling) macOS 上の Microsoft Defender for Endpoint を削除する方法の詳細については、「アンインストール」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed9fe-273">See [Uninstalling](mac-resources.md#uninstalling) for details on how to remove Microsoft Defender for Endpoint on macOS from client devices.</span></span>
