---
title: "ファイル ベースのドライバー |Microsoft ドキュメント"
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
- file-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
- drivers [ODBC], file-based drivers
ms.assetid: d92e0c5c-d176-4282-bbe1-d449e2223d50
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c9873f0b61364bd12bca0823ba66749513a4342c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="file-based-drivers"></a>ファイル ベースのドライバー
ファイル ベースのドライバーがドライバーを使用するためのスタンドアロン データベース エンジンを提供しない dBASE などのデータ ソースで使用されます。 これらのドライバーでは、物理的なデータに直接アクセスし、プロセス SQL ステートメントをデータベース エンジンを実装する必要があります。 標準的な方法は、ファイル ベースのドライバーでのデータベース エンジンは、最小 SQL への準拠レベルによって定義された ODBC SQL のサブセットを実装します。この準拠レベル内の SQL ステートメントの一覧は、次を参照してください。[付録 c: SQL 文法](../../odbc/reference/appendixes/appendix-c-sql-grammar.md)です。  
  
 比較するファイルをベースし、DBMS に基づいたドライバーのファイル ベースのドライバーは、ネットワーク部分がないために、構成する簡単な データベース エンジン コンポーネントを記述するは困難ほど強力少数のユーザーがデータベースに書き込む時間エンジンが強力でデータベースの企業によって生成されたものです。  
  
 次の図は、ネットワーク ファイル サーバー上のファイル ベースのドライバー、データがローカルに存在する 1 つが存在する 2 つの異なる構成を示します。  
  
 ![ファイルの 2 つの構成 &#45; ベースのドライバー](../../odbc/reference/media/pr06.gif "pr06")
