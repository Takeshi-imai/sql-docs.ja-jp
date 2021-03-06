---
title: "動的 SQL |Microsoft ドキュメント"
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
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], dynamic SQL
- SQL statements [ODBC], embedded SQL
- dynamic SQL [ODBC]
- SQL [ODBC], dynamic SQL
- embedded SQL [ODBC]
ms.assetid: 0bfb9ab7-9c15-4433-93bc-bad8b6c9d287
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: a2378a7e84b62102666985f3166bd9c8586837e3
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="dynamic-sql"></a>動的 SQL
静的 SQL さまざまな状況でも適切に動作しますが、アプリケーションをデータ アクセスを事前に決定することはできませんのクラスがあります。 たとえば、スプレッドシートにより、ユーザーは、スプレッドシートに送信 DBMS データを取得するクエリを入力します。 このクエリの内容明らかに知ることができない、プログラマ、スプレッドシート プログラムが書き込まれるときにします。  
  
 この問題を解決するためには、スプレッドシートは、動的 SQL と呼ばれる embedded SQL の形式を使用します。 静的な SQL ステートメントでは、プログラムにハードコードされてとは異なりには、動的 SQL ステートメントを実行時に構築して文字列のホスト変数内に配置することができます。 処理のため、DBMS にし、送信されます。 DBMS には、動的 SQL ステートメントの実行時アクセス プランを生成する必要があります、ために、動的 SQL は、静的 SQL より一般的に遅くなります。 動的 SQL ステートメントを含むプログラムがコンパイルされると、動的 SQL ステートメントは、静的 SQL と同様に、プログラムからは削除できません。 代わりに、DBMS 以外に、ステートメントを渡される関数呼び出しに置き換えられます通常、同じプログラム内で静的な SQL ステートメントが処理されます。  
  
 動的 SQL ステートメントを実行する最も簡単な方法では、即時実行ステートメントを使用します。 このステートメントは、SQL ステートメントをコンパイルおよび実行に関する、DBMS に渡します。  
  
 即時実行ステートメントの 1 つの欠点は、各ステートメントが実行されるたびに SQL ステートメントの処理の 5 つの手順を経由、DBMS しなければならないことです。 多くのステートメントが動的に実行され、これらのステートメントが同じ場合は無駄な場合、このプロセスで発生するオーバーヘッドは大幅なできます。 このような状況に対処するには、動的 SQL は、次の手順を使用して、準備実行と呼ばれる実行の最適化された形式を提供します。  
  
1.  プログラムは、即時実行ステートメントと同様に、バッファー内の SQL ステートメントを構築します。 ホストの変数の代わりに、定数、定数の値を後で指定することを示すステートメント テキスト内の任意の場所の疑問符 (?) に置き換えられることができます。 パラメーター マーカーとして疑問符 () と呼びます。  
  
2.  プログラムは、SQL ステートメントをよう計画すること、DBMS 解析、検証、およびステートメントの最適化および実行を生成する要求を準備するステートメントを DBMS に渡します。 プログラムは、EXECUTE ステートメント (されません直ちに実行ステートメント) を使用して後で準備のステートメントを実行します。 SQL データ領域または SQLDA と呼ばれる特別なデータ構造でステートメントのパラメーターの値が渡されます。  
  
3.  プログラムは、動的ステートメントが実行されるたびに異なるパラメーター値を指定して、EXECUTE ステートメントを繰り返し、使用できます。  
  
 準備実行はまだありません静的 SQL と同じです。 静的な SQL で SQL ステートメントの処理の最初の 4 つの手順はコンパイル時に行われます。 準備実行では、次の手順も実行、実行時に、1 回だけ実行されます。プランの実行は、EXECUTE を呼び出したときにのみ行われます。 これにより、動的 SQL のアーキテクチャに固有のパフォーマンスの欠点の一部を排除できます。 次の図は、静的 SQL、即時実行は、動的 SQL、準備実行での動的 SQL の相違を示します。
