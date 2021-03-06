---
title: "データ ソース オブジェクト (Analysis Services) に対するアクセス許可を与える |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.asvs.roledesignerdialog.datasources.f1
helpviewer_keywords:
- read/write permissions
- user access rights [Analysis Services], data sources
- security [Analysis Services], data sources
- connection strings [Analysis Services]
- data sources [Analysis Services], security
ms.assetid: b4e302d3-c93b-4383-aa4a-37d15c129830
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f7cd02446a61b7ff1c8d9fdaa2803c30ee81a6e0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="grant-permissions-on-a-data-source-object-analysis-services"></a>データ ソース オブジェクトに対する権限の付与 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]ほとんどのユーザーの通常、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の基になるデータ ソースへのアクセスは必要ありません、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクト。 ユーザーは通常、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース内部のデータを要求するクエリを発行するだけです。 ただし、データ マイニングのコンテキストでは、マイニング モデルに基づいた予測の実行など、マイニング モデルの登録済みデータをユーザーが入力したデータに結合しなければならない場合があります。 ユーザーが入力したデータが含まれているデータ ソースに接続するには、[OPENQUERY &#40;DMX&#41;](../../dmx/source-data-query-openquery.md) 句または [OPENROWSET &#40;DMX&#41;](../../dmx/source-data-query-openrowset.md) 句を含んでいるデータ マイニング拡張機能 (DMX) クエリを使用します。  
  
 データ ソースに接続する DMX クエリを実行するには、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース内のデータ ソース オブジェクトに対するアクセス権が必要です。 既定では、サーバー管理者またはデータベース管理者のみが、データ ソース オブジェクトにアクセスできます。 つまり、ユーザーは管理者から権限を付与されている場合を除いてデータ ソース オブジェクトにアクセスできません。  
  
> [!IMPORTANT]  
>  セキュリティ上の理由から、OPENROWSET 句内の開いている接続文字列を使用して DMX クエリを送信することはできないようになっています。  
  
## <a name="set-read-permissions-to-a-data-source"></a>データ ソースに対する読み取り権限の設定  
 データベース ロールには、データ ソース オブジェクトへのアクセス権をまったく与えないか、または読み取り権限を与えることができます。  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続し、オブジェクト エクスプローラーで適切なデータベースの **[ロール]** を展開し、データベース ロールをクリックするか、新しいデータベース ロールを作成します。  
  
2.  **[データ ソース アクセス]** ペインで、 **[データ ソース]** ボックスの一覧からデータ ソース オブジェクトを探し、データ ソースの **[アクセス]** ボックスの一覧で **[読み取り]** を選択します。 このオプションを使用できない場合は、 **[全般]** ペインでフル コントロールが選択されているかどうかを確認してください。 フル コントロールによって権限が既に提供されているため、データ ソースに対する権限を上書きすることはできません。  
  
## <a name="working-with-the-connection-string-used-by-a-data-source-object"></a>データ ソース オブジェクトが使用する接続文字列の操作  
 データ ソース オブジェクトには、基になるデータ ソースに接続するための接続文字列が含まれています。 この接続文字列を使用すると、次のいずれかを指定できます。  
  
-   **ユーザー名とパスワードを指定する**  
  
     データ ソース オブジェクトで使用される接続文字列によってユーザー名とパスワードを指定すると、それぞれ異なるユーザー アカウントが設定された複数のデータ ソース オブジェクトを作成できます。 複数のデータ ソース オブジェクトを作成すると、ユーザーが特定のデータ ソース オブジェクトにだけアクセスし、その他のデータ ソース オブジェクトにアクセスできないようにすることができます。 このようなその他のデータ ソース オブジェクトは、キューブやマイニング モデルなどのオブジェクトを処理するために [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 自体によって使用されます。  
  
-   **Windows 認証を指定する**  
  
     データ ソース オブジェクトで使用される接続文字列によって Windows 認証を指定すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、クライアントの権限を借用できるようになります。 データ ソースがリモート コンピューターにある場合、そのリモート コンピューターと Analysis Services のコンピューターの両方に、Kerberos 認証を使用して、権限借用のための認証を設定する必要があります。設定しないとクエリは失敗します。 詳細については、「 [Kerberos の制約付き委任のための Analysis Services の構成](../../analysis-services/instances/configure-analysis-services-for-kerberos-constrained-delegation.md) 」を参照してください。  
  
     OLE DB またはその他のクライアント コンポーネントの権限借用レベル プロパティを通じての権限借用をクライアントが許可していない場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、基になるデータ ソースに匿名接続しようとします。 リモート データ ソースへの匿名接続が成功することはほとんどありません。これは、大部分のデータ ソースで匿名アクセスが許可されないためです。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのデータ ソース](../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)   
 [接続文字列のプロパティ &#40;です。Analysis Services &#41;](../../analysis-services/instances/connection-string-properties-analysis-services.md)   
 [Analysis Services でサポートされる認証方法](../../analysis-services/instances/authentication-methodologies-supported-by-analysis-services.md)   
 [データ &#40; をディメンションにカスタムのアクセスを許可します。Analysis Services &#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)   
 [キューブ権限またはモデル権限の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)   
 [セル データへのカスタム アクセス権の付与 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)  
  
  
