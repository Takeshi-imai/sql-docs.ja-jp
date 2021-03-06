---
title: "[SQL Server エージェントのプロパティ]([詳細設定] ページ) | Microsoft Docs"
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
f1_keywords: sql13.ag.agent.advanced.f1
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d548d31a905a64651e75d929dea58f70585b4bc1
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-agent-properties-advanced-page"></a>[SQL Server エージェントのプロパティ] ([詳細設定] ページ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このページを使用すると、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスの詳細プロパティを表示および変更できます。  
  
## <a name="options"></a>および  
**[SQL Server イベントの転送]**  
このカテゴリのオプションを使用して、イベントの転送をアクティブにしたり、構成したりします。  
  
**[イベントを別のサーバーに転送する]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント イベントを別のサーバーに転送します。  
  
**[サーバー]**  
イベントの転送先のサーバー名を選択します。  
  
**[未処理のイベント]**  
未処理のイベントのみを指定のサーバーに転送します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントは、警告が返されないイベントのみを転送します。  
  
**[すべてのイベント]**  
すべてのイベントを転送します。 ローカル インスタンスの警告がイベントに応答した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントはイベントの転送と警告の処理の両方を行います。  
  
**[次のレベル以上のイベント発生時]**  
指定された重大度レベル以上のイベントのみを転送します。  
  
**[CPU のアイドル状態]**  
このカテゴリのオプションは、CPU のアイドル スケジュールで実行がスケジュールされたジョブを、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントが実行するための条件を定義します。  
  
**[CPU のアイドル状態を定義する]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントにより CPU がアイドル状態であると見なされる条件を定義します。  
  
**[CPU の平均使用量が次の値以下になったとき]**  
CPU がアイドル状態であると見なされる CPU の使用量の割合です。  
  
**[かつ、この使用率以下で次の期間を経過]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントが CPU のアイドル スケジュールのジョブを実行する前に、CPU の平均使用量が指定されたレベルを下回っていなければならない時間です。  
  
## <a name="see-also"></a>参照  
[スケジュールの作成とジョブへのアタッチ](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
[イベントの管理](../../ssms/agent/manage-events.md)  
  
