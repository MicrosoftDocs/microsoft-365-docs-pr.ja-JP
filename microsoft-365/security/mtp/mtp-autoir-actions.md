---
title: 自動調査後に保留中のアクションを承認または拒否する
description: アクション センターを使用して、自動調査と応答に関連するアクションを管理する
keywords: アクション、センター、autoair、自動、調査、応答、修復
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.date: 12/09/2020
ms.openlocfilehash: b34f4a532571d6215500ab2bec022489fd462d0f
ms.sourcegitcommit: 29eb89b8ba0628fbef350e8995d2c38369a4ffa2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "49683369"
---
# <a name="approve-or-reject-pending-actions-following-an-automated-investigation"></a>自動調査後に保留中のアクションを承認または拒否する

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**適用対象:**
- Microsoft 365 Defender

自動調査が実行されたときに、調査を続行するには承認を必要とする 1 つまたは複数の[修復](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-remediation-actions)アクションが発生する場合があります。 たとえば、一連のメール メッセージを削除する必要がある場合や、検疫されたファイルを削除する必要がある場合があります。 自動調査を続行し適時完了できるよう、保留中のアクションはできるだけ早く承認 (または拒否) することが重要です。 

> [!TIP]
> Microsoft 365 Defender の自動調査および対応機能によって何かが見逃された、または誤って検出されたと思う場合は、お知らせします。 [Microsoft 365 Defender](mtp-autoir-report-false-positives-negatives.md)の自動調査および対応 (AIR) 機能で誤検知/陰性を報告する方法をご覧ください。

保留中のアクションは、アクション センターまたは調査の詳細ビュー[](#review-a-pending-action-in-the-action-center)を使用して確認[および承認できます](#review-a-pending-action-in-the-investigation-details-view)。

> [!NOTE]
> 修復アクションを承認または拒否するには、[適切なアクセス許可](mtp-action-center.md#required-permissions-for-action-center-tasks)が必要です。 詳しくは、Microsoft 365 Defender での自動調査と対応の [前提条件に関するページをご覧ください](mtp-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender)。

## <a name="review-a-pending-action-in-the-action-center"></a>保留中のアクションをアクション センターで確認する

1. [https://security.microsoft.com](https://security.microsoft.com) にアクセスし、サインインします。 

2. ナビゲーション ウィンドウで、[**アクション センター**] を選択します。 

3. アクション センターの [**Pending (保留中)**] タブで、リスト内のアイテムを選択します。 

    - [**Investigation number (調査番号)**] 列でアイテムを選択すると、[Investigation details (調査の詳細)] ページが開きます。 このページでは、調査の結果を表示し、推奨されるアクションを承認または拒否できます。
 
    - リスト内の行を選択すると、ポップアップが開き、そのアイテムに関する情報が表示されます。 <br/>![アクションを承認または拒否する](../../media/air-actioncenter-itemselected.png)<br/>リンクを使用して関連付けられている警告または調査を表示し、アクションを承認または拒否します。

## <a name="review-a-pending-action-in-the-investigation-details-view"></a>保留中のアクションを調査の詳細ビューで確認する

![調査の詳細](../../media/mtp-air-investdetails.png)

1. [[Investigation details (調査の詳細)](mtp-autoir-results.md)] ページで、[**Pending actions (保留中のアクション)**] (または [**Actions (アクション)**]) タブを選択します。承認待ちのアイテムがそこに表示されます。

2. リスト内のアイテムを選択し、[**Approve (承認)**] または [**Reject (拒否)**] を選択します。

## <a name="next-steps"></a>次のステップ

- [自動調査の詳細と結果を表示する](mtp-autoir-results.md)
- [自動調査および対応機能で誤検知/陰性を処理する](mtp-autoir-report-false-positives-negatives.md)
