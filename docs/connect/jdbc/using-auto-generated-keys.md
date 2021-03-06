---
title: "生成されたキーを Auto を使用して |Microsoft ドキュメント"
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
ms.assetid: 55a062c7-45ce-40e3-9a6f-4a0f4da4e2a6
caps.latest.revision: "18"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b0b4689b22287f2c6bf96d89f5ff0540d513d4de
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="using-auto-generated-keys"></a>自動生成キーの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]生成された行識別子を自動的に取得する JDBC 3.0 Api がオプションをサポートしています。 この機能の主な重要性は、クエリ、およびサーバーに対する 2 回目のラウンドトリップを要求することなく、データベース テーブルを更新するアプリケーションで IDENTITY 値を利用できることです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]識別子の擬似列をサポートしていませんが、自動生成キー機能を使用する必要がある更新プログラムが ID 列を含むテーブルに対して実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]1 つのテーブルの 1 つは IDENTITY 列だけを許可します。 によって返される結果セットは[getGeneratedKeys](../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)のメソッド、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)クラスは 1 列だけで返される列名は GENERATED_KEYS を持ちます。 生成されたキーが IDENTITY 列のないテーブルで要求された場合、JDBC ドライバーは null の結果セットを返します。  
  
 たとえば、次の表を作成、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
```  
  
 次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]関数に渡し、サンプル データベース、SQL ステートメントを作成、テーブルにデータを追加して、ステートメントを実行し、ID 列の値が表示されます。  
  
 [!code[JDBC#UsingAutoGeneratedKeys1](../../connect/jdbc/codesnippet/Java/using-auto-generated-keys_1.java)]  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーでのステートメントの使用](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
