---
title: "Integration Services バージョンのサイド バイ サイド インストール | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability and coexistence [Integration Services]
- Integration Services, interoperability and coexistence
ms.assetid: edfbcd56-012f-462e-a542-95491394fda9
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b14e919cc180e8934b0cf9435d8d286c6468ccc2
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="installing-integration-services-versions-side-by-side"></a>Integration Services バージョンのサイド バイ サイド インストール
  Integration Services (SSIS) は、   
      [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 前のバージョンの SSIS とサイド バイ サイドでインストールできます。 このトピックでは、サイド バイ サイド インストールの制限事項について説明します。  
  
## <a name="designing-and-maintaining-packages"></a>パッケージの設計と管理  
 SQL Server 2016、SQL Server 2014、または SQL Server 2012 を対象とするパッケージを設計および管理するには、Visual Studio 2015 用の SQL Server Data Tools (SSDT) を使用します。 SSDT を入手する方法については、「 [最新の SQL Server Data Tools のダウンロード](../../ssdt/download-sql-server-data-tools-ssdt.md)」を参照してください。  
  
 Integration Services プロジェクトのプロパティ ページでは、 **[構成プロパティ]** の **[全般]**タブで **[TargetServerVersion]** プロパティを選択し、[SQL Server 2016]、[SQL Server 2014]、または [SQL Server 2012] を選択します。  
  
|SQL Server の対象バージョン|SSIS パッケージの開発環境|  
|----------------------------------|-----------------------------------------------|  
|2016|Visual Studio 2015 用 SQL Server Data Tools|  
|2014|Visual Studio 2015 用 SQL Server Data Tools<br /><br /> 内の複数の<br /><br /> SQL Server Data Tools - Business Intelligence for Visual Studio 2013|  
|2012|Visual Studio 2015 用 SQL Server Data Tools<br /><br /> 内の複数の<br /><br /> SQL Server Data Tools - Business Intelligence for Visual Studio 2012|  
|2008|SQL Server 2008 の Business Intelligence Development Studio|  
  
 既存のパッケージを既存のプロジェクトに追加すると、パッケージは、プロジェクトの対象となる形式に変換されます。  
  
## <a name="running-packages"></a>パッケージの実行  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンの **dtexec** ユーティリティまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用すると、以前のバージョンの開発ツールで作成された Integration Services パッケージを実行できます。 この [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ツールは、以前のバージョンの開発ツールで開発されたパッケージを読み込むときに、メモリ内のパッケージを、 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] が使用するパッケージに一時的に変換します。 パッケージに問題があり、適切に変換できない場合、その問題が解決されるまで、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ツールでパッケージを実行することはできません。 詳細については、「 [Integration Services パッケージのアップグレード](../../integration-services/install-windows/upgrade-integration-services-packages.md)」を参照してください。  
  
  
