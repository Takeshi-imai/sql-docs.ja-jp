---
title: sys.dm_broker_activated_tasks (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_broker_activated_tasks
- sys.dm_broker_activated_tasks_TSQL
- dm_broker_activated_tasks
- dm_broker_activated_tasks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_broker_activated_tasks dynamic management view
ms.assetid: 17e6f87f-8f56-489d-9aed-216afc8ef310
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ddcb504228d8307e9ba8de1655d5fc0523dd47be
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmbrokeractivatedtasks-transact-sql"></a>sys.dm_broker_activated_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Service Broker によってアクティブにされたストアド プロシージャごとに 1 行のデータを返します。  
 

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**spid**|**int**|アクティブにされたストアド プロシージャのセッションの ID。 NULL 値は許可されます。|  
|**database_id**|**smallint**|キューが定義されているデータベースの ID。 NULL 値は許可されます。|  
|**queue_id**|**int**|ストアド プロシージャをアクティブにしたキューのオブジェクトの ID。 NULL 値は許可されます。|  
|**procedure_name**|**nvarchar(650)**|アクティブにされたストアド プロシージャの名前。 NULL 値は許可されます。|  
|**execute_as**|**int**|ストアド プロシージャを実行するユーザーの ID。 NULL 値は許可されます。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="physical-joins"></a>物理結合  
 ![Sys.dm_broker_activated_tasks の結合](../../relational-databases/system-dynamic-management-views/media/join-dm-broker-activated-tasks-1.gif "sys.dm_broker_activated_tasks の結合")  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|リレーションシップ|  
|----------|--------|------------------|  
|dm_broker_activated_tasks.spid|dm_exec_sessions.session_id|一対一|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Service Broker 関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

