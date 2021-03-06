---
title: date (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- date_TSQL
- date
dev_langs:
- TSQL
helpviewer_keywords:
- data types [SQL Server], date
- date and time [SQL Server], date
- dates [SQL Server], data types
- date data type [SQL Server]
- data types [SQL Server], date and time
ms.assetid: c963e8b4-5a85-4bd0-9d48-3f8da8f6516b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 1776f70f2136f7b46fe3aa9205f76108a2807170
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="date-transact-sql"></a>date (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で日付を定義します。
  
## <a name="date-description"></a>date の説明
  
|プロパティ|ReplTest1|  
|--------------|-----------|  
|構文|**date**|  
|使用方法|DECLARE @MyDate **date**<br /><br /> CREATE TABLE Table1 ( Column1 **date** )|  
|既定の文字列リテラル形式<br /><br /> (下位のクライアントに使用)|-YYYY-MM-DD<br /><br /> 詳細については、以下の「下位クライアントの下位互換性」セクションを参照してください。|  
|範囲|0001-01-01 ～ 9999-12-31 (Informatica の場合は 1582-10-15 ～ 9999-12-31)<br /><br /> 1 年 1 月 1 日 CE ～ 9999 年 12 月 31 日 CE (Informatica の場合は 1582 年 10 月 15 日 CE ～9999 年 12 月 31 日 CE)|  
|要素範囲|YYYY は、0001 ～ 9999 の年を表す 4 桁の数字です。 Informatica では、YYYY は 1582 ～ 9999 の範囲に制限されます。<br /><br /> MM は、指定された年の 01 ～ 12 の月を表す 2 桁の数字です。<br /><br /> DD は、指定された月の (月に応じて) 01 ～ 31 の日を表す 2 桁の数字です。|  
|文字長|10 文字|  
|有効桁数、小数点以下桁数|10, 0|  
|ストレージのサイズ|3 バイト、固定|  
|ストレージ構造|1 つの 3 バイト整数で日付を格納します。|  
|精度|1 日|  
|既定値|1900-01-01<br /><br /> この値は、**time** から **datetime2** または **datetimeoffset** への暗黙的な変換で、付加的な日付要素として使用されます。|  
|カレンダー|グレゴリオ暦|  
|ユーザー定義の 1 秒未満の秒の有効桁数|いいえ|  
|タイム ゾーン オフセットへの対応と保持|いいえ|  
|夏時間への対応|いいえ|  
  
## <a name="supported-string-literal-formats-for-date"></a>date でサポートされる文字列リテラル形式
次の表は、**date** データ型に使用できる有効な文字列リテラル形式を示しています。
  
|数値|Description|  
|-------------|-----------------|  
|mdy<br /><br /> [m]m/dd/[yy]yy<br /><br /> [m] m - dd-[yy] yy<br /><br /> [m]m.dd.[yy]yy<br /><br /> myd<br /><br /> mm/[yy]yy/dd<br /><br /> mm-[yy]yy/dd<br /><br /> [m]m.[yy]yy.dd<br /><br /> dmy<br /><br /> dd/[m]m/[yy]yy<br /><br /> dd-[m]m-[yy]yy<br /><br /> dd.[m]m.[yy]yy<br /><br /> dym<br /><br /> dd/[yy]yy/[m]m<br /><br /> dd-[yy]yy-[m]m<br /><br /> dd.[yy]yy.[m]m<br /><br /> ymd<br /><br /> [yy]yy/[m]m/dd<br /><br /> [yy]yy-[m]m-dd<br /><br /> [yy]yy-[m]m-dd|[m]m、dd、および [yy]yy は、スラッシュ (/)、ハイフン (-)、またはピリオド (.) で区切られた文字列の月、日、および年を表します。<br /><br /> 4 桁または 2 桁の年だけがサポートされています。 可能な限り 4 桁の年を使用してください。 2 桁の年を 4 桁の西暦年として解釈する場合に、基準になる年を 0001 ～ 9999 の範囲の整数で指定するには、「[two digit year cutoff サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md)」を使用します。<br /><br /> **メモ** Informatica では、YYYY は 1582 ～ 9999 の範囲に制限されます。<br /><br /> 2 桁の西暦が、終了年の末尾の 2 桁の数値以下である場合は、終了年と同じ世紀として解釈されます。 終了年の末尾の 2 桁の数値よりも大きい場合は、終了年の 1 つ前の世紀と解釈されます。 たとえば、two digit year cutoff が 2049 (既定値) である場合、2 桁表記が 49 であれば、2049 年と解釈されます。2 桁表記が 50 であれば、1950 年と解釈されます。<br /><br /> 既定の日付形式は、現在の言語設定によって決まります。 日付形式は、[SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) ステートメントおよび [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md) ステートメントを使って変更できます。<br /><br /> **date** では、**ydm** 形式はサポートされません。|  
  
|アルファベット|Description|  
|------------------|-----------------|  
|mon [dd][,] yyyy<br /><br /> mon dd[,] [yy]yy<br /><br /> mon yyyy [dd]<br /><br /> [dd] mon[,] yyyy<br /><br /> dd mon[,][yy]yy<br /><br /> dd [yy]yy mon<br /><br /> [dd] yyyy mon<br /><br /> yyyy mon [dd]<br /><br /> yyyy [dd] mon|**ydm** は、現在の言語における月の正式名または省略形を表します。 コンマは省略可能であり、大文字と小文字は無視されます。<br /><br /> こうしたあいまいさを排除するため、4 桁の西暦を使用してください。<br /><br /> 日を省略したときは、その月の 1 日が指定されます。|  
  
|ISO 8601|説明|  
|--------------|----------------|  
|-YYYY-MM-DD<br /><br /> YYYYMMDD|SQL 標準と同じです。 これが国際標準として定義された唯一の形式です。|  
  
|区切りなし|Description|  
|-----------------|-----------------|  
|[yy]yymmdd<br /><br /> yyyy[mm][dd]|**date** データは、4 桁、6 桁、または 8 桁で指定できます。 6 桁または 8 桁の文字列は、常に **ymd** と解釈されます。 月と日は常に 2 桁です。 4 桁の文字列は年として解釈されます。|  
  
|ODBC|Description|  
|----------|-----------------|  
|{ d 'yyyy-mm-dd' }|ODBC API 固有です。|  
  
|W3C XML 形式|Description|  
|--------------------|-----------------|  
|yyyy-mm-ddTZD|XML/SOAP 用にサポートされています。<br /><br /> TZD は、タイム ゾーン指定子 (Z または +hh:mm または -hh:mm) です。<br /><br /> -   hh:mm はタイム ゾーン オフセットを表します。 hh は、タイム ゾーン オフセットの時間数を表す 0 ～ 14 の 2 桁の数字です。<br />-   MM は、タイム ゾーン オフセットの付加的な分数を表す 0 ～ 59 の 2 桁の数字です。<br />-   タイム ゾーン オフセットでは、+ (正負号) または – (負符号) を必ず指定します。 ローカル時刻を取得する際、協定世界時 (UTC) を基準としてタイム ゾーン オフセットを加算するか、減算するかを示します。 タイム ゾーン オフセットの有効範囲は -14:00 ～ +14:00 までです。|  
  
## <a name="ansi-and-iso-8601-compliance"></a>ANSI および ISO 8601 への準拠  
**date** は、グレゴリオ暦に対する ANSI SQL 標準の定義に従います。ANSI SQL 標準の NOTE 85 には、"Datetime データ型では、グレゴリオ形式の日付を 0001–01–01 CE ～ 9999–12–31 CE の日付範囲で格納できます" と定義されています。
  
下位クライアント用の既定の文字列リテラル形式は、SQL 標準形式 (YYYY-MM-DD) に準拠します。 この形式は、DATE に対する ISO 8601 の定義と同じです。
  
> [!NOTE]  
>  Informatica の場合、範囲は 1582-10-15 (1582 年 10 月 15 日 CE) から 9999-12-31 (9999 年 12 月 31 日 CE) に制限されます。  
  
## <a name="backward-compatibility-for-down-level-clients"></a>下位クライアントの下位互換性
一部の下位レベル クライアントは、**time**、**date**、**datetime2**、**datetimeoffset** データ型をサポートしていません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の上位インスタンスと下位クライアントの間のデータ型マッピングを次の表に示します。
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ型|下位クライアントに渡される既定の文字列リテラル形式|下位 ODBC|下位 OLEDB|下位 JDBC|下位 SQLCLIENT|  
| --- | --- | --- | --- | --- | --- |
|**time**|hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR または SQL_VARCHAR|DBTYPE_WSTR または DBTYPE_STR|Java.sql.String|String または SqString|  
|**date**|-YYYY-MM-DD|SQL_WVARCHAR または SQL_VARCHAR|DBTYPE_WSTR または DBTYPE_STR|Java.sql.String|String または SqString|  
|**datetime2**|YYYY-MM-DD hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR または SQL_VARCHAR|DBTYPE_WSTR または DBTYPE_STR|Java.sql.String|String または SqString|  
|**datetimeoffset**|YYYY-MM-DD hh:mm:ss[.nnnnnnn] [+&#124;-]hh:mm|SQL_WVARCHAR または SQL_VARCHAR|DBTYPE_WSTR または DBTYPE_STR|Java.sql.String|String または SqString|  
  
## <a name="converting-date-and-time-data"></a>日付および時刻データ型の変換
data データ型と time データ型に変換する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で日付や時刻と認識できない値はすべて拒否されます。 CAST 関数および CONVERT 関数で日付と時刻のデータを使用する方法については、「[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)」をご覧ください。  
  
### <a name="converting-date-to-other-date-and-time-types"></a>date から他の日付/時刻データ型への変換
ここでは、**date** データ型が他の日付/時刻データ型に変換される場合の処理について説明します。
  
**time(n)** に変換すると、変換は失敗し、エラー メッセージ 206 "オペランド型の不整合: date は time と互換性がありません" が発生します。
  
**datetime** に変換する場合は、日付がコピーされます。 次のコードでは、`date` の値を `datetime` の値に変換した結果を示します。
  
```sql
DECLARE @date date= '12-10-25';  
DECLARE @datetime datetime= @date;  
  
SELECT @date AS '@date', @datetime AS '@datetime';  
  
--Result  
--@date      @datetime  
------------ -----------------------  
--2025-12-10 2025-12-10 00:00:00.000  
--  
--(1 row(s) affected)  
```  
  
**smalldatetime** への変換では、**date** の値が [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) の範囲内にある場合は、日付部分がコピーされ、時刻部分が 00:00:00.000 に設定されます。 **date** の値が **smalldatetime** 値の範囲外の場合は、"date データ型から smalldatetime データ型への変換の結果、範囲外の値になりました" というエラー メッセージ 242 が表示され、**smalldatetime** の値は NULL に設定されます。 次のコードでは、`date` の値を `smalldatetime` の値に変換した結果を示します。
  
```sql
DECLARE @date date= '1912-10-25';  
DECLARE @smalldatetime smalldatetime = @date;  
  
SELECT @date AS '@date', @smalldatetime AS '@smalldatetime';  
  
--Result  
--@date      @smalldatetime  
------------ -----------------------  
--1912-10-25 1912-10-25 00:00:00  
--  
--(1 row(s) affected)  
```  
  
**datetimeoffset(n)** への変換の場合は、日付がコピーされ、時刻が 00:00.0000000 +00:00 に設定されます。 次のコードでは、`date` の値を `datetimeoffset(3)` の値に変換した結果を示します。
  
```sql
DECLARE @date date = '1912-10-25';  
DECLARE @datetimeoffset datetimeoffset(3) = @date;  
  
SELECT @date AS '@date', @datetimeoffset AS '@datetimeoffset';  
  
--Result  
--@date      @datetimeoffset  
------------ ------------------------------  
--1912-10-25 1912-10-25 00:00:00.000 +00:00  
--  
--(1 row(s) affected)  
```  
  
**datetime2(n)** への変換では、日付部分がコピーされ、時刻部分が 00:00.000000 に設定されます。 次のコードでは、`date` の値を `datetime2(3)` の値に変換した結果を示します。
  
```sql
DECLARE @date date = '1912-10-25'  
DECLARE @datetime2 datetime2(3) = @date;  
  
SELECT @date AS '@date', @datetime2 AS '@datetime2(3)';  
  
--Result  
--@date      @datetime2(3)  
------------ -----------------------  
--1912-10-25 1912-10-25 00:00:00.000  
--  
--(1 row(s) affected)  
```  
  
### <a name="converting-string-literals-to-date"></a>文字列リテラルの日付への変換
文字列リテラルから日付/時刻データ型への変換は、文字列のすべての部分が有効な形式になっている場合に可能になります。 それ以外の場合は実行時エラーが発生します。 日付/時刻データ型から文字列リテラルへの暗黙的な変換や、スタイルを指定しない明示的な変換では、現在のセッションの既定の形式が使用されます。 次の表では、文字列リテラルを **date** データ型に変換する規則を示します。
  
|入力文字列リテラル|**date**|  
|---|---|
|ODBC 日付|ODBC 文字列リテラルは、**datetime** データ型にマップされます。 ODBC 日付時刻リテラルから **date** 型への代入演算を行うと、**datetime** 型とこれらの型との間で、変換規則で定義されている暗黙的な変換が行われます。|  
|ODBC 時刻|上記の ODBC 日付の規則を参照。|  
|ODBC 日付時刻|上記の ODBC 日付の規則を参照。|  
|DATE のみ|単純変換|  
|TIME のみ|既定値が設定される|  
|タイム ゾーンのみ|既定値が設定される|  
|日付 + 時刻|入力文字列の日付部分が使用される|  
|日付 + タイム ゾーン|許可されていません。|  
|時刻 + タイム ゾーン|既定値が設定される|  
|日付 + 時刻 + タイム ゾーン|ローカル datetime の日付部分が使用される|  
  
## <a name="examples"></a>使用例  
次の例では、文字列をそれぞれの日付および時刻データ型にキャストした結果を比較します。
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29. 1234567 +12:15' AS time(7)) AS 'time'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS date) AS 'date'   
    ,CAST('2007-05-08 12:35:29.123' AS smalldatetime) AS   
        'smalldatetime'   
    ,CAST('2007-05-08 12:35:29.123' AS datetime) AS 'datetime'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS datetime2(7)) AS   
        'datetime2'  
    ,CAST('2007-05-08 12:35:29.1234567 +12:15' AS datetimeoffset(7)) AS   
        'datetimeoffset';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|データ型|[出力]|  
|---------------|------------|  
|**time**|12:35:29. 1234567|  
|**date**|2007-05-08|  
|**smalldatetime**|2007-05-08 12:35:00|  
|**datetime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**datetimeoffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
## <a name="see-also"></a>参照
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  
