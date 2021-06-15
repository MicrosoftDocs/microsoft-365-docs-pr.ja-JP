---
title: GetByUniqueId
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: reference
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection: m365initiative-syntex
localization_priority: Priority
description: REST APIを使用して、SharePoint Syntex ドキュメント理解モデルに関する情報を取得または更新します。
ms.openlocfilehash: aa97e0fde57c6d5200b437a8f9c7187c0980cc5b
ms.sourcegitcommit: 33d19853a38dfa4e6ed21b313976643670a14581
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2021
ms.locfileid: "52904312"
---
# <a name="getbyuniqueid"></a><span data-ttu-id="24f54-103">GetByUniqueId</span><span class="sxs-lookup"><span data-stu-id="24f54-103">GetByUniqueId</span></span>

<span data-ttu-id="24f54-104">SharePoint Syntex ドキュメント理解モデルに関する情報を取得または更新します ( [例](rest-getbyuniqueid-method.md#examples)参照)。</span><span class="sxs-lookup"><span data-stu-id="24f54-104">Gets or updates information about a SharePoint Syntex document understanding model (see [example](rest-getbyuniqueid-method.md#examples)).</span></span>

## <a name="http-request"></a><span data-ttu-id="24f54-105">HTTP 要求</span><span class="sxs-lookup"><span data-stu-id="24f54-105">HTTP request</span></span>

```HTTP
GET /_api/machinelearning/models/getbyuniqueid(‘{modelUniqueId}') HTTP/1.1
```

<span data-ttu-id="24f54-106">この同じ方法をモデルの削除にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="24f54-106">This same method can be used for deleting a model, too.</span></span> 

```HTTP
DELETE /_api/machinelearning/models/getbyuniqueid(‘{modelUniqueId}') HTTP/1.1
```
## <a name="uri-parameters"></a><span data-ttu-id="24f54-107">URI パラメーター</span><span class="sxs-lookup"><span data-stu-id="24f54-107">URI parameters</span></span>

|<span data-ttu-id="24f54-108">名前</span><span class="sxs-lookup"><span data-stu-id="24f54-108">Name</span></span> |<span data-ttu-id="24f54-109">In</span><span class="sxs-lookup"><span data-stu-id="24f54-109">In</span></span> |<span data-ttu-id="24f54-110">必須</span><span class="sxs-lookup"><span data-stu-id="24f54-110">Required</span></span>|<span data-ttu-id="24f54-111">型</span><span class="sxs-lookup"><span data-stu-id="24f54-111">Type</span></span>|<span data-ttu-id="24f54-112">説明</span><span class="sxs-lookup"><span data-stu-id="24f54-112">Description</span></span>|
|-----|---|--------|----|-----------|
|<span data-ttu-id="24f54-113">modelUniqueId</span><span class="sxs-lookup"><span data-stu-id="24f54-113">modelUniqueId</span></span>|<span data-ttu-id="24f54-114">query</span><span class="sxs-lookup"><span data-stu-id="24f54-114">query</span></span>|<span data-ttu-id="24f54-115">はい</span><span class="sxs-lookup"><span data-stu-id="24f54-115">True</span></span>|<span data-ttu-id="24f54-116">string</span><span class="sxs-lookup"><span data-stu-id="24f54-116">string</span></span>|<span data-ttu-id="24f54-117">Syntex モデル ファイルの ID。</span><span class="sxs-lookup"><span data-stu-id="24f54-117">ID of the Syntex model file.</span></span>|

## <a name="request-headers"></a><span data-ttu-id="24f54-118">要求ヘッダー</span><span class="sxs-lookup"><span data-stu-id="24f54-118">Request headers</span></span>

| <span data-ttu-id="24f54-119">ヘッダー</span><span class="sxs-lookup"><span data-stu-id="24f54-119">Header</span></span> | <span data-ttu-id="24f54-120">値</span><span class="sxs-lookup"><span data-stu-id="24f54-120">Value</span></span> |
|--------|-------|
|<span data-ttu-id="24f54-121">Accept</span><span class="sxs-lookup"><span data-stu-id="24f54-121">Accept</span></span>|<span data-ttu-id="24f54-122">application/json;odata=verbose</span><span class="sxs-lookup"><span data-stu-id="24f54-122">application/json;odata=verbose</span></span>|

## <a name="request-body"></a><span data-ttu-id="24f54-123">要求本文</span><span class="sxs-lookup"><span data-stu-id="24f54-123">Request body</span></span>

<span data-ttu-id="24f54-124">GET には要求本文は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="24f54-124">For GET, no request body is needed.</span></span>

## <a name="responses"></a><span data-ttu-id="24f54-125">応答</span><span class="sxs-lookup"><span data-stu-id="24f54-125">Responses</span></span>

| <span data-ttu-id="24f54-126">名前</span><span class="sxs-lookup"><span data-stu-id="24f54-126">Name</span></span>   | <span data-ttu-id="24f54-127">型</span><span class="sxs-lookup"><span data-stu-id="24f54-127">Type</span></span>  | <span data-ttu-id="24f54-128">説明</span><span class="sxs-lookup"><span data-stu-id="24f54-128">Description</span></span>|
|--------|-------|------------|
|<span data-ttu-id="24f54-129">200 OK</span><span class="sxs-lookup"><span data-stu-id="24f54-129">200 OK</span></span>| |<span data-ttu-id="24f54-130">成功</span><span class="sxs-lookup"><span data-stu-id="24f54-130">Success</span></span>|

## <a name="examples"></a><span data-ttu-id="24f54-131">例</span><span class="sxs-lookup"><span data-stu-id="24f54-131">Examples</span></span>

### <a name="get-the-contoso-contract-model-by-id"></a><span data-ttu-id="24f54-132">ID で Contoso コントラクト モデルを取得する</span><span class="sxs-lookup"><span data-stu-id="24f54-132">Get the Contoso Contract model by ID</span></span>

<span data-ttu-id="24f54-133">このサンプルでは、Contoso 契約書ドキュメント理解モデルの ID は `7645e69d-21fb-4a24-a17a-9bdfa7cb63dc`です。</span><span class="sxs-lookup"><span data-stu-id="24f54-133">In this sample, the ID of the Contoso Contract document understanding model is `7645e69d-21fb-4a24-a17a-9bdfa7cb63dc`.</span></span>

#### <a name="sample-request"></a><span data-ttu-id="24f54-134">要求のサンプル</span><span class="sxs-lookup"><span data-stu-id="24f54-134">Sample request</span></span>

```HTTP
GET /_api/machinelearning/models/getbyuniqueid(‘{7645e69d-21fb-4a24-a17a-9bdfa7cb63dc}') HTTP/1.1
```

#### <a name="sample-response"></a><span data-ttu-id="24f54-135">応答のサンプル</span><span class="sxs-lookup"><span data-stu-id="24f54-135">Sample response</span></span>

<span data-ttu-id="24f54-136">**Status code:** 204</span><span class="sxs-lookup"><span data-stu-id="24f54-136">**Status code:** 204</span></span>

```HTTP
{
    "@odata.context": "https://contoso.sharepoint.com/sites/filerepository/_api/$metadata#models/$entity",
    "@odata.type": "#Microsoft.Office.Server.ContentCenter.SPMachineLearningModel",
    "@odata.id": "https://contoso.sharepoint.com/sites/filerepository/_api/machinelearning/models/getbyuniqueId('7645e69d-21fb-4a24-a17a-9bdfa7cb63dc')",
    "@odata.etag": "\"7645e69d-21fb-4a24-a17a-9bdfa7cb63dc,111\"",
    "@odata.editLink": " https://contoso.sharepoint.com/sites/filerepository /_api/machinelearning/models/getbyuniqueId('7645e69d-21fb-4a24-a17a-9bdfa7cb63dc')",
    "ConfidenceScore": "{\"trainingStatus\":{\"kind\":\"original\",\"ClassifierStatus\":{\"TrainingStatus\":\"success\",\"TimeStamp\":1611716640535},\"ExtractorsStatus\":[{\"TimeStamp\":1585175746775,\"ExtractorName\":\"Contract Name\",\"TrainingStatus\":\"success\"},{\"TimeStamp\":1586905975794,\"ExtractorName\":\"Client \",\"TrainingStatus\":\"success\"},{\"TimeStamp\":1586906061099,\"ExtractorName\":\"Contract Date\",\"TrainingStatus\":\"success\"},{\"TimeStamp\":1586907912388,\"ExtractorName\":\"Fee\",\"TrainingStatus\":\"success\"},{\"TimeStamp\":1611716640115,\"ExtractorName\":\"ServiceType\",\"TrainingStatus\":\"success\"}]},\"modelAccuracy\":{\"Classifier\":1,\"Extractors\":{\"Contract Name\":1,\"Client \":1,\"Contract Date\":1,\"Fee\":1,\"ServiceType\":1}},\"perSampleAccuracy\":{\"133\":{\"Classifier\":1,\"Extractors\":{\"ServiceType\":1}},\"249\":{\"Classifier\":1,\"Extractors\":{\"ServiceType\":1}},\"252\":{\"Classifier\":1,\"Extractors\":{\"ServiceType\":1}},\"253\":{\"Classifier\":1,\"Extractors\":{\"ServiceType\":1}},\"254\":{\"Classifier\":1,\"Extractors\":{\"ServiceType\":1}},\"255\":{\"Classifier\":1,\"Extractors\":{\"ServiceType\":1}},\"256\":{\"Extractors\":{\"ServiceType\":1}},\"257\":{\"Extractors\":{\"ServiceType\":1}}},\"perSamplePrediction\":{\"133\":{\"Extractors\":{\"ServiceType\":[]}},\"249\":{\"Extractors\":{\"ServiceType\":[\"Writing\"]}},\"252\":{\"Extractors\":{\"ServiceType\":[\"Catering\"]}},\"253\":{\"Extractors\":{\"ServiceType\":[\"Design\"]}},\"254\":{\"Extractors\":{\"ServiceType\":[\"Marketing\"]}},\"255\":{\"Extractors\":{\"ServiceType\":[\"Financial Planning\"]}},\"256\":{\"Extractors\":{\"ServiceType\":[\"Writing\"]}},\"257\":{\"Extractors\":{\"ServiceType\":[\"Writing\"]}}},\"trainingFailures\":{}}",
    "ContentTypeGroup": "Intelligent Document Content Types",
    "ContentTypeId": "0x01010083DF84D4F59BBD4CB06F075AA81F58AA",
    "ContentTypeName": "Contoso Contract",
    "Created": "2020-03-25T22:04:04Z",
    "CreatedBy": "i:0#.f|membership|meganb@contoso.com",
    "DriveId": "b!O-aG9qer5UiXx2jEwd8pL0221maIb9lNs9tH5vAMU-h2NuHxlYUiTJyiwKQHZobK",
    "Explanations": "{\"Classifier\":[{\"id\":\"8122ac1d-8fcb-4705-8872-2825cbf05bfe\",\"kind\":\"dictionaryFeature\",\"name\":\"agreement\",\"active\":true,\"nGrams\":[\"CONSULTING AGREEMENT\",\"SERVICES AGREEMENT\"],\"caseSensitive\":false,\"ignoreDigitIdentity\":false,\"ignoreLetterIdentity\":false},{\"id\":\"af83bea8-bc53-4e93-a3da-f1e697eb6bef\",\"kind\":\"modelFeature\",\"name\":\"Contract Name\",\"active\":true,\"modelReference\":\"Contract Name\",\"conceptId\":\"841d0dcf-7f1d-4a39-931c-53923d10c346\"},{\"id\":\"e3734994-9e34-40e3-82c7-bb6c7bc5a0c3\",\"kind\":\"modelFeature\",\"name\":\"Client \",\"active\":true,\"modelReference\":\"Client \",\"conceptId\":\"8b8490d0-9a09-4c16-bcff-59ce62e05c28\"},{\"id\":\"7c93e7fe-cbfb-47ee-8cca-46ecdf5f628f\",\"kind\":\"modelFeature\",\"name\":\"Contract Date\",\"active\":true,\"modelReference\":\"Contract Date\",\"conceptId\":\"6ba58918-e2f0-4685-9080-98ec4c3adc7c\"},{\"id\":\"5cc85b62-148a-4b07-9155-d9fb7cebb6d0\",\"kind\":\"modelFeature\",\"name\":\"Fee\",\"active\":true,\"modelReference\":\"Fee\",\"conceptId\":\"9c7f764d-afd2-49cd-aaa2-e9407156bfb3\"},{\"id\":\"0f8a23a6-c744-4cae-82bd-d836332ceb56\",\"kind\":\"modelFeature\",\"name\":\"ServiceType\",\"active\":true,\"modelReference\":\"ServiceType\",\"conceptId\":\"4aa9f2fe-cfab-49f8-86b1-11646c79cdbf\"}],\"Extractors\":{\"Contract Name\":[{\"id\":\"8804fbeb-bcf8-44c0-8ade-3fc65496037f\",\"kind\":\"dictionaryFeature\",\"name\":\"before\",\"active\":true,\"nGrams\":[\"- AND -\"],\"caseSensitive\":false,\"ignoreDigitIdentity\":false,\"ignoreLetterIdentity\":false}],\"Client \":[{\"id\":\"606c56de-9e71-42ef-8ec6-f0bbf351d673\",\"kind\":\"dictionaryFeature\",\"name\":\"start\",\"active\":true,\"nGrams\":[\"BETWEEN:\"],\"caseSensitive\":false,\"ignoreDigitIdentity\":false,\"ignoreLetterIdentity\":false},{\"id\":\"334e6df5-e076-40db-a47b-f11ceec7af9a\",\"kind\":\"dictionaryFeature\",\"name\":\"after\",\"active\":true,\"nGrams\":[\"of\"],\"caseSensitive\":false,\"ignoreDigitIdentity\":false,\"ignoreLetterIdentity\":false},{\"id\":\"bccefd2e-88a4-406c-aa9d-81d508bbafb3\",\"kind\":\"proximityFeature\",\"name\":\"prox\",\"active\":true,\"patterns\":[[{\"id\":\"606c56de-9e71-42ef-8ec6-f0bbf351d673\",\"kind\":\"proximityFeatureReference\"},{\"kind\":\"proximityTokenRange\",\"minCount\":1,\"maxCount\":6},{\"id\":\"334e6df5-e076-40db-a47b-f11ceec7af9a\",\"kind\":\"proximityFeatureReference\"}]]}],\"Contract Date\":[{\"id\":\"fabe1ed3-07af-4dc6-852d-fe9521c64801\",\"kind\":\"dictionaryFeature\",\"name\":\"dated\",\"active\":true,\"nGrams\":[\"dated\"],\"caseSensitive\":false,\"ignoreDigitIdentity\":false,\"ignoreLetterIdentity\":false},{\"id\":\"983da7b8-51d7-4a85-9644-007b488fce0b\",\"kind\":\"dictionaryFeature\",\"name\":\"betw\",\"active\":true,\"nGrams\":[\"between\"],\"caseSensitive\":false,\"ignoreDigitIdentity\":false,\"ignoreLetterIdentity\":false}],\"Fee\":[{\"id\":\"f4cf89dc-64d1-49a1-9be4-41debda251b6\",\"kind\":\"dictionaryFeature\",\"name\":\"flat fee of \",\"active\":true,\"nGrams\":[\"flat fee of $\",\"flat fee of $$\"],\"caseSensitive\":false,\"ignoreDigitIdentity\":false,\"ignoreLetterIdentity\":false}],\"ServiceType\":[{\"id\":\"c04408f5-ce14-4eb0-81d0-f72ea9fa7e83\",\"kind\":\"dictionaryFeature\",\"name\":\"Before label\",\"active\":true,\"nGrams\":[\"will provide \"],\"caseSensitive\":false,\"ignoreDigitIdentity\":false,\"ignoreLetterIdentity\":false},{\"id\":\"ea94fa7f-e41b-4e09-a484-355912bfbdff\",\"kind\":\"dictionaryFeature\",\"name\":\"After label\",\"active\":true,\"nGrams\":[\"services for \"],\"caseSensitive\":false,\"ignoreDigitIdentity\":false,\"ignoreLetterIdentity\":false}]}}",
    "ID": 16,
    "LastTrained": "2021-01-27T03:04:00Z",
    "ListID": "f1e13676-8595-4c22-9ca2-c0a4076686ca",
    "ModelSettings": null,
    "ModelType": 2,
    "Modified": "2021-01-27T03:05:04Z",
    "ModifiedBy": "i:0#.f|membership|kevinche@contoso.com",
    "ObjectId": "01ZBWEM5E54ZCXN6ZBERFKC6U336T4WY64",
    "PublicationType": 0,
    "Schemas": "{\"Extractors\":{\"Contract Name\":{\"concepts\":{\"841d0dcf-7f1d-4a39-931c-53923d10c346\":{\"name\":\"Contract Name\"}},\"relationships\":[]},\"Client \":{\"concepts\":{\"8b8490d0-9a09-4c16-bcff-59ce62e05c28\":{\"name\":\"Client \"}},\"relationships\":[]},\"Contract Date\":{\"concepts\":{\"6ba58918-e2f0-4685-9080-98ec4c3adc7c\":{\"name\":\"Contract Date\"}},\"relationships\":[]},\"Fee\":{\"concepts\":{\"9c7f764d-afd2-49cd-aaa2-e9407156bfb3\":{\"name\":\"Fee\"}},\"relationships\":[]},\"ServiceType\":{\"concepts\":{\"4aa9f2fe-cfab-49f8-86b1-11646c79cdbf\":{\"name\":\"ServiceType\",\"termSetId\":\"76c12efb-5173-4982-ae9b-5f9e37187171\"}},\"relationships\":[]}}}",
    "SourceUrl": null,
    "UniqueId": "7645e69d-21fb-4a24-a17a-9bdfa7cb63dc"
}
```
### <a name="get-and-delete-the-contoso-contract-model-by-id"></a><span data-ttu-id="24f54-137">ID で Contoso コントラクト モデルを取得して削除する</span><span class="sxs-lookup"><span data-stu-id="24f54-137">Get and delete the Contoso Contract model by ID</span></span>

<span data-ttu-id="24f54-138">このサンプルでは、Contoso 契約書ドキュメント理解モデルの ID は `7645e69d-21fb-4a24-a17a-9bdfa7cb63dc`です。</span><span class="sxs-lookup"><span data-stu-id="24f54-138">In this sample, the ID of the Contoso Contract document understanding model is `7645e69d-21fb-4a24-a17a-9bdfa7cb63dc`.</span></span>

#### <a name="sample-request"></a><span data-ttu-id="24f54-139">要求のサンプル</span><span class="sxs-lookup"><span data-stu-id="24f54-139">Sample request</span></span>

```HTTP
DELETE /_api/machinelearning/models/getbyuniqueid(‘{7645e69d-21fb-4a24-a17a-9bdfa7cb63dc}') HTTP/1.1
```

## <a name="see-also"></a><span data-ttu-id="24f54-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="24f54-140">See also</span></span>

[<span data-ttu-id="24f54-141">Syntex ドキュメント理解モデル REST API</span><span class="sxs-lookup"><span data-stu-id="24f54-141">Syntex document understanding model REST API</span></span>](syntex-model-rest-api.md)