---
title: "レプリケーション モニターでのパブリケーションおよびサブスクリプションの状態の表示 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Log Reader Agent, monitoring
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- publications [SQL Server replication], viewing information
- Snapshot Agent, monitoring
- Distribution Agent, monitoring
- monitoring performance [SQL Server replication], publication status
- monitoring performance [SQL Server replication], subscription status
- subscriptions [SQL Server replication], viewing status
- Replication Monitor, publication and subscription status
ms.assetid: 16590771-9867-463e-a973-36a5c145ac16
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c3823675277eb587977892e5e1724bd8dda7b0a9
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="view-publication-and-subscription-status-in-replication-monitor"></a>レプリケーション モニターでのパブリケーションおよびサブスクリプションの状態の表示
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション モニターには、パブリケーションおよびサブスクリプションの状態情報が表示されます。  
  
-   パブリケーションの状態は、そのサブスクリプションの最も優先度の高い状態によって決定されます。 たとえば、あるパブリケーションに対する 1 つのサブスクリプションにエラーが発生し、別のサブスクリプションにはパフォーマンス上の問題がある場合、そのパブリケーションに対してはエラーの状態が表示されます。  
  
-   サブスクリプションの状態は、そのサブスクリプションにサービスを提供するエージェントの状態によって決定されます。 マージ レプリケーションの場合はマージ エージェントです。 トランザクション レプリケーションの場合は、ログ リーダー エージェントまたはディストリビューション エージェントです (優先度の高い方の状態が表示されます。キュー更新サブスクリプションが使用されている場合は、状態はキュー リーダー エージェントによっても決定されます)。 スナップショット レプリケーションの場合は、スナップショット エージェントまたはディストリビューション エージェントです (優先度の高い方の状態が表示されます)。  
  
 以下に、パブリケーションおよびサブスクリプションの状態の値の一覧を示します。 しきい値に達したか、超えた場合にのみ、3 つの状態値が表示されます。  
  
-   有効期限切れサブスクリプション  
  
     この状態値は、すべての種類のレプリケーションに適用されます。 詳細については、「 [レプリケーション モニターのしきい値と警告の設定](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。  
  
-   [パフォーマンス クリティカル]  
  
     この状態値は、トランザクション レプリケーションとマージ レプリケーションに適用されます。 詳細については、「[レプリケーション モニターを使用したパフォーマンスの監視](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)」をご覧ください。  
  
-   [長期マージ]  
  
     この状態値はマージ レプリケーションに適用されます。 詳細については、「[レプリケーション モニターを使用したパフォーマンスの監視](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)」をご覧ください。  
  
 パブリケーションおよびサブスクリプションの状態の他に、マージ レプリケーションではアーティクル レベルの統計が使用できます。この情報は、マージ フェーズの完了までに要する時間、指定されたアーティクルの処理に費やされた時間、サブスクライバーが使用している接続の種類、およびその他の重要な情報についての詳細を提供します。 統計情報は、レプリケーション モニターの [マージ エージェント] ウィンドウに表示されます。 スナップショット レプリケーションおよびトランザクション レプリケーションでは、ディストリビューション エージェントの処理に関する詳細が提供されます。  
  
 **パブリケーションおよびサブスクリプションの状態を表示するには**  
  
-   レプリケーション モニター: [パブリケーションの情報の表示とタスクの実行 &#40;レプリケーション モニター&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)[サブスクリプションの情報の表示とタスクの実行 &#40;レプリケーション モニター&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)  
  
 **エージェントの詳細情報を表示するには**  
  
-   レプリケーション モニター: [パブリケーションに関連付けられているエージェントの情報の表示とタスクの実行 &#40;レプリケーション モニター&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md)、[サブスクリプションに関連付けられているエージェントの情報の表示とタスクの実行 &#40;レプリケーション モニター&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md)。  
  
## <a name="publication-status-values"></a>パブリケーションの状態の値  
 次の表は、パブリケーションの状態の値と対応するアイコンを優先度順に示しています。  
  
|状態|アイコン|  
|------------|----------|  
|[エラー]|![UI アイコン: エラー](../../../database-engine/availability-groups/windows/media/repl-icon-error.gif "UI アイコン: エラー")|  
|[パフォーマンス クリティカル]|![UI アイコン: 警告](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "UI アイコン: 警告")|  
|[失敗したコマンドの再試行]|![UI アイコン: レプリケーション エージェントの再試行](../../../relational-databases/replication/monitor/media/repl-icon-retry.gif "UI アイコン: レプリケーション エージェントの再試行")|  
|[OK]|なし|  
  
## <a name="subscription-status-values"></a>サブスクリプションの状態値  
 次の表は、サブスクリプションの状態値と対応するアイコンを優先度順に示しています。 サブスクリプションは、" **まもなく期限切れ/期限切れ** " と " **失敗したコマンドの再試行**" など同時に 2 つの状態になることがあります。その場合、最も優先度の高い状態が表示されます。  
  
 状態値 " **パフォーマンス クリティカル**"、" **まもなく期限切れ/期限切れ**"、および " **初期化されていないサブスクリプション** " は警告です。 警告が表示されるとき、レプリケーション モニターにはエージェントが実行中であるかどうかも表示されます。 たとえば、 **[実行中]、[パフォーマンス クリティカル]**という形で状態が表示されます。  
  
### <a name="transactional-subscriptions"></a>トランザクション サブスクリプション  
  
|状態|アイコン|  
|------------|----------|  
|[エラー]|![UI アイコン: エラー](../../../database-engine/availability-groups/windows/media/repl-icon-error.gif "UI アイコン: エラー")|  
|[パフォーマンス クリティカル]|![UI アイコン: 警告](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "UI アイコン: 警告")|  
|まもなく期限切れ/期限切れ|![UI アイコン: 警告](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "UI アイコン: 警告")|  
|[初期化されていないサブスクリプション]|![UI アイコン: 警告](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "UI アイコン: 警告")|  
|[失敗したコマンドの再試行]|![UI アイコン: レプリケーション エージェントの再試行](../../../relational-databases/replication/monitor/media/repl-icon-retry.gif "UI アイコン: レプリケーション エージェントの再試行")|  
|[実行されていません]|![UI アイコン: レプリケーション エージェントの停止](../../../relational-databases/replication/monitor/media/repl-icon-stopped.gif "UI アイコン: レプリケーション エージェントの停止")|  
|実行中|![UI アイコン: レプリケーション エージェントの実行](../../../relational-databases/replication/monitor/media/repl-icon-running.gif "UI アイコン: レプリケーション エージェントの実行")|  
  
### <a name="merge-subscriptions"></a>マージ サブスクリプション  
  
|状態|アイコン|  
|------------|----------|  
|[エラー]|![UI アイコン: エラー](../../../database-engine/availability-groups/windows/media/repl-icon-error.gif "UI アイコン: エラー")|  
|[パフォーマンス クリティカル]|![UI アイコン: 警告](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "UI アイコン: 警告")|  
|[長期マージ]|![UI アイコン: 警告](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "UI アイコン: 警告")|  
|まもなく期限切れ/期限切れ|![UI アイコン: 警告](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "UI アイコン: 警告")|  
|[初期化されていないサブスクリプション]|![UI アイコン: 警告](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "UI アイコン: 警告")|  
|[失敗したコマンドの再試行]|![UI アイコン: レプリケーション エージェントの再試行](../../../relational-databases/replication/monitor/media/repl-icon-retry.gif "UI アイコン: レプリケーション エージェントの再試行")|  
|[同期中]|![UI アイコン: レプリケーション エージェントの実行](../../../relational-databases/replication/monitor/media/repl-icon-running.gif "UI アイコン: レプリケーション エージェントの実行")|  
|同期されていません|![UI アイコン: レプリケーション エージェントの停止](../../../relational-databases/replication/monitor/media/repl-icon-stopped.gif "UI アイコン: レプリケーション エージェントの停止")|  
  
### <a name="snapshot-subscriptions"></a>スナップショット サブスクリプション  
  
|状態|アイコン|  
|------------|----------|  
|[エラー]|![UI アイコン: エラー](../../../database-engine/availability-groups/windows/media/repl-icon-error.gif "UI アイコン: エラー")|  
|[まもなく期限切れ/期限切れ]|![UI アイコン: 警告](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "UI アイコン: 警告")|  
|[初期化されていないサブスクリプション]|![UI アイコン: 警告](../../../database-engine/availability-groups/windows/media/repl-icon-warn.gif "UI アイコン: 警告")|  
|[失敗したコマンドの再試行]|![UI アイコン: レプリケーション エージェントの再試行](../../../relational-databases/replication/monitor/media/repl-icon-retry.gif "UI アイコン: レプリケーション エージェントの再試行")|  
|[同期中]|![UI アイコン: レプリケーション エージェントの実行](../../../relational-databases/replication/monitor/media/repl-icon-running.gif "UI アイコン: レプリケーション エージェントの実行")|  
|同期されていません|![UI アイコン: レプリケーション エージェントの停止](../../../relational-databases/replication/monitor/media/repl-icon-stopped.gif "UI アイコン: レプリケーション エージェントの停止")|  
  
## <a name="see-also"></a>参照  
 [レプリケーションの監視](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
