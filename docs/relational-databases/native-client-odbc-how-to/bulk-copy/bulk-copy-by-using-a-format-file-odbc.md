---
title: "フォーマット ファイル (ODBC) を使用して一括コピー |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- bulk copy using format file [ODBC]
- ODBC, bulk copy operations
ms.assetid: 970fd3af-f918-4fc3-a5b1-92596515d4de
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3f8c656fef2db1b137fbd10828e25accc6b25ff7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="bulk-copy-by-using-a-format-file-odbc"></a>フォーマット ファイルを使用した一括コピー (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  このサンプルでは、ODBC bcp_init 関数をフォーマット ファイルと共に使用する方法を示します。  
  
### <a name="to-bulk-copy-by-using-a-format-file"></a>フォーマット ファイルを使用して一括コピーするには  
  
1.  環境ハンドルおよび接続ハンドルを割り当てます。  
  
2.  一括コピー操作が有効になるように SQL_COPT_SS_BCP および SQL_BCP_ON を設定します。  
  
3.  Microsoft® SQL Server™ に接続します。  
  
4.  呼び出す[bcp_init](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)を次の情報を設定します。  
  
    -   一括コピー操作の対象になるテーブルまたはビューの名前  
  
    -   データベースにコピーするデータが含まれたデータ ファイルの名前、またはデータベースからのコピー時にデータを受け取るデータ ファイルの名前  
  
    -   一括コピー エラー メッセージを受信するデータ ファイルの名前 (メッセージ ファイルが不要な場合は NULL を指定)。  
  
    -   コピーの方向 (ファイルからテーブルまたはビューへのコピーの場合は DB_IN)  
  
5.  呼び出す[bcp_readfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)一括コピー操作で使用するデータ ファイルを記述したフォーマット ファイルを読み取れません。  
  
6.  呼び出す[bcp_exec](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)を一括コピー操作を実行します。  
  
## <a name="example"></a>例  
 このサンプルは IA64 ではサポートされていません。  
  
 AdventureWorks と呼ばれる ODBC データ ソース (既定のデータベースは AdventureWorks サンプル データベース) が必要です  (AdventureWorks サンプル データベースは、[Microsoft SQL Server のサンプルとコミュニティのプロジェクト](http://go.microsoft.com/fwlink/?LinkID=85384)のホーム ページからダウンロードできます)。このデータ ソースには、オペレーティング システムに用意されている ODBC ドライバーが使用されている必要があります (ドライバー名は "SQL Server")。 このサンプルを 64 ビット オペレーティング システムで 32 ビット アプリケーションとしてビルドし、実行する場合、%windir%\SysWOW64\odbcad32.exe の ODBC アドミニストレーターを使用して ODBC データ ソースを作成する必要があります。  
  
 このサンプルでは、コンピューターの既定の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスに接続します。 名前付きインスタンスに接続するには、ODBC データ ソースの定義を変更し、server\namedinstance 形式でそのインスタンスを指定します。 [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] は、既定で名前付きインスタンスとしてインストールされます。  
  
 最初の実行 ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) コード サンプルを使用するテーブルを作成するリスト。  
  
 2 つ目のコード リストをコピーし、Bcpfmt.fmt という名前のファイルに貼り付けます。 テーブルの各列はタブ文字で区切られています。  
  
 3 つ目のコード リストをコピーし、Bcpodbc.bcp という名前のファイルに貼り付けます。 ファイル内の各キャリッジ リターンの前にはタブ文字があります。  
  
 odbc32.lib と odbcbcp.lib を使用して 4 つ目の (C++) コード リストをコンパイルします。 MSBuild.exe でビルドした場合は、まずプロジェクト ディレクトリの Bcpfmt.fmt と Bcpodbc.bcp を .exe があるディレクトリにコピーし、次に .exe を起動します。  
  
 5 つ目の ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) コード リストを実行して、サンプルで使用したテーブルを削除します。  
  
```  
use AdventureWorks  
CREATE TABLE BCPDate (cola int, colb datetime)  
```  
  
```  
8.0  
2  
1SQLCHAR04"\t"1colaSQL_Latin1_General_Cp437_Bin  
2SQLCHAR08"\r\n"2colbSQL_Latin1_General_Cp437_Bin  
```  
  
```  
1  
2  
  
```  
  
```  
// compile with: odbc32.lib odbcbcp.lib  
#include <stdio.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
HDBC hdbc1 = SQL_NULL_HDBC;   
  
void Cleanup() {  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
   SDWORD cRows;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle, set BCP mode, and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLSetConnectAttr(hdbc1, SQL_COPT_SS_BCP, (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetConnectAttr(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security. Create SQL Server DSN using Windows NT authentication.  
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "BCPDate", "BCPODBC.bcp", NULL, DB_IN);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Read the format file.  
   retcode = bcp_readfmt(hdbc1, "BCPFMT.fmt");  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_readfmt(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the bulk copy.  
   retcode = bcp_exec(hdbc1, &cRows);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_exec(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied in = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
```  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPDate')  
     DROP TABLE BCPDate  
GO  
```  
  
## <a name="see-also"></a>参照  
 [一括コピーでは、SQL Server ODBC ドライバーの操作方法に関するトピック &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/bulk-copy/bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md)   
 [データ ファイルとフォーマット ファイルの使用](../../../relational-databases/native-client-odbc-bulk-copy-operations/using-data-files-and-format-files.md)  
  
  