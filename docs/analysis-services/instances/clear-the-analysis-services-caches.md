---
title: "Analysis Services キャッシュのクリア |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6bf66fdd-6a03-4cea-b7e2-eb676ff276ff
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 19055dc68ebd1e9baa2fa1b1330370d01f7d864a
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="clear-the-analysis-services-caches"></a>Analysis Services キャッシュのクリア
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Analysis Services は、クエリのパフォーマンス向上のためにデータをキャッシュします。 このトピックでは、MDX クエリへの応答で作成されたキャッシュを、XMLA ClearCache コマンドを使用してクリアするための推奨事項について説明します。 ClearCache を実行した場合の効果は、テーブル モデルまたは多次元モデルのどちらを使用しているかによって異なります。  
  
 **多次元モデルのキャッシュをクリアする場合**  
  
 多次元データベースの場合、Analysis Services は、計算を評価する際、数式エンジン内にキャッシュを構築し、ディメンション クエリやメジャー グループ クエリの結果に対しては、ストレージ エンジン内にキャッシュを構築します。 メジャー グループ クエリは、数式エンジンがセル座標またはサブキューブのデータを測定する必要がある場合に発生します。 ディメンション クエリは、不自然階層をクエリするときや、autoexists を適用するときに発生します。  
  
 パフォーマンス テストを実施する場合、キャッシュをクリアすることをお勧めします。 次回のテスト実行までの間にキャッシュをクリアすることで、クエリ デザインの変更による影響を計測するテストの結果が、キャッシュによってゆがめられないようにすることができます。  
  
 **テーブル モデルのキャッシュをクリアする場合**  
  
 一般的にテーブル モデルはメモリに保存されます。クエリが実行されるとき、集計やその他の計算はメモリで実行されます。 そのため、ClearCache コマンドがテーブル モデルに与える影響は限定的です。 テーブル モデルでは、MDX クエリが実行される場合、そのデータが Analysis Services キャッシュに追加されます。 特に、MDX によって参照される DAX メジャーおよび autoexists 操作は、結果を数式キャッシュおよびディメンション キャッシュ内にそれぞれキャッシュできます。 ただし、不自然階層とメジャー グループ クエリは、ストレージ エンジン内にキャッシュしないことに注意してください。 また、重要な点は、DAX クエリは、数式エンジンおよびストレージ エンジン内に結果をキャッシュしないことです。 MDX クエリの結果としてキャッシュが存在する限り、テーブル モードに対する ClearCache の実行は、システムからのすべてのキャッシュ データを無効にします。  
  
 また、ClearCache を実行すると、xVelocity メモリ内分析エンジン (VertiPaq) のメモリ内キャッシュもクリアされます。 xVelocity エンジンは、キャッシュされた小さな結果セットを保持します。 ClearCache を実行すると、xVelocity エンジンのキャッシュも無効化されます。  
  
 最後に、ClearCache を実行すると、テーブル モデルが **DirectQuery** モード用に再構築されるときにメモリ内の残存データも削除されます。 これは、厳密に管理される機密データがモデルに含まれる場合、特に重要です。 この場合、ClearCache の実行は、機密データが想定した場所にのみ存在することを確実にするための予防的なアクションとなります。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用してモデルを配置し、クエリ モードを変更する場合、キャッシュは手動でクリアする必要があります。 一方、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] を使用して、モデルに **DirectQuery** を指定した場合、そのクエリ モードを使用するようにモデルを切り替えると、パーティションが自動的にキャッシュをクリアします。  
  
 多次元モデルのキャッシュをパフォーマンス テスト中にクリアするための推奨事項と比べると、テーブル モデルのキャッシュをクリアするための推奨事項はあまり多くありません。 機密データを含むテーブル モデルの配置を管理していない場合は、キャッシュをクリアするために実施される特定の管理タスクはありません。  
  
## <a name="clear-the-cache-for-analysis-services-models"></a>Analysis Services モデルのキャッシュをクリアする  
 キャッシュをクリアするには、XMLA と [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用します。 データベース、キューブ、ディメンション、テーブルのキャッシュ、またはメジャー グループ レベルのキャッシュをクリアできます。 次の手順は、データベース レベルでキャッシュをクリアするために、多次元モデルとテーブル モデルの両方に適用されます。  
  
> [!NOTE]  
>  厳密なパフォーマンス テストを実施するには、より包括的なキャッシュをクリアする手法が必要です。 Analysis Services とファイル システム キャッシュをフラッシュする方法については、「 [SQL Server 2008 R2 Analysis Services 操作ガイド](http://go.microsoft.com/fwlink/?linkID=http://go.microsoft.com/fwlink/?LinkID=225539)」のキャッシュのクリアに関するセクションを参照してください。  
  
 多次元モードとテーブル モードの両方に対して、これらのキャッシュをクリアするには、ClearCache が実行された時点でキャッシュを無効にし、その後、次のクエリを受信したときに、そのキャッシュを空にするという 2 段階の処理を行います。 キャッシュが実際に空になると、メモリの消費量の削減が明らかになります。  
  
 キャッシュをクリアするには、XMLA クエリの **ClearCache** ステートメントに、オブジェクトの識別子を指定する必要があります。 このトピックの最初のステップでは、オブジェクト識別子を取得する方法を説明します。  
  
#### <a name="step-1-get-the-object-identifier"></a>手順 1: オブジェクトの識別子を取得する  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でオブジェクトを右クリックし、 **[プロパティ]**を選択して、 **[プロパティ]** ペインの ID プロパティの値をコピーします。 この方法は、データベース、キューブ、ディメンション、またはテーブルに使用できます。  
  
2.  メジャー グループの ID を取得するには、メジャー グループを右クリックし、 **[メジャー グループをスクリプト化]**を選択します。 **[作成]** または **[変更]**のいずれかを選択し、クエリをウィンドウに送信します。 メジャー グループの ID は、オブジェクト定義に表示されます。 オブジェクト定義の ID をコピーします。  
  
#### <a name="step-2-run-the-query"></a>手順 2: クエリを実行する  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でデータベースを右クリックし、 **[新しいクエリ]**をポイントして、 **[XMLA]**を選択します。  
  
2.  XMLA クエリ ウィンドウに次のコードをコピーします。 **DatabaseID** を現在の接続のデータベース ID に変更します。  
  
    ```  
    <ClearCache xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
      <Object>  
        <DatabaseID> Adventure Works DW Multidimensional</DatabaseID>  
      </Object>  
    </ClearCache>  
  
    ```  
  
     または、メジャー グループなどの子オブジェクトのパスを指定して、そのオブジェクトのキャッシュだけをクリアすることもできます。  
  
    ```  
    <ClearCache xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
            <CubeID>Adventure Works</CubeID>  
            <MeasureGroupID>Fact Currency Rate</MeasureGroupID>  
      </Object>  
    </ClearCache>  
    ```  
  
3.  F5 キーを押してクエリを実行します。 次の結果を確認してください。  
  
    ```  
    <return xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <root xmlns="urn:schemas-microsoft-com:xml-analysis:empty" />  
    </return>  
    ```  
  
## <a name="see-also"></a>参照  
 [Analysis Services インスタンスを監視します。](../../analysis-services/instances/monitor-an-analysis-services-instance.md)  
  
  
