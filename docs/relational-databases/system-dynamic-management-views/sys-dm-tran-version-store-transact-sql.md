---
title: "sys.dm_tran_version_store (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_version_store_TSQL
- sys.dm_tran_version_store
- dm_tran_version_store
- dm_tran_version_store_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_version_store dynamic management view
ms.assetid: 7ab44517-0351-4f91-bdd9-7cf940f03c51
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: be8779d40624e9f88ee74ea85a1126c1b4b76ebf
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmtranversionstore-transact-sql"></a>sys.dm_tran_version_store (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  バージョン ストア内のすべてのバージョン レコードを表示する仮想テーブルを返します。 **sys.dm_tran_version_store**バージョン ストア全体のクエリを実行し、バージョン ストアが非常に大きくなることができますので、効率的ではありません。  
  
 各バージョン レコードは、追跡情報または状態情報と共にバイナリ データとして格納されます。 データベース テーブル内のレコードと同様、バージョン ストア レコードは 8,192 バイトのページに格納されます。 レコードが 8,192 バイトを超える場合は、2 つのレコードに分割されます。  
  
 バージョン レコードはバイナリとして格納されるので、複数のデータベースの照合順序が異なっていても問題にはなりません。 使用して**sys.dm_tran_version_store**バージョン ストアに存在している、バイナリ表記で、行の以前のバージョンが見つかりません。  
  
  
## <a name="syntax"></a>構文  
  
```  
sys.dm_tran_version_store  
```  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**transaction_sequence_num**|**bigint**|レコード バージョンを生成するトランザクションのシーケンス番号。|  
|**version_sequence_num**|**bigint**|バージョン レコードのシーケンス番号。 この値はバージョンを生成するトランザクション内で一意です。|  
|**database_id**|**int**|バージョン レコードのデータベース ID。|  
|**rowset_id**|**bigint**|レコードの行セット ID。|  
|**ステータス**|**tinyint**|バージョン レコードが 2 つのレコードに分割されているかどうかを示します。 値が 0 の場合、レコードは 1 ページに格納されています。 値が 1 の場合、レコードは 2 つのレコードに分割され、2 つの異なるページに格納されています。|  
|**min_length_in_bytes**|**smallint**|レコードの最小長 (バイト単位)。|  
|**record_length_first_part_in_bytes**|**smallint**|バージョン レコードの最初の部分の長さ (バイト単位)。|  
|**record_image_first_part**|**varbinary(8000)**|バージョン レコードの最初の部分のバイナリ イメージ。|  
|**record_length_second_part_in_bytes**|**smallint**|バージョン レコードの 2 番目の部分の長さ (バイト単位)。|  
|**record_image_second_part**|**varbinary(8000)**|バージョン レコードの 2 番目の部分のバイナリ イメージ。|  
  
## <a name="permissions"></a>権限  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium 階層が必要です、`VIEW DATABASE STATE`データベースの権限です。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。  
 

  
## <a name="examples"></a>使用例  
 次の例では、4 つの同時実行トランザクションが存在するテスト シナリオを使用します。これらのトランザクションはそれぞれトランザクション シーケンス番号 (XSN) で識別され、ALLOW_SNAPSHOT_ISOLATION オプションと READ_COMMITTED_SNAPSHOT オプションが ON に設定されているデータベース内で実行されます。 実行されるトランザクションは次のとおりです。  
  
-   XSN-57。SERIALIZABLE 分離での更新操作です。  
  
-   XSN-58 では、xsn-57 と同じです。  
  
-   XSN-59。スナップショット分離での選択操作です。  
  
-   Xsn-60 では、xsn-59 と同じです。  
  
 次のクエリを実行します。  
  
```  
SELECT  
    transaction_sequence_num,  
    version_sequence_num,  
    database_id rowset_id,  
    status,  
    min_length_in_bytes,  
    record_length_first_part_in_bytes,  
    record_image_first_part,  
    record_length_second_part_in_bytes,  
    record_image_second_part  
  FROM sys.dm_tran_version_store;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
transaction_sequence_num version_sequence_num database_id  
------------------------ -------------------- -----------  
57                      1                    9             
57                      2                    9             
57                      3                    9             
58                      1                    9             
  
rowset_id            status min_length_in_bytes  
-------------------- ------ -------------------  
72057594038321152    0      12                   
72057594038321152    0      12                   
72057594038321152    0      12                   
72057594038386688    0      16                   
  
record_length_first_part_in_bytes  
---------------------------------  
29                                 
29                                 
29                                 
33                                 
  
record_image_first_part                                               
--------------------------------------------------------------------  
0x50000C0073000000010000000200FCB000000001000000270000000000          
0x50000C0073000000020000000200FCB000000001000100270000000000          
0x50000C0073000000030000000200FCB000000001000200270000000000          
0x500010000100000002000000030000000300F800000000000000002E0000000000  
  
record_length_second_part_in_bytes record_image_second_part  
---------------------------------- ------------------------  
0                                  NULL  
0                                  NULL  
0                                  NULL  
0                                  NULL  
```  
  
 この出力は、XSN-57 で 1 つのテーブルから 3 つの行バージョンが作成され、XSN-58 で他のテーブルから 1 つの行バージョンが作成されたことを示しています。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [トランザクション関連の動的管理ビューおよび関数  &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
