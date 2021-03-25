---
title: Microsoft Defender ATP での SIEM ツール統合の問題のトラブルシューティング
description: Microsoft Defender ATP で SIEM ツールを使用するときに発生する可能性のある問題のトラブルシューティングを行います。
keywords: トラブルシューティング, siem, クライアント シークレット, secret
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
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: c1c8fdb0b6e84d4265defb95d91b59a584b7f4c2
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51185781"
---
# <a name="troubleshoot-siem-tool-integration-issues"></a>SIEM ツールの統合に関する問題のトラブルシューティング

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-pullalerts-abovefoldlink) 

SIEM ツールで検出を引き出す際に問題のトラブルシューティングが必要になる場合があります。

このページでは、発生する可能性がある問題をトラブルシューティングするための詳細な手順を示します。


## <a name="learn-how-to-get-a-new-client-secret"></a>新しいクライアント シークレットを取得する方法について
クライアント シークレットの有効期限が切れた場合、または SIEM ツール アプリケーションを有効にするときに提供されたコピーを置き忘れた場合は、新しいシークレットを取得する必要があります。

1. Azure 管理ポータル [にログインします](https://portal.azure.com)。

2. [**Azure Active Directory**] を選択します。

3. テナントを選択します。

4. [アプリ **の登録] をクリックします**。 次に、アプリケーションの一覧で、アプリケーションを選択します。

5. [ **キー] セクション** を選択し、キーの説明を入力し、キーの有効期間を指定します。

6. **[保存]** をクリックします。 キー値が表示されます。

7. 値をコピーし、安全な場所に保存します。


## <a name="error-when-getting-a-refresh-access-token"></a>更新アクセス トークンを取得するときにエラーが発生する
脅威インテリジェンス API または SIEM ツールを使用するときに更新トークンを取得しようとするときにエラーが発生した場合は、Azure Active Directory で関連するアプリケーションの返信 URL を追加する必要があります。

1. Azure 管理ポータル [にログインします](https://ms.portal.azure.com)。

2. [**Azure Active Directory**] を選択します。

3. テナントを選択します。

4. [アプリ **の登録] をクリックします**。 次に、アプリケーションの一覧で、アプリケーションを選択します。

5. 次の URL を追加します。
   - EU の場合: `https://winatpmanagement-eu.securitycenter.windows.com/UserAuthenticationCallback`
   - 英国の場合: `https://winatpmanagement-uk.securitycenter.windows.com/UserAuthenticationCallback`
   - 米国の場合:  `https://winatpmanagement-us.securitycenter.windows.com/UserAuthenticationCallback` .
 
6. **[保存]** をクリックします。

## <a name="error-while-enabling-the-siem-connector-application"></a>SIEM コネクタ アプリケーションを有効にしている間のエラー
SIEM コネクタ アプリケーションを有効にしようとするときにエラーが発生した場合は、ブラウザーのポップアップ ブロッカー設定を確認してください。 機能を有効にするときに開いている新しいウィンドウがブロックされている可能性があります。




>Microsoft Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-troubleshootsiem-belowfoldlink) 

## <a name="related-topics"></a>関連項目
- [エンドポイント向け Microsoft Defender で SIEM 統合を有効にする](enable-siem-integration.md)
- [エンドポイント検出用の Microsoft Defender をプルする ArcSight の構成](configure-arcsight.md)
- [SIEM ツールへの検出のプル](configure-siem.md)
- [Microsoft Defender for Endpoint Detection フィールド](api-portal-mapping.md)
- [REST API を使用したエンドポイント検出用の Microsoft Defender のプル](pull-alerts-using-rest-api.md)