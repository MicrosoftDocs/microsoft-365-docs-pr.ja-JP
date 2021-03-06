---
title: Defender で高度な検索クエリ結果をMicrosoft 365する
description: Defender の高度な検索によって返されるクエリ結果をMicrosoft 365する
keywords: 高度な狩猟、脅威の検出、サイバー脅威の検出、Microsoft 365 Defender、microsoft 365、m365、検索、クエリ、テレメトリ、カスタム検出、スキーマ、kusto、視覚化、グラフ、フィルター、ドリルダウン
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: eccf93b019baa240a46260a28f3f0bc109345dd4
ms.sourcegitcommit: 7cc2be0244fcc30049351e35c25369cacaaf4ca9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2021
ms.locfileid: "51952598"
---
# <a name="work-with-advanced-hunting-query-results"></a>高度な検索クエリの結果を処理する

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**適用対象:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

高度な検索クエリを[](advanced-hunting-overview.md)作成して非常に正確な情報を取得することもできますが、クエリの結果を処理して、さらに詳しい分析情報を得て、特定のアクティビティとインジケーターを調査することもできます。 クエリ結果に対して次のアクションを実行できます。

- 結果を表またはグラフとして表示する
- 表とグラフのエクスポート
- 詳細なエンティティ情報にドリルダウンする
- 結果から直接クエリを調整するか、フィルターを適用する

## <a name="view-query-results-as-a-table-or-chart"></a>クエリ結果を表またはグラフとして表示する
既定では、高度な検索ではクエリ結果が表形式データとして表示されます。 グラフと同じデータを表示することもできます。 高度な検索では、次のビューがサポートされています。

| ビューの種類 | 説明 |
| -- | -- |
| **表** | クエリ結果を表形式で表示する |
| **縦棒グラフ** | X 軸上の一連の一意の項目を、高さが別のフィールドの数値を表す垂直バーとしてレンダリングされます。 |
| **積み上げ列グラフ** | x 軸上の一連の一意のアイテムを、高さが 1 つ以上の他のフィールドの数値を表す積み上げ縦棒としてレンダリングされます。 |
| **円グラフ** | 一意のアイテムを表す断面円グラフをレンダリングします。 各円グラフのサイズは、別のフィールドの数値を表します。 |
| **ドーナツ グラフ** | 一意のアイテムを表す断面円弧をレンダリングします。 各円弧の長さは、別のフィールドの数値を表します。 |
| **折れ線グラフ** | 一連の一意の項目の数値をプロットし、プロットされた値を接続する |
| **散布図** | 一連の一意の項目の数値をプロットする |
| **エリア グラフ** | 一連の一意の項目の数値をプロットし、プロットされた値の下のセクションを塗りつぶし |

### <a name="construct-queries-for-effective-charts"></a>効果的なグラフのクエリを作成する
グラフをレンダリングする場合、高度な検索では、関心のある列と集計する数値が自動的に識別されます。 意味のあるグラフを取得するには、表示する特定の値を返すクエリを作成します。 サンプル クエリと結果のグラフを次に示します。

#### <a name="alerts-by-severity"></a>重大度別のアラート
グラフを `summarize` 作成する値の数値カウントを取得するには、演算子を使用します。 以下のクエリでは、演算子 `summarize` を使用して重大度別のアラート数を取得します。

```kusto
AlertInfo
| summarize Total = count() by Severity
```
結果をレンダリングすると、各重大度値が個別の列として列グラフに表示されます。

![列グラフとして表示される高度な検索クエリ結果の画像 重要度別のアラートのクエリ結果を列グラフ ](../../media/advanced-hunting-column-chart.jpg)
 *として表示する*

#### <a name="alert-severity-by-operating-system"></a>オペレーティング システムによるアラートの重大度
演算子を使用して、 `summarize` 複数のフィールドの値をグラフ化する結果を準備することもできます。 たとえば、アラートの重大度がオペレーティング システム (OS) 全体に分散される方法を理解できます。 

次のクエリでは、演算子を使用してテーブルから OS 情報を取得し、列と列の両方の値をカウント `join` `DeviceInfo` `summarize` `OSPlatform` `Severity` します。

```kusto
AlertInfo
| join AlertEvidence on AlertId
| join DeviceInfo on DeviceId
| summarize Count = count() by OSPlatform, Severity 
```
これらの結果は、積み上げ列グラフを使用して最適に視覚化されます。

![積み上げグラフとして表示される高度な検索クエリ結果のイメージ OS によるアラートのクエリ結果と、積み上げグラフとして ](../../media/advanced-hunting-stacked-chart.jpg)
 *表示* される重大度

#### <a name="phishing-emails-across-top-ten-sender-domains"></a>上位 10 個の送信者ドメインのフィッシングメール
有限ではない値のリストを扱う場合は、演算子を使用して、最も多くのインスタンスを持つ値のみを `Top` グラフ化できます。 たとえば、フィッシングメールが最も多い上位 10 個の送信者ドメインを取得するには、次のクエリを使用します。

```kusto
EmailEvents
| where ThreatTypes has "Phish" 
| summarize Count = count() by SenderFromDomain 
| top 10 by Count
```
円グラフ ビューを使用して、上位ドメイン全体の分布を効果的に表示します。

![上位の送信者ドメイン間でのフィッシングメールの配布を示す円グラフとして表示される高度な検索クエリ結果 ](../../media/advanced-hunting-pie-chart.jpg)
 *の画像*

#### <a name="file-activities-over-time"></a>時間の間のファイル アクティビティ
演算子を `summarize` 関数と一緒に使用すると、時間のとともに特定のインジケーター `bin()` に関連するイベントを確認できます。 以下のクエリは、ファイルに関連するイベントを 30 分間隔でカウントして、そのファイルに関連するアクティビティの `invoice.doc` スパイクを表示します。

```kusto
AppFileEvents
| union DeviceFileEvents
| where FileName == "invoice.doc"
| summarize FileCount = count() by bin(Timestamp, 30m)
```
以下の線グラフは、以下を含むより多くのアクティビティを含む期間を明確に強調表示します `invoice.doc` 。 

![ファイルに関連するイベントの時間の数を示す線グラフとして表示される高度な検索クエリ ](../../media/advanced-hunting-line-chart.jpg)
 *結果のイメージ*


## <a name="export-tables-and-charts"></a>表とグラフのエクスポート
クエリを実行した後、[エクスポート] **を選択** して、結果をローカル ファイルに保存します。 選択したビューは、結果のエクスポート方法を決定します。

- **テーブル ビュー** - クエリ結果が表形式でブックとしてエクスポートMicrosoft Excelされます。
- **任意のグラフ** - クエリ結果は、レンダリングされたグラフの JPEG イメージとしてエクスポートされます。

## <a name="drill-down-from-query-results"></a>クエリ結果からドリルダウンする
クエリ結果のレコードをすばやく検査するには、対応する行を選択して [レコードの検査] パネル **を開** きます。 パネルには、選択したレコードに基づいて次の情報が表示されます。

- **アセット** - レコード内にある主な資産 (メールボックス、デバイス、およびユーザー) の要約ビューで、リスクや露出レベルなどの利用可能な情報が充実しています。
- **プロセス ツリー** - プロセス情報を含むレコードに対して生成され、利用可能なコンテキスト情報を使用して強化されます。一般に、より多くの列を返すクエリを実行すると、より豊富なプロセス ツリーが生成される可能性があります。
- **すべての詳細** - レコード内の列のすべての値  

![選択したレコードの画像(レコードを検査するパネル付き)](../../media/mtp-ah/inspect-record.png)

コンピューター、ファイル、ユーザー、IP アドレス、URL など、クエリ結果内の特定のエンティティに関する詳細情報を表示するには、エンティティ識別子を選択して、そのエンティティの詳細なプロファイル ページを開きます。

## <a name="tweak-your-queries-from-the-results"></a>結果からクエリを絞り込む
結果セットの値を右クリックすると、クエリがすばやく強化されます。 次のようなオプションを使用できます。

- 選択した値 (`==`) を明示的に検索する
- 選択した値をクエリ (`!=`) から除外する 
- クエリに値を追加するためのより高度な演算子 `contains`、`starts with`、および `ends with` を取得する 

![高度な検索結果セットのイメージ](../../media/advanced-hunting-results-filter.png)

## <a name="filter-the-query-results"></a>クエリ結果をフィルター処理する
右に表示されるフィルターは、結果セットの要約を提供します。 各列には、その列で見つかった個別の値とインスタンスの数を一覧表示する独自のセクションがあります。

クエリを絞り込むには、含める値または除外する値のボタンを選択し、[クエリの実行 `+` `-` ] **を選択します**。

![高度な捜索フィルターの画像](../../media/advanced-hunting-filter.png)

フィルターを適用してクエリを変更し、クエリを実行すると、結果がそれに応じて更新されます。

>[!NOTE]
>この記事の一部のテーブルは、Microsoft Defender for Endpoint では使用できない場合があります。 [Defender を有効Microsoft 365、](m365d-enable.md)より多くのデータ ソースを使用して脅威を探します。 「Advanced Hunting queries from Microsoft Defender for Endpoint 」 の手順に従って、高度なハンティング ワークフローを Microsoft Defender for Endpoint から Microsoft 365 Defender に[移動できます](advanced-hunting-migrate-from-mde.md)。

## <a name="related-topics"></a>関連項目
- [高度な追求の概要](advanced-hunting-overview.md)
- [クエリ言語の説明](advanced-hunting-query-language.md)
- [共有クエリを使用する](advanced-hunting-shared-queries.md)
- [デバイス、メール、アプリ、ID 全体で探す](advanced-hunting-query-emails-devices.md)
- [スキーマを理解する](advanced-hunting-schema-tables.md)
- [クエリのベスト プラクティスを適用する](advanced-hunting-best-practices.md)
- [カスタム検出の概要](custom-detections-overview.md)
