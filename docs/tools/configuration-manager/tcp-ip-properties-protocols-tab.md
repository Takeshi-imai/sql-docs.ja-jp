---
title: "TCP/IP のプロパティ ([プロトコル] タブ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/24/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: a37c630af512d85e22b3547eb520aebe22546040
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# [TCP/IP のプロパティ] ダイアログ ボックス ([プロトコル] タブ)
  **[TCP/IP のプロパティ]** ダイアログ ボックスは、TCP/IP プロトコルのオプションを構成するために使用します。 左ペインで **[TCP/IP]** をクリックすると、詳細ペインに個々の IP アドレス構成が表示されます。  
  
 変更を有効にするには、Microsoft SQL Server を再起動する必要があります。  
  
## オプション  
 **有効**  
 可能な値は、 **[はい]** と **[いいえ]**です。  
  
 **[Keep Alive]**  
 接続のリモート側のコンピューターが使用可能かどうかを確認するために、Keep Alive パケットを送信する間隔 (ミリ秒) を指定します。  
  
 **[すべて受信待ち]**  
 コンピューター上のネットワーク カードに割り当てられているすべての IP アドレスで SQL Server がリッスンするかどうかを指定します。 **[いいえ]**に設定した場合は、各 IP アドレスのプロパティ ダイアログ ボックスを使用して、IP アドレスごとに個別の構成を行ってください。 **[はい]**に設定した場合は、 **[IPAll]** プロパティ ボックスの設定がすべての IP アドレスに適用されます。 既定値は **[はい]**です。  
  
 **[遅延なし]**  
 SQL Server では、このプロパティに対する変更は実装されません。  
  
## 参照  
 [ネットワーク プロトコルの選択](https://msdn.microsoft.com/library/ms187892(v=sql.130).aspx)   
 [TCP/IP を使用した有効な接続文字列の作成](/sql-docs/docs/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip)  
  
  
