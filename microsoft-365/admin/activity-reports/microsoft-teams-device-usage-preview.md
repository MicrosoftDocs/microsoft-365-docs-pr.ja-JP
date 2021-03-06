---
title: Microsoft 365管理センターのレポート - Microsoft Teamsの使用状況
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: '[レポート] からアプリMicrosoft Teamsレポートを取得して、組織で使用Microsoft Teamsアプリに関するMicrosoft 365します。'
ms.openlocfilehash: 096954ad246f3b10369dfbf683d04b6c81950b5e
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "51579640"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-device-usage"></a>Microsoft 365管理センターのレポート - Microsoft Teamsの使用状況

Microsoft 365 の [**レポート**] ダッシュボードには、組織内での製品全体に関するアクティビティが表示されます。 これにより、個別の製品レベルのレポートを詳細に確認して、各製品内のアクティビティについてより詳しく知ることができます。 [レポートの概要に関するトピック](activity-reports.md)を参照してください。 [アプリMicrosoft Teamsレポートでは、組織で使用されているアプリMicrosoft Teamsを把握できます。
  
> [!NOTE]
> レポートを表示するには、Microsoft 365 のグローバル管理者、グローバル閲覧者、レポート閲覧者、または Exchange、SharePoint、Skype for Business の管理者である必要があります。  
 
## <a name="how-to-get-to-the-microsoft-teams-app-usage-report"></a>Microsoft Teams アプリの使用状況レポートを取得する手順

1. 管理センターで、[**レポート**] \> [<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">使用状況</a>] ページの順に移動します。 
2. ダッシュボードのホームページで、アクティビティ カード **の**[その他の表示] Microsoft Teamsクリックします。
  
## <a name="interpret-the-microsoft-teams-app-usage-report"></a>Microsoft Teams アプリの使用状況レポートを解釈する

[デバイスの使用状況] タブを選択すると、Teamsレポートでデバイスの使用状況 **を表示** できます。<br/>![Microsoft 365レポート - Microsoft Teamsデバイスの使用状況を確認します。](../../media/e46c7f7c-8371-4a20-ae82-b20df64b0205.png)

[列 **の選択]** を選択して、レポートの列を追加または削除します。  <br/> ![Teamsデバイス レポート - 列の選択](../../media/3358d5d9-931b-4d30-931f-450b2f5717da.png)

また、[**エクスポート**] リンクを選択して、レポート データを Excel の .csv ファイルにエクスポートすることもできます。 これにより、すべてのユーザーのデータがエクスポートされ、単純な並べ替えとフィルター処理を行ってさらに分析することができます。 ユーザー数が 2000 未満である場合は、レポート自体のテーブル内で並べ替えとフィルター処理を行うことができます。 ユーザー数が 2000 を超える場合は、フィルター処理と並べ替えを行うために、データをエクスポートする必要があります。 

[ **Microsoft Teams デバイスの使用状況**] レポートでは、過去 7 日間、30 日間、90 日間、または 180 日間の傾向を確認できます。 ただし、レポートで特定の日を選択すると、表 (7) には、(レポートが生成された日付ではなく) 現在の日付から最大 28 日間のデータが表示されます。
  
|アイテム|説明|
|:-----|:-----|
|**測定基準**|**定義**|
|ユーザー名  <br/> |ユーザーの表示名。  <br/> |
|Windows  <br/> |ユーザーがデスクトップ クライアントのデスクトップ クライアントでアクティブTeamsベースのコンピューター上Windows選択されます。  <br/> |
|Mac  <br/> |ユーザーが macOS コンピューター上のデスクトップ Teamsでアクティブだった場合に選択されます。  <br/> |
|iOS  <br/> |iOS のモバイル クライアントでユーザーがアクティブTeams選択されます。  <br/> |
|Android スマートフォン  <br/> | Android のモバイル クライアントでユーザーがアクティブTeams選択されます。  <br/> |
|Chrome OS  <br/> |ユーザーが ChromeOS コンピューター上のデスクトップ Teamsでアクティブだった場合に選択されます。|
|Linux  <br/> | ユーザーが Linux コンピューター上のデスクトップ Teamsでアクティブだった場合に選択されます。  <br/> |
|Web  <br/> |ユーザーがデバイス上の Web クライアントでアクティブTeams選択されます。|
|最終アクティビティ日 (UTC)  <br/> |ユーザーがアクティビティに参加した最後の日付 (UTC) Teamsです。  <br/> |
|ライセンスが必要です|ユーザーにライセンスが割り当てTeams。|
|||