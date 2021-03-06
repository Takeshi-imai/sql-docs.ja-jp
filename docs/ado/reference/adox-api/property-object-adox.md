---
title: "プロパティのオブジェクト (ADOX) |Microsoft ドキュメント"
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
apitype: COM
helpviewer_keywords:
- Property object [ADOX]
ms.assetid: 6a56def6-dbe6-4ccc-a491-8d076889f019
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c9d13366eb3554738fbd50da2ed09db8bceb6f5d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="property-object-adox"></a>プロパティのオブジェクト (ADOX)
ADOX オブジェクトの特性を表します。  
  
## <a name="remarks"></a>解説  
 ADOX オブジェクトが 2 種類のプロパティを設定します。 組み込みと動的です。  
  
 組み込みのプロパティは、MyObject.Property 構文を使用して、すべての新しいオブジェクトにすぐに利用可能なこれらのプロパティです。 オブジェクトのプロパティ オブジェクトとしては表示されません[Properties コレクション](../../../ado/reference/ado-api/properties-collection-ado.md)ので、その値を変更できますが、その特性を変更することはできません。  
  
 動的プロパティは、基になるデータ プロバイダーによって定義され、適切な ADOX オブジェクトのプロパティのコレクションに表示されます。  動的なプロパティは、MyObject.Properties(0) または MyObject.Properties("Name") 構文を使用して、コレクションからのみ参照できます。  
  
 プロパティのいずれかの種類を削除することはできません。  
  
 動的プロパティ オブジェクトには、独自の 4 つの組み込みプロパティがあります。  
  
 [名前](../../../ado/reference/ado-api/name-property-ado.md)プロパティは、プロパティを識別する文字列。  
  
 [型](../../../ado/reference/ado-api/type-property-ado.md)プロパティは、プロパティのデータ型を指定する整数。  
  
 [値](../../../ado/reference/ado-api/value-property-ado.md)プロパティは、プロパティの設定を含んでいるバリアント。 値は、プロパティ オブジェクトの既定のプロパティです。  
  
 [属性](../../../ado/reference/ado-api/attributes-property-ado.md)プロパティは、プロバイダーに固有のプロパティの特性を示す long 値です。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [ADOX Property オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/adox-property-object-properties-methods-and-events.md)
