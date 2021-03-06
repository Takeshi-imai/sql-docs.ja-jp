---
title: "sqlsrv_next_result |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: sqlsrv_next_result
apitype: NA
helpviewer_keywords:
- multiple result sets
- sqlsrv_next_result
- stored procedure support
- API Reference, sqlsrv_next_result
ms.assetid: 41270d16-0003-417c-b837-ea51439654cd
caps.latest.revision: "26"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fb34a1e134bf13f797157fbe49d1cb210fb4f036
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="sqlsrvnextresult"></a>sqlsrv_next_result
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

指定したステートメントの次の結果 (結果セット、行数、または出力パラメーター) をアクティブにします。  
  
> [!NOTE]  
> バッチ クエリまたはストアド プロシージャによって返される最初の (または唯一の) の結果を呼び出さなくてもアクティブな**sqlsrv_next_result**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_next_result( resource $stmt )  
```  
  
#### <a name="parameters"></a>パラメーター  
*$stmt*: 次の結果をアクティブにした、実行されたステートメントです。  
  
## <a name="return-value"></a>戻り値  
次の結果を正常にアクティブにできたら、ブール値 **true** が返されます。 次の結果をアクティブにする際にエラーが発生した場合、 **false** が返されます。 これ以上結果がない場合、 **null** が返されます。  
  
## <a name="example"></a>例  
次の例では、 *Production.ProductReview* テーブルに製品のレビューに挿入するストアド プロシージャを作成して実行します。その後、指定した製品のすべてのレビューを選択します。 ストアド プロシージャの実行後、最初の結果 (の挿入クエリ、ストアド プロシージャの影響を受ける行の数) は呼び出さずに消費**sqlsrv_next_result**です。 次の結果 (ストアド プロシージャで SELECT クエリによって返される行) を使用可能を呼び出して**sqlsrv_next_result**を使用して消費[sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)です。  
  
> [!NOTE]  
> 正規の構文を使用してストアド プロシージャを呼び出すことをお勧めします。 正規の構文の詳細については、「 [ストアド プロシージャの呼び出し](http://go.microsoft.com/fwlink/?linkid=119517)」を参照してください。  
  
この例では、SQL Server および [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) データベースはローカル コンピューターにインストールされていることを前提にしています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Drop the stored procedure if it already exists. */  
$tsql_dropSP = "IF OBJECT_ID('InsertProductReview', 'P') IS NOT NULL  
                DROP PROCEDURE InsertProductReview";  
$stmt1 = sqlsrv_query( $conn, $tsql_dropSP);  
if( $stmt1 === false )  
{  
     echo "Error in executing statement 1.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Create the stored procedure. */  
$tsql_createSP = " CREATE PROCEDURE InsertProductReview  
                                    @ProductID int,  
                                    @ReviewerName nvarchar(50),  
                                    @ReviewDate datetime,  
                                    @EmailAddress nvarchar(50),  
                                    @Rating int,  
                                    @Comments nvarchar(3850)  
                   AS  
                       BEGIN  
                             INSERT INTO Production.ProductReview   
                                         (ProductID,  
                                          ReviewerName,  
                                          ReviewDate,  
                                          EmailAddress,  
                                          Rating,  
                                          Comments)  
                                    VALUES  
                                         (@ProductID,  
                                          @ReviewerName,  
                                          @ReviewDate,  
                                          @EmailAddress,  
                                          @Rating,  
                                          @Comments);  
                             SELECT * FROM Production.ProductReview  
                                WHERE ProductID = @ProductID;  
                       END";  
$stmt2 = sqlsrv_query( $conn, $tsql_createSP);  
  
if( $stmt2 === false)  
{  
     echo "Error in executing statement 2.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
/*-------- The next few steps call the stored procedure. --------*/  
  
/* Define the Transact-SQL query. Use question marks (?) in place of the  
parameters to be passed to the stored procedure */  
$tsql_callSP = "{call InsertProductReview(?, ?, ?, ?, ?, ?)}";  
  
/* Define the parameter array. */  
$productID = 709;  
$reviewerName = "Customer Name";  
$reviewDate = "2008-02-12";  
$emailAddress = "customer@email.com";  
$rating = 3;  
$comments = "[Insert comments here.]";  
$params = array(   
                 $productID,  
                 $reviewerName,  
                 $reviewDate,  
                 $emailAddress,  
                 $rating,  
                 $comments  
               );  
  
/* Execute the query. */  
$stmt3 = sqlsrv_query( $conn, $tsql_callSP, $params);  
if( $stmt3 === false)  
{  
     echo "Error in executing statement 3.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Consume the first result (rows affected by INSERT query in the  
stored procedure) without calling sqlsrv_next_result. */  
echo "Rows affectd: ".sqlsrv_rows_affected($stmt3)."-----\n";  
  
/* Move to the next result and display results. */  
$next_result = sqlsrv_next_result($stmt3);  
if( $next_result )  
{  
     echo "\nReview information for product ID ".$productID.".---\n";  
     while( $row = sqlsrv_fetch_array( $stmt3, SQLSRV_FETCH_ASSOC))  
     {  
          echo "ReviewerName: ".$row['ReviewerName']."\n";  
          echo "ReviewDate: ".date_format($row['ReviewDate'],  
                                             "M j, Y")."\n";  
          echo "EmailAddress: ".$row['EmailAddress']."\n";  
          echo "Rating: ".$row['Rating']."\n\n";  
     }  
}  
elseif( is_null($next_result))  
{  
     echo "No more results.\n";  
}  
else  
{  
     echo "Error in moving to next result.\n";  
     die(print_r(sqlsrv_errors(), true));  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt1 );  
sqlsrv_free_stmt( $stmt2 );  
sqlsrv_free_stmt( $stmt3 );  
sqlsrv_close( $conn );  
?>  
```  
  
出力パラメーターがあるストアド プロシージャを実行する場合は、出力パラメーターの値にアクセスする前にその他のすべての結果を消費することをお勧めします。 詳細については、「 [方法: SQLSRV ドライバーを使用してパラメーターの方向を指定する](../../connect/php/how-to-specify-parameter-direction-using-the-sqlsrv-driver.md)」を参照してください。  
  
## <a name="example"></a>例  
次の例では、指定した製品 ID の製品レビュー情報を取得し、製品のレビューを挿入し、次いで指定した製品 ID の製品レビュー情報を再取得するバッチ クエリを実行します。 新しく挿入した製品のレビューは、バッチ クエリの最終的な結果セットに含められます。 この例では [sqlsrv_next_result](../../connect/php/sqlsrv-next-result.md) を使用し、バッチ クエリの 1 つの結果から、次に移動します。  
  
> [!NOTE]  
> バッチ クエリまたはストアド プロシージャによって返される最初の (または唯一の) の結果を呼び出さなくてもアクティブな**sqlsrv_next_result**です。  
  
この例では、 *AdventureWorks* データベースの [Purchasing.ProductReview](http://go.microsoft.com/fwlink/?linkid=67739) テーブルを使用します。また、このデータベースがサーバーにインストールされていることを前提としています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Define the batch query. */  
$tsql = "--Query 1  
         SELECT ProductID, ReviewerName, Rating   
         FROM Production.ProductReview   
         WHERE ProductID=?;  
  
         --Query 2  
         INSERT INTO Production.ProductReview (ProductID,   
                                               ReviewerName,   
                                               ReviewDate,   
                                               EmailAddress,   
                                               Rating)  
         VALUES (?, ?, ?, ?, ?);  
  
         --Query 3  
         SELECT ProductID, ReviewerName, Rating   
         FROM Production.ProductReview   
         WHERE ProductID=?;";  
  
/* Assign parameter values and execute the query. */  
$params = array(798,   
                798,   
                'CustomerName',   
                '2008-4-15',   
                'test@customer.com',   
                3,   
                798 );  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if( $stmt === false )  
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the first result. */  
echo "Query 1 result:\n";  
while( $row = sqlsrv_fetch_array( $stmt, SQLSRV_FETCH_NUMERIC ))  
{  
     print_r($row);  
}  
  
/* Move to the next result of the batch query. */  
sqlsrv_next_result($stmt);  
  
/* Display the result of the second query. */  
echo "Query 2 result:\n";  
echo "Rows Affected: ".sqlsrv_rows_affected($stmt)."\n";  
  
/* Move to the next result of the batch query. */  
sqlsrv_next_result($stmt);  
  
/* Retrieve and display the third result. */  
echo "Query 3 result:\n";  
while( $row = sqlsrv_fetch_array( $stmt, SQLSRV_FETCH_NUMERIC ))  
{  
     print_r($row);  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt );  
sqlsrv_close( $conn );  
?>  
```  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)  
[データの取得](../../connect/php/retrieving-data.md)  
[データの更新 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)  
[サンプル アプリケーション &#40;SQLSRV ドライバー&#41;](../../connect/php/example-application-sqlsrv-driver.md)  
  
