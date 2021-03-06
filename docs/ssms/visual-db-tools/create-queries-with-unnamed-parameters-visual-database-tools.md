---
title: "無名のパラメーターを使用したクエリの作成 (Visual Database Tools) | Microsoft Docs"
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
helpviewer_keywords:
- unnamed parameters
- parameters [SQL Server], unnamed
ms.assetid: 5f4b664b-3d3d-4d07-a0e7-791d78743504
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 33e5ffe37109fa5d1f5f85ed7c6ef9689aa01ec3
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="create-queries-with-unnamed-parameters-visual-database-tools"></a>無名のパラメーターを使用したクエリの作成 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] リテラル値のプレースホルダーとして疑問符 (?) を指定すると、無名のパラメーターを持つクエリを作成できます。 クエリおよびビュー デザイナーにより、一時的な名前が指定されます。 クエリには、必要な数の無名のパラメーターを指定できます。  
  
クエリおよびビュー デザイナーでクエリを実行すると、一時的な名前と共に [クエリ パラメーター] ダイアログ ボックスが表示されます。  
  
### <a name="to-specify-an-unnamed-parameter"></a>無名のパラメーターを指定するには  
  
1.  検索する列または式を [抽出条件ペイン](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)に追加します。 検索列または検索式をクエリ出力に表示しない場合は、出力列から削除します。  
  
2.  検索するデータ列または式を含む行を選択し、 **[フィルター]** グリッド列に疑問符 (?) を入力します。  
  
    既定では、"=" 演算子が追加されます。 ただし、セルを編集して、">"、"<"、または他の SQL 比較演算子にも変更できます。  
  
## <a name="see-also"></a>参照  
[パラメーターを使用したクエリ (Visual Database Tools)](../../ssms/visual-db-tools/query-with-parameters-visual-database-tools.md)  
  
