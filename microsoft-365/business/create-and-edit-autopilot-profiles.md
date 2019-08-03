---
title: AutoPilot プロファイルの作成と編集
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5cf7139e-cfa1-4765-8aad-001af1c74faa
description: 'AutoPilot プロファイルを作成、編集、削除、または削除する方法について説明します。 '
ms.openlocfilehash: 7987cafb3ea234d81be72c79aee8e584a3770875
ms.sourcegitcommit: 66bb5af851947078872a4d31d3246e69f7dd42bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34073492"
---
# <a name="create-and-edit-autopilot-profiles"></a>AutoPilot プロファイルの作成と編集

## <a name="create-a-profile"></a>プロファイルの作成

プロファイルがデバイスまたはデバイスのグループに割り当てられます。
  
1. Microsoft 365 Business 管理センターで、[**デバイス** \> **AutoPilot**] を選択します。
  
2. [**AutoPilot**] ページで、 **** [プロファイル\> ] タブを選択して**プロファイルを作成**します。
    
3. [ **プロファイルの作成**] ページで、識別に役立つプロファイルの名前を入力します。たとえば、マーケティングでは、必要な設定をオンにして (詳細については、「[AutoPilot プロファイルの設定について](autopilot-profile-settings.md)」を参照)、[ **保存**] を選びます。
    
    ![Enter name and turn on settings in the Create profile panel.](media/63b5a00d-6a5d-48d0-9557-e7531e80702a.png)
  
### <a name="apply-profile-to-a-device"></a>プロファイルをデバイスに適用する

プロファイルを作成した後、デバイスまたはデバイスのグループに適用することができます。[ステップ バイ ステップ ガイド](add-autopilot-devices-and-profile.md)で既存のプロファイルを選んだり、プロファイルを新しいデバイスに適用したり、デバイスまたはデバイスのグループの既存のプロファイルを置き換えたりすることができます。 
  
1. [ **Windows の準備**] ページで、[ **デバイス**] タブを選びます。 
    
2. Click the check-box next to a device name and in the **Device** panel, choose a profile from the **Assigned profile** drop-down \> **Save**.
    
    ![In the Device panel, select an Assigned profile to apply it.](media/ed0ce33f-9241-4403-a5de-2dddffdc6fb9.png)
  
## <a name="edit-delete-or-remove-a-profile"></a>プロファイルの編集または削除

デバイスにプロファイルを割り当てると、そのデバイスを既にユーザーに渡していても、そのプロファイルを更新できます。デバイスをインターネットに接続すると、セットアップ プロセス中に最新バージョンのプロファイルをダウンロードします。ユーザーがデバイスを出荷時の既定の設定にリセットする場合は、デバイスはもう一度プロファイルに最新の更新プログラムをダウンロードします。 
  
### <a name="edit-a-profile"></a>プロファイルを編集する

1. [ **Windows の準備**] ページで、[ **プロファイル**] タブを選びます。 
    
2. Click the check-box next to a device name and in the **Profile** panel update any of the available settings \> **Save**.
    
    ユーザーがデバイスをインターネットに接続する前にこの操作を行った場合、プロファイルはセットアップ プロセスに適用されます。
    
### <a name="delete-a-profile"></a>プロファイルを削除する

1. [ **Windows の準備**] ページで、[ **プロファイル**] タブを選びます。 
    
2. Click the check-box next to a device name and in the **Profile** panel click **Delete profile** \> **Save**.
    
    プロファイルを削除すると、プロファイルが割り当てられていたデバイスまたはデバイスのグループから削除されます。
    
### <a name="remove-a-profile"></a>プロフィールを削除する

1. [ **Windows の準備**] ページで、[ **デバイス**] タブを選びます。 
    
2. Click the check-box next to a device name and in the **Device** panel, choose a **None** from the **Assigned profile** drop-down \> **Save**.
    
