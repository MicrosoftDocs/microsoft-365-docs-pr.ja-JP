---
title: 別の地域の場所に OneDrive サイトを移動する
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Normal
description: サイトの移動をスケジュールするOneDrive、ユーザーに期待を伝える方法など、さまざまな地域の場所にサイトを移動する方法に関する情報を確認します。
ms.openlocfilehash: 59b3fb47fd195967e7af056c7a71fb4e736471d1
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46691597"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="abbb7-103">別の地域の場所に OneDrive サイトを移動する</span><span class="sxs-lookup"><span data-stu-id="abbb7-103">Move a OneDrive site to a different geo location</span></span> 

<span data-ttu-id="abbb7-104">地理OneDrive移動を使用すると、ユーザーのデータを別OneDrive場所に移動できます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-104">With OneDrive geo move, you can move a user's OneDrive to a different geo location.</span></span> <span data-ttu-id="abbb7-105">OneDriveの移動は、オンライン管理者またはSharePoint管理者によってMicrosoft 365されます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-105">OneDrive geo move is performed by the SharePoint Online administrator or the Microsoft 365 global administrator.</span></span> <span data-ttu-id="abbb7-106">位置情報の移動をOneDriveする前に、OneDrive が移動中のユーザーに通知し、移動中のすべてのファイルを閉じすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="abbb7-106">Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move.</span></span> <span data-ttu-id="abbb7-107">(ユーザーが移動中に Office クライアントを使用してドキュメントを開いている場合は、移動が完了したら、ドキュメントを新しい場所に保存する必要があります)。必要に応じて、移動を将来の時間にスケジュールできます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-107">(If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="abbb7-108">サービスOneDrive Azure Blob を使用してStorageを格納します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-108">The OneDrive service uses Azure Blob Storage to store content.</span></span> <span data-ttu-id="abbb7-109">ユーザー Storageに関連付けられている OneDrive BLOB は、ユーザーが使用できる宛先の場所から 40 日以内に、OneDrive場所に移動されます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-109">The Storage blob associated with the user's OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user.</span></span> <span data-ttu-id="abbb7-110">ユーザーのサーバーへのアクセスはOneDriveが利用可能になるとすぐにOneDrive復元されます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-110">The access to the user's OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="abbb7-p103">OneDrive 地域の移動の期間中 (約 2 ～ 6 時間)、ユーザーの OneDrive は読み取り専用に設定されます。ユーザーは今まで通り OneDrive 同期クライアントまたは SharePoint Online の OneDrive サイトからファイルにアクセスできます。OneDrive 地域の移動の完了後に、ユーザーが Microsoft 365 アプリ起動ツールで OneDrive に移動すると、移動先の地域の場所にある OneDrive に自動的に接続されます。同期クライアントは、新しい場所からの同期を自動的に開始します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Microsoft 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="abbb7-115">この記事の手順には、[Microsoft Office SharePoint Online の PowerShell モジュール](https://www.microsoft.com/download/details.aspx?id=35588)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="abbb7-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/download/details.aspx?id=35588).</span></span>

## <a name="communicating-to-your-users"></a><span data-ttu-id="abbb7-116">ユーザーへの連絡</span><span class="sxs-lookup"><span data-stu-id="abbb7-116">Communicating to your users</span></span>

<span data-ttu-id="abbb7-p104">OneDrive サイトの地理的場所を移動する際には、想定される動作についてユーザーに通知することが重要です。これは、ユーザーが混乱してヘルプ デスクに問い合わせる可能性を減らすのに役立ちます。移動の前に、次の情報について電子メールでユーザーに連絡してください。</span><span class="sxs-lookup"><span data-stu-id="abbb7-p104">When moving OneDrive sites between geo locations, it's important to communicate to your users what to expect. This can help reduce user confusion and calls to your help desk. Email your users before the move and let them know the following information:</span></span>

- <span data-ttu-id="abbb7-120">移動開始予定時刻と予定所要時間</span><span class="sxs-lookup"><span data-stu-id="abbb7-120">When the move is expected to start and how long it is expected to take</span></span>
- <span data-ttu-id="abbb7-121">ユーザーの OneDrive の移動先となる地理的場所、および新しい場所にアクセスするための URL</span><span class="sxs-lookup"><span data-stu-id="abbb7-121">What geo location their OneDrive is moving to, and the URL to access the new location</span></span>
- <span data-ttu-id="abbb7-122">移動中はファイルを閉じた状態にし、編集を加えてはならないこと。</span><span class="sxs-lookup"><span data-stu-id="abbb7-122">They should close their files and not make edits during the move.</span></span>
- <span data-ttu-id="abbb7-123">移動してもファイルの許可と共有は変更されないこと。</span><span class="sxs-lookup"><span data-stu-id="abbb7-123">File permissions and sharing will not change as a result of the move.</span></span>
- <span data-ttu-id="abbb7-124">[複数地理環境でのユーザー エクスペリエンス](multi-geo-user-experience.md)として期待されること</span><span class="sxs-lookup"><span data-stu-id="abbb7-124">What to expect from the [user experience in a multi-geo environment](multi-geo-user-experience.md)</span></span>

<span data-ttu-id="abbb7-125">移動が正常に終了した時点で、ユーザーに対し、OneDrive での作業を再開できることを伝える電子メールを送信するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="abbb7-125">Be sure to send your users an email when the move has successfully completed informing them that they can resume working in OneDrive.</span></span>

## <a name="scheduling-onedrive-site-moves"></a><span data-ttu-id="abbb7-126">OneDrive サイトの移動のスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="abbb7-126">Scheduling OneDrive site moves</span></span>

<span data-ttu-id="abbb7-p105">OneDrive サイトの移動を事前にスケジュールすることができます (この記事の後半でご説明いたします)。少数のユーザーの移動から始め、ワークフローと連絡手順を確認することをお勧めします。プロセスが満足できるものであった場合、次のように移動をスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="abbb7-p105">You can schedule OneDrive site moves in advance (described later in this article). We recommend that you start with a small number of users to validate your workflows and communication strategies. Once you are comfortable with the process, you can schedule moves as follows:</span></span>

- <span data-ttu-id="abbb7-130">一度に最大 4,000 件の移動をスケジュールすることができます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-130">You can schedule up to 4,000 moves at a time.</span></span>
- <span data-ttu-id="abbb7-131">移動開始後はスケジュールを追加でき、常時最大 4,000 件の保留中の移動をキューに置いておけます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-131">As the moves begin, you can schedule more, with a maximum of 4,000 pending moves in the queue and any given time.</span></span>
- <span data-ttu-id="abbb7-132">移動できる OneDrive の最大サイズは 1 テラバイト (1 TB) です。</span><span class="sxs-lookup"><span data-stu-id="abbb7-132">The maximum size of a OneDrive that can be moved is 1 terabyte (1 TB).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="abbb7-133">OneDrive サイトの移動</span><span class="sxs-lookup"><span data-stu-id="abbb7-133">Moving a OneDrive site</span></span>

<span data-ttu-id="abbb7-134">地域移動をOneDriveするには、テナント管理者が最初にユーザーの優先データの場所 (PDL) を適切な地理的位置に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="abbb7-134">To perform a OneDrive geo move, the tenant administrator must first set the user's Preferred Data Location (PDL) to the appropriate geo location.</span></span> <span data-ttu-id="abbb7-135">PDL が設定された後、PDL 更新プログラムが地理的位置間で同期するまで少なくとも 24 時間待機してから、OneDriveを開始します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-135">Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="abbb7-136">geo move コマンドレットを使用する場合は、次の構文を使用して、ユーザーの現在の場所OneDrive SPO Service に接続します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-136">When using the geo move cmdlets, connect to SPO Service at the user's current OneDrive geo location, using the following syntax:</span></span>

`Connect-SPOService -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="abbb7-137">たとえば、ユーザー OneDrive 'Matt@contosoenergy.onmicrosoft.com' の場所を移動するには、ユーザーのOneDriveが EUR 地域の場所にあるとき、EUR SharePoint 管理センターに接続します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-137">For example: To move OneDrive of user 'Matt@contosoenergy.onmicrosoft.com', connect to EUR SharePoint Admin center as the user's OneDrive is in EUR geo location:</span></span>

`Connect-SPOSservice -url https://contosoenergyeur-admin.sharepoint.com`

![Connect-SPOService コマンドレットを示す PowerShell ウィンドウのスクリーン ショット](../media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="abbb7-139">環境の検証</span><span class="sxs-lookup"><span data-stu-id="abbb7-139">Validating the environment</span></span>

<span data-ttu-id="abbb7-140">OneDrive 地域移動の開始前に、目的の環境を検証するようにお勧めします。</span><span class="sxs-lookup"><span data-stu-id="abbb7-140">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="abbb7-141">すべての地域の場所に互換性があることを確認するために、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-141">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCrossCompatibilityStatus`

<span data-ttu-id="abbb7-142">地域の場所のリストが表示され、その場所間でコンテンツを移動できるかどうかが「互換性あり」として示されます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-142">You will see a list of your geo locations and whether content can be moved between will be denoted as "Compatible".</span></span> <span data-ttu-id="abbb7-143">コマンドが「互換性なし」を返した場合は、後日、状態の検証をあとでもう一度お試しください。</span><span class="sxs-lookup"><span data-stu-id="abbb7-143">If the command returns "Incompatible" please retry validating the status at a later date.</span></span>

<span data-ttu-id="abbb7-144">たとえば、サブサイトが含まれている場合、OneDrive は移動できません。</span><span class="sxs-lookup"><span data-stu-id="abbb7-144">If a OneDrive contains a subsite, for example, it cannot be moved.</span></span> <span data-ttu-id="abbb7-145">OneDrive が移動可能かどうかを検証するには、-ValidationOnly パラメーターを指定した Start-SPOUserAndContentMove コマンドレットを使用してください。</span><span class="sxs-lookup"><span data-stu-id="abbb7-145">You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="abbb7-p109">OneDrive の移動が可能な状態になっている場合は Success が返されます。移動を妨げる訴訟ホールドまたはサブサイトがある場合は Fail が返されます。OneDrive が移動できる状態になっていることを確認したら、移動を開始します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-p109">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="abbb7-148">OneDrive 地域移動の開始</span><span class="sxs-lookup"><span data-stu-id="abbb7-148">Start a OneDrive geo move</span></span>

<span data-ttu-id="abbb7-149">移動を開始するには、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-149">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="abbb7-150">次に示すパラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-150">Using these parameters:</span></span>

-   <span data-ttu-id="abbb7-151">_UserPrincipalName_: 移動する OneDrive を所有するユーザーの UPN です。</span><span class="sxs-lookup"><span data-stu-id="abbb7-151">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="abbb7-152">_DestinationDataLocation_ – Geo-Location移動するOneDriveする必要がある場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-152">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved.</span></span> <span data-ttu-id="abbb7-153">これは、ユーザーの優先データの場所と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="abbb7-153">This should be same as the user's preferred data location.</span></span>

<span data-ttu-id="abbb7-154">たとえば、matt@contosoenergy.onmicrosoft.com の OneDrive を EUR から AUS に移動するには、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-154">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![Start-SPOUserAndContentMove コマンドレットを示す PowerShell ウィンドウのスクリーン ショット](../media/move-onedrive-between-geo-locations-image2.png)

<span data-ttu-id="abbb7-156">将来の地域移動をスケジュールするには、次に示すパラメーターのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-156">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="abbb7-p111">_PreferredMoveBeginDate_: 移動は、この指定時刻に開始されると見込まれます。時刻は、協定世界時 (UTC) で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="abbb7-p111">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="abbb7-p112">_PreferredMoveEndDate_: 移動は、最善努力の原則で、この指定時刻に完了すると見込まれます。時刻は、協定世界時 (UTC) で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="abbb7-p112">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="abbb7-161">OneDrive 地域移動のキャンセル</span><span class="sxs-lookup"><span data-stu-id="abbb7-161">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="abbb7-162">コマンドレットを使用して、移動が進行中または完了していないOneDrive、ユーザーのユーザーのデータの地理的な移動を停止できます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-162">You can stop the geo move of a user's OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="abbb7-163">_UserPrincipalName_ は、移動を停止する OneDrive の所有ユーザーの UPN です。</span><span class="sxs-lookup"><span data-stu-id="abbb7-163">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="abbb7-164">現在の状態の確認</span><span class="sxs-lookup"><span data-stu-id="abbb7-164">Determining current status</span></span>

<span data-ttu-id="abbb7-165">このコマンドレットを使用して、OneDrive接続している geo 内または地域外に移動する場所の状態をGet-SPOUserAndContentMoveStateできます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-165">You can check the status of a OneDrive geo move in or out of the geo that you're connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="abbb7-166">移動の状態については、次に示す表で説明します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-166">The move statuses are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="abbb7-167"><strong>状態</strong></span><span class="sxs-lookup"><span data-stu-id="abbb7-167"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="abbb7-168"><strong>説明</strong></span><span class="sxs-lookup"><span data-stu-id="abbb7-168"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="abbb7-169">NotStarted</span><span class="sxs-lookup"><span data-stu-id="abbb7-169">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="abbb7-170">移動は開始されていません。</span><span class="sxs-lookup"><span data-stu-id="abbb7-170">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="abbb7-171">InProgress (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="abbb7-171">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="abbb7-172">移動は、検証 (1/4)、バックアップ (2/4)、復元 (3/4)、クリーンアップ (4/4) のいずれかの状態で進行中です。</span><span class="sxs-lookup"><span data-stu-id="abbb7-172">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="abbb7-173">Success</span><span class="sxs-lookup"><span data-stu-id="abbb7-173">Success</span></span></td>
<td align="left"><span data-ttu-id="abbb7-174">移動は正常に完了しています。</span><span class="sxs-lookup"><span data-stu-id="abbb7-174">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="abbb7-175">Failed</span><span class="sxs-lookup"><span data-stu-id="abbb7-175">Failed</span></span></td>
<td align="left"><span data-ttu-id="abbb7-176">移動は失敗しました。</span><span class="sxs-lookup"><span data-stu-id="abbb7-176">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="abbb7-177">特定のユーザーの移動の状態を確認するには、UserPrincipalName パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-177">To find the status of a specific user's move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="abbb7-178">接続している地理的位置の移動または移動の状態を確認するには、MoveState パラメーターを使用して、NotStarted、InProgress、Success、Failed、All のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-178">To find the status of all of the moves in or out of the geo location that you're connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="abbb7-179">また、より詳細な移動状態の説明が示されるように、`-Verbose` パラメーターを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-179">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="abbb7-180">ユーザー エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="abbb7-180">User Experience</span></span>

<span data-ttu-id="abbb7-p113">ユーザーの OneDrive を別の地域の場所に移動する場合は、OneDrive のユーザーに最小限の説明についての通知が必要です。移動中は読み取り専用の状態になることの説明に加えて、既存のリンクとアクセス許可は移動の完了後に引き続き期待どおりに動作することも説明します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-p113">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="abbb7-183">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="abbb7-183">OneDrive for Business</span></span>

<span data-ttu-id="abbb7-184">移動が進行中に、ユーザーのOneDrive読み取り専用に設定されます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-184">While the move is in progress the user's OneDrive is set to read-only.</span></span> <span data-ttu-id="abbb7-185">移動が完了すると、ユーザーは OneDrive アプリ 起動ツールまたは web ブラウザーの OneDrive に移動すると、OneDrive Microsoft 365 に移動します。</span><span class="sxs-lookup"><span data-stu-id="abbb7-185">Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Microsoft 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="abbb7-186">OneDrive コンテンツに対するアクセス許可</span><span class="sxs-lookup"><span data-stu-id="abbb7-186">Permissions on OneDrive content</span></span>

<span data-ttu-id="abbb7-187">コンテンツに対するアクセスOneDriveユーザーは、移動中および完了した後もコンテンツにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-187">Users with permissions to OneDrive content will continue to have access to the content during the move and after it's complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="abbb7-188">OneDrive 同期クライアント</span><span class="sxs-lookup"><span data-stu-id="abbb7-188">OneDrive Sync Client</span></span> 

<span data-ttu-id="abbb7-p115">OneDrive 同期クライアントは、OneDrive 地域移動の完了後に、自動的に新しい OneDrive の場所を検出し、シームレスに同期を転換します。ユーザーは、再度サインインするなどの操作を一切実行する必要がありません。(同期クライアントのバージョン 17.3.6943.0625 以降が必要。)</span><span class="sxs-lookup"><span data-stu-id="abbb7-p115">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.  (Version 17.3.6943.0625 or later of the sync client required.)</span></span>

<span data-ttu-id="abbb7-192">OneDrive 地域移動の進行中にユーザーがファイルを更新すると、同期クライアントにより、移動が進行している間はファイルの更新が保留されることが通知されます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-192">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="abbb7-193">共有リンク</span><span class="sxs-lookup"><span data-stu-id="abbb7-193">Sharing links</span></span> 

<span data-ttu-id="abbb7-194">OneDrive 地域移動の完了時に、移動されたファイルの既存の共有リンクは、新しい地域の場所に自動的にリダイレクトされるようになります。</span><span class="sxs-lookup"><span data-stu-id="abbb7-194">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="abbb7-195">OneNote エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="abbb7-195">OneNote Experience</span></span> 

<span data-ttu-id="abbb7-p116">OneNote win32 クライアントと UWP (ユニバーサル) アプリは、OneDrive 地域移動の完了後に、自動的に新しい OneDrive の場所を検出してシームレスにノートブックを同期します。ユーザーは、再度サインインするなどの操作を一切実行する必要がありません。ユーザーが認識できることは、OneDrive 地域移動が進行中のときにノートブックの同期が失敗することのみです。このエクスペリエンスは、次に示す OneNote クライアントのバージョンで利用できます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-p116">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="abbb7-200">OneNote win32: バージョン 16.0.8326.2096 (以降)</span><span class="sxs-lookup"><span data-stu-id="abbb7-200">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="abbb7-201">OneNote UWP: バージョン 16.0.8431.1006 (以降)</span><span class="sxs-lookup"><span data-stu-id="abbb7-201">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="abbb7-202">OneNote モバイル アプリ: バージョン 16.0.8431.1011 (以降)</span><span class="sxs-lookup"><span data-stu-id="abbb7-202">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="abbb7-203">Teams アプリ</span><span class="sxs-lookup"><span data-stu-id="abbb7-203">Teams app</span></span>

<span data-ttu-id="abbb7-p117">OneDrive 地域移動の完了時に、ユーザーは Teams アプリで OneDrive ファイルにアクセスできます。さらに、地域移動の前に OneDrive から Teams チャットで共有したファイルは、移動の完了後も引き続き操作できます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-p117">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="abbb7-206">OneDrive for Business モバイル アプリ (iOS)</span><span class="sxs-lookup"><span data-stu-id="abbb7-206">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="abbb7-207">OneDrive 地域移動の完了時に、ユーザーは、新しい OneDrive の場所に同期するために、iOS モバイル アプリでサインアウトしてから再度サインインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="abbb7-207">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="abbb7-208">既存のフォロー対象グループおよびサイト</span><span class="sxs-lookup"><span data-stu-id="abbb7-208">Existing followed groups and sites</span></span>

<span data-ttu-id="abbb7-209">フォローされたサイトとグループは、地理的な場所に関係なく、OneDriveに表示されます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-209">Followed sites and groups will show up in the user's OneDrive regardless of their geo location.</span></span> <span data-ttu-id="abbb7-210">別の地域の場所でホストされているサイトとグループは、別のタブで開きます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-210">Sites and groups hosted in another geo location will open in a separate tab.</span></span>

### <a name="delve-geo-url-updates"></a><span data-ttu-id="abbb7-211">Delve地域 URL の更新</span><span class="sxs-lookup"><span data-stu-id="abbb7-211">Delve Geo URL updates</span></span>

<span data-ttu-id="abbb7-212">ユーザーは、ユーザーが新Delveに移動された後にのみ、PDL に対応する OneDriveに送信されます。</span><span class="sxs-lookup"><span data-stu-id="abbb7-212">Users will be sent to the Delve geo corresponding to their PDL only after their OneDrive has been moved to the new geo.</span></span>
