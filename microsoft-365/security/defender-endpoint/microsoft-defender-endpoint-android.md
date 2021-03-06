---
title: Android 用 Microsoft Defender for Endpoint
ms.reviewer: ''
description: Android に Microsoft Defender for Endpoint をインストールして使用する方法について説明します。
keywords: microsoft、 defender、 Microsoft Defender for Endpoint, android, installation, deploy, uninstallation, intune
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
ms.openlocfilehash: ceccd9e3c8a8137f672e7be519675034a84c7881
ms.sourcegitcommit: fa9efab24a84f71fec7d001f2ad8949125fa8eee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2021
ms.locfileid: "53055104"
---
# <a name="microsoft-defender-for-endpoint-on-android"></a>Android 用 Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

このトピックでは、Android 上で Defender for Endpoint をインストール、構成、更新、および使用する方法について説明します。

> [!CAUTION]
> Android で Defender for Endpoint と共に他のサード パーティ製のエンドポイント保護製品を実行すると、パフォーマンスの問題や予期しないシステム エラーが発生する可能性があります。


## <a name="how-to-install-microsoft-defender-for-endpoint-on-android"></a>Android に Microsoft Defender for Endpoint をインストールする方法

### <a name="prerequisites"></a>前提条件

-   **エンド ユーザー向け**

    -   アプリのエンド ユーザーに割り当てられた Microsoft Defender for Endpoint ライセンス。 [「Microsoft Defender for Endpoint ライセンス要件」を参照してください。](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements)

    -   Intune ポータル サイトは Google Play からダウンロード[可能](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)で、Android デバイスで利用できます。

        -   さらに、Intune デバイスコンプライアンス ポリシーを[](/mem/intune/user-help/enroll-device-android-company-portal)適用するために、Intune ポータル サイトアプリを介してデバイスを登録できます。 これには、エンド ユーザーにライセンスを割り当てるMicrosoft Intune必要があります。

    -   ライセンスを割り当てる方法の詳細については、「ユーザーにライセンスを割り当 [てる」を参照してください](/azure/active-directory/users-groups-roles/licensing-groups-assign)。
        

-   **管理者向け**

    -   ポータルへのアクセスMicrosoft Defender セキュリティ センターします。

        > [!NOTE]
        > Microsoft Intuneは、Android に Microsoft Defender for Endpoint を展開する場合にサポートされている唯一のモバイル デバイス管理 (MDM) ソリューションです。 現在、Intune で Android 関連のデバイス コンプライアンス ポリシーで Defender for Endpoint を適用する場合は、現在登録されているデバイスだけがサポートされています。 

    -   管理[Microsoft エンドポイント マネージャーアクセスして](https://go.microsoft.com/fwlink/?linkid=2109431)、組織の登録済みユーザー グループにアプリを展開します。
        
### <a name="network-requirements"></a>ネットワーク要件

- Microsoft Defender for Endpoint on Android がネットワークに接続されている場合に機能するには [、Microsoft Defender for Endpoint](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)サービス URL へのアクセスを有効にするようにファイアウォール/プロキシを構成する必要があります。

### <a name="system-requirements"></a>システム要件

-   Android 6.0 以上を実行している携帯電話。 **Android を実行しているタブレットや他のモバイル デバイスは現在サポートされていません。** 

-   Intune ポータル サイトは Google Play から[ダウンロードされ、](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)インストールされます。 Intune デバイス コンプライアンス ポリシーを適用するには、デバイスの登録が必要です。

### <a name="installation-instructions"></a>インストール手順

Android 上の Microsoft Defender for Endpoint は、登録されているデバイスの両方のモード (従来のデバイス管理者モードと Android デバイス モード) へのインストールEnterpriseサポートしています。
**現在、仕事用プロファイルと企業所有の完全に管理されたユーザー デバイス登録を持つ個人所有のデバイスは、Android Enterprise でサポートされています。他の Android Enterpriseのサポートは、準備ができたら発表されます。**

Android での Microsoft Defender for Endpoint の展開は、Microsoft Intune (MDM) 経由です。
詳細については、「Deploy Microsoft Defender for Endpoint on Android with Microsoft Intune」[を参照してください](android-intune.md)。


> [!NOTE]
> **Android 上のエンドポイント用 Microsoft Defender は [、Google Play で利用](https://play.google.com/store/apps/details?id=com.microsoft.scmx) できます。** <br> Intune から Google Play に接続して、Microsoft Defender for Endpoint アプリを展開し、デバイス管理者モードと Android デバイス Enterprise展開できます。 

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-android"></a>Android 上のエンドポイント用 Microsoft Defender を構成する方法

Android の機能で Microsoft Defender for Endpoint を構成する方法については、「Configure Microsoft Defender for Endpoint on Android フィーチャー [」を参照してください](android-configure.md)。



## <a name="related-topics"></a>関連項目
- [Microsoft Intune を使用した Android 用 Microsoft Defender for Endpoint の展開](android-intune.md)
- [Android 機能用に Microsoft Defender for Endpoint を構成する](android-configure.md)

