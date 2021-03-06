---
title: エンドポイント用 Microsoft Defender への切り替え - 準備
description: これは、Microsoft Defender for Endpoint に移行するフェーズ 1 の準備です。
keywords: 移行, Microsoft Defender for Endpoint, edr
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-migratetomdatp
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
ms.topic: article
ms.custom: migrationguides
ms.date: 06/14/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 56a63c09690e28f0ca4990dcbcbcb6cfff7d5eef
ms.sourcegitcommit: 3d30ec03628870a22c54b6ec5d865cbe94f34245
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2021
ms.locfileid: "52929505"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-1-prepare"></a>エンドポイント用 Microsoft Defender に切り替える - フェーズ 1: 準備

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| ![フェーズ 1: 準備](images/phase-diagrams/prepare.png)<br/>フェーズ 1: 準備 | [![フェーズ 2: 設定](images/phase-diagrams/setup.png)](switch-to-microsoft-defender-setup.md)<br/>[フェーズ 2: 設定](switch-to-microsoft-defender-setup.md) | [![フェーズ 3: オンボード](images/phase-diagrams/onboard.png)](switch-to-microsoft-defender-onboard.md)<br/>[フェーズ 3: オンボード](switch-to-microsoft-defender-onboard.md) |
|--|--|--|
|*お前はここにいる!*| | |

**Defender for Endpoint への切り [替えの準備フェーズへようこそ](switch-to-microsoft-defender-migration.md#the-migration-process)**。 

この移行フェーズには、次の手順が含まれます。

1. [組織のデバイス全体で更新プログラムを取得して展開する](#get-and-deploy-updates-across-your-organizations-devices)
2. [エンドポイントの Defender を取得します](#get-microsoft-defender-for-endpoint)。
3. [サーバーへのアクセスを許可Microsoft Defender セキュリティ センター。](#grant-access-to-the-microsoft-defender-security-center)
4. [デバイス プロキシとインターネット接続の設定を構成します](#configure-device-proxy-and-internet-connectivity-settings)。

## <a name="get-and-deploy-updates-across-your-organizations-devices"></a>組織のデバイス全体で更新プログラムを取得して展開する

ベスト プラクティスとして、組織のデバイスとエンドポイントを最新の状態に保ちます。 既存のエンドポイント保護とウイルス対策ソリューションが最新であり、組織のオペレーティング システムとアプリにも最新の更新プログラムが含まれています。 これで、Defender for Endpoint に移行した後で問題が発生し、問題が発生Microsoft Defender ウイルス対策。

### <a name="make-sure-your-existing-solution-is-up-to-date"></a>既存のソリューションが最新の情報を提供する

既存のエンドポイント保護ソリューションを最新の状態に保ち、組織のデバイスに最新のセキュリティ更新プログラムが含まれています。 

サポートが必要な場合 ソリューション プロバイダーのドキュメントを参照してください。

### <a name="make-sure-your-organizations-devices-are-up-to-date"></a>組織のデバイスが最新の情報を提供する

組織のデバイスの更新に関するヘルプが必要ですか? 以下のリソースを参照してください。

|OS | Resource |
|:--|:--|
|Windows |[Microsoft Update](https://www.update.microsoft.com) |
|macOS | [Mac でソフトウェアを更新する方法](https://support.apple.com/HT201541)|
|iOS |[iPod touch iPhone、iPad、または iPod touch を更新する](https://support.apple.com/HT204204)|
|Android |[Android &更新する方法を確認する](https://support.google.com/android/answer/7680439) |
|Linux | [Linux 101: システムの更新](https://www.linux.com/training-tutorials/linux-101-updating-your-system) |

## <a name="get-microsoft-defender-for-endpoint"></a>エンドポイントの Microsoft Defender を取得する

組織のデバイスを更新したので、次の手順では、Defender for Endpoint を取得し、ライセンスを割り当て、サービスがプロビジョニングされているのを確認します。

1. Defender for Endpoint を今すぐ購入または試してみてください。 [無料試用版を開始するか、見積もりを要求します](https://aka.ms/mdatp)。 

2. ライセンスが適切にプロビジョニングされていることを確認します。 [ライセンスの状態を確認します](production-deployment.md#check-license-state)。

3. グローバル管理者またはセキュリティ管理者として、Defender for Endpoint の専用クラウド インスタンスをセットアップします。 「Defender [for Endpoint setup: Tenant configuration」を参照してください](production-deployment.md#tenant-configuration)。

4. 組織内のエンドポイント (デバイスなど) がプロキシを使用してインターネットにアクセスする場合は [、「Defender for Endpoint setup: Network configuration」を参照してください](production-deployment.md#network-configuration)。
 
この時点で、セキュリティ管理者 Microsoft Defender セキュリティ センターとセキュリティオペレーターにアクセス権を付与する準備が整いました。 [https://securitycenter.windows.com](https://securitycenter.windows.com) 

> [!NOTE]
> このMicrosoft Defender セキュリティ センター Defender for Endpoint ポータルと呼ばれる場合があります。 [https://securitycenter.windows.com](https://securitycenter.windows.com) 

## <a name="grant-access-to-the-microsoft-defender-security-center"></a>サーバーへのアクセスを許可Microsoft Defender セキュリティ センター

このMicrosoft Defender セキュリティ センター ( ) は、Defender for Endpoint の機能にアクセスして [https://securitycenter.windows.com](https://securitycenter.windows.com) 構成する場所です。 詳細については、「概要」[を参照Microsoft Defender セキュリティ センター。](use.md)

アクセス許可は、Microsoft Defender セキュリティ センターアクセス許可または役割ベースのアクセス制御 (RBAC) を使用して付与できます。 アクセス許可を細かく制御するには、RBAC を使用することをお勧めします。

1. セキュリティ管理者とセキュリティオペレーターの役割とアクセス許可を計画します。 「 [役割ベースのアクセス制御」を参照してください](prepare-deployment.md#role-based-access-control)。

2. RBAC を設定して構成します。 Intune を使用[して RBAC](/mem/intune/fundamentals/what-is-intune)を構成することをお勧めします。特に、組織で、Windows 10、macOS、iOS、および Android デバイスの組み合わせを使用している場合。 Intune を [使用した RBAC のセットアップを参照してください](/mem/intune/fundamentals/role-based-access-control)。

    組織で Intune 以外の方法が必要な場合は、次のいずれかのオプションを選択します。

    - [構成マネージャー](/mem/configmgr/core/servers/deploy/configure/configure-role-based-administration)
    - [高度なグループ ポリシーの管理](/microsoft-desktop-optimization-pack/agpm)
    - [Windows管理センター](/windows-server/manage/windows-admin-center/overview)

3. ユーザーにアクセス権を付与Microsoft Defender セキュリティ センター。 (ヘルプが必要ですか? 「RBAC [を使用したポータル アクセスの管理」を参照](rbac.md)してください。

## <a name="configure-device-proxy-and-internet-connectivity-settings"></a>デバイス プロキシとインターネット接続の設定を構成する

デバイスと Defender for Endpoint 間の通信を有効にするには、プロキシとインターネットの設定を構成します。 次の表に、さまざまなオペレーティング システムと機能のプロキシとインターネット設定を構成するために使用できるリソースへのリンクを示します。

| 機能  | オペレーティング システム | リソース |
|:--|:--|:--|
| [エンドポイントの検出と応答](overview-endpoint-detection-response.md)(EDR) | [Windows 10](/windows/release-health/release-information) <p>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<p>[Windowsサーバー 1803 以降](/windows-server/get-started/whats-new-in-windows-server-1803)  | [コンピューター プロキシとインターネット接続の設定を構成する](configure-proxy-internet.md) |
| EDR | [Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016) <p>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<p>[WindowsServer 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<p>[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<p>[Windows 7 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |[プロキシとインターネット接続の設定を構成する](onboard-downlevel.md#configure-proxy-and-internet-connectivity-settings) |
| EDR  | macOS:<p>11.3.1 (Big Sur)<p>10.15 (Catalina)<p>10.14 (Mojave)   | [macOS 上のエンドポイントの Defender: ネットワーク接続](microsoft-defender-endpoint-mac.md#network-connections)  |
| [Microsoft Defender ウイルス対策](microsoft-defender-antivirus-in-windows-10.md) | [Windows 10](/windows/release-health/release-information) <p>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019)<p>[Windowsサーバー 1803 以降](/windows-server/get-started/whats-new-in-windows-server-1803) <p>[Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016) | [Microsoft Defender ウイルス対策 ネットワーク接続を構成および検証する](configure-network-connections-microsoft-defender-antivirus.md)<br/> |
| ウイルス対策 | macOS:<p>11.3.1 (Big Sur)<p>10.15 (Catalina)<p>10.14 (Mojave) | [macOS 上のエンドポイントの Defender: ネットワーク接続](microsoft-defender-endpoint-mac.md#network-connections) |
| ウイルス対策 | Linux: <p>RHEL 7.2+<p>CentOS Linux 7.2+<p>Ubuntu 16 LTS 以上の LTS<p>SLES 12+<p>Debian 9+<p>Oracle Linux 7.2 | [Defender for Endpoint on Linux: Network connections](microsoft-defender-endpoint-linux.md#network-connections) |

## <a name="next-step"></a>次の手順

**おめでとう** ございます! Defender for Endpoint への **切** り替えの [準備フェーズが完了しました](switch-to-microsoft-defender-migration.md#the-migration-process)。

- [[Defender for Endpoint] のセットアップに進みます](switch-to-microsoft-defender-setup.md)。
