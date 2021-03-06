---
title: 自動調査後の修復アクションの確認
description: 自動調査の後で修復アクションを確認および承認 (または拒否) します。
keywords: autoir, 自動, 調査, 検出, 修復, アクション, 保留中, 承認済み
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: JoeDavies-MSFT
ms.author: josephd
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: how-to
ms.date: 01/29/2021
ms.technology: mde
ms.openlocfilehash: 410972bd823c3a3c4fda53cacc225014d83f3457
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2021
ms.locfileid: "52844012"
---
# <a name="review-remediation-actions-following-an-automated-investigation"></a>自動調査後の修復アクションの確認

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


## <a name="remediation-actions"></a>修復アクション

自動調査 [が実行されると](automated-investigations.md) 、調査された証拠ごとに評決が生成されます。 評決には、悪意のある *、疑わしい、* または検出 *された脅威がない可能性があります*。  

に応じて

- 脅威の種類 
- 結果の評決、および 
- 組織のデバイス グループ [の構成](/microsoft-365/security/defender-endpoint/machine-groups) 方法 

修復アクションは、自動的に行われるか、組織のセキュリティ運用チームによる承認時にのみ実行されます。 

いくつかの例を示します。

- **例 1**: Fabrikam のデバイス グループが Full **に設定されている -** 脅威を自動的に修復する (推奨される設定)。 この場合、自動調査後に悪意のあると見なされるアーティファクトに対して修復アクションが自動的に実行されます (「完了したアクションの確認 [」を参照](#review-completed-actions))。

- **例 2**: Contoso のデバイスは、Semi に設定されているデバイス グループに含まれています。修復には承認 **が必要です**。 この場合、Contoso のセキュリティ運用チームは、自動調査の後ですべての修復アクションを確認して承認する必要があります (「保留中のアクションの確認 [」を参照](#review-pending-actions))。

- **例 3:** Tailspin Toys のデバイス グループは [自動応答なし] **に設定** されています (推奨されません)。 この場合、自動調査は行われません。 修復アクションは実行または保留中で、デバイスのアクション センターにアクションは[](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)記録されません (「デバイス グループの管理[」を参照](/microsoft-365/security/defender-endpoint/machine-groups#manage-device-groups))。

自動的に行う場合も承認時に行う場合でも、自動調査によって、次の 1 つ以上の修復アクションが発生する可能性があります。
- ファイルの検疫
- レジストリ キーを削除する 
- プロセスを終了する 
- サービスを停止する 
- ドライバーを無効にする 
- スケジュールされたタスクを削除する

## <a name="review-pending-actions"></a>保留中のアクションを確認する

1. セキュリティ センター ( ) Microsoft 365に移動し [https://security.microsoft.com](https://security.microsoft.com) 、サインインします。
2. ナビゲーション ウィンドウで、[**アクション センター**] を選択します。 
3. [保留中] タブの **アイテムを確認** します。 
4. アクションを選択して、そのフライアウト ウィンドウを開きます。
5. フライアウト ウィンドウで情報を確認し、次のいずれかの手順を実行します。
   - [ **調査ページを開く]** を選択して、調査の詳細を表示します。
   - [承認 **] を** 選択して保留中のアクションを開始します。
   - 保留中 **のアクション** が実行されるのを防ぐには、[拒否] を選択します。
   - [Go **hunt] を** 選択して高度な [ハンティングに入る](advanced-hunting-overview.md)。 

## <a name="review-completed-actions"></a>完了したアクションを確認する

1. セキュリティ センター ( ) Microsoft 365に移動し [https://security.microsoft.com](https://security.microsoft.com) 、サインインします。
2. ナビゲーション ウィンドウで、[**アクション センター**] を選択します。 
3. [履歴] タブのアイテム **を確認** します。 
4. アイテムを選択すると、その修復アクションの詳細が表示されます。
 
## <a name="undo-completed-actions"></a>完了した操作を元に戻す

デバイスまたはファイルが脅威ではないと判断した場合は、これらのアクションが自動的または手動で実行されたかどうかに関わり、実行された修復アクションを元に戻すことができます。 [アクション センター] の [履歴] **タブ** で、次の操作を元に戻すことができます。  

| アクション ソース | サポートされているアクション |
|:---|:---|
| - 自動調査 <br/>- Microsoft Defender ウイルス対策 <br/>- 手動応答アクション | - デバイスの分離 <br/>- コードの実行を制限する <br/>- ファイルを検疫する <br/>- レジストリ キーを削除する <br/>- サービスを停止する <br/>- ドライバーを無効にする <br/>- スケジュールされたタスクを削除する |

### <a name="to-undo-multiple-actions-at-one-time"></a>複数のアクションを一度に元に戻すには

1. アクション センター ( ) に移動 [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) し、サインインします。
2. [履歴 **] タブ** で、元に戻す操作を選択します。 同じアクションの種類を持つアイテムを選択してください。 フライアウト ウィンドウが開きます。
3. フライアウト ウィンドウで、[元に戻す] を **選択します**。

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>複数のデバイス間で検疫からファイルを削除するには 

1. アクション センター ( ) に移動 [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) し、サインインします。
2. [履歴 **] タブ** で、アクションタイプの検疫ファイルを持つアイテム **を選択します**。
3. フライアウト ウィンドウで、[このファイルの **インスタンスを X** に適用する] を選択し、[元に戻す] を **選択します**。

## <a name="automation-levels-automated-investigation-results-and-resulting-actions"></a>自動化レベル、自動化された調査結果、および結果のアクション

オートメーション レベルは、特定の修復アクションが自動的に実行されるのか、承認時にのみ実行されるのかに影響します。 自動調査の結果に応じて、セキュリティ運用チームが実行する手順が多い場合があります。 次の表は、自動化レベル、自動調査の結果、および各ケースで実行する操作の概要を示しています。 

|デバイス グループの設定 | 自動調査結果 | 操作 |
|:---|:---|:---|
|**完全 - 脅威を自動的に修復** する (推奨設定) |証拠の一部に *対して悪意* のあるという評決に達します。 <br/><br/>適切な修復アクションが自動的に実行されます。 |[完了したアクションを確認する](#review-completed-actions) |
|**完全 - 脅威を自動的に修復する** |証拠の一部に *対して疑* わしいという評決に達します。 <br/><br/>修復アクションは、続行するための承認待ちです。 | [保留中のアクションを承認 (または拒否) する](#review-pending-actions) |
|**Semi - 修復の承認が必要**  |証拠の一部に対 *して、悪意のあるか**疑わしい* かの評決に達します。 <br/><br/>修復アクションは、続行するための承認待ちです。  |[保留中のアクションを承認 (または拒否) する](#review-pending-actions) |
|**Semi - コア フォルダー修復の承認が必要** |証拠の一部に *対して悪意* のあるという評決に達します。 <br/><br/>成果物がファイルまたは実行可能ファイルであり、オペレーティング システム ディレクトリ (Windows フォルダーや Program files フォルダーなど) にある場合、修復アクションは承認待ちです。 <br/><br/>成果物がオペレーティング *システム ディレクトリに* 存在しない場合は、修復アクションが自動的に実行されます。 |1. [保留中のアクションを承認 (または拒否) する](#review-pending-actions)<br/><br/>2. [完了したアクションを確認する](#review-completed-actions) |
|**Semi - コア フォルダー修復の承認が必要** |証拠の一部に *対して疑* わしいという評決に達します。 <br/><br/>修復アクションは承認待ちです。  |[保留中のアクションを承認 (または拒否) します](#review-pending-actions)。|
|**Semi - 一時フォルダー以外の修復の承認が必要** |証拠の一部に *対して悪意* のあるという評決に達します。 <br/><br/>成果物が、ユーザーのダウンロード フォルダーや一時フォルダーなど、一時フォルダーに含されていないファイルまたは実行可能ファイルである場合、修復アクションは承認待ちです。 <br/><br/>成果物が一時フォルダー内 *のファイルまたは* 実行可能ファイルである場合、修復アクションは自動的に実行されます。  |1. [保留中のアクションを承認 (または拒否) する](#review-pending-actions)<br/><br/>2. [完了したアクションを確認する](#review-completed-actions)  |
|**Semi - 一時フォルダー以外の修復の承認が必要** |証拠の一部に *対して疑* わしいという評決に達します。 <br/><br/>修復アクションは承認待ちです。 |[保留中のアクションを承認 (または拒否) する](#review-pending-actions)  | 
|完全または **半の** オートメーションレベル |証拠の一部に *対する脅威が見つからない* という評決に達しました。 <br/><br/>修復アクションは実行され、承認待ちアクションはありません。 |[自動調査の詳細と結果を表示する](/microsoft-365/security/defender-endpoint/auto-investigation-action-center) |
|**自動応答なし** (推奨されません)|自動調査は実行されません。そのため、評決に達したり、修復アクションを実行したり、承認を待つ操作を行う必要はありません。 |[フル オートメーションまたは Semi オートメーションを使用するデバイス グループ **の設定または** 変更 **を検討** する](/microsoft-365/security/defender-endpoint/machine-groups) |

Microsoft Defender for Endpoint では、すべての評決がアクション センターで [追跡されます](auto-investigation-action-center.md#new-a-unified-action-center)。

## <a name="next-steps"></a>次の手順

- [ライブ応答機能の詳細](live-response.md)
- [高度な狩猟で脅威を積極的に探す](advanced-hunting-overview.md)
- [Microsoft Defender for Endpoint での誤検出/検出漏れに対処する](defender-endpoint-false-positives-negatives.md)

## <a name="see-also"></a>関連項目

- [自動調査の概要](automated-investigations.md)
