---
title: 管理ケースで保管担当者をAdvanced eDiscoveryする
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: 詳細を表示し、編集し、一括編集する方法については、Advanced eDiscoveryしてください。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a1e9e9d481073c8bb2827d5d65537dbf2b63ef1f
ms.sourcegitcommit: 555b200b618085706dabf8648d27fb6d6427cfce
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/30/2020
ms.locfileid: "49739870"
---
# <a name="manage-custodians-in-an-advanced-ediscovery-case"></a>管理ケースで保管担当者をAdvanced eDiscoveryする

ケース内の [ソース]タブAdvanced eDiscoveryには、ケースに追加されたすべての保管担当者の一覧が表示されます。 カストディアンをケースに追加すると、各保管担当者に関する詳細が Azure Active Directory から自動的に収集され、Advanced eDiscovery。

![保管担当者の管理](../media/CustodianDetails.PNG)

## <a name="view-custodian-details"></a>保管担当者の詳細を表示する

保管担当者に関する詳細を表示するには、[保管担当者] タブの一覧からカストディアン **をクリック** します。フライアウト ページが表示され、保管担当者に関する次の情報が含まれます。

- 連絡先情報

  - **[表示名** ] - 保管担当者のアドレス帳に表示される名前。 これは通常、保管担当者の名、ミドル イニシャル、および名の組み合わせです。
  
   - **Mail/SMTP** - 保管担当者のプライマリ SMTP アドレス (たとえば、brianj@contoso.onmicrosoft.com。 保管担当者のユーザー プリンシパル名 (UPN) も一覧表示されます。

  - **Title** - 保管担当者の役職。

  - **Department** - 保管担当者が動作する部署の名前。

  - **マネージャー** - 保管担当者のマネージャー。 指定された管理者は、この保管担当者のエスカレーション通信を受け取る。
  
- 場所情報

  - **City** - 保管担当者が置かれる都市。

  - **State** - 保管担当者の住所の州または州。

  - **国/地域** - 保管担当者が置かれる国/地域。

  - **Office** - 保管担当者の所在地。

- ケース情報

  - **保留状態** - 保管担当者が保留にされたかどうかを示します。 

  - **通信状態**: 保管担当者が保留通知を発行したかどうかを示します。 保管担当者が通知を発行した場合、このプロパティのこの値は発行 **済みです**。 保管担当者が通知を発行されていない場合、状態は未公開 **です**。 

  - **Status** - ケース内の保管担当者の状態。 Active の状態 **は** 、保管担当者がケースの一部である場合を示します。 カストディアンがケースから解放された場合、ステータスは [リリース済み] に **変更されます**。 

- データ ソースとインデックス情報

    - **データ ソース**- 保管担当者に関連付けられた、ケースの一部であるデータ ソース (メールボックス、サイト、および Teams) の数と種類を示します。

    - **インデックス更新時刻** - 高度なインデックス ジョブが最後にトリガーされた日時を示します。 このプロパティは、高度なインデックス作成プロセスが現在進行中の場合も示します。


## <a name="edit-a-custodian"></a>カストディアンの編集

ケースが進むにつれて、特定の保管担当者に関連する追加のデータ ソース&可能性があります。 その他のシナリオでは、確認され、関連性が高いとみなされた特定のデータ ソースを削除できます。

保管担当者に関連付けられているデータ ソースを更新するには、次の方法を実行します。

1. [電子情報開示 **] に> Advanced eDiscovery** ケースを開きます。
  
2. [ソース] **タブをクリック** します。
  
3. [カ **ストディアン] ページで** 、リストからカストディアンを選択し、フライアウト ページの **[編集** ] をクリックします。

    ![データ ソースの編集](../media/EditCustodianDataSource.PNG)
  
4. [**データ ソースの選択**] タブをクリックして、保管担当者のメールボックスとアカウントのExchangeを変更OneDrive、[データ ソースの選択] を **クリックします**。
  
5. [追加の **データ ソースの** 選択] タブをクリックして、保管担当者Teams、SharePoint、Exchangeメールボックスを追加または削除します。 

    保管担当者に関連付けられたデータ ソースの詳細については、「ケースに保管担当者を追加する」 [を参照してください](add-custodians-to-case.md)。 
  
6. [ **保管ホールドの配置] をクリック** して、保管担当者の保留を有効または無効にします。

## <a name="re-index-custodian-data"></a>保管担当者データの再インデックス

法的調査のためのほとんどの電子情報開示ワークフローでは、保管担当者が法的ケースに追加された後、保管担当者のデータのサブセットが検索されます。 ファイル サイズが非常に大きいか、データが破損する可能性があるため、保管担当者に関連付けられたデータ ソース内の一部のアイテムに部分的にインデックスが作成される場合があります。 Advanced eDiscovery の[高度](indexing-custodian-data.md)なインデックス作成機能を使用すると、ほとんどの部分的にインデックス付きアイテムをオンデマンドで再インデックス化することで自動的に修復できます。

カストディアンがケースに追加された場合、保管担当者に関連付けられたデータ ソースにあるデータは、(高度なインデックス作成プロセスによって) 自動的に再インデックス化されます。 つまり、データをダウンロードして修復してからオフラインで検索する代わりに、データを一所に残しておくことができます)。 ただし、法的ケースのライフサイクル中に、新しいデータ ソースが保管担当者に関連付けられている可能性があります。 この場合、高度なインデックス処理を実行して、部分的にインデックス付けされたアイテムを修復し、保管担当者のデータのインデックスを更新することで、保管担当者のデータを再インデックス化できます。

部分的にインデックス付けされたアイテムに対処するために再インデックスプロセスをトリガーするには、次の手順を実行します。

1. [電子情報開示 **] に> Advanced eDiscovery** ケースを開きます。

2. [ソース] **タブをクリック** します。

3. [保管 **担当者] ページで** 、データのインデックスを再作成する必要がある保管担当者を選択します。

4. [フライアウト] ページで、[インデックスの更新] **をクリックします**。

   インデックス ジョブが作成されたというダイアログが表示されます。

保管担当者データの再インデックスは、長時間実行されるプロセスです。作成された対応するジョブの名前は、保管 **担当者データの再インデックス化です**。 [ジョブ] タブまたは[カストディアン]タブで進行状況を追跡するには、[インデックスジョブの状態] 列の状態 **を監視** します。

詳細については、以下を参照してください。

- [処理中のエラーの操作](processing-data-for-case.md)

- [ジョブを管理する](managing-jobs-ediscovery20.md)

## <a name="release-a-custodian-from-a-case"></a>ケースから保管担当者を解放する

カストディアンは、ケースが閉じている場合、保管担当者がケースのコンテンツを保持する義務がなくなった場合、または保管担当者がケースに関連しなくなったと判断された場合に解放されます。 

保留通知が公開された後に保管担当者を解放すると、リリース通知が保管担当者に送信されます。 さらに、保管担当者に関連付けられたデータ ソースに配置された保留は削除されます。 保管担当者がサイレント ホールドに置かれた場合 、法的保留通知は発行されませんが、その保管担当者に関連付けられたデータ ソースに対する保留は削除されます。

保管担当者を解放するには、次の方法を使用します。 

1. [電子情報開示 **] に> Advanced eDiscovery** ケースを開きます。

2. [ソース] **タブをクリック** します。

3. [保管 **担当者] ページ** で、ケースから解放される保管担当者を選択します。

4. [フライアウト] ページで、[カストディアン **の解放] をクリックします**。

   保管担当者に関連付けられたデータ ソースに保留が設定されている場合、保留は削除され、別の Advanced eDiscovery ケースに関連付けられているその他の保留は引き続き適用されるという警告ページが表示されます。 これには、その他の種類の保持機能 (アイテム保持ポリシー Microsoft 365含まれます。

5. [ **はい]** をクリックして、保管担当者を解放する必要があります。 

    [保管担当者] タブのこのユーザーの状態が [リリース済み] に設定され、フライアウト ページの保留状態が False に **変更されます**。  

> [!NOTE]
> 保管担当者が複数の法的ケースに同時に関与している可能性があります。 カストディアンがケースから解放されると、他の事項の保留と通知は影響を受け取らない。

## <a name="bulk-edit-custodians"></a>保管担当者の一括編集

一括エディターを使用して、複数の保管担当者を同時に編集できます。 これを行うには、[保管担当者] タブで 2つ以上のカストディアンを選択して、一括エディターを表示し、タスクの 1 つをクリックします。

![複数の保管担当者の設定を編集するフライアウト ページ](../media/AeDBulkEditCustodians.png)
