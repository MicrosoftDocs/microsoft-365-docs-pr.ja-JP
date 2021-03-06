---
title: 検索クエリをビルドAdvanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom: seo-marvel-mar2020
description: キーワードと条件を使用して、データを検索する際に検索範囲を絞り込むには、Advanced eDiscoveryをMicrosoft 365。
ms.openlocfilehash: e0df319257776d3995a4b8e37781d7b5dad54d82
ms.sourcegitcommit: 8f1721de52dbe3a12c11a0fa5ed0ef5972ca8196
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2021
ms.locfileid: "50838483"
---
# <a name="build-search-queries-for-collections-in-advanced-ediscovery"></a>データベース内のコレクションの検索クエリをAdvanced eDiscovery

Advanced eDiscovery ケースでコレクションを作成するときに検索[](collections-overview.md)クエリを構成する場合、キーワードを使用して特定のコンテンツと条件を検索し、検索範囲を絞り込み、法的調査に最も関連のあるアイテムを返します。

![キーワードと条件を使用して検索の結果を絞り込む](../media/SearchQueryBox.png)

## <a name="keyword-searches"></a>キーワード検索

検索クエリの [キーワード] **ボックスに** キーワード クエリを入力します。 キーワード、電子メール メッセージのプロパティ (送信日と受信日など)、またはファイル名やドキュメントが最後に変更された日付などのドキュメント プロパティを指定できます。 **AND**、**OR**、**NOT**、**NEAR** などのブール演算子を使用するより複雑なクエリを使用できます。 SharePoint および OneDrive (電子メール メッセージではなく) のドキュメントで機密情報 (社会保障番号など) を検索したり、外部で共有されたドキュメントを検索することもできます。 この **キーワード** ボックスを空のままにすると、指定したコンテンツの場所にあるすべてのコンテンツが検索結果に入ります。

## <a name="keyword-list"></a>キーワード リスト

または、[キーワード 一 **覧を表示** する] チェック ボックスをオンにして、各行にキーワードまたはキーワード 語句を入力することもできます。 各行のキーワードは、作成された検索クエリの **OR** 演算子と同様の機能を持つ論理演算子 (検索クエリ構文では *c:s* として表されます) によって接続されます。 つまり、任意の行にキーワードを含むアイテムが検索結果に表示されます。 検索クエリでは、キーワード リストに最大 180 行Advanced eDiscoveryできます。

![キーワード リストを使用して、クエリ内の各キーワードの統計情報を取得する](../media/KeywordListSearch.png)

キーワード リストを使用する理由 キーワード リスト内の各キーワードに一致するアイテムの数を示す統計情報を取得できます。 これにより、最も効果的な (および最も少ない) キーワードをすばやく特定できます。 キーワード リストの行にキーワード 語句 (かっこで囲む) を使用できます。 検索統計の詳細については、「検索統計」 [を参照してください](search-statistics-in-advanced-ediscovery.md)。

## <a name="conditions"></a>条件

検索条件を追加して、検索範囲を絞り込み、より絞り込みされた結果のセットを返します。 各条件によって、作成された検索クエリに句が追加され、ユーザーが検索を開始するとそのクエリが実行されます。 条件は **、AND** 演算子と同様の機能を持つ論理演算子 (検索クエリ構文では *c:c* として表される) によって、キーワード ボックスで指定されたキーワード クエリに論理的に接続されます。 つまり、アイテムはキーワード クエリと検索結果に含める 1 つ以上の条件の両方を満たす必要があります。 このように、条件を使用して結果を絞り込むことができます。 検索クエリで使用できる条件の一覧と説明については、「キーワード クエリと検索条件」の「検索条件」 [セクションを参照してください](keyword-queries-and-search-conditions.md#search-conditions)。
