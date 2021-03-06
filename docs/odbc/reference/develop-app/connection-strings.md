---
title: "接続文字列 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to driver [ODBC], connection strings
- functions [ODBC], data source or driver connections
- connection strings [ODBC], about connection strings
- connecting to data source [ODBC], connection strings
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: 724c7b86-300a-4fa9-ad96-4afa0fdcb3e9
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3abf812d73f780533a77a42498bfde4c299996d5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="connection-strings"></a>接続文字列
接続文字列には、接続の確立に使用される情報が含まれています。 完全な接続文字列には、接続を確立するために必要なすべての情報が含まれています。 接続文字列は、一連のキーワード/値ペアのセミコロンで区切られたです。 (接続文字列の完全な構文を参照してください、 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)関数の説明です)。接続文字列で使用されます。  
  
-   **SQLDriverConnect**ユーザーとの対話によって、接続文字列が完了します。  
  
-   **SQLBrowseConnect**、データ ソースとやり取りしながら、接続文字列が完了します。  
  
 **SQLConnect**接続文字列を使用しませんを使用して**SQLConnect**は正確に 3 つのキーワード/値ペアの接続文字列を使用して接続するのと似ています (データ ソース名とは、必要に応じて、ユーザー ID とパスワード).
