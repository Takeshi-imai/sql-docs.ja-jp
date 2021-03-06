---
title: "C から SQL へ: GUID |Microsoft ドキュメント"
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
- converting data from c to SQL types [ODBC], guid
- data conversions from C to SQL types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: 9168b0b6-a828-4fef-b8cd-bdf439776f23
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9a393aefa101bef2738e15ed12b0f1679e4a6c9c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="c-to-sql-guid"></a>C から SQL へ: GUID
GUID の ODBC C データ型の識別子です。  
  
 SQL_C_GUID  
  
 次の表は、ODBC SQL データ型の GUID の C データを変換することがありますを示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを C から SQL データ型を](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)です。  
  
|SQL 型の識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR|列のバイト長 > 36 を =|n/a|  
|SQL_VARCHAR|列のバイトの長さ < 36|22001|  
|SQL_LONGVARCHAR|データ値が有効な GUID ではありません。|22018|  
|SQL_WCHAR|列の文字の長さ > 36 を =|n/a|  
|SQL_WVARCHAR|列の長さ < 36 文字します。|22001|  
|SQL_WLONGVARCHAR|データ値が有効な GUID ではありません。|22018|  
|SQL_GUID|[A] [なし]|n/a|  
  
 [a] のすべての 16 進値は、GUID として有効です。  
  
 ドライバーは、GUID の C データ型からデータを変換するときに長さ/インジケーター値を無視し、データ バッファーのサイズが GUID の C データ型のサイズであると見なされます。 長さ/インジケーター値に渡されます、 *StrLen_or_Ind*引数**SQLPutData**とで指定したバッファー内の*StrLen_or_IndPtr* で引数**SQLBindParameter**です。 データ バッファーを指定した、 *DataPtr*引数**SQLPutData**と*ParameterValuePtr*引数**SQLBindParameter**.
