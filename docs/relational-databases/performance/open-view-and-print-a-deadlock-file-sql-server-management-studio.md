---
title: "デッドロック ファイルを開く、表示、および印刷する方法 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deadlocks [SQL Server], printing files
- deadlocks [SQL Server], opening files
- opening deadlock files
- printing deadlock files
ms.assetid: 5061b13f-2cb7-457a-b8d0-fbd437b510ab
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ce9c52fb2842133193893bd4d551e54a1aeed015
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="open-view-and-print-a-deadlock-file-sql-server-management-studio"></a>デッドロック ファイルを開く、表示、および印刷する方法 (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] でデッドロックが発生したら、デッドロック情報をキャプチャしてファイルに保存できます。 保存したデッドロック ファイルは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で開いて表示または印刷できます。  
  
## <a name="open-and-view-a-deadlock-file"></a>デッドロック ファイルを開いて表示する  
  
1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で **[ファイル]** メニューの **[開く]** をポイントし、**[ファイル]** を選択します。  
  
2. **[ファイルを開く]** ダイアログ ボックスで、 **[ファイルの種類]** ボックスの一覧から [SQL デッドロック ファイル] を選択します。 これにより、デッドロック ファイルだけが一覧表示されます。  
  
## <a name="print-a-deadlock-file"></a>デッドロック ファイルを印刷する  
  
1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で **[ファイル]** メニューの **[開く]** をポイントし、**[ファイル]** を選択します。  
  
2. **[ファイルを開く]** ダイアログ ボックスで、 **[ファイルの種類]** ボックスの一覧から [SQL デッドロック ファイル] を選択します。 これにより、デッドロック ファイルだけが一覧表示されます。  
  
3. 印刷するデッドロック ファイルを選択して、**[開く]** を選択します。  
  
4. **[ファイル]** メニューの **[印刷]** を選択します。  
  
## <a name="see-also"></a>参照  
 [Deadlock Graph の保存 (SQL Server Profiler)](../../relational-databases/performance/save-deadlock-graphs-sql-server-profiler.md)  
  
  
