---
title: "SET NULL コマンド |Microsoft ドキュメント"
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
helpviewer_keywords: set nullSET NULL
ms.assetid: 410c5a6e-e957-4ecc-9e2d-e591cbc0bc4f
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1050db2b6a50fc794626b6017bd26af05f458a8a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="set-null-command"></a>SET NULL コマンド
決定方法 - SQL、CREATE TABLE、ALTER TABLE SQL、および INSERT - で null 値がサポートされている SQL コマンド。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET NULL ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 (ドライバーの既定値以外の場合は Visual FoxPro の既定値は OFF です。)ALTER TABLE と CREATE TABLE で作成されたテーブルのすべての列で null 値を使用できることを指定します。 列の定義に NOT NULL 句を含めることで、テーブルの列に null 値のサポートをオーバーライドできます。  
  
 INSERT - SQL は null 値を挿入 INSERT - SQL VALUE 句に含まれていない任意の列にも指定します。 INSERT のときに SQL によって null 値が null 値が許容される列にのみ挿入されます。  
  
 OFF  
 ALTER TABLE と CREATE TABLE で作成されたテーブルのすべての列が null 値にできないことを指定します。 列の定義に NULL 句を含めることで、ALTER TABLE と CREATE TABLE 内の列に対して null 値のサポートを指定できます。  
  
 INSERT - SQL は空白に値を挿入 INSERT - SQL VALUE 句に含まれていない列も指定します。  
  
## <a name="remarks"></a>解説  
 NULL に設定の影響のみどの null 値は、ALTER TABLE、CREATE TABLE、および INSERT - SQL によってサポートされます。 その他のコマンドは、SET NULL による影響を受けません。  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE の SQL コマンド](../../odbc/microsoft/alter-table-sql-command.md)   
 [テーブルの SQL コマンドを作成します。](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT - SQL コマンド](../../odbc/microsoft/insert-sql-command.md)
