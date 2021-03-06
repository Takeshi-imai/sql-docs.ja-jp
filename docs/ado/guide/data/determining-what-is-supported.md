---
title: "サポートされている機能を決定する |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editing data [ADO], Supports method
- Supports method [ADO]
ms.assetid: 65090cba-6d46-4775-8d61-f6838e7752a6
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 31d9ca56af28416f68555511a3d4a8439d370200
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="determining-what-is-supported"></a>サポートされている機能を決定します。
**をサポートしている**メソッドを使用して、指定したかどうかを判断**Recordset**オブジェクトは、特定の種類の機能をサポートしています。 次の構文があります。  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="remarks"></a>解説  
 **サポート**メソッドすべて CursorOptions 引数によって示されている機能のプロバイダーがサポートするかどうかを示すブール値を返します。 使用することができます、**をサポートしている**機能の種類を特定する方法、 **Recordset**サポートしています。 場合、 **Recordset**オブジェクトを定数に対応するが、機能をサポートしている*CursorOptions*、**をサポートしている**メソッドを返します**をTrue**。 返しますそれ以外の場合、 **False**です。  
  
 使用して、**サポート**メソッドの機能を確認することができます、 **Recordset**新しいレコードを追加、ブックマークを使用して、使用するオブジェクト、**検索**方法、スクロールを使用して、を使用します。**インデックス**プロパティ、およびバッチ更新を実行します。 定数とその意味の一覧については、次を参照してください。 [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)です。  
  
 **サポート**メソッドが返す可能性があります**True**の特定の機能とは限りませんプロバイダーは、実行できること、機能のすべての状況で使用可能な。 **サポート**メソッドは単に特定の条件が満たされたと仮定した場合で、指定された機能をプロバイダーがサポートできるかどうかを返します。 たとえば、**をサポートしている**メソッド可能性があります、**レコード セット**オブジェクトは、カーソルは、複数のテーブル結合に基づいている場合でも、更新をサポートしている — 一部の列は更新不可能なです。
