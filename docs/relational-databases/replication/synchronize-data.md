---
title: "データの同期 | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
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
helpviewer_keywords:
- synchronization [SQL Server replication], about synchronization
- merge replication synchronization [SQL Server replication]
- scripts [SQL Server replication], synchronization and
- synchronization [SQL Server replication]
- snapshot replication [SQL Server], synchronization
- transactional replication, synchronization
- subscriptions [SQL Server replication], synchronizing
- on demand script execution
- replication [SQL Server], synchronization
- scripts [SQL Server replication]
ms.assetid: 724802f7-7d69-46d3-a330-bd8aa7f53114
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 96387cb192e0b13656788786bc52512d20ffe9fb
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="synchronize-data"></a>データの同期
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  データの同期とは、初期スナップショットをサブスクライバーで適用した後に、パブリッシャーとサブスクライバーの間でデータとスキーマ変更を反映する処理のことです。 同期は、次のように実行されます。  
  
-   連続して実行。これは通常、トランザクション レプリケーションの場合です。  
  
-   要求時に実行。これは通常、マージ レプリケーションの場合です。  
  
-   スケジュールに基づいて実行。これは通常、スナップショット レプリケーションの場合です。  
  
 サブスクリプションが同期されると、使用しているレプリケーションの種類に基づいて異なる処理が実行されます。  
  
-   スナップショット レプリケーション。 同期とは、ディストリビューション エージェントがサブスクライバーでスナップショットを再適用して、サブスクリプション データベースのスキーマおよびデータがパブリケーション データベースとの一貫性を持つようにすることを意味します。  
  
     データまたはスキーマへの変更がパブリッシャーで行われている場合、サブスクライバーに変更を反映させるために、新しいスナップショットを生成する必要があります。  
  
-   トランザクション レプリケーション。 同期とは、ディストリビューション エージェントが更新、挿入、削除、およびその他の変更をディストリビューション データベースからサブスクライバーに転送することを意味します。  
  
-   マージ レプリケーション。 同期とは、マージ エージェントがサブスクライバーからパブリッシャーに変更をアップロードし、パブリッシャーからサブスクライバーに変更をダウンロードすることを意味します。 競合が存在する場合は、検出されて解決されます。 データは集約され、最終的にパブリッシャーとすべてのサブスクライバーでデータ値が同じになります。 競合が検出されて解決された場合、一部のユーザーがコミットした作業は、定義されたポリシーに応じて、競合が解決するように変更されます。  
  
 スナップショット パブリケーションでは、同期が発生するたびに、サブスクライバーでスキーマが完全に更新されます。そのため、すべてのスキーマ変更がサブスクライバーに適用されます。 トランザクション レプリケーションとマージ レプリケーションでも、最も一般的なスキーマ変更がサポートされます。 詳細については、「[パブリケーション データベースでのスキーマの変更](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)」を参照してください。  
  
 プッシュ サブスクリプションを同期するには、「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」を参照してください。  
  
 プル サブスクリプションを同期するには、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md)」を参照してください。  
  
 同期のスケジュールを設定するには、「 [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md)」を参照してください。  
  
 **同期の競合を表示および解決するには**  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [マージ パブリケーションでのデータの競合の表示および解決 &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/view-and-resolve-data-conflicts-for-merge-publications.md)  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [トランザクション パブリケーションのデータの競合の表示 &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
## <a name="executing-code-during-synchronization"></a>同期中のコード実行  
 レプリケーションでは、同期中にコードを実行する方法が 2 つサポートされています。  
  
-   要求時スクリプト実行は、トランザクション レプリケーションおよびマージ レプリケーションでサポートされています。 要求時スクリプト実行を使用すると、同期中に実行する SQL スクリプトを指定できます。 スクリプトはサブスクライバーにコピーされ、同期処理の開始時に **sqlcmd** を使用して実行されます。 スクリプトは、レプリケートされた変更をサブスクライバーに適用するときに、それらの変更へはアクセスしません。 詳細については、「[同期中のスクリプトの実行 &#40;レプリケーション Transact-SQL プログラミング&#41;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)」を参照してください。  
  
-   ビジネス ロジック ハンドラーは、マージ レプリケーションでサポートされています。 ビジネス ロジック ハンドラー フレームワークを使用すると、マネージ コードのアセンブリを記述して、マージ同期処理中に呼び出すことができます。 このアセンブリには、データの変更、競合、およびエラーなど、同期中に発生するさまざまな状況に対処するためのビジネス ロジックを記述できます。 詳細については、「[Execute Business Logic During Merge Synchronization](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)」 (マージ同期中のビジネス ロジックの実行) を参照してください。  
  
## <a name="see-also"></a>参照  
 [マージ レプリケーションの競合の検出と解決](../../relational-databases/replication/merge/advanced-merge-replication-resolve-merge-replication-conflicts.md)  
  
  
