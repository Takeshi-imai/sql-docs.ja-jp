---
title: "setReadOnly メソッド (SQLServerConnection) |Microsoft ドキュメント"
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
apiname: SQLServerConnection.setReadOnly
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: bd11fd50-f092-43a0-a6bc-c63e70cff8da
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7acd45c0594d53e4121f1162c98a91a183b650a8
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setreadonly-method-sqlserverconnection"></a>setReadOnly メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  これは、 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトをデータベースの最適化を有効にするには、JDBC driver にヒントとしての読み取り専用モードにします。  
  
> [!NOTE]  
>  このメソッドでサポートされていない、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]です。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setReadOnly(boolean readOnly)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *読み取り専用*  
  
 **true**接続する場合は読み取り専用です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setReadOnly メソッドは、java.sql.Connection インターフェイスの setReadOnly メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
