---
title: ドメインを追加する
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
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
- AdminTemplateSet
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: 組織では、複数のドメインが必要になる場合があります。 サブスクリプションに別のドメインを追加する方法について学習します。
ms.openlocfilehash: 766d0f6c1e3c68a262bc01ba432e042f0d274ce8
ms.sourcegitcommit: 00f001019c653269d85718d410f970887d904304
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2021
ms.locfileid: "53394847"
---
# <a name="add-another-domain"></a>別のドメインを追加する

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4dN8c?autoplay=false]

会社によって、さまざまな目的で複数のドメイン名が必要になる場合があります。 たとえば、顧客が既にその会社名を使用していて、顧客とのコミュニケーションに失敗した場合、会社名に別のスペルを追加したい場合があります。

## <a name="try-it"></a>お試しください!

1. Microsoft 365 管理センターで、[**セットアップ**] を選択します。
1. [**カスタム ドメインをセットアップする**] にて、[**表示**］ を選択します。
1. [**管理**]、[**ドメインの追加**] の順に選択します。
1. 追加する新しいドメイン名を入力し、[**次へ**] を選択します。
1. ドメイン レジストラー (この場合は GoDaddy) にサインインし、[**次へ**] を選択します。
1. メッセージが表示されたら、レジストラーにサインインしてから、[**承認**] を選択します。
1. [**DNS レコードを追加してもらう**] を選び、[**次へ**] を選択します。
1. 新しいドメインのサービスを選び、別のドメインで処理されるサービスのチェック ボックスをオフにします。 たとえば、メール用に新しいドメインを使うだけなら、［**Exchange**］ を選び、［**Skype for Business**］ と ［**Mobile Device Management for Office 365**］ のチェック ボックスをオフにします。
1. [**次へ**］、［**承認**］、［**次へ**］ の順に選択してから、［**完了**］ を選択します。 新しいドメインが追加されました。

新しいドメインでメールを受信するには、各ユーザーの新しいメール エイリアスを追加する必要があります。

1. [**ユーザー**］、［**アクティブなユーザー**］ の順に選択してから、新しいエイリアスが割り当てられるユーザーを選択します。
1. [**メール エイリアスの管理**]、[**エイリアスを追加**] の順に選択します。
1. ユーザー名を入力し、ドロップダウン リストから新しいドメインを選択します。
1. [**変更を保存する**] を選択し、ウィンドウを閉じます。
1. 新しいドメインでメールを受信する必要がある各ユーザーに、これらの手順を繰り返します。

## <a name="related-content"></a>関連コンテンツ

[ドメインをドメインに追加Microsoft 365](../admin/setup/add-domain.md) (記事)\
[DNS レコードを追加してドメインに接続](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) する (記事)\
[任意のドメイン レジストラーで Microsoft 365 をセットアップするためにネームサーバーを変更する](../admin/get-help-with-domains/change-nameservers-at-any-domain-registrar.md) (記事)\
[ドメインの FAQ](../admin/setup/domains-faq.yml) (記事)