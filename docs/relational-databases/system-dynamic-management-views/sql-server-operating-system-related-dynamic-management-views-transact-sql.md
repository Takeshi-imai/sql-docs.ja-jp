---
title: "SQL Server オペレーティング システム関連の動的管理ビュー (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/16/2016
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
dev_langs:
- TSQL
helpviewer_keywords:
- operating systems [SQL Server], dynamic management objects
- SQL Operating System dynamic management objects [SQL Server]
- SQL OS dynamic management objects [SQL Server]
- dynamic management objects [SQL Server], SQL OS
ms.assetid: 3030c86a-0a74-4fed-ac0f-392e244cb965
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 075969e966be06a8fd0f7572d212bf045621ff5e
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sql-server-operating-system-related-dynamic-management-views-transact-sql"></a>SQL Server オペレーティング システム関連の動的管理ビュー (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このセクションには、関連付けられている動的管理ビューが含まれています、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オペレーティング システム (SQLOS)。 固有のオペレーティング システム リソースの管理を担当は、SQLOS[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
|||  
|-|-|  
|[sys.dm_os_buffer_descriptors &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-buffer-descriptors-transact-sql.md)|[sys.dm_os_memory_pools &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-pools-transact-sql.md)|  
|[sys.dm_os_child_instances &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-child-instances-transact-sql.md)|[sys.dm_os_nodes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-nodes-transact-sql.md)|  
|[sys.dm_os_cluster_nodes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)|[sys.dm_os_performance_counters &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)|  
|[sys.dm_os_dispatcher_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-dispatcher-pools-transact-sql.md)|[sys.dm_os_process_memory &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-process-memory-transact-sql.md)|  
|[sys.dm_os_host_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)|[sys.dm_os_schedulers &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md)|  
|[sys.dm_os_hosts &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-hosts-transact-sql.md)|[sys.dm_os_stacks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-stacks-transact-sql.md)|  
|[sys.dm_os_latch_stats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md)|[sys.dm_os_sys_info &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)|  
|[sys.dm_os_loaded_modules &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-loaded-modules-transact-sql.md)|[sys.dm_os_sys_memory &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-memory-transact-sql.md)|  
|[sys.dm_os_memory_brokers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-brokers-transact-sql.md)|[sys.dm_os_tasks と組み合わせます &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)|  
|[sys.dm_os_memory_cache_clock_hands &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-clock-hands-transact-sql.md)|[sys.dm_os_threads &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql.md)|  
|[sys.dm_os_memory_cache_counters &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md)|[sys.dm_os_virtual_address_dump &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-virtual-address-dump-transact-sql.md)|  
|[sys.dm_os_memory_cache_entries &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-entries-transact-sql.md)|[sys.dm_os_volume_stats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-volume-stats-transact-sql.md)|  
|[sys.dm_os_memory_cache_hash_tables &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-hash-tables-transact-sql.md)|[sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)|  
|[sys.dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)|[sys.dm_os_waiting_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-waiting-tasks-transact-sql.md)|  
|[sys.dm_os_memory_nodes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-nodes-transact-sql.md)|[sys.dm_os_windows_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md)|  
|[sys.dm_os_memory_objects &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md)|[sys.dm_os_workers &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)|  
  
 次[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オペレーティング システム関連の動的管理ビューは[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]します。  
  
|||  
|-|-|  
|**sys.dm_os_function_symbolic_name**|**sys.dm_os_ring_buffers**|  
|**sys.dm_os_memory_allocations**|**sys.dm_os_sublatches**|  
|**sys.dm_os_worker_local_storage**||  
  
## <a name="see-also"></a>参照  
 [動的管理ビューおよび関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

