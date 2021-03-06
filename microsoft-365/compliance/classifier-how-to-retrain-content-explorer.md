---
title: コンテンツ エクスプローラーで分類子を再トレーニングする方法
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: コンテンツ エクスプローラーでトレーニング可能な分類子にフィードバックを提供する方法について学習します。
ms.openlocfilehash: ef0539a3d474ffecaeac8633b4a58aa068a5c182
ms.sourcegitcommit: f3d1009840513703c38bab99a6e13a3656eae5ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2021
ms.locfileid: "52793066"
---
# <a name="how-to-retrain-a-classifier-in-content-explorer"></a>コンテンツ エクスプローラーで分類子を再トレーニングする方法

トレーニングMicrosoft 365分類子は、さまざまな種類のコンテンツを認識するトレーニングツールです。 トレーニングが完了したら、このラベルを使用して、Office、通信コンプライアンス ポリシー、および保持ラベル ポリシーを適用するためのアイテムを識別できます。

この記事では、追加のフィードバックを提供することで、カスタムトレーニング可能な分類子といくつかの事前トレーニング済みの分類子のパフォーマンスを向上させる方法を示します。

分類子の種類の詳細については、「トレーニング可能な分類子について」 [を参照してください](classifier-learn-about.md)。

チューニングと再トレーニングプロセスの概要については、このビデオをご覧ください。 詳細を取得するには、この記事の全文を読む必要があります。

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyGMs]


## <a name="permissions"></a>アクセス許可

コンプライアンス センターで分類子にMicrosoft 365するには、次のMicrosoft 365使用します。

- 分類子をトレーニングするには、コンプライアンス管理者の役割またはコンプライアンス データ管理者が必要です

次のシナリオで分類子を使用するには、次のアクセス許可を持つアカウントが必要です。

- アイテム保持ラベル ポリシーのシナリオ: レコード管理と保持管理の役割 

## <a name="overall-workflow"></a>全体的なワークフロー

> [!IMPORTANT]
> コンテンツ エクスプローラーで、アイテムにアイテムを自動適用するアイテム保持ラベル ポリシー Exchangeフィードバックを提供し、分類子を条件として使用します。 **アイテム保持ラベルを Exchange アイテムに自動的に適用し、分類子を条件として使用するアイテム保持ポリシーを持ってない場合は、ここで停止します。**

分類子を使用する場合は、分類の精度を上げてほしい場合があります。 これを行うには、一致または一致ではないと識別されたアイテムに対して行われた分類の品質を評価します。 分類子に対して 30 の評価を行った後、そのフィードバックを受け取り、自動的に再トレーニングを行います。

分類子の再トレーニングの全体的なワークフローの詳細については、「分類子を再トレーニングするプロセス フロー」 [を参照してください](classifier-learn-about.md#retraining-classifiers)。

> [!NOTE]
> 分類子を再トレーニングするには、分類子が既に公開され、使用されている必要があります。

## <a name="how-to-retrain-a-classifier-in-content-explorer"></a>コンテンツ エクスプローラーで分類子を再トレーニングする方法

1. コンプライアンス管理者またはセキュリティ管理者Microsoft 365アクセスしてコンプライアンス センターにサインインし、コンプライアンス センター **データ** Microsoft 365コンテンツ エクスプローラー  >  **を**  >  **開きます**。 
2. [ラベル、 **情報の種類、または** カテゴリのフィルター] ボックスの一覧で、[トレーニング可能な **分類子] を展開します**。

> [!IMPORTANT]
> トレーニング可能な分類子の見出しの下に集計アイテムが表示されるには、最大 8 日かかる場合があります。

3. 保持ラベル ポリシーの自動適用で使用したトレーニング可能な分類子を選択します。 これは、フィードバックを提供するトレーニング可能な分類子です。

> [!NOTE]
> アイテムに [アイテム保持ラベル] 列にエントリ **がある** 場合は、アイテムが " として分類された" という意味です `match` 。  アイテムに [保持ラベル] 列にエントリが含されていない場合は、アイテムが [ 保持ラベル] 列に分類されたという意味です `close match` 。 アイテムに関するフィードバックを提供することで、分類子の精度を最も向上 `close match` できます。 

4. アイテムを選択して開きます。
 
 > [!TIP]
> 複数のアイテムに対するフィードバックを同時に提供するには、それらをすべて選択し、コマンド バーで [分類の **改善]** を選択します。

5. [フィードバック **の提供] を選択します**。
6. [詳細 **なフィードバック] ウィンドウで** 、アイテムが正の場合は、[一致] を **選択します**。  アイテムが誤検知の場合、カテゴリに誤って含まれている場合は、[一致しない **] を選択します**。
7. アイテムに適した別の分類子がある場合は、[他のトレーニング可能な分類子を提案する] リストから分類 **子を選択** できます。 これにより、他の分類子がアイテムを評価します。
8. [ **フィードバックの送信]** を選択して、評価の送信、分類、その他のトレーニング可能な分類子 `match` `not a match` の提案を行います。 分類子にフィードバックの 30 インスタンスを提供すると、自動的に再トレーニングされます。 再トレーニングには 1 ~ 4 時間かかる場合があります。 分類子は、1 日に 2 回のみ再トレーニングできます。

> [!IMPORTANT]
> この情報はテナントの分類子に表示されます **。Microsoft には戻らない。**

9. トレーニング **可能な分類子を開きます**。
10. コミュニケーション コンプライアンス ポリシーで使用された分類子は、[再トレーニング] 見出し **の下に表示** されます。

![再トレーニング状態の分類子](../media/classifier-retraining.png)

11. 再トレーニングが完了したら、分類子を選択して再トレーニングの概要を開きます。

![分類子の再トレーニング結果の概要](../media/classifier-retraining-overview.png)

12. 推奨されるアクションと、再トレーニング済みおよび現在公開されているバージョンの分類子の予測比較を確認します。
13. 再トレーニングの結果に満足している場合は、[再発行] **を選択します**。
14. 再トレーニングの結果に満足できない場合は、Content Explorer インターフェイスで分類子に追加のフィードバックを提供し、別の再トレーニング サイクルを開始するか、現在公開されているバージョンの分類子が引き続き使用されます。 

## <a name="details-on-republishing-recommendations"></a>推奨事項の再発行の詳細

再トレーニングされた分類子を再発行するか、さらに再トレーニングを提案する推奨事項を策定する方法に関する少しの情報を次に示します。 これには、トレーニング可能な分類子の動作を少し深く理解する必要があります。

再トレーニングの後、分類子のトレーニングに使用されたアイテムとフィードバックを含む両方のアイテムに対する分類子のパフォーマンスを評価します。 

- 組み込みモデルの場合、分類子のトレーニングに使用されるアイテムは、Microsoft がモデルの構築に使用するアイテムです。
- カスタム モデルの場合、元のトレーニングで使用されるアイテムは、テストとレビューのために追加したサイトの分類子です。

再トレーニング済み分類子と発行済み分類子の両方の項目セットのパフォーマンス番号を比較し、再発行の改善が行われたかどうかの推奨事項を示します。 

## <a name="see-also"></a>関連項目

- [トレーニング可能な分類子の詳細](classifier-learn-about.md)
- [SharePoint Server での既定のクロール対象ファイル名拡張子および解析対象ファイルの種類](/sharepoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)