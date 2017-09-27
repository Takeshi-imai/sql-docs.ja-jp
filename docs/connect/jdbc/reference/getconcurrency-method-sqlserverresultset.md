---
title: "getConcurrency メソッド (SQLServerResultSet) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerResultSet.getConcurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 207e25f4-769c-4ff3-913c-3517b06208e4
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: eec9174be2430b8711669e479faea89e34f30b4c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getconcurrency-method-sqlserverresultset"></a>getConcurrency メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この同時実行モードを取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getConcurrency()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**同時実行の種類は、次の値のいずれかを示します。  
  
 ResultSet.CONCUR_READ_ONLY  
  
 ResultSet.CONCUR_UPDATABLE  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getConcurrency メソッドは、java.sql.ResultSet インターフェイスの getConcurrency メソッドによって指定されます。  
  
 によって使用された同時実行が決定されます、 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)結果セットを作成するオブジェクト。  
  
 このメソッドを使用すると、実際の同時実行を確認できます。 アプリケーションが CONCUR_READ_ONLY または CONCUR_UPDATABLE を選択した場合は、これらが返されます。 アプリケーションが既定の同時実行を使用した場合は、CONCUR_READ_ONLY が返されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  