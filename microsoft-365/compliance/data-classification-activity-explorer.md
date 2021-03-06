---
title: アクティビティ エクスプローラーの使用を開始する
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: アクティビティ エクスプローラーでは、ラベル付きコンテンツを取り扱うユーザーの操作の確認およびフィルター処理を行い、データ分類機能の機能性を完全なものにします。
ms.openlocfilehash: 414ef4e5d9f6472180a5eaef391d3eba33463b02
ms.sourcegitcommit: 05f40904f8278f53643efa76a907968b5c662d9a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2021
ms.locfileid: "52114009"
---
# <a name="get-started-with-activity-explorer"></a>アクティビティ エクスプローラーの使用を開始する

データ[分類の概要と](data-classification-overview.md)[コンテンツ エクスプローラーの](data-classification-content-explorer.md)タブを使用すると、どのコンテンツが検出され、ラベル付けされ、そのコンテンツがどこに表示されるのかを確認できます。 アクティビティ エクスプローラーでは、ラベル付きコンテンツに対して実行される内容を監視できるようにすることで、こうした一連の機能性を完全なものにします。 アクティビティ エクスプローラーは、ラベル付きコンテンツのアクティビティの履歴ビューを提供します。 アクティビティ情報は、統合監査ログMicrosoft 365収集され、アクティビティ エクスプローラー UI で変換され、使用可能になります。 

![アクティビティ エクスプローラーのプレースホルダー スクリーンショットの全体像](../media/data-classification-activity-explorer-1.png)

使用可能なフィルターは 30 種類以上あり、以下がその一例です。

- 日付の範囲
- アクティビティの種類
- 場所
- ユーザー
- 機密ラベル
- 保持ラベル
- ファイル パス
- DLP ポリシー



## <a name="prerequisites"></a>前提条件

データ分類にアクセスして使用するすべてのアカウントには、これらのいずれかのサブスクリプションのライセンスが割り当てられている必要があります。

- Microsoft 365 (E5)
- Office 365 (E5)
- 高度なコンプライアンス (E5) アドオン
- 高度な脅威インテリジェンス (E5) アドオン
- Microsoft 365 E5/A5 情報保護およびガバナンス
- Microsoft 365 E5/A5 コンプライアンス

### <a name="permissions"></a>アクセス許可

 [アクティビティ エクスプローラー] タブにアクセスするには、アカウントにこれらの役割グループのメンバーシップを明示的に割り当てるか、役割を明示的に付与する必要があります。

<!--
> [!IMPORTANT]
> Access to Activity explorer via the Security reader or Device Management role groups or other has been removed-->

**Microsoft 365 の役割グループ**

- 全体管理者
- コンプライアンス管理者
- セキュリティ管理者
- コンプライアンス データ管理者

**Microsoft 365ロール**

- コンプライアンス管理者
- セキュリティ管理者

## <a name="activity-types"></a>アクティビティの種類

アクティビティ エクスプローラーは、複数のアクティビティ ソースの監査ログからアクティビティ情報を収集します。 どのラベル付けアクティビティがアクティビティ エクスプローラーに表示されるかの詳細については、「アクティビティ エクスプローラーで利用可能なイベントのラベル付け [」を参照してください](data-classification-activity-explorer-available-events.md)。

 Office ネイティブ アプリケーション、Azure Information Protection アドイン、SharePoint Online、Exchange Online (感度ラベルのみ)、および OneDrive からの感度ラベル アクティビティと保持ラベル付けアクティビティ。 次に例を示します。

- ラベルの適用
- ラベルの変更 (アップグレード、ダウングレード、または削除)
- 自動ラベル付けのシミュレーション
- ファイルの読み取り 

**Azure Information Protection (AIP) スキャナーと AIP クライアント**

- 適用される保護
- 保護の変更
- 保護が削除されました
- 検出されたファイル 

また、アクティビティ エクスプローラーは、Exchange Online、SharePoint Online、OneDrive、Teams チャットとチャネル (プレビュー)、オンプレミスの SharePoint フォルダーとライブラリ、オンプレミスのファイル共有、およびエンドポイント データ損失防止 **(DLP)** を介して Windows 10 デバイスからのイベントに一致するイベントを収集します。 デバイスからのイベントの例Windows 10ファイルです。

- 削除
- creations
- クリップボードにコピー
- 更新日時
- read
- 印刷済み
- 名前の変更
- ネットワーク共有にコピーされる
- 許可されていないアプリによってアクセスされる 

機密性の高いラベル付きコンテンツで実行されるアクションを理解する価値は、データ損失防止など、既に設定したコントロールが有効か、有効[](dlp-learn-about-dlp.md)ではないかを確認することです。 そうでない場合、つまり、多数の `highly confidential` でラベル付けされたアイテムおよび `general` にダウングレードされたアイテムなどの予想しない何かが検出された場合は、各種ポリシーを管理して、望ましくない動作を制限するための新しい操作を行うことができます。

> [!NOTE]
> アクティビティ エクスプローラーは現在、Exchange Online の保持アクティビティを監視していません。

## <a name="see-also"></a>関連項目

- [秘密度ラベルの詳細](sensitivity-labels.md)
- [アイテム保持ポリシーと保持ラベルの詳細](retention.md)
- [機密情報の種類に関する詳細情報](sensitive-information-type-learn-about.md)
- [データ分類について](data-classification-overview.md)
