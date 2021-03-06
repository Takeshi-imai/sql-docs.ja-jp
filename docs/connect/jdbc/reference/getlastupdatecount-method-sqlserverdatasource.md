---
title: "getLastUpdateCount メソッド (SQLServerDataSource) |Microsoft ドキュメント"
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
apiname: SQLServerDataSource.getLastUpdateCount
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 4c4fbb24-0b02-42da-928c-a903bb591cc7
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: db133035f7145c61fb856fcfa308550d9883da17
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getlastupdatecount-method-sqlserverdatasource"></a>getLastUpdateCount メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  返します、**ブール**lastUpdateCount プロパティが有効かどうかを示す値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean getLastUpdateCount()  
```  
  
## <a name="return-value"></a>戻り値  
 **true** lastUpdateCount が有効になっている場合。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 LastUpdateCount プロパティ設定されている場合**true**、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]最後だけを返す、サーバーに渡された SQL ステートメントからの更新プログラムの数。 LastUpdateCount プロパティ設定されている場合**false**ドライバーはすべての更新数が発生した可能性があるすべてのトリガーによって返されるものなどを返します。 LastUpdateCount プロパティが設定されていない場合、getLastUpdateCount メソッドは、の既定値を返します**true**です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
