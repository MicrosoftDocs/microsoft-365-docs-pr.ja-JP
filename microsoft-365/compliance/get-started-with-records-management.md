---
title: レコード管理の使用を開始する
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: 法的事項、ビジネス、または規制上の義務を有する価値の高いコンテンツを管理する、Microsoft 365 向けのレコード管理ソリューションが必要であるのに、どこから開始すればいいかわからなくなっていませんか? 開始するのに役立つ実用的なガイダンスをご覧ください。
ms.openlocfilehash: bec70df94ce81ee7497b3ec236dca5649ce90cb7
ms.sourcegitcommit: 1780359234abdf081097c8064438d415da92fb85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "46778643"
---
# <a name="get-started-with-records-management"></a>レコード管理の使用を開始する

>*[セキュリティとコンプライアンスのための Microsoft 365 ライセンス ガイダンス](https://aka.ms/ComplianceSD)。*

レコード管理ソリューションを使用して、組織内の法的事項、ビジネス、または規制上の義務を有する価値の高いコンテンツの管理を開始する準備はできましたか? 開始するために、次の高水準なガイダンスを参考にできます。

1. **レコード管理ソリューションの理解**と、ドキュメントやメールがレコード宣言される場合にどのようなアクションが許可されたり禁止されたりするかについて説明します。[レコード管理に関する詳細情報](records-management.md)。 

2. 保持ラベルはレコード宣言に使用されるため、SharePoint および Exchange 向けの**アイテム保持レベルや保持の機能を理解してください**。[保持ポリシーおよび保持ラベルに関する詳細情報](retention.md)

3. 既存のプランをお持ちの場合は、[既存のプランをインポート](file-plan-manager.md#import-retention-labels-into-your-file-plan )することで**保持設定およびアクションのためのファイルプランを作成**するか、[レコード宣言する新しい保持ラベル](declare-records.md)を作成します。

4. **保持ラベルを発行して適用**します。 保持ラベルは複数のポリシーで使用できる再利用可能な文書パーツで、ユーザーのワークフローに組み込むことができます。 
    
    - [アイテム保持ラベルを作成してアプリに適用する](create-apply-retention-labels.md)
    - [保持ラベルをコンテンツに自動的に適用する](apply-retention-labels-automatically.md)

## <a name="subscription-and-licensing-requirements-for-retention-policies-and-retention-labels"></a>アイテム保持ポリシーと保持ラベルのサブスクリプションおよびライセンス要件

レコード管理はさまざまな異なるサブスクリプションに対応しており、ユーザーのライセンス要件は使用する機能によって異なります。

Microsoft 365 コンプライアンス機能のメリットを得られるようにユーザーにライセンスを付与するためのオプションを確認するには、「[セキュリティとコンプライアンスのための Microsoft 365 ライセンス ガイダンス](https://aka.ms/ComplianceSD)」を参照してください。 レコード管理については、「[レコード管理](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#records-management)」セクション、および機能レベルのライセンス要件に関する PDF または Excel ダウンロード ファイルを参照してください。

## <a name="permissions-required-for-records-management"></a>レコード管理に必要なアクセス許可

レコード管理を担当するコンプライアンス チームのメンバーには、[Microsoft 365 コンプライアンス センター](https://compliance.microsoft.com/)へのアクセス許可が必要です。 既定により、テナント管理者 (グローバル管理者) はこの場所にアクセスでき、コンプライアンス責任者やその他のユーザーにテナント管理者のすべての権限を与えることなくアクセスできます。この制限された管理に権限を付与するには、ユーザーを [**レコード管理**] の管理者役割グループに追加することをお勧めします。 手順については、「[ユーザーにセキュリティ/コンプライアンス センターへのアクセス権を付与する](https://docs.microsoft.com/microsoft-365/security/office-365-security/grant-access-to-the-security-and-compliance-center)」を参照してください。

これらのアクセス許可は、レコード宣言する保持ラベルの作成、構成、適用にのみ必要です。 保持ラベルを構成するユーザーは、コンテンツへのアクセスを必要としません。

## <a name="common-scenarios-for-records-management"></a>レコード管理の一般的なシナリオ

次の表は、レコード管理でサポートされているシナリオにビジネス要件をマッピングするのに役立ちます。

> [!NOTE]
> レコード管理では、アイテム保持ラベルを使用してアイテムをレコードとしてマークするため、この表にある多くのシナリオは、[アイテム保持ポリシーと保持ラベルの一般的なシナリオ](get-started-with-retention.md#common-scenarios-for-retention-policies-and-retention-labels)としても表示されます。

|必要な作業...|ドキュメント|
|----------------|---------------|
|レコードを宣言する |[保持ラベルを使用してレコードを宣言する](declare-records.md)|
|レコードを更新する |[SharePoint または OneDrive に保存されているレコードを更新するためにレコードのバージョン管理を使用する](record-versioning.md)|
|管理者とユーザーが、ドキュメントやメールに対して保持アクションと削除アクションのセットを手動で適用できるようにする <br />-  SharePoint <br />- OneDrive <br />- Outlook および Outlook on the web|[アイテム保持ラベルを作成してアプリに適用する](create-apply-retention-labels.md)|
|サイト管理者が、SharePoint ライブラリ、フォルダー、ドキュメント セット内のすべてのコンテンツに既定の保持ラベルを設定できるようにする|[アイテム保持ラベルを作成してアプリに適用する](create-apply-retention-labels.md)|
|ユーザーが、Outlook のルールを使用して、メールに保持ラベルを自動的に適用できるようにする|[アイテム保持ラベルを作成してアプリに適用する](create-apply-retention-labels.md)|
|ドキュメントやメールに対して保持アクションと削除アクションのセットを自動的に適用する |[保持ラベルをコンテンツに自動的に適用する](apply-retention-labels-automatically.md)|
|次のようなイベントが発生したときに保持期間を開始する  <br />- 従業員が退職する <br />- 契約満了 <br />- 製品の有効期間の終了| [イベントの発生時に保持を開始する](event-driven-retention.md)|
|SharePoint で各種ドキュメントのライフサイクルを管理する| [保持ラベルを使用して、SharePoint に保存されているドキュメントのライフサイクルを管理する](auto-apply-retention-labels-scenario.md)|
|保持期間の終了時にコンテンツが削除される前に、誰かがレビューと承認を行うようにする|[廃棄確認](disposition.md#disposition-reviews) |
|保持期間の終了時に削除されるコンテンツの廃棄の証明を取得する|[レコードの廃棄](disposition.md#disposition-of-records) |
| 保持ラベルが適用される方法と場所を監視する | [保持ラベルの監視](retention.md#monitoring-retention-labels) |

## <a name="end-user-documentation-for-records"></a>レコードに関するエンド ユーザー向けのドキュメント

レコード管理に使用されている保持ラベルは、Microsoft 365 アプリで UI に存在します。 保持ラベルを運用ネットワークに展開する前に、エンド ユーザーとヘルプ デスクに必ずガイダンスを提供してください。

最も効果的なエンド ユーザー向けのドキュメントは、選択した保持ラベル名と構成に関するカスタマイズされたガイダンスと手順です。 ただし、基本的な手順については次の情報を使用できます。

- [保持ラベルを手動で適用する](create-apply-retention-labels.md#manually-apply-retention-labels)