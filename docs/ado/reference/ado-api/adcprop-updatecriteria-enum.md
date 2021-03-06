---
title: ADCPROP_UPDATECRITERIA_ENUM | Microsoft Docs
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
- ADCPROP_UPDATECRITERIA_ENUM
helpviewer_keywords:
- ADCPROP_UPDATECRITERIA_ENUM [ADO]
ms.assetid: 33fd7b65-2ec8-4f62-91a7-630b5dab1aa2
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cf0c00fb7f353171686f57405879b3beb544aa1d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="adcpropupdatecriteriaenum"></a>ADCPROP_UPDATECRITERIA_ENUM
オプティミスティックを持つデータ ソースの行の更新中に競合を検出するために使用できるフィールドを指定します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
 これらの定数を使用して、 **Recordset** "**更新基準**"動的なプロパティで参照されている、 [ADO の動的プロパティのインデックス](../../../ado/reference/ado-api/ado-dynamic-property-index.md)に記載されていると[OLE DB 用の Microsoft カーソル サービス](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)ドキュメント。  
  
|定数|[値]|Description|  
|--------------|-----------|-----------------|  
|**adCriteriaAllCols**|1|データ ソースの行の任意の列が変更された場合は、競合を検出します。|  
|**adCriteriaKey**|0|ソース行のキー列のデータの場合に競合が変更された行が削除されていることを検出します。|  
|**adCriteriaTimeStamp**|3|ソース行のデータのタイムスタンプ場合に競合が変更された後に、行がアクセスされたつまりを検出、**レコード セット**取得されました。|  
|**adCriteriaUpdCols**|2|更新されたフィールドに対応している場合は、データ ソースの列のいずれかの行を競合を検出、 **Recordset**が変更されました。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.AdcPropUpdateCriteria.ALLCOLS|  
|AdoEnums.AdcPropUpdateCriteria.KEY|  
|AdoEnums.AdcPropUpdateCriteria.TIMESTAMP|  
|AdoEnums.AdcPropUpdateCriteria.UPDCOLS|
