---
title: Microsoft Defender for Endpoint から Microsoft 365 セキュリティ センターへのアカウントのリダイレクト
description: Defender for Endpoint から Microsoft 365 セキュリティ センターにアカウントとセッションをリダイレクトする方法。
keywords: Microsoft 365 セキュリティ センター、Microsoft 365 セキュリティ センターの使用開始、セキュリティ センターのリダイレクト
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 626bc9950512438bfa43e6500adf72940ddcbfec
ms.sourcegitcommit: 3d48e198e706f22ac903b346cadda06b2368dd1e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "50727567"
---
# <a name="redirecting-accounts-from-microsoft-defender-for-endpoint-to-the-microsoft-365-security-center"></a>Microsoft Defender for Endpoint から Microsoft 365 セキュリティ センターへのアカウントのリダイレクト

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**適用対象:**
- Microsoft 365 Defender
- Defender for Endpoint

SIEM と拡張検出および応答 (XDR) による脅威保護に対する Microsoft のクロスドメインアプローチに合わせ、Microsoft Defender Advanced Threat Protection を Microsoft Defender for Endpoint として再ブランド化し、それを単一の統合ポータルである Microsoft 365 セキュリティ センターに統合しました。

このガイドでは、以前の Microsoft Defender for Endpoint ポータル (securitycenter.windows.com または securitycenter.microsoft.com) から Microsoft 365 セキュリティ センター ポータル (security.microsoft.com) への自動リダイレクトを有効にすることで、アカウントを Microsoft 365 セキュリティ センターにルーティングする方法について説明します。

> [!NOTE]
> Microsoft 365 セキュリティ センターの Microsoft Defender for Endpoint は[、Microsoft Defender](https://docs.microsoft.com/microsoft-365/security/mtp/mssp-access)セキュリティ センターでアクセスを許可する方法と同じ方法で、マネージド セキュリティ サービス プロバイダー [(MSSP)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access)へのアクセスを許可します。

## <a name="what-to-expect"></a>何を期待する
自動リダイレクトが有効になると、securitycenter.windows.com または securitycenter.microsoft.com の元の Microsoft Defender for Endpoint ポータルにアクセスするアカウントが、security.microsoft.com の Microsoft 365 セキュリティ センター ポータルに自動的にルーティングされます。
 
変更点について詳しくは [、Microsoft 365](microsoft-365-security-center-mde.md)セキュリティ センターの Microsoft Defender for Endpoint をご覧ください。

これには、以前の securitycenter.windows.com ポータルを指すリンク (電子メール通知のリンクなど) や SIEM API 呼び出しによって返されるリンクなど、ブラウザー経由で以前のポータルに直接アクセスするリダイレクトが含まれます。  

 メール通知または SIEM API からの外部リンクには、現在、両方のポータルへのリンクが含まれている。 リダイレクトが有効になると、古いリンクが最終的に削除されるまで、両方のリンクが Microsoft 365 セキュリティ センターを指します。 Microsoft 365 セキュリティ センターを指す新しいリンクを採用してください。

リンクとルーティングの詳細については、以下の表を参照してください。
## <a name="siem-api-routing"></a>SIEM API ルーティング

|**プロパティ**  |**リダイレクトが OFF の場合の宛先**  |**リダイレクトが ON の場合の宛先** | 
|---------|---------|---------|
| LinkToWDATP | [アラート] ページ (securitycenter.windows.com | [アラート] ページ (security.microsoft.com  |
| IncidentLinkToWDATP | [インシデント] ページ (securitycenter.windows.com  | [インシデント] ページ (security.microsoft.com  |
| LinkToMTP | [アラート] ページ (security.microsoft.com | [アラート] ページ (security.microsoft.com  |
| IncidentLinkToMTP | [インシデント] ページ (security.microsoft.com  | [インシデント] ページ (security.microsoft.com  

## <a name="email-alert-notifications"></a>電子メールアラート通知

|**プロパティ**  |**リダイレクトが OFF の場合の宛先**  |**リダイレクトが ON の場合の宛先** |
|---------|---------|---------|
| [アラート] ページ  | [アラート] ページ (securitycenter.windows.com  | [アラート] ページ (security.microsoft.com  |
| インシデント ページ  |[インシデント] ページ (securitycenter.windows.com  | [インシデント] ページ (security.microsoft.com  
| セキュリティ センター ポータルの [アラート] ページ | [アラート] ページ (security.microsoft.com | [アラート] ページ (security.microsoft.com | 
| セキュリティ センター ポータルのインシデント ページ | [インシデント] ページ (security.microsoft.com  | [インシデント] ページ (security.microsoft.com  |

## <a name="when-does-this-take-effect"></a>これはいつ有効になりますか? 
有効にすると、この更新プログラムは一部のアカウントでほぼ直ちに有効になる可能性があります。 ただし、リダイレクトが組織内のすべてのアカウントに伝達されるのに時間がかかる場合があります。 この設定が適用されている間、アクティブなセッションのアカウントはセッションから取り出されません。現在のセッションを終了して再びサインインした後にのみ、Microsoft 365 セキュリティ センターにルーティングされます。  

### <a name="set-up-portal-redirection"></a>ポータルリダイレクトの設定
Microsoft 365 セキュリティ センターへのアカウントのルーティングを開始するには、次の手順を実行します。
1. Azure Active directory でグローバル管理者またはセキュリティ管理者のアクセス許可を持っている必要があります。 

2. [](https://security.microsoft.com/) Microsoft 365 セキュリティ センターにサインインします。

3. [設定エンドポイント **]**  >  **[全般ポータル]**  >  **リダイレクト**  >  **に移動するか、**[ここをクリックします](https://security.microsoft.com/preferences2/portal_redirection)。  

4. [自動リダイレクト] 設定を [オン] に **切り替える**。

5. [ **有効にする]** をクリックして、Microsoft 365 セキュリティ センター ポータルに自動リダイレクトを適用します。

>[!IMPORTANT]
>この設定を有効にすると、アクティブなユーザー セッションは終了しません。 この設定が適用されている間にアクティブ なセッションに参加しているアカウントは、現在のセッションを終了して再度サインインした後にのみ、Microsoft 365 セキュリティ センターに移動されます。

>[!NOTE]
>この設定を有効または無効にするには、グローバル管理者または Azure Active Directory のセキュリティ管理者のアクセス許可が必要です。  

## <a name="can-i-go-back-to-using-the-former-portal"></a>以前のポータルを使用して戻ってみませんか?
何かが機能していない場合、または Microsoft 365 セキュリティ センター ポータルで完了できないものがある場合は、その点について説明します。 リダイレクトに関する問題が発生した場合は、[フィードバックの送信] フォームを使用してお知らせください。

元の Microsoft Defender for Endpoint ポータルに戻すには、次の操作を行います。

1. [](https://security.microsoft.com/) Microsoft 365 セキュリティ センターにグローバル管理者としてサインインするか、Azure Active directory でセキュリティ管理者のアクセス許可を使用してアカウントを使用します。

2. [設定エンドポイント **]**  >  **[全般ポータル]**  >  **リダイレクト**  >  **に移動するか、**[ここでページを開きます](https://security.microsoft.com/preferences2/portal_redirection)。  

3. [自動リダイレクト] 設定を [オフ] に **切り替えます**。

4. メッセージが **表示されたら** 、[&フィードバックを共有する] をクリックします。

この設定は、いつでも再度有効にできます。 

無効にすると、アカウントは security.microsoft.com にルーティングされ、以前のポータル (securitycenter.windows.com または securitycenter.microsoft.com) に再びアクセスできます。 

## <a name="related-information"></a>関連情報
- [Microsoft 365 セキュリティ センターの概要](overview-security-center.md)
- [Microsoft 365 セキュリティ センターのエンドポイント用 Microsoft Defender](microsoft-365-security-center-mde.md)
- [Microsoft は、セキュリティ操作を最新化するために統合された SIEM と XDR を提供します。](https://www.microsoft.com/security/blog/?p=91813) 
- [XDR と SIEM のインフォグラフィック](https://afrait.com/blog/xdr-versus-siem/) 
- [新しい Defender](https://afrait.com/blog/the-new-defender/) 
- [Microsoft 365 Defender について](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender) 
- [Microsoft セキュリティ ポータルと管理センター](portals.md)