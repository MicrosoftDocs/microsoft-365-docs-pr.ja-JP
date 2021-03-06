---
title: Windows Virtual Desktop の Windows 10 マルチセッション デバイスのオンボード
description: この記事の詳細については、「Windows 10デスクトップでのマルチセッション デバイスのオンボーディングWindows参照してください。
keywords: Windows仮想デスクトップ、WVD、microsoft Defender、エンドポイント、オンボード
search.product: eADQiWindows 10XVcnh
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
audience: ITPro
ms.topic: article
author: dansimp
ms.author: dansimp
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.openlocfilehash: 9114a825ad011f0b2a17cea4929ab2a09bfa2172
ms.sourcegitcommit: 0d1b065c94125b495e9886200f7918de3bda40b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/08/2021
ms.locfileid: "53339480"
---
# <a name="onboard-windows-10-multi-session-devices-in-windows-virtual-desktop"></a>Windows Virtual Desktop の Windows 10 マルチセッション デバイスのオンボード 
読み取り 6 分 

適用対象: 
- Windows 10仮想デスクトップ (WVD) でWindowsセッションを実行する場合 

Microsoft Defender for Endpoint は、VDI セッションと仮想デスクトップ セッションWindowsサポートしています。 組織のニーズに応じて、従業員が管理されていないデバイス、リモートの場所、または類似のシナリオから企業データやアプリにアクセスするために、VDI または Windows Virtual Desktop セッションを実装する必要があります。 Microsoft Defender for Endpoint を使用すると、これらの仮想マシンで異常なアクティビティを監視できます。

 ## <a name="before-you-begin"></a>開始する前に
非永続的な [VDI の考慮事項について理解してください](/microsoft-365/security/defender-endpoint/configure-endpoints-vdi#onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-1)。 仮想[Windows非](/azure/virtual-desktop/overview)永続化オプションは提供されませんが、新しいホストのプロビジョニングとマシンの再展開に使用できるゴールデン Windows イメージを使用する方法を提供します。 これにより、環境の変動性が高まるため、Microsoft Defender for Endpoint ポータルで作成および管理されるエントリに影響が及び、セキュリティ アナリストの可視性が低下する可能性があります。

> [!NOTE]
> オンボーディング方法の選択に応じて、デバイスは次のように Microsoft Defender for Endpoint ポータルに表示されます。 
> - 仮想デスクトップごとに 1 つのエントリ 
> - 仮想デスクトップごとに複数のエントリ 

Microsoft では、仮想Windows 1 つのエントリとして仮想デスクトップをオンボーディングする方法をお勧めします。 これにより、Microsoft Defender Endpoint ポータルでの調査エクスペリエンスが、コンピューター名に基づいて 1 つのデバイスのコンテキスト内に確実に表示されます。 WVD ホストを頻繁に削除および再展開する組織では、同じコンピューターの複数のオブジェクトが Microsoft Defender for Endpoint ポータルに作成されるのを防ぐため、このメソッドの使用を強く検討する必要があります。 これは、インシデントを調査するときに混乱を招く可能性があります。 テスト環境または非揮発性環境の場合は、別の方法で選択できます。 

Microsoft では、Microsoft Defender for Endpoint オンボーディング スクリプトを WVD ゴールデン イメージに追加する方法をお勧めします。 この方法で、このオンボーディング スクリプトが最初の起動時にすぐに実行されるのを確認できます。 これは、WVD ゴールデン イメージからプロビジョニングされたすべての WVD コンピューターで最初に起動スクリプトとして実行されます。 ただし、変更せずにギャラリー イメージのいずれかを使用している場合は、スクリプトを共有の場所に配置し、ローカル またはドメイン グループ ポリシーから呼び出します。 

> [!NOTE]
> WVD ゴールデン イメージ上の VDI オンボーディングスタートアップ スクリプトの配置と構成によって、WVD の起動時に実行されるスタートアップ スクリプトとして構成されます。 実際の WVD ゴールデン イメージのオンボードは推奨されません。 もう 1 つの考慮事項は、スクリプトの実行に使用されるメソッドです。 セッションを受信できるコンピューターとサービスへのデバイスオンボーディングの時間を短縮するには、スタートアップ/プロビジョニング プロセスの早い段階で実行する必要があります。 以下のシナリオ 1 & 2 では、これを考慮します。

### <a name="scenarios"></a>シナリオ
WVD ホスト コンピューターをオンボードする方法は次のとおりです。

- 起動時に、ゴールデン イメージ (または共有の場所から) でスクリプトを実行します。
- 管理ツールを使用してスクリプトを実行します。

#### <a name="scenario-1-using-local-group-policy"></a>*シナリオ 1: ローカル グループ ポリシーの使用*
このシナリオでは、スクリプトをゴールデン イメージに配置する必要があります。ローカル グループ ポリシーを使用して、起動プロセスの早い段階で実行します。

「非永続的仮想デスクトップ インフラストラクチャ [(VDI) デバイスのオンボード」の手順を使用します](configure-endpoints-vdi.md#onboard-the-non-persistent-virtual-desktop-infrastructure-vdi-devices)。

デバイスごとに 1 つのエントリの指示に従います。

#### <a name="scenario-2-using-domain-group-policy"></a>*シナリオ 2: ドメイン グループ ポリシーの使用*
このシナリオでは、中央に位置するスクリプトを使用し、ドメイン ベースのグループ ポリシーを使用してスクリプトを実行します。 また、スクリプトをゴールデン イメージに配置し、同じ方法で実行することもできます。

**セキュリティ センターWindowsDefenderATPOnboardingPackage.zipファイルをWindows Defenderする**

1. VDI 構成パッケージ ファイルを開.zip (WindowsDefenderATPOnboardingPackage.zip)  

    1. [新しいMicrosoft Defender セキュリティ センター] ウィンドウで、[オンボーディング]**設定**  >  **選択します**。 
    1. オペレーティング システムWindows 10を選択します。 
    1. [展開方法 **] フィールド** で、永続的でないエンドポイントの VDI オンボーディング スクリプトを選択します。 
    1. [パッケージ **のダウンロード] を** クリックし、.zip保存します。 

2. デバイスからアクセスできる.zipファイルの内容を読み取り専用の共有場所に抽出します。 **OptionalParamsPolicy** という名前のフォルダーと **、WindowsDefenderATPOnboardingScript.cmd** とファイルが必要 **Onboard-NonPersistentMachine.ps1。**

**グループ ポリシー管理コンソールを使用して、仮想マシンの起動時にスクリプトを実行する**

1. グループ ポリシー管理コンソール (GPMC) を開き、構成するグループ ポリシー オブジェクト (GPO) を右クリックし、[編集] を **クリックします**。

2. グループ ポリシー管理エディターで、[コンピューター構成の基本設定 \> **] コントロール** \> **パネルの設定に移動します**。 

3. [スケジュールされたタスク **] を右クリック** し、[**新規**] をクリックし、[イ **ミディ** エイト タスク] (少なくとも 7) をWindowsします。 

4. 開く [タスク] ウィンドウで、[全般] タブ **に移動** します。[セキュリティ **オプション] で、[****ユーザーまたはグループの変更] をクリックし、「SYSTEM」** と入力します。 [名前 **の確認] をクリック** し、[OK] をクリックします。 NT AUTHORITY\SYSTEM は、タスクが実行されるユーザー アカウントとして表示されます。 

5. [ **ユーザーがログオンするかどうかを実行する] を選択し** 、[最高の特権で実行する **] チェック ボックスを** オンにします。 

6. [操作] タブに **移動し** 、[新規] を **クリックします**。 [アクション **] フィールドで [プログラム** の開始] が選択されている必要があります。 次の情報を入力します。 

   `Action = "Start a program"`

   `Program/Script = C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe`

   `Add Arguments (optional) = -ExecutionPolicy Bypass -command "& \\Path\To\Onboard-NonPersistentMachine.ps1"`

   次に **、[OK] を** 選択し、開いている GPMC ウィンドウを閉じます。

#### <a name="scenario-3-onboarding-using-management-tools"></a>*シナリオ 3: 管理ツールを使用したオンボーディング*

管理ツールを使用してコンピューターを管理する予定の場合は、デバイスを管理ツールでオンボードMicrosoft Endpoint Configuration Manager。

詳細については、「Configuration Manager を使用[したオンボード Windows 10デバイス」を参照してください](configure-endpoints-sccm.md)。

> [!WARNING]
> 攻撃表面縮小ルールを[](attack-surface-reduction.md)使用する場合は、ルール["PSExec](attack-surface-reduction.md#block-process-creations-originating-from-psexec-and-wmi-commands)および WMI コマンドから発生するプロセスの作成をブロックする" は使用できません。このルールは、Microsoft Endpoint Configuration Manager による管理と互換性がありません。 このルールは、Configuration Manager クライアントが正しく機能するために使用する WMI コマンドをブロックします。 

> [!TIP]
> デバイスのオンボード後、検出テストを実行して、デバイスがサービスに適切にオンボードされていることを確認できます。 詳細については、「新しくオンボードされた Microsoft Defender for Endpoint デバイスで検出テストを実行する [」を参照してください](run-detection-test.md)。 

#### <a name="tagging-your-machines-when-building-your-golden-image"></a>ゴールデン イメージを作成する際のコンピューターのタグ付け 

オンボーディングの一環として、Microsoft セキュリティ センターで WVD マシンを容易に区別できるよう、コンピューター タグの設定を検討する必要があります。 詳細については、「レジストリ キーの [値を設定してデバイス タグを追加する」を参照してください](machine-tags.md#add-device-tags-by-setting-a-registry-key-value)。 

#### <a name="other-recommended-configuration-settings"></a>その他の推奨構成設定 

ゴールデン イメージを作成する場合は、初期保護設定も構成できます。 詳細については、「その他の推奨 [される構成設定」を参照してください](configure-endpoints-gp.md#other-recommended-configuration-settings)。 

また、FSlogix ユーザー プロファイルを使用している場合は、次のファイルを常時保護から除外することをお勧めします。 

**ファイルの除外:** 

`%ProgramFiles%\FSLogix\Apps\frxdrv.sys`

`%ProgramFiles%\FSLogix\Apps\frxdrvvt.sys`

`%ProgramFiles%\FSLogix\Apps\frxccd.sys`

`%TEMP%\*.VHD`

`%TEMP%\*.VHDX`

`%Windir%\TEMP\*.VHD`

`%Windir%\TEMP\*.VHDX`

`\\storageaccount.file.core.windows.net\share\*\*.VHD`

`\\storageaccount.file.core.windows.net\share\*\*.VHDX`

**プロセスを除外する:**

`%ProgramFiles%\FSLogix\Apps\frxccd.exe`

`%ProgramFiles%\FSLogix\Apps\frxccds.exe`

`%ProgramFiles%\FSLogix\Apps\frxsvc.exe`

#### <a name="licensing-requirements"></a>ライセンスの要件 

ライセンスに関する注意: Windows 10 Enterprise マルチセッションを使用する場合は、要件に応じて、Microsoft Defender for Endpoint (ユーザーあたり)、Windows Enterprise E5、Microsoft 365 Security、または Microsoft 365 E5 を介してすべてのユーザーにライセンスを取得するか、Azure Defender を介して VM のライセンスを取得するように選択できます。
エンドポイントの Microsoft Defender のライセンス要件については、「ライセンス要件」 [を参照してください](minimum-requirements.md#licensing-requirements)。

#### <a name="related-links"></a>関連リンク

[PowerShell を使用して Microsoft Defender の除外を追加する](/azure/architecture/example-scenario/wvd/windows-virtual-desktop-fslogix#add-exclusions-for-windows-defender-by-using-powershell)
