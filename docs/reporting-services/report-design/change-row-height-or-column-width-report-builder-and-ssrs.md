---
title: "行の高さまたは列の幅 (レポート ビルダーおよび SSRS) の変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f061c204-5cd5-4467-9a9c-8a12803d93ba
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: c13295c229dc4450b9661c25f86d7eacf669787d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# <a name="change-row-height-or-column-width-report-builder-and-ssrs"></a>行の高さまたは列の幅の変更 (レポート ビルダーおよび SSRS)
  行の高さを設定することは、表示されるレポートの行の最大の高さを指定することです。 ただし、既定では、行のテキスト ボックスは実行時に格納するデータに合わせて縦方向に拡張されるように設定されているので、行の高さが指定した高さを超える場合があります。 行の高さを固定するには、行の高さが自動的に拡張されないようにテキスト ボックスのプロパティを変更する必要があります。  
  
 列の幅を設定することは、表示されるレポートの列の最大の幅を指定することです。 列の幅は、格納するテキストに合わせて自動的に調整されたりはしません。  
  
 行または列のセルに四角形領域またはデータ領域が含まれる場合、セルの最小の高さおよび幅は、セルに含まれるアイテムの高さおよび幅によって決定されます。 詳しくは、「[レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md)」をご覧ください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-row-height-by-moving-row-handles"></a>行ハンドルを移動して行の高さを変更するには  
  
1.  [デザイン] ビューで、Tablix データ領域の任意の場所をクリックして選択します。 Tablix データ領域の外側の境界線に灰色の行ハンドルが表示されます。  
  
2.  拡張する行ハンドルの端の上にマウス ポインターを移動します。 両方向矢印が表示されます。  
  
3.  行の端をクリックしてつかみ、上または下に動かして行の高さを調整します。  
  
### <a name="to-change-row-height-by-setting-cell-properties"></a>セル プロパティを設定して行の高さを変更するには  
  
1.  [デザイン] ビューで、テーブル行のセルをクリックします。  
  
     ![テーブルのセルを選択した](../../reporting-services/report-design/media/table-selectcell.png "テーブル内のセルの選択")  
  
2.  表示された **[プロパティ]** ペインで **[高さ]** プロパティを変更し、 **[プロパティ]** ペインの外側の任意の場所をクリックします。  
  
     ![選択したテーブルのセルのプロパティ ペイン](../../reporting-services/report-design/media/cell-propertiespane.png "選択したテーブルのセルのプロパティ ペイン")  
  
### <a name="to-prevent-a-row-from-automatically-expanding-vertically"></a>行の高さが自動的に拡張されないようにするには  
  
1.  [デザイン] ビューで、Tablix データ領域の任意の場所をクリックして選択します。 Tablix データ領域の外側の境界線に灰色の行ハンドルが表示されます。  
  
2.  行ハンドルをクリックして行を選択します。  
  
3.  プロパティ ペインで、CanGrow を **False**に設定します。  
  
    > [!NOTE]  
    >  プロパティ ペインが表示されない場合は、 **[表示]** メニューの **[プロパティ]**をクリックします。  
  
### <a name="to-change-column-width"></a>列の幅を変更するには  
  
1.  [デザイン] ビューで、Tablix データ領域の任意の場所をクリックして選択します。 Tablix データ領域の外側の境界線に灰色の列ハンドルが表示されます。  
  
2.  拡張する列ハンドルの端の上にマウス ポインターを移動します。 両方向矢印が表示されます。  
  
3.  列の端をクリックしてつかみ、左または右に動かして列の幅を調整します。  
  
## <a name="see-also"></a>参照  
 [Tablix データ領域 (レポート ビルダーおよび SSRS)](/sql-docs/docs/reporting-services/report-design/tablix-data-region-report-builder-and-ssrs)   
 [Tablix データ領域のセル、行、および列 (レポート ビルダー) と SSRS](/sql-docs/docs/reporting-services/report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs)   
 [テーブル (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [マトリックス (レポート ビルダーおよび SSRS)](/sql-docs/docs/reporting-services/report-design/create-a-matrix-report-builder-and-ssrs)   
 [一覧 (レポート ビルダーおよび SSRS)](/sql-docs/docs/reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs)   
 [テーブル、マトリックス、および一覧 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  