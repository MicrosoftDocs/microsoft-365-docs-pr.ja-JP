---
title: ランサムウェア攻撃から回復する
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.article: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
description: Microsoft 365 管理者は、ランサムウェア攻撃から回復する方法について学ぶことができます。
ms.openlocfilehash: ad3f044e338abeb56046538bdda8df7b8510be0e
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "49615902"
---
# <a name="recover-from-a-ransomware-attack-in-microsoft-365"></a>Microsoft 365 のランサムウェア攻撃からの回復

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


組織を保護するためにすべての予防措置を講じたとしても、 [ランサムウェア](https://docs.microsoft.com/windows/security/threat-protection/intelligence/ransomware-malware) 攻撃に被害を与えることができます。 ランサムウェアは大規模で、攻撃は非常に巧妙になっています。

この記事の手順では、データを復元し、感染の内部蔓延を停止するための最適な方法を提供します。 開始する前に、次の項目を考慮する必要があります。

- Ransom からファイルへのアクセスが返される保証はありません。 実際には、ransom を支払うことで、ランサムウェアをさらに確保することができます。

  既に支払いを行っているが、攻撃者の解決策を使用せずに回復した場合は、銀行に連絡して、取引をブロックできるかどうかを確認してください。

  また、この記事の後半で説明するように、ランサムウェア攻撃を司法機関、詐欺報告用 web サイト、Microsoft に報告することをお勧めします。

- 攻撃とその影響に迅速に対応することが重要です。 待機時間が長くなるほど、影響を受けるデータを回復できる可能性が低くなります。

## <a name="step-1-verify-your-backups"></a>手順 1: バックアップを確認する

オフラインバックアップを使用している場合は、使用している環境からランサムウェアペイロード (マルウェア) を削除 **した後** で、暗号化されたデータを復元する可能性があります。

バックアップがない場合、またはバックアップがランサムウェアの影響を受けている場合は、この手順を省略できます。

## <a name="step-2-disable-exchange-activesync-and-onedrive-sync"></a>手順 2: Exchange ActiveSync および OneDrive sync を無効にする

ここで重要な点は、ランサムウェアによるデータ暗号化の拡散を停止することです。

ランサムウェアの暗号化の対象として電子メールの疑いがある場合は、メールボックスへのユーザーアクセスを一時的に無効にします。 Exchange ActiveSync は、デバイスと Exchange Online メールボックスの間でデータを同期します。

メールボックスの Exchange ActiveSync を無効にする方法については、「exchange [Online でユーザーの Exchange activesync を無効にする方法](https://support.microsoft.com/help/2795303)」を参照してください。

メールボックスへの他の種類のアクセスを無効にするには、以下を参照してください。

- [メールボックスの MAPI を有効または無効](https://docs.microsoft.com/Exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-mapi)にします。

- [ユーザーの POP3 または IMAP4 アクセスを有効または無効にする](https://docs.microsoft.com/Exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)

OneDrive 同期を一時停止すると、潜在的に感染しているデバイスによるクラウドデータの更新を防ぐことができます。 詳細については、「 [OneDrive で同期を一時停止および再開する方法](https://support.microsoft.com/office/2152bfa4-a2a5-4d3a-ace8-92912fb4421e)」を参照してください。

## <a name="step-3-remove-the-malware-from-the-affected-devices"></a>手順 3: 影響を受けたデバイスからマルウェアを削除する

すべての疑いのあるコンピューターおよびデバイスで、完全に最新のウイルス対策スキャンを実行して、ランサムウェアに関連付けられているペイロードを検出して削除します。

データを同期しているデバイス、またはマップされたネットワークドライブのターゲットをスキャンすることを忘れないでください。

[Microsoft Security Essentials](https://www.microsoft.com/download/details.aspx?id=5201)は、 [Windows Defender](https://www.microsoft.com/windows/comprehensive-security)または (古いクライアントの場合) を使用できます。

また、ランサムウェアまたはマルウェアを削除するための代替手段として、悪意のある [ソフトウェアの削除ツール (MSRT)](https://www.microsoft.com/download/details.aspx?id=9905)もあります。

これらのオプションが機能しない場合は、[マルウェアの検出と削除に関する問題のトラブルシューティング](https://support.microsoft.com/help/4466982)を[Windows Defender オフライン](https://support.microsoft.com/help/17466)で試みることができます。

## <a name="step-4-recover-files-on-a-cleaned-computer-or-device"></a>手順 4: クリーニングされたコンピューターまたはデバイス上のファイルを復元する

前の手順を完了して、使用している環境からランサムウェアのペイロードを削除します (これにより、ランサムウェアによるファイルの暗号化や削除ができなくなります)。 windows 7 では、windows 8.1 10 の [ファイル履歴](https://support.microsoft.com/help/17128) を使用して、ローカルのファイルとフォルダーの回復を試みることができます。

**注**:

- また、一部のランサムウェアはバックアップバージョンを暗号化または削除するので、ファイル履歴またはシステム保護を使用してファイルを復元することはできません。 その場合は、次のセクションで説明するように、ランサムウェアまたは OneDrive の影響を受けない外部ドライブまたはデバイスでバックアップを使用する必要があります。

- フォルダーが OneDrive に同期されていて、最新バージョンの Windows を使用していない場合は、ファイル履歴を使用するといくつかの制限があります。

## <a name="step-5-recover-your-files-in-your-onedrive-for-business"></a>手順 5: OneDrive for Business のファイルを復元する

OneDrive for business のファイルの復元を使用すると、OneDrive 全体を過去30日以内に過去の時点に復元することができます。 詳細については、「 [OneDrive を復元する](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15)」を参照してください。

## <a name="step-6-recover-deleted-email"></a>手順 6: 削除済みメールを復元する

ランサムウェアによってすべての電子メールが削除された場合は、削除済みアイテムを回復できる場合があります。 詳細については、以下を参照してください。

- [ユーザーのメールボックス内の削除済みメッセージを復元する](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-user-mailboxes/recover-deleted-messages)

- [Windows 版 Outlook で削除済みのアイテムを復元する](https://support.microsoft.com/office/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)

## <a name="step-7-re-enable-exchange-activesync-and-onedrive-sync"></a>手順 7: Exchange ActiveSync と OneDrive の同期を再度有効にする

コンピューターとデバイスを消去してデータを回復した後、 [手順 2](#step-2-disable-exchange-activesync-and-onedrive-sync)で以前無効にした Exchange ActiveSync と OneDrive 同期を再度有効にすることができます。

## <a name="step-8-optional-block-onedrive-sync-for-specific-file-extensions"></a>手順 8 (オプション): 特定のファイル拡張子に対して OneDrive 同期をブロックする

回復した後で、OneDrive for Business クライアントがこのランサムウェアの影響を受けたファイルの種類を同期できないようにすることができます。 詳細については、「 [get-spotenantsyncclientrestriction](https://docs.microsoft.com/powershell/module/sharepoint-online/set-spotenantsyncclientrestriction) 」を参照してください。

## <a name="report-the-attack"></a>攻撃を報告する

### <a name="contact-law-enforcement"></a>連絡先の法的執行

地域または連邦法執行機関に連絡する必要があります。 たとえば、米国内にいる場合は、 [FBI ローカルフィールド office](https://www.fbi.gov/contact-us/field)、 [IC3](http://www.ic3.gov/complaint/default.aspx) 、または [Secret サービス](http://www.secretservice.gov/)に問い合わせることができます。

### <a name="submit-a-report-to-your-countrys-scam-reporting-website"></a>国内の詐欺報告 web サイトにレポートを提出する

詐欺の報告 web サイトは、詐欺を防止および回避する方法についての情報を提供します。 また、詐欺の被害を受けた場合に報告するメカニズムも提供します。

- オーストラリア: [Scamwatch](http://www.scamwatch.gov.au/)

- カナダ: [カナダの詐欺防止センター](http://www.antifraudcentre-centreantifraude.ca/)

- フランス: [agence nationale de la sécurité des systèmes d'information](http://www.ssi.gouv.fr/)

- ドイツ: [Bundesamt Für Sicherheit in Der Informationst k](https://www.bsi.bund.de/DE/Home/home_node.html)

- アイルランド: [Garda Síochána](http://www.garda.ie/)

- ニュージーランド: [消費者詐欺詐欺](http://www.consumeraffairs.govt.nz/scams)

- 英国: [アクションの不正行為](http://www.actionfraud.police.uk/)

- 米国: [ガードオンライン](http://www.onguardonline.gov/)

お住まいの国が表示されない場合は、地域または連邦法執行機関にお問い合わせください。

### <a name="submit-email-messages-to-microsoft"></a>Microsoft に電子メールメッセージを送信する

ランサムウェアを含むフィッシングメッセージは、いくつかの方法のいずれかを使用して報告できます。 詳細については、「[メッセージとファイルを Microsoft に報告する](report-junk-email-messages-to-microsoft.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [サム](https://docs.microsoft.com/windows/security/threat-protection/intelligence/ransomware-malware)

- [サムウェア対策応答—支払いを行うかどうかを確認します。](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)

- [Norsk Hydro は、透過可能なランサム攻撃に応答します。](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)

- [OneDrive でのファイルのランサムウェア検出と復元](https://support.microsoft.com/office/0d90ec50-6bfd-40f4-acc7-b8c12c73637f)

- [Microsoft セキュリティインテリジェンスレポート](https://www.microsoft.com/securityinsights/)

- [Office ファイルのマクロを有効または無効にする](https://support.microsoft.com/office/12b036fd-d140-4e74-b45e-16fed1a7e5c6)

- [EOP および Microsoft Defender for Office 365 のセキュリティに関する推奨設定](recommended-settings-for-eop-and-office365-atp.md)

- [アップグレードに値する場合: Windows 10 の次世代セキュリティは、2017でランサムウェアに対する回復性を証明します。](https://www.microsoft.com/security/blog/2018/01/10/a-worthy-upgrade-next-gen-security-on-windows-10-proves-resilient-against-ransomware-outbreaks-in-2017/)

- [Mas なし、Samas このランサムウェアの modus の動作](https://www.microsoft.com/security/blog/2016/03/17/no-mas-samas-whats-in-this-ransomwares-modus-operandi/)

- [Locky マルウェア、幸運による回避](https://www.microsoft.com/security/blog/2016/02/24/locky-malware-lucky-to-avoid-it/)

- [MSRT 2016 年7月: Cerber ランサムウェア](https://www.microsoft.com/security/blog/2016/07/12/msrt-july-2016-cerber-ransomware/)

- [Cer(英語) のような、Cerber ランサムウェアの3つのヘッド](https://www.microsoft.com/security/blog/2016/03/09/the-three-heads-of-the-cerberus-like-cerber-ransomware/)

- [() Da Vinci コードによって影響を受ける Troldesh ランサムウェア](https://www.microsoft.com/security/blog/2016/07/13/troldesh-ransomware-influenced-by-the-da-vinci-code/)
