---
title: セットアップの概要
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_M365SetupBanner
- BCS365_M365SetupBanner
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: 6e7a2dfd-8ec4-4eb7-8390-3ee103e5fece
description: Microsoft 365 Business のセットアップ手順の概要について説明します。
ms.openlocfilehash: efa4d352b00ebba0cb9754c93e773d1ddaef19df
ms.sourcegitcommit: 720881c1a9c5f708e1b4adf7e5ea4ff8da48ea99
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "33970454"
---
# <a name="overview-of-setup"></a>セットアップの概要

セットアップ手順のほとんどはセットアップウィザードで行うことができますが、その他のオプションも表示されます。


## <a name="step-1-add-your-domain-and-users"></a>手順 1: ドメインとユーザーを追加する

   - **[ドメインを追加する](set-up.md#add-your-domain-to-personalize-sign-in)**([サインアップ](sign-up.md)中にドメインを購入した場合、この手順は既に完了しています。)

    - **ユーザーを追加**します。 これは、次の3つの方法のいずれかで行うことができます。
        - [ウィザード](set-up.md#add-users-in-the-wizard)で。
        - オンプレミスの Active directory を使用している場合は、ディレクトリ同期を使用して、 [AZURE AD Connect を使用してユーザーを追加](https://docs.microsoft.com/office365/enterprise/set-up-directory-synchronization)します。
        - 後で管理センターで[ユーザーを追加](add-users-m365b.md)することもできます。
## <a name="step-2-set-up-security-policies-and-configure-devices"></a>手順 2: セキュリティポリシーを設定し、デバイスを構成する 

  - [セットアップウィザード](set-up.md#set-up-security-policies-and-device-configurations)を使用して、デバイスとセキュリティのポリシーを構成します。 
  - また、後で[管理センター](view-policies-and-devices.md)および[Intune ポータル](https://docs.microsoft.com/intune/tutorial-walkthrough-intune-portal)で追加または編集することもできます。
  - セットアップウィザードのセキュリティ設定に加えて、次の設定を追加することによって、セキュリティを向上させることができます。

      - **メールマルウェア対策**
      - **Advanced Threat Protection (ATP) の安全なリンク**
      - **ATP の安全な添付ファイル機能**
      - **ATP のフィッシング対策**
      - **Exchange Online Archiving**
      - **データ損失防止 (DLP)**
      - **Azure Information Protection (Plan1**)

          開始するには、「 [advanced security policies をセットアップ](set-up-advanced-security.md)する」を参照してください。

        セキュリティに関するベストプラクティスのロードマップについては[、Microsoft 365 Business をセキュリティで保護するための10のトップの方法](https://docs.microsoft.com/office365/admin/security-and-compliance/secure-your-business-data)も参照してください。

## <a name="step-3-set-up-and-manage-windows-10-devices"></a>手順 3: Windows 10 デバイスをセットアップおよび管理する

   Windows 10 デバイスを Azure AD に参加させると、[手順 2](#step-2-set-up-security-policies-and-configure-devices)で設定したポリシーが適用されます。

   - Windows 10 Pro は Microsoft 365 Business の[前提条件](pre-requisites-for-data-protection.md)ですが、Windows 7 Pro、Windows 8 pro、または Windows 8.1 Pro を使用している場合は、サブスクリプションによって[windows 10 pro へのアップグレード](https://docs.microsoft.com/microsoft-365/business/upgrade-to-windows-pro-creators-update)ができます。
    - [セットアップウィザード](set-up.md#set-up-security-policies-and-device-configurations)を使用して、Windows 10 デバイスのポリシーを構成します。

## <a name="stes-4-install-office-365-business"></a>Stes 4: Office 365 Business をインストールする
- [セットアップウィザード](set-up.md#deploy-office-365-client-apps)を使用して、Windows デバイスに Office を自動的にインストールすることができます。
- 管理センターから Office を自動的に[インストール](auto-install-or-uninstall-office.md)します。
- ユーザーが Windows およびデバイス用の[Office アプリをインストール](https://docs.microsoft.com/office365/admin/setup/install-applications)できるようにします。
     
## <a name="advanced"></a>詳細情報
- **AutoPilotを使用して新しいデバイスをセットアップする**
            
     [Windows AutoPilot](add-autopilot-devices-and-profile.md)を使用して、ユーザーに対して**新しい**windows 10 デバイスを自動的に事前構成することができますが、これを実行できる[パートナー](https://www.microsoft.com/solution-providers/search)を取得する方が簡単な場合があります。 [Microsoft ストア](https://go.microsoft.com/fwlink/?linkid=874598)に移動して、クラウドテクノロジエキスパートに購入した新しいデバイスのセットアップを依頼することもできます。

- **オンプレミスのリソースにアクセスする**

     - 組織がオンプレミスの Windows Server Active Directory を使用している場合は、Windows 10 のデバイスを保護するように Microsoft 365 Business をセットアップし、ローカル認証を必要とするオンプレミスのリソースへのアクセスを維持することができます。 「[ドメインに参加している Windows 10 デバイスが Microsoft 365 Business で管理される](manage-windows-devices.md)ようにする」の手順に従って、これを設定します。 この方法は推奨されており、この状態のデバイスはハイブリッド Azure AD 参加デバイスと呼ばれます。

    - オンプレミスのリソース (ファイル共有やプリンターなど) を含むローカルな Active Directory が企業にある場合は、次の手順に従って、Azure AD に参加しているデバイスにこれらのリソースへのアクセス権を付与できます。 [Microsoft 365 Business の Azure AD に参加しているデバイス](access-resources.md)。

  
