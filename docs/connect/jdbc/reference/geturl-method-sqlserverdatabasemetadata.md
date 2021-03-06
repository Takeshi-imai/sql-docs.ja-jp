---
title: "getURL メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDatabaseMetaData.getURL
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: fcb66851-db5f-4ae8-b728-d129480b6f42
caps.latest.revision: "20"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cbc569dbd45ede9429b6299e2f37d7f7a5cb269c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="geturl-method-sqlserverdatabasemetadata"></a>getURL メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースの URL を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getURL()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**URL を格納しています。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getURL メソッドは、java.sql.DatabaseMetaData インターフェイスの getURL メソッドによって指定されます。  
  
 使用する場合、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]で、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データベースで、このメソッドが戻る、**文字列**次の情報を含む値です。  
  
-   URL 値の "jdbc:sqlserver://"  
  
-   省略可能な接続プロパティなど**serverName**、 **instanceName**、および**portNumber**  
  
-   他の接続プロパティによって、ユーザーとすべての接続プロパティが空または null 以外のドライバーを既定値の設定を除く**userName**、**パスワード**、および**integratedSecurity**.  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
