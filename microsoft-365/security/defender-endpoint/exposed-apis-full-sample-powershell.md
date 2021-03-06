---
title: PowerShell API ガイドを使用した高度なハンティング
ms.reviewer: ''
description: これらのコード サンプルを使用して、いくつかの Microsoft Defender for Endpoint API を照会します。
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
ms.date: 09/24/2018
ms.technology: mde
ms.openlocfilehash: ef6d05bb27018bb72f731da2e8b7837c9d9f0127
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2021
ms.locfileid: "52842064"
---
# <a name="microsoft-defender-for-endpoint-apis-using-powershell"></a>PowerShell を使用したエンドポイント API 用 Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

> Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

>Microsoft Defender ATP を試してみたいですか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-enablesiem-abovefoldlink)

Microsoft Defender for Endpoint の複数の API を使用した完全なシナリオ。

このセクションでは、PowerShell サンプルを 
- トークンの取得 
- トークンを使用して Microsoft Defender for Endpoint の最新のアラートを取得する
- アラートごとに、アラートの優先度が中または高で、まだ進行中の場合は、デバイスが不審な URL に接続した回数を確認します。

**前提条件**: 最初にアプリを [作成する必要があります](apis-intro.md)。

## <a name="preparation-instructions"></a>準備手順

- PowerShell のウィンドウを開きます。
- ポリシーで PowerShell コマンドを実行できない場合は、次のコマンドを実行できます。
  ```
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

詳細については [、「PowerShell のドキュメント」を参照してください。](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>トークンの取得

以下を実行します。

- $tenantId: クエリを実行する代わりにテナントの ID (つまり、このテナントのデータに対してクエリが実行されます)
- $appId: AAD アプリの ID (アプリに Defender for Endpoint への 「高度なクエリの実行」 アクセス許可が必要)
- $appSecret: Azure AD アプリの秘密

- $suspiciousUrl: URL


```
$tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
$appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
$appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here
$suspiciousUrl = 'www.suspiciousUrl.com' # Paste your own URL here

$resourceAppIdUri = 'https://securitycenter.onmicrosoft.com/windowsatpservice'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$authBody = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$aadToken = $authResponse.access_token


#Get latest alert
$alertUrl = "https://api.securitycenter.microsoft.com/api/alerts?`$top=10"
$headers = @{ 
    'Content-Type' = 'application/json'
    Accept = 'application/json'
    Authorization = "Bearer $aadToken" 
}
$alertResponse = Invoke-WebRequest -Method Get -Uri $alertUrl -Headers $headers -ErrorAction Stop
$alerts =  ($alertResponse | ConvertFrom-Json).value

$machinesToInvestigate = New-Object System.Collections.ArrayList

Foreach($alert in $alerts)
{
    #echo $alert.id $alert.machineId    $alert.severity $alert.status

    $isSevereAlert = $alert.severity -in 'Medium', 'High'
    $isOpenAlert = $alert.status -in 'InProgress', 'New'
    if($isOpenAlert -and $isSevereAlert)
    {
        if (-not $machinesToInvestigate.Contains($alert.machineId))
        {
            $machinesToInvestigate.Add($alert.machineId) > $null
        }
    }
}

$commaSeparatedMachines = '"{0}"' -f ($machinesToInvestigate -join '","')

$query = "NetworkCommunicationEvents
| where MachineId in ($commaSeparatedMachines)
| where RemoteUrl  == `"$suspiciousUrl`"
| summarize ConnectionsCount = count() by MachineId"

$queryUrl = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"

$queryBody = ConvertTo-Json -InputObject @{ 'Query' = $query }
$queryResponse = Invoke-WebRequest -Method Post -Uri $queryUrl -Headers $headers -Body $queryBody -ErrorAction Stop
$response =  ($queryResponse | ConvertFrom-Json).Results
$response
```


## <a name="see-also"></a>関連項目
- [エンドポイント API 用 Microsoft Defender](apis-intro.md)
- [高度な追及 API](run-advanced-query-api.md)
- [Python を使用した高度な追求](run-advanced-query-sample-python.md)
