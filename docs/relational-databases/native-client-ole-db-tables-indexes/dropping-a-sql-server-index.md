---
title: "SQL Server インデックスの削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-tables-indexes
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: add3ba14-10b1-4723-b7c0-3e83689e9fdd
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9398c26930243753e17727925c9bcf614176163b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="dropping-a-sql-server-index"></a>SQL Server インデックスの削除
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを公開、 **iindexdefinition::dropindex**関数。 これにより、コンシューマーからのインデックスを削除する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが公開一部[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インデックスと PRIMARY KEY 制約と UNIQUE 制約。 テーブルの所有者、データベース所有者、および管理者の役割の一部のメンバーを変更できる、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル、制約を削除します。 既定では、テーブル所有者だけが既存のインデックスを削除できます。 したがって、 **DropIndex**成功または失敗が示されているインデックスの種類にもアプリケーション ユーザーのアクセス権だけでなく依存します。  
  
 コンシューマーでは、テーブル名を指定の Unicode 文字の文字列として、 *pwszName*のメンバー、 *uName*共用体の*pTableID*パラメーター。 *EKind*のメンバー *pTableID* dbkind_name にする必要があります。  
  
 コンシューマーは、Unicode 文字の文字列としてインデックスの名前を指定、 *pwszName*のメンバー、 *uName*共用体の*pIndexID*パラメーター。 *EKind*のメンバー *pIndexID* dbkind_name にする必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、OLE DB の機能のすべてのインデックス、テーブルの削除をサポートしていませんとき*pIndexID*が null です。 場合*pIndexID*が null である E_INVALIDARG が返されます。  
  
## <a name="see-also"></a>参照  
 [テーブルとパーティション インデックス](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md)  
  
  
