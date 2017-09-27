---
title: "モデルの配置パッケージの編集 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b0fdb7d-83dd-4392-9011-4ae642c471f1
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: a5b5a850ad5f21670776629c4bc85c5d82b587d1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="edit-a-model-deployment-package"></a>モデルの配置パッケージの編集
  このトピックでは、モデル全体ではなく、モデルの選択した部分を MDS に配置する方法について説明します。 これを行うには、モデル パッケージ エディターを使用して MDS モデル パッケージを編集します。  
  
 モデル パッケージ エディター ウィザードを使用すると、MDS パッケージに含めるモデル内の特定のエンティティ、派生階層、サブスクリプション ビュー、およびビジネス ルールを選択して、後で配置することができます。 配置しないモデルの部分は除外できます。 エンティティを選択すると、そのエンティティの依存オブジェクトもすべて自動的に選択されます。  
  
 モデル パッケージ エディターを使用して、MDSModelDeploy ツール (オブジェクトとデータを含むパッケージ ファイルを作成します) またはモデル配置ウィザード (モデル構造のみを含むファイルを作成します) で作成したパッケージ ファイル内のモデルの部分を選択します。 パッケージ内のモデルを編集したら、MDSModelDeploy ツールを使用してオブジェクトとデータを配置するか、モデル配置ウィザードを使用してモデル構造のみを配置します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
-   モデル パッケージを編集するには、そのモデル パッケージが存在する必要があります。 詳細については、「[モデルの配置 (マスター データ サービス)](../master-data-services/deploying-models-master-data-services.md)」と「[ウィザードを使用したモデルの配置パッケージの作成](../master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)」、または「[MDSModelDeploy を使用したモデルの配置パッケージの作成](../master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)」を参照してください。  
  
### <a name="to-edit-a-model-deployment-package"></a>モデルの配置パッケージを編集するには  
  
1.  MDS サーバーの Windows エクスプ ローラーで、&lt; *ドライブ*&gt;:\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration に移動します。  
  
2.  ModelPackageEditor.exe を実行します。  
  
3.  モデル パッケージ エディター ウィザードで、 **[参照]**をクリックしてパッケージが格納されているフォルダーに移動し、パッケージを選択して **[開く]**をクリックします。 **[次へ]**をクリックします。  
  
4.  配置するエンティティ、派生階層、サブスクリプション ビュー、またはビジネス ルールを選択します。 配置しない項目は選択を解除します。 **[次へ]**をクリックします。  
  
5.  配置する選択項目の一覧を確認します。 変更するには、 **[戻る]** をクリックして手順 4 を繰り返します。  
  
6.  **[参照]**をクリックし、部分的なパッケージを保存するフォルダーに移動して、部分的なパッケージのファイル名を入力します (.pkg 拡張子を付けます)。 **[保存]**をクリックします。  
  
7.  **[完了]**をクリックします。  
  
## <a name="next-steps"></a>次の手順  
  
-   [ウィザードを使用したモデルの配置パッケージの展開](../master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)  
  
-   [MDSModelDeploy を使用したモデルの配置パッケージの配置](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  