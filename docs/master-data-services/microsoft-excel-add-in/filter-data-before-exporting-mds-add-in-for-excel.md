---
title: "エクスポート前のデータのフィルター処理 (Excel 用 MDS アドイン) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
caps.latest.revision: 10
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 13a0720defc0a9e837f771a73f44bca343773ce1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="filter-data-before-exporting-mds-add-in-for-excel"></a>エクスポート前のデータのフィルター処理 (Excel 用 MDS アドイン)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] で、Excel にエクスポートするデータのサイズまたはスコープを制限するには、データをフィルター処理します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
### <a name="to-filter-data-before-exporting"></a>エクスポート前のデータをフィルター処理するには  
  
1.  Excel を開いて、 **[マスター データ]** タブで MDS リポジトリに接続します。 詳細については、「[MDS リポジトリへの接続 (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md)」を参照してください。  
  
2.  **[マスター データ エクスプローラー]** ペインで、モデルおよびバージョンを選択します。 エンティティの一覧が作成されます。  
  
    -   **[マスター データ エクスプローラー]** ペインが表示されない場合は、 **[接続と読み込み]** グループの **[エクスプローラーの表示]**をクリックします。  
  
    -   **[マスター データ エクスプローラー]** ペインが無効になっている場合は、既存のシートに MDS によって管理されるデータが既に含まれています。 ペインを有効にするには、新しいワークシートを開きます。  
  
3.  **[マスター データ エクスプローラー]** ペインのエンティティの一覧で、フィルター処理するエンティティをクリックします。  
  
4.  リボンの **[接続と読み込み]** グループで、 **[フィルター]**をクリックします。  
  
5.  **[フィルター]** ダイアログ ボックスで、表示する属性 (列) を選択して列の順序を設定し、必要に応じて、返される行が少なくなるようにデータをフィルター処理します。 **[概要]** ペインで、返されるデータ量を確認します。 詳細については、「[[フィルター] ダイアログ ボックス (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)」を参照してください。  
  
6.  **[データの読み込み]**をクリックします。 シートに MDS によって管理されるデータが入力されます。  
  
    > [!NOTE]  
    >  -   最初の 100 万個のメンバーだけが Excel に読み込まれます。  
    > -   制約リスト (ドメイン ベースの属性) の列では、既定で最初の 25,000 個の値だけが読み込まれます。  
  
## <a name="next-steps"></a>次の手順  
 [Excel からマスター データ サービスにデータをインポートする (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>参照  
 [概要: Excel へのデータのエクスポート (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [[フィルター] ダイアログ ボックス (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [列の並べ替え (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/reorder-columns-mds-add-in-for-excel.md)  
  
  