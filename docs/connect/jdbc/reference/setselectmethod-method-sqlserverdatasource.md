---
title: "setSelectMethod メソッド (SQLServerDataSource) |Microsoft ドキュメント"
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
apiname: SQLServerDataSource.setSelectMethod
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 7934276d-5ac9-4cbc-a2a0-2c65c93733ac
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1348b8e7724edb9366ffff07594874dcc8d5c2b0
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setselectmethod-method-sqlserverdatasource"></a>setSelectMethod メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  これを使用して作成されるすべての結果セットに使用される既定のカーソルの種類を設定[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setSelectMethod(java.lang.String selectMethod)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *selectMethod*  
  
 A**文字列**既定のカーソルの種類を含む値です。  
  
## <a name="remarks"></a>解説  
 selectMethod は、結果セットで使用される既定のカーソルの種類です。 このプロパティは、大きな結果セットを処理しているときに、クライアント側のメモリに結果セット全体を格納したくない場合に役立ちます。 このプロパティを "cursor" に設定することで、一度にフェッチするデータのチャンクを小さくできるサーバー側のカーソルを作成できます。 SelectMethod プロパティが設定されていない場合[getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md) "direct"の既定値を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
