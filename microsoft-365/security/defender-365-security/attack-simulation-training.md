---
title: Microsoft Defender を使用してフィッシング攻撃をシミュレートOffice 365
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: 管理者は、Microsoft Defender for microsoft Defender for Office 365 を使用して、フィッシング攻撃をシミュレートし、フィッシング防止に関するユーザーをトレーニングする方法について説明します。
ms.technology: mdo
ms.openlocfilehash: 27279f927a15ea94ae84112ffdc23d88ea42d2ff
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51065476"
---
# <a name="simulate-a-phishing-attack"></a><span data-ttu-id="22fb6-103">フィッシング攻撃をシミュレートする</span><span class="sxs-lookup"><span data-stu-id="22fb6-103">Simulate a phishing attack</span></span>

<span data-ttu-id="22fb6-104">Microsoft Defender for Office 365 の攻撃シミュレーション トレーニングを使用すると、組織で良性のサイバー攻撃シミュレーションを実行してセキュリティ ポリシーとプラクティスをテストし、従業員が攻撃に対する意識を高め、攻撃に対する影響を減らします。</span><span class="sxs-lookup"><span data-stu-id="22fb6-104">Attack simulation training in Microsoft Defender for Office 365 lets you run benign cyberattack simulations on your organization to test your security policies and practices, as well as train your employees to increase their awareness and decrease their susceptibility to attacks.</span></span> <span data-ttu-id="22fb6-105">この記事では、攻撃シミュレーション トレーニングを使用してシミュレートされたフィッシング攻撃を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="22fb6-105">This article walks you through creating  a simulated phishing attack using attack simulation training.</span></span>

<span data-ttu-id="22fb6-106">攻撃シミュレーション トレーニングの概要については、「攻撃シミュレーション トレーニングの使用を開始 [する」を参照してください](attack-simulation-training-get-started.md)。</span><span class="sxs-lookup"><span data-stu-id="22fb6-106">For getting started information about Attack simulation training, see [Get started using Attack simulation training](attack-simulation-training-get-started.md).</span></span>

<span data-ttu-id="22fb6-107">シミュレートされたフィッシング攻撃を起動するには [、Microsoft 365](https://security.microsoft.com/)セキュリティ センターを開き、[メール &**コラボレーション** 攻撃シミュレーション トレーニング] に移動し、[シミュレーション] タブ \> [**に切り替**](https://security.microsoft.com/attacksimulator?viewid=simulations)えます。</span><span class="sxs-lookup"><span data-stu-id="22fb6-107">To launch a simulated phishing attack, open the [Microsoft 365 security center](https://security.microsoft.com/), go to **Email & collaboration** \> **Attack simulation training**, and switch to the [**Simulations**](https://security.microsoft.com/attacksimulator?viewid=simulations) tab.</span></span>

<span data-ttu-id="22fb6-108">[ **シミュレーション] で**、[+ **シミュレーションの起動] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="22fb6-108">Under **Simulations**, select **+ Launch a simulation**.</span></span>

![Microsoft 365 セキュリティ センターでシミュレーション ボタンを起動する](../../media/attack-sim-preview-launch.png)

> [!NOTE]
> <span data-ttu-id="22fb6-110">シミュレーション作成時の任意の時点で、保存して閉じて、後でシミュレーションの構成を続行できます。</span><span class="sxs-lookup"><span data-stu-id="22fb6-110">At any point during simulation creation, you can save and close to continue configuring the simulation at a later time.</span></span>

## <a name="selecting-a-social-engineering-technique"></a><span data-ttu-id="22fb6-111">ソーシャル エンジニアリング手法の選択</span><span class="sxs-lookup"><span data-stu-id="22fb6-111">Selecting a social engineering technique</span></span>

<span data-ttu-id="22fb6-112">4 つの異なる手法から選択します [。MITRE ATT および CK&フレームワーク®します](https://attack.mitre.org/techniques/enterprise/)。</span><span class="sxs-lookup"><span data-stu-id="22fb6-112">Select from 4 different techniques, curated from the [MITRE ATT&CK® framework](https://attack.mitre.org/techniques/enterprise/).</span></span> <span data-ttu-id="22fb6-113">さまざまなペイロードは、さまざまな手法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="22fb6-113">Different payloads are available for different techniques:</span></span>

- <span data-ttu-id="22fb6-114">**資格情報の取得** は、ユーザー名とパスワードを送信するための入力ボックスを持つよく知られている Web サイトにユーザーを連れて行き、資格情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="22fb6-114">**Credential harvest** attempts to collect credentials by taking users to a well-known looking website with input boxes to submit a username and password.</span></span>
- <span data-ttu-id="22fb6-115">**マルウェアの添付** ファイルは、悪意のある添付ファイルをメッセージに追加します。</span><span class="sxs-lookup"><span data-stu-id="22fb6-115">**Malware attachment** adds a malicious attachment to a message.</span></span> <span data-ttu-id="22fb6-116">ユーザーが添付ファイルを開くと、攻撃者がターゲットのデバイスを侵害するのに役立つ任意のコードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="22fb6-116">When the user opens the attachment, arbitrary code is run that will help the attacker compromise the target's device.</span></span>
- <span data-ttu-id="22fb6-117">**添付ファイル内のリンク** は、資格情報の取得ハイブリッドの一種です。</span><span class="sxs-lookup"><span data-stu-id="22fb6-117">**Link in attachment** is a type of credential harvest hybrid.</span></span> <span data-ttu-id="22fb6-118">攻撃者は電子メールの添付ファイルに URL を挿入します。</span><span class="sxs-lookup"><span data-stu-id="22fb6-118">An attacker inserts a URL into an email attachment.</span></span> <span data-ttu-id="22fb6-119">添付ファイル内の URL は、資格情報の取得と同じ手法に従います。</span><span class="sxs-lookup"><span data-stu-id="22fb6-119">The URL within the attachment follows the same technique as credential harvest.</span></span>
- <span data-ttu-id="22fb6-120">**マルウェアへのリンクは** 、既知のファイル共有サービスでホストされているファイルから任意のコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="22fb6-120">**Link to malware** will run some arbitrary code from a file hosted on a well-known file sharing service.</span></span> <span data-ttu-id="22fb6-121">ユーザーに送信されるメッセージには、この悪意のあるファイルへのリンクが含まれる。</span><span class="sxs-lookup"><span data-stu-id="22fb6-121">The message sent to the user will contain a link to this malicious file.</span></span> <span data-ttu-id="22fb6-122">ファイルを開き、攻撃者がターゲットのデバイスを侵害するのを助ける。</span><span class="sxs-lookup"><span data-stu-id="22fb6-122">Opening the file and help the attacker compromise the target's device.</span></span>
- <span data-ttu-id="22fb6-123">**ドライブ URL は** 、メッセージ内の悪意のある URL が、ユーザーのデバイス上でコード コードをサイレントモードで実行またはインストールする見慣れた Web サイトにユーザーを連れ込む場所です。</span><span class="sxs-lookup"><span data-stu-id="22fb6-123">**Drive-by URL** is where the malicious URL in the message takes the user to a familiar-looking website that silently runs and/or installs code code on the user's device.</span></span>

> [!TIP]
> <span data-ttu-id="22fb6-124">[各手法の **説明内の** 詳細を表示する] をクリックすると、その手法に関する詳細情報とシミュレーション手順が表示されます。</span><span class="sxs-lookup"><span data-stu-id="22fb6-124">Clicking on **View details** within the description of each technique will display further information and the simulation steps for the technique.</span></span>
>
> ![Microsoft 365 セキュリティ センターでの攻撃シミュレーション トレーニング内での資格情報の取得のためのシミュレーション手順](../../media/attack-sim-preview-sim-steps.png)

<span data-ttu-id="22fb6-126">テクニックを選択し、[次へ] をクリックした **後、シミュレーション** に名前と必要に応じて説明を指定します。</span><span class="sxs-lookup"><span data-stu-id="22fb6-126">After you've selected the technique and clicked on **Next**, give your simulation a name and optionally a description.</span></span>

## <a name="selecting-a-payload"></a><span data-ttu-id="22fb6-127">ペイロードの選択</span><span class="sxs-lookup"><span data-stu-id="22fb6-127">Selecting a payload</span></span>

<span data-ttu-id="22fb6-128">次に、既存のペイロード カタログからペイロードを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="22fb6-128">Next, you'll need to either select a payload from the pre-existing payload catalog.</span></span>

<span data-ttu-id="22fb6-129">ペイロードには、次の選択に役立つデータ ポイントが多数含まれています。</span><span class="sxs-lookup"><span data-stu-id="22fb6-129">Payloads have a number of data points to help you choose:</span></span>

- <span data-ttu-id="22fb6-130">**クリック率は** 、このペイロードをクリックしたユーザーの数をカウントします。</span><span class="sxs-lookup"><span data-stu-id="22fb6-130">**Click rate** counts how many people clicked this payload.</span></span>
- <span data-ttu-id="22fb6-131">**予測された妥協** 率は、365 人のユーザーに対する Microsoft Defender 全体のペイロードの履歴データに基づいて、このペイロードによって侵害される人の割合Office予測します。</span><span class="sxs-lookup"><span data-stu-id="22fb6-131">**Predicted compromise rate** predicts the percentage of people that will get compromised by this payload based on historical data for the payload across Microsoft Defender for Office 365 customers.</span></span>
- <span data-ttu-id="22fb6-132">**起動されたシミュレーションは** 、このペイロードが他のシミュレーションで使用された回数をカウントします。</span><span class="sxs-lookup"><span data-stu-id="22fb6-132">**Simulations launched** counts the number of times this payload was used in other simulations.</span></span>
- <span data-ttu-id="22fb6-133">**フィルターで** 使用できる複雑 **さは、** 攻撃の対象となるペイロード内のインジケーターの数に基づいて計算されます。</span><span class="sxs-lookup"><span data-stu-id="22fb6-133">**Complexity**, available through **filters**, is calculated based on the number of indicators within the payload that clue targets in on it being an attack.</span></span> <span data-ttu-id="22fb6-134">インジケーターが多い場合、複雑さも低くなります。</span><span class="sxs-lookup"><span data-stu-id="22fb6-134">More indicators lead to lower complexity.</span></span>
- <span data-ttu-id="22fb6-135">**フィルター** を **使用して使用可能** なソースは、ペイロードがテナントに作成されたのか、Microsoft の既存のペイロード カタログ (グローバル) の一部であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="22fb6-135">**Source**, available through **filters**, indicates whether the payload was created on your tenant or is a part of Microsoft's pre-existing payload catalog (global).</span></span>

![Microsoft 365 セキュリティ センターで攻撃シミュレーション トレーニング内で選択されたペイロード](../../media/attack-sim-preview-select-payload.png)

<span data-ttu-id="22fb6-137">リストからペイロードを選択すると、ペイロードのプレビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="22fb6-137">Select a payload from the list to see a preview of the payload with additional information about it.</span></span>

<span data-ttu-id="22fb6-138">独自のペイロードを作成する場合は、「攻撃シミュレーション トレーニング用のペイロード [を作成する」を参照してください](attack-simulation-training-payloads.md)。</span><span class="sxs-lookup"><span data-stu-id="22fb6-138">If you'd like to create your own payload, read [create a payload for attack simulation training](attack-simulation-training-payloads.md).</span></span>

## <a name="audience-targeting"></a><span data-ttu-id="22fb6-139">対象ユーザーの設定</span><span class="sxs-lookup"><span data-stu-id="22fb6-139">Audience targeting</span></span>

<span data-ttu-id="22fb6-140">次に、このシミュレーションの対象ユーザーを選択します。</span><span class="sxs-lookup"><span data-stu-id="22fb6-140">Now it's time to select this simulation's audience.</span></span> <span data-ttu-id="22fb6-141">組織内のすべてのユーザーを **含めるか** 、特定のユーザーとグループ **のみを含めるか選択できます**。</span><span class="sxs-lookup"><span data-stu-id="22fb6-141">You can choose to **include all users in your organization** or **include only specific users and groups**.</span></span>

<span data-ttu-id="22fb6-142">特定のユーザーと **グループのみを含める場合は** 、次のいずれかを実行できます。</span><span class="sxs-lookup"><span data-stu-id="22fb6-142">When you choose to **include only specific users and groups** you can either:</span></span>

- <span data-ttu-id="22fb6-143">**ユーザーを** 追加します。これにより、テナントの検索と高度な検索およびフィルター機能 (過去 3 か月間シミュレーションの対象とされていないユーザーをターゲットに設定する機能など) を利用できます。</span><span class="sxs-lookup"><span data-stu-id="22fb6-143">**Add users**, which allows you to leverage search for your tenant, as well as advanced search and filtering capabilities, like targeting users who haven't been targeted by a simulation in the last 3 months.</span></span>
  <span data-ttu-id="22fb6-144">![Microsoft 365 セキュリティ センターでの攻撃シミュレーション トレーニングでのユーザー フィルター](../../media/attack-sim-preview-user-targeting.png)</span><span class="sxs-lookup"><span data-stu-id="22fb6-144">![User filtering in attack simulation training on Microsoft 365 security center](../../media/attack-sim-preview-user-targeting.png)</span></span>
- <span data-ttu-id="22fb6-145">**CSV からインポートすると** 、このシミュレーション用に定義済みの一連のユーザーをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="22fb6-145">**Import from CSV** allows you to import a predefined set of users for this simulation.</span></span>

## <a name="assigning-training"></a><span data-ttu-id="22fb6-146">トレーニングの割り当て</span><span class="sxs-lookup"><span data-stu-id="22fb6-146">Assigning training</span></span>

<span data-ttu-id="22fb6-147">トレーニングを行う従業員が同様の攻撃を受けにくいので、シミュレーションごとにトレーニングを割り当てすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="22fb6-147">We recommend that you assign training for each simulation, as employees who go through training are less susceptible to similar attacks.</span></span>

<span data-ttu-id="22fb6-148">トレーニングを割り当てるか、自分でトレーニング コースとモジュールを選択できます。</span><span class="sxs-lookup"><span data-stu-id="22fb6-148">You can either choose to have training assigned for you or select training courses and modules yourself.</span></span>

<span data-ttu-id="22fb6-149">トレーニング期日 **を選択して** 、従業員が適切な方法でトレーニングを終了します。</span><span class="sxs-lookup"><span data-stu-id="22fb6-149">Select the **training due date** to make sure employees finish their training in a timely manner.</span></span>

> [!NOTE]
> <span data-ttu-id="22fb6-150">自分でコースとモジュールを選択した場合でも、推奨されるコンテンツと利用可能なすべてのコースとモジュールを表示できます。</span><span class="sxs-lookup"><span data-stu-id="22fb6-150">If you choose to select courses and modules yourself, you'll still be able to see the recommended content as well as all available courses and modules.</span></span>
>
> ![Microsoft 365 セキュリティ センターでの攻撃シミュレーション トレーニング内での推奨トレーニングの追加](../../media/attack-sim-preview-add-training.png)

<span data-ttu-id="22fb6-152">次の手順では、自分でトレーニングを選択し、トレーニングのランディング ページをカスタマイズする場合は、[トレーニングの追加] が必要です。</span><span class="sxs-lookup"><span data-stu-id="22fb6-152">In the next steps you'll need to **Add trainings** if you opted to select it yourself, and customize your training landing page.</span></span> <span data-ttu-id="22fb6-153">トレーニングランディング ページをプレビューし、ヘッダーと本文を変更できます。</span><span class="sxs-lookup"><span data-stu-id="22fb6-153">You'll be able to preview the training landing page, as well as change the header and body of it.</span></span>

## <a name="launch-details-and-review"></a><span data-ttu-id="22fb6-154">起動の詳細とレビュー</span><span class="sxs-lookup"><span data-stu-id="22fb6-154">Launch details and review</span></span>

<span data-ttu-id="22fb6-155">すべてが構成されたので、このシミュレーションを直ちに起動するか、後日スケジュールを設定できます。</span><span class="sxs-lookup"><span data-stu-id="22fb6-155">Now that everything is configured, you can launch this simulation immediately or schedule it for a later date.</span></span> <span data-ttu-id="22fb6-156">また、このシミュレーションを終了する時間を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="22fb6-156">You will also need to choose when to end this simulation.</span></span> <span data-ttu-id="22fb6-157">選択した時間を過ぎたこのシミュレーションとの相互作用のキャプチャを停止します。</span><span class="sxs-lookup"><span data-stu-id="22fb6-157">We will stop capturing interaction with this simulation past the selected time.</span></span>

<span data-ttu-id="22fb6-158">**地域対応のタイム ゾーン配信を** 有効にして、地域に基づいて勤務時間中に従業員にシミュレートされた攻撃メッセージを配信します。</span><span class="sxs-lookup"><span data-stu-id="22fb6-158">**Enable region aware timezone delivery** to deliver simulated attack messages to your employees during their working hours based on their region.</span></span>

<span data-ttu-id="22fb6-159">完了したら、[次へ] **をクリック** し、シミュレーションの詳細を確認します。</span><span class="sxs-lookup"><span data-stu-id="22fb6-159">Once you're done, click on **Next** and review the details of your simulation.</span></span> <span data-ttu-id="22fb6-160">任意の **パーツの [** 編集] をクリックして戻り、変更が必要な詳細を変更します。</span><span class="sxs-lookup"><span data-stu-id="22fb6-160">Click on **Edit** on any of the parts to go back and change any details that need changing.</span></span> <span data-ttu-id="22fb6-161">完了したら、[送信] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="22fb6-161">Once done, click **Submit**.</span></span>