---
title: "メンバー グループを定義する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member groups [Analysis Services]
- grouping members
- DiscretizationMethod property
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 36110a1967917adda6c06ca0e32d138639e1871e
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="attribute-properties---define-member-groups"></a>属性のプロパティ - メンバー グループの定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
特定の属性に多数のメンバーが存在する場合は、そのメンバーをバケットにグループ化すると、階層内のデータを参照するときに表示されるメンバーの数を減らすことができます。 メンバーをグループ化するバケットの数を指定したり、バケットの名前付けスキーマを設定したりできます。 詳細については、[「属性メンバーのグループ化 (分離)](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md)」を参照してください。  
  
 メンバーをグループ化するには、**DiscretizationMethod** プロパティを設定します。このプロパティには、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の **[プロパティ]** ウィンドウからアクセスできます。  
  
 メンバー グループを作成した場合、ディメンションを処理するまで他のユーザーは変更内容を利用できません。 詳細については、「[多次元モデルの処理 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)」を参照してください。  
  
### <a name="to-create-member-groups"></a>メンバー グループを作成するには  
  
1.  作業するディメンションを開きます。 既定では、 **[ディメンション構造]** タブが表示されます。  
  
2.  **[属性]**で、グループ化するメンバーの属性を右クリックし、 **[プロパティ]**をクリックします。  
  
3.  **[DiscretizationMethod]** の横のドロップダウン リストから、メンバーのグループ化方法を選択します。 **[DiscretizationMethod]** の設定の詳細については、「[属性メンバーのグループ化 (分離)](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md)」を参照してください。  
  
  
