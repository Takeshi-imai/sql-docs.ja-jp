---
title: "ODBC コンポーネントのレジストリ エントリ |Microsoft ドキュメント"
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
- subkeys [ODBC]
- installing ODBC components [ODBC], registry entries
- registry entries for components [ODBC]
- subkeys [ODBC], for components
- registry entries for components [ODBC], about registry entries
ms.assetid: c90aa8a4-6ece-48de-901c-17d23739a9ff
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2eba696dec938321f270acf7cfd3c38141ec3f2f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="registry-entries-for-odbc-components"></a>ODBC コンポーネントのレジストリ エントリ
> [!NOTE]  
>  Windows XP および Windows Server 2003 以降、Windows オペレーティング システムに ODBC が含まれます。 以前のバージョンの Windows で ODBC を明示的にのみインストールしてください。  
  
 インストーラー DLL は、レジストリにインストールされている各 ODBC コンポーネントに関する情報を保持します。 Microsoft Windows NT および Microsoft Windows 95/98 を実行するコンピューターでこの情報は、次のレジストリ キーの下のサブキーに格納されます。  
  
 HKEY_LOCAL_MACHINE  
  
 ソフトウェア  
  
 ODBC  
  
 Odbcinst.ini  
  
 Odbcinst.ini には、サブキー HKEY_LOCAL_MACHINE ツリーのための ODBC コンポーネントに関する情報は、マシンのすべてのユーザーに利用可能なです。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC Core サブキー](../../../odbc/reference/install/odbc-core-subkey.md)  
  
-   [ODBC ドライバーのサブキー](../../../odbc/reference/install/odbc-drivers-subkey.md)  
  
-   [ドライバーの仕様のサブキー](../../../odbc/reference/install/driver-specification-subkeys.md)  
  
-   [既定のドライバーのサブキー](../../../odbc/reference/install/default-driver-subkey.md)  
  
-   [ODBC トランスレーターのサブキー](../../../odbc/reference/install/odbc-translators-subkey.md)  
  
-   [ドライバーの仕様のサブキー](../../../odbc/reference/install/translator-specification-subkeys.md)
