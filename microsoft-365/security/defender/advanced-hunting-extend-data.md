---
title: 適切な設定で高度な狩猟範囲を拡張する
description: 高度な検索で最も包括的なデータを取得するために、Windows デバイスや他の設定の監査設定を確認する
keywords: 高度なハンティング、インシデント、ピボット、エンティティ、監査設定、ユーザー アカウント管理、セキュリティ グループ管理、脅威の検出、サイバー脅威の検出、検索、クエリ、テレメトリ、Microsoft 365、Microsoft Threat Protection
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: eaa0068fe52119bfd9dc2381b253b259cb8df907
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51062084"
---
# <a name="extend-advanced-hunting-coverage-with-the-right-settings"></a>適切な設定で高度な狩猟範囲を拡張する

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**適用対象:**
- Microsoft 365 Defender

[高度な検索](advanced-hunting-overview.md) は、デバイス、Office 365 ワークスペース、Azure AD、Microsoft Defender for Identity など、さまざまなソースからのデータに依存します。 可能な限り包括的なデータを取得するには、対応するデータ ソースに正しい設定が含されていることを確認します。

## <a name="advanced-security-auditing-on-windows-devices"></a>Windows デバイスでの高度なセキュリティ監査
これらの高度な監査設定をオンにし、ローカル アカウント管理、ローカル セキュリティ グループ管理、サービスの作成など、デバイス上のアクティビティに関するデータを取得します。

| データ | 説明 | スキーマ テーブル | 構成する方法 |
| --- | --- | --- | --- |
| アカウント管理 | ローカル アカウントの作成、削除、その他のアカウント関連のアクティビティを示すさまざまな値 `ActionType` としてキャプチャされるイベント | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - 高度なセキュリティ監査ポリシーの展開: [ユーザー アカウント管理の監査](/windows/security/threat-protection/auditing/audit-user-account-management)<br> - [高度なセキュリティ監査ポリシーの詳細](/windows/security/threat-protection/auditing/advanced-security-auditing) |
| セキュリティ グループの管理 | ローカル セキュリティ グループの作成および他のローカル グループ管理アクティビティを示すさまざまな `ActionType` 値としてキャプチャされたイベント | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - 高度なセキュリティ監査ポリシーの展開: [セキュリティ グループ管理の監査](/windows/security/threat-protection/auditing/audit-security-group-management)<br> - [高度なセキュリティ監査ポリシーの詳細](/windows/security/threat-protection/auditing/advanced-security-auditing) |
| サービスのインストール | サービスが作成されたことを示 `ActionType` す値 `ServiceInstalled` でキャプチャされたイベント | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - 高度なセキュリティ監査ポリシーの展開: [セキュリティ システム拡張機能の監査](/windows/security/threat-protection/auditing/audit-security-system-extension)<br> - [高度なセキュリティ監査ポリシーの詳細](/windows/security/threat-protection/auditing/advanced-security-auditing) |

## <a name="microsoft-defender-for-identity-sensor-on-the-domain-controller"></a>ドメイン コントローラー上の Id センサー用 Microsoft Defender
オンプレミスで Active Directory を実行している場合は、Microsoft Defender for Identity のデータを取得するには、ドメイン コントローラーに Microsoft Defender for Identity センサーをインストールする必要があります。 インストールされ、適切に構成されている場合、このデータは、Microsoft Defender for Identity を介した高度な検索にもフィードされ、ネットワーク内の ID 情報とイベントの全体像を提供します。 また、このデータを使用すると、Microsoft Defender for Identity が高度な狩猟の対象となる関連するアラートを生成する機能も強化されます。 

| データ | 説明 | スキーマ テーブル | 構成する方法 |
| --- | --- | --- | --- |
| ドメイン コントローラ | Microsoft Defender for Identity に送信されるオンプレミスの Active Directory からのデータ、アカウントの詳細、ログオン アクティビティ、Active Directory クエリなどの ID 関連情報の強化 | [IdentityInfo、IdentityLogonEvents、IdentityQueryEvents](advanced-hunting-identitylogonevents-table.md)などの複数の[](advanced-hunting-identityinfo-table.md)[テーブル](advanced-hunting-identityqueryevents-table.md)  | - [Microsoft Defender for Identity センサーのインストール](/azure-advanced-threat-protection/install-atp-step4)<br>- [関連する Windows イベントを有効にする](/azure-advanced-threat-protection/configure-event-collection) |

## <a name="related-topics"></a>関連項目
- [高度な検出の概要](advanced-hunting-overview.md)
- [スキーマを理解する](advanced-hunting-schema-tables.md)