---
title: "sp_server_info (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_server_info
- sp_server_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_server_info
ms.assetid: 2dc2c262-3cfa-4a84-8127-3632ba583543
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0261a011e7c331745494070efb5a3d38e37ffa23
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spserverinfo-transact-sql"></a>sp_server_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  属性の名前と一致する値の一覧を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、データベース ゲートウェイ、または基になるデータ ソース。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_server_info [[@attribute_id = ] 'attribute_id']  
```  
  
## <a name="arguments"></a>引数  
 [  **@attribute_id =** ] **'***attribute_id***'**  
 属性の整数 ID です。 *attribute_id*は**int**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**ATTRIBUTE_ID**|**int**|属性の ID 番号です。|  
|**ATTRIBUTE_NAME**|**varchar (**60**)**|属性名です。|  
|**ATTRIBUTE_VALUE**|**varchar (**255**)**|属性の現在の設定です。|  
  
 次の表に属性の一覧を示します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)]ODBC クライアント ライブラリは、現在の属性を使用して**1**、 **2**、 **18**、 **22**、および**500**で接続時間です。  
  
|ATTRIBUTE_ID|ATTRIBUTE_NAME の説明|ATTRIBUTE_VALUE|  
|-------------------|---------------------------------|----------------------|  
|**1**|DBMS_NAME|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**2**|DBMS_VER|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] - *x.xx.xxxx*|  
|"**10**"|OWNER_TERM|owner|  
|**11**|TABLE_TERM|テーブル|  
|**12**|MAX_OWNER_NAME_LENGTH|128|  
|**13**|TABLE_LENGTH<br /><br /> テーブル名の最大文字数です。|128|  
|**14**|MAX_QUAL_LENGTH<br /><br /> テーブル修飾子の名前 (3 つの要素から成る名前の最初の部分) の最大の長さです。|128|  
|**15**|COLUMN_LENGTH<br /><br /> 列名の最大文字数です。|128|  
|**16**|IDENTIFIER_CASE<br /><br /> データベース内のユーザー定義の名前 (テーブル名、列名、ストアド プロシージャ名) です。大文字か小文字かは、システム カタログ内でオブジェクトの名前に従います。|SENSITIVE|  
|**17**|TX_ISOLATION<br /><br /> SQL-92 に定義されている分離レベルに対応する、サーバーが仮定する初期トランザクション分離レベルです。|2|  
|**18**|COLLATION_SEQ<br /><br /> このサーバーの文字セットの順序です。|charset=iso_1 sort_order=dictionary_iso charset_num=1 sort_order_num=51|  
|**19**|SAVEPOINT_SUPPORT<br /><br /> 基になる DBMS が、名前付きセーブポイントをサポートするかどうかを示します。|Y|  
|**20**|MULTI_RESULT_SETS<br /><br /> 基になるデータベースまたはゲートウェイ自体が、複数の結果セットをサポートするかどうか (複数のステートメントをゲートウェイを使用して送り、複数の結果セットをクライアントに返すことができるかどうか) を示します。|Y|  
|**22**|ACCESSIBLE_TABLES<br /><br /> 指定でかどうか**sp_tables**、唯一のテーブル、ビュー、およびに、現在のユーザー (つまり、テーブルの少なくとも SELECT 権限を持っているユーザー) がアクセスできるゲートウェイが返されます。|Y|  
|"**100**"|USERID_LENGTH<br /><br /> ユーザー名の最大文字数を示します。|128|  
|**101**|QUALIFIER_TERM<br /><br /> DBMS ベンダーの用語で、テーブル修飾子 (3 つの要素から成る名前の最初の部分) を示します。|database|  
|**102**|NAMED_TRANSACTIONS<br /><br /> 基になる DBMS が、名前付きトランザクションをサポートするかどうかを示します。|Y|  
|**103**|SPROC_AS_LANGUAGE<br /><br /> ストアド プロシージャを言語イベントとして実行できるかどうかを示します。|Y|  
|**104**|ACCESSIBLE_SPROC<br /><br /> 指定では、ある**sp_stored_procedures**ゲートウェイが現在のユーザーが実行可能なストアド プロシージャのみを返します。|Y|  
|**105**|MAX_INDEX_COLS<br /><br /> DBMS のインデックス内の列の最大数を示します。|16|  
|**106**|RENAME_TABLE<br /><br /> テーブルの名前を変更できるかどうかを示します。|Y|  
|**107**|RENAME_COLUMN<br /><br /> 列の名前を変更できるかどうかを示します。|Y|  
|**108**|DROP_COLUMN<br /><br /> 列を削除できるかどうかを示します。|Y|  
|**109**|INCREASE_COLUMN_LENGTH<br /><br /> 列のサイズを大きくできるかどうかを示します。|Y|  
|**110**|DDL_IN_TRANSACTION<br /><br /> DDL ステートメントをトランザクションで使用できるかどうかを示します。|Y|  
|**111**|DESCENDING_INDEXES<br /><br /> 降順のインデックスがサポートされるかどうかを示します。|Y|  
|**112**|SP_RENAME<br /><br /> ストアド プロシージャの名前を変更できるかどうかを示します。|Y|  
|**113**|REMOTE_SPROC<br /><br /> ストアド プロシージャを DB-Library のリモート ストアド プロシージャ関数を使用して実行できるかどうかを示します。|Y|  
|**500**|SYS_SPROC_VERSION<br /><br /> 現在実装されているストアド プロシージャ カタログのバージョンを示します。|現在のバージョン番号です。|  
  
## <a name="remarks"></a>解説  
 **sp_server_info**によって提供される情報のサブセットを返します**SQLGetInfo** ODBC にします。  
  
## <a name="permissions"></a>Permissions  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [カタログのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
