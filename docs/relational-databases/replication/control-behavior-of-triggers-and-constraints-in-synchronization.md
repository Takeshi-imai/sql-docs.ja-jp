---
title: "同期のトリガーと制約の動作を制御する | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- identities [SQL Server replication]
- constraints [SQL Server], replication
- triggers [SQL Server], replication
- triggers [SQL Server replication]
- constraints [SQL Server replication]
- NOT FOR REPLICATION option
- NFR option
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 75ba5c451d179978255559021d635689a461a484
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="control-behavior-of-triggers-and-constraints-in-synchronization"></a>同期のトリガーと制約の動作を制御する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  同期中、レプリケートされるテーブルでは、[INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)、[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)、[DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md) の各ステートメントがレプリケーション エージェントによって実行され、これらのテーブルに対して設定されていたデータ操作言語 (DML) のトリガーが実行されます。 同期中はこれらのトリガーが起動しないようにしたり、制約が適用されないようにすることが必要になる場合があります。 このときの動作は、トリガーまたは制約がどのように作成されたかによって異なります。  
  
### <a name="to-prevent-triggers-from-executing-during-synchronization"></a>同期中にトリガーが実行されないようにするには  
  
1.  新しいトリガーを作成する場合は、[CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md) の NOT FOR REPLICATION オプションを指定します。  
  
2.  既存のトリガーの場合は、[ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md) の NOT FOR REPLICATION オプションを指定します。  
  
### <a name="to-prevent-constraints-from-being-enforced-during-synchronization"></a>同期中に制約が適用されないようにするには  
  
1.  CHECK 制約または FOREIGN KEY 制約を新たに作成する場合は、 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md) の制約定義で、CHECK NOT FOR REPLICATION オプションを指定します。  
  
## <a name="see-also"></a>参照  
 [テーブルの作成 &#40;データベース エンジン&#41;](../../relational-databases/tables/create-tables-database-engine.md)  
  
  
