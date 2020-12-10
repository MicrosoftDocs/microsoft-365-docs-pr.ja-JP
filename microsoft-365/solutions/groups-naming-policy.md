---
title: Microsoft 365 グループの名前付けポリシー
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 6ceca4d3-cad1-4532-9f0f-d469dfbbb552
description: Microsoft 365 グループの名前付けポリシーを作成する方法について説明します。
ms.openlocfilehash: 15fcbace737398c6edd2062e72622e8551ebd222
ms.sourcegitcommit: a0cddd1f888edb940717e434cda2dbe62e5e9475
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2020
ms.locfileid: "49613504"
---
# <a name="microsoft-365-groups-naming-policy"></a>Microsoft 365 グループの名前付けポリシー

グループの名前付けポリシーを使用して、組織内のユーザーによって作成されたグループに一貫した名前付け戦略を適用することができます。 名前付けポリシーにより、お客様とユーザーがグループの機能、メンバーシップ、地域、グループの作成者を特定できるようになります。 名前付けポリシーは、アドレス帳のグループの分類にも役立ちます。 ポリシーを使用して、特定の単語をグループの名前やエイリアスで使われないようにブロックすることができます。

名前付けポリシーは、すべてのグループのワークロードに対して作成されたグループ (Outlook、Microsoft Teams、SharePoint、Planner、Yammer など) に適用されます。 グループ名とグループのエイリアスの両方に適用されます。 名前付けポリシーは、ユーザーによるグループの作成時、または既存のグループのグループ名やエイリアスの編集時に適用されます。

> [!TIP]
> Microsoft 365 グループの名前付けポリシーは、Microsoft 365 グループにのみ適用されます。 Exchange Online で作成された配布グループには適用されません。 配布グループの名前付けポリシーを作成するには、「 [配布グループ名前付けポリシーを作成](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-distribution-groups/create-group-naming-policy)する」を参照してください。

グループの名前付けポリシーは、次の機能で構成されています。

- **プレフィックス/サフィックスの名前付けポリシー**: グループの名前付け規則を定義するには、プレフィックスまたはサフィックスを使用できます (例: "US \_ My Group \_ Engineering")。 プレフィックス/サフィックスは、固定文字列、またはグループを作成しているユーザーに基づいて置換される [Department] などのユーザー属性のいずれかにすることができます。

- ユーザー **設定のブロック** された単語: 組織に固有で、ユーザーが作成したグループでブロックされるブロックされる単語のセットをアップロードできます。 (例: "CEO, Payroll, HR")。

## <a name="licensing-requirements"></a>ライセンスの要件

Microsoft 365 グループの Azure AD 名前付けポリシーを使用するには、1つ以上の Microsoft 365 グループのメンバーである一意のユーザー (ゲストを含む) ごとに、Azure Active Directory Premium P1 ライセンスまたは Azure AD Basic EDU ライセンスを所有している必要がありますが、必ずしも割り当てることはできません。

これは、グループの名前付けポリシーを作成する管理者にも必要になります。

## <a name="prefix-suffix-naming-policy"></a>Prefix-Suffix 名前付けポリシー

プレフィックスとサフィックスは、固定文字列またはユーザー属性のいずれかにすることができます。

### <a name="fixed-strings"></a>固定文字列

短い文字列を使用して、GAL とグループワークロードの左側のナビゲーションでグループを区別するのに役立つ場合があります。 一般的なプレフィックスのサフィックスには、' Grp \_ Name '、' \# name '、' \_ name ' などのキーワードがあります。

### <a name="attributes"></a>属性

属性を使って、[Department] のようにグループを作成したユーザー、および [Country] のように作成された場所を識別するのに役立てることができます。

例:

- Policy = "GRP [GroupName] [Department]"
- User's department = Engineering
- Created group name = "GRP My Group Engineering"

サポートされている Azure Active Directory (Azure AD) 属性は、[部署]、[会社]、[Office]、[StateOrProvince]、[CountryOrRegion]、[Title] です。

- サポートされていないユーザー属性は、[郵便番号] などの固定文字列と見なされます。

- 拡張属性とカスタム属性はサポートされません。

組織のすべてのユーザーに対して、値が設定された属性を使用することをお勧めします。長い値が設定された属性は使用しないでください。

### <a name="things-to-look-out-for"></a>次の項目を参照してください。

- ポリシーを作成するときは、プレフィックスとサフィックスの合計文字数は 53 文字に制限されます。

- プレフィックスとサフィックスには、グループ名とグループのエイリアスでサポートされている特殊文字を含めることができます。 プレフィックスとサフィックスに、グループエイリアスで許可されていない特殊文字が含まれている場合、それらはグループ名にのみ適用されます。 そのため、この場合は、グループ名に適用されているプレフィックスとサフィックスは、グループのエイリアスに適用されているものとは異なります。

  > [!NOTE]
  > グループ名の任意の場所にピリオド (.) またはハイフン (-) を使用できます。ただし、名前の先頭または末尾にある場合は除きます。 グループ名の任意の場所にアンダースコア (_) を使用できます。名前の先頭または末尾を含むこともできます。

- Yammer Office 365 に接続されたグループを使用している場合は、名前付けポリシーで次の文字を使用しないでください。 @、 \# 、 \[ 、、 \] \<, and \> 。 これらの文字が名前付けポリシーに含まれている場合、正規の Yammer ユーザーはグループを作成できません。

> [!Tip]
> - 短い文字列をサフィックスとして使用します。
> - 値が指定された属性を使用します。
> - 創造的なので、名前の長さの合計は264文字までです。
> - 使用制限する組織固有の禁止単語をアップロードします。

## <a name="custom-blocked-words"></a>ユーザー設定のブロックされた単語

ブロックされた単語のリストをコンマ区切りで入力できます。これは、グループの名前とエイリアスでブロックされます。

サブ文字列検索は実行されません。具体的には、エラーを発生させるには、ユーザーが入力した名前とカスタムのブロックされた単語が完全に一致している必要があります。

次 **の点に注目して** ください。

- ブロックする単語は、大文字と小文字を区別します。

- ユーザーがブロックする単語を入力すると、グループ クライアントによって、ブロックされた単語を含むエラー メッセージが表示されます。

- ブロックする単語で使用する文字に制限はありません。

- ブロックされた単語として設定できる単語数の制限は5000です。

## <a name="admin-override"></a>管理者による上書き

一部の管理者は、これらのポリシーから除外され、それらのグループのワークロードおよびエンドポイント全体で、これらのブロックされた単語を使用してグループを作成したり、必要な名前付け規則を使用したりすることができます。 グループの名前付けポリシーの適用から除外される管理者の役割リストは次のとおりです。

- 全体管理者

- パートナー レベル 1 のサポート

- パートナー レベル 2 のサポート

- ユーザー アカウント管理者

- ディレクトリ製作者

## <a name="how-to-set-up-the-naming-policy"></a>名前付けポリシーをセットアップする方法

名前付けポリシーをセットアップするには、次のようにします。

1. [Azure Active Directory](https://aad.portal.azure.com)の [**管理**] で、[**グループ**] をクリックします。
2. [ **設定**] の [ **名前付けポリシー**] をクリックします。
3. [ **グループの名前付けポリシー** ] タブを選択します。
4. [ **現在のポリシー**] で、プレフィックスかサフィックス、あるいはその両方を要求するかどうかを選択し、適切なチェックボックスをオンにします。
5. 各行の **属性** と **文字列** を選択してから、属性または文字列を指定します。
6. 必要なプレフィックスとサフィックスを追加したら、[ **保存**] をクリックします。

![Azure Active Directory のグループの名前付けポリシーの設定のスクリーンショット](../media/groups-naming-policy-azure.png)

## <a name="related-topics"></a>関連項目

[コラボレーションガバナンスの計画のステップバイステップ](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[コラボレーションのガバナンス計画を作成する](collaboration-governance-first.md)

[グループ設定を構成するための Azure Active Directory コマンドレット](https://go.microsoft.com/fwlink/?linkid=868341)
