---
title: Microsoft Defender for Endpoint (Linux) でスキャンをスケジュールする方法
description: 組織の資産をよりよく保護するために、Microsoft Defender for Endpoint (Linux) の自動スキャン時間をスケジュールする方法について説明します。
keywords: microsoft、Defender、atp、Linux、スキャン、ウイルス対策、エンドポイント用 microsoft Defender (Linux)
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
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: d3f5d4c490e28c7985a0420fa5013a8e0f51a167
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "51065723"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-linux"></a><span data-ttu-id="e0b4e-104">Microsoft Defender for Endpoint (Linux) でのスキャンのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="e0b4e-104">Schedule scans with Microsoft Defender for Endpoint (Linux)</span></span>

<span data-ttu-id="e0b4e-105">Linux のスキャンを実行するには、「サポートされている [コマンド」を参照してください](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/linux-resources#supported-commands)。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-105">To run a scan for Linux, see [Supported Commands](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/linux-resources#supported-commands).</span></span>

<span data-ttu-id="e0b4e-106">Linux (および Unix) には、スケジュールされたタスクを実行できる **crontab** (タスク スケジューラと同様) というツールがあります。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-106">Linux (and Unix) have a tool called **crontab** (similar to Task Scheduler) to be able to run scheduled tasks.</span></span>

## <a name="pre-requisite"></a><span data-ttu-id="e0b4e-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="e0b4e-107">Pre-requisite</span></span>

> [!NOTE]
> <span data-ttu-id="e0b4e-108">すべてのタイム ゾーンの一覧を取得するには、次のコマンドを実行します。 `timedatectl list-timezones`</span><span class="sxs-lookup"><span data-stu-id="e0b4e-108">To get a list of all the time zones, run the following command: `timedatectl list-timezones`</span></span><br>
> <span data-ttu-id="e0b4e-109">タイム ゾーンの例:</span><span class="sxs-lookup"><span data-stu-id="e0b4e-109">Examples for timezones:</span></span>
> - `America/Los_Angeles`
> - `America/New_York`
> - `America/Chicago`
> - `America/Denver`

## <a name="to-set-the-cron-job"></a><span data-ttu-id="e0b4e-110">Cron ジョブを設定するには</span><span class="sxs-lookup"><span data-stu-id="e0b4e-110">To set the Cron job</span></span>
<span data-ttu-id="e0b4e-111">次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-111">Use the following commands:</span></span>

<span data-ttu-id="e0b4e-112">**crontab エントリをバックアップするには**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-112">**To backup crontab entries**</span></span>

`sudo crontab -l > /var/tmp/cron_backup_200919.dat`

> [!NOTE]
> <span data-ttu-id="e0b4e-113">Where 200919 == YRMMDD</span><span class="sxs-lookup"><span data-stu-id="e0b4e-113">Where 200919 == YRMMDD</span></span>

> [!TIP]
> <span data-ttu-id="e0b4e-114">編集または削除する前に、この操作を行います。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-114">Do this before you edit or remove.</span></span> <br>

<span data-ttu-id="e0b4e-115">crontab を編集し、新しいジョブをルート ユーザーとして追加するには、次の方法を実行します。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-115">To edit the crontab, and add a new job as a root user:</span></span> <br>
`sudo crontab -e`

> [!NOTE]
> <span data-ttu-id="e0b4e-116">既定のエディターは VIM です。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-116">The default editor is VIM.</span></span>

<span data-ttu-id="e0b4e-117">次の情報が表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-117">You might see:</span></span>

<span data-ttu-id="e0b4e-118">0 \* \* \* \* \* /etc/opt/microsoft/mdatp/logrorate.sh</span><span class="sxs-lookup"><span data-stu-id="e0b4e-118">0 \* \* \* \* /etc/opt/microsoft/mdatp/logrorate.sh</span></span>

<span data-ttu-id="e0b4e-119">"Insert" を押す</span><span class="sxs-lookup"><span data-stu-id="e0b4e-119">Press “Insert”</span></span>

<span data-ttu-id="e0b4e-120">次のエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-120">Add the following entries:</span></span>

<span data-ttu-id="e0b4e-121">CRON_TZ=America/Los_Angeles</span><span class="sxs-lookup"><span data-stu-id="e0b4e-121">CRON_TZ=America/Los_Angeles</span></span>

<span data-ttu-id="e0b4e-122">0 2 \* sat /bin/mdatp スキャン クイック > ~/mdatp_cron_job.log</span><span class="sxs-lookup"><span data-stu-id="e0b4e-122">0 2 \* \* sat /bin/mdatp scan quick > ~/mdatp_cron_job.log</span></span>

> [!NOTE]
><span data-ttu-id="e0b4e-123">この例では、00 分、2 時に設定しています。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-123">In this example, we have  set it to 00 minutes, 2 a.m.</span></span> <span data-ttu-id="e0b4e-124">(24 時間形式の時間)、月の任意の日、任意の月、土曜日。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-124">(hour in 24 hour format), any day of the month, any month, on Saturdays.</span></span> <span data-ttu-id="e0b4e-125">つまり、土曜日は 2:00 に実行されます。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-125">Meaning it will run Saturdays at 2:00 a.m.</span></span> <span data-ttu-id="e0b4e-126">太平洋 (UTC –8)。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-126">Pacific (UTC –8).</span></span>

<span data-ttu-id="e0b4e-127">"Esc" を押す</span><span class="sxs-lookup"><span data-stu-id="e0b4e-127">Press “Esc”</span></span>

<span data-ttu-id="e0b4e-128">二重引用符を付けずに":wq" と入力します。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-128">Type “:wq” without the double quotes.</span></span>

> [!NOTE]
> <span data-ttu-id="e0b4e-129">w == 書き込み、q == quit</span><span class="sxs-lookup"><span data-stu-id="e0b4e-129">w == write, q == quit</span></span>

<span data-ttu-id="e0b4e-130">cron ジョブを表示するには、 `sudo crontab -l`</span><span class="sxs-lookup"><span data-stu-id="e0b4e-130">To view your cron jobs, type `sudo crontab -l`</span></span>

:::image type="content" source="/microsoft-365/security/defender-endpoint/images/linux-mdatp-1" alt-text="linux mdatp":::

<span data-ttu-id="e0b4e-132">**cron ジョブの実行を調するには**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-132">**To inspect cron job runs**</span></span>

`sudo grep mdatp /var/log/cron`

<span data-ttu-id="e0b4e-133">**mdatp_cron_job.log を調するには**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-133">**To inspect the mdatp_cron_job.log**</span></span>

`sudo nano mdatp_cron_job.log`

## <a name="for-those-who-use-ansible-chef-or-puppet"></a><span data-ttu-id="e0b4e-134">Ansible、Chef、または Puppet を使用するユーザー向け</span><span class="sxs-lookup"><span data-stu-id="e0b4e-134">For those who use Ansible, Chef, or Puppet</span></span>

<span data-ttu-id="e0b4e-135">次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-135">Use the following commands:</span></span>
### <a name="to-set-cron-jobs-in-ansible"></a><span data-ttu-id="e0b4e-136">Ansible で cron ジョブを設定するには</span><span class="sxs-lookup"><span data-stu-id="e0b4e-136">To set cron jobs in Ansible</span></span>

`cron – Manage cron.d and crontab entries`

<span data-ttu-id="e0b4e-137">詳細については、「[https://docs.ansible.com/ansible/latest/modules/cron_module.html](https://docs.ansible.com/ansible/latest/modules/cron_module.html)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-137">See [https://docs.ansible.com/ansible/latest/modules/cron_module.html](https://docs.ansible.com/ansible/latest/modules/cron_module.html) for more information.</span></span>

### <a name="to-set-crontabs-in-chef"></a><span data-ttu-id="e0b4e-138">Chef で crontabs を設定するには</span><span class="sxs-lookup"><span data-stu-id="e0b4e-138">To set crontabs in Chef</span></span>
`cron resource`

<span data-ttu-id="e0b4e-139">詳細については、「[https://docs.chef.io/resources/cron/](https://docs.chef.io/resources/cron/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-139">See [https://docs.chef.io/resources/cron/](https://docs.chef.io/resources/cron/) for more information.</span></span>

### <a name="to-set-cron-jobs-in-puppet"></a><span data-ttu-id="e0b4e-140">Puppet で cron ジョブを設定するには</span><span class="sxs-lookup"><span data-stu-id="e0b4e-140">To set cron jobs in Puppet</span></span>
<span data-ttu-id="e0b4e-141">リソースの種類: cron</span><span class="sxs-lookup"><span data-stu-id="e0b4e-141">Resource Type: cron</span></span>

<span data-ttu-id="e0b4e-142">詳細については、「[https://puppet.com/docs/puppet/5.5/types/cron.html](https://puppet.com/docs/puppet/5.5/types/cron.html)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-142">See [https://puppet.com/docs/puppet/5.5/types/cron.html](https://puppet.com/docs/puppet/5.5/types/cron.html) for more information.</span></span>

<span data-ttu-id="e0b4e-143">Puppet による自動化: Cron ジョブとスケジュールされたタスク</span><span class="sxs-lookup"><span data-stu-id="e0b4e-143">Automating with Puppet: Cron jobs and scheduled tasks</span></span>

<span data-ttu-id="e0b4e-144">詳細については、「[https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/](https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-144">See [https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/](https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/) for more information.</span></span>

## <a name="additional-information"></a><span data-ttu-id="e0b4e-145">ページの先頭へ</span><span class="sxs-lookup"><span data-stu-id="e0b4e-145">Additional information</span></span>

<span data-ttu-id="e0b4e-146">**crontab のヘルプを表示するには**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-146">**To get help with crontab**</span></span>

`man crontab`

<span data-ttu-id="e0b4e-147">**現在のユーザーの crontab ファイルの一覧を取得するには**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-147">**To get a list of crontab file of the current user**</span></span>

`crontab -l`

<span data-ttu-id="e0b4e-148">**別のユーザーの crontab ファイルの一覧を取得するには**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-148">**To get a list of crontab file of another user**</span></span>

`crontab -u username -l`

<span data-ttu-id="e0b4e-149">**crontab エントリをバックアップするには**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-149">**To backup crontab entries**</span></span>

`crontab -l > /var/tmp/cron_backup.dat`

> [!TIP]
> <span data-ttu-id="e0b4e-150">編集または削除する前に、この操作を行います。</span><span class="sxs-lookup"><span data-stu-id="e0b4e-150">Do this before you edit or remove.</span></span> <br>

<span data-ttu-id="e0b4e-151">**crontab エントリを復元するには**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-151">**To restore crontab entries**</span></span>

`crontab /var/tmp/cron_backup.dat`

<span data-ttu-id="e0b4e-152">**crontab を編集し、新しいジョブをルート ユーザーとして追加するには**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-152">**To edit the crontab and add a new job as a root user**</span></span>

`sudo crontab -e`

<span data-ttu-id="e0b4e-153">**crontab を編集して新しいジョブを追加するには**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-153">**To edit the crontab and add a new job**</span></span>

`crontab -e`

<span data-ttu-id="e0b4e-154">**他のユーザーの crontab エントリを編集するには**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-154">**To edit other user’s crontab entries**</span></span>

`crontab -u username -e`

<span data-ttu-id="e0b4e-155">**すべての crontab エントリを削除するには**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-155">**To remove all crontab entries**</span></span>

`crontab -r`

<span data-ttu-id="e0b4e-156">**他のユーザーの crontab エントリを削除するには**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-156">**To remove other user’s crontab entries**</span></span>

`crontab -u username -r`

<span data-ttu-id="e0b4e-157">**説明**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-157">**Explanation**</span></span>

<span data-ttu-id="e0b4e-158">+—————- 分 (値: 0 ~ 59) (特殊文字: 、 – \* /)</span><span class="sxs-lookup"><span data-stu-id="e0b4e-158">+—————- minute (values: 0 – 59) (special characters: , – \* /)</span></span>  <br>
<span data-ttu-id="e0b4e-159">|+————-時間 (値: 0 ~ 23) (特殊文字: 、 – \* /)</span><span class="sxs-lookup"><span data-stu-id="e0b4e-159">| +————- hour (values: 0 – 23) (special characters: , – \* /)</span></span> <br>
<span data-ttu-id="e0b4e-160">| |+———-日 (値: 1 ~ 31) (特殊文字: , – \* / L W C)</span><span class="sxs-lookup"><span data-stu-id="e0b4e-160">| | +———- day of month (values: 1 – 31) (special characters: , – \* / L W C)</span></span>  <br>
<span data-ttu-id="e0b4e-161">| | |+——-月 (値: 1 ~ 12) (特殊文字: ,- \* / )</span><span class="sxs-lookup"><span data-stu-id="e0b4e-161">| | | +——- month (values: 1 – 12) (special characters: ,- \* / )</span></span>  <br>
<span data-ttu-id="e0b4e-162">| | | |+—- 日 (値: 0 ~ 6) (日曜日=0 または 7) (特殊文字: , – \* / L W C)</span><span class="sxs-lookup"><span data-stu-id="e0b4e-162">| | | | +—- day of week (values: 0 – 6) (Sunday=0 or 7) (special characters: , – \* / L W C)</span></span> <br>
<span data-ttu-id="e0b4e-163">| | | | |\*\*\*\*\*コマンドを実行する</span><span class="sxs-lookup"><span data-stu-id="e0b4e-163">| | | | |\*\*\*\*\*command to be executed</span></span>

