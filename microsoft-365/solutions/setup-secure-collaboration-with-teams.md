---
title: Microsoft 365 とセキュリティで保護された共同作業を設定する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-collaboration
- m365solution-securecollab
- m365solution-overview
ms.custom:
- M365solutions
- seo-marvel-jun2020
f1.keywords: NOCSH
description: 機密情報に基づいてデータを保護するために Teams でセキュリティで保護されたコンテンツコラボレーションをセットアップする方法について説明します。
ms.openlocfilehash: 4f2e157025f00660e77ba3377221368e37e45445
ms.sourcegitcommit: 1beaf89d2faa32f11fe1613be2fa2b31c4bc4a91
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "49602075"
---
# <a name="set-up-secure-collaboration-with-microsoft-365"></a>Microsoft 365 とセキュリティで保護された共同作業を設定する

情報を適切な人と簡単に共有できるようにする一方で、過剰な共有が組織の成功にとって重要であることを防ぎます。 これには、機密データをアクセスする必要があるユーザーに対してのみ安全に共有できることが含まれます。 プロジェクトによっては、機密データを組織外のユーザーと共有する場合があります。

このコラボレーションソリューションのガイダンスには、次のような2つのコンポーネントが含まれています。
- 各プロジェクトの適切なレベルの保護を使用して Microsoft Teams を展開する
- プロジェクトごとに適切なセキュリティ設定を使用して外部共有を構成する

![適切な保護を使用して Teams を展開し、適切なセキュリティ設定を使用して外部共有を構成する](..\media\solutions-architecture-center\secure-collaboration-overview.png)

多目的で使いやすいコンテンツコラボレーションツールを使用できない場合、ユーザーはメールでドキュメントを送信して共同作業することがよくあります。 これは、単調でエラーが発生しやすいコラボレーションの方法であり、情報が不適切に共有されるリスクを高めることができます。 ユーザーが情報を共有することが困難すぎる場合は、その情報が管理されていないコンシューマー製品の使用に戻ることができます。 これにより、さらに大きなリスクが生じる可能性があります。

Microsoft 365 では、次のようなさまざまな構成を使用して Teams を展開できます。

- 知的所有権を保護する
- 簡単にコラボレーションを有効にする
- セキュリティと操作性のバランスを確立して、ユーザーの満足度を上げ、シャドウを考慮するリスクを軽減する

ほとんどの組織にはさまざまな情報があり、機密度が異なり、情報が適切に共有されていない場合にはさまざまなビジネスへの影響があります。 特定の情報の機密性に応じて、次のような共有を許可することができます。

- すべてのユーザー (認証されていない)
- 組織内のユーザー
- 組織内の特定のユーザー
- 組織の内部および外部の特定のユーザー

マーケティングパンフレットなどの情報は、組織外での共有を目的としています。 カフェテリアのメニューなどの情報は、外部共有を目的としたものではありませんが、外部で共有されている場合はビジネスへの影響はありません。 これらの種類の情報は、ほとんどまたはまったく保護する必要はありません。

開発中の同じマーケティングパンフレットは、組織内でのみ共有することができます。 この場合は、Teams の既定の共有設定で十分です。

開発中の新しい製品に関する情報は、組織内であっても機密であると見なされる場合があります。 この場合は、より高いレベルの保護が適している場合があります。 たとえば、特定のチームのメンバーに対するこの情報へのアクセスを制限することができます。 プロジェクトによっては、ベンダーやパートナー組織などの組織外のユーザーと共同作業が必要になる場合があります。

組織の成功にとって重要な情報、またはセキュリティやコンプライアンスに関する厳しい要件がある場合は、より高いレベルの保護が必要になることがあります。

![低 (リリースパンフレット) から高 (機密性の高いビジネスデータ) までのリスクスケール](../media/solutions-architecture-center/SecureCollaboration-SensitivityAndBusinessImpactofSharing-fromVisio.png)

上記のすべてのシナリオでは、Microsoft Teams の teams を使用して、情報を格納、共有、および共同作業することができます。 

セキュリティで保護されたグループ作業を構成するには、次の Microsoft 365 の機能と機能を使用します。

| 製品またはコンポーネント | 機能 | ライセンス |
|:-------|:-----|:-------|
| Microsoft Defender for Office 365 | SPO、OneDrive、Teams の安全な添付ファイル。安全なドキュメント。Teams の安全なリンク    | Microsoft 365 E1、E3、E5 |
| SharePoint    | サイトとファイルの共有のポリシー、サイトの共有のアクセス許可、共有リンク、アクセスの要求、サイトのゲスト共有設定 | Microsoft 365 E1、E3、E5 |
| Microsoft Teams   | ゲストアクセス、プライベートチーム、プライベートチャネル | Microsoft 365 E1、E3、E5 |
| Microsoft 365 コンプライアンス  | 秘密度ラベル    | Microsoft 365 E3、E5 |

### <a name="using-teams-for-all-kinds-of-data"></a>すべての種類のデータに Teams を使用する

さまざまな反応を持つ情報へのアクセスを管理するために、 [Teams に対して3つの異なる保護レベル](configure-teams-three-tiers-protection.md)を開発しました。 これらの層のいずれかをカスタマイズして、ニーズやビジネスに適したものにすることができます。 

![Teams の論理的なアーキテクチャ ポスターのサムネイル](../media/solutions-architecture-center/Teams-tiers-of-protection-1.png)


次の表に示すよう *に、これら* の *階層によって、過度**な共有* や情報漏洩を防止するための保護が徐々に増加します。

|-|**ベースライン層**|**機密層**|**非常に機密性の高い層**|
|:--|:-----------|:------------|:-------------------|
|パブリックまたはプライベートチーム|[Either/リンク/埋め込み]|Kirkland|Kirkland|
|認証されていない共有|Blocked|Blocked|Blocked|
|ファイル共有|可|可|チーム所有者のみが共有できます。|
|チームメンバーシップ|すべてのユーザーがパブリックチームに参加できます。<br>チーム所有者の承認は、プライベートチームに参加するために必要です。|参加するには、チーム所有者の承認が必要です。|参加するには、チーム所有者の承認が必要です。|
|ドキュメントの暗号化|||機密ラベルで使用可能|
|ゲスト共有|可|許可またはブロックできる|許可またはブロックできる|
|非管理対象デバイス|制限なし|Web 専用アクセス|Blocked|

これらの層の構成には以下が含まれます。

- Teams でゲストアクセスおよびプライベートチャネルの設定を構成する
- 内部およびゲストの共有、アクセスの要求、および共有リンクについて、チームの関連付けられた SharePoint サイトの設定を構成する
- *機密性* の *高い機密* 層に対して、チームを分類するための機密ラベルを構成し、管理されていないデバイスからゲストの共有とアクセスを制御する
- 非常に *機密性の高い* 層の場合は、機密ラベルを構成して、適用されるドキュメントを暗号化します。

ベースライン層から始め、必要に応じて *機密* および *機密性の高い* 階層を使用する teams を追加して、組織内の情報を保護します。 開始するには、次のリソースを参照してください。

- [ベースライン保護を使用してチームを構成する](configure-teams-baseline-protection.md)
- [機密データに対する保護機能を使用してチームを構成する](configure-teams-sensitive-protection.md)
- [機密データに対する保護機能を使用してチームを構成する](configure-teams-highly-sensitive-protection.md)

組織内でも、共有に対する追加の保護を必要とする非常に機密性の高いプロジェクトがある場合は、チームのメンバーだけがファイルを読むことができるように、独自の機密ラベルを使用してファイルを暗号化するようにチームを構成できます。 詳細について [は、「セキュリティの分離を使用してチームを構成](secure-teams-security-isolation.md) する」をご覧ください。

### <a name="sharing-with-people-outside-your-organization"></a>組織外のユーザーとの共有

[組織外のユーザーとの秘密度の情報を共有](collaborate-with-people-outside-your-organization.md)する必要がある場合があります。 これは、単一のドキュメントを1人のユーザーと共有することから、世界中の大規模なパートナー組織またはフリーランサーを持つ主要なプロジェクトで共同作業を行うことまで多岐に沿っています。 Microsoft 365 では、機密情報を保護するための適切な保護対策を使用して、この範囲の外部共有を簡単に行うことができます。

これらのリソースは、組織外のユーザーと共同作業するための環境のセットアップを開始するのに役立ちます。

- フォルダーの個々のファイルを共有するために[ドキュメントで共同作業](collaborate-on-documents.md)を行います。
- SharePoint サイトのゲストと共同作業するために[サイトで共同作業](collaborate-in-site.md)を行います。
- チーム内のゲストと共同作業を行う[チームとして共同作業](collaborate-as-team.md)を行います。

共有されている情報の機密性に応じて、保護を追加して、過度の共有を防止できます。 次のリソースは、組織に必要な保護を設定するのに役立ちます。

- [認証されていないユーザーとファイルおよびフォルダーを共有するためのベスト プラクティス](best-practices-anonymous-sharing.md)
- [組織外のユーザーと共有する場合、ファイルが偶発的に公開されることを制限する](share-limit-accidental-exposure.md)
- [セキュリティで保護されたゲスト共有環境を作成する](create-secure-guest-sharing-environment.md)

パートナー組織との主要なプロジェクトがある場合は、プロジェクトに対して設定したチームで、Azure の資格管理を使用してその組織からゲストを管理できます。 詳細について [は、「管理されたゲストでの B2B エクストラネットの作成](b2b-extranet.md) 」を参照してください。

## <a name="deploy-the-secure-collaboration-solution"></a>セキュリティで保護されたコラボレーションソリューションを展開する

このソリューションを展開する準備ができたら、次の手順を続行します。
1. [Teams の3つの異なる保護層](configure-teams-three-tiers-protection.md)を構成します。
2. [組織外の人との秘密度の情報を共有](collaborate-with-people-outside-your-organization.md)するための設定を構成します。

## <a name="see-also"></a>関連項目

[Microsoft 365 のセキュリティに関するドキュメント](https://docs.microsoft.com/microsoft-365/security)

[Microsoft 365 コンプライアンスのドキュメント](https://docs.microsoft.com/microsoft-365/compliance)

[Microsoft Teams にようこそ](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
