---
title: Yammer の保持の詳細
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
description: Yammer に適用されるアイテム保持ポリシーについて説明します。
ms.openlocfilehash: 1398bf385631967d92de760924ef94e2b3c16441
ms.sourcegitcommit: f7fbf45af64c5c0727fd5eaab309d20ad097a483
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2021
ms.locfileid: "53362296"
---
# <a name="learn-about-retention-for-yammer"></a>Yammer の保持の詳細

>*[セキュリティとコンプライアンスのための Microsoft 365 ライセンス ガイダンス](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)。*

> [!NOTE]
> この機能は現在プレビュー段階であり、変更される可能性があります。

この記事の情報は[保持の詳細](retention.md)に関する記事を補足するもので、Yammer に固有の情報が含まれています。

その他のワークロードについては、以下を参照してください。

- [SharePoint と OneDrive の保持の詳細](retention-policies-sharepoint.md)
- [Microsoft Teams の保持の詳細](retention-policies-teams.md)
- [Exchange の保持の詳細](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>保持と削除の対象となる機能

コミュニティ メッセージとユーザー メッセージの Yammer アイテムは、Yammer のアイテム保持ポリシーを使用して保持および削除できます。

絵文字の形で他人からの反応はこれらのメッセージに含まれていません。

## <a name="how-retention-works-with-yammer"></a>Yammer での保持のしくみ

このセクションを使用して、コンプライアンス要件がバックエンド ストレージとプロセスによってどのように満たされているかを説明します。現在、Yammer アプリに表示されているメッセージではなく、電子情報開示ツールで確認する必要があります。

アイテム保持ポリシーを使用して、Yammer のコミュニティ メッセージとユーザー メッセージのデータを保持し、これらのメッセージを削除できます。 バックグラウンドでは、Exchange メールボックスを使用してこれらのメッセージからコピーされたデータを保存します。 Yammer ユーザーのメッセージのデータは、ユーザー メッセージに含まれる各ユーザーのメールボックスの隠しフォルダーに保存され、グループ メールボックスの同様の隠しフォルダーがコミュニティ メッセージに使用されます。

コミュニティ メッセージのコピーは、ユーザーに @メンションしたり、ユーザーに返信を通知したりするときに、ユーザー メールボックスの隠しフォルダーに保存することもできます。 これらのメッセージはコミュニティ メッセージとして発信されますが、Yammer ユーザーのメッセージのアイテム保持ポリシーには、コミュニティ メッセージのコピーが含まれることがよくあります。

これらの隠しフォルダーは、ユーザーまたは管理者が直接アクセスできるようには設計されていませんが、代わりに、コンプライアンス管理者が電子情報開示ツールで検索できるデータを保存します。

> [!IMPORTANT]
> コミュニティ メッセージのコピーはユーザー メールボックスにも保存できるため、Yammer ユーザーのメッセージの削除アクションを含むアイテム保持ポリシーにより、元のコミュニティ メッセージが Yammer アプリのユーザーに表示されなくなる可能性があります。
> 
> ただし、元のメッセージのコピーは、コミュニティ グループ メールボックスの隠しフォルダーに引き続き存在し、コンプライアンスの目的で電子情報開示検索を使用してアクセスできます。

Yammer のメッセージは、Exchange メールボックスに対して構成されているアイテム保持ポリシーの影響を受けません。 Yammer のメッセージは Exchange に保存されますが、この Yammer のデータは、**Yammer コミュニティのメッセージ** と **Yammer ユーザーのメッセージ** の場所に対して構成されているアイテム保持ポリシーによってのみ含まれます。

> [!NOTE]
> ユーザーが Yammer のデータを保持するアクティブなアイテム保持ポリシーに含まれている場合、このポリシーに含まれるユーザーのメールボックスを削除すると、Yammer のデータを保持するためにメールボックスは[非アクティブなメールボックス](inactive-mailboxes-in-office-365.md)に変換されます。 ユーザーのこの Yammer データを保持する必要がない場合は、メールボックスを削除する前に、アイテム保持ポリシーからそのユーザー アカウントを除外します。

Yammer メッセージのアイテム保持ポリシーが構成されると、Exchange サービスのタイマー ジョブが、これらの Yammer メッセージが保存されている隠しフォルダ内のアイテムを定期的に評価します。 このタイマー ジョブを実行するには、最大 7 日間かかります。 アイテムの保持期間が満了すると、これらのアイテムは SubstrateHolds フォルダに移動されます。これは、すべてのユーザーまたはグループのメールボックスにある隠しフォルダで、アイテムが完全に削除される前の "論理的に削除済み" のアイテムが保存されます。

> [!NOTE]
> [データ保持の第 1 原則により](retention.md#the-principles-of-retention-or-what-takes-precedence)、別のアイテム保持ポリシーのために同じアイテムを保持する必要がある場合、または法的、調査上の理由から電子情報開示の保留リストにある場合、完全な削除は常に中断されます。

アイテム保持ポリシーが Yammer メッセージに対して構成された後のコンテンツのパスは、アイテム保持ポリシーの保持後に削除、保持のみ、あるいは削除のみのどれであるかによって異なります。

アイテム保持ポリシーが保持されてから削除される場合

![Yammer メッセージの保持フローの図](../media/yammerretentionlifecycle.png)

図内の 2 つのパスの場合:

1. 保持期間中にユーザーによって **Yammer メッセージが編集または削除された場合**、元のメッセージは直ちに SubstrateHolds フォルダーにコピー (編集の場合) または移動 (削除の場合) されてます。 メッセージは保存期間が終了するまで保存され、その後直ちに完全に削除されます。

2. **Yammer メッセージが削除されない場合**、および編集した後の現在のメッセージの場合は、保持期間満了後にメッセージは SubstructateHolds フォルダに移動されます。 このアクションには、有効期限から最大で 7 日かかります。 メッセージが SubstrateHolds フォルダにある場合は、直ちに完全に削除されます。 

> [!NOTE]
> SubstrateHolds フォルダー内のメッセージは、電子情報開示ツールで検索できます。 メッセージは完全に削除されるまで（SubstituteHolds フォルダ内）、メッセージは電子情報開示ツールで検索できます。

アイテム保持ポリシーが保持のみ、または削除のみの場合、コンテンツ パスは保持か削除かで異なります。

### <a name="content-paths-for-retain-only-retention-policy"></a>アイテム保持ポリシーが保持のみのコンテンツ パス

1. **Yammer メッセージが編集または削除された場合**、元のメッセージのコピーは直ちに SubstrateHolds フォルダに作成され、保持期間が満了するまでそこに保持されます。 その後直ちに、メッセージは SubstrateHolds フォルダから完全に削除されます。

2. **Yammer メッセージが変更または削除されていない場合**、および保持期間中に編集した後の現在のメッセージの場合は、保持期間の前後には何も起こらず、メッセージは元の場所に残ります。

### <a name="content-paths-for-delete-only-retention-policy"></a>アイテム保持ポリシーが削除のみのコンテンツ パス

1. 保持期間中に **Yammer メッセージが削除されない場合**、保持期間の終了時にメッセージは SubstrateHolds フォルダーに移動されます。 このアクションには、有効期限から最大で 7 日かかります。 その後直ちに、メッセージは SubstrateHolds フォルダから完全に削除されます。

2. 期間中に **ユーザーが Yammer メッセージを削除した場合**、そのアイテムは直ちに SubstrateHolds フォルダーに移動され、完全に削除されます。


## <a name="messages-and-external-users"></a>メッセージと外部ユーザー

既定では、Yammer ユーザーのメッセージのアイテム保持ポリシーは、組織内のすべてのユーザーに適用され、外部ユーザーには適用されません。 含まれているユーザーに対して **[編集]** オプションを使用して、アカウントを指定することで、外部ユーザーにアイテム保持ポリシーを適用することができます。

現時点では、Azure B2B ゲストユーザーはサポートされていません。

## <a name="when-a-user-leaves-the-organization"></a>ユーザーが組織を離れる場合 

ユーザーが組織を離れ、そのユーザーの Microsoft 365 アカウントが削除された場合、保持の対象となる Yammer ユーザーのメッセージは、非アクティブなメールボックスに保存されます。 これらのメッセージは、引き続きメールボックスが非アクティブになる前にユーザーに配置されたアイテム保持ポリシーの適用対象となり、電子情報開示の検索が可能です。 詳細については、「[Exchange Online の非アクティブなメールボックス](inactive-mailboxes-in-office-365.md)」を参照してください。 

ユーザーが Yammer にファイルを保存している場合は、SharePoint と OneDrive の「[同等のセクション](retention-policies-sharepoint.md#when-a-user-leaves-the-organization)」を参照してください。

## <a name="limitations"></a>制限事項

現在、Yammer のアイテム保持ポリシーはプレビュー中であり、継続的に保持機能の最適化に努めています。 当面は、Yammer のコミュニティ メッセージとユーザー メッセージで保持を使用する場合は、次の制限に注意してください。

- **Yammer ユーザーのメッセージ** の場所にある **[編集]** を選択した場合、ゲストや、メールボックス ユーザー以外のユーザーが表示される場合があります。 アイテム保持ポリシーはこれらのユーザー向けに設計されていないため、選択しないでください。

## <a name="configuration-guidance"></a>構成ガイダンス

Microsoft 365 で保持を構成するのが初めての場合は、「[アイテム保持ポリシーと保持ラベルの使用を開始する](get-started-with-retention.md)」を参照してください。

Yammer 用のアイテム保持ポリシーを構成する準備ができた場合は、「[アイテム保持ポリシーを作成して構成する](create-retention-policies.md)」を参照してください。