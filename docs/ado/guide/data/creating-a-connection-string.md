---
title: "接続文字列の作成 |Microsoft ドキュメント"
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
helpviewer_keywords:
- connections [ADO]
- connection strings [ADO]
ms.assetid: 14eae122-2d1e-40c8-b88e-b7cb8dfbc93b
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6d8c472f66f0b39e575b96d874d60948bb1a98b6
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="creating-a-connection-string"></a>接続文字列の作成
接続文字列は、セミコロンで区切られた引数と値のペア (つまり、パラメーター) の一覧で構成されます。 例:  
  
```  
"arg1=val1; arg2=val2; ... argN=valN;"  
```  
  
 すべてのパラメーターは、ADO または指定されたプロバイダーで認識する必要があります。  
  
 ADO では、接続文字列に次の 5 つの引数を認識します。  
  
|引数|Description|  
|--------------|-----------------|  
|*プロバイダー*|接続に使用するプロバイダーの名前を指定します。|  
|*[ファイル名]*|事前設定された接続情報を含むプロバイダー固有のファイル (たとえば、永続化されたデータ ソース オブジェクト) の名前を指定します。|  
|*[URL]*|ファイルまたはディレクトリなどのリソースを識別する絶対 URL として接続文字列を指定します。|  
|*リモート プロバイダー*|クライアント側の接続を開くときに使用するプロバイダーの名前を指定します。 (リモート データのサービスのみ。)|  
|*リモート サーバー*|クライアント側の接続を開くときに使用するサーバーのパス名を指定します。 (リモート データのサービスのみ。)|  
  
 その他の引数で指定されたプロバイダーに渡される、*プロバイダー* ADO で処理されず、引数。  
  
 HelloData アプリケーション[HelloData: A 単純な ADO アプリケーション](../../../ado/guide/data/hellodata-a-simple-ado-application.md)次の接続文字列を使用します。  
  
```  
m_sConnStr = "Provider=SQLOLEDB;Data Source=MySqlServer;" & _  
             "Initial Catalog=Northwind;Integrated Security='SSPI';"  
```  
  
 この接続文字列で ADO が認識するだけ、 `"Provider=SQLOLEDB"` ADO データ ソースとして SQL Server 用 Microsoft OLE DB プロバイダーを指定するパラメーターです。 引数と値のペアの残りの部分`"Data Source=MySqlServer; Initial Catalog=Northwind;Integrated Security='SSPI';"`、このプロバイダーにもそのまま渡されます。 このようなパラメーターの有効性と型は、プロバイダー固有です。 接続文字列で渡すことができる有効なパラメーターについては、個々 のプロバイダーのマニュアルを参照してください。  
  
 OLE DB Provider for SQL Server のドキュメント、に従って、用、"Server"を置き換えることができます、*データソース*パラメーターと「データベース」を*初期カタログ*パラメーター。 したがって、次の接続文字列では、上記と同じ結果が生成。  
  
```  
m_sConnStr = "Provider=SQLOLEDB;Server=MySqlServer;" & _  
             "Database=Northwind;Integrated Security='SSPI';"  
```
