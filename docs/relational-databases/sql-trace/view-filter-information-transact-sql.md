---
title: "フィルター情報の表示 (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- displaying filter information
- filters [SQL Server], viewing
- filters [SQL Server], traces
- traces [SQL Server], filters
- viewing filter information
ms.assetid: b7e52c13-8c83-47c2-8cd0-af7a49eceb5c
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ce6c2cf81a054b4dd32fe9a74039a5388c80c5c7
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="view-filter-information-transact-sql"></a>フィルター情報の表示 (Transact-SQL)
  このトピックでは、組み込み関数を使用してトレース フィルター情報を表示する方法について説明します。  
  
### <a name="to-view-filter-information"></a>フィルター情報を表示するには  
  
1.  フィルター情報が必要なトレースの ID を指定して、 **fn_trace_getfilterinfo** を実行します。 この関数は、フィルター、フィルターが適用されている列、およびフィルターで使用している値の一覧を返します。  
  
     この関数を呼び出すには、次のステートメントを実行します。  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getfilterinfo(trace_id)  
    ```  
  
## <a name="see-also"></a>参照  
 [sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [SQL Server Profiler のストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  