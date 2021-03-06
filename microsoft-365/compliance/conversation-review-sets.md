---
title: '[チャット] で会話をAdvanced eDiscovery'
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Advanced eDiscovery グループでのチャット会話の再構築、レビュー、エクスポートを行う Advanced eDiscovery での会話の再構築機能についてMicrosoft TeamsおよびYammerします。
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 9848280a7d6dbcbd6128fff06f150c8458f09701
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/30/2021
ms.locfileid: "53227189"
---
# <a name="conversation-threading-in-advanced-ediscovery"></a>スレッド内のスレッドAdvanced eDiscovery

インスタント メッセージングは、質問をしたり、アイデアを共有したり、大規模なユーザー間ですばやくコミュニケーションを取る便利な方法です。 Microsoft Teams グループや Yammer グループなどのインスタント メッセージング プラットフォームがエンタープライズ コラボレーションの中核となる中、組織は電子情報開示ワークフローがこれらの新しい形式のコミュニケーションとコラボレーションにどう対応するのか評価する必要があります。

コンテキスト コンテンツを特定し、Advanced eDiscoveryの会話ビューを作成するのに役立つ、会話の再構成機能です。 この機能により、Microsoft Teams のようなプラットフォームで生成される完全なインスタント メッセージ会話 (スレッド *会話とも呼* ばれる) を効率的かつ迅速に確認Microsoft Teams。

Conversation Reconstruction を使用すると、組み込みの機能を使用してスレッド会話を再構築、レビュー、エクスポートできます。 スレッドのAdvanced eDiscoveryを使用して、次の設定を行います。

- 会話内のすべてのメッセージに対して一意のメッセージ レベルのメタデータを保持します。

- 検索結果に関するコンテキスト メッセージを収集します。

- スレッドスレッドの会話の確認、注釈付け、やり直しを行います。

- 個々のメッセージまたはスレッドスレッドの会話をエクスポートする

## <a name="terminology"></a>用語

会話の再構築の使用を始めるのに役立ついくつかの定義を次に示します。

- **メッセージ:** 会話の最小単位を表します。 メッセージのサイズ、構造、およびメタデータは異なる場合があります。

- **会話:** 1 つ以上のメッセージのグループ化を表します。 異なるアプリケーション間で、会話はさまざまな方法で表される場合があります。 一部のアプリケーションでは、既存のメッセージに返信する明示的なアクションがあります。 会話は、このユーザー操作の結果として明示的に形成されます。 たとえば、次に、チャネル会話のスクリーンショットを示Microsoft Teams。

   ![Microsoft Teamsチャネルの会話](../media/threadedchat.png)

   他のアプリ (Teams の 1xN チャット メッセージなど) では、正式な返信チェーンが用意されていないので、メッセージは単一スレッド内の "平らなメッセージの川" として表示されます。 これらの種類のアプリでは、会話は、特定の時間内に発生するメッセージのグループから推測されます。 このメッセージの "ソフト グループ化" は、(返信チェーンではなく) 特定のトピックに関する "前後" の会話を表します。

## <a name="step-1-create-a-draft-collection"></a>手順 1: 下書きコレクションを作成する

関連する保管担当者とコンテンツの場所を特定した後、検索を作成して関連性の高いコンテンツを検索できます。 このケース **の [** コレクション] タブAdvanced eDiscovery、[新しいコレクション] をクリックしてウィザードに従ってコレクションを作成できます。 コレクションを作成し、検索クエリを作成し、検索結果をプレビューする方法については、「下書きコレクションを作成 [する」を参照してください](create-draft-collection.md)。

## <a name="step-2-commit-a-draft-collection-to-a-review-set"></a>手順 2: 下書きコレクションをレビュー セットにコミットする

コレクション内の検索クエリを確認して終了したら、検索結果をレビュー セットに追加できます。 検索結果をレビュー セットに追加すると、元のデータは、レビューおよび分析プロセスを容易にするために、Azure Storage領域にコピーされます。 レビュー セットに検索結果を追加する方法の詳細については、「レビュー セットに下書きコレクションをコミット [する」を参照してください](commit-draft-collection.md)。

会話からレビュー セットにアイテムを追加する場合は、スレッド会話オプションを使用して、コレクションの検索条件に一致するアイテムを含む会話からコンテキスト メッセージを収集できます。 スレッドの会話オプションを選択すると、次のことが発生する可能性があります。

  ![会話の取得](../media/messagesandconversations.png)

1. キーワードと日付範囲のクエリを使用して、検索でメッセージ 3 のヒット *が返されました*。 このメッセージは *、CRC1* によって示される、より大きな会話の一部でした。

2. レビュー セットにデータを追加し、会話の取得オプションを有効にした場合、Advanced eDiscovery *CRC1* の他のアイテムを収集します。

3. アイテムがレビュー セットに追加された後 *、CRC1* からのすべての個々のメッセージを確認できます。

スレッド会話オプションを有効にするには、「下書きコレクションをレビュー セットにコミット [する」を参照してください](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set)。

## <a name="step-3-review-and-export-threaded-conversations"></a>手順 3: スレッド会話の確認とエクスポート

コンテンツが処理され、レビュー セットに追加された後、レビュー セットのデータの確認を開始できます。 レビュー機能は、コンテンツが標準のレビュー セットまたは会話レビュー セットに追加されたかどうかによって異なります。

### <a name="reviewing-conversations-in-a-standard-review-set"></a>標準レビュー セットでの会話の確認

標準のレビュー セットでは、メッセージはメールボックス フォルダーに格納される方法と同様に、個々のアイテムとして処理および表示されます。 このワークフローでは、各メッセージは個別のアイテムとして処理されます。 そのため、スレッド化された概要とエクスポートのオプションは、標準のレビュー セットでは使用できません。

  ![標準レビュー セット](../media/standardrs.PNG)

### <a name="reviewing-conversations-in-a-conversation-review-set"></a>会話レビュー セットでの会話の確認

会話レビュー セットでは、個々のメッセージがスレッド化され、会話として表示されます。 これにより、コンテキスト会話を確認およびエクスポートできます。

  ![会話レビュー セット](../media/ConversationRSOptions.PNG)

次のセクションでは、会話レビュー セット内の会話の確認とエクスポートについて説明します。

#### <a name="reviewing-conversations"></a>会話の確認

会話レビュー セットでは、次のオプションを使用してレビュー プロセスを容易にできます。

- **会話によるグループ化:** 同じ会話内のメッセージをグループ化して、ユーザーがレビュー プロセスを簡素化し、迅速に行うのに役立ちます。

- **概要ビュー:** スレッドスレッドの会話を表示します。 このビューでは、会話全体を確認し、個々のメッセージのメタデータにもアクセスできます。

   - 個々のメッセージのメタデータを表示する

   - 個々のメッセージをダウンロードする

- **テキスト ビュー:** 会話全体の抽出されたテキストを提供します。

- **注釈ビュー:** スレッドビューをマークアップできます。 会話内のすべてのメッセージは、同じ注釈付きドキュメントを共有します。

- **タグ付け:** レビュー セットで会話を表示する場合は、[コーディング] パネルの[タグ付け] パネルをクリックしてタグを表示および適用できます。

- **会話の変換を再実行する:** メッセージを会話レビュー セットに追加すると、変換ジョブが自動的に実行され、スレッド化された概要が作成され、ビューに注釈が付きます。 会話の再構築ジョブが失敗した場合は、[アクション] をクリックしてこのジョブを再実行し>で会話 **PDF を** 作成します。

#### <a name="exporting-conversations"></a>会話のエクスポート

会話レビュー セットでは、次のオプションを設定して会話をエクスポートできます。

![会話のエクスポート オプション](../media/export.png)

1. メタデータ オプション:
   - **ファイルの読み込み:** メタデータは、個々のメッセージ、電子メール、およびドキュメントごとに含まれます。 会話内のメッセージごとに 1 行があります。
   - **タグ:** レビュー プロセスのタグがメタデータ ファイルに含まれます。 会話内のメッセージは同じタグを共有します。

2. 会話のオプション:
   - **会話ファイル:** 会話ファイルをエクスポートすると、注釈付きビューが PDF ファイルに変換され、エクスポート フォルダーにダウンロードされます。 1 つの会話ファイル内のメッセージは、同じ会話ファイルの PDF バージョンを指します。
   - **個々のチャット メッセージ:** 個々のメッセージをエクスポートすると、会話内の各一意のメッセージがスタンドアロン アイテムとしてエクスポートされます。 ファイルは、メールボックスと同じ形式でエクスポートされます。 特定の会話では、複数の .msg ファイルを受信します。

     > [!NOTE]
     > 会話ファイルに注釈を適用した場合、これらの注釈は個々のメッセージに転送されません。

3. その他のオプション:
   - **エクスポートされたコンテンツのテキスト ファイルを生成します。** レビュー セットからエクスポートされた会話ごとにテキスト ファイルを生成します。
   - **エクスポートされたコンテンツを、変更された PDF に置き換える:** 編集された会話ファイルがレビュー プロセス中に生成された場合、エクスポート時にこれらのファイルを使用できます。 (このオプションを選択しない) ネイティブ ファイルのみをエクスポートするか、ネイティブ ファイルを PDF ファイルとしてエクスポートする (このオプションを選択して) 元のバージョンのネイティブ ファイルに置き換えるかどうかを決定できます。

## <a name="more-information"></a>詳細

ケース データを確認する方法の詳細については、Advanced eDiscovery記事を参照してください。

- [ケース データの表示](view-documents-in-review-set.md)
- [ケース データを分析する](analyzing-data-in-review-set.md)
- [ケース データをエクスポートする](exporting-data-ediscover20.md)
