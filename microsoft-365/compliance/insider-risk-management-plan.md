---
title: インサイダー リスク管理のための計画
description: 組織内のインサイダー リスク管理ポリシーの使用を計画する方法について説明します。
keywords: Microsoft 365、インサイダー リスク、リスク管理、コンプライアンス
localization_priority: Normal
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: 19149c7f53cee537450ac12ce5a346a12d43bd91
ms.sourcegitcommit: 997a21b83795789cda0a6b4a77f9985a3233d0c0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2021
ms.locfileid: "53430515"
---
# <a name="plan-for-insider-risk-management"></a>インサイダー リスク管理のための計画

組織内のイン [サイダー](insider-risk-management.md) リスク管理を開始する前に、情報技術とコンプライアンス管理チームで検討すべき重要な計画活動と考慮事項があります。 以下の分野での展開を十分に理解し、計画することで、インサイダー リスク管理機能の実装と使用が円滑に進み、ソリューションのベスト プラクティスに沿って行うのに役立ちます。

以下のビデオを見て、組織の価値、文化、およびユーザー エクスペリエンスを優先順位付けしながら、組織がリスクを防止、検出、および含むのに役立つインサイダー リスク管理ワークフローについて説明します。
<br>
<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OUXB]

## <a name="work-with-stakeholders-in-your-organization"></a>組織内の関係者と連携する

インサイダーリスク管理アラートとケースに対するアクションを実行するために、組織内の適切な利害関係者を特定します。 初期計画やエンドツーエンドのインサイダー リスク管理ワークフローに含めて検討する[](insider-risk-management.md#workflow)推奨される関係者には、組織の次の分野の関係者が含まれます。

- 情報技術
- コンプライアンス
- プライバシー
- セキュリティ
- 人事管理
- 法務

## <a name="determine-any-regional-compliance-requirements"></a>地域のコンプライアンス要件を決定する

地理的領域と組織領域が異なる場合は、組織の他の領域とは異なるコンプライアンス要件とプライバシー要件を持つ場合があります。 これらの分野の関係者と協力して、インサイダーリスク管理におけるコンプライアンスとプライバシー管理、および組織の異なる分野での使用方法を理解します。 一部のシナリオでは、コンプライアンスおよびプライバシー要件では、一部の利害関係者を、その地域のユーザーまたは規制またはポリシー要件に基づいて調査やケースから指定または制限するポリシーが必要になる場合があります。

特定の地域、役割、または部門のユーザーが関与するケース調査に特定の関係者が関与する必要がある場合は、異なる地域と人口を対象とする個別の (同一の [)](insider-risk-management-policies.md) インサイダー リスク管理ポリシーを実装できます。 この構成により、適切な関係者が役割と地域に関連するケースをトリアージおよび管理しやすくなります。 さらに、調査員やレビュー担当者がユーザーと同じ言語を話す地域のプロセスとポリシーの作成を検討して、インサイダーリスク管理のアラートとケースのエスカレーション プロセスを合理化することもできます。

## <a name="plan-for-the-review-and-investigation-workflow"></a>レビューと調査のワークフローを計画する

専用の関係者を選択して、サーバー内の定期的なケイデンスに関するアラートとケースを監視および[確認Microsoft 365 コンプライアンス センター。](https://compliance.microsoft.com/) インサイダー リスク管理で使用できるさまざまな役割グループに異なる利害関係者を割り当てる方法を理解してください。

コンプライアンス管理チームの構造に応じて、ユーザーを特定の役割グループに割り当て、さまざまな一連のインサイダー リスク機能を管理するオプションがあります。 Office 365 セキュリティ& コンプライアンス センターの [アクセス許可] タブを表示し、役割グループを管理するには、組織の管理役割グループに割り当てられているか、役割の管理役割を割り当てる *必要* があります。 インサイダー リスク管理を構成する場合は、次の役割グループ オプションから選択します。

| **役割グループ** | **ロール権限** |
| :------------- | :------------------- |
| **Insider リスク管理** | この役割グループを使用して、単一グループで組織のインサイダー リスク管理を管理します。 指定された管理者、アナリスト、調査員、監査人のすべてのユーザー アカウントを追加することで、1 つのグループでインサイダー リスク管理のアクセス許可を構成できます。 この役割グループには、すべてのインサイダー リスク管理アクセス許可ロールと関連するアクセス許可が含まれる。 この構成は、インサイダー リスク管理を迅速に開始する最も簡単な方法であり、個別のユーザー グループに対して個別のアクセス許可を定義する必要がない組織に適しています。 この構成を使用する場合は、ポリシーが期待通り動作し、ユーザーがポリシーを作成および編集し、ソリューション設定を構成し、ポリシーの正常性警告を確認できるよう、常に少なくとも 1 人のユーザーがこの役割グループに割り当てられている必要があります。 |
| **Insider リスク管理管理者** | この役割グループを使用して、インサイダー リスク管理を最初に構成し、後でインサイダー リスク管理者を定義されたグループに分離します。 この役割グループのユーザーは、分析インサイトを有効にして表示し、インサイダー リスク管理ポリシー、グローバル設定、役割グループの割り当てを作成、読み取り、更新、および削除できます。 この構成を使用する場合は、ポリシーが期待通り動作し、ユーザーがポリシーを作成および編集し、ソリューション設定を構成し、ポリシーの正常性警告を確認できるよう、常に少なくとも 1 人のユーザーがこの役割グループに割り当てられている必要があります。 |
| **インサイダー リスク管理アナリスト** | このグループを使用して、インサイダー リスク ケース アナリストとして機能するユーザーに権限を割り当てます。 この役割グループのユーザーは、すべてのインサイダー リスク管理アラート、ケース、分析インサイト、および通知テンプレートにアクセスして表示できます。 インサイダー リスク コンテンツ エクスプローラーにはアクセスできません。 |
| **インサイダー リスク管理調査担当者** | このグループを使用して、インサイダー リスク データ調査担当者として機能するユーザーに権限を割り当てます。 この役割グループのユーザーは、すべてのケースについて、すべてのインサイダー リスク管理アラート、ケース、通知テンプレート、およびコンテンツ エクスプローラーにアクセスできます。 |
| **Insider リスク管理監査人** | インサイダー リスク管理アクティビティを監査するユーザーにアクセス許可を割り当てるには、このグループを使用します。 この役割グループのユーザーは、インサイダー リスク監査ログにアクセスできます。 |

## <a name="understand-requirements-and-dependencies"></a>要件と依存関係を理解する

インサイダー リスク管理ポリシーの実装方法に応じて、適切な Microsoft 365 ライセンス サブスクリプションを持ち、ソリューションの前提条件を理解して計画する必要があります。

**ライセンス:** Insider リスク管理は、ライセンス サブスクリプションの幅広い選択Microsoft 365利用できます。 詳細については、「Insider リスク管理の開始 [」の記事を参照](insider-risk-management-configure.md#subscriptions-and-licensing) してください。

既存の Microsoft 365 Enterprise E5 プランをお持ちで、インサイダー リスク管理を試す場合は、Microsoft 365 を既存のサブスクリプションに追加するか[、Microsoft 365 Enterprise](/office365/admin/try-or-buy-microsoft-365) E5 の試用版にサインアップできます。 [](https://www.microsoft.com/microsoft-365/enterprise)

**ポリシー テンプレートの要件:** 選択したポリシー テンプレートに応じて、組織内でインサイダー リスク管理を構成する前に理解し、計画する必要がある要件があります。

- ユーザー テンプレートを削除してデータ盗難を使用する場合は、Microsoft 365 HR コネクタを構成して、組織内のユーザーの辞任と終了日の情報を定期的にインポートする必要があります。 組織用の HR コネクタの段階的な構成手順については「[Microsoft 365 HR コネクタでデータをインポートする](import-hr-data.md)」を参照してください。
- データ 漏え **い** テンプレートを使用する場合は、組織内の機密情報を定義し、重大度の高い DLP ポリシーアラートのインサイダー リスク アラートを受信するために、少なくとも 1 つのデータ損失防止 (DLP) ポリシーを構成する必要があります。 組織の DLP ポリシーを構成する方法については、「[DLP ポリシーの作成、テスト、調整](create-test-tune-dlp-policy.md)」の記事をご覧ください。
- セキュリティ ポリシー違反 **テンプレートを使用する** 場合は、セキュリティ違反アラートをインポートするために、Defender セキュリティ センターで Microsoft Defender for Endpoint のインサイダー リスク管理統合を有効にする必要があります。 Defender for Endpoint とインサイダー リスク管理の統合を有効にする手順については [、「Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/advanced-features) の高度な機能を構成する」の記事を参照してください。
- **Disgruntled** ユーザー テンプレートを使用する場合は、組織内のユーザーのパフォーマンスまたは降格状態情報を定期的にインポートする Microsoft 365 HR コネクタを構成する必要があります。 組織用の HR コネクタの段階的な構成手順については「[Microsoft 365 HR コネクタでデータをインポートする](import-hr-data.md)」を参照してください。

## <a name="test-with-a-small-group-of-users-in-a-production-environment"></a>実稼働環境の小さなユーザー グループでテストする

実稼働環境でソリューションを広く有効にする前に、組織で必要なコンプライアンス、プライバシー、法的レビューを実施しながら、小規模な一連の実稼働ユーザーでポリシーをテストする場合があります。 テスト環境でインサイダー リスク管理を評価するには、シミュレートされたユーザー アクションや他のシグナルを生成して、トリアージやケースの処理に関するアラートを作成する必要があります。 この方法は、ほとんどの組織では実用的ではないので、運用環境で小規模なユーザー グループでインサイダー リスク管理をテストする方が望ましいです。

ツール内のプライバシーを維持するために、このテスト中にインサイダー リスク管理コンソールでユーザーの表示名を匿名化するポリシー設定で匿名化機能を有効にしてください。 この設定は、ポリシーの一致を持つユーザーのプライバシーを保護し、インサイダー リスクアラートのデータ調査と分析レビューの客観性を促進するのに役立ちます。

インサイダー リスク管理ポリシーを構成した直後にアラートが表示されない場合は、最小リスクしきい値がまだ満たされていない可能性があります。 ポリシーがトリガーされ、期待通り動作しているか確認する良い方法は、[ユーザー] ページでユーザーがポリシーのスコープ内にあるか **確認する方法** です。

## <a name="resources-for-stakeholders"></a>関係者向けリソース

インサイダー リスク管理のドキュメントを、管理および修復ワークフローに含まれる組織内の関係者と共有します。

- [インサイダー リスク ポリシーを作成して管理する](insider-risk-management-policies.md)
- [インサイダー リスク アクティビティを調査する](insider-risk-management-activities.md)
- [インサイダー リスクのケースに対処する](insider-risk-management-cases.md)
- [インサイダー リスク コンテンツ エクスプローラーでケース データを確認する](insider-risk-management-content-explorer.md)
- [インサイダー リスク通知のテンプレートを作成する](insider-risk-management-notices.md)

## <a name="ready-to-get-started"></a>始める準備はいいですか。

組織のインサイダー リスク管理を構成する準備はできましたか? 次の記事を確認します。

- [グローバル ポリシー設定を構成するインサイダー](insider-risk-management-settings.md) リスク管理設定について説明します。
- [前提条件の構成、ポリシー](insider-risk-management-configure.md) の作成、アラートの受信を開始するインサイダー リスク管理について説明します。
