---
title: レポート メッセージ アドインを有効にする
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
manager: dansimp
audience: Admin
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 4250c4bc-6102-420b-9e0a-a95064837676
ms.collection:
- M365-security-compliance
description: Outlook および Outlook on the web 用のレポート メッセージ アドインを、個々のユーザーまたは組織全体で有効にする方法について説明します。
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4e85af902eaaa41eb82acf8d4b4baedc538e7888
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51064531"
---
# <a name="enable-the-report-message-add-in"></a><span data-ttu-id="b4b39-103">レポート メッセージ アドインを有効にする</span><span class="sxs-lookup"><span data-stu-id="b4b39-103">Enable the Report Message add-in</span></span>

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

<span data-ttu-id="b4b39-104">**適用対象**</span><span class="sxs-lookup"><span data-stu-id="b4b39-104">**Applies to**</span></span>
- [<span data-ttu-id="b4b39-105">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="b4b39-105">Exchange Online Protection</span></span>](exchange-online-protection-overview.md)
- [<span data-ttu-id="b4b39-106">Microsoft Defender for Office 365 プラン 1 およびプラン 2</span><span class="sxs-lookup"><span data-stu-id="b4b39-106">Microsoft Defender for Office 365 plan 1 and plan 2</span></span>](defender-for-office-365.md)
- [<span data-ttu-id="b4b39-107">Microsoft 365 Defender</span><span class="sxs-lookup"><span data-stu-id="b4b39-107">Microsoft 365 Defender</span></span>](../defender/microsoft-365-defender.md)

> [!NOTE]
> <span data-ttu-id="b4b39-108">Exchange Online メールボックスを使用する Microsoft 365 組織の管理者である場合は、セキュリティ & コンプライアンス センターで申請ポータルを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b4b39-108">If you're an admin in a Microsoft 365 organization with Exchange Online mailboxes, we recommend that you use the Submissions portal in the Security & Compliance Center.</span></span> <span data-ttu-id="b4b39-109">詳細については、「管理申請を [使用して疑わしいスパム、フィッシング、URL、](admin-submission.md)ファイルを Microsoft に提出する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4b39-109">For more information, see [Use Admin Submission to submit suspected spam, phish, URLs, and files to Microsoft](admin-submission.md).</span></span>

<span data-ttu-id="b4b39-110">Outlook および Outlook on the web (以前は Outlook Web App と呼ばれる) のレポート メッセージとレポートフィッシング アドインを使用すると、ユーザーは誤検知 (悪いとマークされた良いメール) または誤検知 (悪いメールが許可されている) を Microsoft とその関連会社に簡単に報告して分析できます。</span><span class="sxs-lookup"><span data-stu-id="b4b39-110">The Report Message and Report Phishing add-ins for Outlook and Outlook on the web (formerly known as Outlook Web App) enables people to easily report false positives (good email marked as bad) or false negatives (bad email allowed) to Microsoft and its affiliates for analysis.</span></span>

<span data-ttu-id="b4b39-111">Microsoft では、これらの申請を使用して、電子メール保護テクノロジの有効性を向上します。</span><span class="sxs-lookup"><span data-stu-id="b4b39-111">Microsoft uses these submissions to improve the effectiveness of email protection technologies.</span></span> <span data-ttu-id="b4b39-112">たとえば、レポート メッセージ アドインを使用して迷惑メールとしてフラグが設定されたメッセージが多く報告されている場合、組織のセキュリティ チームはスパム対策ポリシーを調整する必要があります。 [](configure-your-spam-filter-policies.md)</span><span class="sxs-lookup"><span data-stu-id="b4b39-112">For example, if people are reporting a lot of messages that were flagged as junk mail as Not Junk by using the Report Message add-in, your organization's security team might need to adjust [anti-spam policies](configure-your-spam-filter-policies.md).</span></span>

<span data-ttu-id="b4b39-113">[レポート メッセージ] アドインまたは [レポート フィッシング] アドインをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="b4b39-113">You can install either the Report Message or Report Phishing add-in.</span></span> <span data-ttu-id="b4b39-114">ユーザーにフィッシング メッセージのみを報告する場合は、組織にレポートフィッシング アドインを展開します。</span><span class="sxs-lookup"><span data-stu-id="b4b39-114">If you want your users to report only phishing messages, deploy the Report Phishing add-in in your organization.</span></span> <span data-ttu-id="b4b39-115">詳細については、「レポートフィッシング [アドインを有効にする」を参照してください](enable-the-report-phish-add-in.md)。</span><span class="sxs-lookup"><span data-stu-id="b4b39-115">For more information, see [Enable the Report Phishing add-in](enable-the-report-phish-add-in.md).</span></span>

<span data-ttu-id="b4b39-116">レポート メッセージ アドインには、スパム メッセージとフィッシング メッセージの両方を報告するオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="b4b39-116">The Report Message add-in provides the option to report both spam and phishing messages.</span></span> <span data-ttu-id="b4b39-117">管理者は、組織のレポート メッセージ アドインを有効にし、個々のユーザーが自分でインストールできます。</span><span class="sxs-lookup"><span data-stu-id="b4b39-117">Admins can enable the Report Message add-in for the organization, and individual users can install it for themselves.</span></span>

<span data-ttu-id="b4b39-118">個々のユーザーの場合は、自分でレポート メッセージ [アドインを有効にできます](#get-the-report-message-add-in-for-yourself)。</span><span class="sxs-lookup"><span data-stu-id="b4b39-118">If you're an individual user, you can [enable the Report Message add-in for yourself](#get-the-report-message-add-in-for-yourself).</span></span>

<span data-ttu-id="b4b39-119">グローバル管理者または Exchange Online 管理者で、Exchange が OAuth 認証を使用するように構成されている場合は、組織でレポート メッセージ アドイン [を有効にできます](#get-and-enable-the-report-message-add-in-for-your-organization)。</span><span class="sxs-lookup"><span data-stu-id="b4b39-119">If you're a global administrator or an Exchange Online administrator, and Exchange is configured to use OAuth authentication, you can [enable the Report Message add-in for your organization](#get-and-enable-the-report-message-add-in-for-your-organization).</span></span> <span data-ttu-id="b4b39-120">[レポート メッセージ] Add-Inは、集中展開 [を通じて利用できます](../../admin/manage/centralized-deployment-of-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="b4b39-120">The Report Message Add-In is now available through [Centralized Deployment](../../admin/manage/centralized-deployment-of-add-ins.md).</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="b4b39-121">始める前に把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="b4b39-121">What do you need to know before you begin?</span></span>

- <span data-ttu-id="b4b39-122">レポート メッセージ アドインは、ほとんどの Microsoft 365 サブスクリプションと次の製品で動作します。</span><span class="sxs-lookup"><span data-stu-id="b4b39-122">The Report Message add-in works with most Microsoft 365 subscriptions and the following products:</span></span>

  - <span data-ttu-id="b4b39-123">Outlook on the web</span><span class="sxs-lookup"><span data-stu-id="b4b39-123">Outlook on the web</span></span>
  - <span data-ttu-id="b4b39-124">Outlook 2013 SP1 以降</span><span class="sxs-lookup"><span data-stu-id="b4b39-124">Outlook 2013 SP1 or later</span></span>
  - <span data-ttu-id="b4b39-125">Outlook 2016 for Mac</span><span class="sxs-lookup"><span data-stu-id="b4b39-125">Outlook 2016 for Mac</span></span>
  - <span data-ttu-id="b4b39-126">エンタープライズ向け Microsoft 365 アプリに含まれる Outlook</span><span class="sxs-lookup"><span data-stu-id="b4b39-126">Outlook included with Microsoft 365 apps for Enterprise</span></span>
  - <span data-ttu-id="b4b39-127">iOS と Android 用 Outlook アプリ</span><span class="sxs-lookup"><span data-stu-id="b4b39-127">Outlook app for iOS and Android</span></span>

- <span data-ttu-id="b4b39-128">レポート メッセージ アドインは、オンプレミスの Exchange 組織の共有メールボックスまたはメールボックスでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="b4b39-128">The Report Message add-in is not available for shared mailboxes or mailboxes in on-premises Exchange organizations.</span></span>

- <span data-ttu-id="b4b39-129">指定したメールボックスにコピーまたはリダイレクトするレポート メッセージを構成できます。</span><span class="sxs-lookup"><span data-stu-id="b4b39-129">You can configure reported messages to be copied or redirected to a mailbox that you specify.</span></span> <span data-ttu-id="b4b39-130">詳細については、「ユーザー申請 [ポリシー」を参照してください](user-submission.md)。</span><span class="sxs-lookup"><span data-stu-id="b4b39-130">For more information, see [User submissions policies](user-submission.md).</span></span>

- <span data-ttu-id="b4b39-131">既存の Web ブラウザーは、レポート メッセージ アドインで動作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4b39-131">Your existing web browser should work with the Report Message add-in.</span></span> <span data-ttu-id="b4b39-132">ただし、アドインが使用できないか、期待通り動作していない場合は、別のブラウザーを試してください。</span><span class="sxs-lookup"><span data-stu-id="b4b39-132">But, if you notice the add-in is not available or not working as expected, try a different browser.</span></span>

- <span data-ttu-id="b4b39-133">組織のインストールでは、OAuth 認証を使用するように組織を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4b39-133">For organizational installs, the organization needs to be configured to use OAuth authentication.</span></span> <span data-ttu-id="b4b39-134">詳細については、「アドインの集中展開が組織で機能するかどうかを判断する」 [を参照してください](../../admin/manage/centralized-deployment-of-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="b4b39-134">For more information, see [Determine if Centralized Deployment of add-ins works for your organization](../../admin/manage/centralized-deployment-of-add-ins.md).</span></span>

- <span data-ttu-id="b4b39-135">管理者は、グローバル管理者役割グループのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4b39-135">Admins need to be a member of the Global admins role group.</span></span> <span data-ttu-id="b4b39-136">詳細については、「[セキュリティ/コンプライアンス センターのアクセス許可](permissions-in-the-security-and-compliance-center.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4b39-136">For more information, see [Permissions in the Security & Compliance Center](permissions-in-the-security-and-compliance-center.md).</span></span>

## <a name="get-the-report-message-add-in-for-yourself"></a><span data-ttu-id="b4b39-137">自分でレポート メッセージ アドインを取得する</span><span class="sxs-lookup"><span data-stu-id="b4b39-137">Get the Report Message add-in for yourself</span></span>

1. <span data-ttu-id="b4b39-138">[Microsoft AppSource] に移動し <https://appsource.microsoft.com/marketplace/apps> 、レポート メッセージ アドインを検索します。</span><span class="sxs-lookup"><span data-stu-id="b4b39-138">Go to the Microsoft AppSource at <https://appsource.microsoft.com/marketplace/apps> and search for the Report Message add-in.</span></span> <span data-ttu-id="b4b39-139">レポート メッセージ アドインに直接移動するには、に移動します <https://appsource.microsoft.com/product/office/wa104381180> 。</span><span class="sxs-lookup"><span data-stu-id="b4b39-139">To go directly to the Report Message add-in, go to <https://appsource.microsoft.com/product/office/wa104381180>.</span></span>

2. <span data-ttu-id="b4b39-140">[今 **すぐ取得] をクリックします**。</span><span class="sxs-lookup"><span data-stu-id="b4b39-140">Click **GET IT NOW**.</span></span>

   ![レポート メッセージ - 今すぐ取得する](../../media/ReportMessageGETITNOW.png)

3. <span data-ttu-id="b4b39-142">表示されるダイアログで、使用条件とプライバシー ポリシーを確認し、[続行] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="b4b39-142">In the dialog that appears, review the terms of use and privacy policy, and then click **Continue**.</span></span>

4. <span data-ttu-id="b4b39-143">仕事用または学校用のアカウント (ビジネス用) または Microsoft アカウント (個人用) を使用してサインインします。</span><span class="sxs-lookup"><span data-stu-id="b4b39-143">Sign in using your work or school account (for business use) or your Microsoft account (for personal use).</span></span>

<span data-ttu-id="b4b39-144">アドインをインストールして有効にすると、次のアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4b39-144">After the add-in is installed and enabled, you'll see the following icons:</span></span>

- <span data-ttu-id="b4b39-145">Outlook では、アイコンは次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4b39-145">In Outlook, the icon looks like this:</span></span>

  ![Outlook のレポート メッセージ アドイン アイコン](../../media/OutlookReportMessageIcon.png)

- <span data-ttu-id="b4b39-147">Outlook on the web では、アイコンは次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4b39-147">In Outlook on the web, the icon looks like this:</span></span>

  ![Outlook on the web Report Message add-in icon](../../media/d9326d0b-1769-4bc2-ae58-51f0ebc69a17.png)

<span data-ttu-id="b4b39-149">アドインの使い方については、「レポート メッセージ アドインを使用 [する」を参照してください](https://support.microsoft.com/office/b5caa9f1-cdf3-4443-af8c-ff724ea719d2)。</span><span class="sxs-lookup"><span data-stu-id="b4b39-149">To learn how to use the add-in, see [Use the Report Message add-in](https://support.microsoft.com/office/b5caa9f1-cdf3-4443-af8c-ff724ea719d2).</span></span>

## <a name="get-and-enable-the-report-message-add-in-for-your-organization"></a><span data-ttu-id="b4b39-150">組織のレポート メッセージ アドインを取得して有効にする</span><span class="sxs-lookup"><span data-stu-id="b4b39-150">Get and enable the Report Message add-in for your organization</span></span>

> [!NOTE]
> <span data-ttu-id="b4b39-151">アドインが組織に表示するには、最大で 12 時間かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b4b39-151">It could take up to 12 hours for the add-in to appear in your organization.</span></span>

1. <span data-ttu-id="b4b39-152">Microsoft 365 管理センターで、[設定アドイン] ページの [アドイン] ページに移動し、[アドイン] ページが表示しない場合は、[統合アプリ] ページの上部にある [設定統合アプリ アドイン] リンクに移動します。 \>  <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns>   \>  \>  </span><span class="sxs-lookup"><span data-stu-id="b4b39-152">In the Microsoft 365 admin center, go to the go to the **Settings** \> **Add-ins** page at <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns>, If you don't see the **Add-in** Page, go to the **Settings** \> **Integrated apps** \> **Add-ins** link on the top of the **Integrated apps** page.</span></span>

2. <span data-ttu-id="b4b39-153">ページ **の上部にある [アドインの** 展開] を選択し、[次へ] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="b4b39-153">Select **Deploy Add-in** at the top of the page, and then select **Next**.</span></span>

   ![Microsoft 365 管理センターの [サービスとアドイン] ページ](../../media/ServicesAddInsPageNewM365AdminCenter.png)

3. <span data-ttu-id="b4b39-155">表示される **[新しいアドインの展開]** フライアウトで、情報を確認し、[次へ] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="b4b39-155">In the **Deploy a new add-in** flyout that appears, review the information, and then click **Next**.</span></span>

4. <span data-ttu-id="b4b39-156">次のページで、[ストアから **選択] をクリックします**。</span><span class="sxs-lookup"><span data-stu-id="b4b39-156">On the next page, click **Choose from the Store**.</span></span>

   ![新しいアドイン ページの展開](../../media/NewAddInScreen2.png)

5. <span data-ttu-id="b4b39-158">表示される **[アドインの選択] ページ** で、[検索]ボックスをクリックし、[レポート メッセージ] と入力し、[検索検索] アイコン **を** ![ クリックします ](../../media/search-icon.png) 。</span><span class="sxs-lookup"><span data-stu-id="b4b39-158">In the **Select add-in** page that appears, click in the **Search** box, enter **Report Message**, and then click **Search** ![Search icon](../../media/search-icon.png).</span></span> <span data-ttu-id="b4b39-159">結果の一覧で、[レポート メッセージ] **を探し、[** 追加] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="b4b39-159">In the list of results, find **Report Message** and then click **Add**.</span></span>

   ![アドインの検索結果を選択する](../../media/NewAddInScreen3.png)

6. <span data-ttu-id="b4b39-161">表示されるダイアログで、ライセンスとプライバシー情報を確認し、[続行] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="b4b39-161">In the dialog that appears, review the licensing and privacy information, and then click **Continue**.</span></span>

7. <span data-ttu-id="b4b39-162">表示される **[アドインの構成]** ページで、次の設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="b4b39-162">In the **Configure add-in** page that appears, configure the following settings:</span></span>

   - <span data-ttu-id="b4b39-163">**割り当てられたユーザー**: 次のいずれかの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="b4b39-163">**Assigned users**: Select one of the following values:</span></span>

     - <span data-ttu-id="b4b39-164">**すべてのユーザー** (既定)</span><span class="sxs-lookup"><span data-stu-id="b4b39-164">**Everyone** (default)</span></span>
     - <span data-ttu-id="b4b39-165">**特定のユーザー/グループ**</span><span class="sxs-lookup"><span data-stu-id="b4b39-165">**Specific users / groups**</span></span>
     - <span data-ttu-id="b4b39-166">**私だけです**</span><span class="sxs-lookup"><span data-stu-id="b4b39-166">**Just me**</span></span>

   - <span data-ttu-id="b4b39-167">**展開方法**: 次のいずれかの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="b4b39-167">**Deployment method**: Select one of the following values:</span></span>

     - <span data-ttu-id="b4b39-168">**固定 (既定)**: 指定したユーザーにアドインが自動的に展開され、削除できない。</span><span class="sxs-lookup"><span data-stu-id="b4b39-168">**Fixed (Default)**: The add-in is automatically deployed to the specified users and they can't remove it.</span></span>
     - <span data-ttu-id="b4b39-169">**利用可能**: ユーザーは、ホーム アドイン \> **の取得** 管理でアドイン \> **をインストールできます**。</span><span class="sxs-lookup"><span data-stu-id="b4b39-169">**Available**: Users can install the add-in at **Home** \> **Get add-ins** \> **Admin-managed**.</span></span>
     - <span data-ttu-id="b4b39-170">**オプション**: アドインは指定したユーザーに自動的に展開されますが、削除を選択できます。</span><span class="sxs-lookup"><span data-stu-id="b4b39-170">**Optional**: The add-in is automatically deployed to the specified users, but they can choose to remove it.</span></span>

   ![[アドインの構成] ページ](../../media/configure-add-in.png)

   <span data-ttu-id="b4b39-172">完了したら、[展開] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="b4b39-172">When you're finished, click **Deploy**.</span></span>

8. <span data-ttu-id="b4b39-173">表示される **[レポート メッセージの展開** ] ページに、進行状況レポートが表示され、その後にアドインが展開されたという確認が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4b39-173">In the **Deploy Report Message** page that appears, you'll see a progress report followed by a confirmation that the add-in was deployed.</span></span> <span data-ttu-id="b4b39-174">情報を読んだら、[次へ] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="b4b39-174">After you read the information, click **Next**.</span></span>

   ![[レポート メッセージの展開] ページ](../../media/deploy-report-message-page.png)

9. <span data-ttu-id="b4b39-176">表示される **[アドインのアナウンス] ページ** で、情報を確認し、[閉じる] を **クリックします**。</span><span class="sxs-lookup"><span data-stu-id="b4b39-176">On the **Announce add-in** page that appears, review the information, and then click **Close**.</span></span>

   ![[アドインのアナウンス] ページ](../../media/announce-add-in-page.png)

## <a name="learn-how-to-use-the-report-message-add-in"></a><span data-ttu-id="b4b39-178">レポート メッセージ アドインの使い方について</span><span class="sxs-lookup"><span data-stu-id="b4b39-178">Learn how to use the Report Message add-in</span></span>

<span data-ttu-id="b4b39-179">アドインが割り当てられているユーザーには、次のアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4b39-179">People who have the add-in assigned to them will see the following icons:</span></span>

- <span data-ttu-id="b4b39-180">Outlook では、アイコンは次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4b39-180">In Outlook, the icon looks like this:</span></span>

  ![Outlook の [レポート メッセージ アドイン] アイコン](../../media/OutlookReportMessageIcon.png)

- <span data-ttu-id="b4b39-182">Outlook on the web では、アイコンは次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4b39-182">In Outlook on the web, the icon looks like this:</span></span>

  ![Outlook on the Web Report Message Add-in icon](../../media/d9326d0b-1769-4bc2-ae58-51f0ebc69a17.png)

<span data-ttu-id="b4b39-184">レポート メッセージ アドインについてユーザーに通知する場合は、[レポート メッセージ アドインを使用する] へのリンク [を含める必要があります](https://support.microsoft.com/office/b5caa9f1-cdf3-4443-af8c-ff724ea719d2)。</span><span class="sxs-lookup"><span data-stu-id="b4b39-184">When you notify users about the Report Message add-in, include a link to [Use the Report Message add-in](https://support.microsoft.com/office/b5caa9f1-cdf3-4443-af8c-ff724ea719d2).</span></span>

## <a name="review-or-edit-settings-for-the-report-message-add-in"></a><span data-ttu-id="b4b39-185">レポート メッセージ アドインの設定を確認または編集する</span><span class="sxs-lookup"><span data-stu-id="b4b39-185">Review or edit settings for the Report Message add-in</span></span>

1. <span data-ttu-id="b4b39-186">Microsoft 365 管理センターで、[設定アドイン] ページの [アドイン] ページに移動し、[アドイン] ページが表示しない場合は、[統合アプリ] ページの上部にある [設定統合アプリ アドイン] リンクに移動します。 \>  <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns>   \>  \>  </span><span class="sxs-lookup"><span data-stu-id="b4b39-186">In the Microsoft 365 admin center, go to the go to the **Settings** \> **Add-ins** page at <https://admin.microsoft.com/AdminPortal/Home#/Settings/AddIns>, If you don't see the **Add-in** Page, go to the **Settings** \> **Integrated apps** \> **Add-ins** link on the top of the **Integrated apps** page.</span></span>

   ![新しい Microsoft 365 管理センターAdd-Insの [サービスとサービス] ページ](../../media/ServicesAddInsPageNewM365AdminCenter.png)

2. <span data-ttu-id="b4b39-188">レポート メッセージ アドインを **検索して** 選択します。</span><span class="sxs-lookup"><span data-stu-id="b4b39-188">Find and select the **Report Message** add-in.</span></span>

3. <span data-ttu-id="b4b39-189">表示される **[レポート メッセージの編集** ] フライアウトで、組織に合った設定を確認および編集します。</span><span class="sxs-lookup"><span data-stu-id="b4b39-189">In the **Edit Report Message** flyout that appears, review and edit settings as appropriate for your organization.</span></span> <span data-ttu-id="b4b39-190">完了したら、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b4b39-190">When you're finished, click **Save**.</span></span>

   ![レポート メッセージ アドインの設定](../../media/EditReportMessageAddIn.png)

## <a name="view-and-review-reported-messages"></a><span data-ttu-id="b4b39-192">報告されたメッセージの表示と確認</span><span class="sxs-lookup"><span data-stu-id="b4b39-192">View and review reported messages</span></span>

<span data-ttu-id="b4b39-193">ユーザーが Microsoft に報告するメッセージを確認するには、次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="b4b39-193">To review messages that users report to Microsoft, you have these options:</span></span>

- <span data-ttu-id="b4b39-194">管理者申請ポータルを使用します。</span><span class="sxs-lookup"><span data-stu-id="b4b39-194">Use the Admin Submissions portal.</span></span> <span data-ttu-id="b4b39-195">詳細については [、「Microsoft へのユーザー申請の表示」を参照してください](admin-submission.md#view-user-submissions-to-microsoft)。</span><span class="sxs-lookup"><span data-stu-id="b4b39-195">For more information, see [View user submissions to Microsoft](admin-submission.md#view-user-submissions-to-microsoft).</span></span>

- <span data-ttu-id="b4b39-196">報告されたメッセージのコピーを送信するメール フロー ルール (トランスポート ルールとも呼ばれる) を作成します。</span><span class="sxs-lookup"><span data-stu-id="b4b39-196">Create a mail flow rule (also known as a transport rule) to send copies of reported messages.</span></span> <span data-ttu-id="b4b39-197">手順については、「メール フロー ルールを使用して、ユーザーが Microsoft に報告している [情報を確認する」を参照してください](use-mail-flow-rules-to-see-what-your-users-are-reporting-to-microsoft.md)。</span><span class="sxs-lookup"><span data-stu-id="b4b39-197">For instructions, see [Use mail flow rules to see what your users are reporting to Microsoft](use-mail-flow-rules-to-see-what-your-users-are-reporting-to-microsoft.md).</span></span>