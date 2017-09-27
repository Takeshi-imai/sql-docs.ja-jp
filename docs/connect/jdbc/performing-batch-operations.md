---
title: "バッチ操作の実行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a576d95-7da6-4b7b-8b32-59e5b4d354c4
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 01a355319eb7c65bd87e25137e013b14406048c4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="performing-batch-operations"></a>バッチ操作の実行
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  複数の更新プログラムと、パフォーマンスを向上させるために、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースが発生した場合、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]バッチとも呼びます作業の 1 つの単位として複数の更新を送信する機能を提供します。  
  
 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)、 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)、および[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスすべて使用できますをバッチ更新を送信します。 [AddBatch](../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)コマンドを追加するメソッドを使用します。 [ClearBatch](../../connect/jdbc/reference/clearbatch-method-sqlserverpreparedstatement.md)コマンドの一覧を消去するメソッドを使用します。 [ExecuteBatch](../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md)処理のためのすべてのコマンドを送信するメソッドを使用します。 バッチの一部として実行できるのは、単純に更新数を返すデータ操作言語 (DML) ステートメントおよびデータ定義言語 (DDL) ステートメントだけです。  
  
 ExecuteBatch メソッドの配列を返します**int**各コマンドの更新数に対応する値。 コマンドのいずれかが失敗した場合は、BatchUpdateException がスローされ、BatchUpdateException クラスの getUpdateCounts メソッドを使用して、更新数の配列を取得する必要があります。 いずれかのコマンドが失敗した場合、JDBC ドライバーでは残りのコマンドの処理は続行されます。 ただし、コマンドに構文エラーがある場合は、バッチ内のステートメントが失敗します。  
  
> [!NOTE]  
>  更新数を使用していない場合に SET nocount ON ステートメントを最初に発行できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 これによりネットワーク トラフィックが減少し、アプリケーションのパフォーマンスがさらに強化されます。  
  
 たとえば、次の表を作成、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
```  
  
 次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベースが関数に渡された、addBatch メソッドが実行されるステートメントを作成するために使用、および executeBatch メソッドは、データベースにバッチを送信します。  
  
```  
public static void executeBatchUpdate(Connection con) {  
   try {  
      Statement stmt = con.createStatement();  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('X', 100)");  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('Y', 200)");  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('Z', 300)");  
      int[] updateCounts = stmt.executeBatch();  
      stmt.close();  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーでステートメントを使用します。](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  