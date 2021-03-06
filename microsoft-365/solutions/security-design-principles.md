---
title: Microsoft 365 Enterpriseリソース計画 - サイバーセキュリティ アーキテクチャ
description: Microsoft のサイバーセキュリティ アーキテクトである Kozeta Garrett の Microsoft Enterpriseアーキテクチャにおけるセキュリティの課題を克服する方法について説明します。
ms.author: bcarter
author: brendacarter
manager: bcarter
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- M365solutions
ms.custom: seo-marvel-jun2020
f1.keywords: NOCSH
ms.openlocfilehash: 7cd9098766024093a0b9fa2d6e95131bf13d09df
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51052484"
---
# <a name="security-hurdles-you-can-sail-overone-architects-viewpoint"></a>セキュリティ上のハードル :1 人の建築家の視点

この記事では、Microsoft のサイバーセキュリティ アーキテクトである [Kozeta Garrett](https://www.linkedin.com/in/kozeta-garrett-53013a6/)が、企業組織で遭遇するセキュリティ上の最も重要な課題について説明し、これらのハードルを乗り越える方法をお勧めします。

## <a name="about-the-author"></a>筆者について

![Kozeta Garrett 写真](../media/solutions-architecture-center/kozeta-garrett-security.jpg)

クラウド セキュリティ アーキテクトとしての私の役割では、複数の組織と協力して、Microsoft 365 および Azure に移行する顧客向けセキュリティ アーキテクチャの設計と実装、エンタープライズ セキュリティ ソリューションの開発、ビジネスの回復のためのセキュリティ アーキテクチャと文化の変革に焦点を当てた戦略的および技術的なガイダンスを提供しました。 私の経験には、インシデントの検出と対応、マルウェア分析、侵入テスト、IT セキュリティと防御態勢の改善の推奨が含まれます。 最新化の取り組みを含め、ビジネスのイナバーとしてセキュリティにつながる主要な変革に非常に熱心です。

ここ数年、セキュリティ近代化の考え方を採用した組織が、最近の COVID-19 の状況にもかかわらず、安全な方法でリモート操作を継続できる大きな立場にあるのを見て、最も満足しています。 残念ながら、これらの状況は、この即時の必要性に備えなかった一部の顧客に対するウェイクアップの呼び出しにも機能しています。 多くの組織は、このような非常に異常な状況で運用できるよう、急速に近代化し、蓄積された IT セキュリティ負債を廃止し、セキュリティ態勢を一晩で改善する必要があるという状況に気付いてきた。

良いニュースは、組織がセキュリティの態勢を迅速に強化するために、Microsoft がいくつかの優れたリソースを管理しているというニュースです。 これらのリソースに加えて、これらのハードルを乗り越えていけそうとして、お客様と毎日遭遇した最高の課題を共有します。

現在は北バージニア州に住んでいて、ワシントンDCの首都に近いです。 ランニング、サイクリング、ハイキング、水泳など、あらゆる種類の屋外アクティビティとエクササイズが大好きです。 これらに対抗するために、私は料理、グルメ料理、旅行と同じ量を楽しむ。

## <a name="partner-with-the-security-team-from-the-start-of-cloud-adoption"></a>クラウド導入の開始からセキュリティ チームと提携する

まず、組織のチームが最初から調整することがいかに重要かについて十分に強調できないのです。 セキュリティ チームは、クラウドの導入と設計の初期段階で重要なパートナーとして受け入れる必要があります。 つまり、セキュリティ チームをクラウド導入のチャンピオンにし、ビジネスに追加された機能 (セキュリティで保護されたモバイル デバイスからの優れたユーザー エクスペリエンス、完全な機能アプリケーションからの優れたユーザー エクスペリエンス、限られた機能の電子メールや生産性アプリケーションを超えた企業データの価値の作成など) だけでなく、新旧のセキュリティ課題を解決するのに役立つストレージ、AI、コンピューティング分析機能を活用します。 セキュリティ チームは、成功するために、人 (カルチャ)、プロセス (トレーニング)、テクノロジなど、このシフトのすべての側面を管理する必要があります。 また、セキュリティ 運用センター (SOC) の最新化と継続的な改善への投資も意味します。 セキュリティ戦略とビジネス戦略と環境の傾向を一致して、デジタル変換を安全に行います。 これがうまくいった場合、組織は、ビジネス、IT、セキュリティの変更を含む変更に迅速に適応する機能を開発します。

お客様がハードルを乗り越えるのを最も目にしているのは、運用チームと SOC チームの間に本当のパートナーシップがない場合です。 運用チームは、クラウドの導入期限が厳しく、プレッシャーと義務付けも行っていますが、セキュリティ チームは、包括的なセキュリティ戦略を修正して計画するプロセスの早い段階で必ずしも含まれているとは限らない。 これには、さまざまなクラウド コンポーネントとコンポーネントを事前に統合する必要があります。 このパートナーシップの欠如は、特定のコンポーネントのコントロールを実装するためにサイロで機能しているように見えるさまざまなチームにさらにトリクルダウンし、実装、トラブルシューティング、統合の複雑さにつながる。

これらのハードルを乗り越えるお客様は、運用とガバナンスとセキュリティおよびリスク管理チームの間で良好なパートナーシップを結び、ハイブリッド クラウド ワークロードを保護するためのセキュリティ戦略と要件を刷新します。 サイバーセキュリティ ガバナンス、リスク、コンプライアンス要件に従って、データ保護とシステムとサービスの可用性という、究極のセキュリティ目標と結果に焦点を当て、 これらの組織は、運用チームとガバナンス チームと SOC の間で初期段階のパートナーシップを構築します。これはセキュリティ設計アプローチにとって重要であり、投資の価値を最大化します。

## <a name="build-a-modern-identity-based-security-perimeter"></a>最新の (ID ベースの) セキュリティ境界を構築する

次に、ゼロ信頼アーキテクチャアプローチを採用します。 これは、ID ベースの最新のセキュリティ境界の構築から始まります。 セキュリティ アーキテクチャを設計し、オンプレムでもクラウドでも、すべてのアクセス試行が検証されるまで信頼されていないと処理されます。"信頼しない、常に確認する"。 この設計アプローチは、セキュリティと生産性を向上させるだけでなく、ユーザーが任意の種類のデバイスでどこからでも作業することもできます。 高度なクラウド コントロールは、Microsoft 365レベルに基づいて貴重なリソースへのアクセスを制御しながら、ユーザーの ID を保護するのに役立ちます。

推奨される構成については、「Identity and [device access configurations」を参照してください](../security/defender-365-security/microsoft-365-policies-configurations.md)。

## <a name="transition-security-controls-to-the-cloud"></a>セキュリティ制御をクラウドに移行する

多くのセキュリティ チームは、"ネットワーク境界セキュリティ" を維持し、オンプレミスのセキュリティ ツールとコントロールをクラウド ソリューションに "強制" しようとするなど、すべてのオンプレミスの世界で構築された従来のセキュリティベスト プラクティスを引き続き使用しています。 このようなコントロールは、クラウド用に設計されたのではなく、効果が低下し、最新のクラウド機能の導入を妨げている。 ネットワーク境界セキュリティ アプローチで機能するプロセスとツールは、非効率でクラウド機能を妨げ、最新の自動化されたセキュリティ機能を利用できないと証明されています。

このハードルを乗り越えるには、防御戦略をクラウド管理保護、自動調査と修復、自動ペン テスト、Office 365 用 Defender、インシデント分析に移行します。 最新のデバイス管理ソリューションを使用しているお客様は、自動化された管理、標準化されたパッチ適用、ウイルス対策、ポリシー適用、およびアプリケーション保護をすべてのデバイス (スマートフォン、パーソナル コンピューター、ラップトップ、タブレットなど) に実装しています。 これにより、VPN、Microsoft System Center Configuration Manager (SCCM)、Active Directory グループ ポリシーが不要になります。 これにより、条件付きアクセス ポリシーと組み合わせて、ユーザーの操作場所に関係なく、強力な制御と可視性を提供し、リソースへのアクセスを合理化します。

## <a name="strive-for-best-together-security-tools"></a>「ベスト な一緒に」セキュリティ ツールを目指す

もう 1 つのハードルは、お客様がつまずくのを見て、セキュリティ ツールに対して「最高の種類」のアプローチを取る方法です。 新たなセキュリティ ニーズに対応するために、継続的に 「最高の品種」のポイント ソリューションを重ね合合すると、エンタープライズ セキュリティが壊れかねない。 最善の意図を持つ場合でも、ほとんどの環境のツールは、コストが高く複雑になり、統合されません。 これにより、チームが処理できるよりもトリアージするアラートが多く、可視性にギャップが生じる。 新しいツールで SecOps チームを再トレーニングする方法も、常に課題になります。

'simple is better' アプローチはセキュリティでも機能します。 「ベスト オブ ブリーダー」ツールの後に移動する代わりに、既定で一緒に動作するツールを使用して「ベスト 一緒に」戦略を採用することで、このハードルを乗り越える必要があります。 Microsoft のセキュリティ機能は、アプリケーション、ユーザー、クラウドにまたがる統合された脅威保護を使用して組織全体を保護します。 統合により、組織は、攻撃に攻撃者を入れ込み、攻撃を迅速に修復することで、組織の回復力を高め、リスクを軽減できます。

## <a name="balance-security-with-functionality"></a>セキュリティと機能のバランスを取る

長いサイバーセキュリティの背景と経験から来たので、最も安全な構成から始め、組織が運用およびセキュリティのニーズに基づいてセキュリティ構成をリラックスすることを好む傾向があります。 ただし、これは機能が失われ、ユーザー エクスペリエンスが低下する多額の価格で発生する可能性があります。 多くの組織が学んだ通り、セキュリティがユーザーに対して難しすぎる場合は、アンマネージ クラウド サービスの使用を含め、ユーザーを回避する方法を見つけるでしょう。 私が受け入れるのが難しいのと同じで、繊細な機能とセキュリティのバランスを実現する必要があるという認識を得ました。

ユーザーを実現する組織は、自分の仕事を完了するために必要なことを何でも行い、「シャドウ IT の戦い」は戦う価値がないことを認識します。 シャドウ IT と、承認されていない SaaS アプリケーションを自分の仕事に使用する場合、IT 従業員が最大の犯罪者だと認識しています。 彼らは戦略を変えて、(抑制する代わりに) その使用を奨励し、それが作り出す可能性があるリスクの軽減に集中しました。 これらの組織のセキュリティ チームは、すべてがブロックされ、ログに記録され、リバース プロキシまたは VPN を介して送信されるとは主張していません。 むしろ、これらのセキュリティ チームは、貴重で機密性の高いデータが間違った関係者や悪意のあるアプリに公開されるのを防ごう努力を倍増しています。 データの整合性を保護するために機能します。 暗号化、セキュリティで保護された多要素認証、自動リスクとコンプライアンス、Cloud App Security Broker (CASB) 機能など、より高度なクラウド情報保護機能をフルに活用しながら、複数のプラットフォーム間で保護された共有を許可および奨励しています。 影の IT を創造性、生産性、コラボレーションに変え、ビジネスが競争力を維持できます。

## <a name="adopt-a-methodical-approach"></a>方法的なアプローチを採用する

業界に関係なく、さまざまな組織でクラウド セキュリティを実装する上で経験したほとんどの課題は、非常に似ています。 まず、特定の機能と機能に関する素晴らしいドキュメントが豊富に含まれていますが、組織レベルでは、その機能に適用される対象、セキュリティ機能が重複する場所、および機能を統合する方法について、一連の混乱があります。 また、どのセキュリティ機能が事前に構成され、組織が構成を必要としているかについて、一部の不確実性があります。 さらに、SOC チームは残念ながら、組織が急速なクラウド導入とデジタル変革に備える上で必要な完全な露出、トレーニング、または予算配分を持ってはいなかっています。

これらのハードルをクリアするために、Microsoft は、セキュリティ戦略と実装に対して方法的なアプローチを取るのを助けるために設計されたいくつかのリソースを管理しました。

|Resource   |詳細情報  |
|---------|---------|
|[自宅での作業をサポートするセキュリティ チームの主なタスク](../security/top-security-tasks-for-remote-work.md)      | ほとんどが在宅の従業員を突然サポートしている場合、この記事はセキュリティを迅速に強化するのに役立ちます。 これには、ライセンス計画に基づいて推奨される最も推奨されるタスクが含まれます。    |
|[Microsoft 365ビジネス上の意思決定者向けセキュリティ](../security/Microsoft-365-security-for-bdm.md)    | より包括的な計画を立てる時間がある場合、この記事には、攻撃の表面によって優先順位付けされた、Microsoft 365にまたがった推奨事項が含まれています。 また、ライセンスと領域 (ID、脅威保護、監視など) で並べ替えに使用できるスプレッドシートも付属しています。  |
|[Microsoft のセキュリティ アーキテクチャに関する推奨事項](/security/compass/compass)    | セキュリティ アーキテクトの場合は、ID、ネットワーク、セキュリティ操作など、専門分野別に組織されたセキュリティの推奨事項を確認してください。   |
|[Microsoft セキュリティ操作の推奨事項](/security/compass/security-operations-videos-and-decks)|セキュリティ 運用センター (SOC) のセットアップと実行に関する Microsoft の推奨事項について説明します。 |
|[最高情報セキュリティ責任者 (CISO) ワークショップ トレーニング](/security/ciso-workshop/ciso-workshop)   | クラウド セキュリティを初めから利用する場合は、この一連のビデオをお見逃しなく。        |
|[docs.security.com/security](/security/)    | セキュリティ戦略とアーキテクチャに関する Microsoft 全体の技術ガイダンス。        |
| | |

これらのリソースはすべて、開始点として使用され、組織のニーズに合わせて調整するように設計されています。