---
title: 高度な検索 Api
description: Microsoft の脅威保護 API を使用して高度な検索クエリを実行する方法について説明します。
keywords: 高度な検索、Api、api、MTP
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: dd7b02200e370588bbb9470a3d7e897b30234ead
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/22/2020
ms.locfileid: "48197811"
---
# <a name="advanced-hunting-apis"></a><span data-ttu-id="7bde5-104">高度な検索 Api</span><span class="sxs-lookup"><span data-stu-id="7bde5-104">Advanced hunting APIs</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


<span data-ttu-id="7bde5-105">**適用対象:**</span><span class="sxs-lookup"><span data-stu-id="7bde5-105">**Applies to:**</span></span>
- <span data-ttu-id="7bde5-106">Microsoft Threat Protection</span><span class="sxs-lookup"><span data-stu-id="7bde5-106">Microsoft Threat Protection</span></span>

>[!IMPORTANT] 
><span data-ttu-id="7bde5-107">一部の情報は、市販される前に大幅に変更される可能性がある prereleased 製品に関連しています。</span><span class="sxs-lookup"><span data-stu-id="7bde5-107">Some information relates to prereleased product which may be substantially modified before it's commercially released.</span></span> <span data-ttu-id="7bde5-108">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span><span class="sxs-lookup"><span data-stu-id="7bde5-108">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>

## <a name="limitations"></a><span data-ttu-id="7bde5-109">制限事項</span><span class="sxs-lookup"><span data-stu-id="7bde5-109">Limitations</span></span>
1. <span data-ttu-id="7bde5-110">クエリは、過去30日間のデータに対してのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="7bde5-110">You can only run a query on data from the last 30 days.</span></span>
2. <span data-ttu-id="7bde5-111">結果には最大10万行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7bde5-111">The results will include a maximum of 100,000 rows.</span></span>
3. <span data-ttu-id="7bde5-112">実行回数は、テナントによって制限されます。1分あたり最大10件の通話、1時間ごとに10分の時間、実行時間は1日に4時間。</span><span class="sxs-lookup"><span data-stu-id="7bde5-112">The number of executions is limited per tenant: up to 10 calls per minute, 10 minutes of running time every hour and 4 hours of running time a day.</span></span>
4. <span data-ttu-id="7bde5-113">1回の要求の最大実行時間は10分です。</span><span class="sxs-lookup"><span data-stu-id="7bde5-113">The maximal execution time of a single request is 10 minutes.</span></span>
5. <span data-ttu-id="7bde5-114">429応答は、要求数または CPU によってクォータ制限値に達したことを表します。</span><span class="sxs-lookup"><span data-stu-id="7bde5-114">429 response will represent reaching quota limit either by number of requests or by CPU.</span></span> <span data-ttu-id="7bde5-115">また、429応答本文は、クォータが更新されるまでの時間も示します。</span><span class="sxs-lookup"><span data-stu-id="7bde5-115">The 429 response body will also indicate the time until the quota is renewed.</span></span> 


## <a name="permissions"></a><span data-ttu-id="7bde5-116">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="7bde5-116">Permissions</span></span>
<span data-ttu-id="7bde5-117">この API を呼び出すには、次のいずれかのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="7bde5-117">One of the following permissions is required to call this API.</span></span> <span data-ttu-id="7bde5-118">アクセス許可の選択方法を含む詳細については、「 [Microsoft の脅威保護 api にアクセス](api-access.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7bde5-118">To learn more, including how to choose permissions, see [Access the Microsoft Threat Protection APIs](api-access.md)</span></span>

<span data-ttu-id="7bde5-119">アクセス許可の種類</span><span class="sxs-lookup"><span data-stu-id="7bde5-119">Permission type</span></span> |   <span data-ttu-id="7bde5-120">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="7bde5-120">Permission</span></span>  |   <span data-ttu-id="7bde5-121">アクセス許可の表示名</span><span class="sxs-lookup"><span data-stu-id="7bde5-121">Permission display name</span></span>
:---|:---|:---
<span data-ttu-id="7bde5-122">アプリケーション</span><span class="sxs-lookup"><span data-stu-id="7bde5-122">Application</span></span> |   <span data-ttu-id="7bde5-123">AdvancedHunting</span><span class="sxs-lookup"><span data-stu-id="7bde5-123">AdvancedHunting.Read.All</span></span> |  <span data-ttu-id="7bde5-124">[高度なクエリを実行する]</span><span class="sxs-lookup"><span data-stu-id="7bde5-124">'Run advanced queries'</span></span>
<span data-ttu-id="7bde5-125">委任 (職場または学校のアカウント)</span><span class="sxs-lookup"><span data-stu-id="7bde5-125">Delegated (work or school account)</span></span> | <span data-ttu-id="7bde5-126">AdvancedHunting</span><span class="sxs-lookup"><span data-stu-id="7bde5-126">AdvancedHunting.Read</span></span> | <span data-ttu-id="7bde5-127">[高度なクエリを実行する]</span><span class="sxs-lookup"><span data-stu-id="7bde5-127">'Run advanced queries'</span></span>

>[!Note]
> <span data-ttu-id="7bde5-128">ユーザー資格情報を使用してトークンを取得する場合:</span><span class="sxs-lookup"><span data-stu-id="7bde5-128">When obtaining a token using user credentials:</span></span>
>- <span data-ttu-id="7bde5-129">ユーザーは ' View Data ' AD の役割を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7bde5-129">The user needs to have 'View Data' AD role</span></span>
>- <span data-ttu-id="7bde5-130">ユーザーはデバイスグループの設定に基づいて、デバイスへのアクセス権を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7bde5-130">The user needs to have access to the device, based on device group settings.</span></span>

## <a name="http-request"></a><span data-ttu-id="7bde5-131">HTTP 要求</span><span class="sxs-lookup"><span data-stu-id="7bde5-131">HTTP request</span></span>
```
POST https://api.security.microsoft.com/api/advancedhunting/run
```

## <a name="request-headers"></a><span data-ttu-id="7bde5-132">要求ヘッダー</span><span class="sxs-lookup"><span data-stu-id="7bde5-132">Request headers</span></span>

<span data-ttu-id="7bde5-133">ヘッダー</span><span class="sxs-lookup"><span data-stu-id="7bde5-133">Header</span></span> | <span data-ttu-id="7bde5-134">値</span><span class="sxs-lookup"><span data-stu-id="7bde5-134">Value</span></span> 
:---|:---
<span data-ttu-id="7bde5-135">Authorization</span><span class="sxs-lookup"><span data-stu-id="7bde5-135">Authorization</span></span> | <span data-ttu-id="7bde5-136">ベアラー {token}。</span><span class="sxs-lookup"><span data-stu-id="7bde5-136">Bearer {token}.</span></span> <span data-ttu-id="7bde5-137">**必須**。</span><span class="sxs-lookup"><span data-stu-id="7bde5-137">**Required**.</span></span>
<span data-ttu-id="7bde5-138">Content-Type</span><span class="sxs-lookup"><span data-stu-id="7bde5-138">Content-Type</span></span>    | <span data-ttu-id="7bde5-139">application/json</span><span class="sxs-lookup"><span data-stu-id="7bde5-139">application/json</span></span>

## <a name="request-body"></a><span data-ttu-id="7bde5-140">要求本文</span><span class="sxs-lookup"><span data-stu-id="7bde5-140">Request body</span></span>
<span data-ttu-id="7bde5-141">要求本文で、次のパラメーターを使用して JSON オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="7bde5-141">In the request body, supply a JSON object with the following parameters:</span></span>

<span data-ttu-id="7bde5-142">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7bde5-142">Parameter</span></span> | <span data-ttu-id="7bde5-143">種類</span><span class="sxs-lookup"><span data-stu-id="7bde5-143">Type</span></span>    | <span data-ttu-id="7bde5-144">説明</span><span class="sxs-lookup"><span data-stu-id="7bde5-144">Description</span></span>
:---|:---|:---
<span data-ttu-id="7bde5-145">クエリ</span><span class="sxs-lookup"><span data-stu-id="7bde5-145">Query</span></span> | <span data-ttu-id="7bde5-146">テキスト</span><span class="sxs-lookup"><span data-stu-id="7bde5-146">Text</span></span> |  <span data-ttu-id="7bde5-147">実行するクエリを示します。</span><span class="sxs-lookup"><span data-stu-id="7bde5-147">The query to run.</span></span> <span data-ttu-id="7bde5-148">**必須**。</span><span class="sxs-lookup"><span data-stu-id="7bde5-148">**Required**.</span></span>

## <a name="response"></a><span data-ttu-id="7bde5-149">応答</span><span class="sxs-lookup"><span data-stu-id="7bde5-149">Response</span></span>
<span data-ttu-id="7bde5-150">成功した場合、このメソッドは 200 OK を返し、応答本文で _Queryresponse_ オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="7bde5-150">If successful, this method returns 200 OK, and _QueryResponse_ object in the response body.</span></span> <br><br>

<span data-ttu-id="7bde5-151">Response オブジェクトは3つの部分 (プロパティ) に分かれています。</span><span class="sxs-lookup"><span data-stu-id="7bde5-151">The response object is divided to 3 parts (properties):</span></span><br>
1) <span data-ttu-id="7bde5-152">```Stats``` -クエリパフォーマンス統計。</span><span class="sxs-lookup"><span data-stu-id="7bde5-152">```Stats``` - Query performance statistics.</span></span><br>
2) <span data-ttu-id="7bde5-153">```Schema``` -応答のスキーマ。各列の名前の種類のペアのリスト。</span><span class="sxs-lookup"><span data-stu-id="7bde5-153">```Schema``` - The schema of the response, a list of Name-Type pairs for each column.</span></span> <br>
3) <span data-ttu-id="7bde5-154">```Results``` -高度な検索イベントのリスト。</span><span class="sxs-lookup"><span data-stu-id="7bde5-154">```Results``` - A list of Advanced Hunting events.</span></span>

## <a name="example"></a><span data-ttu-id="7bde5-155">例</span><span class="sxs-lookup"><span data-stu-id="7bde5-155">Example</span></span>

<span data-ttu-id="7bde5-156">要求</span><span class="sxs-lookup"><span data-stu-id="7bde5-156">Request</span></span>

<span data-ttu-id="7bde5-157">以下は、要求の例です。</span><span class="sxs-lookup"><span data-stu-id="7bde5-157">Here is an example of the request.</span></span>


```json
{
    "Query":"DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2"
}

```

<span data-ttu-id="7bde5-158">応答</span><span class="sxs-lookup"><span data-stu-id="7bde5-158">Response</span></span>

<span data-ttu-id="7bde5-159">以下は、応答の例です。</span><span class="sxs-lookup"><span data-stu-id="7bde5-159">Here is an example of the response.</span></span>


```json
{
    "Stats": {
        "ExecutionTime": 4.621215,
        "resource_usage": {
            "cache": {
                "memory": {
                    "hits": 773461,
                    "misses": 4481,
                    "total": 777942
                },
                "disk": {
                    "hits": 994,
                    "misses": 197,
                    "total": 1191
                }
            },
            "cpu": {
                "user": "00:00:19.0468750",
                "kernel": "00:00:00.0156250",
                "total cpu": "00:00:19.0625000"
            },
            "memory": {
                "peak_per_node": 236822432
            }
        },
        "dataset_statistics": [
            {
                "table_row_count": 2,
                "table_size": 102
            }
        ]
    },
    "Schema": [
        {
            "Name": "Timestamp",
            "Type": "DateTime"
        },
        {
            "Name": "FileName",
            "Type": "String"
        },
        {
            "Name": "InitiatingProcessFileName",
            "Type": "String"
        }
    ],
    "Results": [
        {
            "Timestamp": "2020-08-30T06:38:35.7664356Z",
            "FileName": "conhost.exe",
            "InitiatingProcessFileName": "powershell.exe"
        },
        {
            "Timestamp": "2020-08-30T06:38:30.5163363Z",
            "FileName": "conhost.exe",
            "InitiatingProcessFileName": "powershell.exe"
        }
    ]
}

```

## <a name="related-topic"></a><span data-ttu-id="7bde5-160">関連トピック</span><span class="sxs-lookup"><span data-stu-id="7bde5-160">Related topic</span></span>
- [<span data-ttu-id="7bde5-161">Microsoft の脅威保護 Api にアクセスする</span><span class="sxs-lookup"><span data-stu-id="7bde5-161">Access the Microsoft Threat Protection APIs</span></span>](api-access.md)