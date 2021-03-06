---
title: "VFP FoxPro ODBC ドライバーを使用してアプリケーションを使用して Visual Basic |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], visual basic applications
- Visual Basic applications [ODBC]
- FoxPro ODBC driver [ODBC], visual basic applications
- Visual FoxPro data [ODBC], visual basic applications
ms.assetid: 5223ca23-5df6-4ebc-aa3b-70682ff27a8c
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 266577d54e579956fcc2435283a9835c19f9ef36
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="using-the-vfp-foxpro-odbc-driver-with-your-visual-basic-application"></a>Visual Basic アプリケーションで VFP FoxPro ODBC ドライバーを使用
Microsoft® Visual Basic® アプリケーションは、Visual FoxPro データ ソースに接続するデータ コントロールを作成することで、Visual FoxPro データと通信できます。  
  
#### <a name="to-connect-to-visual-foxpro-data-using-the-data-control-in-visual-basic"></a>Visual FoxPro を Visual Basic では、データ コントロールを使用してデータに接続するには  
  
1.  Visual FoxPro に含まれる TasTrade サンプル データベースに接続するデータ ソースが"test"という名前を作成します。 Visual FoxPro の既定のインストール場所に TasTrade サンプル データベースに配置します。  
  
    ```  
    c:\vfp\samples\mainsamp\data\tastrade.dbc  
    ```  
  
2.  Visual Basic では、新しいフォームを作成し、テキスト ボックスと、上のデータ コントロールを配置します。  
  
3.  次のように、データ コントロールの接続プロパティを変更します。  
  
    ```  
    ODBC;DATABASE=tastrade;DSN=test  
    ```  
  
4.  レコード セットを次のように変更します。  
  
    ```  
    2 - Snapshot  
    ```  
  
5.  レコード ソース プロパティを次のように変更します。  
  
    ```  
    customer  
    ```  
  
6.  テキスト ボックスの DataSource プロパティを次に、データ コントロールの既定の名前に変更します。  
  
    ```  
    data1  
    ```  
  
7.  テキスト ボックスの DataField プロパティを次のように変更します。  
  
    ```  
    customer_id  
    ```  
  
8.  フォームを実行し、Visual FoxPro TasTrade サンプル データベースから顧客 id フィールドをスキップするデータ コントロールを使用します。
