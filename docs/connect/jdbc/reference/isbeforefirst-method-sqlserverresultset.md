---
title: "isBeforeFirst メソッド (SQLServerResultSet) |Microsoft ドキュメント"
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
apiname: SQLServerResultSet.isBeforeFirst
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: e0e2bd28-6949-47dc-b9dd-145ffb337069
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c15e9a81eaad27b21cd9c7ebcf835d9e1ae54023
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="isbeforefirst-method-sqlserverresultset"></a>isBeforeFirst メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この最初の行の前にカーソルがあるかどうかを取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean isBeforeFirst()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**最初の行の前に、カーソルがある場合。 **false**またはその他の任意の位置にカーソルがある場合、結果セットに行が含まれていない場合。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この isBeforeFirst メソッドは、java.sql.ResultSet インターフェイスの isBeforeFirst メソッドによって指定されます。  
  
 このメソッドが動的カーソル (順方向専用、読み取り専用カーソルを含む) で使用され、selectMethod 接続プロパティが "cursor" に設定されている場合は、例外が発生します。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
