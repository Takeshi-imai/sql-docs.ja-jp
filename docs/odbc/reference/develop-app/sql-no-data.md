---
title: "SQL_NO_DATA |Microsoft ドキュメント"
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
- SQL_NO_DATA [ODBC]
- application upgrades [ODBC], SQL_NO_DATA
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
- upgrading applications [ODBC], SQL_NO_DATA
ms.assetid: 07a4144a-a548-4578-b2be-715c3cf73bf8
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: da9e5ffc19d884d2cb182190e11ba4dcf0a915bd
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlnodata"></a>SQL_NO_DATA
ODBC 3 時にします。*x*アプリケーション呼び出し**SQLExecDirect**、 **SQLExecute**、または**SQLParamData** ODBC 2 *。x*検索の更新を実行またはデータ ソース、ドライバーでの任意の行には影響しませんステートメントを削除するドライバーが SQL_SUCCESS、いない SQL_NO_DATA を返す必要があります。 ODBC 2 時にします。*x*または ODBC 3 *。x* ODBC 3 を使用するアプリケーション*。x*ドライバー呼び出し**SQLExecDirect**、 **SQLExecute**、または**SQLParamData** ODBC 3、同じ結果にします*。x*ドライバーが SQL_NO_DATA を返す必要があります。
