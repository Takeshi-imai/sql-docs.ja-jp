---
title: "同期中のスクリプトの実行 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- synchronization [SQL Server replication], scripts
- scripts [SQL Server replication], synchronization and
- sp_addscriptexec
ms.assetid: b58a0877-4e43-4fab-a281-24e6022d3fb1
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2703dfb45f6a1cc2532b15d48becdef930cac3a3
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="execute-scripts-during-synchronization-replication-transact-sql-programming"></a>同期中のスクリプトの実行 (レプリケーション Transact-SQL プログラミング)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  レプリケーションでは、トランザクション パブリケーションおよびマージ パブリケーションのサブスクライバーに対し、要求時にスクリプトを実行できます。 スクリプトはレプリケーションの作業ディレクトリにコピーされ、サブスクライバー側で **sqlcmd** を使って適用されます。 トランザクション パブリケーションのサブスクリプションに対してスクリプトを適用しているときにエラーが発生した場合、既定では、ディストリビューション エージェントの実行が停止します。 レプリケーションのストアド プロシージャを使用すると、指定した [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトをプログラムから実行できます。  
  
### <a name="to-specify-a-script-to-run-for-all-subscribers-to-a-snapshot-transactional-or-merge-publication"></a>スナップショット、トランザクション、マージ パブリケーションのすべてのサブスクライバーに対して実行するスクリプトを指定するには  
  
1.  要求時に実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを作成およびテストします。  
  
2.  スクリプト ファイルを、パブリケーションのスナップショット エージェントがアクセスできる場所に保存します。  
  
3.  パブリッシャー側のパブリケーション データベースに対して、[sp_addscriptexec &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql.md) を実行します。 **@publication** を指定し、手順 2. で作成したスクリプト ファイル名を完全 UNC パスで **@scriptfile** に指定して、さらに、次のいずれかの値を **@skiperror** に指定します。  
  
    -   **0** - エラーが発生した場合、エージェントがスクリプトの実行を停止します。  
  
    -   **1** - エラーが発生した場合、エージェントによってエラー ログが記録され、スクリプトの実行が継続されます。  
  
4.  指定したスクリプトは、エージェントが次にサブスクリプションを同期するときに、各サブスクライバーで実行されます。  
  
## <a name="see-also"></a>参照  
 [データの同期](../../relational-databases/replication/synchronize-data.md)  
  
  
