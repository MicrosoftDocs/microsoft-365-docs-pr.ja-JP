---
title: Microsoft 365 コンプライアンスを開始するためのクイック タスク
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- m365-security-compliance
- m365initiative-compliance
localization_priority: Normal
description: コンプライアンスを迅速に開始するのに役立つタスクについては、Microsoft 365。
ms.openlocfilehash: 61a057c3666faae51a012dd9db2d4c63ded0f77a
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/30/2021
ms.locfileid: "53227261"
---
# <a name="quick-tasks-for-getting-started-with-microsoft-365-compliance"></a>Microsoft 365 コンプライアンスを開始するためのクイック タスク

コンプライアンスを初め、どこからMicrosoft 365を開始する必要がある場合は、この記事で基本に関するガイダンスを提供し、重要なコンプライアンス タスクの優先順位を設定します。 この記事では、データの管理と監視、情報の保護、インサイダー リスクの最小化を迅速に開始するのに役立ちます。

この記事は、リスクを管理し、データを保護し、新たにリモートの従業員と規制と標準に準拠し続けるために最善の方法を考える場合にも役立ちます。 従業員は新しい方法で共同作業を行い、互いに接続しています。つまり、既存のコンプライアンス プロセスとコントロールに適応する必要がある場合があります。 組織内でこれらの新しいコンプライアンス リスクを特定および管理するには、データを保護し、脅威とリスクを最小限に抑える上で重要です。

これらの基本的なコンプライアンス タスクを完了したら、追加のコンプライアンス ソリューションを実装して、組織内のコンプライアンス範囲を拡大Microsoft 365検討してください。

## <a name="task-1-configure-compliance-permissions"></a>タスク 1: コンプライアンスのアクセス許可を構成する

コンテンツを表示し、管理タスクを実行するには、組織内のユーザーがMicrosoft 365 コンプライアンス センターアクセス権を持つユーザーを管理することが重要です。 Microsoft 365は、コンプライアンスに固有の管理役割を提供し、アプリケーションに含まれるツールを使用Microsoft 365 コンプライアンス センター。

まず、組織内のユーザーにコンプライアンスアクセス許可を割り当て、これらのタスクを実行し、権限のないユーザーが自分の責任外の領域にアクセスするのを防ぐことから始める。 Microsoft 365 に含まれるコンプライアンス ソリューションの構成と実装を開始する前に、コンプライアンス データ管理者とコンプライアンス管理者の役割に適切なユーザーを割り当て済みである必要があります。 また、コンプライアンス マネージャーでデータを表示するには、グローバル リーダー Azure Active Directoryにユーザーを割り当てる必要があります。

アクセス許可を構成し、管理者の役割にユーザーを割り当てる手順については、「Security & コンプライアンス センターのアクセス許可」 [を参照してください](../security/office-365-security/permissions-in-the-security-and-compliance-center.md)。

## <a name="task-2-know-your-state-of-compliance"></a>タスク 2: コンプライアンスの状態を知る

自分がどこにいるか分からない場合は、どこに行くのか分からない。 コンプライアンスニーズを満たすには、現在のリスクレベルと、変化するこれらの時代に必要な更新プログラムを理解する必要があります。 組織がコンプライアンス要件に新しいか、業界を管理する標準と規制に関する深い経験を持っている場合でも、コンプライアンスを改善するために最善の方法は、組織がどこに立っているのかを理解することです。

[Microsoft コンプライアンス マネージャーは](compliance-manager.md) 、組織のコンプライアンス体制を理解し、改善が必要な領域を強調するのに役立ちます。 コンプライアンス マネージャーは、一元的なダッシュボードを使用してリスクベースのスコアを計算し、データ保護と規制基準に関するリスクを軽減するアクションの完了状況を測定します。 コンプライアンス マネージャーをツールとして使用して、すべてのリスク評価を追跡することもできます。 一般的なツールを使用してリスク評価を効率的に完了させるためのワークフロー機能を提供します。

コンプライアンス マネージャーの使用を開始する手順については、「コンプライアンス マネージャーの使用を開始 [する」を参照してください](compliance-manager-setup.md)。

> [!IMPORTANT]
> セキュリティとコンプライアンスは、ほとんどの組織で緊密に統合されています。 セキュリティとコンプライアンスの両方に対する防御の詳細なアプローチを提供するために、組織が基本的なセキュリティ、脅威保護、ID およびアクセス管理領域に対応することが重要です。
>
> セキュリティ センター[でMicrosoft 365スコア](../security/defender/microsoft-secure-score.md)を確認Microsoft 365、次の記事で説明されているタスクを完了します。
>
> - [セキュリティロードマップ - 最初の 30 日間、90 日間、それ以降の最優先事項](../security/office-365-security/security-roadmap.md)
> - [自宅での作業をサポートするセキュリティ チームの上位 12 のタスク](../security/top-security-tasks-for-remote-work.md)

## <a name="task-3-enable-auditing-for-your-organization"></a>タスク 3: 組織の監査を有効にする

組織の現在の状態とコンプライアンス機能を管理できるユーザーを決定したので、次の手順では、コンプライアンス調査を実行し、組織内のネットワークおよびユーザー アクティビティのレポートを生成するデータを取得します。 監査の有効化は、この記事で後で説明するコンプライアンス ソリューションの重要な前提条件です。

インサイトログによって提供される機能は、コンプライアンス要件と、改善が必要なコンプライアンス領域の管理と監視に役立つソリューションを満たすのに役立つ貴重なツールです。 監査ログは、アクティビティが記録される前と監査ログを検索する前に有効にする必要があります。 有効にすると、組織のユーザーと管理者のアクティビティが監査ログに記録され、ユーザーに割り当てられたライセンスに応じて 90 日間、最大 1 年間保持されます。

監査を有効にする手順については、「監査ログ検索を有効またはオフにする」 [を参照してください](turn-audit-log-search-on-or-off.md)。

## <a name="task-4-create-policies-to-alert-you-about-potential-compliance-issues"></a>タスク 4: ポリシーを作成して、潜在的なコンプライアンスの問題について通知する

Microsoft では、管理アクセス許可の悪用、マルウェアアクティビティ、外部および内部の潜在的な脅威、情報ガバナンスのリスクを特定するのに役立つ、いくつかの組み込みのアラート ポリシーを提供しています。 これらのポリシーは既定で有効になっていますが、組織固有のコンプライアンス要件の管理に役立つカスタムアラートを構成する必要がある場合があります。

アラート ポリシーとアラート ダッシュボード ツールを使用してカスタムアラート ポリシーを作成し、ユーザーがポリシー条件に一致するアクティビティを実行するときに生成されるアラートを表示します。 一部の例では、アラート ポリシーを使用して、組織内のコンプライアンス要件、アクセス許可、およびデータ損失インシデントに影響を与えるユーザーと管理者のアクティビティを追跡できます。

カスタム アラート ポリシーを作成する手順については、「セキュリティとコンプライアンス センターのアラート ポリシー [」を参照してください](alert-policies.md)。

## <a name="task-5-classify-and-protect-sensitive-data"></a>タスク 5: 機密データの分類と保護

組織の従業員は、業務を行うために組織内外の関係者と共同作業を行います。このためコンテンツはファイアウォールの内側だけでなく、さまざまなデバイス、アプリ、サービスを越えて存在することになります。この場合、組織のビジネス ポリシーとコンプライアンス ポリシーを満たす安全な方法でコンテンツを保護することが必要です。

[感度ラベルを](sensitivity-labels.md) 使用すると、組織のデータを分類して保護できます。一方で、ユーザーの生産性と共同作業能力に支障が生じなかねない。 暗号化と使用制限を適用するには、感度ラベルを使用して視覚的なマーキングを適用し、プラットフォームやデバイス、オンプレミス、クラウドの間で情報を保護します。

感度ラベルを構成して使用する手順については、「感度ラベルの使用を開始する [」を参照してください](get-started-with-sensitivity-labels.md)。 感度ラベルのライセンス情報については、「セキュリティとコンプライアンス[Microsoft 365ライセンス ガイダンス」を&してください](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)。

## <a name="task-6-configure-a-retention-policy"></a>タスク 6: アイテム保持ポリシーを構成する

アイテム [保持ポリシーを](retention.md) 使用すると、コンテンツを保持するか、コンテンツを削除するか、その両方を事前に決定し、指定した保持期間の終わりにコンテンツを保持および削除できます。 これらのアクションは、業界の規制や内部ポリシーに準拠し、訴訟やセキュリティ侵害が発生した場合のリスクを軽減するために必要な場合があります。

コンテンツがアイテム保持ポリシーの対象となる場合、ユーザーは何も変更されなかっていないかのように、コンテンツの編集と作業を続行できます。 コンテンツは元の場所に保持されます。 ただし、保持ポリシーの対象となるコンテンツを編集または削除した場合、元のコンテンツのコピーは、そのコンテンツの保持ポリシーが有効な間、保持される安全な場所に保存されます。

Exchange メール、SharePoint サイト、OneDrive アカウント、Microsoft 365 グループなど、Microsoft 365 環境内の複数の場所に対して保持ポリシーをすばやく設定できます。 このポリシーに自動的に含めるメールボックスまたはサイトの数に制限はありません。 ただし、より選択的に取得する必要がある場合は、特定の場所のアイテム保持ポリシーを構成し、サイトまたはユーザーを含めるか除外します。

アイテム保持ポリシーを構成する手順については、「アイテム保持ポリシーの作成と構成 [」を参照してください](create-retention-policies.md)。 Microsoft 365 で保持を構成するのが初めての場合は、「[アイテム保持ポリシーと保持ラベルの使用を開始する](get-started-with-retention.md)」を参照してください。

## <a name="task-7-configure-sensitive-information-and-offensive-language-policies"></a>タスク 7: 機密情報と不快な言語ポリシーを構成する

機密情報を保護し、職場のハラスメント インシデントを検出して行動することが、内部のポリシーと標準の遵守の重要な部分です。 [電子メールや](communication-compliance-feature-reference.md)Microsoft 365の修復アクションを迅速に検出、キャプチャ、実行することで、これらのリスクを最小限に抑えるために、Microsoft Teams役立ちます。 これには、組織の内部および外部で機密情報を共有する不適切な情報、脅威、ハラスメントやコミュニケーションを含む不適切なコミュニケーションが含まれます。

定義済みの不快な *言語と* ハラスメント対策ポリシー テンプレートを使用すると、ポリシーの一致について内部および外部の通信をスキャンして、指定されたレビュー担当者が確認できます。 レビュー担当者は、組織内のスキャンされた電子メール、Microsoft Teams、Yammer、またはサードパーティの通信を調査し、組織の標準に準拠しているか確認するために適切な修復アクションを実行できます。

定義済みの機密情報ポリシーテンプレートを使用すると、定義された機密情報の種類またはキーワードを含む電子メールと Microsoft Teams 通信をスキャンするポリシーをすばやく作成し、重要なデータがアクセスできないユーザーと共有されるのを確実にするのに役立ちます。 これらのアクティビティには、機密プロジェクトに関する不正なコミュニケーションや、インサイダー取引や他の共謀活動に関する業界固有のルールが含まれる場合があります。

通信コンプライアンスを計画および構成する手順については、「通信コンプライアンスの計画」[](communication-compliance-plan.md)および「通信コンプライアンスの概要[」を参照してください](communication-compliance-configure.md)。 通信コンプライアンス のライセンス情報については、「セキュリティMicrosoft 365コンプライアンスに関する[&参照してください](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance)。

## <a name="task-8-see-whats-happening-with-your-sensitive-items"></a>タスク 8: 機密性の高いアイテムで何が起こっているかを確認する

機密ラベル、機密情報の種類、保持ラベルとポリシー、トレーニング可能な分類子を使用して、Exchange、SharePoint、および OneDrive 全体で、前のタスクで見た機密アイテムを分類およびラベル付けできます。 クイック タスクの最後の手順は、ラベルが付けられているアイテムと、ユーザーがそれらの機密性の高いアイテムに対して実行しているアクションを確認します。 [コンテンツ エクスプローラーと](data-classification-content-explorer.md)[アクティビティ エクスプローラーは、](data-classification-activity-explorer.md)この可視性を提供します。

### <a name="content-explorer"></a>コンテンツ エクスプローラー
 コンテンツ エクスプローラーを使用すると、機密情報の種類として分類された、またはトレーニング可能な分類子によって特定の分類に属するすべてのアイテムと、機密性または保持ラベルが適用されているすべてのアイテムをネイティブ形式で表示できます。

コンテンツ エクスプローラーを使用する手順については、「データを知る - データ分類の [概要](data-classification-overview.md)」および「コンテンツ エクスプローラーの概要 [」を参照してください](data-classification-content-explorer.md)。

### <a name="activity-explorer"></a>アクティビティ エクスプローラー
アクティビティ エクスプローラーは、機密アイテムとラベル付けされた機密アイテムの実行を監視するのに役立ちます。
- SharePoint
- Exchange
- OneDrive

使用可能なフィルターは 30 種類以上あり、以下がその一例です。

- 日付の範囲
- アクティビティの種類
- 場所
- ユーザー
- 機密ラベル
- 保持ラベル
- ファイル パス
- DLP ポリシー

アクティビティ エクスプローラーを使用する手順については、「アクティビティ エクスプローラーの使用を開始 [する」を参照してください](data-classification-activity-explorer.md)。

## <a name="next-steps"></a>次のステップ

組織のコンプライアンス管理の基本を構成しましたので、Microsoft 365 で次のコンプライアンス ソリューションを検討して、機密情報を保護し、追加のインサイダー リスクを検出して行動します。

### <a name="configure-retention-labels"></a>保持ラベルを構成する

アイテム保持ポリシーはコンテナー レベルで SharePoint サイトや Exchange メールボックスなどの場所に適用されます。保持ラベルを使用[](retention.md#retention-labels)すると、保持ポリシーと削除ポリシーに対するより具体的なターゲット設定が可能になります。 たとえば、管理者による自動アプリケーションに加えて、エンド ユーザーが手動で適用できるドキュメントまたは電子メール メッセージ レベルの場合です。 SharePoint のドキュメント ライブラリ、フォルダー、またはドキュメント セットに保持ラベルを適用して、その場所に保存されているすべてのドキュメントが既定の保持ラベルを継承することもできます。

さらに、保持ラベルは、コンテンツ [をレコードとしてマーク](records-management.md) するレコード管理をサポートします。 この場合、ラベルは、組織が規制要件を遵守するために必要になる可能性のあるコンテンツに追加の制限を設定します。

保持ラベルを作成および発行する手順については、次のガイダンスを参照してください。
- [アイテム保持ラベルを作成してアプリに適用する](create-apply-retention-labels.md)
- [保持ラベルをコンテンツに自動的に適用する](apply-retention-labels-automatically.md)

レコード管理を開始するには、「レコード管理の開始 [」を参照してください](get-started-with-records-management.md)。

### <a name="identify-and-define-sensitive-information-types"></a>機密情報の種類を特定して定義する

組織のデータ内の情報に含まれるパターンに基づいて機密情報の種類を定義します。 組 [み込みの機密情報の種類を使用](./sensitive-information-type-entity-definitions.md) すると、クレジット カード番号、銀行口座番号、パスポート番号などの識別と保護に役立ちます。 または、組織に [固有の独自のカスタムの](create-a-custom-sensitive-information-type.md) 感度情報の種類を作成します。

カスタムの機密情報の種類を定義する手順については、「セキュリティ コンプライアンス センターでカスタム機密情報の種類を作成する」 [を&してください](./create-a-custom-sensitive-information-type.md)。

### <a name="prevent-data-loss"></a>データの損失を防止する

[データ損失防止 (DLP)](dlp-learn-about-dlp.md)ポリシーを使用すると、組織全体で機密情報を特定、監視、およびMicrosoft 365できます。 DLP ポリシーを使用して、Microsoft サービス 間で機密性の高いアイテムを識別し、機密性の高いアイテムを偶発的に共有しないようにし、ユーザーがワークフローを中断することなくコンプライアンスを維持する方法を学ぶのに役立ちます。

DLP ポリシーを構成する手順については、DLP ポリシーの作成、 [テスト、調整を行います](create-test-tune-dlp-policy.md)。 データ損失管理のライセンス情報については、「セキュリティMicrosoft 365コンプライアンスに関する[&参照してください](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#office-365-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business)。

### <a name="detect-and-act-on-insider-risks"></a>インサイダー リスクの検出と対応

従業員は、幅広いプラットフォームとサービスでデータを作成、管理、共有するためのアクセスを増やしています。 ほとんどの場合、組織には、コンプライアンス要件と従業員のプライバシー基準を満たしながら、組織全体のリスクを特定および軽減するためのリソースとツールが限られています。 これらのリスクには、従業員を退出してデータを盗み、偶発的な過剰共有や悪意のある意図による組織外の情報のデータ漏洩が含まれる場合があります。

[Microsoft 365](insider-risk-management-policies.md)の Insider リスク管理は、サービスとサードパーティのインジケーターの全幅を使用して、リスクの高いユーザー アクティビティをすばやく特定し、トリアージし、行動するのに役立ちます。 Microsoft 365 および Microsoft Graph のログを使用すると、インサイダー リスク管理を使用して、リスク インジケーターを特定し、これらのリスクを軽減するためのアクションを実行するための特定のポリシーを定義できます。

インサイダー リスク管理ポリシーを計画および構成する手順については、「インサイダー[](insider-risk-management-plan.md)リスク管理の計画」および「インサイダー リスク管理の概要」を[参照してください](insider-risk-management-configure.md)。 インサイダー リスク管理のライセンス情報については、「セキュリティMicrosoft 365コンプライアンスに関する[ライセンス ガイダンス&参照してください](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#insider-risk-management)。