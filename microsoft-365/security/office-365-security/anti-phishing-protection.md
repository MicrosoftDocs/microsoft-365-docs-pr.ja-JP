---
title: フィッシング対策保護
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 75af74b2-c7ea-4556-a912-8c48e07271d3
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- TopSMBIssues
- seo-marvel-apr2020
description: 管理者は、Exchange Online Protection (EOP) および Microsoft Defender for Office 365 のフィッシング対策保護機能について学ぶことができます。
ms.openlocfilehash: 5b175a252f95c62a40348a78e694628ee58488bd
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "49614993"
---
# <a name="anti-phishing-protection-in-microsoft-365"></a>Microsoft 365 でのフィッシング対策保護

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


*フィッシング* は、正当または信頼された送信者から送られたように見えるメッセージで、機密情報を盗もうとする電子メール攻撃です。 フィッシングには特定のカテゴリがあります。 例:

- **スピアーフィッシング** は、対象の受信者に特化した、優先されるカスタマイズされたコンテンツを使用します (通常は、受信者が攻撃者による偵察後に行います)。

- **Whaling** は、組織内のエグゼクティブまたはその他の高価値のターゲットに対して最大の効果を与えるように指示されます。

- **ビジネスメールの侵害 (BEC)** は、偽造された信頼できる送信者 (金融責任者、顧客、信頼できるパートナーなど) を使用して、顧客に対して支払いの承認、預金の移管、顧客データの開示を行います。

- データを暗号化し、暗号化を解除するために支払いを要求する **ランサムウェア** は、常にフィッシングメッセージで開始します。 フィッシング対策保護は暗号化されたファイルの解読には役立ちませんが、ランサムウェアキャンペーンに関連付けられている最初のフィッシングメッセージを検出するのに役立ちます。 ランサムウェア攻撃からの回復の詳細については、「 [Microsoft 365 のランサムウェアからの回復](recover-from-ransomware.md)」を参照してください。

攻撃の複雑さが増すにつれて、熟練したユーザーが高度なフィッシングメッセージを識別することが困難になります。 幸いなことに、Exchange Online Protection (EOP) と Microsoft Defender for Office 365 の追加機能は役に立つことがあります。

## <a name="anti-phishing-protection-in-eop"></a>EOP のフィッシング対策保護

EOP (つまり、microsoft Defender for Office 365 を使用しない Microsoft 365 組織) には、組織をフィッシング脅威から保護するのに役立つ機能が含まれています。

- **スプーフィング インテリジェンス**: 内部および外部ドメインの送信者からのスプーフィングされたメッセージを確認し、その送信者を許可またはブロックします。 詳細については、「 [Configure スプーフ知能 IN EOP」](learn-about-spoof-intelligence.md)を参照してください。

- **EOP のフィッシング対策ポリシー**: スプーフィングインテリジェンスを有効または無効にしたり、Outlook で認証されていない送信者の識別を有効または無効にしたり、ブロックされた送信者に対するアクションを指定したりします ([迷惑メール] フォルダーまたは検疫に移動)。 詳細については、「 [CONFIGURE EOP」の「フィッシング対策ポリシーを構成する](configure-anti-phishing-policies-eop.md)」を参照してください。

- **暗黙的な電子メール認証**: EOP では、受信電子メールの標準の電子メール認証チェック ([SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md)、 [dkim](use-dkim-to-validate-outbound-email.md)、 [DMARC](use-dmarc-to-validate-email.md)) を使用して、送信者評価、送信者履歴、受信者履歴、動作分析、その他の高度な手法を使用して偽造された送信者を特定できます。 詳細については、「[Microsoft 365 でのメール認証](email-validation-and-authentication.md)」をご覧ください。

## <a name="additional-anti-phishing-protection-in-microsoft-defender-for-office-365"></a>Microsoft Defender for Office 365 のその他のフィッシング対策保護

Microsoft Defender for Office 365 には、追加の高度なフィッシング対策機能が含まれています。

- **Microsoft Defender For Office 365 のフィッシング対策ポリシー**: 新しいカスタムポリシーを作成し、偽装設定 (ユーザーおよびドメインを偽装から保護)、メールボックスインテリジェンス設定、および調整可能な高度なフィッシングしきい値を構成します。 詳細については、「 [Configure フィッシング対策ポリシーを Microsoft Defender の Office 365 に構成する](configure-atp-anti-phishing-policies.md)」を参照してください。 Office 365 の Defender での EOP とフィッシング詐欺対策ポリシーの相違点の詳細については、「 [Microsoft 365 のフィッシング対策ポリシー](set-up-anti-phishing-policies.md)」を参照してください。

- [**キャンペーンビュー**]: コンピューター学習およびその他のヒューリスティックは、サービスと組織全体に対して、組織的なフィッシング攻撃に関係するメッセージを識別して分析します。 詳細については、「 [Microsoft Defender For Office 365](campaigns.md)」の「キャンペーンビュー」を参照してください。

- **アタックシミュレータ**: 管理者は偽のフィッシングメッセージを作成し、それを教育ツールとして内部ユーザーに送信できます。 詳細については、「 [Microsoft Defender For Office 365](attack-simulator.md)」の「アタックシミュレータ」を参照してください。

## <a name="other-anti-phishing-resources"></a>その他のフィッシング対策リソース

- エンドユーザーの場合: [フィッシング対策やその他の形式のオンライン詐欺から保護](https://support.microsoft.com/office/be0de46a-29cd-4c59-aaaf-136cf177d593)します。

- [Microsoft 365 がフィッシングを防ぐために差出人アドレスを検証する方法](how-office-365-validates-the-from-address.md)。
