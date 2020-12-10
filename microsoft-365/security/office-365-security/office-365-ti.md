---
title: 脅威調査 & 応答能力-Microsoft Defender for Office 365 プラン2
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 12/09/2019
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 32405da5-bee1-4a4b-82e5-8399df94c512
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom:
- seo-marvel-apr2020
description: Microsoft Defender for Office 365 プランの脅威の調査および応答機能について説明します。
ms.openlocfilehash: cbda50dacd6b892c976ce55632c8fc35813839b7
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "49614776"
---
# <a name="threat-investigation-and-response"></a>脅威の調査および対応

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


[Microsoft Defender For Office 365 の](office-365-atp.md)脅威の調査と応答の機能セキュリティアナリストと管理者は、次のようにして、組織の microsoft 365 をビジネスユーザーに保護します。

- Cyberattacks を容易に識別、監視、理解できるようにする
- Exchange Online、SharePoint Online、OneDrive for Business、および Microsoft Teams での脅威への迅速な対応
- 組織に対する cyberattacks を防止するためにセキュリティ操作を支援するための洞察と知識の提供
- メールベースの重要な脅威に対して [Office 365 で自動化された調査と応答](automated-investigation-response-office.md) を使用する

脅威の調査と応答の機能によって、セキュリティ & コンプライアンスセンターで利用可能な脅威と関連する応答アクションが洞察されます。 これらの洞察は、組織のセキュリティチームが電子メールまたはファイルベースの攻撃からユーザーを保護するのに役立ちます。 機能は、ユーザーアクティビティ、認証、電子メール、危険にさらされた Pc、セキュリティインシデントなど、複数のソースからのデータを監視し、データを収集するのに役立ちます。 ビジネス意思決定者およびセキュリティ運用チームは、この情報を使用して組織との脅威を理解し、知的財産権を保護することができます。

## <a name="get-acquainted-with-threat-investigation-and-response-tools"></a>脅威の調査と応答のツールについて理解する

脅威の調査と応答の機能は、セキュリティ & コンプライアンスセンターで、次のような一連のツールと応答のワークフローとして提供されます。

- [脅威ダッシュボード](#threat-dashboard)
- [Explorer](#threat-explorer)
- [インシデント](#incidents)
- [攻撃シミュレータ](#attack-simulator)
- [自動調査および対応](automated-investigation-response-office.md)

### <a name="threat-dashboard"></a>脅威ダッシュボード

脅威ダッシュボード ( [セキュリティダッシュボード](security-dashboard.md)とも呼ばれます) を使用して、どのような脅威が解決されたかをすばやく確認し、Microsoft 365 サービスがビジネスをどのようにセキュリティ保護しているかをビジネス意思決定者に報告することができます。

![脅威ダッシュボード](../../media/ce013a31-3f80-4d09-bb95-bfb7623b8bc4.png)

このダッシュボードを表示して使用するには、セキュリティ & コンプライアンスセンターで、[**脅威管理**] ダッシュボードに移動し \> ます。

### <a name="threat-explorer"></a>脅威エクスプローラー

脅威 [エクスプローラー (およびリアルタイム検出)](threat-explorer.md) を使用して脅威を分析し、時間の経過と共に攻撃の量を確認し、脅威ファミリ、攻撃インフラストラクチャなどによるデータの分析を行います。 脅威エクスプローラー (エクスプローラーとも呼ばれます) は、セキュリティアナリストの調査ワークフローの出発点です。

![脅威エクスプローラー](../../media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png)

このレポートを表示して使用するには、セキュリティ & コンプライアンスセンターで、[**脅威管理** エクスプローラー] に移動し \> ます。

### <a name="incidents"></a>インシデント

インシデントリスト (調査とも呼ばれます) を使用して、フライトセキュリティインシデントの一覧を表示します。 インシデントは、不審な電子メールメッセージなどの脅威を追跡し、さらに調査と修復を行うために使用されます。

![Office 365 の現在の脅威インシデントの一覧](../../media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png)

組織の現在のインシデントの一覧を表示するには、セキュリティ & コンプライアンスセンターで、[ **脅威管理** の \> **レビュー** \> **インシデント**] に移動します。

![[セキュリティ & コンプライアンスセンター] で、[脅威管理のレビュー] を選択します。 \>](../../media/e0f46454-fa38-40f0-a120-b595614d1d22.png)

### <a name="attack-simulator"></a>攻撃シミュレータ

アタックシミュレータを使用して、組織内で現実的な cyberattacks を設定して実行し、実際の cyberattack がビジネスに影響を与える前に、脆弱性のある人物を特定します。 詳細については、「 [Office 365 のアタックシミュレータ](attack-simulator.md)」を参照してください。

### <a name="automated-investigation-and-response"></a>自動調査および対応

自動化された調査と応答 (AIR) 機能を使用して、コンテンツ、デバイス、およびユーザーを組織内の脅威から危険に関連付ける時間と労力を節約します。 AIR プロセスは、特定の警告がトリガーされたとき、またはセキュリティ操作チームによって開始されたときに開始できます。 詳細については、「 [Office 365 の自動調査と応答](automated-investigation-response-office.md)」を参照してください。

## <a name="threat-intelligence-widgets"></a>脅威インテリジェンスウィジェット

セキュリティアナリストは、Microsoft Defender for Office 365 プラン2のサービスの一部として、既知の脅威の詳細を確認できます。 これは、ユーザーを安全に保つために実行できる追加の予防策/手順があるかどうかを判断するのに役立ちます。

![最近の脅威に関する情報を示すセキュリティ傾向](../../media/11e7d40d-139b-4c56-8d52-c091c8654151.png)

## <a name="how-do-we-get-these-capabilities"></a>これらの機能はどのように入手できますか?

Microsoft 365 の脅威の調査と応答の機能は、Enterprise E5 または特定のサブスクリプションのアドオンとして組み込まれている Office 365 プラン2の Microsoft Defender に含まれています。 詳細については、「 [Defender For Office 365 プラン1およびプラン 2](office-365-atp.md#microsoft-defender-for-office-365-plan-1-and-plan-2)」を参照してください。

## <a name="required-roles-and-permissions"></a>必要な役割と権限

Microsoft Defender for Office 365 は、役割ベースのアクセス制御を使用します。 アクセス許可は、Azure Active Directory、Microsoft 365 管理センター、またはセキュリティ & コンプライアンスセンターの特定の役割によって割り当てられます。

> [!TIP]
> セキュリティ管理者などの一部の役割は、セキュリティ & コンプライアンスセンターで割り当てることができますが、代わりに Microsoft 365 管理センターまたは Azure Active Directory のどちらかを使用することを検討してください。 役割、役割グループ、およびアクセス許可の詳細については、以下のリソースを参照してください。
>
> - [セキュリティ/コンプライアンス センターのアクセス許可](permissions-in-the-security-and-compliance-center.md)
>
> - [Azure Active Directory での管理者役割のアクセス許可](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)

****

|アクティビティ|ロールと権限|
|---|---|
|脅威ダッシュボード (または新しい [セキュリティダッシュボード](security-dashboard.md)) を使用する <p> 最近の脅威または現在の脅威に関する情報を表示する|以下のいずれか: <ul><li>**グローバル管理者**</li><li>**セキュリティ管理者**</li><li>**セキュリティリーダ**</li></ul> <p> これらの役割は、Azure Active Directory ( <https://portal.azure.com> ) または Microsoft 365 admin center () のいずれかで割り当てることができ <https://admin.microsoft.com> ます。|
|脅威 [エクスプローラー (およびリアルタイム検出)](threat-explorer.md) を使用して脅威を分析する|以下のいずれか: <ul><li>**グローバル管理者**</li><li>**セキュリティ管理者**</li><li>**セキュリティリーダ**</li></ul> <p> これらの役割は、Azure Active Directory ( <https://portal.azure.com> ) または Microsoft 365 admin center () のいずれかで割り当てることができ <https://admin.microsoft.com> ます。|
|インシデント (調査とも呼ばれる) を表示する <p> インシデントに電子メールメッセージを追加する|以下のいずれか: <ul><li>**グローバル管理者**</li><li>**セキュリティ管理者**</li><li>**セキュリティリーダ**</li></ul> <p> これらの役割は、Azure Active Directory ( <https://portal.azure.com> ) または Microsoft 365 admin center () のいずれかで割り当てることができ <https://admin.microsoft.com> ます。|
|インシデントで電子メールアクションをトリガーする <p> 疑わしい電子メールメッセージの検索と削除|以下のいずれか: <ul><li>**グローバル管理者**</li><li>**セキュリティ管理者** 、 **および検索と削除** の役割</li></ul> <p> **グローバル管理** 者および **セキュリティ管理者** の役割は、Azure Active Directory ( <https://portal.azure.com> ) または Microsoft 365 admin center () のいずれかに割り当てることができ <https://admin.microsoft.com> ます。 <p> **検索および削除** の役割は、セキュリティ & コンプライアンスセンター () で割り当てる必要があり <https://protection.office.com> ます。|
|エンドポイントの Microsoft Defender と Office 365 プラン2の統合  <p> Microsoft Defender for Office 365 プラン2を SIEM サーバーと統合する|**グローバル管理者** または Azure Active Directory () または Microsoft 365 admin center () のいずれかに割り当てられている **セキュリティ管理者** の役割 <https://portal.azure.com> <https://admin.microsoft.com> 。 <p> --- **plus** --- <p> 追加のアプリケーション ( [Microsoft Defender セキュリティセンター](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/user-roles) 、SIEM サーバーなど) に割り当てられている適切な役割。|
|

## <a name="next-steps"></a>次の手順

- [脅威のトラッカーについて-新知識と注目](threat-trackers.md)

- [配信された悪意のある電子メールを検索して調査する (Office 365 の脅威の調査と応答)](investigate-malicious-email-that-was-delivered.md)

- [エンドポイントの Microsoft Defender で Office 365 の脅威の調査と応答を統合する](integrate-office-365-ti-with-wdatp.md)

- [アタックシミュレータについて](attack-simulator.md)
