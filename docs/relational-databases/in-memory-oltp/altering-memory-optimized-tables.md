---
title: "メモリ最適化テーブルの変更 | Microsoft Docs"
ms.custom: 
ms.date: 06/19/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 690b70b7-5be1-4014-af97-54e531997839
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 89709d63c40233091fe01688e655ff5b53145711
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="altering-memory-optimized-tables"></a>メモリ最適化テーブルの変更
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  メモリ最適化テーブルのスキーマとインデックスの変更は、ALTER TABLE ステートメントを使用して実行できます。 SQL Server 2016 と Azure SQL Database では、メモリ最適化テーブルに対する ALTER TABLE 操作は OFFLINE です。つまり、操作が行われている間、テーブルのクエリを行うことはできません。 データベース アプリケーションは実行を継続できます。また、テーブルにアクセスする操作は、変更プロセスが完了するまでブロックされます。 1 つの ALTER TABLE ステートメントに、複数の ADD、DROP、または ALTER 操作を組み合わせることができます。
  
## <a name="alter-table"></a>ALTER TABLE  
 
ALTER TABLE 構文は、テーブル スキーマを変更する場合だけでなく、インデックスの追加、削除、および再構築の場合にも使用します。 インデックスは、テーブル定義の一部と見なされます。  
  
-   構文 ALTER TABLE … ADD/DROP/ALTER INDEX は、メモリ最適化テーブルでのみサポートされます。  
  
-   ALTER TABLE ステートメントを使用しない場合、メモリ最適化テーブルのインデックスにステートメント CREATE INDEX、DROP INDEX、および ALTER INDEX を *使用できません* 。  
  
 次の構文は、ALTER TABLE ステートメントの ADD、DROP、および ALTER の各 INDEX 句に使用されます。  
  
```
| ADD   
     {   
        <column_definition>  
      | <table_constraint>  
      | <table_index>    
     } [ ,...n ]  
  
| DROP   
     {  
         [ CONSTRAINT ]   
         {   
              constraint_name   
         } [ ,...n ]  
         | COLUMN   
         {  
              column_name   
         } [ ,...n ]  
         | INDEX   
         {  
              index_name   
         } [ ,...n ]  
     } [ ,...n ]  
  
| ALTER INDEX index_name  
     {   
         REBUILD WITH ( <rebuild_index_option> )     
     }  
}  
```  
  
 次の種類の変更がサポートされています。  
  
-   バケット数の変更  
  
-   インデックスの追加と削除  
  
-   列の変更、追加、削除  
  
-   定数の追加と削除  
  
 ALTER TABLE の機能と詳細な構文については、「[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)」を参照してください。  
  
## <a name="schema-bound-dependency"></a>スキーマ バインド依存関係  
 スキーマ バインドであるためには、アクセスするメモリ最適化テーブルおよび参照する列に対するスキーマ バインド依存関係を持つネイティブ コンパイル ストアド プロシージャが必要です。 スキーマ バインド依存関係とは、参照元エンティティが存在する限り、参照先エンティティを削除したり、互換性のない方法で変更したりすることができない 2 つのエンティティ間のリレーションシップです。  
  
 たとえば、スキーマ バインドのネイティブ コンパイル ストアド プロシージャがテーブル *mytable* の列 *c1*を参照している場合、列 *c1* は削除できません。 同様に、このようなプロシージャで列リストのない INSERT ステートメント (たとえば `INSERT INTO dbo.mytable VALUES (...)`) を使用している場合、テーブルの列はどれも削除できません。  
 
## <a name="logging-of-alter-table-on-memory-optimized-tables"></a>メモリ最適化テーブルの ALTER TABLE のログ記録
メモリ最適化テーブルでは、ほとんどの ALTER TABLE シナリオが並列に実行され、トランザクション ログへの書き込みが最適化されるようになりました。 最適化は、メタデータの変更のみをトランザクション ログに記録することによって実現されます。 ただし、次の ALTER TABLE 操作ではシングル スレッドが実行され、ログ最適化は行われません。

この場合のシングル スレッド操作は、変更されたテーブルの内容全体をトランザクション ログに記録します。 シングル スレッド操作の一覧を以下に示します。

- nvarchar(max)、varchar(max)、varbinary(max) などのラージ オブジェクト (LOB) 型を使用するために列を変更または追加します。

- COLUMNSTORE インデックスを追加または削除します。

- [行外列](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md)に影響するほぼあらゆる操作。

    - 行内の列を行外に移動します。

    - 行外の列を行内に移動します。

    - 新しい行外の列を作成します。

    - *例外:* 既存の行外列が長くなった場合は、最適化された方法でログに記録されます。 
  
## <a name="examples"></a>使用例  
 次の例では、既存のハッシュ インデックスのバケット数を変更します。 その結果、新しいバケット数でハッシュ インデックスが再構築されますが、ハッシュ インデックスの他のプロパティは変わりません。  
  
```sql
ALTER TABLE Sales.SalesOrderDetail_inmem   
       ALTER INDEX imPK_SalesOrderDetail_SalesOrderID_SalesOrderDetailID  
              REBUILD WITH (BUCKET_COUNT=67108864);  
GO
```
  
 次の例では、NOT NULL 制約と DEFAULT 定義を指定した列を追加し、WITH VALUES を使用して、テーブルに存在する各行の値を指定します。 WITH VALUES を使用しない場合、新しい列には NULL 値が格納されます。  
  
```sql  
ALTER TABLE Sales.SalesOrderDetail_inmem  
       ADD Comment NVARCHAR(100) NOT NULL DEFAULT N'' WITH VALUES;  
GO
```  
  
 次の例では、プライマリ キー制約を既存の列に追加します。  
  
```sql
CREATE TABLE dbo.UserSession (   
   SessionId int not null,   
   UserId int not null,   
   CreatedDate datetime2 not null,   
   ShoppingCartId int,   
   index ix_UserId nonclustered hash (UserId) with (bucket_count=400000)   
)   
WITH (MEMORY_OPTIMIZED=ON, DURABILITY=SCHEMA_ONLY) ;  
GO  
  
ALTER TABLE dbo.UserSession  
       ADD CONSTRAINT PK_UserSession PRIMARY KEY NONCLUSTERED (SessionId);  
GO
```  
  
 次の例では、インデックスを削除します。  
  
```sql
ALTER TABLE Sales.SalesOrderDetail_inmem  
       DROP INDEX ix_ModifiedDate;  
GO
```  
  
 次の例では、インデックスを追加します。  
  
```sql  
ALTER TABLE Sales.SalesOrderDetail_inmem  
       ADD INDEX ix_ModifiedDate (ModifiedDate);  
GO  
```  
  
 次の例では、インデックスと制約が指定された複数の列を追加します。  
  
```sql
ALTER TABLE Sales.SalesOrderDetail_inmem  
       ADD    CustomerID int NOT NULL DEFAULT -1 WITH VALUES,  
              ShipMethodID int NOT NULL DEFAULT -1 WITH VALUES,  
              INDEX ix_Customer (CustomerID);  
GO  
```


<a name="logging-of-alter-table-on-memory-optimized-tables-124"></a>


## <a name="see-also"></a>参照  

[メモリ最適化テーブル](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  

