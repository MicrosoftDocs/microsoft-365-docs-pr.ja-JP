---
title: Azure での暗号化
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-security-compliance
- Strat_O365_Enterprise
description: Azure で使用可能な暗号化 (Azure ディスク暗号化など) について説明します。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ee4eb2bec814d7e06d418518bb9be272f1bd5aaa
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2021
ms.locfileid: "50926255"
---
# <a name="encryption-in-azure"></a>Azure での暗号化

暗号化された通信や運用プロセスなど、Azure の技術的な保護措置は、データのセキュリティ保護に役立ちます。 また、追加の暗号化機能を実装し、独自の暗号化キーを管理することもできます。 お客様の構成に関係なく、Microsoft は暗号化を適用して Azure の顧客データを保護します。 Microsoft では、暗号化キーの暗号化、制御、管理、およびデータへのアクセスの制御と監査を行うさまざまな高度なテクノロジを通じて、Azure でホストされるデータを制御することもできます。 さらに、Azure Storage には、開発者がセキュリティで保護されたアプリケーションを構築するための包括的なセキュリティ機能のセットが提供されています。

Azure には、データをある場所から別の場所に移動する場合に、データを保護するための多くのメカニズムが用意されています。 Microsoft は、クラウド サービスと顧客の間を移動する際に TLS を使用してデータを保護します。 Microsoft のデータ センターは、Azure サービスに接続するクライアント システムとの TLS 接続をネゴシエートします。 Perfect Forward Secrecy (PFS) は、お客様のクライアント システムと Microsoft のクラウド サービス間の接続を一意のキーで保護します。 接続では、RSA ベースの 2,048 ビット暗号化キーの長さも使用します。 この組み合わせにより、転送中のデータを傍受してアクセスすることは困難になります。

クライアント側の暗号化、HTTPS、または SMB 3.0 を使用して、アプリケーションと Azure 間の転送中にデータをセキュリティで保護できます。 [](/azure/storage/storage-client-side-encryption) 独自の仮想マシン (VM) とユーザー間のトラフィックの暗号化を有効にできます。 [Azure Virtual Networks を](https://azure.microsoft.com/services/virtual-network/)使用すると、業界標準の IPsec プロトコルを使用して、企業の VPN ゲートウェイと Azure の間、および仮想ネットワーク上にある VM 間のトラフィックを暗号化できます。

保存中のデータの場合、Azure には AES-256 のサポートなど、多くの暗号化オプションが用意されています。ニーズに最適なデータ ストレージ シナリオを柔軟に選択できます。 データは、ストレージ サービス暗号化を使用して Azure [](/azure/storage/storage-service-encryption)Storage に書き込まれると自動的に暗号化され、VM で使用されるオペレーティング システムとデータ ディスクを暗号化できます。 詳細については [、「Azure の Windows 仮想マシンのセキュリティに関する推奨事項」を参照してください](/azure/security/azure-security-disk-encryption)。 さらに、Azure Storage のデータ オブジェクトへの委任されたアクセスは、共有アクセス署名を使用 [して付与できます](/azure/storage/storage-dotnet-shared-access-signature-part-1)。 Azure は、Azure データベースとデータ ウェアハウス用の透過的なデータ暗号化を使用して、保存SQL [暗号化も提供します](/sql/relational-databases/security/encryption/transparent-data-encryption-azure-sql)。

Azure での暗号化の詳細については、「Azure [暗号化](/azure/security/security-azure-encryption-overview) の概要」および [「Azure Data Encryption-at-Rest」を参照してください](/azure/security/azure-security-encryption-atrest)。

## <a name="azure-disk-encryption"></a>Azure ディスクの暗号化

Azure Disk Encryption を使用すると、Windows および Linux Infrastructure as a Service (IaaS) VM ディスクを暗号化できます。 Azure Disk Encryption は、Windows の BitLocker 機能と Linux DM-Crypt機能を活用して、オペレーティング システムとデータ ディスクにボリューム レベルの暗号化を提供します。 また、VM ディスク上のすべてのデータが Azure ストレージの保存時に暗号化されます。 Azure Disk Encryption は Azure Key Vault と統合され、暗号化キーとシークレットの使用を制御、管理、監査するのに役立ちます。

詳細については [、「Azure の Windows 仮想マシンのセキュリティに関する推奨事項」を参照してください](/azure/virtual-machines/windows/security-recommendations)。

## <a name="azure-storage-service-encryption"></a>Azure Storage Service の暗号化

[Azure Storage Service Encryption を使用すると](/azure/storage/storage-service-encryption)、Azure Storage はデータをストレージに保持する前にデータを自動的に暗号化し、取得前にデータを復号化します。 暗号化、復号化、およびキー管理プロセスは、ユーザーに対して完全に透過的です。 Azure Storage Service の暗号化は [、Azure Blob Storage および Azure Files](https://azure.microsoft.com/services/storage/blobs/) に [使用できます](https://azure.microsoft.com/services/storage/files/)。 Azure Storage Service の暗号化で Microsoft で管理された暗号化キーを使用することもできますし、独自の暗号化キーを使用することもできます。 (独自のキーの使用の詳細については、「Azure Key Vault の顧客管理キーを使用したストレージ サービスの暗号化」 [を参照してください](/azure/storage/common/storage-service-encryption-customer-managed-keys)。 Microsoft 管理キーの使用の詳細については、「Storage Service Encryption for Data at Rest .)」 [を参照してください](/azure/storage/storage-service-encryption)。さらに、暗号化の使用を自動化できます。 たとえば[、Azure](/rest/api/storagerp/)Storage Resource Provider REST [API、.NET](/dotnet/api/overview/azure/storage)用ストレージ リソース プロバイダー クライアント ライブラリ[、Azure PowerShell、](/powershell/azureps-cmdlets-docs)[または Azure CLI](/azure/storage/storage-azure-cli)を使用して、ストレージ アカウントで記憶域サービスの暗号化をプログラムで有効または無効にできます。

一部の Microsoft 365 サービスでは、Azure を使用してデータを格納しています。 たとえば、SharePoint Online および OneDrive for Business ストア データは Azure BLOB ストレージに格納され、Microsoft Teams はチャット サービスのデータをテーブル、BLOB、キューに格納します。 さらに、Microsoft 365 コンプライアンス センターのコンプライアンス マネージャー機能は [、Azure Cosmos DB](/azure/cosmos-db/database-encryption-at-rest)、サービスとしてのプラットフォーム (PaaS)、グローバルに分散されたマルチモデル データベースに暗号化された形式で格納される顧客入力データを格納します。 Azure Storage Service Encryption は、Azure BLOB ストレージとテーブルに格納されたデータを暗号化し、Azure Disk Encryption はキュー内のデータと Windows および IaaS 仮想マシン ディスクを暗号化して、オペレーティング システムとデータ ディスクのボリューム暗号化を提供します。 このソリューションにより、仮想マシン ディスク上のすべてのデータが Azure ストレージの保存時に暗号化されます。 [Azure Cosmos DB の保存](/azure/cosmos-db/database-encryption-at-rest) 時の暗号化は、セキュリティで保護されたキー ストレージ システム、暗号化されたネットワーク、暗号化 API など、いくつかのセキュリティ テクノロジを使用して実装されます。

## <a name="azure-key-vault"></a>Azure Key Vault

セキュリティで保護されたキー管理は、暗号化のベスト プラクティスのコアではありません。また、クラウド内のデータを保護するためにも重要です。 [Azure Key Vault](/azure/key-vault/key-vault-whatis) を使用すると、ハードウェア セキュリティ モジュール (HSM) に格納されているキーを使用するパスワードなど、キーや小さなシークレットを暗号化できます。 Azure Key Vault は、クラウド サービスで使用される暗号化キーへのアクセスを管理および制御するための Microsoft の推奨ソリューションです。 キーにアクセスするためのアクセス許可は、サービスまたは Azure Active Directory アカウントを持つユーザーに割り当てることができます。 Azure Key Vault を使用すると、組織は、HSM とキー管理ソフトウェアを構成、修正、保守する必要が軽減されます。 Azure Key Vault を使用すると、Microsoft ではキーが表示され、アプリケーションはキーに直接アクセスすることはできません。コントロールを維持します。 また、HSM でキーをインポートまたは生成することもできます。 Azure Information Protection を含むサブスクリプションを持つ組織は、顧客管理キー [Bring Your Own Key](/information-protection/plan-design/byok-price-restrictions) (BYOK) を使用するように Azure Information Protection テナントを構成し、その使用状況を [ログに記録できます](/information-protection/deploy-use/log-analyze-usage)。