---
title: Microsoft Defender for Endpoint でアラート通知を構成する
description: Microsoft Defender for Endpoint を使用すると、重大度や他の条件に基づいて、セキュリティアラートの電子メール通知設定を構成できます。
keywords: 電子メール通知、アラート通知の構成、Microsoft Defender atp 通知、Microsoft Defender atp アラート、Windows 10 enterprise、Windows 10 Education
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d8b68e6b6dc42de5730aa634386406d4762b1fa2
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51163685"
---
# <a name="configure-alert-notifications-in-microsoft-defender-atp"></a>Microsoft Defender ATP でアラート通知を構成する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-emailconfig-abovefoldlink)

Defender for Endpoint を構成して、新しい通知のために指定した受信者に電子メール通知を送信できます。 この機能を使用すると、直ちに通知を受け取り、重大度に基づいてアラートに基づいて行動できる個人のグループを識別できます。

> [!NOTE]
> [セキュリティ設定の管理] 権限を持つユーザーだけが電子メール通知を構成できます。 基本的なアクセス許可管理の使用を選択した場合、セキュリティ管理者またはグローバル管理者の役割を持つユーザーは、電子メール通知を構成できます。

通知をトリガーするアラートの重大度レベルを設定できます。 電子メール通知の受信者を追加または削除できます。 新しい受信者は、追加後に発生したアラートに関する通知を受け取る。 アラートの詳細については、「アラート キューの [表示と整理」を参照してください](alerts-queue.md)。

役割ベースのアクセス制御 (RBAC) を使用している場合、受信者は通知ルールで構成されたデバイス グループに基づく通知のみを受信します。
適切なアクセス許可を持つユーザーは、デバイス グループ管理スコープに限定された通知のみを作成、編集、または削除できます。
グローバル管理者ロールに割り当てられたユーザーだけが、すべてのデバイス グループに対して構成されている通知ルールを管理できます。

電子メール通知には、アラートに関する基本情報と、さらに調査を行うポータルへのリンクが含まれています。


## <a name="create-rules-for-alert-notifications"></a>アラート通知のルールを作成する
電子メール通知を送信するデバイスとアラートの重大度と通知受信者を決定するルールを作成できます。


1. ナビゲーション ウィンドウで、[設定アラート通知 **]**  >  **を選択します**。

2. [通知 **ルールの追加] をクリックします**。

3. [全般] 情報を指定します。
    - **ルール名** - 通知ルールの名前を指定します。
    - **[組織名を含** める] - 電子メール通知に表示される顧客名を指定します。
    - **[テナント固有のポータル リンクを含める** ] - 特定のテナントへのアクセスを許可するテナント ID を含むリンクを追加します。
    - **[デバイス情報を含** める] - 電子メール通知本文にデバイス名を含める。
    
        >[!NOTE]
        > この情報は、Defender for Endpoint データで選択した地理的な場所ではない受信者メール サーバーによって処理される場合があります。

    - **[デバイス** ] - すべてのデバイス (グローバル管理者の役割のみ) または選択したデバイス グループの通知を受信者に通知するかどうかを選択します。 詳細については、「デバイス グループの作成 [と管理」を参照してください](machine-groups.md)。
    - **アラートの重大度** - アラートの重大度レベルを選択します。

4. **[次へ]** をクリックします。
    
5. 受信者のメール アドレスを入力し、[受信者の追加] **をクリックします**。 複数のメール アドレスを追加することができます。

6. [テストメールの送信] を選択して、電子メール受信者が電子メール通知を **受信できると確認します**。

7. [通知 **ルールの保存] をクリックします**。

## <a name="edit-a-notification-rule"></a>通知ルールの編集
1. 編集する通知ルールを選択します。

2. [全般] タブと [受信者] タブ情報を更新します。

3. [通知 **ルールの保存] をクリックします**。


## <a name="delete-notification-rule"></a>通知ルールの削除

1. 削除する通知ルールを選択します。

2. **[削除]** をクリックします。


## <a name="troubleshoot-email-notifications-for-alerts"></a>アラートの電子メール通知のトラブルシューティング
このセクションでは、アラートに電子メール通知を使用するときに発生する可能性があるさまざまな問題の一覧を示します。

**問題:** 対象の受信者は、通知を取得していないと報告します。

**ソリューション:** 通知がメール フィルターによってブロックされないのを確認します。

1. Defender for Endpoint の電子メール通知が迷惑メール フォルダーに送信されないか確認します。 [迷惑メールではない] としてマークします。
2. メール セキュリティ製品が Defender for Endpoint からの電子メール通知をブロックしていないか確認します。
3. Defender for Endpoint の電子メール通知をキャッチして移動する可能性がある電子メール アプリケーションルールを確認します。

## <a name="related-topics"></a>関連項目
- [データ保持設定の更新](data-retention-settings.md)
- [高度な機能を構成する](advanced-features.md)
