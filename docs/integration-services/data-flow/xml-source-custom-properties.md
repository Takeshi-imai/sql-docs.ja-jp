---
title: "XML ソースのカスタム プロパティ | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb29b28c-3159-41ec-b3d7-fce5b2f2be55
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5a56fae7a047bbb49f955b36a05b068eec23195a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="xml-source-custom-properties"></a>XML 入力元のカスタム プロパティ
  XML ソースには、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、XML ソースのカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer|XML データへのアクセスに使用するモード。|  
|UseInlineSchema|ブール値|XML ソース内のインライン スキーマ定義を使用するかどうかを示す値。 このプロパティの既定値は **False**です。|  
|XMLData|String|XML データを取得するファイルまたは変数。<br /><br /> このプロパティの値は、プロパティ式を使用して指定することができます。|  
|XMLSchemaDefinition|String|スキーマ定義ファイル (.xsd) のパスおよびファイル名。<br /><br /> このプロパティの値は、プロパティ式を使用して指定することができます。|  
  
 次の表は、XML ソースの出力のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|Description|  
|-------------------|---------------|-----------------|  
|RowsetID|String|出力に関連付けられた行セットを識別する値。|  
  
 XML ソースの出力列には、カスタム プロパティがありません。  
  
 詳細については、「 [XML ソース](../../integration-services/data-flow/xml-source.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
