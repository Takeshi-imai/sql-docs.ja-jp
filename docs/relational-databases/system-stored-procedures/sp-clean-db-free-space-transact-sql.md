---
title: "sp_clean_db_free_space (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_clean_db_free_space_TSQL
- sp_clean_db_free_space
dev_langs:
- TSQL
helpviewer_keywords:
- sp_clean_db_free_space
- ghost records
ms.assetid: faa96f7e-be92-47b1-8bc5-4dbba5331655
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 28035865fa180e9b1e379a0fbb3843956e162ccf
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spcleandbfreespace-transact-sql"></a>sp_clean_db_free_space (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ変更ルーチンのためにデータベース ページに残った残存情報を削除します。 sp_clean_db_free_space は、データベースのすべてのファイルのすべてのページをクリーニングします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_clean_db_free_space   
[ @dbname ] = 'database_name'   
[ , [ @cleaning_delay = ] 'delay_in_seconds' ] [;]  
```  
  
## <a name="arguments"></a>引数  
 [ @dbname=] '*database_name*'  
 クリーニングするデータベースの名前です。 *dbname*は**sysname** NULL にすることはできません。  
  
 [ @cleaning_delay=] '*delay_in_seconds*'  
 ページをクリーニングする間隔を指定します。 この値を指定することにより、I/O システムへの影響を低減することができます。 *delay_in_seconds*は**int**既定値は 0 です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 テーブルから、操作を削除または更新操作行に移動することができますを直ちに解放、ページ上の領域、行への参照を削除することで、その原因です。 ただし、特定の状況下では、行がゴースト レコードとして、物理的にデータ ページ上に残ってしまう場合があります。 ゴースト レコードは、バックグラウンド プロセスによって定期的に削除されます。 この残存データがによって返されません、[!INCLUDE[ssDE](../../includes/ssde-md.md)]クエリに応答します。 ただし、データまたはバックアップ ファイルの物理的なセキュリティに不安があるような環境では、sp_clean_db_free_space を使用することで、これらのゴースト レコードをクリーニングすることができます。  
  
 sp_clean_db_free_space の実行にかかる時間は、ファイルのサイズ、使用可能な空き領域、および、ディスク容量によって異なります。 sp_clean_db_free_space プロシージャは、I/O アクティビティに著しく影響する場合があるため、通常の業務時間を避けて実行することをお勧めします。  
  
 sp_clean_db_free_space を実行する前に、データベースの完全バックアップを作成することをお勧めします。  
  
 関連する[sp_clean_db_file_free_space](../../relational-databases/system-stored-procedures/sp-clean-db-file-free-space-transact-sql.md)ストアド プロシージャは、1 つのファイルをクリーンアップできます。  
  
## <a name="permissions"></a>Permissions  
 db_owner データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例からのすべての残存情報をクリーンアップする、`AdventureWorks2012`データベース。  
  
```  
USE master;  
GO  
EXEC sp_clean_db_free_space   
@dbname = N'AdventureWorks2012' ;  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
