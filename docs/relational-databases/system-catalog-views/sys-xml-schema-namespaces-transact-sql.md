---
title: "あります (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_namespaces_TSQL
- sys.xml_schema_namespaces
- xml_schema_namespaces
- xml_schema_namespaces_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_namespaces catalog view
ms.assetid: 3ed42dd6-929a-41de-80e8-d3a0a488bc7a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1bb313a162da69a9f624f120c1c5e53916771f1b
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysxmlschemanamespaces-transact-sql"></a>sys.xml_schema_namespaces (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  XSD 定義の XML 名前空間ごとに 1 行のデータを返します。 次の組は一意: **collection_id**、 **namespace_id**、および**collection_id**、および**名前**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**xml_collection_id**|**int**|名前空間を含む XML スキーマ コレクションの ID。|  
|**name**|**nvarchar (4000)**|XML 名前空間の名前。 空白**名前**ターゲットの名前空間がないことを示します。|  
|**xml_namespace_id**|**int**|データベースの XML 名前空間を一意に識別する、1 から始まる序数。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML スキーマと #40 です。XML 型システム &#41;カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
