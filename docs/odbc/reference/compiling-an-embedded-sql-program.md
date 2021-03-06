---
title: "埋め込み SQL プログラムのコンパイル |Microsoft ドキュメント"
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
- SQL statements [ODBC], embedded SQL
- compiling embedded SQL programs [ODBC]
- embedded SQL [ODBC]
ms.assetid: 9e94146a-5b80-4a01-b586-1e03ff05b9ac
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: aeb3dbb46b8ac3e5e715a479923694cdea28a97f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="compiling-an-embedded-sql-program"></a>埋め込み SQL プログラムのコンパイル
埋め込み SQL プログラムには、SQL とホスト言語のステートメントの組み合わせが含まれている、ために、ホスト言語のコンパイラに直接送信することはできません。 代わりに、複数の手順の手順は、コンパイルします。 このプロセスには、製品が異なる場合は、操作は、ほぼすべての製品と同じです。  
  
 この図は、埋め込み SQL プログラムをコンパイルするために必要な手順を示します。  
  
 ![埋め込み SQL プログラムのコンパイル手順](../../odbc/reference/media/pr02.gif "pr02")  
  
 埋め込み SQL プログラムをコンパイルするのには、5 つの手順が必要。  
  
1.  埋め込み SQL プログラムは、SQL プリ プログラミング ツールに送信されます。 プリは、プログラムをスキャン、埋め込みの SQL ステートメントを検索し、それらを処理します。 さまざまなプリが DBMS によってサポートされているプログラミング言語ごとに必要です。 DBMS 製品は、通常、1 つまたは複数の言語では、C、Pascal、COBOL、Fortran、Ada、PL precompilers を提供/、およびさまざまなアセンブリ言語。  
  
2.  プリは、2 つの出力ファイルを生成します。 最初のファイルは、埋め込まれた SQL ステートメントを削除した、ソース ファイルです。 その代わりに、プリに、プログラムと、DBMS の間でランタイムのリンクを提供する専用の DBMS ルーチンへの呼び出しが置換されます。 通常、これらのルーチンの呼び出しの順序および名前のみが把握プリと DBMS;DBMS にパブリック インターフェイスではありません。 2 番目のファイルは、プログラムで使用されるすべての埋め込まれた SQL ステートメントのコピーです。 このファイルは、データベース要求モジュールの場合、または DBRM とも呼ばれます。  
  
3.  プリからソース ファイルの出力は、ホストのプログラミング言語 (C または COBOL コンパイラ) などの標準的なコンパイラに送信されます。 コンパイラは、ソース コードを処理し、その出力としてオブジェクト コードを生成します。 このステップでは、DBMS や SQL を実行することに注意してください。  
  
4.  リンカーは、コンパイラによって生成されたオブジェクト モジュールを受け入れるにさまざまなライブラリ ルーチンを使用してリンクし、実行可能プログラムを生成します。 実行可能プログラムにリンクするライブラリ ルーチンには、手順 2. で説明されている専用の DBMS ルーチンが含まれます。  
  
5.  プリ コンパイラによって生成されたデータベースの要求のモジュールは、特別なバインド ユーティリティに送信されます。 このユーティリティ SQL ステートメントを調べ、解析、検証すると、および、それらを最適化およびアクセスの各ステートメントに対してプランを生成します。 結果は、埋め込まれた SQL ステートメントの実行可能ファイルのバージョンを表すプログラム全体の統合されたアクセス プランです。 バインディング ユーティリティでは、データベース、通常それを使用するアプリケーション プログラムの名前を割り当てることで、プランが格納されます。 この手順がコンパイル時または実行時の場所を実行するかどうかは、DBMS に依存します。  
  
 埋め込み SQL プログラムをコンパイルするための手順は、前述の手順と非常に密接に関連付けるために注意してください[SQL ステートメントの処理](../../odbc/reference/processing-a-sql-statement.md)です。 具体的には、確認するプリはホスト言語コードから SQL ステートメントを区切りますバインディング ユーティリティを解析し、SQL ステートメントを検証し、アクセス プランを作成します。 Dbms が 5 のステップが実行されるコンパイル時に、SQL ステートメントの処理の最初の 4 つの手順行わ、コンパイル時に (実行) の最後の手順の実行時に実行中です。 これは、このような Dbms 非常に高速でクエリの実行を行うことの影響です。
