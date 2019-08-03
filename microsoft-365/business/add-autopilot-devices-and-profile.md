---
title: ステップ バイ ステップ ガイドを使用して、Autopilot デバイスとプロファイルを追加する
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.collection:
- M365-subscription-management
- M365-identity-device-management
localization_priority: Normal
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: be5b6d90-3344-4c5e-bf40-5733eb845beb
description: Windows AutoPilotを使用して、ビジネス用に新しい Windows 10 デバイスをセットアップする方法について説明します。
ms.openlocfilehash: 9a70978156fb26ac3aad08f1758b7ee125067d38
ms.sourcegitcommit: 66bb5af851947078872a4d31d3246e69f7dd42bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34072152"
---
# <a name="use-the-step-by-step-guide-to-add-autopilot-devices-and-profile"></a>ステップ バイ ステップ ガイドを使用して、Autopilot デバイスとプロファイルを追加する

Windows AutoPilotを使用して、従業員に提供されるとすぐに生産性を高めることができるように、自社の**新しい**windows 10 デバイスをセットアップすることができます。
  
## <a name="device-requirements"></a>デバイスの要件

デバイスは次の要件を満たしている必要があります。
  
- Windows 10 バージョン 1703 以降。
    
- Windows out-of-box experience を行っていない新しいデバイス。
    
## <a name="use-the-setup-guide-to-create-devices-and-profiles"></a>セットアップ ガイドを使用して、デバイスとプロファイルを作成する

![をhttps://aka.ms/aboutM365preview指すバナー。](media/m365admincenterchanging.png)

まだ作成したデバイス グループまたはプロファイルがない場合は、ステップ バイ ステップ ガイドを使用して開始するのが最適な方法ですが、ガイドを使用せずに、[デバイスを追加](create-and-edit-autopilot-devices.md)して[プロファイルを割り当てる](create-and-edit-autopilot-profiles.md)こともできます。 
  
1. の管理センターに移動<a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>します。

2. 左側のナビゲーションで、[**デバイス** \>の**AutoPilot**] を選択します。

    ![管理センターで、[デバイス] を選択し、[AutoPilot] をクリックします。](media/AutoPilot.png)
  
2. [**AutoPilot**] ページで、[**スタートガイド**] をクリックまたはタップします。
    
    ![Click Start guide for step-by-step instructions for Autopilot.](media/31662655-d1e6-437d-87ea-c0dec5da56f7.png)
  
3. On the **Upload .csv file with list of devices** page, browse to a locations where you have the prepared .CSV file, then **Open** \> **Next**. The file should have three headers:
    
  - 列 A:デバイスのシリアル番号
    
  - 列 B:Windows 製品 ID
    
  - 列 C:ハードウェア ハッシュ
    
    この情報は、ハードウェアの製造元から、または CSV ファイルを生成する [Get-WindowsAutoPilotInfo PowerShell スクリプト](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo)を使って、入手できます。 
    
    詳細については、[デバイスの一覧の CSV ファイル](https://support.office.com/article/932e3676-2491-49f0-9177-d893d2f5276e)を参照してください。また、[ **デバイスの一覧を含む .csv ファイルのアップロード**] ページでサンプル ファイルをダウンロードすることもできます。 
    
4. [ **プロファイルの割り当て**] ページで、既存のプロファイルを選択するか、新しいプロファイルを作成します。まだプロファイルがない場合は、新しく作成するように求めるメッセージが表示されます。 
    
    プロファイルは、1 つのデバイスまたはデバイスのグループに適用できる設定のコレクションです。
    
    既定の機能は必須であり、自動的に設定されます。既定の機能は次のとおりです。
    
  - Cortana、OneDrive、および OEM の登録はスキップされます。
    
  - 会社のブランドを含む、サインイン エクスペリエンスを作成します。
    
  - 使用しているデバイスは、Azure Active Directory アカウントに接続され、Microsoft 365 Business で管理されるように自動的に登録されます。
    
    詳しくは、
    
    「[AutoPilot プロファイルの設定について](autopilot-profile-settings.md)」をご覧ください。 
    
5. 他の設定には、[ **プライバシーの設定をスキップする**] や [ **ユーザーがローカルの管理者になることを許可しない**] があります。既定では、両方が [ **オフ**] に設定されます。 
    
    [ **次へ**] を選びます。
    
6. [ **完了しました**] ページでは、作成 (または選択) したプロファイルが、デバイスの一覧をアップロードして作成したデバイス グループに適用されることを示しています。デバイスのユーザーが次にサインインすると、これらの設定が有効になります。[ **閉じる**] を選びます。
    
