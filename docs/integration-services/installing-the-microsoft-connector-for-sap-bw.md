---
title: "Microsoft Connector for SAP BW のインストール | Microsoft Docs"
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
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f1d2716714e810143e17d3435c61de394e82b9bc
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="installing-the-microsoft-connector-for-sap-bw"></a>Microsoft Connector for SAP BW のインストール
  [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW for SQL Server 2016 は、SQL Server 2016 の Feature Pack のコンポーネントです。 Connector for SAP BW およびそのドキュメントをインストールするには、 [SQL Server 2016 Feature Pack Web ページ](http://go.microsoft.com/fwlink/?LinkId=746297)からインストーラーをダウンロードして実行します。  
  
> [!IMPORTANT]  
>  Microsoft Connector for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。 SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。  
  
> [!IMPORTANT]  
>  SAP Netweaver BW からデータを抽出するには、追加の SAP のライセンスが必要です。 これらの要件を確認するには、SAP にお問い合わせください。  
  
## <a name="required-sap-files"></a>必要な SAP のファイル  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW を使用するために、SAP フロント エンド ソフトウェア (SAP GUI) をローカル コンピューターにインストールする必要はありません。  
  
 ただし、SAP の .NET コネクタ ファイルである librfc32.dll を、Windows フォルダー内の system サブフォルダーにコピーする必要があります (通常は、このフォルダーの場所は、 **C:\Windows\system32**です)。  
  
## <a name="considerations-for-64-bit-computers"></a>64 ビット コンピューターに関する注意事項  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW は、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows の 64 ビット バージョンを完全サポートしています。 64 ビット コンピューターでは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector for SAP BW に次の要件があります。  
  
-   任意の 64 ビット Windows オペレーティング システムで、パッケージを 64 ビット モードで実行するには、SAP GUI ファイルの 64 ビット バージョンである librfc32.dll を、Windows フォルダー内の **system32** フォルダーにコピーします (通常は、このファイルの場所は、 **C:\Windows\system32**です)。  
  
-   任意の 64 ビット Windows オペレーティング システムで、パッケージを 32 ビット モードで実行するには、SAP GUI ファイルである librfc32.dll を、Windows フォルダー内の **SysWow64** フォルダーにコピーします (通常は、このフォルダーの場所は、 **C:\Windows\SysWow64**です)。  
  
  
