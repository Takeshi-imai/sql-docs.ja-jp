---
title: "MDSCHEMA_MEASUREGROUP_DIMENSIONS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MDSCHEMA_MEASUREGROUP_DIMENSIONS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_MEASUREGROUP_DIMENSIONS rowset
ms.assetid: c731c06a-7382-4e50-ba0e-d8cee3ab4f28
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 62ee9e17d9f53d981e5e44918ec690c9abceddbb
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemameasuregroupdimensions-rowset"></a>MDSCHEMA_MEASUREGROUP_DIMENSIONS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]メジャー グループのディメンションを列挙します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **MDSCHEMA_MEASUREGROUP_DIMENSIONS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||このメジャー グループが所属するカタログの名前。 **NULL**プロバイダーがカタログをサポートしていない場合。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||サポートされていません。|  
|**CUBE_NAME**|**DBTYPE_WSTR**||このメジャー グループが所属するキューブの名前。|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**||メジャー グループの名前。|  
|**MEASUREGROUP_CARDINALITY**|**DBTYPE_WSTR**||メジャー グループ内のメジャーが 1 つのディメンション メンバーに対して持つことができるインスタンスの数。 有効な値は次のとおりです。<br /><br /> **1 つ**<br /><br /> **多く**|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**||ディメンションの一意の名前。|  
|**DIMENSION_CARDINALITY**|**DBTYPE_WSTR**||ディメンション メンバーがメジャー グループの 1 つのメジャー インスタンスに対して持つことができるインスタンスの数。 有効な値は次のとおりです。<br /><br /> **1 つ**<br /><br /> **多く**|  
|**DIMENSION_IS_VISIBLE**|**DBTYPE_BOOL**||ディメンションの階層が表示されるかどうかを示すブール値。<br /><br /> 返します**TRUE**ディメンション内の 1 つまたは複数の階層が表示されている、それ以外の場合は**FALSE**です。|  
|**DIMENSION_IS_FACT_DIMENSION**|**DBTYPE_BOOL**||ディメンションがファクト ディメンションであるかどうかを示すブール値。<br /><br /> 返します**TRUE**ディメンションはファクト ディメンションである場合は、それ以外の場合、 **FALSE**です。|  
|**DIMENSION_PATH**|**DBTYPE_HCHAPTER**||参照ディメンションのディメンションの一覧。|  
|**DIMENSION_GRANULARITY**|**DBTYPE_WSTR**||粒度階層の一意の名前。|  
  
 行セットでの並べ替えをサポートしている**CATALOG_NAME**、 **SCHEMA_NAME**、 **CUBE_NAME**、 **MEASUREGROUP_NAME**、 **DIMENSION_UNIQUE_NAME**です。  
  
## <a name="restriction-columns"></a>制限の列  
 **MDSCHEMA_MEASUREGROUP_DIMENSIONS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|省略可。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|省略可。|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**DIMENSION_VISIBILITY**|**DBTYPE_UI2**|(省略可) 次のいずれかの有効値を含むビットマップ。<br /><br /> 1 表示<br /><br /> 2 not 表示<br /><br /> 既定の制限の値は 1 です。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
