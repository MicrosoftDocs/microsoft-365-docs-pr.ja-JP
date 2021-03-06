---
title: Microsoft 365管理センターのレポート - Microsoft Teamsアクティビティ
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: ユーザー アクティビティ レポートのMicrosoft Teamsを取得し、組織のアクティビティTeamsを得る方法について学習します。
ms.openlocfilehash: a4f8cd995d1559da3846fbb38cc5a9441358da72
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "51579616"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-user-activity"></a>Microsoft 365管理センターのレポート - Microsoft Teamsアクティビティ

Microsoft 365 の [**レポート**] ダッシュボードには、組織内での製品全体に関するアクティビティが表示されます。 これにより、個別の製品レベルのレポートを詳細に確認して、各製品内のアクティビティについてより詳しく知ることができます。 [レポートの概要に関するトピック](activity-reports.md)を参照してください。 Microsoft Teams ユーザー アクティビティ レポートで、組織内の Microsoft Teams アクティビティに関する分析情報を取得します。
  
> [!NOTE]
> レポートを表示するには、Microsoft 365 のグローバル管理者、グローバル閲覧者、レポート閲覧者、または Exchange、SharePoint、Skype for Business の管理者である必要があります。  
 
## <a name="how-to-get-to-the-microsoft-teams-user-activity-report"></a>Microsoft Teams ユーザー アクティビティ レポートを取得する手順

1. 管理センターで、[**レポート**] \> [<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">使用状況</a>] ページの順に移動します。
2. ダッシュボードのホームページで、アクティビティ カード **の**[その他の表示] Microsoft Teamsクリックします。

## <a name="interpret-the-microsoft-teams-user-activity-report"></a>Microsoft Teams ユーザー アクティビティ レポートを解釈する

[ユーザー アクティビティ] タブを選択すると、Teamsレポートでユーザー アクティビティ **を表示** できます。 <br/>![Microsoft 365レポート - ユーザー Microsoft Teamsアクティビティを指定します。](../../media/1011877f-3cf0-4417-9447-91d0b2312aab.png)

[列 **の選択]** を選択して、レポートの列を追加または削除します。  <br/> ![Teams user activity report - choose columns](../../media/6d3c013e-2c5e-4d66-bb41-998aa4bd1c20.png)

また、[**エクスポート**] リンクを選択して、レポート データを Excel の .csv ファイルにエクスポートすることもできます。 これにより、すべてのユーザーのデータがエクスポートされ、単純な並べ替えとフィルター処理を行ってさらに分析することができます。 ユーザー数が 2000 未満である場合は、レポート自体のテーブル内で並べ替えとフィルター処理を行うことができます。 ユーザー数が 2000 を超える場合は、フィルター処理と並べ替えを行うために、データをエクスポートする必要があります。 オーディオ時間、ビデオ **時間、** 画面 **共有** 時間のエクスポート形式は、ISO8601 継続時間形式に従います。

[ **Microsoft Teams ユーザー アクティビティ**] レポートでは、過去 7 日間、30 日間、90 日間、または 180 日間の傾向を確認できます。 ただし、レポートで特定の日を選択すると、表 (7) には、(レポートが生成された日付ではなく) 現在の日付から最大 28 日間のデータが表示されます。

データ品質を確保するために、過去 3 日間の毎日のデータ検証チェックを実行し、検出されたギャップを埋めます。 プロセス中に履歴データに違いがある場合があります。

|アイテム|説明|
|:-----|:-----|
|**測定基準**|**定義**|
|ユーザー名  <br/> |ユーザーの電子メール アドレス。 実際のメール アドレスを表示することも、このフィールドを匿名にすることもできます。   <br/> |
|チャネル メッセージ   <br/> |ユーザーが指定した期間中にチーム チャットに投稿した一意のメッセージの数。  <br/> |
|チャットのメッセージ   <br/> |ユーザーが指定した期間中にプライベート チャットに投稿した一意のメッセージの数。  <br/> |
|会議の合計   <br/> |指定した期間中にユーザーが参加したオンライン会議の数。  <br/> |
|1:1 通話   <br/> | 指定した期間中にユーザーが参加した 1:1 呼び出しの数。  <br/> |
|最終アクティビティ日 (UTC)  <br/> |ユーザーがアクティビティに参加した最後のMicrosoft Teams日付。<br/> |
|会議はアドホックに参加しました   <br/> | 指定した期間中にユーザーが参加した臨時会議の数。  <br/> |
|臨時に開催される会議 <br/> |指定した期間中にユーザーが組織した臨時会議の数。 <br/>|
|組織された会議の合計  <br/> |指定した期間中にユーザーが組織した 1 回限りのスケジュール済み、定期的、アドホック、および未分類の会議の合計。  <br/> |
|参加した会議の総数  <br/> |ユーザーが指定した期間中に参加した、スケジュールされた、定期的、アドホック、および未分類の 1 回限りの会議の合計。  <br/> |
|スケジュールされた 1 回の会議  <br/> |指定した期間中にユーザーが組織した 1 回のスケジュールされた会議の数。  <br/> |
|定期的にスケジュールされた会議  <br/> |指定した期間中にユーザーが組織した定期的な会議の数。  <br/> |
|会議は、スケジュールされた 1 回に参加しました  <br/> |指定した期間中にユーザーが参加した 1 回のスケジュールされた会議の数。  <br/> |
|会議は定期的なスケジュールに参加しました  <br/> |指定した期間中にユーザーが参加した定期的な会議の数。  <br/> |
|ライセンスが必要です  <br/> |ユーザーにライセンスが割り当てTeams。 <br/>|
|その他のアクティビティ  <br/>|ユーザーはアクティブですが、レポートで提供される公開されたアクションの種類以外のアクティビティを実行しています (チャネル メッセージとチャット メッセージの送信または返信、スケジュール設定、または 1:1 の通話と会議への参加)。 アクションの例は、ユーザーがメッセージの状態またはTeams状態Teamsを変更するか、チャネル メッセージの投稿を開いたが返信しない場合です。  <br/>|
|未分類の会議 <br/>|スケジュールまたは定期的または臨時として分類できないもの。 これらは数が短く、テレメトリ情報が改ざんされたため、ほとんどを特定できない。 |
|||