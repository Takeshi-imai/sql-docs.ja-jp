---
title: "データの結合 (Excel 用 MDS アドイン) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
caps.latest.revision: 6
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 8a8ee3e56e5b8ed42bca6b30192c3b14686d1240
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="combine-data-mds-add-in-for-excel"></a>データの結合 (Excel 用 MDS アドイン)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]で、パブリッシュする前にデータを比較する場合は、2 つのワークシートのデータを結合します。 この手順では、2 つのワークシートのデータを 1 つに結合します。 これにより、さらに比較を実行して、MDS リポジトリにパブリッシュするデータを決定することができます。  
  
## <a name="prerequisites"></a>前提条件  
  
-   MDS によって管理されるデータが含まれているワークシートが必要です。 詳細については、「 [マスター データ サービスからデータを Excel にエクスポート](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)」を参照してください。  
  
-   MDS によって管理されるデータに結合するデータが含まれているワークシートが必要です。 このシートには、ヘッダー行が必要です。  
  
### <a name="to-combine-non-managed-data-into-an-mds-managed-sheet"></a>MDS によって管理されるシートに管理されないデータを結合するには  
  
1.  MDS によって管理されるデータを含むシートで、 **[パブリッシュと検証]** グループの **[データの結合]**をクリックします。  
  
2.  **[データの結合]** ダイアログ ボックスで、 **[MDS データと結合する範囲]** ボックスの横にあるアイコンをクリックします。 ダイアログ ボックスが縮小されます。  
  
3.  結合するデータを含むシートをクリックします。  
  
4.  シート上の結合するすべてのセル (ヘッダー行を含む) を強調表示します。  
  
5.  **[データの結合]** ダイアログ ボックスで、アイコンをクリックします。 ダイアログ ボックスが拡張されます。  
  
6.  MDS エンティティに一覧表示される列について、 **[対応する列]**の下にある列を選択します。 すべての MDS 列に対応する列が必要なわけではありません。  
  
7.  **[結合]**をクリックします。 MDS からのデータか外部ソースからのデータかを示す **[SOURCE]** 列が表示されます。  
  
## <a name="next-steps"></a>次の手順  
  
-   MDS によって管理されるデータと外部データの類似性を見つける場合は、「[類似データの照合 &#40;Excel 用 MDS アドイン&#41;](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [概要: Excel へのデータのエクスポート (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Excel 用 MDS アドインでのデータ品質照合](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
  