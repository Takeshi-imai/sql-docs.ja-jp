---
title: "[ジョブの利用状況モニター] | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.jobactivitymonitor.alljobs.f1
- SQL13.SWB.ACTIVITYMON.F1
ms.assetid: 11f2182c-5f71-46f8-8d2b-74f0fc48f2d6
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c928b0ea88d129e5ccbb7bf514d43e4d99ae327f
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="job-activity-monitor"></a>[ジョブの利用状況モニター]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このページでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント ジョブの現在の利用状況を参照できます。 **[フィルター]** をクリックすると、表示されるジョブが限定されます。 **[エージェント ジョブの利用状況]** グリッドは読み取り専用です。 列ヘッダーをクリックすると、グリッドが並べ替えられます。 ジョブを変更するには、ジョブをダブルクリックして **[ジョブのプロパティ]** ダイアログ ボックスを開きます。 グリッドでジョブを右クリックして表示されるメニューから、すべてのジョブ ステップの実行の開始、特定のジョブ ステップの実行、ジョブの無効化または有効化、ジョブの更新、ジョブの削除、ジョブの履歴の表示、ジョブのプロパティの表示ができます。 **[最新の情報に更新]** をクリックすると、グリッドが現在の情報で更新されます。  
  
## <a name="options"></a>および  
**名前**  
ジョブの名前。  
  
**有効**  
ジョブが有効 (**[はい]**) か無効 (**[いいえ]**) かを示します。  
  
**[状態]***  
ジョブの現在の状態です。  
  
**[最終実行の結果]**  
最終実行時のジョブの状態です。  
  
**[最終実行]**  
サーバーのローカル時刻に基づき、ジョブが最後に実行された日付と時刻を示します。  
  
**[次の実行]***  
サーバーのローカル時刻に基づき、ジョブが次に実行される予定の日付と時刻を示します。  
  
**カテゴリ**  
ジョブに割り当てられているジョブ カテゴリです。  
  
**実行可能**  
ジョブを実行できる場合は**[はい]** 、実行できない場合は **[いいえ]** になります。 ステップがないジョブおよび対象サーバーがないジョブは実行できません。  
  
**[スケジュール]**  
ジョブがジョブ スケジュールに割り当てられている場合は**[はい]** 、ジョブにスケジュールがない場合は **[いいえ]** になります。  
  
* [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] の sysadmin 固定サーバー ロールおよびサーバー管理者グループのメンバーのみがこの列の値を表示できます。 SQLAgentOperatorRole ロールのメンバーはこの列の値を表示できません。  
  
#### <a name="to-open-the-job-activity-monitor"></a>[ジョブの利用状況モニター] を開くには  
  
-   **オブジェクト エクスプローラー**で、サーバーを展開して **[SQL Server エージェント]**を展開し、 **[ジョブの利用状況モニター]**を右クリックした後、 **[ジョブの利用状況の表示]**をクリックします。  
  
## <a name="see-also"></a>参照  
[ジョブの利用状況の監視](../../ssms/agent/monitor-job-activity.md)  
  
