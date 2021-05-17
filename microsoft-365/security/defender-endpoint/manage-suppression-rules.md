---
title: エンドポイント抑制ルールの Microsoft Defender の管理
description: 抑制ルールを使用して、ポータルにアラートが表示されるのを防ぐ必要がある場合があります。 Microsoft Defender for Endpoint で抑制ルールを管理する方法について説明します。
keywords: 抑制、ルール、ルール名、スコープ、アクション、アラートの管理、オン、オフ
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
ms.openlocfilehash: f1549512a02fe3af71d32c6b33c69cc705de99a8
ms.sourcegitcommit: 22505ce322f68a2d0ce70d71caf3b0a657fa838a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2021
ms.locfileid: "51862129"
---
# <a name="manage-suppression-rules"></a>抑制ルールの管理

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


ポータルへのアラートの表示を抑制する必要がある場合があります。 組織内の既知のツールやプロセスなど、無実と知られている特定のアラートに対して抑制ルールを作成できます。 アラートを抑制する方法の詳細については、「アラートを抑制する」 [を参照してください](manage-alerts.md)。

すべての抑制ルールの一覧を表示し、1 か所で管理できます。 アラート抑制ルールをオンまたはオフに切り替えできます。


1. ナビゲーション ウィンドウで、[アラートの抑制]**設定**  >  **選択します**。 組織内のユーザーが作成した抑制ルールの一覧が表示されます。

2. ルール名の横にあるチェック ボックスをクリックして、ルールを選択します。

3. [ルール **を有効にする]** **、[ルールの編集]**、または [  **ルールの削除] をクリックします**。 ルールに変更を加える場合、これらのアラートが新しい条件と一致するかどうかに関係なく、既に抑制されているアラートを解放できます。 


## <a name="view-details-of-a-suppression-rule"></a>抑制ルールの詳細を表示する

1. ナビゲーション ウィンドウで、[アラートの抑制]**設定**  >  **選択します**。 組織内のユーザーが作成した抑制ルールの一覧が表示されます。

2. ルール名をクリックします。 ルールの詳細が表示されます。 ルールが作成された状態、スコープ、アクション、一致するアラートの数、作成日時などのルールの詳細が表示されます。 関連付けられたアラートとルールの条件を表示することもできます。

## <a name="related-topics"></a>関連項目

- [アラートの管理](manage-alerts.md)
