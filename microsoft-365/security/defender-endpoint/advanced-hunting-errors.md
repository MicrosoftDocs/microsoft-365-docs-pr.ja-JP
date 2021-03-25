---
title: Microsoft Defender ATP の高度な検索でエラーを処理する
description: 高度な検索を使用する場合に表示されるエラーを理解する
keywords: 高度な狩猟、脅威狩り、サイバー脅威の狩猟、mdatp、microsoft Defender atp、wdatp、m365、検索、クエリ、テレメトリ、スキーマ、kusto、タイムアウト、リソース、エラー、不明なエラー
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
ms.openlocfilehash: 64c8a13ba9e8110d761245315969b9e1882b3448
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51067475"
---
# <a name="handle-advanced-hunting-errors"></a>高度なハンティング エラーの処理

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)


>Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-advancedhunting-abovefoldlink)

高度な検索では、構文の間違いを通知するエラーと、クエリが定義済みの制限に達するたびに [エラーが表示されます](advanced-hunting-limits.md)。 エラーを解決または回避する方法のヒントについては、以下の表を参照してください。 

| エラーの種類 | 原因 | 解決策 | エラー メッセージの例 |
|--|--|--|--|
| 構文エラー | クエリには、存在しない演算子、列、関数、またはテーブルへの参照を含む、認識されていない名前が含まれます。 | [Kusto 演算子と関数への参照が正しいか](https://docs.microsoft.com/azure/data-explorer/kusto/query/)確認します。 スキーマ [で、適切](advanced-hunting-schema-reference.md) な高度な検索列、関数、およびテーブルを確認します。 変数文字列を引用符で囲み、認識します。 クエリを記述する場合は、クエリの自動入力候補を使用IntelliSense。 | `A recognition error occurred.` |
| セマンティック エラー | クエリは有効な演算子、列、関数、またはテーブル名を使用しますが、その構造と結果のロジックにエラーがあります。 高度な検索では、エラーの原因となる特定の演算子が識別される場合があります。 | クエリの構造のエラーを確認します。 ガイダンスについては [、Kusto のドキュメント](https://docs.microsoft.com/azure/data-explorer/kusto/query/) を参照してください。 クエリを記述する場合は、クエリの自動入力候補を使用IntelliSense。 |  `'project' operator: Failed to resolve scalar expression named 'x'`|
| タイムアウト | クエリは、限られた期間内 [にしか実行されず、タイミングアウトが発生します](advanced-hunting-limits.md)。このエラーは、複雑なクエリを実行するときにより頻繁に発生する可能性があります。 | [クエリを最適化する](advanced-hunting-best-practices.md) | `Query exceeded the timeout period.` |
| CPU 調整 | 同じテナント内のクエリが、テナントのサイズに基づいて割り当てられた [CPU](advanced-hunting-limits.md) リソースを超えました。 | このサービスは、15 分ごとに CPU リソース使用率をチェックし、割り当てられた制限の 10% を超えた使用状況の後に警告を表示します。 使用率が 100% に達すると、サービスは次の 1 日または 15 分のサイクルの後までクエリをブロックします。 [CPU 制限に達しないようにクエリを最適化する](advanced-hunting-best-practices.md) | - `This query used X% of your organization's allocated resources for the current 15 minutes.`<br>- `You have exceeded processing resources allocated to this tenant. You can run queries again in <duration>.` |
| 結果のサイズ制限を超えた  | クエリの結果セットの集計サイズが上限を超えています。 このエラーは、結果セットが大きいので、10,000 レコードの制限での切り捨てが許容できるサイズに減らできない場合に発生する可能性があります。 コンテンツが大きな複数の列を持つ結果は、このエラーの影響を受けそうになります。 | [クエリを最適化する](advanced-hunting-best-practices.md) | `Result size limit exceeded. Use "summarize" to aggregate results, "project" to drop uninteresting columns, or "take" to truncate results.` |
| リソースの過剰な消費 | クエリは過剰な量のリソースを消費し、完了を停止しました。 高度な検索では、最適化が行えなかった特定の演算子が識別される場合があります。 | [クエリを最適化する](advanced-hunting-best-practices.md) | -`Query stopped due to excessive resource consumption.`<br>-`Query stopped. Adjust use of the <operator name> operator to avoid excessive resource consumption.` |
| 不明なエラー | 不明な理由でクエリが失敗しました。 | クエリの実行を再試行してください。 クエリが不明なエラーを引き続き返す場合は、ポータルから Microsoft に問い合わせください。 | `An unexpected error occurred during query execution. Please try again in a few minutes.`

## <a name="related-topics"></a>関連項目
- [高度な狩猟のベスト プラクティス](advanced-hunting-best-practices.md)
- [サービスの制限](advanced-hunting-limits.md)
- [スキーマを理解する](advanced-hunting-schema-reference.md)
- [Kusto クエリ言語の概要](https://docs.microsoft.com/azure/data-explorer/kusto/query/)