---
title: "多対多リレーションシップと多対多リレーションシップのプロパティの定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: many-to-many relationships [Analysis Services]
ms.assetid: edb5f61a-a581-467a-a367-134b7f9b849f
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 5377557da99938446a0746e0183e2adcf321dab3
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="define-a-many-to-many-relationship-and-many-to-many-relationship-properties"></a>多対多のリレーションシップと多対多のリレーションシップのプロパティの定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]このトピックでは、ときに使用して、それらを作成する方法を含め、Analysis Services の多対多ディメンションについて説明します。  
  
## <a name="introduction"></a>概要  
 Analysis Services は、多対多ディメンションをサポートし、従来のスター スキーマで記述できる以上に複雑な分析に対応できます。 従来のスター スキーマでは、すべてのディメンションがファクト テーブル内で一対多のリレーションシップを持ちます。 各ファクトは 1 つのディメンション メンバーと結合しています。1 つのディメンション メンバーは複数のファクトに関連付けられます。  
  
 多対多では、単一のファクト (口座残高など) を、同じディメンションの複数のメンバーに関連付けできるようにすること (共同名義口座の残高を、その口座の複数の所有者に帰属させることができる) で、モデル化に関するこの制約を取り除きます。  
  
 概念的には、Analysis Services 内の多対多ディメンションのリレーションシップは、従来のモデル内の多対多リレーションシップと同等であり、同じ種類のシナリオに対応しています。 多対多の一般的な例として、次のものを挙げることができます。  
  
-   学生は複数のコースに登録され、各コースに複数の学生が参加します。  
  
-   医師は複数の患者を担当し、患者は複数の医師から対応を受けます。  
  
-   顧客は複数の銀行口座を持ち、銀行口座は複数の顧客に帰属する可能性があります。  
  
-   Adventure Works では、多くの顧客が複数の購入動機で 1 回の製品注文をし、1 つの購入動機が複数の注文に結び付くことがあります。  
  
 分析の観点では、多対多の関係で解決する問題は、ディメンションのリレーションシップを基準としたカウントまたは合計に関する正確な表現形式 (通常は特定のディメンション メンバーに関する計算を実行するときに、二重カウントを除去します) です。 この点を明確にするのには例が必要です。 複数のカテゴリに属する 1 つの製品またはサービスについて考えます。 仮にカテゴリごとにサービスをカウントする場合は、両方のカテゴリに属する 1 つのサービスを、どちらにカテゴリにも含めたいと考えます。 同時に、提供しているサービスの数を過大に表示することも避けたいと考えます。 多対多ディメンションのリレーションシップを指定することで、カテゴリごとまたはサービスごとのクエリを実行するときに、正確な結果を取得できる可能性がいっそう高くなります。 ただし、この考え方が適切であることを確認するために、全体的なテストが常に必要です。  
  
 構造的には、多対多ディメンションのリレーションシップを作成することは、リレーショナル データ モデル内で多対多を作成する方法に似ています。 リレーショナル モデルは *交差テーブル* を使用して行のアソシエーションを格納するのに対し、多次元モデルは *中間メジャー グループ*を使用します。 中間メジャー グループとは、異なるディメンションから取得したメンバーをマップするテーブルを参照するために使用する用語です。  
  
 視覚的には、多対多ディメンションのリレーションシップはキューブ図では表示されません。 代わりに、[ディメンションの使用法] タブを使用して、モデル内にあるすべての多対多リレーションシップをすばやく識別することができます。 多対多リレーションシップは、次のアイコンによって示されます。  
  
 ![ディメンションの使用法の多対多アイコン](../../analysis-services/multidimensional-models/media/ssas-m2m-icondimusage.png "多対多ディメンションの使用法のアイコン")  
  
 ボタンをクリックすると、[リレーションシップの定義] ダイアログ ボックスが開き、リレーションシップの種類が多対多であることを確認し、リレーションシップ内で使用されている中間メジャー グループを表示することができます。  
  
 ![ディメンションの使用法を定義するリレーションシップ ボタン](../../analysis-services/multidimensional-models/media/ssas-m2m-btndimusage.png "ディメンションの使用法 [リレーションシップの定義] ボタン")  
  
 これ以降のセクションでは、多対多リレーションシップを設定する方法と、モデルの動作をテストする方法を学習します。 代わりに、追加情報を確認する場合や、チュートリアルを最初に試す場合は、この記事の最後にある「 **詳細情報** 」を参照してください。  
  
## <a name="create-a-many-to-many-dimension"></a>多対多ディメンションの作成  
 単純な多対多リレーションシップには、多対多の基数を含む 2 つのディメンション、メンバー アソシエーションを格納するための中間メジャー グループ、総売上や銀行口座の残高の合計など測定可能なデータを含むファクト メジャー グループが含まれています。  
  
 多対多リレーションシップ内の各ディメンションには、DSV 内の対応テーブルが含まれている可能性があり、その場合は、モデル内の各ディメンションが、データ ソース内の既存のテーブルに基づいています。 逆に、モデル内のディメンションが、DSV 内の少数の物理テーブルや複数の物理テーブルから派生した可能性もあります。 Sales Reasons と Sales Orders を適切な例として使用して、Adventure Works のサンプル キューブはモデルのみのデータ構造として存在するディメンションを活用して多対多の関係を示しますが、DSV 内に物理的な同等の存在はありません。 Sales Order ディメンションは、基になるデータ ソース内のディメンション テーブルではなく、ファクト テーブルに基づいています。  
  
 次の手順では、多対多リレーションシップにどのエンティティが参加しているかを既に把握していることを想定しています。 詳細情報を確認するには、「 **詳細情報** 」を参照してください。  
  
 多対多リレーションシップを作成する手順を示すために、Adventure Works のサンプル キューブ内にある多対多リレーションシップの 1 つを、この手順で作成し直します。 リレーショナル データベース エンジンのインスタンスにソース データ (つまり、Adventure Works サンプル データ ウェアハウス) を既にインストールしてある場合は、次の手順に従うことができます。  
  
#### <a name="step-1-verify-dsv-relationships"></a>手順 1: DSV リレーションシップの確認  
  
1.  SQL Server データ ツールの多次元プロジェクトで、SQL Server データベース エンジンのインスタンスでホストされている Adventure Works DW 2012 リレーショナル データ ウェアハウスに接続するデータ ソースを作成します。  
  
2.  次の既存のテーブルを使用して、データ ソース ビューを作成します。  
  
    -   FactInternetSales  
  
    -   FactInternetSalesReason  
  
    -   DimSalesReason  
  
3.  多対多リレーションシップで使用することを計画しているすべてのテーブルが、DSV 内で主キーのリレーションシップを通じて関連付けられていることを確認します。 これは、これ以降の手順で中間メジャー グループへのリンクを確立するための要件です。  
  
    > [!NOTE]  
    >  基になるデータ ソースが主キー リレーションシップや外部キー リレーションシップを提供していない場合は、DSV 内でそれらのリレーションシップを手動で作成できます。 詳細については、「[データ ソース ビューでの論理リレーションシップの定義 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/define-logical-relationships-in-a-data-source-view-analysis-services.md)」を参照してください。  
  
     この手順で使用するテーブルが主キーを使用してリンクされていることを、次の例で確認します。  
  
     ![関連テーブルを示す DSV](../../analysis-services/multidimensional-models/media/ssas-m2m-dsvpkeys.PNG "関連テーブルを示す DSV")  
  
#### <a name="step-2-create-dimensions-and-measure-groups"></a>手順 2: ディメンションとメジャー グループの作成  
  
1.  SQL Server データ ツールの多次元プロジェクトで、 **[ディメンション]** を右クリックし、 **[新しいディメンション]**をクリックします。  
  
2.  既存のテーブル **DimSalesReason**に基づいて新しいディメンションを作成します。 ソースを指定するときに、すべての既定値をそのまま使用します。  
  
     属性に関しては、すべてを選択します。  
  
     ![新しいディメンションの属性リスト](../../analysis-services/multidimensional-models/media/ssas-m2m-dimsalesreason.PNG "新しいディメンションの属性リスト")  
  
3.  既存のテーブル Fact Internet Sales に基づいて 2 番目のディメンションを作成します。 これはファクト テーブルですが、Sales Order 情報を格納しています。 このテーブルを使用して、Sales Order ディメンションを作成します。  
  
4.  [基になる情報の指定] で、[名前] 列を指定する必要があることを示す警告が表示されます。 [名前] として、 **SalesOrderNumber** を選択します。  
  
     ![[名前] 列を示す sales Order ディメンション](../../analysis-services/multidimensional-models/media/ssas-m2m-dimsalesordersource.PNG "名前列を示す Sales Order ディメンション")  
  
5.  ウィザードの次のページで、属性を選択します。 この例では、 **SalesOrderNumber**のみを選択できます。  
  
     ![Sales order ディメンションを示す属性リスト](../../analysis-services/multidimensional-models/media/ssas-m2m-dimsalesorderattrib.PNG "Sales order ディメンションを示す属性の一覧")  
  
6.  そのディメンションを **Dim Sales Orders**という名前に変更します。その結果、ディメンションに関して、一貫性のある名前付け規約を使用できます。  
  
     ![ディメンションの名前変更を示すウィザード ページ](../../analysis-services/multidimensional-models/media/ssas-m2m-dimsalesorders.PNG "ディメンションの名前変更を示すウィザード ページ")  
  
7.  **[キューブ]** を右クリックし、 **[新しいキューブ]**をクリックします。  
  
8.  メジャー グループ テーブルで、 **FactInternetSales** と **FactInternetSalesReason**を選択します。  
  
     **FactInternetSales** を選択する理由は、キューブで使用するメジャーがこの中に含まれていることです。 **FactInternetSalesReason** を選択する理由は、これが、販売注文を購入動機に関連付けるメンバー アソシエーション データを提供する中間メジャー グループであることです。  
  
9. 各ファクト テーブルに対応するメジャーを選択します。  
  
     モデルを簡略化するために、すべてのメジャーをクリアしてから、リストの下部にある **Sales Amount** と **Fact Internet Sales Count** のみを選択します。 **FactInternetSalesReason** にはただ 1 つのメジャーがあることから、このメジャーが自動的に選択されます。  
  
10. ディメンション リストで、 **Dim Sales Reason** と **Dim Sales Orders**が表示されます。  
  
     [新しいディメンションの選択] ページで、 **Fact Internet Sales Dimension**に対応する新しいディメンションを作成するように要求されます。 このディメンションは必要ないため、リストからこのディメンションをクリアできます。  
  
11. キューブに名前を付け、 **[完了]**をクリックします。  
  
#### <a name="step-3-define-many-to-many-relationship"></a>手順 3: 多対多リレーションシップの定義  
  
1.  キューブ デザイナーで、[ディメンションの使用法] タブをクリックします。**Dim Sales Reason** と **Fact Internet Sales**の間に、既に多対多アイコンがあることに注意してください。 次のアイコンが、多対多リレーションシップを示していることに注意してください。  
  
     ![ディメンションの使用法の多対多アイコン](../../analysis-services/multidimensional-models/media/ssas-m2m-icondimusage.png "多対多ディメンションの使用法のアイコン")  
  
2.  **Dim Sales Reason** と **Fact Internet Sales**の交差セルをクリックし、ボタンをクリックして [リレーションシップの定義] ダイアログ ボックスを開きます。  
  
     このダイアログ ボックスを使用して、多対多リレーションシップを指定できることがわかります。 代わりに、標準のリレーションシップを持つディメンションを追加する場合は、このダイアログ ボックスを使用して多対多に変更することになります。  
  
     ![ディメンションの使用法を定義するリレーションシップ ボタン](../../analysis-services/multidimensional-models/media/ssas-m2m-btndimusage.png "ディメンションの使用法 [リレーションシップの定義] ボタン")  
  
3.  プロジェクトを、Analysis Services 多次元インスタンスに配置します。 次の手順で、Excel でこのキューブを参照し、その動作を確認します。  
  
## <a name="testing-many-to-many"></a>多対多のテスト  
 キューブ内で多対多リレーションシップを定義する場合は、クエリが正しい結果を返すことを確認するために、テストが必要不可欠です。 エンド ユーザーが使用する予定のクライアント アプリケーション ツールで、キューブをテストする必要があります。 次の手順で、Excel を使用してキューブに接続し、クエリ結果を確認します。  
  
#### <a name="browse-the-cube-in-excel"></a>Excel 内でのキューブの参照  
  
1.  プロジェクトを配置し、キューブを参照して、集計が有効であることを確認します。  
  
2.  Excel で、**[データ]**  |  **[その他のデータソース]**  |  **[Analysis Services]** をクリックします。 サーバーの名前を入力し、データベースとキューブを選択します。  
  
3.  次のものを使用するピボットテーブルを作成します。  
  
    -   値として**Sales Amount**   
  
    -   列で**Sales Reason Name**   
  
    -   行で**Sales Order Number**   
  
4.  結果を分析します。 サンプル データを使用しているため、最初は、すべての販売注文が同じ値になっているという印象を受けます。 ただし、下へスクロールすると、データに差異があることに気が付きます。  
  
     途中まで進んだところで、注文番号 **SO5382**に対応する売上高と購入同期に気が付きます。 この特定の注文の総計は **539.99**であり、この注文に属する購入動機には、Promotion (プロモーション)、Other (その他)、および Price (価格) が含まれています。  
  
     ![多対多集計を示す Excel ワークシート](../../analysis-services/multidimensional-models/media/ssas-m2m-excel.png "多対多集計を示す Excel ワークシート")  
  
     この注文に対応する Sales Amount (売上高) が正確に計算され、注文全体で **539.99** であることがわかります。 動機ごとに **539.99** が示されていますが、3 つの値すべてに対してこの値が合計されて総合計を誤って膨張させることはありません。  
  
     各購入動機の下で、最初に売上高が配置されているのはなぜでしょうか。 そのように配置することにより、各動機に適用できる売上高を特定できるからです。  
  
5.  ワークシートの下端までスクロールします。 他の理由、および総計と比較すると、顧客の購入にとって最も重要な動機が Price (価格) であることがわかります。  
  
     ![多対多の合計を示す Excel ブック](../../analysis-services/multidimensional-models/media/ssas-m2m-excelgrandtotal.png "多対多の合計を示す Excel ブック")  
  
#### <a name="tips-for-handling-unexpected-query-results"></a>予期しないクエリ結果を処理するためのヒント  
  
1.  クエリで意味のある結果を返さない、カウントのような中間メジャー グループ内のメジャーを非表示にします。 この結果、ユーザーが意味のあるデータを作成する目的で集計などを使用することを防止できます。 メジャーを非表示にするには、ディメンション デザイナー内の属性で **Visibility** (表示) を **False** に設定します。  
  
2.  実行しようとする分析操作に役立つ一部のメジャーとディメンションを使用するために、パースペクティブを作成します。 キューブに含まれている多くのメジャー グループやディメンションは、あらゆる状況で互いに密接に関連するわけではありません。 組み合わせて使用することを意図しているディメンションとメジャー グループを特定することで、予測可能性の高い結果を生成できます。  
  
3.  モデルを変更した後、必ず配置と再接続を行ってください。 Excel で、リボンの [ピボットテーブル ツール] にある [更新] ボタンを使用します。  
  
4.  複数の多対多リレーションシップで、リンク メジャー グループを使用することは避けてください。特に、これらのリレーションシップが異なるキューブ内に存在する場合です。 このような方法で使用すると、あいまいな集計になります。 詳細については、「 [多対多リレーションシップを含むキューブでリンク メジャーの値が不適切](http://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx)」を参照してください。  
  
##  <a name="bkmk_Learn"></a> Learn more  
 以下のリンクを使用して、この内容を習得するのに役立つ詳細情報を参照してください。  
  
 [多対多の回転 2.0](http://go.microsoft.com/fwlink/?LinkId=324760)  
  
 [チュートリアル : SQL Server Analysis Services を対象とする多対多ディメンションの例](http://go.microsoft.com/fwlink/?LinkId=324761)  
  
## <a name="see-also"></a>参照  
 [ディメンション リレーションシップ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [Analysis Services 多次元モデリング チュートリアル用サンプル データとプロジェクトをインストールします。](../../analysis-services/install-sample-data-and-projects.md)   
 [Analysis Services プロジェクト &#40; を展開します。SSDT &#41;](../../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)   
 [多次元モデルのパースペクティブ](../../analysis-services/multidimensional-models/perspectives-in-multidimensional-models.md)  
  
  
