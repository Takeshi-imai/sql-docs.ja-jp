---
title: "Name プロパティ (ADOX) |Microsoft ドキュメント"
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
- _Table::PutName
- _Table::GetName
- _Key::Name
- _Key::get_Name
- _Column::GetName
- _Index::Name
- _Index::put_Name
- _Column::PutName
- _Key::put_Name
- _Table::put_Name
- _User25::PutName
- _Index::get_Name
- _Column::get_Name
- _Group25::Name
- _Group25::get_Name
- _Column::Name
- _User25::get_Name
- _Table::Name
- _Group25::GetName
- _Index::PutName
- _Column::put_Name
- _Key::GetName
- _Table::get_Name
- _User25::Name
- _User25::put_Name
- _Index::GetName
- _User25::GetName
helpviewer_keywords:
- Name property [ADOX]
ms.assetid: 81b92baf-b6b9-4f4e-9f33-4503795518cd
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 10e899d43bd2990bff5724d87b4deefffd559090
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="name-property-adox"></a>Name プロパティ (ADOX)
オブジェクトの名前を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**文字列**値。  
  
## <a name="remarks"></a>解説  
 名前をコレクション内で一意である必要はありません。  
  
 **名前**プロパティが読み取り/書き込み[列](../../../ado/reference/adox-api/column-object-adox.md)、[グループ](../../../ado/reference/adox-api/group-object-adox.md)、[キー](../../../ado/reference/adox-api/key-object-adox.md)、[インデックス](../../../ado/reference/adox-api/index-object-adox.md)、 [テーブル](../../../ado/reference/adox-api/table-object-adox.md)、および[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)オブジェクト。 **名前**プロパティは読み取り専用で[カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)、[プロシージャ](../../../ado/reference/adox-api/procedure-object-adox.md)、および[ビュー](../../../ado/reference/adox-api/view-object-adox.md)オブジェクト。  
  
 オブジェクトの読み取り/書き込み (**列**、**グループ**、**キー**、**インデックス**、**テーブル**と**ユーザー**オブジェクト)、既定値は空の文字列 ("") です。  
  
> [!NOTE]
>  キー、このプロパティは読み取り専用で**キー**オブジェクトをコレクションに既に追加されています。 テーブル、このプロパティは読み取り専用です**テーブル**オブジェクトをコレクションに既に追加されています。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Column オブジェクト (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)|[Group オブジェクト (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Index オブジェクト (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)|  
|[Key オブジェクト (ADOX)](../../../ado/reference/adox-api/key-object-adox.md)|[Procedure オブジェクト (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Property オブジェクト (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
|[Table オブジェクト (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[User オブジェクト (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|[View オブジェクト (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>参照  
 [列とテーブル名プロパティの例 (VB) のメソッドを追加します。](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [キーは、メソッド、キーの種類、RelatedColumn、RelatedTable および UpdateRule プロパティの例 (VB を) 追加します。](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog プロパティの例 (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
