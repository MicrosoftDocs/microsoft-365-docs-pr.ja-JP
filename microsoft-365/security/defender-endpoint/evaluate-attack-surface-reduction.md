---
title: 攻撃表面の縮小ルールを評価する
description: カスタム デモ ツールを使用して攻撃をブロックおよび防止する攻撃表面の縮小方法について説明します。
keywords: 攻撃表面の縮小、腰、ホスト侵入防止システム、保護ルール、悪用防止、脆弱性対策、悪用、感染防止、評価、テスト、デモ
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
audience: ITPro
author: levinec
ms.author: ellevin
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 13b1ac5f71f2bc24ad6f52af6722e12fab935270
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51067795"
---
# <a name="evaluate-attack-surface-reduction-rules"></a>攻撃表面の縮小ルールを評価する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Microsoft Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-enablesiem-abovefoldlink)

攻撃表面の縮小ルールは、デバイスやネットワークを侵害するためにマルウェアが通常使用するアクションを防ぐのに役立ちます。 次のエディションとバージョンの Windows を実行しているデバイスに対して攻撃表面の縮小ルールを設定します。

- Windows 10 Pro [バージョン 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) 以降
- Windows 10 Enterprise バージョン [1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) 以降
- Windows Server バージョン [1803 (半期チャネル)](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1803) 以降
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)

監査モードで組織の機能を直接テストすることで、攻撃表面の縮小ルールを評価する方法について学習します。

> [!TIP]
> また、Microsoft Defender for Endpoint のデモ シナリオ web サイト demo.wd.microsoft.com 機能 [が](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) 動作し、動作を確認することもできます。

## <a name="use-audit-mode-to-measure-impact"></a>監査モードを使用して影響を測定する

監査モードで攻撃表面の縮小ルールを有効にして、機能が完全に有効になっている場合にブロックされた可能性があるアプリのレコードを表示します。 組織で機能がどのように機能されるかをテストして、その機能が業務上のアプリに影響を与えなかねない方法を確認します。 また、通常の使用中にルールが発生する頻度を確認することもできます。

監査モードで攻撃表面の縮小ルールを有効にするには、次の PowerShell コマンドレットを使用します。

```PowerShell
Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
```

攻撃 `<rule ID>` 表面の [縮小ルールの GUID 値はここで指定します](attack-surface-reduction.md#attack-surface-reduction-rules)。

監査モードで追加された攻撃表面の縮小ルールを有効にするには、次の PowerShell コマンドレットを使用します。

```PowerShell
(Get-MpPreference).AttackSurfaceReductionRules_Ids | Foreach {Add-MpPreference -AttackSurfaceReductionRules_Ids $_ -AttackSurfaceReductionRules_Actions AuditMode}
```

> [!TIP]
> 組織内での攻撃表面の縮小ルールの動作を完全に監査する場合は、管理ツールを使用して、ネットワーク内のデバイスにこの設定を展開する必要があります。

グループ ポリシー、Intune、またはモバイル デバイス管理 (MDM) 構成サービス プロバイダー (CSP) を使用して、設定を構成および展開することもできます。 詳しくは、「攻撃表面の [縮小ルール」のメイン記事を参照](attack-surface-reduction.md) してください。

## <a name="review-attack-surface-reduction-events-in-windows-event-viewer"></a>Windows イベント ビューアーで攻撃表面の縮小イベントを確認する

ブロックされているアプリを確認するには、Microsoft-Windows-Windows Defender/運用ログでイベント ビューアーを開き、イベント ID 1121 をフィルター処理します。 次の表に、すべてのネットワーク保護イベントを示します。

イベント ID | 説明
-|-
 5007 | 設定が変更された場合のイベント
 1121 | ブロック モードで攻撃表面の縮小ルールが発生した場合のイベント
 1122 | 監査モードで攻撃表面の縮小ルールが発生した場合のイベント

## <a name="customize-attack-surface-reduction-rules"></a>攻撃表面の縮小ルールをカスタマイズする

評価中に、各ルールを個別に構成したり、特定のファイルやプロセスが機能によって評価されるのを除外したりすることもできます。

グループ [ポリシーと](customize-attack-surface-reduction.md) MDM CSP ポリシーを含む管理ツールを使用して機能を構成する方法については、「攻撃表面の縮小ルールをカスタマイズする」を参照してください。

## <a name="see-also"></a>関連項目

* [攻撃表面の縮小ルールを使用して攻撃表面を削減する](attack-surface-reduction.md)
* [監査モードを使用して、監査Windows Defender](audit-windows-defender.md)
* [攻撃表面の縮小に関する FAQ](attack-surface-reduction.md)