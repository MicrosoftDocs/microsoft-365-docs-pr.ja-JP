---
title: 管理センターの microsoft 365 レポート-Microsoft 365 アプリの使用状況
ms.author: sirkkuw
author: sirkkuw
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
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
description: Microsoft 365 管理センターの Microsoft 365 レポートダッシュボードを使用して、Microsoft 365 アプリの利用状況レポートを取得する方法について説明します。
ms.openlocfilehash: 0c30cee0c1abd76553d3adfebebb8fe38e92c56a
ms.sourcegitcommit: 039205fdaaa2a233ff7e95cd91bace474b84b68c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2020
ms.locfileid: "49611919"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-apps-usage"></a>管理センターの microsoft 365 レポート-Microsoft 365 アプリの使用状況

Microsoft 365 **Reports** dashboard には、組織内の製品全体にわたるアクティビティの概要が表示されます。 これにより、個別の製品レベルのレポートを詳細に確認して、各製品内のアクティビティについてより詳しく知ることができます。 [レポートの概要に関するトピック](activity-reports.md)を参照してください。

 たとえば、Microsoft 365 アプリアプリを使用するためにライセンスを付与された各ユーザーのアクティビティを、各アプリでのアクティビティと、プラットフォーム間でどのように利用するかを理解することができます。


 > [!NOTE]
 > レポートを表示するには、Microsoft 365 または Exchange、SharePoint、または Skype for Business 管理者のグローバル管理者、グローバルリーダー、またはレポート閲覧者である必要があります。

## <a name="how-to-get-to-the-microsoft-365-apps-usage-report"></a>Microsoft 365 アプリの使用状況レポートを取得する方法

1. 管理センターで、[**レポート**] \> [<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">使用状況</a>] ページの順に移動します。 
2. ダッシュボードのホームページで、[アクティブなユーザー]-[Microsoft 365 アプリカード] の [ **表示** ] をクリックします。

## <a name="interpret-the-microsoft-365-apps-usage-report"></a>Microsoft 365 アプリの使用状況レポートを解釈する

ユーザーおよび **プラットフォーム** のグラフを **見ると、** ユーザーの Microsoft 365 アプリアクティビティを表示できます。

![Microsoft 365 アプリの使用状況レポート](../../media/0bcf67e6-a6e4-4109-a215-369f9f20ad84.png)

|アイテム|説明|
 |:-----|:-----|
 |1. <br/> |過去7日間、30 90 日間、30日間、または180日の傾向を確認するには、 **Microsoft 365 アプリの使用状況** レポートを表示することができます。 ただし、レポートで特定の日を選択すると、表 (7) には、(レポートが生成された日付ではなく) 現在の日付から最大 28 日間のデータが表示されます。 <br/> |
 |2. <br/> |各レポートのデータは、通常、過去7日間にカバーされます。 <br/> |
 |3. <br/> |[ **ユーザー** ] ビューには、各アプリ (Outlook、Word、Excel、PowerPoint、OneNote、Teams) のアクティブユーザー数の傾向が表示されます。 "アクティブユーザー" とは、これらのアプリ内で意図的なアクションを実行するユーザーのことです。 <br/> |
 |4. <br/> |[ **プラットフォーム** ] ビューには、各プラットフォーム (Windows、Mac、Web、モバイル) について、すべてのアプリにわたってアクティブなユーザーの傾向が表示されます。 <br/> |
 |5.<br/>|[ **ユーザー** ] グラフの Y 軸は、それぞれのアプリに対してアクティブな一意のユーザーの数です。 [ **プラットフォーム**   ] グラフの Y 軸は、それぞれのプラットフォームの一意のユーザー数です。 両方のグラフの X 軸は、特定のプラットフォームでアプリが使用された日付です。<br/>|
 6.<br/>|凡例の項目を選択して、グラフに表示する系列をフィルター処理できます。 たとえば、[ **ユーザー** ] グラフでは、Outlook、Word、Excel、PowerPoint、OneDrive、または Teams を選択すると、それぞれに関連する情報のみが表示されます。 この選択を変更しても、その下のグリッドテーブルの情報は変更されません。|
 |7.<br/>|テーブルには、ユーザー レベルでのデータの内訳が表示されます。 テーブルの列は追加または削除できます。 <br/><br/>**Username** は、Microsoft アプリのアクティビティを実行したユーザーの電子メールアドレスです。<br><br/>[**最終アクティブ化日 (UTC)** ] は、ユーザーが Microsoft 365 アプリのサブスクリプションをアクティブ化した最新の日付です。<br/><br/>[**最後のアクティビティの日付 (UTC)** ] は、ユーザーによって意図的なアクティビティが実行された最新の日付です。 特定の日付に発生したアクティビティを表示するには、直接グラフ内の日付を選択します。<br/><br/>その他の列は、選択した期間にそのアプリ (Microsoft 365 アプリ内) でユーザーがアクティブであったかどうかを識別します。 |
 |8.<br/>|レポートに列を追加または削除するには、[ **列の選択** ] アイコンを選択します。|
 |9.<br/>|また、[**エクスポート**] リンクを選択して、レポート データを Excel の .csv ファイルにエクスポートすることもできます。 これにより、すべてのユーザーのデータがエクスポートされ、単純な集計、並べ替え、およびフィルター処理を行ってさらに分析することができます。 ユーザー数が100未満の場合は、レポート自体のテーブル内で並べ替えとフィルター処理を行うことができます。 100を超えるユーザーがいる場合は、フィルター処理と並べ替えを行うために、データをエクスポートする必要があります。|
