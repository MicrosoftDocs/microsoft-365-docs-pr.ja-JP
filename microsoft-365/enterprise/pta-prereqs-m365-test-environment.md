---
title: Microsoft 365 テスト環境のパススルー認証に必要な ID およびデバイス アクセスの前提条件
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
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: パススルー認証用の前提条件で ID とデバイスのアクセスをテストするための Microsoft 365 環境を作成します。
ms.openlocfilehash: f257b85672a1a1b27f600d145b1f9f3296b21980
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "51199851"
---
# <a name="identity-and-device-access-prerequisites-for-pass-through-authentication-in-your-microsoft-365-test-environment"></a>Microsoft 365 テスト環境のパススルー認証に必要な ID およびデバイス アクセスの前提条件

*このテスト ラボ ガイドは、エンタープライズ テスト環境の Microsoft 365 でのみ使用できます。*

[ID およびデバイス](../security/office-365-security/microsoft-365-policies-configurations.md) アクセス構成は、Azure Active Directory (Azure Active Directory )と統合されたエンタープライズ向け Microsoft 365 のすべてのサービスへのアクセスを保護するための一連の構成と条件付きアクセス ポリシーです。AD。

この記事では、ID とデバイス アクセス用の[パススルー認証の前提条件構成](../security/office-365-security/identity-access-prerequisites.md#prerequisites)に関する要件を満たす Microsoft 365 テスト環境を構成する方法を説明します。

このテスト環境をセットアップするには、10 のフェーズがあります。

1. パススルー認証を実装するシミュレーション エンタープライズ Microsoft 365 テスト環境を構築する
2. Azure AD シームレス シングル サインオンを構成する
3. 名前付きの場所を構成する
4. パスワード ライトバックを構成する
5. セルフサービスのパスワードのリセットを構成する
6. 多要素認証を構成する
7. ドメインに参加している Windows コンピューターのデバイスの自動登録を有効にする
8. Azure ADパスワード保護を構成する 
9. Azure AD Identity Protection を有効化する
10. Exchange Online および Skype for Business Online に対して先進認証を有効化する

## <a name="phase-1-build-out-your-simulated-enterprise-with-pass-through-authentication-microsoft-365-test-environment"></a>フェーズ 1: パススルー認証を実装するシミュレーション エンタープライズ Microsoft 365 テスト環境を構築する

「[パススルー認証](pass-through-auth-m365-ent-test-environment.md)」の手順に従います。

最終的な構成は、次のようになります。

![パススルー認証を実装するシミュレーション エンタープライズ テスト環境](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
 
## <a name="phase-2-configure-azure-ad-seamless-single-sign-on"></a>フェーズ 2: Azure AD シームレス シングル サインオンを構成する

[テスト ラボ ガイドの「Azure AD シームレス シングル サインオン」のフェーズ 2](single-sign-on-m365-ent-test-environment.md#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso) に説明されている手順に従います。

## <a name="phase-3-configure-named-locations"></a>フェーズ 3: 名前付きの場所を構成する

最初に、組織で使用されているパブリック IP アドレスまたはアドレス範囲を確認します。

次に、「[Azure Active Directory で名前付きの場所を構成する](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations)」の手順に従って、アドレスまたはアドレス範囲を名前付きの場所として追加します。 

## <a name="phase-4-configure-password-writeback"></a>フェーズ 4: パスワード ライトバックを構成する

[テスト ラボ ガイドの「パスワード ライトバック」のフェーズ 2](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain) に説明されている手順に従います。

## <a name="phase-5-configure-self-service-password-reset"></a>フェーズ 5: セルフサービスのパスワードのリセットを構成する

次に、テスト ラボ ガイドの[「パスワードのリセット」のフェーズ 3](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset) に説明されている手順に従います。 

特定の Azure AD グループに含まれるアカウントのパスワード リセットを有効にする場合は、それらのアカウントを **パスワードのリセット** グループに追加します。

- ユーザー 2
- ユーザー 3
- ユーザー 4
- ユーザー 5

User 2 アカウントのパスワードのリセットのみテストします。

## <a name="phase-6-configure-multi-factor-authentication"></a>フェーズ 6: 多要素認証を構成する

次のユーザー アカウントについて、[テスト ラボ ガイドの「多要素認証」のフェーズ 2](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) に説明されている手順に従います。

- ユーザー 2
- ユーザー 3
- ユーザー 4
- ユーザー 5

User 2 アカウントの多要素認証のみテストします。

## <a name="phase-7-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>フェーズ 7: ドメインに参加している Windows コンピューターのデバイスの自動登録を有効にする 

ドメイン [に参加している Windows コンピューター](/azure/active-directory/devices/hybrid-azuread-join-plan) のデバイスの自動登録を有効にするには、次の手順に従います。

## <a name="phase-8-configure-azure-ad-password-protection"></a>フェーズ 8: Azure のパスワード保護AD構成する 

既知 [の脆弱なパスワードとその](/azure/active-directory/authentication/concept-password-ban-bad) バリアントをブロックするには、次の手順に従います。

## <a name="phase-9-enable-azure-ad-identity-protection"></a>フェーズ 9: Azure AD ID 保護を有効にする

[テスト ラボ ガイドの「Azure AD Identity Protection」のフェーズ 2](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection) に説明されている手順に従います。 

## <a name="phase-10-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>フェーズ 10: Exchange Online と Skype for Business Online のモダン認証を有効にする

Exchange Online については、[こちら](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online#enable-or-disable-modern-authentication-in-exchange-online-for-client-connections-in-outlook-2013-or-later)で説明されている手順に従います。 

Skype for Business Online については、

1. [Skype for Business Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell) に接続します。

2. 次のコマンドを実行します。

  ```powershell
  Set-CsOAuthConfiguration -ClientAdalAuthOverride Allowed
  ```

3. 次のコマンドを使用して、変更が成功したことを確認します。

  ```powershell
  Get-CsOAuthConfiguration
  ```

上述の手順により、ID とデバイス アクセス用の[パススルー認証の前提条件構成](../security/office-365-security/identity-access-prerequisites.md#prerequisites)に関する要件を満たすテスト環境が作成されます。 

## <a name="next-step"></a>次の手順

[共通 ID とデバイスのアクセス ポリシー](../security/office-365-security/identity-access-policies.md)を使用して、前提条件に基づいて構築し ID とデバイスを保護するポリシーを構成します。

## <a name="see-also"></a>関連項目

[その他の ID のテスト ラボ ガイド](m365-enterprise-test-lab-guides.md#identity)

[ID ロードマップ](identity-roadmap-microsoft-365.md)

[Microsoft 365 Enterprise のテスト ラボ ガイド](m365-enterprise-test-lab-guides.md)

[Microsoft 365 for enterprise の概要](microsoft-365-overview.md)

[Microsoft 365 for enterprise のドキュメント](/microsoft-365-enterprise/)
