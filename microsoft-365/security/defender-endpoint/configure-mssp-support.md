---
title: マネージ セキュリティ サービス プロバイダーのサポートを構成する
description: エンドポイント用 Microsoft Defender との MSSP 統合を構成するために必要な手順を実行する
keywords: マネージド セキュリティ サービス プロバイダー、mssp、構成、統合
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d82bffd6eea54256f2c6773f843030a19e27275d
ms.sourcegitcommit: 0d1b065c94125b495e9886200f7918de3bda40b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/08/2021
ms.locfileid: "53339360"
---
# <a name="configure-managed-security-service-provider-integration"></a>マネージド セキュリティ サービス プロバイダーの統合を構成する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Defender for Endpoint を体験してみませんか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-mssp-support-abovefoldlink)
 
[!include[Prerelease information](../../includes/prerelease.md)]

管理セキュリティ サービス プロバイダー (MSSP) の統合を有効にするには、次の構成手順を実行する必要があります。

>[!NOTE]
>この記事では、サービス プロバイダーとサービス コンシューマーを区別するために、次の用語を使用します。
> - MSSP: 組織のセキュリティ デバイスの監視と管理を提供するセキュリティ組織。
> - MSSP のお客様: MSSP のサービスを利用する組織。

統合により、MSSP は次のアクションを実行できます。

- MSSP 顧客のポータルへのアクセスMicrosoft 365 Defenderする
- 電子メール通知を取得し、 
- セキュリティ情報とイベント管理 (SIEM) ツールを使用してアラートを取得する

MSSP がこれらのアクションを実行する前に、MSSP のお客様は、MSSP がポータルにアクセスできるよう、Defender for Endpoint テナントへのアクセスを許可する必要があります。 
 

通常、MSSP のお客様は初期構成手順を実行して、MSSP にセキュリティ セントラル テナントへのアクセス権Windows Defender付与します。 アクセスが許可された後、他の構成手順は、MSSP カスタマーまたは MSSP によって実行できます。


一般に、次の構成手順を実行する必要があります。


- **MSSP にアクセス権を付与Microsoft 365 Defender** <br>
このアクションは、MSSP のお客様が行う必要があります。 MSSP のお客様の Defender for Endpoint テナントへの MSSP アクセスを許可します。
 

- **MSSP に送信されるアラート通知を構成する** <br>
このアクションは、MSSP カスタマーまたは MSSP によって実行できます。 これにより、MSSP は、MSSP のお客様に対処する必要があるアラートを知る必要があります。

- **MSSP 顧客のテナントから SIEM システムへのアラートの取得** <br> このアクションは MSSP によって実行されます。 これにより、MSSP は SIEM ツールでアラートをフェッチできます。

- **API を使用して MSSP 顧客のテナントからアラートを取得する** <br>
このアクションは MSSP によって実行されます。 これにより、MSSP は API を使用してアラートをフェッチできます。

## <a name="multi-tenant-access-for-mssps"></a>MSSP のマルチテナント アクセス
マルチテナント委任アクセスを実装する方法については [、「Managed Security Service Providers](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/multi-tenant-access-for-managed-security-service-providers/ba-p/1533440)のマルチテナント アクセス」を参照してください。



## <a name="related-topics"></a>関連項目
- [ポータルへの MSSP アクセスを許可する](grant-mssp-access.md)
- [MSSP カスタマー ポータルにアクセスする](access-mssp-portal.md)
- [アラート通知を構成する](configure-mssp-notifications.md)
- [顧客テナントからアラートを取得する](fetch-alerts-mssp.md)

