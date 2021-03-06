---
title: 自動調査と修復の自動化レベル
description: オートメーション レベルの概要と、Microsoft Defender for Endpoint での動作の概要を確認する
keywords: 自動化された、 調査、 レベル、 Microsoft Defender for Endpoint
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: JoeDavies-MSFT
ms.author: josephd
ms.date: 10/22/2020
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
ms.openlocfilehash: 6d453a8b6e5c4947c0fb03131c539b083227c28a
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2021
ms.locfileid: "52844648"
---
# <a name="automation-levels-in-automated-investigation-and-remediation-capabilities"></a>自動調査および修復機能の自動化レベル

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Microsoft Defender for Endpoint の自動調査および修復 (AIR) 機能は、いくつかのレベルの自動化に構成できます。 自動化レベルは、AIR 調査後の修復アクションが自動的に実行されるのか、承認時にのみ実行されるのかに影響します。  
- *完全な自動化* (推奨) は、悪意のあると判断されたアーティファクトに対して修復アクションが自動的に実行されます。
- *半自動化とは、* 一部の修復アクションが自動的に実行されますが、他の修復アクションは承認を待って実行される前に行われます。 (「オートメーションのレベル」 [の表を参照](#levels-of-automation)してください。
- 保留中か完了かの修復アクションはすべて、アクション センター ( ) で追跡されます [https://securitycenter.windows.com](https://securitycenter.windows.com) 。 

> [!TIP]
> 最良の結果を得る場合は、AIR を構成するときに完全自動化を [使用することをお勧めします](configure-automated-investigations-remediation.md)。 過去 1 年間に収集および分析されたデータは、フル オートメーションを使用しているお客様が、低レベルの自動化を使用している顧客よりも 40% 高信頼のマルウェア サンプルが削除されたことを示しています。 完全な自動化は、セキュリティ運用リソースを解放し、戦略的な取り組みにより集中するのに役立ちます。

## <a name="levels-of-automation"></a>オートメーションのレベル

次の表では、オートメーションの各レベルと動作について説明します。

|オートメーション レベル | 説明|
|:---|:---|
|**完全 - 脅威を自動的に修復する** <br/>(フル オートメーションとも *呼ばれます*)| 完全な自動化により、修復アクションは自動的に実行されます。 実行される修復アクションはすべて、[履歴] タブの [[アクション](auto-investigation-action-center.md) センター] で **表示** できます。必要に応じて、修復アクションを元に戻すことができます。<br/><br/>**_完全な自動化は推奨_* され、Microsoft Defender for Endpoint で 2020 年 8 月 16 日以降に作成されたテナントでは既定で選択され、デバイス グループがまだ定義されていません。*  |
|**Semi - 修復の承認が必要** <br/>(セミオートメーション *とも呼ばれます*)| このレベルのセミオートメーションでは、修復アクションに対して承認 *が* 必要です。 このような保留中のアクションは、[保留中] タブの [[](auto-investigation-action-center.md)アクション センター] で表示および **承認** できます。<br/><br/>*このレベルのセミオートメーションは、Microsoft Defender for Endpoint で 2020 年 8 月 16 日より前に作成されたテナントに対して既定で選択され、デバイス グループは定義されていません。*|
|**Semi - コア フォルダー修復の承認が必要** <br/>(また、セミオートメーション *の一種*)  | このレベルのセミオートメーションでは、コア フォルダー内のファイルまたは実行可能ファイルに必要な修復アクションに対して承認が必要です。 コア フォルダーには、オペレーティング システム ディレクトリ () などの **Windows** があります `\windows\*` 。<br/><br/>修復アクションは、他の (コア以外の) フォルダーにあるファイルまたは実行可能ファイルに対して自動的に実行できます。 <br/><br/>コア フォルダー内のファイルまたは実行可能ファイルの保留中のアクションは、[保留中] タブの [](auto-investigation-action-center.md)[アクション センター] で表示および **承認** できます。 <br/><br/>他のフォルダーのファイルまたは実行可能ファイルに対して実行されたアクションは、[アクション [](auto-investigation-action-center.md)センター] の [履歴] タブ **で表示** できます。 |
|**Semi - 一時フォルダー以外の修復の承認が必要** <br/>(また、セミオートメーション *の一種*)| このレベルのセミオートメーションでは、一時フォルダーに含まれるファイルまたは実行可能ファイルに必要な修復アクションに対して承認 *が* 必要です。 <br/><br/>一時フォルダーには、次の例を含めできます。 <br/>- `\users\*\appdata\local\temp\*`<br/>- `\documents and settings\*\local settings\temp\*` <br/>- `\documents and settings\*\local settings\temporary\*`<br/>- `\windows\temp\*`<br/>- `\users\*\downloads\*`<br/>- `\program files\` <br/>- `\program files (x86)\*`<br/>- `\documents and settings\*\users\*`<br/><br/>修復アクションは、一時フォルダー内のファイルまたは実行可能ファイルに対して自動的に実行できます。 <br/><br/>一時フォルダーに含めされていないファイルまたは実行可能ファイルの保留中のアクションは、[保留中] タブの [](auto-investigation-action-center.md)[アクション センター] で表示および **承認** できます。<br/><br/>一時フォルダー内のファイルまたは実行可能ファイルに対して実行されたアクションは、[履歴] タブ [](auto-investigation-action-center.md)の [アクション センター] で表示および **承認** できます。   |
|**自動応答なし** <br/>(オートメーションなしとも *呼ばれます*) | 自動化を行う必要がない場合、組織のデバイスでは自動調査は実行されません。 その結果、自動調査の結果として修復アクションや保留中は実行されません。 ただし、ウイルス対策機能と次世代保護機能[](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)の構成方法によっては、望ましくない可能性のあるアプリケーションからの保護など、他の脅威保護機能が有効になる場合があります。<br/><br/>***組織の *デバイスの* セキュリティ** 体制が低下しますので、自動化なしオプションの使用は推奨されません。 [オートメーション レベルを完全オートメーション (または](/microsoft-365/security/defender-endpoint/machine-groups)少なくとも半オートメーション) *に設定する場合を検討してください。 |

## <a name="important-points-about-automation-levels"></a>オートメーション レベルに関する重要な点

- 完全な自動化は、信頼性、効率、および安全であることが証明され、すべてのお客様にお勧めします。 完全な自動化により、重要なセキュリティ リソースが解放されますので、戦略的な取り組みにより重点的に取り組む必要があります。

- Microsoft Defender for Endpoint を使用して新しいテナント (2020 年 8 月 16 日以降に作成されたテナントを含む) は、既定で完全自動化に設定されます。

- セキュリティ チームが自動化レベルでデバイス グループを定義している場合、これらの設定は、展開される新しい既定の設定では変更されません。 

- 既定のオートメーション設定を維持するか、組織のニーズに応じて変更できます。 設定を変更するには、 [オートメーションのレベルを設定します](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation#set-up-device-groups)。

## <a name="next-steps"></a>次の手順

- [Microsoft Defender for Endpoint で自動調査および修復機能を構成する](configure-automated-investigations-remediation.md)

- [アクション センターにアクセスする](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
