---
title: "エンティティ (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 04/01/2016
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
- entities [Master Data Services], about entities
- entities [Master Data Services]
ms.assetid: 0af057d5-6b73-472b-99eb-9f5eb61a9b5b
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ee34c6829e0faed75a375727850c7caf9034b7d4
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="entities-master-data-services"></a>エンティティ (Master Data Services)
  エンティティは、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] モデルに含まれるオブジェクトです。 各エンティティには、管理対象のマスター データの行であるメンバーが含まれています。  
  
## <a name="how-many-entities-are-appropriate"></a>適切なエンティティ数  
 モデルには、管理を希望する数だけエンティティを含めることができます。 各エンティティでは、類似するデータをグループ化する必要があります。 たとえば、組織のすべてのアカウントのエンティティや従業員のマスター リストのエンティティなどが考えられます。  
  
 一般に、ビジネスにとって重要な 1 つ以上の中心となるエンティティが存在し、そのエンティティにモデル内の他のオブジェクトを関連付けます。 たとえば、Product モデルであれば、Product という中心となるエンティティを作成し、その Product エンティティに Subcategory や Category というエンティティを関連付けます。 ただし、中心となるエンティティの作成は必須ではありません。 要件に応じて、重要性が同等と見なせる複数のエンティティを作成することもできます。  
  
## <a name="how-entities-relate-to-other-model-objects"></a>エンティティと他のモデル オブジェクトの関連付け  
 エンティティはマスター データを含むテーブルと考えることができます。行がメンバーを表し、列が属性を表します。  
  
 ![テーブルとして表されたマスター データ サービス エンティティ](../master-data-services/media/mds-conc-entity-table.gif "テーブルとして表されたマスター データ サービス エンティティ")  
  
 管理対象のマスター データのリストをエンティティに設定します。  
  
 複数のエンティティを使用して派生階層を構築できます。派生階層とは、複数のエンティティに基づくレベルベースの階層です。 詳細については、「 [派生階層 (マスター データ サービス)](../master-data-services/derived-hierarchies-master-data-services.md)」を参照してください。  
  
 また、場合によっては、エンティティに明示的階層 (単一のエンティティに基づく不規則な構造) とコレクション (メンバーのサブセットの 1 回限りの組み合わせ) を含めることも可能です。 詳細については、「[明示的階層 (マスター データ サービス)](../master-data-services/explicit-hierarchies-master-data-services.md)」および「[コレクション (マスター データ サービス)](../master-data-services/collections-master-data-services.md)」を参照してください。  
  
## <a name="using-entities-as-constrained-lists"></a>制約リストとしてのエンティティの使用  
 ユーザーはエンティティ内のメンバーに属性を割り当てるときに、値の制約リストから属性を選択することができます。 これを行うには、エンティティを使用して属性用に値のリストを設定します。 これを、ドメイン ベースの属性といいます。 詳細については、「[ドメインベースの属性 (マスター データ サービス)](../master-data-services/domain-based-attributes-master-data-services.md)」を参照してください。  
  
## <a name="base-entities"></a>ベース エンティティ  
 ベース エンティティは、モデル内でオブジェクト間を移動するときのユーザーの開始点です。 ユーザーが **[エクスプローラー]** 機能領域を開いてメニュー バーの **[エクスプローラー]** をクリックすると、ベース エンティティによって画面のレイアウトが決定されます。 エンティティをベース エンティティに指定するには、 **[システム管理]** 機能領域に移動します。 **[モデル ビュー]** ページで、右側のツリー コントロールのエンティティを左側のツリー コントロールのモデルの名前にドラッグします。  
  
## <a name="entity-security"></a>エンティティのセキュリティ  
 関連するモデル オブジェクトを含む、エンティティに対する権限をユーザーに付与できます。 詳細については、「[エンティティ権限 (マスター データ サービス)](../master-data-services/entity-permissions-master-data-services.md)」を参照してください。  
  
## <a name="entity-examples"></a>エンティティの例  
 次の例では、エンティティに Name、Code、Subcategory、StandardCost、ListPrice、および FilePhoto という属性があることを示しています。 これらの属性はメンバーを表します。 各メンバーは、属性値の 1 行で表されます。  
  
 ![自転車製品エンティティ テーブル](../master-data-services/media/mds-conc-entity-table-w-data.gif "自転車製品エンティティ テーブル")  
  
 次の例では、Product エンティティが中心となるエンティティです。 Subcategory エンティティは、Product エンティティのドメイン ベースの属性です。 Category エンティティは、Subcategory エンティティのドメイン ベースの属性です。 StandardCost および ListPrice は、Product エンティティの自由形式属性で、FilePhoto は Product エンティティのファイル属性です。  
  
 ![製品エンティティ ツリー構造](../master-data-services/media/mds-conc-entity-ui.gif "製品エンティティ ツリー構造")  
  
> [!NOTE]  
>  これは、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ユーザー インターフェイスに基づく例です。 階層ツリー構造は、エンティティとドメイン ベースの属性間のリレーションシップを示します。 これは、リレーションシップを示すもので、重要度を表すものではありません。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|新規エンティティを作成する。|[エンティティを作成する (マスター データ サービス)](../master-data-services/create-an-entity-master-data-services.md)|  
|既存のエンティティの名前を変更する。|[エンティティを編集する (マスター データ サービス)](../master-data-services/edit-an-entity-master-data-services.md)|  
|既存のエンティティを削除する。|[エンティティを削除する (マスター データ サービス)](../master-data-services/delete-an-entity-master-data-services.md)|  
|エンティティに権限を割り当てる。|[モデル オブジェクト権限を割り当てる (マスター データ サービス)](../master-data-services/assign-model-object-permissions-master-data-services.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [モデル (マスター データ サービス)](../master-data-services/models-master-data-services.md)  
  
-   [メンバー (マスター データ サービス)](../master-data-services/members-master-data-services.md)  
  
-   [属性 (マスター データ サービス)](../master-data-services/attributes-master-data-services.md)  
  
  
