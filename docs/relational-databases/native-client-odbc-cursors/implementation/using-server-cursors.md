---
title: "サーバー カーソルの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-cursors
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ODBC applications, cursors
- cursors [ODBC], server cursors
- ODBC cursors, server cursors
- server cursors [SQL Server]
ms.assetid: 8a6d99b7-10b8-4474-8639-4914b25ba170
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d4d7c4d1ff435aa662ca128e595b580ccd91fff6
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="using-server-cursors"></a>サーバー カーソルの使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  ODBC アプリケーションでは、ODBC カーソル属性のいずれかを設定、既定値以外にする場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーが、同じ種類の API サーバー カーソルを実装するサーバーを要求します。 API サーバー カーソルを使用すると、クライアント側のメモリを解放でき、クライアントとサーバー間のネットワーク トラフィックを大幅に削減できます。  
  
 API サーバー カーソルの潜在的な欠点は、現時点では、すべての SQL ステートメントをサポートしているわけではないことです。 次の機能は、API サーバー カーソルでは実行できません。  
  
-   複数の結果セットを返すバッチまたはストアド プロシージャ  
  
-   COMPUTE 句、COMPUTE BY 句、FOR BROWSE 句、または INTO 句を伴う SELECT ステートメント  
  
-   リモート ストアド プロシージャを参照する EXECUTE ステートメント  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続している場合、サーバー カーソルを使用してこのような特性のステートメントを実行すると、カーソルは既定の結果セットに変換されます。 以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に接続している場合は、エラーになります。  
  
## <a name="see-also"></a>参照  
 [カーソルの実装方法](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  
