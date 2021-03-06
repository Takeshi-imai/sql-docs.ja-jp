---
title: "sys.extended_properties (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.extended_properties
- sys.extended_properties_TSQL
- extended_properties
- extended_properties_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.extended_properties catalog view
ms.assetid: 439b7299-dce3-4d26-b1c7-61be5e0df82a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 931d52eb19e9dcd27cc8a256650e401928805679
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="extended-properties-catalog-views---sysextendedproperties"></a>拡張プロパティ カタログ ビューの sys.extended_properties
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  現在のデータベース内の拡張プロパティごとに 1 行のデータを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|class|**tinyint**|プロパティが属するアイテムのクラスを識別します。 次のいずれかになります。<br /><br /> 0 = データベース<br /><br /> 1 = オブジェクトまたは列<br /><br /> 2 = パラメーター<br /><br /> 3 = スキーマ<br /><br /> 4 = データベース プリンシパル<br /><br /> 5 = アセンブリ<br /><br /> 6 = 型<br /><br /> 7 = インデックス<br /><br /> 10 = XML スキーマ コレクション<br /><br /> 15 = メッセージの種類<br /><br /> 16 = サービス コントラクト<br /><br /> 17 = サービス<br /><br /> 18 = リモート サービス バインド<br /><br /> 19 = ルート<br /><br /> 20 = データ領域 (ファイル グループまたはパーティションのスキーマ)<br /><br /> 21 = パーティション関数<br /><br /> 22 = データベース ファイル<br /><br /> 27 = プラン ガイド|  
|class_desc|**nvarchar (60)**|拡張プロパティが属するクラスの説明です。 次のいずれかになります。<br /><br /> DATABASE<br /><br /> OBJECT_OR_COLUMN<br /><br /> PARAMETER<br /><br /> SCHEMA<br /><br /> DATABASE_PRINCIPAL<br /><br /> ASSEMBLY<br /><br /> TYPE<br /><br /> INDEX<br /><br /> XML_SCHEMA_COLLECTION<br /><br /> MESSAGE_TYPE<br /><br /> SERVICE_CONTRACT<br /><br /> SERVICE<br /><br /> REMOTE_SERVICE_BINDING<br /><br /> ROUTE<br /><br /> DATASPACE<br /><br /> PARTITION_FUNCTION<br /><br /> DATABASE_FILE<br /><br /> PLAN_GUIDE|  
|major_id|**int**|拡張プロパティが属するアイテムの ID です。アイテムのクラスに従って解釈されます。 大部分のアイテムでは、この ID はクラス自体に適用される ID に等しくなります。 非標準的なメジャー ID の解釈は次のようになります。<br /><br /> class が 0 の場合、major_id は常に 0 になります。<br /><br /> class が 1、2、または 7 の場合、major_id は object_id になります。|  
|minor_id|**int**|拡張プロパティが属するアイテムのセカンダリ ID です。アイテムのクラスに従って解釈されます。 大部分のアイテムでは、この ID が 0 になります。0 以外の場合、ID は次のようになります。<br /><br /> class が 1 の場合、minor_id は、列であれば column_id に、オブジェクトであれば 0 になります。<br /><br /> class が 2 の場合、minor_id は parameter_id になります。<br /><br /> class が 7 の場合、minor_id は index_id になります。|  
|name|**sysname**|class、major_id、および minor_id で一意となるプロパティ名です。|  
|value|**sql_variant**|拡張プロパティの値です。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [拡張プロパティ カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/f39fd324-efd4-4468-884c-bf77ed1a026f)   
 [sys.fn_listextendedproperty &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-listextendedproperty-transact-sql.md)   
 [sp_addextendedproperty &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md)   
 [sp_dropextendedproperty &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dropextendedproperty-transact-sql.md)   
 [sp_updateextendedproperty &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-updateextendedproperty-transact-sql.md)  
  
  
