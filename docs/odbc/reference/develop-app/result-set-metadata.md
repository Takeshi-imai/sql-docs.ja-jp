---
title: "結果セットのメタデータ |Microsoft ドキュメント"
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
- result sets [ODBC], metadata
- metadata [ODBC]
ms.assetid: 6d134515-e34d-4563-96d7-8ad7714818fd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0f5de9f9b5b2a6da81fa175f24cd5bdf1b14e6e8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="result-set-metadata"></a>結果セットのメタデータ
*メタデータ*は、その他のデータを説明するデータ。 たとえば、結果セットのメタデータには、結果セット内の列の数、それらの列、名前、有効桁数、null 値許容属性、およびなどのデータ型など、結果セットがについて説明します。  
  
 相互運用可能アプリケーションは、結果セットの列のメタデータを常に確認する必要があります。 結果セット内の列のメタデータは、カタログ関数によって返される列のメタデータから異なる場合があります。 たとえば、更新可能な列が 2 つのテーブルを結合して作成される結果セットに含まれているとします。 中に**SQLColumnPrivileges**可能性があるユーザーは、列を更新できます、結果セットのメタデータは、列の結合の「多」側でない場合があります多くのデータ ソースではなく、結合の"一"側の列を更新できます、"。多"側です。 データ型もできないと見なされますは同じであるため、データ ソースは、結果セットの作成中に、データ型を昇格する可能性があります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [メタデータを使用する方法ですか。](../../../odbc/reference/develop-app/how-is-metadata-used.md)  
  
-   [SQLDescribeCol と SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md)