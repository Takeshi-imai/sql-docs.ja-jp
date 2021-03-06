---
title: "パブリケーション情報、[警告](マージ パブリケーション、SQL Server 2005 以降) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
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
f1_keywords:
- sql13.rep.monitor.publicationinfo.warningsandagents.merge.f1
ms.assetid: 9bef3565-5f13-42ac-8723-ebe55b0c11e6
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ff89a5c3cd17f79ae90d57e987edd30827e3bee0
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="publication-information-warnings-merge-publication-sql-server-2005-and-later"></a>パブリケーション情報、[警告] \(マージ パブリケーション、SQL Server 2005 以降)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **以降を実行しているディストリビューターでは、** [警告] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] タブを使用できます。 **[警告]** タブでは、選択されているパブリケーションに対して次の操作を実行できます。  
  
-   警告を有効にする。  
  
-   警告に関連するしきい値を指定する。  
  
-   警告に関連する通知を定義する。  
  
## <a name="warnings-thresholds-and-alerts"></a>警告、しきい値、および通知  
 既定では、レプリケーション モニターは、初期化されていないサブスクリプションに対して警告を表示します。サブスクリプション情報を含むページの **[状態]** 列に、警告として **[初期化されていないサブスクリプション]** という状態が表示されます。 マージ パブリケーションの場合は、以下の追加条件で警告を表示するかどうかを指定できます。  
  
-   差し迫ったサブスクリプションの有効期限。  
  
     これは、 **[サブスクリプションの有効期限がしきい値内で切れる場合に警告します。]**オプションに対応します。 指定したしきい値に到達するか、しきい値を超過すると、(より優先度が高い問題を表示する必要がない限り) **[まもなく期限切れ/期限切れ]** というサブスクリプション状態が表示されます。  
  
-   指定した同期時刻を超えた場合。  
  
     これは、オプション **[ダイヤルアップ接続のマージ長がしきい値を超えた場合に警告します。]** および **[LAN 接続のマージ長がしきい値を超えた場合に警告します。]**に対応します。 これらのしきい値は両方とも設定できますが、特定の同期の実行中に使用できるのはいずれか 1 つだけです。 マージ エージェントは、接続の種類に基づいて適切なしきい値を適用します。  
  
     指定したしきい値に到達するかまたはしきい値を超過すると、(より優先度が高い問題を表示する必要がない限り) **[長期マージ]** というサブスクリプション状態が表示されます。  
  
-   指定した数の行を特定の時間内で処理できない場合。  
  
     これは、オプション **[ダイヤルアップ接続で 1 秒あたりにマージされる行数がしきい値未満の場合に警告します。]** および **[LAN 接続のマージ長がしきい値を超えた場合に警告します。]**に相当します。 これらのしきい値は両方とも設定できますが、特定の同期の実行中に使用できるのはいずれか 1 つだけです。 マージ エージェントは、接続の種類に基づいて適切なしきい値を適用します。  
  
     指定したしきい値に到達するか、しきい値を超過すると、(より優先度が高い問題を表示する必要がない限り) **[パフォーマンス クリティカル]** というサブスクリプション状態が表示されます。  
  
 警告を有効にする場合は、しきい値も設定します。 たとえば、警告 **[LAN 接続のマージ長がしきい値を超えた場合に警告します。]**を有効にした場合は、マージ同期の長さとして許容できる最大値を設定します。  
  
 しきい値に到達した場合は、レプリケーション モニターに警告を表示でき、さらに通知を発行することができます。 通知を定義するには、 **[警告の構成]** をクリックし、 **[レプリケーションの警告の構成]** ダイアログ ボックスに情報を入力します。  
  
## <a name="options"></a>および  
 **有効**  
 警告を有効にする場合に選択します。その場合は、しきい値を指定します。  
  
 **警告**  
 特定のレプリケーションの警告用の警告の設定を有効にする場合に選択します。  
  
 **警告**  
 しきい値に関連付けられている警告の説明です。  
  
 **しきい値**  
 しきい値の値を指定します。  
  
 **[警告の構成]**  
 **[警告]** グリッドの行を選択し、 **[警告の構成]** をクリックすると、 **[レプリケーションの警告の構成]** ダイアログ ボックスが表示されます。 このダイアログ ボックスでは、選択したしきい値および警告に関連付けた通知を定義できます。  
  
 **[変更の破棄]**  
 クリックすると、警告およびしきい値に対する変更が破棄されます。  
  
> [!NOTE]  
>  **[変更の破棄]** をクリックしても、 **[レプリケーションの警告の構成]** ダイアログ ボックスに定義されている通知は影響を受けません。  
  
 **[変更の保存]**  
 クリックすると、警告およびしきい値に対する変更が保存されます。  
  
## <a name="see-also"></a>参照  
 [レプリケーション モニターの開始](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [パブリケーションの情報の表示とタスクの実行 &#40;レプリケーション モニター&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [レプリケーション モニターを使用したパフォーマンスの監視](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)   
 [レプリケーションの監視](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [レプリケーション モニターのしきい値と警告の設定](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  
