---
title: Microsoft Defender ウイルス対策が更新プログラムを受信する方法と場所を管理する
description: Microsoft Defender ウイルス対策が保護更新プログラムを受け取る方法のフォールバック順序を管理します。
keywords: 更新プログラム、セキュリティ 基準、保護、フォールバック順序、ADL、MMPC、UNC、ファイル パス、共有、WSUS
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.reviewer: pahuijbr
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.openlocfilehash: d218e9dea58f064fd54dbd9bb976f512a721df91
ms.sourcegitcommit: bbad1938b6661d4a6bca99f235c44e521b1fb662
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2021
ms.locfileid: "53007330"
---
# <a name="manage-the-sources-for-microsoft-defender-antivirus-protection-updates"></a>Microsoft Defender ウイルス対策更新プログラムのソースを管理する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=22154037)

<a id="protection-updates"></a>
<!-- this has been used as anchor in VDI content -->

ウイルス対策保護を最新の状態に保つことは重要です。 Microsoft Defender ウイルス対策の保護更新プログラムを管理するには、次の 2 つのコンポーネントがあります。 
- *更新* プログラムのダウンロード先。そして 
- *更新* プログラムをダウンロードして適用する場合。 

この記事では、更新プログラムをダウンロードする場所を指定する方法について説明します (これはフォールバック順序とも呼ばれています)。 更新 [プログラムの動作の](manage-updates-baselines-microsoft-defender-antivirus.md) 概要、および更新プログラムの他の側面 (更新プログラムのスケジュール設定など) を構成する方法については、「Microsoft Defender ウイルス対策更新プログラムの管理と基準計画の適用」を参照してください。

> [!IMPORTANT]
> Microsoft Defender ウイルス対策セキュリティ インテリジェンスの更新プログラムは、Windows Update を通じて配信され、2019 年 10 月 21 日月曜日から開始され、すべてのセキュリティ インテリジェンス更新プログラムは SHA-2 専用に署名されます。 セキュリティ インテリジェンスを更新するには、SHA-2 をサポートするためにデバイスを更新する必要があります。 詳細については [、「2019 SHA-2 Code Signing Support requirement for Windows および WSUS」を参照してください](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus)。  


<a id="fallback-order"></a>

## <a name="fallback-order"></a>フォールバック順序

通常、プライマリ ソースから更新プログラムを個別にダウンロードし、その後、ネットワーク構成に基づいて優先度の高い順に他のソースをダウンロードするエンドポイントを構成します。 更新プログラムは、指定した順序でソースから取得されます。 ソースが使用できない場合は、リスト内の次のソースがすぐに使用されます。

更新プログラムが発行されると、更新プログラムのサイズを最小限に抑えるためのロジックが適用されます。 ほとんどの場合、最新の更新プログラムと、デバイスに現在インストールされている更新プログラム (デルタと呼ばれます) の違いだけがダウンロードされて適用されます。 ただし、デルタのサイズは、次の 2 つの主な要因に依存します。
- デバイスの最後の更新プログラムの年齢。そして 
- 更新プログラムのダウンロードと適用に使用されるソース。 

エンドポイントの更新プログラムが古いほど、ダウンロードは大きくなります。 ただし、ダウンロード頻度も考慮する必要があります。 更新スケジュールが頻繁に行われると、ネットワーク使用量が増加しますが、スケジュールが低いほどダウンロードあたりのファイル サイズが大きくなる可能性があります。 

エンドポイントが更新プログラムを取得する場所を指定できる場所は 5 種類です。 

- [Microsoft Update](https://support.microsoft.com/help/12373/windows-update-faq)
- [Windows Server Update Service](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)
- [Microsoft Endpoint Configuration Manager](/configmgr/core/servers/manage/updates)
- [ネットワーク ファイル共有](#unc-share)
- [Microsoft Defender ウイルス対策および他](https://www.microsoft.com/en-us/wdsi/defenderupdates) の Microsoft マルウェア対策のセキュリティ インテリジェンス更新プログラム (ポリシーとレジストリには、マイクロソフト マルウェア プロテクション センター (MMPC) セキュリティ インテリジェンス (以前の名前) としてリストされている場合があります。

Microsoft Update では、最高レベルの保護を確保するために、迅速なリリースが可能になります。つまり、頻繁にダウンロードする頻度が少なめになります。 Windows Server Update Service、Microsoft Endpoint Configuration Manager、Microsoft セキュリティ インテリジェンス更新プログラムのソースは、更新プログラムの頻度が低い。 したがって、デルタを大きくすると、ダウンロードが大きくなる可能性があります。 

> [!IMPORTANT]
> Windows Server Update Service または Microsoft Update の後に Microsoft [Security](https://www.microsoft.com/security/portal/definitions/adl.aspx) インテリジェンス ページの更新プログラムをフォールバック ソースとして設定した場合、更新プログラムは、現在の更新プログラムが古いと見なされた場合にのみ、セキュリティ インテリジェンス更新プログラムからダウンロードされます。 (既定では、Windows Server Update Service または Microsoft Update サービスから更新プログラムを適用できない日が 7 日間連続しています)。
> ただし、保護が古いとして報告される日数を [設定できます](/windows/threat-protection/microsoft-defender-antivirus/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date)。<p>
> 2019 年 10 月 21 日月曜日から、セキュリティ インテリジェンス更新プログラムは SHA-2 専用に署名されます。 最新のセキュリティ インテリジェンス更新プログラムを取得するには、SHA-2 をサポートするためにデバイスを更新する必要があります。 詳細については [、「2019 SHA-2 Code Signing Support requirement for Windows および WSUS」を参照してください](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus)。

各ソースには、次の表で説明するように、更新プログラムを発行する頻度に加えて、ネットワークの構成方法に依存する一般的なシナリオがあります。

|場所 | シナリオ例 |
|---|---|
|Windows Server Update Service | Windows Server Update Service を使用して、ネットワークの更新プログラムを管理しています。|
|Microsoft Update | エンドポイントを Microsoft Update に直接接続する必要があります。 これは、エンタープライズ ネットワークに不定期に接続するエンドポイントや、更新プログラムを管理するために Windows Server Update Service を使用しない場合に役立ちます。|
|ファイル共有 | インターネットに接続されていないデバイス (VM など) があります。 インターネットに接続された VM ホストを使用して、更新プログラムをネットワーク共有にダウンロードし、そこから VM が更新プログラムを取得できます。 仮想デスクトップ [インフラストラクチャ (VDI)](deployment-vdi-microsoft-defender-antivirus.md) 環境でファイル共有を使用する方法については、VDI 展開ガイドを参照してください。|
|Microsoft エンドポイント マネージャー | Microsoft Endpoint Manager を使用してエンドポイントを更新しています。|
|Microsoft Defender ウイルス対策と他の Microsoft マルウェア対策 (以前は MMPC と呼ばば) のセキュリティ インテリジェンス更新プログラム |[SHA-2 をサポートするためにデバイスが更新されていないことを確認します](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus)。 Microsoft Defender ウイルス対策セキュリティ インテリジェンスの更新プログラムは Windows Update を通じて配信され、2019 年 10 月 21 日月曜日からセキュリティ インテリジェンス更新プログラムは SHA-2 によって排他的に署名されます。 <br/>最近の感染による最新の保護更新プログラムをダウンロードするか、VDI 展開用の強力な基本イメージを準備 [するのに役立ちます](deployment-vdi-microsoft-defender-antivirus.md)。 このオプションは通常、プライマリ ソースではなく、最終的なフォールバック ソースとしてのみ使用する必要があります。 指定した日数、Windows Server Update Service または Microsoft Update から更新プログラムをダウンロードできない場合にのみ [使用されます](/windows/threat-protection/microsoft-defender-antivirus/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date)。|

グループ ポリシー、Microsoft Endpoint Configuration Manager、PowerShell コマンドレット、WMI で更新ソースを使用する順序を管理できます。

> [!IMPORTANT]
> Windows Server Update Service をダウンロード場所として設定する場合は、場所の指定に使用する管理ツールに関係なく、更新プログラムを承認する必要があります。 Windows Server Update Service を使用して自動承認ルールを設定できます。これは、更新プログラムが少なくとも 1 日に 1 回届く場合に役立つ場合があります。 詳細については、「スタンドアロン [Windows Server Update Service でのエンドポイント保護更新プログラムの同期」を参照してください](/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus)。

この記事の手順では、最初に注文を設定する方法と、注文を有効にしている場合は [ファイル共有] オプションを設定する方法について説明します。

## <a name="use-group-policy-to-manage-the-update-location"></a>グループ ポリシーを使用して更新場所を管理する

1. グループ ポリシー管理マシンで、グループ ポリシー [管理](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))コンソールを開き、構成するグループ ポリシー オブジェクトを右クリックし、[編集] をクリック **します**。

2. グループ ポリシー **管理エディターで、[コンピューター** の構成] **に移動します**。

3. [ポリシー **] をクリックし** 、[ **管理用テンプレート] をクリックします**。

4. 署名の更新プログラムを使用 **してツリー** Windows Defender Windows コンポーネント  >    >  **に展開し**、次の設定を構成します。

   1.  [セキュリティ インテリジェンス **更新プログラム** をダウンロードするためのソースの順序を定義する] 設定をダブルクリックし、オプションを [有効] に **設定します**。

   2.  次のスクリーンショットに示すように、1 つのパイプで区切られたソースの順序 `InternalDefinitionUpdateServer|MicrosoftUpdateServer|MMPC` を入力します。たとえば、次のようにします。

      :::image type="content" source="../../media/wdav-order-update-sources.png" alt-text="ソースの順序を示すグループ ポリシー設定":::

   3. **[OK]** を選択します。 これにより、保護更新プログラムのソースの順序が設定されます。

   4. [セキュリティ インテリジェンス更新プログラムをダウンロード **するための** ファイル共有の定義] 設定をダブルクリックし、オプションを [有効] に **設定します**。

   5. ファイル共有ソースを指定します。 複数のソースがある場合は、使用する順序で各ソースを 1 つのパイプで区切って入力します。 パス [を示す標準の UNC](/openspecs/windows_protocols/ms-dtyp/62e862f4-2a51-452e-8eeb-dc4ff5ee33cc) 表記を使用します。たとえば、次のようになります `\\host-name1\share-name\object-name|\\host-name2\share-name\object-name` 。  パスを入力しない場合、VM が更新プログラムをダウンロードすると、このソースはスキップされます。

   6. **[OK]** をクリックします。 これにより、ソースが参照される場合のファイル共有の順序が [ソースの順序の定義 **... グループ** ポリシー設定で設定されます。

> [!NOTE]
> Windows 10 バージョン 1703 から 1809 まで、ポリシー パスは Windows コンポーネント **> Microsoft Defender** Antivirus > Signature Updates for Windows 10 バージョン 1903 の場合、ポリシー パスは Windows コンポーネント > Microsoft Defender Antivirus >**セキュリティ** インテリジェンス更新プログラムです。

## <a name="use-configuration-manager-to-manage-the-update-location"></a>Configuration Manager を使用して更新場所を管理する

Microsoft Endpoint Manager (現在のブランチ) の構成の詳細については、「Configure Security Intelligence Updates for Endpoint [Protection」](/configmgr/protect/deploy-use/endpoint-definition-updates) を参照してください。


## <a name="use-powershell-cmdlets-to-manage-the-update-location"></a>PowerShell コマンドレットを使用して更新場所を管理する

更新順序を設定するには、次の PowerShell コマンドレットを使用します。

```PowerShell
Set-MpPreference -SignatureFallbackOrder {LOCATION|LOCATION|LOCATION|LOCATION}
Set-MpPreference -SignatureDefinitionUpdateFileSharesSource {\\UNC SHARE PATH|\\UNC SHARE PATH}
```
詳細については、次の記事を参照してください。
- [Set-MpPreference -SignatureFallbackOrder](/powershell/module/defender/set-mppreference)
- [Set-MpPreference -SignatureDefinitionUpdateFileSharesSource](/powershell/module/defender/set-mppreference#-signaturedefinitionupdatefilesharessources)
- [PowerShell コマンドレットを使用して Microsoft Defender ウイルス対策を構成および実行する](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Defender コマンドレット](/powershell/module/defender/index)

## <a name="use-windows-management-instruction-wmi-to-manage-the-update-location"></a>Windows 管理命令 (WMI) を使用して更新場所を管理する

次の [**プロパティ** に対して **、MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) クラスの Set メソッドを使用します。

```WMI
SignatureFallbackOrder
SignatureDefinitionUpdateFileSharesSource
```

詳細については、次の記事を参照してください。
- [Windows Defender WMIv2 API](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="use-mobile-device-management-mdm-to-manage-the-update-location"></a>モバイル デバイス管理 (MDM) を使用して更新場所を管理する

MDM [の構成の詳細については、「Policy CSP - Defender/SignatureUpdateFallbackOrder」](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdatefallbackorder) を参照してください。

## <a name="what-if-were-using-a-third-party-vendor"></a>サードパーティベンダーを使用している場合は、

この記事では、更新プログラムを構成および管理する方法について説明Microsoft Defender ウイルス対策。 ただし、サード パーティベンダーは、これらのタスクを実行するために使用できます。 

たとえば、Contoso 社が Fabrikam を雇ってセキュリティ ソリューションを管理したとします。これには、セキュリティ ソリューションMicrosoft Defender ウイルス対策。 Fabrikam は通常、Windows[管理](./use-wmi-microsoft-defender-antivirus.md)インストルメンテーション[、PowerShell](./use-powershell-cmdlets-microsoft-defender-antivirus.md)コマンドレット、または Windowsコマンド ラインを使用[して](./command-line-arguments-microsoft-defender-antivirus.md)、パッチと更新プログラムを展開します。 

> [!NOTE]
> Microsoft は、サード パーティ製のソリューションをテストして管理Microsoft Defender ウイルス対策。

<a id="unc-share"></a>
## <a name="create-a-unc-share-for-security-intelligence-updates"></a>セキュリティ インテリジェンス更新プログラムの UNC 共有を作成する

スケジュールされたタスクを使用して MMPC サイトからセキュリティ インテリジェンス更新プログラムをダウンロードするネットワーク ファイル共有 (UNC/マップドライブ) を設定します。

1. 共有をプロビジョニングして更新プログラムをダウンロードするシステムで、スクリプトを保存するフォルダーを作成します。
    ```DOS
    Start, CMD (Run as admin)
    MD C:\Tool\PS-Scripts\
    ```

2. 署名の更新を保存するフォルダーを作成します。
    ```DOS
    MD C:\Temp\TempSigs\x64
    MD C:\Temp\TempSigs\x86
    ```

3. PowerShell スクリプトをダウンロードするには、次[の www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4。](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4)

4. [手動 **ダウンロード] をクリックします**。

5. [生 **の nupkg ファイルをダウンロードする] をクリックします**。

6. ファイルを抽出します。

7. ファイルをコピーSignatureDownloadCustomTask.ps1作成したフォルダー C:\Tool\PS-Scripts\ にコピーします。

8. コマンド ラインを使用して、スケジュールされたタスクを設定します。
    > [!NOTE]
    > 更新プログラムには、完全とデルタの 2 種類があります。
   - x64 デルタの場合:

       ```DOS
       Powershell (Run as admin)
    
       C:\Tool\PS-Scripts\
    
       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $true -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - x64 フルの場合:

       ```DOS
       Powershell (Run as admin)
    
       C:\Tool\PS-Scripts\
    
       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $false -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - x86 デルタの場合:

       ```DOS
       Powershell (Run as admin)
    
       C:\Tool\PS-Scripts\
    
       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $true -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - x86 フルの場合:

       ```DOS
       Powershell (Run as admin)
    
       C:\Tool\PS-Scripts\
    
       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $false -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

    > [!NOTE]
    > スケジュールされたタスクが作成されると、[タスク スケジューラ] の [Microsoft\Windows\Windows Defender
9. 各タスクを手動で実行し、次のフォルダーにデータ (mpam-d.exe、mpam-fe.exe、および nis_full.exe) が含まれています (別の場所を選択している可能性があります)。

   - C:\Temp\TempSigs\x86
   - C:\Temp\TempSigs\x64

   スケジュールされたタスクが失敗した場合は、次のコマンドを実行します。

    ```DOS
    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $False -destDir C:\Temp\TempSigs\x64"
    
    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $True -destDir C:\Temp\TempSigs\x64"
    
    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $False -destDir C:\Temp\TempSigs\x86"
    
    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $True -destDir C:\Temp\TempSigs\x86"
    ```
    > [!NOTE]
    > 問題は、実行ポリシーが原因である可能性があります。
    
10. C:\Temp\TempSigs をポイントする共有を作成します (例: \\ server\updates)。
    > [!NOTE]
    > 少なくとも、認証されたユーザーには "読み取り" アクセス権が必要です。
11. ポリシー内の共有場所を共有に設定します。

    > [!NOTE]
    > パスに x64 (または x86) フォルダーを追加しない。 このプロセスmpcmdrun.exe自動的に追加されます。

## <a name="related-articles"></a>関連記事

- [展開Microsoft Defender ウイルス対策](deploy-manage-report-microsoft-defender-antivirus.md)
- [更新Microsoft Defender ウイルス対策を管理し、基準計画を適用する](manage-updates-baselines-microsoft-defender-antivirus.md)
- [最新のエンドポイントの更新プログラムを管理する](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [イベントベースの強制更新プログラムを管理する](manage-event-based-updates-microsoft-defender-antivirus.md)
- [モバイル デバイスと VM の更新プログラムを管理する](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Microsoft Defender ウイルス対策 (Windows 10)](microsoft-defender-antivirus-in-windows-10.md)
