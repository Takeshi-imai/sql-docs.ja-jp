---
title: "SSMA の SAP ASE (SybaseToSQL) のインストール |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/29/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8d5a4ce6-b747-46e3-9184-645d56e8b35c
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 508af2c209711c6063ee58243a29066323b641f8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="installing-ssma-for-sap-ase-sybasetosql"></a>SSMA の SAP ASE (SybaseToSQL) のインストール
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) の SAP Adaptive Server Enterprise (ASE) を SAP ASE からの移行の実行に使用するクライアント アプリケーションから成る[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。 移行されたデータベースのデータの移行と ASE システム関数の使用をサポートする拡張機能パックも含まれています。  
  
移行手順を実行するコンピューターにクライアント アプリケーションをインストールします。 実行しているコンピューターに拡張機能パック ファイルのインストール[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]でホストされるようには、データベースを移行します。  
  
## <a name="upgrading-ssma-for-sap-ase"></a>SAP ASE for SSMA をアップグレードします。  
SAP ASE for SSMA の以降のバージョンにアップグレードする場合は、クライアントとサーバーの拡張機能パックをアンインストールする必要があります最初。 新しいバージョンをインストールします。  
  
SAP ASE の SSMA の以前のバージョンからプロジェクトを開く場合 SSMA は、プロジェクトを新しいバージョンに変換するように求めます。 をクリックして**はい**SSMA の新しいバージョンでプロジェクトを使用します。  
  
## <a name="contents"></a>目次  
  
|[アーティクル]|Description|  
|---------|---------------|  
|[SAP ASE クライアント &#40; を SSMA をインストールします。SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)|SSMA for SAP ASE クライアントをインストールするための手順と情報を提供します。|  
|[SQL Server &#40; SSMA コンポーネントをインストールします。SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)|インスタンスで拡張機能パックをインストールするための手順と情報を提供[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。|  
|[SAP ASE コンポーネント &#40; に対して SSMA を削除します。SybaseToSQL &#41;](../../ssma/sybase/removing-ssma-for-sybase-components-sybasetosql.md)|プログラムと拡張機能パックのクライアントをアンインストールするための手順を説明します。|  
  
## <a name="see-also"></a>参照  
[SAP ASE データベース Azure SQL データベース &#40; SQL Server - への移行SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
