---
title: DAP Microsoft 365のWindows PowerShellを管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: Syndication および クラウド ソリューション プロバイダー (CSP) パートナーが顧客テナントWindows PowerShell管理Microsoft 365する方法。
ms.openlocfilehash: 352a9a01414b94a1593de6a734151b687524fe7d
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "50909528"
---
# <a name="how-to-manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-partners"></a>委任されたアクセス許可Microsoft 365パートナー Windows PowerShellを管理する方法

*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*

委任アクセス許可 (DAP) パートナー とは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。 多くはネットワークまたは通信プロバイダーです。 サブスクリプションをMicrosoft 365サービスにバンドルします。 Microsoft 365 サブスクリプションを販売すると、顧客のテナンシーに対する管理 (AOBO) アクセス許可が自動的に付与され、それらのテナントを管理および報告できます。 これらのタスクは、管理センターで行Microsoft 365困難です。 PowerShell を使用すると、次のような管理Microsoft 365実行する方がずっと簡単です。
- すべての顧客の **TenantId とそのドメイン** を一覧表示する 
- 顧客テナントのすべてのユーザーと割り当てられたライセンスを識別する
> [!NOTE]
> 一部の管理タスクは PowerShell でのみ実行できます。

次の記事では、Syndication パートナーと CSP パートナーが PowerShell を使用して顧客テナンシーを管理する方法を示します。
  
- [委任Microsoft 365アクセス許可 (DAP) パートナー Windows PowerShellを使用してテナントを管理する](manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [委任アクセス許可 (DAP) パートナー用 Windows PowerShell でクライアント テナンシーにドメインを追加する](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [Exchange Online PowerShell への接続](/powershell/exchange/connect-to-exchange-online-powershell)
    
- [委任アクセス許可 (DAP) パートナー用 Windows PowerShell を使用して顧客のテナント レポート データを取得する](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
