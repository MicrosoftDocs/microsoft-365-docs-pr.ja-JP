---
title: Microsoft Defender 更新プログラムの段階的なロールアウト プロセスを管理する
description: 段階的な更新プロセスとコントロールの詳細
keywords: 更新、更新プロセス、コントロール、リリース
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
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: fac6205e3045828cf2bbcc27a9a8020c3d63186c
ms.sourcegitcommit: ccbdf2638fc6646bfb89450169953f4c3ce4b9b0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2021
ms.locfileid: "53105617"
---
#  <a name="manage-the-gradual-rollout-process-for-microsoft-defender-updates"></a>Microsoft Defender 更新プログラムの段階的なロールアウト プロセスを管理する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)


重要な保護機能を提供し、攻撃を防止するには、クライアント コンポーネントが最新の状態にすることが重要です。

機能は、次の複数のコンポーネントを介して提供されます。 

- [エンドポイント検出&応答](overview-endpoint-detection-response.md) 
- [クラウドによる保護による](microsoft-defender-antivirus-in-windows-10.md#microsoft-defender-antivirus-your-next-generation-protection)[次世代の保護](cloud-protection-microsoft-defender-antivirus.md) 
- [攻撃表面の縮小](overview-attack-surface-reduction.md)

更新プログラムは、段階的なリリース プロセスを使用して毎月リリースされます。 このプロセスは、早期障害検出が発生した時点で影響をキャッチし、大規模なロールアウトの前に迅速に対処するのに役立ちます。 

> [!NOTE]
> 日次定義の更新を制御する方法の詳細については、「定義の更新をスケジュールする - Microsoft Defender ウイルス対策[のWindowsを参照|Microsoft Docs](manage-protection-update-schedule-microsoft-defender-antivirus.md).定義の更新により、クラウドによる保護がエンドポイントで利用できない場合でも、次世代の保護が新しい脅威から防御されます。

## <a name="microsoft-gradual-rollout-model"></a>Microsoft 段階的ロールアウト モデル

次の段階的ロールアウト モデルは、毎月の Defender 更新プログラムに従います。

1. 最初のリリースはベータ チャネルのサブスクライバーに送信されます。
2. 検証、フィードバック、および修正が完了すると、段階的なロールアウト プロセスが調整された方法で開始され、最初にチャネルサブスクライバーをプレビューします。
3. その後、グローバル人口の残りの部分への更新プログラムのリリースに進み、10 ~ 100% のスケール アウトを行います。

エンジニアは継続的に影響を監視し、問題をエスカレートして、必要に応じて修正プログラムを作成します。

## <a name="how-to-customize-your-internal-deployment-process"></a>内部展開プロセスをカスタマイズする方法

コンピューターが Windows Update から Defender 更新プログラムを受け取っている場合、段階的なロールアウトプロセスによって、一部のコンピューターが他のコンピューターよりも早く Defender 更新プログラムを受け取る可能性があります。 次のセクションでは、更新プログラム チャネル構成を活用して、自動更新を特定のデバイス グループに異なる方法でフローできる戦略を定義する方法について説明します。

> [!NOTE]
> 独自の段階的なリリースを計画する場合は、プレビュー チャネルと段階的チャネルに登録されているデバイスを常に選択してください。 これにより、組織と Microsoft が環境固有の問題を防止または見つけて修正する機会が提供されます。

Windows Server Update Services (WSUS) や Microsoft Endpoint Configuration Manager (MECM) などの更新プログラムを受け取るコンピューターの場合、Microsoft Defender for Endpoint のオプションを含め、Windows のすべての更新プログラムに対してさらに多くのオプションを使用できます。

- WSUS、MECM のようなソリューションを使用して更新プログラムの配布とアプリケーションを管理する方法の詳細については、「Microsoft Defender ウイルス対策 更新プログラムの管理とベースラインの適用 - Windows セキュリティ | [Microsoft Docs](manage-updates-baselines-microsoft-defender-antivirus.md#product-updates).

## <a name="update-channels-for-monthly-updates"></a>月次更新プログラムのチャネルを更新する

コンピューターを更新チャネルに割り当て、コンピューターが毎月エンジンとプラットフォームの更新プログラムを受け取るケイデンスを定義できます。

更新プログラムを構成する方法の詳細については、「Microsoft Defender 更新プログラムのカスタム段階的ロールアウト プロセスを作成する」 [を参照してください](configure-updates.md)。

次の更新プログラム チャネルを使用できます。

| チャネル名  | 説明  | アプリケーション  |
|-|-|-|
| ベータ チャネル - プレリリース  | 他のユーザーより前に更新プログラムをテストする  | このチャネルに設定されたデバイスは、新しい月次更新プログラムを最初に受信します。 [ベータ チャネル] を選択して、Microsoft への問題の特定と報告に参加します。 Insider Program Windowsデバイスは、既定でこのチャネルにサブスクライブされます。 テスト環境でのみ使用できます。  |
| 最新機能提供チャネル (プレビュー)  | 段階的なリリース中に以前に **現在のチャネル** 更新プログラムを取得する  | このチャネルに設定されたデバイスには、段階的なリリース サイクルの最も早い更新プログラムが提供されます。 実稼働前/検証前の環境で推奨されます。  |
| 現在のチャネル (ステージ)  | 段階的なリリース中に後で現在のチャネル更新プログラムを取得する  | デバイスは、段階的なリリース サイクル中に後で更新プログラムを提供されます。 デバイスの母集団の小さな代表的な部分 (~10%)に適用する必要があります。  |
| 現在のチャネル (Broad) | 段階的なリリースの最後に更新プログラムを取得する  | 段階的なリリース サイクルが完了した後にのみ、デバイスに更新プログラムが提供されます。 実稼働人口 (~10~100%)の幅広いデバイスセットに適用する必要があります。  |
| (既定)  |   | このポリシーを無効にするか構成しない場合、デバイスは現在のチャネル (既定) に残ります。段階的なリリース サイクル中に自動的に最新の状態を維持します。 ほとんどのデバイスに適しています。  |

### <a name="update-channels-for-daily-definition-updates"></a>毎日の定義更新のチャネルを更新する

コンピューターをチャネルに割り当て、毎日の定義更新を受け取るケイデンスを定義できます。 月次プロセスとは異なり、Beta チャネルは提供され、この段階的なリリース サイクルは 1 日に複数回発生します。
  
| チャネル名  | 説明  | アプリケーション  |
|-|-|-|
| 現在のチャネル (ステージ)  | 段階的なリリース中に後で現在のチャネル更新プログラムを取得する  | デバイスは、段階的なリリース サイクル中に後で更新プログラムを提供されます。 デバイスの母集団の小さな代表的な部分 (~10%)に適用する必要があります。  |
| 現在のチャネル (Broad) | 段階的なリリースの最後に更新プログラムを取得する  | デバイスは、段階的なリリース サイクルの後に更新プログラムが提供されます。 制限付き更新プログラムのみを受信するデータセンター コンピューターに最適です。 注: この設定は、すべての Defender 更新プログラムに適用されます。  |
| (既定)  |   | このポリシーを無効にするか構成しない場合、デバイスは現在のチャネル (既定) に残ります。段階的なリリース サイクル中に自動的に最新の状態を維持します。 ほとんどのデバイスに適しています  |

> [!NOTE]
> 時間の遅延を利用する代わりに最新の署名を強制的に更新する場合は、まずこのポリシーを削除する必要があります。

## <a name="update-guidance"></a>更新のガイダンス

ほとんどの場合、Windows Update を使用する場合の推奨される構成は、エンドポイントが受信した際に、毎月の Defender 更新プログラムを受信して適用できます。 これにより、保護と、導入できる変更に関連する可能性のある影響の最適なバランスが提供されます。

自動 Defender 更新プログラムの段階的なロールアウトの制御が必要な環境では、展開グループを使用したアプローチを検討してください。

1. Insider プログラムWindows参加するか、デバイスのグループをベータ チャネルに割り当てる。
2. プレビュー チャネル (通常は検証環境) にオプトインするパイロット グループを指定して、新しい更新プログラムを早期に受信します。
3. 段階的なチャネルからの段階的なロールアウト中に後で更新プログラムを受け取るコンピューターのグループを指定します。 通常、これは人口の約 10% を代表します。
4. 段階的なリリース サイクルの完了後に更新プログラムを受け取るコンピューターのグループを指定します。 これらは通常、重要な実稼働システムです。

残りのデバイスの場合、既定の設定では、Microsoft の段階的なロールアウト プロセス中に新しい更新プログラムを受信し、それ以上の構成は必要ありません。 

このモデルの採用:
- 製品環境に到達する前に早期リリースをテストできます 
- 実稼働環境で定期的な更新プログラムを受け取り、重大な脅威に対する保護を確実に行います。

## <a name="management-tools"></a>管理ツール
月次更新プログラム用に独自のカスタム段階的ロールアウト プロセスを作成するには、次のツールを使用できます。

- グループ ポリシー
- Microsoft エンドポイント マネージャー
- PowerShell

これらのツールの使い方の詳細については、「Microsoft Defender 更新プログラムのカスタム段階的ロールアウト プロセスを作成する [」を参照してください](configure-updates.md)。
