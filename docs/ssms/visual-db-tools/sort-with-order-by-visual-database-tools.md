---
title: "ORDER BY 句での並べ替え (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ORDER BY clause [Visual Database Tools]
ms.assetid: 459f5640-8058-4c24-97e7-7bbd6168bc39
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 42bffc99ff8a14f31e3d5f4ed40cb8c0c93a43c5
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="sort-with-order-by-visual-database-tools"></a>ORDER BY 句での並べ替え (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] ORDER BY 句を使用すると、返される行内のクエリの結果を、1 つまたは複数の列を使用して並べ替えることができます。 ORDER BY 句は、抽出条件ペインでオプションを選択することによって定義できます。  
  
### <a name="to-sort-a-query-using-an-order-by-clause"></a>ORDER BY 句を使用してクエリを並べ替えるには  
  
1.  クエリを開くか、新規作成します。  
  
2.  [抽出条件ペイン](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)で、クエリ結果の並べ替えに使用する列に対応する行の **[並べ替えの種類]** 列をクリックします。  
  
3.  ドロップダウン リストから、 *[昇順]* または *[降順]* を選択します。  
  
> [!NOTE]  
> 列の **[並べ替えの種類]** のエントリを削除すると、その列が ORDER BY 句から削除されます。  
  
抽出条件ペインで操作を行うと、最後に行った操作に合わせてクエリの UNION 句が変化します。  
  
> [!NOTE]  
> 複数の列を使用して結果を並べ替えるときは、 **[並べ替え順序]** 列を使用して、列を検索する順序を互いの列を基準にして指定します。 詳細については、「 **クエリ内の複数の列を並べ替える方法**」をご覧ください。  
  
## <a name="see-also"></a>参照  
[クエリ結果の並べ替えおよびグループ化 (Visual Database Tools)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[クエリ結果の要約 (Visual Database Tools)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
