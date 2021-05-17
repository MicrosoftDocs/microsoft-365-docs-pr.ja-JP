---
title: Microsoft 365 への一括移行に PowerShell を使用する
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: PowerShell を使用してソース 電子メール システムからコンテンツを一度に移動する方法については、一度に一度に移行を実行して、移行元のメール システムMicrosoft 365。
ms.openlocfilehash: 6e59ac4d590208e0faed22e94cabe05601b17f18
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "51581060"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-microsoft-365"></a><span data-ttu-id="5588e-103">Microsoft 365 への一括移行に PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="5588e-103">Use PowerShell to perform a cutover migration to Microsoft 365</span></span>

<span data-ttu-id="5588e-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="5588e-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="5588e-105">カットオーバー移行を使用して、ユーザー メールボックスの内容をソース 電子メール システムMicrosoft 365一度に移行できます。</span><span class="sxs-lookup"><span data-stu-id="5588e-105">You can migrate the contents of user mailboxes from a source email system to Microsoft 365 all at once by using a cutover migration.</span></span> <span data-ttu-id="5588e-106">この記事では、Exchange Online PowerShell を使用した電子メールの一括移行の作業を順を追って説明します。</span><span class="sxs-lookup"><span data-stu-id="5588e-106">This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell.</span></span>

<span data-ttu-id="5588e-107">トピック「Microsoft 365 へのメールの一切の移行について知る必要がある」を参照[すると](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration)、移行プロセスの概要を確認できます。</span><span class="sxs-lookup"><span data-stu-id="5588e-107">By reviewing the topic, [What you need to know about a cutover email migration to Microsoft 365](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration), you can get an overview of the migration process.</span></span> <span data-ttu-id="5588e-108">記事の内容に満足いただけたら、段階的メール移行を使用して、あるメール システムから別のメール システムへのメールボックスの移行を開始してください。</span><span class="sxs-lookup"><span data-stu-id="5588e-108">When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>

> [!NOTE]
> <span data-ttu-id="5588e-109">また、一括移行を実行するには、Exchange 管理センターを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5588e-109">You can also use the Exchange admin center to perform a cutover migration.</span></span> <span data-ttu-id="5588e-110">「[メールからメールへの一切の移行を実行する」を参照Microsoft 365。](/Exchange/mailbox-migration/cutover-migration-to-office-365)</span><span class="sxs-lookup"><span data-stu-id="5588e-110">See [Perform a cutover migration of email to Microsoft 365](/Exchange/mailbox-migration/cutover-migration-to-office-365).</span></span>

## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="5588e-111">始める前に把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="5588e-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="5588e-112">このタスクの予想所要時間:移行バッチの作成に 2 ～ 5 分。</span><span class="sxs-lookup"><span data-stu-id="5588e-112">Estimated time to complete this task: 2-5 minutes to create a migration batch.</span></span> <span data-ttu-id="5588e-113">移行バッチ開始後の移行時間は、バッチ内のメールボックスの数、各メールボックスのサイズ、および使用可能なネットワーク容量によって異なります。</span><span class="sxs-lookup"><span data-stu-id="5588e-113">After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity.</span></span> <span data-ttu-id="5588e-114">メールボックスを移行する時間に影響を与えるその他の要因については、「移行パフォーマンス」をMicrosoft 365[を参照してください](/Exchange/mailbox-migration/office-365-migration-best-practices)。</span><span class="sxs-lookup"><span data-stu-id="5588e-114">For information about other factors that affect how long it takes to migrate mailboxes to Microsoft 365, see [Migration Performance](/Exchange/mailbox-migration/office-365-migration-best-practices).</span></span>

<span data-ttu-id="5588e-p105">この手順を実行する際には、あらかじめアクセス許可を割り当てる必要があります。必要なアクセス許可を確認するには、トピック「[受信者のアクセス許可](/exchange/recipients-permissions-exchange-2013-help)」内の表にある「移行」エントリを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5588e-p105">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](/exchange/recipients-permissions-exchange-2013-help) topic.</span></span>

<span data-ttu-id="5588e-p106">Exchange Online PowerShell コマンドレットを使用するには、サインインしてコマンドレットをローカルの Windows PowerShell セッションにインポートする必要があります。手順については、「[リモート PowerShell による Exchange への接続](/powershell/exchange/connect-to-exchange-online-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5588e-p106">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) for instructions.</span></span>

<span data-ttu-id="5588e-119">移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](/powershell/exchange/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5588e-119">For a full list of migration commands, see [Move and migration cmdlets](/powershell/exchange/).</span></span>

## <a name="migration-steps"></a><span data-ttu-id="5588e-120">移行の手順</span><span class="sxs-lookup"><span data-stu-id="5588e-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-cutover-migration"></a><span data-ttu-id="5588e-121">ステップ 1:一括移行を準備する</span><span class="sxs-lookup"><span data-stu-id="5588e-121">Step 1: Prepare for a cutover migration</span></span>
<span data-ttu-id="5588e-122"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="5588e-122"><a name="BK_Step1"> </a></span></span>

- <span data-ttu-id="5588e-123">**オンプレミスの組織をExchange組織の受け入れドメインMicrosoft 365します。**</span><span class="sxs-lookup"><span data-stu-id="5588e-123">**Add your on-premises Exchange organization as an accepted domain of your Microsoft 365 organization.**</span></span> <span data-ttu-id="5588e-124">移行サービスは、オンプレミスのメールボックスの SMTP アドレスを使用して、新しいメールボックスMicrosoft Online Servicesユーザー ID と電子メール アドレスMicrosoft 365します。</span><span class="sxs-lookup"><span data-stu-id="5588e-124">The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Microsoft 365 mailboxes.</span></span> <span data-ttu-id="5588e-125">移行は、Exchangeドメインが承認されたドメインまたは組織のプライマリ ドメインではない場合Microsoft 365されます。</span><span class="sxs-lookup"><span data-stu-id="5588e-125">Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Microsoft 365 organization.</span></span> <span data-ttu-id="5588e-126">詳細については、「ドメインを確認 [する」を参照してください](../admin/setup/add-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="5588e-126">For more information, see [Verify your domain](../admin/setup/add-domain.md).</span></span>

- <span data-ttu-id="5588e-p108">**社内 Exchange サーバーで Outlook Anywhere を構成する。** 電子メール移行サービスは、RPC over HTTP または Outlook Anywhere を使用して社内 Exchange サーバーに接続します。Exchange 2010、Exchange 2007、および Exchange 2003 で Outlook Anywhere をセットアップする方法については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5588e-p108">**Configure Outlook Anywhere on your on-premises Exchange server.** The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server. For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:</span></span>

  - <span data-ttu-id="5588e-130">「[Exchange 2010:Outlook Anywhere を有効にする](/previous-versions/office/exchange-server-2010/bb123542(v=exchg.141))」</span><span class="sxs-lookup"><span data-stu-id="5588e-130">[Exchange 2010: Enable Outlook Anywhere](/previous-versions/office/exchange-server-2010/bb123542(v=exchg.141))</span></span>

  - <span data-ttu-id="5588e-131">「[Exchange 2007:Outlook Anywhere を有効にする方法](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))」</span><span class="sxs-lookup"><span data-stu-id="5588e-131">[Exchange 2007: How to Enable Outlook Anywhere](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))</span></span>

  - <span data-ttu-id="5588e-132">「[Exchange 2003:RPC over HTTP の展開シナリオ](/previous-versions/tn-archive/bb124876(v=exchg.65))」</span><span class="sxs-lookup"><span data-stu-id="5588e-132">[Exchange 2003: Deployment Scenarios for RPC over HTTP](/previous-versions/tn-archive/bb124876(v=exchg.65))</span></span>

  - <span data-ttu-id="5588e-133">「[Exchange 2003 での Outlook Anywhere を構成する方法](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))」</span><span class="sxs-lookup"><span data-stu-id="5588e-133">[How to Configure Outlook Anywhere with Exchange 2003](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="5588e-p109">Outlook Anywhere の構成は、信頼された証明機関 (CA) により発行された証明書を使用して行う必要があります。自己署名入りの証明書では構成できません。詳細については、「[Outlook Anywhere のために SSL を構成する方法](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5588e-p109">Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA). It can't be configured with a self-signed certificate. For more information, see [How to Configure SSL for Outlook Anywhere](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).</span></span>

- <span data-ttu-id="5588e-p110">**Outlook Anywhere を使用して Exchange 組織に接続できることを確認する。** 次のいずれかの方法で、接続設定をテストしてください:</span><span class="sxs-lookup"><span data-stu-id="5588e-p110">**Verify that you can connect to your Exchange organization using Outlook Anywhere.** Try one of these methods to test your connection settings:</span></span>

  - <span data-ttu-id="5588e-139">企業ネットワークの外部から Microsoft Outlook を使用して、社内 Exchange メールボックスに接続します。</span><span class="sxs-lookup"><span data-stu-id="5588e-139">Use Microsoft Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>

  - <span data-ttu-id="5588e-p111">Microsoft [Exchange リモート接続アナライザー](https://www.testexchangeconnectivity.com/)を使用して接続設定をテストします。Outlook Anywhere (RPC over HTTP) または Outlook 自動検出テストを使用します。</span><span class="sxs-lookup"><span data-stu-id="5588e-p111">Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>

  - <span data-ttu-id="5588e-142">Exchange Online PowerShell で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="5588e-142">Run the following commands in Exchange Online PowerShell.</span></span>

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- <span data-ttu-id="5588e-143">**Exchange 組織のメールボックスへのアクセスに必要なアクセス許可を社内ユーザー アカウントに割り当てる。**</span><span class="sxs-lookup"><span data-stu-id="5588e-143">**Assign an on-premises user account the necessary permissions to access mailboxes in your Exchange organization.**</span></span> <span data-ttu-id="5588e-144">オンプレミスの Exchange 組織 (移行管理者とも呼ばれる) への接続に使用するオンプレミス ユーザー アカウントには、Microsoft 365 に移行するオンプレミス メールボックスにアクセスするために必要なアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="5588e-144">The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Microsoft 365.</span></span> <span data-ttu-id="5588e-145">このユーザー アカウントは、社内組織の移行エンドポイントを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5588e-145">This user account is used to create a migration endpoint to your on-premises organization.</span></span>

    <span data-ttu-id="5588e-p113">以下の一覧に、一括移行を使用してメールボックスを移行するために必要な管理者権限を示します。3 つの可能なオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="5588e-p113">The following list shows the administrative privileges required to migrate mailboxes using a cutover migration. There are three possible options.</span></span>

  - <span data-ttu-id="5588e-148">移行管理者は、社内組織の Active Directory の **Domain Admins** グループのメンバーである必要がある。</span><span class="sxs-lookup"><span data-stu-id="5588e-148">The migration administrator must be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>

    <span data-ttu-id="5588e-149">または</span><span class="sxs-lookup"><span data-stu-id="5588e-149">Or</span></span>

  - <span data-ttu-id="5588e-150">移行管理者は、各社内メールボックスへの **フル アクセス** のアクセス許可が割り当てられている必要がある。</span><span class="sxs-lookup"><span data-stu-id="5588e-150">The migration administrator must be assigned the **FullAccess** permission for each on-premises mailbox.</span></span>

    <span data-ttu-id="5588e-151">または</span><span class="sxs-lookup"><span data-stu-id="5588e-151">Or</span></span>

  - <span data-ttu-id="5588e-152">移行管理者は、ユーザーのメールボックスを格納する社内メールボックス データベースへの **受信者** アクセス許可が割り当てられている必要がある。</span><span class="sxs-lookup"><span data-stu-id="5588e-152">The migration administrator must be assigned the **Receive As** permission on the on-premises mailbox database that stores the user mailboxes.</span></span>

- <span data-ttu-id="5588e-p114">**ユニファイド メッセージングを無効にする。** 移行する社内メールボックスでユニファイド メッセージング (UM) が有効である場合、メールボックスを移行する前にメールボックスで UM を無効にする必要があります。移行が完了すると、メールボックスで UM を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="5588e-p114">**Disable Unified Messaging.** If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them. You can then enable UM on the mailboxes after the migration is complete.</span></span>

- <span data-ttu-id="5588e-156">**セキュリティ グループと代理人** メール移行サービスは、オンプレミスの Active Directory グループがセキュリティ グループであるかどうかを検出できないので、移行されたグループを Microsoft 365 でセキュリティ グループとしてプロビジョニングすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5588e-156">**Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Microsoft 365.</span></span> <span data-ttu-id="5588e-157">Microsoft 365 テナントにセキュリティ グループを設定する場合は、カットオーバー移行を開始する前に、まず Microsoft 365 テナントに空のメールが有効なセキュリティ グループをプロビジョニングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5588e-157">If you want to have security groups in your Microsoft 365 tenant, you must first provision an empty mail-enabled security group in your Microsoft 365 tenant before starting the cutover migration.</span></span> <span data-ttu-id="5588e-158">さらに、この移行方法では、メールボックス、メール ユーザー、メール連絡先、およびメールが有効なグループのみを移動します。</span><span class="sxs-lookup"><span data-stu-id="5588e-158">Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups.</span></span> <span data-ttu-id="5588e-159">Microsoft 365 に移行されていないユーザーなど、他の Active Directory オブジェクトがマネージャーとして割り当てられている場合、移行するオブジェクトに委任する場合は、移行する前にオブジェクトから削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5588e-159">If any other Active Directory object, such as user that is not migrated to Microsoft 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.</span></span>

### <a name="step-2-create-a-migration-endpoint"></a><span data-ttu-id="5588e-160">ステップ 2:移行エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="5588e-160">Step 2: Create a migration endpoint</span></span>
<span data-ttu-id="5588e-161"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="5588e-161"><a name="BK_Step2"> </a></span></span>

<span data-ttu-id="5588e-162">メールを正常に移行するにはMicrosoft 365メール システムに接続して通信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5588e-162">To migrate email successfully, Microsoft 365 needs to connect and communicate with the source email system.</span></span> <span data-ttu-id="5588e-163">これを行うには、Microsoft 365エンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="5588e-163">To do this, Microsoft 365 uses a migration endpoint.</span></span> <span data-ttu-id="5588e-164">一括移行用に Outlook Anywhere の移行エンドポイントを作成するには、最初に [リモート PowerShell による Exchange への接続](/powershell/exchange/connect-to-exchange-online-powershell)を行います。</span><span class="sxs-lookup"><span data-stu-id="5588e-164">To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).</span></span>

<span data-ttu-id="5588e-165">移行コマンドの完全な一覧については、「[移動と移行のコマンドレット](/powershell/exchange/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5588e-165">For a full list of migration commands, see [Move and migration cmdlets](/powershell/exchange/).</span></span>

<span data-ttu-id="5588e-166">Exchange Online PowerShell で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="5588e-166">Run the following commands in Exchange Online PowerShell:</span></span>

```powershell
$Credentials = Get-Credential
```

<span data-ttu-id="5588e-167">この例では、[Test-MigrationServerAvailability](/powershell/module/exchange/test-migrationserveravailability) コマンドレットを使用して、社内の Exchange サーバーへの接続設定を取得およびテストしてから、この接続設定を使用して "CutoverEndpoint" という移行エンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="5588e-167">The example uses the [Test-MigrationServerAvailability](/powershell/module/exchange/test-migrationserveravailability) cmdlet to obtain and test the connection settings to the on-premises Exchange server, and then uses those connection settings to create the migration endpoint called "CutoverEndpoint".</span></span>

```powershell
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> <span data-ttu-id="5588e-p117">**New-MigrationEndpoint** コマンドレットで **-TargetDatabase** オプションを使用することによって、使用するサービスに対してデータベースを指定することができます。それ以外の場合、データベースは、管理メールボックスが配置されている Active Directory フェデレーション サービス (AD FS) 2.0 サイトからランダムに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="5588e-p117">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>

#### <a name="verify-it-worked"></a><span data-ttu-id="5588e-170">機能していることを確認する</span><span class="sxs-lookup"><span data-stu-id="5588e-170">Verify it worked</span></span>

<span data-ttu-id="5588e-171">Exchange Online PowerShell で、次のコマンドを実行して "CutoverEndpoint" 移行エンドポイントに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="5588e-171">In Exchange Online PowerShell, run the following command to display information about the "CutoverEndpoint" migration endpoint:</span></span>

```powershell
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a><span data-ttu-id="5588e-172">ステップ 3:一括移行バッチを作成する</span><span class="sxs-lookup"><span data-stu-id="5588e-172">Step 3: Create the cutover migration batch</span></span>
<span data-ttu-id="5588e-173"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="5588e-173"><a name="BK_Step3"> </a></span></span>

<span data-ttu-id="5588e-p118">Exchange Online PowerShell の **New-MigrationBatch** コマンドレットを使用すると、一括移行の移行バッチを作成できます。 _AutoStart_ パラメーターを含めると、移行バッチを作成して自動的に開始できます。また、別の方法として、 **Start-MigrationBatch** コマンドレットを使用することにより、移行バッチを作成して後で手動で開始できます。この例では、"CutoverBatch" という移行バッチを作成して、前の例で作成した移行エンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="5588e-p118">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span></span>

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

<span data-ttu-id="5588e-p119">この例でも、"CutoverBatch" という移行バッチを作成して、前の例で作成した移行エンドポイントを使用します。 _AutoStart_ パラメーターが含まれていないため、移行バッチは移行ダッシュボードで、または **Start-MigrationBatch** コマンドレットを使用して手動で開始する必要があります。前述のように、一度に存在できる一括移行バッチは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="5588e-p119">This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="5588e-181">機能していることを確認する</span><span class="sxs-lookup"><span data-stu-id="5588e-181">Verify it worked</span></span>

<span data-ttu-id="5588e-182">一括移行用の移行バッチが正常に作成されたことを確認するには、Exchange Online PowerShell で次のコマンドを実行して、新しい移行バッチに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="5588e-182">To verify that you've successfully created a migration batch for a cutover migration, run the following command in Exchange Online PowerShell to display information about the new migration batch:</span></span>

```powershell
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a><span data-ttu-id="5588e-183">ステップ 4:一括移行バッチを開始する</span><span class="sxs-lookup"><span data-stu-id="5588e-183">Step 4: Start the cutover migration batch</span></span>
<span data-ttu-id="5588e-184"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="5588e-184"><a name="BK_Step4"> </a></span></span>

<span data-ttu-id="5588e-p120">Exchange Online PowerShell で移行バッチを開始するには、次のコマンドを実行します。そうすると、"CutoverBatch" という移行バッチが作成されます。</span><span class="sxs-lookup"><span data-stu-id="5588e-p120">To start the migration batch in Exchange Online PowerShell, run the following command. This will create a migration batch called "CutoverBatch".</span></span>

```powershell
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a><span data-ttu-id="5588e-187">機能していることを確認する</span><span class="sxs-lookup"><span data-stu-id="5588e-187">Verify it worked</span></span>

<span data-ttu-id="5588e-p121">移行バッチが正常に開始されると、移行ダッシュボードのバッチの状態は「同期中」になります。Exchange Online PowerShell を使用して移行バッチが正常に開始したことを確認するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="5588e-p121">If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing. To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:</span></span>

```powershell
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a><span data-ttu-id="5588e-190">手順 5: メールをメールにルーティングMicrosoft 365</span><span class="sxs-lookup"><span data-stu-id="5588e-190">Step 5: Route your email to Microsoft 365</span></span>
<span data-ttu-id="5588e-191"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="5588e-191"><a name="BK_Step5"> </a></span></span>

<span data-ttu-id="5588e-192">電子メール システムでは、電子メールを配信する場所を知るために、MX レコードと呼ばれる DNS レコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="5588e-192">Email systems use a DNS record called an MX record to figure out where to deliver emails.</span></span> <span data-ttu-id="5588e-193">電子メールの移行プロセス中、MX レコードの宛先は移行元の電子メール システムでした。</span><span class="sxs-lookup"><span data-stu-id="5588e-193">During the email migration process, your MX record was pointing to your source email system.</span></span> <span data-ttu-id="5588e-194">メールの移行が完了Microsoft 365、MX レコードを現在のユーザーにMicrosoft 365。</span><span class="sxs-lookup"><span data-stu-id="5588e-194">Now that the email migration to Microsoft 365 is complete, it's time to point your MX record at Microsoft 365.</span></span> <span data-ttu-id="5588e-195">これにより、メールがユーザーのメールボックスに配信Microsoft 365できます。</span><span class="sxs-lookup"><span data-stu-id="5588e-195">This helps make sure that email is delivered to your Microsoft 365 mailboxes.</span></span> <span data-ttu-id="5588e-196">MX レコードを移動することによって、準備ができたら古い電子メール システムをオフにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="5588e-196">By moving the MX record, you can also you turn off your old email system when you're ready.</span></span>

<span data-ttu-id="5588e-197">多くの DNS プロバイダーについては、MX レコードを変更するための具体的な手順があります。</span><span class="sxs-lookup"><span data-stu-id="5588e-197">For many DNS providers, there are specific instructions to change your MX record.</span></span> <span data-ttu-id="5588e-198">使用している DNS プロバイダーが含まれていない場合、または一般的な手順を知りたい場合は、 [「MX レコードの一般的な手順」](https://support.office.microsoft.com/article/7b7b075d-79f9-4e37-8a9e-fb60c1d95166#bkmk_add_mx)も参照してください。</span><span class="sxs-lookup"><span data-stu-id="5588e-198">If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions](https://support.office.microsoft.com/article/7b7b075d-79f9-4e37-8a9e-fb60c1d95166#bkmk_add_mx) are provided as well.</span></span>

<span data-ttu-id="5588e-p124">御社のお客様およびパートナーの電子メール システムが MX レコードの変更を認識するまでに最大 72 時間かかることがあります。次の作業に進むまで、72 時間以上待ちます。 [ステップ 6:一括移行バッチを削除する](use-powershell-to-perform-a-cutover-migration-to-microsoft-365.md#Bk_step6).</span><span class="sxs-lookup"><span data-stu-id="5588e-p124">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-microsoft-365.md#Bk_step6).</span></span>

### <a name="step-6-delete-the-cutover-migration-batch"></a><span data-ttu-id="5588e-201">ステップ 6:一括移行バッチを削除する</span><span class="sxs-lookup"><span data-stu-id="5588e-201">Step 6: Delete the cutover migration batch</span></span>
<span data-ttu-id="5588e-202"><a name="Bk_step6"> </a></span><span class="sxs-lookup"><span data-stu-id="5588e-202"><a name="Bk_step6"> </a></span></span>

<span data-ttu-id="5588e-203">MX レコードを変更し、すべてのメールが Microsoft 365 メールボックスにルーティングされているのを確認した後、ユーザーにメールが送信Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="5588e-203">After you change the MX record and verify that all email is being routed to Microsoft 365 mailboxes, notify the users that their mail is going to Microsoft 365.</span></span> <span data-ttu-id="5588e-204">その後、一括移行バッチを削除できます。</span><span class="sxs-lookup"><span data-stu-id="5588e-204">After this, you can delete the cutover migration batch.</span></span> <span data-ttu-id="5588e-205">移行バッチを削除する前に、次の点を確認します。</span><span class="sxs-lookup"><span data-stu-id="5588e-205">Verify the following before you delete the migration batch.</span></span>

- <span data-ttu-id="5588e-206">すべてのユーザーがメールボックスMicrosoft 365使用しています。</span><span class="sxs-lookup"><span data-stu-id="5588e-206">All users are using Microsoft 365 mailboxes.</span></span> <span data-ttu-id="5588e-207">バッチが削除された後、オンプレミスのメールボックスに送信Exchange Serverは、対応するメールボックスにMicrosoft 365されません。</span><span class="sxs-lookup"><span data-stu-id="5588e-207">After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Microsoft 365 mailboxes.</span></span>

- <span data-ttu-id="5588e-208">Microsoft 365メールが直接送信され始めた後、少なくとも 1 回はメールボックスが同期されました。</span><span class="sxs-lookup"><span data-stu-id="5588e-208">Microsoft 365 mailboxes were synchronized at least once after mail began being sent directly to them.</span></span> <span data-ttu-id="5588e-209">これを行うには、移行バッチの [最後に同期された時刻] ボックスの値が、メールがメールボックスに直接ルーティングされ始めた場合よりもMicrosoft 365してください。</span><span class="sxs-lookup"><span data-stu-id="5588e-209">To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Microsoft 365 mailboxes.</span></span>

<span data-ttu-id="5588e-210">Exchange Online PowerShell で "CutoverBatch" 移行バッチを削除するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="5588e-210">To delete the "CutoverBatch" migration batch in Exchange Online PowerShell, run the following command:</span></span>

```powershell
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a><span data-ttu-id="5588e-211">セクション 7:ユーザー ライセンスの割り当て</span><span class="sxs-lookup"><span data-stu-id="5588e-211">Section 7: Assign user licenses</span></span>
<span data-ttu-id="5588e-212"><a name="BK_Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="5588e-212"><a name="BK_Step7"> </a></span></span>

 <span data-ttu-id="5588e-213">**ライセンスMicrosoft 365して、移行されたアカウントのユーザー アカウントをアクティブ化します。**</span><span class="sxs-lookup"><span data-stu-id="5588e-213">**Activate Microsoft 365 user accounts for the migrated accounts by assigning licenses.**</span></span> <span data-ttu-id="5588e-214">ライセンスを割り当てないと、猶予期間が終了したとき (30 日) にメールボックスが無効になります。</span><span class="sxs-lookup"><span data-stu-id="5588e-214">If you don't assign a license, the mailbox is disabled when the grace period ends (30 days).</span></span> <span data-ttu-id="5588e-215">管理センターでライセンスを割り当てるMicrosoft 365割り当てまたは割り当て[解除するを参照してください](../admin/manage/assign-licenses-to-users.md)。</span><span class="sxs-lookup"><span data-stu-id="5588e-215">To assign a license in the Microsoft 365 admin center, see [Assign or unassign licenses](../admin/manage/assign-licenses-to-users.md).</span></span>

### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="5588e-216">ステップ 8:移行後のタスクを完了する</span><span class="sxs-lookup"><span data-stu-id="5588e-216">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="5588e-217"><a name="BK_Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="5588e-217"><a name="BK_Step8"> </a></span></span>

- <span data-ttu-id="5588e-218">**ユーザーが各自のメールボックスに簡単にアクセスできるように、自動検出 DNS レコードを作成します。**</span><span class="sxs-lookup"><span data-stu-id="5588e-218">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span></span> <span data-ttu-id="5588e-219">すべてのオンプレミスメールボックスを Microsoft 365 に移行した後、Microsoft 365 組織の自動検出 DNS レコードを構成して、ユーザーが Outlook およびモバイル クライアントを使用して新しい Microsoft 365 メールボックスに簡単に接続できます。</span><span class="sxs-lookup"><span data-stu-id="5588e-219">After all on-premises mailboxes are migrated to Microsoft 365, you can configure an Autodiscover DNS record for your Microsoft 365 organization to enable users to easily connect to their new Microsoft 365 mailboxes with Outlook and mobile clients.</span></span> <span data-ttu-id="5588e-220">この新しい自動検出 DNS レコードでは、組織で使用している名前空間と同じ名前空間Microsoft 365があります。</span><span class="sxs-lookup"><span data-stu-id="5588e-220">This new Autodiscover DNS record has to use the same namespace that you're using for your Microsoft 365 organization.</span></span> <span data-ttu-id="5588e-221">たとえば、クラウドベースの名前空間が cloud.contoso.com の場合、作成する必要のある自動検出 DNS レコードは autodiscover.cloud.contoso.com となります。</span><span class="sxs-lookup"><span data-stu-id="5588e-221">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>

    <span data-ttu-id="5588e-222">Exchange Server を保持する場合は、移行後の内部 DNS と外部 DNS の両方で自動検出 DNS CNAME レコードが Microsoft 365 をポイントし、Outlook クライアントが正しいメールボックスに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5588e-222">If you keep your Exchange Server, you should also make sure that Autodiscover DNS CNAME record has to point to Microsoft 365 in both internal and external DNS after the migration so that the Outlook client will to connect to the correct mailbox.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="5588e-223">Exchange 2007、Exchange 2010、および Exchange 2013 では、 `Set-ClientAccessServer AutodiscoverInternalConnectionURI` を `Null` に設定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="5588e-223">In Exchange 2007, Exchange 2010, and Exchange 2013 you should also set `Set-ClientAccessServer AutodiscoverInternalConnectionURI` to `Null`.</span></span>

    <span data-ttu-id="5588e-224">Microsoft 365 CNAME レコードを使用して、モバイル クライアントとモバイル クライアントの自動検出Outlook実装します。</span><span class="sxs-lookup"><span data-stu-id="5588e-224">Microsoft 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span></span> <span data-ttu-id="5588e-225">自動検出 CNAME レコードには以下の情報が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5588e-225">The Autodiscover CNAME record must contain the following information:</span></span>

  - <span data-ttu-id="5588e-226">**エイリアス:** autodiscover</span><span class="sxs-lookup"><span data-stu-id="5588e-226">**Alias:** autodiscover</span></span>

  - <span data-ttu-id="5588e-227">**リンク先:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="5588e-227">**Target:** autodiscover.outlook.com</span></span>

    <span data-ttu-id="5588e-228">詳細については、[「DNS レコードを追加してドメインに接続する」](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5588e-228">For more information, see [Add DNS records to connect your domain](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).</span></span>

- <span data-ttu-id="5588e-229">**社内の Exchange サーバーの使用を停止します。**</span><span class="sxs-lookup"><span data-stu-id="5588e-229">**Decommission on-premises Exchange servers.**</span></span> <span data-ttu-id="5588e-230">すべての電子メールが Microsoft 365 メールボックスに直接ルーティングされ、オンプレミスの電子メール組織を維持する必要がなくなったか、シングル サインオン (SSO) ソリューションの実装を計画しない場合は、サーバーから Exchange をアンインストールし、オンプレミスの Exchange 組織を削除できます。</span><span class="sxs-lookup"><span data-stu-id="5588e-230">After you've verified that all email is being routed directly to the Microsoft 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>

    <span data-ttu-id="5588e-231">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5588e-231">For more information, see the following:</span></span>

  - <span data-ttu-id="5588e-232">「[Exchange 2010 の変更または削除](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))」</span><span class="sxs-lookup"><span data-stu-id="5588e-232">[Modify or Remove Exchange 2010](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))</span></span>

  - <span data-ttu-id="5588e-233">「[Exchange 2007 組織を削除する方法](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))」</span><span class="sxs-lookup"><span data-stu-id="5588e-233">[How to Remove an Exchange 2007 Organization](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))</span></span>

  - <span data-ttu-id="5588e-234">「[Exchange Server 2003 をアンインストールする方法](/previous-versions/tn-archive/bb125110(v=exchg.65))」</span><span class="sxs-lookup"><span data-stu-id="5588e-234">[How to Uninstall Exchange Server 2003](/previous-versions/tn-archive/bb125110(v=exchg.65))</span></span>