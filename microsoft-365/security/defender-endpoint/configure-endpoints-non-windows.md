---
title: Windows 以外のデバイスを Microsoft Defender for Endpoint サービスにオンボードする
description: センサー データを Microsoft Defender ATP サービスに送信できるよう、Windows 以外のデバイスを構成します。
keywords: Windows 以外のデバイスのオンボード、macos、Linux、デバイス管理、Windows ATP デバイスの構成、Microsoft Defender for Endpoint デバイスの構成
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c292c57c179a832728b03a7fc94fb7085d3ea0ec
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51166079"
---
# <a name="onboard-non-windows-devices"></a>Windows 以外のデバイスをオンボードする

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**プラットフォーム**
- macOS
- Linux

>Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-nonwindows-abovefoldlink) 

Defender for Endpoint は、Windows および Windows 以外のプラットフォームに対して一元的なセキュリティ操作エクスペリエンスを提供します。 Microsoft Defender Security Center でサポートされているさまざまなオペレーティング システム (OS) からのアラートを確認し、組織のネットワークをより保護することができます。 

統合を機能するには、Defender for Endpoint と互換性のある Linux ディストリビューションと macOS の正確なバージョンを知る必要があります。 詳細については、以下を参照してください。
- [Microsoft Defender for Endpoint for Linux システム要件](microsoft-defender-endpoint-linux.md#system-requirements)  
- [Microsoft Defender for Endpoint for Mac システム要件](microsoft-defender-endpoint-mac.md#system-requirements).

## <a name="onboarding-non-windows-devices"></a>Windows 以外のデバイスのオンボーディング
Windows 以外のデバイスをオンボードするには、次の手順を実行する必要があります。
1. オンボーディングの好みの方法を選択します。

   - macOS デバイスの場合は、Microsoft Defender ATP またはサード パーティ製ソリューションを使用してオンボードを選択できます。 詳細については [、「Microsoft Defender for Endpoint for Mac」を参照してください](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/microsoft-defender-atp-mac)。
   - その他の Windows 以外のデバイスの場合は、[サードパーティとの統合による Windows 以外のデバイスのオンボード **] を選択します**。   
       
     1. ナビゲーション ウィンドウで、[相互運用性パートナー]**を**  >  **選択します**。 サード パーティ製のソリューションが一覧に表示されます。

        2. [パートナー **アプリケーション] タブで** 、Windows 以外のデバイスをサポートするパートナーを選択します。

        3. [ **パートナー ページを開く]** を選択して、パートナーのページを開きます。 ページに記載されている手順に従います。

        4. アカウントを作成するか、パートナー ソリューションをサブスクライブした後、組織のテナントのグローバル管理者がパートナー アプリケーションからのアクセス許可要求を受け入れるという要求を受け入れるステージに進む必要があります。 アクセス許可要求を注意深く読み、必要なサービスと一致している必要があります。 

        
2. サード パーティソリューションの指示に従って検出テストを実行します。

## <a name="offboard-non-windows-devices"></a>Windows 以外のオフボード デバイス

1. サード パーティのドキュメントに従って、Microsoft Defender for Endpoint からサード パーティ製ソリューションを切断します。

2. Azure のサードパーティ ソリューションのアクセス許可を削除し、ADします。
   1. [Azure portal](https://portal.azure.com) にサインインします。
   2. [Azure **Active Directory >エンタープライズ アプリケーション] を選択します**。
   3. オフボードするアプリケーションを選択します。
   4. [削除] **ボタンを** 選択します。


## <a name="related-topics"></a>関連項目
- [オンボード Windows 10 デバイス](configure-endpoints.md)
- [オンボード サーバー](configure-server-endpoints.md)
- [プロキシとインターネット接続の設定を構成する](configure-proxy-internet.md)
- [Microsoft Defender for Endpoint オンボーディングの問題のトラブルシューティング](troubleshoot-onboarding.md)