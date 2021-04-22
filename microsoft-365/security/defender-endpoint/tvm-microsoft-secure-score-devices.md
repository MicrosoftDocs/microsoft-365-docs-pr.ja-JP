---
title: デバイス向けの Microsoft セキュア スコア
description: デバイスのスコアは、アプリケーション、オペレーティング システム、ネットワーク、アカウント、およびセキュリティ制御全体にわたるデバイスの一括セキュリティ構成状態を示します。
keywords: Microsoft Secure Score for Devices, Microsoft Defender for Endpoint Microsoft Secure Score for Devices, secure score, configuration score, threat and vulnerability management, security controls, improvement opportunitis, security configuration score over time, security configuration score, baseline
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: f2c799d477c400482c16b09b4d8a5cdc01106dfa
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2021
ms.locfileid: "51934083"
---
# <a name="microsoft-secure-score-for-devices"></a><span data-ttu-id="7d581-104">デバイス向けの Microsoft セキュア スコア</span><span class="sxs-lookup"><span data-stu-id="7d581-104">Microsoft Secure Score for Devices</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

<span data-ttu-id="7d581-105">**適用対象:**</span><span class="sxs-lookup"><span data-stu-id="7d581-105">**Applies to:**</span></span>

- [<span data-ttu-id="7d581-106">Microsoft Defender for Endpoint</span><span class="sxs-lookup"><span data-stu-id="7d581-106">Microsoft Defender for Endpoint</span></span>](https://go.microsoft.com/fwlink/?linkid=2154037)
- [<span data-ttu-id="7d581-107">脅威と脆弱性の管理</span><span class="sxs-lookup"><span data-stu-id="7d581-107">Threat and vulnerability management</span></span>](next-gen-threat-and-vuln-mgt.md)
- [<span data-ttu-id="7d581-108">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="7d581-108">Microsoft 365 Defender</span></span>](https://go.microsoft.com/fwlink/?linkid=2118804)

> <span data-ttu-id="7d581-109">Defender for Endpoint を体験してみませんか?</span><span class="sxs-lookup"><span data-stu-id="7d581-109">Want to experience Defender for Endpoint?</span></span> [<span data-ttu-id="7d581-110">無料試用版にサインアップしてください。</span><span class="sxs-lookup"><span data-stu-id="7d581-110">Sign up for a free trial.</span></span>](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-pullalerts-abovefoldlink) 


>[!NOTE]
> <span data-ttu-id="7d581-111">構成スコアは、Microsoft Secure Score for Devices として脅威と脆弱性管理の一部です。</span><span class="sxs-lookup"><span data-stu-id="7d581-111">Configuration score is now part of threat and vulnerability management as Microsoft Secure Score for Devices.</span></span>

<span data-ttu-id="7d581-112">デバイスのスコアは、Microsoft Defender[](tvm-dashboard-insights.md)セキュリティ センターの脅威と脆弱性管理ダッシュボードに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d581-112">Your score for devices is visible in the [threat and vulnerability management dashboard](tvm-dashboard-insights.md) of the Microsoft Defender Security Center.</span></span> <span data-ttu-id="7d581-113">デバイスの Microsoft セキュア スコアが高いということは、エンドポイントがサイバー セキュリティの脅威攻撃に対してより回復力があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="7d581-113">A higher Microsoft Secure Score for Devices means your endpoints are more resilient from cybersecurity threat attacks.</span></span> <span data-ttu-id="7d581-114">これは、次のカテゴリにわたるデバイスの一括セキュリティ構成状態を反映します。</span><span class="sxs-lookup"><span data-stu-id="7d581-114">It reflects the collective security configuration state of your devices across the following categories:</span></span>

- <span data-ttu-id="7d581-115">アプリケーション</span><span class="sxs-lookup"><span data-stu-id="7d581-115">Application</span></span>
- <span data-ttu-id="7d581-116">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="7d581-116">Operating system</span></span>
- <span data-ttu-id="7d581-117">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="7d581-117">Network</span></span>
- <span data-ttu-id="7d581-118">アカウント</span><span class="sxs-lookup"><span data-stu-id="7d581-118">Accounts</span></span>
- <span data-ttu-id="7d581-119">セキュリティ制御</span><span class="sxs-lookup"><span data-stu-id="7d581-119">Security controls</span></span>

<span data-ttu-id="7d581-120">カテゴリを選択して、[セキュリティの推奨事項 [**] ページに移動**](tvm-security-recommendation.md) し、関連する推奨事項を表示します。</span><span class="sxs-lookup"><span data-stu-id="7d581-120">Select a category to go to the [**Security recommendations**](tvm-security-recommendation.md) page and view the relevant recommendations.</span></span>

## <a name="turn-on-the-microsoft-secure-score-connector"></a><span data-ttu-id="7d581-121">Microsoft Secure Score コネクタを有効にする</span><span class="sxs-lookup"><span data-stu-id="7d581-121">Turn on the Microsoft Secure Score connector</span></span>

<span data-ttu-id="7d581-122">Microsoft Defender for Endpoint シグナルを転送し、Microsoft Secure Score をデバイスのセキュリティ状態に可視化します。</span><span class="sxs-lookup"><span data-stu-id="7d581-122">Forward Microsoft Defender for Endpoint signals, giving Microsoft Secure Score visibility into the device security posture.</span></span> <span data-ttu-id="7d581-123">転送されたデータは、Microsoft Secure Score データと同じ場所に保存および処理されます。</span><span class="sxs-lookup"><span data-stu-id="7d581-123">Forwarded data is stored and processed in the same location as your Microsoft Secure Score data.</span></span>

<span data-ttu-id="7d581-124">変更は、ダッシュボードに反映するために数時間かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7d581-124">Changes might take up to a few hours to reflect in the dashboard.</span></span>

1. <span data-ttu-id="7d581-125">ナビゲーション ウィンドウで、[設定] [高度な  >  **機能] に移動します。**</span><span class="sxs-lookup"><span data-stu-id="7d581-125">In the navigation pane, go to **Settings** > **Advanced features**</span></span> 

2. <span data-ttu-id="7d581-126">下にスクロールして **Microsoft Secure Score に移動** し、設定を [オン] に **切り替える**。</span><span class="sxs-lookup"><span data-stu-id="7d581-126">Scroll down to **Microsoft Secure Score** and toggle the setting to **On**.</span></span>

3. <span data-ttu-id="7d581-127">[基本 **設定の保存] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="7d581-127">Select **Save preferences**.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="7d581-128">メカニズム</span><span class="sxs-lookup"><span data-stu-id="7d581-128">How it works</span></span>

>[!NOTE]
> <span data-ttu-id="7d581-129">Microsoft Secure Score for Devices は現在、グループ ポリシーを介して設定された構成をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="7d581-129">Microsoft Secure Score for Devices currently supports configurations set via Group Policy.</span></span> <span data-ttu-id="7d581-130">現在の部分的な Intune のサポートにより、Intune を介して設定されている可能性がある構成が正しく構成されていないと表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="7d581-130">Due to the current partial Intune support, configurations which might have been set through Intune might show up as misconfigured.</span></span> <span data-ttu-id="7d581-131">組織が安全な構成管理のために Intune を使用している場合に、IT 管理者に問い合わせて実際の構成状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="7d581-131">Contact your IT Administrator to verify the actual configuration status in case your organization is using Intune for secure configuration management.</span></span>

<span data-ttu-id="7d581-132">Microsoft Secure Score for Devices カードのデータは、細心の注意を払い、継続的な脆弱性検出プロセスの製品です。</span><span class="sxs-lookup"><span data-stu-id="7d581-132">The data in the Microsoft Secure Score for Devices card is the product of meticulous and ongoing vulnerability discovery process.</span></span> <span data-ttu-id="7d581-133">次の構成検出評価が継続的に集計されます。</span><span class="sxs-lookup"><span data-stu-id="7d581-133">It is aggregated with configuration discovery assessments that continuously:</span></span>

- <span data-ttu-id="7d581-134">収集された構成と収集されたベンチマークを比較して、構成が誤ったアセットを検出する</span><span class="sxs-lookup"><span data-stu-id="7d581-134">Compare collected configurations to the collected benchmarks to discover misconfigured assets</span></span>
- <span data-ttu-id="7d581-135">構成を修正または部分的に修復できる脆弱性にマップする (リスクの軽減)</span><span class="sxs-lookup"><span data-stu-id="7d581-135">Map configurations to vulnerabilities that can be remediated or partially remediated (risk reduction)</span></span>
- <span data-ttu-id="7d581-136">ベスト プラクティス構成ベンチマーク (ベンダー、セキュリティ フィード、内部調査チーム) を収集して維持する</span><span class="sxs-lookup"><span data-stu-id="7d581-136">Collect and maintain best practice configuration benchmarks (vendors, security feeds, internal research teams)</span></span>
- <span data-ttu-id="7d581-137">すべてのアセットからセキュリティ制御構成状態の変更を収集および監視する</span><span class="sxs-lookup"><span data-stu-id="7d581-137">Collect and monitor changes of security control configuration state from all assets</span></span>

## <a name="improve-your-security-configuration"></a><span data-ttu-id="7d581-138">セキュリティ構成の改善</span><span class="sxs-lookup"><span data-stu-id="7d581-138">Improve your security configuration</span></span>

<span data-ttu-id="7d581-139">セキュリティの推奨事項の一覧から問題を修復して、セキュリティ構成を改善します。</span><span class="sxs-lookup"><span data-stu-id="7d581-139">Improve your security configuration by remediating issues from the security recommendations list.</span></span> <span data-ttu-id="7d581-140">そうすると、Microsoft Secure Score for Devices が向上し、組織はサイバーセキュリティの脅威や脆弱性に対してより回復力が高くなります。</span><span class="sxs-lookup"><span data-stu-id="7d581-140">As you do so, your Microsoft Secure Score for Devices improves and your organization becomes more resilient against cybersecurity threats and vulnerabilities.</span></span>

1. <span data-ttu-id="7d581-141">脅威と脆弱性管理ダッシュボードの Microsoft Secure Score for Devices カードから、カテゴリのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="7d581-141">From the Microsoft Secure Score for Devices card in the threat and vulnerability management dashboard, select the one of the categories.</span></span> <span data-ttu-id="7d581-142">そのカテゴリに関連する推奨事項の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d581-142">You'll view the list of recommendations related to that category.</span></span> <span data-ttu-id="7d581-143">[セキュリティの推奨事項] [**ページに移動**](tvm-security-recommendation.md) します。</span><span class="sxs-lookup"><span data-stu-id="7d581-143">It will take you to the [**Security recommendations**](tvm-security-recommendation.md) page.</span></span> <span data-ttu-id="7d581-144">すべてのセキュリティ推奨事項を表示する場合は、[セキュリティの推奨事項] ページに移動したら、検索フィールドをクリアします。</span><span class="sxs-lookup"><span data-stu-id="7d581-144">If you want to see all security recommendations, once you get to the Security recommendations page, clear the search field.</span></span>

2. <span data-ttu-id="7d581-145">リストでアイテムを選択します。</span><span class="sxs-lookup"><span data-stu-id="7d581-145">Select an item on the list.</span></span> <span data-ttu-id="7d581-146">フライアウト パネルが開き、推奨事項に関連する詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d581-146">The flyout panel will open with details related to the recommendation.</span></span> <span data-ttu-id="7d581-147">[修復 **オプション] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="7d581-147">Select **Remediation options**.</span></span>

   ![セキュリティ制御関連のセキュリティ推奨事項](images/tvm_security_controls.png)

3. <span data-ttu-id="7d581-149">説明を読んで、問題のコンテキストと次に何を行うのかを理解します。</span><span class="sxs-lookup"><span data-stu-id="7d581-149">Read the description to understand the context of the issue and what to do next.</span></span> <span data-ttu-id="7d581-150">期日を選択し、メモを追加し、[すべての修復アクティビティ データを **CSV** にエクスポートする] を選択して、フォローアップのためにメールに添付できます。</span><span class="sxs-lookup"><span data-stu-id="7d581-150">Select a due date, add notes, and select **Export all remediation activity data to CSV** so you can attach it to an email for follow-up.</span></span>

4. <span data-ttu-id="7d581-151">**要求を送信します**。</span><span class="sxs-lookup"><span data-stu-id="7d581-151">**Submit request**.</span></span> <span data-ttu-id="7d581-152">修復タスクが作成されたという確認メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7d581-152">You'll see a confirmation message that the remediation task has been created.</span></span>
   <span data-ttu-id="7d581-153">![修復タスクの作成確認](images/tvm_remediation_task_created.png)</span><span class="sxs-lookup"><span data-stu-id="7d581-153">![Remediation task creation confirmation](images/tvm_remediation_task_created.png)</span></span>

5. <span data-ttu-id="7d581-154">CSV ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="7d581-154">Save your CSV file.</span></span>
   <span data-ttu-id="7d581-155">![csv ファイルを保存する](images/tvm_save_csv_file.png)</span><span class="sxs-lookup"><span data-stu-id="7d581-155">![Save csv file](images/tvm_save_csv_file.png)</span></span>

6. <span data-ttu-id="7d581-156">IT 管理者にフォローアップ メールを送信し、修復がシステムに伝達される時間を許可します。</span><span class="sxs-lookup"><span data-stu-id="7d581-156">Send a follow-up email to your IT Administrator and allow the time that you've allotted for the remediation to propagate in the system.</span></span>

7. <span data-ttu-id="7d581-157">ダッシュボードで **Microsoft Secure Score for Devices** カードを再度確認します。</span><span class="sxs-lookup"><span data-stu-id="7d581-157">Review the **Microsoft Secure Score for Devices** card again on the dashboard.</span></span> <span data-ttu-id="7d581-158">セキュリティ制御の推奨事項の数は減少します。</span><span class="sxs-lookup"><span data-stu-id="7d581-158">The number of security controls recommendations will decrease.</span></span> <span data-ttu-id="7d581-159">[セキュリティの **推奨事項]** ページに戻る[セキュリティ コントロール] を選択すると、アドレス指定したアイテムは表示されません。</span><span class="sxs-lookup"><span data-stu-id="7d581-159">When you select **Security controls** to go back to the **Security recommendations** page, the item that you've addressed won't be listed there anymore.</span></span> <span data-ttu-id="7d581-160">Microsoft Secure Score for Devices は増加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d581-160">Your Microsoft Secure Score for Devices should increase.</span></span>

>[!IMPORTANT]
><span data-ttu-id="7d581-161">脆弱性評価の検出率を上げるには、次の必須のセキュリティ更新プログラムをダウンロードし、ネットワークに展開します。</span><span class="sxs-lookup"><span data-stu-id="7d581-161">To boost your vulnerability assessment detection rates, download the following mandatory security updates and deploy them in your network:</span></span>
>- <span data-ttu-id="7d581-162">19H1 のお客様| [KB 4512941](https://support.microsoft.com/help/4512941/windows-10-update-kb4512941)</span><span class="sxs-lookup"><span data-stu-id="7d581-162">19H1 customers | [KB 4512941](https://support.microsoft.com/help/4512941/windows-10-update-kb4512941)</span></span>
>- <span data-ttu-id="7d581-163">RS5 のお客様| [KB 4516077](https://support.microsoft.com/help/4516077/windows-10-update-kb4516077)</span><span class="sxs-lookup"><span data-stu-id="7d581-163">RS5 customers | [KB 4516077](https://support.microsoft.com/help/4516077/windows-10-update-kb4516077)</span></span>
>- <span data-ttu-id="7d581-164">RS4 のお客様| [KB 4516045](https://support.microsoft.com/help/4516045/windows-10-update-kb4516045)</span><span class="sxs-lookup"><span data-stu-id="7d581-164">RS4 customers | [KB 4516045](https://support.microsoft.com/help/4516045/windows-10-update-kb4516045)</span></span>
>- <span data-ttu-id="7d581-165">RS3 のお客様| [KB 4516071](https://support.microsoft.com/help/4516071/windows-10-update-kb4516071)</span><span class="sxs-lookup"><span data-stu-id="7d581-165">RS3 customers | [KB 4516071](https://support.microsoft.com/help/4516071/windows-10-update-kb4516071)</span></span>
>
><span data-ttu-id="7d581-166">セキュリティ更新プログラムをダウンロードするには、次の方法を実行します。</span><span class="sxs-lookup"><span data-stu-id="7d581-166">To download the security updates:</span></span>
>1. <span data-ttu-id="7d581-167">[Microsoft Update [Catalog] に移動します](https://www.catalog.update.microsoft.com/home.aspx)。</span><span class="sxs-lookup"><span data-stu-id="7d581-167">Go to [Microsoft Update Catalog](https://www.catalog.update.microsoft.com/home.aspx).</span></span>
>2. <span data-ttu-id="7d581-168">ダウンロードする必要があるセキュリティ更新プログラムの KB 番号をキーインし、[検索] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="7d581-168">Key-in the security update KB number that you need to download, then click **Search**.</span></span>  

## <a name="related-topics"></a><span data-ttu-id="7d581-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d581-169">Related topics</span></span>

- [<span data-ttu-id="7d581-170">脅威と脆弱性の管理の概要</span><span class="sxs-lookup"><span data-stu-id="7d581-170">Threat and vulnerability management overview</span></span>](next-gen-threat-and-vuln-mgt.md)
- [<span data-ttu-id="7d581-171">ダッシュボード</span><span class="sxs-lookup"><span data-stu-id="7d581-171">Dashboard</span></span>](tvm-dashboard-insights.md)
- [<span data-ttu-id="7d581-172">暴露スコア</span><span class="sxs-lookup"><span data-stu-id="7d581-172">Exposure score</span></span>](tvm-exposure-score.md)
- [<span data-ttu-id="7d581-173">セキュリティ上の推奨事項</span><span class="sxs-lookup"><span data-stu-id="7d581-173">Security recommendations</span></span>](tvm-security-recommendation.md)
