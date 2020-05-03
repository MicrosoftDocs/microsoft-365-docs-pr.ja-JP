---
title: 個人情報の漏えいを監視する
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 02/07/2018
audience: ITPro
ms.topic: overview
ms.collection:
- Strat_O365_Enterprise
- Ent_O365
- GDPR
- M365-security-compliance
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
description: 個人データの漏えいの監視に使用できる 3 つのツールについて説明します。
ms.openlocfilehash: 9bc56d1de153f1357064d2b3ddada0d0533bc3cf
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "43635162"
---
# <a name="monitor-for-leaks-of-personal-data"></a>個人情報の漏えいを監視する

個人データの使用と転送を監視するために使用できるツールは数多くあります。このトピックでは、効果的な 3 つのツールについて説明します。

![個人データの使用と転送を監視するためのツール](../../media/Monitor-for-leaks-of-personal-data-image1.png)

この図について:

- まず、SharePoint Online、OneDrive for Business、転送中の電子メールの個人データを監視するための Microsoft 365 データ損失防止レポートから開始します。このレポートは、個人データを監視するための最も詳細なレベルの内容を提供します。ただし、このレポートには Office 365 のすべてのサービスが含まれているわけではありません。

- 次に、アラート ポリシーと監査ログを使用して、サービス全体のアクティビティを監視します。進行中の監視を設定するか、または監査ログを検索してインシデントを調査します。監査ログは、Sway、PowerBI、電子情報開示、Dynamics 365、Microsoft Flow、Microsoft Teams、管理アクティビティ、OneDrive for Business、SharePoint Online、転送中のメール、保存メールボックスなどのサービス全体で機能します。Skype の会話は保存メールボックスに含まれます。

- 最後に、Microsoft Cloud App Security を使用して、他の SaaS プロバイダーの機密データを含むファイルを監視します。機密情報タイプと統合ラベルを Azure Information Protection と Cloud App Security が有効な Office で使用できる機能が近日公開予定です。すべての SaaS アプリまたは特定のアプリ (ボックスなど) に適用するポリシーを設定できます。Cloud App Security では、電子メールに添付されたファイルを含め、Exchange Online のファイルは検出されません。

## <a name="data-loss-prevention-reports"></a>データ損失防止レポート

データ損失防止 (DLP) ポリシーを作成したら、意図したとおりに動作し、コンプライアンスの遵守に役立っているか確認します。Office 365 の DLP レポートを使用すると、DLP ポリシーの一致項目、上書き、誤検知の数をすぐに確認したり、時間の経過とともに増加または減少する傾向があるかどうかを見極めたりできます。また、さまざまな方法でレポートをフィルター処理したり、グラフ上の系列の特定のポイントを選択して詳細情報を表示したりできます。

DLP レポートを使用すると、以下のことを行えます。

- 特定の期間に絞り込み、スパイクや傾向の理由を理解します。

- 組織の DLP ポリシーに違反するビジネス プロセスを検出します。

- DLP ポリシーのビジネスに及ぼす影響を理解します。

- ユーザーがポリシーを上書きしたり、誤検知を報告したりしてポリシーのヒントを解決するときに送信する正当な理由を表示します。

- 特定の DLP ポリシーに関する一致箇所を表示することによって、そのポリシーのコンプライアンス遵守を確認します。

- 詳細ウィンドウで、DLP ポリシーに一致する機密データを含むファイルの一覧を表示します。

さらに、テスト モードで実行するときに、DLP レポートを使用して DLP ポリシーを微調整することができます。

DLP レポートは、セキュリティ/コンプライアンス センターにあります。 [レポート] \> [レポートの表示] に移動します。 [データ損失防止 (DLP)] の下で、[DLP ポリシーおよびルールの一致] または [DLP の誤検知と上書き] に移動します。

詳細については、「[データ損失防止のレポートの表示](https://docs.microsoft.com/microsoft-365/compliance/view-the-dlp-reports)」を参照してください。

![DLP ポリシーと一致することを示すレポート](../../media/Monitor-for-leaks-of-personal-data-image2.png)

## <a name="audit-log-and-alert-policies"></a>監査ログおよびアラートのポリシー

監査ログには、Exchange Online、SharePoint Online、OneDrive for Business、Azure Active Directory、Microsoft Teams、Power BI、Sway などの サービスからのイベントが含まれます。

セキュリティ/コンプライアンス センターでは、監査ログを監視およびレポートする 2 つの方法を提供しています。

- アラート ポリシーの設定、アラートの表示、トレンドの監視には、セキュリティ センターまたはコンプライアンス センターのいずれかにあるアラート ポリシーとアラート ダッシュボード ツールを使用します。

- 監査ログを直接検索するには、指定した日付の範囲ですべてのイベントを検索します。また、操作を実行したユーザー、操作、または対象オブジェクトなど、特定の条件に基づいて結果をフィルター処理することもできます。

情報セキュリティおよびコンプライアンス チームは、これらのツールを使用して、エンド ユーザーと管理者の両方がサービスで実行したアクティビティを予防的に確認することができます。特定のアクティビティが特定のサイト コレクションで発生した場合に (たとえば、GDPR 関連情報が含まれていることがわかっているサイトからコンテンツを共有する場合など)、電子メール通知を送信するように自動アラートを設定できます。これによってチームは、ユーザーをフォローアップして、企業のセキュリティ ポリシー遵守の徹底、追加のトレーニング提供などを行うことができます。

情報セキュリティ チームは、監査ログを検索して疑いのあるデータ侵害を調査し、根本原因と違反の程度の両方を判断することもできます。この組み込み機能は、GDPR の第 33 条および第 34 条の遵守を円滑にします。これらの条項では、データ違反について GDPR 監督当局およびデータ主体に、特定期間内に通知することが要求されています。監査ログ エントリは、サービス内で 90 日間のみ保持されます。多くの場合、これらのログをより長期間保持することが推奨され、多くの企業もそれを必要としていました。

Microsoft 管理アクティビティ API を使用して統一監査ログを購読し、必要に応じてログ エントリを保存し、高度なダッシュボードとアラートを提供することができるソリューションを活用できます。たとえば、[Microsoft Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/oms-solution-office-365) などです。

アラート ポリシーと監査ログの検索については、以下を参照してください。

- [Microsoft 365 セキュリティ/コンプライアンス センターのアラート ポリシー](https://docs.microsoft.com/microsoft-365/compliance/alert-policies)

- [Office 365 で監査ログを検索してユーザーと管理者のアクティビティを確認する](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log) (概要)

- [監査ログ検索を有効または無効にする](https://docs.microsoft.com/microsoft-365/compliance/turn-audit-log-search-on-or-off)

- [監査ログを検索する](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance)

- [Search-UnifiedAuditLog](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog) (コマンドレット)

- [監査ログの詳細なプロパティ](https://docs.microsoft.com/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log)

## <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security

Microsoft Cloud App Security は、ネットワーク上で使用されている他の SaaS アプリや、これらのアプリとの間でやり取りされる機密データを検出するのに役立ちます。

Microsoft Cloud App Security は、クラウド アプリのための詳細な可視化、きめ細かいコントロール、高度な脅威の防止を提供する包括的なサービスです。ネットワーク上のすべてのデバイスから 15,000 以上のクラウド アプリケーションを識別し、リスク スコアリングや継続的なリスク評価と分析を提供します。ファイアウォールやプロキシから情報を収集して、クラウドの使用状況とシャドー IT に関する完全な可視性とコンテキストを提供するため、仲介は不要です。

クラウド環境をよりよく理解するために、Cloud App Security の調査機能は、承認および管理されているアプリのすべてのアクティビティ、ファイル、アカウントの詳細内容を可視化します。ファイル レベルの詳細な情報を取得し、クラウド アプリでのデータの移動を把握できます。

たとえば、次の図は GDPR に役立つ 2 つのクラウド アプリケーション セキュリティ ポリシーを示しています。

![クラウド アプリケーション セキュリティ ポリシーの例](../../media/Monitor-for-leaks-of-personal-data-image3.png)

1 番目のポリシーは、選択した事前定義の PII 属性またはカスタム式を持つファイルが、選択した SaaS アプリから組織外で共有されると警告します。

2 番目のポリシーは、管理対象外のデバイスへのファイル ダウンロードをブロックします。検索するファイル内の属性と、ポリシーを適用する SaaS アプリを選択します。

これらの属性タイプは、Cloud App Security に近日公開されます。

- 機密情報の種類

- Microsoft 365 および Azure Information Protection での統一ラベル

### <a name="cloud-app-security-dashboard"></a>Cloud App Security ダッシュボード

まだ Cloud App Security の使用を開始していない場合は、まず開始してください。Cloud App Security には <https://portal.cloudappsecurity.com> からアクセスできます。

注: Cloud App Security の使用を開始するときやラベルを割り当てる前に、[一般設定] の [Azure Information Protection 分類ラベルについてファイルを自動的にスキャンする] を有効にしてください。設定後は、Cloud App Security は、変更されるまで既存ファイルを再スキャンしません。

![アラートに関する情報を表示するダッシュボード](../../media/Monitor-for-leaks-of-personal-data-image4.png)

詳しくは、以下の資料を参照してください。

- [Cloud App Security を展開する](https://docs.microsoft.com/cloud-app-security/getting-started-with-cloud-app-security)

- [Microsoft Cloud App Security の詳細情報](https://www.microsoft.com/cloud-platform/cloud-app-security)

- [Microsoft Cloud App Security プロキシを使用して機密情報のダウンロードをブロックする](https://docs.microsoft.com/cloud-app-security/use-case-proxy-block-session-aad)

## <a name="example-file-and-activity-policies-to-detect-sharing-of-personal-data"></a>個人データの共有を検出するためのファイル ポリシーとアクティビティ ポリシーの例

### <a name="detect-sharing-of-files-containing-pii--credit-card-number"></a>PII (クレジット カード番号) を含むファイルの共有を検出する

承認されたクラウド アプリから、クレジット カード番号を含むファイルが共有されたときに警告します。

<table>
<thead>
<tr class="header">
<th align="left"><strong>コントロール</strong></th>
<th align="left"><strong>設定</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">ポリシーの種類</td>
<td align="left">ファイル ポリシー</td>
</tr>
<tr class="even">
<td align="left">ポリシー テンプレート</td>
<td align="left">テンプレートなし</td>
</tr>
<tr class="odd">
<td align="left">ポリシーの重要度</td>
<td align="left">高</td>
</tr>
<tr class="even">
<td align="left">カテゴリ</td>
<td align="left">DLP</td>
</tr>
<tr class="odd">
<td align="left">フィルター設定</td>
<td align="left"><p>Access level = Public (Internet), Public, External</p>
<p>App = &lt;select apps&gt; (特定の SaaS アプリに監視を制限する場合は、この設定を使用します)</p></td>
</tr>
<tr class="even">
<td align="left">適用先</td>
<td align="left">すべてのファイル、すべての所有者</td>
</tr>
<tr class="odd">
<td align="left">内容の検査</td>
<td align="left"><p>現在の式に一致するファイルを含む: All countries: Finance: Credit card number</p>
<p>関連するコンテキストを必要としない: オフ (これはキーワードと正規表現に一致します)</p>
<p>1 つでも一致するファイルを含む</p>
<p>違反の最後の 4 文字をマスク解除する: オン</p></td>
</tr>
<tr class="even">
<td align="left">アラート</td>
<td align="left"><p>一致するファイルごとにアラートを作成する: オン</p>
<p>1 日のアラート制限: 1000</p>
<p>電子メールとしてアラートを選択する: オン</p>
<p>宛先: infosec@contoso.com</p></td>
</tr>
<tr class="odd">
<td align="left">ガバナンス</td>
<td align="left"><p>Microsoft OneDrive for Business</p>
<p>非公開にする: 外部ユーザーの削除をオン</p>
<p>その他のすべての設定: オフ</p>
<p>Microsoft SharePoint Online</p>
<p>非公開にする: 外部ユーザーの削除をオン</p>
<p>その他のすべての設定: オフ</p></td>
</tr>
</tbody>
</table>

類似のポリシー:

- PII (メール アドレス) を含むファイルの共有を検出する

- PII (パスポート番号) を含むファイルの共有を検出する

### <a name="detect-customer-or-hr-data-in-box-or-onedrive-for-business"></a>Box for Business または OneDrive for Business の顧客データや人事データを検出する

OneDrive for Business または Box for Business に Customer Data (顧客データ) または HR Data (人事データ) という名前のファイルがアップロードされたときに警告します。

注:

- Box の監視では、API Connector SDK を使用してコネクタを設定する必要があります。

- このポリシーには、現在プライベート プレビューになっている機能が必要です。

<table>
<thead>
<tr class="header">
<th align="left"><strong>コントロール</strong></th>
<th align="left"><strong>設定</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">ポリシーの種類</td>
<td align="left">アクティビティ ポリシー</td>
</tr>
<tr class="even">
<td align="left">ポリシー テンプレート</td>
<td align="left">テンプレートなし</td>
</tr>
<tr class="odd">
<td align="left">ポリシーの重要度</td>
<td align="left">高</td>
</tr>
<tr class="even">
<td align="left">カテゴリ</td>
<td align="left">制御を共有</td>
</tr>
<tr class="odd">
<td align="left">操作対象</td>
<td align="left">1 つのアクティビティ</td>
</tr>
<tr class="even">
<td align="left">フィルター設定</td>
<td align="left"><p>アクティビティの種類 = ファイルのアップロード</p>
<p>アプリ = Microsoft OneDrive for Business および Box</p>
<p>分類ラベル (現在はプライベート プレビュー): Azure Information Protection = 顧客データ、人事—給与データ、人事—従業員データ</p></td>
</tr>
<tr class="odd">
<td align="left">アラート</td>
<td align="left"><p>アラートを作成する: オン</p>
<p>1 日のアラート制限: 1000</p>
<p>電子メールとしてアラートを選択する: オン</p>
<p>宛先: infosec@contoso.com</p></td>
</tr>
<tr class="even">
<td align="left">ガバナンス</td>
<td align="left"><p>すべてのアプリ</p>
<p>ユーザーを検疫に入れる: オン</p>
<p>その他のすべての設定: オフ</p>
<p>Office 365</p>
<p>ユーザーを検疫に入れる: オン</p>
<p>その他のすべての設定: オフ</p></td>
</tr>
</tbody>
</table>

類似のポリシー:

- 顧客データや人事データの大量ダウンロードを検出する — 顧客データや人事データを含む多数のファイルが、単一ユーザーによって短時間にダウンロードされたことが検出されたときに警告します。

- 顧客および人事データの共有を検出する — 顧客または人事データを含むファイルが共有されたときに警告します。
