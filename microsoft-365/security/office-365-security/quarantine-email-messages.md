---
title: 検疫済み電子メール メッセージ
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: overview
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 4c234874-015e-4768-8495-98fcccfc639b
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: 管理者は、潜在的に危険なメッセージや望ましくないメッセージを保持する Exchange Online Protection (EOP) の検疫について学習できます。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b2a11f5f9e1e730a3b0cc09625ec8e8cb592d869
ms.sourcegitcommit: 967f64dfa1a05f31179c8316b96bfb7758a5d990
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2021
ms.locfileid: "52333808"
---
# <a name="quarantined-email-messages-in-eop"></a>EOP で検疫された電子メール メッセージ

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**適用対象**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 プラン 1 およびプラン 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online メールボックスのない Exchange Online またはスタンドアロンの Exchange Online Protection (EOP) 組織のメールボックスを持つ Microsoft 365 組織では、潜在的に危険なメッセージや望ましくないメッセージを保持するために検疫を利用できます。

マルウェア対策ポリシーは、添付ファイルにマルウェアが含まれていると検出された場合、メッセージを自動的に検疫します。 詳細については [、「EOP でマルウェア対策ポリシーを構成する」を参照してください](configure-anti-malware-policies.md)。

既定では、スパム対策はフィッシング メッセージを検疫し、スパムメッセージとバルク メール メッセージをユーザーの迷惑メール フォルダーに配信します。 ただし、スパム対策ポリシーを作成およびカスタマイズして、スパムメッセージとバルクメール メッセージを検疫することもできます。 詳細については、「[EOP でのスパム対策ポリシーの構成](configure-your-spam-filter-policies.md)」を参照してください。

ユーザーと管理者の両方が検疫済みメッセージを処理できます。

- 管理者は、すべてのユーザーのすべての種類の検疫済みメッセージを処理できます。 マルウェア、高信頼フィッシング、またはメール フロー ルール (トランスポート ルールとも呼ばれる) の結果として検疫されたメッセージは、管理者だけが処理できます。 詳細については、「[EOP の管理者として検疫済みのメッセージやファイルを管理する](manage-quarantined-messages-and-files.md)」を参照してください。

- ユーザーは、メッセージがスパム、バルク メール、または (2020 年 4 月現在) フィッシングとして検疫された場合、受信者である検疫済みメッセージを操作できます。 詳細については、「EOP で検疫済みメッセージをユーザーとして検索して解放する [」を参照してください](find-and-release-quarantined-messages-as-a-user.md)。

  ユーザーが検疫済みフィッシング メッセージを管理しきれなくするために、管理者はスパム対策ポリシーのフィッシングメール フィルターの評決に対して別のアクションを構成できます。 詳細については、「[EOP でのスパム対策ポリシーの構成](configure-your-spam-filter-policies.md)」を参照してください。

- 管理者とユーザーは、検疫中に誤検知を Microsoft に報告できます。

検疫の詳細については、「検疫に関するよく寄せられる質問 [」を参照してください](quarantine-faq.yml)。
