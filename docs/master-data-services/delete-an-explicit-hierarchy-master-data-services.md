---
title: "明示的階層を削除する (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- explicit hierarchies, deleting
- deleting explicit hierarchies [Master Data Services]
ms.assetid: 4ce177b0-9884-47a2-9cea-212e845dd762
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 97194db5e215df90d4260cb7f96d55c7bc008fa0
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="delete-an-explicit-hierarchy-master-data-services"></a>明示的階層を削除する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、不要になった明示的階層を削除します。  
  
> [!WARNING]  
>  明示的階層を削除すると、階層内の統合メンバーもすべて削除されます。 エンティティに対する明示的階層を削除すると、エンティティのコレクションもすべて削除され、明示的階層およびコレクションに対してエンティティが無効になります。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
### <a name="to-delete-an-explicit-hierarchy"></a>明示的階層を削除するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  **[モデルの管理]** ページでグリッドからモデルを選択し、 **[エンティティ]**をクリックします。  
  
3.  **[エンティティの管理]** ページで、削除する明示的階層を含むエンティティの行をグリッドから選択します。  
  
4.  **[明示的階層]**をクリックします。  
  
5.  **[明示的階層の管理]** ページで、削除する明示的階層をクリックします。  
  
6.  **[編集]**をクリックします。  
  
7.  確認のダイアログ ボックスで **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [明示的階層を作成する (マスター データ サービス)](../master-data-services/create-an-explicit-hierarchy-master-data-services.md)   
 [明示的階層 (マスター データ サービス)](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
