---
title: 通信コンプライアンスの計画
description: 組織で通信コンプライアンスを使用する計画について学習します。
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: d64edc9d80722080db18c45127bfc82110d1ea9e
ms.sourcegitcommit: fdb5f9d865037c0ae23aae34a5c0f06b625b2f69
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2020
ms.locfileid: "48131539"
---
# <a name="plan-for-communication-compliance"></a>通信コンプライアンスの計画

組織のコミュニケーション コンプライアンス [を開始](communication-compliance.md) する前に、情報技術とコンプライアンス管理チームが検討すべき重要な計画活動と考慮事項があります。 次の分野での展開を十分に理解し、計画することで、通信コンプライアンス機能の実装と使用が円滑に進み、ソリューションのベスト プラクティスに沿って行うのに役立ちます。

## <a name="work-with-stakeholders-in-your-organization"></a>組織内の関係者と連携する

コミュニケーション コンプライアンスアラートに対するアクションを実行するために共同作業を行う組織の適切な関係者を特定します。 初期計画やエンドツーエンドのコミュニケーション コンプライアンス ワークフローに含めて検討する推奨される[](communication-compliance.md#workflow)関係者の中には、組織の次の分野のユーザーが含まれます。

- 情報技術
- コンプライアンス
- プライバシー
- セキュリティ
- 人事管理
- 法務

## <a name="plan-for-the-investigation-and-remediation-workflow"></a>調査と修復ワークフローの計画

専用の関係者を選択して、コンプライアンス センターの定期的なケイデンスに関するアラートと[ケースMicrosoft 365確認します](https://compliance.microsoft.com/)。 組織内の異なるコミュニケーション コンプライアンス役割グループにユーザーと関係者を割り当てる方法を理解してください。

通信ポリシーとアラートの管理方法に応じて、管理者、レビュー担当者、および調査担当者用の 1 つ以上の役割グループにユーザーを割り当てる必要があります。 通信コンプライアンス機能の異なるセットを管理するために、ユーザーを特定の役割グループに割り当てるオプションがあります。 または、すべての通信コンプライアンス ユーザーを [通信コンプライアンス] 役割グループに割り当てる場合があります。 コンプライアンス管理要件に最適な 1 つの役割グループまたは複数のグループを使用します。

通信コンプライアンスを構成するときに、次の役割グループ オプションから選択する計画を立てします。

|**役割**|**ロール権限**|
|:-----|:-----|
| **コミュニケーションコンプライアンス** | この役割グループを使用して、1 つのグループで組織の通信コンプライアンスを管理します。 指定された管理者、アナリスト、調査者、閲覧者のすべてのユーザー アカウントを追加することで、1 つのグループで通信コンプライアンスのアクセス許可を構成できます。 この役割グループには、すべての通信コンプライアンスアクセス許可の役割が含まれる。 この構成は、通信コンプライアンスを迅速に開始する最も簡単な方法であり、個別のユーザー グループに対して個別のアクセス許可を定義する必要がない組織に適しています。 |
| **コミュニケーション コンプライアンス管理者** | この役割グループを使用して、通信コンプライアンスを最初に構成し、後で通信コンプライアンス管理者を定義されたグループに分離します。 この役割グループに割り当てられたユーザーは、通信コンプライアンス ポリシー、グローバル設定、および役割グループの割り当てを作成、読み取り、更新、および削除できます。 この役割グループに割り当てられたユーザーは、メッセージ通知を表示できません。 |
| **コミュニケーション コンプライアンス アナリスト** | コミュニケーション コンプライアンス アナリストとして機能するユーザーにアクセス許可を割り当てるには、このグループを使用します。 この役割グループに割り当てられたユーザーは、レビュー担当者として割り当てられているポリシーを表示したり、メッセージ メタデータ (メッセージ コンテンツではなく) を表示したり、追加のレビュー担当者にエスカレートしたり、ユーザーに通知を送信したりできます。 アナリストは保留中のアラートを解決できません。 |
| **コミュニケーション コンプライアンス調査員** | このグループを使用して、通信コンプライアンス調査員として機能するユーザーにアクセス許可を割り当てる。 この役割グループに割り当てられたユーザーは、メッセージのメタデータとコンテンツを表示し、追加のレビュー担当者にエスカレートし、Advanced eDiscovery ケースにエスカレートし、ユーザーに通知を送信し、アラートを解決できます。 |
| **コミュニケーション コンプライアンス ビューアー** | このグループを使用して、通信レポートを管理するユーザーにアクセス許可を割り当てる。 この役割グループに割り当てられたユーザーは、通信コンプライアンス ホーム ページのすべてのレポート ウィジェットにアクセスし、すべての通信コンプライアンス レポートを表示できます。 |

## <a name="plan-for-policies"></a>ポリシーの計画

通信コンプライアンス ポリシーの作成は、攻撃的な[](communication-compliance-feature-reference.md#policy-templates)言語、機密情報、および規制コンプライアンスに関する定義済みのテンプレートを使用して迅速かつ簡単に作成できます。 カスタム通信コンプライアンス ポリシーを使用すると、組織と要件に固有の問題を柔軟に検出および調査できます。

通信コンプライアンス ポリシーを計画する場合は、次の領域を検討してください。

- 組織内のすべてのユーザーを、通信コンプライアンス ポリシーのスコープ内に追加する場合を検討してください。 特定のユーザーを個々のポリシーのスコープ内として識別すると、状況によっては役に立ちますが、ほとんどの組織では、ハラスメントや差別の検出用に最適化されたコミュニケーション コンプライアンス ポリシーにすべてのユーザーを含める必要があります。
- セットアップを簡略化するには、コミュニケーションを確認する必要があるユーザー向けグループの作成を検討してください。 グループを使用している場合。いくつか必要な場合があります。 たとえば、2 つの異なるグループ間の通信を監視する場合や、監督対象ではないグループを指定する場合などです。
- 100% で確認する通信の割合を構成して、ポリシーが組織の通信に関する懸念事項を確実にキャッチします。
- サードパーティソースからの通信[を](communication-compliance-feature-reference.md#supported-communication-types)スキャンして、組織のメールボックスにインポートされたデータMicrosoft 365できます。 これらのプラットフォームに通信のレビューを含めるには、ポリシー条件を満たしたメッセージが通信ポリシーによって監視される前に、これらのサービスへのコネクタを構成する必要があります。
- ポリシーは、カスタム通信コンプライアンス ポリシーで英語以外の言語の監視をサポートできます。 好きな[言語で](communication-compliance-feature-reference.md#custom-keyword-dictionaries)不快な単語のカスタム キーワード 辞書を作成するか、またはトレーニング可能な分類子を[](classifier-get-started-with.md)使用して独自の機械学習モデルを構築Microsoft 365。
- すべての組織に異なる通信基準とポリシーのニーズがあります。 通信コンプライアンス ポリシー条件を使用して特定のキーワードを [監視するか、](communication-compliance-feature-reference.md#conditional-settings) カスタムの機密情報の種類を持つ特定の種類の [情報を監視します](create-a-custom-sensitive-information-type.md)。

## <a name="ready-to-get-started"></a>始める準備はいいですか。

Microsoft 365 組織の通信コンプライアンスを構成するには、「Microsoft 365 の通信コンプライアンスを構成する」を参照するか[、Contoso](communication-compliance-case-study.md)のケース スタディを参照し、Microsoft Teams、Exchange Online、および Yammer の通信で不快な言語を監視するように通信コンプライアンス ポリシーを迅速に構成した方法を確認してください。 [](communication-compliance-configure.md)
