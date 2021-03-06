---
title: Microsoft Defender for Endpoint にオンボードされているデバイスを取得する
description: Intune で管理されたデバイスの Microsoft Defender for Endpoint へのオンボーディングを追跡し、オンボーディング 速度を向上します。
keywords: オンボード、Intune 管理、Microsoft Defender for Endpoint、Microsoft Defender、Windows Defender、構成管理
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 7798f3b6bd2f99d48a8fa85ecf088023f4629b7b
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2021
ms.locfileid: "52841572"
---
# <a name="get-devices-onboarded-to-microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpoint にオンボードされているデバイスを取得する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

オンボードされた各デバイスは、追加のエンドポイント検出と応答 (EDR) センサーを追加し、ネットワーク内の侵害アクティビティに対する可視性を向上します。 また、オンボーディングにより、デバイスで脆弱なコンポーネントやセキュリティ構成の問題をチェックし、攻撃中に重大な修復アクションを受け取る可能性があります。

デバイスのオンボーディングを追跡および管理する前に、
- [Intune 管理にデバイスを登録する](configure-machines.md#enroll-devices-to-intune-management)
- [必要なアクセス許可を持っている必要があります。](configure-machines.md#obtain-required-permissions)

## <a name="discover-and-track-unprotected-devices"></a>保護されていないデバイスの検出と追跡

オンボーディング カードは、実際に Defender for Endpoint にオンボードされた Windows 10 デバイスの数と Intune で管理された Windows 10 デバイスの総数を比較することで、オンボーディング レートの概要を提供します。

![デバイス構成管理オンボード カード](images/secconmgmt_onboarding_card.png)<br>
*オンボード デバイスと Intune で管理されているデバイスの合計数と比較Windows 10カード*

>[!NOTE]
>セキュリティ センター構成マネージャー、オンボーディング スクリプト、または Intune プロファイルを使用しないその他のオンボーディング 方法を使用した場合、データの不一致が発生する可能性があります。 これらの不一致を解決するには、Defender for Endpoint オンボーディングに対応する Intune 構成プロファイルを作成し、そのプロファイルをデバイスに割り当てる必要があります。

## <a name="onboard-more-devices-with-intune-profiles"></a>Intune プロファイルを使用して他のデバイスをオンボードする

Defender for Endpoint には、デバイスをオンボーディングするための便利な[Windows 10があります](onboard-configure.md)。 ただし、Intune で管理されるデバイスの場合は、Intune プロファイルを活用して Defender for Endpoint センサーを便利に展開してデバイスを選択し、これらのデバイスをサービスに効果的にオンボーディングできます。

[オンボード] **カードで、[** その他のデバイス **の** オンボード] を選択して、Intune でプロファイルを作成して割り当てる。 このリンクを使用すると、Intune のデバイス コンプライアンス ページに移動し、オンボーディング状態の同様の概要を示します。

![Intune デバイス管理の Microsoft Defender for Endpoint デバイスコンプライアンス ページ](images/secconmgmt_onboarding_1deviceconfprofile.png)<br>
   *Intune デバイス管理の Microsoft Defender for Endpoint デバイスコンプライアンス ページ*

>[!TIP]
>または、[すべてのサービス] から Microsoft Azure ポータルの [[Defender](https://portal.azure.com/) for Endpoint オンボーディング コンプライアンス] ページに移動> Intune >**デバイス** コンプライアンス > Microsoft Defender ATP。

>[!NOTE]
> 最新のデバイス データを表示する場合は、[ATP センサーのないデバイスの一覧 **] をクリックします**。

[デバイスコンプライアンス] ページで、Defender for Endpoint センサーの展開専用の構成プロファイルを作成し、そのプロファイルをオンボードするデバイスに割り当てる。 これを行うには、次のいずれかを実行できます。

- [ **デバイス構成プロファイルの作成] を選択して、定義済** みのデバイス構成プロファイルから開始する ATP センサーを構成します。
- デバイス構成プロファイルを最初から作成します。

詳細については [、「Intune デバイス構成プロファイルを使用してデバイスを Defender for Endpoint にオンボードする」を参照してください](/intune/advanced-threat-protection#onboard-devices-by-using-a-configuration-profile)。

>Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>関連項目
- [デバイスが正しく構成されていることを確認する](configure-machines.md)
- [Defender for Endpoint セキュリティ ベースラインへのコンプライアンスを強化する](configure-machines-security-baseline.md)
- [ASR ルールの展開と検出を最適化する](configure-machines-asr.md)
