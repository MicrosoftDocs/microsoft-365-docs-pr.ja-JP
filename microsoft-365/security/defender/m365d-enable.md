---
title: セキュリティ センターでMicrosoft 365 Defenderを有効Microsoft 365する
description: セキュリティ インシデントと対応のMicrosoft 365 Defenderを有効にし、統合を開始する方法について学習します。
keywords: 開始する、Microsoft 365 Defender、Microsoft 365 Defender、M365、セキュリティ、データの場所、必要なアクセス許可、ライセンスの適格性、設定ページを有効にする
search.product: eADQiWindows 10XVcnh
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
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 102666834562d0576920c746842582c2870b3738
ms.sourcegitcommit: bbad1938b6661d4a6bca99f235c44e521b1fb662
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2021
ms.locfileid: "53007611"
---
# <a name="turn-on-microsoft-365-defender"></a>Microsoft 365 Defender を有効にする

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**適用対象:**
- Microsoft 365 Defender

[Microsoft 365 Defender、Microsoft](microsoft-365-defender.md) Defender for Endpoint、Microsoft Defender for Office 365、Microsoft Cloud App Security、および Microsoft Defender for Identity を統合することで、インシデント対応プロセスを統合します。 この統合されたエクスペリエンスにより、Microsoft 365 セキュリティ センターでアクセスできる強力な機能が追加されました。

Microsoft 365 Defenderアクセス許可を持つ対象ユーザーがセキュリティ センターにアクセスすると、自動的Microsoft 365オンになります。 この記事では、さまざまな前提条件とプロビジョニングのMicrosoft 365 Defender説明します。

## <a name="check-license-eligibility-and-required-permissions"></a>ライセンスの適格性と必要なアクセス許可を確認する

一般に、Microsoft 365製品のライセンスは、追加のライセンスコストなしでMicrosoft 365 Defender Microsoft 365を使用できます。 サポートされているサービスへのアクセスを提供するライセンスMicrosoft 365 E5 E5 Security、A5、A5 セキュリティ ライセンス、または有効なライセンスの組み合わせを取得することをお勧めします。

ライセンスの詳細については、「ライセンス [要件」を参照してください](prerequisites.md#licensing-requirements)。

### <a name="check-your-role"></a>役割を確認する

サーバーを有効に **するには、** グローバル管理者またはセキュリティ管理者Azure Active Directory必要Microsoft 365 Defender。 [Azure AD でロールを表示AD](/azure/active-directory/users-groups-roles/directory-manage-roles-portal)

## <a name="supported-services"></a>サポートされているサービス

Microsoft 365 Defender、既に展開したさまざまなサポートされているサービスのデータを集計します。 データを一元的に処理して保存し、新しい分析情報を特定し、一元的な応答ワークフローを可能にします。 これは、統合サービスに関連付けられている既存の展開、設定、またはデータに影響を与えることなく行います。

最適な保護と最適化をMicrosoft 365 Defender、該当するサポートされているサービスをネットワークに展開することをお勧めします。 詳細については、「サポート [されているサービスの展開」を参照してください](deploy-supported-services.md)。

## <a name="onboard-to-the-service"></a>サービスにオンボードする
ユーザーへのオンボーディングMicrosoft 365 Defender簡単です。 ナビゲーション メニューから &、インシデント やアラート、ハンティング、アクション センター **、または** 脅威分析などの任意のアイテムを選択して、オンボーディング プロセスを開始します。  

### <a name="data-center-location"></a>データ センターの場所

Microsoft 365 Defenderは、Microsoft Defender for Endpoint で使用されるのと同じ場所にデータ[を格納して処理します](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy)。 Microsoft Defender for Endpoint をお持ちでない場合は、アクティブなセキュリティ サービスの場所に基づいて、新しいデータ センター Microsoft 365選択されます。 選択したデータ センターの場所が画面に表示されます。

セキュリティ **センターで [ヘルプが必要** Microsoft 365] を選択して、別のデータ センターの場所でのプロビジョニングに関Microsoft 365 Defender Microsoft サポートに問い合わせします。

> [!NOTE]
> Azure Defender を使用してオンにした場合、Microsoft Defender for Endpoint は欧州連合 (EU) データ センターで自動的にプロビジョニングされました。 Microsoft 365 Defender、過去にこの方法で Defender for Endpoint をプロビジョニングしたお客様に対して、同じ EU データ センターで自動的にプロビジョニングされます。

### <a name="confirm-that-the-service-is-on"></a>サービスが有効になっていることを確認する

サービスがプロビジョニングされると、次の機能が追加されます。

- [イベント管理](incidents-overview.md)
- [アラート キュー](investigate-alerts.md)
- [自動化された調査と対応](m365d-autoir.md)を管理するアクション センター
- [高度なハンティング](advanced-hunting-overview.md) 機能
- 脅威の分析

![インシデント管理Microsoft 365その他の機能Microsoft 365 Defenderセキュリティ Microsoft 365機能を備えたセキュリティ センター ナビゲーション ウィンドウ ](../../media/overview-incident.png)
 *Microsoft 365 Defender画像*

### <a name="getting-microsoft-defender-for-identity-data"></a>Id データの Microsoft Defender の取得 
サーバーとの統合を有効Microsoft Cloud App Security、少なくとも 1 回は、Microsoft Cloud App Securityする必要があります。

## <a name="get-assistance"></a>サポートを利用する

ユーザー設定のオンに関する最も一般的な質問に対する回答をMicrosoft 365 Defender FAQ[を参照してください](m365d-enable-faq.md)。

Microsoft サポート スタッフは、テナントのサービスおよび関連リソースのプロビジョニングまたはプロビジョニング解除を支援できます。 サポートについては、セキュリティ センターで [ヘルプ **が必要Microsoft 365** 選択します。 サポートに問い合わせする場合は、Microsoft 365 Defender。

## <a name="related-topics"></a>関連項目

- [よく寄せられる質問](m365d-enable-faq.md)
- [ライセンス要件およびその他の前提条件](prerequisites.md)
- [サポートされているサービスを展開する](deploy-supported-services.md)
- [Microsoft 365 Defender概要](microsoft-365-defender.md)
- [Microsoft Defender for Endpoint の概要](../defender-endpoint/microsoft-defender-endpoint.md)
- [Defender for Office 365概要](../office-365-security/defender-for-office-365.md)
- [Microsoft Cloud App Security の概要](/cloud-app-security/what-is-cloud-app-security)
- [Microsoft Defender for Identity の概要](/azure-advanced-threat-protection/what-is-atp)
- [Microsoft Defender for Endpoint data storage](../defender-endpoint/data-storage-privacy.md)
