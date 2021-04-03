---
title: Microsoft 365 管理センターでセキュリティ グループを作成、編集、削除する
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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 55c96b32-e086-4c9e-948b-a018b44510cb
description: セキュリティ グループの作成、編集、削除について説明します。
ms.openlocfilehash: 03e391727f9a61b1fc8e819e92d5a119017c38e0
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "51579340"
---
# <a name="create-edit-or-delete-a-security-group-in-the-microsoft-365-admin-center"></a>Microsoft 365 管理センターでセキュリティ グループを作成、編集、削除する

[Microsoft 365 **グループ** ] ページで、SharePoint Online と CRM Online で同じアクセス許可を割り当てるのに使用できるユーザー アカウントのグループを作成できます。 たとえば、管理者は、特定のユーザー グループに対して SharePoint サイトへのアクセス権を付与するセキュリティ グループを作成できます。 セキュリティ グループを作成、編集、または削除できるのは、グローバル管理者とユーザー管理の管理者だけです。詳細については、「[管理者ロールの割り当て](../add-users/assign-admin-roles.md)」をご覧ください。 
  
他に、メールの送信やユーザー グループにアクセス許可を割り当てるために使用できる [Exchange Online グループと SharePoint Online グループ](#groups-in-exchange-online-and-sharepoint-online)と、ユーザーに権限を付与し、サイトとサイト コレクションへのアクセスを許可する [Exchange Online グループと SharePoint Online グループ](#groups-in-exchange-online-and-sharepoint-online)があります。 
  
> [!IMPORTANT]
>  サイト メールボックスを使用しますか? 個別ではなくセキュリティ グループを使用して SharePoint に追加されたすべてのユーザーは、SharePoint からのみサイト メールボックスを使用できます。 これらのユーザーは、Outlook からサイト メールボックスにアクセスすることはできません。 詳細については、「サイト メールボックスの [代わりに Microsoft 365 グループを使用する」を参照してください](https://support.microsoft.com/office/737d6b1f-67cc-41fe-8db8-f2d09dd1673b)。 
  
## <a name="manage-security-groups-in-the-admin-center"></a>管理センターでセキュリティ グループを管理する

### <a name="add-a-security-group"></a>セキュリティ グループを追加する

1. Microsoft 365 管理センターで、**[グループ]** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">[グループ]</a> の順に移動します。
  
2. [**グループ**] ページで、[**グループの追加**] を選択します。
    
3. [**グループの種類の選択**] ページで、[**セキュリティ**] を選択します。 
    
4. 手順に従って、グループの作成を完了します。 
 
### <a name="add-members-to-a-security-group"></a>メンバーをセキュリティ グループに追加する

::: moniker range="o365-worldwide"
    
1. [**グループ**] ページでセキュリティ グループ名を選択し、[**メンバー**] タブで [**すべてのメンバーの表示と管理**] を選択します。 
    
2. グループ ウィンドウで、[**メンバーの追加**] を選択し、リストから人を選択するか、[**検索**] ボックスに追加する人の名前を入力して、[**保存**] を選択します。
    
    メンバーを削除するには、そのメンバー名の横にある [X] を選択します。 
  
::: moniker-end

::: moniker range="o365-germany"

1. [**グループ**] ページでセキュリティ グループ名を選択し、[**メンバー**] の横にある [**編集**] を選択します。 
    
2. グループ ウィンドウで、[**メンバーの追加**] を選択し、リストから人を選択するか、[**検索**] ボックスに追加する人の名前を入力して、[**保存**] を選択します。
    
    メンバーを削除するには、そのメンバー名の横にある [X] を選択します。 
  
::: moniker-end

::: moniker range="o365-21vianet"


1. [**グループ**] ページでセキュリティ グループ名を選択し、[**メンバー**] の横にある [**編集**] を選択します。 
    
2. グループ ウィンドウで、[**メンバーの追加**] を選択し、リストから人を選択するか、[**検索**] ボックスに追加する人の名前を入力して、[**保存**] を選択します。
    
    メンバーを削除するには、そのメンバー名の横にある [X] を選択します。

::: moniker-end

### <a name="edit-a-security-group"></a>セキュリティ グループを編集する

::: moniker range="o365-worldwide"

1. 管理センターで、[**グループ**] \> [<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">グループ</a>] ページの順に移動します。
  
2. [**グループ**] ページで、グループ名を選択します。 
    
3. [設定] ウィンドウで、[**全般**] タブまたは [**メンバー**] タブを選択し、グループの詳細またはメンバーを編集します。

::: moniker-end

::: moniker range="o365-germany"

1. 管理センター <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">で、[</a>グループ グループ] **ページ** \> **に移動** します。  
  
2. [**グループ**] ページで、グループ名を選択します。 
    
3. [セキュリティ グループ] ウィンドウで、[**名前**] タブまたは [**メンバー**] タブの横にある [**編集**] を選択し、グループの詳細またはメンバーを編集します。
    
4. 変更が完了したら、[**保存**] \> [**閉じる**] の順に選択します。

::: moniker-end

::: moniker range="o365-21vianet"

1. 管理センター <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">で、[</a>グループ グループ] **ページ** \> **に移動** します。
  
2. [**グループ**] ページで、グループ名を選択します。 
    
3. [セキュリティ グループ] ウィンドウで、[**名前**] タブまたは [**メンバー**] タブの横にある [**編集**] を選択し、グループの詳細またはメンバーを編集します。
    
4. 変更が完了したら、[**保存**] > [**閉じる**] の順に選択します。

::: moniker-end


### <a name="delete-a-security-group"></a>セキュリティ グループを削除する

1. 管理センターで、[**グループ**]  >  [<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">グループ</a>] ページに移動します。
    
2. [**グループ**] ページで、グループ名を選択します。 
    
3. [**グループの削除**] (ゴミ箱アイコン) を選択し、[**削除**] を選択して確認します。
    
    グループが削除されたら、[**閉じる**] を選択します。 
    
## <a name="groups-in-exchange-online-and-sharepoint-online"></a>Exchange Online グループと SharePoint Online グループ

ユーザー グループを作成して全員にメールを同時に送信できるようにする場合は、Exchange 管理センターで [**管理**] \> [**Exchange**] \> [**宛先**] \> [**グループ**] の順に移動します。 次に、[**新規**]、[![追加](../../media/328ffb57-5f31-430a-b653-4a6b8e76d338.png)] の順に選択し、作成するグループの種類を選択します。 
  
- **配布グループ**: メッセージをユーザー グループに配布するために使用します。 また、メールが有効な配布 *グループ、または* 配布リストとも *呼ばれる。* 詳細については、「[配布グループの管理](/exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups)」をご覧ください。
    
- **セキュリティ グループ**: メッセージをユーザー グループに配布する、またはリソースへのアクセス許可を付与するために使用します。 このグループは、*メールが有効なセキュリティ グループ* とも呼ばれます。 詳細については、「[メールが有効なセキュリティ グループの管理](/Exchange/recipients/mail-enabled-security-groups)」をご覧ください。
    
- **動的配布グループ**: メッセージの送信時に、定義されたフィルターと条件に基づいて宛先リストが毎回再確認されるタイプの配布グループ。 詳細については、「[動的配布グループの管理](/Exchange/recipients/dynamic-distribution-groups/dynamic-distribution-groups)」をご覧ください。
    
Exchange 管理センターで配布グループとメールが有効なセキュリティ グループを作成すると、その名前とユーザー リストが [セキュリティ グループ **] ページに表示** されます。 このグループは、どちらの場所でも削除できますが、編集は Exchange 管理センターでのみ実行できます。 動的配布グループは 、[セキュリティ グループ] ページ **に表示** されます。 
  
 SharePoint グループは、サイト コレクションの作成時に自動的に作成されます。 既定のグループは、SharePoint の既定のアクセス許可レベル (SharePoint ロールと呼ばれることもあります) を使用して、ユーザーに権限とアクセス権を付与します。 詳細については、「[SharePoint Online の既定の SharePoint グループ](/sharepoint/default-sharepoint-groups)」をご覧ください。
  
## <a name="how-is-a-security-group-different-from-security-groups-i-create-in-sharepoint"></a>セキュリティ グループは、SharePoint で作成したセキュリティ グループとどのように異なりますか?

セキュリティ グループは、SharePoint、Exchange、MDM、Windows などで使用できます。 SharePoint で作成したセキュリティ グループは、その SharePoint サイト コレクションでしか認識されません。
  
## <a name="do-i-have-to-use-security-groups-for-my-organization-to-be-secure"></a>組織をセキュリティで保護するためにはセキュリティ グループを使用する必要がありますか?

いいえ。これは、組織のセキュリティを管理できる方法の 1 つです。常にユーザーにはアクセス許可およびサイトへのアクセス権限を個別に付与することができます。ただし、セキュリティ グループを使用すれば、大規模なユーザー グループを容易に管理することができます。
  
## <a name="can-i-send-email-to-a-security-group"></a>セキュリティ グループにメールを送信できますか?

はい。 ただし、メールとコラボレーションにグループを使用する場合は、代わりに [Microsoft 365](../create-groups/create-groups.md) グループを作成することをお勧めします。 
