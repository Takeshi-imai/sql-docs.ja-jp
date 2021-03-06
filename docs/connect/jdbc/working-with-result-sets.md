---
title: "結果セットの操作 |Microsoft ドキュメント"
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
ms.assetid: 4fc4b1c6-3075-4ad7-9244-865d9ede7ae6
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9d90a11fa3c617f529d4bc13e3b80f5755423310
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="working-with-result-sets"></a>結果セットの処理
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  含まれるデータを操作する際に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース、データを操作するための 1 つのメソッドは、結果セットを使用します。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 、結果セットの使用をサポートする、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。 SQLServerResultSet オブジェクトを使用すると、SQL ステートメントまたはストアド プロシージャから返されるデータの取得、必要に応じて、データを更新でき、次にデータをデータベースに戻して保持できます。  
  
 さらに、SQLServerResultSet オブジェクトは、データの行間を移動する、取得またはそれに含まれるデータを設定して、基になるデータベースでさまざまなレベルの変更に応答性を確立するためのメソッドを提供します。  
  
> [!NOTE]  
>  結果セットを変更に対する応答性などの管理の詳細については、次を参照してください。 [JDBC ドライバーでの結果セットの管理](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)です。  
  
 このセクションのトピックに含まれているデータを操作する結果セットを使用できるさまざまな方法を説明する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[結果セットのデータ サンプルの取得](../../connect/jdbc/retrieving-result-set-data-sample.md)|結果セットからデータを取得するを使用する方法について説明、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースを表示します。|  
|[結果セットのデータ サンプルの変更](../../connect/jdbc/modifying-result-set-data-sample.md)|挿入、取得、およびデータの変更に結果セットを使用する方法について説明します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。|  
|[結果セットのデータ サンプルのキャッシング](../../connect/jdbc/caching-result-set-data-sample.md)|大量のデータの取得に結果セットを使用する方法について説明します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースをクライアントにそのデータをキャッシュする方法を制御したりします。|  
  
## <a name="see-also"></a>参照  
 [サンプル JDBC Driver アプリケーション](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  
