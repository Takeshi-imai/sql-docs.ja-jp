---
title: "SQL には、c: 日付 |Microsoft ドキュメント"
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
- converting data from SQL to C types [ODBC], date
- date data type [ODBC]
- data conversions from SQL to C types [ODBC], date
ms.assetid: 703c7960-9cf4-4d7a-9920-53b29c184f97
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 87a62501d4d03073d8c43b2f791ceffeec9b0b30
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sql-to-c-date"></a>SQL には、c: 日付
ODBC SQL データ型が日付の識別子。  
  
 SQL_TYPE_DATE  
  
 次の表は、ODBC C データ型の SQL データの日付を変換することがありますを示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを SQL から C データ型に](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)です。  
  
|C 型識別子|テスト|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > バイトの長さを文字<br /><br /> 11 < = *BufferLength* < 文字バイトの長さを =<br /><br /> *BufferLength* < 11|data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|10<br /><br /> バイト単位でデータの長さ<br /><br /> 未定義。|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > 文字長<br /><br /> 11 < = *BufferLength* < 文字の長さを =<br /><br /> *BufferLength* < 11|data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|10<br /><br /> データの文字の長さ<br /><br /> 未定義。|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|データのバイト長 < = *BufferLength*<br /><br /> データのバイト長 > *BufferLength*|data<br /><br /> 未定義。|バイト単位でデータの長さ<br /><br /> 未定義。|n/a<br /><br /> 22003|  
|SQL_C_TYPE_DATE|[A] [なし]|data|6 [c]|n/a|  
|SQL_C_TYPE_TIMESTAMP|[A] [なし]|データ [b]|16 [c]|n/a|  
  
 [a] の値*BufferLength*この変換では無視されます。 ドライバーでのサイズ **TargetValuePtr* C データ型のサイズです。  
  
 [b] の時刻のタイムスタンプの構造体のフィールドは、0 に設定されます。  
  
 [c] これは、対応する C データ型のサイズです。  
  
 SQL データの日付が文字データに変換されると、結果の文字列は、"*yyyy*-*mm*-*dd*"の形式です。 この形式は Windows® 国設定の影響を受けません。
