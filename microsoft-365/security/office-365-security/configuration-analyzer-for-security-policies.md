---
title: セキュリティポリシーの構成アナライザー
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: 管理者は、構成アナライザーを使用して、標準保護と厳格な保護の事前設定セキュリティポリシーの下にあるセキュリティポリシーを検索して修正する方法を学習できます。
ms.openlocfilehash: 5a57e16dcac6afee910ce546d3a40c2c9c669f2d
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "49616154"
---
# <a name="configuration-analyzer-for-protection-policies-in-eop-and-microsoft-defender-for-office-365"></a>EOP および Microsoft Defender for Office 365 の保護ポリシーの構成アナライザー

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


> [!NOTE]
> このトピックで説明する機能はプレビュー段階にあり、組織によっては使用できず、変更される可能性があります。 リリーススケジュールの詳細については、 [Microsoft 365 ロードマップ](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=config%2Canalyzer)をご覧ください。

セキュリティ & コンプライアンスセンターの構成アナライザーでは、設定が [既定のセキュリティポリシー](preset-security-policies.md)の標準保護と厳密な保護プロファイル設定より下にあるセキュリティポリシーを検索して修正するための一元的な場所が提供されます。

次の種類のポリシーが、構成アナライザーによって分析されます。

- **Exchange Online Protection (EOP) ポリシー**: これには、exchange online メールボックスを使用する Microsoft 365 組織と、exchange online メールボックスを持たないスタンドアロン EOP 組織が含まれます。

  - [スパム対策ポリシー](configure-your-spam-filter-policies.md)。
  - [マルウェア対策ポリシー](configure-anti-malware-policies.md)。
  - [EOP フィッシング対策ポリシー](set-up-anti-phishing-policies.md#spoof-settings)。

- **Microsoft Defender For office 365 ポリシー**: これには、office 365 アドオンサブスクリプションの Microsoft 365 E5 または Defender を使用する組織が含まれます。

  - Microsoft Defender for Office 365 のフィッシング対策ポリシーは次のとおりです。

    - EOP のフィッシング対策ポリシーで使用可能なものと同じ [スプーフィング設定](set-up-anti-phishing-policies.md#spoof-settings) 。
    - [偽装設定](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [高度なフィッシングしきい値](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)

  - 「[安全なリンク」ポリシー](set-up-atp-safe-links-policies.md)。

  - [安全な添付ファイルのポリシー](set-up-atp-safe-attachments-policies.md)。

ベースラインとして使用される **標準** および **厳密** なポリシー設定値については、「 [EOP の推奨設定」と「office 365 セキュリティのための Microsoft Defender](recommended-settings-for-eop-and-office365-atp.md)」を参照してください。

## <a name="what-do-you-need-to-know-before-you-begin"></a>はじめに把握しておくべき情報

- <https://protection.office.com/> でセキュリティ/コンプライアンス センターを開きます。 [ **構成アナライザー** ] ページに直接移動するには、を使用 <https://protection.office.com/configurationAnalyzer> します。

- Exchange Online PowerShell へ接続するには、「[Exchange Online PowerShell に接続する](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)」を参照してください。

- この記事の手順を実行する前に、セキュリティ & コンプライアンスセンターでアクセス許可を割り当てる必要があります。
  - 構成アナライザーを使用 **して** セキュリティポリシーを更新するには、 **組織の管理** 役割グループまたは **セキュリティ管理者** 役割グループのメンバーである必要があります。
  - 構成アナライザーへの読み取り専用アクセスでは、 **グローバル閲覧** 者または **セキュリティリーダー** の役割グループのメンバーである必要があります。

  詳細については、「[セキュリティ/コンプライアンス センターのアクセス許可](permissions-in-the-security-and-compliance-center.md)」を参照してください。

  **注**:

  - Microsoft 365 管理センターで、対応する Azure Active Directory の役割にユーザーを追加すると、ユーザーには、セキュリティ/コンプライアンス センター の必要なアクセス許可 _および_ Microsoft 365 のその他の機能に必要なアクセス許可が付与されます。 詳細については、「[管理者の役割について](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles)」を参照してください。
  - [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups) の **閲覧専用の組織管理** の役割グループが この機能への読み取り専用アクセス権も付与します。

## <a name="use-the-configuration-analyzer-in-the-security--compliance-center"></a>セキュリティ & コンプライアンスセンターで構成アナライザーを使用する

[セキュリティ & コンプライアンスセンター] で、[ **脅威管理** \> **ポリシー** \> **構成アナライザー**] に移動します。

![[脅威管理ポリシー] ページの [構成アナライザー] ウィジェット \>](../../media/configuration-analyzer-widget.png)

構成アナライザーには、次の2つの主要なタブがあります。

- **設定と推奨事項**: Standard または Strict を選択し、それらの設定を既存のセキュリティポリシーと比較します。 結果では、設定の値を調整して、Standard または Strict と同じレベルにすることができます。

- **構成誤差の分析と履歴**: このビューを使用すると、時間の経過とともにポリシーの変更を追跡できます。

### <a name="setting-and-recommendations-tab-in-the-configuration-analyzer"></a>構成アナライザーの [設定] タブと [おすすめ候補] タブ

既定では、タブは標準の保護プロファイルと比較して開きます。 厳密保護プロファイルの比較に切り替えるには、[厳密な **推奨事項の表示**] をクリックします。 元に戻すには、[ **標準的な推奨事項を表示** する] を選択します。

![構成アナライザーの [設定と推奨事項] ビュー](../../media/configuration-analyzer-settings-and-recommendations-view.png)

既定では、[ **ポリシーグループ] と [設定名** ] 列には、さまざまな種類のセキュリティポリシーと、改善が必要な設定 (存在する場合) の数が表示されます。 ポリシーの種類は次のとおりです。

- **スパム対策**
- **フィッシング対策**
- **マルウェア対策**
- **ATP の安全な添付ファイル** (サブスクリプションに Microsoft Defender for Office 365 が含まれている場合)
- **ATP の安全なリンク** (サブスクリプションに Microsoft Defender for Office 365 が含まれている場合)

既定のビューでは、すべてが折りたたまれています。 各ポリシーの横に、ポリシーからの比較結果 (変更可能) と、標準または厳密な保護プロファイルの対応するポリシーの設定 (変更できない) の概要が表示されます。 比較している保護プロファイルについて、次の情報が表示されます。

- **緑**: すべての既存ポリシーのすべての設定は、少なくとも保護プロファイルと同じセキュリティで保護されています。
- **オレンジ**: 既存のポリシーの設定の一部は、保護プロファイルほど安全ではありません。
- **赤**: 既存のポリシーの設定の多くは、保護プロファイルほど安全ではありません。 これは、多くのポリシーの設定のいくつか、または1つのポリシーの多くの設定の場合があります。

好ましい比較には、次のテキストが表示されます。 **すべての設定** は \<**Standard** or **Strict**\> **推奨事項** に従います。 そうしないと、変更する推奨設定の数が表示されます。

[ **ポリシーグループ]/[設定名**] を展開すると、アテンションを必要とする特定の各ポリシーのすべてのポリシーと関連付けられた設定が表示されます。 または、特定の種類のポリシー ( **スパム対策** など) を拡張して、注意が必要な種類のポリシーの設定のみを表示することもできます。

比較に改善に関する推奨策 (緑色) がない場合は、ポリシーを拡張しても何も示されません。 改善に関していくつかの推奨事項 (黄色または赤) がある場合は、注意を要する設定が表示され、対応する情報が次の列に表示されます。

- 注意が必要な設定の名前。 たとえば、前のスクリーンショットでは、スパム対策ポリシーの **バルクメールのしきい値** です。

- **Policy**: 設定を含む影響を受けるポリシーの名前。

- **適用** 対象: 影響を受けたポリシーが適用されるユーザーの数。

- **現在の構成**: 設定の現在の値。

- **最終更新** 日: ポリシーが最後に変更された日付。

- **推奨事項**: 標準または厳密な保護プロファイルの設定値。 ポリシーの設定の値を、保護プロファイルの推奨値と一致するように変更するには、[ **採用**] をクリックします。 変更に成功すると、「 **推奨事項**」というメッセージが表示されます。 [ **更新** ] をクリックして、推奨数の削減、および結果からの特定の設定/ポリシー行の削除を確認します。

### <a name="configuration-drift-analysis-and-history-tab-in-the-configuration-analyzer"></a>構成アナライザーの [構成誤差の分析と履歴] タブ

このタブでは、カスタムセキュリティポリシーに加えた変更を追跡できます。 既定では、次の情報が表示されます。

- **最終更新日時**
- **更新者**
- **設定名**
- **ポリシー**
- **型**

結果をフィルター処理するには、**[フィルター]** をクリックします。 表示される [ **フィルター** ] ポップアップでは、次のフィルターから選択できます。

- **開始** 時刻と **終了時刻** (date)
- **標準保護** または **厳密な保護**

結果を .csv ファイルにエクスポートするには、[ **エクスポート**] をクリックします。

![構成アナライザーの構成誤差分析と履歴ビュー](../../media/configuration-analyzer-configuration-drift-analysis-view.png)
