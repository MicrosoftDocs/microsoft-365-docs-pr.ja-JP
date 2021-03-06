---
title: セキュリティとコンプライアンス センター Office 365ユーザーをサーバーにリダイレクトMicrosoft 365 コンプライアンス センター
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.service: O365-seccomp
audience: ITPro
ms.topic: article
localization_priority: Normal
description: セキュリティとコンプライアンス センターのOffice 365ユーザーを自動的にユーザーにリダイレクトする方法Microsoft 365 コンプライアンス センター。。
ms.collection: M365-security-compliance
ms.openlocfilehash: 62fc302f9f065ac7bb0475a6e72dc240a56a1fe1
ms.sourcegitcommit: 0d1b065c94125b495e9886200f7918de3bda40b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/08/2021
ms.locfileid: "53339408"
---
# <a name="redirect-users-from-the-office-365-security-and-compliance-center-to-the-microsoft-365-compliance-center"></a>セキュリティとコンプライアンス センター Office 365ユーザーをサーバーにリダイレクトMicrosoft 365 コンプライアンス センター

この記事では、Office 365 セキュリティ とコンプライアンス センター (protection.office.com) から Microsoft 365 コンプライアンス センター (compliance.microsoft.com) へのコンプライアンス ソリューションにアクセスするユーザーの自動リダイレクトのしくみについて説明します。

## <a name="what-to-expect"></a>想定される変化

自動リダイレクトは、セキュリティとコンプライアンス (Office 365) で次のコンプライアンス関連のソリューションにアクセスしているすべてのユーザーに対して既定 protection.office.com。

- データ損失防止 (DLP)
- 分類
- 情報ガバナンス
- レコード管理
- コミュニケーションコンプライアンス (以前は '監督')

ユーザーは自動的に同じコンプライアンス ソリューションにルーティングされます (Microsoft 365 コンプライアンス センター (compliance.microsoft.com)。

> [!NOTE]
> Office 365 セキュリティとコンプライアンス センターに含まれる他のコンプライアンス ソリューションについては、ユーザーは引き続き Microsoft 365 コンプライアンス センター または Office 365 セキュリティ とコンプライアンス センターでこれらのソリューションを管理します。 これらのコンプライアンス ソリューションの自動リダイレクトは、近日利用可能になります。

この機能と関連付けられたコントロールでは、Microsoft Defender のセキュリティ機能の自動リダイレクトが有効Office 365。 セキュリティ機能のリダイレクトを有効にするには[、「Microsoft Defender](/microsoft-365/security/defender/microsoft-365-security-mdo-redirection)からアカウントをリダイレクトする」を参照Office 365セキュリティ センター Microsoft 365を参照してください。

## <a name="can-i-go-back-to-using-the-former-portal"></a>以前のポータルを使用して戻ってみませんか?

何かが機能していない場合、または Microsoft 365 コンプライアンス センター ポータルで完了できない場合は、すべてのユーザーの自動リダイレクトを一時的に無効にできます。

> [!IMPORTANT]
> このMicrosoft 365 コンプライアンス センターは、セキュリティとコンプライアンス センターで現在管理されているコンプライアンス ソリューションOffice 365管理ポータルです。 すべてのMicrosoft 365コンプライアンス ソリューションは、ユーザーが管理するMicrosoft 365 コンプライアンス センター。 サーバーへのリダイレクトを無効Microsoft 365 コンプライアンス センター短期的な解決策である必要があります。

すべてのユーザーの Office 365 およびコンプライアンス センター (protection.microsoft.com) に切り替えるには、次の手順を実行します。

1. グローバル管理者[としてMicrosoft 365 コンプライアンス センター、](https://compliance.microsoft.com)または Azure Active directory のコンプライアンス管理者のアクセス許可を持つ任意のアカウントを使用して、管理者にサインインします。
2. コンプライアンス センターの **設定**  >  **に移動します**。
3. [自動リダイレクト] 設定を [オフ] に **切り替えます**。
4. メッセージが **表示されたら、[** オフにし、フィードバックを共有する] を選択します。

無効にすると、ユーザーは compliance.microsoft.com にルーティングされ、Office 365 セキュリティ とコンプライアンス センター (protection.microsoft.com) に protection.microsoft.com。 この設定は、グローバル管理者またはコンプライアンス管理者がいつでも再度有効にできます。

## <a name="related-information"></a>関連情報

- [Microsoft 365 コンプライアンス センター概要](/microsoft-365/compliance/microsoft-365-compliance-center)
