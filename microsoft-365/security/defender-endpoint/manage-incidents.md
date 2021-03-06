---
title: エンドポイント インシデントの Microsoft Defender の管理
description: インシデントの割り当て、状態の更新、または分類の設定によってインシデントを管理します。
keywords: インシデント、管理、割り当て、状態、分類、真のアラート、誤ったアラート
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
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c86b53abf54788740c8c78cb0ecf9251b10ea8f7
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2021
ms.locfileid: "52842340"
---
# <a name="manage-microsoft-defender-for-endpoint-incidents"></a>エンドポイント インシデントの Microsoft Defender の管理

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

インシデントの管理は、すべてのサイバーセキュリティ操作の重要な部分です。 インシデントを管理するには、[インシデント] キューまたは [インシデント管理] ウィンドウからインシデント **を選択します**。 


インシデント キューからインシデントを選択すると、[インシデント管理]ウィンドウが表示されます。インシデントの詳細については、インシデント ページを開きます。


![インシデント管理ウィンドウのイメージ](images/atp-incidents-mgt-pane-updated.png)

インシデントを自分に割り当て、ステータスと分類を変更したり、名前を変更したり、コメントを付け、進捗状況を追跡することができます。

> [!TIP]
> 一目で見たインシデント名は、影響を受けるエンドポイントの数、影響を受けるユーザー、検出元、カテゴリなどのアラート属性に基づいて自動的に生成されます。 これにより、インシデントの範囲をすばやく理解できます。
>
> たとえば、複数 *のソースによって報告された複数のエンドポイントに対するマルチステージ インシデント。*
>
> 自動インシデント名前付けのロールアウトの前に存在していたインシデントは、その名前を保持します。
>


![インシデントの詳細ページの画像](images/atp-incident-details-updated.png)

## <a name="assign-incidents"></a>インシデントを割り当てる
インシデントがまだ割り当てられていない場合は、[自分に割り当てる] を選択して、インシデントを自分に割り当てることができます。 これにより、インシデントの所有権だけでなくそのインシデントと関連するすべての警告の所有権が自分に割り当てられます。

## <a name="set-status-and-classification"></a>状態と分類を設定する
### <a name="incident-status"></a>インシデントの状態
インシデントは、調査の進捗に合わせて状態を変更することにより、**Active (アクティブ)** または **Resolved (解決済み)** に分類できます。 こうすることで、チームでのインシデントへの対応方法を整理して管理できます。

たとえば、SoC アナリストは、その日の緊急 **の** アクティブ インシデントを確認し、調査のために自分に割り当てました。

または、インシデントが修復された場合、SoC アナリストがインシデントを **解決** 済みとして設定する場合もあります。 

### <a name="classification"></a>分類
分類を設定しないことも、インシデントが真または偽であると指定することもできます。 こうすることで、チームにはインシデントの傾向が示され、チームの学習につながります。

### <a name="add-comments"></a>コメントを追加する
警告にはコメントを追加することができ、インシデントに関する過去のイベントを表示して、以前に行われた変更を確認できます。

警告に変更またはコメントが加えられるたびに、[Comments and history (コメントと履歴)] セクションに記録されます。

追加されたコメントは直ちにウィンドウに表示されます。



## <a name="related-topics"></a>関連項目
- [インシデント キュー](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [インシデント キューを表示および整理する](view-incidents-queue.md)
- [インシデントの調査](investigate-incidents.md)
