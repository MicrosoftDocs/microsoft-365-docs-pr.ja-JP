---
title: Skype for Business および Exchange からのハイブリッド先進認証の削除または無効化
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
description: この記事では、Skype for Business と Exchange からハイブリッド先進認証を削除または無効化する方法について説明します。
ms.openlocfilehash: da0887936f5def69ad80c8f04381bcb3a85c2349
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2020
ms.locfileid: "46691692"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="b73de-103">Skype for Business および Exchange からのハイブリッド先進認証の削除または無効化</span><span class="sxs-lookup"><span data-stu-id="b73de-103">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="b73de-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="b73de-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="b73de-105">ハイブリッドモダン認証 (HMA) を有効にして、現在の環境に適していないことを検出した場合は、HMA を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="b73de-105">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA.</span></span> <span data-ttu-id="b73de-106">この記事では、その方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b73de-106">This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="b73de-107">この記事の対象読者</span><span class="sxs-lookup"><span data-stu-id="b73de-107">Who is this article for?</span></span>

<span data-ttu-id="b73de-108">Skype for Business Online、オンプレミス、または Exchange Online またはオンプレミスで先進認証を有効にしている場合に、HMA を無効にするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="b73de-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b73de-109">Skype for business Online またはオンプレミスでトポロジが混在していて、開始する前にサポートされているトポロジを確認する必要がある場合は、「[先進認証でサポートされている skype For business トポロジ](https://technet.microsoft.com/library/mt803262.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b73de-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="b73de-110">ハイブリッド先進認証を無効にする方法 (Exchange)</span><span class="sxs-lookup"><span data-stu-id="b73de-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="b73de-111">**Exchange オンプレミス**: Exchange 管理シェルを開き、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b73de-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="b73de-112">**Exchange online**: リモート PowerShell を使用して [exchange online に接続](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) します。</span><span class="sxs-lookup"><span data-stu-id="b73de-112">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="b73de-113">*OAuth2ClientProfileEnabled*フラグを ' false ' にするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b73de-113">Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="b73de-114">ハイブリッド先進認証を無効にする方法 (Skype for Business)</span><span class="sxs-lookup"><span data-stu-id="b73de-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="b73de-115">**Skype For Business オンプレミス**: skype For Business 管理シェルで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b73de-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="b73de-116">**Skype For Business online**: リモート PowerShell を使用して [Skype for business online に接続](manage-skype-for-business-online-with-microsoft-365-powershell.md) します。</span><span class="sxs-lookup"><span data-stu-id="b73de-116">**Skype for Business Online**: [Connect to Skype for Business Online](manage-skype-for-business-online-with-microsoft-365-powershell.md) with Remote PowerShell.</span></span> <span data-ttu-id="b73de-117">先進認証を無効にするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b73de-117">Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="b73de-118">[モダン認証の概要に戻る](hybrid-modern-auth-overview.md)</span><span class="sxs-lookup"><span data-stu-id="b73de-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  
