---
title: "prepareStatement (java.lang.String、int, int) メソッド |Microsoft ドキュメント"
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
apiname: SQLServerConnection.prepareStatement (java.lang.String, int, int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 5bb96dbe-f673-41b5-911b-8f661cca071a
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1f95cff779202f7dc5c03855b098ca78b6fe43eb
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="preparestatement-method-javalangstring-int-int"></a>prepareStatement (java.lang.String, int, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  作成、 [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)を生成するオブジェクト[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)特定の種類および同時実行のオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.PreparedStatement prepareStatement(java.lang.String sSql,  
                                                   int resultSetType,  
                                                   int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sSql*  
  
 A**文字列**SQL ステートメントを含むです。  
  
 *resultSetType*  
  
 **Int**結果セットの種類を示すです。  
  
 *resultSetConcurrency*  
  
 **Int**結果セットの同時実行の種類を示すです。  
  
## <a name="return-value"></a>戻り値  
 PreparedStatement オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この prepareStatement メソッドは、java.sql.Connection インターフェイスの prepareStatement メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection メソッド](../../../connect/jdbc/reference/sqlserverconnection-methods.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
