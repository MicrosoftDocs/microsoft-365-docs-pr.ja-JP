---
title: LivePerson Conversational Cloud データをアーカイブするコネクタを設定Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
description: 17a-4 LivePerson Conversational Cloud DataParser コネクタをセットアップして使用して、LivePerson Conversational Cloud データをインポートおよびアーカイブする方法についてMicrosoft 365。
ms.openlocfilehash: 3a4156d817e1b7471f769a2365c5af9d58ade991
ms.sourcegitcommit: 778103d20a2b4c43e524aa436775764d8d8d4c33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2021
ms.locfileid: "53097298"
---
# <a name="set-up-a-connector-to-archive-liveperson-conversational-cloud-data-preview"></a><span data-ttu-id="c2045-103">LivePerson Conversational Cloud データをアーカイブするコネクタをセットアップする (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="c2045-103">Set up a connector to archive LivePerson Conversational Cloud data (preview)</span></span>

<span data-ttu-id="c2045-104">17a-4 LLC の[LivePerson Conversational Cloud DataParser](https://www.17a-4.com/liveperson-dataparser/)を使用して、LivePerson Conversational Cloud から Microsoft 365 組織内のユーザー メールボックスにデータをインポートおよびアーカイブします。</span><span class="sxs-lookup"><span data-stu-id="c2045-104">Use the [LivePerson Conversational Cloud DataParser](https://www.17a-4.com/liveperson-dataparser/) from 17a-4 LLC to import and archive data from LivePerson Conversational Cloud to user mailboxes in your Microsoft 365 organization.</span></span> <span data-ttu-id="c2045-105">DataParser には LivePerson Conversational Cloud コネクタが含まれており、サードパーティのデータ ソースからアイテムをキャプチャし、それらのアイテムを Microsoft 365 にインポートするように構成されています。</span><span class="sxs-lookup"><span data-stu-id="c2045-105">The DataParser includes a LivePerson Conversational Cloud connector that's configured to capture items from a third-party data source and import those items to Microsoft 365.</span></span> <span data-ttu-id="c2045-106">LivePerson Conversational Cloud DataParser コネクタは、データを電子メール メッセージ形式に変換し、それらのアイテムをユーザー メールボックスにインポートMicrosoft 365。</span><span class="sxs-lookup"><span data-stu-id="c2045-106">The LivePerson Conversational Cloud DataParser connector converts data to an email message format and then imports those items to user mailboxes in Microsoft 365.</span></span>

<span data-ttu-id="c2045-107">ユーザー メールボックスにデータを格納した後、訴訟ホールド、電子情報開示、保持ポリシーと保持ラベル、通信コンプライアンスなどのコンプライアンス機能Microsoft 365コンプライアンス機能を適用できます。</span><span class="sxs-lookup"><span data-stu-id="c2045-107">After data is stored in user mailboxes, you can apply Microsoft 365 compliance features such as Litigation Hold, eDiscovery, retention policies and retention labels, and communication compliance.</span></span> <span data-ttu-id="c2045-108">LivePerson Conversational Cloud コネクタを使用して、Microsoft 365データをインポートおよびアーカイブすると、組織が政府機関および規制ポリシーに準拠し続けるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c2045-108">Using a LivePerson Conversational Cloud connector to import and archive data in Microsoft 365 can help your organization stay compliant with government and regulatory policies.</span></span>

## <a name="overview-of-archiving-liveperson-conversational-cloud-data"></a><span data-ttu-id="c2045-109">LivePerson Conversational Cloud データのアーカイブの概要</span><span class="sxs-lookup"><span data-stu-id="c2045-109">Overview of archiving LivePerson Conversational Cloud data</span></span>

<span data-ttu-id="c2045-110">次の概要では、データ コネクタを使用して LivePerson Conversational Cloud データをアーカイブするプロセスを、Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="c2045-110">The following overview explains the process of using a data connector to archive LivePerson Conversational Cloud data in Microsoft 365.</span></span>

![17a-4 の LivePerson Conversational Cloud データのアーカイブ ワークフロー](../media/LiveEngageDataParserConnectorWorkflow.png)

1. <span data-ttu-id="c2045-112">組織は 17a-4 を使用して LivePerson Conversational Cloud DataParser をセットアップおよび構成します。</span><span class="sxs-lookup"><span data-stu-id="c2045-112">Your organization works with 17a-4 to set up and configure the the LivePerson Conversational Cloud DataParser.</span></span>

2. <span data-ttu-id="c2045-113">LivePerson Conversational Cloud アイテムは、定期的に DataParser によって収集されます。</span><span class="sxs-lookup"><span data-stu-id="c2045-113">On a regular basis, LivePerson Conversational Cloud items are collected by the DataParser.</span></span> <span data-ttu-id="c2045-114">DataParser は、メッセージのコンテンツを電子メール メッセージ形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="c2045-114">The DataParser also converts the content of a message to an email message format.</span></span>

3. <span data-ttu-id="c2045-115">Microsoft 365 コンプライアンス センター で作成した LivePerson Conversational Cloud DataParser コネクタは、DataParser に接続し、Microsoft クラウド内のセキュリティで保護された Azure Storage 場所にメッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="c2045-115">The LivePerson Conversational Cloud DataParser connector that you create in the Microsoft 365 compliance center connects to DataParser and transfers the messages to a secure Azure Storage location in the Microsoft cloud.</span></span>

4. <span data-ttu-id="c2045-116">**LivePerson Conversational Cloud DataParser** という名前の受信トレイ フォルダー内のサブフォルダーがユーザー メールボックスに作成され、そのフォルダーにアイテムがインポートされます。</span><span class="sxs-lookup"><span data-stu-id="c2045-116">A subfolder in the Inbox folder named **LivePerson Conversational Cloud DataParser** is created in the user mailboxes, and the items are imported to that folder.</span></span> <span data-ttu-id="c2045-117">コネクタは *、Email* プロパティの値を使用してアイテムをインポートするメールボックスを決定します。</span><span class="sxs-lookup"><span data-stu-id="c2045-117">The connector determines which mailbox to import items to by using the value of the *Email* property.</span></span> <span data-ttu-id="c2045-118">すべてのアイテムには、このプロパティが含まれるので、すべての参加者の電子メール アドレスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="c2045-118">Every item contains this property, which is populated with the email address of every participant.</span></span>

## <a name="before-you-set-up-a-connector"></a><span data-ttu-id="c2045-119">コネクタをセットアップする前に</span><span class="sxs-lookup"><span data-stu-id="c2045-119">Before you set up a connector</span></span>

- <span data-ttu-id="c2045-120">Microsoft コネクタ用の DataParser アカウントを作成します。</span><span class="sxs-lookup"><span data-stu-id="c2045-120">Create a DataParser account for Microsoft connectors.</span></span> <span data-ttu-id="c2045-121">これを行うには [、17a-4 LLC にお問い合わせください](https://www.17a-4.com/contact/)。</span><span class="sxs-lookup"><span data-stu-id="c2045-121">To do this, contact [17a-4 LLC](https://www.17a-4.com/contact/).</span></span> <span data-ttu-id="c2045-122">手順 1 でコネクタを作成する場合は、このアカウントにサインインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2045-122">You need to sign into this account when you create the connector in Step 1.</span></span>

- <span data-ttu-id="c2045-123">手順 1 で LivePerson Conversational Cloud DataParser コネクタを作成し (手順 3 で完了する) ユーザーは、Exchange Online のメールボックスインポートエクスポートの役割に割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2045-123">The user who creates the LivePerson Conversational Cloud DataParser connector in Step 1 (and completes it in Step 3) must be assigned to the Mailbox Import Export role in Exchange Online.</span></span> <span data-ttu-id="c2045-124">この役割は、データ コネクタ ページの[データ コネクタ] ページにコネクタを追加Microsoft 365 コンプライアンス センター。</span><span class="sxs-lookup"><span data-stu-id="c2045-124">This role is required to add connectors on the **Data connectors** page in the Microsoft 365 compliance center.</span></span> <span data-ttu-id="c2045-125">既定では、この役割はグループ内の役割グループExchange Online。</span><span class="sxs-lookup"><span data-stu-id="c2045-125">By default, this role is not assigned to a role group in Exchange Online.</span></span> <span data-ttu-id="c2045-126">[メールボックスのインポートエクスポート] 役割は、組織の [組織の管理] 役割グループに追加Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="c2045-126">You can add the Mailbox Import Export role to the Organization Management role group in Exchange Online.</span></span> <span data-ttu-id="c2045-127">または、役割グループを作成し、メールボックスインポートエクスポートの役割を割り当て、適切なユーザーをメンバーとして追加できます。</span><span class="sxs-lookup"><span data-stu-id="c2045-127">Or you can create a role group, assign the Mailbox Import Export role, and then add the appropriate users as members.</span></span> <span data-ttu-id="c2045-128">詳細については、「グループ内の[役割グループを](/Exchange/permissions-exo/role-groups#create-role-groups)管理[](/Exchange/permissions-exo/role-groups#modify-role-groups)する」の「役割グループの作成」または「役割グループの変更」セクションを参照Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="c2045-128">For more information, see the [Create role groups](/Exchange/permissions-exo/role-groups#create-role-groups) or [Modify role groups](/Exchange/permissions-exo/role-groups#modify-role-groups) sections in the article "Manage role groups in Exchange Online".</span></span>

## <a name="step-1-set-up-a-liveperson-conversational-cloud-dataparser-connector"></a><span data-ttu-id="c2045-129">手順 1: LivePerson Conversational Cloud DataParser コネクタをセットアップする</span><span class="sxs-lookup"><span data-stu-id="c2045-129">Step 1: Set up a LivePerson Conversational Cloud DataParser connector</span></span>

<span data-ttu-id="c2045-130">最初の手順は、Microsoft 365 コンプライアンス センター の [データ コネクタ] ページにアクセスし、LivePerson Conversational Cloud データ用の 17a-4 コネクタを作成することです。</span><span class="sxs-lookup"><span data-stu-id="c2045-130">The first step is to access to the Data connectors page in the Microsoft 365 compliance center and create a 17a-4 connector for LivePerson Conversational Cloud data.</span></span>

1. <span data-ttu-id="c2045-131">に移動 <https://compliance.microsoft.com> し、[**データ** コネクタ  >  **LivePerson Conversational Cloud DataParser] をクリックします**。</span><span class="sxs-lookup"><span data-stu-id="c2045-131">Go to <https://compliance.microsoft.com> and then click **Data connectors** > **LivePerson Conversational Cloud DataParser**.</span></span>

2. <span data-ttu-id="c2045-132">**LivePerson Conversational Cloud DataParser** 製品の説明ページで、[コネクタの追加]**をクリックします**。</span><span class="sxs-lookup"><span data-stu-id="c2045-132">On the **LivePerson Conversational Cloud DataParser** product description page, click **Add connector**.</span></span>

3. <span data-ttu-id="c2045-133">[サービス条件 **] ページで、[** 同意する] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="c2045-133">On the **Terms of service** page, click **Accept**.</span></span>

4. <span data-ttu-id="c2045-134">コネクタを識別する一意の名前を入力し、[次へ] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="c2045-134">Enter a unique name that identifies the connector and then click **Next**.</span></span>

5. <span data-ttu-id="c2045-135">17a-4 アカウントにサインインし、LivePerson Conversational Cloud DataParser 接続ウィザードの手順を完了します。</span><span class="sxs-lookup"><span data-stu-id="c2045-135">Sign in to your 17a-4 account and complete the steps in the LivePerson Conversational Cloud DataParser connection wizard.</span></span>

## <a name="step-2-configure-the-liveperson-conversational-cloud-dataparser-connector"></a><span data-ttu-id="c2045-136">手順 2: LivePerson Conversational Cloud DataParser コネクタを構成する</span><span class="sxs-lookup"><span data-stu-id="c2045-136">Step 2: Configure the LivePerson Conversational Cloud DataParser connector</span></span>

<span data-ttu-id="c2045-137">17a-4 サポートを使用して LivePerson Conversational Cloud DataParser コネクタを構成します。</span><span class="sxs-lookup"><span data-stu-id="c2045-137">Work with 17a-4 Support to configure the LivePerson Conversational Cloud DataParser connector.</span></span>

## <a name="step-3-map-users"></a><span data-ttu-id="c2045-138">手順 3: ユーザーをマップする</span><span class="sxs-lookup"><span data-stu-id="c2045-138">Step 3: Map users</span></span>

<span data-ttu-id="c2045-139">LivePerson Conversational Cloud DataParser コネクタは、ユーザーにデータをインポートする前に、Microsoft 365 メール アドレスにユーザーを自動的にマップMicrosoft 365。</span><span class="sxs-lookup"><span data-stu-id="c2045-139">The LivePerson Conversational Cloud DataParser connector will automatically map users to their Microsoft 365 email addresses before importing data to Microsoft 365.</span></span>

## <a name="step-4-monitor-the-liveperson-conversational-cloud-dataparser-connector"></a><span data-ttu-id="c2045-140">手順 4: LivePerson Conversational Cloud DataParser コネクタを監視する</span><span class="sxs-lookup"><span data-stu-id="c2045-140">Step 4: Monitor the LivePerson Conversational Cloud DataParser connector</span></span>

<span data-ttu-id="c2045-141">LivePerson Conversational Cloud DataParser コネクタを作成した後は、コネクタの状態を [スレッド] Microsoft 365 コンプライアンス センター。</span><span class="sxs-lookup"><span data-stu-id="c2045-141">After you create a LivePerson Conversational Cloud DataParser connector, you can view the connector status in the Microsoft 365 compliance center.</span></span>

1. <span data-ttu-id="c2045-142">左側の <https://compliance.microsoft.com> ナビゲーションで [ **データ コネクタ] に** 移動してクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2045-142">Go to <https://compliance.microsoft.com> and click **Data connectors** in the left nav.</span></span>

2. <span data-ttu-id="c2045-143">[コネクタ **] タブを** クリックし、作成した LivePerson Conversational Cloud DataParser コネクタを選択して、コネクタのプロパティと情報を含むフライアウト ページを表示します。</span><span class="sxs-lookup"><span data-stu-id="c2045-143">Click the **Connectors** tab and then select the LivePerson Conversational Cloud DataParser connector that you created to display the flyout page, which contains the properties and information about the connector.</span></span>

3. <span data-ttu-id="c2045-144">[**ソースを含むコネクタの状態**] で、[ログのダウンロード] リンクをクリックして、コネクタの状態ログを開く (または保存) します。 </span><span class="sxs-lookup"><span data-stu-id="c2045-144">Under **Connector status with source**, click the **Download log** link to open (or save) the status log for the connector.</span></span> <span data-ttu-id="c2045-145">このログには、Microsoft クラウドにインポートされたデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c2045-145">This log contains data that has been imported to the Microsoft cloud.</span></span>

## <a name="known-issues"></a><span data-ttu-id="c2045-146">既知の問題</span><span class="sxs-lookup"><span data-stu-id="c2045-146">Known issues</span></span>

<span data-ttu-id="c2045-147">現時点では、10 MB を超える添付ファイルやアイテムのインポートはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c2045-147">At this time, we don't support importing attachments or items that are larger than 10 MB.</span></span> <span data-ttu-id="c2045-148">大きいアイテムのサポートは、後日利用できます。</span><span class="sxs-lookup"><span data-stu-id="c2045-148">Support for larger items will be available at a later date.</span></span>
