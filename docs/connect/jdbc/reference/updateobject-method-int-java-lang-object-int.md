---
title: "updateObject (int、java.lang.Object, int) メソッド |Microsoft ドキュメント"
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
apiname: SQLServerResultSet.updateObject (int, java.lang.Object, int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 9d33571b-4887-49d3-96df-8abda7b5a904
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 02e266b085e2a0cf58f44c511d1a805243e3ddd3
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="updateobject-method-int-javalangobject-int"></a>updateObject (int, java.lang.Object, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列の更新、**オブジェクト**列のインデックスと小数点以下桁数を指定された値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateObject(int index,  
                         java.lang.Object x,  
                         int scale)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 **Int**列インデックスを示すです。  
  
 *obj*  
  
 **オブジェクト**値。  
  
 *scale*  
  
 java.sql.Types.DECIMAL 型または java.sql.Types.NUMERIC 型の場合、この値は小数点以下の桁数になります。 他のすべての型については、この値は無視されます。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>参照  
 [updateObject メソッド &#40;です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/updateobject-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
