---
title: "既存のトレースの変更 (Transact-SQL) | Microsoft Docs"
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
- traces [SQL Server], modifying
- modifying traces
ms.assetid: 8792b43f-2510-44e3-9239-e73ad8227b89
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0f58e12e1c04c65974dbc985c8acc525ed44be06
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="modify-an-existing-trace-transact-sql"></a>既存のトレースの変更 (Transact-SQL)
  このトピックでは、ストアド プロシージャを使用して既存のトレースを変更する方法について説明します。  
  
### <a name="to-modify-an-existing-trace"></a>既存のトレースを変更するには  
  
1.  トレースが既に実行中の場合は、**@status = 0** を指定して **sp_trace_setstatus** を実行し、トレースを停止します。  
  
2.  トレース イベントを変更するには、パラメーターを使用して変更を指定し、 **sp_trace_setevent** を実行します。 パラメーターは次の順序で指定します。  
  
    -   **@traceid** (トレース ID)  
  
    -   **@eventid** (イベント ID)  
  
    -   **@columnid** (列 ID)  
  
    -   **@on** (ON)  
  
     **@on** パラメーターを変更する場合は、**@columnid** パラメーターとの相互作用を考慮してください。  
  
    |ON|列 ID|結果|  
    |--------|---------------|------------|  
    |ON (**1**)|NULL|イベントはオンになります。 すべての列は消去されます。|  
    ||NOT NULL|指定されたイベントに対して列はオンになります。|  
    |OFF (**0**)|NULL|イベントはオフになります。 すべての列は消去されます。|  
    ||NOT NULL|指定されたイベントに対して列はオフになります。|  
  
> [!IMPORTANT]  
>  通常のストアド プロシージャとは異なり、すべての [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ストアド プロシージャ (**sp_trace_*xx***) で、パラメーターのデータ型が厳密に定義されており、データ型の自動変換はサポートしていません。 これらのパラメーターが、引数の説明で指定されている正しいデータ型で呼び出されないと、このストアド プロシージャではエラーが返されます。  
  
## <a name="see-also"></a>参照  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [SQL Server Profiler のストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  