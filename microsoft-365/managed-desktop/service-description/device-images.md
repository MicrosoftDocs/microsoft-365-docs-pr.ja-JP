---
title: デバイス イメージ
description: 新しいデバイスを注文する場合、または既存のデバイスを再利用する場合のイメージ要件
keywords: Microsoft マネージド デスクトップ、Microsoft 365、サービス、ドキュメント
ms.service: m365-md
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: 9a263cbc6bdd0d521e835f086967a6f7236c6948
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51167043"
---
# <a name="device-images"></a>デバイス イメージ


新しい[デバイスを注文](#new-devices)する場合でも[](#existing-devices)、既存のデバイスを再利用する場合でも、デバイス上のイメージがデバイス要件を満たしていることを確認するためのいくつかのオプション[があります](device-requirements.md#check-hardware-requirements)。

## <a name="new-devices"></a>新しいデバイス
承認された製造元から新しいデバイスを[](device-requirements.md#minimum-requirements)注文する場合は、次の手順に従って、適切な Microsoft Managed Desktop イメージとソフトウェア構成でデバイスを出荷します。

### <a name="dell"></a>Dell
Microsoft Managed Desktop によって承認されたイメージが注文のデバイスに適用されるのを確認する Dell 営業担当者と直接作業します。 Dell デバイス、イメージ、および注文プロセスに関する詳細な質問については、次の MMD_at_dell@dell.com。

### <a name="hp"></a>HP 
HP から新しいデバイスを注文する場合は、[プログラム デバイス] に示すように、各モデルの [追加要件] セクションに記載されている特定の SKU を [必ず使用してください](device-list.md#hp)。

例外として承認されているが、現在 [デバイス一覧] ページに[](customizing.md)表示されていない HP からデバイスを注文する場合は、必ずモデルに使用する SKU を要求してください。 例外要求を使用してこの情報を取得するために HP と作業します。 次のアドレスを使用して、デバイスとデバイスの順序付け手順に関する質問については、HP に直接お問い合わせください。
 
- 南北アメリカ: mmd-americas@hp.com
- ヨーロッパ/中東/アフリカ: mmd-emea@hp.com
- アジア太平洋/日本: mmd-apj@hp.com
- グローバル: mmd@hp.com

### <a name="lenovo"></a>Lenovo
Microsoft Managed Desktop で使用するために Lenovo からデバイスを注文する場合は、注文の一部として含まれる特定のパーツ番号を指定する必要があります。 Lenovo の営業担当者または Lenovo チャネル パートナーに問い合わせて、デバイス要件を満たすシステムを使用して"特別入札 *モデル"* を作成 [してください。](device-requirements.md#minimum-requirements) Microsoft Managed Desktop と互換性のある事前読み込みイメージを含めるには、営業担当者に「システム構築ブロックのパーツ番号 *SBB0Q94938 – MMD Enablement*」を参照してください。

現在、Microsoft Managed Desktop サポートで有効になっている製品は次のとおりです。

- L13 Gen 1
- L13 Yoga Gen 1
- L14 Gen 1 (Intel)
- L14 Gen 1 (AMD)
- L15 Gen 1 (Intel)
- L15 Gen 1 (AMD)
- X1 Carbon Gen 8
- X1 Yoga Gen 5
- T14 Gen 1 (Intel)
- T14 Gen 1 (AMD)
- T15 Gen 1
- X13 Gen 1 (Intel)


### <a name="microsoft"></a>Microsoft
デバイス要件を満たすすべての Microsoft デバイスには、Microsoft Managed Desktop で動作するイメージが用意されています。 他の手順は必要ありません。

Microsoft デバイスのファクトリで利用可能な最新のイメージを取得するには、Surface スペシャリストと一緒に Surface "Pegged PO" プロセスを使用します。

## <a name="existing-devices"></a>既存のデバイス

既存のデバイスは、デバイス要件とソフトウェア要件の両方を[](device-requirements.md#minimum-requirements)満たしている限り[再利用できます](device-requirements.md#installed-software)。 製造元に関連する手順に従います。

デバイスは、製造元のイメージを使用するか、Microsoft Managed Desktop "ユニバーサル イメージ" を使用して再イメージ化できます。 適切な製造元イメージを取得するには、再利用するモデルの新[](#new-devices)しいデバイスを少なくとも 1 つ注文できます。 その後、そのデバイスからイメージを取得し、まったく同じモデルの他のデバイスに適用できます。

> [!NOTE]
> イメージの作成、テスト、展開は、ユーザーが責任を負います。 また、カスタム イメージ ("ユニバーサル イメージ" を含む) の代わりに、可能な限り製造元が提供する適切な画像を使用することをお勧めします。

### <a name="hp"></a>HP

HP Corporate Ready Image に同梱されている HP 商用 PC には、 が含まれます。回復用の WIM ファイル。 このイメージを使用して、工場出荷時の復元イメージを同じモデルの他のデバイスに適用できます。

これらの手順では、デバイス上のすべてのデータが削除されます。そのため、開始する前に、保持するデータをバックアップする必要があります。

1. WinPE[を使用して起動可能な USB ドライブ](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive)を作成します。
2. C: SOURCES から \\ USB ドライブにこれらのファイルをコピーします。
    - 工場出荷時の回復 WIM ファイル (HP \_ EliteBook \_ 840 \_ G7 \_ ノートブック PC CR \_ \_ \_ 2004.wim など)
    - DEPLOY。CMD
    - ReCreatePartitions.txt
3. [WinPE にデバイスを起動する](https://store.hp.com/us/en/tech-takes/how-to-boot-from-usb-drive-on-windows-10-pcs) USB ドライブ。
4. コマンド プロンプトで、次のコマンド[をDiskpart.exe。 ](https://docs.microsoft.com/windows-server/administration/windows-commands/diskpart#additional-references)
5. Diskpart で、実行し、プライマリ 記憶域ディスク番号 (通常はディスク `list disk` 0) をメモします。
6. 入力して Diskpart を終了 `exit` します。
7. コマンド プロンプトで、 を実行します。sys_disk は、決定したプライマリ ストレージ ディスクのディスク番号であり、recovery_wim ファイル名です `deploy.cmd <sys_disk> <recovery_wim>` 。  前にコピーした WIM ファイル。
8. USB ドライブを取り外し、デバイスを再起動します。

### <a name="microsoft"></a>Microsoft 

Microsoft Surface デバイスには、各モデルに固有の "ベア メタル [回復"](https://support.microsoft.com/en-us/surfacerecoveryimage) イメージが含まれます。 これらのイメージを使用してデバイスを再イメージ化できます。

これらのイメージは Windows 回復環境 (WinRE) を使用し、これは手動プロセスです (自動化されません)。 「Surface の USB 回復ドライブ [を作成して使用する」の手順に従います](https://support.microsoft.com/surface/creating-and-using-a-usb-recovery-drive-for-surface-677852e2-ed34-45cb-40ef-398fc7d62c07)。


### <a name="universal-image"></a>ユニバーサル イメージ
Microsoft Managed Desktop は、Microsoft Managed Desktop で使用できる Windows 10 Pro と Microsoft 365 Apps for Enterprise を含むイメージを作成しました。 ただし、ユーザーがサインインしたら更新する必要がある古い Windows バージョンを意味する場合でも、可能な限り、製造元が提供する Microsoft Managed Desktop に適したイメージを使用してください。 Microsoft Managed Desktop Universal イメージの使用は、最終的なオプションである必要があります。

- 30~60 日ごとに最新の Windows 月次品質更新プログラムと、Microsoft 365 Apps for Enterprise 更新プログラムを少なくとも年 2 回更新して画像を更新します。
- イメージには、Windows の回復シナリオに従って Microsoft 365 Apps for Enterprise が復元されるのを確認するための回復プロビジョニング パッケージが含まれています。
- USB ドライブを使用してイメージを展開できます。 ドライバーを挿入するスクリプト可能なプロセスが含まれています (イメージに含まれるドキュメントで説明されています)。
- 含まれているスクリプトとフォルダーは、特定の累積的な更新プログラムの追加、ファイル コピー コードの追加、その他のチェックの実行など、他のカスタマイズで使用するために変更できます。
- ドライバーと品質更新プログラムは、USB ドライブからの展開中に Windows に追加されます。

> [!NOTE]
> 必要なすべてのドライバーを追加し、すべてのテストを実行し、最終的に展開されたイメージに問題が発生しなかからず確認する必要があります。 ユニバーサル イメージは"as-is" で提供されますが、技術的なガイダンスを提供し、質問に答えます。 連絡先 MMDImage@microsoft.com。

管理ポータルで変更要求を作成して、ユニバーサル イメージのコンテンツとドキュメントの要求を [送信します](../get-started/access-admin-portal.md)。

