---
title: "sp_set_session_context (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- sp_set_session_context
- sp_set_session_context_TSQL
- sys.sp_set_session_context
- sys.sp_set_session_context_TSQL
helpviewer_keywords:
- sp_set_session_context
ms.assetid: 7a3a3b2a-1408-4767-a376-c690e3c1fc5b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a55ee31e1f4d9f5f98766550f60a16d3dd56843c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spsetsessioncontext-transact-sql"></a>sp_set_session_context (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

セッションのコンテキストでは、キー値のペアを設定します。  
  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_set_session_context [ @key= ] 'key', [ @value= ] 'value'  
    [ , [ @read_only = ] { 0 | 1 } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 [ @key=] 'key'  
 型の設定キー **sysname**です。 キーの最大サイズは、128 バイトです。  
  
 [ @value=] 'value'  
 型の指定したキーの値**sql_variant**です。 メモリを解放する、値は NULL を設定します。 最大サイズは 8,000 バイトです。  
  
 [ @read_only= ] { 0 | 1 }  
 型のフラグ**ビット**です。 1 の場合、し、指定されたキーの値変更できませんもう一度この論理接続で。 場合は 0 (既定値) の場合、その値を変更できます。  
  
## <a name="permissions"></a>Permissions  
 すべてのユーザーは、そのセッションのセッションのコンテキストを設定できます。  
  
## <a name="remarks"></a>解説  
 その他のストアド プロシージャでは、ように唯一のリテラルと変数 (not 式または関数の呼び出し)、パラメーターとして渡すことができます。  
  
 セッション コンテキストの合計サイズは、256 kb に制限されます。 この制限を超えた原因となった値を設定、ステートメントが失敗したかどうか。 全体のメモリ使用量を監視する[sys.dm_os_memory_objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md).  
  
 全体のメモリ使用量を監視するにはクエリを実行して[sys.dm_os_memory_cache_counters &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md)次のようにします。`SELECT * FROM sys.dm_os_memory_cache_counters WHERE type = 'CACHESTORE_SESSION_CONTEXT';`  
  
## <a name="examples"></a>使用例  
 次の例では、設定および英語の値を持つ言語の名前付きセッションのコンテキスト キーを取得する方法を示します。  
  
```  
EXEC sp_set_session_context 'language', 'English';  
SELECT SESSION_CONTEXT(N'language');  
```  
  
 次の例では、省略可能な読み取り専用フラグの使用を示します。  
  
```  
EXEC sp_set_session_context 'user_id', 4, @read_only = 1;  
```  
  
## <a name="see-also"></a>参照  
 [CURRENT_TRANSACTION_ID &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/current-transaction-id-transact-sql.md)   
 [SESSION_CONTEXT &#40;Transact-SQL&#41;](../../t-sql/functions/session-context-transact-sql.md)   
 [行レベルのセキュリティ](../../relational-databases/security/row-level-security.md)   
 [CONTEXT_INFO &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/context-info-transact-sql.md)   
 [SET CONTEXT_INFO &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-context-info-transact-sql.md)  
  
  
