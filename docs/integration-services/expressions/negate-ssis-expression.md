---
title: "- (負数化) (SSIS 式) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e2a59d861afa6a7c7b2bd321d431b52f9e63b0d8
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="--negate-ssis-expression"></a>- (負数化) (SSIS 式)
  数値式を負数化します。  
  
## <a name="syntax"></a>構文  
  
```  
  
-numeric_expression  
  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression*  
 任意の数値データ型の有効な式です。 サポートされるデータ型は、符号付き数値データ型のみです。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## <a name="result-types"></a>戻り値の型  
 データ型を返す *numeric_expression*です。  
  
## <a name="expression-examples"></a>式の例  
 この例では、変数 **Counter** の値を負数化して、数値リテラル 50 を加算します。  
  
```  
-@Counter + 50  
```  
  
## <a name="see-also"></a>参照  
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 (SSIS 式)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
