---
title: 'ファイルのインジケーターを作成 '
ms.reviewer: ''
description: エンティティの検出、防止、除外を定義するファイル ハッシュのインジケーターを作成します。
keywords: ファイル、ハッシュ、管理、許可、ブロック、ブロック、クリーン、悪意のある、ファイル ハッシュ、IP アドレス、URL、ドメイン
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: b56a18e1b35b65629318ab29f2189ef1f73373f5
ms.sourcegitcommit: a4c93a4c7d7db08fe3b032b58d5c7dbbb9476e90
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2021
ms.locfileid: "53256917"
---
# <a name="create-indicators-for-files"></a>ファイルのインジケーターを作成 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Defender for Endpoint を体験してみませんか? [無料試用版にサインアップしてください。](https://www.microsoft.com/en-us/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

悪意のある可能性のあるファイルやマルウェアの疑いを禁止することで、組織での攻撃の伝播をさらに防ぐ。 悪意のある可能性のあるポータブル実行可能ファイル (PE) ファイルが分かっている場合は、そのファイルをブロックできます。 この操作によって、組織内のデバイスで読み取り、書き込み、または実行されるのを防ぐ。

ファイルのインジケーターを作成するには、次の 3 つの方法があります。

- 設定ページからインジケーターを作成する
- ファイルの詳細ページからインジケーターの追加ボタンを使用してコンテキスト インジケーターを作成する
- インジケーター API を使用してインジケーター [を作成する](ti-indicator.md)

## <a name="before-you-begin"></a>はじめに

ファイルのインジケーターを作成する前に、次の前提条件を理解することが重要です。

- この機能は、組織が (アクティブ モードで **)** Microsoft Defender ウイルス対策を使用し、クラウドベースの保護が有効 **になっている場合に使用できます**。 詳細については、「クラウドベースの保護 [を管理する」を参照してください](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus)。

- マルウェア対策クライアントのバージョンは、4.18.1901.x 以降である必要があります。 「 [月次プラットフォームとエンジンのバージョン」を参照してください。](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions)

- 2019 年Windows 10バージョン 1703 以降のデバイスWindows Server 2016サポートされています。

- ファイルのブロックを開始するには、まず、ファイルのブロックまたは許可 [機能](advanced-features.md)を有効にする設定。

この機能は、疑わしいマルウェア (または悪意のある可能性のあるファイル) が Web からダウンロードされるのを防ぐために設計されています。 現在、ポータブル実行可能ファイル (PE) ファイルがサポートされています 。このファイルには、.exeファイル.dllがあります。 対象範囲は時間の長い期間延長されます。

## <a name="create-an-indicator-for-files-from-the-settings-page"></a>設定ページからファイルのインジケーターを作成する

1. ナビゲーション ウィンドウで、[インジケーター] **を設定 >します**。

2. [ファイル ハッシュ **] タブを選択**   します。

3. [インジケーター **の追加] を選択します**。

4. 次の詳細を指定します。
    - Indicator - エンティティの詳細を指定し、インジケーターの有効期限を定義します。
    - Action - 実行するアクションを指定し、説明を入力します。
    - Scope - デバイス グループのスコープを定義します。

5. [概要] タブで詳細を確認し、[保存] を **選択します**。

## <a name="create-a-contextual-indicator-from-the-file-details-page"></a>ファイルの詳細ページからコンテキスト インジケーターを作成する

ファイルに対して応答アクションを実行 [する場合のオプションの 1](respond-file-alerts.md)つは   、ファイルのインジケーターを追加することです。 ファイルのインジケーター ハッシュを追加すると、組織内のデバイスがファイルの実行を試みるたびに、アラートを発生してファイルをブロックできます。

インジケーターによって自動的にブロックされたファイルは、ファイルのアクション センターには表示されませんが、アラートはアラート キューに表示されます。

>[!IMPORTANT]
>- 通常、ファイル ブロックは数分以内に適用および削除されますが、30 分以上かかる場合があります。
> 
>- 同じ適用の種類とターゲットを持つファイル IoC ポリシーが競合している場合は、より安全なハッシュのポリシーが適用されます。 SHA-256 ファイル ハッシュ IoC ポリシーは SHA-1 ファイル ハッシュ IoC ポリシーに勝ちます。ハッシュの種類が同じファイルを定義している場合、MD5 ファイル ハッシュ IoC ポリシーに勝ちます。 これは、デバイス グループに関係なく常に true です。 
>   それ以外のすべての場合、同じ適用ターゲットを持つ競合するファイル IoC ポリシーがすべてのデバイスとデバイスのグループに適用されると、デバイスの場合、デバイス グループ内のポリシーが勝ちます。 
>   
>- EnableFileHashComputation グループ ポリシーを無効にすると、ファイル IoC のブロック精度が低下します。 ただし、有効にすると、 `EnableFileHashComputation` デバイスのパフォーマンスに影響を与える可能性があります。 たとえば、ネットワーク共有からローカル デバイス (特に VPN 接続を使用して) に大きなファイルをコピーすると、デバイスのパフォーマンスに影響を与える可能性があります。
>
>   EnableFileHashComputation グループ ポリシーの詳細については [、「Defender CSP」を参照してください。](/windows/client-management/mdm/defender-csp)

## <a name="policy-conflict-handling"></a>ポリシーの競合の処理  

Cert および File IoC ポリシー処理の競合は、次の順序に従います。

- アプリケーションコントロールと AppLocker の強制モード ポリシー/Windows Defenderによってファイルが許可されていない場合は、[**ブロック**]

- それ以外の場合は、ファイルが除外によって許可されている場合Microsoft Defender ウイルス対策許可する

- それ以外の場合、ファイルがブロックまたは警告ファイル IoC によってブロックまたは警告される場合は、ブロック **/警告**

- それ以外の場合は、ファイルが許可ファイルの IoC ポリシーで許可されている場合は、[**許可**]

- それ以外の場合は、ASR ルール、CFA、AV、SmartScreen、その後ブロックによってファイルがブロック **されます**。  

- Else **Allow** (アプリケーション制御Windows Defender AppLocker &に渡す場合、IoC ルールは適用されません)

同じ適用の種類とターゲットを持つファイル IoC ポリシーが競合している場合は、より安全な (長い) ハッシュのポリシーが適用されます。 たとえば、SHA-256 ファイル ハッシュ IoC ポリシーは、両方のハッシュの種類が同じファイルを定義している場合、MD5 ファイル ハッシュ IoC ポリシーに勝ちます。

脅威と脆弱性の管理のブロック脆弱なアプリケーション機能は、ファイル IoC を適用に使用し、上記の競合処理順序に従います。

### <a name="examples"></a>例

|コンポーネント |コンポーネントの適用 |ファイル インジケーター アクション |結果
|--|--|--|--|
|攻撃表面の縮小ファイル パスの除外 |許可 |ブロック |ブロック
|攻撃表面の縮小ルール |ブロック |許可 |許可
|Windows Defender Application Control |許可 |ブロック |許可 |
|Windows Defender Application Control |ブロック |許可 |ブロック
|Microsoft Defender ウイルス対策除外 |許可 |ブロック |許可

## <a name="see-also"></a>関連項目

- [インジケーターの作成](manage-indicators.md)
- [IP および URL/ドメインのインジケーターを作成](indicator-ip-domain.md)
- [証明書に基づいてインジケーターを作成する](indicator-certificates.md)
- [インジケーターの管理](indicator-manage.md)
