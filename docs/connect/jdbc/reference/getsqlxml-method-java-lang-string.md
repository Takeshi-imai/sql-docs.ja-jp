---
title: "getSQLXML (java.lang.String) メソッド |Microsoft ドキュメント"
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
ms.assetid: f56b192a-3255-4215-b552-8e494fbca083
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a44a73f30aec2b193e93dfb62a7a5423e7377cc5
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getsqlxml-method-javalangstring"></a>getSQLXML (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  パラメーター名を指定された SQLXML オブジェクトとして指定されたパラメーターの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final java.sql.SQLXML getSQLXML(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *パラメーター名*  
  
 A**文字列**パラメーターの名前を示すです。  
  
## <a name="return-value"></a>戻り値  
 ASQLXMLobject です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getSQLXML メソッドは、java.sql.CallableStatement インターフェイスの getSQLXML メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [getSQLXML メソッド &#40;です。SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
