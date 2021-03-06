---
title: Microsoft Defender for Endpoint パートナーの機会とシナリオ
ms.reviewer: ''
description: 開いているフレームワークと豊富な API の上に既存のセキュリティ サービスを拡張して、Microsoft Defender for Endpoint との拡張機能と統合を構築する方法について説明します。
keywords: API、パートナー、拡張、オープン フレームワーク、API、拡張機能、統合、検出、管理、応答、脆弱性、インテリジェンス
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: be2f33514a568f290a3fc5cf0adc62db72243a6f
ms.sourcegitcommit: 22505ce322f68a2d0ce70d71caf3b0a657fa838a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "51861111"
---
# <a name="microsoft-defender-for-endpoint-partner-opportunities-and-scenarios"></a>Microsoft Defender for Endpoint パートナーの機会とシナリオ

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Defender for Endpoint を体験してみませんか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 


パートナーは、オープン フレームワークと豊富で完全な API の上に既存のセキュリティ サービスを簡単に拡張して、Defender for Endpoint との拡張機能と統合を構築できます。 

API は、検出、管理、対応、脆弱性、インテリジェンスの幅広い使用例などの機能領域にまたがっています。 使用例と必要性に基づいて、パートナーは Defender for Endpoint からデータをストリームまたはクエリできます。 


## <a name="scenario-1-external-alert-correlation-and-automated-investigation-and-remediation"></a>シナリオ 1: 外部アラートの相関関係と自動調査と修復
Defender for Endpoint は、インシデント対応を大規模に駆動する独自の自動調査および修復機能を提供します。 

自動調査と対応機能をネットワーク セキュリティ製品や他のエンドポイント セキュリティ製品などの他のソリューションと統合すると、アラートに対処できます。 また、この統合により、ネットワークとデバイス信号の相関関係を取り巻く複雑さを最小限に抑え、デバイスの調査と脅威の修復アクションを効率的に合理化できます。

Defender for Endpoint は、次の形式でこのシナリオのサポートを追加します。

- 外部アラートを Defender for Endpoint にプッシュし、Defender for Endpoint からの追加のデバイス ベースのアラートを並べて表示できます。 このビューは、アラートの完全なコンテキスト (実際のプロセスと攻撃の完全なストーリー) を提供します。

- アラートが生成されると、企業内のすべての Defender for Endpoint 保護エンドポイント間で信号が共有されます。 Defender for Endpoint は、アラートに対処するために、直ちに自動化された応答またはオペレーター支援応答を受け取る。

## <a name="scenario-2-security-orchestration-and-automation-response-soar-integration"></a>シナリオ 2: セキュリティ オーケストレーションとオートメーション応答 (SOAR) の統合
オーケストレーション ソリューションは、プレイブックを構築し、Defender for Endpoint API がデバイス データのクエリ、デバイス分離のトリガー、ブロック/許可、アラートの解決などの応答を調整するために公開するリッチ データ モデルとアクションを統合するのに役立ちます。

## <a name="scenario-3-indicators-matching"></a>シナリオ 3: インジケーターの一致 
侵害インジケーター (IoCs) マッチングは、すべてのエンドポイント保護ソリューションで不可欠な機能です。 この機能は Defender for Endpoint で使用できます。エンティティの予防、検出、除外のインジケーターの一覧を設定できます。 1 つは、実行するアクションと、アクションを適用する期間を定義できます。

上記のシナリオは、プラットフォームの拡張性の例として機能します。 例に限定されるのではなく、オープン フレームワークを活用して他のシナリオを発見し、探索してください。

「エンドポイント向け Microsoft Defender パートナーになる」の手順に従 [って、Defender](get-started-partner-integration.md) for Endpoint にソリューションを統合します。

## <a name="related-topic"></a>関連トピック
- [管理と API の概要](management-apis.md)
