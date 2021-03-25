---
title: 動作のブロックと格納
description: Microsoft Defender ATP の動作のブロックと格納機能について説明します。
keywords: Microsoft Defender ATP、ブロック モードの EDR、パッシブ モードのブロック
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
localization_priority: Normal
ms.custom:
- next-gen
- edr
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.technology: mde
ms.openlocfilehash: dcad3b7233f2efd444d41c15916eaae195634c8c
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "51166235"
---
# <a name="behavioral-blocking-and-containment"></a>動作のブロックと格納

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Defender for Endpoint を体験してみませんか? [無料試用版にサインアップします。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>概要

今日の脅威の状況は、ファイルレス[](https://docs.microsoft.com/windows/security/threat-protection/intelligence/fileless-threats)マルウェアによって過剰に実行され、土地から離れ、従来のソリューションよりも高速に変化する高度な多態性の脅威、および侵害されたデバイスで敵が見つけたものに適応する人が操作する攻撃です。 従来のセキュリティ ソリューションでは、このような攻撃を止めるには十分ではありません。Defender for Endpoint に含まれる、動作ブロックや格納などの人工知能 (AI) とデバイス学習 (ML) のサポート機能 [が必要です](https://docs.microsoft.com/windows/security)。 

動作のブロックと格納機能は、脅威の実行が開始された場合でも、その動作とプロセス ツリーに基づいて、脅威を特定して停止するのに役立ちます。 次世代の保護、EDR、Defender for Endpoint のコンポーネントと機能は、動作ブロック機能と格納機能で機能します。 

:::image type="content" source="images/mdatp-next-gen-EDR-behavblockcontain.png" alt-text="動作のブロックと格納":::

動作のブロックと格納機能は、Defender for Endpoint の複数のコンポーネントと機能と組み合わせ、攻撃を直ちに停止し、攻撃の進行を防止します。

- [次世代の保護](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10) (Microsoft Defender Antivirus を含む) は、動作を分析して脅威を検出し、実行を開始した脅威を停止できます。

- [エンドポイントの検出と応答](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) (EDR) は、ネットワーク、デバイス、カーネルの動作全体でセキュリティ信号を受信します。 脅威が検出されると、アラートが作成されます。 同じ種類の複数のアラートがインシデントに集約され、セキュリティ運用チームが調査して対応しやすくなります。

- [Defender for Endpoint](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) には、EDR を介して受信されたネットワーク、エンドポイント、カーネルの動作信号に加えて、ID、電子メール、データ、およびアプリにわたる幅広い光学機能があります。 [Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/defender/microsoft-threat-protection)のコンポーネントである Defender for Endpoint は、これらのシグナルを処理して関連付け、検出アラートを発生し、インシデントに関連するアラートを接続します。

これらの機能を使用すると、実行を開始した場合でも、より多くの脅威を防止またはブロックできます。 疑わしい動作が検出されると、脅威が含まれる、アラートが作成され、脅威は追跡で停止されます。 

次の図は、動作ブロックと格納機能によってトリガーされたアラートの例を示しています。

:::image type="content" source="images/blocked-behav-alert.png" alt-text="動作のブロックと格納によるアラートの例":::

## <a name="components-of-behavioral-blocking-and-containment"></a>動作のブロックと格納のコンポーネント

- **クライアント上のポリシー駆動型攻撃 [表面の縮小ルール](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/attack-surface-reduction)** 定義済みの一般的な攻撃動作は、攻撃表面の縮小ルールに従って実行されません。 このような動作を実行しようとすると、Microsoft Defender セキュリティ センターで情報アラート [https://securitycenter.windows.com](https://securitycenter.windows.com) として表示されます。 (攻撃表面の縮小ルールは既定では有効になっていません。Microsoft Defender セキュリティ センターでポリシーを構成します)。

- **[クライアントの動作のブロック](client-behavioral-blocking.md)** エンドポイント上の脅威は機械学習によって検出され、ブロックされ、自動的に修復されます。 (クライアントの動作ブロックは既定で有効になっています)。 

- **[フィードバック ループブロック](feedback-loop-blocking.md)** (高速保護とも呼ばれます) 脅威検出は、行動インテリジェンスを通じて観察されます。 脅威は停止され、他のエンドポイントで実行されません。 (フィードバック ループのブロックは既定で有効になっています)。 

- **[ブロック モードでのエンドポイントの検出と応答 (EDR)](edr-in-block-mode.md)** 侵害後の保護によって観察される悪意のあるアーティファクトや動作はブロックされ、含まれる。 ブロック モードの EDR は、Microsoft Defender Antivirus がプライマリ ウイルス対策ソリューションではない場合でも機能します。 (ブロック モードの EDR は既定では有効になっていません。Microsoft Defender セキュリティ センターで有効にします)。 

Microsoft は引き続き脅威保護の機能を向上させるので、行動のブロックと格納の領域でさらに多くのことを期待してください。 今計画されている計画と展開を確認するには [、Microsoft 365 ロードマップを参照してください](https://www.microsoft.com/microsoft-365/roadmap)。

## <a name="examples-of-behavioral-blocking-and-containment-in-action"></a>動作ブロックとアクション内の格納の例

動作のブロックと封じ込め機能によって、次のような攻撃者の手法がブロックされています。

- LSASS からの資格情報のダンプ
- プロセス間の挿入
- プロセスの空洞化
- ユーザー アカウント制御のバイパス
- ウイルス対策の改ざん (無効にする、マルウェアを除外として追加するなど)
- ペイロードをダウンロードするコマンドとコントロール (C&C) への連絡
- コイン マイニング
- ブート レコードの変更
- ハッシュパス攻撃
- ルート証明書のインストール
- さまざまな脆弱性に対する悪用の試み

以下に、実際の動作ブロックとイントメントの 2 つの実際の例を示します。

### <a name="example-1-credential-theft-attack-against-100-organizations"></a>例 1: 100 組織に対する資格情報の盗難攻撃

「AI[](https://www.microsoft.com/security/blog/2019/10/08/in-hot-pursuit-of-elusive-threats-ai-driven-behavior-based-blocking-stops-attacks-in-their-tracks)による行動ベースのブロックは、追跡中の攻撃を停止する」で説明したように、世界中の 100 の組織に対する資格情報の盗難攻撃は、行動ブロックと格納機能によって停止されました。 ルアー ドキュメントを含むスピア フィッシングメール メッセージが、対象の組織に送信されました。 受信者が添付ファイルを開いた場合、関連するリモート ドキュメントはユーザーのデバイスでコードを実行し、Lokibot マルウェアを読み込む事ができた。これは資格情報を盗み、盗まれたデータを汚し、コマンド アンド コントロール サーバーからのさらなる指示を待った。 

Defender for Endpoint の動作ベースのデバイス学習モデルは、攻撃チェーンの 2 つのポイントで攻撃者の手法をキャッチして停止しました。
- 最初の保護層が悪用の動作を検出しました。 クラウド内のデバイス学習分類子は、脅威を正しく識別し、すぐにクライアント デバイスに攻撃をブロックするように指示しました。
- 2 番目の保護層は、攻撃が最初のレイヤーを越え、プロセスの空きを検出し、そのプロセスを停止し、対応するファイル (Lokibot など) を削除した場合の停止に役立ちます。 

攻撃が検出および停止されている間に、"初期アクセスアラート" などのアラートがトリガーされ、Microsoft Defender セキュリティ センター ( ) に表示されました [https://securitycenter.windows.com](https://securitycenter.windows.com) 。

:::image type="content" source="images/behavblockcontain-initialaccessalert.png" alt-text="Microsoft Defender セキュリティ センターでの初期アクセス通知":::

次の使用例は、クラウド内の動作ベースのデバイス学習モデルが、実行を開始した後でも、攻撃に対する新しい保護層を追加する方法を示しています。

### <a name="example-2-ntlm-relay---juicy-potato-malware-variant"></a>例 2: NTLM リレー - ジューシー ポテト マルウェアバリアント

最近のブログ投稿「ビヘイビアーブロック[](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection)と格納: 光学を保護に変換する」で説明したように、2020 年 1 月に Defender for Endpoint は組織内のデバイスで特権エスカレーション アクティビティを検出しました。 "NTLM リレーを使用した特権エスカレーションの可能性" というアラートがトリガーされました。

:::image type="content" source="images/NTLMalertjuicypotato.png" alt-text="ジューシー ジャガイモ マルウェアに関する NTLM アラート":::

脅威はマルウェアである判明しました。これは、デバイスの特権エスカレーションを取得するために攻撃者によって使用される、ジュート ポテトと呼ばれる悪名高いハッキング ツールの新しい、前に見られないバリアントでした。 

アラートがトリガーされた数分後、ファイルが分析され、悪意のあるものに確認されました。 次の図に示すように、プロセスは停止およびブロックされました。

:::image type="content" source="images/Artifactblockedjuicypotato.png" alt-text="アーティファクトがブロックされている":::

アーティファクトがブロックされた数分後、同じデバイス上で同じファイルの複数のインスタンスがブロックされ、追加の攻撃者や他のマルウェアがデバイスに展開されるのを防ぐ。 

この例では、動作のブロックと封じ込め機能を使用すると、脅威が検出され、格納され、自動的にブロックされます。 

## <a name="next-steps"></a>次の手順

- [Defender for Endpoint の詳細](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)

- [攻撃表面の縮小ルールを構成する](attack-surface-reduction.md)

- [ブロック モードで EDR を有効にする](edr-in-block-mode.md)

- [最近のグローバル脅威アクティビティを確認する](https://www.microsoft.com/wdsi/threats)

- [Microsoft 365 Defender の概要を確認する ](https://docs.microsoft.com/microsoft-365/security/defender/microsoft-threat-protection)