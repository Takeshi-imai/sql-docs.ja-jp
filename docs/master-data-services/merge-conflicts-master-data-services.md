---
title: "競合のマージ (マスター データ サービス) | Microsoft Docs"
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
ms.assetid: 797219ad-5109-4666-94d3-dd1d59440a33
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 18254780cba8b4d0b61116d4f148f3feb656c30a
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="merge-conflicts-master-data-services"></a>競合のマージ (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でパブリッシュしようとしているデータが他のユーザーによって変更されている場合、パブリッシュ操作は競合エラーで失敗します。 このエラーを解決するには、競合のマージを実行した後で変更を再パブリッシュします。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
-   更新するエンティティのリーフ モデル オブジェクトに対する更新権限が最低限必要です。  
  
### <a name="to-merge-conflicts"></a>競合をマージするには  
  
1.  **[エクスプローラー]** ページで、メンバー属性を更新します。  
  
2.  同じメンバー属性が別のユーザーによって変更されている場合、 **[Merge Conflicts]** (競合のマージ) ダイアログが表示されます。  
  
3.  **[Merge Conflicts]** (競合のマージ) ダイアログでは、次の操作を行うことができます。  
  
    -   保留中の変更を元に戻し、サーバーから最新のバージョンを再び読み込む場合は、 **[最新]** を選択し、 **[適用]** をクリックします。  
  
    -   ワークシートの元のバージョンを適用する場合は、 **[オリジナル]** を選択し、 **[適用]** をクリックします。  
  
    -   既存のローカルの変更を保持する場合は、 **[このユーザーの変更]** を選択し、 **[適用]** をクリックします。  
  
4.  **[適用]**をクリックした後、さらに変更を加えて、再びパブリッシュすることができます。 または、 **[キャンセル]** をクリックして更新を取り消し、サーバーから最新のバージョンを再び読み込むことができます。  
  
## <a name="see-also"></a>参照  
 [メンバー (マスター データ サービス)](../master-data-services/members-master-data-services.md)  
  
  
