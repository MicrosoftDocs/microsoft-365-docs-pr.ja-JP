---
title: Microsoft から別のホストにドメインを転送する
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
description: 'Microsoft から別のレジストラーにドメインを転送する手順については、こちらを参照してください。 '
ms.openlocfilehash: f34e9733ab53c8bdc6f4432c96e6232ecc26ee06
ms.sourcegitcommit: eac5d9f759f290d3c51cafaf335a1a1c43ded927
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "50126349"
---
# <a name="transfer-a-domain-from-microsoft-to-another-host"></a>Microsoft から別のホストにドメインを転送する

Microsoft からドメインを購入Microsoft 365 60 日間、別のレジストラーにドメインを転送できない。

> [!NOTE]
> Whois _クエリは_、Microsoft が購入したドメイン レジストラー   をワイルド ウェスト ドメイン LLC として表示します。 ただし、購入したドメインに関して Microsoft Microsoft 365する必要があります。

次の手順に従って、Microsoft 365 でコードを取得し、他のドメイン レジストラー Web サイトに移動して、ドメイン名を新しいレジストラーに転送する設定を行います。

## <a name="transfer-a-domain"></a>ドメインの転送

1. 管理センターで、[ドメイン] に   **移動設定**   >  **します**。

2. [ドメイン **] ページ** で、別Microsoft 365に転送するドメインを選択し、[正常性の確認]**を選択します**。

3. ページの上部で、[ドメインの転送] **を選択します**。

4. [ドメインの **転送先の選択] ページで** 、[ **別のレジスト** ラー] を選択し、[次へ] を **クリックします**。

5. [ドメイン転送 **のロック解除] ページ** で、[ドメインのロック解除 **_<]_ >** を選択し、[次へ] を **選択します**。

6. ドメイン転送の連絡先情報を確認し、[次へ] を **選択します**。

7. 認証コードをコピーし、ドメイン転送の状態が [登録] タブの **[転送** のロック解除済み] に変わるまで約 30 分待機してから、次の手順に進みます。

8. 今後ドメイン名を管理するドメイン レジストラーの Web サイトに移動します。 ドメインを転送するための指示に従います (Web サイトでヘルプを検索します)。 これは通常、転送手数料を支払い、新しいレジストラーに Authcode を渡して、転送を開始できるという意味です。 Microsoft から転送要求を受け取ったことを確認するメールが送信され、ドメインは 5 日以内に転送されます。

    認証コードの [登録] タブ **は**、[ドメイン] ページの [ **ドメイン]** Microsoft 365。
    
    > [!TIP]
    > .uk ドメインでは、別の手順が必要です。 Microsoft サポートに連絡して、今後ドメインを管理するレジストラーと一致するように **IPS Tag タグを変更** を依頼します。 タグを変更すると、ドメインは直ちに新しいレジストラーに移動します。 転送を完了するには、新しいレジストラーでするべきことがあります。移転手数料を支払って、新しいレジストラーで転送されたドメインをアカウントに追加する必要があります。

9. 移行の完了後は、新しいドメイン レジストラーでドメインの更新を実行します。

10. プロセスを完了するには、管理センターの **[ドメイン** ] ページに戻り、[ドメイン転送の完了]  **を選択します**。 これにより、ドメインはドメインから購入されなくなったMicrosoft 365し、ドメイン サブスクリプションを無効にします。 テナントからドメインは削除されません。また、ドメイン上の既存のユーザーとメールボックスには影響を与えかねない。

> [!NOTE]
> Microsoft 365ドメインは、ネームサーバーの変更や組織間でのドメインの転送Microsoft 365されません。 これらのどちらかが必要な場合は、ドメイン登録を別のレジストラーに転送する必要があります。
