---
title: "getParameterMode メソッド (SQLServerParameterMetaData) |Microsoft ドキュメント"
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
apiname: SQLServerParameterMetaData.getParameterMode
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: d93c9b70-18c2-44bb-a6de-70a7e940d806
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 089a9996eb22fd354b394a61624a00f5b3a489d3
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getparametermode-method-sqlserverparametermetadata"></a>getParameterMode メソッド (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターのモードを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getParameterMode(int param)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *param*  
  
 **Int**パラメーター インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 **Int**を示す、モードを指定されたパラメーターの値は次のいずれかを指定することができます。  
  
 ParameterMetaData.parameterModeIn  
  
 ParameterMetaData.parameterModeInOut  
  
 ParameterMetaData.parameterModeOut  
  
 ParameterMetaData.parameterModeUnknown  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getParameterMode メソッドは、java.sql.ParameterMetaData インターフェイスの getParameterMode メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerParameterMetaData のメソッド](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData のメンバー](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData クラス](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
