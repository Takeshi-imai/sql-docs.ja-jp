---
title: "sys.dm_os_sys_memory (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_os_sys_memory
- sys.dm_os_sys_memory_TSQL
- sys.dm_os_sys_memory
- dm_os_sys_memory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_sys_memory dynamic management view
ms.assetid: 1ca58814-1caa-44c1-b307-ff0bdcbbef62
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5ac5e7d7fad2ceabdbfbfe30b73529ffb8d960d2
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmossysmemory-transact-sql"></a>sys.dm_os_sys_memory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  オペレーティング システムからメモリ情報を返します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で範囲指定し、オペレーティング システム レベルと、基になるハードウェアの物理的な制限で外部メモリ状況に応答します。 システム全体の状態を調査することは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のメモリ使用量を評価するうえで重要な要素です。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_sys_memory**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**total_physical_memory_kb**|**bigint**|オペレーティング システムが利用できる物理メモリの合計サイズ (KB 単位)。|  
|**available_physical_memory_kb**|**bigint**|使用できる物理メモリのサイズ (KB 単位)。|  
|**total_page_file_kb**|**bigint**|オペレーティング システムによって報告されたコミット制限のサイズ (KB 単位)。|  
|**available_page_file_kb**|**bigint**|未使用のページ ファイルの合計サイズ (KB 単位)。|  
|**system_cache_kb**|**bigint**|システム キャッシュ メモリの合計サイズ (KB 単位)。|  
|**kernel_paged_pool_kb**|**bigint**|ページ カーネル プールの合計サイズ (KB 単位)。|  
|**kernel_nonpaged_pool_kb**|**bigint**|非ページ カーネル プールの合計サイズ (KB 単位)。|  
|**system_high_memory_signal_state**|**bit**|システムの高メモリ リソース通知の状態。 この値が 1 の場合、Windows によって高メモリ シグナルが設定されていることを意味します。 詳細については、次を参照してください。 [CreateMemoryResourceNotification](http://go.microsoft.com/fwlink/?LinkId=82427) 、MSDN ライブラリです。|  
|**system_low_memory_signal_state**|**bit**|システムの低メモリ リソース通知の状態。 この値が 1 の場合、Windows によって低メモリ シグナルが設定されていることを意味します。 詳細については、次を参照してください。 [CreateMemoryResourceNotification](http://go.microsoft.com/fwlink/?LinkId=82427) 、MSDN ライブラリです。|  
|**system_memory_state_desc**|**nvarchar (256)**|メモリの状態の説明。 次の表を参照してください。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
|条件|[値]|  
|---------------|-----------|  
|system_high_memory_signal_state = 1<br /><br /> 」、「<br /><br /> system_low_memory_signal_state = 0|使用可能な物理メモリが十分に存在します。|  
|system_high_memory_signal_state = 0<br /><br /> 」、「<br /><br /> system_low_memory_signal_state = 1|使用可能な物理メモリが不足しています。|  
|system_high_memory_signal_state = 0<br /><br /> 」、「<br /><br /> system_low_memory_signal_state = 0|物理メモリの使用量が安定しています。|  
|system_high_memory_signal_state = 1<br /><br /> 」および「<br /><br /> system_low_memory_signal_state = 1|物理メモリの状態が遷移しています。<br /><br /> 高シグナルと低シグナルが同時にオンになることはありません。 ただし、オペレーティング システム レベルでの急激な変化によって、ユーザー モードのアプリケーションから両方の値がオンに見えることはあります。 両方のシグナルがオンのように見えるとき、その状態は遷移中の状態と解釈されます。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server オペレーティング システム関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


