---
title: "プロパティ (ADO) の準備 |Microsoft ドキュメント"
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
- Command15::Prepared
helpviewer_keywords:
- Prepared property [ADO]
ms.assetid: 11ca8825-765e-4bb4-a6ce-3f6564ad8755
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c5b45f14d0513dfda61688dc664affbf760c8598
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="prepared-property-ado"></a>準備済みのプロパティ (ADO)
コンパイル済みのバージョンを保存するかどうかを示す、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)実行前にします。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**ブール**値に設定**True**コマンドを準備することを示します。  
  
## <a name="remarks"></a>解説  
 使用して、 **Prepared**プロパティで指定されたクエリの準備 (またはコンパイル済み) のバージョンを保存するプロバイダーが、 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)前に、プロパティ、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトの最初に実行します。 コマンドの最初の実行が低下する可能性がありますが、プロバイダーはパフォーマンスの向上と、その後の実行のコンパイル済みのバージョンのコマンドを使用して、プロバイダーは、コマンドをコンパイルするとします。  
  
 プロパティが場合**False**、プロバイダーが実行されます、**コマンド**コンパイル済みのバージョンを作成せずに直接オブジェクト。  
  
 このプロパティ設定されている場合に、エラーを返す可能性がありますが、プロバイダーがコマンドの準備をサポートしていない場合**True**です。 コマンドとセットを準備する要求を無視プロバイダーでエラーが返されない場合、 **Prepared**プロパティを**False**です。  
  
## <a name="applies-to"></a>適用対象  
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [準備済みのプロパティの例 (VB)](../../../ado/reference/ado-api/prepared-property-example-vb.md)   
 [Prepared プロパティの例 (VC++)](../../../ado/reference/ado-api/prepared-property-example-vc.md)   
