---
title: "sysarticlecolumns (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticlecolumns system table
ms.assetid: 55918592-e05d-43b6-843b-7e4d82fa6275
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2b4872dce57b1f7f33a1fc03af3aae31562ceab2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysarticlecolumns-transact-sql"></a>sysarticlecolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sysarticlecolumns**テーブルに 1 行がスナップショット パブリケーションまたはトランザクション パブリケーションでパブリッシュされ、各列をアーティクルにマップするテーブルの各列のデータが含まれています。 このテーブルは、パブリケーション データベース内に保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|アーティクルの識別子です。|  
|**返された colid**|**smallint**|アーティクル内の列の識別子。|  
|**is_udt**|**bit**|列がユーザー定義データ型 (UDT) 列であるかどうかを示します。 値**1** UDT 列を示します。|  
|**is_xml**|**bit**|列があるかどうかを示す、 **xml**列です。 値**1** xml 列を示します。|  
|**is_max**|**bit**|列が大きな値データ型の列であるかどうかを示します**varchar (max)**、 **nvarchar (max)**、および**varbinary (max)**です。 値**1**大きな値の列を示します。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
