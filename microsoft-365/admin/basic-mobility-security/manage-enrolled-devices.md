---
title: モバイル デバイス管理に登録されているデバイスを管理する (Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
search.appverid:
- MET150
description: 基本的なモビリティとセキュリティは、モバイル デバイスのセキュリティ保護と管理に役立ちます。
ms.openlocfilehash: 4ff1c43343e00b7eac7aa38b2d266f163f79e2a7
ms.sourcegitcommit: 72795ec56a7c4db863dcaaff5e9f7c41c653fda8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2021
ms.locfileid: "52023883"
---
# <a name="manage-devices-enrolled-in-mobile-device-management-in-microsoft-365"></a>モバイル デバイス管理に登録されているデバイスを管理する (Microsoft 365

Microsoft 365 用の組み込みのモバイル デバイス管理は、iPhone、iPad、Android、携帯電話など、ユーザーのモバイル デバイスをセキュリティで保護し、管理Windowsします。 最初の手順は、基本モビリティとセキュリティMicrosoft 365にサインインしてセットアップします。 詳細については、「Set [up Basic Mobility and Security 」を参照してください](set-up.md)。

セットアップが行った後、組織内のユーザーがデバイスをサービスに登録する必要があります。 詳細については、「Basic [Mobility and Security を使用してモバイル デバイスを登録する」を参照してください](enroll-your-mobile-device.md)。その後、Basic Mobility and Security を使用して、組織内のデバイスを管理できます。 たとえば、デバイス セキュリティ ポリシーを使用して、電子メール アクセスや他のサービスの制限、デバイス レポートの表示、デバイスのリモート ワイプを行えます。 通常、これらのタスクを実行するには、セキュリティ &コンプライアンス センターに移動します。 詳細については、「コンプライアンス センター Microsoft 365[を参照してください](../../compliance/microsoft-365-compliance-center.md)。

## <a name="device-management-tasks"></a>デバイス管理タスク

デバイス管理パネルにアクセスするには、次の手順を実行します。

1. 管理センターに [移動Microsoft 365します](../../admin/admin-overview/about-the-admin-center.md)。

2. [モバイル デバイスの管理] を検索フィールドに入力し、結果の一覧から [モバイル デバイス **の管理**   ] を選択します。

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="モバイル デバイス管理オプション":::

3. [  **始めましょう] を選択します**。

## <a name="manage-mobile-devices"></a>モバイル デバイスの管理

基本モビリティとセキュリティをセットアップした後、組織内のモバイル デバイスを管理する方法を次に示します。

|**目的**|**説明**|
|:----------------|:------------------------------------------------------------------------------|
|デバイスをワイプする |[デバイスの管理] パネルで、[デバイス名  ****] *を選択* し、[フル ワイプ] を選択してすべての情報を削除するか、デバイス上の組織情報のみを削除する選択的ワイプ     ****   を選択します。 詳細については、「Basic [Mobility and Security でモバイル デバイスをワイプする」を参照してください](wipe-mobile-device.md)。|
|サポートされていないデバイスによる Exchange ActiveSync を使用した Exchange メールへのアクセスをブロックする |[デバイスの管理] パネルで、[ブロック] を  **選択します**。 |
|パスワード要件やセキュリティ設定など、デバイス ポリシーを設定する |[デバイスの管理] パネルで、[**デバイス セキュリティ ポリシーの追加**   >  **+] を選択します**。 詳細については、「Basic [Mobility and Security でデバイス セキュリティ ポリシーを作成する」を参照してください](create-device-security-policies.md)。|
|ブロックされたデバイスの一覧を表示する  |[デバイス管理] パネルの [ビューの  **選択] で、[ブロック**   ]  **を選択します**。 |
|ユーザーまたはユーザーのグループに対して、準拠していない、またはサポートされていないデバイスのブロックを解除する  |デバイスのブロックを解除するには、次のいずれかを選択します。<br/>- ポリシーが適用されているセキュリティ グループからユーザーまたはユーザーを削除します。 [グループ] Microsoft 365に移動>**グループ** 名を選択します。 [メンバー **と管理者の編集] を選択します**。<br/>- ユーザーがメンバーであるセキュリティ グループをデバイス ポリシーから削除します。 [セキュリティ とコンプライアンス & ポリシー>デバイス ****   >  **のセキュリティ ポリシー] に移動します**。 [デバイス ポリシー名] を選択し、[展開の編集]**を**  >  **選択します**。<br/>- デバイス ポリシーのすべての非準拠デバイスのブロックを解除します。 [セキュリティ とコンプライアンス & ポリシー>デバイス ****   >  **のセキュリティ ポリシー] に移動します**。 [デバイス ポリシー名] を選択し、[アクセス要件 **の編集**  >  **] を選択します**。 [アクセス  **とレポート違反を許可する] を選択します**。<br/>- ユーザーまたはユーザーグループの準拠していないデバイスまたはサポートされていないデバイスのブロックを解除するには、「セキュリティ & コンプライアンス センター > **セキュリティ** ポリシー デバイス管理 デバイス アクセス設定の管理」に   >  ****   >  **移動** します。 グループへのアクセスがブロックされるから除外するメンバーを含むセキュリティ グループをMicrosoft 365。 詳細については、「管理センターでセキュリティ グループを作成、編集[、または削除するMicrosoft 365参照してください](../../admin/email/create-edit-or-delete-a-security-group.md)。|
|ユーザーを削除して、デバイスが Basic Mobility and Security によって管理されなくなった |ユーザーを削除するには、Basic Mobility と Security のデバイス管理ポリシーを持つセキュリティ グループを編集します。 詳細については、「管理センターでセキュリティ グループを作成、編集  [、または削除するMicrosoft 365参照してください](../../admin/email/create-edit-or-delete-a-security-group.md)。<br/>すべてのユーザーから基本モビリティとセキュリティをMicrosoft 365、「基本モビリティとセキュリティをオフ[にする」を参照してください](turn-off.md)。|

Live (v14)