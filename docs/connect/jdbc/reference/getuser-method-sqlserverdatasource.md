---
title: "getUser メソッド (SQLServerDataSource) |Microsoft ドキュメント"
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
apiname: SQLServerDataSource.getUser
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 3513dd7f-6ae5-4010-bde0-454ac4365bce
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d0be6cc3ac11282b6188129a6b04f3f47043862b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getuser-method-sqlserverdatasource"></a>getUser メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データ ソースへの接続に使用されるユーザー名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.lang.String getUser()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**ユーザー名を格納しています。  
  
## <a name="remarks"></a>解説  
 [SetUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md)メソッドのインスタンスに接続するときに使用されるユーザー名を設定[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。 ユーザー名の値が設定されていない場合、getUser メソッドは既定値の null を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
