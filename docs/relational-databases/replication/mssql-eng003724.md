---
title: MSSQL_ENG003724 | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
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
helpviewer_keywords:
- MSSQL_ENG003724 error
ms.assetid: 10cb119d-92df-4124-b85d-cd2f2666c99c
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c469d2d552d02fb3829a1a176877378cecb10ccc
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="mssqleng003724"></a>MSSQL_ENG003724
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|3724|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|%S_MSG '%.*ls' を %S_MSG できません。レプリケーションに使用されています。|  
  
## <a name="explanation"></a>説明  
 データベース内のオブジェクトがレプリケートされると、システム テーブル **sysarticles** (スナップショット パブリケーションまたはトランザクション パブリケーションの場合) または **sysmergearticles** (マージ パブリケーションの場合) に、レプリケート済みのマークが付けられています。 レプリケート済みのオブジェクトを削除しようとした場合に、このエラーが発生します。  
  
## <a name="user-action"></a>ユーザーの操作  
 データベース オブジェクトを削除する前に、そのオブジェクトがレプリケートされていないことを確認します。 例 :  
  
-   パブリケーション データベースでエラーが発生した場合、オブジェクトを削除する前にパブリケーションからアーティクルを削除します。 詳細については、「[Add Articles to and Drop Articles from Existing Publications](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)」 (既存のパブリケーションでのアーティクルの追加および削除) を参照してください。  
  
-   サブスクリプション データベースでエラーが発生した場合、オブジェクトを削除する前にそのサブスクリプションを削除します。 詳細については、「[パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)」をご覧ください。 トランザクション パブリケーションに対するサブスクリプションの場合、パブリケーション全体を削除するのではなく、個々のアーティクルに対するサブスクリプションを削除することができます。 詳細については、「[sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)」を参照してください。  
  
 レプリケートされていないデータベースでこのエラーが発生した場合は、[sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) を実行して、データベース内のオブジェクトにレプリケート済みのマークが付かないようにしてください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
