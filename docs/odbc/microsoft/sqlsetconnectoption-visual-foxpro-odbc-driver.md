---
title: "SQLSetConnectOption (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5a35449e-4694-4ee5-9fa1-45d5a8fe7823
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 14e3708e58d87a1ab38f4b22e9917320969c105b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconnectoption-visual-foxpro-odbc-driver"></a>SQLSetConnectOption (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 部分的な  
  
 レベル 1 の ODBC API への準拠:  
  
 接続の側面を制御するオプションを設定します。 この関数は部分的にサポートされています: ドライバーのすべての値をサポートしている、 *fOption*引数の一部でサポートされていません*vParam*の値を*fOption*引数SQL_TXN_ISOLATION です。  
  
 次の表に、これらの引数の Visual FoxPro ODBC ドライバーの実装に固有の動作とのみ**SQLSetConnectOption**です。  
  
|*fOption*|解説|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|アプリケーションのコミットまたはでトランザクションをロールバックする必要があります明示的に SQL_AUTOCOMMIT_OFF 場合は、 [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); Visual FoxPro ODBC ドライバーが完了したときに transactable ステートメントを自動的にコミットできません。 ドライバーは、トランザクションを開始するステートメントが transactable 場合。|  
|SQL_CURRENT_QUALIFIER|完全修飾できる[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)名または完全修飾パスを含むディレクトリ 0 個以上[テーブルの空き](../../odbc/microsoft/visual-foxpro-terminology.md)です。|  
|SQL_LOGINTIMEOUT|「ドライバーは対応していない」エラーが返されます。|  
|SQL_CURSORS|「ドライバーは対応していない」エラーが返されます。|  
|SQL_PACKET_SIZE|「ドライバーは対応していない」エラーが返されます。|  
|SQL_TXN_ISOLATION|ドライバーは、SQL_TXN_READ_COMMITTED のみを使用します。<br /><br /> 次*vParam*s はサポートされていません。<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 詳細については、次を参照してください。 [SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md)で、 *ODBC プログラマ リファレンス*です。