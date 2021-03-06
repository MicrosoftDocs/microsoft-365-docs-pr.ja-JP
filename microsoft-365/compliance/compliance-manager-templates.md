---
title: Microsoft コンプライアンス マネージャーでの評価テンプレートの操作
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Microsoft コンプライアンス マネージャーで評価を構築するためのテンプレートを使用および管理する方法について説明します。 書式設定されたファイルを使用してテンプレートを作成Excelします。
ms.openlocfilehash: 4386f5be67d01d3d6961ccc4bd51ecf729bc8a38
ms.sourcegitcommit: 41c7f7bd5c808ee5ceca0f6efe13d4e67da0262b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2021
ms.locfileid: "53419585"
---
# <a name="working-with-assessment-templates-in-compliance-manager"></a>コンプライアンス マネージャーでの評価テンプレートの操作

**この記事では、次の情報を参照してください。** テンプレート **の動作と評価** テンプレート **ページ** からテンプレートを管理する方法について説明します。 新しいテンプレートの作成 **、** 既存のテンプレートの拡張と変更、Excel を使用したテンプレート **データの** 書式設定、およびテンプレート レポートのエクスポートに関する手順を取得 **します**。

> [!IMPORTANT]
> 組織で使用できる評価テンプレートは、ライセンス契約によって異なります。 [詳細を確認します](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)。

## <a name="templates-overview"></a>テンプレートの概要

テンプレートは、コンプライアンス マネージャーで評価を作成するためのコントロールのフレームワークです。 当社の包括的なテンプレートセットは、データの収集と使用を管理する国内、地域、および業界固有の要件を組織が遵守するのに役立ちます。 テンプレートは、EU GDPR テンプレートや ISO/IEC 27701:2019 テンプレートなど、基になる認定または規制と同じ名前で参照されます。 コンプライアンス管理はさまざまな種類の製品を評価するために使用できます。各テンプレートには、Microsoft 365 に適用されるバージョンと、選択した製品に合わせてカスタマイズできるユニバーサル バージョンの 2 つのバージョンがあります。

## <a name="template-availability-and-licensing"></a>テンプレートの可用性とライセンス

使用できるテンプレートは、組織のライセンス契約 (ライセンスの詳細の表示)[に基づいて作成されます](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)。 テンプレートには、組み込みとプレミアムの 2 つのカテゴリがあります。

#### <a name="included-and-premium-templates"></a>含まれるテンプレートとプレミアム テンプレート

1. **含まれるテンプレートは** 、ライセンスによって付与され、主要な規制と要件をカバーします。
2. **プレミアムテンプレートを購入** して、ライブラリを拡張し、特定のニーズに対応できます。 購入後は、必要に応じてテンプレートから評価を作成できます。 [プレミアム テンプレートを購入する方法について説明します](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)。

テンプレートの [完全な一覧を表示します](compliance-manager-templates-list.md)。

#### <a name="active-and-inactive-templates"></a>アクティブなテンプレートと非アクティブなテンプレート

テンプレートはアクティブまたは非アクティブとしてアクティブ状態を表示します。

- テンプレートは、そのテンプレート **から評価** を作成するとアクティブと見なされます。
- 組織が評価に **テンプレート** を使用しない場合、テンプレートは非アクティブと見なされます。

購入したプレミアム テンプレートに評価をリンクすると、そのテンプレートは 1 年間アクティブになります。 キャンセルしない限り、購入は自動的に更新されます。

また、プレミアム テンプレートを試用することもできます。 試用版ライセンスは、30 日間、最大 25 のテンプレートに対して良好です。 試用版が開始すると、テンプレートは 48 時間以内にテナントで利用できる必要があります。 試用版は、ライセンスを使用してMicrosoft 365 管理センター。

#### <a name="activated-templates-counter"></a>アクティブ化されたテンプレート カウンター

評価ページと評価テンプレート ページには、上部の **近くにアクティブ化されたテンプレート** カウンターがあります。 このカウンターには、ライセンス契約に従って使用する資格がある数の中で使用されているテンプレートの数が表示されます。 テンプレートの使用は、認定レベルでカウントされます。

たとえば、カウンターに 2/5 が表示されている場合、使用できる 5 つのテンプレートの中から 2 つのテンプレートがアクティブ化されています。

カウンターに 5/2 が表示されている場合は、組織が制限を超え、使用しているプレミアム テンプレートの 3 つを購入する必要があります。

Microsoft 365ユニバーサル バージョンのテンプレートには共同ライセンスが適用され、複数の製品で同じ基になる証明書を使用できます。 同じテンプレートのどちらかまたは両方のバージョンを使用すると、アクティブ化されたテンプレートは 1 つのみカウントされます。

詳細については、「コンプライアンス マネージャーの [ライセンス ガイダンス」を参照してください](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)。

## <a name="view-and-manage-templates"></a>テンプレートの表示と管理

コンプライアンス マネージャーの [評価テンプレート] ページには、テンプレートの一覧と、テンプレートに関する主要な詳細が表示されます。 このリストには、コンプライアンス マネージャーが提供するテンプレートのほか、組織が変更または作成したテンプレートも含まれます。 フィルターを適用して、認定、製品範囲、国、業界、作成者、および評価の作成にテンプレートが有効になっているかどうかに基づいてテンプレートを検索できます。

行からテンプレートを選択して、詳細ページを表示します。 このページには、テンプレートの説明と、認定、スコープ、およびコントロールの詳細に関する詳細情報が含まれています。 このページでは、適切なボタンを選択して、評価の作成、テンプレート データのエクセルへのエクスポート、またはテンプレートの変更を行うことができます。

## <a name="format-template-data-with-excel"></a>テンプレート を使用してテンプレート データをExcel

テンプレートExcel作成または変更するために使用されるスプレッドシート[(例](https://go.microsoft.com/fwlink/?linkid=2124865)をダウンロード) には、コンプライアンス マネージャーに正しくインポートするために使用する必要がある特定の形式とスキーマがあります。 このタブには 4 つのタブが含まれています。3 つが必須です。

1. [テンプレート](#template-tab) (必須)
2. [ControlFamily](#controlfamily-tab) (必須)
3. [アクション](#actions-tab) (必須)
4. [ディメンション](#dimensions-tab) (オプション)

スプレッドシートにテンプレート データを入力する場合、スプレッドシートは上記の順序でタブを含める必要があります。それ以外の場合、データはテンプレートに正常にインポートされません。

##### <a name="template-tab"></a>[テンプレート] タブ

[ **テンプレート] タブ** が必要です。 このタブの情報は、テンプレートに関するメタデータを提供します。 必須の列は 4 つ。 列は、次に示すシートの順序Excel保持する必要があります。 4 つの列の **後に独自** の列を追加して、独自のディメンションを指定できます。 これを行う場合は、[ディメンション] タブに必ず **追加** してください。

- **title**: これはテンプレートのタイトルで、一意である必要があります。 独自のテンプレートやコンプライアンス マネージャー テンプレートなど、コンプライアンス マネージャーにある別のテンプレートと名前を共有できない。

- **product**: これは必須のディメンションです。 テンプレートに関連付けられている製品を一覧表示します。

- **証明**: これは、テンプレートに使用している規制です。

- **inScopeServices**: これらは、この評価が対応する製品内のサービスです (たとえば、Office 365 を製品としてリストした場合、Microsoft Teams はスコープ内サービスである可能性があります)。 複数のサービスを 2 つのセミコロンで区切って一覧表示できます。

> [!NOTE]
> スプレッドシートをインポートしてテンプレートを作成またはカスタマイズした後、製品セルと認定セルに挿入したデータを編集できない。 また、同じ製品と認定の組み合わせを持つ 2 つの評価 **をグループに含め、その評価を含め** きらねない場合があります。 同じ製品と認定の組み合わせで複数のテンプレートを作成できます。

##### <a name="controlfamily-tab"></a>ControlFamily タブ

**[ControlFamily] タブ** が必要です。  このタブの必須列は、サンプル スプレッドシートに示されている順序に従う必要があります。

- **controlName**: これは、認定、標準、または規制のコントロール名です。これは、通常、ID のいくつかの種類です。 コントロール名は、テンプレート内で一意である必要があります。 スプレッドシート内に同じ名前の複数のコントロールを持つ必要があります。

- **controlFamily**: コントロールの広範なグループ化を識別する controlFamily の単語または語句を指定します。 controlFamily は一意である必要があります。スプレッドシートに複数のリストを表示できます。 同じ controlFamily を複数のテンプレートに一覧表示することもできますが、互いに関係はありません。 すべての controlFamily は、少なくとも 1 つのコントロールにマップする必要があります。

- **controlTitle**: コントロールのタイトルを指定します。 controlName は参照コードですが、タイトルは通常、規制で見られるリッチ テキスト形式です。

- **controlDescription**: コントロールの説明を指定します。

- **controlActionTitle**: これは、このコントロールに関連付けるアクションのタイトルです。 複数のアクションを追加するには、2 つのセミコロンで区切り、その間にスペースを含めはありません。 リストするコントロールには、少なくとも 1 つのアクションが含まれる必要があります。アクションが存在する必要があります (つまり、同じスプレッドシートの [アクション] タブにリストするアクション、別のテンプレートに存在するアクション、または Microsoft によって作成されたアクションを一覧表示できます)。 異なるコントロールが同じアクションを参照できます。

##### <a name="actions-tab"></a>[アクション] タブ

[ **アクション] タブ** が必要です。  コンプライアンス マネージャーに既に存在する Microsoft ではなく、組織が管理する改善アクションを指定します。 このタブに必要な列は、サンプル スプレッドシートに示されている順序に従う必要があります。

- **actionTitle**: これはアクションのタイトルであり、必須フィールドです。 指定するタイトルは一意である必要があります。 **重要**: 既に存在するアクション (別のテンプレートなど) を参照し、後続の列の要素を変更すると、それらの変更は他のテンプレートの同じアクションに伝達されます。

- **implementationType**: この必須フィールドで、以下の 3 つの実装の種類の 1 つをリストします。
    - **運用** - 組織システム、資産、データ、および人員の機密性、整合性、可用性を保護するための人とプロセスによって実装されるアクション (セキュリティ認識とトレーニングなど)
    - **技術** - 情報システムのハードウェア、ソフトウェア、またはファームウェア コンポーネントに含まれるテクノロジとメカニズムを使用して、組織のシステムとデータの機密性、整合性、可用性を保護することで完了するアクション (多要素認証など)
    - **ドキュメント** - 組織システム、資産、データ、および人員の機密性、整合性、可用性を保護するために必要なコントロールを確立および定義する文書化されたポリシーと手順を通じて実装されるアクション (例: 情報セキュリティ ポリシー)

- **actionScore**: この必須フィールドに、アクションの数値スコア値を指定します。 値は、1 ~ 99 の範囲の数値である必要があります。0、null、または空白にすることはできません。 数値が大きいほど、コンプライアンス態勢の向上に向けてその値が大きくなります。 次の図は、コンプライアンス マネージャーがコントロールをスコア付けする方法を示しています。

  ![コンプライアンス マネージャーがポイント値を制御する](../media/compliance-score-action-scoring.png "コンプライアンス マネージャーがポイント値を制御する")

- **actionDescriptionTitle**: これは説明のタイトルであり、必須です。 この説明タイトルを使用すると、複数のテンプレートで同じアクションを実行し、各テンプレートで異なる説明を表示できます。  このフィールドは、説明が参照しているテンプレートを明確にするのに役立ちます。 ほとんどの場合、作成するテンプレートの名前をこのフィールドに入力できます。

- **actionDescription**: アクションの説明を指定します。 太字やハイパーリンクなどの書式を適用できます。 これは必須フィールドです。

- **dimension-Action の目的**: これはオプションのフィールドです。 ヘッダーを含める場合は、"dimension-" プレフィックスを含める必要があります。 ここに含めるディメンションは、コンプライアンス マネージャーのフィルターとして使用され、コンプライアンス マネージャーの [改善アクションの詳細] ページに表示されます。

##### <a name="dimensions-tab"></a>[ディメンション] タブ

[ **ディメンション] タブ** はオプションです。 ただし、別の場所でディメンションを参照する場合は、既に作成したテンプレートまたは Microsoft テンプレートに存在しない場合は、ここで指定する必要があります。 このタブの列を以下に示します。

- **dimensionKey**: list as "product", "certifications, " action purpose"
- **dimensionValue**: 例: Office 365, HIPPA, Preventative, Detective

既存のテンプレートをエクスポートすると、エクスポートされたスプレッドシートに [ディメンション] タブが表示され、テンプレートで使用されるディメンションが一覧表示されます。

## <a name="create-an-assessment-template"></a>評価テンプレートの作成

カスタム評価用の独自の新しいテンプレートを作成するには、特別に書式設定されたスプレッドシートExcelを使用して、必要なコントロール データを組み立てます。 スプレッドシートが完成すると、コンプライアンス マネージャーにインポートされます。

#### <a name="required-roles"></a>必須の役割

テンプレートを作成および変更できるのは、グローバル管理者またはコンプライアンス マネージャーの管理役割を持つユーザーのみです。 役割とアクセス [許可について詳しくは、次のページをご覧ください](compliance-manager-setup.md#set-user-permissions-and-assign-roles)。

### <a name="create-new-template-in-compliance-manager"></a>コンプライアンス マネージャーで新しいテンプレートを作成する

1. コンプライアンス マネージャーの **[評価テンプレート]** ページに移動します。
2. [新 **しいテンプレートの作成] を選択します**。 テンプレート作成ウィザードが開きます。
3. 作成するテンプレートの種類を選択します。 この場合は、[カスタム テンプレートの **作成] を選択し**、[次へ] を **選択します**。
4. [ファイルの **アップロード] 画面** で、[参照] を選択して、必要なすべてのテンプレート データを含むExcelファイルを検索してアップロードします。
5. ファイルに問題がない場合は、アップロードしたファイルの名前が表示されます。 [**次へ**] を選んで続行します。 (ファイルを変更する必要がある場合は、別 **のアップロードを選択します**)。
    - ファイルにエラーが発生した場合は、上部にエラー メッセージが表示されます。 ファイルを修正し、もう一度アップロードする必要があります。 スプレッドシートが正しく書式設定されていない場合、または特定のフィールドに無効な情報が含まれている場合、エラーが発生します。
6. [ **レビューと終了] 画面** には、改善アクションとコントロールの数とテンプレートの最大スコアが表示されます。 承認する準備ができたら、[テンプレートの作成] **を選択します。** (変更が必要な場合は、[戻る] **を選択** します)。
7. 最後の画面で、新しいテンプレートが作成されたのが確認されます。 [完了 **] を** 選択してウィザードを終了します。
8. 新しいテンプレートの詳細ページにアクセスし、評価を [作成できます](compliance-manager-assessments.md#create-assessments)。

## <a name="extend-microsoft-365-assessment-templates"></a>評価Microsoft 365を拡張する

コンプライアンス マネージャーには、Microsoft が提供する既存のテンプレートに独自のコントロールと改善アクションを追加するオプションがあります。 このプロセスは、Microsoft テンプレートの拡張と呼ばれる。 テンプレートを拡張すると、Microsoft がリリースした更新プログラムを引き続き受け取ります。これは、関連する規制または製品に変更がある場合に発生する可能性があります (「評価の更新プログラムを受け入れる」を [参照](compliance-manager-assessments.md#accept-updates-to-assessments))。

製品以外の製品の評価を設定する場合は、Microsoft 365が異なります。 詳細については、「ユニバーサル評価テンプレート [の拡張」を参照してください](#extend-universal-assessment-templates)。

### <a name="prepare-template-data-and-create-extension"></a>テンプレート データの準備と拡張機能の作成

準備するには、必要なテンプレート データをインポートするために、特別に書式設定されたExcelスプレッドシートを組み立てる必要があります。 このExcelは、上記と同じ一般的な形式に従いますが、拡張機能には特別な要件があります。 エラーを防止するには、次の追加の点を参照してください。

- スプレッドシートには、評価に追加するアクションとコントロールのみを含む必要があります。
- 変更する評価に既に存在するコントロールやアクションをスプレッドシートに含めすることはできません。
- テンプレートのタイトルに "拡張子" を含める (たとえば、"GDPR - [会社名] 拡張子" など)。 これにより、評価テンプレート ページの一覧で、Microsoft が提供する標準のテンプレートや、同様の名前のカスタム テンプレートとは異なる識別が容易になります。 

スプレッドシートの書式を設定した後、以下の手順に従います。

1. [評価テンプレート] **ページに移動し、[** 新しいテンプレートの **作成] を選択します**。 テンプレート作成ウィザードが開きます。

2. 作成するテンプレートの種類を選択します。 この場合は **、[Microsoft テンプレートを拡張する] を選択し、[Microsoft****テンプレートの選択] を選択します**。

3. テンプレート選択のフライアウト ウィンドウが画面の右側に表示され、すべてのテンプレートの一覧と、アクティブまたは非アクティブの状態が表示されます。 アクティブ **化されたテンプレート カウンター** には、使用できる合計数の中で現在使用されているテンプレートの数が表示されます。 制限を超える場合は、メッセージ バーに通知が表示されます。

4. テンプレート選択のフライアウト ウィンドウが画面の右側に表示されます。 検索 **を使用** して、必要なテンプレートを検索するフィルターを適用する

5. テンプレートを見つけると、名前の左側にあるラジオ ボタンを選択し、[保存] を **選択します**。

6. 次の画面には、選択したテンプレートが表示されます。 正しい場合は、[次へ] を **選択します**。 (正しくない場合は、[別の **テンプレートを選択してもう一** 度選択する] を選択します)。

7. [ファイルの **アップロード] 画面** で、[参照] を選択して、必要なすべてのテンプレート データを含むExcelファイルを検索してアップロードします。

8. ファイルに問題がない場合は、次の画面にアップロードされたファイルの名前が表示されます。 [**次へ**] を選択して続行します (ファイルを変更する必要がある場合は、別の **アップロードを選択します**)。

    - ファイルに問題がある場合は、上部にエラー メッセージが表示されます。 ファイルを修正して再アップロードする必要があります。 スプレッドシートが正しく書式設定されていない場合、または特定のフィールドに無効な情報が含まれている場合、エラーが発生します。

9. [ **レビューと終了] 画面** には、改善アクションとコントロールの数とテンプレートの最大スコアが表示されます。 承認する準備ができたら、[次へ] を **選択します**。 (変更が必要な場合は、別の **アップロードを選択** します。)

10. 最後の画面で、新しいテンプレートが作成されたのが確認されます。 [完了 **] を** 選択してウィザードを終了します。

11. 新しいテンプレートの詳細ページが表示されます。 ここから、[評価の作成] を選択して評価 **を作成できます**。 ガイダンスについては、「評価の [ビルドと管理」を参照してください](compliance-manager-assessments.md#create-assessments)。

## <a name="extend-universal-assessment-templates"></a>ユニバーサル評価テンプレートの拡張

また、ユニバーサル バージョンのテンプレートを拡張して、製品固有の評価をカスタマイズすることもできます。 ユニバーサル テンプレートを使用して評価を作成すると、特別な拡張テンプレートが受け取り、評価に固有の製品と認定の組み合わせがあります。 これは、ニーズに合わせて変更できます。 テンプレートを編集する方法のガイダンスについては、テンプレートの変更に関する以下の手順を参照してください。

ユニバーサル テンプレートを編集する場合、テンプレート内のすべてのコンテンツを変更できますが、変更すると親テンプレートとの継承が壊れる可能性があります。 つまり、親テンプレートが更新された場合、Microsoft から更新プログラムが自動的に受信されなくなりました。

## <a name="modify-a-template"></a>テンプレートを変更するには

コントロールの追加や改善アクションの追加や削除など、既に作成したテンプレートを変更することができます。 このプロセスは、テンプレートの作成プロセスと似ています。このプロセスでは、書式設定されたファイルをテンプレート データExcelアップロードします。

ただし、既存のテンプレート データを変更してファイルを書式設定する場合は、注意が必要です。 **保持する既存のデータを上書きしない場合は、これらの手順を慎重に確認することをお勧めします。**

### <a name="format-your-excel-file-to-modify-an-existing-template"></a>既存のテンプレートExcelするファイルの書式設定

評価テンプレート **ページで**   、変更するテンプレートを選択すると、詳細ページが表示されます。 次に、[ **エクスポートしてエクスポート] をExcel** します。 すべてのExcelファイルがダウンロードされます。 ファイルをローカル コンピューターに保存します。

このファイルを操作するには、以下のセクションに移動して、必要な手順をすばやく見つけることができます。

- [メイン テンプレートの属性を編集する](#edit-the-main-template-attributes)
- [改善アクションの追加](#add-an-improvement-action)
- [改善アクションの情報を編集する](#edit-an-improvement-actions-information)
- [改善アクションの名前を変更する](#change-an-improvement-actions-name)
- [改善アクションを削除する](#remove-an-improvement-action)
- [コントロールを削除する](#remove-a-control)

#### <a name="edit-the-main-template-attributes"></a>メイン テンプレートの属性を編集する

[テンプレート **] タブ** では、タイトル列 **、inScopeServices** 列、および追加した可能性があるその他の列で何でも編集できます。  ただし、製品または認定の列では **何も****編集** できません。

#### <a name="add-an-improvement-action"></a>改善アクションの追加

1. [操作] タブ **に移動** します。既存のアクションの下にある最初の空の行の必須フィールドに情報を追加します。
2. **[ControlFamily] タブに移動** します。改善アクションがマップするコントロールを含む行を検索します。 その行の **controlActionTitle** 列に新しいアクションを追加します (このフィールド内の複数のアクションを 2 つのセミコロンで区切り、その間にスペースを入れる必要はありません)。
3. スプレッドシートを保存します。

#### <a name="edit-an-improvement-actions-information"></a>改善アクションの情報を編集する

タイトル以外の改善アクションの情報 *は変更できます*。 列 B 以降から任意のセルを編集し、ファイルをテンプレートにインポートし戻す際に、そのテンプレートの改善アクションに更新されたデータが含まれます。

**actionTitle** (列 A) を編集することはできません。この操作を行う場合、コンプライアンス マネージャーはこれを新しい改善アクションと見なします。 改善アクションの名前を変更する場合は、以下の手順を参照してください。

#### <a name="change-an-improvement-actions-name"></a>改善アクションの名前を変更する

改善アクションの名前を変更する場合は、既存の名前を新しい名前に置き換えるスプレッドシートで明示的に指定する必要があります。 次の手順を実行します。

1. スプレッドシートの **[アクション** ] タブで、列 A の後に新しい列をスプレッドシートに追加します。
2. この新しい列 (現在は列 B) では、行 1 のヘッダーとして **oldActionTitle を入力します**。
3. 列 A の内容をコピーし、列 B に貼り付けます。これにより、変更する既存の改善アクション タイトルが列 B に追加されます。
4. 列 A の **actionTitle** で、古い名前を削除し、改善アクションの新しい名前に置き換える。

コントロールで参照するときに認識するには、改善アクションと Microsoft アクションの両方のアクション タイトルを英語で記述する必要があります。

#### <a name="remove-an-improvement-action"></a>改善アクションを削除する

テンプレートから改善アクションを削除するには、テンプレートを参照しているすべてのコントロールから削除する必要があります。 スプレッドシートを変更するには、以下の手順に従います。

1. **[ControlFamily] タブ** で、削除する改善アクションのタイトルを検索します。
2. 表示されるセルの改善アクションのタイトルを削除します。 その行で改善アクションが唯一のアクションである場合は、行全体 (コントロールを削除する) を削除します。
3. [アクション **] タブ** で、削除する改善アクションを含む行を削除します。
4. スプレッドシートを保存します。

スプレッドシートをテンプレートにインポートし戻す場合、改善アクションはテンプレートから削除されます。

テンプレートから改善アクションを削除しても、コンプライアンス マネージャーから改善アクションが完全に削除されるという問題はありません。 そのアクションは、別のテンプレートで参照できます。

#### <a name="remove-a-control"></a>コントロールを削除する

コントロールを削除するには、以下の手順に従ってスプレッドシートを変更し、スプレッドシートを再インポートします。

1. **[ControlFamily] タブ** で、削除するコントロールを **controlName 列で検索** します。
2. そのコントロールの行を削除します。
    - この削除されたコントロールに、他のコントロールから参照されていない改善アクションが含まれている場合は、[アクション] タブからそれらの改善アクションを **削除する必要** があります。それ以外の場合は、検証エラーが表示されます。

3. スプレッドシートを保存します。

スプレッドシートをテンプレートにインポートし戻す場合、コントロールはテンプレートから削除されます。

### <a name="modify-template-info-in-compliance-manager"></a>コンプライアンス マネージャーでテンプレート情報を変更する

ファイルのExcel保存したら、次の手順を実行します。

1. 評価テンプレート ページを再度開き、テンプレートを選択します。 テンプレートの詳細ページで、[テンプレートの変更] **を選択して** 変更ウィザードを開始します。
2. [ファイルの **アップロード] 画面で**、[参照]**を選択** して、ファイルを検索してアップロードExcelします。
3. ファイルに問題がない場合は、次の画面にアップロードされたファイルの名前が表示されます。 [**次へ**] を選択して続行します (ファイルを変更する必要がある場合は、別の **アップロードを選択します**)。
    - ファイルに問題がある場合は、上部にエラー メッセージが表示されます。 ファイルを修正し、もう一度アップロードする必要があります。 スプレッドシートが正しく書式設定されていない場合、または特定のフィールドに無効な情報が含まれている場合、エラーが発生します。

4. [ **レビューと終了] 画面** には、改善アクションとコントロールの数とテンプレートの最大スコアが表示されます。 承認する準備ができたら、[次へ] を **選択します**。
5. 最後の画面で、テンプレートが変更されたのが確認されます。 [完了 **] を** 選択してウィザードを終了します。

これで、テンプレートに加えた変更が含まれます。 この変更されたテンプレートを使用する評価には保留中の更新プログラムが表示され、テンプレートで行われた変更を反映するために、評価の更新を受け入れる必要があります。 評価の更新 [プログラムの詳細については、次のリンクを参照してください](compliance-manager-assessments.md#accept-updates-to-assessments)。

> [!NOTE]
> 英語以外の言語でコンプライアンス マネージャーを使用している場合は、テンプレートを英語でエクスポートするときにテキストが表示Excel。 コントロールで認識するには、アクションのタイトル (改善アクションと、該当する場合は Microsoft アクション) が英語である必要があります。 アクション タイトルに変更を加えた場合は、ファイルが正しくインポートされるように、必ず英語で記述してください。

## <a name="export-a-template"></a>テンプレートのエクスポート

テンプレートのすべてのデータをExcelファイルをエクスポートできます。 テンプレートを変更するには、変更プロセスで編集およびアップロードする Excelファイルになりますので、テンプレートをエクスポートする[必要があります](#modify-a-template)。 新しいカスタム テンプレートの作成中にデータを使用する場合は、参照用にテンプレートをエクスポートすることもできます。

テンプレートをエクスポートするには、テンプレートの詳細ページに移動し、[テンプレートにエクスポート] ボタン **Excel** します。

コンプライアンス マネージャー テンプレートから拡張したテンプレートをエクスポートする場合、エクスポートされるファイルには、テンプレートに追加した属性だけが含まれます。 エクスポートされたファイルには、Microsoft が提供する元のテンプレート データは含めされません。 このようなレポートを取得するには、評価レポートをエクスポートする [手順を参照してください](compliance-manager-assessments.md#export-an-assessment-report)。
