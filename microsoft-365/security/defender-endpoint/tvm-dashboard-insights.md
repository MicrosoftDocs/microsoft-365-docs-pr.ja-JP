---
title: ダッシュボードの分析情報 - 脅威と脆弱性の管理
description: この脅威と脆弱性の管理は、SecOps とセキュリティ管理者がサイバーセキュリティの脅威に対処し、組織のセキュリティの回復力を構築するのに役立ちます。
keywords: Microsoft Defender for Endpoint-tvm, Microsoft Defender for Endpoint-tvm ダッシュボード, Threat & 脆弱性の管理, 脅威と脆弱性の管理, リスクベースの脅威 & 脆弱性の管理, セキュリティ構成, Microsoft Secure Score for Devices, exposure score
search.appverid: met150
search.product: eADQiWindows 10XVcnh
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 82b6123a99eb406918708c6bf23b870ef3bc3d79
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2021
ms.locfileid: "51934143"
---
# <a name="dashboard-insights---threat-and-vulnerability-management"></a>ダッシュボードの分析情報 - 脅威と脆弱性の管理

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [脅威と脆弱性の管理](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Defender for Endpoint を体験してみませんか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-portaloverview-abovefoldlink)

脅威と脆弱性の管理は Defender for Endpoint のコンポーネントであり、セキュリティ管理者とセキュリティ運用チームの両方に、次の固有の値を提供します。


- エンドポイントの脆弱性に関連したリアルタイムのエンドポイント検出と応答（EDR）の分析
- インシデント調査中の貴重なデバイスの脆弱性コンテキスト
- 組み込みの修復プロセスは、Microsoft IntuneとMicrosoft Endpoint Configuration Manager  
  
次のコマンドで[脅威と脆弱性の管理機能Microsoft Defender セキュリティ センター](https://securitycenter.windows.com/)使用できます。

- 露出スコアと Microsoft Secure Score for Devices を、セキュリティ上の推奨事項、ソフトウェアの脆弱性、修復アクティビティ、公開されたデバイスと共に表示する
- 分析情報EDRエンドポイントの脆弱性と関連付け、それらを処理する
- 修復オプションを選択して修復タスクをトリアージおよび追跡する
- 例外オプションを選択し、アクティブな例外を追跡する

> [!NOTE]
> 過去 30 日間にアクティブではないデバイスは、組織の 脅威と脆弱性の管理 露出スコアと Microsoft Secure Score for Devices を反映するデータには考慮されません。

このビデオでは、ダッシュボードに表示される機能の概要を脅威と脆弱性の管理してください。

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4r1nv]

## <a name="threat-and-vulnerability-management-dashboard"></a>脅威と脆弱性の管理ダッシュボード

 ![Microsoft Defender for Endpoint portal](images/tvm-dashboard-devices.png)

分野 | 説明
:---|:---
**選択したデバイス グループ (#/#)**   | ダッシュボードに脅威と脆弱性の管理するデータをフィルター処理し、デバイス グループ別にカードをフィルター処理します。 フィルターで選択した項目は、ページ全体に脅威と脆弱性の管理されます。
[**暴露スコア**](tvm-exposure-score.md)   | 組織のデバイスが脅威や脆弱性にさらされている現在の状態を確認します。 デバイスで検出された弱点、デバイスが侵害される可能性、組織に対するデバイスの価値、デバイスで検出された関連アラートなど、組織の露出スコアに影響を与える要因がいくつかあります。 目標は、組織の露出スコアを下げ、より安全に行う方法です。 スコアを減らすには、セキュリティに関する推奨事項に記載されている関連するセキュリティ構成の問題を修復する必要があります。
[**デバイス向けの Microsoft セキュア スコア**](tvm-microsoft-secure-score-devices.md) | 組織のオペレーティング システム、アプリケーション、ネットワーク、アカウント、およびセキュリティ制御のセキュリティ体制を参照してください。 目標は、関連するセキュリティ構成の問題を修復して、デバイスのスコアを上げです。 バーを選択すると、[セキュリティの推奨事項] **ページに移動** します。
**デバイスの露出の分布** | 露出レベルに基づいて公開されるデバイスの数を確認します。 ドーナツ グラフのセクションを選択して、[デバイス] リストページに移動し、影響を受けるデバイス名、露出レベル、リスク レベル、その他の詳細 (ドメイン、オペレーティング システム プラットフォーム、正常性状態、最後に表示された状態、タグなど) を表示します。
**セキュリティに関する推奨事項の上位** | 組織のリスクエクスポージャーと必要な緊急性に基づいて並べ替え、優先順位が付けられている照合されたセキュリティ推奨事項を参照してください。 [ **詳細を表示]** を選択すると、一覧に残りのセキュリティ推奨事項が表示されます。 例外 **がある推奨事項の一** 覧の [例外の表示] を選択します。
**脆弱なソフトウェアの上位** | ネットワークのデバイスにインストールされている脆弱なソフトウェアのスタックランクのリストと、そのソフトウェアが組織の露出スコアに与える影響について、組織のソフトウェア インベントリをリアルタイムで可視化します。 [ソフトウェア インベントリ]ページで、脆弱なソフトウェアリストの残りの部分を表示するには、詳細のアイテムを選択するか、[詳細を表示]**を選択** します。
**上位の修復アクティビティ** | セキュリティ推奨事項から生成された修復アクティビティを追跡します。 リスト上の各アイテムを選択して、[修復] ページで詳細を表示するか、[詳細を表示] を選択して、残りの修復アクティビティとアクティブな例外を表示できます。
**上位の公開デバイス** | 公開されているデバイス名とその露出レベルを表示します。 リストからデバイス名を選択すると、デバイス ページに移動して、公開されているデバイスに関連するアラート、リスク、インシデント、セキュリティ推奨事項、インストール済みソフトウェア、および検出された脆弱性を表示できます。 [ **詳細を表示] を** 選択して、公開されているデバイスの残りの一覧を表示します。 デバイスリストから、タグの管理、自動調査の開始、ライブ応答セッションの開始、調査パッケージの収集、ウイルス対策スキャンの実行、アプリの実行の制限、デバイスの分離を行えます。

ポータル全体で使用されるアイコンの詳細については [、「Microsoft Defender for Endpoint アイコン」を参照してください](portal-overview.md#microsoft-defender-for-endpoint-icons)。


## <a name="related-topics"></a>関連項目

- [脅威と脆弱性の管理概要](next-gen-threat-and-vuln-mgt.md)
- [暴露スコア](tvm-exposure-score.md)
- [デバイス向けの Microsoft セキュア スコア](tvm-microsoft-secure-score-devices.md)
- [セキュリティ上の推奨事項](tvm-security-recommendation.md)
- [ソフトウェア インベントリ](tvm-software-inventory.md)
- [イベントのタイムライン](threat-and-vuln-mgt-event-timeline.md)

