---
title: "キャッシュの場所 |Microsoft ドキュメント"
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
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 240d6162-4da6-4b1f-96c7-f379f4ecb16f
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f8d2c2083175bcccf1fba0157bcdf30c8b83af81
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="location-of-cache"></a>キャッシュの場所
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 カーソル ライブラリでは、メモリ内と Windows® 一時ファイルにデータをキャッシュします。 これにより、使用可能なディスク容量によってのみ、カーソル ライブラリを処理できる結果セットのサイズが制限されます。 カーソル ライブラリのキャッシュの最後に挿入された場合、キャッシュに保存するデータはセグメントの境界を越えると、一時ファイルが使用されます。 代わりに、キャッシュに保存するデータは、キャッシュ内のデータの最後に保存されたブロックの代わりに追加されます。 最後に保存されたデータ ブロックは、一時ファイルに保存されます。 などの電源が失敗すると、カーソル ライブラリが異常終了した場合、ディスク上に Windows 一時ファイルを残したまま。 これらの名前は ~ CTT*nnnn*.tmp とは、現在のディレクトリ内に作成します。  
  
> [!NOTE]  
>  カーソル ライブラリの Microsoft® WindowsNT®/windows 2000 しようとすると、現在のディレクトリに一時ファイルのキャッシュ データを読み取り専用の共有または (Microsoft Foundation Class ライブラリ サンプルの場合) などのコンパクト ディスクから、アプリケーションの実行中に SQLSTATEHY000 (一般的なエラー-できませんファイル バッファーを作成する) が返されます。
