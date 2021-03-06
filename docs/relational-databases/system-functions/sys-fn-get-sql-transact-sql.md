---
title: "sys.fn_get_sql (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fn_get_sql
- sys.fn_get_sql_TSQL
- fn_get_sql_TSQL
- sys.fn_get_sql
dev_langs:
- TSQL
helpviewer_keywords:
- fn_get_sql function
- text [SQL Server], SQL handles
- sys.fn_get_sql function
- valid SQL handles [SQL Server]
- SQL handles
ms.assetid: d5fe49b5-0813-48f2-9efb-9187716b2fd4
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 941417a97ce739173e2aba195d51ec845848186f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="sysfngetsql-transact-sql"></a>sys.fn_get_sql (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定した SQL ハンドルに対して、SQL ステートメントのテキストを返します。  
  
> [!IMPORTANT]  
>  この機能は、Microsoft SQL Server の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに sys.dm_exec_sql_text を使用してください。 詳細については、次を参照してください。 [sys.dm_exec_sql_text &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)。  
  
 
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_get_sql ( SqlHandle )  
```  
  
## <a name="arguments"></a>引数  
 *SqlHandle*  
 ハンドル値を指定します。 *SqlHandle*は**varbinary (64)**既定値はありません。  
  
## <a name="tables-returned"></a>返されたテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|dbid|**smallint**|データベース ID。 アドホック SQL ステートメントおよび準備された SQL ステートメントの場合、ステートメントがコンパイルされたデータベースの ID。|  
|objectid|**int**|データベース オブジェクトの ID。 アドホック SQL ステートメントの場合は NULL になります。|  
|number|**smallint**|プロシージャがグループ化されている場合、そのグループの番号。<br /><br /> 0 = エントリはプロシージャではない<br /><br /> NULL = アドホック SQL ステートメント|  
|encrypted|**bit**|オブジェクトが暗号化されているかどうかを示します。<br /><br /> 0 = 暗号化されていません。<br /><br /> 1 = 暗号化|  
|text|**text**|SQL ステートメントのテキスト。 暗号化されているオブジェクトの場合は NULL になります。|  
  
## <a name="remarks"></a>解説  
 有効な SQL ハンドルは、の sql_handle 列から取得できます、 [sys.dm_exec_requests &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)動的管理ビュー。  
  
 ハンドルを渡すを不要になった場合と、キャッシュ内に存在**l**は空の結果セットを返します。 無効なハンドルを渡すと、バッチは停止し、エラー メッセージが返されます。  
  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]一部をキャッシュできません[!INCLUDE[tsql](../../includes/tsql-md.md)]一括コピー ステートメントや文字列リテラルは 8 KB を超えるを含むステートメントなどのステートメント。 このようなステートメントに対するハンドルは、fn_get_sql では取得できません。  
  
 **テキスト**パスワードを含む可能性のあるテキストに対して結果セットの列はフィルター処理します。 詳細については、セキュリティに関連するストアド プロシージャについては監視されませんを次を参照してください。[トレースをフィルター処理](../../relational-databases/sql-trace/filter-a-trace.md)です。  
  
 Fn_get_sql 関数は、次のような情報を返します、 [DBCC INPUTBUFFER](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)コマンド。 次は、DBCC INPUTBUFFER を使用できず、fn_get_sql 関数を使用できる場合の例です。  
  
-   イベントの文字数が 255 文字を超える場合。  
  
-   ストアド プロシージャに関する、現在の入れ子における最上位レベルの情報を返す必要がある場合。 たとえば、sp_1 と sp_2 という名前の 2 つのストアド プロシージャがある場合に、 sp_1 で sp_2 を呼び出し、sp_2 の実行中に sys.dm_exec_requests 動的管理ビューからハンドルを取得すると、fn_get_sql 関数では sp_2 に関する情報が返されます。 さらに fn_get_sql 関数では、現在の入れ子の最上位レベルにあるストアド プロシージャの完全なテキストが返されます。  
  
## <a name="permissions"></a>権限  
 ユーザーには、サーバーに対する VIEW SERVER STATE 権限が必要があります。  
  
## <a name="examples"></a>使用例  
 データベース管理者は、次の例のように fn_get_sql 関数を使用して、問題があるプロセスを診断できます。 この場合、まず問題があるセッション ID を特定した後、そのセッションに対する SQL ハンドルを取得します。次にそのハンドルで fn_get_sql を呼び出した後、開始オフセットと終了オフセットを使用して、問題があるセッション ID の SQL ステートメントを確認します。  
  
```  
DECLARE @Handle varbinary(64);  
SELECT @Handle = sql_handle   
FROM sys.dm_exec_requests   
WHERE session_id = 52 and request_id = 0;  
SELECT * FROM sys.fn_get_sql(@Handle);  
GO  
```  
  
## <a name="see-also"></a>参照  
 [DBCC INPUTBUFFER &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)   
 [sys.sysprocesses &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)   
 [sys.dm_exec_requests &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
  
