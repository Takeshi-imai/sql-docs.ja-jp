---
title: "getScale メソッド (SQLServerResultSetMetaData) |Microsoft ドキュメント"
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
apiname: SQLServerResultSetMetaData.getScale
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: fe29aa5f-4cc5-413f-8bbd-a58064993d87
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 735f2aa42382009aae985adc10e6ad1affe2d04d
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getscale-method-sqlserverresultsetmetadata"></a>getScale メソッド (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列の小数点以下の桁数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getScale(int column)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *列*  
  
 **Int**列インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 **Int**列の小数点以下桁数を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getScale メソッドは、java.sql.ResultSetMetaData インターフェイスの getScale メソッドによって指定されます。  
  
 [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0 では、DECIMAL_DIGITS 列の動作の変更。 参照してください[SQLServerDatabaseMetaData.getColumns](../../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md)詳細についてはします。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSetMetaData のメンバー](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData クラス](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
