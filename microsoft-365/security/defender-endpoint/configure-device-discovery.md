---
title: デバイス検出の構成
description: 基本または標準の検出を使用して、Microsoft 365 Defender検出を構成する方法について説明します。
keywords: 基本、標準、エンドポイント検出の構成、デバイスの検出
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
localization_priority: normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 7125a6953b9be46af9073b50c9268ce65dc0cd30
ms.sourcegitcommit: 0d1b065c94125b495e9886200f7918de3bda40b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/08/2021
ms.locfileid: "53339530"
---
# <a name="configure-device-discovery"></a>デバイス検出の構成

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


[!include[Prerelease information](../../includes/prerelease.md)]

検出は、標準モードまたは基本モードで構成できます。 標準オプションを使用して、ネットワーク内のデバイスをアクティブに検索し、エンドポイントの検出を保証し、より豊富なデバイス分類を提供します。 

標準検出の実行に使用するデバイスの一覧をカスタマイズできます。 この機能をサポートしているすべてのオンボード デバイス (現在は Windows 10 デバイスのみ) で標準検出を有効にするか、デバイス タグを指定してデバイスのサブセットまたはサブセットを選択できます。

> [!IMPORTANT]
> プレビューの場合は、最初にプレビュー機能をオンにする必要Microsoft 365 Defender。
> その後、セキュリティ センターでデバイス検出Microsoft 365アクセスできます。 管理されていないデバイスとセキュリティに関する推奨事項の一覧は、Microsoft 365 Defender と Microsoft 365 の両方のセキュリティ センターで使用できます。ダッシュボード タイルは Microsoft 365 セキュリティ センターでのみ使用できます。

セキュリティ センターで次の構成Microsoft 365実行します。

1. [デバイスの検出 **設定 >に移動します**。
2. オンボード デバイスで使用する検出モードを選択します。
3. 標準検出を使用する場合は、アクティブなプロブに使用するデバイス (すべてのデバイスまたはデバイス タグを指定してサブセット上) を選択します。
4. [**保存**] をクリックします。

## <a name="exclude-devices-from-being-actively-probed-in-standard-discovery"></a>デバイスが標準検出でアクティブにプローブされるのを除外する

ネットワーク上にアクティブにスキャンすべきではないデバイス (たとえば、別のセキュリティ ツールでハニーポットとして使用されるデバイス) がある場合は、除外リストを定義してスキャンを防止することもできます。 デバイスは、基本検出モードを使用して検出できます。 これらのデバイスは受動的に検出されますが、アクティブにプローブされません。 

## <a name="select-networks-to-monitor"></a>監視するネットワークの選択

 Microsoft Defender for Endpoint は、ネットワークを分析し、監視が必要な企業ネットワークか、無視できる非企業ネットワークかどうかを判断します。 通常、企業ネットワークは監視対象として選択されます。 ただし、オンボードデバイスが見つかった企業以外のネットワークを監視することで、この決定を上書きできます。 

監視するネットワークを指定することで、デバイスの検出を実行できる場所を構成できます。 ネットワークを監視すると、デバイス検出をそのネットワークで実行できます。 

デバイス検出を実行できるネットワークの一覧が、[監視対象のネットワーク] **ページに表示** されます。 

> [!NOTE]
> 上位 50 のネットワーク (関連付けられているデバイスの数に応じて) だけがネットワーク リストで使用できます。 

監視対象のネットワークの一覧は、過去 7 日間にネットワークに表示されたデバイスの総数に基づいて並べ替えます。

フィルターを適用して、次のネットワーク検出状態を表示できます。

- **監視対象のネットワーク** - デバイス検出が実行されるネットワーク。
- **無視されたネットワーク** - このネットワークは無視され、デバイス検出は実行されません。
- **All** - 監視対象ネットワークと無視されたネットワークの両方が表示されます。

### <a name="configure-the-network-monitor-state"></a>ネットワーク モニターの状態を構成する

デバイス検出の実行場所を制御します。 監視対象のネットワークは、デバイスの検出が実行される場所であり、通常は企業ネットワークです。 ネットワークを無視するか、状態を変更した後の最初の検出分類を選択するように選択できます。

最初の検出分類を選択すると、既定のシステムで作成されたネットワーク モニター状態が適用されます。 既定のシステム製のネットワーク モニター状態を選択すると、企業として識別され、監視され、非企業として識別されたネットワークは自動的に無視されます。

1. [デバイス **設定 >] を選択します**。
2. [監視 **対象のネットワーク] を選択します**。
3. ネットワークの一覧を表示します。
4. ネットワーク名の横にある 3 つのドットを選択します。
5. 初期検出分類を監視、無視、または使用するかどうかを選択します。

    > [!WARNING]
    >
    > - Microsoft Defender for Endpoint によって企業ネットワークとして識別されていないネットワークを監視すると、企業ネットワークの外部でデバイスの検出が発生し、自宅や他の企業以外のデバイスを検出する可能性があります。
    > - ネットワークを無視すると、そのネットワーク内のデバイスの監視と検出が停止します。 既に検出されたデバイスはインベントリから削除されませんが、更新されなくなるので、Defender for Endpoint のデータ保持期間が経過するまで詳細が保持されます。
    > - 企業以外のネットワークを監視する前に、その権限を持っている必要があります。

6. 変更を行う必要があります。 

## <a name="explore-devices-in-the-network"></a>ネットワーク内のデバイスを探索する

次の高度な検索クエリを使用して、ネットワーク リストで説明されている各ネットワーク名に関するコンテキストを取得できます。 クエリには、過去 7 日以内に特定のネットワークに接続されたオンボード デバイスすべてが一覧表示されます。

```kusto
DeviceNetworkInfo
| where Timestamp > ago(7d)
| summarize arg_max(Timestamp, *) by DeviceId
| where ConnectedNetworks  != ""
| extend ConnectedNetworksExp = parse_json(ConnectedNetworks)
| mv-expand bagexpansion = array ConnectedNetworks=ConnectedNetworksExp
| extend NetworkName = tostring(ConnectedNetworks ["Name"]), Description = tostring(ConnectedNetworks ["Description"]), NetworkCategory = tostring(ConnectedNetworks ["Category"])
| where NetworkName == "<your network name here>"
```

## <a name="see-also"></a>関連項目

- [デバイス検出の概要](device-discovery.md)
- [デバイスの検出に関するよくある質問](device-discovery-faq.md)
