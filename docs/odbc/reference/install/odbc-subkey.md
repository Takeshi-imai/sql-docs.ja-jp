---
title: "ODBC サブキー |Microsoft ドキュメント"
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
- registry entries for data sources [ODBC], ODBC subkey
- subkeys [ODBC], ODBC subkey
- ODBC subkey [ODBC]
ms.assetid: f9534144-8f42-4946-b0fb-638e9dcde9c8
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bf33666d0bf8c02b91b26d94f72ec2883e4cba9d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-subkey"></a>ODBC のサブキー
ODBC のサブキーの下の値は、ODBC トレース オプションを指定します。 によって表示される ODBC データ ソース アドミニストレーター ダイアログ ボックスの トレース タブでこれらのオプションを設定**SQLManageDataSources**です。 ODBC サブキー自体はオプションです。 これらの値の形式は、次の表に示すようにします。  
  
|[オブジェクト名]|データ型|data|  
|----------|---------------|----------|  
|Trace|REG_SZ|**0** &#124; **1**|  
|TraceFile|REG_SZ|*tracefile パス*|  
  
 値には、次の表には意味があります。  
  
|値|意味|  
|-----------|-------------|  
|Trace|トレースの値が設定されている場合すると 1 に、アプリケーションが呼び出す**SQLAllocHandle** sql_handle_env としてオプションを使用して、呼び出し元アプリケーションのトレースが有効です。<br /><br /> アプリケーションを呼び出すときに、トレースのキーワードが 0 に設定されてかどうか**SQLAllocHandle** sql_handle_env としてオプションを使用して、呼び出し元アプリケーションのトレースが無効です。 これが既定値です。<br /><br /> アプリケーションでは、有効にしたり、SQL_ATTR_TRACE 接続属性を持つトレースを無効にすることができます。 ただし、そのため変わりませんこの値のデータ。|  
|TraceFile|トレースが有効になっている場合、ドライバー マネージャーは、トレースファイル値で指定されたトレース ファイルに書き込みます。<br /><br /> トレース ファイルが指定されていない場合、ドライバー マネージャーは、現在のドライブに Sql.log ファイルに書き込みます。 これが既定値です。<br /><br /> 1 つのアプリケーションにのみトレースを使用する必要があります。 または各アプリケーションは、別のトレース ファイルを指定する必要があります。 それ以外の場合、2 つまたは複数のアプリケーションを開こうと同じトレース ファイル、同時にエラーが発生します。<br /><br /> アプリケーションは、SQL_ATTR_TRACEFILE 接続属性を持つ、新しいトレース ファイルを指定できます。 ただし、そのため変わりませんこの値のデータ。|  
  
 たとえば、トレースを有効にし、トレース ファイルは C:\Odbc.log ことです。 ODBC のサブキーの下の値に次のようになります。  
  
```  
Trace : REG_SZ : 1  
TraceFile : REG_SZ : C:\ODBC.LOG  
  
```
