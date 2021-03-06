---
title: 高度な電子情報開示でのタグ付けと関連性のトレーニング
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 8576cc86-d51b-4285-b54b-67184714cc62
ROBOTS: NOINDEX, NOFOLLOW
description: Advanced eDiscovery の関連性トレーニング ステージで、タグ付けしてから 40 ファイルのトレーニング サンプルを使用する手順について説明します。
ms.openlocfilehash: ae4a9f2e9fd87fdd0679bbfd8f287b6eaa98e41f
ms.sourcegitcommit: 5ba0015c1554048f817fdfdc85359eee1368da64
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "49769222"
---
# <a name="tagging-and-relevance-training-in-advanced-ediscovery"></a>高度な電子情報開示でのタグ付けと関連性のトレーニング
  
この記事では、Advanced eDiscovery の関連性トレーニング モジュールを操作する手順について説明します。
  
Advanced eDiscovery で評価が完了し、関連性トレーニング ステージに入った後、40 ファイルのトレーニング サンプルがタグ付けのために [タグ] タブに表示されます。
  
## <a name="performing-relevance-training"></a>関連性トレーニングの実行

1. [関連性 **タグ] \> タブ** で、[タグ付け] ウィンドウが既定で左側のウィンドウに表示され、タグ付け用のサンプル ファイルが一度に 1 つ表示されます。

    ![関連性タグ パネル](../media/0cf19ab4-b427-4a7f-8749-0f4ed9afaf58.png)
  
    [タグ **] タブ** には、ファイルの表示名が表示されます。 パス、電子メールの件名、タイトル、またはユーザー定義の名前を指定できます。 ID、ファイル パス、またはテキスト パスは、ファイルのパスを右クリックしてコピーできます。

    [ **タグ** ] タブのタグ付け統計には、ファイル サンプル番号 (左側のウィンドウの上部)、サンプル内の合計ファイルの現在表示されているファイルの数 (右ウィンドウの下部)、およびサンプル内のタグ付けされたファイルの現在の総数 (左側のウィンドウの下部) が表示され、ファイルのタグ付け時に変更されます。 これは、評価、トレーニング、キャッチアップ、またはテストで行われた関連性のタグ付けに適用されます。

    コメント、タグ、およびファミリ ファイルの存在を示すアイコンが、ファイルの上のバーのファイル ビューに表示されます。

2. 次の表に示すように、[タグ付け] オプション アイコン ボタンまたはキーボード ショートカットを使用して、ケースの問題に対するファイルの関連性を判断し、ファイルにタグを付けることができます。

   |**タグ付けオプション**|**説明**|**ショートカット キー**|**一括タグ付けキーボード ショートカット (複数の問題の場合)**|
   |-----|-----|-----|-----|
   |R  <br/> |関連する  <br/> |Z  <br/> |`Shift + Z`  <br/> |
   |NR  <br/> |関連性が高い  <br/> |X  <br/> |`Shift + X`  <br/> |
   |スキップ  <br/> |スキップ  <br/> |C  <br/> |`Shift + A`  <br/> |
   |||||

   - ファイルに複数の問題が存在する場合、1 つの問題をタグ付けした後、選択内容は次の問題 (存在する場合) に移動します。  

   - キーワードを強調表示するときに管理者またはケース マネージャーによって定義されたキーワード (関連性の設定 強調表示されたキーワード) は、タグ付け中に関連するファイルを識別するのに役立つ (指定された色で) 表示されます。 \> キーワードに下線が 2 つ表示されている場合は、クリックすると、キーワードの説明を含むツール ヒントを表示できます。

     必要に応じて、[タグ] **タブで** [タグの設定] **をクリックして** 、次のオプションを設定します。

      ![関連性タグの設定](../media/533e89fa-7eb4-409e-ab07-f5aab9296dd8.png)
  
   - **一** 括タグ : [すべて] を選択して、選択したファイルのタグをすべての問題 (既にタグ付けされた問題を上書きする) を設定するか、[残り]を選択してタグを残りのタグに適用することで、ファイルに複数の問題を割り当てるには、このオプションを使用します。 選択したオプションは、そのユーザーが変更するまで、このユーザーのすべてのケースに対して有効なままです (設定は、すべてのユーザーのケースに対してユーザーごとに設定されます)。

   - **自動タグ**: ファイルの他の問題を 1 つの関連タグ付けの後に関連しないとして設定するには、このチェック ボックスをオンにします。

   - **[自動進** む]: 最後の問題またはタグ付けされていない問題のみをタグ付けするときに、表示されるファイルの選択を次のファイルに移動するには、このチェック ボックスをオンにします。

    スキップされたファイルは、関連性トレーニングと関連性スコアリングの目的では考慮されません。

3. ファイルに関連付けられたフリーテキスト コメントは、左側のウィンドウ ドロップダウン リストの **[コメント** ] オプションを使用して表示および編集できます。 (省略可能)

4. タグ付けのガイドラインは、左側のウィンドウ ドロップダウン リストで [タグ付けガイドライン] オプションを選択すると表示できます。

5. リスト内のすべてのファイルのタグ付けを完了し、結果を計算する準備ができたら、[計算] を **クリックします**。 [ **トラック] タブ** が表示されます。  

## <a name="working-with-the-sample-files-list"></a>サンプル ファイルリストの操作

サンプル ファイルの一覧を使用すると、トレーニング サンプル内のファイルの一覧を表示し、1 つ以上のファイルに対してさまざまなアクションを実行できます。 [関連性 **タグ] タブ** の [サンプル ファイル] 左側のウィンドウには、評価、トレーニング、キャッチアップ、および不整合プロセスで処理するサンプル ファイルの一覧が \> 表示されます。
  
1. [関連性 **タグ] \> タブで** 、左側のウィンドウドロップダウン リストで [サンプル ファイル] を選択します。 サンプル ファイルは、左側のウィンドウに一覧表示されます。

    ![関連性タグのサンプル ファイル一覧](../media/fd058bdd-645a-4af1-a1eb-bff08581cb18.png)
  
2. [サンプル] ボックスまたは [ファイル] ボックスに番号を入力または選択して、特定のサンプル番号またはファイル **番号****を** 選択します。

   - ファイル シーケンス番号は、[タグ] タブに表示されるファイル一覧の左側の列 **に表示** されます。ヘッダーをクリックすると、ファイルの元の表示順序が元の順序に戻されます。

   - ファイル行をクリックすると、右側のウィンドウにコンテンツが表示されます。

   - 下のメニュー バーオプションを使用して、現在のサンプル内のファイル間を移動します。 さらに、ナビゲーション キーボード ショートカットも使用できます。
  
     - サンプルの最初のファイルに移動するには、次の方法を実行します。 `Shift + Ctrl + <`

     - サンプル内の前のファイルに移動するには、次の方法を実行します。 `Shift + <`

     - サンプルの次のファイルに移動するには、次の手順を実行します。 `Shift + >`

     - サンプルの最後のファイルに移動するには、次の方法を実行します。 `Shift + Ctrl + >`
