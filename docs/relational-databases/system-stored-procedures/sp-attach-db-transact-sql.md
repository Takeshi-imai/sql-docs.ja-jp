---
title: "sp_attach_db (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/01/2016
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
- sp_attach_db_TSQL
- sp_attach_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_attach_db
ms.assetid: 59bc993e-7913-4091-89cb-d2871cffda95
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b17a11f31faff52e2519d2c10d34af88108f0399
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="spattachdb-transact-sql"></a>sp_attach_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベースをサーバーにアタッチします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] CREATE DATABASE を使用することをお勧め*database_name* FOR ATTACH 代わりにします。 詳細については、「[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)」を参照してください。  
  
> [!NOTE]  
>  1 つまたは複数が別の場所は、複数のログ ファイルを再構築、CREATE DATABASE を使用して*database_name* FOR ATTACH_REBUILD_LOG です。  
  
> [!IMPORTANT]  
>  不明なソースや信頼されていないソースからデータベースをアタッチまたは復元しないことをお勧めします。 こうしたデータベースには、意図しない [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを実行したり、スキーマまたは物理データベース構造を変更してエラーを発生させるような、悪意のあるコードが含まれている可能性があります。 不明または信頼できないソースのデータベースを使用する前に、実稼働用ではないサーバーでそのデータベースに対し [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) を実行し、さらに、そのデータベースのストアド プロシージャやその他のユーザー定義コードなどのコードを調べます。  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_attach_db [ @dbname= ] 'dbname'  
    , [ @filename1= ] 'filename_n' [ ,...16 ]   
```  
  
## <a name="arguments"></a>引数  
 [ **@dbname=** ] **'***dbnam* **'**  
 サーバーにアタッチされるデータベースの名前を指定します。 名前は一意である必要があります。 *dbname*は**sysname**、既定値は NULL です。  
  
 [ **@filename1=** ] **'***filename_n***'**  
 データベース ファイルの物理名を、パスも含めて指定します。 *filename_n*は**nvarchar (260)**、既定値は NULL です。 ファイル名は 16 個まで指定できます。 最初のパラメーター名 **@filename1** に 1 ずつ増分 **@filename16**です。 指定するファイルには少なくともプライマリ ファイルが含まれている必要があります。 プライマリ ファイルには、データベース内の他のファイルを参照するシステム テーブルが含まれています。 また、データベースがデタッチされた後で移動したファイルも指定する必要があります。  
  
> [!NOTE]  
>  この引数は、CREATE DATABASE ステートメントの FILENAME パラメーターにマップされます。 詳細については、「[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)」を参照してください。  
>   
>  フルテキスト カタログ ファイルを含む [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] データベースを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] サーバー インスタンスにアタッチする場合、カタログ ファイルは [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]と同様に他のデータベース ファイルと一緒に以前の場所からアタッチされます。 詳細については、「 [フルテキスト検索のアップグレード](../../relational-databases/search/upgrade-full-text-search.md)」を参照してください。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **Sp_attach_db**ストアド プロシージャは、明示的に使用して、データベース サーバーからデタッチされたデータベースでのみ実行する必要があります**sp_detach_db**オペレーション データベース、またはコピーします。 16 を超えるファイルを指定した場合は、CREATE DATABASE を使用します。 *database_name* FOR ATTACH または CREATE DATABASE *database_name* for_attach_rebuild_log を使用します。 詳細については、「[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)」を参照してください。  
  
 指定されていないファイルは、最後に指定された場所にあることが想定されます。 異なる場所にあるファイルを使用するには、新しい場所を指定する必要があります。  
  
 新しいバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で作成したデータベースは、それ以前のバージョンでアタッチすることはできません。  
  
> [!NOTE]  
>  データベース スナップショットのデタッチおよびアタッチは行うことができません。  
  
 レプリケートされたデータベースをアタッチするとき、そのデータベースがデタッチではなくコピーされたものである場合は、次の点を考慮してください。  
  
-   元のデータベースと同じサーバー インスタンスおよびバージョンにデータベースをアタッチする場合は、必要な追加手順はありません。  
  
-   場合は、同じサーバー インスタンスにデータベースをアタッチする場合は、実行する必要があります、アップグレードされたバージョン[sp_vupgrade_replication](../../relational-databases/system-stored-procedures/sp-vupgrade-replication-transact-sql.md)アタッチ操作が完了した後にレプリケーションをアップグレードします。  
  
-   実行する必要があります、バージョンにかかわらず、別のサーバー インスタンスにデータベースをアタッチする場合[sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)アタッチ操作が完了した後にレプリケーションを削除します。  
  
 データベースが最初に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の新しいインスタンスにアタッチまたは復元されるとき、データベース マスター キー (サービス マスター キーにより暗号化されたもの) のコピーはまだサーバーに格納されていません。 **OPEN MASTER KEY** を使用して、データベース マスター キー (DMK) を暗号化解除する必要があります。 DMK の暗号化が解除されると、 **ALTER MASTER KEY REGENERATE** ステートメントを使用して、サービス マスター キー (SMK) で暗号化された DMK のコピーをサーバーに提供することにより、将来、自動的に暗号化解除することも可能となります。 データベースを以前のバージョンからアップグレードした場合、新しい AES アルゴリズムを使用するように DMK を再作成する必要があります。 DMK を再作成する方法については、「[ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md)」を参照してください。 DMK キーを再作成して AES にアップグレードするのに必要な時間は、DMK によって保護されているオブジェクトの数によって異なります。 DMK キーを再作成して AES にアップグレードする作業は、1 回限りで済み、今後のキー ローテーション方法には影響を与えません。  
  
## <a name="permissions"></a>権限  
 データベースをアタッチするときにアクセス許可を処理する方法については、次を参照してください。 [CREATE DATABASE &#40;です。SQL Server TRANSACT-SQL &#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
## <a name="examples"></a>使用例  
 次の例からのファイルをアタッチする[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]現在のサーバーにします。  
  
```  
EXEC sp_attach_db @dbname = N'AdventureWorks2012',   
    @filename1 =   
N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_Data.mdf',   
    @filename2 =   
N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_log.ldf';  
```  
  
## <a name="see-also"></a>参照  
 [データベースのデタッチとアタッチ &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_detach_db &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)   
 [sp_helpfile を実行 &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sp_removedbreplication &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
