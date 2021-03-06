---
title: "Sql ステートメントを使用して |Microsoft ドキュメント"
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
ms.assetid: fe28f48a-e1bc-48ff-a5e7-c24cd6e5ecc7
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e672add8738558615d01d6d402bec5cbe34dc295
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="using-statements-with-sql"></a>SQL でのステートメントの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  データを操作する際に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースを使用して、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]およびインライン SQL ステートメントがさまざまなクラスを使用することができます。 使用するクラスは、実行する SQL ステートメントの種類によって異なります。  
  
 使用して、SQL ステートメントに IN パラメーターが含まれていない場合、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)クラス場合は、パラメーターが含まれて、使用、 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)クラスです。  
  
> [!NOTE]  
>  両方に含まれる SQL ステートメントを使用する必要があり、OUT パラメーターにする必要がありますストアド プロシージャとして実装を使用して呼び出すこと、 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスです。 詳細については、ストアド プロシージャを使用して、次を参照してください。[ストアド プロシージャを使用してステートメント](../../connect/jdbc/using-statements-with-stored-procedures.md)です。  
  
 次のセクションでは、さまざまなシナリオでデータの操作についての説明、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SQL ステートメントを使用してデータベース。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[パラメーターのない SQL ステートメントの使用](../../connect/jdbc/using-an-sql-statement-with-no-parameters.md)|パラメーターを含まない SQL ステートメントの使用方法について説明します。|  
|[パラメーターがある SQL ステートメントの使用](../../connect/jdbc/using-an-sql-statement-with-parameters.md)|パラメーターを含む SQL ステートメントの使用方法について説明します。|  
|[SQL ステートメントを使用したデータベース オブジェクトの変更](../../connect/jdbc/using-an-sql-statement-to-modify-database-objects.md)|SQL ステートメントを使用してデータベース オブジェクトを変更する方法について説明します。|  
|[SQL ステートメントを使用したデータの変更](../../connect/jdbc/using-an-sql-statement-to-modify-data.md)|SQL ステートメントを使用してデータベースのデータを変更する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーでのステートメントの使用](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
