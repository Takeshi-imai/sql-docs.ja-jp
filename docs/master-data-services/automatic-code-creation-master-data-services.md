---
title: "コードの自動作成 (Master Data Services) | Microsoft Docs"
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
ms.assetid: 9adbd5e1-f28c-4fb5-afa7-082de2831f3e
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 71f49623abe25581d9bdf5e53f0a208384b2aca7
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="automatic-code-creation-master-data-services"></a>コードの自動作成 (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、Code 属性の数値または他の数値属性の数値を自動的に生成できます。 コードを自動生成するときは、コードに他の値を入力してもかまいません。正確には、初期値が自動的に設定されます。  
  
## <a name="generating-code-values"></a>コード値の生成  
 管理者は、関連付けられているエンティティのプロパティを編集することによって、Code 属性の値の自動生成を構成できます。 初期値を指定でき、後続の各値は 1 ずつ増分されます。  
  
 いずれかのツールで、またはステージング処理を使用してコード値を MDS に入力するとき、コード値をブランクのままにすると、コード値が自動的に生成されます。 または、自分で選択したコード値を指定することもできます。  
  
## <a name="generating-other-attribute-values"></a>他の属性値の生成  
 管理者は、ビジネス ルールを作成することによって、Code 以外の属性値を自動的に生成できます。 初期値を指定できるだけでなく、後続の各値での増分値も指定できます。  
  
 いずれかのツールで、またはステージング処理を使用して属性値を MDS に入力するとき、属性値をブランクのままにできます。 ビジネス ルールが適用されると、既存の最高の値に基づいて値が増分されます。 たとえば、ルールが "1 から開始して 4 ずつ増加する生成値に対する既定の属性" であり、属性の現在最も高い値が 700 である場合、追加される次のメンバーの値は 704 になります。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|Code 属性の値を自動的に生成します。|[Code 属性の値の自動生成 (マスター データ サービス)](../master-data-services/automatically-generate-code-attribute-values-master-data-services.md)|  
|他の属性の値を自動的に生成します。|[Code 以外の属性の値の自動生成 (マスター データ サービス)](../master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [マスター データ サービスの概要 (MDS)](../master-data-services/master-data-services-overview-mds.md)  
  
-   [ビジネス ルール (マスター データ サービス)](../master-data-services/business-rules-master-data-services.md)  
  
-   [エンティティ (マスター データ サービス)](../master-data-services/entities-master-data-services.md)  
  
  
