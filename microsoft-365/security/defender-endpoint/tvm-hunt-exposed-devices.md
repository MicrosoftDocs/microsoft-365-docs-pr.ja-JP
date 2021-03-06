---
title: 露出したデバイスの追求
description: セキュリティ管理者脅威と脆弱性の管理 It 管理者、および SecOps の共同作業を支援する方法について学習します。
keywords: Microsoft Defender for Endpoint-tvm シナリオ、Microsoft Defender for Endpoint、tvm、tvm シナリオ、脅威& の脆弱性の暴露を減らし、脅威と脆弱性を軽減し、セキュリティ構成を改善し、デバイスの Microsoft Secure Score を増やし、デバイスの脅威 & の脆弱性を高める Microsoft Secure Score、Microsoft Secure Score for Devices、露出スコア、セキュリティコントロール
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a9a8ebcc89c3009cd93fbb42f2a74bbb9ffcc31b
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2021
ms.locfileid: "51934095"
---
# <a name="hunt-for-exposed-devices---threat-and-vulnerability-management"></a>公開されているデバイスのハント - 脅威と脆弱性の管理

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [脅威と脆弱性の管理](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="use-advanced-hunting-to-find-devices-with-vulnerabilities"></a>高度な検索を使用して脆弱性のあるデバイスを検索する

高度な捜索は、クエリ ベースの脅威の捜索ツールで、最大 30 日間のロー データを検索できます。 ネットワーク内のイベントを事前に検査して、脅威インジケーターとエンティティを特定できます。 データへの柔軟なアクセスにより、既知の脅威と潜在的な脅威の両方に対する拘束されていない検出が可能です。 [高度な狩猟の詳細](advanced-hunting-overview.md)

### <a name="schema-tables"></a>スキーマ テーブル

- [DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md) - デバイスにインストールされているソフトウェアのインベントリ (バージョン情報やサポート終了の状態を含む)。

- [DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md) - デバイスで見つかったソフトウェアの脆弱性と、各脆弱性に対処する利用可能なセキュリティ更新プログラムの一覧。

- [DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md) - 悪用コードが一般に公開されているかどうかを含む、一般に公開された脆弱性のナレッジ ベース。

- [DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md) - デバイス上のさまざまなセキュリティ構成の状態を示す、脆弱性の管理およびセキュリティ評価イベント。

- [DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md) - Threat & 脆弱性管理でデバイスを評価するために使用されるさまざまなセキュリティ構成のナレッジ ベース。さまざまな標準とベンチマークへのマッピングが含まれています

## <a name="check-which-devices-are-involved-in-high-severity-alerts"></a>重大度の高いアラートに関係するデバイスを確認する

1. [高度 **な検索] に** 移動するには、アプリの左側のナビゲーション ウィンドウMicrosoft Defender セキュリティ センター。

2. TVM 高度なハンティング スキーマまで下にスクロールして、列名を理解します。

3. 次のクエリを入力します。

```kusto
// Search for devices with High active alerts or Critical CVE public exploit
DeviceTvmSoftwareVulnerabilities
| join kind=inner(DeviceTvmSoftwareVulnerabilitiesKB) on CveId
| where IsExploitAvailable == 1 and CvssScore >= 7
| summarize NumOfVulnerabilities=dcount(CveId),
DeviceName=any(DeviceName) by DeviceId
| join kind =inner(DeviceAlertEvents) on DeviceId  
| summarize NumOfVulnerabilities=any(NumOfVulnerabilities),
DeviceName=any(DeviceName) by DeviceId, AlertId
| project DeviceName, NumOfVulnerabilities, AlertId  
| order by NumOfVulnerabilities desc
```

## <a name="related-topics"></a>関連項目

- [脅威と脆弱性の管理概要](next-gen-threat-and-vuln-mgt.md)
- [セキュリティ上の推奨事項](tvm-security-recommendation.md)
- [API](next-gen-threat-and-vuln-mgt.md#apis)
- [ユーザー ロールのデータ アクセス脅威と脆弱性の管理構成する](user-roles.md#create-roles-and-assign-the-role-to-an-azure-active-directory-group)
- [高度な追求の概要](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [すべての高度な検索テーブル](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference.md)
