---
title: "結果セット (拡張ストアド プロシージャ API) サーバーへの送信 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 897addc38cc2bbff5ccd536692750a3d0c75cd7b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>結果セットのサーバーへの送信 (拡張ストアド プロシージャ API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 代わりに CLR Integration を使用してください。  
  
 結果セットを送信するときに[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、拡張ストアド プロシージャは次のように、適切な API を呼び出す必要があります。  
  
-   **Srv_sendmsg**前に、または後で送信されたすべての行 (あれば)、任意の順序で関数を呼び出すことが**srv_sendrow**です。 完了ステータスを送信する前に、クライアントにすべてのメッセージを送信する必要があります**srv_senddone**です。  
  
-   **srv_sendrow** 関数は、クライアントに送信される各行につき 1 回呼び出されます。 すべての行は、メッセージ、状態値の前に、クライアントに送信する必要がありますまたは完了状態を送信する**srv_sendmsg**、 **srv_status**の引数**srv_pfield**、または**srv_senddone**です。  
  
-   すべての列で定義されていない行を送る**srv_describe**により、アプリケーションは、情報エラー メッセージを発生させるし、クライアントに FAIL が返さです。 この場合、その行は送信されません。  
  
## <a name="see-also"></a>参照  
 [拡張ストアド プロシージャの作成](../../relational-databases/extended-stored-procedures-programming/creating-extended-stored-procedures.md)  
  
  
