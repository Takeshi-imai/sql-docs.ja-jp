---
title: "prepareCall (java.lang.String) メソッド |Microsoft ドキュメント"
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
apiname: SQLServerConnection.prepareCall (java.lang.String)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: cb83b567-4ce5-447a-93cc-895d4eaf3a05
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1d908f7417a637f86c743af36e4a1ec624192663
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="preparecall-method-javalangstring"></a>prepareCall (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  作成、 [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)データベースのストアド プロシージャを呼び出すためのオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.CallableStatement prepareCall(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sql*  
  
 A**文字列**SQL ステートメントを含むです。  
  
## <a name="return-value"></a>戻り値  
 CallableStatement オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この prepareCall メソッドは、java.sql.Connection インターフェイスの prepareCall メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [prepareCall メソッド &#40;です。SQLServerConnection &#41;](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
