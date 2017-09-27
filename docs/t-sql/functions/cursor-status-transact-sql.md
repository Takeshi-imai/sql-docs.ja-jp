---
title: "CURSOR_STATUS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CURSOR_STATUS
- CURSOR_STATUS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server], cursors
- CURSOR_STATUS function
- cursors [SQL Server], status information
ms.assetid: 3a4a840e-04f8-43bd-aada-35d78c3cb6b0
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e88dd4f14d8bd6fc90c40df101bfd9b2895bf229
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="cursorstatus-transact-sql"></a>CURSOR_STATUS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

指定されたパラメーターでプロシージャがカーソルと結果セットを返したかどうかを、ストアド プロシージャの呼び出し元が判断するためのスカラー関数です。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
CURSOR_STATUS   
     (  
          { 'local' , 'cursor_name' }   
          | { 'global' , 'cursor_name' }   
          | { 'variable' , 'cursor_variable' }   
     )  
```  
  
## <a name="arguments"></a>引数  
'local'  
カーソルのソースがローカル カーソル名であることを示す定数です。
  
'*cursor_name*'  
カーソルの名前です。 カーソル名は、識別子の規則に従っている必要があります。
  
'global'  
カーソルのソースがグローバル カーソル名であることを示す定数です。
  
'variable'  
カーソルのソースを示す定数ですが、ローカル変数であることを指定します。
  
'*cursor_variable*'  
カーソル変数の名前です。 使用して、カーソル変数を定義する必要があります、**カーソル**データ型。
  
## <a name="return-types"></a>戻り値の型
**smallint**
  
|戻り値|カーソル名|カーソル変数|  
|---|---|---|
|1|カーソルの結果セットは 1 つ以上の行で構成されます。<br /><br /> 状態非依存のキーセット カーソルの場合、結果セットは 1 つ以上の行で構成されます。<br /><br /> 動的カーソルの場合、結果セットは 0、1、または複数の行で構成されます。|この変数に割り当てられているカーソルはオープンしています。<br /><br /> 状態非依存のキーセット カーソルの場合、結果セットは 1 つ以上の行で構成されます。<br /><br /> 動的カーソルの場合、結果セットは 0、1、または複数の行で構成されます。|  
|0|カーソルの結果セットは空です。*|この変数に割り当てられているカーソルはオープンしていますが、結果セットは完全に空です。*|  
|-1|カーソルはクローズしています。|この変数に割り当てられているカーソルはクローズしています。|  
|-2|該当なし。|次の値をとります。<br /><br /> 以前に呼び出されたプロシージャによって、この OUTPUT 変数にカーソルは割り当てられませんでした。<br /><br /> 以前に呼び出されたプロシージャによって、この OUTPUT 変数にカーソルが割り当てられましたが、プロシージャの終了時点ではカーソルはクローズした状態でした。 このため、カーソルの割り当てが解除され、呼び出し元のプロシージャに返されません。<br /><br /> 宣言されたカーソル変数にはカーソルが割り当てられていません。|  
|-3|指定された名前のカーソルは存在しません。|指定された名前のカーソル変数は存在しません。または、存在してもカーソルがまだ割り当てられていません。|  
  
* 動的カーソルがこのような結果を返すことはありません。
  
## <a name="examples"></a>使用例  
次の例では、`CURSOR_STATUS` 関数を使用して、カーソルのオープンとクローズの前後の状態を表示します。
  
```sql
CREATE TABLE #TMP  
(  
   ii int  
)  
GO  
  
INSERT INTO #TMP(ii) VALUES(1)  
INSERT INTO #TMP(ii) VALUES(2)  
INSERT INTO #TMP(ii) VALUES(3)  
  
GO  
  
--Create a cursor.  
DECLARE cur CURSOR  
FOR SELECT * FROM #TMP  
  
--Display the status of the cursor before and after opening  
--closing the cursor.  
  
SELECT CURSOR_STATUS('global','cur') AS 'After declare'  
OPEN cur  
SELECT CURSOR_STATUS('global','cur') AS 'After Open'  
CLOSE cur  
SELECT CURSOR_STATUS('global','cur') AS 'After Close'  
  
--Remove the cursor.  
DEALLOCATE cur  
  
--Drop the table.  
DROP TABLE #TMP  
  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`After declare`
  
`---------------`
  
 `-1`  
  
`After Open`
  
`----------`
  
 `1`  
  
`After Close`
  
`-----------`
  
 `-1`  
  
## <a name="see-also"></a>参照
[カーソル関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cursor-functions-transact-sql.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  
