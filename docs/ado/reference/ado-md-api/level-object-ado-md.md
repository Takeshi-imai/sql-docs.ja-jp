---
title: "レベルのオブジェクト (ADO MD) |Microsoft ドキュメント"
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
f1_keywords:
- Level
helpviewer_keywords:
- Level object [ADO MD]
ms.assetid: 37815869-ed30-45fd-9aea-0a986c1b305c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f690e2efc97b4da9ea588e5028055fb758b93a48
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="level-object-ado-md"></a>レベル オブジェクト (ADO MD)
それぞれが、階層内で同じランクを持つメンバーのセットが含まれています。  
  
## <a name="remarks"></a>解説  
 コレクションのプロパティと、**レベル**オブジェクトを次を行うことができます。  
  
-   識別、**レベル**で、[名前](../../../ado/reference/ado-md-api/name-property-ado-md.md)と[UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)プロパティです。  
  
-   表示するときに使用する文字列を返す、**レベル**で、[キャプション](../../../ado/reference/ado-md-api/caption-property-ado-md.md)プロパティです。  
  
-   説明するわかりやすい文字列を返す、**レベル**で、[説明](../../../ado/reference/ado-md-api/description-property-ado-md.md)プロパティです。  
  
-   返す、[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)を構成するオブジェクト、**レベル**で、[メンバー](../../../ado/reference/ado-md-api/members-collection-ado-md.md)コレクション。  
  
-   ルートからレベルの数を返す、**レベル**で、[深さ](../../../ado/reference/ado-md-api/depth-property-ado-md.md)プロパティです。  
  
-   標準の ADO を使用して[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)に関する追加情報を取得するコレクション、**レベル**オブジェクト。  
  
 **プロパティ**コレクションには、プロバイダーが指定したプロパティが含まれています。 次の表は、利用可能なプロパティを一覧表示します。 実際のプロパティの一覧は、プロバイダーの実装によって異なる場合があります。 使用可能なプロパティの完全な一覧については、プロバイダーのドキュメントを参照してください。  
  
|名前|Description|  
|----------|-----------------|  
|CatalogName|このキューブに所属するカタログの名前。|  
|CubeName|キューブの名前。|  
|Description|レベルのわかりやすい説明。|  
|DimensionUniqueName|明確な名前、[ディメンション](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)です。|  
|HierarchyUniqueName|階層の明確な名前。|  
|LevelCaption|ラベルまたはキャプション、レベルに関連付けられています。|  
|LevelCardinality|レベル内のメンバーの数。|  
|LevelGUID|レベルの GUID です。|  
|LevelName|レベルの名前です。|  
|LevelNumber|レベルと階層のルートの距離。|  
|LevelType|レベルの型。|  
|LevelUniqueName|レベルの明確な名前。|  
|SchemaName|このキューブが属しているスキーマの名前。|  
  
 このセクションには、次のトピックが含まれています。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/level-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [CubeDef 例 (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Hierarchy オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)   
 [Levels コレクション (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [メンバーのコレクション (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
