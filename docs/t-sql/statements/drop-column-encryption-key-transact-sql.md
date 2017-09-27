---
title: "列暗号化キーの削除 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP COLUMN ENCRYPTION
- DROP COLUMN ENCRYPTION KEY
- DROP_COLUMN_ENCRYPTION_TSQL
- DROP_COLUMN_ENCRYPTION_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP COLUMN ENCRYPTION KEY statement
- column encryption key, drop
ms.assetid: 86415302-1383-4d36-9fc7-f780831a2d37
caps.latest.revision: 10
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 47208c011acad2d06fdf91cb3762474ca848e23e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-column-encryption-key-transact-sql"></a>暗号化キーの列 (TRANSACT-SQL) を削除します。
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  列の暗号化キーをデータベースから削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP COLUMN ENCRYPTION KEY key_name [;]  
```  
  
## <a name="arguments"></a>引数  
 *key_name*  
 列の暗号化は、データベースから削除するキーの名前です。  
  
## <a name="remarks"></a>解説  
 データベース内のすべての列の暗号化に使用されている場合は、列の暗号化キーを削除することはできません。 列の暗号化キーを使用してすべての列を削除することが最初にする必要があります。  
  
## <a name="permissions"></a>Permissions  
 必要があります**ALTER ANY COLUMN ENCRYPTION KEY**データベースに対する権限。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-dropping-a-column-encryption-key"></a>A. 列の暗号化キーを削除します。  
 次の例と呼ばれる列の暗号化キーを削除する`MyCEK`です。  
  
```  
DROP COLUMN ENCRYPTION KEY MyCEK;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [Always Encrypted &#40;データベース エンジン&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [ALTER COLUMN ENCRYPTION KEY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)   
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)  
  
  
