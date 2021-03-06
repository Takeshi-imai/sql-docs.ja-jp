---
title: "メンバーのコレクション (ADO MD) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Level::Members
- Members
- Position::Members
helpviewer_keywords:
- Members collection [ADO MD]
ms.assetid: 3a647cde-efdc-4394-b1b9-8cbb1b9d689f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 087809ddb783b323a094a509aedd4c5b88005764
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="members-collection-ado-md"></a>メンバーのコレクション (ADO MD)
含まれています、[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)レベル、または軸に沿った位置からのオブジェクト。  
  
## <a name="remarks"></a>解説  
 A**メンバー**は次の種類のメンバーを格納するコレクションを使用します。  
  
-   キューブ内のレベルを構成するメンバー。 含まれる、**メンバー**のコレクション、[レベル](../../../ado/reference/ado-md-api/level-object-ado-md.md)オブジェクト。 サンプルを使用するなど、[マルチ ディメンション スキーマの概要とデータ](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)国のレベルの 4 つのメンバーは、カナダ、アメリカ合衆国、英国、およびドイツです。  
  
-   階層内で特定のメンバーの子であるメンバー。 これらのメンバーは、によって返される、[子](../../../ado/reference/ado-md-api/children-property-ado-md.md)、親**メンバー**オブジェクト。 たとえば、もう一度同じサンプルを使用して、Canada メンバーの 2 つの子はカナダ東部およびカナダ西部です。  
  
-   軸に沿った特定の位置を定義するメンバー、[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)です。 セル セットを使用して[多次元データを扱う](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)バレンタインおよびシアトル例として、x 軸の最初の位置の 2 つのメンバーは、します。 これらのメンバーに含まれる、**メンバー**のコレクション、[位置](../../../ado/reference/ado-md-api/position-object-ado-md.md)オブジェクト。  
  
 **メンバー**標準 ADO コレクションです。 プロパティとメソッドのコレクションでは、次の操作を実行できます。  
  
-   使用して、コレクション内のオブジェクトの数を取得、[カウント](../../../ado/reference/ado-api/count-property-ado.md)プロパティです。  
  
-   既定値を使用してコレクションからオブジェクトを返す[項目](../../../ado/reference/ado-api/item-property-ado.md)プロパティです。  
  
-   使用してプロバイダーから、コレクション内のオブジェクトを更新、[更新](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドです。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/members-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [メンバーの例 (VBScript)](../../../ado/reference/ado-md-api/members-example-vbscript.md)   
 [Member オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)
