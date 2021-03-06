---
title: "UPDATE、DELETE、および INSERT ステートメント |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updating data [ODBC], about updating data
- DELETE [ODBC]
- UPDATE [ODBC]
- INSERT [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 5004ea72-4c49-4064-9752-f7032ba7f133
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 592d135ccf66f8a9fde2cc064a51dc25617cf127
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="update-delete-and-insert-statements"></a>UPDATE、DELETE、および INSERT ステートメント
SQL ベースのアプリケーションを実行してテーブルに変更を加える、**更新**、**削除**、および**挿入**ステートメントです。 これらのステートメントでは、Minimum SQL 文法の準拠レベルの一部であるし、すべてのドライバーとデータ ソースでサポートする必要があります。  
  
 これらのステートメントの構文です。  
  
 **UPDATE**  *table-name*  
  
 **設定***列識別子*  **=**  {*式*&#124; です。**NULL**}  
  
 [**、** *列識別子*  **=**  {*式*&#124; です。**NULL**}].  
  
 [**WHERE** *search-condition*]  
  
 **DELETE FROM** *table-name*[**WHERE** *search-condition*]  
  
 **INSERT INTO** *table-name*[**(***column-identifier* [**,** *column-identifier*]...**)**]  
  
 {*クエリ仕様*&#124;です。**値 (* * * 挿入値*[* *、** *挿入値*].**)**}  
  
 なお、*クエリ仕様*要素は、コアと拡張 SQL 文法とするでのみ有効、*式*と*検索条件*要素の詳細になりますコアと拡張 SQL 文法で複雑です。  
  
 などの他の SQL ステートメント**更新**、**削除**、および**挿入**ステートメントはよりは多くの場合、パラメーターが使用すると、効率的です。 たとえば、次のステートメントを準備および繰り返し実行して、Orders テーブルの複数の行を挿入します。  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 パラメーター値の配列を渡すことによって、この効率性を強化できます。 ステートメントのパラメーターおよびパラメーター値の配列の詳細については、次を参照してください。[ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)です。
