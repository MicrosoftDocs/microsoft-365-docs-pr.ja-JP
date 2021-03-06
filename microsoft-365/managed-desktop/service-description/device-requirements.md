---
title: デバイスの要件
description: デバイスがデバイスで動作する最小ハードウェア要件とソフトウェア要件の概要Microsoft マネージド デスクトップ
keywords: Microsoft マネージド デスクトップ、Microsoft 365、サービス、ドキュメント
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: b17585f7449f1151c7a5f5cd75d06b8e723fbe4b
ms.sourcegitcommit: 2fd60871975d61e60d4827b36cd689021fd2a4c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2021
ms.locfileid: "53438014"
---
# <a name="device-requirements"></a>デバイスの要件

Microsoft マネージド デスクトップに含めるデバイス要件を定期的に評価します。 この記事では、デバイスがデバイスで動作するために満たす必要があるハードウェア要件とソフトウェア要件Microsoft マネージド デスクトップ。 これらの要件に基づいて、サービスでの使用が既に承認されている特定のデバイスの一覧を確認できます。 ビジネス デバイス サイトMicrosoft マネージド デスクトップ[のサイトWindows 10 Proフィルター](https://www.microsoft.com/windowsforbusiness/view-all-devices)

> [!NOTE]
> これらの要件は、いつでも変更できますが、ハードウェア要件の変更に関する 30 日間の通知を提供します。 最近変更された要件は、 でマークされます **\*** 。 

## <a name="check-hardware-requirements"></a>ハードウェア要件の確認

デバイスの仕様を確認する以外に、ダウンロード可能な準備状況評価[](../get-ready/readiness-assessment-downloadable.md)チェッカーを使用して、特定のデバイスが必要な要件を満たしていることを確認することもできます。 また、このツールは、サービスが動作するために必要なネットワーク設定とエンドポイントもチェックします。

## <a name="minimum-requirements"></a>最小要件

デバイスは、これらの要件Microsoft マネージド デスクトップ以上の要件を満たす必要があります。

### <a name="manufacturer"></a>製造元

デバイスは、次のいずれかの製造元によって作成されている必要があります。

- Dell
- HP
- Lenovo
- Microsoft


### <a name="installed-software"></a>インストール済みソフトウェア

デバイスには、次のソフトウェアがプレインストールされている必要があります。

- Windows 10 Enterprise、Pro、または Pro ワークステーション エディション
- 64 ビット バージョンの Microsoft 365 Apps for enterprise 
- 適用可能なすべてのデバイス ドライバー

> [!NOTE]
> Windows 11 は、一般提供に達すると、プレインストールされたソフトウェアの追加オプションになります。
>
### <a name="physical-features"></a>物理機能

デバイスには、次の機能が必要です。

- UEFI セキュア ブートに対して有効 
- 信頼できるプラットフォーム モジュール 2.0 
- 仮想化ベースのセキュリティが可能 
- [BIOS でサポートされるハイパーバイザー](/windows-hardware/drivers/bringup/device-guard-and-credential-guard) で保護されたコード整合性

これらの機能とサービスが使用するテクノロジの詳細については[、「Microsoft マネージド デスクトップ」を参照してください](../intro/technologies.md)。

> [!NOTE]
>- ARMプロセッサはサポートされていません。
>- Windows 11 には追加の[ハードウェア要件があります](/windows/whats-new/windows-11-requirements)。

デバイスは、ストレージとメモリの次の制限を満たすか、または超える必要があります。

- ブート ドライブは、ハード ディスク以外の種類である必要があります。 たとえば、SSD、NVMe、および eMMC ドライブはすべて有効な選択肢です。
- ブート ドライブの容量は 128 GB 以上である必要があります。
- 内部デバイス メモリ (RAM) は 8 GB 以上である必要があります。

デバイスが 2020 年 7 月 1 日以降に作成された場合は、IR カメラ、指紋リーダー、または両方を使用して、デバイスをサポート[Windows Hello。](/windows-hardware/design/device-experiences/windows-hello-enhanced-sign-in-security)

## <a name="recommended-features"></a>推奨される機能

次の機能を備えたデバイスを選択すると、ユーザーのエクスペリエンスが向上します。

- Intel vPro-platform プロセッサまたは AMD Ryzen Proプロセッサ
- 容量が 256 GB 以上の SSD タイプのブート ドライブ
- 16 GB 以上の内部デバイス メモリ (RAM)
- モダン スタンバイのサポート
- デバイスがセキュリティで保護されたコア PC の種類
- カーネル DMA 保護をサポート
