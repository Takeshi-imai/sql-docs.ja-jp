---
title: "復元、復旧、バックアップ (T-SQL) の管理用の RESTORE ステートメント |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- restoring files [SQL Server], RESTORE statement
- RESTORE statement, about restore operations
- database restores [SQL Server], RESTORE statement
- restoring databases [SQL Server], RESTORE statement
- database backups [SQL Server], RESTORE statement
- backing up databases [SQL Server], RESTORE statement
- file restores [SQL Server], RESTORE statement
- transaction log backups [SQL Server], RESTORE statement
ms.assetid: fb29a151-f312-4f85-b857-5deeca0de8ce
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d756c4fb9f299abe88ef46c14726f613e8f66497
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="restore-statements-for-restoring-recovering-and-managing-backups-transact-sql"></a>バックアップの復元、復旧、管理用の RESTORE ステートメント (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  ここでは、バックアップ用の RESTORE ステートメントについて説明します。 バックアップを復元および復旧するためのメインの RESTORE {DATABASE | LOG} ステートメントの他に、いくつか補助的な RESTORE ステートメントを使用すると、バックアップの管理や復元シーケンスの計画で役立ちます。 補助的な RESTORE のコマンドには、RESTORE FILELISTONLY、RESTORE HEADERONLY、RESTORE LABELONLY、RESTORE REWINDONLY、RESTORE VERIFYONLY があります。  
  
> [!IMPORTANT]  
>  以前のバージョンの SQL Server では、RESTORE FILELISTONLY、RESTORE HEADERONLY、RESTORE LABELONLY、および RESTORE VERIFYONLY という Transact-SQL ステートメントを使用すると、すべてのユーザーがバックアップ セットやバックアップ デバイスに関する情報を入手できました。 これらのステートメントではバックアップ ファイルの内容に関する情報が明らかになるため、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンでは、これらのステートメントの実行に CREATE DATABASE 権限が必要になります。 この要件により、以前のバージョンよりも、バックアップ ファイルの安全性が高くなり、バックアップ情報が十分保護されます。 このアクセス許可の詳細については、「[データベースの権限の許可&#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|ステートメントから削除してください。|Description|  
|---------------|-----------------|  
|[RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)|RESTORE DATABASE および RESTORE LOG Transact-SQL ステートメントについて説明します。これらのステートメントは、BACKUP コマンドで作成されたバックアップからデータベースを復元および復旧するときに使用します。 RESTORE DATABASE は、すべての復旧モデルのデータベースに使用できます。 RESTORE LOG は、完全復旧モデルと一括ログ復旧モデルでのみ使用できます。 RESTORE DATABASE は、データベースをデータベース スナップショットに戻す場合にも使用できます。|  
|[RESTORE の引数 &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md)|RESTORE ステートメントと、関連する一連の補助ステートメント (RESTORE FILELISTONLY、RESTORE HEADERONLY、RESTORE LABELONLY、RESTORE REWINDONLY、RESTORE VERIFYONLY) の「構文」セクションで説明されている引数について説明します。 ほとんどの引数は、これら 6 つのステートメントでのみ使用できます。 それぞれの引数の説明では、その引数を使用できるステートメントについても示します。|  
|[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)|RESTORE FILELISTONLY Transact-SQL ステートメントについて説明します。このステートメントでは、バックアップ セットに含まれるデータベースとログ ファイルの一覧を含む結果セットが返されます。|  
|[RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)|RESTORE HEADERONLY Transact-SQL ステートメントについて説明します。このステートメントでは、特定のバックアップ デバイス上にあるすべてのバックアップ セットに関して、すべてのバックアップ ヘッダー情報を含む結果セットが返されます。|  
|[RESTORE LABELONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-labelonly-transact-sql.md)|RESTORE LABELONLY Transact-SQL ステートメントについて説明します。このステートメントでは、特定のバックアップ デバイスによって指定されるバックアップ メディアの情報を含む結果セットが返されます。|  
|[RESTORE REWINDONLY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)|RESTORE REWINDONLY Transact-SQL について説明します、このステートメントは、BACKUP または RESTORE ステートメントを NOREWIND オプションで実行した後、開いたままになっているテープ デバイスを巻き戻して閉じるときに使用します。|  
|[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)|RESTORE VERIFYONLY Transact-SQL ステートメントについて説明します。このステートメントではバックアップが検証されますが、復元は行われません。また、バックアップ セットが完全でありバックアップ全体が読み取り可能かどうかが確認されますが、データの構造は検証されません。|  
  
## <a name="see-also"></a>参照  
 [SQL Server データベースのバックアップと復元](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
