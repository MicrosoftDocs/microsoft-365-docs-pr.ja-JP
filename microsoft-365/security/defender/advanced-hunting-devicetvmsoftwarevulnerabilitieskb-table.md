---
title: 高度な捜索スキーマの DeviceTvmSoftwareVulnerabilitiesKB テーブル
description: 高度な捜索スキーマの DeviceTvmSoftwareVulnerabilitiesKB テーブルで、脅威と脆弱性の管理によって追跡されるソフトウェアの脆弱性について説明します。
keywords: 高度なハンティング、脅威の検出、サイバー脅威の検出、Microsoft 脅威保護、microsoft 365、mtp、m365、検索、クエリ、テレメトリ、スキーマ、リファレンス、kusto、table、column、data type、description、Threat & の脆弱性管理、TVM、デバイス管理、ソフトウェア、インベントリ、脆弱性、CVE ID、CVSS、DeviceTvmSoftwareVulnerabilitiesKBabilities
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
ms.openlocfilehash: a7042ac24822c8f4d866640e005ecd3176bb6409
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51062092"
---
# <a name="devicetvmsoftwarevulnerabilitieskb"></a>DeviceTvmSoftwareVulnerabilitiesKB

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**適用対象:**
- Microsoft 365 Defender



高度な捜索スキーマの `DeviceTvmSoftwareVulnerabilitiesKB` テーブルには、[脅威と脆弱性の管理](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)が評価するデバイスの脆弱性リストが含まれています。 このテーブルの情報を返すクエリを作成するには、このレファレンスを使用します。

高度な捜索スキーマのその他のテーブルの詳細については、「[高度な捜索のリファレンス](advanced-hunting-schema-tables.md)」 を参照してください。

| 列名 | データ型 | 説明 |
|-------------|-----------|-------------|
| `CveId` | string | 共通脆弱性識別子 (CVE) システムでセキュリティの脆弱性に割り当てられている一意の識別子  |
| `CvssScore` | 文字列型 | 共通脆弱性評価システム (CVSS) でセキュリティの脆弱性に割り当てられている重大度スコア |
| `IsExploitAvailable` | ブール型 | 脆弱性の悪用コードが公開されているかどうかを示す |
| `VulnerabilitySeverityLevel` | 文字列型 | CVSS スコアと脅威の度合いの影響を受ける動的要因に基づいて、セキュリティの脆弱性に割り当てられている重大度レベル |
| `LastModifiedTime` | 日付型 | アイテムまたは関連するメタデータが最後に変更された日付 |
| `PublishedDate` | 日付型 | 脆弱性が一般に公開された日付 |
| `VulnerabilityDescription` | 文字列型 | 脆弱性と関連するリスクの説明 |
| `AffectedSoftware` | 文字列型 | 脆弱性の影響を受けるすべてのソフトウェア製品の一覧 |

## <a name="related-topics"></a>関連項目

- [積極的に脅威を捜索する](advanced-hunting-overview.md)
- [クエリ言語の説明](advanced-hunting-query-language.md)
- [共有クエリを使用する](advanced-hunting-shared-queries.md)
- [デバイス、メール、アプリ、ID 全体で探す](advanced-hunting-query-emails-devices.md)
- [スキーマを理解する](advanced-hunting-schema-tables.md)
- [クエリのベスト プラクティスを適用する](advanced-hunting-best-practices.md)
- [脅威および脆弱性管理の概要](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)