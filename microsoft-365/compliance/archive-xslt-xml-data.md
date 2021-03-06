---
title: XSLT/XML データをアーカイブするコネクタを設定Microsoft 365
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
description: 管理者は、Veritas から XSLT/XML データをインポートおよびアーカイブするコネクタを、Microsoft 365。 このコネクタを使用すると、Microsoft 365 のサード パーティデータ ソースからデータをアーカイブし、法的保持、コンテンツ検索、保持ポリシーなどのコンプライアンス機能を使用して、組織のサードパーティ データを管理できます。
ms.openlocfilehash: 51b05f83c51626bc60dc19b5ec9a63750903281c
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51163761"
---
# <a name="set-up-a-connector-to-archive-xsltxml-data"></a>XSLT/XML データをアーカイブするコネクタをセットアップする

コンプライアンス センターの Veritas コネクタをMicrosoft 365して、Web ページ ソースから組織のユーザー メールボックスにデータをインポートおよびアーカイブMicrosoft 365します。 Veritas には、XSLT (拡張可能スタイル シート言語変換) を使用して作成されたファイルを迅速に開発して、XML ファイルを Microsoft 365 にインポートできる他のファイル形式 (HTML やテキストなど) に変換できる[XSLT/XML](https://globanet.com/xslt-xml)コネクタが用意されています。 コネクタは、アイテムのコンテンツを XSLT/XML ソースから電子メール メッセージ形式に変換し、変換されたアイテムを別のメールボックスMicrosoft 365します。

XSLT/XML データがユーザー メールボックスに格納された後、訴訟ホールド、電子情報開示、保持ポリシー、保持ラベルなどのコンプライアンス機能Microsoft 365を適用できます。 XSLT/XML コネクタを使用してデータをインポートおよびアーカイブMicrosoft 365、組織が政府機関および規制ポリシーに準拠しつ付けるのに役立ちます。

## <a name="overview-of-archiving-xsltxml-data"></a>XSLT/XML データのアーカイブの概要

次の概要では、コネクタを使用して XSLT/XML ソース データをアーカイブするプロセスについて説明Microsoft 365。

![XSLT/XML データのアーカイブ ワークフロー](../media/XSLT-XMLConnectorWorkflow.png)

1. 組織は XSLT/XML ソースを使用して XSLT/XML サイトを設定および構成します。

2. 24 時間に 1 回、XSLT/XML ソースからのチャット メッセージが Veritas Merge1 サイトにコピーされます。 コネクタは、コンテンツを電子メール メッセージ形式に変換します。

3. Microsoft 365 コンプライアンス センターで作成した XSLT/XML コネクタは、毎日 Veritas Merge1 サイトに接続し、Microsoft クラウド内のセキュリティで保護された Azure Storage 場所にメッセージを転送します。

4. コネクタは、手順 3 で説明したように、自動ユーザー マッピングの *Email* プロパティの値を使用して、変換されたメッセージ アイテムを特定のユーザーのメールボックスにインポートします。 **XSLT/XML** という名前の受信トレイ フォルダー内の新しいサブフォルダーがユーザー メールボックスに作成され、メッセージ アイテムがそのフォルダーにインポートされます。 コネクタは、Email プロパティの値を使用して *これを行* います。 すべてのメッセージには、このプロパティが含まれるので、メッセージのすべての参加者の電子メール アドレスが設定されます。

## <a name="before-you-begin"></a>はじめに

- Microsoft コネクタ用の Veritas Merge1 アカウントを作成します。 このアカウントを作成するには [、Veritas カスタマー サポートにお問い合わせください](https://www.veritas.com/content/support/)。 手順 1 でコネクタを作成するときに、このアカウントにサインインします。

- 手順 1 で XSLT/XML コネクタを作成し (手順 3 で完了する) ユーザーは、Exchange Online のメールボックスインポートエクスポートの役割に割り当てる必要があります。 この役割は、コンプライアンス センターの [**データ** コネクタ] ページにコネクタを追加Microsoft 365必要です。 既定では、この役割はグループ内の役割グループExchange Online。 [メールボックスのインポートエクスポート] 役割は、組織の [組織の管理] 役割グループに追加Exchange Online。 または、役割グループを作成し、メールボックスインポートエクスポートの役割を割り当て、適切なユーザーをメンバーとして追加できます。 詳細については、「グループ内の[役割グループを](/Exchange/permissions-exo/role-groups#create-role-groups)管理[](/Exchange/permissions-exo/role-groups#modify-role-groups)する」の「役割グループの作成」または「役割グループの変更」セクションを参照Exchange Online。

## <a name="step-1-set-up-an-xsltxml-connector"></a>手順 1: XSLT/XML コネクタをセットアップする

最初の手順は、コンプライアンス センターの **データ** コネクタMicrosoft 365 XSLT/XML データのコネクタを作成することです。

1. に移動し [https://compliance.microsoft.com](https://compliance.microsoft.com/) 、[データコネクタ  >  **XSLT/XML] をクリックします**。

2. **[XSLT/XML 製品の説明]** ページで、[新しいコネクタの **追加] をクリックします**。

3. [サービス条件 **] ページで、[** 同意する] を **クリックします**。

4. コネクタを識別する一意の名前を入力し、[次へ] を **クリックします**。

5. コネクタを構成するには、Merge1 アカウントにサインインします。

## <a name="step-2-configure-an-xsltxml-connector"></a>手順 2: XSLT/XML コネクタを構成する

2 番目の手順は、Merge1 サイトで XSLT/XML コネクタを構成することです。 Veritas Merge1 サイトで XSLT/XML コネクタを構成する方法については [、「Merge1 サード](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20XSLT-XML%20User%20Guide%20.pdf)パーティ コネクタ ユーザー ガイド」を参照してください。

[ファイルの **保存と&完了**] をクリックすると、コンプライアンス センターのコネクタ ウィザードの [ユーザー Microsoft 365] ページが表示されます。

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>手順 3: ユーザーをマップし、コネクタのセットアップを完了する

1. ユーザーをマップし、コンプライアンス センターでコネクタMicrosoft 365するには、以下の手順に従います。

2. **[XSLT/XML ユーザーをユーザーにマップMicrosoft 365] ページ** で、自動ユーザー マッピングを有効にします。 XSLT/XML アイテムには、組織内のユーザーの電子メール アドレスを含む *Email* というプロパティが含まれます。 コネクタでこのアドレスをユーザーに関連付Microsoft 365、アイテムはユーザーのメールボックスにインポートされます。

3. [**次へ**] をクリックし、設定を確認し、[データ コネクタ] ページに移動して、新しいコネクタのインポート プロセスの進行状況を確認します。

## <a name="step-4-monitor-the-xsltxml-connector"></a>手順 4: XSLT/XML コネクタを監視する

XSLT/XML コネクタを作成した後、コンプライアンス センターでコネクタのMicrosoft 365できます。

1. 左側の [https://compliance.microsoft.com](https://compliance.microsoft.com) ナビゲーションで [ **データ コネクタ] に** 移動してクリックします。

2. [コネクタ **] タブをクリック** し **、XSLT/XML** コネクタを選択して、フライアウト ページを表示します。 このページには、コネクタに関するプロパティと情報が含まれる。

3. [**ソースを含むコネクタの状態**] で、[ログのダウンロード] リンクをクリックして、コネクタの状態ログを開く (または保存) します。  このログには、Microsoft クラウドにインポートされたデータが含まれます。

## <a name="known-issues"></a>既知の問題

- 現時点では、10 MB を超える添付ファイルやアイテムのインポートはサポートされていません。 大きいアイテムのサポートは、後日利用できます。