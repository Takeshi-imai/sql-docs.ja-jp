---
title: "ビジネス ルールの例 (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 01/05/2017
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
ms.assetid: 3974b9be-4b7c-4a37-ab26-1a36ef455744
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e01b4c5141011209f5fdf314711e9cc26595c5f5
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="business-rule-examples-master-data-services"></a>ビジネス ルールの例 (マスター データ サービス)
この記事では、 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]のビジネス ルールの例を示します。 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]のインストールに含まれるサンプル モデルに、これらの例が見つかります。   
  
サンプル モデルを配置する方法の手順については、「[マスター データ サービスのインストールと構成](../master-data-services/master-data-services-installation-and-configuration.md)」を参照してください。  
  
  
## <a name="business-rule-examples"></a>ビジネス ルールの例  
サンプル モデル |Entity  |ビジネス ルール名| Description  
---------|---------|---------|-----------|  
Customer    | Customer   | Person pmt terms| 顧客の既定の支払条件を指定します。          
次のビジネス ルールで、CustomerType 属性値が `is equal` [ルール条件](../master-data-services/business-rule-conditions-master-data-services.md)に一致する場合は、 `defaults to` [ルール アクション](../master-data-services/business-rule-conditions-master-data-services.md) が PaymentTerms 属性に適用されます。 それ以外の場合は、アクションが行われません。  
```  
If  
    CustomerType is equal to 2  
Then  
    PaymentTerms defaults to CASH  
Else  
    None      
```  
  
**--------------------------------------------------**  
  
サンプル モデル  |Entity  |ビジネス ルール名|Description    
---------|---------|---------|---------------  
Customer     | Customer    | Org pmt terms | 組織の既定の支払条件を指定します。         
次のビジネス ルールで、CustomerType 属性値が `is equal` [ルール条件](../master-data-services/business-rule-conditions-master-data-services.md)に一致する場合は、 `defaults to` [ルール アクション](../master-data-services/business-rule-actions-master-data-services.md) が PaymentTerms 属性に適用されます。 それ以外の場合は、アクションが行われません。  
```  
If  
    CustomerType is equal to 1  
Then  
    PaymentTerms defaults to 210Net30  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
サンプル モデル  |Entity  |ビジネス ルール名| Description    
---------|---------|---------|-----------  
Product     |  Product       | DaysToManufacture |社内の製造に対して製造日数の範囲を指定します。          
次のビジネス ルールで、InHouseManufacture 属性値が `is equal` [ルール条件](../master-data-services/business-rule-conditions-master-data-services.md)に一致する場合は、 `must be between` [ルール アクション](../master-data-services/business-rule-actions-master-data-services.md) が DaysToManufacture 属性に適用されます。 それ以外の場合は、アクションが行われません。  
```  
If  
    InHouseManufacture is equal to Y  
Then  
    DaysToManufacture must be between 1 and 10  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
サンプル モデル  |Entity  |ビジネス ルール名|Description    
---------|---------|---------|-------------  
Product     |Product         |Required fields| 製品エンティティ メンバーの必須の属性を指定します。           
次のビジネス ルールで、すべての条件下で `is required` [検証アクション](../master-data-services/business-rule-actions-master-data-services.md) が指定された属性に対して行われます。 属性値は、Null または空白にすることはできません。  
```  
If  
    None  
Then  
    Name is required  
    ProductSubCategory is required  
    Color is required  
    StandardCost is required  
    SafetyStockLevel is required  
    ReorderPoint is required  
    InHouseManufacture is required  
    SellStartDate is required  
    FinishedGoodIndicator is required  
    ProductLine is required  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
サンプル モデル  |Entity  |ビジネス ルール名|Description    
---------|---------|---------|-----------  
Product     | Product        |  Std Cost| 標準的なコストは 0 より大きくする必要があります。        
次のビジネス ルールで、すべての条件下で `must be greater than` [ルール アクション](../master-data-services/business-rule-actions-master-data-services.md) は製品の StandardCost 属性に適用されます。  
```  
If  
    None  
Then  
    StandardCost must be greater than 0  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
サンプル モデル  |Entity  |ビジネス ルール名|Description    
---------|---------|---------|------------  
Product     | Product        | FG MSRP Cost|製品が完成品である場合は、MSRP (メーカー希望小売価格) と販売店コストは 0 より大きくする必要があることを指定します。           
  
次のビジネス ルールで、FinishedGoodIndicator 属性値が `is equal` [ルール条件](../master-data-services/business-rule-conditions-master-data-services.md)に一致する場合は、 `must be greater than` [ルール アクション](../master-data-services/business-rule-actions-master-data-services.md) が MSRP and DealerCost 属性に適用されます。  
```  
If  
    FinishedGoodIndicator is equal to Y  
Then  
    MSRP must be greater than 0  
    DealerCost must be greater than 0  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
サンプル モデル  |Entity  |ビジネス ルール名|Description    
---------|---------|---------|------------  
Product     | Product        |  Default Name| Color 属性と Class 属性の値に基づいて既定の製品名を指定します。 Color 属性値が YLO ではなく、Class 属性が NA ではない場合は、既定の名前は Yellow NA になります。         
次のビジネス ルールで、Color 属性と Class 属性が `is equal` ルール条件に一致しない場合は、 `defaults to` [ルール アクション](../master-data-services/business-rule-actions-master-data-services.md) が Name 属性に適用されます。  
```  
If  
    (Color is equal to YLO AND Class is equal to NA) is not true  
Then  
    Name defaults to Yellow NA  
Else  
    Name defaults to Other  
```  
  
**--------------------------------------------------**  
  
  
**サンプル モデルのビジネス ルールの例を表示するには**  
1. MDS をインストールしてから設定する [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] Web サイトに移動し、 **[システム管理]** ボックスをクリックします。   
Web サイトを設定する手順については、「[マスター データ サービスのインストールと構成](../master-data-services/master-data-services-installation-and-configuration.md)」を参照してください。  
2. 上記の表に一覧されているビジネス ルールを含むサンプル モデルをクリックして、 **[エンティティ]**をクリックします。  
3. 上記の表に一覧されているルールを適用するエンティティをクリックして、 **[ビジネス ルール]**をクリックします。  
4. 表示するビジネス ルールの名前をクリックします。 UI を展開すると、 **If**、 **Then** 、および **Else** ステートメントが表示されます。  
  
## <a name="did-this-article-help-you-were-listening"></a>この記事は役に立ちましたか? フィードバックをお待ちしております。   
どのような情報をお探しでしたか? お探しの情報は見つかりましたか? コンテンツ改善のため、フィードバックをお待ちしています。 [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com) にコメントをお送りください。   
  
  
  
  

