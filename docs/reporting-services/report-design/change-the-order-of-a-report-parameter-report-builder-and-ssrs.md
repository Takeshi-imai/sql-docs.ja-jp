---
title: "レポート パラメーターの順序の変更 (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
caps.latest.revision: "9"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 73d4bee574572e4c68c00222be9b07e09e4fa2c6
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a>レポート パラメーターの順序の変更 (レポート ビルダーおよび SSRS)
  従属パラメーターが、そのパラメーターが依存するパラメーターの前にリストされている場合、レポート パラメーターの順序を変更します。 カスケード型パラメーターがある場合や、パラメーターの既定値をユーザーに対して示してから他のパラメーターの値をユーザーが選択する場合に、パラメーターの順序は重要です。 従属レポート パラメーターには、既定値のクエリまたは有効値のクエリのいずれかの、クエリ パラメーターへの参照が含まれます。これは、 **レポート データ** ペインのパラメーター リストでその後にあるレポート パラメーターを参照します。  
  
 レポートの実行時、レポート ビューアー ツール バーでのパラメーターの表示順は、 **レポート データ** ペインのパラメーターの順序とカスタム パラメーター ペイン内のパラメーターの場所によって決まります。 詳細については、「[レポートのパラメーター ペインをカスタマイズする &#40;レポート ビルダー&#41;](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-change-the-order-of-report-parameters"></a>レポート パラメーターの表示順を変更するには  
  
レポート パラメーターの表示順は、次のいずれかの操作で変更できます。  
  
-   次の図のように、 **レポート データ** ペインでパラメーターをクリックし、上矢印および下矢印ボタンを使用して、一覧内でのパラメーターの位置を移動します。  **レポート データ** ペインでパラメーターの順序を変更すると、パラメーター ペインのパラメーターの位置が変わります。  
  
     ![[レポート データ] ペインのパラメーターの順序を変更する](../../reporting-services/report-design/media/ssrs-changeorderofparameters-reportdata.png "[レポート データ] ペインのパラメーターの順序を変更する")  
  
-   パラメーター ペインで、パラメーターをペイン内の新しい列または行にドラッグします。 ペイン内でパラメーターの位置を変更すると、 **レポート データ** ペインのパラメーターの順序が変わります。 ペイン内のパラメーターの位置を変更する方法については、「[レポートのパラメーター ペインをカスタマイズする &#40;Report Builder&#41;](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [レポート ビルダーのダイアログ ボックス、ペイン、およびウィザードに関するヘルプ](http://msdn.microsoft.com/en-us/2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [カスケード型パラメーターのレポートへの追加 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [チュートリアル: レポートへのパラメーターの追加 &#40;レポート ビルダー&#41;](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [データセット フィルター、データ領域フィルター、およびグループ フィルターの追加 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Parameters コレクションの参照 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  
