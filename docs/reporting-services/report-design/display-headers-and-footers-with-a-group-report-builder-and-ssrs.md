---
title: "表示 (レポート ビルダーおよび SSRS) のグループでヘッダーとフッター |Microsoft ドキュメント"
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
ms.assetid: 8eb7d648-4df2-491a-96cb-99e55629d617
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 052e0f66818fd3d9e4cd4ad59720da4a7280c988
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# <a name="display-headers-and-footers-with-a-group-report-builder-and-ssrs"></a>グループ単位でのヘッダーとフッターの表示 (レポート ビルダーおよび SSRS)
  Tablix データ領域では、グループに関連付けられている動的行と一緒に、静的行 (グループ ヘッダー、グループ フッターなど) を表示するかどうかを制御できます。  
  
 複数のページですべての列見出しまたは行見出しを繰り返し表示するには、Tablix データ領域のプロパティを設定します。 詳細については、次を参照してください。[表示行および列ヘッダーを複数のページ (レポート ビルダーおよび SSRS) で](/sql-docs/docs/reporting-services/report-design/display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs)です。  
  
 入れ子になったグループに関連付けられている動的行と動的列の表示動作、または、ラベルや小計に関連付けられている静的行と静的列の表示動作を制御するには、Tablix メンバーのプロパティを設定する必要があります。 Tablix メンバーは、静的な行または列、あるいは動的な行または列を表します。 静的メンバーが表示されるのは 1 回だけです。 たとえば、代表的な静的行に、総計行があります。 動的メンバーは、1 グループにつき 1 回表示されます。 たとえば、特定のグループに対し [Territory] というグループ式が割り当てられているとき、そのグループに関連付けられている行は、一意の区域 (territory) 値ごとに 1 回表示されることになります。 Tablix メンバーの詳細については、次を参照してください。 [Tablix データ領域のセル、行と列 & #40 です。レポート ビルダー"&"#41;SSRS](../../reporting-services/report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)です。  
  
 Tablix メンバーのプロパティを設定するには、グループ化ペインで Tablix メンバーを選択し、プロパティ ペインで **KeepWithGroup**、 **KeepTogether**、および **RepeatOnNewPage** の各プロパティを設定します。 グループ ヘッダーとグループ フッターをグループと同じページに表示するには、 **KeepWithGroup** を使用します。 グループの行または列と一緒に静的メンバーを表示するには、 **KeepTogether** を使用します。 **KeepWithGroup** 値によって指定された行グループ メンバーの少なくとも 1 つの完全なインスタンスが表示されるページごとにグループ ヘッダーまたはグループ フッターを繰り返すには、 **RepeatOnNewPage** を使用します。 列グループ メンバーに対して、**RepeatOnNewPage** はサポートされません。  
  
> [!NOTE]  
>  **KeepWithGroup**、 **KeepTogether**、および**RepeatOnNewPage**グループ メンバーのプロパティを使用して設定できるは、 **詳細設定モード**のグループ化ウィンドウです。 詳細については、次を参照してください。[グループ化ペインと #40 です。レポート ビルダー"&"#41;](../../reporting-services/report-design/grouping-pane-report-builder.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-keep-a-static-row-with-a-set-of-dynamic-rows-associated-with-a-row-group"></a>静的行を行グループに関連付けられている一連の動的行と一緒に表示するには  
  
1.  デザイン画面で、Tablix データ領域の任意の場所をクリックして選択します。 グループ化ペインに、データ領域の行グループと列グループが表示されます。  
  
2.  グループ化ペインの右側にある下矢印をクリックし、 **[詳細設定モード]**をクリックします。 行グループ ペインには、行グループ階層の静的メンバーおよび動的メンバーが階層的に表示されます。  
  
3.  グループ行と共に維持する行ヘッダーまたは行フッターに対応する静的メンバーをクリックします。 プロパティ ペインに **[Tablix メンバー]** プロパティが表示されます。  
  
4.  プロパティ ペインで、 **KeepWithGroup**をクリックし、ドロップダウン リストから次のいずれかの値を選択します。  
  
    -   **[なし]** 選択した行グループのメンバーと共にこのメンバーを維持しない場合は、このオプションを選択します。  
  
    -   **[前]** 前のグループのメンバーと共にこのメンバーを維持する場合は、このオプションを選択します。 このオプションはグループ フッター行に使用できます。  
  
    -   **[後]** 次のグループのメンバーと共にこのメンバーを維持する場合は、このオプションを選択します。 このオプションはグループ ヘッダー行に使用できます。  
  
5.  (省略可) レポートをプレビューします。 レポート レンダラーは、可能な限り、指定された行グループ メンバーと共にこのメンバーを維持します。  
  
### <a name="to-keep-a-static-column-with-a-set-of-dynamic-columns-associated-with-a-column-group"></a>静的列を列グループに関連付けられている一連の動的列と一緒に表示するには  
  
1.  デザイン画面で、Tablix データ領域の任意の場所をクリックして選択します。 グループ化ペインに、データ領域の行グループと列グループが表示されます。  
  
2.  グループ化ペインの右側にある下矢印をクリックし、 **[詳細設定モード]**をクリックします。 列グループ ペインには、列グループ階層の静的メンバーおよび動的メンバーが階層的に表示されます。  
  
3.  グループ列と共に維持する静的列に対応する静的メンバーをクリックします。 プロパティ ペインに **[Tablix メンバー]** プロパティが表示されます。  
  
4.  プロパティ ペインで、 **KeepWithGroup**をクリックし、ドロップダウン リストから次のいずれかの値を選択します。  
  
    -   **[なし]** 選択した列グループのメンバーと共にこのメンバーを維持しない場合は、このオプションを選択します。  
  
    -   **[前]** 前のグループのメンバーと共にこのメンバーを維持する場合は、このオプションを選択します。 このオプションは、指定した列グループ メンバーの前に表示する列ラベルに使用できます。  
  
    -   **[後]** 次のグループのメンバーと共にこのメンバーを維持する場合は、このオプションを選択します。 このオプションは、指定した列グループ メンバーの後に表示する列の合計に使用できます。  
  
5.  (省略可) レポートをプレビューします。 可能な限り、レポート レンダラーは指定された列グループ メンバーと共にこのメンバーを維持します。  
  
## <a name="see-also"></a>参照  
 [Tablix データ領域のセル、行、および列 (レポート ビルダー) と SSRS](/sql-docs/docs/reporting-services/report-design/tablix-data-region-report-builder-and-ssrs)   
 
  
  