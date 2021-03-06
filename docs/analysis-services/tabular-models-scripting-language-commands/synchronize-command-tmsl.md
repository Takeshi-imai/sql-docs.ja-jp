---
title: "Synchronize コマンド (TMSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a32ff053-f38f-49d7-afdc-e19f59c88135
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b2bd9ea464b69e1b62ada91fbdee23f790080f86
ms.sourcegitcommit: 6b1618aa3b24bf6759b00a820e09c52c4996ca10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="synchronize-command-tmsl"></a>Synchronize コマンド (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Analysis Services データベースを既存の別のデータベースと同期させます。  
  
## <a name="request"></a>要求  
 JSON で受け入れられるプロパティ synchronize コマンドのとおりです。  
  
```  
{   
   "synchronize":{   
      "database":"AdventureWorksDW_Production",  
      "source":"Provider=MSOLAP.7;Data Source=localhost;Integrated Security=SSPI;Initial Catalog=AdventureWorksDW_Dev",  
      "synchronizeSecurity":"copyAll",  
      "applyCompression":true  
   }  
}  
```  
  
 JSON で受け入れられるプロパティ synchronize コマンドのとおりです。  
  
||||  
|-|-|-|  
|**プロパティ**|**[Default]**|**Description**|  
|[データベース]||同期するデータベース オブジェクトの名前。|  
|source||移行元サーバーへの接続に使用する接続文字列。|  
|synchronizeSecurity|skipMembership|ロールや権限など、セキュリティ定義を復元する方法を指定する列挙値。 有効な値には、skipMembership、copyAll、ignoresecurity のいずれかが含まれています。|  
|applyCompression|True|True の場合、圧縮、同期操作中に適用されることを示すブール値それ以外の場合は false。|  
  
## <a name="response"></a>応答  
 コマンドが成功した場合は、空の結果を返します。 それ以外の場合、XMLA 例外が返されます。  
  
## <a name="usage-endpoints"></a>使用状況 (エンドポイント)  
 このコマンドの要素がのステートメントで使用される、[メソッドの実行&#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md)呼び出しで、次の方法で公開される XMLA エンドポイント。  
  
-   SQL Server Management Studio (SSMS) での XMLA ウィンドウとして  
  
-   入力ファイルとして、**呼び出す ascmd** PowerShell コマンドレット  
  
-   SSIS タスクまたは SQL Server エージェント ジョブへの入力として  
  
 SSMS からこのコマンドであらかじめ用意されているスクリプトを生成するには、データベースの同期 ダイアログ ボックスで スクリプト ボタンをクリックします。  
  
 [ \[MS-t SSAS\]: QL Server Analysis Services Tabular (SQL Server の技術的なプロトコル)](http://go.microsoft.com/fwlink/p/?LinkId=784855) JSON 表形式メタデータ コマンドとオブジェクトの構造を説明するセクション 3.1.5.2.2 がドキュメントに含まれています。 現時点では、そのドキュメントでは、コマンドや TMSL スクリプトで実装されていない機能について説明します。 トピックを参照してください[表形式モデル スクリプト言語&#40;TMSL&#41;参照](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)明確にする新機能がサポートされている.  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
