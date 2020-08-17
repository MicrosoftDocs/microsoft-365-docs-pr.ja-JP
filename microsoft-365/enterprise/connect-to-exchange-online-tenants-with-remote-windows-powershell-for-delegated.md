---
title: DAP パートナー用のリモート Windows PowerShell で Exchange Online テナントに接続する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: '概要: リモート Windows PowerShell で DelegatedOrg 値を使用して、Exchange Online に接続します。'
ms.openlocfilehash: 1351a6a6d19fac408b673796c1179bca0ede9c9f
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46691975"
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="9d5b6-103">委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する</span><span class="sxs-lookup"><span data-stu-id="9d5b6-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="9d5b6-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="9d5b6-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9d5b6-p101">このトピックの手順は、委任アクセス許可 (DAP) パートナー専用です。DAP パートナーでない場合は、このトピックの手順を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-p101">The procedures in this topic are only for Delegated Access Permission (DAP) partners. If you aren't a DAP partner, don't use the procedures in this topic.</span></span> 
  
<span data-ttu-id="9d5b6-107">DAP パートナーとは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-107">DAP partners are Syndication and Cloud Solution Providers (CSP) partners.</span></span> <span data-ttu-id="9d5b6-108">他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-108">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="9d5b6-109">それらのパートナーは、顧客に提供するサービスにサブスクリプションをバンドルします。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-109">They bundle subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="9d5b6-110">お客様は、Microsoft 365 カスタマーテナンシーに対して (AOBO) アクセス許可を自動的に付与されたパートナーテナントを所有しており、すべての顧客テナンシーの管理とレポートを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-110">They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Microsoft 365 customer tenancies so they can administer and report on all of their customer tenancies.</span></span>

<span data-ttu-id="9d5b6-111">DAP パートナーは、Exchange Online PowerShell を使用して、ユーザーの Exchange Online の設定を管理したり、Microsoft 365 レポートをコマンドラインから取得したりできます。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-111">DAP partners can use Exchange Online PowerShell to manage customer Exchange Online settings and get Microsoft 365 reports from the command line.</span></span> <span data-ttu-id="9d5b6-112">ローカル コンピューター上で Windows PowerShell を使用して Exchange Online に対するリモート PowerShell セッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-112">You use Windows PowerShell on your local computer to create a remote PowerShell session to Exchange Online.</span></span> <span data-ttu-id="9d5b6-113">これは、資格情報を入力し、必要な接続設定を指定してから、Exchange Online コマンドレットをローカルの Windows PowerShell セッションにインポートして使用できるようにする、簡単な3段階のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-113">It's a simple three-step process where you enter your credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>

> [!NOTE]
> <span data-ttu-id="9d5b6-p104">DAP パートナーは、「[多要素認証を使用して Exchange Online PowerShell に接続する](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)」の手順を使用して Exchange Online PowerShell に接続することはできません。MFA と Exchange Online リモート PowerShell モジュールは、委任された認証では機能しません。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-p104">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell. MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="9d5b6-116">はじめに把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="9d5b6-116">What do you need to know before you begin?</span></span>

- <span data-ttu-id="9d5b6-117">予想所要時間 : 5 分</span><span class="sxs-lookup"><span data-stu-id="9d5b6-117">Estimated time to complete: 5 minutes</span></span>

- <span data-ttu-id="9d5b6-118">次の Windows のバージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-118">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="9d5b6-119">Windows 10</span><span class="sxs-lookup"><span data-stu-id="9d5b6-119">Windows 10</span></span>

  - <span data-ttu-id="9d5b6-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="9d5b6-120">Windows 8.1</span></span>

  - <span data-ttu-id="9d5b6-121">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="9d5b6-121">Windows Server 2016</span></span>

  - <span data-ttu-id="9d5b6-122">Windows Server 2012 または Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="9d5b6-122">Windows Server 2012 or Windows Server 2012 R2</span></span>

  - <span data-ttu-id="9d5b6-123">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="9d5b6-123">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span></span>

  - <span data-ttu-id="9d5b6-124">Windows Server 2008 R2 SP1<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="9d5b6-124">Windows Server 2008 R2 SP1<sup>\*</sup></span></span>

    <span data-ttu-id="9d5b6-p105"><sup>\*</sup> 以前のバージョンの Windows の場合は、Microsoft.NET Framework 4.5 以降をインストールしてから、更新バージョンの Windows Management Framework (3.0、4.0、5.1 のいずれか 1 つ) をインストールする必要があります。詳細については、「[.NET Framework のインストール](https://go.microsoft.com/fwlink/p/?LinkId=257868)」、「[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)」、「[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)」、「[Windows Management Framework 5.1](https://aka.ms/wmf5download)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-p105"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one). For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span></span>

- <span data-ttu-id="9d5b6-p106">スクリプトを実行するように Windows PowerShell を構成する必要があります。既定では、そのように構成されていないため、接続を試行すると、次に示すエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-p106">Windows PowerShell needs to be configured to run scripts, and by default, it isn't. You'll get the following error when you try to connect:</span></span>

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  <span data-ttu-id="9d5b6-129">インターネットからダウンロードしたすべての PowerShell スクリプトが信頼された発行元によって署名されていることを要求するには、管理者特権の Windows PowerShell ウィンドウ (**[管理者として実行]** を選択したときに開く Windows PowerShell ウィンドウ) で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-129">To require all PowerShell scripts that you download from the internet are signed by a trusted publisher, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you open by selecting **Run as administrator**):</span></span>

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  <span data-ttu-id="9d5b6-130">この設定は、コンピューターで一度だけ構成すれば、接続ごとに行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-130">You need to configure this setting only once on your computer, not every time you connect.</span></span>

- <span data-ttu-id="9d5b6-131">このトピックの手順に適用されるキーボード ショートカットについては、「[Exchange 管理センターのキーボード ショートカット](https://go.microsoft.com/fwlink/p/?LinkId=534017)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-131">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>

## <a name="connect-to-exchange-online-for-customer-organizations"></a><span data-ttu-id="9d5b6-132">顧客の組織の Exchange Online に接続する</span><span class="sxs-lookup"><span data-stu-id="9d5b6-132">Connect to Exchange Online for customer organizations</span></span>

1. <span data-ttu-id="9d5b6-133">ローカル コンピューターで、Windows PowerShell を開き、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-133">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```

    <span data-ttu-id="9d5b6-134">**[Windows PowerShell 資格情報の要求]** ダイアログ ボックスで、DAP 管理者のユーザー名とパスワードを入力してから **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-134">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="9d5b6-135">_\<customer tenant domain name\>_ を接続先のテナントドメインの名前に置き換えて、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-135">Replace _\<customer tenant domain name\>_ with the name of the tenant domain that you want to connect to, and run the following command:</span></span>
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    <span data-ttu-id="9d5b6-136">このコマンドの重要な手順は、レポート情報にアクセスする顧客を指定することです。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-136">The key step in this command is specifying which customer to access for the reporting information.</span></span> <span data-ttu-id="9d5b6-137">この操作は、  _Connectionuri_ パラメーターで行います。この場合、最初のドメイン名の FQDN をの値として指定し `?DelegatedOrg=` ます。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-137">You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value for `?DelegatedOrg=`.</span></span> <span data-ttu-id="9d5b6-138">この値は、接続先の正しい Exchange Online PowerShell エンドポイントを示します。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-138">This value indicates the correct Exchange Online PowerShell endpoint to connect to.</span></span> <span data-ttu-id="9d5b6-139">リモート PowerShell は、レポートが実行されるたびに、特定の顧客のコンテキストで、Microsoft 365 reporting に接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-139">Remote PowerShell must connect to Microsoft 365 reporting in the context of a specific customer each time a report is run.</span></span> <span data-ttu-id="9d5b6-140">Exchange Online の PowerShell に接続すると、これ以降のすべてのコマンドが顧客のコンテキストで実行されます。これにより、お客様に対して利用可能なすべてのレポートにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-140">After you connect to Exchange Online PowerShell, all subsequent commands are run in the context of the customer, which gives you access to all of the available reports for the customer.</span></span>
    
3. <span data-ttu-id="9d5b6-141">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-141">Run the following command.</span></span>
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> <span data-ttu-id="9d5b6-p108">1 つのアカウントで同時に実行できるセッションは 3 つに制限されています。完了した時点でリモート PowerShell セッションを切断してください。セッションを切断せずに Windows PowerShell ウィンドウを閉じると、使用可能なリモート PowerShell セッションがすべて消費される可能性があるため、セッションの有効期限が切れるまで待つ必要があります。リモート PowerShell セッションを切断するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-p108">There's a limit of three simultaneous sessions that can run under one account. Be sure to disconnect the remote PowerShell session when you're finished. If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire. To disconnect the remote PowerShell session, run the following command:</span></span>

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="9d5b6-146">正常な動作を確認する方法</span><span class="sxs-lookup"><span data-stu-id="9d5b6-146">How do you know this worked?</span></span>

<span data-ttu-id="9d5b6-p109">手順 3 の後に、Exchange Online コマンドレットがローカル Windows PowerShell セッションにインポートされます。その様子が進行状況バーに表示されます。何もエラーが表示されなければ、正常に接続されています。簡単に確かめるには、Exchange Online コマンドレット (**Get-Mailbox** など) を実行して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-p109">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar. If you don't receive any errors, you connected successfully. A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span></span>
  
<span data-ttu-id="9d5b6-150">エラーが表示された場合は、次の要件を確認します。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-150">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="9d5b6-p110">よく起きる問題がパスワードの入力ミスです。もう一度 3 つのステップを実行します。特に、ステップ 1 ではユーザー名とパスワードを慎重に入力します。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-p110">A common problem is an incorrect password. Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="9d5b6-p111">Exchange Online への接続に使うアカウントは、リモート PowerShell に対して有効になっている必要があります。詳しくは、「[Exchange Online でリモート PowerShell アクセスを管理する](https://go.microsoft.com/fwlink/p/?LinkId=534018)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-p111">The account you use to connect to Exchange Online must be enabled for remote PowerShell. For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="9d5b6-p112">ローカル コンピューターと Exchange Online の間に TCP ポート 80 トラフィックを開く必要があります。組織で厳格なインターネット アクセス ポリシーが使用されている場合は、開いている可能性がありますが、確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-p112">TCP port 80 traffic needs to be open between your local computer and Exchange Online. It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="9d5b6-157">Invoke-Command で直接コマンドレットを呼び出す</span><span class="sxs-lookup"><span data-stu-id="9d5b6-157">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="9d5b6-p113">PowerShell リモート セッション (手順 3) のインポートは、_すべての_ Exchange Online コマンドレットを取り入れるため、時間がかかる処理になります。これは、(たとえば、さまざまなテナントに対してレポートを実行したり一括変更したりするような) バッチ処理の際に問題になります。**Import-PSSession** を使用する代わりに、**Invoke-Command** で直接使用するコマンドレットを呼び出すことができます。たとえば、**Get-Milbox** コマンドレットを呼び出すには、手順 3 の `Import-PSSession $Session` コマンドの次の構文を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-p113">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets. This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants). As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**. For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="9d5b6-162">その他のレポート コマンドレット</span><span class="sxs-lookup"><span data-stu-id="9d5b6-162">More reporting cmdlets</span></span>

<span data-ttu-id="9d5b6-p114">このトピックで使用したコマンドレットは Windows PowerShell コマンドレットです。これらのコマンドレットの詳細については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d5b6-p114">The cmdlets that you used in this topic are Windows PowerShell cmdlets. For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="9d5b6-165">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="9d5b6-165">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="9d5b6-166">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="9d5b6-166">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="9d5b6-167">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="9d5b6-167">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="9d5b6-168">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="9d5b6-168">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="9d5b6-169">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="9d5b6-169">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    
