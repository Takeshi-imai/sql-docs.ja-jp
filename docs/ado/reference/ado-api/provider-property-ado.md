---
title: "プロバイダーのプロパティ (ADO) |Microsoft ドキュメント"
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
- Connection15::get_Provider
- Connection15::PutProvider
- Connection15::put_Provider
- Connection15::GetProvider
- Connection15::Provider
helpviewer_keywords:
- Provider property [ADO]
ms.assetid: 0ff70e72-0061-4ffc-90fb-e3ea23129bb2
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 40cf90e63ac27fd6d6b088a4405db3e44d3c5b65
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="provider-property-ado"></a>プロバイダーのプロパティ (ADO)
プロバイダーの名前を示す、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**文字列**プロバイダー名を示す値。  
  
## <a name="remarks"></a>解説  
 使用して、**プロバイダー**プロパティを設定または接続のプロバイダーの名前を取得します。 内容でこのプロパティを設定することできますも、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティまたは*ConnectionString*の引数、[開く](../../../ado/reference/ado-api/open-method-ado-connection.md)メソッドですただし、プロバイダーを指定します。呼び出し中に複数の場所で、**開く**メソッドは、予期しない結果を持つことができます。 プロパティは既定 MSDASQL にプロバイダーが指定されていない場合 ([Microsoft OLE DB Provider for ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md))。  
  
 **プロバイダー**プロパティが読み取り/書き込みが開いているとき、接続が閉じていて、読み取り専用です。 設定は有効になりませんまで開くか、**接続**オブジェクトまたはアクセス、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)のコレクション、**接続**オブジェクト。 設定が有効でない場合は、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [プロバイダーと DefaultDatabase プロパティの例 (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [プロバイダーと DefaultDatabase プロパティの例 (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Microsoft OLE DB Provider for ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)   
 [付録 A: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)
