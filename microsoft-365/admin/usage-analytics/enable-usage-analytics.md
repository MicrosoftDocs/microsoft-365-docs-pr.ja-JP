---
title: Microsoft 365 利用状況分析を有効にする
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9db96e9f-a622-4d5d-b134-09dcace55b6a
description: テナントのデータ収集を開始する方法については、Microsoft 365 Usage Analytics テンプレート アプリを使用Power BI。
ms.openlocfilehash: c0e39a307ee75c661e0f91fcbbcfeae3d95c7257
ms.sourcegitcommit: 00f001019c653269d85718d410f970887d904304
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2021
ms.locfileid: "53394751"
---
# <a name="enable-microsoft-365-usage-analytics"></a>Microsoft 365 利用状況分析を有効にする

Microsoft 365の使用状況分析は、米国政府機関向けMicrosoft 365まだCommunity。

## <a name="before-you-begin"></a>はじめに

使用状況分析をMicrosoft 365するには、まずデータを Microsoft 365 管理センター で使用し、次にテンプレート アプリを開始する必要Power BI。

## <a name="get-power-bi"></a>Power BI を取得する

まだインストールしていない場合は[Power BIにサインアップ](https://go.microsoft.com/fwlink/p/?linkid=845347)Power BI Pro。 [**無料で試** 用] を選択して試用版にサインアップするか、[今すぐ購入] を選択して、Power BI Pro。


[ **製品**] を展開して Power BI のバージョンを購入することもできます。

> [!NOTE]
> テンプレート アプリをインストールPower BI Pro配布するには、ユーザー ライセンスが必要です。 詳細については、「前提条件」を [参照してください](/power-bi/service-template-apps-install-distribute?source=docs#prerequisites)。

データを共有するには、ユーザーとデータを共有するユーザー、Power BI Pro ライセンスが必要、またはコンテンツが Power BI プレミアム サービスの[ワークスペースにある必要があります](/power-bi/service-premium-what-is)。

## <a name="enable-the-template-app"></a>テンプレート アプリを有効にする

テンプレート アプリを有効にするには、グローバル管理者である **必要があります**。

詳細 [については、「管理者の役割」](../add-users/about-admin-roles.md) を参照してください。

1. 管理センターで、[組織設定サービス] タブ **設定** \> **に** \> **移動** します。

2. [サービス] **タブで** 、[レポート] を  **選択します**。

3. 開く [レポート] パネルで、[レポート データを有効にする] を [Microsoft 365の使用状況分析で使用Power BI] を [**保存中**]**に** \> **設定します**。

データ収集プロセスは、テナントのサイズに応じて 2 ~ 48 時間で完了します。 データ **収集が完了Power BI[** 移動] ボタンが有効になります (灰色は表示されません)。

## <a name="start-the-template-app"></a>テンプレート アプリを起動する

テンプレート アプリを起動するには、グローバル管理者、レポートリーダー、Exchange管理者、Skype for Business管理者、または管理者SharePoint **する必要があります**。 

1. テナント ID をコピーし、[移動]**を選択Power BI。**

2. When you get to Power BI, sign in. 次に **、[アプリ]** -> **ナビゲーション メニューから**[アプリを取得する] を選択します。

3. [アプリ **] タブ** で、検索ボックスにMicrosoft 365を入力し、[使用状況分析Microsoft 365今すぐ取得する] \> **を選択します**。

    [![[今すぐ取得] を選択します。](../../media/78102250-9874-4a32-8365-436f13560b52.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics)

4. アプリがインストールされた後。 タイルを選択して開きます。

5. [アプリ **の探索] を** 選択して、サンプル データを使用してアプリを表示します。 **[Connect]** を選択して、アプリを組織のデータに接続します。

6. [Connect] を選択し、[Connect から Microsoft 365 利用状況分析] 画面で、手順 (1) でコピーしたテナント ID (ダッシュなし) を入力し、[次へ] を選択します。  

7. 次の画面で、[認証]**メソッドとして [OAuth2]** **を選択します** \> 。 他の認証方法を選択すると、テンプレート アプリへの接続が失敗します。

    ![認証方法として Microsoft アカウントを選択する](../../media/ab6f0463-c3f7-4088-a605-67c699fa86adnew.png)

8. テンプレート アプリがインスタンス化されると、Microsoft 365分析ダッシュボードが web 上Power BIで利用できます。 ダッシュボードの初期読み込みには 2 ~ 30 分かかります。

テナント レベルの集計は、オプトイン後にすべてのレポートで使用できます。 **ユーザー レベルの詳細は、オプトイン後の次の暦月の 5 日の周りにのみ利用できます**。 これは、[ユーザー アクティビティ] の下のすべての[](navigate-and-utilize-reports.md)レポートに影響します (これらのレポートを表示および使用する方法のヒントについては、「Microsoft 365 利用状況分析のレポートを移動して利用する」を参照してください)。

## <a name="make-the-collected-data-anonymous"></a>収集されたデータを匿名にする

すべてのレポート用に収集されるデータを匿名にするためには、グローバル管理者になる必要があります。 これにより、レポートやテンプレート アプリのユーザー名、グループ名、サイト名などの識別可能な情報が非表示になります。

1. 管理センターで、[組織] の[組織設定] 設定[サービス] タブで \> **、[** レポート] を選択 **します**。 

2. [ **レポート] を** 選択し、[匿名識別子の **表示] を選択します**。 この設定は、使用状況レポートとテンプレート アプリの両方に適用されます。

3. [**変更の保存**] を選択します。

## <a name="related-content"></a>関連コンテンツ

[利用状況分析について](usage-analytics.md) (記事)\
[使用状況分析の最新バージョンを取得](get-the-latest-version-of-usage-analytics.md) する (記事)\
[使用状況分析のレポートを移動Microsoft 365活用する](navigate-and-utilize-reports.md)(記事)