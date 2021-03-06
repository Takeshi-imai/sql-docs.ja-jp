---
title: "データ マイニング クエリ ツール |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
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
- predictions [Analysis Services], DMX prediction queries
- predictions [DMX]
- DMX [Analysis Services], prediction queries
- prediction queries [DMX]
- predictions [Analysis Services]
- queries [DMX], prediction queries
- mining models [Analysis Services], DMX
ms.assetid: a8952427-fd8c-4300-8f62-25f57ac1be0c
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 71337bc66abab8e91fd997cd2cde635945b0ef82
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="data-mining-query-tools"></a>データ マイニング クエリ ツール
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
すべてのデータ マイニング クエリで、データ マイニング拡張機能 (DMX) の言語が使用されます。 DMX を使って、分類、リスク分析、推奨設定の生成、線形回帰など、あらゆる種類の Machine Learning タスクのモデルを作成できます。 またモデル処理時に生成されたパターンおよび統計に関する情報を取得するための DMX クエリを作成することもできます。  
  
 独自の DMX を作成することも、 **予測クエリ ビルダー** などのツールを使用して基本的な DMX を作成して変更することもできます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] と [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のどちらにも、DMX 予測クエリの作成に便利なツールが用意されています。 このトピックでは、これらのツールを使って、データ マイニング クエリを作成および実行する方法について説明します。  
  
-   [予測クエリ ビルダー](#bkmk_Builder)  
  
-   [クエリ エディター](#bkmk_QueryEditor)  
  
-   [[DMX テンプレート]](#bkmk_Templates)  
  
-   [Integration Services](#bkmk_SSIS)  
  
-   [アプリケーション プログラミング インターフェイス](#bkmk_API)  
  
##  <a name="bkmk_Builder"></a> 予測クエリ ビルダー  
 予測クエリ ビルダーは、データ マイニング デザイナーの **[マイニング モデル予測]** タブに含まれ、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]および [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で入手できます。  
  
 クエリ ビルダーでは、マイニング モデルの選択、新しいケース データの追加、予測関数の追加などの操作を実行できます。 テキスト エディターに切り替えてクエリを手動で編集することも、 **結果** ペインに切り替えてクエリの結果を表示することもできます。  
  
##  <a name="bkmk_QueryEditor"></a> クエリ エディター  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のクエリ エディターを使用して、DMX クエリを作成して実行できます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続して、データベース、マイニング構造列、およびマイニング モデルを選択できます。 **メタデータ エクスプ ローラー** には、参照できる予測関数の一覧が含まれています。  
  
##  <a name="bkmk_Templates"></a> [DMX テンプレート]  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、DMX クエリの作成に使用できる対話型の DMX クエリ テンプレートが提供されます。 テンプレートの一覧を表示するには、ツール バーの **[表示]** をクリックし、 **[テンプレート エクスプローラー]**を選択します。 DMX、MDX、および XMLA のテンプレートを含むすべての [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] テンプレートを表示するには、キューブ アイコンをクリックします。  
  
 テンプレートを使用してクエリをビルドするには、開いているクエリ ウィンドウにテンプレートをドラッグするか、テンプレートをダブルクリックして新しい接続と新しいクエリ ペインを開きます。  
  
 テンプレートから予測クエリを作成する方法の例については、「 [テンプレートからの単一予測クエリの作成](../../analysis-services/data-mining/create-a-singleton-prediction-query-from-a-template.md)」を参照してください。  
  
> [!WARNING]  
>  Microsoft Office Excel データ マイニング アドインにも多くのクエリ テンプレートが含まれ、複雑な DMX ステートメントを作成するための対話形式のクエリ ビルダーも提供されます。 テンプレートを使用するには、データ マイニング クライアントで **[クエリ]**と **[詳細設定]** を順にクリックします。  
  
##  <a name="bkmk_SSIS"></a> Integration Services データ マイニング コンポーネント  
 予測クエリを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの一部として含めることもできます。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の次のタスクおよび変換では、DMX 予測クエリと DMX ステートメントの作成と実行がサポートされます。  
  
|コンポーネント|Description|  
|---------------|-----------------|  
|データ マイニング クエリ タスク|DMX クエリおよびその他の DMX ステートメントを制御フローの一部として実行します。<br /><br /> タスク エディターには、予測クエリ ビルダーと、手動で DMX クエリを変更するためのテキスト ボックスがあります。 ただし、タスク エディターでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ソリューションでのオブジェクトに対するクエリを検証できません。 このため、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] または [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] でクエリを作成してから、ステートメントまたはクエリのテキストをタスク エディターに貼り付けることをお勧めします。|  
|データ マイニング クエリ変換|データ フロー ソースから渡されるデータを使用してデータ フロー内で予測クエリを実行します。<br /><br /> タスク エディターには、予測クエリ ビルダーと、手動で DMX クエリを変更するためのテキスト ボックスがあります。<br /><br /> 変換を使用できるのは、データ フローのデータを使用するクエリ (つまり、PREDICTION JOIN 構文を使用するクエリ) を作成する場合のみです。 このコンポーネントは、コンテンツ クエリまたはその他の種類の DMX ステートメントの実行には使用できません。|  
  
##  <a name="bkmk_API"></a> アプリケーション プログラミング インターフェイス  
 さまざまなプログラミング言語を使用し、OLE DB、Analysis Services ADOMD クライアントなどのサーバー プロトコルを組み合わせ、データ マイニング モデルに対してクエリを実行するカスタム アプリケーションを作成できます。 詳細については、「 [データ マイニングのプログラミング](../../analysis-services/data-mining-programming.md)」を参照してください。  
  
 ただし、XMLA は、Analysis Service サーバーとのすべてのやり取りのもとになるメッセージ形式を構成します。 XMLA メッセージ内では、DMX に基づく予測クエリ、コンテンツ クエリ、またはデータ マイニング スキーマ行セットを使用してモデル メタデータを取得するクエリのどれを送信しているかにより、クエリの表示の方法が異なります。  
  
-   **予測クエリ** (および他のすべての DMX ステートメント) のテキストは、[Execute (XMLA)](../../analysis-services/xmla/xml-elements-methods-execute.md) メソッドを使用し、XMLA [Command (XMLA)](../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md) 要素の [Statement (XMLA)](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) 要素内のテキストとして配置される DMX クエリと共に、XMLA で送信されます。  
  
-   クラスター数、デシジョン ツリーで使用される属性、モデルの最終処理日、モデル作成時に使用されるアルゴリズム パラメーターなどの**モデル コンテンツ**および**モデル メタデータ**を取得するには、[Discover (XMLA)](../../analysis-services/xmla/xml-elements-methods-discover.md) メソッドを使用し、[RequestType (XMLA)](../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) ヘッダーでデータ マイニング スキーマ行セットの 1 つを指定します。 クエリの範囲を絞り込むには、基準を [RestrictionList (XMLA)](../../analysis-services/xmla/xml-elements-properties/restrictionlist-element-xmla.md) 要素の制限として入力します。  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41;参照](../../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング ソリューション](../../analysis-services/data-mining/data-mining-solutions.md)   
 [DMX の Select ステートメントを理解します](../../dmx/understanding-the-dmx-select-statement.md)   
 [構造と DMX 予測クエリの使用状況](../../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [予測クエリ ビルダーを使用して予測クエリを作成します。](../../analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)   
 [SQL Server Management Studio で、DMX クエリを作成します。](../../analysis-services/data-mining/create-a-dmx-query-in-sql-server-management-studio.md)  
  
  
