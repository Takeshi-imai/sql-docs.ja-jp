---
title: "マイニング モデル (Analysis Services - データ マイニング) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/20/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- algorithms [data mining]
- mining models [Analysis Services]
- logical architecture [Analysis Services Multidimensional Data]
- properties [Analysis Services]
- mining models [Analysis Services], about data mining models
- architecture [Analysis Services]
ms.assetid: cd4df273-0c6a-4b3e-9572-8a7e313111e8
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 9fe63b761a9834e53832c1525d8d77ea00a9a508
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="mining-models-analysis-services---data-mining"></a>マイニング モデル (Analysis Services - データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
*マイニング モデル* は、データにアルゴリズムを適用することによって作成されますが、単なるアルゴリズムまたはメタデータ コンテナーではなく、予測を生成し、リレーションシップを推定するために新しいデータに適用されるデータ、統計情報、およびパターンのセットです。  
  
 ここでは、データ マイニング モデルおよびその使用方法 (モデルおよび構造の基本的なアーキテクチャ、マイニング モデルのプロパティ、およびマイニング モデルの作成方法と操作方法) について説明します。  
  
 [マイニング モデルのアーキテクチャ](#bkmk_mdlArch)  
  
 [データ マイニング モデルの定義](#bkmk_mdlDefine)  
  
 [マイニング モデルのプロパティ](#bkmk_mdlProps)  
  
 [マイニング モデル列](#bkmk_mdlCols)  
  
 [マイニング モデルの処理](#bkmk_mdlProcess)  
  
 [マイニング モデルの表示とクエリ](#bkmk_mdlView)  
  
##  <a name="bkmk_mdlArch"></a> マイニング モデルのアーキテクチャ  
 データ マイニング モデルは、マイニング構造からデータを取得し、データ マイニング アルゴリズムを使用してそのデータを分析します。 マイニング構造とマイニング モデルは別個のオブジェクトです。 マイニング構造には、データ ソースを定義する情報が格納されます。 マイニング モデルには、分析の結果として検出されたパターンなど、データの統計的な処理から導き出された情報が格納されます。  
  
 マイニング モデルは、マイニング構造から提供されたデータの処理と分析が完了するまでは空の状態です。 処理後のマイニング モデルには、メタデータ、結果、およびマイニング構造へのバインドが含まれています。  
  
 ![モデルには、メタデータ、パターン、およびバインドが含まれている](../../analysis-services/data-mining/media/dmcon-modelarch2.gif "モデルには、メタデータ、パターン、およびバインドが含まれています。")  
  
 メタデータは、モデルの名前、モデルが格納されているサーバー、モデルの定義 (モデルの構築に使用されたマイニング構造の列、モデルの処理時に適用されたフィルターの定義、データの分析に使用されたアルゴリズムなど) を示します。 データ列およびそのデータ型、フィルター、およびアルゴリズムの選択は分析結果に多大な影響を及ぼします。  
  
 たとえば、同じデータを使用して複数のモデルを作成するために、クラスタリング アルゴリズム、デシジョン ツリー アルゴリズム、および Naïve Bayes アルゴリズムを使用できます。 予測の作成に使用できるパターン、アイテムセット、ルール、または式のセットは、モデルの種類ごとに異なります。 通常、各アルゴリズムではデータをさまざまな方法で分析するため、結果のモデルの *コンテンツ* もさまざまな構造で構成されます。 あるモデルの種類では、データとパターンが *クラスター*にグループ化され、別のモデルの種類のデータは、データを分割して定義するツリー、分岐、およびルールで構成されます。  
  
 また、モデルはトレーニングを行う際のデータの影響も受けます。同じマイニング構造でトレーニングを行ったモデルでも、データのフィルター処理の方法が異なったり、分析時に異なるシードを使用すると、異なる結果が生成される場合があります。 ただし、実際のデータはモデルには格納されません。概要の統計のみが格納され、実際のデータはマイニング構造に存在します。 モデルのトレーニングを行ったときのデータに基づいてフィルターを作成した場合、フィルターの定義もモデル オブジェクトと一緒に保存されます。  
  
 モデルには、マイニング構造にキャッシュされているデータを指すバインドのセットが含まれます。 データが構造内にキャッシュされ、処理後に消去されていない場合、このバインドによって結果から結果を裏付けるケースへのドリルスルーが可能になります。 ただし、実際のデータはモデル内ではなく、構造キャッシュに格納されています。  
  
 [マイニング モデルのアーキテクチャ](#bkmk_mdlArch)  
  
##  <a name="bkmk_mdlDefine"></a> データ マイニング モデルの定義  
 通常、データ マイニング モデルは次の手順で作成します。  
  
-   基になるマイニング構造を作成し、必要になる可能性があるデータの列を含めます。  
  
-   分析タスクに最適なアルゴリズムを選択します。  
  
-   構造からモデルで使用する列を選択し、予測する結果を含んでいる列や入力専用の列など、列の使用方法を指定します。  
  
-   必要に応じて、アルゴリズムによる処理を微調整するパラメーターを設定します。  
  
-   構造およびモデルを *処理* してモデルにデータを入力します。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、マイニング モデルの管理に役立つ以下のツールが用意されています。  
  
-   データ マイニング ウィザードは、マイニング構造および関連マイニング モデルの作成に役立ちます。 これは最も使いやすい方法です。 このウィザードを使用すると、必要なマイニング構造が自動的に作成され、重要な設定を構成しやすくなります。  
  
-   DMX CREATE MODEL ステートメントは、モデルを定義するために使用できます。 必要な構造は処理の一環として自動的に作成されるため、この方法では既存の構造を再利用することはできません。 この方法は、作成するモデルを既に正確に把握している場合またはモデルのスクリプトを作成する場合に使用します。  
  
-   DMX ALTER STRUCTURE ADD MODEL ステートメントは、既存の構造に新しいマイニング モデルを追加するために使用できます。 この方法は、同じデータセットに基づくさまざまなモデルをテストする場合に使用します。  
  
 AMO や XML/A を使用するか、または Excel 用データ マイニング クライアントなどの他のクライアントを使用することによって、プログラムでマイニング モデルを作成することもできます。 詳細については、次の各トピックを参照してください。  
  
 [マイニング モデルのアーキテクチャ](#bkmk_mdlArch)  
  
##  <a name="bkmk_mdlProps"></a> マイニング モデルのプロパティ  
 それぞれのマイニング モデルには、モデルとそのメタデータを定義するプロパティがあります。 プロパティには、名前、説明、モデルが最後に処理された日付、モデルに対する権限、トレーニングに使用されるデータに対するフィルターなどが含まれます。  
  
 各マイニング モデルには、マイニング構造から派生するプロパティや、モデルに使用するデータ列を記述するプロパティもあります。 入れ子になったテーブルの列をモデルで使用する場合は、その列に適用される別個のフィルターが存在することもあります。  
  
 さらに、それぞれのマイニング モデルには、 <xref:Microsoft.AnalysisServices.MiningModel.Algorithm%2A> と <xref:Microsoft.AnalysisServices.MiningModelColumn.Usage%2A>という 2 つの特殊なプロパティが含まれます。  
  
-   **Algorithm プロパティ** モデルの作成に使用するアルゴリズムを指定します。 使用できるアルゴリズムは、使用しているプロバイダーによって異なります。 含まれているアルゴリズムの一覧については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を参照してください[データ マイニング アルゴリズムと #40 です。Analysis Services - データ マイニング &#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md). **Algorithm** プロパティはマイニング モデルに適用し、各モデルに対して 1 回だけ設定できます。 後でアルゴリズムを変更できますが、選択したアルゴリズムによってサポートされていないために、マイニング モデルの列が無効になる場合があります。 このプロパティを変更した後は、モデルを再処理する必要があります。  
  
-   **Usage プロパティ** モデルによる各列の使用方法を定義します。 列の使用法は、 **[入力]**、 **[予測]**、 **[予測のみ]**、または **[キー]**のいずれかに定義できます。 **Usage** プロパティは、マイニング モデルの個別の列に適用し、モデルに含まれるすべての列に個別に設定する必要があります。 モデルで使用しない列が構造に含まれる場合は、使用法を **Ignore**に設定します。 顧客名や電子メール アドレスなどは、マイニング構造に含まれていても分析には使用されないデータの例です。 このように、後でクエリを実行する場合、分析フェーズで列を含める必要はありません。  
  
 マイニング モデルのプロパティの値は、マイニング モデルの作成後に変更できます。 ただし、たとえマイニング モデルの名前の変更であっても、なんらかの変更を加えた場合はマイニング モデルの再処理が必要になります。 モデルを再処理すると、結果が変化する場合があります。  
  
 [マイニング モデルのアーキテクチャ](#bkmk_mdlArch)  
  
##  <a name="bkmk_mdlCols"></a> マイニング モデル列  
 マイニング モデルには、マイニング構造で定義された列から取得されたデータの列が含まれています。 マイニング構造からモデルで使用する列を選択し、マイニング構造列のコピーを作成して、その名前や使用法を変更することもできます。 また、モデル構築プロセスでモデルごとに列の使用法を定義する必要があります。 このとき、列がキーかどうか、列を予測に使用するかどうか、アルゴリズムで列を無視するかどうかなどの情報を定義します。  
  
 モデルを構築する場合、使用可能なデータのすべての列を自動的に追加するのではなく、構造内のデータを十分に確認し、分析に必要な列のみをモデルに含めることをお勧めします。 たとえば、同じデータを繰り返す複数の列を含めたり、ほとんどの値が一意の列を使用したりすることは避けます。 使用しない列がある場合、その列をマイニング構造またはマイニング モデルから削除する必要はなく、モデルの構築時に無視することを示すフラグを列に設定するだけで済みます。 つまり、列は、マイニング構造に存在していますが、マイニング モデルには使用されません。 モデルからマイニング構造へのドリルスルーが有効な場合、列の情報を後から取得できます。  
  
 選択するアルゴリズムによっては、マイニング構造内の一部の列が特定の種類のモデルと互換性を持たない場合や、有効な結果が得られない場合があります。 たとえば、データに Income 列のような連続する数値データが含まれていてモデルに不連続値が必要な場合、データを不連続な範囲に変換するか、モデルから削除する必要があります。 アルゴリズムによってはデータが自動的に変換または削除される場合もありますが、予想した結果が得られるとは限りません。 列の追加のコピーを作成し、別のモデルを試すことを検討してください。 また、特別な処理が必要であることを示すフラグを個々の列に設定することもできます。 たとえば、null が含まれているデータの場合、モデリング フラグを使用して処理を制御できます。 特定の列をモデルのリグレッサーとして指定する場合は、モデリング フラグを使用することで指定できます。  
  
 モデルを作成した後で、列の追加や削除、モデル名の変更などの変更を加えることができます。 ただし、たとえモデル メタデータのみの変更であっても、なんらかの変更を加えた場合はモデルの再処理が必要になります。  
  
 [マイニング モデルのアーキテクチャ](#bkmk_mdlArch)  
  
##  <a name="bkmk_mdlProcess"></a> マイニング モデルの処理  
 データ マイニング モデルは、処理されるまでは空のオブジェクトです。 モデルを処理するとき、構造にキャッシュされたデータは、モデルにフィルターが定義されていればフィルターを通して渡され、アルゴリズムによって分析されます。 アルゴリズムは、データを説明する一連の概要の統計を計算し、データ内のルールとパターンを識別し、これらのルールとパターンを使用してモデルを作成します。  
  
 処理後のマイニング モデルには、統計、ルール、回帰式など、分析によって検出されたデータおよびパターンに関する豊富な情報が含まれています。 カスタム ビューアーを使用してこの情報を参照したり、データ マイニング クエリを作成してこの情報を取得し、分析および表示に使用できます。  
  
 [マイニング モデルのアーキテクチャ](#bkmk_mdlArch)  
  
##  <a name="bkmk_mdlView"></a> マイニング モデルの表示とクエリ  
 モデルの処理が完了したら、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] および [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で提供されているカスタム ビューアーを使用してモデルを調べることができます。 For  
  
 予測を行う場合や、モデル メタデータまたはモデルによって作成されるパターンを取得する場合に、マイニング モデルに対するクエリを作成することもできます。 クエリの作成には、データ マイニング拡張機能 (DMX) を使用します。  
  
## <a name="related-content"></a>関連コンテンツ  
  
|トピック|リンク|  
|------------|-----------|  
|複数のマイニング モデルをサポートするマイニング構造の構築方法について説明します。 モデルにおける列の使用法についても説明します。|[マイニング構造列](../../analysis-services/data-mining/mining-structure-columns.md)<br /><br /> [マイニング モデル列](../../analysis-services/data-mining/mining-model-columns.md)<br /><br /> [コンテンツの種類 (&) #40 です。 データ マイニング &#41;](../../analysis-services/data-mining/content-types-data-mining.md)|  
|さまざまなアルゴリズム、およびアルゴリズムの選択がモデル コンテンツに与える影響について説明します。|[マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)<br /><br /> [データ マイニング アルゴリズムと #40 です。Analysis Services - データ マイニング &#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)|  
|モデルのコンポジションと動作に影響を与えるプロパティの設定方法について説明します。|[マイニング モデルのプロパティ](../../analysis-services/data-mining/mining-model-properties.md)<br /><br /> [モデリング フラグ &#40;データ マイニング&#41;](../../analysis-services/data-mining/modeling-flags-data-mining.md)|  
|データ マイニングのプログラミング可能なインターフェイスについて説明します。|[分析管理オブジェクト &#40; を使用した開発AMO &#41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)<br /><br /> [データ マイニング拡張機能 &#40;DMX&#41; リファレンス](../../dmx/data-mining-extensions-dmx-reference.md)|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でのカスタム データ マイニング ビューアーの使用方法について説明します。|[データ マイニング モデル ビューアー](../../analysis-services/data-mining/data-mining-model-viewers.md)|  
|データ マイニング モデルに対して使用できるさまざまな種類のクエリの例について説明します。|[データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)|  
  
## <a name="related-tasks"></a>関連タスク  
 データ マイニング モデルの操作方法の詳細については、次のリンクを参照してください。  
  
|タスク|リンク|  
|----------|----------|  
|マイニング モデルを追加および削除する|[既存のマイニング構造にマイニング モデルを追加します。](../../analysis-services/data-mining/add-a-mining-model-to-an-existing-mining-structure.md)<br /><br /> [マイニング構造からのマイニング モデルの削除](../../analysis-services/data-mining/delete-a-mining-model-from-a-mining-structure.md)|  
|マイニング モデルの列を操作する|[マイニング モデルからの列の除外](../../analysis-services/data-mining/exclude-a-column-from-a-mining-model.md)<br /><br /> [モデル列の別名を作成します。](../../analysis-services/data-mining/create-an-alias-for-a-model-column.md)<br /><br /> [マイニング モデル内の列の分離の変更](../../analysis-services/data-mining/change-the-discretization-of-a-column-in-a-mining-model.md)<br /><br /> [モデルでリグレッサーとして使用する列の指定](../../analysis-services/data-mining/specify-a-column-to-use-as-regressor-in-a-model.md)|  
|モデルのプロパティを変更する|[マイニング モデルのプロパティの変更](../../analysis-services/data-mining/change-the-properties-of-a-mining-model.md)<br /><br /> [マイニング モデルにフィルターを適用します。](../../analysis-services/data-mining/apply-a-filter-to-a-mining-model.md)<br /><br /> [マイニング モデルからフィルターを削除します。](../../analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)<br /><br /> [マイニング モデルのドリルスルーを有効にします。](../../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md)<br /><br /> [ビューまたはアルゴリズム パラメーターの変更](../../analysis-services/data-mining/view-or-change-algorithm-parameters.md)|  
|モデルをコピー、 移動、または管理する|[マイニング モデルのコピーを作成します。](../../analysis-services/data-mining/make-a-copy-of-a-mining-model.md)<br /><br /> [マイニング モデルのビューをコピーします。](../../analysis-services/data-mining/copy-a-view-of-a-mining-model.md)<br /><br /> [エクスポート &#40;DMX&#41;](../../dmx/export-dmx.md)<br /><br /> [インポート &#40;DMX&#41;](../../dmx/import-dmx.md)|  
|モデルにデータを入力する、またはモデルのデータを更新する|[マイニング モデルを処理します。](../../analysis-services/data-mining/process-a-mining-model.md)|  
|OLAP モデルを操作する|[データ マイニング ディメンションを作成します。](../../analysis-services/data-mining/create-a-data-mining-dimension.md)|  
  
## <a name="see-also"></a>参照  
 [データベース オブジェクト &#40;Analysis Services - 多次元データ&#41;](../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
