---
title: "[ポリシーのインポート] ダイアログ ボックス | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.dmf.importpolicy.f1
ms.assetid: 78ab5f6e-2f13-4788-937e-8892ef4e2345
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d7719420505e002b9961fda5c88e379568b5649f
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="import-policies-dialog-box"></a>[ポリシーのインポート] ダイアログ ボックス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このダイアログ ボックスを使用すると、XML ファイルとして保存された 1 つ以上のポリシー (およびその参照された条件) を [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] の現在のインスタンスにインポートできます。  
  
## <a name="options"></a>および  
 **[インポートするファイル]**  
 XML ファイルからポリシーをインポートするには、ファイルのパスと名前を入力するか、参照ボタン (**[...]**) を使用します。  
  
 **[インポートされるアイテムと重複部分を置き換える]**  
 この [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスに同じ名前のポリシーまたは条件が既に存在する場合、その既存のポリシーまたは条件が上書きされます。 依存ポリシーを使用している条件は、依存ポリシーも上書きしない限り上書きできません。 このオプションを選択していない場合は、同じ条件式を使用している既存の条件によってエラーが発生することはありません。  
  
 **[ポリシーの状態]**  
 インポートしたポリシーの状態を選択します。  
  
-   **[インポート時にポリシーの状態を保存します]**  
  
-   **[インポート時にすべてのポリシーを有効にします]**  
  
-   **[インポート時にすべてのポリシーを無効にします]**  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したサーバーの管理](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [ポリシー ベースの管理ポリシーのインポート](../../relational-databases/policy-based-management/import-a-policy-based-management-policy.md)   
 [ポリシー ベースの管理ポリシーのエクスポート](../../relational-databases/policy-based-management/export-a-policy-based-management-policy.md)  
  
  
