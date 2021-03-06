---
title: "SQL Server で JSON データを操作する | Microsoft Docs"
ms.custom: 
ms.date: 01/31/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.component: json
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- JSON
- JSON, built-in support
ms.assetid: c9a4e145-33c3-42b2-a510-79813e67806a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: a59a53bb9c279a8f66a4aa259212269179d477b1
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="json-data-in-sql-server"></a>SQL Server の JSON データ
[!INCLUDE[appliesto-ss2016-asdb-xxxx-xxx-md.md](../../includes/appliesto-ss2016-asdb-xxxx-xxx-md.md)]

JSON は、最新の Web アプリケーションとモバイル アプリケーションでデータを交換するために使用される、一般的なテキスト形式のデータ形式です。 また、JSON はログ ファイル内の非構造化データや Microsoft Azure Cosmos DB のような NoSQL データベースを格納するためも使用されます。 REST Web サービスの多くは結果を JSON テキスト形式で返し、データを JSON 形式で受け取ります。 たとえば、Azure Search、Azure Storage、Azure Cosmos DB などの Azure のほとんどのサービスには、JSON を返すか使用する REST エンドポイントがあります。 JSON は、AJAX 呼び出しを使用して Web ページおよび Web サーバー間でデータをやり取りするための主な形式でもあります。 
 
JSON テキストの例を次に示します。 
 
```json 
[{
    "name": "John",
    "skills": ["SQL", "C#", "Azure"]
}, {
    "name": "Jane",
    "surname": "Doe"
}]
``` 
 
SQL Server の組み込みの関数と演算子を使用すると、JSON テキストで次の操作を実行できます。 
 
- JSON テキストを解析し、値を読み取るか、変更する。  
- JSON オブジェクトの配列を表形式に変換する。  
- 変換された JSON オブジェクトに対して任意の Transact-SQL クエリを実行する。  
- Transact-SQL クエリの結果を JSON 形式で書式設定する。  
  
![組み込みの JSON サポートの概要](../../relational-databases/json/media/jsonslides1overview.png "組み込みの JSON サポートの概要")  
  
## <a name="key-json-capabilities-of-sql-server-and-sql-database"></a>SQL Server と SQL Database の主な JSON 機能
SQL Server がその組み込みの JSON サポートで提供する主な機能について以下に説明します。

### <a name="extract-values-from-json-text-and-use-them-in-queries"></a>JSON テキストから値を抽出し、それらをクエリで使用する
データベース テーブルに格納されている JSON テキストがある場合は、組み込み関数を使用して JSON テキスト内の値を読み取るか、変更することができます。  
  
-   **JSON_VALUE** 。JSON 文字列からスカラー値を抽出します。
-   **JSON_QUERY** 。JSON 文字列からオブジェクトまたは配列を抽出します。
-   **ISJSON** 。文字列に有効な JSON が含まれているかどうかをテストします。
-   **JSON_MODIFY**。JSON 文字列の値を変更します。

**例**
  
次の例のクエリでは、テーブルからリレーショナル データと (`jsonCol` という名前の列に格納された) JSON データの両方を使用しています。  
  
```sql  
SELECT Name,Surname,
 JSON_VALUE(jsonCol,'$.info.address.PostCode') AS PostCode,
 JSON_VALUE(jsonCol,'$.info.address."Address Line 1"')+' '
  +JSON_VALUE(jsonCol,'$.info.address."Address Line 2"') AS Address,
 JSON_QUERY(jsonCol,'$.info.skills') AS Skills
FROM People
WHERE ISJSON(jsonCol)>0
 AND JSON_VALUE(jsonCol,'$.info.address.Town')='Belgrade'
 AND Status='Active'
ORDER BY JSON_VALUE(jsonCol,'$.info.address.PostCode')
```  
  
アプリケーションやツールでは、スカラー テーブル列から取得した値であるか、JSON 列から取得した値であるかの見分けは付きません。 JSON テキストからの値は、Transact-SQL クエリのすべての部分で使用できます (例: WHERE 句、ORDER BY 句、または GROUP BY 句、ウィンドウの集計など)。 JSON 関数は、JavaScript のような構文を使用して JSON テキスト内の値を参照します。

詳細については、「[組み込み関数を使用した JSON データの検証、クエリ、変更 (SQL Server)](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md)」、「[JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md)」、「[JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md)」を参照してください。  
  
### <a name="change-json-values"></a>JSON 値の変更
JSON テキストの一部を修正する必要がある場合は、**JSON_MODIFY** 関数を使用して JSON 文字列のプロパティの値を更新し、更新された JSON 文字列を返します。 次の例では、JSON を格納する変数のプロパティの値を更新します。  
  
```sql  
DECLARE @jsonInfo NVARCHAR(MAX)

SET @jsonInfo=JSON_MODIFY(@jsonInfo,'$.info.address[0].town','London') 
```  
  
### <a name="convert-json-collections-to-a-rowset"></a>JSON コレクションを行セットに変換する
SQL Server で JSON のクエリを実行するのにカスタム クエリ言語は不要です。 JSON データのクエリを実行するには、標準の T-SQL を使用することができます。 JSON データのクエリまたはレポートを作成する必要がある場合は、**OPENJSON** 行セット関数を呼び出して JSON データを簡単に行と列に変換できます。 詳細については、[OPENJSON を使用して JSON データを行と列に変換する方法 (SQL Server)](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md) に関するページを参照してください。  
  
次の例では、**OPENJSON** を呼び出し、`@json` 変数に格納されたオブジェクトの配列を、標準の SQL **SELECT** ステートメントを使用してクエリを実行できる行セットに変換します。  
  
```sql  
DECLARE @json NVARCHAR(MAX)
SET @json =  
N'[  
       { "id" : 2,"info": { "name": "John", "surname": "Smith" }, "age": 25 },  
       { "id" : 5,"info": { "name": "Jane", "surname": "Smith" }, "dob": "2005-11-04T12:00:00" }  
 ]'  
   
SELECT *  
FROM OPENJSON(@json)  
  WITH (id int 'strict $.id',  
        firstName nvarchar(50) '$.info.name', lastName nvarchar(50) '$.info.surname',  
        age int, dateOfBirth datetime2 '$.dob')  
```  
  
**結果**  
  
|id|firstName|lastName|age|dateOfBirth|  
|--------|---------------|--------------|---------|-----------------|  
|2|John|Smith|25||  
|5|Jane|Smith||2005-11-04T12:00:00|  
  
**OPENJSON** では、JSON オブジェクトの配列がテーブルに変換され、各オブジェクトが 1 つの行として表わされ、キーと値のペアがセルとして返されます。 出力は、次の規則を監視します。
- **OPENJSON** は JSON 値を **WITH** 句で指定された型に変換します。
- **OPENJSON** は、フラットなキーと値のペアと、入れ子になった階層構造のオブジェクトの両方を処理できます。
- JSON テキストに含まれるすべてのフィールドを返す必要はありません。
- JSON 値が存在しない場合、**OPENJSON** は NULL 値を返します。
- オプションで型指定の後にパスを指定して、入れ子にされたプロパティを参照するか、異なる名前のプロパティを参照できます。
- パス内の省略可能な **strict** プレフィックスでは、指定されたプロパティの値が JSON テキストに存在していなければならないことを指定します。

詳細については、[OPENJSON を使用して JSON データを行と列に変換する方法 (SQL Server)](../../relational-databases/json/convert-json-data-to-rows-and-columns-with-openjson-sql-server.md) に関するページと「[OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md)」を参照してください。  
  
### <a name="convert-sql-server-data-to-json-or-export-json"></a>SQL Server のデータを JSON に変換または JSON をエクスポートする
**FOR JSON** 句を **SELECT** ステートメントに追加して、SQL Server データまたは SQL クエリの結果を JSON として書式設定します。 **FOR JSON** を使用して、JSON 出力の形式設定をクライアント アプリケーションから SQL Server に委任します。 詳細については、「[FOR JSON を使用してクエリ結果を JSON として書式設定する (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)」を参照してください。  
  
次の例では、PATH モードを **FOR JSON** 句とともに使用しています。  
  
```sql  
SELECT id, firstName AS "info.name", lastName AS "info.surname", age, dateOfBirth as dob  
FROM People  
FOR JSON PATH  
```  
  
[曜日] **FOR JSON** 句は SQL 結果を JSON テキスト形式に設定し、JSON を理解するすべてのアプリケーションで使用できます。 PATH オプションでは、SELECT 句にドット区切りのエイリアスを使用して、クエリ結果内のオブジェクトを入れ子にします。  
  
**結果**  
  
```json  
[{
    "id": 2,
    "info": {
        "name": "John",
        "surname": "Smith"
    },
    "age": 25
}, {
    "id": 5,
    "info": {
        "name": "Jane",
        "surname": "Smith"
    },
    "dob": "2005-11-04T12:00:00"
}] 
```  
  
詳細については、「[FOR JSON を使用してクエリ結果を JSON として書式設定する (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)」と「[FOR 句 (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md)」を参照してください。  
  
## <a name="combine-relational-and-json-data"></a>リレーショナル データと JSON データを結合する
SQL Server は、標準の Transact-SQL 言語を使用してリレーショナル データと JSON データの両方を格納および処理するハイブリッド モデルを提供します。 テーブル内の JSON ドキュメントのコレクションを整理し、それらの間のリレーションシップを確立、テーブルに格納された厳密に型指定されたスカラー列を JSON 列に格納された柔軟なキーと値のペアに結合し、完全な Transact-SQL を使用して 1 つ以上のテーブルのスカラー値と JSON 値の両方についてクエリを実行します。
 
JSON テキストは varchar 列または nvarchar 列に格納されており、プレーン テキストとしてインデックスが作成されます。 テキストをサポートするすべての SQL Server の機能またはコンポーネントは JSON をサポートします。そのため、JSON とその他の SQL Server 機能間の対話には、ほとんど制約がありません。 JSON はメモリ内テーブルやテンポラル テーブルに格納できるほか、行レベルのセキュリティの述語を JSON テキストに適用することなどができます。

純粋な JSON ワークロードがあり、JSON ドキュメントの処理のためにカスタマイズされたクエリ言語を使用する場合は、Microsoft Azure [Cosmos DB](https://azure.microsoft.com/services/cosmos-db/) の使用をお勧めします。  
  
ここでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で組み込みの JSON サポートの使用方法を示すユース ケースを紹介します。  

## <a name="store-and-index-json-data-in-sql-server"></a>JSON データの SQL Server への格納とインデックスの追加

JSON データの SQL Server への保存、インデックスの追加、最適化のオプションに関する詳細については、次の記事を参照してください。
-   [SQL Server または SQL Database に JSON ドキュメントを格納する](store-json-documents-in-sql-tables.md)
-   [JSON データへのインデックスの追加](index-json-data.md)
-   [インメモリ OLTP を使用した JSON の処理の最適化](optimize-json-processing-with-in-memory-oltp.md)

### <a name="load-json-files-into-sql-server"></a>SQL Server に JSON ファイルを読み込む  
ファイルに格納された情報は、標準の JSON または行区切りの JSON 形式に書式設定できます。 SQL Server は JSON ファイルのコンテンツをインポートし、**OPENJSON** または **JSON_VALUE** 関数を使用してそれを解析してテーブルに読み込むことができます。  
  
-   JSON ドキュメントが SQL Server がアクセスできるローカル ファイル、共有ネットワーク ドライブ、Azure File の場所に格納されている場合は、一括インポートを使用して SQL Server に JSON データを読み込むことができます。 このシナリオの詳細については、「[Importing JSON files into SQL Server using OPENROWSET (BULK)](http://blogs.msdn.com/b/sqlserverstorageengine/archive/2015/10/07/importing-json-files-into-sql-server-using-openrowset-bulk.aspx)」(OPENROWSET (BULK) を使用して SQL Server に JSON ファイルをインポートする) を参照してください。  
  
-   行区切りの JSON ファイルが Azure Blob Storage または Hadoop ファイル システムに格納されている場合、PolyBase を使用して JSON テキストを読み込み、Transact-SQL コードでそれを解析してテーブルに読み込むことができます。  

### <a name="import-json-data-into-sql-server-tables"></a>SQL Server に JSON データをインポートする  
JSON データを外部サービスから SQL Server に読み込む必要がある場合は、アプリケーション レイヤー内でデータを解析する代わりに、**OPENJSON** を使用してデータを SQL Server にインポートできます。  
  
```sql  
DECLARE @jsonVariable NVARCHAR(MAX)

SET @jsonVariable = N'[  
        {  
          "Order": {  
            "Number":"SO43659",  
            "Date":"2011-05-31T00:00:00"  
          },  
          "AccountNumber":"AW29825",  
          "Item": {  
            "Price":2024.9940,  
            "Quantity":1  
          }  
        },  
        {  
          "Order": {  
            "Number":"SO43661",  
            "Date":"2011-06-01T00:00:00"  
          },  
          "AccountNumber":"AW73565",  
          "Item": {  
            "Price":2024.9940,  
            "Quantity":3  
          }  
       }  
  ]'
  
INSERT INTO SalesReport  
SELECT SalesOrderJsonData.*  
FROM OPENJSON (@jsonVariable, N'$.Orders.OrdersArray')  
           WITH (  
              Number   varchar(200) N'$.Order.Number',   
              Date     datetime     N'$.Order.Date',  
              Customer varchar(200) N'$.AccountNumber',   
              Quantity int          N'$.Item.Quantity'  
           )  
  AS SalesOrderJsonData;  
```  
  
JSON 変数の内容は、外部 REST サービスによって提供されたり、クライアント側 JavaScript フレームワークからのパラメーターとして送信されたり、外部ファイルから読み込まれたりします。 結果は、JSON テキストから SQL Server テーブルに簡単に挿入、更新、マージできます。 このシナリオの詳細については、次のブログの投稿を参照してください。
-   [JSON データを SQL Server にインポートする](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/09/22/openjson-the-easiest-way-to-import-json-text-into-table/)
-   [Upsert JSON documents in SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/03/upsert-json-documents-in-sql-server-2016)
-   [GeoJSON データを SQL Server 2016 に読み込む](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/05/loading-geojson-data-into-sql-server/)  

## <a name="analyze-json-data-with-sql-queries"></a>SQL クエリで JSON データを分析する  
レポート作成のために JSON データをフィルター処理または集計する必要がある場合は、**OPENJSON** を使用して JSON をリレーショナル形式に変換できます。 その後、標準の [!INCLUDE[tsql](../../includes/tsql-md.md)] と組み込み関数を使用してレポートを用意することができます。  
  
```sql  
SELECT Tab.Id, SalesOrderJsonData.Customer, SalesOrderJsonData.Date  
FROM   SalesOrderRecord AS Tab  
          CROSS APPLY  
     OPENJSON (Tab.json, N'$.Orders.OrdersArray')  
           WITH (  
              Number   varchar(200) N'$.Order.Number',   
              Date     datetime     N'$.Order.Date',  
              Customer varchar(200) N'$.AccountNumber',   
              Quantity int          N'$.Item.Quantity'  
           )  
  AS SalesOrderJsonData  
WHERE JSON_VALUE(Tab.json, '$.Status') = N'Closed'  
ORDER BY JSON_VALUE(Tab.json, '$.Group'), Tab.DateModified  
```  
  
同じクエリに標準テーブルの列と JSON テキストからの値の両方を使用できます。 `JSON_VALUE(Tab.json, '$.Status')` 式にインデックスを追加して、クエリのパフォーマンスを向上させることができます。 詳細については、「[JSON データへのインデックスの追加](../../relational-databases/json/index-json-data.md)」を参照してください。
 
## <a name="return-data-from-a-sql-server-table-formatted-as-json"></a>JSON として書式設定された SQL Server テーブルからデータを返す  
データベース層からデータを取得し、それを JSON 形式で返す Web サービスがある場合、または JSON 形式に設定されたデータを受け取る JavaScript フレームワークまたはライブラリがある場合、JSON 出力を SQL クエリで直接設定できます。 コードを記述するかライブラリを追加して、表形式のクエリ結果を変換し、それからオブジェクトを JSON 形式にシリアル化する代わりに、**FOR JSON** を使用して JSON 形式への設定を SQL Server に委任できます。  
  
たとえば、OData の仕様に準拠した JSON 出力を生成するとします。 Web サービスは、次の形式の要求と応答を求めています。 
  
-   要求: `/Northwind/Northwind.svc/Products(1)?$select=ProductID,ProductName`  
  
-   応答: `{"@odata.context":"http://services.odata.org/V4/Northwind/Northwind.svc/$metadata#Products(ProductID,ProductName)/$entity","ProductID":1,"ProductName":"Chai"}`  
  
この OData URL は、`id` が 1 の製品の ProductID 列と ProductName 列に対する要求を表します。 **FOR JSON** を使用して、出力を SQL Server で求められている形式に設定できます。  
  
```sql  
SELECT 'http://services.odata.org/V4/Northwind/Northwind.svc/$metadata#Products(ProductID,ProductName)/$entity'
 AS '@odata.context',   
 ProductID, Name as ProductName   
FROM Production.Product  
WHERE ProductID = 1  
FOR JSON AUTO  
```  
  
このクエリの出力は、OData 仕様に完全に準拠した JSON テキストになります。形式設定とエスケープは、SQL Server によって処理されます。 SQL Server ではクエリ結果を OData JSON や GeoJSON など、任意の形式に設定することもできます。 詳細については、「[Returning spatial data in GeoJSON format](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/05/returning-spatial-data-in-geojson-format-part-1)」(空間データを GeoJSON 形式で返す) を参照してください。  
  
## <a name="test-drive-built-in-json-support-with-the-adventureworks-sample-database"></a>AdventureWorks サンプル データベースを使用して、組み込みの JSON サポートを試用できます。
AdventureWorks サンプル データベースを入手するには、[Microsoft ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=49502)から最小限のデータベース ファイルとサンプルおよびスクリプト ファイルをダウンロードしてください。 
 
SQL Server 2016 のインスタンスにサンプル データベースを復元したら、サンプル ファイルを展開し、JSON フォルダーから *JSON Sample Queries procedures views and indexes.sql* ファイルを開きます。 このファイルのスクリプトを実行して JSON データとして既存のデータの一部の形式を再度設定し、JSON データに対してサンプル クエリとレポートをテストしてから、JSON データにインデックスを付けて JSON をインポートおよびエクスポートします。  
  
ファイルに含まれているスクリプトでは、次のことを実行できます。  
  
* 既存のスキーマを非正規化して JSON データの列を作成する。
  
    * SalesReasons、SalesOrderDetails、SalesPerson、Customer、およびその他の販売注文に関する情報を含むテーブルからの情報を、SalesOrder_json テーブルの JSON 列に格納します。  
  
    * EmailAddresses/PersonPhone テーブルからの情報を、Person_json に JSON オブジェクトの配列として格納します。  
  
* JSON データに対してクエリを実行するプロシージャとビューを作成する。  
  
* JSON データにインデックスを追加する。 JSON のプロパティとフルテキスト インデックスにインデックスを作成する。  
  
* JSON をインポートおよびエクスポートする。 Person テーブルと SalesOrder テーブルのコンテンツを JSON の結果としてエクスポートする、および JSON 入力をインポートして Person テーブルと SalesOrder テーブルを更新するプロシージャを作成して実行します。  
  
* サンプル クエリを実行する。 手順 2 と 4 で作成したストアド プロシージャとビューを呼び出すいくつかのクエリを実行します。  
  
* スクリプトをクリーンアップする。 手順 2 と 4 で作成したストアド プロシージャとビューを保持する場合は、この部分を実行しないでください。  
  
## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>SQL Server と Azure SQL Database の JSON の詳細情報  
  
### <a name="microsoft-blog-posts"></a>マイクロソフトのブログ記事  
  
具体的なソリューション、ユース ケース、推奨事項については、SQL Server および Azure SQL Database に組み込まれている JSON のサポートに関する[ブログ投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)を参照してください。  

### <a name="microsoft-videos"></a>Microsoft ビデオ

SQL Server と Azure SQL Database に組み込まれている JSON のサポートの視覚的な紹介は、次のビデオをご覧ください。

*SQL Server 2016 と JSON のサポート*
> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support/player]

*SQL Server 2016 と Azure SQL Database での JSON の使用*
> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database/player]

*NoSQL とリレーショナル環境間の架け橋としての JSON*
> [!VIDEO https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds/player]
   
### <a name="reference-articles"></a>関連記事  
  
-   [FOR 句 (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md) (FOR JSON)  
-   [OPENJSON (Transact-SQL)](../../t-sql/functions/openjson-transact-sql.md)  
-   [JSON 関数 (TRANSACT-SQL)](../../t-sql/functions/json-functions-transact-sql.md)  
    -   [ISJSON (TRANSACT-SQL)](../../t-sql/functions/isjson-transact-sql.md)  
    -   [JSON_VALUE (Transact-SQL)](../../t-sql/functions/json-value-transact-sql.md)  
    -   [JSON_QUERY (Transact-SQL)](../../t-sql/functions/json-query-transact-sql.md)  
    -   [JSON_MODIFY (Transact-SQL)](../../t-sql/functions/json-modify-transact-sql.md)  
  
  
