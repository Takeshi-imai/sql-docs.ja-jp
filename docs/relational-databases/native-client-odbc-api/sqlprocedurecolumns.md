---
title: "SQLProcedureColumns |Microsoft ドキュメント"
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
- SQLProcedureColumns function
ms.assetid: 6671e180-0072-4de5-90f5-314306d2ba9c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dd9ef3f21e8bcafa103bfd5252d0df621c033922
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="sqlprocedurecolumns"></a>SQLProcedureColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLProcedureColumns**レポートのすべての戻り値の属性に 1 行返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ストアド プロシージャです。  
  
 **SQLProcedureColumns**値が存在するかどうかに関係なく SQL_SUCCESS を返します*CatalogName*、 *SchemaName*、 *ProcName*、または*ColumnName*パラメーター。 **SQLFetch** SQL_NO_DATA が返されるこれらのパラメーターに無効な値を使用する場合。  
  
 **SQLProcedureColumns**は静的サーバー カーソルで実行できます。 実行すると**SQLProcedureColumns**更新可能な (動的カーソルまたはキーセット カーソル) では、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO を返します。  
  
 次の表に、によって返される結果セットとどのように処理する拡張されている列、 **udt**と**xml**データ型を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ODBC ドライバー。  
  
|列名|Description|  
|-----------------|-----------------|  
|SS_UDT_CATALOG_NAME|UDT (ユーザー定義型) を含むカタログの名前を返します。|  
|SS_UDT_SCHEMA_NAME|UDT を含むスキーマの名前を返します。|  
|SS_UDT_ASSEMBLY_TYPE_NAME|UDT のアセンブリ修飾名を返します。|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|XML スキーマ コレクション名が定義されているカタログの名前を返します。 カタログ名が見つからない場合は、この変数に空文字列が含まれます。|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|XML スキーマ コレクション名が定義されているスキーマの名前を返します。 スキーマ名が見つからない場合は、この変数に空文字列が含まれます。|  
|SS_XML_SCHEMACOLLECTION_NAME|XML スキーマ コレクションの名前を返します。 名前が見つからない場合は、この変数に空文字列が含まれます。|  
  
## <a name="sqlprocedurecolumns-and-table-valued-parameters"></a>SQLProcedureColumns とテーブル値パラメーター  
 SQLProcedureColumns は、CLR ユーザー定義型と同様の方法でテーブル値パラメーターを処理します。 テーブル値パラメーターに対して返される行では、列に次の値が設定されます。  
  
|列名|説明/値|  
|-----------------|------------------------|  
|DATA_TYPE|SQL_SS_TABLE|  
|TYPE_NAME|テーブル値パラメーターのテーブル型の名前。|  
|COLUMN_SIZE|NULL|  
|BUFFER_LENGTH|0|  
|DECIMAL_DIGITS|テーブル値パラメーターの列数。|  
|NUM_PREC_RADIX|NULL|  
|NULLABLE|SQL_NULLABLE|  
|REMARKS|NULL|  
|COLUMN_DEF|NULL。 テーブル型には既定値がない場合があります。|  
|SQL_DATA_TYPE|SQL_SS_TABLE|  
|SQL_DATEIME_SUB|NULL|  
|CHAR_OCTET_LENGTH|NULL|  
|IS_NULLABLE|"YES"|  
|SS_TYPE_CATALOG_NAME|テーブル型または CLR ユーザー定義型を含むカタログの名前を返します。|  
|SS_TYPE_SCHEMA_NAME|テーブル型または CLR ユーザー定義型を含むスキーマの名前を返します。|  
  
 SS_TYPE_CATALOG_NAME 列および SS_TYPE_SCHEMA_NAME 列は [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンで利用可能であり、これらの列はそれぞれ、テーブル値パラメーターのカタログとスキーマを返します。 テーブル値パラメーターに加え CLR ユーザー定義型パラメーターに対しても、これらの列が作成されます  (CLR ユーザー定義型パラメーターの既存のスキーマ列とカタログ列は、この追加機能の影響を受けません。 これらの列は、旧バージョンとの互換性を維持するためにも作成されます)。  
  
 SS_TYPE_CATALOG_NAME および SS_TYPE_SCHEMA_NAME は、ODBC 仕様に準拠して、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で追加されたドライバー固有のすべての列の前、かつ ODBC 自体によって指定されるすべての列の後に作成されます。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
## <a name="sqlprocedurecolumns-support-for-enhanced-date-and-time-features"></a>SQLProcedureColumns による機能強化された日付と時刻のサポート  
 日付/時刻型に対して返される値は、次を参照してください。[カタログ メタデータ](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md)です。  
  
 一般的な情報について、次を参照してください。[日付と時刻の強化 &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)です。  
  
## <a name="sqlprocedurecolumns-support-for-large-clr-udts"></a>SQLProcedureColumns による大きな CLR UDT のサポート  
 **SQLProcedureColumns**大きなの CLR ユーザー定義型 (Udt) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型 &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLProcedureColumns 関数](http://go.microsoft.com/fwlink/?LinkId=59363)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
