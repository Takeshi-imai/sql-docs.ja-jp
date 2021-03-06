---
title: "コレクション セット レポートの表示 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: data-collection
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.dc.reporthistory.calendar.f1
helpviewer_keywords:
- collection sets [SQL Server], viewing reports
- reports [SQL Server], viewing collection set
ms.assetid: c3b1e791-9aa1-4bba-9622-4954568e1820
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 537ccf1648d36229ead7680826f63d081663c998
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="view-a-collection-set-report-sql-server-management-studio"></a>コレクション セット レポートの表示 (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
管理データ ウェアハウスを構成した後、コレクション セットのレポートを [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で表示できます。 セットアップ中にインストールされるシステム データ コレクション セットについては、レポートが用意されています。 レポートには、次のものが含まれます。  
  
-   ディスク使用量の概要  
  
-   クエリ統計の履歴  
  
-   サーバーの利用状況の履歴  
  
 この手順では、 **[ディスク使用量]** コレクション セットのレポートを表示します。 同様の一般的な手順を使用して、他のシステム データ コレクション セットのレポートを表示できます。  
  
### <a name="to-view-a-collection-set-report"></a>コレクション セットのレポートを表示するには  
  
1.  レポートのテーブルは、収集したデータの初回アップロード時に作成されます。 この初回アップロード以前にレポートを表示しようとするとエラーが発生し、レポートは表示されません。 ディスク使用量コレクション セットのデータをアップロードするには、オブジェクト エクスプローラーで、 **[管理]** フォルダー、 **[データ コレクション]**、 **[システム データ コレクション セット]**の順に展開し、 **[ディスク使用量]** コレクション セットを右クリックして、 **[今すぐ収集してアップロード]**をクリックします。  
  
2.  レポートを表示するには、オブジェクト エクスプローラーで、 **[管理]** フォルダーを展開し、 **[データ コレクション]**を右クリックします。次に、 **[レポート]**、 **[管理データ ウェアハウス]**の順にポイントし、 **[ディスク使用量の概要]**をクリックします。  
  
    > [!NOTE]  
    >  一部のレポートでは、データ コレクション タイムラインの下にカレンダーのボタンが表示される場合があります。 このボタンをクリックして、 **データ コレクション レポート カレンダー**にアクセスします。  
  
#### <a name="data-collection-report-calendar"></a>データ コレクション レポート カレンダー  
 このダイアログ ボックスを使用すると、レポート対象にするデータの開始日、開始時刻、および実行時間を指定できます。 たとえば、先週の水曜日の特定の 12 時間におけるサーバーのディスク利用状況をレポート対象とすることができます。  
  
 **開始日**  
 レポート データの開始日を入力するか、カレンダーから開始日を選択します。  
  
 **[開始時刻]**  
 レポート データの開始時刻を入力するか、矢印をクリックして開始時刻を指定します。  
  
 **Duration**  
 レポートに含める時間範囲を指定します。 既定値は 240 分です。 選択できる値は、15 分、60 分、240 分 (4 時間)、720 分 (12 時間)、および 1440 分 (24 時間) です。  
  
## <a name="see-also"></a>参照  
 [[データ コレクション]](../../relational-databases/data-collection/data-collection.md)   
 [Management Studio におけるカスタム レポート](http://msdn.microsoft.com/library/1ba3f758-f39b-4f5f-91ca-516cedc78979)   
 [管理データ ウェアハウスの構成 &#40;SQL Server Management Studio&#41;](../../relational-databases/data-collection/configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
