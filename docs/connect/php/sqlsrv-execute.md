---
title: "sqlsrv_execute |Microsoft ドキュメント"
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
apiname: sqlsrv_execute
apitype: NA
helpviewer_keywords:
- sqlsrv_exclude
- executing queries
- API Reference, sqlsrv_execute
ms.assetid: 38331bc2-4391-4f9f-aa83-9873dad605a0
caps.latest.revision: "24"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e73d11dd8d28d8cd845b71ea5694d1ad61ceada0
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="sqlsrvexecute"></a>sqlsrv_execute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

事前に準備されたステートメントを実行します。 実行するステートメントの準備の詳細については、「 [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) 」を参照してください。  
  
> [!NOTE]  
> この関数は、さまざまなパラメーター値を使用して事前に準備したステートメントを複数回実行する場合に適しています。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_execute( resource $stmt)  
```  
  
#### <a name="parameters"></a>パラメーター  
*$stmt*: 実行するステートメントを指定するリソースです。 ステートメント リソースの作成方法の詳細については、「 [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)」を参照してください。  
  
## <a name="return-value"></a>戻り値  
ブール値: ステートメントが正常に実行された場合、 **true** です。 それ以外の場合は、 **false**です。  
  
## <a name="example"></a>例  
次の例では、 *AdventureWorks* データベースの [Sales.SalesOrderDetail](http://go.microsoft.com/fwlink/?LinkID=67739) テーブルのフィールドを更新するステートメントを実行します。 この例では、ローカル コンピューターに SQL Server および AdventureWorks データベースがインストールされていることを前提にしています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false)  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET OrderQty = ( ?)   
         WHERE SalesOrderDetailID = ( ?)";  
  
/* Set up the parameters array. Parameters correspond, in order, to  
question marks in $tsql. */  
$params = array( 5, 10);  
  
/* Create the statement. */  
$stmt = sqlsrv_prepare( $conn, $tsql, $params);  
if( $stmt )  
{  
     echo "Statement prepared.\n";  
}  
else  
{  
     echo "Error in preparing statement.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Execute the statement. Display any errors that occur. */  
if( sqlsrv_execute( $stmt))  
{  
      echo "Statement executed.\n";  
}  
else  
{  
     echo "Error in executing statement.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)  
[sqlsrv_query](../../connect/php/sqlsrv-query.md)  
  
