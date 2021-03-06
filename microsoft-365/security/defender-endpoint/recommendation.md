---
title: 推奨メソッドとプロパティ
description: 最近使用した上位のアラートを取得します。
keywords: apis, graph api, supported apis, get, alerts, recent
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: bd7aa2af2c7500bbe02108bb8aa5dee452ff2998
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2021
ms.locfileid: "52771599"
---
# <a name="recommendation-resource-type"></a>おすすめリソースの種類

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

> Defender for Endpoint を体験してみませんか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>メソッド
メソッド |戻り値の型 |説明
:---|:---|:---
[すべての推奨事項を一覧表示する](get-all-recommendations.md) | おすすめコレクション | 組織に影響を与えるすべてのセキュリティ推奨事項の一覧を取得します。
[ID による推奨事項の取得](get-recommendation-by-id.md) | 推奨事項 | セキュリティの推奨事項を ID で取得します。
[おすすめソフトウェアを取得する](get-recommendation-software.md)| [ソフトウェア](software.md) | 特定のソフトウェアに関連するセキュリティ推奨事項を取得します。
[おすすめデバイスを取得する](get-recommendation-machines.md)|MachineRef コレクション | セキュリティ推奨事項に関連付けられているデバイスの一覧を取得します。
[推奨事項の脆弱性を取得する](get-recommendation-vulnerabilities.md) | [脆弱性の](vulnerability.md) コレクション | セキュリティ推奨事項に関連付けられている脆弱性の一覧を取得します。


## <a name="properties"></a>プロパティ
プロパティ |   種類   |   説明
:---|:---|:---
id | String | 推奨事項 ID
productName | 文字列型 (String) | 関連するソフトウェア名  
recommendationName | String | おすすめ名
弱点 | Long | 検出された脆弱性の数
ベンダー | String | 関連ベンダー名
recommendedVersion | String | 推奨バージョン
recommendationCategory | String | おすすめカテゴリ。 使用できる値は、"Accounts"、"Application"、"Network"、"OS"、"SecurityStack" です。
subCategory | String | おすすめサブカテゴリ
severityScore | Double | 組織の Microsoft Secure Score for Devices に対する構成の潜在的な影響 (1-10)
publicExploit | Boolean | パブリックエクスプロイトが利用可能 
activeAlert | Boolean | アクティブなアラートは、この推奨事項に関連付けられている
associatedThreats | String collection | 脅威分析レポートは、この推奨事項に関連付けられている
remediationType | String | 修復の種類。 指定できる値は、"ConfigurationChange"、"Update"、"Upgrade"、"Uninstall" です。
状態 | 列挙 | 推奨事項の例外の状態。 指定できる値は、"Active" と "Exception" です。
configScoreImpact | Double | デバイスの Microsoft Secure Score の影響
exposureImpacte | Double | 露出スコアの影響
totalMachineCount | Long | インストールされているデバイスの数
exposedMachinesCount | Long | 脆弱性にさらされるインストール済みデバイスの数
nonProductivityImpactedAssets | Long | 影響を受けないデバイスの数  
relatedComponent | String |  関連するソフトウェア コンポーネント
