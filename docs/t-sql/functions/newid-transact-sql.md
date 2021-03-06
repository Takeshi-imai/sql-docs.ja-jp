---
title: "NEWID (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NEWID
- NEWID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- uniqueidentifier data type
- NEWID function
ms.assetid: f7014e60-96d5-457e-afc3-72b60ba20c0f
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: cb2a6d743037b040b609ee73e09a44ebbe6b29f1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="newid-transact-sql"></a>NEWID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  型の一意の値を作成**uniqueidentifier**です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
NEWID ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 **uniqueidentifier**  
  
## <a name="remarks"></a>解説  
 `NEWID()` は RFC4122 に準拠しています。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-the-newid-function-with-a-variable"></a>A. NEWID 関数を変数と共に使用する  
 次の例で`NEWID()`として宣言された変数に値を割り当てる、 **uniqueidentifier**データ型。 値、 **uniqueidentifier**値をテストする前に、データ型の変数を出力します。  
  
```  
-- Creating a local variable with DECLARE/SET syntax.  
DECLARE @myid uniqueidentifier  
SET @myid = NEWID()  
PRINT 'Value of @myid is: '+ CONVERT(varchar(255), @myid)  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Value of @myid is: 6F9619FF-8B86-D011-B42D-00C04FC964FF  
```  
  
> [!NOTE]  
>  NEWID によって返される値は、コンピューターごとに異なります。 ここに示す値はあくまでも 1 つの例です。  
  
### <a name="b-using-newid-in-a-create-table-statement"></a>B. CREATE TABLE ステートメント内で NEWID を使用する  
  
**適用されます**:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
  
 次の例を作成、`cust`を持つテーブル、 **uniqueidentifier**既定値を持つテーブルを入力するには、データ型、および NEWID を使用します。 `NEWID()` の既定値が代入されると、新しい行と既存の行の `CustomerID` 列にそれぞれ一意な値が設定されます。  
  
```  
-- Creating a table using NEWID for uniqueidentifier data type.  
CREATE TABLE cust  
(  
 CustomerID uniqueidentifier NOT NULL  
   DEFAULT newid(),  
 Company varchar(30) NOT NULL,  
 ContactName varchar(60) NOT NULL,   
 Address varchar(30) NOT NULL,   
 City varchar(30) NOT NULL,  
 StateProvince varchar(10) NULL,  
 PostalCode varchar(10) NOT NULL,   
 CountryRegion varchar(20) NOT NULL,   
 Telephone varchar(15) NOT NULL,  
 Fax varchar(15) NULL  
);  
GO  
-- Inserting 5 rows into cust table.  
INSERT cust  
(CustomerID, Company, ContactName, Address, City, StateProvince,   
 PostalCode, CountryRegion, Telephone, Fax)  
VALUES  
 (NEWID(), 'Wartian Herkku', 'Pirkko Koskitalo', 'Torikatu 38', 'Oulu', NULL,  
 '90110', 'Finland', '981-443655', '981-443655')  
,(NEWID(), 'Wellington Importadora', 'Paula Parente', 'Rua do Mercado, 12', 'Resende', 'SP',  
 '08737-363', 'Brasil', '(14) 555-8122', '')  
,(NEWID(), 'Cactus Comidas para Ilevar', 'Patricio Simpson', 'Cerrito 333', 'Buenos Aires', NULL,   
 '1010', 'Argentina', '(1) 135-5555', '(1) 135-4892')  
,(NEWID(), 'Ernst Handel', 'Roland Mendel', 'Kirchgasse 6', 'Graz', NULL,  
 '8010', 'Austria', '7675-3425', '7675-3426')  
,(NEWID(), 'Maison Dewey', 'Catherine Dewey', 'Rue Joseph-Bens 532', 'Bruxelles', NULL,  
 'B-1180', 'Belgium', '(02) 201 24 67', '(02) 201 24 68');  
GO  
```  
  
### <a name="c-using-uniqueidentifier-and-variable-assignment"></a>C. uniqueidentifier と変数代入を使用する  
 次の例と呼ばれるローカル変数を宣言する`@myid`の変数として**uniqueidentifier**データ型。 次に、変数に値が代入を使用して、`SET`ステートメントです。  
  
```  
DECLARE @myid uniqueidentifier ;  
SET @myid = 'A972C577-DFB0-064E-1189-0154C99310DAAC12';  
SELECT @myid;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [NEWSEQUENTIALID &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/newsequentialid-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CAST および CONVERT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [システム関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [一意識別子と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/uniqueidentifier-transact-sql.md)   
 [シーケンス番号](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  
