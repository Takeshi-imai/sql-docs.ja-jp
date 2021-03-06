---
title: "SQLServerClob のメンバー |Microsoft ドキュメント"
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
apitype: Assembly
ms.assetid: 7db785ca-edd5-4833-8053-17fdbf87279a
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a8416bd8dea2a36d3421ab44084649e64f39345b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverclob-members"></a>SQLServerClob のメンバー
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  次の表に、によって公開されるメンバー、 [SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)クラスです。  
  
## <a name="constructors"></a>コンス トラクター  
  
|名前|Description|  
|----------|-----------------|  
|[SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-constructor-sqlserverconnection-java-lang-string.md)|SQLServerClob クラスの新しいインスタンスを初期化します。|  
  
## <a name="fields"></a>フィールド  
 [なし] :  
  
## <a name="inherited-fields"></a>継承されたフィールド  
 [なし] :  
  
## <a name="methods"></a>メソッド  
  
|名前|Description|  
|----------|-----------------|  
|[解放](../../../connect/jdbc/reference/free-method-sqlserverclob.md)|このメソッドは、CLOB オブジェクトと、それが占有していたリソースを解放します。|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverclob.md)|Clob を ASCII ストリームとして具体化します。|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverclob.md)|Clob データを、java.io.Reader オブジェクトまたは文字のストリームとして返します。|  
|[getSubString](../../../connect/jdbc/reference/getsubstring-method-sqlserverclob.md)|渡された開始位置とコピーする文字数に基づいて、指定された Clob の部分文字列のコピーを返します。|  
|[長さ](../../../connect/jdbc/reference/length-method-sqlserverclob.md)|Clob の文字数を返します。|  
|[位置](../../../connect/jdbc/reference/position-method-sqlserverclob.md)|指定された開始位置に基づいて、指定された Clob オブジェクトまたは Clob の部分文字列の文字位置を返します。|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlserverclob.md)|ASCII 文字を Clob の指定された位置から書き込むために使用するストリームを返します。|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverclob.md)|Unicode 文字のストリームを Clob の指定された位置から書き込むために使用するストリームを返します。|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)|渡された文字列を Clob の指定された位置から書き込みます。|  
|[truncate](../../../connect/jdbc/reference/truncate-method-sqlserverclob.md)|Clob を指定された長さに切り捨てます。|  
  
## <a name="inherited-methods"></a>継承されたメソッド  
  
|継承されたクラス|メソッド|  
|--------------------------|-------------|  
|java.lang.Object|clone、equals、finalize、getClass、hashCode、notify、notifyAll、toString、wait|  
  
## <a name="see-also"></a>参照  
 [SQLServerClob クラス](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
