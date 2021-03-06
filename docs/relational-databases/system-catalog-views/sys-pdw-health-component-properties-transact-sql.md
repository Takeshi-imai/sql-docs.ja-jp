---
title: "sys.pdw_health_component_properties (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66999c0c-dc43-4327-99fb-8366f465e69d
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 55d033f0e0001377cb0a7d5be6e4bbff35833c24
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwhealthcomponentproperties-transact-sql"></a>sys.pdw_health_component_properties (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  デバイスを記述するプロパティを格納します。 一部のプロパティは、デバイスの状態を表示し、いくつかのプロパティは、デバイス自体を説明します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|コンポーネントのプロパティの一意の識別子。<br /><br /> property_id と component_id は、このビューのキーを形成します。|NOT NULL|  
|component_id|**int**|コンポーネントの ID。 参照してください[sys.pdw_health_components &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)。<br /><br /> property_id と component_id は、このビューのキーを形成します。|NOT NULL|  
|property_name|**nvarchar (255)**|プロパティの名前です。|NOT NULL|  
|physical_name|**nvarchar(32)**|プロパティ名、製造元によって定義されています。|NOT NULL|  
|is_key|**bit**|デバイス インスタンスが一意か一意でないかどうかを判断します。|NOT NULL<br /><br /> 0 - デバイスのインスタンスは一意です。<br /><br /> 1 のデバイス インスタンスは一意ではありません。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
