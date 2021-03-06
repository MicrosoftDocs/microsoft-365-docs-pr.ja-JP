---
title: Microsoft Defender for Endpoint のデバイスの正常性とコンプライアンス レポート
description: デバイスの正常性とコンプライアンス レポートを使用して、デバイスの正常性状態の検出、ウイルス対策の状態、OS プラットフォーム、Windows 10バージョンを追跡する
keywords: 正常性状態、ウイルス対策、OS プラットフォーム、Windows 10 バージョン、バージョン、正常性、コンプライアンス、状態
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
ms.openlocfilehash: 35100a4b8bdaee23c427816450e948ced9ed3191
ms.sourcegitcommit: 22505ce322f68a2d0ce70d71caf3b0a657fa838a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "51860293"
---
# <a name="device-health-and-compliance-report-in-microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpoint のデバイスの正常性とコンプライアンス レポート

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

デバイスの状態レポートは、組織内のデバイスに関する高レベルの情報を提供します。 このレポートには、センサーの正常性状態、ウイルス対策の状態、OS プラットフォーム、および最新バージョンを示すWindows 10含まれています。

ダッシュボードは、デバイス レポートのイメージという 2 ![ つのセクションに構成されています。](images/device-reports.png)
 
Section | 説明
:---|:---
1 | デバイスの傾向
2 | デバイスの概要 (現在の日)
 
 
## <a name="device-trends"></a>デバイスの傾向 
既定では、デバイスの傾向には、最新の 1 日で終わる 30 日間の期間のデバイス情報が表示されます。 組織で発生している傾向についてより良い視点を得るために、表示される期間を調整してレポート期間を微調整できます。 期間を調整するには、ドロップダウン オプションから時間範囲を選択します。
 
- 30 日間
- 3 か月
- 6 か月
- Custom

>[!NOTE]
>これらのフィルターは、[デバイスの傾向] セクションにのみ適用されます。 [デバイスの概要] セクションには影響を及ぼします。

## <a name="device-summary"></a>デバイスの概要 
デバイスの傾向はデバイス情報の傾向を示しますが、デバイスの概要には、現在の日を対象にしたデバイス情報が表示されます。 

>[!NOTE]
>[概要] セクションに反映されるデータの範囲は、現在の日付の 180 日前です。 たとえば、今日の日付が 2019 年 3 月 27 日の場合、概要セクションのデータには、2018 年 9 月 28 日から 2019 年 3 月 27 日の数値が反映されます。<br>
> [傾向] セクションに適用されるフィルターは、[概要] セクションには適用されません。 
 
[デバイスの傾向] セクションでは、対応するフィルターが適用されたデバイス リストにドリルダウンできます。 たとえば、センサーの正常性状態カードの [非アクティブ] バーをクリックすると、センサーの状態が非アクティブなデバイスのみを表示する結果が表示されるデバイスの一覧が表示されます。 
 
 
 
## <a name="device-attributes"></a>デバイス属性
レポートは、次のデバイス属性を表示するカードで構成されます。
 
- **正常性状態**: デバイス上のセンサー状態に関する情報を表示し、アクティブなデバイス、通信障害、非アクティブ、またはセンサー データが見られないデバイスの集計ビューを提供します。
  
- **アクティブなデバイスのウイルス対策Windows 10:** デバイスの数とデバイスの状態をMicrosoft Defender ウイルス対策。
    
- **OS プラットフォーム**: 組織内に存在する OS プラットフォームの配布を示します。 
 
- **Windows 10バージョン**: 組織のデバイスとWindows 10の配布を示します。
 
 
 
## <a name="filter-data"></a>データをフィルター処理する
 
指定されたフィルターを使用して、特定の属性を持つデバイスを含めるか除外します。

デバイス属性から適用する複数のフィルターを選択できます。 
 
>[!NOTE]
>これらのフィルターは、 **レポート内のすべての** カードに適用されます。
 
たとえば、アクティブ センサーの正常性状態を持Windows 10デバイスに関するデータを表示するには、次の方法を実行します。
 
1. [ **フィルター] >センサーの正常性状態>アクティブです**。
2. 次に **、[OS プラットフォーム]** を> Windows 10します。
3. **[適用]** を選択します。


## <a name="related-topic"></a>関連トピック
- [脅威保護レポート](threat-protection-reports.md)
