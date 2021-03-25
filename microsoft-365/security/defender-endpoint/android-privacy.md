---
title: Android 用 Microsoft Defender ATP - プライバシー情報
description: プライバシーコントロール、プライバシーに影響を与えるポリシー設定を構成する方法、および Microsoft Defender ATP for Android で収集された診断データに関する情報。
keywords: microsoft, defender, atp, android, プライバシー, 診断
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
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: abb22b2e733d1e40bd4f2733ef2d25767c69ccf7
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51163329"
---
#  <a name="microsoft-defender-for-endpoint-for-android---privacy-information"></a>Microsoft Defender for Endpoint for Android - プライバシー情報

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 


Defender for Endpoint for Android は、構成済みの Android デバイスから情報を収集し、Defender for Endpoint を持つ同じテナントに格納します。

情報は、Defender for Endpoint for Android のセキュリティを確保し、最新の状態に保ち、期待通り実行し、サービスをサポートするために収集されます。

## <a name="required-data"></a>必須データ 

必要なデータは、Android 用 Defender for Endpoint を期待通り動作させるのに必要なデータで構成されます。 このデータはサービスの運用に不可欠であり、エンド ユーザー、組織、デバイス、アプリに関連するデータを含めできます。 収集するデータの種類の一覧を次に示します。

### <a name="app-information"></a>アプリ情報

デバイス上の Android アプリケーション パッケージ (APK) に関する情報 (以下を含む)

-  ソースのインストール
-  APK の保存場所 (ファイル パス)
-  インストールの時間、APK のサイズ、およびアクセス許可

### <a name="web-page--network-information"></a>Web ページ / ネットワーク情報

- [完全な URL] (サポートされているブラウザーの場合) (クリック時)
- 接続情報
- プロトコルの種類 (HTTP、HTTPS など)


### <a name="device-and-account-information"></a>デバイスとアカウントの情報

- 日付、時刻、&、OEM モデル、CPU 情報、デバイス識別子などのデバイス情報
- デバイス識別子は、次のいずれかを示します。
    - Wi-Fi MAC アドレス
    - [Android ID](https://developer.android.com/reference/android/provider/Settings.Secure#ANDROID_ID) (デバイスの初回起動時に Android によって生成された場合)
    - ランダムに生成されたグローバル一意識別子 (GUID)

- テナント、デバイス、およびユーザー情報
    -   Azure Active Directory (AD) デバイス ID と Azure ユーザー ID: デバイスを一意に識別します。ユーザーは、それぞれ Azure Active directory にあります。

    -   Azure テナント ID - Azure Active Directory 内の組織を識別する GUID

    -   Microsoft Defender ATP 組織 ID - デバイスが属する企業に関連付けられた一意の識別子。 Microsoft は、問題が企業の選択セットに影響を与えるかどうか、および影響を受け取る企業の数を特定できます。 

    -   ユーザー プリンシパル名 – ユーザーの電子メール ID

### <a name="product-and-service-usage-data"></a>製品とサービスの使用状況データ
-   名前、バージョン、アプリアップグレードの状態を含むアプリ パッケージ情報

-   アプリで実行されるアクション

-   脅威の検出情報 (脅威名、カテゴリなど)

-   Android によって生成されたクラッシュ レポート ログ

## <a name="optional-data"></a>オプションのデータ

オプションのデータには、診断データとフィードバック データが含まれます。 オプションの診断データは、製品の改良に役立ち、問題の検出、診断、修正に役立つ高度な情報を提供する追加データです。 オプションの診断データには、次の情報が含まれます。

-   アプリ、CPU、およびネットワークの使用状況

-   アプリの観点からデバイスの状態 (スキャンの状態、スキャンのタイミング、付与されたアプリのアクセス許可、アップグレードの状態など)

-   管理者が構成した機能

-   デバイス上のブラウザーに関する基本情報

**フィードバック データは** 、ユーザーが提供するアプリ内フィードバックを通じて収集されます。

-   ユーザーの電子メール アドレスを指定する場合

-   フィードバックの種類 (微笑み、顔をしかめ、アイデア) と、ユーザーが送信したフィードバック コメント