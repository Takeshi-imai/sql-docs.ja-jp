---
title: MSSQLSERVER_10507 | Microsoft Docs
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
- 10507 (Database Engine error)
ms.assetid: cd83fa81-ac37-4eda-a3c3-17610b051de2
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0943ae13586a5ceefe2a6ec7e07b7cb498a1b525
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver10507"></a>MSSQLSERVER_10507
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10507|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_STMT_DOES_NOT_MATCH|  
|メッセージ テキスト|プラン ガイド '%.\*ls' を作成できません。**@stmt** と **@module_or_batch** または **@plan_handle** と **@statement_start_offset** で指定したステートメントが、指定したモジュールまたはバッチのステートメントと一致しません。 モジュールまたはバッチのステートメントと一致するように値を変更してください。|  
  
## <a name="explanation"></a>説明  
指定したモジュールまたはバッチのステートメントが、指定したステートメントまたはステートメントのオフセット値と一致しませんでした。  
  
## <a name="user-action"></a>ユーザーの操作  
モジュールまたはバッチのステートメントと一致するように指定のパラメーター値を変更します。  
  
## <a name="see-also"></a>参照  
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
