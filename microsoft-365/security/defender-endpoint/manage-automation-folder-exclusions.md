---
title: 自動化フォルダーの除外を管理する
description: 自動化フォルダーの除外を追加して、自動調査から除外されるファイルを制御します。
keywords: 管理, 自動化, 除外, ブロック, クリーン, 悪意のある
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 05c103cba051c7d5e7f45e5dd3feb288013ee367
ms.sourcegitcommit: 718759c7146062841f7eb4a0a9a8bdddce0139b0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2021
ms.locfileid: "53454819"
---
# <a name="manage-automation-folder-exclusions"></a>自動化フォルダーの除外を管理する 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Defender for Endpoint を体験してみませんか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-automationexclusionfolder-abovefoldlink)

オートメーション フォルダーの除外を使用すると、自動調査がスキップするフォルダーを指定できます。 

スキップするフォルダーに関する次の属性を制御できます。
- Folders 
- ファイルの拡張機能
- ファイル名


**フォルダー**<br>
スキップするフォルダーとそのサブフォルダーを指定できます。 


>[!NOTE]
>現時点では、ディレクトリ内のファイルを除外する方法としてワイルドカードを使用する方法はまだサポートされていません。 


**拡張機能**<br>
特定のディレクトリで除外する拡張機能を指定できます。 拡張機能は、攻撃者が除外フォルダーを使用して悪用を隠すのを防ぐ方法です。 拡張機能は、無視するファイルを明示的に定義します。 

**ファイル名**<br>
特定のディレクトリで除外するファイル名を指定できます。 名前は、攻撃者が除外されたフォルダーを使用して悪用を隠すのを防ぐ方法です。 名前は、無視するファイルを明示的に定義します。 



## <a name="add-an-automation-folder-exclusion"></a>オートメーション フォルダーの除外を追加する
1. ナビゲーション ウィンドウで、[エンドポイント **ルールの設定**  >  **除外**]  >    >  **を選択します**。  

2. [新 **しいフォルダーの除外] をクリックします**。  

3. フォルダーの詳細を入力します。

    - Folder
    - 拡張機能
    - ファイル名
    - 説明

4. **[保存]** をクリックします。

>[!NOTE]
> 除外されたファイルを収集または調べる Live Response コマンドは、"ファイルが除外されました" というエラーで失敗します。 さらに、自動調査では除外されたアイテムは無視されます。

## <a name="edit-an-automation-folder-exclusion"></a>オートメーション フォルダーの除外を編集する 
1. ナビゲーション ウィンドウで、[エンドポイント **ルールの設定**  >  **除外**]  >    >  **を選択します**。 

2. フォルダーの **除外で** [編集] をクリックします。  

3. ルールの詳細を更新し、[保存] を **クリックします**。

## <a name="remove-an-automation-folder-exclusion"></a>オートメーション フォルダーの除外を削除する 
1. ナビゲーション ウィンドウで、[エンドポイント **ルールの設定**  >  **除外**]  >    >  **を選択します**。  
2. [除外 **の削除] をクリックします**。 


## <a name="related-topics"></a>関連項目
- [許可/ブロックされたリストの自動化を管理する](manage-indicators.md)
- [自動化ファイルのアップロードを管理する](manage-automation-file-uploads.md)
