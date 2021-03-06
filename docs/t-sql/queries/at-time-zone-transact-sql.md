---
title: "タイム ゾーン (TRANSACT-SQL) で |Microsoft ドキュメント"
ms.date: 11/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AT TIME ZONE
- AT_TIME_ZONE_TSQL
helpviewer_keywords:
- AT TIME ZONE function
ms.assetid: 311f682f-7f1b-43b6-9ea0-24e36b64f73a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 8b77aeb47515f4140f78a70288e9e25d2acc52d1
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="at-time-zone-transact-sql"></a>タイム ゾーン (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  変換、 *inputdate* 、対応する*datetimeoffset*対象のタイム ゾーンの値。 場合*inputdate*関数があると仮定して、タイム ゾーンのオフセットを適用するオフセット情報がない場合は*inputdate*対象のタイム ゾーンで値を指定します。 場合*inputdate*として提供される、 *datetimeoffset*値よりも**AT TIME ZONE**句にタイム ゾーンの変換規則を使用して対象のタイム ゾーンに変換します。  
  
 **タイム ゾーンで**実装を変換する Windows 機構に依存している**datetime**タイム ゾーン間での値。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
inputdate AT TIME ZONE timezone  
```  
  
## <a name="arguments"></a>引数  
 *inputdate*  
 式に解決されることができるは、 **smalldatetime**、 **datetime**、 **datetime2**、または**datetimeoffset**値。  
  
 *timezone*  
 変換先タイム ゾーンの名前です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Windows レジストリに格納されているタイム ゾーンに依存します。 次のレジストリ ハイブに、コンピューターにインストールされているすべてのタイム ゾーンが格納されている: **KEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time ゾーン**です。 を通じてインストールされているタイム ゾーンの一覧が公開されても、 [sys.time_zone_info &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-time-zone-info-transact-sql.md)ビュー。  
  
## <a name="return-types"></a>戻り値の型  
 データ型を返す**datetimeoffset**  
  
## <a name="return-value"></a>戻り値  
 **Datetimeoffset**対象のタイム ゾーンの値。  
  
## <a name="remarks"></a>解説  
 **タイム ゾーンで**入力値に変換するための特定の規則を適用**smalldatetime**、 **datetime**と**datetime2**に分類されるデータ型、間隔の影響を受ける DST 変更の影響。  
  
-   クロックがどの期間は、クロックの調整の期間によって決まります。 ローカル時刻にギャップがあるし、事前設定されてと (通常 1 時間、ができるタイム ゾーンに応じて、30 ~ 45 分) です。 その場合は、この時間差に属している時点のオフセットを使用に変換されます*後*DST 変更します。  
  
    ```  
    /*  
        Moving to DST in "Central European Standard Time" zone: 
        offset changes from +01:00 -> +02:00   
        Change occurred on March 29th, 2015 at 02:00:00.   
        Adjusted local time became 2015-03-29 03:00:00.  
    */  
    
    --Time before DST change has standard time offset (+01:00)
    SELECT CONVERT(datetime2(0), '2015-03-29T01:01:00', 126)     
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-03-29 01:01:00 +01:00   
  
    /*
      Adjusted time from the "gap interval" (between 02:00 and 03:00)
      is moved 1 hour ahead and presented with the summer time offset
      (after the DST change) 
    */
    SELECT CONVERT(datetime2(0), '2015-03-29T02:01:00', 126)   
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-03-29 03:01:00 +02:00
      
    --Time after 03:00 is presented with the summer time offset (+02:00)
    SELECT CONVERT(datetime2(0), '2015-03-29T03:01:00', 126)   
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-03-29 03:01:00 +02:00  
  
    ```  
  
- クロックが戻る設定されている場合のローカル時間で 2 時間は 1 時間にオーバー ラップします。  その場合は、重複した間隔に属している時間内のポイントが表示されます、オフセット*する前に*クロックの変更。  
  
    ```  
    /*  
        Moving back from DST to standard time in 
        "Central European Standard Time" zone: 
        offset changes from +02:00 -> +01:00.  
        Change occurred on October 25th, 2015 at 03:00:00.   
        Adjusted local time became 2015-10-25 02:00:00   
    */  
    
    --Time before the change has DST offset (+02:00)
    SELECT CONVERT(datetime2(0), '2015-10-25T01:01:00', 126)      
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-10-25 01:01:00 +02:00  
    
    /*
      Time from the "overlapped interval" is presented with standard time 
      offset (before the change)    
    */
    SELECT CONVERT(datetime2(0), '2015-10-25T02:00:00', 126)   
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-10-25 02:00:00 +02:00  
    
    
    --Time after 03:00 is regularly presented with the standard time offset (+01:00)    
    SELECT CONVERT(datetime2(0), '2015-10-25T03:01:00', 126)   
    AT TIME ZONE 'Central European Standard Time';  
    --Result: 2015-10-25 03:01:00 +01:00
  
    ```  

外部 (タイム ゾーンの規則) などのいくつかの情報を保持するため[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]不定期の変更されると、 **AT TIME ZONE**関数は、非決定的化されました。 
  
## <a name="examples"></a>使用例  
  
### <a name="a-add-target-time-zone-offset-to-datetime-without-offset-information"></a>A. Datetime オフセット情報がない場合にターゲットのタイム ゾーン オフセットを追加します。  
 使用して**AT TIME ZONE**ことがわかっている場合に、タイム ゾーンの規則に基づいてオフセットを追加する元**datetime**値は、同じタイム ゾーンで提供されます。  
  
```  
USE AdventureWorks2016;  
GO  
  
SELECT SalesOrderID, OrderDate,   
    OrderDate AT TIME ZONE 'Pacific Standard Time' AS OrderDate_TimeZonePST  
FROM Sales.SalesOrderHeader;  
```  
  
### <a name="b-convert-values-between-different-time-zones"></a>B. 異なるタイム ゾーン間の変換します。  
 次の例では、異なるタイム ゾーン間で値に変換します。  
  
```  
USE AdventureWorks2016;  
GO  
  
SELECT SalesOrderID, OrderDate,   
    OrderDate AT TIME ZONE 'Pacific Standard Time' AS OrderDate_TimeZonePST,  
    OrderDate AT TIME ZONE 'Pacific Standard Time'   
    AT TIME ZONE 'Central European Standard Time' AS OrderDate_TimeZoneCET  
FROM Sales.SalesOrderHeader;  
```  
  
### <a name="c-query-temporal-tables-using-local-time-zone"></a>C. ローカル タイム ゾーンを使用して、テンポラル テーブルをクエリします。  
 次の例では、テンポラル テーブルからデータを選択します。  
  
```  
USE AdventureWorks2016;  
GO  
  
DECLARE @ASOF datetimeoffset;  
SET @ASOF = DATEADD (month, -1, GETDATE()) AT TIME ZONE 'UTC';  
  
-- Query state of the table a month ago projecting period   
-- columns as Pacific Standard Time  
SELECT BusinessEntityID, PersonType, NameStyle, Title,   
    FirstName, MiddleName,  
    ValidFrom AT TIME ZONE 'Pacific Standard Time' 
FROM  Person.Person_Temporal  
FOR SYSTEM_TIME AS OF @ASOF;  
```  
  
## <a name="see-also"></a>参照  
 [日付と時刻型](../../t-sql/data-types/date-and-time-types.md)   
 [日付および時刻データ型および関数 &#40;TRANSACT-SQL と #41 です。](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)  
  
  
