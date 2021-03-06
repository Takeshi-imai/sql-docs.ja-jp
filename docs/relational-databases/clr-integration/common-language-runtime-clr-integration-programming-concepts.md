---
title: "共通言語ランタイム (CLR) 統合のプログラミングの概念 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- CLR [SQL Server] See common language runtime [SQL Server]
- Database Engine [SQL Server], .NET Framework
- .NET Framework [SQL Server], Database Engine programming
- common language runtime [SQL Server]
- .NET Framework [SQL Server]
ms.assetid: 951bf851-3e6e-4361-ae6a-2bcd5b837ebd
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ef0f1548b77e570bf41c8a5d0b720794e2329918
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="common-language-runtime-clr-integration-programming-concepts"></a>CLR (共通言語ランタイム) 統合のプログラミング概念
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、.NET Framework for [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows の CLR (共通言語ランタイム) コンポーネントが統合されました。 つまり、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET や [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# などの .NET Framework 言語を使用して、ストアド プロシージャ、トリガー、ユーザー定義型、ユーザー定義関数、ユーザー定義集計、およびストリーミング テーブル値関数を記述できるようになります。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] における CLR プログラミングのためのコア機能は、Microsoft.SqlServer.Server 名前空間に存在します。 ただし、Microsoft.SqlServer.Server 名前空間については、.NET Framework SDK ドキュメントをご覧ください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックには、このドキュメントが含まれていません。  
  
> [!IMPORTANT]  
>  既定では、.NET Framework は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と共にインストールされますが、.NET Framework SDK はインストールされません。 SDK がコンピューターにインストールされていない場合やオンライン ブックに含まれていない場合は、このセクションにある SDK のコンテンツへのリンクが機能しません。 .NET Framework SDK をインストールしてください。 インストールした後、SDK をオンライン ブック コレクションと目次に追加」の指示に従って[、.NET Framework SDK をインストールする](http://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)です。  
  
> [!NOTE]  
>  CLR ユーザー関数などの CLR 機能は、*いない*Azure SQL データベースでサポートされています。  
  
 次の表は、このセクションのトピックを一覧表示します。  
  
 [共通言語ランタイム &#40;です。CLR &#41;統合の概要](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md)  
 CLR の概要を簡単に紹介し、このテクノロジが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用される方法と理由について説明します。 CLR を使用してデータベース オブジェクトを作成する利点についても説明します。  
  
 [アセンブリ &#40;データベース エンジン&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではなく、[!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework CLR (共通言語ランタイム) がサポートするマネージ コード言語の 1 つを使用して作成された関数、ストアド プロシージャ、トリガー、ユーザー定義集計、ユーザー定義型の配置に、[!INCLUDE[tsql](../../includes/tsql-md.md)] でアセンブリがどのように使用されるかについて説明します。  
  
 [共通言語ランタイム &#40; によるデータベース オブジェクトの構築CLR &#41;統合](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md)  
 CLR を使用して作成できるオブジェクトの種類について説明し、CLR データベース オブジェクトの作成要件を確認します。  
  
 [CLR データベース オブジェクトからのデータ アクセス](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに格納されているデータに CLR ルーチンからアクセスする方法について説明します。  
  
 [CLR 統合のセキュリティ](../../relational-databases/clr-integration/security/clr-integration-security.md)  
 CLR 統合のセキュリティ モデルについて説明します。  
  
 [CLR データベース オブジェクトのデバッグ](../../relational-databases/clr-integration/debugging-clr-database-objects.md)  
 CLR データベース オブジェクトをデバッグする場合の制限事項と要件について説明します。  
  
 [CLR データベース オブジェクトを展開します。](../../relational-databases/clr-integration/deploying-clr-database-objects.md)  
 実稼働サーバーへのアセンブリの配置について説明します。  
  
 [CLR 統合アセンブリの管理](../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)  
 CLR 統合のアセンブリの作成および削除方法について説明します。  
  
 [マネージ データベース オブジェクトの監視とトラブルシューティング](../../relational-databases/clr-integration/monitoring-and-troubleshooting-managed-database-objects.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行されるマネージ データベース オブジェクトとアセンブリの監視およびトラブルシューティングに使用できるツールに関する情報を提供します。  
  
 [使用シナリオと例については、共通言語ランタイム &#40;です。CLR &#41;統合](http://msdn.microsoft.com/library/33aac25f-abb4-4f29-af88-4a0dacd80ae7)  
 CLR オブジェクトを使用する使用シナリオとコード サンプルについて説明します。  
  
## <a name="see-also"></a>参照  
 [アセンブリ &#40;データベース エンジン&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)   
 [.NET Framework SDK のインストール](http://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)  
  
  
