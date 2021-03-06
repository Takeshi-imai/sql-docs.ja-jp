---
title: "複数のファクト テーブルを使用してパーティション ソースの変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- fact tables [Analysis Services]
- partitions [Analysis Services], fact tables
ms.assetid: 5508312f-8e46-4802-9362-6688ca03d098
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ded060a7f5451e7bf0907f40da78d9fb9e95b8dc
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="change-a-partition-source-to-use-a-different-fact-table"></a>別のファクト テーブルを使用するためのパーティション ソースの変更
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
キューブのパーティションを作成する場合、複数のファクト テーブルを使用するように選択できます。 複数のテーブルは、単一のデータ ソース ビュー、複数のデータ ソース ビュー、または複数のデータ ソースから得たものである場合があります。 データ ソース ビューには、複数のデータ ソースから得た複数のテーブルが含まれている場合もあります。  
  
 キューブのパーティションのファクト テーブルとディメンションはすべて、キューブのファクト テーブルおよびディメンションと同一構造であることが必要です。 たとえば、同一構造の複数のファクト テーブルに、異なる年度のデータや異なる製品ラインのデータを格納できます。  
  
 ファクト テーブルはパーティション ウィザードの **[基になる情報の指定]** で指定します。 このページの **[検索対象]**の横の [パーティション ソース] で、検索するデータ ソースまたはデータ ソース ビューを指定します。 次に、 **[テーブルの検索]**をクリックし、 **[使用できるテーブル]**で使用するテーブルを選択します。  
  
 複数のファクト テーブルを使用する場合は、パーティション間でデータが重複していないことを確認してください。 たとえば、あるファクト テーブルに 2012 年のトランザクションのみが含まれ、別のファクト テーブルに 2013 年のトランザクションのみが含まれる場合、これらのテーブルに含まれるデータは重複しません。 同様に、異なる製品ラインや異なる地域のファクト テーブルにも重複データは含まれません。  
  
 重複データを含む複数のファクト テーブルを使用することは可能ですが、お勧めはできません。 使用する場合は、パーティション内でフィルターを使用して、あるパーティションで使用されるデータが、別のパーティションで使用されないようにする必要があります。 詳細については、「[ローカル パーティションの作成と管理 (Analysis Services)](../../analysis-services/multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [作成し、ローカル パーティション &#40; を管理Analysis Services &#41;](../../analysis-services/multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)  
  
  
