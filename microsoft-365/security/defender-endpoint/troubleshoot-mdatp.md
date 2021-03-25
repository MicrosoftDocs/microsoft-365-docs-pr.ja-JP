---
title: Microsoft Defender for Endpoint Service の問題のトラブルシューティング
description: サービスにアクセスしようとするときにサーバー エラーなどの既知の問題に対する解決策と回避策を見つける。
keywords: エンドポイントの Microsoft Defender のトラブルシューティング、Windows ATP のトラブルシューティング、サーバー エラー、アクセス拒否、無効な資格情報、データなし、ダッシュボード ポータル、許可、イベント ビューアー
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: 112f682836da37ddfb51c103282518ff74563727
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51186019"
---
# <a name="troubleshoot-service-issues"></a>サービスの問題のトラブルシューティング

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-pullalerts-abovefoldlink) 


このセクションでは、Microsoft Defender Advanced Threat サービスを使用する際に発生する可能性のある問題について説明します。

## <a name="server-error---access-is-denied-due-to-invalid-credentials"></a>サーバー エラー - 無効な資格情報が原因でアクセスが拒否されました
サービスにアクセスしようとするときにサーバー エラーが発生した場合は、ブラウザーの Cookie 設定を変更する必要があります。
Cookie を許可するブラウザーを構成します。

## <a name="elements-or-data-missing-on-the-portal"></a>ポータルに存在する要素またはデータ
一部の要素やデータが Microsoft Defender セキュリティ センターで見つからない場合は、プロキシ設定でブロックされている可能性があります。

プロキシ許可リスト `*.securitycenter.windows.com` が含まれているか確認します。


> [!NOTE]
> 次のエンドポイントを追加する場合は、HTTPS プロトコルを使用する必要があります。

## <a name="microsoft-defender-for-endpoint-service-shows-event-or-error-logs-in-the-event-viewer"></a>Microsoft Defender for Endpoint Service は、イベント ビューアーにイベント ログまたはエラー ログを表示します。

Microsoft [](event-error-codes.md) Defender for Endpoint サービスによって報告されるイベントの一覧については、「イベント ビューアーを使用してイベントとエラーを確認する」を参照してください。 この記事には、イベント エラーのトラブルシューティング手順も含まれています。

## <a name="microsoft-defender-for-endpoint-service-fails-to-start-after-a-reboot-and-shows-error-577"></a>Microsoft Defender for Endpoint service が再起動後に開始に失敗し、エラー 577 が表示される

オンボード デバイスが正常に完了したが、再起動後に Microsoft Defender for Endpoint が起動し、エラー 577 が表示される場合は、Windows Defender がポリシーによって無効にされていないか確認します。

詳細については、「ポリシーによって Microsoft Defender ウイルス対策が無効にされていないか確認 [する」を参照してください](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)。

## <a name="known-issues-with-regional-formats"></a>地域の形式に関する既知の問題

**日付と時刻の形式**<br>
時刻と日付の形式にはいくつかの既知の問題があります。 

次の日付形式がサポートされています。
- MM/dd/yyyy
- dd/MM/yyyy

現在、次の日付と時刻の形式はサポートされていません。
- 日付形式 yyyy/MM/dd
- 日付形式 dd/MM/yyy
- yy の日付形式。 yyyy のみを表示します。
- 時間形式 HH:mm:ss はサポートされていません (12 時間 AM/PM 形式はサポートされていません)。 24 時間形式だけがサポートされています。

**コンマを使用して千を示す**<br>
数値の区切り記号としてコンマを使用するサポートはサポートされていません。 数字がコンマで区切られ、1000 を示す領域では、ドットが区切り記号としてのみ表示されます。 たとえば、15,5K は 15.5K と表示されます。

>Microsoft Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-troubleshoot-belowfoldlink)

## <a name="microsoft-defender-for-endpoint-tenant-was-automatically-created-in-europe"></a>Microsoft Defender for Endpoint テナントがヨーロッパで自動的に作成されました
Azure Security Center を使用してサーバーを監視すると、Microsoft Defender for Endpoint テナントが自動的に作成されます。 Microsoft Defender for Endpoint データは、既定でヨーロッパに保存されます。





## <a name="related-topics"></a>関連項目
- [Microsoft Defender for Endpoint オンボーディングの問題のトラブルシューティング](troubleshoot-onboarding.md)
- [イベント ビューアーを使用してイベントとエラーを確認する](event-error-codes.md)