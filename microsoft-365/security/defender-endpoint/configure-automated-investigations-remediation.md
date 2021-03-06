---
title: 自動調査と修復機能の構成
description: Microsoft Defender for Endpoint で自動調査および修復機能をセットアップします。
keywords: 構成、セットアップ、自動化、調査、検出、アラート、修復、応答
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: JoeDavies-MSFT
ms.author: josephd
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: how-to
ms.date: 01/27/2021
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.openlocfilehash: bd86458749db4019bb247a3664748b9891965754
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2021
ms.locfileid: "52841348"
---
# <a name="configure-automated-investigation-and-remediation-capabilities-in-microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpoint で自動調査および修復機能を構成する

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**適用対象:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Defender for Endpoint を体験してみませんか? [無料試用版にサインアップしてください。](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

組織が[](/microsoft-365/security/defender-endpoint/automated-investigations)Microsoft [Defender for Endpoint (Defender for Endpoint)](/windows/security/threat-protection/)を使用している場合、自動調査および修復機能により、セキュリティ運用チームの時間と労力を節約できます。 このブログ記事で [説明するように、](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/enhance-your-soc-with-microsoft-defender-atp-automatic/ba-p/848946)これらの機能は、セキュリティ アナリストが脅威の調査と修復に必要な理想的な手順を模倣します。 [自動調査と修復の詳細については、次のリンクを参照してください](/microsoft-365/security/defender-endpoint/automated-investigations)。 

自動調査と修復を構成するには、
1. [機能を有効にする](#turn-on-automated-investigation-and-remediation)。そして 
2. [デバイス グループを設定します](#set-up-device-groups)。

## <a name="turn-on-automated-investigation-and-remediation"></a>自動調査と修復を有効にする

1. グローバル管理者またはセキュリティ管理者として、管理者 ( ) にMicrosoft Defender セキュリティ センター [https://securitycenter.windows.com](https://securitycenter.windows.com) サインインします。
2. ナビゲーション ウィンドウで、[次へ]**を設定。**
3. [全般] **セクションで** 、[高度な機能 **] を選択します**。
4. [自動調査]**と [アラートの****自動解決] の両方をオンにします**。

## <a name="set-up-device-groups"></a>デバイス グループを設定する

1. [Microsoft Defender セキュリティ センター ] ( [https://securitycenter.windows.com](https://securitycenter.windows.com) ) の [アクセス許可]**設定** で、[デバイス グループ]**を選択します**。 
2. [+ **デバイス グループの追加] を選択します**。
3. 次のように、少なくとも 1 つのデバイス グループを作成します。
   - デバイス グループの名前と説明を指定します。
   - [オートメーション レベル **] ボックスの** 一覧で、[完全] などのレベルを選択し、脅威 **を自動的に修復します**。 オートメーション レベルは、修復アクションが自動的に実行されるのか、承認時にのみ実行されるのかを決定します。 詳細については、「自動調査と [修復」の「オートメーション レベル」を参照してください](automation-levels.md)。
   - [メンバー **] セクション** で、1 つ以上の条件を使用してデバイスを識別して含める。
   - [ユーザー **アクセス] タブ** で [](/azure/active-directory/fundamentals/active-directory-manage-groups?context=azure/active-directory/users-groups-roles/context/ugr-context)、Azure Active Directoryするデバイス グループにアクセスする必要があるグループを選択します。
4. デバイス **グループの** 設定が完了したら、[完了] を選択します。

## <a name="next-steps"></a>次の手順

- [アクション センターにアクセスして、保留中の修復アクションと完了済み修復アクションを表示する](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
- [保留中のアクションの確認と承認](/microsoft-365/security/defender-endpoint/manage-auto-investigation)

## <a name="see-also"></a>関連項目

- [Microsoft Defender for Endpoint での誤検出/検出漏れに対処する](defender-endpoint-false-positives-negatives.md)
