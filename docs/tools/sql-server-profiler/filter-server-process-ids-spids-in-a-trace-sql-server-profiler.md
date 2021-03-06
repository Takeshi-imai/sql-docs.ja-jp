---
title: "トレース (SQL Server Profiler) でサーバー プロセス Id (Spid) をフィルター処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters [SQL Server], traces
- filters [SQL Server], SPIDs
- traces [SQL Server], filters
ms.assetid: f5945c39-be6b-4632-91cb-92066c80e188
caps.latest.revision: "25"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 67926fa0506f797c4f39988061c4d1b7b731e5fa
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="filter-server-process-ids-spids-in-a-trace-sql-server-profiler"></a>トレースでのサーバー プロセス ID (SPID) のフィルター選択 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]このトピックを使用して、トレースでサーバー プロセス id (Spid) をフィルター処理する方法について説明[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]です。  
  
### <a name="to-filter-system-ids-in-a-trace"></a>トレースでシステム ID をフィルター選択するには  
  
1.  **[ファイル]** メニューの **[新しいトレース]**をクリックし、SQL Server のインスタンスに接続します。  
  
     **[トレースのプロパティ]** ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  場合**接続の確立直後後にトレースを開始**が選択されている、**トレースのプロパティ** ダイアログ ボックスが表示されず、トレースが開始します。 この設定をオフに、**ツール** メニューのをクリックして**オプション**、オフにし、**接続の確立直後後にトレースを開始**チェック ボックスをオンします。  
  
2.  **[トレース名]** ボックスに、トレースの名前を入力します。  
  
3.  **テンプレートを使用して**ボックスの一覧で、トレース テンプレートを選択します。  
  
4.  必要に応じて、トレース結果の保存先ファイルまたは保存先テーブルを指定します。  
  
5.  **イベントの選択**タブをクリックし、 **SPID**列見出しを**フィルターの編集** ダイアログ ボックス。 このダイアログ ボックスは、列見出しを右クリックして **[列フィルターの編集]**をクリックしても表示することができます。 **[SPID]** 列が表示されていない場合は、 **[すべての列を表示する]** チェック ボックスをオンにします。  
  
6.  **[フィルターの編集]** ダイアログ ボックスで適切な比較演算子を展開し、比較の値として SPID を入力します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
