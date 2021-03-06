---
title: "NULL および不明 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 9d491846-4730-4740-a680-77c69fae4a58
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c26004fdfa5f2607235ffe7dddb7826a77f38b31
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="null-and-unknown-transact-sql"></a>NULL および不明 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  NULL では、値が不明であることを示します。 Null 値では、空または 0 の値と異なるです。 2 つの NULL 値は等しいとは限りません。 各 NULL の値が不明であるために、2 つの null 値または null 値とその他の値の間の比較は不明な返します。  
  
 Null 値は、通常、不明な適用できないデータを示すか、後で追加します。 たとえば、受注時には顧客のミドル名イニシャルはわかりません。  
  
 Null 値については、次に注意してください。  
  
-   クエリ内で NULL 値を調べるには、WHERE 句で IS NULL または IS NOT NULL を使用します。  
  
-   INSERT または UPDATE ステートメントで NULL を明示的に記述、または INSERT ステートメントからの列にすることで、null 値を列に挿入できます。  
  
-   Null 値は、主キーなど、またはディストリビューション キーなどの行の配信に使用される情報のテーブル内の別の行から、テーブル内の 1 つの行を区別するために必要な情報として使用できません。  
  
 データに NULL 値がある場合、論理演算子と比較演算子は、TRUE や FALSE ではなく UNKNOWN を返すことがあります。 このように 3 つの値を生成する論理は、アプリケーション エラーの原因になります。 論理演算子を未知の要素を含むブール式では、演算子の結果が不明な式に依存しない限り、UNKNOWN を返します。 これらのテーブルは、この動作の例を示します。  
  
 次の表は、1 つの式に UNKNOWN が返されます次の 2 つのブール式を AND 演算子を適用した結果を示します。  
  
|1 の式|Expression 2|結果|  
|---------------|---------------|------------|  
|TRUE|UNKNOWN|UNKNOWN|  
|UNKNOWN|UNKNOWN|UNKNOWN|  
|FALSE|UNKNOWN|FALSE|  
  
 次の表は、1 つの式に UNKNOWN が返されます次の 2 つのブール式に OR 演算子を適用した結果を示します。  
  
|1 の式|Expression 2|結果|  
|---------------|---------------|------------|  
|TRUE|UNKNOWN|TRUE|  
|UNKNOWN|UNKNOWN|UNKNOWN|  
|FALSE|UNKNOWN|UNKNOWN|  
  
## <a name="see-also"></a>参照  
 [および &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/and-transact-sql.md)   
 [または &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/or-transact-sql.md)   
 [いない &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/not-transact-sql.md)   
 [NULL と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/is-null-transact-sql.md)  
  
  
