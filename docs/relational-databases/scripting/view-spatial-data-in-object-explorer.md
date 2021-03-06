---
title: "オブジェクト エクスプローラーでの空間データの表示 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d8f01e7e2e0d13d80e3289f5da90b112f5806a6f
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="view-spatial-data-in-object-explorer"></a>オブジェクト エクスプローラーでの空間データの表示
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] クエリ エディターの **[空間結果]** ウィンドウには、**[結果]** ウィンドウにグリッド形式で表示されるデータに加えて、空間データ結果を表示するための視覚的なマッピング ツールが用意されています。 **[空間結果]** ウィンドウに空間データを表示するには、geometry 型または geography 型のデータを含む空間データ列が少なくとも 1 つクエリ結果に含まれている必要があります。  
  
### <a name="to-view-spatial-data-in-the-spatial-results-window"></a>[空間結果] ウィンドウに空間データを表示するには  
  
1.  クエリ エディターで、 **[空間結果]** タブをクリックします。  
  
    > [!NOTE]  
    >  クエリ結果に空間データが含まれていない場合、または結果がテキストとして返されるように指定した場合、このウィンドウは使用できません。  
  
2.  **[空間列の選択]** の一覧から、表示する列を選択します。 テーブル内に空間列が 1 つしかない場合は、この列が一覧の既定のオプションです。  
  
3.  **[ラベル列の選択]** の一覧から、データ ラベルとして使用する、空間列以外の列を選択します。  
  
4.  **[投影の選択]** の一覧から、geography 型のデータに使用する投影法を選択します。 既定の投影法は正距円筒図法です。その他に、メルカトル図法、ロビンソン図法、およびボンヌ図法という投影法を使用できます。  
  
    > [!NOTE]  
    >  空間列に geometry 型のデータが含まれている場合、**[投影の選択]** は使用できません。  
  
5.  **[ズーム]** スライダーを調整して、マップされた要素の視覚的なサイズを大きくします。 多角形の場合、ラベルが表示されるのは、図形がラベルのテキストを保持するのに十分な大きさの場合だけです。  
  
## <a name="see-also"></a>参照  
 [[空間結果] ウィンドウ](../../relational-databases/scripting/spatial-results-window.md)   
 [データベース エンジン クエリ エディター &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)   
 [クエリおよびテキスト エディター &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
