---
title: "[結合] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs"
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
f1_keywords:
- vdt.ppg.joinline
- vdtsql.chm:69638
ms.assetid: 0d9516bb-4ad3-4fcf-bb77-93474dea698f
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 65ee5adf9736860cd9cd9e8e75d6ff387af84348
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="join-dialog-box-visual-database-tools"></a>[結合] ダイアログ ボックス (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] このダイアログ ボックスを使用すると、テーブルを結合するオプションを指定できます。 このダイアログにアクセスするには、 **[デザイン]** ペインで結合線を選択します。 次に、 **[プロパティ]** ウィンドウの **[結合条件と種類]**をクリックして、プロパティの右側に表示される省略記号 ( **[...]** ) をクリックします。  
  
既定では、関連するテーブルは内部結合によって結合されます。この場合、結合列に一致した情報を含んでいる行に基づいて、結果セットが作成されます。 **[結合]** ダイアログ ボックスのオプションを設定することにより、別の演算子に基づいて結合を指定したり、外部結合を指定したりできます。  
  
テーブルの結合の詳細については、「 [結合を使用したクエリ (Visual Database Tools)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)」を参照してください。  
  
## <a name="options"></a>および  
  
|**項目**|**定義**|  
|------------|------------------|  
|**Table**|結合するテーブルまたはテーブル値オブジェクトの名前です。 ここではテーブルの名前は変更できません。この情報は参照用としてのみ表示されます。|  
|**列**|テーブルの結合に使用する列の名前です。 演算子一覧の演算子によって、列のデータ間の関係を指定します。 ここでは列の名前は変更できません。この情報は参照用としてのみ表示されます。|  
|**[演算子]**|結合列を関連付けるために使用する演算子を指定します。 等号 (=) 以外の演算子を指定する場合は、一覧で選択します。 プロパティ ページを閉じると、選択した演算子が結合線の菱形記号の中に次のように表示されます。<br /><br />![Visual Database Tools のアイコン](../../ssms/visual-db-tools/media/dv3wbii.gif "Visual Database Tools のアイコン")|  
|**次のすべての行: <table1>**|右側のテーブルに対応する一致がない場合でも、左側のテーブルのすべての行を出力に含めるように指定します。 右側のテーブルに一致するデータのない列は、NULL として出力されます。 このオプションを選択することは、SQL ステートメントで LEFT OUTER JOIN を指定することと同じです。|  
|**次のすべての行: <table2>**|左側のテーブルに対応する一致がない場合でも、右側のテーブルのすべての行を出力に含めるように指定します。 左側のテーブルに一致するデータのない列は、NULL として出力されます。 このオプションを選択することは、SQL ステートメントで RIGHT OUTER JOIN を指定することと同じです。|  
  
**[<table1> のすべての行]** と **[<table2> のすべての行]** の両方を選択することは、SQL ステートメントで FULL OUTER JOIN を指定することと同じです。  
  
外部結合を作成するためにオプションを選択すると、結合線中の菱形記号が変化して、結合が LEFT OUTER、RIGHT OUTER、FULL OUTER のいずれであるかを示します。  
  
> [!NOTE]  
> この "LEFT" や "RIGHT" という単語は、必ずしも [ダイアグラム] ペイン内のテーブルの位置に対応しません。 "LEFT" とは、SQL ステートメントでキーワード JOIN の左側に名前が記述されるテーブルを示し、"RIGHT" とは、SQL ステートメントでキーワード JOIN の右側に名前が記述されるテーブルを示しています。 **[ダイアグラム]** ペイン内でテーブルを移動しても、この意味でのテーブルの左右が入れ替わることはありません。  
  
## <a name="see-also"></a>参照  
[結合を使用したクエリ (Visual Database Tools)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
[クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
