---
title: Python API ガイドを使用した高度なハンティング
ms.reviewer: ''
description: 例を使用して、Python を使用して Microsoft Defender for Endpoint API を使用してクエリを実行する方法について説明します。
keywords: apis、サポートされている API、高度な検索、クエリ
search.product: eADQiWindows 10XVcnh
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 17ad28121935adfc958629f7999311c11a8d784e
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2021
ms.locfileid: "52771449"
---
# <a name="advanced-hunting-using-python"></a><span data-ttu-id="9dbd3-104">Python を使用した高度な追求</span><span class="sxs-lookup"><span data-stu-id="9dbd3-104">Advanced Hunting using Python</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

<span data-ttu-id="9dbd3-105">**適用対象:** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)</span><span class="sxs-lookup"><span data-stu-id="9dbd3-105">**Applies to:** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)</span></span>

- <span data-ttu-id="9dbd3-106">Microsoft Defender ATP を試してみたいですか?</span><span class="sxs-lookup"><span data-stu-id="9dbd3-106">Want to experience Microsoft Defender for Endpoint?</span></span> [<span data-ttu-id="9dbd3-107">無料試用版にサインアップしてください。</span><span class="sxs-lookup"><span data-stu-id="9dbd3-107">Sign up for a free trial.</span></span>](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

<span data-ttu-id="9dbd3-108">Python を使用して高度なクエリを実行するには [、「Advanced Hunting API」を参照してください](run-advanced-query-api.md)。</span><span class="sxs-lookup"><span data-stu-id="9dbd3-108">Run advanced queries using Python, see [Advanced Hunting API](run-advanced-query-api.md).</span></span>

<span data-ttu-id="9dbd3-109">このセクションでは、Python サンプルを共有してトークンを取得し、それを使用してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="9dbd3-109">In this section, we share Python samples to retrieve a token and use it to run a query.</span></span>

><span data-ttu-id="9dbd3-110">**前提条件**: 最初にアプリを [作成する必要があります](apis-intro.md)。</span><span class="sxs-lookup"><span data-stu-id="9dbd3-110">**Prerequisite**: You first need to [create an app](apis-intro.md).</span></span>

## <a name="get-token"></a><span data-ttu-id="9dbd3-111">トークンの取得</span><span class="sxs-lookup"><span data-stu-id="9dbd3-111">Get token</span></span>

- <span data-ttu-id="9dbd3-112">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9dbd3-112">Run the following commands:</span></span>

```

import json
import urllib.request
import urllib.parse

tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here

url = "https://login.microsoftonline.com/%s/oauth2/token" % (tenantId)

resourceAppIdUri = 'https://api.securitycenter.microsoft.com'

body = {
    'resource' : resourceAppIdUri,
    'client_id' : appId,
    'client_secret' : appSecret,
    'grant_type' : 'client_credentials'
}

data = urllib.parse.urlencode(body).encode("utf-8")

req = urllib.request.Request(url, data)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
aadToken = jsonResponse["access_token"]

```

<span data-ttu-id="9dbd3-113">どこ</span><span class="sxs-lookup"><span data-stu-id="9dbd3-113">where</span></span>
- <span data-ttu-id="9dbd3-114">tenantId: クエリを実行するテナントの ID (つまり、このテナントのデータに対してクエリが実行されます)</span><span class="sxs-lookup"><span data-stu-id="9dbd3-114">tenantId: ID of the tenant on behalf of which you want to run the query (that is, the query will be run on the data of this tenant)</span></span>
- <span data-ttu-id="9dbd3-115">appId: Azure AD アプリの ID (アプリには、Microsoft Defender for Endpoint への 「高度なクエリの実行」 アクセス許可が必要です)</span><span class="sxs-lookup"><span data-stu-id="9dbd3-115">appId: ID of your Azure AD app (the app must have 'Run advanced queries' permission to Microsoft Defender for Endpoint)</span></span>
- <span data-ttu-id="9dbd3-116">appSecret: Azure アプリAD秘密</span><span class="sxs-lookup"><span data-stu-id="9dbd3-116">appSecret: Secret of your Azure AD app</span></span>

## <a name="run-query"></a><span data-ttu-id="9dbd3-117">クエリの実行</span><span class="sxs-lookup"><span data-stu-id="9dbd3-117">Run query</span></span>

 <span data-ttu-id="9dbd3-118">次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="9dbd3-118">Run the following query:</span></span>

```
query = 'RegistryEvents | limit 10' # Paste your own query here

url = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"
headers = { 
    'Content-Type' : 'application/json',
    'Accept' : 'application/json',
    'Authorization' : "Bearer " + aadToken
}

data = json.dumps({ 'Query' : query }).encode("utf-8")

req = urllib.request.Request(url, data, headers)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
schema = jsonResponse["Schema"]
results = jsonResponse["Results"]

```

- <span data-ttu-id="9dbd3-119">schema には、クエリの結果のスキーマが含まれている</span><span class="sxs-lookup"><span data-stu-id="9dbd3-119">schema contains the schema of the results of your query</span></span>
- <span data-ttu-id="9dbd3-120">結果にはクエリの結果が含まれる</span><span class="sxs-lookup"><span data-stu-id="9dbd3-120">results contain the results of your query</span></span>

### <a name="complex-queries"></a><span data-ttu-id="9dbd3-121">複雑なクエリ</span><span class="sxs-lookup"><span data-stu-id="9dbd3-121">Complex queries</span></span>

<span data-ttu-id="9dbd3-122">複雑なクエリ (または複数行クエリ) を実行する場合は、クエリをファイルに保存し、上記のサンプルの最初の行ではなく、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9dbd3-122">If you want to run complex queries (or multilines queries), save your query in a file and, instead of the first line in the above sample, run the below command:</span></span>

```
queryFile = open("D:\\Temp\\myQuery.txt", 'r') # Replace with the path to your file
query = queryFile.read()
queryFile.close()
```

## <a name="work-with-query-results"></a><span data-ttu-id="9dbd3-123">クエリ結果を操作する</span><span class="sxs-lookup"><span data-stu-id="9dbd3-123">Work with query results</span></span>

<span data-ttu-id="9dbd3-124">これで、クエリ結果を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9dbd3-124">You can now use the query results.</span></span>

<span data-ttu-id="9dbd3-125">結果を反復処理するには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="9dbd3-125">To iterate over the results do the below:</span></span>

```
for result in results:
    print(result) # Prints the whole result
    print(result["EventTime"]) # Prints only the property 'EventTime' from the result


```


<span data-ttu-id="9dbd3-126">クエリの結果を CSV 形式でファイル形式で出力するにはfile1.csvを実行します。</span><span class="sxs-lookup"><span data-stu-id="9dbd3-126">To output the results of the query in CSV format in file file1.csv do the below:</span></span>

```
import csv

outputFile = open("D:\\Temp\\file1.csv", 'w')
output = csv.writer(outputFile)
output.writerow(results[0].keys())
for result in results:
    output.writerow(result.values())

outputFile.close()
```

<span data-ttu-id="9dbd3-127">クエリの結果を JSON 形式でファイル形式で出力するには、file1.jsを実行します。</span><span class="sxs-lookup"><span data-stu-id="9dbd3-127">To output the results of the query in JSON format in file file1.json do the below:</span></span>

```
outputFile = open("D:\\Temp\\file1.json", 'w')
json.dump(results, outputFile)
outputFile.close()
```


## <a name="related-topic"></a><span data-ttu-id="9dbd3-128">関連トピック</span><span class="sxs-lookup"><span data-stu-id="9dbd3-128">Related topic</span></span>
- [<span data-ttu-id="9dbd3-129">エンドポイント API 用 Microsoft Defender</span><span class="sxs-lookup"><span data-stu-id="9dbd3-129">Microsoft Defender for Endpoint APIs</span></span>](apis-intro.md)
- [<span data-ttu-id="9dbd3-130">高度な追及 API</span><span class="sxs-lookup"><span data-stu-id="9dbd3-130">Advanced Hunting API</span></span>](run-advanced-query-api.md)
- [<span data-ttu-id="9dbd3-131">PowerShell を使用した高度な追求</span><span class="sxs-lookup"><span data-stu-id="9dbd3-131">Advanced Hunting using PowerShell</span></span>](run-advanced-query-sample-powershell.md)
