---
title: "sys.dm_os_memory_pools (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_pools_TSQL
- dm_os_memory_pools
- dm_os_memory_pools_TSQL
- sys.dm_os_memory_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_pools dynamic management view
ms.assetid: 1ef053f3-c6f3-456e-82b6-26e4bd630d46
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4e3c98075a42b2f4a9f5c956c5f71ba017192aad
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmosmemorypools-transact-sql"></a>sys.dm_os_memory_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  インスタンスの各オブジェクトのストアの行を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 このビューを使用すると、キャッシュ メモリの使用状況を監視したり、無効なキャッシュ動作を識別できます。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_memory_pools**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**memory_pool_address**|**varbinary(8)**|メモリ プールを表すエントリのメモリ アドレス。 NULL 値は許可されません。|  
|**pool_id**|**int**|プールのセット内にある特定プールの ID。 NULL 値は許可されません。|  
|**type**|**nvarchar(60)**|オブジェクト プールの種類。 NULL 値は許可されません。 詳細については、次を参照してください。 [sys.dm_os_memory_clerks &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)。|  
|**name**|**nvarchar (256)**|システムによって割り当てられた、メモリ オブジェクトの名前。 NULL 値は許可されません。|  
|**max_free_entries_count**|**bigint**|プールに含めることができる空きエントリの最大数。 NULL 値は許可されません。|  
|**free_entries_count**|**bigint**|現在プール内にある空きエントリ数。 NULL 値は許可されません。|  
|**removed_in_all_rounds_count**|**bigint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの起動後、プールから削除されたエントリ数。 NULL 値は許可されません。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>権限  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium 階層が必要です、`VIEW DATABASE STATE`データベースの権限です。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントは、場合によってキャッシュの同種でステートレスな種類のデータに共通のプール フレームワークを使用します。 プール フレームワークは、キャッシュ フレームワークよりも単純です。 プール内のすべてのエントリは、等しいと見なされます。 内部的には、プールはメモリ クラークであり、メモリ クラークが使用される場所で使用できます。  
  
## <a name="see-also"></a>参照  
 
  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


