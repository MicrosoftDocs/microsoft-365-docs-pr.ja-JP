---
title: Linux での Microsoft Defender for Endpoint の手動展開
ms.reviewer: ''
description: コマンド ラインから手動で Microsoft Defender for Endpoint を Linux に展開する方法について説明します。
keywords: microsoft、 defender, atp, linux, installation, deploy, uninstallation, puppet, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 2beb46c62de2e9720d1626e0e1e5ce806a6d7e19
ms.sourcegitcommit: 13ce4b31303a1a21ca53700a54bcf8d91ad2f8c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2021
ms.locfileid: "51903918"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-manually"></a><span data-ttu-id="7c73e-104">Linux での Microsoft Defender for Endpoint の手動展開</span><span class="sxs-lookup"><span data-stu-id="7c73e-104">Deploy Microsoft Defender for Endpoint on Linux manually</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


<span data-ttu-id="7c73e-105">**適用対象:**</span><span class="sxs-lookup"><span data-stu-id="7c73e-105">**Applies to:**</span></span>
- [<span data-ttu-id="7c73e-106">Microsoft Defender for Endpoint</span><span class="sxs-lookup"><span data-stu-id="7c73e-106">Microsoft Defender for Endpoint</span></span>](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [<span data-ttu-id="7c73e-107">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="7c73e-107">Microsoft 365 Defender</span></span>](https://go.microsoft.com/fwlink/?linkid=2118804)

> <span data-ttu-id="7c73e-108">Defender for Endpoint を体験してみませんか?</span><span class="sxs-lookup"><span data-stu-id="7c73e-108">Want to experience Defender for Endpoint?</span></span> [<span data-ttu-id="7c73e-109">無料試用版にサインアップしてください。</span><span class="sxs-lookup"><span data-stu-id="7c73e-109">Sign up for a free trial.</span></span>](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-investigateip-abovefoldlink)

<span data-ttu-id="7c73e-110">この記事では、Microsoft Defender for Endpoint を Linux に手動で展開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-110">This article describes how to deploy Microsoft Defender for Endpoint on Linux manually.</span></span> <span data-ttu-id="7c73e-111">展開が成功するには、次のすべてのタスクを完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c73e-111">A successful deployment requires the completion of all of the following tasks:</span></span>

- [<span data-ttu-id="7c73e-112">Linux での Microsoft Defender for Endpoint の手動展開</span><span class="sxs-lookup"><span data-stu-id="7c73e-112">Deploy Microsoft Defender for Endpoint on Linux manually</span></span>](#deploy-microsoft-defender-for-endpoint-on-linux-manually)
  - [<span data-ttu-id="7c73e-113">前提条件とシステム要件</span><span class="sxs-lookup"><span data-stu-id="7c73e-113">Prerequisites and system requirements</span></span>](#prerequisites-and-system-requirements)
  - [<span data-ttu-id="7c73e-114">Linux ソフトウェア リポジトリの構成</span><span class="sxs-lookup"><span data-stu-id="7c73e-114">Configure the Linux software repository</span></span>](#configure-the-linux-software-repository)
    - [<span data-ttu-id="7c73e-115">RHEL とバリアント (CentOS および Oracle Linux)</span><span class="sxs-lookup"><span data-stu-id="7c73e-115">RHEL and variants (CentOS and Oracle Linux)</span></span>](#rhel-and-variants-centos-and-oracle-linux)
    - [<span data-ttu-id="7c73e-116">SLES とバリアント</span><span class="sxs-lookup"><span data-stu-id="7c73e-116">SLES and variants</span></span>](#sles-and-variants)
    - [<span data-ttu-id="7c73e-117">Ubuntu システムと Debian システム</span><span class="sxs-lookup"><span data-stu-id="7c73e-117">Ubuntu and Debian systems</span></span>](#ubuntu-and-debian-systems)
  - [<span data-ttu-id="7c73e-118">アプリケーションのインストール</span><span class="sxs-lookup"><span data-stu-id="7c73e-118">Application installation</span></span>](#application-installation)
  - [<span data-ttu-id="7c73e-119">オンボーディング パッケージをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="7c73e-119">Download the onboarding package</span></span>](#download-the-onboarding-package)
  - [<span data-ttu-id="7c73e-120">クライアント構成</span><span class="sxs-lookup"><span data-stu-id="7c73e-120">Client configuration</span></span>](#client-configuration)
  - [<span data-ttu-id="7c73e-121">インストーラー スクリプト</span><span class="sxs-lookup"><span data-stu-id="7c73e-121">Installer script</span></span>](#installer-script)
  - [<span data-ttu-id="7c73e-122">ログ インストールの問題</span><span class="sxs-lookup"><span data-stu-id="7c73e-122">Log installation issues</span></span>](#log-installation-issues)
  - [<span data-ttu-id="7c73e-123">オペレーティング システムのアップグレード</span><span class="sxs-lookup"><span data-stu-id="7c73e-123">Operating system upgrades</span></span>](#operating-system-upgrades)
  - [<span data-ttu-id="7c73e-124">アンインストール</span><span class="sxs-lookup"><span data-stu-id="7c73e-124">Uninstallation</span></span>](#uninstallation)

## <a name="prerequisites-and-system-requirements"></a><span data-ttu-id="7c73e-125">前提条件とシステム要件</span><span class="sxs-lookup"><span data-stu-id="7c73e-125">Prerequisites and system requirements</span></span>

<span data-ttu-id="7c73e-126">開始する前に、現在のソフトウェア バージョンの前提条件とシステム要件の説明については [、「Microsoft Defender for Endpoint on Linux」](microsoft-defender-endpoint-linux.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c73e-126">Before you get started, see [Microsoft Defender for Endpoint on Linux](microsoft-defender-endpoint-linux.md) for a description of prerequisites and system requirements for the current software version.</span></span>

## <a name="configure-the-linux-software-repository"></a><span data-ttu-id="7c73e-127">Linux ソフトウェア リポジトリの構成</span><span class="sxs-lookup"><span data-stu-id="7c73e-127">Configure the Linux software repository</span></span>

<span data-ttu-id="7c73e-128">Defender for Endpoint for Linux は、以下のいずれかのチャネル *([channel] と* 示す) から展開できます。insiders-fast *、insiders-slow、\*\*または prod* です。 これらの各チャネルは、Linux ソフトウェア リポジトリに対応します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-128">Defender for Endpoint for Linux can be deployed from one of the following channels (denoted below as *[channel]*): *insiders-fast*, *insiders-slow*, or *prod*. Each of these channels corresponds to a Linux software repository.</span></span> <span data-ttu-id="7c73e-129">これらのリポジトリのいずれかを使用するためにデバイスを構成する手順を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-129">Instructions for configuring your device to use one of these repositories are provided below.</span></span>

<span data-ttu-id="7c73e-130">チャネルの選択によって、デバイスに提供される更新プログラムの種類と頻度が決されます。</span><span class="sxs-lookup"><span data-stu-id="7c73e-130">The choice of the channel determines the type and frequency of updates that are offered to your device.</span></span> <span data-ttu-id="7c73e-131">*insiders-fast* のデバイスは、更新プログラムと新機能を受け取る最初のデバイスで、後で *insiders-slow* と最後に *prod が続きます*。</span><span class="sxs-lookup"><span data-stu-id="7c73e-131">Devices in *insiders-fast* are the first ones to receive updates and new features, followed later by *insiders-slow* and lastly by *prod*.</span></span>

<span data-ttu-id="7c73e-132">新機能をプレビューし、早期のフィードバックを提供するために、インサイダー高速またはインサイダー低速のいずれかを使用するために、企業の一部のデバイスを構成をお *勧めします*。</span><span class="sxs-lookup"><span data-stu-id="7c73e-132">In order to preview new features and provide early feedback, it is recommended that you configure some devices in your enterprise to use either *insiders-fast* or *insiders-slow*.</span></span>

> [!WARNING]
> <span data-ttu-id="7c73e-133">最初のインストール後にチャネルを切り替える場合は、製品を再インストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c73e-133">Switching the channel after the initial installation requires the product to be reinstalled.</span></span> <span data-ttu-id="7c73e-134">製品チャネルを切り替える: 既存のパッケージをアンインストールし、新しいチャネルを使用するデバイスを再構成し、このドキュメントの手順に従って新しい場所からパッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="7c73e-134">To switch the product channel: uninstall the existing package, re-configure your device to use the new channel, and follow the steps in this document to install the package from the new location.</span></span>

### <a name="rhel-and-variants-centos-and-oracle-linux"></a><span data-ttu-id="7c73e-135">RHEL とバリアント (CentOS および Oracle Linux)</span><span class="sxs-lookup"><span data-stu-id="7c73e-135">RHEL and variants (CentOS and Oracle Linux)</span></span>

- <span data-ttu-id="7c73e-136">まだ `yum-utils` インストールされていない場合はインストールします。</span><span class="sxs-lookup"><span data-stu-id="7c73e-136">Install `yum-utils` if it isn't installed yet:</span></span>

    ```bash
    sudo yum install yum-utils
    ```

- <span data-ttu-id="7c73e-137">配布とバージョンに注意し、その下の最も近いエントリ (メジャー、マイナー) を識別します `https://packages.microsoft.com/config/` 。</span><span class="sxs-lookup"><span data-stu-id="7c73e-137">Note your distribution and version, and identify the closest entry (by major, then minor) for it under `https://packages.microsoft.com/config/`.</span></span> <span data-ttu-id="7c73e-138">たとえば、RHEL 7.9 は 8 よりも 7.4 に近いです。</span><span class="sxs-lookup"><span data-stu-id="7c73e-138">For instance, RHEL 7.9 is closer to 7.4 than to 8.</span></span>

    <span data-ttu-id="7c73e-139">以下のコマンドで *、[distro]* と *[version]* を、特定した情報に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c73e-139">In the below commands, replace *[distro]* and *[version]* with the information you've identified:</span></span>

    > [!NOTE]
    > <span data-ttu-id="7c73e-140">Oracle Linux の場合 *、[distro] を "rhel"* に置き換える。</span><span class="sxs-lookup"><span data-stu-id="7c73e-140">In case of Oracle Linux, replace *[distro]* with “rhel”.</span></span>

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/[distro]/[version]/[channel].repo
    ```

    <span data-ttu-id="7c73e-141">たとえば、CentOS 7 を実行し、Prod チャネルから Defender for Endpoint for Linux を展開する場合は、次の *コマンドを実行* します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-141">For example, if you are running CentOS 7 and want to deploy Defender for Endpoint for Linux from the *prod* channel:</span></span>

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/centos/7/prod.repo
    ```

    <span data-ttu-id="7c73e-142">または、選択したデバイス上の新機能を確認する場合は、Linux 用 MDE を *insiders-fast チャネルに展開する必要* があります。</span><span class="sxs-lookup"><span data-stu-id="7c73e-142">Or if you wish to explore new features on selected devices, you might want to deploy MDE for Linux to *insiders-fast* channel:</span></span>

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/centos/7/insiders-fast.repo
    ```

- <span data-ttu-id="7c73e-143">Microsoft GPG 公開キーをインストールします。</span><span class="sxs-lookup"><span data-stu-id="7c73e-143">Install the Microsoft GPG public key:</span></span>

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

- <span data-ttu-id="7c73e-144">現在有効になっている yum リポジトリのすべてのメタデータをダウンロードして使用可能にします。</span><span class="sxs-lookup"><span data-stu-id="7c73e-144">Download and make usable all the metadata for the currently enabled yum repositories:</span></span>

    ```bash
    yum makecache
    ```

### <a name="sles-and-variants"></a><span data-ttu-id="7c73e-145">SLES とバリアント</span><span class="sxs-lookup"><span data-stu-id="7c73e-145">SLES and variants</span></span>

- <span data-ttu-id="7c73e-146">配布とバージョンをメモし、その下で最も近いエントリ (メジャー、マイナー) を識別します `https://packages.microsoft.com/config/` 。</span><span class="sxs-lookup"><span data-stu-id="7c73e-146">Note your distribution and version, and identify the closest entry(by major, then minor) for it under `https://packages.microsoft.com/config/`.</span></span>

    <span data-ttu-id="7c73e-147">次のコマンドで *、[distro]* と *[version]* を、特定した情報に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c73e-147">In the following commands, replace *[distro]* and *[version]* with the information you've identified:</span></span>

    ```bash
    sudo zypper addrepo -c -f -n microsoft-[channel] https://packages.microsoft.com/config/[distro]/[version]/[channel].repo
    ```

    <span data-ttu-id="7c73e-148">たとえば、SLES 12 を実行し、Prod チャネルから Linux 用 MDE を展開する場合は、次の *コマンドを実行* します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-148">For example, if you are running SLES 12 and wish to deploy MDE for Linux from the *prod* channel:</span></span>

    ```bash
    sudo zypper addrepo -c -f -n microsoft-prod https://packages.microsoft.com/config/sles/12/prod.repo
    ```

- <span data-ttu-id="7c73e-149">Microsoft GPG 公開キーをインストールします。</span><span class="sxs-lookup"><span data-stu-id="7c73e-149">Install the Microsoft GPG public key:</span></span>

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="ubuntu-and-debian-systems"></a><span data-ttu-id="7c73e-150">Ubuntu システムと Debian システム</span><span class="sxs-lookup"><span data-stu-id="7c73e-150">Ubuntu and Debian systems</span></span>

- <span data-ttu-id="7c73e-151">まだ `curl` インストールされていない場合はインストールします。</span><span class="sxs-lookup"><span data-stu-id="7c73e-151">Install `curl` if it isn't installed yet:</span></span>

    ```bash
    sudo apt-get install curl
    ```

- <span data-ttu-id="7c73e-152">まだ `libplist-utils` インストールされていない場合はインストールします。</span><span class="sxs-lookup"><span data-stu-id="7c73e-152">Install `libplist-utils` if it isn't installed yet:</span></span>

    ```bash
    sudo apt-get install libplist-utils
    ```

- <span data-ttu-id="7c73e-153">配布とバージョンに注意し、その下の最も近いエントリ (メジャー、マイナー) を識別します `https://packages.microsoft.com/config` 。</span><span class="sxs-lookup"><span data-stu-id="7c73e-153">Note your distribution and version, and identify the closest entry (by major, then minor) for it under `https://packages.microsoft.com/config`.</span></span>

    <span data-ttu-id="7c73e-154">次のコマンドで *、[distro]* と *[version]* を、特定した情報に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c73e-154">In the below command, replace *[distro]* and *[version]* with the information you've identified:</span></span>

    ```bash
    curl -o microsoft.list https://packages.microsoft.com/config/[distro]/[version]/[channel].list
    ```

    <span data-ttu-id="7c73e-155">たとえば、Ubuntu 18.04 を実行し *、Prod* チャネルから Linux 用 MDE を展開する場合は、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="7c73e-155">For example, if you are running Ubuntu 18.04 and wish to deploy MDE for Linux from the *prod* channel:</span></span>

    ```bash
    curl -o microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list
    ```

- <span data-ttu-id="7c73e-156">リポジトリ構成をインストールします。</span><span class="sxs-lookup"><span data-stu-id="7c73e-156">Install the repository configuration:</span></span>

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-[channel].list
    ```
    <span data-ttu-id="7c73e-157">たとえば、prod チャネル *を選択した* 場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7c73e-157">For example, if you chose *prod* channel:</span></span>
    
    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-prod.list
    ```   

- <span data-ttu-id="7c73e-158">まだインストール `gpg` されていない場合は、パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="7c73e-158">Install the `gpg` package if not already installed:</span></span>

    ```bash
    sudo apt-get install gpg
    ```

  <span data-ttu-id="7c73e-159">使用 `gpg` できない場合は、インストールします `gnupg` 。</span><span class="sxs-lookup"><span data-stu-id="7c73e-159">If `gpg` is not available, then install `gnupg`.</span></span>

- <span data-ttu-id="7c73e-160">Microsoft GPG 公開キーをインストールします。</span><span class="sxs-lookup"><span data-stu-id="7c73e-160">Install the Microsoft GPG public key:</span></span>

    ```bash
    curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

- <span data-ttu-id="7c73e-161">https ドライバーが存在しない場合は、インストールします。</span><span class="sxs-lookup"><span data-stu-id="7c73e-161">Install the https driver if it's not already present:</span></span>

    ```bash
    sudo apt-get install apt-transport-https
    ```

- <span data-ttu-id="7c73e-162">リポジトリ のメタデータを更新します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-162">Update the repository metadata:</span></span>

    ```bash
    sudo apt-get update
    ```

## <a name="application-installation"></a><span data-ttu-id="7c73e-163">アプリケーションのインストール</span><span class="sxs-lookup"><span data-stu-id="7c73e-163">Application installation</span></span>

- <span data-ttu-id="7c73e-164">RHEL とバリアント (CentOS および Oracle Linux):</span><span class="sxs-lookup"><span data-stu-id="7c73e-164">RHEL and variants (CentOS and Oracle Linux):</span></span>

    ```bash
    sudo yum install mdatp
    ```

    <span data-ttu-id="7c73e-165">デバイスに複数の Microsoft リポジトリが構成されている場合は、パッケージをインストールするリポジトリを特定できます。</span><span class="sxs-lookup"><span data-stu-id="7c73e-165">If you have multiple Microsoft repositories configured on your device, you can be specific about which repository to install the package from.</span></span> <span data-ttu-id="7c73e-166">次の例は、このデバイスでリポジトリ チャネルも構成されている場合に、チャネルからパッケージをインストール `production` `insiders-fast` する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7c73e-166">The following example shows how to install the package from the `production` channel if you also have the `insiders-fast` repository channel configured on this device.</span></span> <span data-ttu-id="7c73e-167">この状況は、デバイスで複数の Microsoft 製品を使用している場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7c73e-167">This situation can happen if you are using multiple Microsoft products on your device.</span></span> <span data-ttu-id="7c73e-168">サーバーの配布とバージョンによっては、リポジトリ エイリアスが次の例と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7c73e-168">Depending on the distribution and the version of your server, the repository alias might be different than the one in the following example.</span></span>

    ```bash
    # list all repositories
    yum repolist
    ```
    ```Output
    ...
    packages-microsoft-com-prod               packages-microsoft-com-prod        316
    packages-microsoft-com-prod-insiders-fast packages-microsoft-com-prod-ins      2
    ...
    ```
    ```bash
    # install the package from the production repository
    sudo yum --enablerepo=packages-microsoft-com-prod install mdatp
    ```

- <span data-ttu-id="7c73e-169">SLES とバリアント:</span><span class="sxs-lookup"><span data-stu-id="7c73e-169">SLES and variants:</span></span>

    ```bash
    sudo zypper install mdatp
    ```

    <span data-ttu-id="7c73e-170">デバイスに複数の Microsoft リポジトリが構成されている場合は、パッケージをインストールするリポジトリを特定できます。</span><span class="sxs-lookup"><span data-stu-id="7c73e-170">If you have multiple Microsoft repositories configured on your device, you can be specific about which repository to install the package from.</span></span> <span data-ttu-id="7c73e-171">次の例は、このデバイスでリポジトリ チャネルも構成されている場合に、チャネルからパッケージをインストール `production` `insiders-fast` する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7c73e-171">The following example shows how to install the package from the `production` channel if you also have the `insiders-fast` repository channel configured on this device.</span></span> <span data-ttu-id="7c73e-172">この状況は、デバイスで複数の Microsoft 製品を使用している場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7c73e-172">This situation can happen if you are using multiple Microsoft products on your device.</span></span>

    ```bash
    zypper repos
    ```

    ```Output
    ...
    #  | Alias | Name | ...
    XX | packages-microsoft-com-insiders-fast | microsoft-insiders-fast | ...
    XX | packages-microsoft-com-prod | microsoft-prod | ...
    ...
    ```
    ```bash
    sudo zypper install packages-microsoft-com-prod:mdatp
    ```

- <span data-ttu-id="7c73e-173">Ubuntu および Debian システム:</span><span class="sxs-lookup"><span data-stu-id="7c73e-173">Ubuntu and Debian system:</span></span>

    ```bash
    sudo apt-get install mdatp
    ```

    <span data-ttu-id="7c73e-174">デバイスに複数の Microsoft リポジトリが構成されている場合は、パッケージをインストールするリポジトリを特定できます。</span><span class="sxs-lookup"><span data-stu-id="7c73e-174">If you have multiple Microsoft repositories configured on your device, you can be specific about which repository to install the package from.</span></span> <span data-ttu-id="7c73e-175">次の例は、このデバイスでリポジトリ チャネルも構成されている場合に、チャネルからパッケージをインストール `production` `insiders-fast` する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7c73e-175">The following example shows how to install the package from the `production` channel if you also have the `insiders-fast` repository channel configured on this device.</span></span> <span data-ttu-id="7c73e-176">この状況は、デバイスで複数の Microsoft 製品を使用している場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7c73e-176">This situation can happen if you are using multiple Microsoft products on your device.</span></span>

    ```bash
    cat /etc/apt/sources.list.d/*
    ```
    ```Output
    deb [arch=arm64,armhf,amd64] https://packages.microsoft.com/ubuntu/18.04/prod insiders-fast main
    deb [arch=amd64] https://packages.microsoft.com/ubuntu/18.04/prod bionic main
    ```
    ```bash
    sudo apt -t bionic install mdatp
    ```

## <a name="download-the-onboarding-package"></a><span data-ttu-id="7c73e-177">オンボーディング パッケージをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="7c73e-177">Download the onboarding package</span></span>

<span data-ttu-id="7c73e-178">Microsoft Defender セキュリティ センターからオンボーディング パッケージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="7c73e-178">Download the onboarding package from Microsoft Defender Security Center:</span></span>

1. <span data-ttu-id="7c73e-179">Microsoft Defender セキュリティ センターで、[デバイス管理とオンボード **>設定>移動します**。</span><span class="sxs-lookup"><span data-stu-id="7c73e-179">In Microsoft Defender Security Center, go to **Settings > Device Management > Onboarding**.</span></span>
2. <span data-ttu-id="7c73e-180">最初のドロップダウン メニューで、オペレーティング システム **として [Linux Server]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-180">In the first drop-down menu, select **Linux Server** as the operating system.</span></span> <span data-ttu-id="7c73e-181">2 番目のドロップダウン メニューで、展開方法として [ローカル スクリプト] **(最大 10** 台のデバイス) を選択します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-181">In the second drop-down menu, select **Local Script (for up to 10 devices)** as the deployment method.</span></span>
3. <span data-ttu-id="7c73e-182">[オンボード **パッケージのダウンロード] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="7c73e-182">Select **Download onboarding package**.</span></span> <span data-ttu-id="7c73e-183">ファイルを [ファイル名] WindowsDefenderATPOnboardingPackage.zip。</span><span class="sxs-lookup"><span data-stu-id="7c73e-183">Save the file as WindowsDefenderATPOnboardingPackage.zip.</span></span>

    ![Microsoft Defender セキュリティ センターのスクリーンショット](images/atp-portal-onboarding-linux.png)

4. <span data-ttu-id="7c73e-185">コマンド プロンプトから、ファイルが存在するように確認します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-185">From a command prompt, verify that you have the file.</span></span>
    <span data-ttu-id="7c73e-186">アーカイブの内容を抽出します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-186">Extract the contents of the archive:</span></span>

    ```bash
    ls -l
    ```

    ```Output
    total 8
    -rw-r--r-- 1 test  staff  5752 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```

    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```
    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: MicrosoftDefenderATPOnboardingLinuxServer.py
    ```


## <a name="client-configuration"></a><span data-ttu-id="7c73e-187">クライアント構成</span><span class="sxs-lookup"><span data-stu-id="7c73e-187">Client configuration</span></span>

1. <span data-ttu-id="7c73e-188">ターゲット MicrosoftDefenderATPOnboardingLinuxServer.py にコピーします。</span><span class="sxs-lookup"><span data-stu-id="7c73e-188">Copy MicrosoftDefenderATPOnboardingLinuxServer.py to the target device.</span></span>

    <span data-ttu-id="7c73e-189">最初は、クライアント デバイスは組織に関連付けではありません。</span><span class="sxs-lookup"><span data-stu-id="7c73e-189">Initially the client device is not associated with an organization.</span></span> <span data-ttu-id="7c73e-190">*orgId 属性は空白* です。</span><span class="sxs-lookup"><span data-stu-id="7c73e-190">Note that the *orgId* attribute is blank:</span></span>

    ```bash
    mdatp health --field org_id
    ```

2. <span data-ttu-id="7c73e-191">次 MicrosoftDefenderATPOnboardingLinuxServer.py を実行し、このコマンドを実行するには、デバイスにインストール `python` されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c73e-191">Run MicrosoftDefenderATPOnboardingLinuxServer.py, and note that, in order to run this command, you must have `python` installed on the device:</span></span>

    ```bash
    python MicrosoftDefenderATPOnboardingLinuxServer.py
    ```

3. <span data-ttu-id="7c73e-192">デバイスが組織に関連付けられていると確認し、有効な組織識別子を報告します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-192">Verify that the device is now associated with your organization and reports a valid organization identifier:</span></span>

    ```bash
    mdatp health --field org_id
    ```

4. <span data-ttu-id="7c73e-193">インストールが完了した数分後に、次のコマンドを実行して状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="7c73e-193">A few minutes after you complete the installation, you can see the status by running the following command.</span></span> <span data-ttu-id="7c73e-194">戻り値は `1` 、製品が期待通り機能している状態であることを示します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-194">A return value of `1` denotes that the product is functioning as expected:</span></span>

    ```bash
    mdatp health --field healthy
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="7c73e-195">製品が初めて起動すると、最新のマルウェア対策定義がダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="7c73e-195">When the product starts for the first time, it downloads the latest antimalware definitions.</span></span> <span data-ttu-id="7c73e-196">インターネット接続によっては、数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7c73e-196">Depending on your Internet connection, this can take up to a few minutes.</span></span> <span data-ttu-id="7c73e-197">この間、上記のコマンドはの値を返します `false` 。</span><span class="sxs-lookup"><span data-stu-id="7c73e-197">During this time the above command returns a value of `false`.</span></span> <span data-ttu-id="7c73e-198">定義の更新の状態は、次のコマンドを使用して確認できます。</span><span class="sxs-lookup"><span data-stu-id="7c73e-198">You can check the status of the definition update using the following command:</span></span>
    > ```bash
    > mdatp health --field definitions_status
    > ```
    > <span data-ttu-id="7c73e-199">初期インストールの完了後にプロキシの構成が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="7c73e-199">Please note that you may also need to configure a proxy after completing the initial installation.</span></span> <span data-ttu-id="7c73e-200">静的 [プロキシ検出用に Defender for Endpoint for Linux を構成する: インストール後の構成を参照してください](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/linux-static-proxy-configuration#post-installation-configuration)。</span><span class="sxs-lookup"><span data-stu-id="7c73e-200">See [Configure Defender for Endpoint for Linux for static proxy discovery: Post-installation configuration](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/linux-static-proxy-configuration#post-installation-configuration).</span></span>

5. <span data-ttu-id="7c73e-201">検出テストを実行して、デバイスが適切にオンボードされ、サービスに報告されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-201">Run a detection test to verify that the device is properly onboarded and reporting to the service.</span></span> <span data-ttu-id="7c73e-202">新しくオンボードされたデバイスで次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-202">Perform the following steps on the newly onboarded device:</span></span>

    - <span data-ttu-id="7c73e-203">リアルタイム保護が有効であることを確認します (次のコマンドを実行した結果 `1` で示されます)。</span><span class="sxs-lookup"><span data-stu-id="7c73e-203">Ensure that real-time protection is enabled (denoted by a result of `1` from running the following command):</span></span>

        ```bash
        mdatp health --field real_time_protection_enabled
        ```

    - <span data-ttu-id="7c73e-204">ターミナル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="7c73e-204">Open a Terminal window.</span></span> <span data-ttu-id="7c73e-205">次のコマンドをコピーして実行します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-205">Copy and execute the following command:</span></span>

        ``` bash
        curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    - <span data-ttu-id="7c73e-206">このファイルは、Defender for Endpoint for Linux によって検疫されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c73e-206">The file should have been quarantined by Defender for Endpoint for Linux.</span></span> <span data-ttu-id="7c73e-207">次のコマンドを使用して、検出された脅威の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-207">Use the following command to list all the detected threats:</span></span>

        ```bash
        mdatp threat list
        ```

## <a name="installer-script"></a><span data-ttu-id="7c73e-208">インストーラー スクリプト</span><span class="sxs-lookup"><span data-stu-id="7c73e-208">Installer script</span></span>

<span data-ttu-id="7c73e-209">または、公開 GitHub リポジトリで提供されている自動インストーラー [bash](https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/mde_installer.sh) [スクリプトを使用することもできます](https://github.com/microsoft/mdatp-xplat/)。</span><span class="sxs-lookup"><span data-stu-id="7c73e-209">Alternatively, you can use an automated [installer bash script](https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/mde_installer.sh) provided in our [public GitHub repository](https://github.com/microsoft/mdatp-xplat/).</span></span>
<span data-ttu-id="7c73e-210">スクリプトは配布とバージョンを識別し、最新のパッケージをプルしてインストールするデバイスをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="7c73e-210">The script identifies the distribution and version, and sets up the device to pull the latest package and install it.</span></span>
<span data-ttu-id="7c73e-211">指定されたスクリプトを使用してオンボードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="7c73e-211">You can also onboard with a provided script.</span></span>

```bash
❯ ./mde_installer.sh --help
usage: basename ./mde_installer.sh [OPTIONS]
Options:
-c|--channel      specify the channel from which you want to install. Default: insiders-fast
-i|--install      install the product
-r|--remove       remove the product
-u|--upgrade      upgrade the existing product
-o|--onboard      onboard/offboard the product with <onboarding_script>
-p|--passive-mode set EPP to passive mode
-t|--tag          set a tag by declaring <name> and <value>. ex: -t GROUP Coders
-m|--min_req      enforce minimum requirements
-w|--clean        remove repo from package manager for a specific channel
-v|--version      print out script version
-h|--help         display help
```

<span data-ttu-id="7c73e-212">詳細については、 [こちらを参照してください](https://github.com/microsoft/mdatp-xplat/tree/master/linux/installation)。</span><span class="sxs-lookup"><span data-stu-id="7c73e-212">Read more [here](https://github.com/microsoft/mdatp-xplat/tree/master/linux/installation).</span></span>

## <a name="log-installation-issues"></a><span data-ttu-id="7c73e-213">ログ インストールの問題</span><span class="sxs-lookup"><span data-stu-id="7c73e-213">Log installation issues</span></span>

<span data-ttu-id="7c73e-214">エラー [が発生した場合](linux-resources.md#log-installation-issues) にインストーラーによって作成される自動的に生成されたログを検索する方法の詳細については、「Log installation issues」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c73e-214">See [Log installation issues](linux-resources.md#log-installation-issues) for more information on how to find the automatically generated log that is created by the installer when an error occurs.</span></span>

## <a name="operating-system-upgrades"></a><span data-ttu-id="7c73e-215">オペレーティング システムのアップグレード</span><span class="sxs-lookup"><span data-stu-id="7c73e-215">Operating system upgrades</span></span>

<span data-ttu-id="7c73e-216">オペレーティング システムを新しいメジャー バージョンにアップグレードする場合は、まず Defender for Endpoint for Linux をアンインストールし、アップグレードをインストールし、最後にデバイスで Defender for Endpoint for Linux を再構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c73e-216">When upgrading your operating system to a new major version, you must first uninstall Defender for Endpoint for Linux, install the upgrade, and finally reconfigure Defender for Endpoint for Linux on your device.</span></span>

## <a name="how-to-migrate-from-insiders-fast-to-production-channel"></a><span data-ttu-id="7c73e-217">サーバーから実稼働チャネルInsiders-Fast移行する方法</span><span class="sxs-lookup"><span data-stu-id="7c73e-217">How to migrate from Insiders-Fast to Production channel</span></span>

1. <span data-ttu-id="7c73e-218">Linux 用 MDE の "Insiders-Fast チャネル" バージョンをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="7c73e-218">Uninstall the “Insiders-Fast channel” version of MDE for Linux.</span></span>

    ``
    sudo yum remove mdatp
    ``

1. <span data-ttu-id="7c73e-219">Linux の MDE を無効Insiders-Fastレポ  ``
    sudo yum repolist
    ``</span><span class="sxs-lookup"><span data-stu-id="7c73e-219">Disable the MDE for Linux Insiders-Fast repo  ``
    sudo yum repolist
 ``</span></span>

    > [!NOTE]
    > <span data-ttu-id="7c73e-220">出力には "packages-microsoft-com-fast-prod" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7c73e-220">The output should show “packages-microsoft-com-fast-prod”.</span></span>

    ``
    sudo yum-config-manager --disable packages-microsoft-com-fast-prod
    ``
1. <span data-ttu-id="7c73e-221">"実稼働チャネル" を使用して Linux 用 MDE を再展開します。</span><span class="sxs-lookup"><span data-stu-id="7c73e-221">Redeploy MDE for Linux using the “Production channel”.</span></span>


## <a name="uninstallation"></a><span data-ttu-id="7c73e-222">アンインストール</span><span class="sxs-lookup"><span data-stu-id="7c73e-222">Uninstallation</span></span>

<span data-ttu-id="7c73e-223">クライアント デバイス [から Defender](linux-resources.md#uninstall) for Endpoint for Linux を削除する方法の詳細については、「アンインストール」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c73e-223">See [Uninstall](linux-resources.md#uninstall) for details on how to remove Defender for Endpoint for Linux from client devices.</span></span>
