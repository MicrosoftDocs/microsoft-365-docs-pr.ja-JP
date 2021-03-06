---
title: Microsoft Defender for Endpoint (Linux) の更新プログラムをスケジュールする方法
description: 組織の資産を保護するために Microsoft Defender for Endpoint (Linux) の更新プログラムをスケジュールする方法について説明します。
keywords: microsoft、 defender、 Microsoft Defender for Endpoint, Linux, スキャン, ウイルス対策, microsoft Defender for endpoint (linux)
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
ms.openlocfilehash: 7ebb37e80cae0e9dd70d01600c47bd1459c122c3
ms.sourcegitcommit: 6749455c52b0f98a92f6fffbc2bb86caf3538bd8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2021
ms.locfileid: "53194903"
---
# <a name="schedule-an-update-of-the-microsoft-defender-for-endpoint-linux"></a>Microsoft Defender for Endpoint (Linux) の更新をスケジュールする

Microsoft Defender for Endpoint on Linux で更新プログラムを実行するには [、「Deploy updates for Endpoint on Linux」を参照してください](/microsoft-365/security/defender-endpoint/linux-updates)。

Linux (および Unix) には、スケジュールされたタスクを実行できる **crontab** (タスク スケジューラと同様) というツールがあります。

## <a name="pre-requisite"></a>前提条件

> [!NOTE]
> すべてのタイム ゾーンの一覧を取得するには、次のコマンドを実行します。 `timedatectl list-timezones`<br>
> タイム ゾーンの例: <br>
> - `America/Los_Angeles`
> - `America/New_York`
> - `America/Chicago`
> - `America/Denver`

## <a name="to-set-the-cron-job"></a>Cron ジョブを設定するには
次のコマンドを使用します。

**crontab エントリをバックアップするには**

`sudo crontab -l > /var/tmp/cron_backup_201118.dat`

> [!NOTE]
> Where 201118 == YYMMDD

> [!TIP]
> 編集または削除する前に、この操作を行います。 <br>

crontab を編集し、新しいジョブをルート ユーザーとして追加するには、次の方法を実行します。 <br>
`sudo crontab -e`

> [!NOTE]
> 既定のエディターは VIM です。

次の情報が表示される場合があります。

0****/etc/opt/microsoft/mdatp/logrorate.sh

And

02**sat /bin/mdatp スキャンクイック>~/mdatp_cron_job.log

「Microsoft [Defender for Endpoint (Linux) でのスキャンのスケジュール設定」を参照してください。](linux-schedule-scan-atp.md)

"Insert" を押す

次のエントリを追加します。

CRON_TZ=America/Los_Angeles

> #<a name="rhel-and-variants-centos-and-oracle-linux"></a>!RHEL とバリアント (CentOS および Oracle Linux)

`06**sun[$(date +\%d) -le 15] sudo yum update mdatp>>~/mdatp_cron_job.log`

> #<a name="sles-and-variants"></a>!SLES とバリアント

`06**sun[$(date +\%d) -le 15] sudo zypper update mdatp>>~/mdatp_cron_job.log`

> #<a name="ubuntu-and-debian-systems"></a>!Ubuntu システムと Debian システム

`0 6 * * sun [$(date +\%d) -le 15] sudo apt-get install --only-upgrade mdatp>>~/mdatp_cron_job.log`

> [!NOTE]
> 上記の例では、00 分、24 時間形式の 6.m.(hour)、月の任意の日、任意の月、日曜日に設定しています。[$(date + \% d) -le 15] == 15 日 (3 週目) 以下の場合は実行されません。 つまり、月の第 3 日曜日(7) ごとに 6:00 に実行されます。 太平洋 (UTC -8)。

"Esc" を押す

二重引用符を付け、":wq" と入力します。

> [!NOTE]
> w == 書き込み、q == quit

cron ジョブを表示するには、 `sudo crontab -l`

:::image type="content" source="images/update-MDE-linux-4634577.jpg" alt-text="Linux 上のエンドポイントの Defender を更新する":::

cron ジョブの実行を検査するには、次のコマンドを実行します。 `sudo grep mdatp /var/log/cron`

mdatp_cron_job.log を調するには `sudo nano mdatp_cron_job.log`

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>Ansible、Chef、または Puppet を使用するユーザー向け

次のコマンドを使用します。
### <a name="to-set-cron-jobs-in-ansible"></a>Ansible で cron ジョブを設定するには

`cron – Manage cron.d and crontab entries`

詳細については、「[https://docs.ansible.com/ansible/latest/modules/cron_module.html](https://docs.ansible.com/ansible/latest/modules/cron_module.html)」を参照してください。

### <a name="to-set-crontabs-in-chef"></a>Chef で crontabs を設定するには
`cron resource`

詳細については、「[https://docs.chef.io/resources/cron/](https://docs.chef.io/resources/cron/)」を参照してください。

### <a name="to-set-cron-jobs-in-puppet"></a>Puppet で cron ジョブを設定するには
リソースの種類: cron

詳細については、「[https://puppet.com/docs/puppet/5.5/types/cron.html](https://puppet.com/docs/puppet/5.5/types/cron.html)」を参照してください。

Puppet による自動化: Cron ジョブとスケジュールされたタスク

詳細については、「[https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/](https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/)」を参照してください。

## <a name="additional-information"></a>追加情報

**crontab のヘルプを表示するには**

`man crontab`

**現在のユーザーの crontab ファイルの一覧を取得するには**

`crontab -l`

**別のユーザーの crontab ファイルの一覧を取得するには**

`crontab -u username -l`

**crontab エントリをバックアップするには**

`crontab -l > /var/tmp/cron_backup.dat`

> [!TIP]
> 編集または削除する前に、この操作を行います。 <br>

**crontab エントリを復元するには**

`crontab /var/tmp/cron_backup.dat`

**crontab を編集し、新しいジョブをルート ユーザーとして追加するには**

`sudo crontab -e`

**crontab を編集して新しいジョブを追加するには**

`crontab -e`

**他のユーザーの crontab エントリを編集するには**

`crontab -u username -e`

**すべての crontab エントリを削除するには**

`crontab -r`

**他のユーザーの crontab エントリを削除するには**

`crontab -u username -r`

**説明**

<pre>
+—————- minute (values: 0 – 59) (special characters: , – * /)  <br>
| +————- hour (values: 0 – 23) (special characters: , – * /) <br>
| | +———- day of month (values: 1 – 31) (special characters: , – * / L W C)  <br>
| | | +——- month (values: 1 – 12) (special characters: ,- * / )  <br>
| | | | +—- day of week (values: 0 – 6) (Sunday=0 or 7) (special characters: , – * / L W C) <br>
| | | | |*****command to be executed
</pre>

