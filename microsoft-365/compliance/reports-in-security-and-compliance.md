---
title: セキュリティ センターとコンプライアンス センターのレポート
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: overview
f1_keywords:
- ms.o365.cc.AuditingHelp
ms.service: O365-seccomp
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: 7acd33ce-1ec8-49fb-b625-43bac7b58c5a
description: セキュリティ コンプライアンス センター&使用して、SharePoint Online および Exchange Online 組織のさまざまなレポートと Azure Active Directory レポートを取得します。
ms.openlocfilehash: 3e72ecab68ece31c44d99f85806492e788f4cd7c
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "50926155"
---
# <a name="reports-in-the-security--compliance-center"></a>セキュリティ センターとコンプライアンス センターのレポート

セキュリティ コンプライアンス センターの **[レポート** の表示] ページを& SharePoint Online 組織および Exchange Online 組織の監査レポートにすばやくアクセスできます。 [レポートの表示] ページから、Azure Active Directory (AD) ユーザー サインイン レポート、ユーザー アクティビティ レポート、および Azure AD 監査ログに **アクセス** することもできます。 これは、有料の Microsoft 365 サブスクリプションに Microsoft Azure への無料サブスクリプションが含まれるためです。 これらの Azure レポートに初めてアクセスする場合は、1 回の登録プロセスを完了する必要があります。 
  
> [!TIP]
> 組織のアクティビティに関するその他のレポートを表示するには [、「Microsoft 365](../admin/activity-reports/activity-reports.md)管理センターのアクティビティ レポート」を参照してください。 
  
 **はじめに**
  
セキュリティ コンプライアンス センターでレポートを表示するには、次&必要です。
  
- Exchange 管理センター (EAC &) でセキュリティ リーダーの役割を割り当てる必要があります。 既定では、この役割は EAC の [組織の管理] および [セキュリティ リーダー] 役割グループに割り当てられます。
    
- セキュリティ View-Only コンプライアンス センターで DLP レポートを表示するには、セキュリティ & コンプライアンス センターで DLP コンプライアンス管理の役割&する必要があります。 既定では、この役割は、コンプライアンス 管理者、組織の管理、セキュリティ管理者、セキュリティ リーダーの各役割グループに割り当て&されます。

- さらに、EAC で DLP レポートを表示するには、EAC View-Only受信者の役割を割り当てる必要があります。 既定では、この役割は EAC のコンプライアンス管理、組織の管理View-Onlyグループに割り当てられます。
  
 **セキュリティ コンプライアンス センターで [レポートの表示] ページを&するには、次の&使用します。**
  
1. [https://protection.office.com/#/viewreports](https://protection.office.com/#/viewreports) に移動します。
    
2. 組織内のユーザー アカウントの資格情報を使用してサインインします。
    
[レポートの **表示] ページ** で、次の種類のレポートを表示できます。 
  
- [監査レポート](#auditing-reports)
- [監督レビュー レポート](#supervisory-review-report)
- [データ損失防止レポート](#data-loss-prevention-reports)
    
## <a name="auditing-reports"></a>監査レポート

次の表では、セキュリティ コンプライアンスセンターの [レポートの表示] ページの [監査&説明します。 
  
|**レポート**|**説明**|
|:-----|:-----|
|**監査ログ レポート** <br/> |監査ログで、組織内のユーザーと管理者のアクティビティを検索できます。 このレポートには、Exchange Online、SharePoint Online、OneDrive for Business、Azure Active Directory のエントリユーザーと管理者アクティビティが含まれます。これは、Office 365 のディレクトリ サービスです。 詳細については、「[Search the audit log in the Office 365 (Office 365 での監査ログの検索)](search-the-audit-log-in-security-and-compliance.md)」を参照してください。  <br/> |
|**Azure AD レポート** <br/> |組織内で異常または疑わしいサインイン アクティビティを探す場合は、Microsoft Azure でサインインレポートとアクティビティ レポートを使用できます。 Azure の監査ログでイベントをADすることもできます。 Azure でレポートを表示するには、[Azure レポートの表示] AD **クリックします**。 詳細については、以下を参照してください。 <br/><br/>[365 で無料の Azure Active Directory サブスクリプションOffice使用します](use-your-free-azure-ad-subscription-in-office-365.md)。 <br/> [アクセスレポートと利用状況レポートを表示します](/azure/active-directory/reports-monitoring/overview-reports)。  <br/> |
|**Exchange 監査レポート** <br/> | Microsoft 365 の監査機能を使用して、組織の管理者が Exchange Online 構成に加えた変更を追跡できます。 Microsoft データ センター管理者または委任された管理者によって Exchange Online 組織に加えた変更もログに記録されます。 Exchange Online では、管理者監査ログは既定で有効になっているので、有効にするには何もする必要はありません。 Exchange Online には、メールボックス所有者以外のユーザーによるメールボックスへのアクセスを追跡できるメールボックス監査ログも用意されています。 所有者以外のアクセスを追跡する各メールボックスでメールボックス監査ログを有効にする必要があります。  <br/>  管理者監査ログとメールボックス監査ログの両方で、監査ログ エントリを表示する監査レポートを実行することができます。 また、メールボックス監査ログおよび管理者監査ログをエクスポートし、24 時間以内にメールに添付された XML ファイル形式で受信することができます。 <br/><br/>監査ログのエクスポートについては、以下を参照してください。  <br/><br/> [メールボックス監査ログのエクスポート](/exchange/security-and-compliance/exchange-auditing-reports/export-mailbox-audit-logs) <br/> [データセンター管理者監査ログの表示とエクスポート](/exchange/security-and-compliance/exchange-auditing-reports/view-external-admin-audit-log) <br/> [役割グループの変更または管理者監査ログを検索する](/exchange/security-and-compliance/exchange-auditing-reports/search-role-group-changes) <br/>   [Exchange 監査レポート](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports)。  <br/> |
   
## <a name="supervisory-review-report"></a>監督レビュー レポート

監督レビュー レポートを使用すると、組織内のすべての監督レビュー ポリシーの状態を確認できます。 詳細については、「組織の [監督レビュー ポリシーを構成する」を参照してください](./communication-compliance-configure.md)。
  
## <a name="data-loss-prevention-reports"></a>データ損失防止レポート

データ損失防止 (DLP) レポートには、DLP ポリシーに関する情報が含まれており、コンテンツに適用されたルールには、組織内の機密データが含まれる。 DLP ポリシーおよび規則に基づいて実行した DLP 操作に関する情報を表示するようレポートを構成することもできます。 詳細については、「データ損失 [防止のためのレポートの表示」を参照してください](view-the-dlp-reports.md)。