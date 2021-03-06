---
title: Defender の高度な検索クエリ言語Microsoft 365する
description: 最初の脅威の捜索クエリを作成し、一般的な演算子と高度な捜索クエリ言語の他の側面について学習する
keywords: 高度な検索、脅威の検出、サイバー脅威の検出、Microsoft 365 Defender、microsoft 365、m365、検索、クエリ、言語、学習、最初のクエリ、テレメトリ、イベント、テレメトリ、カスタム検出、スキーマ、kusto、演算子、データ型、powershell ダウンロード、クエリの例
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
ms.openlocfilehash: 14287fb6dea9dda8accb580246b383f0427c3b3f
ms.sourcegitcommit: 7cc2be0244fcc30049351e35c25369cacaaf4ca9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2021
ms.locfileid: "51952622"
---
# <a name="learn-the-advanced-hunting-query-language"></a>高度な捜索のクエリ言語について学習する

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**適用対象:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

高度な捜索は、[Kusto クエリ言語](/azure/kusto/query/)に基づいています。 Kusto 演算子とステートメントを使用して、特殊なスキーマ内の情報を検索するクエリを作成 [できます](advanced-hunting-schema-tables.md)。 これらの概念をよりよく理解するために、最初のクエリを実行します。

## <a name="try-your-first-query"></a>最初のクエリを試してみる

セキュリティ Microsoft 365で、[ハンティング] に移動 **して** 最初のクエリを実行します。 次の例を使用してください。

```kusto
// Finds PowerShell execution events that could involve a download
union DeviceProcessEvents, DeviceNetworkEvents
| where Timestamp > ago(7d)
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
// Suspicious commands
| where ProcessCommandLine has_any("WebClient",
 "DownloadFile",
 "DownloadData",
 "DownloadString",
"WebRequest",
"Shellcode",
"http",
"https")
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

**[高度な検索でこのクエリを実行する](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2TW0sCURSF93PQfxh8Moisp956yYIgQtLoMaYczJpbzkkTpN_et_dcdPQkcpjbmrXXWftyetKTQG5lKqmMpeB9IJksJJKZDOWdZ8wKeP5wvcm3OLgZbMXmXCmIxjnYIfcAVgYvRi8w3TnfsXEDGAG47pCCZXyP5ViO4KeNbt-Up-hEuJmB6lvButnY8XSL-cDl0M2I-GwxVX8Fe2H5zMzHiKjEVB0eEsnBrszfBIWuXOLrxCJ7VqEBfM3DWUYTkNKrv1p5y3X0jwetemzOQ_NSVuuXZ1c6aNTKRaN8VvWhY9n7OS-o6J5r7mYeQypdEKc1m1qfiqpjCSuspsDntt2J61bEvTlXls5AgQfFl5bHM_gr_BhO2RF1rztoBv2tWahrso_TtzkL93KGMGZVr2pe7eWR-xeZl91f_113UOsx3nDR4Y9j5R6kaCq8ajr_YWfFeedsd27L7it-Z6dAZyxsJq1d9-2ZOSzK3y2NVd8-zUPjtZaJnYsIH4Md7AmdeAcd2Cl1XoURc5PzXlfU8U9P54WcswL6t_TW9Q__qX-xygQAAA&runQuery=true&timeRangeId=week)**

### <a name="describe-the-query-and-specify-the-tables-to-search"></a>クエリを記述し、検索するテーブルを指定する
クエリの先頭に短いコメントが追加され、それが何を行うのかを説明しています。 このコメントは、後でクエリを保存し、組織内の他のユーザーと共有する場合に役立ちます。 

```kusto
// Finds PowerShell execution events that could involve a download
```

クエリ自体は、通常、テーブル名の後にパイプ ( ) で始まる複数の要素で始まる `|` 。 この例では、まず 2 つのテーブルの共用体を作成し、必要に応じてパイプ要素  `DeviceProcessEvents` `DeviceNetworkEvents` を追加します。

```kusto
union DeviceProcessEvents, DeviceNetworkEvents
```
### <a name="set-the-time-range"></a>時間範囲を設定する
最初のパイプ処理された要素は、前の 7 日間にスコープ設定された時間フィルターです。 時間範囲を制限すると、クエリのパフォーマンスが向上し、管理可能な結果が返され、時間が取れなかることができます。

```kusto
| where Timestamp > ago(7d)
```

### <a name="check-specific-processes"></a>特定のプロセスを確認する
時間範囲の直後に、PowerShell アプリケーションを表すプロセス ファイル名を検索します。

```kusto
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
```

### <a name="search-for-specific-command-strings"></a>特定のコマンド文字列を検索する
その後、クエリは、PowerShell を使用してファイルをダウンロードするために通常使用されるコマンド ライン内の文字列を検索します。

```kusto
// Suspicious commands
| where ProcessCommandLine has_any("WebClient",
    "DownloadFile",
    "DownloadData",
    "DownloadString",
    "WebRequest",
    "Shellcode",
    "http",
    "https")
```

### <a name="customize-result-columns-and-length"></a>結果の列と長さをカスタマイズする 
クエリで検索するデータが明確に識別されたので、結果の外観を定義できます。 `project` 特定の列を返し、 `top` 結果の数を制限します。 これらの演算子は、結果の形式が適切で、合理的に大きく、処理が容易であることを確認するのに役立ちます。

```kusto
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

[クエリ **の実行] を** 選択して結果を表示します。 クエリ エディターの右上にある展開アイコンを使用して、検索クエリと結果に注目します。 

![高度な検索クエリ エディターの Expand コントロールのイメージ](../../media/advanced-hunting-expand.png)

>[!TIP]
>クエリ結果をグラフとして表示し、フィルターをすばやく調整できます。 ガイダンスについては、「 [クエリ結果の操作」を参照してください。](advanced-hunting-query-results.md)

## <a name="learn-common-query-operators"></a>一般的なクエリ演算子の詳細

最初のクエリを実行し、そのコンポーネントに関する一般的なアイデアを得たばかりです。 少しバックトラックし、いくつかの基本を学ぶ時間です。 高度な捜索で使用される Kusto クエリ言語は、次のような一般的な演算子をサポートします。

| 演算子 | 説明および使用法 |
|--|--|
| `where` | 述語に適合する行のサブセットにテーブルをフィルター処理します。 |
| `summarize` | 入力テーブルの内容を集約したテーブルを作成します。 |
| `join` | 各テーブルから指定された列の値を照合して、2 つのテーブルの行を結合し、新しいテーブルを作成します。 |
| `count` | 入力レコード セットのレコード数を返します。 |
| `top` | 指定された列によって並べ替えられた最初の N レコードを返します。 |
| `limit` | 指定された行数まで返します。 |
| `project` | 新しい計算列を含める、名前を変更する、またはドロップする列を選択し、挿入します。 |
| `extend` | 計算列を作成し、結果セットに追加します。 |
| `makeset` |  Expr がグループ内でとる個別の値のセットの動的 (JSON) 配列を返します。 |
| `find` | テーブルのセットで述語と一致する行を検索します。 |

これらの演算子の実際の例を見るには、高度な捜索の [**はじめに**] セクションから実行します。

## <a name="understand-data-types"></a>データ型について

高度な検索では、次の一般的な種類を含む Kusto データ型がサポートされています。

| データ型 | 説明とクエリの意味 |
|--|--|
| `datetime` | 通常、イベントのタイムスタンプを表すデータと時刻の情報。 [サポートされている日時形式を参照してください。](/azure/data-explorer/kusto/query/scalar-data-types/datetime) |
| `string` | 文字列は、UTF-8 ( ) または二重引用符 ( `'` ) で囲まれます `"` 。 [文字列の詳細](/azure/data-explorer/kusto/query/scalar-data-types/string) |
| `bool` | このデータ型は、サポート `true` または `false` 状態です。 [サポートされているリテラルと演算子を参照してください。](/azure/data-explorer/kusto/query/scalar-data-types/bool) |
| `int` | 32 ビット整数  |
| `long` | 64 ビット整数 |

これらのデータ型の詳細については [、「Kusto スカラー データ型」を参照してください](/azure/data-explorer/kusto/query/scalar-data-types/)。

## <a name="get-help-as-you-write-queries"></a>クエリを記述するときにヘルプを参照する
次の機能を利用して、クエリをより速く記述します。
- **Autosuggest**-you write queries, advanced hunting providess suggestions from IntelliSense. 
- **スキーマ ツリー**: テーブルの一覧とその列を含むスキーマ表現が、作業領域の横に表示されます。 詳細については、アイテムにカーソルを合わせてください。 アイテムをダブルクリックして、クエリ エディターに挿入します。
- **[スキーマ参照](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)**-テーブルと列の説明、サポートされているイベントの種類 (値) とサンプル クエリを含むポータル `ActionType` 内参照

## <a name="work-with-multiple-queries-in-the-editor"></a>エディターで複数のクエリを処理する
クエリ エディターを使用して、複数のクエリを実験できます。 複数のクエリを使用するには、次のコマンドを実行します。

- 各クエリを空の行で分離します。
- クエリを実行する前に、クエリの任意の部分にカーソルを置き、そのクエリを選択します。 これにより、選択したクエリだけが実行されます。 別のクエリを実行するには、カーソルを適切に移動し、[クエリの実行] **を選択します**。

![複数のクエリを含むクエリ エディターのイメージ](../../media/mtp-ah/ah-multi-query.png)

## <a name="use-sample-queries"></a>サンプル クエリを使用する

[**はじめに**] セクションでは、一般的に使用されている演算子を使用した簡単なクエリーをいくつか提供します。 これらのクエリを実行して、少し変更してみてください。

![高度な捜索ウィンドウの画像](../../media/advanced-hunting-get-started.png)

>[!NOTE]
>基本的なクエリ サンプルとは別に、特定の脅威の捜索シナリオの[共有クエリ](advanced-hunting-shared-queries.md)にアクセスすることもできます。 ページの左側またはクエリ リポジトリの共有クエリ[をGitHubします](https://aka.ms/hunting-queries)。

## <a name="access-query-language-documentation"></a>クエリ言語のドキュメントにアクセスする

Kusto クエリ言語およびサポートされる演算子の詳細については、「[Kusto クエリ言語のドキュメント](/azure/kusto/query/)」を参照してください。

>[!NOTE]
>この記事の一部のテーブルは、Microsoft Defender for Endpoint では使用できない場合があります。 [Defender を有効Microsoft 365、](m365d-enable.md)より多くのデータ ソースを使用して脅威を探します。 「Advanced Hunting queries from Microsoft Defender for Endpoint 」 の手順に従って、高度なハンティング ワークフローを Microsoft Defender for Endpoint から Microsoft 365 Defender に[移動できます](advanced-hunting-migrate-from-mde.md)。

## <a name="related-topics"></a>関連項目
- [高度な追求の概要](advanced-hunting-overview.md)
- [クエリ結果を操作する](advanced-hunting-query-results.md)
- [共有クエリを使用する](advanced-hunting-shared-queries.md)
- [デバイス、メール、アプリ、ID 全体で探す](advanced-hunting-query-emails-devices.md)
- [スキーマを理解する](advanced-hunting-schema-tables.md)
- [クエリのベスト プラクティスを適用する](advanced-hunting-best-practices.md)