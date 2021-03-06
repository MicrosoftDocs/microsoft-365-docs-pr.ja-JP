---
title: アクティビティアラートの作成
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 11/7/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- BCS160
- MET150
ms.assetid: 72bbad69-035b-4d33-b8f4-549a2743e97d
ROBOTS: NOINDEX, NOFOLLOW
description: ユーザーが特定のアクティビティを実行するときに、&通知を送信Microsoft 365セキュリティ コンプライアンス センターでアクティビティ通知を追加および管理する
ms.openlocfilehash: b48093de66fdefa9a298b6cdc0f0324ee720fbbf
ms.sourcegitcommit: 5db5047c24b56f3af90c2bc5c830a7a13eeeccad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2021
ms.locfileid: "53341606"
---
# <a name="create-activity-alerts"></a>アクティビティアラートの作成

ユーザーが特定のアクティビティを実行するときに電子メール通知を送信するアクティビティアラートを作成Office 365。 アクティビティアラートは、監査ログ内のイベントの検索に似ていますが、アラートを作成したアクティビティのイベントが発生すると電子メール メッセージが送信される点を除きます。

 **監査ログを検索する代わりにアクティビティ通知を使用する理由** 特定のユーザーが実際に知りたい特定の種類のアクティビティやアクティビティが実行されている場合があります。 これらのアクティビティの監査ログを検索する必要が生じするのではなく、アクティビティ通知を使用して、ユーザーがそれらのアクティビティを実行するときにMicrosoft 365メール メッセージを送信できます。 たとえば、SharePoint でユーザーがファイルを削除した場合に通知するアクティビティ アラートを作成したり、ユーザーがメールボックスからメッセージを完全に削除した場合に通知するアラートを作成できます。 送信される電子メール通知には、どのアクティビティが実行されたか、および実行したユーザーに関する情報が含まれます。

> [!NOTE]
> アクティビティ通知は非推奨です。 新しいアクティビティ通知を作成する代わりに、セキュリティとコンプライアンス センターでアラート ポリシーの使用を開始することをお勧めします。 アラート ポリシーは、ユーザーが指定したアクティビティを実行するときにアラートをトリガーするアラート ポリシーを作成する機能や、セキュリティとコンプライアンス センターの [アラートの表示] ページにアラートを表示する機能などの追加機能を提供します。 詳細については、「アラート ポリシー [」を参照してください](alert-policies.md)。

## <a name="confirm-roles-and-configure-audit-logging"></a>役割の確認と監査ログの構成

- アクティビティ通知を管理するには、セキュリティ コンプライアンス センターで組織&役割を割り当てる必要があります。 既定では、この役割はコンプライアンス管理者および組織の管理役割グループに割り当てられます。 役割グループにメンバーを追加する方法の詳細については、「ユーザーにセキュリティ コンプライアンス センターへのアクセス権を与える [」&参照してください](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)。

- アクティビティ通知の使用を開始するには、まず組織の監査ログを有効にする必要があります。 これを行うには、[アクティビティ通知] ページの [ **ユーザーと管理者** のアクティビティの記録を開始 **する] をクリック** します。 (このリンクが表示されていない場合は、組織の監査が既に有効です)。また、セキュリティ コンプライアンス センターの[監査ログの検索] ページで監査&オンにすることもできます ([監査ログ検索の検索 \> **] に移動します**)。 これを行う必要があるのは、組織に対して 1 回のみです。

- 監査ログで検索できるアクティビティと同じアクティビティに対してアラートを作成できます。 アラートを [作成できる一](#more-information) 般的なシナリオ (および監視する特定のアクティビティ) の一覧については、「詳細」セクションを参照してください。

- セキュリティ &コンプライアンス センターの [アクティビティ通知] ページを使用して、組織のアドレス帳に一覧表示されているユーザーが実行するアクティビティに対するアラートのみを作成できます。 このページを使用して、アドレス帳に記載されていない外部ユーザーが実行するアクティビティのアラートを作成することはできません。

## <a name="create-an-activity-alert"></a>アクティビティアラートを作成する

1. <https://compliance.microsoft.com/managealerts> に移動します。

2. 職場または学校のアカウントを使用してサインインします。

3. [アクティビティ通知 **] ページで** 、[追加] ![ アイコン [新規] を ](../media/8ee52980-254b-440b-99a2-18d068de62d3.gif) **クリックします**。

   アクティビティアラートを作成するフライアウト ページが表示されます。


    ![アクティビティアラートを作成する](../media/53888bd5-9fa2-4398-8ccc-1a9dc72517ac.png)

4. アクティビティアラートを作成するには、次のフィールドに入力します。

    a.  **[名前** ] - アラートの名前を入力します。 アラート名は組織内で一意である必要があります。

    b.  **説明** (省略可能) - 追跡されているアクティビティやユーザー、電子メール通知の送信ユーザーなどのアラートを記述します。 説明は、他の管理者に対するアラートの目的を迅速かつ簡単に説明する方法を提供します。

    c.  **アラートの種類** - [カスタム] **オプションが** 選択されている必要があります。

    d.  **[この通知を送信する場合** ] - [この通知 **を送信** する] をクリックして、次の 2 つのフィールドを構成します。

    - **[アクティビティ** ] - ドロップダウン リストをクリックして、アラートを作成できるアクティビティを表示します。 これは、監査ログを検索するときに表示されるアクティビティリストと同じです。 1 つ以上の特定のアクティビティを選択するか、アクティビティ グループ名をクリックしてグループ内のすべてのアクティビティを選択できます。 これらのアクティビティの説明については、「監査ログの検索」の「監査されたアクティビティ [」セクションを参照してください](search-the-audit-log-in-security-and-compliance.md#audited-activities)。 ユーザーがアラートに追加したアクティビティを実行すると、電子メール通知が送信されます。

     - **[ユーザー** ] - このボックスをクリックし、1 つ以上のユーザーを選択します。 このボックスのユーザーが [アクティビティ] ボックスに追加したアクティビティを **実行すると、** アラートが送信されます。 [ユーザー **] ボックス** は空白のままにして、組織内のユーザーがアラートで指定されたアクティビティを実行するときにアラートを送信します。

    e. **[** このアラートを送信する] - [このアラートの送信] をクリックし、[受信者] ボックスをクリックして名前を入力して、ユーザー ([ユーザー] ボックスで指定) がアクティビティを実行するときに電子メール通知を受け取るユーザーを追加します ([アクティビティ] ボックスで指定)。  既定では、受信者の一覧に追加されます。 このリストから名前を削除できます。

5. [保存 **] をクリック** してアラートを作成します。

    新しいアラートが [アクティビティ通知] ページの一 **覧に表示** されます。

    ![[アクティビティの通知] ページにアラートの一覧が表示されます。](../media/02b774f2-1719-41de-bbc9-5e5b7576f335.png)

    アラートの状態が [オン] に **設定されています**。 通知の送信時に電子メール通知を受け取る受信者も一覧表示されます。

## <a name="turn-off-an-activity-alert"></a>アクティビティアラートをオフにする

アクティビティ通知をオフにし、電子メール通知が送信されません。 アクティビティアラートをオフにした後も、組織のアクティビティ通知の一覧に表示され、そのプロパティを表示できます。

1. <https://compliance.microsoft.com/managealerts> に移動します。

2. 職場または学校のアカウントを使用してサインインします。

3. 組織のアクティビティ通知の一覧で、オフにするアラートをクリックします。

4. [アラートの **編集] ページで** 、[ **オン** ] トグル スイッチをクリックして状態を **[オフ**] に変更し、[保存] を **クリックします**。

    [アクティビティ通知] ページのアラート **の状態が** [オフ] に **設定されています**。

アクティビティアラートをオンに戻す場合は、これらの手順を繰り返し、[ **オフ** ] トグル スイッチをクリックして状態を [オン] に **変更します**。

## <a name="more-information"></a>詳細情報

- セキュリティ & コンプライアンス センターの [このアラートの送信先] フィールド (および [アクティビティ通知] ページの[受信者]に一覧表示) で指定されているユーザーに送信される電子メール通知の例を次に示します。

    ![アクティビティアラートに送信される電子メール通知の例](../media/a5f91611-fae6-4fe9-82f5-58521a2e2541.png)

- アクティビティアラートを作成できる一般的なドキュメントアクティビティと電子メール アクティビティを次に示します。 表は、アクティビティ、アラートを作成するアクティビティの名前、およびアクティビティが [アクティビティ] ドロップダウン リストに表示されるアクティビティ グループの名前を示しています。 アクティビティアラートを作成できるアクティビティの完全なリストを表示するには、「監査ログの検索」の「監査されたアクティビティ」 [セクションを参照してください](search-the-audit-log-in-security-and-compliance.md#audited-activities)。

    > [!TIP]
    > 任意のユーザーが実行する 1 つのアクティビティに対して、アクティビティ アラートを作成できます。 または、1 人または複数のユーザーが実行した複数のアクティビティを追跡するアクティビティ アラートを作成する場合があります。

    次の表に、ドキュメントまたはドキュメントの一般的なアクティビティSharePointまたはOneDrive for Business。

    |**ユーザーがこれを行う場合。..**|**このアクティビティのアラートを作成する**|**アクティビティ グループ**|
    |:-----|:-----|:-----|
    |サイト上のドキュメントを表示します。  <br/> |ファイルがアクセスされました  <br/> |ファイルとフォルダーのアクティビティ  <br/> |
    |ドキュメントを編集または変更します。  <br/> |ファイルの変更  <br/> |ファイルとフォルダーのアクティビティ  <br/> |
    |組織外のユーザーとドキュメントを共有します。  <br/> |ファイル、フォルダー、またはサイトを共有する  <br/> And  <br/> 共有への招待の作成  <br/> 詳細については、「[監査ログで共有監査を使用する](use-sharing-auditing.md)」を参照してください。  <br/> |共有アクティビティとアクセス要求アクティビティ  <br/> |
    |ドキュメントをアップロードまたはダウンロードします。  <br/> |ファイルのアップロード  <br/> And/or  <br/> ファイルのダウンロード  <br/> |ファイルとフォルダーのアクティビティ  <br/> |
    |サイトへのアクセス許可を変更します。  <br/> |サイト アクセス許可の変更  <br/> |サイト管理アクティビティ  <br/> |

    次の表に、電子メール関連の一般的なアクティビティを示Exchange Online。

    |**ユーザーがこれを行う場合。..**|**このアクティビティのアラートを作成する**|**アクティビティ グループ**|
    |:-----|:-----|:-----|
    |メールボックスから電子メール メッセージを完全に削除 (削除) します。  <br/> |メールボックスから削除されたメッセージ  <br/> | Exchange メールボックス アクティビティ  <br/> |
    |共有メールボックスから電子メール メッセージを送信します。  <br/> |送信者権限を使ったメッセージの送信  <br/> And  <br/> 代理送信権限を使ったメッセージの送信  <br/> | Exchange メールボックス アクティビティ  <br/> |

- セキュリティ & コンプライアンス センター PowerShell の **New-ActivityAlert** コマンドレットと **Set-ActivityAlert** コマンドレットを使用して、アクティビティ通知を作成および編集することもできます。 これらのコマンドレットを使用してアクティビティ通知を作成または編集する場合は、次のことを念頭に置いておきます。

  - コマンドレットを使用して、[アクティビティ] ドロップダウン リストに表示されていないアラートにアクティビティを追加すると、プロパティ ページにメッセージが表示され、"このアラートにはカスタム操作がピッカーに表示されません" というメッセージが表示されます。

  - コマンドレットを使用してアクティビティアラートを作成または編集する良い理由は、組織外のユーザーに電子メール通知を送信する方法です。 この外部ユーザーは、アラートの受信者の一覧に表示されます。 ただし、この外部ユーザーをアラートから削除した場合、そのユーザーは [警告の編集] ページを使用してアラートに再 **追加** できます。 **Set-ActivityAlert** コマンドレットを使用して外部ユーザーを再追加するか **、New-ActivityAlert** コマンドレットを使用して同じ (または異なる) 外部ユーザーを新しいアラートに追加する必要があります。
