---
title: "スレッドのサポート (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント"
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
- thread support [ODBC]
- Visual FoxPro ODBC driver [ODBC], thread support
- FoxPro ODBC driver [ODBC], thread support
- multithreaded applications [ODBC]
ms.assetid: 0c6abbbc-012b-41aa-bded-5e7e362d015b
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0c92c727b79c2fc33c98e02580d7980c219c56d6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="thread-support-visual-foxpro-odbc-driver"></a>スレッド サポート (Visual FoxPro ODBC ドライバー)
Visual FoxPro ODBC ドライバーは、スレッド セーフです。 環境ハンドルへのアクセス (*ごく*)、接続ハンドル (*hdbc*)、およびステートメントのハンドル (*hstmt*) を他のプロセスを防ぐために適切なセマフォでラップされますアクセスし、可能性のあるドライバーの内部データ構造を変更します。  
  
 マルチ スレッド アプリケーションでは、同期的に実行されている関数を取り消すことができます、 *hstmt*を呼び出して[SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md)別のスレッドでします。  
  
 ドライバーは、プログレッシブ フェッチを使用すると、データをフェッチするのに別のスレッドを使用します。 データ ソースのプログレッシブ フェッチを使用するのには、選択、**バック グラウンドでデータをフェッチ**チェック ボックスをオン、 [ODBC Visual FoxPro セットアップ ダイアログ ボックス](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)キーワードを使用して、BackgroundFetch 属性は、接続または文字列。 マルチ スレッド アプリケーションからドライバーを呼び出す場合は、バック グラウンドでフェッチを使用しないでください。 接続文字列キーワードの属性については、次を参照してください。[接続文字列を使用して](../../odbc/microsoft/using-connection-strings.md)です。  
  
 スレッドの詳細については、 **SQLCancel**を参照してください[SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md)で、 *ODBC プログラマ リファレンス*です。
