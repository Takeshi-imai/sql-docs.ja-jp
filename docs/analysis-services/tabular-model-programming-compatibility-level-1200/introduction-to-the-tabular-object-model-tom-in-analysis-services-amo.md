---
title: "サービス AMO の分析で表形式オブジェクト モデル (TOM) の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 57a4a934-ecd0-4365-8147-d36899d86751
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 7efb5e145bbc4b481f73624a4c0d08d9698dc24c
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="introduction-to-the-tabular-object-model-tom-in-analysis-services-amo"></a>Analysis Services AMO では、表形式オブジェクト モデル (TOM) の概要
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
表形式オブジェクト モデル (TOM) は、互換性レベル 1200 以上で作成された表形式モデルのプログラミング シナリオをサポートするために作成された、Analysis Services 管理オブジェクト (AMO) クライアント ライブラリの拡張です。 同様に、AMO は、TOM は、モデルを作成する、インポートとデータを更新するロールとアクセス許可の割り当てなどの管理機能を処理するプログラムによる方法を提供します。  
  
TOM など、ネイティブの表形式メタデータを公開**モデル**、**テーブル**、**列**、および**リレーションシップ**オブジェクト。  以下に、オブジェクト モデル ツリーの概要を表示では、コンポーネント部分がどのように関連しているかを示します。  
  
 TOM は、AMO の拡張機能であるために、SQL Server 2016 で導入された新しい表形式オブジェクトを表すすべてのクラスは、新しい Microsoft.AnalysisServices.Tabular.dll アセンブリで実装されます。 AMO の汎用クラスでは、Microsoft.AnalysisServices.Core アセンブリに移動されました。 コードは、両方のアセンブリを参照する必要があります。
参照してください[これをインストールすると、配布、および表形式オブジェクト モデル &#40; を参照Microsoft.AnalysisServices.Tabular &#41;](../../analysis-services/tabular-model-programming-compatibility-level-1200/install-distribute-and-reference-the-tabular-object-model.md)詳細についてはします。  
  
 現時点では、API は、.NET framework 経由でマネージ コードでのみ使用できます。 スクリプトおよびクエリの言語サポートを含む、オプションのプログラミングの完全な一覧を確認するのを参照してください。[互換性レベル 1200 の表形式モデルをプログラミング](../../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md)です。  
  
## <a name="tabular-object-model-hierarchy"></a>表形式オブジェクト モデル階層  
 論理的な観点から表形式のすべてのオブジェクト ツリーを形成するがのルートは、**モデル**データベースの子孫です。 **サーバー**と**データベース**は考慮されません「表形式」これらのオブジェクトを表す場合も、多次元データベース、多次元モードまたは下位の互換性で表形式モデルで実行しているサーバーでホストされているためレベルを使用しない表形式メタデータ オブジェクトの定義にします。 
  
 例外を除いて**AttributeHierarchy**、 **KPI**、および**LinguisticMetadata**、各子オブジェクトのコレクションのメンバーであることができます。 たとえば、**モデル**オブジェクトのコレクションを格納する**テーブル**オブジェクト (を使用して、**テーブル**プロパティ)、各**テーブル**オブジェクトコレクションを含む**列**オブジェクト、およびなどです。  
  
 この階層内の任意の親オブジェクトの最下位レベルの子孫が、**注釈**必要に応じてそれを処理するコードを提供する限り、スキーマを拡張するために使用できるオブジェクト。  
  
 ![オブジェクト階層のダイアグラム](../../analysis-services/tabular-model-programming-compatibility-level-1200/media/ssastomobjectmodeldiagram.png "オブジェクト階層のダイアグラム")  
  
## <a name="tom-and-other-related-technologies"></a>TOM とその他の関連テクノロジ

TOM は多次元および表形式のデータベース互換性レベル 1200 の下にも対応する AMO インフラストラクチャに基づいて構築します。

これにより、実際的な影響があります。
表形式のメタデータで指定されていないオブジェクトを管理するときにすべての最初の (など、**サーバー**または**データベース**)、それらのオブジェクトを記述する、既存の AMO スタックの部分を活用する必要があります。 レガシ API と共に、またはサーバーに保存されると、サーバーから検出されたオブジェクトの状態の詳細な説明を提供するオブジェクトがメジャーおよびマイナーの概念です。 Microsoft.AnalysisServices 名前空間の下 MajorObject クラスのメソッドを公開**更新**と**更新**です。 副次オブジェクトはのみの更新または主要なオブジェクトを使用して保存を格納していること。

これに対し、表形式メタデータの一部であるオブジェクトを管理する場合 (など**モデル**または**テーブル**)、まったく新しい表形式のスタックを活用することです。 このスタック内の更新プログラムは詳細なつまりすべてのメタデータ オブジェクト (から派生した、 **MetadataObject** Microsoft.AnalysisServices.Tabular 名前空間の下のクラス)、サーバーに個別に保存できます。 全体を探索する通常、**モデル**、その下にある個別のメタデータ オブジェクトを変更する (など**テーブル**または**列**)、呼び出す**Model.SaveChanges()**メソッド (これは粒度の細かいレベルで加えた変更を認識する) 場合は、変更されたオブジェクトのみを更新するサーバーにコマンドを送信します。

### <a name="tom-and-xmla"></a>TOM と XMLA

ネットワーク上で TOM、XMLA プロトコルを使用して、Analysis Services サーバーとの通信オブジェクトを管理します。 表ではないオブジェクトを管理するには、TOM を使用して[ASSL](../scripting/analysis-services-scripting-language-assl-for-xmla.md)XMLA の Analysis Services スクリプト言語拡張機能です。 表形式オブジェクトを管理するには、TOM は XMLA の拡張機能も MS SSAS 表形式のプロトコルを使用します。 参照してください[MS-t SSAS SQL Server Analysis Services 表形式のプロトコルのドキュメント](https://msdn.microsoft.com/library/mt719260.aspx)詳細についてはします。

### <a name="tom-and-json"></a>TOM と JSON

表形式のメタデータは、JSON ドキュメントとして構成されているが、新しいコマンドとオブジェクト モデル定義の構文、表形式モデル スクリプト言語を使用して[TMSL](../tabular-model-scripting-language-tmsl-reference.md)です。 スクリプト言語は、要求と応答の本文の JSON を使用します。

TMSL と TOM の両方が同じオブジェクトを公開 (**テーブル**、**列**など) と同じ操作、および (**作成**、**削除**、 **更新**)、TOM (プロトコルを使用して、MS SSAS 表形式代わりに、前述のとおり)、ネットワーク上で TMSL を使用しません。

ユーザーは、c# プログラムか PowerShell スクリプトから TOM ライブラリ、または PowerShell、SQL Server Management Studio (SSMS) または SQL Server エージェント ジョブによって実行される TMSL スクリプトを通じて、表形式データベースを管理するかどうかを選択できます。

どちらか一方を使用するかは、、要件の詳細を得られます。 TOM ライブラリでは、TMSL と比較してより豊富な機能を提供します。 具体的には、TMSL は、データベース、テーブル、パーティション、またはロール レベルの粒度の粗い操作のみを提供する一方、TOM は操作をくらい細かくようにします。 生成またはモデルをプログラムで更新、TOM ライブラリ内の API のすべての範囲が必要です。
  
## <a name="see-also"></a>参照  
 [互換性レベル 1200 の表形式モデルのプログラミング](../../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md)   
 [Analysis Services での表形式モデルの互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
[Analysis Services PowerShell](../../analysis-services/powershell/analysis-services-powershell-reference.md)
  
