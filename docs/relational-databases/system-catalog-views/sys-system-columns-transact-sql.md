---
title: "sys.system_columns (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- system_columns_TSQL
- system_columns
- sys.system_columns
- sys.system_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_columns catalog view
ms.assetid: 4ab1d48a-d57a-4e76-a08c-9627eeaf4588
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f8a710e9575af43cbbe8bfdcaf7d66f09ca26d41
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syssystemcolumns-transact-sql"></a>sys.system_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  列を持つシステム オブジェクトの列ごとに 1 行のデータを保持します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|この列が属するオブジェクトの ID です。|  
|**name**|**sysname**|列の名前です。 オブジェクト内で一意です。|  
|**column_id**|**int**|列の ID です。 オブジェクト内で一意です。<br /><br /> 列 ID は連続した値にならないことがあります。|  
|**system_type_id**|**tinyint**|列のシステム型の ID です。|  
|**user_type_id**|**int**|ユーザーが定義した列の型の ID です。<br /><br /> 型の名前を返すに参加させる、 [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)カタログをこの列に表示します。|  
|**max_length**|**smallint**|列の最大長 (バイト数) です。<br /><br /> -1 = 列のデータ型は**varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、または**xml**です。<br /><br /> **テキスト**、列、 **max_length**値は 16 かによって設定された値になります**sp_tableoption** 'text in row' です。|  
|**有効桁数**|**tinyint**|数値ベースの場合は、列の有効桁数です。それ以外の場合は、0 です。|  
|**小数点以下桁数**|**tinyint**|数値ベースの場合は、列の小数点以下桁数です。それ以外の場合は、0 です。|  
|**collation_name**|**sysname**|文字ベースの場合は、列の照合順序の名前です。それ以外の場合は、NULL です。|  
|**によって is_nullable**|**bit**|1 = 列で NULL 値を使用できます。|  
|**is_ansi_padded**|**bit**|1 = 文字、バイナリ、またはバリアントの場合、列で ANSI_PADDING ON 動作を使用します。<br /><br /> 0 = 列は文字、バイナリ、またはバリアントではありません。|  
|**is_rowguidcol**|**bit**|1 = 列は宣言された ROWGUIDCOL です。|  
|**is_identity**|**bit**|1 = 列は ID 値を保持しています。|  
|**is_computed**|**bit**|1 = 列は計算列です。|  
|**is_filestream**|**bit**|1 = 列はファイル ストリーム ストレージを使用するよう宣言されています。|  
|**is_replicated**|**bit**|1 = 列はレプリケートされています。|  
|**is_non_sql_subscribed**|**bit**|1 = 列にはない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。|  
|**is_merge_published**|**bit**|1 = 列はマージ パブリッシュされています。|  
|**is_dts_replicated**|**bit**|1 = を使用して列をレプリケート[!INCLUDE[ssIS](../../includes/ssis-md.md)]です。|  
|**is_xml_document**|**bit**|1 = 内容が完全な XML ドキュメントです。<br /><br /> 0 = コンテンツは、ドキュメント フラグメント、または列のデータ型が無効**xml**です。|  
|**xml_collection_id**|**int**|列のデータ型が場合は 0 以外**xml** XML が型指定されたとします。 この値は、列の検証 XML スキーマ名前空間を含むコレクションの ID です。<br /><br /> 0 = いいえの XML スキーマ コレクションです。|  
|**default_object_id**|**int**|スタンドアロンかどうかに関係なく、既定のオブジェクトの ID [sys.sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)、または、インラインの列レベルの既定の制約。 **Parent_object_id**インラインの列レベルの既定のオブジェクトの列は、テーブル自体への参照。 既定値がない場合は 0 です。|  
|**rule_object_id**|**int**|使用して、列にバインドするスタンドアロン ルールの ID **sys.sp_bindrule**です。<br /><br /> 0 = スタンドアロン ルールはありません。<br /><br /> 列レベルの CHECK 制約を参照してください。 [sys.check_constraints &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md).|  
|is_sparse|**bit**|1 = 列はスパース列です。 詳細については、「 [スパース列の使用](../../relational-databases/tables/use-sparse-columns.md)」を参照してください。|  
|is_column_set|**bit**|1 = 列は列セットです。 詳細については、「 [列セットの使用](../../relational-databases/tables/use-column-sets.md)」を参照してください。|  
|generated_always_type|**tinyint**|列の型を表す数値。<br /><br /> 0 = NOT_APPLICABLE<br /><br /> 1 = AS_ROW_START<br /><br /> 2 = AS_ROW_END|  
|generated_always_type_desc|**nvarchar (60)**|列の型のテキストの説明:<br /><br /> NOT_APPLICABLE<br /><br /> AS_ROW_START<br /><br /> AS_ROW_END<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server のシステム カタログよく寄せられる質問のクエリを実行します。](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)  
  
  
