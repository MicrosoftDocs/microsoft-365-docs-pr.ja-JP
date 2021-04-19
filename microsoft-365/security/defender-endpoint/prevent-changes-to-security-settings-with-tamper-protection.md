---
title: 改ざん防止でセキュリティ設定を保護する
ms.reviewer: shwjha, hayhov
manager: dansimp
description: タンパープロテクションを使用して、悪意のあるアプリが重要なセキュリティ設定を変更するのを防ぐ。
keywords: マルウェア、防御者、ウイルス対策、改ざん防止
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: normal
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.technology: mde
ms.openlocfilehash: 84864965d7a18902a01307c1dcf373fa7c0534e8
ms.sourcegitcommit: 7a339c9f7039825d131b39481ddf54c57b021b11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "51765577"
---
# <a name="protect-security-settings-with-tamper-protection"></a>改ざん防止でセキュリティ設定を保護する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**

- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/)

タンパープロテクションは、次のいずれかのバージョンの Windows を実行しているデバイスで使用できます。

- Windows 10
- Windows Server 2019
- Windows Server バージョン 1803 以降
- Windows Server 2016

## <a name="overview"></a>概要

一部の種類のサイバー攻撃では、悪いアクターがコンピューターでウイルス対策保護などのセキュリティ機能を無効にしようとします。 悪いアクターは、データに簡単にアクセスしたり、マルウェアをインストールしたり、データ、ID、デバイスを悪用したりするために、セキュリティ機能を無効にしています。 タンパープロテクションは、このような事態が発生するのを防ぐのに役立ちます。

タンパープロテクションを使用すると、悪意のあるアプリは次のようなアクションを実行できます。

- ウイルスおよび脅威の保護の無効化
- リアルタイム保護の無効化
- 動作の監視の無効化
- ウイルス対策(IOfficeAntivirus (IOAV) など) の無効化
- クラウド配信の保護の無効化
- セキュリティ インテリジェンスの更新プログラムの削除

### <a name="how-it-works"></a>メカニズム

タンパープロテクションは基本的に Microsoft Defender ウイルス対策をロックし、次のようなアプリやメソッドを通じてセキュリティ設定が変更されるのを防ぐ。

- Windows デバイスのレジストリ エディターで設定を構成する
- PowerShell コマンドレットによる設定の変更
- グループ ポリシーによるセキュリティ設定の編集または削除

改ざん防止では、セキュリティ設定を表示できない場合があります。 また、改ざん防止は、サードパーティのウイルス対策アプリが Windows セキュリティ アプリに登録する方法には影響を与えかねない。 組織で Windows 10 Enterprise E5 を使用している場合、個々のユーザーは改ざん防止設定を変更できます。このような場合、改ざん防止はセキュリティ チームによって管理されます。

### <a name="what-do-you-want-to-do"></a>目的に合ったトピックをクリックしてください

| このタスクを実行するには... | このセクションを参照してください。 |
|:---|:---|
| Microsoft Defender セキュリティ センターでタンパープロテクションをオン (またはオフ) にする <p>テナント全体の改ざん防止を管理する | [Microsoft Defender セキュリティ センターを使用して組織の改ざん防止を管理する](#manage-tamper-protection-for-your-organization-using-the-microsoft-defender-security-center) |
| Intune を使用して組織のすべてまたは一部のタンパープロテクションをオン (またはオフ) にする <p>組織内の改ざん防止設定を微調整する | [Intune を使用して組織の改ざん防止を管理する](#manage-tamper-protection-for-your-organization-using-intune) |
| Configuration Manager を使用して組織の改ざん防止を有効 (または無効にする) | [Configuration Manager バージョン 2006 でテナント接続を使用して組織の改ざん防止を管理する](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006) |
| 個々のデバイスのタンパープロテクションをオン (またはオフ) にする | [個々のデバイスで改ざん防止を管理する](#manage-tamper-protection-on-an-individual-device) |
| デバイスでの改ざんの試みについての詳細を表示する | [改ざんの試行に関する情報を表示する](#view-information-about-tampering-attempts) |
| セキュリティに関する推奨事項を確認する | [セキュリティに関する推奨事項を確認する](#review-your-security-recommendations) |
| よく寄せられる質問 (FAQ) の一覧を確認する | [FAQ を参照する](#view-information-about-tampering-attempts) |

## <a name="manage-tamper-protection-for-your-organization-using-the-microsoft-defender-security-center"></a>Microsoft Defender セキュリティ センターを使用して組織の改ざん防止を管理する

Microsoft Defender セキュリティ センター ( ) を使用して、テナントのタンパープロテクションを有効または無効にできます [https://securitycenter.windows.com](https://securitycenter.windows.com) 。 以下に注意点を示します。

- 現在、Microsoft Defender セキュリティ センターでタンパープロテクションを管理するオプションは、新しい展開では既定でオンになっています。 既存の展開では、改ざん防止はオプトインベースで利用できます。近い将来、この方法を既定の方法にする予定です。 (オプトインするには、Microsoft Defender セキュリティ センターで、[設定] を **選択します。**  > **高度な機能**  > **タンパープロテクション**.) 

- Microsoft Defender セキュリティ センターを使用してタンパープロテクションを管理する場合は、Intune またはテナント接続方法を使用する必要があります。

- Microsoft Defender セキュリティ センターで改ざん防止を管理する場合、この設定はテナント全体に適用され、Windows 10、Windows Server 2016、または Windows Server 2019 を実行しているすべてのデバイスに影響を与えます。 タンパープロテクションを微調整するには (一部のデバイスではタンパープロテクションをオンにし、他のデバイスではオフにするなど [)、Intune](#manage-tamper-protection-for-your-organization-using-intune) または Configuration Manager をテナント接続で [使用します](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)。

- ハイブリッド環境がある場合、Intune で構成されたタンパープロテクション設定は、Microsoft Defender セキュリティ センターで構成された設定よりも優先されます。 

### <a name="requirements-for-managing-tamper-protection-in-the-microsoft-defender-security-center"></a>Microsoft Defender セキュリティ センターでタンパープロテクションを管理するための要件

- グローバル管理者、セキュリティ [管理者、](/microsoft-365/security/defender-endpoint/assign-portal-access)セキュリティ操作など、適切なアクセス許可が必要です。

- Windows デバイスは、次のいずれかのバージョンの Windows を実行している必要があります。
   - Windows 10
   - [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
   - Windows Server バージョン [1803](/windows/release-health/status-windows-10-1803) 以降
   - [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
   - リリースの詳細については [、「Windows 10 リリース情報」を参照してください](/windows/release-health/release-information)。

- デバイスは、Microsoft [Defender for Endpoint にオンボードされている必要があります](/microsoft-365/security/defender-endpoint/onboarding)。

- デバイスでマルウェア対策プラットフォーム バージョン 4.18.2010.7 (以上) とマルウェア対策エンジン バージョン 1.1.17600.5 (以上) を使用している必要があります。 ([Microsoft Defender ウイルス対策の更新プログラムを管理し、ベースラインを適用](manage-updates-baselines-microsoft-defender-antivirus.md)します。)

- [クラウドによる保護を](enable-cloud-protection-microsoft-defender-antivirus.md) 有効にする必要があります。

### <a name="turn-tamper-protection-on-or-off-in-the-microsoft-defender-security-center"></a>Microsoft Defender セキュリティ センターでタンパープロテクションをオン (またはオフ) にする 

![Microsoft Defender セキュリティ センターでタンパープロテクションを有効にする](images/mde-turn-tamperprotect-on.png)

1. Microsoft Defender セキュリティ センター ( ) に移動 [https://securitycenter.windows.com](https://securitycenter.windows.com) し、サインインします。

2. [設定 **] を選択します**。

3. [全般高度 **な**  >  **機能] に移動** し、タンパープロテクションを有効にしてください。

## <a name="manage-tamper-protection-for-your-organization-using-intune"></a>Intune を使用して組織の改ざん防止を管理する

組織のセキュリティ チームの一員であり、サブスクリプションに [Intune](/intune/fundamentals/what-is-intune)が含まれる場合は [、Microsoft Endpoint Manager](https://endpoint.microsoft.com) 管理センター ポータルで組織の改ざん防止を有効 (または無効) にできます。 タンパープロテクションの設定を微調整する場合は、Intune を使用します。 たとえば、一部のデバイスでタンパープロテクションを有効にするが、すべてではない場合は、Intune を使用します。

### <a name="requirements-for-managing-tamper-protection-in-intune"></a>Intune でタンパープロテクションを管理するための要件

- グローバル管理者、セキュリティ [管理者、](/microsoft-365/security/defender-endpoint/assign-portal-access)セキュリティ操作など、適切なアクセス許可が必要です。

- 組織は Intune を [使用してデバイスを管理します](/intune/fundamentals/what-is-device-management)。 ([Intune ライセンスが](/intune/fundamentals/licenses) 必要です。Intune は Microsoft 365 E5 に含まれています)。

- Windows デバイスで Windows 10 OS [1709 、1803、1809](/windows/release-health/status-windows-10-1709)以降を実行している必要があります。 [](/windows/release-health/status-windows-10-1803) [](/windows/release-health/status-windows-10-1809-and-windows-server-2019) (リリースの詳細については [、「Windows 10 リリース情報」を参照してください](/windows/release-health/release-information))。

- Windows セキュリティを使用して、セキュリティ [インテリジェンスが](https://www.microsoft.com/wdsi/definitions) バージョン 1.287.60.0 (以上) に更新されている必要があります。

- デバイスでマルウェア対策プラットフォーム バージョン 4.18.1906.3 (以上) とマルウェア対策エンジン バージョン 1.1.15500.X (以上) を使用している必要があります。 ([Microsoft Defender ウイルス対策の更新プログラムを管理し、ベースラインを適用](manage-updates-baselines-microsoft-defender-antivirus.md)します。)

### <a name="turn-tamper-protection-on-or-off-in-intune"></a>Intune でタンパープロテクションをオン (またはオフ) にする

![Intune で改ざん防止を有効にする](images/turnontamperprotect-MEM.png)

1. Microsoft Endpoint Manager 管理 [センターに移動し](https://endpoint.microsoft.com) 、仕事または学校のアカウントでサインインします。

2. [**デバイス**  >  **構成プロファイル] を選択します**。

3. 次の設定を含むプロファイルを作成します。
    - **プラットフォーム: Windows 10 以降**
    - **プロファイルの種類: エンドポイント保護**
    - **カテゴリ: Microsoft Defender セキュリティ センター**
    - **タンパープロテクション: 有効**

4. プロファイルを 1 つ以上のグループに割り当てる。

### <a name="are-you-using-windows-os-1709-1803-or-1809"></a>Windows OS 1709、1803、または 1809 を使用していますか?

Windows 10 OS  [1709、1803、](/windows/release-health/status-windows-10-1709)または[1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019)を使用している場合、Windows セキュリティ アプリにタンパープロテクションは表示されます。 [](/windows/release-health/status-windows-10-1803) 代わりに、PowerShell を使用して、改ざん防止が有効になっているかどうかを判断できます。

#### <a name="use-powershell-to-determine-whether-tamper-protection-is-turned-on"></a>PowerShell を使用して、改ざん防止が有効になっているかどうかを判断する

1. アプリを開Windows PowerShellします。

2. [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus?preserve-view=true&view=win10-ps) PowerShell コマンドレットを使用します。

3. 結果の一覧で、 を探します `IsTamperProtected` 。 (true の値は *、改* ざん防止が有効になっているという意味です。

## <a name="manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006"></a>Configuration Manager バージョン 2006 で組織の改ざん防止を管理する

Configuration Manager の [バージョン 2006 を](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2006)使用している場合は、テナント接続というメソッドを使用して、Windows 10、Windows Server 2016、および Windows Server 2019 で改ざん防止設定を *管理できます*。 テナント接続を使用すると、オンプレミス専用の Configuration Manager デバイスを Microsoft Endpoint Manager 管理センターに同期し、エンドポイント セキュリティ構成ポリシーをデバイスのオンプレミス コレクション&できます。

![エンドポイント マネージャーでの Windows セキュリティ エクスペリエンス](images/win-security- exp-policy-endpt-security.png)

> [!NOTE]
> この手順を使用して、Windows 10 および Windows Server 2019 を実行しているデバイスに改ざん防止を拡張できます。 この手順で説明されているリソースの前提条件と他の情報を必ず確認してください。

1. テナント接続を設定します。 このヘルプについては、「Microsoft Endpoint Manager テナント接続: デバイスの同期と [デバイスの操作」を参照してください](/mem/configmgr/tenant-attach/device-sync-actions)。

2. Microsoft [Endpoint Manager 管理センターで、[](https://go.microsoft.com/fwlink/?linkid=2109431)エンドポイント **セキュリティ** ウイルス対策] に移動し、[+ ポリシーの作成]  >  **を選択します**。<br/> 
   - [プラットフォーム **] ボックスの** 一覧で **、[Windows 10] と [Windows Server (ConfigMgr) ] を選択します**。  
   - [プロファイル] **リストで** 、[Windows セキュリティ エクスペリエンス **(プレビュー) ] を選択します**。 <br/>

3. デバイス コレクションにポリシーを展開します。

### <a name="need-help-with-this-method"></a>このメソッドのヘルプが必要ですか? 

以下のリソースを参照してください。

- [Microsoft Intune の Windows セキュリティ エクスペリエンス プロファイルの設定](/mem/intune/protect/antivirus-security-experience-windows-settings)
- [Tech Community Blog: Configuration Manager テナント接続クライアントのタンパープロテクションの発表](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

## <a name="manage-tamper-protection-on-an-individual-device"></a>個々のデバイスで改ざん防止を管理する

> [!NOTE]
> 改ざん防止ブロックは、レジストリを介して Microsoft Defender ウイルス対策の設定を変更しようと試みをブロックします。
>
> これらの設定を変更するサードパーティのセキュリティ製品やエンタープライズ インストール スクリプトにタンパープロテクションが干渉しないようにするには **、「Windows Security」** に移動し、セキュリティ インテリジェンスをバージョン 1.287.60.0 以降に更新します。 (「セキュリティ [インテリジェンスの更新プログラム」を参照](https://www.microsoft.com/wdsi/definitions)してください。
>
> この更新プログラムを作成すると、改ざん防止はレジストリ設定を保護し続け、ログはエラーを返さずに変更を試みる。

ホーム ユーザーである場合、またはセキュリティ チームが管理する設定の対象ではない場合は、Windows セキュリティ アプリを使用して改ざん防止を管理できます。 改ざん防止などのセキュリティ設定を変更するには、デバイスに適切な管理者アクセス許可が必要です。

Windows セキュリティ アプリに表示される情報を次に示します。

![Windows 10 Home でタンパープロテクションが有効になっている](images/tamperprotectionturnedon.png)

1. [スタート **] を選択** し、[セキュリティ] の入力 *を開始します*。 検索結果で、[Windows セキュリティ] **を選択します**。

2. [**ウイルス対策&ウイルス**  >  **対策] を選択&の設定を選択します**。

3. タン **パープロテクションを** **On または** Off に **設定します**。



## <a name="view-information-about-tampering-attempts"></a>改ざんの試行に関する情報を表示する

改ざんの試みは、通常、より大きなサイバー攻撃を示します。 悪いアクターは、セキュリティ設定を変更して、検出されない状態を維持します。 組織のセキュリティ チームの一員である場合は、そのような試みについての情報を表示し、脅威を軽減するために適切なアクションを実行できます。

改ざんの試行が検出されると、Microsoft Defender セキュリティ センター ( ) で [アラートが発生](/microsoft-365/security/defender-endpoint/portal-overview) します [https://securitycenter.windows.com](https://securitycenter.windows.com) 。

![Microsoft Defender セキュリティ センター](images/tamperattemptalert.png)

Microsoft [](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) Defender for [](/microsoft-365/security/defender-endpoint/advanced-hunting-overview) Endpoint のエンドポイント検出および応答機能と高度なハンティング機能を使用して、セキュリティ運用チームはそのような試みを調査し、対処できます。

## <a name="review-your-security-recommendations"></a>セキュリティに関する推奨事項を確認する

タンパープロテクションは [、脅威&管理機能と](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) 統合されます。 [セキュリティに関する推奨事項には](/microsoft-365/security/defender-endpoint/tvm-security-recommendation) 、改ざん防止が有効になっていることを確認する方法が含まれます。 たとえば、次の図に示 *すように*、改ざん時に検索できます。

![改ざん防止により、セキュリティに関する推奨事項が表示される](/images/securityrecs-tamperprotect.jpg)

結果では、[タンパープロテクションを **有効** にする] を選択して詳細を確認し、有効にできます。

![改ざん防止を有効にする](images/tamperprotectsecurityrecos.png)

脅威の脆弱性管理の詳細& Microsoft Defender セキュリティ センターの「脅威& [脆弱性管理」を参照してください](/microsoft-365/security/defender-endpoint/tvm-dashboard-insights#threat--vulnerability-management-in-microsoft-defender-security-center)。

## <a name="frequently-asked-questions"></a>よく寄せられる質問

### <a name="to-which-windows-os-versions-is-configuring-tamper-protection-is-applicable"></a>タンパープロテクションを構成している Windows OS のバージョンは、どのバージョンに適用されますか?

Windows 10 OS [1709](/windows/release-health/status-windows-10-1709)、 [1803](/windows/release-health/status-windows-10-1803)、 [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019)以降と [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint).

Configuration Manager バージョン 2006 をテナント接続で使用している場合は、改ざん防止を Windows Server 2019 に拡張できます。 「 [テナント接続: 管理センターからエンドポイント セキュリティ](/mem/configmgr/tenant-attach/deploy-antivirus-policy)ウイルス対策ポリシーを作成して展開する (プレビュー)」を参照してください。

### <a name="will-tamper-protection-have-any-impact-on-third-party-antivirus-registration"></a>改ざん防止はサードパーティのウイルス対策登録に影響しますか?

いいえ。 サードパーティのウイルス対策製品は、引き続き Windows Security アプリケーションに登録されます。

### <a name="what-happens-if-microsoft-defender-antivirus-is-not-active-on-a-device"></a>Microsoft Defender ウイルス対策がデバイスでアクティブではない場合は、どうなるでしょうか。

Microsoft Defender for Endpoint にオンボードされているデバイスでは、Microsoft Defender Antivirus がパッシブ モードで実行されます。 改ざん防止は、サービスとその機能を引き続き保護します。 

### <a name="how-can-i-turn-tamper-protection-onoff"></a>改ざん防止のオン/オフを切り替えますか?

ホーム ユーザーの場合は、「個々のデバイスで [タンパープロテクションを管理する」を参照してください](#manage-tamper-protection-on-an-individual-device)。

Microsoft Defender for [Endpoint](/microsoft-365/security/defender-endpoint)を使用している組織の場合は、他のエンドポイント保護機能を管理する方法と同様に、Intune でタンパープロテクションを管理できる必要があります。 この記事の以下のセクションを参照してください。 

- [Intune を使用して改ざん防止を管理する](#manage-tamper-protection-for-your-organization-using-intune)
- [Configuration Manager バージョン 2006 を使用して改ざん防止を管理する](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)
- [Microsoft Defender セキュリティ センターを使用して改ざん防止を管理する](#manage-tamper-protection-for-your-organization-using-the-microsoft-defender-security-center) (現在プレビュー中)

### <a name="how-does-configuring-tamper-protection-in-intune-affect-how-i-manage-microsoft-defender-antivirus-through-my-group-policy"></a>Intune でタンパープロテクションを構成すると、グループ ポリシーを通じて Microsoft Defender ウイルス対策を管理する方法にどのような影響がありますか?

通常のグループ ポリシーは改ざん防止には適用されません。改ざん防止がオンの場合、Microsoft Defender ウイルス対策の設定に対する変更は無視されます。 

### <a name="for-microsoft-defender-for-endpoint-is-configuring-tamper-protection-in-intune-targeted-to-the-entire-organization-only"></a>Microsoft Defender for Endpoint の場合、Intune でタンパープロテクションを組織全体のみを対象に構成していますか?

Intune または Microsoft Endpoint Manager でタンパープロテクションを構成するには、組織全体と特定のデバイスとユーザー グループを対象とすることができます。

### <a name="can-i-configure-tamper-protection-in-microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager でタンパープロテクションを構成できますか?

テナント接続を使用している場合は、Microsoft Endpoint Configuration Manager を使用できます。 以下のリソースを参照してください。
- [Configuration Manager バージョン 2006 で組織の改ざん防止を管理する](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)
- [Tech Community ブログ: Configuration Manager テナント接続クライアントのタンパープロテクションの発表](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

### <a name="i-have-the-windows-e3-enrollment-can-i-use-configuring-tamper-protection-in-intune"></a>Windows E3 登録があります。 Intune でタンパープロテクションの構成を使用できますか?

現在、Intune でタンパープロテクションを構成できるのは [、Microsoft Defender for Endpoint をお持ちのお客様のみです](/microsoft-365/security/defender-endpoint)。

### <a name="what-happens-if-i-try-to-change-microsoft-defender-for-endpoint-settings-in-intune-microsoft-endpoint-configuration-manager-and-windows-management-instrumentation-when-tamper-protection-is-enabled-on-a-device"></a>デバイスでタンパープロテクションが有効になっているときに、Intune、Microsoft Endpoint Configuration Manager、および Windows 管理インストルメンテーションで Microsoft Defender for Endpoint の設定を変更すると、どうなるでしょうか。

改ざん防止によって保護されている機能を変更できない。このような変更要求は無視されます。

### <a name="im-an-enterprise-customer-can-local-admins-change-tamper-protection-on-their-devices"></a>エンタープライズ顧客です。 ローカル管理者は、デバイスの改ざん防止を変更できますか?

いいえ。 ローカル管理者は、改ざん防止の設定を変更または変更できません。

### <a name="what-happens-if-my-device-is-onboarded-with-microsoft-defender-for-endpoint-and-then-goes-into-an-off-boarded-state"></a>デバイスが Microsoft Defender for Endpoint にオンボードされ、オフボード状態に入った場合は、どうなるでしょうか。

デバイスが Microsoft Defender for Endpoint からオフボードされている場合、タンパープロテクションが有効になります。これは管理されていないデバイスの既定の状態です。 

### <a name="will-there-be-an-alert-about-tamper-protection-status-changing-in-the-microsoft-defender-security-center"></a>Microsoft Defender セキュリティ センターで改ざん防止の状態が変更された場合、警告が表示されますか?

はい。 アラートは [アラート] の下 [https://securitycenter.microsoft.com](https://securitycenter.microsoft.com) に **表示されます**。

セキュリティ運用チームは、次の例のような検索クエリも使用できます。

`DeviceAlertEvents | where Title == "Tamper Protection bypass"`

[改ざんの試行に関する情報を表示します](#view-information-about-tampering-attempts)。

## <a name="see-also"></a>関連項目

[Microsoft Intune のエンドポイント保護を使用して Windows PC をセキュリティで保護する](/intune/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

[Microsoft Defender for Endpoint の概要を確認する](/microsoft-365/security/defender-endpoint)

[より良い一緒に:Microsoft Defender Antivirus と Microsoft Defender for Endpoint](why-use-microsoft-defender-antivirus.md)