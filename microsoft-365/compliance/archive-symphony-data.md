---
title: シンフォニー データをアーカイブするコネクタを設定Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
description: 管理者は、Veritas Symphony からデータをインポートおよびアーカイブするコネクタを設定して、Microsoft 365。 このコネクタを使用すると、サードパーティのデータ ソースからデータをアーカイブできます。Microsoft 365。 このデータをアーカイブした後、法的保持、コンテンツ検索、保持ポリシーなどのコンプライアンス機能を使用して、サードパーティのデータを管理できます。
ms.openlocfilehash: b3ddb6826f7ef68808a819ee1d860b020efea98a
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51163981"
---
# <a name="set-up-a-connector-to-archive-symphony-data"></a>シンフォニー データをアーカイブするコネクタをセットアップする

コンプライアンス センターの Veritas コネクタをMicrosoft 365、シンフォニー データをインポートおよびアーカイブして、組織のユーザー メールボックスMicrosoft 365します。 シンフォニーは、金融サービス業界で使用されるメッセージングとコラボレーション プラットフォームです。 Veritas には[](https://globanet.com/symphony)、Microsoft 365 コンプライアンス センターにシンフォニー データ コネクタが備え付け、サード パーティのデータ ソースからアイテムを (定期的に) キャプチャし、それらのアイテムをユーザー メールボックスにインポートするために構成できます。 コネクタは、アイテムのコンテンツをシンフォニー アカウントから電子メール メッセージ形式に変換し、そのアイテムをメールボックスにインポートMicrosoft 365。

ユーザー メールボックスにシンフォニー通信を格納した後、訴訟ホールド、電子情報開示、保持ポリシーと保持ラベル、通信コンプライアンスなどの Microsoft 365 コンプライアンス機能を適用できます。 シンフォニー コネクタを使用して、Microsoft 365データをインポートおよびアーカイブすると、組織が政府機関および規制ポリシーに準拠しつ付けるのに役立ちます。

## <a name="overview-of-archiving-symphony-data"></a>シンフォニー データのアーカイブの概要

次の概要では、データ コネクタを使用してシンフォニー通信をアーカイブするプロセスについて説明Microsoft 365。

![シンフォニー のアーカイブ ワークフロー](../media/SymphonyConnectorWorkflow.png)

1. 組織は、シンフォニーと一緒にシンフォニー サイトを設定および構成します。

2. 24 時間に 1 回、シンフォニーからのチャット メッセージが Veritas Merge1 サイトにコピーされます。 また、コネクタはチャット メッセージのコンテンツを電子メール メッセージ形式に変換します。

3. Microsoft 365 コンプライアンス センターで作成するシンフォニー コネクタは、毎日 Veritas Merge1 サイトに接続し、Microsoft クラウド内の安全な Azure Storage 場所にメッセージを転送します。

4. コネクタは、手順 3 で説明したように、自動ユーザー マッピングの *Email* プロパティの値を使用して、変換されたメッセージ アイテムを特定のユーザーのメールボックスにインポートします。 **シン** フォニーという名前の受信トレイ フォルダー内の新しいサブフォルダーがユーザー メールボックスに作成され、メッセージ アイテムがそのフォルダーにインポートされます。 コネクタは *、Email* プロパティの値を使用してアイテムをインポートするメールボックスを決定します。 すべてのチャット メッセージには、このプロパティが含まれるので、参加者ごとに電子メール アドレスが設定されます。

## <a name="before-you-begin"></a>はじめに

- Microsoft コネクタ用の Veritas Merge1 アカウントを作成します。 アカウントを作成するには [、Veritas カスタマー サポートにお問い合わせください](https://globanet.com/ms-connectors-contact)。 手順 1 でコネクタを作成するときに、このアカウントにサインインします。

- 手順 1 でシンフォニー コネクタを作成し (および手順 3 で完了する) ユーザーは、Exchange Online のメールボックスインポートエクスポートの役割に割り当てる必要があります。 この役割は、コンプライアンス センターの [**データ** コネクタ] ページにコネクタを追加Microsoft 365必要です。 既定では、この役割はグループ内の役割グループExchange Online。 [メールボックスのインポートエクスポート] 役割は、組織の [組織の管理] 役割グループに追加Exchange Online。 または、役割グループを作成し、メールボックスインポートエクスポートの役割を割り当て、適切なユーザーをメンバーとして追加できます。 詳細については、「グループ内の[役割グループを](/Exchange/permissions-exo/role-groups#create-role-groups)管理[](/Exchange/permissions-exo/role-groups#modify-role-groups)する」の「役割グループの作成」または「役割グループの変更」セクションを参照Exchange Online。

## <a name="step-1-set-up-the-symphony-connector"></a>手順 1: シンフォニー コネクタをセットアップする

最初の手順は、コンプライアンス センターの [データ コネクタ] ページにアクセスしMicrosoft 365シンフォニー データのコネクタを作成することです。

1. [データ コネクタ [https://compliance.microsoft.com](https://compliance.microsoft.com/) シンフォニー]**に移動し、[データ コネクタ**  >  **] をクリックします**。

2. [シンフォ **ニー製品の説明** ] ページで、[コネクタの追加] **をクリックします**。

3. [サービス条件 **] ページで、[** 同意する] を **クリックします**。

4. コネクタを識別する一意の名前を入力し、[次へ] を **クリックします**。

5. コネクタを構成するには、Merge1 アカウントにサインインします。

## <a name="configure-the-symphony-connector-on-the-veritas-merge1-site"></a>Veritas Merge1 サイトでシンフォニー コネクタを構成する

2 番目の手順は、Merge1 サイトでシンフォニー コネクタを構成することです。 Veritas Merge1 サイトでのシンフォニー コネクタの構成の詳細については [、「Merge1 サード](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Symphony%20User%20Guide%20.pdf)パーティ コネクタ ユーザー ガイド」を参照してください。

[ファイルの **保存と&完了**] をクリックすると、コンプライアンス センターのコネクタ ウィザードの [ユーザー Microsoft 365] ページが表示されます。

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>手順 3: ユーザーをマップし、コネクタのセットアップを完了する

ユーザーをマップし、コンプライアンス センターでコネクタMicrosoft 365するには、次の手順を実行します。

1. [外部ユーザー **をユーザーにマップMicrosoft 365] ページで**、自動ユーザー マッピングを有効にします。 シンフォニー アイテムには、組織内のユーザーの電子メール アドレスを含む *Email* というプロパティが含まれます。 コネクタでこのアドレスをユーザーに関連付Microsoft 365、アイテムはユーザーのメールボックスにインポートされます。

2. [**次へ**] をクリックし、設定を確認し、[データ コネクタ] ページに移動して、新しいコネクタのインポート プロセスの進行状況を確認します。

## <a name="step-4-monitor-the-symphony-connector"></a>手順 4: シンフォニー コネクタを監視する

シンフォニー コネクタを作成した後、コンプライアンス センターでコネクタのMicrosoft 365できます。

1. 左側の [https://compliance.microsoft.com](https://compliance.microsoft.com) ナビゲーションで [ **データ コネクタ] に** 移動してクリックします。

2. [コネクタ **] タブをクリック** し、シンフォニー コネクタ **を選択** して、フライアウト ページを表示します。 このページには、コネクタに関するプロパティと情報が含まれる。

3. [**ソースを含むコネクタの状態**] で、[ログのダウンロード] リンクをクリックして、コネクタの状態ログを開く (または保存) します。  このログには、Microsoft クラウドにインポートされたデータに関する情報が含まれます。

## <a name="known-issues"></a>既知の問題

- 現時点では、10 MB を超える添付ファイルやアイテムのインポートはサポートされていません。 大きいアイテムのサポートは、後日利用できます。