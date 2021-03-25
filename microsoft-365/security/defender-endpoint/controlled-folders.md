---
title: フォルダー アクセス制御によるファイルの暗号化から重要なフォルダーをランサムウェアから保護する
description: 既定のフォルダー内のファイルは、悪意のあるアプリによって変更されるから保護できます。 ランサムウェアによるファイルの暗号化を防止します。
keywords: フォルダー アクセスの制御, Windows 10, Windows Defender, ランサムウェア, 保護, ファイル, フォルダー
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
audience: ITPro
ms.date: 02/03/2021
ms.reviewer: v-maave
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: how-to
ms.openlocfilehash: b937dd41f0296f2cf4102f41f8ab10bd55e1c35d
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "51200283"
---
# <a name="protect-important-folders-with-controlled-folder-access"></a>フォルダー アクセスを制御して重要なフォルダーを保護する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-controlled-folder-access"></a>フォルダー アクセスの制御とは

フォルダー アクセスの制御により、ランサムウェアなどの悪意のあるアプリや脅威から貴重なデータを保護できます。 フォルダー アクセスの制御により、既知の信頼できるアプリの一覧に対してアプリをチェックすることで、データを保護します。 Windows Server 2019 および Windows 10 クライアントでサポートされている場合、管理フォルダー アクセスは、Windows セキュリティ アプリ、Microsoft Endpoint Configuration Manager、または Intune (管理対象デバイスの場合) を使用して有効にできます。 

> [!NOTE]
> スクリプト エンジンは信頼されていないので、制御された保護されたフォルダーへのアクセスを許可することはできません。  たとえば、PowerShell は、証明書とファイルインジケーターで許可されている場合でも、フォルダー アクセスの制御 [によって信頼されません](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/indicator-certificates)。 

フォルダー アクセスの制御は [、Microsoft Defender for Endpoint](microsoft-defender-endpoint.md)で最適に機能します。これにより、通常のアラート調査シナリオの一環として、フォルダー アクセスの制御イベントとブロックに関する詳細なレポート [が提供されます](investigate-alerts.md)。

> [!TIP]
> フォルダー アクセスブロックの制御は、アラート キューにアラートを [生成しない](alerts-queue.md)。 ただし、高度な検索を使用している間、またはカスタム検出ルール[](investigate-machines.md)を使用して、デバイス[](advanced-hunting-overview.md)タイムライン ビューでフォルダー アクセス ブロックの制御に関する情報[を表示できます](custom-detection-rules.md)。

## <a name="how-does-controlled-folder-access-work"></a>フォルダー アクセスの制御方法

フォルダー アクセスの制御は、信頼できるアプリが保護されたフォルダーにアクセスできるようにすることでのみ機能します。 保護されたフォルダーは、フォルダー アクセスの制御が構成されている場合に指定されます。 通常、一般的に使用されるフォルダー (ドキュメント、画像、ダウンロードなど) は、管理フォルダーの一覧に含まれます。 

フォルダー アクセスの制御は、信頼できるアプリの一覧で機能します。 信頼できるソフトウェアの一覧に含まれるアプリは、期待通り動作します。 リストに含まれていないアプリは、保護されたフォルダー内のファイルに変更を加えません。 

アプリは、その普及率と評判に基づいてリストに追加されます。 組織全体で非常に普及しているアプリで、悪意のあると見なされる動作を一度も表示したことがないアプリは、信頼できると見なされます。 これらのアプリは自動的にリストに追加されます。

アプリは、Configuration Manager または Intune を使用して、信頼できるリストに手動で追加することもできます。 アプリのファイル インジケーター [の追加](respond-file-alerts.md#add-indicator-to-block-or-allow-a-file) などの追加アクションは、セキュリティ センター コンソールから実行できます。

## <a name="why-controlled-folder-access-is-important"></a>フォルダー アクセスの制御が重要な理由

フォルダー アクセスの制御は、ドキュメントや情報をランサムウェアから保護する場合に特に役立 [ちます](https://www.microsoft.com/wdsi/threats/ransomware)。 ランサムウェア攻撃では、ファイルが暗号化され、人質に保持される可能性があります。 フォルダー アクセスを制御すると、アプリが保護されたフォルダー内のファイルに変更を加えたコンピューターに通知が表示されます。 通知は [、会社の詳細](customize-attack-surface-reduction.md#customize-the-notification) と連絡先情報でカスタマイズできます。 また、ルールを個別に有効にして、機能が監視する手法をカスタマイズすることもできます。

保護 [されたフォルダーには、](#review-controlled-folder-access-events-in-windows-event-viewer) 一般的なシステム フォルダー (ブート セクターを含む) が含まれます。さらにフォルダー [を追加できます](customize-controlled-folders.md#protect-additional-folders)。 アプリが [保護されたフォルダー](customize-controlled-folders.md#allow-specific-apps-to-make-changes-to-controlled-folders) へのアクセス権を与えるのを許可することもできます。

監査モードを [使用して](audit-windows-defender.md) 、フォルダー アクセスが有効になっている場合に組織に与える影響を評価できます。 また、テスト グラウンド web サイト [Windows Defenderサイト](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) demo.wd.microsoft.com 機能が動作し、動作を確認できます。

フォルダー アクセスの制御は、次のバージョンの Windows でサポートされています。
- [Windows 10 バージョン 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) 以降
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)

## <a name="windows-system-folders-are-protected-by-default"></a>Windows システム フォルダーは既定で保護されています

Windows システム フォルダーは、他のいくつかのフォルダーと共に、既定で保護されます。 

- `c:\Users\<username>\Documents`
- `c:\Users\Public\Documents`
- `c:\Users\<username>\Pictures`
- `c:\Users\Public\Pictures`
- `c:\Users\Public\Videos`
- `c:\Users\<username>\Videos`
- `c:\Users\<username>\Music`
- `c:\Users\Public\Music`
- `c:\Users\<username>\Favorites`

> [!NOTE]
> 追加のフォルダーを保護として構成できますが、既定で保護されている Windows システム フォルダーは削除できません。

## <a name="requirements-for-controlled-folder-access"></a>フォルダー アクセスの制御の要件

フォルダー アクセスの制御には [、Microsoft Defender ウイルス対策のリアルタイム保護を有効にする必要があります](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus)。

## <a name="review-controlled-folder-access-events-in-the-microsoft-defender-security-center"></a>Microsoft Defender セキュリティ センターでフォルダー アクセスの制御イベントを確認する

Defender for Endpoint は、アラート調査シナリオの一環として、イベントとブロックに関する詳細 [なレポートを提供します](investigate-alerts.md)。

高度な検索を使用して、Microsoft Defender for Endpoint データ [を照会できます](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/advanced-hunting-windows-defender-advanced-threat-protection)。 監査モード[を使用している](audit-windows-defender.md)場合は、高度な検索[](advanced-hunting-overview.md)を使用して、フォルダー アクセスの制御設定が有効になっている場合に環境に与える影響を確認できます。

クエリ例:

```PowerShell
DeviceEvents
| where ActionType in ('ControlledFolderAccessViolationAudited','ControlledFolderAccessViolationBlocked')
```

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>Windows イベント ビューアーでフォルダー アクセスの制御イベントを確認する

Windows イベント ログを確認して、コントロールされたフォルダー アクセス ブロック (または監査) アプリで作成されるイベントを確認できます。

1. 評価パッケージ [をダウンロードし](https://aka.ms/mp7z2w) 、デバイス上 *cfa-events.xmlアクセスしやすい* 場所にファイルを抽出します。
2. [ **スタート] メニューに** 「イベント ビューアー」と入力して、Windows イベント ビューアーを開きます。
3. 左側のパネルの [アクション] **で、[** カスタム ビュー **のインポート... を選択します**。
4. 抽出した場所に *移動cfa-events.xml選択* します。 または [、XML を直接コピーします](event-views.md)。
5. **[OK]** をクリックします。

次の表に、フォルダー アクセスの制御に関連するイベントを示します。

|イベント ID | 説明 |
|:---|:---|
|5007 | 設定が変更された場合のイベント |
|1124 | 監査されたフォルダー アクセス イベント | 
|1123 | ブロックされたフォルダー アクセス イベント |

## <a name="view-or-change-the-list-of-protected-folders"></a>保護されたフォルダーの一覧を表示または変更する

Windows セキュリティ アプリを使用して、フォルダー アクセスの制御によって保護されているフォルダーの一覧を表示できます。 

1. Windows 10 デバイスで、Windows セキュリティ アプリを開きます。
2. [ **ウイルス対策&を選択します**。
3. [ **ランサムウェア保護] で、[** ランサムウェア **保護の管理] を選択します**。
4. フォルダー アクセスの制御がオフになっている場合は、有効にする必要があります。 保護 **されたフォルダーを選択します**。
5. 次のいずれかの手順を実行します。
   - フォルダーを追加するには、[+ 保護 **されたフォルダーの追加] を選択します**。
   - フォルダーを削除するには、フォルダーを選択し、[削除] を **選択します**。 

> [!NOTE]
> [Windows システム フォルダーは](#windows-system-folders-are-protected-by-default) 既定で保護され、一覧から削除することはできません。

## <a name="see-also"></a>関連項目

- [フォルダー アクセスの制御を評価する](evaluate-controlled-folder-access.md)
- [フォルダー アクセスの制御をカスタマイズする](customize-controlled-folders.md)
- [より多くのフォルダーを保護する](customize-controlled-folders.md#protect-additional-folders)