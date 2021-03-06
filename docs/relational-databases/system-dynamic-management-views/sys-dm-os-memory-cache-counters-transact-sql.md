---
title: "sys.dm_os_memory_cache_counters (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/18/2017
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
- sys.dm_os_memory_cache_counters_TSQL
- dm_os_memory_cache_counters_TSQL
- sys.dm_os_memory_cache_counters
- dm_os_memory_cache_counters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_counters dynamic management view
ms.assetid: ca7bd036-d661-4c17-b00a-e1a975bd8932
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d75cd1785aedd1f2cebe9b14849c6e1eae779988
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmosmemorycachecounters-transact-sql"></a>sys.dm_os_memory_cache_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、キャッシュのヘルスのスナップショットを返します。 **sys.dm_os_memory_cache_counters** provides run-time information about the cache entries allocated, their use, and the source of memory for the cache entries.  
  
> **注:**これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_memory_cache_counters**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|特定のキャッシュに関連付けられているカウンターのアドレス (主キー) を示します。 NULL 値は許可されません。|  
|**name**|**nvarchar (256)**|キャッシュの名前を指定します。 NULL 値は許可されません。|  
|**type**|**nvarchar(60)**|このエントリに関連付けられているキャッシュの型を示します。 NULL 値は許可されません。|  
|**single_pages_kb**|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> 割り当てられている単一ページ メモリの量 (KB 単位)。 これは、単一ページ アロケーターを使用することによって割り当てられたメモリの量です。 キャッシュ用にバッファー プールから直接取得された 8 KB ページを表します。 NULL 値は許可されません。|  
|**pages_kb**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> キャッシュ内で割り当てられているメモリの量を KB 単位で指定します。 NULL 値は許可されません。|  
|**multi_pages_kb**|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> 割り当てられている複数ページ メモリの量 (KB 単位)。 メモリ ノードの複数ページ アロケーターを使用することによって割り当てられるメモリの量です。 このメモリは、バッファー プール外に割り当てられ、メモリ ノードの仮想アロケーターを利用します。 NULL 値は許可されません。|  
|**pages_in_use_kb**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> キャッシュ内で割り当てられ、使用されているメモリの量を KB 単位で指定します。 NULL 値が許可されます。  `USERSTORE_<*>` 型のオブジェクトの値は追跡されません。  これらについては NULL が報告されます。|  
|**single_pages_in_use_kb**|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> 使用されている単一ページ メモリの量 (KB 単位)。 NULL 値が許可されます。 この情報は userstore _ の型のオブジェクトに対しては追跡されません\<* > し、これらの値は NULL になります。|  
|**multi_pages_in_use_kb**|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> 使用されている複数ページ メモリの量 (KB 単位)。 NULL 値は許可されます。 この情報は userstore _ の型のオブジェクトに対しては追跡されません\<* >、およびこれらの値は NULL になります。|  
|**entries_count**|**bigint**|キャッシュ内のエントリの数を指定します。 NULL 値は許可されません。|  
|**entries_in_use_count**|**bigint**|使用されているキャッシュ内のエントリの数を指定します。 NULL 値は許可されません。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>権限  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium 階層が必要です、`VIEW DATABASE STATE`データベースの権限です。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。  

## <a name="see-also"></a>参照  
  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


