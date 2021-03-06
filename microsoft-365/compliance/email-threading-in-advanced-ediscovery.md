---
title: メール スレッド (Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: 分析を実行Advanced eDiscovery、電子メール スレッドは電子メールの会話を解析し、各メッセージを異なるカテゴリに分割します。
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: b087bfc84175f80daaf1c0d2f1394584a70757ac
ms.sourcegitcommit: 2160e7cf373f992dd4d11793a59cb8c44f8d587e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "48285563"
---
# <a name="email-threading-in-advanced-ediscovery"></a>メール スレッド (Advanced eDiscovery

しばらくの間続く電子メールの会話を検討してください。 ほとんどの場合、スレッドの最後のメールには、前のすべてのメールの内容が含まれます。最後のメールを確認すると、スレッドで発生した会話の完全なコンテキストが表示されます。 電子メール スレッドは、このような電子メールを識別し、レビュー担当者はコンテキストを失わずに収集されたドキュメントの一部を確認できます。

## <a name="what-does-email-threading-do"></a>電子メールスレッドは何をしますか?

電子メール スレッドは、各電子メールを解析し、個々のメッセージに分解します。各電子メールは、個々のメッセージのチェーンです。 次に、レビュー セット内のすべてのメールを分析して、電子メールに固有のコンテンツが含まれているか、チェーンが完全に別の電子メールに含まれているかどうかを判断します。 最後に、電子メールは次の 4 つのカテゴリに分けられます。

- **包括的**:電子メールの最後のメッセージには固有のコンテンツがあります。そしてこの電子メールには、他の電子メールに含まれていたすべての添付ファイルが含まれています。いわゆる、電子メールの完全なコンテンツが含まれています。

- **包括的なマイナス**:電子メールの最後のメッセージには一意のコンテンツがあります。ただ、この電子メールにはメールに含まれていた添付ファイルの一部がメールに含まれていません。いわゆる、電子メールの完全なコンテンツが含まれていません。

- **包括的コピー**：包括的/包括的マイナスの電子メールの完全なコピー

- **なし**: この電子メールの内容は、包括的/包括的マイナスとしてマークされた少なくとも1つのメールに完全に含まれています。

## <a name="how-is-it-different-from-conversations-in-outlook"></a>会話とどのように違うのOutlook?

一目でわかると、これはユーザーの会話グループに似Outlook。 ただし、いくつかの重要な違いがあります。 2 つの会話にフォークされた電子メールの会話を検討します。たとえば、誰かが会話の最新ではない電子メールに応答した場合、会話の最後の 2 つのメールの両方に一意のコンテンツがあります。

Outlookメールを 1 つの会話にグループ化します。最後の電子メールのみを読み取る場合は、2 番目から最後の電子メールのコンテキストが欠落し、一意のコンテンツも含まれるという意味です。 電子メール スレッドは各メールを個々のコンポーネントに解析して比較しますので、電子メール スレッドは、最後の 2 つのメールの両方を包括的としてマークし、包括的とマークされたメールを読む限り、コンテキストを見逃す必要はありません。
