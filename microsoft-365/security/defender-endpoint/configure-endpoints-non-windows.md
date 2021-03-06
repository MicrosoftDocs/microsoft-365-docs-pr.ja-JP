---
title: Microsoft Defender for Endpoint サービスWindowsデバイス以外のデバイスをオンボードする
description: Microsoft Defender for Endpoint サービスWindowsセンサー データを送信できるよう、デバイス以外のデバイスを構成します。
keywords: オンボードの非Windowsデバイス、macos、Linux、デバイス管理、エンドポイント デバイス用 Microsoft Defender の構成
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
ms.openlocfilehash: 4aff505f9f35b6144360eed5992ac36cf0847617
ms.sourcegitcommit: 718759c7146062841f7eb4a0a9a8bdddce0139b0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2021
ms.locfileid: "53454711"
---
# <a name="onboard-non-windows-devices"></a>Windows 以外のデバイスをオンボードする

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**プラットフォーム**
- macOS
- Linux

>Defender for Endpoint を体験してみませんか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-nonwindows-abovefoldlink) 

Defender for Endpoint は、セキュリティ プラットフォームだけでなく、Windowsプラットフォームにも一元的なセキュリティWindows提供します。 サポートされているさまざまなオペレーティング システム (OS) からのアラートを、組織のネットワークMicrosoft 365 Defender保護するために役立ちます。 

統合を機能するには、Defender for Endpoint と互換性のある Linux ディストリビューションと macOS の正確なバージョンを知る必要があります。 詳しくは、次のトピックを参照してください。
- [Microsoft Defender for Endpoint on Linux システム要件](microsoft-defender-endpoint-linux.md#system-requirements)  
- [Microsoft Defender for Endpoint on macOS system requirements](microsoft-defender-endpoint-mac.md#system-requirements).

## <a name="onboarding-non-windows-devices"></a>非デバイスのオンボードWindowsする
非デバイスをオンボードするには、次の手順を実行Windows必要があります。
1. オンボーディングの好みの方法を選択します。

   - macOS デバイスの場合は、Microsoft Defender for Endpoint またはサード パーティ製ソリューションを使用してオンボードを選択できます。 詳細については [、「Microsoft Defender for Endpoint on Mac」を参照してください](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-mac)。

   - その他の非デバイスWindows、サードパーティとの統合を通じてWindowsデバイスのオンボード **を選択します**。   
    1. ナビゲーション ウィンドウで、[相互運用性パートナー]**を**  >  **選択します**。 サード パーティ製のソリューションが一覧に表示されます。
    2. [パートナー **アプリケーション] タブ** で、ユーザー以外のデバイスをサポートするパートナー Windowsします。
    3. [ **パートナー ページを開く]** を選択して、パートナーのページを開きます。 ページに記載されている手順に従います。
    4. アカウントを作成するか、パートナー ソリューションをサブスクライブした後、組織のテナントのグローバル管理者がパートナー アプリケーションからのアクセス許可要求を受け入れるという要求を受け入れるステージに進む必要があります。 アクセス許可要求を注意深く読み、必要なサービスと一致している必要があります。 

        
2. サード パーティソリューションの指示に従って検出テストを実行します。

## <a name="offboard-non-windows-devices"></a>オフボードの非Windowsデバイス

1. サード パーティのドキュメントに従って、Microsoft Defender for Endpoint からサード パーティ製ソリューションを切断します。

2. Azure のサードパーティ ソリューションのアクセス許可を削除し、ADします。
   1. [Azure portal](https://portal.azure.com) にサインインします。
   2. [アプリケーション **Azure Active Directory > Enterprise] を選択します**。
   3. オフボードするアプリケーションを選択します。
   4. [削除] **ボタンを** 選択します。


## <a name="related-topics"></a>関連項目
- [Windows 10 デバイスのオンボード](configure-endpoints.md)
- [オンボード サーバー](configure-server-endpoints.md)
- [プロキシとインターネット接続の設定を構成する](configure-proxy-internet.md)
- [Microsoft Defender for Endpoint オンボーディングの問題のトラブルシューティング](troubleshoot-onboarding.md)
