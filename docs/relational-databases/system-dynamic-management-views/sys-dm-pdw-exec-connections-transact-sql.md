---
title: "sys.dm_pdw_exec_connections (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2625466b-d0ef-4c71-bedc-6d13491a8351
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 201c0fe2d8396d5669f2a05ef43343522827c465
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwexecconnections-transact-sql"></a>sys.dm_pdw_exec_connections (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  このインスタンスの [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] との間に確立された接続に関する情報と各接続の詳細を返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|session_id|**int**|この接続に関連付けられたセッションの識別子。 使用して`SESSION_ID()`を返す、`session_id`現在の接続。|  
|connect_time|**datetime**|接続が確立されたタイムスタンプ。 NULL 値は許可されません。|  
|encrypt_option|**nvarchar(40)**|TRUE のことを示します (接続が暗号化される) または FALSE (接続は enctypred ではありません)。|  
|auth_scheme|**nvarchar(40)**|指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Windows 認証スキームがこの接続で使用します。 NULL 値は許可されません。|  
|client_id|**varchar(48)**|このサーバーに接続するクライアントの IP アドレス。 NULL 値が許可されます。|  
|sql_spid|**int**|接続のサーバー プロセス ID。 使用して`@@SPID`を返す、`sql_spid`現在の接続。最も終えたら、使用して、`session_id`代わりにします。|  
  
## <a name="permissions"></a>権限  
 必要があります**VIEW SERVER STATE**サーバーに対する権限。  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
||||  
|-|-|-|  
|dm_pdw_exec_sessions.session_id|dm_pdw_exec_connections.session_id|一対一|  
|dm_pdw_exec_requests.connection_id|dm_pdw_exec_connections.connection_id|多対一|  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 クエリ専用接続についての情報を収集する典型的なクエリ。  
  
```  
SELECT  
    c.session_id, c.encrypt_option,  
    c.auth_scheme, s.client_id, s.login_name,   
    s.status, s.query_count  
FROM sys.dm_pdw_exec_connections AS c  
JOIN sys.dm_pdw_exec_sessions AS s  
    ON c.session_id = s.session_id  
WHERE c.session_id = SESSION_ID();  
```  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  

