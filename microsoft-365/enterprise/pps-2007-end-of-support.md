---
title: PerformancePoint Server 2007 のサポート終了ロードマップ
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- PSV120
- PDD140
- MET150
ms.assetid: 89d9feee-2285-419c-8c14-0f7f583536e0
f1.keywords:
- NOCSH
description: PerformancePoint Server 2007、ProClarity、および SharePoint Server 2007 はサポートの終了に達しました。 この記事を読んで、BI ソリューションのアップグレードを計画する方法についてお読みください。
ms.openlocfilehash: aa6adae24d78b6be72f17fd56c272b1293e6fcdc
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "50927338"
---
# <a name="performancepoint-server-2007-end-of-support-roadmap"></a>PerformancePoint Server 2007 のサポート終了ロードマップ

*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*

Office 2007 のサーバーとアプリケーションは、ビジネス インテリジェンス (BI) ソリューションの一部として使用している可能性があるサーバーやアプリケーションなど、サポートの最後に達しています。 次の表に、影響を受ける BI アプリケーションの一覧を示します。
  
|**Microsoft BI アプリケーション**|**サポートが終了した日付**|
|:-----|:-----|
|ProClarity Analytics Server 6.3 Service Pack 3  <br/> ProClarity Desktop Professional 6.3  <br/> ProClarity SharePoint ビューアー 6.3  <br/> |2017 年 7 月 11 日  <br/> |
|SharePoint Server 2007 Service Pack 3  <br/> |2017 年 10 月 10 日  <br/> |
|PerformancePoint Server 2007 Service Pack 3  <br/> |2018 年 1 月 9 日  <br/> |
   
詳細については [、「2007 年](upgrade-from-office-2007-servers-and-products.md)のサーバーとクライアントからのアップグレードに役立Officeリソース」を参照してください。
  
## <a name="what-does-end-of-support-mean"></a>サポート終了 *とはどういう意味* ですか?

ほとんどの Microsoft 製品と同様に、PerformancePoint Server 2007 SP3、ProClarity ソフトウェア、および SharePoint Server 2007 SP3 にはサポート ライフサイクルがあります。その間、Microsoft は新機能、バグ修正、およびセキュリティ更新プログラムを提供します。 製品のライフサイクルは、通常、製品の最初のリリースから 10 年間続く。 そのライフサイクルの終了は、製品のサポートの終了と呼ばれる。 ProClarity、PerformancePoint Server、および SharePoint Server 2007 がサポートの終了に達すると、Microsoft は次の機能を提供しなくなりました。
  
- 発生する可能性のある問題に対するテクニカル サポート。
    
- 検出され、サーバーの安定性と使いやすさに影響を与える可能性がある問題のバグ修正。
    
- 検出され、サーバーまたはアプリケーションがセキュリティ侵害に対して脆弱になる可能性がある脆弱性に対するセキュリティ修正。
    
- タイム ゾーンの更新。
    
ProClarity、SharePoint Server 2007 SP3、および PerformancePoint Server 2007 SP3 のインストールは、サポートが終了した場合でも引き続き実行されます。 ただし、できるだけ早くこれらのアプリケーションから移行することを強く推奨します。
  
## <a name="what-are-my-options"></a>使用できるオプション

2007 以降、Microsoft BI アプリケーションには多くの変更が加え、次の表に示すいくつかのオプションを検討する必要があります。
  
|**この ... を使用していた場合。**|**これらのオプションについて説明します。.**|**そして、これを念頭に置いて...**|
|:-----|:-----|:-----|
| PerformancePoint Server 2007 Monitoring Analytics 機能( &amp; 以下を含む)<br/>- PerformancePoint 監視サーバー <br/>- PerformancePoint ダッシュボード デザイナー<br/>- ダッシュボード ビューアー (SharePoint Services (PerformancePoint ダッシュボード、スコアカード、レポートのレンダリングに使用)<br/> |**ブラウザー (クラウドまたは** オンプレミス) で Excel を使用する Excel。 概要については [、「Excel および Microsoft 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx)の BI 機能」を参照してください。<br/><br/> **Power BI** (クラウドまたはオンプレミス)。 概要については [、「Power BI とは」を参照してください。](https://go.microsoft.com/fwlink/?linkid=841341) <br/><br/> **SQL Serverレポート サービス** (オンプレミス)。 概要については、「レポート サービス [(SSRS) SQL Server: モバイル](/sql/reporting-services/create-deploy-and-manage-mobile-and-paginated-reports)レポートとページ分割されたレポートを作成、展開、および管理する」を参照してください。 <br/><br/> **PerformancePoint Services** (オンプレミス)。 概要については [、「What's new for PerformancePoint Services (SharePoint Server 2010)」を参照してください](/previous-versions/office/sharepoint-server-2010/ee661741(v=office.14))。 <br/> |Excel は、オンライン (クラウドベース) またはオンプレミス のソリューションとして利用できます。 多くのレポートとダッシュボードのニーズを Excel で満たすことができます。  <br/><br/> Power BI は、オンラインまたはオンプレミスのソリューションとして利用できます。 Power BI は Microsoft 365 には含まれていません。 ただし、無料で Power BI の使用を開始できます。 後で、データ使用量とビジネス ニーズに応じて、Microsoft 365 E5 を使用して Power BI Pro にアップグレードできます。<br/> <br/> Reporting Services と PerformancePoint Servicesは、両方ともオンプレミス ソリューションです。 <br/><br/> PerformancePoint Services SharePoint Server 2010、SharePoint Server 2013、および SharePoint Server 2016 で使用できます。 <br/> <br/> 2007 年から 2007 年PerformancePoint Server使用できる一部の機能とレポートの種類は、Excel、Power BI、Reporting Services、またはレポート サービスPerformancePoint Services。 利用可能な機能を確認して、ビジネス ニーズに最適なソリューションを判断します。 <br/> |
| ProClarity ソフトウェア:<br/>- ProClarity デスクトップ プロフェッショナル<br/> - ProClarity Analytics Server<br/>- ProClarity SharePoint ビューアー<br/> |**Microsoft パートナーと一緒に** 、ニーズに最適なソリューションを特定します。 Microsoft パートナー [センターにアクセスします](https://go.microsoft.com/fwlink/?linkid=841249)。 <br/><br/> ブラウザー、Power BI、レポート サービス、またはレポート サービスで Excel を使用SQL Server検討PerformancePoint Services。  <br/> |ProClarity ソフトウェアの一部の機能は、Excel、Power BI、Reporting Services、およびレポート サービスなど、他の Microsoft 製品PerformancePoint Services。  <br/> |
|SharePoint Server 2007 KPI (MOSS KPI とも呼ばれる)  <br/> |**Excel と Excel Services**。 概要については、「Excel and [Excel Services (SharePoint Server 2013)](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx)のビジネス インテリジェンス」を参照してください。 <br/> |SharePoint Server 2007 を使用して作成された MOSS KPI は、SharePoint Server 2010、SharePoint Server 2013、および SharePoint Server 2016 で使用できます。 ただし、新しい MOSS KPI は作成できない。  <br/> |
|Excel 2007  <br/> |**Excel** (クラウドまたはオンプレミス)。 概要については、「Excel および [365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx)の BI 機能Office参照してください。 <br/><br/> **Power BI** (クラウドまたはオンプレミス)。 概要については [、「Power BI とは」を参照してください。](https://go.microsoft.com/fwlink/?linkid=841341) <br/> |Excel と Power BI の両方で、さまざまなデータ ソースをサポートして、組織のクラウドベースとオンプレミスのソリューションを提供します。  <br/> |
   
### <a name="help-selecting-a-solution"></a>ソリューションの選択に関するヘルプ

利用可能な BI の選択肢が非常に多い場合、最適なオプションを決定するには圧倒的に思えるかもしれません。 オンライン ガイドをご利用いただけます。 分析 [とレポート作成については、「Microsoft Business Intelligence (BI) ツールの選択」を参照してください](/sql/reporting-services/choosing-microsoft-business-intelligence-bi-tools-for-analysis-and-reporting)。
  
### <a name="what-if-i-dont-upgrade-now"></a>今すぐアップグレードしない場合は?

すぐにアップグレードしない選択が可能です。 既存のサーバーとアプリケーションは引き続き実行されます。 ただし、サポートが終了した後、セキュリティ更新プログラムを含むそれ以上の更新プログラムは受け取らない。 サーバー アプリケーションに問題がある場合は、Microsoft テクニカル サポートからヘルプを受け取る必要があります。
  
## <a name="how-do-i-plan-my-upgrade"></a>アップグレードを計画する方法

アップグレード オプションを確認した後、次にアップグレード 計画を準備します。 以下のセクションには、情報と役立つその他のリソースが含まれます。 クラウドまたはオンプレミスの両方で動作する 2 つのオプションと、オンプレミス専用の 2 つを含む 4 つの主なオプションがあります。
  
|**オプション**|**クラウドまたはオンプレミスの場合**|
|:-----|:-----|
|[Excel with SharePoint Server (オンプレミス)](#excel-with-sharepoint-server-on-premises) <br/> |Both/フォーム/データシート  <br/> |
|[Power BI](#use-power-bi-in-the-cloud-or-on-premises)<br/> |Both/フォーム/データシート  <br/> |
|[レポート サービス](#use-reporting-services-on-premises) <br/> |オンプレミスのみ  <br/> |
|[PerformancePoint Services](#use-performancepoint-services-on-premises) <br/> |オンプレミスのみ  <br/> |
   
### <a name="use-excel-in-the-cloud-or-on-premises"></a>Excel を使用する (クラウドまたはオンプレミス)

SharePoint Server の Excel Servicesとも呼ばれる Excel を使用すると、Excel がコンピューターにインストールされていない場合でも、ブラウザー ウィンドウでブックを表示および使用できます。 Excel を使用してレポート、スコアカード、ダッシュボードを作成できます。 次に、Microsoft 365 または SharePoint Server オンプレミスの一部として SharePoint Online を使用しているかに関係ない、ブラウザーで Excel を使用できる他のユーザーとブックを共有します。 オンプレミスまたはクラウドに保存されたデータを使用すると、さまざまなデータ ソースを使用できます。
  
次の表は、Excel と Microsoft 365 を使用して Excel を SharePoint Server で使用する主な利点を比較しています。 詳細については、次の情報を参照してください。
  
|**Excel with Microsoft 365 (クラウド内)**|**Excel with SharePoint Server (オンプレミス)**|
|:-----|:-----|
|**Excel の最新の最大バージョンを取得します**。 Microsoft 365 では、強力な新しいグラフの種類、グラフとテーブルをすばやく簡単に作成する機能、より多くのデータ ソースのサポートを含む最新バージョンの Excel を取得できます。 <br/> <br/> **セットアップははるかに簡単です**。 Excel はビジネス向け Microsoft 365 に含まれているので、重い持ち上げはありません。 サインアップしてサインインすると、オンプレミス サーバーをアップグレードする場合よりも高速かつ効率的に起動して実行できるようになります。 <br/> <br/> **ユーザーは、どこでも自分のブックにアクセスできます**。 ユーザーは、コンピューター、スマートフォン、タブレットを使用して、どこにいてもブックを安全に表示できます。 <br/> <br/> **他にもまだあります！** Excel [および 365 の BI 機能Office参照してください](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx)。 <br/> |**グローバル設定を管理します**。 SharePoint 管理者は、セキュリティ、負荷分散、セッション管理、ブックキャッシュ、外部データ接続などのグローバル設定を指定できます。 <br/> <br/> **このファイルは、Excel ServicesとPerformancePoint Servicesできます**。 SharePoint Server のインストールExcel Services、PerformancePoint Servicesレポートを構成し、PerformancePoint ダッシュボードにExcel Servicesレポートを含めさせることができます。 <br/> <br/> **他にもまだあります！** 「Excel [and Excel Services (SharePoint Server 2013)のビジネス インテリジェンス」を参照してください](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx)。 <br/> |
   
#### <a name="excel-with-microsoft-365-in-the-cloud"></a>Excel with Microsoft 365 (クラウド内)

Microsoft 365 に移行すると、Excel 2016 を含む最新のサービスとアプリケーションが提供されます。 PerformancePoint Services Microsoft 365 では使用できないので、PerformancePoint ダッシュボードのコンテンツを Excel ブックまたは他のレポートに置き換えます。 良いニュースは、Excel 2016 には新しいグラフの種類が多数含め、Excel で印象的なダッシュボードを作成する方がこれまで以上に簡単です。 また、新しい機能は定期的に追加されます。 詳細については [、「What's New in Excel 2016 for Windows」を参照してください](https://support.office.com/article/5fdb9208-ff33-45b6-9e08-1f5cdb3a6c73.aspx)。
  
また、50 シート以上の Microsoft 365 を購入した場合は、Microsoft FastTrack チームがセットアップを支援できます。 詳細については [、「FastTrack」を参照してください](https://www.microsoft.com/fasttrack/microsoft-365)。
  
#### <a name="excel-with-sharepoint-server-on-premises"></a>Excel with SharePoint Server (オンプレミス)

SharePoint の新しいバージョンにアップグレードする場合は、次のように、Excel を Excel Servicesまたはブラウザーで使用できます。
  
- SharePoint Server 2010 の Excel Services
    
- SharePoint Server 2013 の Excel Services
    
- SharePoint Server 2016 とは別にOfficeオンライン サーバーの一部である Excel
    
新しいバージョンPerformancePoint Services SharePoint Server でも構成し、Excel と共に使用できます。
  
SharePoint アップグレード オプションの詳細については [、「SharePoint Server 2007 End of support Roadmap」を参照してください](sharepoint-2007-end-of-support.md)。
  
詳細については、「Excel Services概要 [(SharePoint Server 2010 Excel Services」を参照してください](/previous-versions/office/sharepoint-server-2010/ee424405(v=office.14))。
  
### <a name="use-power-bi-in-the-cloud-or-on-premises"></a>Power BI を使用する (クラウドまたはオンプレミス)

Power BI は、データを分析し、分析情報を共有するためのビジネス分析ツールのスイートです。 Power BI を使用すると、オンプレミスまたはオンラインのデータ ソースを使用して対話型のレポートとダッシュボードを作成できます。 ユーザーは、自分のコンピューターまたはモバイル デバイスでレポートとダッシュボードを表示および使用できます。
  
Power BI は Microsoft 365 または SharePoint Server の一部ではない。 これは、Power BI Desktop、Power BI ゲートウェイ、および Power BI サービスを含む個別の製品です。 Power BI は SharePoint Online にも統合されます。 Power BI の使用を無料で開始できます。 データ使用量とビジネス ニーズに基づいて、後で Microsoft 365 E5 を使用して Power BI Pro にアップグレードできます。 詳細については [、「Power BI とは」を参照してください。](https://go.microsoft.com/fwlink/?linkid=841341)
  
### <a name="use-reporting-services-on-premises"></a>レポート サービスの使用 (オンプレミス)

SQL Serverレポート サービスは、堅牢なレポート ソリューションを提供します。 Reporting Services は、ネイティブ モードまたは SharePoint 統合モードで構成できます。 レポート デザイナー、レポート ビルダー、レポート ビルダーなど、さまざまなツールを使用してレポートを作成Power View。 モバイル レポートの最新リリースSQL Server、モバイル レポート発行元SQL Serverを使用して、任意の画面サイズに合ったレポートを配信することもできます。 これにより、閲覧者はモバイル デバイスでレポートを使用できます。 詳細については、「レポート サービス [(SSRS) SQL Server: モバイル](/sql/reporting-services/create-deploy-and-manage-mobile-and-paginated-reports)レポートとページ分割されたレポートを作成、展開、および管理する」を参照してください。
  
### <a name="use-performancepoint-services-on-premises"></a>[PerformancePoint Servicesを使用する (オンプレミス)

PerformancePoint Server 2007 は SharePoint Server 2007 とは別に販売されました。 SharePoint Server 2010 より、PerformancePoint Services SharePoint Server のサービス アプリケーションです。 そのため、別のサーバー ライセンスまたはハードウェアを購入して、サーバー ライセンスを使用する必要PerformancePoint Services。
  
2007 PerformancePoint Serverから 2007 PerformancePoint Servicesに移動するには、より新しいバージョンの SharePoint Server に移動し、サーバーを構成PerformancePoint Services。 移動する SharePoint Server のバージョンは、既存のダッシュボード コンテンツを 2007 年から 2007 年PerformancePoint ServerにインポートできるかどうかをPerformancePoint Services。
  
- SharePoint Server 2010 にアップグレードする場合は、PerformancePoint ダッシュボード コンテンツを PerformancePoint Server 2007 から SharePoint Server 2010 PerformancePoint Services にインポートできます。 詳細については、「Import [Wizard: PerformancePoint Server 2007 コンテンツから SharePoint Server 2010」を参照してください](/previous-versions/office/sharepoint-server-2010/ee681485(v=office.14))。
    
- SharePoint Server 2013 または SharePoint Server 2016 に移動する場合は、新しいダッシュボード コンテンツ (データ ソース、レポート、スコアカード、ダッシュボード ページ) を作成する必要があります。
    
アップグレード計画の開始PerformancePoint Services、次のリソースを参照してください。
  
- [SharePoint Server 2007 のサポート終了ロードマップ](sharepoint-2007-end-of-support.md)
    
- 移行する SharePoint のバージョンがわかっている場合は、次の記事を参照PerformancePoint Services。
    
  - [プラン PerformancePoint Services (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/ee681486(v=office.14))
    
  - [PerformancePoint Services SharePoint Server 2013 の概要](/sharepoint/administration/performancepoint-services-overview)
    
  - [SharePoint Server 2016 の PerformancePoint Services の概要](/sharepoint/administration/performancepoint-services-overview)
    
この機能にアップグレードPerformancePoint Services、いくつかの新機能と拡張機能が提供されます。 PerformancePoint Servicesスコアカードを提供しています。分解ツリーや KPI 詳細レポートなどの新しい視覚化。グラフの種類が多い。より優れたタイム インテリジェンス フィルター機能。アクセシビリティコンプライアンスの強化。 詳細については [、「What's new for PerformancePoint Services (SharePoint Server 2010)」を参照してください](/previous-versions/office/sharepoint-server-2010/ee661741(v=office.14))。
  
## <a name="where-can-i-get-help-with-my-upgrade"></a>アップグレードに関するヘルプはどこで受け取れるのですか?

オンプレミスにアップグレードする場合も、Microsoft 365 に移行する場合も、Microsoft パートナーと一緒に作業することをお勧めします。 認定パートナーは、ビジネス ニーズに最適なソリューションを特定し、展開に役立ちます。 Microsoft パートナー [センターにアクセスし](https://go.microsoft.com/fwlink/?linkid=841249)、検索フィルターを使用してソリューション プロバイダーを検索します。
  
## <a name="related-topics"></a>関連項目

[Office 2007 のサーバーとクライアントからのアップグレードに役立つリソース](upgrade-from-office-2007-servers-and-products.md)