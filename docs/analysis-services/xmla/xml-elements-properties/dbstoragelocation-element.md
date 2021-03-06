---
title: "DbStorageLocation 要素 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DbStorageLocation element
ms.assetid: 1f448249-103a-479f-ae86-b0017acd0436
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bf2bc5ab8c0419260049d8e588fd491a50099135
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="dbstoragelocation-element"></a>DbStorageLocation 要素
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]フォルダーを指定場所[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]を作成し、すべてのデータベース データとメタデータ ファイルを管理します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Database>  
...  
   <ddl100_100:DbStorageLocation>...</ddl100_100:DbStorageLocation>  
...  
</Database>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|""|  
|基数|0-1: 1 回だけ発生する可能性が省略可能な要素です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[データベース]](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **DbStorageLocation** データベース プロパティには、既存の UNC フォルダー パスまたは空の文字列を設定する必要があります。 空の文字列は、既定のサーバー データ フォルダーを示します。 実行するときに、エラーが発生する、フォルダーが存在しない場合、**作成**、**アタッチ**、または**Alter**コマンド。  
  
 さらに、 **DbStorageLocation**サーバー データ フォルダーまたはそのサブフォルダーを指すデータベース プロパティを設定することはできません。 実行するときに、エラーが発生する場合は、サーバー データ フォルダーまたはそのサブフォルダーを指した、**作成**、**アタッチ**、または**Alter**コマンド。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Analysis Services データベースのインポートとデタッチ](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  
