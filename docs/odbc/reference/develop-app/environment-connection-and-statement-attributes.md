---
title: "環境、接続、およびステートメント属性 |Microsoft ドキュメント"
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
- environment attributes [ODBC]
- connection attributes [ODBC]
- statement attributes [ODBC]
ms.assetid: 9e15b276-3b7a-428a-b72f-a3ddfe1ba1ce
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7d1270026a19c0e5c07a9590f70096046984e455
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="environment-connection-and-statement-attributes"></a>環境、接続、およびステートメント属性
ODBC では、環境、接続、またはステートメントに関連付けられている属性の数を定義します。  
  
 環境属性では、接続プールを有効にするかどうかなど、環境全体に影響します。 環境属性が設定されて**SQLSetEnvAttr**されで取得された**SQLGetEnvAttr**です。  
  
 接続属性に影響を与える接続ごとに個別に、方法などがタイムアウトする前に、データ ソースに接続中にドライバーが待機します。接続属性が設定されて**SQLSetConnectAttr**されで取得された**SQLGetConnectAttr**です。 接続属性の詳細については、次を参照してください。[接続属性](../../../odbc/reference/develop-app/connection-attributes.md)です。  
  
 ステートメント属性は、各ステートメントを個別に、ステートメントを非同期的に実行する必要があるかどうかなど影響します。 ステートメント属性が設定されて**SQLSetStmtAttr**されで取得された**SQLGetStmtAttr**です。 いくつかのステートメント属性は読み取り専用の属性であり、設定することはできません。 たとえば、SQL_ATTR_ROW_NUMBER ステートメント属性を使用する場合は、カーソルの現在の行の数を取得する、は読み取り専用です。 ステートメント属性の詳細については、次を参照してください。[ステートメント属性](../../../odbc/reference/develop-app/statement-attributes.md)です。  
  
 ドライバーには、ODBC によって定義された属性、に加えて、独自の接続とステートメント属性を定義できます。 2 つのドライバーの製造元が同じ整数値に割り当てない異なる、専用の属性を確認するグループを開くには、ドライバー定義の属性を登録する必要があります。 詳細については、次を参照してください。[ドライバー固有のデータ型、記述子の種類、情報の種類、診断の種類、および属性](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)です。  
  
 属性の一覧については、次を参照してください。 [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)、 [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)、および[SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)です。 ほとんどの属性に影響を与える ODBC 関数の説明にも説明します。
