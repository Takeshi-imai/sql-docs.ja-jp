---
title: "ODBC ステートメント ハンドルの解放 |Microsoft ドキュメント"
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
- statement handles [ODBC]
- handles [ODBC], statement
- freeing statement handles [ODBC]
ms.assetid: ee18e2f1-2690-4cc1-9e5c-e20244e5d480
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7a26d7745756904ab8da492cbb96b8714dd969e1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="freeing-a-statement-handle-odbc"></a>ODBC ステートメント ハンドルを解放します。
前述のようよりにドロップし、新しいものを割り当てるステートメントを再利用する方が効率的です。 ステートメントで新しい SQL ステートメントを実行する前に、アプリケーションは、現在のステートメント設定が適切であることを確認する必要があります。 確認する設定には、ステートメント属性、パラメーター バインド、結果セットのバインドがあります。 一般に、パラメーターと、古い SQL ステートメントの結果セットする必要がありますバインドを解除する (呼び出すことによって**SQLFreeStmt** SQL_RESET_PARAMS と SQL_UNBIND オプションを使用) と、新しい SQL ステートメントの再バインドします。  
  
 ステートメントを使用して、アプリケーションが終了呼び出し**SQLFreeHandle**ステートメントを解放します。 これは、ステートメントを解放した後、ODBC 関数の呼び出しでステートメントのハンドルを使用するアプリケーション プログラミング エラーこれには定義されていないが、おそらく致命的な影響します。  
  
 ときに**SQLFreeHandle**が呼び出されると、ドライバーのリリースのステートメントの情報を格納する構造体を使用します。  
  
 **SQLDisconnect**接続ですべてのステートメントを自動的に解放します。
