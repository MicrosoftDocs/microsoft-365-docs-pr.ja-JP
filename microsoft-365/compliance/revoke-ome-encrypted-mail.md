---
title: 高度なメッセージ暗号化によって暗号化された電子メールを取り消す
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.date: 06/11/2020
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: 管理者として、およびメッセージ送信者として、ユーザーが暗号化された特定の電子メールを取り消Office 365 Advanced Message Encryption。
ms.openlocfilehash: 340a9e73dba50e28223ee561db749a089c649df6
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51051719"
---
# <a name="revoke-email-encrypted-by-advanced-message-encryption"></a>高度なメッセージ暗号化によって暗号化された電子メールを取り消す

電子メールの失効は、電子メールの一部Office 365 Advanced Message Encryption。 Office 365 Advanced Message Encryptionは[、Microsoft 365 Enterprise E5、Office 365](https://www.microsoft.com/microsoft-365/enterprise/home)E5、Microsoft 365 E5 (非営利スタッフ価格)、Office 365 Enterprise E5 (非営利スタッフ価格)、および Office 365 Education A5 に含まれています。 組織に Office 365 Advanced Message Encryption を含めないサブスクリプションがある場合は、Microsoft 365 E3、Microsoft 365 E3 (非営利スタッフ価格) の Microsoft 365 E5 Compliance SKU アドオン、または Microsoft 365 E3、Microsoft 365 E3 (非営利スタッフ価格)、または Office 365 SKU の Office 365 Advanced Compliance SKU アドオンを使用して購入できます。

この記事は、この記事に関する一連の[記事の一](ome.md)部Office 365 Message Encryption。

Office 365 Advanced Message Encryption を使用してメッセージが暗号化され、Microsoft 365 管理者である場合、またはメッセージの送信者である場合は、特定の条件下でメッセージを取り消します。 管理者は PowerShell を使用してメッセージを取り消します。 送信者として、Web 上のユーザーから直接送信したOutlook取り消します。 この記事では、失効が可能な状況と取り消し方法について説明します。
  
## <a name="encrypted-emails-that-you-can-revoke"></a>取り消し可能な暗号化されたメール

受信者がリンクベースのブランド化された暗号化メールを受信した場合、管理者とメッセージ送信者は暗号化された電子メールを取り消す可能性があります。 受信者がサポートされているクライアントでネイティブ インライン エクスペリエンスをOutlook場合、メッセージを取り消す事はできません。

受信者がリンク ベースのエクスペリエンスまたはインライン エクスペリエンスを受け取るかどうかは、受信者 ID の種類によって異なります。Office 365 および Microsoft アカウントの受信者 (outlook.com ユーザーなど) は、サポートされている Outlook クライアントでインライン エクスペリエンスを取得します。 Gmail や Yahoo 受信者などの他のすべての受信者の種類は、リンク ベースのエクスペリエンスを取得します。

管理者とメッセージ送信者は、Web 上のユーザーから直接適用された暗号化を使用して暗号化されたOutlook取り消す可能性があります。 たとえば、[暗号化のみ] オプションで暗号化されたメッセージ。

:::image type="content" source="../media/adhocencryptionrevoke.png" alt-text="Web 上の [暗号化のみ] オプションをOutlookスクリーンショット。":::

## <a name="recipient-experience-for-revoked-encrypted-emails"></a>失効した暗号化された電子メールの受信者エクスペリエンス

電子メールが取り消された後、受信者は Office 365 Message Encryption ポータルを介して暗号化された電子メールにアクセスするときにエラーを受け取ります。"メッセージは送信者によって取り消されました"。

![失効した暗号化された電子メールを示すスクリーンショット。](../media/revoked-encrypted-email.png)

## <a name="how-to-revoke-an-encrypted-message-that-you-sent"></a>送信した暗号化されたメッセージを取り消す方法

1 人の受信者に送信したメールを取り消して、ソーシャル アカウントを使用 gmail.com、yahoo.com。 つまり、リンク ベースのエクスペリエンスを受け取った 1 人の受信者に送信された電子メールを取り消す可能性があります。

Office 365 または Microsoft 365 の仕事または学校のアカウントを使用する受信者、または Microsoft アカウントを使用するユーザー (outlook.com アカウントなど) に送信したメールを取り消 outlook.com できません。 

送信した暗号化されたメッセージを取り消す場合は、次の手順を実行します。

1. Web Outlook送信フォルダーで、取り消すメッセージを参照します。

   メールが失効可能な場合は、メッセージの上部に [外部アクセスの削除] リンクが表示されます。

    :::image type="content" source="../media/infoprotect-email-encryption/adhocencryptionrevokesentmsg.png" alt-text="Web 上で無効にしたい暗号化されたメールを示Outlookスクリーンショット。":::

2. [外部 **アクセスの削除] をクリック** して、メッセージを取り消します。

   メッセージは、その状態が取り消された状態を示しています。

   :::image type="content" source="../media/adhocencryptionrevokedmsg.png" alt-text="Web 上で無効にされた暗号化されたメッセージOutlook示すスクリーンショット。":::

## <a name="how-to-revoke-an-encrypted-message-as-an-administrator"></a>管理者として暗号化されたメッセージを取り消す方法

Microsoft 365管理者は、次の一般的な手順に従って、適格な暗号化された電子メールを取り消します。

- 電子メールのメッセージ ID を取得します。
- メッセージを取り消す可能性を確認します。
- メールを取り消します。

### <a name="step-1-obtain-the-message-id-of-the-email"></a>手順 1. 電子メールのメッセージ ID を取得する

暗号化されたメールを取り消す前に、メールのメッセージ ID を収集します。 MessageId は通常、次の形式です。

`<xxxxxxxxxxxxxxxxxxxxxxx@xxxxxx.xxxx.prod.outlook.com>`  

取り消す電子メールのメッセージ ID を検索する方法は複数あります。 このセクションでは、いくつかのオプションについて説明しますが、ID を提供する任意のメソッドを使用できます。

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-message-trace-in-the-security-amp-compliance-center"></a>セキュリティ コンプライアンス センターでメッセージ トレースを使用して取り消す電子メールのメッセージ ID を &amp; 識別するには

1. [セキュリティ] コンプライアンス センターの [新しいメッセージ トレース] を使用して、送信者 [または受信者&検索します](https://blogs.technet.microsoft.com/exchange/2018/05/02/new-message-trace-in-office-365-security-compliance-center/)。

2. 電子メールを見つから選択すると、[メッセージ 追跡の詳細] **ウィンドウが表示** されます。 [詳細 **] を展開** してメッセージ ID を探します。

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-office-message-encryption-reports-in-the-security-amp-compliance-center"></a>セキュリティ コンプライアンス センターの [メッセージ暗号化] レポートを使用してOfficeのメッセージ ID を &amp; 識別するには

1. セキュリティ コンプライアンス センター &amp; で、[メッセージの暗号化] **レポートに移動します**。 このレポートの詳細については、「セキュリティ コンプライアンス センター [で電子メール セキュリティ レポートを表示する」を &amp; 参照してください](../security/defender-365-security/view-email-security-reports.md)。

2. [詳細の **表示] テーブル** を選択し、取り消すメッセージを識別します。

3. メッセージをダブルクリックして、メッセージ ID を含む詳細を表示します。

### <a name="step-2-verify-that-the-mail-is-revocable"></a>手順 2. メールが失効可能な場合の確認

メッセージを取り消すかどうかを確認するには、セキュリティ コンプライアンス センターの [詳細] テーブルの [暗号化]レポートに [失効の状態] フィールドが表示されているかどうかを &amp; 確認します。

メール メッセージを使用して特定の電子メール メッセージを取り消Windows PowerShell、次の手順を実行します。

1. 組織でグローバル管理者アクセス許可を持つ仕事または学校のアカウントを使用して、Windows PowerShell セッションを開始し、Exchange Online。 手順については、「[Exchange Online PowerShell に接続する](/powershell/exchange/connect-to-exchange-online-powershell)」を参照してください。

2. 次のようにGet-OMEMessageStatusコマンドレットを実行します。

     ```powershell
     Get-OMEMessageStatus -MessageId "<message id>" | ft -a  Subject, IsRevocable
     ```

   このコマンドは、メッセージの件名とメッセージが取り消し可能かどうかを返します。 例えば、

     ```console
     Subject        IsRevocable
     -------        -----------
     "Test message" True
     ```

### <a name="step-3-revoke-the-mail"></a>手順 3. メールを取り消す

取り消す電子メールのメッセージ ID がわかり、メッセージが失効可能かどうか確認したら、セキュリティ コンプライアンス センターまたは Windows PowerShell を使用して電子 &amp; メールを取り消Windows PowerShell。

セキュリティ コンプライアンス センターを使用してメッセージを &amp; 取り消す方法

1. 組織でグローバル管理者のアクセス許可を持つ仕事または学校のアカウントを使用して、コンプライアンス センターのセキュリティ &接続します。

2. [暗号化] **レポートの** メッセージの [ **詳細]** テーブルで、[メッセージの取り消し] **を選択します**。

メールを使用してメールを取り消Windows PowerShell、Set-OMEMessageRevocationします。

1. 組織でグローバル管理者のアクセス許可を持つ仕事または学校のアカウントを使用して[、PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)ConnectをExchange Onlineします。

2. 次のようにSet-OMEMessageRevocationコマンドレットを実行します。

    ```powershell
    Set-OMEMessageRevocation -Revoke $true -MessageId "<messageId>"
    ```

3. 電子メールが取り消されたかどうかを確認するには、次のように Get-OMEMessageStatusコマンドレットを実行します。

    ```powershell
    Get-OMEMessageStatus -MessageId "<messageId>" | ft -a  Subject, Revoked
    ```

    失効が成功した場合、コマンドレットは次の結果を返します。  

     ```console
     Revoked: True
     ```

## <a name="more-information-about-office-365-advanced-message-encryption"></a>詳細については、Office 365 Advanced Message Encryption

- [Office 365 Advanced Message Encryption](ome-advanced-message-encryption.md)

- [Office 365 Advanced Message Encryption - メールの有効期限](ome-advanced-expiration.md)

- [メッセージ ポリシーとコンプライアンス サービスの説明](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)