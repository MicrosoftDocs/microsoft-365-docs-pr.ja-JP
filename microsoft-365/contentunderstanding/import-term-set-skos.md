---
title: SKOS ベースの形式を使用して用語セットをインポートする
description: SKOS ベースのフォーマットを使用して用語セットをインポートする方法を学ぶ
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.service: ''
ms.collection: enabler-strategic
search.appverid: ''
localization_priority: Priority
ms.openlocfilehash: ba0f240caa8b3452783436e9a35c53d44baba894
ms.sourcegitcommit: 162c01dfaa2fdb3225ce4c24964c1065ce22ed5d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2021
ms.locfileid: "49976437"
---
# <a name="import-a-term-set-using-a-skos-based-format"></a><span data-ttu-id="7860b-103">SKOS ベースの形式を使用して用語セットをインポートする</span><span class="sxs-lookup"><span data-stu-id="7860b-103">Import a term set using a SKOS-based format</span></span>

<span data-ttu-id="7860b-104">SKOS ベースの形式を使用して用語セットをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="7860b-104">You can import a term set using a SKOS-based format.</span></span> <span data-ttu-id="7860b-105">形式の詳細については、[SharePoint 分類 SKOS フォーマットのリファレンス](skos-format-reference.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7860b-105">For details about the format, see [SharePoint taxonomy SKOS format reference](skos-format-reference.md).</span></span>

<span data-ttu-id="7860b-106">インポートファイルは 20,000 語未満に保つことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7860b-106">We recommend keeping your import files to less than 20,000 terms.</span></span> <span data-ttu-id="7860b-107">ファイルが大きいと、検証とインポートにかかる時間が長くなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7860b-107">Larger files can increase the time taken for validation and import.</span></span>

1. <span data-ttu-id="7860b-108">SharePoint 管理センターで、[**コンテンツサービス**] を展開し、**用語ストア** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7860b-108">In the SharePoint admin center, expand **Content services**, and then click **Term store**.</span></span>

2. <span data-ttu-id="7860b-109">用語セットをインポートする用語グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="7860b-109">Select the term group where you want to import the term set.</span></span>

3. <span data-ttu-id="7860b-110">コマンドバーで、[**用語セットのインポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7860b-110">In the command bar, click **Import term set**.</span></span>
 
4.  <span data-ttu-id="7860b-111">テンプレートとして使用するサンプルファイルをダウンロードする場合は、**sample-metadata.ttl** をクリックして、SKOS ベースの形式を使用するサンプル ファイルを取得します。</span><span class="sxs-lookup"><span data-stu-id="7860b-111">If you want to download a sample file to use as a template, click **sample-metadata.ttl** to get a sample file that uses the SKOS-based format.</span></span>
 
5.  <span data-ttu-id="7860b-112">インポートする用語セットと、用語を含むインポートファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7860b-112">Create the import file that contains the term sets & terms you wish to import.</span></span>

6.  <span data-ttu-id="7860b-113">[**ファイル形式**]で、[**SKOS (\*.ttl)**]を選択します。</span><span class="sxs-lookup"><span data-stu-id="7860b-113">Under **File format**, select **SKOS (\*.ttl)**.</span></span>

7.  <span data-ttu-id="7860b-114">[**参照**] をクリックして、インポートファイルに移動して追加します。</span><span class="sxs-lookup"><span data-stu-id="7860b-114">Click **Browse** and navigate to and add your import file.</span></span>

8.  <span data-ttu-id="7860b-115">[**インポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7860b-115">Click **Import**.</span></span> <span data-ttu-id="7860b-116">インポートが完了するまでパネルを閉じないでください。</span><span class="sxs-lookup"><span data-stu-id="7860b-116">Do not close the panel until the import completes.</span></span>

<span data-ttu-id="7860b-117">ファイルのインポートが成功すると、成功メッセージが表示され、用語ストアが更新され、新しく作成された用語セットに移動できます。</span><span class="sxs-lookup"><span data-stu-id="7860b-117">On successful import of the file, a success message will be displayed, and the term store will refresh and you can navigate to the newly created term sets.</span></span>

## <a name="see-also"></a><span data-ttu-id="7860b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7860b-118">See also</span></span>

[<span data-ttu-id="7860b-119">管理されたメタデータの概要</span><span class="sxs-lookup"><span data-stu-id="7860b-119">Introduction to managed metadata</span></span>](https://docs.microsoft.com/sharepoint/managed-metadata)

[<span data-ttu-id="7860b-120">ドキュメント理解の概要</span><span class="sxs-lookup"><span data-stu-id="7860b-120">Document understanding overview</span></span>](document-understanding-overview.md)

[<span data-ttu-id="7860b-121">用語セット (サイトレベル) をインポートする</span><span class="sxs-lookup"><span data-stu-id="7860b-121">Import term sets (site level)</span></span>](https://support.microsoft.com/office/168fbc86-7fce-4288-9a1f-b83fc3921c18)
