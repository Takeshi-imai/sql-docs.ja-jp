---
title: "エンティティの同期関係の作成と実行 (マスター データ サービス) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0ddceab4-d2b3-4bc1-bd9c-6b852200b414
caps.latest.revision: 6
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 14bc03c2c8c462895102d6c34c62cf23724c706f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="create-and-execute-an-entity-sync-relationship-master-data-services"></a>エンティティの同期関係の作成と実行 (マスター データ サービス)
  エンティティ同期は、エンティティのバージョン間での反復可能な一方向の同期です。 異なるモデルの間でエンティティ データを共有する方法を提供します。  
  
## <a name="prerequisites"></a>前提条件  
 エンティティの同期関係を作成するための前提条件を次に示します。  
  
-   [システム管理] 機能領域にアクセスする権限が必要です。 詳細については、「[機能領域権限 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください。  
  
-   ターゲット モデルのモデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
-   少なくとも、ソース エンティティとそのすべての属性およびメンバーに対する読み取りアクセス権が必要です。  
  
 エンティティの同期関係を実行するための前提条件を次に示します。  
  
-   [システム管理] 機能領域にアクセスする権限が必要です。 詳細については、「[機能領域権限 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください。  
  
-   ターゲット モデルのモデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
 エンティティの同期関係を作成するときには、次の点に注意してください。  
  
-   ソース エンティティとターゲット エンティティは、異なるモデルに存在する必要があります。  
  
-   ターゲット エンティティのバージョンの状態をコミットすることはできません。  
  
-   同期関係が確立されると、ターゲットはすぐにソースと同期します。  
  
-   ターゲット エンティティのバージョンを、別の同期関係のソース エンティティのバージョンにすることはできません。  
  
 エンティティの同期関係を実行するときには、次の点に注意してください。  
  
-   リーフ メンバーのみがコピーされます。  
  
-   ドメイン ベースの属性はコピーされません。  
  
-   ソフト削除されたメンバーはコピーされません。  
  
-   同期では、ターゲット エンティティのトランザクション/履歴は生成されません。  
  
 **エンティティの同期関係を作成するには**  
  
1.  マスター データ マネージャーで、 **[システム管理]**をクリックします。  
  
2.  **[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして、 **[エンティティの同期]**をクリックします。  
  
3.  **[エンティティの同期のメンテナンス]** ページで **[追加]**をクリックします。 右側にパネルが表示されます。  
  
4.  ソースの **[モデル]** ボックスの一覧からモデルを選択します。  
  
5.  ソースの **[バージョン]** ボックスの一覧からバージョンを選択します。  
  
6.  ソースの **[エンティティ]** ボックスの一覧からエンティティを選択します。  
  
7.  ターゲットの **[モデル]** ボックスの一覧からモデルを選択します。  
  
8.  ターゲットの **[バージョン]** ボックスの一覧からバージョンを選択します。  
  
9. 既存のエンティティを同期する場合は、 **[既存のエンティティ]** を選択して、[エンティティ] ボックスの一覧からエンティティを選択します。新しいエンティティに同期する場合は、 **[新しいエンティティ]** を選択して、ターゲット エンティティの名前を入力します。  
  
10. **[オンデマンドで同期]**を選択するか、 **[自動同期]** を選択して頻度を設定します。  
  
11. **[保存]**をクリックします。  
  
 **エンティティの同期関係を実行するには**  
  
1.  マスター データ マネージャーで、 **[システム管理]**をクリックします。  
  
2.  **[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして、 **[Entity Sync]**(エンティティの同期) をクリックします。  
  
3.  **[エンティティの同期のメンテナンス]** ページで、グリッド内の同期関係を選択します。  
  
4.  **[実行]**をクリックします。  
  
## <a name="sync-relationship-information"></a>同期関係の情報  
 作成された同期関係ごとに、10 列の行がグリッドに追加されます。 次の表で各列について説明します。  
  
|列|Description|  
|------------|-----------------|  
|[状態]|同期関係の状態。<br /><br /> **[保存]** をクリックするか、同期関係を実行すると、![更新中状態のアイコン](../master-data-services/media/mds-statusicon-updating.png "更新中状態のアイコン") 画像が表示され、同期関係が更新中であることが示されます。<br /><br /> 同期関係の作成中、編集中、または実行中にエラーが発生すると、![エラー状態のアイコン](../master-data-services/media/mds-statusicon-error.png "エラー状態のアイコン") 画像が表示されます。<br /><br /> それ以外の場合は適切な状態であり、![適切な状態のアイコン](../master-data-services/media/mds-statusicon-ok.png "適切な状態のアイコン") が表示されます。|  
|ソース モデル|ソース モデルの名前。|  
|ソース バージョン|ソース バージョンの名前。|  
|ソース エンティティ|ソース エンティティの名前。|  
|ターゲット モデル|ターゲット モデルの名前。|  
|ターゲット バージョン|ターゲット バージョンの名前。|  
|ターゲット エンティティ|ターゲット エンティティの名前。|  
|頻度|同期関係の頻度を指定します。|  
|前回の試行日時|同期の試行が最後に発生した日時が表示されます。|  
|前回の成功日時|同期の試行が最後に成功した日時が表示されます。|  
  
 インデックスをクリックすると、次の情報が表示されます。  
  
-   **前回の試行エラー**: 前回の同期の試行に関するエラー情報が表示されます。  
  
-   **作成者**: 同期を作成したユーザーの名前。  
  
-   **作成日時**: 同期が作成された日時。  
  
-   **更新者**: 同期を最後に更新したユーザーの名前。  
  
-   **更新日時**: 同期が最後に更新された日時。  
  
## <a name="next-steps"></a>次の手順  
 [エンティティの同期関係の編集と削除 (マスター データ サービス)](../master-data-services/edit-and-delete-an-entity-sync-relationship-master-data-services.md)  
  
  