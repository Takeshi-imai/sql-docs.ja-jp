---
title: MIN_ACTIVE_ROWVERSION (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MIN_ACTIVE_ROWVERSION
- MIN_ACTIVE_ROWVERSION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MIN_ACTIVE_ROWVERSION function [Transact-SQL]
ms.assetid: 87c89547-8ea1-4820-b75e-36be683e4e10
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 954b013f9329f98043673d58b62a5a171335fb51
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="minactiverowversion-transact-sql"></a>MIN_ACTIVE_ROWVERSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベース内でアクティブな最小の **rowversion** 値を返します。 **rowversion** 値がアクティブになるのは、まだコミットされていないトランザクションで使用される場合です。 詳細については、を参照してください。 rowversion (& a) #40 です。TRANSACT-SQL と #41;[](../../t-sql/data-types/rowversion-transact-sql.md).  
  
> [!NOTE]  
>  **rowversion** データ型は、**timestamp** とも呼ばれます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
MIN_ACTIVE_ROWVERSION  
```  
  
## <a name="return-types"></a>戻り値の型  
 返します、 binary (8)** 値。  
  
## <a name="remarks"></a>Remarks  
 MIN_ACTIVE_ROWVERSION は、現在のデータベースの最低のアクティブ **rowversion** 値を返す非決定的関数です。 新しい **rowversion** 値は、通常、 **rowversion**型の列を含むテーブルに対して挿入または更新が実行されたときに生成されます。 データベース内にアクティブな値がない場合は、MIN_ACTIVE_ROWVERSION は @@DBTS + 1 と同じ値を返します。  
  
 **rowversion** 値を使用して一連の変更をグループ化するデータ同期などのシナリオでは、MIN_ACTIVE_ROWVERSION が役立ちます。 アプリケーションで MIN_ACTIVE_ROWVERSION ではなく @@DBTS を使用する場合、同期が行われるときにアクティブな変更が失われる可能性があります。  
  
 MIN_ACTIVE_ROWVERSION 関数は、トランザクション分離レベルでの変更の影響を受けません。  
  
## <a name="examples"></a>使用例  
 次の例では、`MIN_ACTIVE_ROWVERSION` および `@@DBTS` を使用して、**rowversion** 値を返します。 データベース内にアクティブなトランザクションがない場合、値が異なることがわかります。  
  
```  
-- Create a table that has a ROWVERSION column in it.  
CREATE TABLE RowVersionTestTable (rv ROWVERSION)  
GO  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()   
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E2  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E3  
  
-- Insert a row.  
INSERT INTO RowVersionTestTable VALUES (DEFAULT)  
SELECT * FROM RowVersionTestTable  
GO  
---------------- Results ----------------  
--rv  
--0x00000000000007E3  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()  
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E3  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E4  
  
-- Insert a new row inside a transaction but do not commit.  
BEGIN TRAN  
INSERT INTO RowVersionTestTable VALUES (DEFAULT)  
SELECT * FROM RowVersionTestTable  
GO  
---------------- Results ----------------  
--rv  
--0x00000000000007E3  
--0x00000000000007E4  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()   
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E4  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E4  
  
-- Commit the transaction.  
COMMIT  
GO  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()  
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E4  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E5  
```  
  
## <a name="see-also"></a>参照  
 [@@DBTS &#40;Transact-SQL&#41;](../../t-sql/functions/dbts-transact-sql.md)   
 [rowversion &#40;Transact-SQL&#41;](../../t-sql/data-types/rowversion-transact-sql.md)  
  
  
