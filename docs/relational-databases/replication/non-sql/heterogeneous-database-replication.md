---
title: "異種データベース レプリケーション | Microsoft Docs"
ms.custom: 
ms.date: 08/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- heterogeneous database replication, about heterogeneous database replication
- replication [SQL Server], heterogeneous database replication
- heterogeneous database replication
ms.assetid: 3fd983ad-e206-45db-9054-417c9b5bb815
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 8cd44c8b384019418a2a913e5f8d13d82120eac2
ms.openlocfilehash: 5fae2c0c64f4aa703661792641dd99009562ba1a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/29/2017

---
# <a name="heterogeneous-database-replication"></a>異種データベース レプリケーション  
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、トランザクション レプリケーションとスナップショット レプリケーションに対する次の異種シナリオをサポートします。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーへのデータのパブリッシュ  

-   Oracle に対するデータのパブリッシュには次の制限があります。  
  | |2016 以前 |2017 以降 |
  |-------|-------|--------|
  |Oracle からのレプリケーション |Oracle 10g 以前のみをサポート |Oracle 10g 以前のみをサポート |
  |Oracle へのレプリケーション |Oracle 12c まで |サポートされていません |


 SQL Server 以外のサブスクライバーへの異種レプリケーションは推奨されません。 Oracle パブリッシングは推奨されません。 データを移動するには、変更データ キャプチャと [!INCLUDE[ssIS](../../../includes/ssis-md.md)]を使用してソリューションを作成します。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="publishing-data-from-oracle"></a>Oracle からのデータのパブリッシュ  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] スナップショット レプリケーションとトランザクション レプリケーションとほぼ同じ機能を使用し、同様の使いやすさで Oracle からのデータをパブリッシュできます。 この機能には、Oracle バージョン 10g 以前のバージョンが必要です。 Oracle からのデータのパブリッシュは、次のようなシナリオに適しています。  
  
|Scenario|説明|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework アプリケーションの配置|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 以外のデータベースからレプリケートされたデータを使用しながら、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Visual Studio および[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を使用して開発します。|  
|データ ウェアハウジング ステージング サーバー|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ステージング データベースと[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のデータベースとの同期を保ちます。|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|ソース システムの変更のレプリケーション中に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に対してアプリケーションをリアルタイムでテストします。 移行に問題がなければ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に切り替えます。|  
  
 詳細については、「[Oracle Publishing Overview](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)」 (Oracle パブリッシングの概要) を参照してください。  
  
## <a name="publishing-data-to-non-sql-server-subscribers"></a>SQL Server 以外のサブスクライバーへのデータのパブリッシュ  
 以下の[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のデータベースは、スナップショット パブリケーションとトランザクション パブリケーションに対するサブスクライバーとしてサポートされています。  
  
-   Oracle (Oracle がサポートするすべてのプラットフォーム用)  
  
-   IBM DB2 (AS400、MVS、Unix、Linux、および Windows 用)  
  
 詳細については、「 [Non-SQL Server Subscribers](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)」を参照してください。  
  
  
