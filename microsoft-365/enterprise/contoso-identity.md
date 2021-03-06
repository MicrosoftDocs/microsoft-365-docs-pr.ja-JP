---
title: Contoso 社の ID
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Contoso 社で、IDaaS (Identity as a Service) を活用して、従業員向けのクラウド ベース認証や、パートナーと顧客向けのフェデレーション認証を提供している方法を説明します。
ms.openlocfilehash: f3c8746345683652ce601400ae7297e96fff2ee3
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51051522"
---
# <a name="identity-for-the-contoso-corporation"></a>Contoso 社の ID

Microsoft は、Azure Active Directory (Azure Active Directory) を通じてクラウド サービス全体で Identity as a Service (IDaaS) をAD。 Microsoft 365 for enterprise を採用するには、Contoso IDaaS ソリューションでオンプレミス ID プロバイダーを使用し、既存の信頼できるサード パーティ ID プロバイダーとのフェデレーション認証を含める必要がありました。

## <a name="the-contoso-active-directory-domain-services-forest"></a>Contoso Active Directory ドメイン サービス フォレスト

Contoso は、7 つのサブドメインを持つ contoso com の単一の Active Directory ドメイン サービス (DS) フォレスト (AD DS) を使用します。1 つは世界の各地域に \. 1 つです。 本社、地域ハブ オフィス、サテライト オフィスには、ローカルの認証と承認のためのドメイン コントローラーが含まれています。

地域ハブを含む世界の各地域の地域ドメインを持つ Contoso フォレストを次に示します。

![Contoso 社の世界中のフォレストとドメイン](../media/contoso-identity/contoso-identity-fig1.png)
 
Contoso 社は、Microsoft 365 ワークロードとサービスの認証と承認に contoso com フォレスト内のアカウントとグループ \. を使用することを決定しました。

## <a name="the-contoso-federated-authentication-infrastructure"></a>Contoso フェデレーション認証インフラストラクチャ

Contoso 社では次のことが可能です。

- お客様は、Microsoft、Facebook、または Google メール アカウントを使用して、会社のパブリック Web サイトにサインインします。
- ベンダーとパートナーは、LinkedIn、Salesforce、または Google メール アカウントを使用して、会社のパートナーエクストラネットにサインインします。

パブリック Web サイト、パートナー エクストラネット、および Active Directory フェデレーション サービス (FS) サーバーのセットを含む Contoso DMZ をADします。 DMZ は、顧客、パートナー、およびインターネット サービスを含むインターネットに接続されています。

![顧客とパートナーのフェデレーション認証に対する Contoso のサポート](../media/contoso-identity/contoso-identity-fig2.png)
 
AD FS サーバーを使用すると、パブリック Web サイトにアクセスするための ID プロバイダーによる顧客資格情報の認証と、パートナーエクストラネットへのアクセスのためのパートナー資格情報の認証が容易になります。

Contoso 社は、このインフラストラクチャを維持し、顧客とパートナー認証に使用することを決定しました。 Contoso 社の ID アーキテクトは、このインフラストラクチャから Azure AD [B2B](/azure/active-directory/b2b/hybrid-organizations) および [B2C](/azure/active-directory-b2c/solution-articles) ソリューションへの変換を調査しています。

## <a name="hybrid-identity-with-password-hash-synchronization-for-cloud-based-authentication"></a>クラウドベース認証のためのパスワードハッシュ同期によるハイブリッドID

Contoso 社は、Microsoft 365 クラウド リソースADにオンプレミスの DS フォレストを使用したいと考えた。 パスワード ハッシュ同期 (PHS) の使用を決定しました。

PHS は、エンタープライズ サブスクリプションの Microsoft 365 の Azure AD テナントとオンプレミスの AD DS フォレストを同期し、ユーザー アカウントとグループ アカウント、およびハッシュ化されたバージョンのユーザー アカウント パスワードをコピーします。

ディレクトリ同期を行うには、Contoso 社は Azure AD Connect ツールをパリ データセンター内のサーバーに展開しました。

Azure AD Connect を実行しているサーバーは、Contoso AD DS フォレストをポーリングして変更を Azure AD テナントと同期します。

![Contoso PHS ディレクトリ同期インフラストラクチャ](../media/contoso-identity/contoso-identity-fig4.png)
 
## <a name="conditional-access-policies-for-identity-and-device-access"></a>ID およびデバイス アクセスの条件付きアクセス ポリシー

Contosoは、3 つの保護レベルに対して Azure AD と Intune の[条件付きアクセス ポリシー](../security/defender-365-security/identity-access-policies.md)セットを作成しました。

- *ベースライン* 保護は、すべてのユーザー アカウントに適用されます。
- *機密性の* 高い保護は、上級リーダーシップとエグゼクティブ スタッフに適用されます。
- *規制の厳* しい保護は、規制の厳しいデータにアクセスできる財務部門、法務部門、研究部門の特定のユーザーに適用されます。

Contoso ID ポリシーとデバイス条件付きアクセス ポリシーのセットを次に示します。

![Contoso 社の ID およびデバイスの条件付きアクセス ポリシー](../media/contoso-identity/contoso-identity-fig5.png)
 
## <a name="next-step"></a>次の手順

Contoso 社が Microsoft Endpoint Configuration Manager インフラストラクチャを使用して、組織全体に [現在の Windows 10 Enterprise](contoso-win10.md) を展開して維持する方法について説明します。

## <a name="see-also"></a>関連項目

[Microsoft 365 の ID ロードマップ](identity-roadmap-microsoft-365.md)

[Microsoft 365 for enterprise の概要](microsoft-365-overview.md)

[テスト ラボ ガイド](m365-enterprise-test-lab-guides.md)