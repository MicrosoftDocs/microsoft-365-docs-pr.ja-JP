---
title: 手順 2.  契約Microsoft Teamsチャネルを作成するには、次の情報を使用します。
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: 05/10/2021
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
description: カスタム ソリューションを使用してMicrosoft Teams管理チャネルを作成する方法について説明Microsoft 365します。
ms.openlocfilehash: a97f6a77818fc53aa28a5924b97e3c7309d01e3a
ms.sourcegitcommit: 8e4c107e4da3a00be0511b05bc655a98fe871a54
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2021
ms.locfileid: "52281194"
---
# <a name="step-2-use-microsoft-teams-to-create-your-contract-management-channel"></a><span data-ttu-id="7e28a-104">手順 2.</span><span class="sxs-lookup"><span data-stu-id="7e28a-104">Step 2.</span></span> <span data-ttu-id="7e28a-105">契約Microsoft Teamsチャネルを作成するには、次の情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e28a-105">Use Microsoft Teams to create your contract management channel</span></span>

<span data-ttu-id="7e28a-106">組織が契約管理ソリューションをセットアップする場合は、関係者が契約を確認および管理できる中心的な場所が必要です。</span><span class="sxs-lookup"><span data-stu-id="7e28a-106">When your organization sets up a contracts management solution, you need a central location in which stakeholders can review and manage contracts.</span></span> <span data-ttu-id="7e28a-107">この目的のために、Microsoft Teams[を使用](https://docs.microsoft.com/microsoftteams/)して、Teamsチャネルを設定し、Teams使用できます。</span><span class="sxs-lookup"><span data-stu-id="7e28a-107">For this purpose, you can use [Microsoft Teams](https://docs.microsoft.com/microsoftteams/) to set up a Teams channel and use the features in Teams to:</span></span>

- <span data-ttu-id="7e28a-108">**関係者がアクションを必要とするすべての契約を簡単に確認できる場所を作成します。**</span><span class="sxs-lookup"><span data-stu-id="7e28a-108">**Create a location for stakeholders to easily see all contracts that require action.**</span></span> <span data-ttu-id="7e28a-109">たとえば、Teams契約管理チャネルに [契約]タブを作成し、承認が必要なすべての契約の便利なタイル ビューをメンバーに表示できます。</span><span class="sxs-lookup"><span data-stu-id="7e28a-109">For example, in Teams you can create a **Contracts** tab in the Contract Management channel in which members can see a useful tile view of all contracts that need approval.</span></span> <span data-ttu-id="7e28a-110">また、各 "カード" に重要なデータ (クライアント、契約者、手数料など)が一覧表示されるビュー *を構成することもできます*。</span><span class="sxs-lookup"><span data-stu-id="7e28a-110">You can also configure the view so that each "card" lists the important data you care about (such as *Client*, *Contractor*, and *Fee amount*).</span></span>

     ![[契約] タブ。](../media/content-understanding/tile-view.png)

- <span data-ttu-id="7e28a-112">**メンバーが互いに対話し、重要なイベントを表示するための場所を持つ。**</span><span class="sxs-lookup"><span data-stu-id="7e28a-112">**Have a location for members to interact with each other and see important events.**</span></span> <span data-ttu-id="7e28a-113">たとえば、Teams[投稿] タブを使用して、会話を行い、更新プログラムを取得し、アクション (契約を拒否するメンバーなど) を表示できます。</span><span class="sxs-lookup"><span data-stu-id="7e28a-113">For example, in Teams, the **Posts** tab can be used to have conversations, get updates, and see actions (such as a member rejecting a contract).</span></span> <span data-ttu-id="7e28a-114">何かが発生した場合 (承認のために提出された新しい契約など)は、[投稿] タブを使用して、それをアナウンスするだけでなく、その記録を保持することもできます。</span><span class="sxs-lookup"><span data-stu-id="7e28a-114">When something has happened (such as a new contract submitted for approval), the **Posts** tab can be used not only to announce it, but also to keep a record of it.</span></span> <span data-ttu-id="7e28a-115">また、メンバーが通知を購読すると、更新が行されるたびに通知が届く。</span><span class="sxs-lookup"><span data-stu-id="7e28a-115">And if members subscribe to notifications, they'll get notified whenever there's an update.</span></span> 

     ![[投稿] タブ。](../media/content-understanding/posts.png)</br> 

- <span data-ttu-id="7e28a-117">**承認された契約をメンバーが支払いのためにいつ提出できるのか知る場所をメンバーに提供します。**</span><span class="sxs-lookup"><span data-stu-id="7e28a-117">**Have a location for members to see approved contracts to know when they can be submitted for payment.**</span></span> <span data-ttu-id="7e28a-118">このTeams、支払いのために提出する必要があるすべての契約を一覧表示する For <b>Payment</b>チャネルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7e28a-118">In Teams, you can create a <b>For Payment</b> channel that will list all contracts that will need to be submitted to payment.</span></span> <span data-ttu-id="7e28a-119">このソリューションを簡単に拡張して、この情報をサードパーティの金融アプリケーション (Dynamics CRM など) に直接書き込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e28a-119">You can easily extend this solution to instead write this information directly to a third-party financial application (for example, Dynamics CRM).</span></span>

## <a name="attach-your-sharepoint-document-library-to-the-contracts-tab"></a><span data-ttu-id="7e28a-120">[契約] SharePointにドキュメント ライブラリを添付する</span><span class="sxs-lookup"><span data-stu-id="7e28a-120">Attach your SharePoint document library to the Contracts tab</span></span> 

<span data-ttu-id="7e28a-121">Contracts **Management チャネルで [契約]** タブを作成した後、ドキュメント ライブラリSharePoint [に添付する必要があります](https://support.microsoft.com/office/add-a-sharepoint-page-list-or-document-library-as-a-tab-in-teams-131edef1-455f-4c67-a8ce-efa2ebf25f0b)。</span><span class="sxs-lookup"><span data-stu-id="7e28a-121">After you create a **Contracts** tab in your Contracts Management channel, you need to [attach your SharePoint document library to it](https://support.microsoft.com/office/add-a-sharepoint-page-list-or-document-library-as-a-tab-in-teams-131edef1-455f-4c67-a8ce-efa2ebf25f0b).</span></span> <span data-ttu-id="7e28a-122">添付SharePointするドキュメント ライブラリは、前のセクションで syntex ドキュメントSharePointモデルを適用したドキュメント ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="7e28a-122">The SharePoint document library you want to attach is the one in which you applied your SharePoint Syntex document understanding model to in the previous section.</span></span>

<span data-ttu-id="7e28a-123">ドキュメント ライブラリにSharePointすると、既定のリスト ビューを使用して分類された契約を表示できます。</span><span class="sxs-lookup"><span data-stu-id="7e28a-123">After you attach the SharePoint document library, you'll be able to view any classified contracts through a default list view.</span></span>

   ![リスト ビュー。](../media/content-understanding/list-view.png) 

## <a name="customize-your-contracts-tab-tile-view"></a><span data-ttu-id="7e28a-125">[契約] タブのタイル ビューをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="7e28a-125">Customize your Contracts tab tile view</span></span>

<span data-ttu-id="7e28a-126">このTeamsタイル ビューで契約を表示することができますが、それをカスタマイズして、契約カードに表示する契約データを表示できます。</span><span class="sxs-lookup"><span data-stu-id="7e28a-126">While Teams lets you view your contracts in a tile view, you might want to customize it to view the contract data you want to make visible in the contract card.</span></span> <span data-ttu-id="7e28a-127">たとえば、[ **契約]** タブでは、メンバーが契約カードのクライアント、請負業者、および手数料の金額を確認することが重要です。</span><span class="sxs-lookup"><span data-stu-id="7e28a-127">For example, for the **Contracts** tab, it is important for members to see the client, contractor, and fee amount on the contract card.</span></span> <span data-ttu-id="7e28a-128">これらのフィールドはすべて、ドキュメント ライブラリに適用SharePoint Syntex モデルを通じて各コントラクトから抽出されました。</span><span class="sxs-lookup"><span data-stu-id="7e28a-128">All of these fields were extracted from each contract through your SharePoint Syntex model that was applied to your document library.</span></span> <span data-ttu-id="7e28a-129">また、タイル ヘッダー バーを各ステータスの異なる色に変更して、メンバーが承認プロセス内の契約の場所を簡単に確認できます。</span><span class="sxs-lookup"><span data-stu-id="7e28a-129">You also want to be able to change the tile header bar to different colors for each status so that members can easily see where the contract is in the approval process.</span></span> <span data-ttu-id="7e28a-130">たとえば、承認済みのすべての契約には青色のヘッダー バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e28a-130">For example, all approved contracts will have a blue header bar.</span></span>

   ![リスト ビュー。](../media/content-understanding/tile.png)

<span data-ttu-id="7e28a-132">使用するカスタム タイル ビューでは、現在のタイル ビューの書式設定に使用する JSON ファイルを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e28a-132">The custom tile view you use requires you to make changes to the JSON file used to format the current tile view.</span></span> <span data-ttu-id="7e28a-133">カード ビューの作成に使用する JSON ファイルを参照するには、ContractCard.js **をダウンロード** します。</span><span class="sxs-lookup"><span data-stu-id="7e28a-133">You can reference the JSON file used to create the card view by downloading the **ContractCard.json** file.</span></span> <span data-ttu-id="7e28a-134">次のセクションでは、コントラクト カード内の機能に関するコードの特定のセクションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e28a-134">In the following sections, you'll see specific sections of the code for features that are in the contract cards.</span></span>

<span data-ttu-id="7e28a-135">Teams チャネルのビューの JSON コードを表示または変更する場合は、Teams チャネルでビューのドロップダウン メニューを選択し、[現在のビューの書式設定] を選択します。 </span><span class="sxs-lookup"><span data-stu-id="7e28a-135">If you want to see or make changes to the JSON code for your view in your Teams channel, in the Teams channel, select the view drop-down menu, and then select **Format current view**.</span></span>

   ![json 形式。](../media/content-understanding/jason-format.png) 

## <a name="card-size-and-shape"></a><span data-ttu-id="7e28a-137">カードのサイズと図形</span><span class="sxs-lookup"><span data-stu-id="7e28a-137">Card size and shape</span></span>

<span data-ttu-id="7e28a-138">参照 zip **ファイルContractCard.js** ダウンロードしたファイルの詳細については、次のセクションを参照して、カードのサイズと図形の書式設定方法のコードを確認します。</span><span class="sxs-lookup"><span data-stu-id="7e28a-138">In the **ContractCard.json** file that you downloaded in the reference zip file, look at the following section to see the code for how the size and shape of the card is formatted.</span></span>

```JSON
                  {
                    "elmType": "div",
                    "style": {
                      "background-color": "#f5f5f5",
                      "padding": "5px",
                      "width": "180px"
                    },
                    "children": [
                      {
                        "elmType": "img",
                        "attributes": {
                          "src": "@thumbnail.large"
                        },
                        "style": {
                          "width": "185px",
                          "height": "248px"
                        }
                      }
```


## <a name="contract-status"></a><span data-ttu-id="7e28a-139">契約の状態</span><span class="sxs-lookup"><span data-stu-id="7e28a-139">Contract status</span></span>

<span data-ttu-id="7e28a-140">次のコードでは、各タイトル カードの状態を定義できます。</span><span class="sxs-lookup"><span data-stu-id="7e28a-140">The following code lets you define the status of each title card.</span></span> <span data-ttu-id="7e28a-141">各ステータス値 *(New、In* *review、Approved、\*\*および Rejected)* は、それぞれ異なる色コードを表示します。 </span><span class="sxs-lookup"><span data-stu-id="7e28a-141">Note that each status value (*New*, *In review*, *Approved*, and *Rejected*) will display a different color code for each.</span></span> <span data-ttu-id="7e28a-142">ダウンロードした **ContractCard.js** のセクションで、状態を定義するセクションを確認します。</span><span class="sxs-lookup"><span data-stu-id="7e28a-142">In the **ContractCard.json** file that you downloaded, look at the section that defines the status.</span></span>

```JSON
          {
            "elmType": "div",
            "children": [
              {
                "elmType": "div",
                "style": {
                  "color": "white",
                  "background-color": "=if([$Status] == 'New', '#00b7c3', if([$Status] == 'In review', '#ffaa44', if([$Status] == 'Approved', '#0078d4', if([$Status] == 'Rejected', '#d13438', '#8378de'))))",
                  "padding": "5px 15px",
                  "height": "auto",
                  "text-transform": "uppercase",
                  "font-size": "12.5px"
                },
                "txtContent": "[$Status]"
              }
```


## <a name="extracted-fields"></a><span data-ttu-id="7e28a-143">抽出されたフィールド</span><span class="sxs-lookup"><span data-stu-id="7e28a-143">Extracted fields</span></span>

<span data-ttu-id="7e28a-144">各契約カードには、契約ごとに抽出された 3 つのフィールド (*クライアント*、契約者、および手数料金額)*が表示されます*。</span><span class="sxs-lookup"><span data-stu-id="7e28a-144">Each contract card will display three fields that were extracted for each contract (*Client*, *Contractor*, and *Fee Amount*).</span></span> <span data-ttu-id="7e28a-145">さらに、ファイルの識別に使用される Syntex モデルによってファイルが分類SharePoint日付を表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e28a-145">Additionally, you also want to display the time/date that the file was classified by the SharePoint Syntex model used to identify it.</span></span> 

<span data-ttu-id="7e28a-146">ダウンロードした **ContractCard.js** で、次のセクションでは、これらのそれぞれを定義します。</span><span class="sxs-lookup"><span data-stu-id="7e28a-146">In the **ContractCard.json** file that you downloaded, the following sections define each of these.</span></span>

### <a name="client"></a><span data-ttu-id="7e28a-147">クライアント</span><span class="sxs-lookup"><span data-stu-id="7e28a-147">Client</span></span>

<span data-ttu-id="7e28a-148">このセクションでは、カードに "Client" を表示する方法を定義し、特定のコントラクトの値を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e28a-148">This section defines how "Client" will display on the card, and uses the value for the specific contract.</span></span>

```JSON
                      {
                        "elmType": "div",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px"
                        },
                        "txtContent": "Client"
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "16px",
                          "font-weight": "600"
                        },
                        "txtContent": "[$Client]"
                      },
```

### <a name="contractor"></a><span data-ttu-id="7e28a-149">請負業者</span><span class="sxs-lookup"><span data-stu-id="7e28a-149">Contractor</span></span>

<span data-ttu-id="7e28a-150">このセクションでは、"Contractor" がカードに表示される方法を定義し、特定の契約の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e28a-150">This section defines how the "Contractor" will display on the card, and uses the value for the specific contract.</span></span>

```JSON
                      {
                        "elmType": "div",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px"
                        },
                        "txtContent": "Client"
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "16px",
                          "font-weight": "600"
                        },
                        "txtContent": "[$Client]"
},
```


### <a name="fee-amount"></a><span data-ttu-id="7e28a-151">手数料金額</span><span class="sxs-lookup"><span data-stu-id="7e28a-151">Fee Amount</span></span>

<span data-ttu-id="7e28a-152">このセクションでは、カードに "手数料金額" を表示する方法を定義し、特定の契約の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e28a-152">This section defines how the "Fee Amount" will display on the card, and uses the value for the specific contract.</span></span>

```JSON
                      {
                        "elmType": "div",
                        "txtContent": "Fee amount",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px",
                          "margin-bottom": "2px"
                        }
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "14px"
                        },
                        "txtContent": "[$FeeAmount]"
                      },
```



### <a name="classification-date"></a><span data-ttu-id="7e28a-153">分類日</span><span class="sxs-lookup"><span data-stu-id="7e28a-153">Classification date</span></span>

<span data-ttu-id="7e28a-154">このセクションでは、カードに "分類" を表示する方法を定義し、特定のコントラクトの値を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e28a-154">This section defines how "Classification" will display on the card, and uses the value for the specific contract.</span></span>

```JSON
                      {
                        "elmType": "div",
                        "txtContent": "Classified",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px",
                          "margin-bottom": "2px"
                        }
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "14px"
                        },
                        "txtContent": "[$PrimeLastClassified]"
                      }
```

## <a name="next-step"></a><span data-ttu-id="7e28a-155">次の手順</span><span class="sxs-lookup"><span data-stu-id="7e28a-155">Next step</span></span>

[<span data-ttu-id="7e28a-156">手順 3.契約Power Automate処理するフローを作成するには、次の情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e28a-156">Step 3. Use Power Automate to create your flow to process your contracts</span></span>](solution-manage-contracts-step3.md)