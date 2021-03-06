---
title: フィッシングメール攻撃の例
description: フィッシング攻撃の分析例を説明します。
keywords: インシデント、アラート、調査、相関、攻撃、マシン、デバイス、ユーザー、複数の ID、ID、メールボックス、メール、365、Microsoft、M365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 41a2c73ce5e1c3060d88572f4fa7afe63e193f46
ms.sourcegitcommit: de5fce90de22ba588e75e1a1d2e87e03b9e25ec7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2021
ms.locfileid: "52299990"
---
# <a name="example-of-a-phishing-email-attack"></a>フィッシングメール攻撃の例

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**適用対象:**
- Microsoft 365 Defender

Microsoft 365 Defender は、電子メールを介して配信される悪意のある添付ファイルを検出するのに役立ちます。 Office [365](https://protection.office.com/) セキュリティ/コンプライアンス センターは Microsoft 365 Defender と統合されています。セキュリティ アナリストは、Office 365 からの脅威 (電子メールの添付ファイルなど) を可視化できます。

たとえば、アナリストに複数ステージのインシデントが割り当てられたとします。
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-incident.png" alt-text="複数ステージインシデントの例"::: 

インシデントの **[アラート** ] タブに、Defender から 365 Office Microsoft Cloud App Security のアラートが表示されます。 アナリストは、電子メール メッセージの通知を選択Office 365 アラートの Defender にドリルダウンできます。 アラートの詳細がサイド ウィンドウに表示されます。

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png" alt-text="電子メールアラートの例":::
 
さらに下にスクロールすると、より多くの情報が表示され、影響を受ける悪意のあるファイルとユーザーが表示されます。

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-impact.png" alt-text="電子メール アラートのユーザーとファイルへの影響の例":::
  
[アラート **を開く] ページ** を選択すると、特定のアラートに移動し、リンクを選択することでさまざまな情報を詳細に表示できます。 実際の電子メール メッセージは、パネルの下部に向かって **[エクスプローラー** でメッセージを表示する] を選択して表示できます。
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png" alt-text="アラートの詳細の例"::: 

これにより、アナリストが [脅威の管理] ページに移動し、電子メールの件名、受信者、送信者、その他の情報が表示されます。 **[特別な** アクション **] の下の** ZAP は、ゼロ時間自動削除機能が実装されたとアナリストに指示します。 ZAP は、組織全体のメールボックスから悪意のあるメッセージやスパム メッセージを自動的に検出して削除します。 詳細については [、「Exchange Online のゼロ時間自動削除 (ZAP)」を参照してください](../office-365-security/zero-hour-auto-purge.md)。

[アクション] を選択すると、特定のメッセージに対して他のアクションを **実行できます**。 
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-actions.png" alt-text="電子メール メッセージに対して実行できるその他のアクションの例"::: 

## <a name="next-step"></a>次の手順

ID ベース [の攻撃調査パスを](first-incident-path-identity.md) 参照してください。

## <a name="see-also"></a>関連項目

- [インシデントの概要](incidents-overview.md)
- [インシデントの調査](investigate-incidents.md)
- [インシデントの管理](manage-incidents.md)
