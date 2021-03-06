---
title: 脅威エクスプローラーのビューとリアルタイム検出
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 05/15/2020
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: 脅威エクスプローラーとリアルタイム検出レポートを使用して、Defender ポータルで脅威を調査して対応するMicrosoft 365します。
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1c79cc717a2dbe345627f99830590c674fa02f09
ms.sourcegitcommit: 3d30ec03628870a22c54b6ec5d865cbe94f34245
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2021
ms.locfileid: "52929637"
---
# <a name="views-in-threat-explorer-and-real-time-detections"></a>脅威エクスプローラーのビューとリアルタイム検出

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**適用対象**
- [Microsoft Defender for Office 365 プラン 1 およびプラン 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)


![脅威エクスプローラー](../../media/explorer.png)

[Threat Explorer](threat-explorer.md) (およびリアルタイム検出レポート) は、セキュリティ運用チームが Microsoft 365 Defender ポータルの脅威を調査して対応するのに役立つ、リアルタイムに近い強力なツールです。 エクスプローラー (およびリアルタイム検出レポート) には、Office 365 の電子メールやファイルのマルウェアやフィッシングの疑いについての情報、および組織に対するその他のセキュリティ上の脅威やリスクが表示されます。

- Microsoft Defender for [Office 365](defender-for-office-365.md)プラン 2, you have Explorer.
- Microsoft Defender for Office 365プラン 1 の場合は、リアルタイムの検出があります。

エクスプローラー (またはリアルタイム検出レポート) を初めて開いた場合、既定のビューには過去 7 日間のメール マルウェア検出が表示されます。 このレポートには、セーフ リンクで検出された悪意のある URL や、セーフ[添付](safe-links.md)ファイルによって検出された悪意のあるファイルなど、Microsoft Office 365 Defender による検出セーフ[表示することもできます](safe-attachments.md)。 このレポートは、過去 30 日間のデータを表示Office 365できます。 試用版サブスクリプションには、過去 7 日間のデータだけが含まれます。

****

|サブスクリプション|ユーティリティ|データの日数|
|---|---|---|
|Microsoft Defender for Office 365 P1 試用版|リアルタイムの検出|7|
|Microsoft Defender for Office 365 P1 有料|リアルタイムの検出|30|
|Microsoft Defender for Office 365 P1 有料テスト Defender for Office 365 P2 試用版|脅威エクスプローラー|7|
|Microsoft Defender for Office 365 P2 試用版|脅威エクスプローラー|7|
|Microsoft Defender for Office 365 P2 paid|脅威エクスプローラー|30|
|

> [!NOTE]
> 間もなく、試用版テナントのエクスプローラー (およびリアルタイム検出) のデータ保持と検索の制限を 7 日から 30 日間に延長します。 この変更は、ロードマップ 項目 No. 70544 の一部として追跡され、現在ロールアウト段階にあります。

表示する情報 **を** 変更するには、[表示] メニューを使用します。 ツールヒントは、使用するビューを決定するのに役立ちます。

![[脅威エクスプローラーの表示] メニュー](../../media/all-email.png)

ビューを選択したら、フィルターを適用してクエリを設定して、さらに分析を実行できます。 以下のセクションでは、エクスプローラーで使用できるさまざまなビュー (またはリアルタイム検出) の概要を示します。

## <a name="email--malware"></a>メール >マルウェア

このレポートを表示するには、エクスプローラー (またはリアルタイムの検出) で、[電子メール マルウェアの表示 **]** \> **を** \> **選択します**。 このビューには、マルウェアが含まれていると識別された電子メール メッセージに関する情報が表示されます。

![マルウェアとして識別された電子メールに関するデータを表示する](../../media/detection-technology.png)

[送信者 **] を** クリックして、表示オプションの一覧を開きます。 この一覧を使用して、送信者、受信者、送信者ドメイン、件名、検出テクノロジ、保護状態などによってデータを表示します。

たとえば、検出された電子メール メッセージに対して実行されたアクションを確認するには、一覧で [ **保護の状態** ] を選択します。 オプションを選択し、[更新] ボタンをクリックして、そのフィルターをレポートに適用します。

![脅威エクスプローラーの脅威保護の状態オプション](../../media/ThreatExplorerProtectionStatusOptions.png)

グラフの下に、特定のメッセージの詳細を表示します。 リストでアイテムを選択すると、フライアウト ウィンドウが開き、選択したアイテムの詳細を確認できます。

![飛び出しが開いた脅威エクスプローラー](../../media/ThreatExplorerMalwareItemSelectedFlyout.png)

## <a name="email--phish"></a>メール >フィッシング

このレポートを表示するには、エクスプローラー (またはリアルタイムの検出) で、[メール フィッシング **の表示]** \> **を** \> **選択します**。 このビューには、フィッシング詐欺の試みとして識別された電子メール メッセージが表示されます。

![フィッシング詐欺の試みとして識別された電子メールに関するデータを表示する](../../media/phish.png)

[送信者 **] を** クリックして、表示オプションの一覧を開きます。 この一覧を使用して、送信者、受信者、送信者ドメイン、送信者 IP、URL ドメイン、クリックの評決などによってデータを表示します。

たとえば、フィッシング詐欺の試みとして識別された URL をクリックしたユーザーが実行したアクションを確認するには、リストで [Click **verdict]** を選択し、1 つ以上のオプションを選択し、[更新] ボタンをクリックします。

![[フィッシング] レポートの [評決オプション] をクリックします。](../../media/click-verdict.png)

グラフの下に、特定のメッセージ、URL クリック、URL、メール配信元の詳細を表示します。

![電子メール メッセージでフィッシングとして検出された URL](../../media/ThreatExplorerEmailPhishURLs.png)

リスト内のアイテム (検出された URL など) を選択すると、フライアウト ウィンドウが開き、選択したアイテムの詳細を確認できます。

![検出された URL の詳細](../../media/ThreatExplorerEmailPhishURLDetails.png)

## <a name="email--submissions"></a>メール>提出

このレポートを表示するには、エクスプローラー (またはリアルタイムの検出) で、[電子メール送信の表示 **]** \>  \> **を選択します**。 このビューには、ユーザーが迷惑メール、迷惑メール、フィッシングメールとして報告したメールが表示されます。

![ユーザーによって報告された電子メール メッセージ](../../media/ThreatExplorerEmailUserReportedViewOptions.png)

[送信者 **] を** クリックして、表示オプションの一覧を開きます。 この一覧を使用して、送信者、受信者、レポートの種類 (電子メールが迷惑メール、迷惑メール、フィッシングではないというユーザーの判断) などによって情報を表示します。

たとえば、フィッシング詐欺の試みとして報告された電子メール メッセージに関する情報を表示するには、[送信者レポートの種類] をクリックし、[フィッシング] を選択し、[更新] ボタン \> をクリックします。 

![[レポートの種類] フィルターで選択されているフィッシング](../../media/ThreatExplorerEmailUserReportedPhishSelected.png)

グラフの下に、件名、送信者の IP アドレス、迷惑メール、迷惑メール、フィッシングなど、メッセージを報告したユーザーなど、特定の電子メール メッセージの詳細を表示します。

![フィッシング詐欺の試みとして報告されたメッセージ](../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png)

リスト内のアイテムを選択して、追加の詳細を表示します。

## <a name="email--all-email"></a>メール > すべてのメール

このレポートを表示するには、エクスプローラーで[メールのすべて表示 \> **]** \> **を選択します**。 このビューには、フィッシングやマルウェアによる悪意のあると識別されたメールや、悪意のあるメール以外のすべてのメール (通常のメール、スパム、バルク メール) など、電子メールアクティビティのオールアップ ビューが表示されます。

> [!NOTE]
> [表示するデータが多すぎます **]** というエラーが表示された場合は、フィルターを追加し、必要に応じて表示する日付範囲を絞り込みます。

フィルターを適用するには、[送信者] **を** 選択し、一覧でアイテムを選択し、[更新] ボタンをクリックします。 この例では、検出テクノロジ **を** フィルターとして使用しました (使用可能なオプションは複数あります)。 送信者、送信者のドメイン、受信者、件名、添付ファイル名、マルウェア ファミリ、保護状態 (Office 365 の脅威保護機能とポリシーによって実行されるアクション)、検出テクノロジ (マルウェアの検出方法)などによって情報を表示します。

![検出テクノロジによって検出された電子メールに関するデータを表示する](../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png)

グラフの下には、件名、受信者、送信者、状態など、特定の電子メール メッセージの詳細が表示されます。

## <a name="content--malware"></a>コンテンツ >マルウェア

このレポートを表示するには、エクスプローラー (またはリアルタイムの検出) で、[コンテンツ マルウェアの表示 **]** \> **を** \> **選択します**。 このビューには[、Microsoft Defender](mdo-for-spo-odb-and-teams.md)によって、オンライン、Office 365、OneDrive for Business、およびSharePointの悪意のあるファイルがMicrosoft Teams。

マルウェア ファミリ、検出テクノロジ (マルウェアの検出方法)、ワークロード (OneDrive、SharePoint、またはTeams)。

![検出されたマルウェアに関するデータを表示する](../../media/malware-family.png)

グラフの下には、添付ファイルのファイル名、ワークロード、ファイル サイズ、ファイルを最後に変更したユーザーなど、特定のファイルの詳細が表示されます。

## <a name="click-to-filter-capabilities"></a>クリックからフィルターへの機能

エクスプローラー (およびリアルタイム検出) を使用すると、クリックでフィルターを適用できます。 凡例内のアイテムをクリックすると、そのアイテムがレポートのフィルターになります。 たとえば、エクスプローラーでマルウェア ビューを見ているとします。

![[脅威管理エクスプローラー] に \> 移動します。](../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png)

このグラフ **で [ATP の削除]** をクリックすると、次のようなビューが表示されます。

![エクスプローラーがフィルター処理され、削除結果の Defender Office 365表示されます。](../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png)

このビューでは、添付ファイルによって削除されたファイルのデータをセーフ[しています](safe-attachments.md)。 グラフの下には、添付ファイルが添付ファイルで検出された特定の電子メール メッセージに関する詳細セーフ表示されます。

![検出された添付ファイルを含む電子メール メッセージに関する具体的な詳細](../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png)

1 つ以上のアイテムを選択すると、[アクション] メニューがアクティブ化され、選択したアイテムに対して選択できる複数の選択肢があります。

![アイテムを選択すると、[操作] メニューがアクティブ化されます。](../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png)

クリックでフィルター処理して特定の詳細に移動する機能によって、脅威の調査に多くの時間を節約できます。

## <a name="queries-and-filters"></a>クエリとフィルター

エクスプローラー (リアルタイム検出レポートと同様に) には、いくつかの強力なフィルターとクエリ機能が備え付け、上位の対象ユーザー、トップ マルウェア ファミリ、検出テクノロジなど、詳細を掘り下ろします。 レポートの種類ごとに、さまざまな方法でデータを表示および探索できます。

> [!IMPORTANT]
> Explorer のクエリ バー (またはリアルタイムの検出) では、アスタリスクや疑問符などのワイルドカード文字を使用しません。 [件名] フィールドで電子メール メッセージを検索すると、エクスプローラー (またはリアルタイム検出) は部分的な照合を実行し、ワイルドカード検索と同様の結果を生成します。
