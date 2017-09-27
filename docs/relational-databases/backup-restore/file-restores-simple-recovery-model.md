---
title: "ファイルの復元 (単純復旧モデル) | Microsoft Docs"
ms.custom: 
ms.date: 03/24/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file restores [SQL Server]
- simple recovery model [SQL Server]
- restoring files [SQL Server], Transact-SQL restore sequence
- restoring files [SQL Server]
- Transact-SQL restore sequence
- restoring files [SQL Server], simple recovery model
- file restores [SQL Server], simple recovery model
- file restores [SQL Server], Transact-SQL restore sequence
ms.assetid: b6d07386-7c6f-4cc6-be32-93289adbd3d6
caps.latest.revision: 57
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5fdd6a65718ab54c60fcea09317146aa2342e517
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="file-restores-simple-recovery-model"></a>ファイルの復元 (単純復旧モデル)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  このトピックは、1 つ以上の読み取り専用セカンダリ ファイル グループが含まれている単純復旧モデルのデータベースのみに関連しています。  
  
 ファイル復元の目標は、データベース全体を復元することなく 1 つ以上の破損したファイルを復元することです。 単純復旧モデルでは、読み取り専用ファイルだけにファイル バックアップがサポートされます。 プライマリ ファイル グループと読み取り/書き込みセカンダリ ファイル グループは、データベース バックアップまたは部分バックアップを復元することで、常に一緒に復元されます。  
  
 これらのファイル復元のシナリオは次のとおりです。  
  
-   オフライン ファイル復元  
  
     *オフライン ファイル復元*では、破損したファイルまたはファイル グループを復元する間、データベースはオフラインになります。 データベースは、復元シーケンスの最後にオンラインになります。  
  
     [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ではすべてのエディションで、オフラインのファイル復元がサポートされます。  
  
-   オンライン ファイル復元  
  
     *オンライン ファイル復元*では、復元中にデータベースがオンラインであれば、データベースをオンラインにしたままファイル復元を実行できます。 ただし、復元操作時は、ファイルが復元される各ファイル グループがオフラインになります。 オフライン ファイル グループ内のすべてのファイルが復旧されると、そのファイル グループは自動的にオンラインになります。  
  
     オンライン ページおよびファイルの復元の詳細については、「[データベース エンジンの機能とタスク](http://msdn.microsoft.com/library/d9efe145-3306-4d61-bd77-e2af43e19c34)」を参照してください。 オンライン復元の詳細については、「[オンライン復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)」を参照してください。  
  
    > [!TIP]  
    >  ファイル復元のためにデータベースをオフラインにする場合は、 [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-set-options.md) ステートメントの ALTER DATABASE *database_name* SET OFFLINE を実行することにより、データベースをオフラインにしてから復元シーケンスを開始します。  
  
 **このトピックの内容**  
  
-   [単純復旧モデルでのファイルとファイル グループの復元の概要](#Overview)  
  
-   [関連タスク](#RelatedTasks)  
  
##  <a name="Overview"></a> 単純復旧モデルでのファイルとファイル グループの復元の概要  
 ファイル復元のシナリオは、次に示すように、適切なデータをコピーし、ロールフォワードして、復旧する単一の復元シーケンスで構成されます。  
  
1.  破損した各ファイルを最新のファイル バックアップから復元します。  
  
2.  復元されたファイルごとに最新のファイルの差分バックアップを復元し、データベースを復旧します。  
  
### <a name="transact-sql-steps-for-file-restore-sequence-simple-recovery-model"></a>ファイル復元シーケンス用の Transact-SQL 手順 (単純復旧モデル)  
 ここでは、単純ファイル復元シーケンスに必要な [!INCLUDE[tsql](../../includes/tsql-md.md)][RESTORE](../../t-sql/statements/restore-statements-transact-sql.md) オプションを示しています。 説明の目的に関係しない構文や詳細は、省略しています。  
  
 復元シーケンスには、2 つの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントだけが含まれています。 1 つ目のステートメントは `A`というセカンダリ ファイルを復元します。このファイルは、WITH NORECOVERY を指定して復元されます。 2 つ目の操作では、 `B` と `C` という他の 2 つのファイルを復元します。これらのファイルは、WITH RECOVERY を使用して異なるバックアップ デバイスから復元します。  
  
1.  RESTORE DATABASE *database* FILE **=***name_of_file_A*  
  
     FROM *file_backup_of_file_A*  
  
     WITH NORECOVERY**;**  
  
2.  RESTORE DATABASE *database* FILE **=***name_of_file_B***,***name_of_file_C*  
  
     FROM *file_backup_of_files_B_and_C*  
  
     WITH RECOVERY**;**  
  
### <a name="examples"></a>使用例  
  
-   [例 : 読み取り専用ファイルのオンライン復元 &#40;単純復旧モデル&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [例: プライマリ ファイル グループと他のファイル グループを 1 つオフラインで復元する &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model.md)  
  
##  <a name="RelatedTasks"></a> 関連タスク  
 **ファイルおよびファイル グループを復元するには**  
  
-   [既存のファイルにファイルとファイル グループを復元する &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [ファイルおよびファイル グループの復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-files-and-filegroups-sql-server.md)  
  
-   [ファイルおよびファイル グループの復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-files-and-filegroups-sql-server.md)  
  
-   [Restore.SqlRestore メソッド (サーバー) (SMO)](http://msdn.microsoft.com/library/microsoft.sqlserver.management.smo.restore.sqlrestore.aspx)   
  
## <a name="see-also"></a>参照  
 [バックアップと復元: 相互運用性と共存 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-and-restore-interoperability-and-coexistence-sql-server.md)   
 [差分バックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/differential-backups-sql-server.md)   
 [ファイルの完全バックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/full-file-backups-sql-server.md)   
 [バックアップの概要 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)   
 [復元と復旧の概要 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [データベースの全体復元 &#40;単純復旧モデル&#41;](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)   
 [段階的な部分復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)  
  
  