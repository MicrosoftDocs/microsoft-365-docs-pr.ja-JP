---
title: サイトとファイルをゲスト ユーザーと共有する
f1.keywords: NOCSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 89502322-bfbb-43d6-9207-4030f8ce26e0
ROBOTS: NOINDEX
description: '組織外のユーザーとサイトやファイルを共有する方法を説明します。 '
ms.openlocfilehash: 95698a36fe56d2c0d1a842425541e8aa7627d7dd
ms.sourcegitcommit: d4604e333507c6f57d5bf327531a241b649052de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/31/2021
ms.locfileid: "51470931"
---
# <a name="share-sites-and-files-with-guest-users"></a>サイトとファイルをゲスト ユーザーと共有する

組織外のユーザーと共同作業するために、サイト全体または特定のファイルを外部で共有できます。 共有を直接セットアップする場合は、有効にするシナリオを選択します。

- [ゲストと共同でドキュメントの作業をする](../../solutions/collaborate-on-documents.md)
- [サイトでゲストと共同で作業する](../../solutions/collaborate-in-site.md)
- [チームでゲストと共同で作業する](../../solutions/collaborate-as-team.md)
  
## <a name="deciding-how-to-share-your-content"></a>コンテンツの共有方法の決定

コンテンツを外部と共有するかどうか、そしてどのように共有を有効にするかを検討している場合には、次のことを考えます。
  
- だれにサイトとそのサブサイトのコンテンツへのアクセス許可を与えるか、そしてそのユーザーたちが何をできるようにしたいのか。
    
- 組織内のだれに外部とコンテンツを共有する権限を与えるか? 
    
- 組織外の人々には決して閲覧されてはいけないコンテンツがあるかどうか。
    
これらの質問への回答は、コンテンツ共有への戦略を立案するのに役立つはずです。
  
|**次の操作を試してください。**|**目的**|
|:-----|:-----|
|グループにゲストを追加する  <br/> |チーム サイト上の情報とコンテンツへの継続的なアクセスを組織外のだれかに提供する。 これらの人々は、サイトの正式ユーザーのように実行し、コンテンツを作成、編集、表示する必要がある。  <br/> |
|ドキュメントを共有し、ゲストに認証を要求する。  <br/> |確認または共同作業のために、組織外の特定のユーザーにドキュメントへの安全なアクセスを提供する。これらのユーザーはサイトの他のコンテンツにアクセスを行う必要はない。  <br/> |
|ドキュメントを共有するが、認証を要求しない。  <br/> |機密でも極秘でもないドキュメントへのリンクを組織外の人々と共有し、これを表示したり、フィードバックで更新したりできるようにする。 これらのユーザーは、サイト上のコンテンツへのアクセスを必要としない。  <br/> |
   
> [!IMPORTANT]
> 外部共有を無効にすると、現在アクセスできる組織外のユーザーはアクセスできなくなります。 後で外部共有を再び有効にすると、これらのユーザーがアクセスできるようになります。 ユーザーが共有コンテンツにアクセスするのを防ぐには [、Microsoft 365](/office365/admin/create-groups/add-or-remove-members-from-groups)グループから共有コンテンツを削除するか、サイトからアクセス許可を削除するか、ファイルまたはフォルダーの共有を [停止します](https://support.microsoft.com/office/0a36470f-d7fe-40a0-bd74-0ac6c1e13323)。 
  
## <a name="enable-external-sharing-at-the-organization-level"></a>組織レベルで外部共有を有効にする

外部共有は組織レベルで既定で有効になっていますが、すべての新しいサイトで有効ではありません。 詳細については、「[外部共有の概要](/sharepoint/external-sharing-overview)」を参照してください。 

> [!NOTE]
>  任意のサイトで外部共有を許可するには、組織レベルでそれを許可する必要があります。 
  
1. [管理センター](https://go.microsoft.com/fwlink/p/?linkid=2024339)で、[ホーム] ページの検索ボックスに「外部」と入力し、[**サイトの外部共有**] を選択します。
  
2. 開いたページで、ユーザーが共有できる相手を、既存のゲストのみ、新規および既存のゲスト、またはすべてのユーザーの中から選択します。 
    
3. [**保存**] を選択します。
    
組織レベルで外部共有を有効にした後、特定のサイトの外部共有を無効にするように共有設定を微調整できます。 詳細については、「[サイトの外部共有を有効または無効にする](/sharepoint/change-external-sharing-site)」を参照してください。
  

  

