---
title: MSSQLSERVER_1406 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 1406 (Database Engine error)
ms.assetid: 915f97de-9b74-41f8-8bd5-b2d061416718
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4891e44df00520e539aec8e56b7e8c70b7577f00
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver1406"></a>MSSQLSERVER_1406
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|1406|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBM_BADSTATEFORFORCESERVICE|  
|メッセージ テキスト|サービスを安全に実行できません。 アクセスできるようにするには、データベース ミラーリングを削除して、データベース "%.*ls" を復旧してください。|  
  
## <a name="explanation"></a>説明  
ミラーリング状態ではサービスを強制するプロセスが正しく動作することを保証できないため、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]でサービスを強制できません。  
  
## <a name="user-action"></a>ユーザーの操作  
データベース ミラーリングを削除します。 その後、ミラー データベースを復旧して、このデータベースにアクセスできるようにします。  
  
## <a name="see-also"></a>参照  
[データベース ミラーリング セッションでのサービスを強制する &#40;Transact-SQL&#41;](~/database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md)  
[データベース ミラーリングの削除 &#40;SQL Server&#41;](~/database-engine/database-mirroring/removing-database-mirroring-sql-server.md)  
  
