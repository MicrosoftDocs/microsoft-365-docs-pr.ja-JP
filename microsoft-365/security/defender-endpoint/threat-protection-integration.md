---
title: エンドポイント用 Microsoft Defender を他の Microsoft ソリューションと統合する
description: Microsoft Defender for Endpoint が、Microsoft Defender for Identity や Azure Security Center などの他の Microsoft ソリューションと統合する方法について説明します。
author: mjcaparas
ms.author: macapara
ms.prod: m365-security
keywords: microsoft 365 defender, 条件付きアクセス, office, 高度な脅威保護, id 用 microsoft Defender, microsoft defender for office, Azure security center, microsoft cloud app security, azure sentinel
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 287ad9adeccd527b756bdd5304d3c89fc1b2d789
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51068452"
---
# <a name="microsoft-defender-for-endpoint-and-other-microsoft-solutions"></a>エンドポイント向け Microsoft Defender および他の Microsoft ソリューション

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="integrate-with-other-microsoft-solutions"></a>他の Microsoft ソリューションとの統合

Microsoft Defender for Endpoint は、さまざまな Microsoft ソリューションと直接統合します。

### <a name="azure-security-center"></a>Azure Security Center
Microsoft Defender for Endpoint は、Windows サーバー上のエンドポイント検出および応答 (EDR) 機能を含む包括的なサーバー保護ソリューションを提供します。

### <a name="azure-sentinel"></a>Azure Sentinel
Microsoft Defender for Endpoint コネクタを使用すると、Microsoft Defender for Endpoint から Azure Sentinel にアラートをストリーミングできます。 これにより、組織全体のセキュリティ イベントをより包括的に分析し、プレイブックを構築して効果的かつ迅速に対応できます。

### <a name="azure-information-protection"></a>Azure Information Protection
機密データを安全に保ち、データ検出とデータ保護を通じて職場の生産性を実現します。

### <a name="conditional-access"></a>条件付きアクセス
Microsoft Defender for Endpoint の動的デバイス リスク スコアは条件付きアクセス評価に統合され、セキュリティで保護されたデバイスだけがリソースにアクセスできます。 

### <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security
Microsoft Cloud App Security では、Microsoft Defender for Endpoint エンドポイント信号を活用して、サポートされていないクラウド サービス (シャドウ IT) をすべての Microsoft Defender for Endpoint 監視対象デバイスから使用するなど、クラウド アプリケーションの使用状況を直接可視化できます。

### <a name="microsoft-defender-for-identity"></a>Microsoft Defender for Identity
疑わしいアクティビティは、ユーザー コンテキストで実行されているプロセスです。 Microsoft Defender for Endpoint と Azure ATP の統合により、アクティビティと ID 全体でサイバー セキュリティ調査を柔軟に実施できます。

### <a name="microsoft-defender-for-office"></a>Microsoft Defender for Office
[Defender for Office 365](https://docs.microsoft.com/office365/securitycompliance/office-365-atp) は、ATP セーフ リンク、ATP の安全な添付ファイル、高度なフィッシング対策、スプーフィング インテリジェンス機能を通じて、電子メール メッセージまたはファイル内のマルウェアから組織を保護するのに役立ちます。 365 ATP Office Microsoft Defender for Endpoint の統合により、セキュリティ アナリストは攻撃のエントリ ポイントを調査するために上流に移動できます。 脅威インテリジェンスの共有を通じて、攻撃を封じ込め、ブロックすることができます。 

>[!NOTE]
> 過去 30 Office内のイベントに対して、365 データの Defender が表示されます。 アラートの場合、365 Officeの Defender は、最初のアクティビティ時間に基づいて表示されます。 その後、データは Defender で 365 以降Officeされます。

### <a name="skype-for-business"></a>Skype for Business
Skype for Business 統合は、アナリストがポータルから簡単なボタンを使用して、侵害される可能性のあるユーザーまたはデバイスの所有者と通信する方法を提供します。

## <a name="microsoft-365-defender"></a>Microsoft 365 Defender
Microsoft 365 Defender を使用すると、Microsoft Defender for Endpoint とさまざまな Microsoft セキュリティ ソリューションが統合された侵害前および侵害後のエンタープライズ防御スイートを形成し、エンドポイント、ID、電子メール、およびアプリケーション間でネイティブに統合され、高度な攻撃を検出、防止、調査、および自動的に対応します。 
 
[Microsoft 365 Defender の詳細](https://docs.microsoft.com/microsoft-365/security/defender/microsoft-threat-protection)


## <a name="related-topics"></a>関連項目
- [統合などの高度な機能を構成する](advanced-features.md)
- [Microsoft 365 Defender の概要](https://docs.microsoft.com/microsoft-365/security/defender/microsoft-threat-protection)
- [Microsoft 365 Defender を有効にする](https://docs.microsoft.com/microsoft-365/security/defender/mtp-enable)
- [条件付きアクセスを使用してユーザー、データ、デバイスを保護する](conditional-access.md)