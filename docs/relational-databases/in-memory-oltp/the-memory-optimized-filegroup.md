---
title: "メモリ最適化ファイルグループ | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14106cc9-816b-493a-bcb9-fe66a1cd4630
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 039fb20caa7000d9253f88016f756b0cf7babaa5
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="the-memory-optimized-filegroup"></a>メモリ最適化ファイルグループ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
メモリ最適化テーブルを作成するには、まずメモリ最適化ファイルグループを作成する必要があります。 メモリ最適化ファイル グループには 1 つ以上のコンテナーが含まれています。 各コンテナーには、データ ファイルかデルタ ファイル、あるいはその両方が含まれています。  
  
 SCHEMA_ONLY テーブルから取得したデータ行は持続的ではなく、メモリ最適化テーブルに対応するメタデータおよびネイティブ コンパイル ストアド プロシージャは従来型のカタログに格納されますが、メモリ最適化テーブルを含むデータベースを一貫した環境で提供できるように、 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] エンジンでは引き続き、SCHEMA_ONLY メモリ最適化テーブルに対応するメモリ最適化ファイルグループが必要です。  
  
 メモリ最適化ファイルグループは FILESTREAM ファイルグループをベースとしていますが、次の違いがあります。  
  
-   メモリ最適化ファイルグループは、データベースごとに 1 つだけ作成できます。 memory_optimized_data を含めることにより、このファイルグループに明示的にマークを付ける必要があります。 データベースを作成するときにファイルグループを作成することも、後でファイルグループを追加することもできます。  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA  
    ```  
  
-   `MEMORY_OPTIMIZED_DATA` ファイル グループに 1 つ以上のコンテナーを追加する必要があります。 例 :  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod  
    ```  
  
-   メモリ最適化ファイルグループを作成するために、ファイルストリームを有効にする必要はありません ([FILESTREAM の有効化と構成](../../relational-databases/blob/enable-and-configure-filestream.md))。 ファイルストリームへのマッピングは、 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] エンジンによって実行されます。  
  
-   メモリ最適化ファイルグループに対して、新しいコンテナーを追加することができます。 持続性のあるメモリ最適化テーブルのために必要な記憶域を拡張するため、および複数のコンテナーにまたがって IO を分散するために、新しいコンテナーが必要になることがあります。  
  
-   メモリ最適化ファイルグループでのデータの移動は、AlwaysOn 可用性グループ構成によって最適化されます。 セカンダリ レプリカに送信されるファイルストリームのファイルとは異なり、メモリ最適化ファイルグループ内のチェックポイント ファイル (データとデルタの両方) は、セカンダリ レプリカには送信されません。 データ ファイルとデルタ ファイルは、セカンダリ レプリカのトランザクション ログを使用して作成されます。  
  
メモリ最適化ファイル グループには、次の制限が適用されます。  
  
-   メモリ最適化ファイルグループを作成した後、それを削除する唯一の方法はデータベースを削除することです。 運用環境において、メモリ最適化ファイルグループの削除が必要になることはほとんどありません。  
  
-   空ではないコンテナーを削除することや、メモリ最適化ファイルグループ内でデータ ファイルとデルタ ファイルのペアを別のコンテナーに移動することはできません。  
  
-   コンテナーに対して `MAXSIZE` を指定することはできません。  
  
## <a name="configuring-a-memory-optimized-filegroup"></a>メモリ最適化ファイルグループの構成  
 メモリ最適化ファイルグループ内で複数のコンテナーを作成し、それらを複数のドライブに分散して、データをメモリにストリーミングするための帯域幅をより多く確保することを考慮する必要があります。  
  
 記憶域を構成する場合には、持続性のあるメモリ最適化テーブルの 4 倍のサイズの空きディスク領域を指定する必要があります。 また、I/O サブシステムが、対象のワークロードで必要な IOPS をサポートしていることを確認する必要もあります。 データ ファイルとデルタ ファイルのペアが特定の IOPS で作成される場合は、格納操作とマージ操作のために、3 倍の IOPS が必要です。 メモリ最適化ファイルグループに 1 つ以上のコンテナーを追加する方法で、記憶域容量と IOPS を追加できます。  
  
## <a name="see-also"></a>参照  
 [メモリ最適化オブジェクト用ストレージの作成と管理](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
 [データベース ファイルとファイル グループ](../../relational-databases/databases/database-files-and-filegroups.md) 
  
