---
title: "手順 1: 新しい Integration Services プロジェクトの作成 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: f14521b5-941e-443b-8f5e-385f98e37fbf
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 771c956d5e33dfc6b91ff70acfc387244d2513d6
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="lesson-1-1---creating-a-new-integration-services-project"></a>レッスン 1-1 - 新しい Integration Services プロジェクトの作成
[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] でパッケージを作成するには、まず [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを作成する必要があります。 このプロジェクトには、データ変換ソリューションで使用するオブジェクト (データ ソース、データ ソース ビュー、パッケージ) のテンプレートが用意されています。  
  
この [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] チュートリアルで作成するパッケージは、ロケール依存型データの値を解釈します。 コンピューターが地域オプション [英語 (米国)] を使用するように構成されていない場合は、パッケージ内で追加のプロパティを設定する必要があります。 レッスン 2 から 5 では、レッスン 1 で作成したパッケージをコピーして使用します。コピーしたパッケージでは、ロケール依存型のプロパティを更新する必要はありません。  
  
> [!NOTE]  
> このチュートリアルには、Microsoft SQL Server Data Tools が必要です。  
>   
> SQL Server Data Tools のインストールの詳細については、「[SQL Server Data Tools のダウンロード](http://msdn.microsoft.com/data/hh297027)」を参照してください。  
  
### <a name="to-create-a-new-integration-services-project"></a>新しい Integration Services プロジェクトを作成するには  
  
1.  **[スタート]** メニューで、 **[すべてのプログラム]**、 **[Microsoft SQL Server]**の順にポイントし、 **[SQL Server Data Tools]**をクリックします。  
  
2.  新しい **プロジェクトを作成するため、** [ファイル] **メニューの**[新規作成] **をポイントし、** [プロジェクト] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] をクリックします。  
  
3.  **[新しいプロジェクト]** ダイアログ ボックスの **[インストールされているテンプレート]** で **[ビジネス インテリジェンス]**を展開し、 **[テンプレート]** ペインで **[Integration Services プロジェクト]** を選択します。  
  
4.  **[名前]** ボックスに表示されている既定の名前を「 **SSIS Tutorial**」に変更します。 必要に応じて、 **[ソリューションのディレクトリを作成]** チェック ボックスをオフにします。  
  
5.  既定の場所をそのまま使用するか、 **[参照]** をクリックして使用するフォルダーを指定します。 **[プロジェクトの場所]** ダイアログ ボックスで、目的のフォルダーをクリックして **[フォルダーの選択]**をクリックします。  
  
6.  **[OK]** をクリックします。  
  
    既定では、 **Package.dtsx**という名前の空のパッケージが作成され、SSIS パッケージの下のプロジェクトに追加されます。  
  
7.  **ソリューション エクスプローラー** で **[Package.dtsx]**を右クリックし、 **[名前の変更]**をクリックします。表示されている既定のパッケージ名を「 **Lesson 1.dtsx**」に変更します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[手順 2: フラット ファイル接続マネージャーの追加と構成](../integration-services/lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
