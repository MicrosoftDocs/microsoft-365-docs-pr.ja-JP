---
title: Microsoft 365 Business を使い始める
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: 496e690b-b75d-4ff5-bf34-cc32905d0364
description: Microsoft 365 Business をセットアップする方法について説明します。
ms.openlocfilehash: 78f7360c80667b8d34fad9d849cfc2cf83a8577b
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "32278111"
---
# <a name="get-started-with-microsoft-365-business"></a>Microsoft 365 Business を使い始める

## <a name="what-is-microsoft-365-business"></a>Microsoft 365 Business とは

Microsoft 365 Business は、ビジネス生産性と共同作業ツールの包括的なセットです。これには、常に最新の状態に保たれた Outlook、Word、Excel、およびその他の Office 製品が含まれます。iOS、Android、Windows 10 のすべてのデバイス上の作業ファイルを、管理が容易なエンタープライズ レベルのセキュリティで保護することができます。
  
microsoft 365 Business は最大300ライセンスを想定しており、さらにライセンスが必要な場合は、「 [microsoft 365 Enterprise](https://go.microsoft.com/fwlink/p/?linkid=860986)ドキュメント」を参照してください。 
  
## <a name="get-microsoft-365-business"></a>Microsoft 365 Business を入手する

- パートナーがいる場合、パートナーは Microsoft 365 Business を入手します: [Microsoft パートナー センターから Microsoft 365 Business を購入する](get-microsoft-365-business.md)。
    
- パートナーを持っておらず、Microsoft 365 Business を入手したい場合は、[ここで購入](https://www.microsoft.com/en-us/microsoft-365/business)できます。
    
## <a name="set-up-microsoft-365-business"></a>Microsoft 365 Business をセットアップする

 **Microsoft 365 Business Suite のセットアップの概要**
  
次の図では、管理者が Microsoft 365 Business をセットアップする方法について説明します。 また、Microsoft 365 Business 用に Windows pc を準備する手順についても説明します。 また、 [Windows AutoPilot](add-autopilot-devices-and-profile.md)を使用して、Microsoft 365 Business 管理センターで新しいデバイスを追加することもできます。 AutoPilotを使用して、新しいデバイスをセットアップして事前構成し、ユーザーが Microsoft 365 のビジネス資格情報を使用してサインインするとすぐに生産性を向上させることができます。
  
![A diagram that shows the setup and management flow for admins, and also for a user](media/249f81fc-7e79-44c7-8425-3a0b7b651c3b.png)
  
### <a name="1-set-up-microsoft-365-business-admin"></a>1: Microsoft 365 Business をセットアップする (管理者)

グローバル管理者の資格情報で [Microsoft 365 Business 管理センター](https://portal.office.com/adminportal/home)にサインインし、次の手順を完了して Microsoft 365 Business をセットアップします。 
  
1. [Microsoft 365 Business でデバイス上のデータを保護するための前提条件](pre-requisites-for-data-protection.md)
    
    最初に前提条件を読み、デバイスが Microsoft 365 Business の前提条件を満たしていることを確認します。
    
2. [セットアップ ウィザードを使用して Microsoft 365 Business をセットアップする](set-up.md)
    
    **ローカルの Active Directory からクラウドに完全に移動**する場合は、セットアップウィザードを使用して、Microsoft 365 Business 管理センターで手動でユーザーを追加するか、Azure AD Connect との1回限りの同期を行うことができます。 これを行うには 2 つの方法があります。 
    
  - exchange 2010、exchange 2013、または exchange 2016 サーバーもある場合は、最小限の[ハイブリッドを使用して、exchange メールボックスを Office 365 にすばやく移行](https://support.office.com/article/fdecceed-0702-4af3-85be-f2a0013937ef)できます。 最低限のハイブリッドの手順には、ユーザーの Azure AD への 1 回限りの同期と、オンプレミスからクラウドへのメールの移行が含まれます。 この方法を使用すると、メールの移行が完了すると、ディレクトリ同期が自動的にオフになります。
    
  - Office 365 のディレクトリ同期のウィザードを使用して、ユーザーをクラウドに同期させます。「[Office 365 のディレクトリ同期をセットアップする](https://support.office.com/article/1b3b5318-6977-42ed-b5c7-96fa74b08846)」の手順に従って、このプロセスを完了します。ユーザーをクラウドに同期させた後で、[ディレクトリの同期をオフにする](https://support.office.com/article/ee5f861e-bd48-4267-83d1-a4ead4b4a00d)必要があります。
    
    また、このように追加された各ユーザーには、Microsoft 365 Business のライセンスを付与する必要があります。 これは[セットアップウィザード](set-up.md)、または[Office 365 for business のユーザーにライセンスを割り当てる](https://support.office.com/article/997596B5-4173-4627-B915-36ABAC6786DC)ことができます。
    
### <a name="2-prepare-mobile-devices"></a>2: モバイルデバイスの準備

「[microsoft 365 business ユーザー向けのモバイルデバイスのセットアップ](set-up-mobile-devices.md)」の手順に従って、Office アプリをデバイスにインストールし、microsoft 365 business で保護されていることを確認します。 
  
### <a name="3-prepare-pcs"></a>3: pc の準備

管理者は、 [windows AutoPilot](add-autopilot-devices-and-profile.md)を使用して、新しいデバイスの windows 10 pc の設定を事前に選択できます。 ユーザーは、このトピックの手順に従って、既存または新しい windows 10 デバイスをセットアップできます。 [Microsoft 365 Business ユーザーの windows pc をセットアップ](set-up-windows-devices.md)します。 既存のデバイスでは、ユーザーは**オプション**で[ファイルを OneDrive for business に移動](move-files-to-onedrive.md)することもできます。 サードパーティ製のツールを使用して、Windows プロファイルに関連付けられているファイルを OneDrive に移動することもできます。
  
組織がオンプレミスの windows Server Active Directory を使用している場合は、windows 10 のデバイスを保護するように Microsoft 365 Business をセットアップし、ローカル認証を必要とするオンプレミスのリソースへのアクセスを維持することができます。 「[ドメインに参加している Windows 10 デバイスが Microsoft 365 Business で管理される](manage-windows-devices.md)ようにする」の手順に従って、これを設定します。 この方法は推奨されており、この状態のデバイスは**ハイブリッド Azure AD 参加デバイス**と呼ばれます。 
  
オンプレミスのリソース (ファイル共有やプリンターなど) が含まれているローカルの Active Directory を保持する場合は、以下の手順に従って、 **Azure AD に参加**しているデバイスにこれらのリソースへのアクセスを許可できます。 [Microsoft 365 Business の Azure AD に参加しているデバイス](access-resources.md)。
  
Windows 10 pc をセットアップした後、Office をデバイスに[自動的にインストール](auto-install-or-uninstall-office.md)することができます。 
  
## <a name="contact-support"></a>サポートに連絡

 **サポートに連絡する場合:**
  
- パートナーにお問い合わせください。
    
- Microsoft 365 business 管理者は、カスタマーサポートチームへのアクセス権を持ち、 **[ビジネス製品のサポートに問い合わせる-管理者ヘルプ](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)**
    
## <a name="related-topics"></a>関連トピック
[Microsoft 365 Business のドキュメントとリソース](https://go.microsoft.com/fwlink/p/?linkid=853701)
  
[Microsoft 365 Business を管理](manage.md)する[Microsoft 365 Business への移行](migrate-to-microsoft-365-business.md)
  

