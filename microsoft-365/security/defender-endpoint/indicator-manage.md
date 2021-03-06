---
title: インジケーターの管理
ms.reviewer: ''
description: エンティティの検出、防止、除外を定義するファイル ハッシュ、IP アドレス、URL、またはドメインのインジケーターを管理します。
keywords: インポート、インジケーター、リスト、ioc、csv、manage、許可、ブロック、ブロック、クリーン、悪意のある、ファイル ハッシュ、IP アドレス、URL、ドメイン
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
ms.openlocfilehash: 9fd36f63450335247bf57c4cc1f98d6f0d32a9d5
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51185947"
---
# <a name="manage-indicators"></a>インジケーターの管理

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


>Defender for Endpoint を体験してみませんか? [無料試用版にサインアップしてください。](https://www.microsoft.com/en-us/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)


1. ナビゲーション ウィンドウで、[インジケーター]**を設定**  >  **します**。

2. 管理するエンティティの種類のタブを選択します。  

3. インジケーターの詳細を更新し、[保存]**を** クリックするか、一覧からエンティティを削除する場合は [削除] ボタンをクリックします。

## <a name="import-a-list-of-iocs"></a>IoC のリストのインポート

また、インジケーターの属性、実行するアクション、その他の詳細を定義する CSV ファイルをアップロードすることもできます。

サポートされている列属性を知るサンプル CSV をダウンロードします。

1. ナビゲーション ウィンドウで、[インジケーター]**を設定**  >  **します**。

2. インジケーターをインポートするエンティティの種類のタブを選択します。

3. [インポート **] [ファイル**  >  **の選択] を選択します**。 

4. **[インポート]** を選択します。 インポートするファイルすべてについて、この操作を行います。 

5. **[完了]** を選択します。

次の表に、サポートされているパラメーターを示します。

パラメーター | 型    |   説明
:---|:---|:---
indicatorType | 列挙 | インジケーターの種類。 指定できる値は、"FileSha1"、"FileSha256"、"IpAddress"、"DomainName" および "Url" です。 **Required**
indicatorValue | String | Indicator エンティティ [の](ti-indicator.md) ID。 **Required**
action | 列挙 | インジケーターが組織内で検出される場合に実行されるアクション。 指定できる値は、"Alert"、"AlertAndBlock"、"Allowed" です。 **Required**
title | String | インジケーターアラートのタイトル。 **Required**
説明 | String |  インジケーターの説明。 **Required**
expirationTime | DateTimeOffset | 次の形式の YYYYY-MM-DDTHH:MM:SS.0Z のインジケーターの有効期限。 **Optional**
severity | 列挙 | インジケーターの重大度。 指定できる値は、"Informational"、"Low"、"Medium"、"High" です。 **Optional**
recommendedActions | String | TI インジケーターアラート推奨アクション。 **Optional**
rbacGroupNames | String | インジケーターが適用される RBAC グループ名のコンマ区切りのリスト。 **Optional**
category | String | アラートのカテゴリ。 例として、実行アクセスと資格情報アクセスが含まれます。 **Optional**
mitretechniques| String | MITRE の手法 code/id (コンマ区切り)。 詳細については[、「Enterprise」を参照してください](https://attack.mitre.org/tactics/enterprise/)。 **省略可能** MITRE 手法を使用する場合は、カテゴリに値を追加する必要があります。

詳細については [、「Microsoft Defender for Endpoint alert categories are aligned with MITRE ATT&CK! 」を参照してください](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-atp-alert-categories-are-now-aligned-with/ba-p/732748)。


## <a name="see-also"></a>関連項目
- [インジケーターの作成](manage-indicators.md)
- [ファイルのインジケーターを作成 ](indicator-file.md)
- [IP および URL/ドメインのインジケーターを作成](indicator-ip-domain.md)
- [証明書に基づいてインジケーターを作成する](indicator-certificates.md)
