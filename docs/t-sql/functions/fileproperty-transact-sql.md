---
title: FILEPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILEPROPERTY_TSQL
- FILEPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- viewing file properties
- names [SQL Server], files
- displaying file properties
- file properties [SQL Server]
- FILEPROPERTY function
- file names [SQL Server], FILEPROPERTY
ms.assetid: b82244ed-d623-431f-aa06-8017349d847f
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ce71f17549cb286ed95004c62901337ce39c6739
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="fileproperty-transact-sql"></a>FILEPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベース内のファイル名とプロパティ名が指定されたときに、指定されたファイル名のプロパティ値を返します。 現在のデータベース内にないファイルの場合は NULL を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
FILEPROPERTY ( file_name , property )  
```  
  
## <a name="arguments"></a>引数  
 *file_name*  
 プロパティ情報を返す基になる、現在のデータベースに関連付けられたファイルの名前を含む式を指定します。 file_name *は nchar (128)*です。  
  
 *property*  
 返されるファイル プロパティの名前を含む式を指定します。 プロパティ *は varchar (128)*, 、値は次のいずれかを指定することができます。  
  
|ReplTest1|Description|返される値|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|ファイル グループが読み取り専用であるかどうかを示します。|1 = True<br /><br /> 0 = False<br /><br /> NULL = 無効な入力|  
|**IsPrimaryFile**|ファイルがプライマリ ファイルであるかどうかを示します。|1 = True<br /><br /> 0 = False<br /><br /> NULL = 無効な入力|  
|**IsLogFile**|ファイルがログ ファイルであるかどうかを示します。|1 = True<br /><br /> 0 = False<br /><br /> NULL = 無効な入力|  
|**SpaceUsed**|指定したファイルで使用されている容量。|ファイルに割り当てられているページ数|  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>Remarks  
 file_name *に対応する、 名前* 内の列、 sys.master_files **または sys.database_files** カタログ ビューです。  
  
## <a name="examples"></a>使用例  
 次の例では、`IsPrimaryFile` データベース内のファイル名 `AdventureWorks_Data` の [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] プロパティに対する設定を返します。  
  
```  
  
SELECT FILEPROPERTY('AdventureWorks2012_Data', 'IsPrimaryFile')AS [Primary File];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Primary File   
-------------  
1  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [FILEGROUPPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/filegroupproperty-transact-sql.md)   
 [メタデータ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
