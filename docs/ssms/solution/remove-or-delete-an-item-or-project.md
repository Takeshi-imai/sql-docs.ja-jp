---
title: "アイテムやプロジェクトのクリアまたは削除 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-solutions
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting project items
- projects [SQL Server Management Studio], item removal
- removing project items
ms.assetid: 3fd92434-70f5-466e-bef0-7e0fd73ddb1c
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 260005349211feaeb74280a65e1b5d89ef092426
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="remove-or-delete-an-item-or-project"></a>アイテムやプロジェクトのクリアまたは削除
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] プロジェクトに含まれるプロジェクト アイテムには、クエリ、接続、およびその他のファイルがあります。 プロジェクトのクエリとその他のファイルは、記憶域に残したままソリューションからクリアできます。 現在のソリューションでは使用せずに、別のソリューションで使用する場合は、プロジェクトやアイテムをクリアします。  
  
### <a name="to-remove-a-project-item"></a>プロジェクト アイテムをクリアするには  
  
1.  ソリューション エクスプローラーで、クリアするプロジェクト アイテムを選択します。  
  
2.  **[編集]** メニューの **[削除]**をクリックします。  
  
3.  確認ダイアログで **[削除]** をクリックすると、プロジェクトからアイテムが削除されます。  
  
クリアしたアイテムは、ファイル システムにまだ存在しています。 したがって、クリアしたアイテムは、元のソリューションまたは別のソリューションに追加することができます。  
  
#### <a name="to-remove-a-project"></a>プロジェクトをクリアするには  
  
1.  ソリューション エクスプローラーで、クリアするプロジェクトを選択します。  
  
2.  **[編集]** メニューの **[削除]**をクリックします。  
  
3.  確認ダイアログで **[OK]**をクリックします。ソリューションからプロジェクトがクリアされます。  
  
プロジェクトは完全に削除できますが、最初に [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] ソリューションからプロジェクトへの参照をすべてクリアし、次に [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows エクスプローラーを使用して、関連付けられているファイルを記憶域から完全に削除する必要があります。  
  
#### <a name="to-delete-a-project"></a>プロジェクトを削除するには  
  
1.  ソリューション エクスプローラーで、ソリューションから削除するプロジェクトをクリアします。  
  
2.  Windows エクスプローラーで、削除するプロジェクトまたはアイテムに関連付けられているファイルを検索して選択します。  
  
3.  **[ファイル]** メニューの **[削除]**をクリックします。  
  
## <a name="see-also"></a>参照  
[ソリューション エクスプローラー](../../ssms/solution/solution-explorer.md)  
[プロジェクトへの新規項目の追加](../../ssms/solution/add-new-items-to-a-project.md)  
[既存の項目をプロジェクトに追加する](../../ssms/solution/add-existing-items-to-a-project.md)  
  
