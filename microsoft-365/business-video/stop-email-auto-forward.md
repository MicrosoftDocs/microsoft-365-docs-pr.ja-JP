---
title: メールの自動転送を停止する
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: 独自の情報の盗難を回避するためにメール フロー ルールを作成して、電子メールの自動転送を停止する方法について説明します。
ms.openlocfilehash: 82e4c80b0edc501889e0fc4dc28f1ec1ad703568
ms.sourcegitcommit: a05f61a291eb4595fa9313757a3815b7f217681d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2021
ms.locfileid: "52706476"
---
# <a name="stop-email-auto-forward"></a><span data-ttu-id="73727-103">電子メールの自動転送を停止する</span><span class="sxs-lookup"><span data-stu-id="73727-103">Stop email auto-forward</span></span>

## <a name="watch-stop-auto-forwarding-emails"></a><span data-ttu-id="73727-104">ウォッチ: 自動転送メールを停止する</span><span class="sxs-lookup"><span data-stu-id="73727-104">Watch: Stop auto-forwarding emails</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2W6kS?autoplay=false]

<span data-ttu-id="73727-105">ハッカーがユーザーのメールボックスにアクセスすると、ユーザーの電子メールを外部アドレスに自動転送し、専有情報を盗む可能性があります。</span><span class="sxs-lookup"><span data-stu-id="73727-105">If a hacker gains access to a user's mailbox, they can auto-forward the user's email to an outside address and steal proprietary information.</span></span> <span data-ttu-id="73727-106">これを停止するには、メール フロー ルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="73727-106">You can stop this by creating a mail flow rule.</span></span>

## <a name="try-it"></a><span data-ttu-id="73727-107">お試しください!</span><span class="sxs-lookup"><span data-stu-id="73727-107">Try it!</span></span>

1. <span data-ttu-id="73727-108">管理センター Microsoft 365 、[メール フロー] Exchangeを選択し、[ルール] タブでプラス記号を選択し、[新しいルールの作成]**を選択します**。 </span><span class="sxs-lookup"><span data-stu-id="73727-108">From the Microsoft 365 admin center, select **Exchange**, **mail flow**, and on the **rules** tab, select the plus sign and choose **create a new rule**.</span></span>
1. <span data-ttu-id="73727-109">[その **他のオプション] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="73727-109">Select **More options**.</span></span> <span data-ttu-id="73727-110">新しいルールの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="73727-110">Name your new rule.</span></span>
1. <span data-ttu-id="73727-111">次に、ドロップダウンを開いて、送信者を選択し、外部内部である場合にこのルール **を適用します**。</span><span class="sxs-lookup"><span data-stu-id="73727-111">Then open the drop-down for **apply this rule if**, select **the sender**, and then **is external internal**.</span></span>
1. <span data-ttu-id="73727-112">[組織内 **] を選択し\*\*\*\*、[OK] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="73727-112">Select **Inside the organization**, and then **OK**.</span></span>
1. <span data-ttu-id="73727-113">[ **条件の追加]** を選択し、ドロップダウンを開き、[メッセージのプロパティ] を **選択して**、メッセージ **の種類を指定します**。</span><span class="sxs-lookup"><span data-stu-id="73727-113">Choose **add condition**, open the drop-down, select **The message properties**, then **include the message type**.</span></span>
1. <span data-ttu-id="73727-114">[メッセージの **種類の選択] ドロップダウン** を開き、[**自動転送] を選択し\*\*\*\*、[OK] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="73727-114">Open the **select message type** drop-down, choose **Auto-forward**, then **OK**.</span></span>
1. <span data-ttu-id="73727-115">[次の **操作を行う** ] ドロップダウンを開き、[メッセージをブロックする] **を選択し**、メッセージを拒否 **して説明を含める**。</span><span class="sxs-lookup"><span data-stu-id="73727-115">Open the **Do the following** drop-down, select **Block the message**, then **reject the message and include an explanation**.</span></span>
1. <span data-ttu-id="73727-116">説明のメッセージ テキストを入力し **、[OK] を選択します**。</span><span class="sxs-lookup"><span data-stu-id="73727-116">Enter the message text for your explanation, then select **OK**.</span></span>
1. <span data-ttu-id="73727-117">一番下までスクロールし、[保存] を **選択します**。</span><span class="sxs-lookup"><span data-stu-id="73727-117">Scroll to the bottom and select **Save**.</span></span>

    <span data-ttu-id="73727-118">ルールが作成され、ハッカーはメッセージを自動転送できなくなりました。</span><span class="sxs-lookup"><span data-stu-id="73727-118">Your rule has been created, and hackers will no longer be able to auto-forward messages.</span></span>

## <a name="related-content"></a><span data-ttu-id="73727-119">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="73727-119">Related content</span></span>

<span data-ttu-id="73727-120">[ユーザーに別のメール エイリアスを追加する](../admin/email/add-another-email-alias-for-a-user.md) (記事)</span><span class="sxs-lookup"><span data-stu-id="73727-120">[Add another email alias for a user](../admin/email/add-another-email-alias-for-a-user.md) (article)\</span></span>
<span data-ttu-id="73727-121">[Microsoft 365 でメールの転送を構成する](../admin/email/configure-email-forwarding.md) (記事)</span><span class="sxs-lookup"><span data-stu-id="73727-121">[Configure email forwarding in Microsoft 365](../admin/email/configure-email-forwarding.md) (article)\</span></span>
<span data-ttu-id="73727-122">[ビジネス管理者向けメール配信の問題Office 365検索して修正](/exchange/troubleshoot/email-delivery/email-delivery-issues)する (記事)</span><span class="sxs-lookup"><span data-stu-id="73727-122">[Find and fix email delivery issues as an Office 365 for business admin](/exchange/troubleshoot/email-delivery/email-delivery-issues) (article)</span></span>