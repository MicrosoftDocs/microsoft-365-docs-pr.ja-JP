---
title: 高度な検索スキーマMicrosoft 365 Defenderテーブル
description: 高度な捜索スキーマのテーブルについて学習し、脅威の捜索クエリを実行できるデータを理解します。
keywords: 高度な検索、脅威の検出、サイバー脅威の検出、Microsoft 365 Defender、microsoft 365、m365、検索、クエリ、利用統計情報、スキーマ参照、kusto、table、data
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 50a221a65c8264d816de958ec74fa99e9e6db762
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/30/2021
ms.locfileid: "53225994"
---
# <a name="understand-the-advanced-hunting-schema"></a>高度な捜索スキーマの概要

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**適用対象:**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

高度 [な検索スキーマ](advanced-hunting-overview.md) は、イベント情報またはデバイス、アラート、ID、その他のエンティティの種類に関する情報を提供する複数のテーブルで構成されます。 複数のテーブルにまたがるクエリを効果的に構築するには、高度な捜索スキーマのテーブルと列を理解する必要があります。

## <a name="get-schema-information-in-the-security-center"></a>セキュリティ センターでスキーマ情報を取得する
クエリを作成する場合は、組み込みのスキーマ参照を使用して、スキーマ内の各テーブルに関する次の情報をすばやく取得します。

- **テーブルの** 説明 —テーブルに含まれるデータの種類と、そのデータのソース。
- **列**—テーブル内のすべての列。
- **アクションの** 種類 —テーブルでサポートされるイベントの種類を表す列 `ActionType` の可能な値。 この情報は、イベント情報を含むテーブルに対してのみ提供されます。
- **サンプル クエリ**—テーブルの利用方法を特徴付けするクエリの例。

### <a name="access-the-schema-reference"></a>スキーマ参照へのアクセス
スキーマ参照にすばやくアクセスするには、スキーマ表現のテーブル名の横にある [参照の表示] アクションを選択します。 [スキーマ参照] **を選択して** テーブルを検索することもできます。

![ポータル内スキーマ参照にアクセスする方法を示すイメージ](../../media/mtp-ah/ah-reference.png)

## <a name="learn-the-schema-tables"></a>スキーマ テーブルの詳細
次の参照は、スキーマ内のすべてのテーブルを一覧表示します。 各テーブル名は、そのテーブルの列名を説明するページにリンクします。 テーブル名と列名は、高度な検索画面のスキーマ表現の一部としてセキュリティ センターにも表示されます。

| テーブル名 | 説明 |
|------------|-------------|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | アラートに関連付けられたファイル、IP アドレス、URL、ユーザー、またはデバイス |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | Microsoft Defender for Endpoint、Microsoft Defender for Office 365、Microsoft Cloud App Security、および Microsoft Defender for Identity からのアラート (重大度情報と脅威の分類を含む)  |
| **[CloudAppEvents](advanced-hunting-cloudappevents-table.md)** | アプリや他のクラウド アプリやサービスOffice 365アカウントとオブジェクトを含むイベント |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** | Windows Defender ウイルス対策や Exploit Protection などのセキュリティ制御によりトリガーされたイベントを含むさまざまな種類のイベント  |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** | エンドポイント上の証明書検証イベントから取得した署名済みファイルの証明書情報 |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | ファイルの作成、変更、およびその他のファイル システム イベント |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | DLL の読み込みイベント |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | OS 情報を含むマシン情報 |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | デバイスでのサインインと他の認証イベント |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** | ネットワーク接続と関連イベント |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | 物理アダプター、IP アドレス、MAC アドレス、接続されたネットワークおよびドメインを含むデバイスのネットワーク プロパティ |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | プロセスの作成と関連イベント |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | レジストリ エントリの作成と変更 |
| **[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)** | デバイス上のさまざまなセキュリティ構成の状態を示す脅威および脆弱性管理の評価イベント |
| **[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)** | 脅威および脆弱性管理によってデバイスを評価するために使用されるさまざまなセキュリティ構成に関するサポート技術情報 (さまざまな標準およびベンチマークへのマッピングを含む)　  |
| **[DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md)** | デバイスにインストールされているソフトウェアのインベントリ (バージョン情報とサポート終了の状態を含む) |
| **[DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md)** | デバイスで見つかったソフトウェアの脆弱性と、各脆弱性に対処する利用可能なセキュリティ更新プログラムの一覧 |
| **[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)** | 悪用コードが公開されているかどうかなど、公開されている脆弱性のサポート技術情報 |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | メールに添付されているファイルに関する情報 |
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | Microsoft 365配信イベントやブロック イベントを含む電子メール イベントの管理 |
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | 受信者メールボックスに電子メールを配信した後Microsoft 365配信後に発生するセキュリティ イベント |
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | メールの URL に関する情報 |
| **[IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md)** | Active Directory を実行しているオンプレミスのドメイン コントローラーに関連するイベント (AD)。 次の表では、ドメイン コントローラー上の ID 関連イベントとシステム イベントの範囲について説明します。 |
| **[IdentityInfo](advanced-hunting-identityinfo-table.md)** | さまざまなソースからのアカウント情報 (Azure Active Directory |
| **[IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)** | Active Directory および Microsoft オンライン サービスでの認証イベント |
| **[IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)** | ユーザー、グループ、デバイス、ドメインなどの Active Directory オブジェクトのクエリ |

## <a name="related-topics"></a>関連項目
- [高度な追求の概要](advanced-hunting-overview.md)
- [クエリ言語の説明](advanced-hunting-query-language.md)
- [クエリ結果を操作する](advanced-hunting-query-results.md)
- [共有クエリを使用する](advanced-hunting-shared-queries.md)
- [デバイス、メール、アプリ、ID 全体で探す](advanced-hunting-query-emails-devices.md)
- [クエリのベスト プラクティスを適用する](advanced-hunting-best-practices.md)
