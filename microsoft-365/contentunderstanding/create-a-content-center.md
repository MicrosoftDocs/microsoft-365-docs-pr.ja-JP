---
title: Microsoft SharePoint Syntexでコンテンツセンターを作成する
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
localization_priority: Priority
description: コンテンツセンターを作成する方法を説明します。
ms.openlocfilehash: 34ba45cd62214743e5a6784893e0f24e9815fdfb
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "50905826"
---
# <a name="create-a-content-center-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntexでコンテンツセンターを作成する


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CPSF]

</br>

ドキュメント理解モデルを作成および管理するには、まずコンテンツ センターが必要です。 コンテンツ センターはモデル作成インターフェイスであり、公開されたモデルが適用されたドキュメント ライブラリに関する情報も含まれています。</br>

   ![ドキュメントライブラリを選択する](../media/content-understanding/content-center-page.png)</br>

[セットアップ](set-up-content-understanding.md)中に既定のコンテンツ センターを作成します。 ただし、SharePoint 管理者は、必要に応じて追加のセンターを作成することもできます。 すべてのモデル アクティビティをロールアップする環境では単一のコンテンツ センターで十分な場合もありますが、組織内の複数の部門に追加のセンターを用意することもできます。これらの部門では、モデルのニーズと権限要件が異なる場合があります。

> [!NOTE]
> [Microsoft 365 Multi-Geo 環境](../enterprise/microsoft-365-multi-geo.md)では、中央の場所に単一の既定のコンテンツ センターがある場合、その場所内からのみモデル アクティビティのロールアップを提供できます。 現在、Multi-Geo 環境のファーム境界を越えてモデル アクティビティのロールアップを取得することはできません。 


## <a name="create-a-content-center"></a>コンテンツ センターを作成する

SharePoint 管理者は、管理センター サイトプ ロビジョニング パネルを介して[他のSharePoint サイトを作成する](/sharepoint/create-site-collection)のと同じように、コンテンツ センター サイトを作成できます。

新しいコンテンツ センターを作成するには

1. Microsoft 365 管理センターで、SharePoint 管理センターに移動します。

2. SharePoint 管理センターの [**サイト**] で、[**アクティブなサイト**] を選択します。

3. [**アクティブなサイト**] ページで、[**作成**] をクリックし、[**その他のオプション**] を選択します。

4. [**テンプレートの選択**] メニューで、[**コンテンツセンター**] を選択します。

5. 新しいサイトの場合は、**サイト名**、**プライマリ管理者**、および **言語** を指定します。</br>

   > [!NOTE] 
   > コンテンツ センター サイトを選択して、使用可能な任意の言語で表示できますが、現在、モデルは英語のファイルに対してのみ作成できることに注意してください。 また、他のサイト テンプレートと同様に、サイトの作成後に既定のサイトの言語を編集できないことにも注意してください。</br>

6. [**完了**] を選択します。
 
コンテンツセンターサイトを作成すると、SharePoint 管理センターの [**アクティブなサイト**] ページに一覧表示されます。 

### <a name="give-access-to-additional-users"></a>追加のユーザーにアクセスを許可する
 
サイトを作成した後、標準の [SharePoint サイト アクセス許可モデル](/sharepoint/modern-experience-sharing-permissions)を使用して、追加のユーザーにサイトへのアクセスを許可できます。

## <a name="see-also"></a>関連項目
[分類子を作成する](create-a-classifier.md)

[抽出子を作成する](create-an-extractor.md)

[コンテンツ センターを作成する](create-a-content-center.md)

[ドキュメント理解の概要](document-understanding-overview.md)

[フォーム処理モデルを作成する](create-a-form-processing-model.md)

[モデルを適用する](apply-a-model.md)