---
title: "SQLSpecialColumns |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4968dfc8ca30b6e6fee9982521b3dc875c3ec048
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="sqlspecialcolumns"></a>SQLSpecialColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  行識別子を要求するとき (*IdentifierType* SQL_BEST_ROWID)、 **SQLSpecialColumns** SQL_SCOPE_CURROW 以外のスコープを要求された空の結果セット (データ行を含まない) を返します。 生成される結果セットは、列がこのスコープ内でのみ有効であることを示します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、識別子の擬似列がサポートされません。 **SQLSpecialColumns**結果セットでは、すべての列は SQL_PC_NOT_PSEUDO として識別します。  
  
 **SQLSpecialColumns**は静的カーソルで実行することができます。 実行すると**SQLSpecialColumns**更新可能な (キーセット ドリブンまたは動的) の結果に対して、カーソルの種類を示す SQL_SUCCESS_WITH_INFO が変更されました。  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a>SQLSpecialColumns による機能強化された日付と時刻のサポート  
 値については返される列の DATA_TYPE、TYPE_NAME、COLUMN_SIZE、buffer_length 列、および decimal_digts の各日付/時刻型に対してを参照してください[カタログ メタデータ](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md)です。  
  
 一般的な情報について、次を参照してください。[日付と時刻の強化 &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)です。  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a>SQLSpecialColumns による大きな CLR UDT のサポート  
 **SQLSpecialColumns**大きなの CLR ユーザー定義型 (Udt) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型 &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLSpecialColumns 関数](http://go.microsoft.com/fwlink/?LinkId=59371)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
