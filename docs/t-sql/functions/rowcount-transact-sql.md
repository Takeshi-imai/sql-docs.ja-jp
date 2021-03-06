---
title: '@@ROWCOUNT (Transact-SQL) | Microsoft Docs'
ms.custom: 
ms.date: 08/29/2017
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
- '@@ROWCOUNT_TSQL'
- '@@ROWCOUNT'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@ROWCOUNT function'
- number of rows affected by statement
- row affected by statements [SQL Server]
- statements [SQL Server], last statement
- counting rows
ms.assetid: 97a47998-81d9-4331-a244-9eb8b6fe4a56
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: dd23d2af2f35dd0d76557723639f1870ee22e0ee
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40rowcount-transact-sql"></a>&#x40;&#x40;ROWCOUNT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  最後のステートメントの影響を受けた行数を返します。 行の数が 20億を超える場合は、次のようを使用して ROWCOUNT_BIG[](../../t-sql/functions/rowcount-big-transact-sql.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
@@ROWCOUNT  
```  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、次の方法で @@ROWCOUNT に値を設定できます。  
  
-   @@ROWCOUNT に、影響を受ける行または読み取られる行の数を設定します。 行はクライアントに送信しても、送信しなくてもかまいません。  
  
-   前にステートメントを実行したときの @@ROWCOUNT を保存します。  
  
-   @@ROWCOUNT を 0 にリセットしますが、クライアントにはその値を返しません。  
  
 単純な割り当てを行うステートメントの場合、@@ROWCOUNT の値は常に 1 に設定されます。 行はクライアントに送信されません。 これらのステートメントの例を示します。 設定local_variable*, 、RETURN、READTEXT、および選択せずに、クエリ SELECT getdate や SELECT などのステートメントを実行する ' **一般テキスト*'**です。  
  
 クエリで割り当てを行うステートメント、またはクエリ セットで RETURN を使用するステートメントは、クエリに影響を受ける行数、またはクエリで読み取られる行数を @@ROWCOUNT 値に設定します。たとえば、SELECT @*local_variable* = c1 FROM t1 のようになります。  
  
 データ操作言語 (DML) ステートメントは、@@ROWCOUNT 値に、クエリに影響を受ける行の数を設定し、この値をクライアントに返します。 DML ステートメントは、クライアントに行を送信しない場合もあります。  
  
 DECLARE CURSOR および FETCH は、@@ROWCOUNT 値に 1 を設定します。  
  
 EXECUTE ステートメントは、前の @@ROWCOUNT を保存します。  
  
 USE、SET \<option>、DEALLOCATE CURSOR、CLOSE CURSOR、BEGIN TRANSACTION、COMMIT TRANSACTION などのステートメントは、ROWCOUNT 値を 0 にリセットします。  
  
 ネイティブ コンパイル ストアド プロシージャでは、直前の @@ROWCOUNT が維持されます。 ネイティブ コンパイル ストアド プロシージャ内の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、@@ROWCOUNT は設定しないでください。 詳細については、次を参照してください。 ネイティブ コンパイル ストアド プロシージャ[](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)です。  
  
## <a name="examples"></a>使用例  
 次の例では、`UPDATE` ステートメントを実行し、`@@ROWCOUNT` を使用して、変更された行があるかどうかを調べます。  
  
```  
USE AdventureWorks2012;  
GO  
UPDATE HumanResources.Employee   
SET JobTitle = N'Executive'  
WHERE NationalIDNumber = 123456789  
IF @@ROWCOUNT = 0  
PRINT 'Warning: No rows were updated';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [システム関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [SET ROWCOUNT &#40;Transact-SQL&#41;](../../t-sql/statements/set-rowcount-transact-sql.md)  
  
  
