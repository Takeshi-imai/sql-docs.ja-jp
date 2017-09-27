---
title: "エンティティを作成する (マスター データ サービス) | Microsoft Docs"
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
helpviewer_keywords:
- entities [Master Data Services], creating
- creating entities [Master Data Services]
ms.assetid: d9a6a51e-7b53-4785-a118-3baeb7ca2d48
caps.latest.revision: 9
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 9b081ac7c85401a43533863f2495dad9032c7ba0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="create-an-entity-master-data-services"></a>エンティティを作成する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でエンティティを作成して、メンバーおよびその属性を含めます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
-   モデルが存在する必要があります。 詳細については、「[モデルを作成する (マスター データ サービス)](../master-data-services/create-a-model-master-data-services.md)」を参照してください。  
  
### <a name="to-create-an-entity"></a>エンティティを作成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]**をクリックします。  
  
2.  **[Manage Model]** (モデルの管理) ページで、エンティティを作成するモデルをグリッドから選択し、 **[エンティティ]**をクリックします。  
  
3.  **[Manage Entity]** (管理エンティティ) ページで **[追加]**をクリックします。  
  
4.  **[名前]** ボックスに、エンティティの名前を入力します。  
  
5.  必要に応じて、 **[説明]** フィールドに、エンティティの説明を入力します。  
  
6.  必要に応じて、 **[ステージング テーブルの名前]** ボックスに、ステージング テーブルの名前を入力します。  
  
     このフィールドに名前を入力しない場合は、エンティティ名が使用されます。  
  
    > [!TIP]  
    >  ステージング テーブルの名前の一部にはモデル名を使用します。たとえば、 *Modelname_Entityname*のようにします。 こうすることで、データベースからテーブルを見つけやすくなります。 ステージング テーブルの詳細については、「[概要: テーブルからのデータのインポート (マスター データ サービス)](../master-data-services/overview-importing-data-from-tables-master-data-services.md)」を参照してください。  
  
7.  **[トランザクション ログの種類]** フィールドで、ドロップダウン リストからトランザクション ログの種類を選択します。  
  
     詳細については、「[エンティティのトランザクション ログの種類の変更 (マスター データ サービス )](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)」を参照してください。  
  
8.  省略可。 **[コード値を自動的に作成する]** チェック ボックスをオンにします。 詳細については、「[コードの自動作成 (マスター データ サービス)](../master-data-services/automatic-code-creation-master-data-services.md)」を参照してください。  
  
9. 省略可。 **[データ圧縮を有効にする]** チェック ボックスをオンします。 既定では、行の圧縮は有効になっています。 詳細については、「 [Data Compression](../relational-databases/data-compression/data-compression.md)」を参照してください。  
  
10. **[保存]**をクリックします。  
  
## <a name="grid-columns"></a>グリッド列  
 作成されたエンティティごとに、13 列の行がグリッドに追加されます。 その列を次に示します。  
  
|[名前]|[説明]|  
|----------|-----------------|  
|[状態]|エンティティの状態。 **[保存]** をクリックすると、エンティティが更新中であることを示す次のイメージが表示されます。<br /><br /> ![更新中状態のアイコン](../master-data-services/media/mds-statusicon-updating.png "更新中状態のアイコン")<br /><br /> エンティティの作成または編集中にエラーが発生すると、次のイメージが表示されます。<br /><br /> ![エラー状態のアイコン](../master-data-services/media/mds-statusicon-error.png "エラー状態のアイコン")<br /><br /> 適切な状態の場合は、次のイメージが表示されます。<br /><br /> ![適切な状態のアイコン](../master-data-services/media/mds-statusicon-ok.png "適切な状態のアイコン")|  
|名前|エンティティ名。|  
|[説明]|エンティティの説明。|  
|ステージング テーブル|データを格納するために使用されるテーブルのプレフィックス名。|  
|[トランザクション ログの種類]|エンティティのトランザクション ログの種類。|  
|コードの自動作成|コードの自動作成が有効かどうかを示します。|  
|Data Compression|エンティティに対してデータ圧縮が有効かどうかを示します。|  
|同期ターゲット|エンティティが同期関係のターゲットかどうかを示します。|  
|階層が有効|明示的階層に対してエンティティが有効かどうかを示します。 エンティティに対して少なくとも 1 つの明示的階層が作成されている場合は、[はい] になります。|  
|[作成者]|エンティティを作成したユーザーの名前。|  
|作成日時|エンティティが作成された日付と時刻。|  
|更新者|エンティティを最後に更新したユーザーの名前。|  
|更新日時|エンティティが最後に更新された日時。|  
  
## <a name="next-steps"></a>次の手順  
  
-   [テキスト属性を作成する (マスター データ サービス)](../master-data-services/create-a-text-attribute-master-data-services.md)  
  
-   [ドメイン ベースの属性を作成する (マスター データ サービス)](../master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
-   [ファイル属性を作成する (マスター データ サービス)](../master-data-services/create-a-file-attribute-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [エンティティ (マスター データ サービス)](../master-data-services/entities-master-data-services.md)   
 [明示的階層 (マスター データ サービス)](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [エンティティを編集する &#40;マスター データ サービス&#41;](../master-data-services/edit-an-entity-master-data-services.md)   
 [エンティティを削除する (マスター データ サービス)](../master-data-services/delete-an-entity-master-data-services.md)  
  
  