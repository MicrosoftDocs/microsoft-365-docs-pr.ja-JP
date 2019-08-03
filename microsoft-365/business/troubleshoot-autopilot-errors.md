---
title: AutoPilot デバイス エラーのトラブルシューティング
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: troubleshooting
f1_keywords:
- ZTDTroubleshootDeviceErrors
- O365E_ZTDTroubleshootDeviceErrors
- BCS365_ZTDTroubleshootDeviceErrors
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 1f468690-530c-47ea-918f-fede24607c53
description: AutoPilot デバイスファイルエラーをトラブルシューティングする方法について説明します。
ms.openlocfilehash: 9d4a47f78c38d8c076f5b3876a36b6bf46eaaaf3
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "32279840"
---
# <a name="troubleshoot-autopilot-device-errors"></a>AutoPilot デバイス エラーのトラブルシューティング

## <a name="device-file-error-messages"></a>デバイスファイルのエラーメッセージ

Microsoft 365 Business でAutoPilot デバイスファイルを処理するときに表示される可能性のあるいくつかのエラーについては、以下の情報を参照してください。 
  
|**エラー コード**|**解決策を実行する**|
|:-----|:-----|
|無効な要求本文  <br/> |このエラーが発生することはまれです。このエラーが表示された場合は、操作を再試行してください。  <br/> |
|デバイスのハードウェアハッシュ値が正しくありません。  <br/> |このエラーが表示される場合は、1つのデバイスのハードウェアハッシュで CSV ファイルに指定した値が正しくないことを意味します。 最初に、値が正しく入力されたことを確認します。 値が正しいと考えられるが、このエラーがまだ発生している場合は、ハードウェアベンダーにお問い合わせください。  <br/> |
|別のテナントに割り当てられたデバイス  <br/> |このエラーが表示される場合は、1つまたは複数のデバイスのシリアル番号またはプロダクトキーで CSV ファイルに指定した値が正しくないことを意味します。 最初に、値が正しく入力されたことを確認します。 値が正しいと考えられるが、このエラーがまだ発生している場合は、ハードウェアベンダーにお問い合わせください。  <br/> |
|CSV ファイルに無効なシリアル番号またはプロダクトキーが含まれています  <br/> |このエラーが表示される場合は、登録するデバイスが他の組織によって既に登録されていることを意味します。 この問題を解決するには、ハードウェアベンダーにお問い合わせください。  <br/> |
|このデバイスはAutoPilotを使用したセットアップではサポートされていません  <br/> | このエラーは、デバイスがAutoPilot展開の要件を満たしていないことを意味します。 デバイスは次の要件を満たしている必要があります。  <br/>  Windows 10 バージョン 1703 以降。  <br/>  Windows out-of-box experience を行っていない新しいデバイス。  <br/> |
|デバイスが見つかりません  <br/> |このエラーは、CSV ファイル内の1つ以上のデバイスが組織に登録されていないことを意味します。 この問題を解決するには、ハードウェアベンダーにお問い合わせください。  <br/> |
   
