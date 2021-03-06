---
title: Microsoft Viva Topics のセキュリティとプライバシー
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: nkokoye, cjtan
audience: admin
ms.topic: article
ms.service: o365-administration
search.appverid: MET150
localization_priority: Normal
description: Microsoft Viva Topics のセキュリティとプライバシーを計画する方法について説明します。
ms.openlocfilehash: b8c82b1914df739ea9086a4ce1585733a7b6d854
ms.sourcegitcommit: be929f79751c0c52dfa6bd98a854432a0c63faf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2021
ms.locfileid: "52925493"
---
# <a name="microsoft-viva-topics-security-and-privacy"></a>Microsoft Viva Topics のセキュリティとプライバシー

トピックでは、Microsoft 365 の既存のコンテンツ セキュリティ機能と管理コントロールを使用して、組織内のユーザーに表示される AI 生成コンテンツを制御します。 これは、特定のユーザーがトピックMicrosoft 365表示できる内容を決定するセキュリティ設定 (サイト、ファイル、およびフォルダーへのアクセス許可) と Topics 管理設定の組み合わせです。

トピックを設定しても、組織内のコンテンツに対する既存のアクセス制御は一切変更されません。 ユーザーには、そのユーザーが既にアクセス権を持っているコンテンツのみが表示されます。

この記事では、セキュリティの観点からトピックがどのように機能し、ナレッジ管理者とナレッジ マネージャーがトピックの表示を制御する必要があるオプションについて説明します。 トピックの計画の一環として、この [記事をお読みください](plan-topic-experiences.md)。

この記事を読む前に、[トピック](topic-experiences-overview.md)とは[](topic-center-overview.md)何か、トピック センター [](manage-topics.md) 、トピック センターのトピックを操作する方法について理解している必要があります。

## <a name="what-users-can-see-in-topics"></a>トピックでユーザーに表示できる内容

トピックを表示するには、次の項目を使用する必要があります。

- Viva Topics ライセンスを持つ
- トピック ビューアー [、投稿者](topic-experiences-knowledge-rules.md#change-who-can-see-topics-in-your-organization)、または [ナレッジ マネージャーになる](topic-experiences-user-permissions.md)

これら 2 つの機能により、ユーザーはトピック センターにアクセスし、ハイライトとトピック カードを表示できます。

トピック投稿者には、 [トピックの作成](topic-experiences-user-permissions.md) と編集のアクセス許可が追加され、ナレッジ マネージャーはトピックを確認または削除できます。

トピックが最初に検出された場合、ナレッジ マネージャーはトピック センターでトピックを表示できます。 トピックの完成度と関連性に応じて、トピック 閲覧者はトピック カードに表示されるトピックを表示する場合と表示されない場合があります。

トピックには、AI によって生成された情報と、トピック投稿者またはナレッジ マネージャーによって追加または編集された情報を含めできます。

- AI によって追加されたトピックの情報は、ソース コンテンツにアクセスできるユーザーにしか表示されません。
- トピック投稿者またはナレッジ マネージャーによって手動で追加または編集されたテキストは、トピックを表示できるすべてのユーザーに表示されます。

トピック ビューアーと投稿者は、トピック センターで確認済みトピックと発行済みトピックの一覧を表示できますが、特定のユーザーに表示されるトピックの詳細は、ソース 資料に対するアクセス許可と、トピックが手動で編集されたかどうかによって異なります。

次の表は、ユーザー (トピック 閲覧者、投稿者、ナレッジ マネージャー) が、アクセス許可に基づいて特定のトピックで表示できる内容を示しています。

|トピック項目|ユーザーに表示される内容|
|:---------|:------------------|
|トピック名|ユーザーはトピック センターでトピックのトピック名を確認できます。 一部のトピックは、ユーザーがソース コンテンツに対するアクセス許可を持たなかったり、ユーザーとの関連性が低い場合に表示されない場合があります。|
|トピックの説明|AI で生成された説明は、ソース コンテンツに対するアクセス許可を持つユーザーにのみ表示されます。 手動で入力または編集された説明は、すべてのユーザーに表示されます。|
|連絡先|ピン留めされた連絡先はすべてのユーザーに表示されます。 提案された連絡先は、ソース コンテンツに対するアクセス許可を持つユーザーにのみ表示されます。|
|ファイル|ファイルは、ソース コンテンツに対するアクセス許可を持つユーザーにのみ表示されます。|
|ページ|ページは、ソース コンテンツに対するアクセス許可を持つユーザーにのみ表示されます。|
|サイト|サイトは、ソース コンテンツに対するアクセス許可を持つユーザーにのみ表示されます。|

## <a name="users-personal-and-private-data"></a>ユーザーの個人データと個人データ

Viva Topics は、指定したサイトSharePointトピックのみを検出します。 個人用メールやメールなどのユーザーの個人用OneDriveは含まれません。

## <a name="best-practices"></a>ベスト プラクティス

トピックでは、コンテンツに対する既存のアクセス許可に基づいてユーザーに情報を提示します。 Microsoft 365は、機密性の高いコンテンツが適切なユーザーに制限されるさまざまな方法を提供します。 標準的なチームまたはサイトのアクセス許可を超えて、機密ラベルまたは[](../compliance/dlp-learn-about-dlp.md)データ損失防止を使用して、コンテンツへの[](/azure/active-directory/governance/access-reviews-overview)アクセスを制限し、ユーザーによる機密情報へのアクセスを定期的に確認できます。 [](../compliance/sensitivity-labels.md)

これらのツールを使用して、コンテンツのアクセス許可が組織内で適切に設定されるのを確認することをお勧めします。 その後、トピック エクスペリエンスにより、有用で適切な情報をユーザーに提供することができます。

トピック エクスペリエンスから完全に除外するトピックがある場合は、次の方法も実行できます。

- [トピック検出からSharePointサイトを除外します](topic-experiences-discovery.md#select-sharepoint-topic-sources)。 これらのサイトのコンテンツは、トピックのエクスペリエンスに表示されなくなります。

- [トピックを名前で除外します](topic-experiences-discovery.md#exclude-topics-by-name)。 明示的に除外されたトピックは、トピックのエクスペリエンスに表示されなくなります。

- ナレッジ マネージャーにトピック センターのトピックを削除します。

さらに、次のベスト プラクティスをお勧めします。

- 組織の異なる領域からナレッジ マネージャーを募集します。 さまざまな専門知識を持つナレッジ マネージャーと、AI が使用する基になるコンテンツへのアクセスを持つことは、ユーザーにとって最も有用な知識をキュレートし、見つかった場合に機密情報を削除するのに役立ちます。

- 変更を要求するワークフローを設定します。 ナレッジ マネージャーまたはチームまたはサイトの所有者は、新しいプロジェクトが組織内で開始される場合や、不適切なアクセス許可設定を持つコンテンツが見つかった場合に、トピックやサイトの除外を要求できるプロセスを持っている必要があります。

- トピックの説明を作成する際は、対象ユーザーと情報の秘密度に注意します。 これらの説明は、トピックのソース コンテンツに対するアクセス許可を持たないユーザーに表示されるおそれがあります。

個々のトピック ページに対するアクセス許可を変更して、特定のユーザー グループにアクセスを絞り込むこともできますが、必要になる管理作業が多いため、この方法はお勧めできません。

## <a name="see-also"></a>関連項目

[3 層の保護を使って Teams を構成する](../solutions/configure-teams-three-tiers-protection.md)

[トピック エクスペリエンスの計画](plan-topic-experiences.md)

[トピック エクスペリエンスを設定する](set-up-topic-experiences.md)
