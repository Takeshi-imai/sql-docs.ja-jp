---
title: "SQLConnect による接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to driver [ODBC], SQLConnect
- functions [ODBC], data source or driver connections
- SQLConnect function [ODBC], connecting
- connecting to data source [ODBC], SQLConnect
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: b16319d2-2c2c-4341-abb5-caa9e17362b4
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4e3ebe247996127ca1aae6559ece4bdd3f281efc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-with-sqlconnect"></a>SQLConnect による接続
**SQLConnect**最も簡単な接続関数です。 データ ソース名が必要ですし、省略可能なユーザー ID とパスワードを受け取ります。 ハード コード、データ ソース名、ユーザー ID またはパスワードが不要のアプリケーションに対して適切に機能します。 でも使用アプリケーション制御独自「ルック アンド フィール」またはそのユーザー インターフェイスのないにもできます。 このようなアプリケーションを使用してデータ ソースの一覧を作成できる**SQLDataSources**、ユーザーにデータ ソース、ユーザー ID とパスワードを要求し、呼び出す**SQLConnect**です。  
  
 次の例では、Northwind という名前の DSN を使用して、Northwind データベースに接続し、すべての従業員テーブル内のレコードからすべての姓と名フィールドを取得します。  
  
```  
// Connecting_with_SQLConnect.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include <mbstring.h>  
#include <stdio.h>  
  
#define MAX_DATA 100  
#define MYSQLSUCCESS(rc) ((rc == SQL_SUCCESS) || (rc == SQL_SUCCESS_WITH_INFO) )  
  
class direxec {  
   RETCODE rc; // ODBC return code  
   HENV henv; // Environment     
   HDBC hdbc; // Connection handle  
   HSTMT hstmt; // Statement handle  
  
   unsigned char szData[MAX_DATA]; // Returned data storage  
   SDWORD cbData; // Output length of data  
   unsigned char chr_ds_name[SQL_MAX_DSN_LENGTH]; // Data source name  
  
public:  
   direxec(); // Constructor  
   void sqlconn(); // Allocate env, stat, and conn  
   void sqlexec(unsigned char *); // Execute SQL statement  
   void sqldisconn(); // Free pointers to env, stat, conn, and disconnect  
   void error_out(); // Displays errors  
};  
  
// Constructor initializes the string chr_ds_name with the data source name.  
// "Northwind" is an ODBC data source (odbcad32.exe) name whose default is the Northwind database  
direxec::direxec() {  
   _mbscpy_s(chr_ds_name, SQL_MAX_DSN_LENGTH, (const unsigned char *)"Northwind");  
}  
  
// Allocate environment handle and connection handle, connect to data source, and allocate statement handle.  
void direxec::sqlconn() {  
   SQLAllocEnv(&henv);  
   SQLAllocConnect(henv, &hdbc);  
   rc = SQLConnect(hdbc, chr_ds_name, SQL_NTS, NULL, 0, NULL, 0);  
  
   // Deallocate handles, display error message, and exit.  
   if (!MYSQLSUCCESS(rc)) {  
      SQLFreeConnect(henv);  
      SQLFreeEnv(henv);  
      SQLFreeConnect(hdbc);  
      if (hstmt)  
         error_out();  
      exit(-1);  
   }  
  
   rc = SQLAllocStmt(hdbc, &hstmt);  
}  
  
// Execute SQL command with SQLExecDirect() ODBC API.  
void direxec::sqlexec(unsigned char * cmdstr) {  
   rc = SQLExecDirect(hstmt, cmdstr, SQL_NTS);  
   if (!MYSQLSUCCESS(rc)) {  //Error  
      error_out();  
      // Deallocate handles and disconnect.  
      SQLFreeStmt(hstmt,SQL_DROP);  
      SQLDisconnect(hdbc);  
      SQLFreeConnect(hdbc);  
      SQLFreeEnv(henv);  
      exit(-1);  
   }  
   else {  
      for ( rc = SQLFetch(hstmt) ; rc == SQL_SUCCESS ; rc=SQLFetch(hstmt) ) {  
         SQLGetData(hstmt, 1, SQL_C_CHAR, szData, sizeof(szData), &cbData);  
         // In this example, the data is sent to the console; SQLBindCol() could be called to bind   
         // individual rows of data and assign for a rowset.  
         printf("%s\n", (const char *)szData);  
      }  
   }  
}  
  
// Free the statement handle, disconnect, free the connection handle, and free the environment handle.  
void direxec::sqldisconn() {  
   SQLFreeStmt(hstmt,SQL_DROP);  
   SQLDisconnect(hdbc);  
   SQLFreeConnect(hdbc);  
   SQLFreeEnv(henv);  
}  
  
// Display error message in a message box that has an OK button.  
void direxec::error_out() {  
   unsigned char szSQLSTATE[10];  
   SDWORD nErr;  
   unsigned char msg[SQL_MAX_MESSAGE_LENGTH + 1];  
   SWORD cbmsg;  
  
   while (SQLError(0, 0, hstmt, szSQLSTATE, &nErr, msg, sizeof(msg), &cbmsg) == SQL_SUCCESS) {  
      sprintf_s((char *)szData, sizeof(szData), "Error:\nSQLSTATE=%s, Native error=%ld, msg='%s'", szSQLSTATE, nErr, msg);  
      MessageBox(NULL, (const char *)szData, "ODBC Error", MB_OK);  
   }  
}  
  
int main () {  
   direxec x;   // Declare an instance of the direxec object.  
   x.sqlconn();   // Allocate handles, and connect.  
   x.sqlexec((UCHAR FAR *)"SELECT FirstName, LastName FROM employees");   // Execute SQL command  
   x.sqldisconn();   // Free handles and disconnect  
}  
```