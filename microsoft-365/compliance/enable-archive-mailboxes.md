---
title: セキュリティ/コンプライアンス センターでアーカイブ メールボックスを有効にする
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.ArchivingHelp
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 268a109e-7843-405b-bb3d-b9393b2342ce
ms.custom: seo-marvel-apr2020
description: コンプライアンス センターを使用して、組織でのメッセージの保持、電子情報開示、保留に関する要件をサポートするためにアーカイブ メールボックスを有効にする方法を説明します。
ms.openlocfilehash: 72aa3f194197140cd86463598a17ab07fbbd647a
ms.sourcegitcommit: 5db5047c24b56f3af90c2bc5c830a7a13eeeccad
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2021
ms.locfileid: "53341690"
---
# <a name="enable-archive-mailboxes-in-the-compliance-center"></a>セキュリティ/コンプライアンス センターでアーカイブ メールボックスを有効にする

Microsoft 365 でのアーカイブ (*インプレース アーカイブ* とも呼ばれます) では、追加のメールボックスの記憶域がユーザーに提供されます。 アーカイブ メールボックスを有効にすると、ユーザーは Microsoft Outlook と Outlook on the web (以前の Outlook Web App) を使用してアーカイブ メールボックスのメッセージにアクセスし、保存することができます。 ユーザーは、自分のプライマリ メールボックスとアーカイブ メールボックスの間でメッセージを移動したりコピーしたりもできます。 ユーザーはまた、削除済みアイテムの復元ツールを使用して、アーカイブ メールボックスの [回復可能なアイテム] フォルダーから削除済みのアイテムを復元できます。

> [!NOTE]
> Microsoft 365 の自動拡張アーカイブ機能は、アーカイブ メールボックスに追加のストレージを提供します。 自動拡張アーカイブが有効な状態で、ユーザーのアーカイブメールボックスの記憶域クォータの初期値に達すると、Microsoft 365 は追加の記憶域を自動的に追加します。 つまり、管理者が最初にアーカイブ メールボックスを有効にし、自動拡張アーカイブを組織で有効にしておくと、ユーザーのメールボックスの記憶域が足りなくなることも、管理者による管理の必要もなくなります。 詳細については、「[無制限アーカイブの概要](unlimited-archiving.md)」を参照してください。

## <a name="get-the-necessary-permissions"></a>必要なアクセス許可を取得する

アーカイブ メールボックスを有効または無効にするには、Exchange Online でメール受信者役割が自分に割り当てられている必要があります。 既定では、この役割は、Exchange 管理センターの [**アクセス許可**] ページで受信者管理役割グループまたは組織管理役割グループに割り当てられています。 セキュリティ/コンプライアンス センターの [**アーカイブ**] ページが表示されない場合、必要なアクセス許可を自分に割り当ててもらうよう管理者に依頼します。

## <a name="enable-an-archive-mailbox"></a>アーカイブ メールボックスの有効化

1. <https://compliance.microsoft.com> に移動し、サインインします。

2. Microsoft 365 コンプライアンス センターの左のウィンドウで、**[情報ガバナンス]** をクリックしてから、**[アーカイブ]** タブをクリックします。

   **[アーカイブ]** ページが表示されます。**[アーカイブ メールボックス]** 列は、各ユーザーに対してアーカイブ メールボックスが有効か無効かを示します。

   > [!NOTE]
   > **アーカイブ** ページには、最大 500 人のユーザーが表示されます。

4. メールボックスの一覧で、アーカイブ メールボックスを有効にする対象のユーザーを選択します。

   ![アーカイブ メールボックスを有効にするには、選択したユーザーの詳細ウィンドウで [有効にする] をクリックします。](../media/8b53cdec-d5c9-4c28-af11-611f95c37b34.png)

5. 選択したユーザーの [詳細] ウィンドウで、[**有効化**] をクリックします。

   アーカイブ メールボックスを有効にすると、ユーザーのメールボックス内にあるメールボックスに割り当てられているアーカイブ ポリシーより古いアイテムは、新しいアーカイブ メールボックスに移動されるという警告が表示されます。 アイテムがメールボックスに配信またはユーザーによって作成された日付から 2 年間経過すると、Exchange Online のメールボックスに割り当てられているアイテム保持ポリシーの一部である既定のアーカイブ ポリシーにより、アイテムはアーカイブ メールボックスに移動されます。 詳細については、この記事の「**詳細情報**」セクションを参照してください。

6. [**はい**] をクリックしてアーカイブ メールボックスを有効にします。

   アーカイブ メールボックスの作成にはしばらくかかる場合があります。 作成されると、選択したユーザーの詳細ウィンドウに [**アーカイブ メールボックス: 有効**] と表示されます。 詳細ウィンドウの情報を更新するには、[**更新**] ![更新アイコン](../media/O365-MDM-Policy-RefreshIcon.gif) をクリックする必要がある場合があります。

> [!TIP]
> Shift キーまたは Ctrl キーを使用して、アーカイブ メールボックスが無効になっている複数のユーザーを選択して、アーカイブ メールボックスを一括して有効にすることもできます。複数のメールボックスを選択した後に、詳細ウィンドウで **[有効にする]** をクリックします。

## <a name="disable-an-archive-mailbox"></a>アーカイブ メールボックスを無効にする

ユーザーのアーカイブ メールボックスを無効にするために、セキュリティ/コンプライアンス センターの [**アーカイブ**] ページを使用することもできます。 アーカイブ メールボックスを無効にしてから 30 日以内なら、ユーザーのプライマリ メールボックスにそれを再接続できます。 この場合、アーカイブ メールボックスの元の内容が復元されます。 30 日後には、元のアーカイブ メールボックスの内容は完全に削除され、回復不可能になります。 したがって、アーカイブを無効にした後、30 日を超えてから再度有効にすると、新しいアーカイブ メールボックスが作成されます。

ユーザーのメールボックスに割り当てられる既定のアーカイブ ポリシーは、アイテムが配信された日付から 2 年間後にアイテムをアーカイブ メールボックスに移動します。 ユーザーのアーカイブ メールボックスを無効にすると、メールボックスのアイテムに対してアクションは何も実行されず、そのままユーザーのプライマリ メールボックスに残ります。

アーカイブ メールボックスを無効にするには: 

1. <https://compliance.microsoft.com> に移動し、サインインします。

2. Microsoft 365 コンプライアンス センターの左のウィンドウで、**[情報ガバナンス]** をクリックしてから、**[アーカイブ]** タブをクリックします。

   **[アーカイブ]** ページが表示されます。**[アーカイブ メールボックス]** 列は、各ユーザーに対してアーカイブ メールボックスが有効か無効かを示します。

   > [!NOTE]
   > **アーカイブ** ページには、最大 500 人のユーザーが表示されます。

3. メールボックスの一覧で、アーカイブ メールボックスを無効にする対象のユーザーを選択します。

4. [詳細] ウィンドウで、**[無効にする]** をクリックします。

   30 日以内であればアーカイブ メールボックスを再度有効にでき、30 日が経過するとアーカイブ内のすべての情報が完全に削除されることを示す警告メッセージが表示されます。

5. 
            **[はい]** をクリックしてアーカイブ メールボックスを無効にします。

   アーカイブ メールボックスの無効化にはしばらくかかる場合があります。 無効になると、選択したユーザーの詳細ウィンドウに [**アーカイブ メールボックス: 無効]** が表示されます。 詳細ウィンドウの情報を更新するには、[**更新**] ![更新アイコン](../media/O365-MDM-Policy-RefreshIcon.gif) をクリックする必要がある場合があります。

> [!TIP]
> Shift キーまたは Ctrl キーを使用して、アーカイブ メールボックスが有効になっている複数のユーザーを選択して、アーカイブ メールボックスを一括して無効にすることもできます。複数のメールボックスを選択した後に、詳細ウィンドウで **[無効にする]** をクリックします。

## <a name="use-exchange-online-powershell-to-enable-or-disable-archive-mailboxes"></a>Exchange Online PowerShell を使用してアーカイブ メールボックスを有効または無効にする

アーカイブ メールボックスを有効にするには、PowerShell を使用することもできます。 PowerShell を使用する主な理由は、組織内のすべてのユーザーのためにアーカイブ メールボックスをすばやく有効にできるということです。

最初の手順は、Exchange Online PowerShell へ接続することです。 手順については、「[Exchange Online PowerShell に接続する](/powershell/exchange/connect-to-exchange-online-powershell)」を参照してください。

Exchange Online に接続したら、次のセクションのコマンドを実行してアーカイブメール ボックスを有効または無効にできます。

### <a name="enable-archive-mailboxes"></a>アーカイブ メールボックスの有効化

特定のユーザーのアーカイブ メールボックスを有効にするには、次のコマンドを実行します。

```powershell
Enable-Mailbox -Identity <username> -Archive
```

組織内の、アーカイブ メールボックスが現在有効になっていないすべてのユーザーについてアーカイブ メールボックスを有効にするには、次のコマンドを実行します。

```powershell
Get-Mailbox -Filter {ArchiveGuid -Eq "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Enable-Mailbox -Archive
```

### <a name="disable-archive-mailboxes"></a>アーカイブ メールボックスの無効化

特定のユーザーのアーカイブメールボックスを無効にするには、次のコマンドを実行します。

```powershell
Disable-Mailbox -Identity <username> -Archive
```

組織内の、アーカイブ メールボックスが現在有効になっているすべてのユーザーについてアーカイブ メールボックスを無効にするには、次のコマンドを実行します。

```powershell
Get-Mailbox -Filter {ArchiveGuid -Ne "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Disable-Mailbox -Archive
```

## <a name="more-information"></a>詳細情報

- アーカイブ メールボックスが有効になっている場合、ユーザーはメッセージをアーカイブ メールボックスに保存できます。 ユーザーは、Microsoft Outlook と Outlook on the web を使用してアーカイブ メールボックスにアクセスできます。 これらのクライアント アプリケーションのいずれかを使用して、ユーザーは自分のアーカイブ メールボックスでメッセージを表示したり、プライマリ メールボックスとアーカイブ メールボックス間でメッセージを移動またはコピーできます。 また、ユーザーは削除済みアイテム復元ツール使用して、アーカイブ メールボックスの [回復可能なアイテム] フォルダーから削除済みのアイテムを復元できます。

  インプレース アーカイブをサポートしている Outlook のライセンスの一覧については、「[Outlook の Exchange 機能に関するライセンス要件](https://support.microsoft.com/office/46b6b7c5-c3ca-43e5-8424-1e2807917c99)」を参照してください。

- インプレース アーカイブは、組織のアイテム保持、電子情報開示、および保留に関する要件を管理者やユーザーが満たすためのサポートをします。 たとえば、組織の Exchange アイテム保持ポリシーを使用して、メールボックスの内容をユーザーのアーカイブ メールボックスに移動することができます。 セキュリティ/コンプライアンス センターでコンテンツ検索ツールを使用してユーザーのメールボックスで特定のコンテンツを検索するすると、ユーザーのアーカイブ メールボックスも検索されます。 また、ユーザーのメールボックスに訴訟ホールドを配置したりアイテム保持ポリシーを適用したりすると、アーカイブ メールボックス内のアイテムも保持されます。

- アーカイブ メールボックスを有効にした後は、組織では、すべてのメールボックスに自動的に割り当てられる 既定の Exchange アイテム保持ポリシー (メッセージング レコード管理 (MRM) ポリシーとも呼ばれています) を活用できます。 アーカイブ メールボックスを有効にすると、既定の Exchange アイテム保持ポリシーは自動的に次を行います。

  - 2 年間以上経過したアイテムを、ユーザーのプライマリ メールボックスからアーカイブ メールボックスに移動します。

  - 14 日以上経過したアイテムを、ユーザーのプライマリ メールボックスの [回復可能なアイテム] フォルダーから、アーカイブ メールボックスの [回復可能なアイテム] フォルダーへ自動的に移動します

- アーカイブ メールボックスと Exchange アイテム保持ポリシーの詳細については、次のトピックを参照してください。

  - [Exchange Online での保持タグおよびアイテム保持ポリシー](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies)

  - [Exchange Online の既定のアイテム保持ポリシー](/exchange/security-and-compliance/messaging-records-management/default-retention-policy)

  - [組織のメールボックスについて、アーカイブ削除ポリシーを設定する](set-up-an-archive-and-deletion-policy-for-mailboxes.md)