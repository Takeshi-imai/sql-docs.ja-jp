---
title: "メモリ最適化オブジェクト用ストレージの作成と管理 | Microsoft Docs"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 622aabe6-95c7-42cc-8768-ac2e679c5089
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 37aab4a523caee5ca5f4c3ebfc2482ca464dcf71
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="creating-and-managing-storage-for-memory-optimized-objects"></a>メモリ最適化オブジェクト用ストレージの作成と管理
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[hek_2](../../includes/hek-2-md.md)] には [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エンジンが統合されているため、メモリ最適化テーブルと (従来型の) ディスクベース テーブルの両方を同じデータベースに格納することができます。 ただし、メモリ最適化テーブルのストレージ構造は、ディスクベース テーブルとは異なります。  
  
 ディスクベース テーブルのストレージには、次のキー属性があります。  
  
-   ファイル グループにマップされます。ファイル グループは、1 つ以上のファイルを格納します。  
  
-   各ファイルは 8 ページから成るエクステントに分割されます。各ページのサイズは 8K バイトです。  
  
-   1 つのエクステントは複数のテーブルで共有できます。ただし、割り当てられたページと、テーブルまたはインデックスの間には 1 対 1 のマッピングがあります。 つまり、1 つのページが、複数のテーブルまたはインデックスに所属する行を持つことはできません。  
  
-   データは必要に応じてメモリ (バッファー プール) に移動され、変更されたページや新しく作成されたページは非同期的にディスクに書き込まれ、ほぼランダムな IO が生成される結果になります。  
  
 メモリ最適化テーブルのストレージには、次のキー属性があります。  
  
-   すべてのメモリ最適化テーブルは、メモリ最適化データ ファイル グループにマップされます。 このファイル グループは、Filestream に類似した構文とセマンティクスを使用します。  
  
-   ページという単位はなく、データは行として保存されます。  
  
-   メモリ最適化テーブルに対するすべての変更は、アクティブ ファイルへの追加という形で格納されます。 ファイルの読み取りと書き込みのどちらもシーケンシャルに実行されます。  
  
-   更新は、削除、およびその後に続く挿入という形で実装されます。 削除された行は、ストレージから直ちに削除されるわけではありません。 削除された行は、「 [メモリ最適化テーブルの持続性](../../relational-databases/in-memory-oltp/durability-for-memory-optimized-tables.md)」で説明されているポリシーに基づき、MERGE と呼ばれるバックグラウンド プロセスによって削除されます。  
  
-   ディスクベース テーブルとは異なり、メモリ最適化テーブルのストレージは圧縮されません。 圧縮された (行またはページの) ディスクベース テーブルをメモリ最適化テーブルに移行する場合は、サイズの変化を考慮する必要があります。  
  
-   メモリ最適化テーブルは、持続的にすることも、非持続的にすることもできます。 持続性のあるメモリ最適化テーブルに対してのみ、ストレージを構成する必要があります。  
  
 ここでは、チェックポイント ファイル ペアと、メモリ最適化テーブルのデータが格納されるしくみの他の側面について説明します。  
  
 このセクションのトピック:  
  
-   [メモリ最適化テーブルのストレージの構成](../../relational-databases/in-memory-oltp/configuring-storage-for-memory-optimized-tables.md)  
  
-   [メモリ最適化ファイルグループ](../../relational-databases/in-memory-oltp/the-memory-optimized-filegroup.md)  
  
-   [メモリ最適化テーブルの持続性](../../relational-databases/in-memory-oltp/durability-for-memory-optimized-tables.md)  
  
-   [メモリ最適化テーブルのチェックポイント操作](../../relational-databases/in-memory-oltp/checkpoint-operation-for-memory-optimized-tables.md)  
  
-   [メモリ最適化オブジェクトの持続性の定義](../../relational-databases/in-memory-oltp/defining-durability-for-memory-optimized-objects.md)  
  
-   [ディスク ベース テーブル ストレージとメモリ最適化テーブル ストレージの比較](../../relational-databases/in-memory-oltp/comparing-disk-based-table-storage-to-memory-optimized-table-storage.md)  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
