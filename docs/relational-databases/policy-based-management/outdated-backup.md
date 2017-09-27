---
title: "期限切れのバックアップ | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 307a4ad0-675a-4f97-9a3c-cedd61bdfae5
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 94f220565078ceddac2aa43eb8e88f9895c27e9d
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="outdated-backup"></a>期限切れのバックアップ
  このルールでは、データベースに最新のバックアップがあることを確認します。 定期的なバックアップをスケジュールすることは、さまざまなエラーによるデータの損失からデータベースを保護するために重要です。 データをバックアップする適切な頻度は、データベースの復旧モデル、潜在的なデータの損失に関するビジネス要件、およびデータベースの更新頻度によって異なります。 頻繁に更新されるデータベースでは、バックアップ間で作業の損失の危険性が非常に早く高まります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 データ損失からデータベースを保護するために、十分な頻度でバックアップを行うことをお勧めします。  
  
 単純復旧モデルと完全復旧モデルの両方でデータのバックアップを行う必要があります。 いずれの復旧モデルでも、完全バックアップを差分バックアップで補完すると、データ損失の危険性を効率的に低くすることができます。  
  
 完全復旧モデルを使用するデータベースの場合は、ログのバックアップを頻繁に行うことをお勧めします。 非常に重要なデータが含まれている実稼働データベースの場合、ログのバックアップは通常 1 ～ 15 分ごとに行われます。  
  
> [!NOTE]  
>  バックアップのスケジュール方法として、データベース メンテナンス プランをお勧めします。  
  
## <a name="for-more-information"></a>詳細情報  
 [システム データベースのバックアップと復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [復旧モデル &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)  
  
 [データベースの差分バックアップの作成 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)  
  
 [データベースの完全バックアップの作成 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
 [メンテナンス プラン](../../relational-databases/maintenance-plans/maintenance-plans.md)  
  
 [トランザクション ログのバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  