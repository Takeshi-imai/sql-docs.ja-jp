---
title: "ツールとアプローチの処理 (Analysis Services) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
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
- process [Analysis Services]
- processing [Analysis Services]
ms.assetid: 82347a16-4145-4655-8adf-2a300f1fdf99
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2cf9e507347a28aa36f96b1d2499ec0ff0ee741f
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="tools-and-approaches-for-processing-analysis-services"></a>処理するためのツールと方法 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
"処理" とは、Analysis Services がリレーショナル データ ソースにクエリを実行し、そのデータを使用して Analysis Services オブジェクトを設定する操作です。  
  
 Analysis Services のシステム管理者は、以下の方法で [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトの処理の実行と監視を行うことができます。  
  
-   オブジェクトの依存関係や操作のスコープを理解する影響分析の実行  
  
-   SQL Server Management Studio の個々のオブジェクトの処理 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   SQL Server Data Tools (SSDT) の個々のオブジェクトまたは複数のオブジェクトの処理 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   現在のアクションの結果として未処理となる関連オブジェクトの一覧を確認する影響分析の実行  
  
-   個々のオブジェクトまたは複数のオブジェクトを処理するために、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] XMLA クエリ ウィンドウでスクリプトを生成し、実行  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] PowerShell コマンドレットの使用  
  
-   制御フローとタスクで使用する [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージの使用  
  
-   SQL Server Profiler の処理の監視  
  
-   AMO を使用した、カスタム ソリューションのプログラム 詳細については、「 [AMO OLAP 基本オブジェクトのプログラミング](../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-olap-basic-objects.md)」を参照してください。  
  
 処理は、柔軟に構成できる操作で、オブジェクト レベルで発生する完全処理や増分処理の一連の処理オプションを使用して制御します。 オプションとオブジェクトの処理に関する詳細については、「[処理オプションと設定 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)」および「[Analysis Services オブジェクトの処理](../../analysis-services/multidimensional-models/processing-analysis-services-objects.md)」を参照してください。  
  
> [!NOTE]  
>  このトピックでは、多次元モデルを処理するためのツールと方法について説明します。 表形式モデルの処理の詳細については、次を参照してください。[データベースの処理、テーブル、またはパーティション &#40;です。Analysis Services &#41;](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md)と[データ処理](../../analysis-services/tabular-models/process-data-ssas-tabular.md)です。  
  
### <a name="processing-objects-in-sql-server-management-studio"></a>SQL Server Management Studio でのオブジェクトの処理  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を起動し、Analysis Services に接続します。  
  
2.  処理対象の Analysis Services オブジェクトを右クリックし、 **[処理]**をクリックします。 データ処理は、以下のレベルで行うことができます。  
  
    -   データベース  
  
    -   キューブ  
  
    -   メジャー グループ (またはメジャー グループ内の個々のパーティション)  
  
    -   ディメンション  
  
    -   [マイニング モデル]  
  
    -   マイニング構造  
  
     Analysis Services オブジェクトは階層構造になっています。 データベースを選択した場合、そのデータベースに格納されているすべてのオブジェクトに対して処理を適用することができます。 実際に処理が生じるかどうかは、選択した処理オプションとオブジェクトの状態によって異なります。 具体的には、親を処理すると、その子である (未処理の) オブジェクトも処理の対象となります。 オブジェクトの依存関係に関する詳細については、「 [Analysis Services オブジェクトの処理](../../analysis-services/multidimensional-models/processing-analysis-services-objects.md)」を参照してください。  
  
3.  **[処理]** ダイアログ ボックスの **[処理オプション]** で、表示されている既定値をそのまま使用するか、別のオプションを一覧から選択します。 各オプションの詳細については、「[処理オプションと設定 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)」を参照してください。  
  
4.  **[影響分析]** をクリックすると、[処理] ダイアログ ボックスに一覧表示されているオブジェクトが処理された場合に影響を受ける依存オブジェクトを識別し、オプションで処理できます。  
  
5.  必要に応じて、 **[設定の変更]** をクリックし、処理順序や特定の種類のエラーに関する処理の動作などの設定を変更します。  
  
6.  **[OK]**をクリックします。  
  
     [処理の進行状況] ダイアログ ボックスに、各コマンドの進行状況が表示されます。 ステータス メッセージが切り詰められている場合は、 **[詳細表示]** をクリックすると、メッセージ全体を確認できます。  
  
### <a name="processing-objects-in-sql-server-data-tools"></a>SQL Server データ ツールでのオブジェクトの処理  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を起動し、配置されているプロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、配置されたプロジェクトの **[ディメンション]** フォルダーを展開します。  
  
3.  ディメンションを右クリックし、 **[プロセス]**をクリックします。 複数のディメンションを右クリックして、一度に複数のオブジェクトを処理することができます。 詳細については、「[バッチ処理 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/batch-processing-analysis-services.md)」を参照してください。  
  
4.  **[ディメンションの処理]** ダイアログ ボックスにある **[オブジェクト一覧]** の **[処理オプション]** 列で、この列のオプションが **[完全処理]** であることを確認します。 別のオプションが設定されている場合、 **[処理オプション]**列のオプションをクリックし、表示される一覧から **[完全処理]** を選択します。  
  
5.  **[実行]**をクリックします。  
  
6.  処理が完了したら、 **[閉じる]**をクリックします。  
  
##  <a name="bkmk_impactanalysis"></a> オブジェクトの依存関係や操作のスコープを識別する影響分析の実行  
  
1.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] のいずれかの [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]オブジェクトを処理する前に、 **[処理オブジェクト]** ダイアログ ボックスの **[影響分析]** をクリックして、関連オブジェクトへの影響を分析できます。  
  
2.  ディメンション、キューブ、メジャー グループ、またはパーティションを右クリックし、 **[処理オブジェクト]** ダイアログ ボックスを開きます。  
  
3.  **[影響の分析]**をクリックします。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、モデルをスキャンし、処理対象として選択したオブジェクトに関連するオブジェクトの再処理の要件をレポートします。  
  
### <a name="processing-objects-using-xmla"></a>XMLA を使用したオブジェクトの処理  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を起動し、Analysis Services に接続します。  
  
2.  処理するオブジェクトを右クリックし、 **[処理]**をクリックします。  
  
3.  **[処理]** ダイアログ ボックスで、使用する処理オプションを選択します。 必要に応じて他の設定も変更します。 必要な変更は、影響分析を実行して特定できます。  
  
4.  **[処理オブジェクト]** ダイアログ ボックスの **[スクリプト]** をクリックします。  
  
     これにより、XMLA スクリプトが生成され、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA クエリ ウィンドウが表示されます。  
  
5.  ダイアログ ボックスを閉じます。 スクリプトには、処理コマンドとダイアログ ボックスで指定したオプションが含まれます。  
  
6.  同じバッチ内で他のオブジェクトを処理する場合は、スクリプトに続けて追加できます。 続行するには、前の手順を繰り返し、生成されたスクリプトを追加します。それにより、すべての処理操作を行う 1 つのスクリプトを作成できます。 例を表示するには、「 [SQL Server エージェントで SSAS 管理タスクのスケジュール設定を行う](../../analysis-services/instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)」を参照してください。  
  
7.  メニュー バーの **[クエリ]**をクリックし、 **[実行]**をクリックします。  
  
### <a name="processing-objects-using-powershell"></a>PowerShell を使用したオブジェクトの処理  
  
1.  このリリースの SQL Server からは、オブジェクトの処理に、Analysis Services PowerShell コマンドレットを使用できるようになりました。 対話形式またはスクリプトで、次のコマンドレットを実行できます。  
  
    -   [Invoke-ProcessCube コマンドレット](../../analysis-services/powershell/invoke-processcube-cmdlet.md)  
  
    -   [Invoke-ProcessDimension コマンドレット](../../analysis-services/powershell/invoke-processdimension-cmdlet.md)  
  
    -   [Invoke-ProcessPartition コマンドレット](../../analysis-services/powershell/invoke-processpartition-cmdlet.md)  
  
    -   [Invoke-ASCmd コマンドレット](../../analysis-services/powershell/invoke-ascmd-cmdlet.md): 処理コマンドを含んだ XMLA、MDX、または DMX スクリプトを実行するときに使用します。  
  
### <a name="monitoring-object-processing-using-sql-server-profiler"></a>SQL Server Profiler を使用したオブジェクトの処理の監視  
  
1.  SQL Server Profiler で Analysis Services インスタンスに接続します。  
  
2.  [イベントの選択] で、 **[すべてのイベントを表示する]** をクリックしてすべてのイベントをリストに追加します。  
  
3.  次のイベントを選択します。  
  
    -   処理の開始時刻と停止時刻を表示するには、**[コマンド開始]** と **Commと End** to show when processing starts と stops  
  
    -   すべてのエラーをキャプチャするには、**[エラー]**   
  
    -   処理の状態をレポートし、データを取得するために使用した SQL クエリを表示するには、**[進行状況レポートの開始]**, **[進行状況レポートの現在の状態]**、および **[進行状況レポートの終了]**   
  
    -   キューブの計算を表示するには、**[MDX スクリプトの実行の開始]** および **[MDX スクリプトの実行の終了]**   
  
    -   処理に関連するパフォーマンスの問題を診断する場合は、必要に応じて、ロック イベントを追加する  
  
### <a name="process-analysis-services-objects-using-integration-services"></a>Integration Services を使用して、Analysis Services オブジェクトを処理する  
  
1.  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]で Analysis Services 処理タスクを使用するパッケージを作成して、ソース リレーショナル データベースの定期更新を実行するときに、オブジェクトに新しいデータを自動的に設定できます。  
  
2.  **[SSIS ツールボックス]**で **[Analysis Services 処理]** をダブルクリックしてパッケージに追加します。  
  
3.  オブジェクトを処理するデータベースへの接続を指定するタスク、および処理のオプションを編集します。 このタスクの実装方法については、「 [Analysis Services 処理タスク](../../integration-services/control-flow/analysis-services-processing-task.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [多次元モデルの処理 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)  
  
  
