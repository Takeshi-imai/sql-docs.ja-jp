---
title: "ODBC カーソル ライブラリ |Microsoft ドキュメント"
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
- ODBC cursor library [ODBC], about cursor library
- ODBC cursor library [ODBC]
- cursor library [ODBC], about cursor library
- scrollable cursors [ODBC]
- cursors [ODBC], cursor library
- block cursors [ODBC]
ms.assetid: 32fb7df0-953a-4f68-b041-7d2852e45d0f
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 45bce6d2b39ee15bcabd362b0a2fbfba377fe386
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="the-odbc-cursor-library"></a>ODBC カーソル ライブラリ
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 ブロックとスクロール可能なカーソルは、多くのアプリケーションに追加機能を非常に便利です。 ただし、必ずしもすべてのドライバーは、ブロックとスクロール可能なカーソルをサポートします。 同じ位置指定更新の場合は true、および delete ステートメントと**SQLSetPos**は、データ更新で説明します。 したがって、以前に、Microsoft Data Access Components (MDAC) SDK、含まれている、Windows SDK の ODBC コンポーネントには、カーソル ライブラリが含まれています。 カーソル ライブラリは、ブロック、静的カーソル、位置指定の update および delete ステートメントを実装および**SQLSetPos**を開いてグループ標準 CLI 準拠レベルを満たすすべてのドライバーのです。 カーソル ライブラリは、ODBC アプリケーションと共に再配布できる可能性があります。詳細については、SDK の使用許諾契約を参照してください。  
  
 カーソル ライブラリを使用するのには、アプリケーションは、データ ソースに接続する前に SQL_ATTR_ODBC_CURSORS 接続属性を設定します。 カーソル ライブラリの詳細については、次を参照してください。[付録 f: ODBC カーソル ライブラリ](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md)です。
