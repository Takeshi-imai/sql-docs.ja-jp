---
title: "チュートリアル: 作成、オフライン クイック グラフ レポート (レポート ビルダー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reports, creating
- tutorials, getting started
- creating reports
ms.assetid: 6b1db67a-cf75-494c-b70c-09f1e6a8d414
caps.latest.revision: 31
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: a09ebdeda6679c80f3eb32602d38068114e7bf36
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---

# <a name="tutorial-create-a-quick-chart-report-offline-report-builder"></a>チュートリアル: オフラインでのクイック グラフ レポートの作成 (レポート ビルダー)

  このチュートリアルでは、ウィザードを使用して、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] で [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]の改ページ調整されたレポートに円グラフを作成します。 次に、パーセンテージを追加し、円グラフを少し変更します。 
  
このチュートリアルは 2 つの異なる方法で実行できます。 どちらの方法でも、次の図に示すような円グラフが作成されます。  
  
 ![レポート ビルダー クイック円グラフ](../../reporting-services/report-builder/media/report-builder-quick-pie-chart.png "クイック円グラフをレポート ビルダー")  
  
## <a name="prerequisites"></a>前提条件  
 XML データを使用するかどうかまたは[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリ、レポート ビルダーにアクセスする必要があります。 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] は、ネイティブ モードまたは SharePoint 統合モードで [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] から起動するか、Microsoft ダウンロード センターから [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] をダウンロードできます。 詳細については、「 [Install Report Builder](../../reporting-services/install-windows/install-report-builder.md)」を参照してください。  
  
##  <a name="TwoWays"></a> このチュートリアルを実行する 2 つの方法  
  
-   [XML データを使用して円グラフを作成する](#CreatePieChartXML)  
  
-   [データを含む TRANSACT-SQL クエリを使用して円グラフを作成します。](#CreatePieQueryData)  
  
### <a name="using-xml-data-for-this-tutorial"></a>このチュートリアルでの XML データの使用  
 このトピックからコピーしてウィザードに貼り付けた XML データを使用できます。 接続する必要はありません、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]レポート サーバーのネイティブ モードまたは SharePoint 統合モード、および SQL Server のインスタンスにアクセスする必要はありません。  
  
 [XML データを使用して円グラフを作成する](#CreatePieChartXML)  
  
### <a name="using-a-includetsqlincludestsql-mdmd-query-that-contains-data-for-this-tutorial"></a>このチュートリアル用のデータを含む [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを使用する  
 データを含むクエリをこのトピックからコピーし、ウィザードに貼り付けることができます。 資格情報および SQL Server のインスタンスの名前を任意のデータベースに読み取り専用アクセスのための十分な必要があります。 チュートリアルのデータセット クエリは、リテラル データを使用しますが、レポート データセットに必要なメタデータを返す SQL Server のインスタンスでクエリを処理する必要があります。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを使用する利点は、 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] の他のすべてのチュートリアルで同じ方法が使用されているため、他のチュートリアルを実行するときに既に手順がわかっていることです。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリの場合、他にもいくつか必要な前提条件があります。 詳細については、「[チュートリアルの前提条件 &#40;レポート ビルダー&#41;](../../reporting-services/prerequisites-for-tutorials-report-builder.md)」を参照してください。  
  
 [データを含む TRANSACT-SQL クエリを使用して円グラフを作成します。](#CreatePieQueryData)  
  
##  <a name="CreatePieChartXML"></a> XML データを使用して円グラフを作成する  
  
1.  [Web ポータル、SharePoint 統合モードのレポート サーバー、またはコンピューターから、](../../reporting-services/report-builder/start-report-builder.md) レポート ビルダーを起動します [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。  
  
     **[作業の開始]** ダイアログ ボックスが表示されます。  
  
     ![レポート ビルダーを開始](../../reporting-services/media/rb-getstarted.png "レポート ビルダーを開始")  
  
     場合、**作業の開始** ダイアログ ボックスが表示されないをクリックして**ファイル** >**新規**です。 **[新しいレポートまたはデータセット]** ダイアログ ボックスは、 **[作業の開始]** ダイアログ ボックスとほぼ同じ内容です。  
  
2.  左ペインで、 **[新しいレポート]** が選択されていることを確認します。  
  
3.  右ペインで、 **[グラフ ウィザード]**をクリックし、 **[作成]**をクリックします。  
  
4.  **[データセットの選択]** ページで **[データセットを作成する]**をクリックし、 **[次へ]**をクリックします。  
  
5.  **[データ ソースへの接続の選択]** ページで **[新規作成]**をクリックします。  
  
     **[データ ソースのプロパティ]** ダイアログ ボックスが表示されます。  
  
6.  データ ソースに任意の名前を付けることができます。 **[名前]** ボックスに、「 **MyPieChart**」と入力します。  
  
7.  **[接続の種類の選択]** ボックスで、 **[XML]**をクリックします。  
  
8.  クリックして、**資格情報**] タブで [**を使用して現在の Windows ユーザーです。Kerberos 委任が必要になる**、クリックして**OK**です。  
  
9. **[データ ソースへの接続の選択]** ページで **[MyPieChart]**をクリックし、 **[次へ]**をクリックします。  
  
10. 次のテキストをコピーして、 **[クエリのデザイン]** ページの上部の大きいボックスに貼り付けます。  
  
    ```  
    <Query>  
    <ElementPath>Root /S  {@Sales (Integer)} /C {@FullName} </ElementPath>  
    <XmlData>  
    <Root>  
    <S Sales="150">  
      <C FullName="Jae Pak" />  
    </S>  
    <S Sales="350">  
      <C FullName="Jillian  Carson" />  
    </S>  
    <S Sales="250">  
      <C FullName="Linda C Mitchell" />  
    </S>  
    <S Sales="500">  
      <C FullName="Michael Blythe" />  
    </S>  
    <S Sales="450">  
      <C FullName="Ranjit Varkey" />  
    </S>  
    </Root>  
    </XmlData>  
    </Query>  
    ```  
  
11. (省略可能)クリックして、**実行**ボタン (**!**)、グラフの基になるデータを表示します。  
  
     ![レポート ビルダー クエリをデザイン](../../reporting-services/report-builder/media/rb-designquery.png "レポート ビルダー クエリをデザイン")  
  
12. **[次へ]**をクリックします。  
  
13. **[グラフの種類の選択]** ページで **[円]**をクリックし、 **[次へ]**をクリックします。  
  
14. **グラフのフィールドの配置** ページをダブルクリックして、 **Sales**フィールドで、**利用可能なフィールド**ボックス。  
  
     このフィールドは数値なので、 **[値]** ボックスに自動的に移動します。  
  
     ![レポート ビルダー ウィザード フィールドの配置](../../reporting-services/report-builder/media/rb-wizarrangefields.png "レポート ビルダー ウィザード フィールドの配置")  
  
15. ドラッグ、 **FullName**フィールドを**利用可能なフィールド**ボックスを**カテゴリ**ボックス (またはそれをダブルクリックして; に移動、**カテゴリ**ボックス)、をクリックし、 **[次へ]**です。  
  
     [プレビュー] ページには、主要なデータの新しい円グラフが表示されます。 凡例には販売員の名前ではなく Full Name 1、Full Name 2 などが示されており、円のスライスのサイズは正確ではありません。 これは、レポートがどのように表示されるか概要を見るためだけのものです。  
  
     ![レポート ビルダーは、プレビューを新しいグラフ](../../reporting-services/report-builder/media/rb-newchartpreview.png "レポート ビルダーの新しいグラフのプレビュー")  
  
16. **[完了]**をクリックします。  
  
     主要なデータのまま、デザイン ビューに新しい円グラフ レポートが表示されます。  
  
     ![レポート ビルダーのデザイン ビューでの新しい円グラフ](../../reporting-services/report-builder/media/rb-newpiedesign.png "レポート ビルダーのデザイン ビューでの新しい円グラフ")  
  
17. 実際の円グラフを表示するには、リボンの **[ホーム]** タブで **[実行]** をクリックします。  
  
     ![レポート ビルダーが実行を新しいグラフ](../../reporting-services/report-builder/media/rb-newchartrun.png "レポート ビルダーの新しいグラフの実行")  
  
18. 円グラフの変更を続けるには、この記事の「 [ウィザードの実行後](#AfterWizard) 」に進んでください。  
  
##  <a name="CreatePieQueryData"></a>[!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを使用して円グラフを作成する  
  
1.  [Web ポータル、SharePoint 統合モードのレポート サーバー、またはコンピューターから、](../../reporting-services/report-builder/start-report-builder.md) レポート ビルダーを起動します [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。  
  
     **[作業の開始]** ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  場合、**作業の開始** ダイアログ ボックスが表示されないをクリックして**ファイル** >**新規**です。 **[新しいレポートまたはデータセット]** ダイアログ ボックスは、 **[作業の開始]** ダイアログ ボックスとほぼ同じ内容です。  
  
2.  左ペインで、 **[新しいレポート]** が選択されていることを確認します。  
  
3.  右ペインで、 **[グラフ ウィザード]**をクリックし、 **[作成]**をクリックします。  
  
4.  **[データセットの選択]** ページで **[データセットを作成する]**をクリックし、 **[次へ]**をクリックします。  
  
5.  **[データ ソースへの接続の選択]** ページで、既存のデータ ソースを選択するか、レポート サーバーを参照してデータ ソースを選択し、 **[次へ]**をクリックします。 ユーザー名とパスワードの入力が必要な場合があります。  
  
    > [!NOTE]  
    >  適切な権限を持っている限り、選択するデータ ソースは重要ではありません。 データ ソースからはデータを取得しません。 詳細については、「[チュートリアルの前提条件 &#40;レポート ビルダー&#41;](../../reporting-services/prerequisites-for-tutorials-report-builder.md)」を参照してください。  
  
6.  **[クエリのデザイン]** ページで、 **[テキストとして編集]**をクリックします。  
  
7.  次のクエリをクエリ ペインに貼り付けます。  
  
    ```  
    SELECT 150 AS Sales, 'Jae Pak' AS FullName   
    UNION SELECT 350 AS Sales, 'Jillian Carson' AS FullName   
    UNION SELECT 250 AS Sales, 'Linda C Mitchell' AS FullName   
    UNION SELECT 500 AS Sales, 'Michael Blythe' AS FullName   
    UNION SELECT 450 AS Sales, 'Ranjit Varkey' AS FullName   
    ```  
  
8.  (省略可) [実行] ボタン (**!**) をクリックして、グラフの基になるデータを確認します。  
  
9. **[次へ]**をクリックします。  
  
10. **[グラフの種類の選択]** ページで **[円]**をクリックし、 **[次へ]**をクリックします。  
  
11. **グラフのフィールドの配置** ページをダブルクリックして、 **Sales**フィールドで、**利用可能なフィールド**ボックス。  
  
     このフィールドは数値なので、 **[値]** ボックスに自動的に移動します。  
  
12. ドラッグ、 **FullName**フィールドを**利用可能なフィールド**ボックスを**カテゴリ**ボックス (またはそれをダブルクリックして; に移動、**カテゴリ**ボックス)、をクリックし、 **[次へ]**です。  
  
13. **[完了]**をクリックします。  
  
     デザイン画面に、新しい円グラフ レポートが表示されます。 表示内容は見本です。 凡例には販売員の名前ではなく Full Name 1、Full Name 2 などが示されており、円のスライスのサイズは正確ではありません。 これは、レポートがどのように表示されるか概要を見るためだけのものです。  
  
15. 実際の円グラフを表示するには、リボンの **[ホーム]** タブで **[実行]** をクリックします。  
 
##  <a name="AfterWizard"></a> ウィザードの実行後  
 円グラフ レポートが完成したので、操作してみます。 変更を続行するには、リボンの **[実行]** タブで **[デザイン]**をクリックします。  
  
## <a name="make-the-chart-bigger"></a>グラフの拡大  
 円グラフを拡大するには、 
 
*  グラフ内の要素ではなくグラフをクリックして選択し、右下隅をドラッグしてサイズを変更します。  

デザイン画面はドラッグすると拡大することに注意してください。
  
## <a name="add-a-report-title"></a>レポート タイトルの追加  
1. グラフ上部の **[グラフのタイトル]** というテキストを選択し、「 **Sales Pie Chart**」などのタイトルを入力します。  
2. プロパティ ペインで選択したタイトルの変更**色**に**黒**と**FontSize**に**12 pt**です。
  
## <a name="add-percentages"></a>パーセンテージの追加  
 
1.  円グラフを右クリックし **データ ラベルを表示**です。 円グラフの各スライス内にデータ ラベルが表示されます。  
  
2.  ラベルを右クリックし **系列ラベルのプロパティ**です。 **[系列ラベルのプロパティ]** ダイアログ ボックスが表示されます。  
  
3.  **データ ラベル**ボックスに、入力**#PERCENT {P0}**です。  
  
     **{P0}** を指定すると、小数点以下を含まないパーセンテージが表示されます。 だけ入力すると**#PERCENT**、含む小数点以下 2 桁の数値になります。 **#PERCENT**キーワードを計算または関数を実行するその他の多くではありません。 します。  
     
4. **[はい]** をクリックして、 **[UseValueAsLabel]** を **False**に設定することを確認します。

5. **[フォント]** タブで、 **[太字]** を選択し、 **[色]** を **[白]**に変更します。

6. **[OK]**をクリックします。     
  
 グラフのラベルと凡例をカスタマイズする方法の詳細については、「[円グラフへのパーセンテージの表示 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)」および「[凡例アイテムのテキストの変更 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/chart-legend-change-item-text-report-builder.md)」を参照してください。  
  
##  <a name="WhatsNext"></a> 次の課題  
 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]でレポートを初めて自分で作成したので、他のチュートリアルに取り組んで独自のデータからレポートを作成する準備ができました。 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]を実行するには、データベースなどのデータ ソースにアクセスする権限と、実際にデータ ソースに接続するための *接続文字列*が必要です。 システム管理者がこの情報を保持し、ユーザーを設定できます。  
  
 その他のチュートリアルを進めるには、任意のデータベースに読み取り専用アクセスのための十分な資格情報および SQL Server のインスタンスの名前が必要です。 これもシステム管理者が設定できます。  
  
 最後に、レポートをレポート サーバーまたはレポート サーバーと統合されている SharePoint サイトに保存するには、URL と権限が必要です。 作成したレポートは自分のコンピューターから直接実行できますが、レポート サーバーまたは SharePoint サイトから実行するとレポートの機能が増えます。 自分のレポートまたはその他のレポートをパブリッシュ元のレポート サーバーまたは SharePoint サイトから実行する権限が必要です。 アクセス権を取得するには、システム管理者に問い合わせてください。  
  
 開始する前に、いくつかの概念や用語について確認しておくと役立つ場合があります。 参照してください[レポート オーサリングの概念と #40 です。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/report-authoring-concepts-report-builder-and-ssrs.md). また、レポートを初めて自分で作成する前に、計画の時間を取ってください。 時間を費やす価値があります。 「[レポートの計画 &#40;レポート ビルダー&#41;](../../reporting-services/report-design/planning-a-report-report-builder.md)」を参照してください。  

## <a name="next-steps"></a>次の手順

[レポート ビルダー チュートリアル](../../reporting-services/report-builder-tutorials.md)   
[SQL Server 2016 のレポート ビルダー](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md)  

その他のご不明な点は、 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)