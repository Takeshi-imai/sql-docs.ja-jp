---
title: "Error 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Error Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.error
- http://schemas.microsoft.com/analysisservices/2003/engine#Error
- urn:schemas-microsoft-com:xml-analysis#Error
helpviewer_keywords: Error element
ms.assetid: add670cb-cab2-42be-91a3-d0c385f29d16
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e0d513dc324fe6f1efc857a03bf231d06481c10c
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="error-element-xmla"></a>Error 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]インスタンスによって返されるエラーについての情報を含む[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Message>  
   <Error   
      ErrorCode="unsignedint"   
      Severity="string"   
      Description="string"  
      Source="string"  
      HelpFile="string"  
   />  
</Message>  
<!-- or -->  
<Cell><!-- or row -->  
   <!-- A child element -->  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception"  
         < ErrorCode>...</ErrorCode>  
         < Description>...</Description>  
         < Source>...</Source>  
         < HelpFile>...</HelpFile>  
      </Error>  
   <!-- /A child element -- >  
</Cell>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[メッセージ](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
|子要素|次の表を参照してください。|  
  
|Ancestor|子要素|  
|--------------|--------------------|  
|[メッセージ](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|なし|  
|[セル](../../../analysis-services/xmla/xml-elements-properties/cell-element-mddataset-xmla.md)、[行](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|[説明](../../../analysis-services/xmla/xml-elements-properties/description-element-xmla.md)、 [ErrorCode](../../../analysis-services/xmla/xml-elements-properties/errorcode-element-xmla.md)、 [HelpFile](../../../analysis-services/xmla/xml-elements-properties/helpfile-element-xmla.md)、[ソース](../../../analysis-services/xmla/xml-elements-properties/source-element-error-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|属性|Description|  
|---------------|-----------------|  
|ErrorCode|必要な**UnsignedInt**属性 (される場合にのみ**メッセージ**親要素です)。エラーのリターン コード (数値) を含みます。|  
|Severity|省略可能な**文字列**属性 (される場合にのみ**メッセージ**親要素です)。エラーの重大度レベルを格納します。|  
|Description|省略可能な**文字列**属性 (される場合にのみ**メッセージ**親要素です)。エラーについての説明テキストを含みます。|  
|Source|省略可能な**文字列**属性 (される場合にのみ**メッセージ**親要素です)。エラーを生成したコンポーネントの名前を含みます。|  
|HelpFile|省略可能な**文字列**属性 (される場合にのみ**メッセージ**親要素です)。エラーについて説明しているヘルプ ファイルまたはトピックのパス、あるいは URL を含みます。|  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [Warning 要素 &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/warning-element-xmla.md)   
 [プロパティ &#40;です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
