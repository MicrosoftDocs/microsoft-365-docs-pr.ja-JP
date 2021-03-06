---
title: デバイスタイムラインのテクニック
description: Microsoft Defender for Endpoint のデバイス タイムラインについて
keywords: デバイスタイムライン、エンドポイント、MITRE、MITRE ATT&CK、テクニック、戦術
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 6b080c209292c8cac1aa64d748926734f4be964c
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51185469"
---
# <a name="techniques-in-the-device-timeline"></a>デバイスタイムラインのテクニック


**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)


特定のデバイスで発生したイベントを分析することで、調査に関するより多くの洞察を得られる可能性があります。 まず、[デバイス] リストから目的のデバイス [を選択します](machines-view-overview.md)。 デバイス ページで、[タイムライン] タブを **選択** して、デバイスで発生したイベントを表示できます。

## <a name="understand-techniques-in-the-timeline"></a>タイムラインのテクニックを理解する

>[!IMPORTANT]
>一部の情報は、パブリック プレビューで事前リリースされた製品機能に関連します。これは、商用リリース前に大幅に変更される可能性があります。 Microsoft は、ここに記載された情報に関して、明示または黙示を問わず、いかなる保証も行いません。

Microsoft Defender for Endpoint では **、Techniques は** イベント タイムラインの追加データ型です。 技術は [、MITRE ATT](https://attack.mitre.org/) および CK の手法またはサブ&関連するアクティビティに関するより多くの洞察を提供します。 

この機能は、分析者がデバイスで観察されたアクティビティを理解するのを支援することで、調査エクスペリエンスを簡素化します。 アナリストは、さらに調査を行う場合があります。

パブリック プレビューの場合、テクニックは既定で使用できます。デバイスのタイムラインを表示するときにイベントと共に表示されます。 

![デバイス タイムラインのスクリーンショットのテクニック](images/device-timeline-2.png)

テクニックは太字で強調表示され、左側に青いアイコンが表示されます。 対応する MITRE ATT&CK ID とテクニック名は、[追加情報] の下にタグとして表示されます。 

検索オプションとエクスポート オプションは、[テクニック] でも使用できます。

## <a name="investigate-using-the-side-pane"></a>サイド ウィンドウを使用して調査する

[テクニック] を選択して、対応するサイド ウィンドウを開きます。 ここでは、関連する ATT や CK の手法、&説明など、追加情報と分析情報を確認できます。 

特定の *攻撃手法を選択* して、関連する ATT&CK テクニック ページを開き、詳細を確認できます。

右側に青いアイコンが表示されている場合は、エンティティの詳細をコピーできます。 たとえば、関連ファイルの SHA1 をコピーするには、青いページ アイコンを選択します。

![エンティティの詳細のコピー](images/techniques-side-pane-clickable.png)

コマンド ラインでも同じ操作を実行できます。

![コマンド ラインのコピー](images/techniques-side-pane-command.png)


## <a name="investigate-related-events"></a>関連イベントの調査

高度な [検索を使用して](advanced-hunting-overview.md) 、選択したテクニックに関連するイベントを検索するには、[関連イベントのハント **] を選択します**。 これにより、テクニックに関連するイベントを検索するクエリを含む高度な検索ページが表示されます。

![関連イベントのハント](images/techniques-hunt-for-related-events.png)

>[!NOTE]
>[テクニック] **サイド** ウィンドウから [関連イベントのハント] ボタンを使用してクエリを実行すると、特定された手法に関連するイベントはすべて表示されますが、クエリ結果にはテクニック自体は含めされません。


## <a name="customize-your-device-timeline"></a>デバイスのタイムラインをカスタマイズする

デバイスタイムラインの右上で、タイムライン内のイベントとテクニックの数を制限する日付範囲を選択できます。 

公開する列をカスタマイズできます。 データ型またはイベント グループ別にフラグが設定されたイベントをフィルター処理することもできます。

### <a name="choose-columns-to-expose"></a>公開する列を選択する
[列の選択] ボタンを選択すると、タイムラインで公開する列 **を選択** できます。

![列のカスタマイズ](images/filter-customize-columns.png)

そこから、含める情報セットを選択できます。

### <a name="filter-to-view-techniques-or-events-only"></a>フィルターを使用して、手法またはイベントのみを表示する

イベントまたは手法のみを表示するには、デバイスタイムラインから [ **フィルター** ] を選択し、表示するデータ型を選択します。

![フィルターのスクリーンショット](images/device-timeline-filters.png)



## <a name="see-also"></a>関連項目
- [デバイスの一覧を表示および整理する](machines-view-overview.md)
- [Microsoft Defender for Endpoint デバイスのタイムライン イベント フラグ](device-timeline-event-flag.md) 


 
