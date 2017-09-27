---
title: "ODBC 内のエスケープ シーケンス |Microsoft ドキュメント"
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
- escape sequences [ODBC]
- SQL statements [ODBC], escape sequences
- escape sequences [ODBC], about escape sequences
ms.assetid: cf229f21-6c38-4b5b-aca8-f1be0dfeb3d0
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 92fd9745bccacad3d7487c3ed9f1bee58eeb4411
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="escape-sequences-in-odbc"></a>Odbc エスケープ シーケンス
外部結合およびスカラー関数の呼び出しなどの言語機能の数は、一般的な Dbms によって実装されます。 ただし、これらの機能の構文は、さまざまな標準機関で標準的な構文が定義されている場合でも DBMS に固有である傾向があります。 このため、ODBC では、標準の構文では、次の言語機能を含むエスケープ シーケンスが定義されています。  
  
-   日付、時刻、タイムスタンプ、および日時の間隔のリテラル  
  
-   数値などのスカラー関数、文字列、およびデータ型変換関数  
  
-   などの述語のエスケープ文字  
  
-   外部結合  
  
-   プロシージャ呼び出し  
  
 ODBC で使用されるエスケープ シーケンスは次のとおりです。  
  
```  
  
(extension)  
  
```  
  
## <a name="remarks"></a>解説  
 エスケープ シーケンスが認識し、ドライバー、DBMS 固有の文法でエスケープ シーケンスを置換して解析します。 エスケープ シーケンス構文の詳細については、次を参照してください。 [ODBC エスケープ シーケンス](../../../odbc/reference/appendixes/odbc-escape-sequences.md)付録 c: SQL の文法でします。  
  
> [!NOTE]  
>  ODBC 2 です。*x*、これが標準のエスケープ シーケンスの構文: **--(\*仕入先 (***仕入先名***)、製品 (** *製品名***)***拡張子* ** \*)--**  
>   
>  この構文だけでなく略式の構文が定義されているフォームの: **{***拡張子***}**  
>   
>  ODBC 3 です。*x*、エスケープ シーケンスの長い形式は推奨されていません、および短い形式を排他的に使用します。  
  
 エスケープ シーケンスが DBMS に固有の構文では、ドライバーによってマップされているため、アプリケーションは、エスケープ シーケンスまたは DBMS 固有の構文を使用できます。 ただし、DBMS 固有の構文を使用するアプリケーションは相互運用できません。 エスケープ シーケンスを使用する場合は、アプリケーションが SQL_ATTR_NOSCAN ステートメント属性を無効にする、既定ではこれを確認してください。 それ以外の場合、エスケープ シーケンスは、場所、一般に、構文エラーが発生、データ ソースに直接送信されます。  
  
 ドライバーは、基になる言語機能にマップするエスケープ シーケンスのみをサポートします。 データ ソースが外部結合をサポートしていない場合などは、どちらも、ドライバーには。 アプリケーションが呼び出す調べるにはどのエスケープ シーケンスはサポートされて、 **SQLGetTypeInfo**と**SQLGetInfo**です。 詳細については、次のセクションを参照してください。[日付、時刻、およびタイムスタンプのリテラル](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [日付、時刻、およびタイムスタンプのリテラル](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)  
  
-   [スカラー関数の呼び出し](../../../odbc/reference/develop-app/scalar-function-calls.md)  
  
-   [述語のエスケープ文字のように](../../../odbc/reference/develop-app/like-predicate-escape-character.md)  
  
-   [外部結合](../../../odbc/reference/develop-app/outer-joins.md)  
  
-   [プロシージャ呼び出し](../../../odbc/reference/develop-app/procedure-calls.md)