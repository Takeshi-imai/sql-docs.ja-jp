---
title: "setBinaryStream メソッド (SQLServerBlob) |Microsoft ドキュメント"
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
apiname: SQLServerBlob.setBinaryStream
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: abcec31f-1a60-4765-9725-8cf7e9f1f8ab
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1ac8acfad3cd0bc279edf0d11d230d17eaebf195
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="setbinarystream-method-sqlserverblob"></a>setBinaryStream メソッド (SQLServerBlob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  BLOB 値への書き込みに使用できるストリームを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.OutputStream setBinaryStream(long pos)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Pos*  
  
 書き込みを開始する BLOB 値内の位置です。  
  
## <a name="return-value"></a>戻り値  
 出力ストリームです。  
  
## <a name="exceptions"></a>例外  
 java.sql.SQLException  
  
## <a name="remarks"></a>解説  
 この setBinaryStream メソッドは、java.sql.Blob インターフェイスの setBinaryStream メソッドによって指定されます。  
  
 BLOB のデータは、指定された開始位置から出力ストリームによって上書きされ、BLOB の初期データの長さをオーバーランすることができます。 位置 + 1 の値を指定すると、バイトが追加されます。 開始位置に BLOB の長さ + 2 以上 (または 0 以下) の値を渡すと、位置のエラーがスローされます。  
  
## <a name="see-also"></a>参照  
 [SQLServerBlob のメソッド](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob のメンバー](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob クラス](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
