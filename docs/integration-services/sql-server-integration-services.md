---
title: SQL Server Integration Services | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- SSIS
helpviewer_keywords:
- SSIS
- DTS [Integration Services]
- SQL Server Integration Services
- Integration Services
- DTS [Integration Services], about Integration Services
- data integration [Integration Services]
- Data Transformation Services
ms.assetid: c4398655-5657-4ae4-a690-a380790fe84f
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 48d2b81acab290fc27ca351c8e630b8a9cfc5f77
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="sql-server-integration-services"></a>SQL Server Integration Services

 > 以前のバージョンの SQL Server に関連するコンテンツについては、「[SQL Server Integration Services](https://msdn.microsoft.com/library/ms141026(SQL.120).aspx)」をご覧ください。

[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] は、エンタープライズ レベルのデータ統合およびデータ変換ソリューションを構築するためのプラットフォームです。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] を使用すると、ファイルのコピーやダウンロード、イベントへの応答としての電子メール メッセージの送信、データ ウェアハウスの更新、データのクリーニングとマイニング、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のオブジェクトやデータの管理などにより、複雑なビジネスの問題を解決できます。 このパッケージは単独で使用することも、複雑なビジネス要件に対処するために他のパッケージと組み合わせて使用することもできます。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、XML データ ファイル、フラット ファイル、リレーショナル データ ソースなど、さまざまなソースのデータを抽出および変換して、1 つ以上のターゲットに読み込むことができます。<br /><br /> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] には、組み込みのタスクと変換の豊富なセット、パッケージを作成するためのツール、およびパッケージの実行と管理のための [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが含まれています。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のグラフィック ツールを使用すると、コードを 1 行も書かずにソリューションを作成することができます。また、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の広範なオブジェクト モデルを使用して、パッケージをプログラムによって作成することもできます。この場合は、カスタム タスクや他のパッケージ オブジェクトを使用できます。

## <a name="try-sql-server-and-sql-server-integration-services"></a>SQL Server および SQL Server Integration Services をお試しください
- [![Evaluation Center からのダウンロード](../includes/media/download2.png)](http://go.microsoft.com/fwlink/?LinkID=829477) [SQL Server 2017 または 2016 のダウンロード](https://www.microsoft.com/evalcenter/evaluate-sql-server)
- [![Evaluation Center からダウンロードする](../includes/media/download2.png)](../ssdt/download-sql-server-data-tools-ssdt.md) [SQL Server Data Tools (SSDT) のダウンロード](../ssdt/download-sql-server-data-tools-ssdt.md)
- [![Evaluation Center からダウンロードする](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) [SQL Server Management Studio (SSMS) のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)

##  <a name="infotipsql-servermediainfo-tippng-resources"></a>![info_tip](../sql-server/media/info-tip.png) リソース
-   [SSIS フォーラムのヘルプの表示](https://social.msdn.microsoft.com/Forums/home?forum=sqlintegrationservices)
-   [Stack Overflow のヘルプの表示](http://stackoverflow.com/questions/tagged/ssis)  
-   [SSIS チーム ブログのフォロー](https://blogs.msdn.microsoft.com/ssis/)
-   [問題と要求の報告機能](https://feedback.azure.com/forums/908035-sql-server)
-   [PC のドキュメントを入手](../sql-server/sql-server-help-installation.md)
