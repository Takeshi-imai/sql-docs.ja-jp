---
title: "[オプション] ([環境]/[全般] ページ) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-menu
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.TOOLSOPTIONSPAGES.ENVIRONMENT.GENERAL
- VS.ToolsOptionsPages.Environment.SQLEnvironmentOptions
- DevLang-TSQL
ms.assetid: c32ccdb8-2cf8-4c78-b474-a3abd3dbbd13
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5ebd40ed9900768c2f239319f0b2874cc49c99de
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="options-environment---general-page"></a>[オプション] \([環境]/[全般] ページ)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] **[オプション]** ダイアログ ボックスを使用すると、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] スタートアップ アクション、全般的なウィンドウ管理オプション、およびその他の全般設定を構成できます。 **[ツール]** メニューの **[オプション]**をクリックし、 **[環境]** フォルダーを展開して **[全般]**をクリックします。  
  
## <a name="uielement-list"></a>UI 要素の一覧  
**[スタートアップ時]**  
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] の起動時に実行されるアクションを選択します。 使用可能なオプションは次のとおりです。  
  
-   **[オブジェクト エクスプローラーを開く]** 。接続を要求してからオブジェクト エクスプローラーを開きます。  
  
-   **[新しいクエリ ウィンドウを開く]** 。接続を要求してから SQL クエリ エディターを開きます。  
  
-   **[オブジェクト エクスプローラーと新しいクエリを開く]** 。接続を要求してから、その接続でオブジェクト エクスプローラーおよび SQL クエリ エディターの両方を開きます。  
  
-   **[空の環境を開く]** 。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] を開きますが、[SQL クエリ エディター] ウィンドウを表示せず、オブジェクト エクスプローラーをサーバーに接続しません。  
  
**[オブジェクト エクスプローラーのシステム オブジェクトを非表示にする]**  
このチェック ボックスをオンにすると、システム データベース、システム テーブル、システム ビュー、およびシステム ストアド プロシージャがオブジェクト エクスプローラーのツリー ビューから削除されます。 システム関数およびシステム型は非表示になりません。 このオプションは [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] のインスタンスにのみ適用され、既にオブジェクト エクスプローラーに接続されているサーバーに影響を与えません。  
  
## <a name="environment-layout"></a>[環境レイアウト]  
タブ付きドキュメントとマルチ ドキュメント インターフェイス (MDI) 環境モードを切り替えるには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] を閉じてから再度開く必要があります。  
  
**[タブ付きドキュメント]**  
このオプションをオンにすると、エディター内にタブの付いたドキュメント ウィンドウが表示されます。 タブ付きドキュメント ウィンドウは、開いている複数のドキュメントの編成と切り替えを行う場合に便利です。  
  
**[MDI 環境]**  
このオプションをオンにすると、MDI 環境でドキュメントが開きます。 MDI ドキュメント ウィンドウの利点は、タブ付きドキュメント環境でタブによって占有される画面領域を空き領域として確保できることです。 MDI モードでの作業時にドキュメントを切り替えるには、Ctrl + Tab キーを押すか、 **[ウィンドウ]** メニューのタイル オプションを使用します。  
  
## <a name="docked-tool-window-behavior"></a>[ドッキング ツール ウィンドウの動作]  
**[[閉じる] ボタンを、アクティブになっているタブに対してのみ実行する]**  
このチェック ボックスがオンになっている場合は、ドッキングしたセット内のすべてのツール ウィンドウではなく、現在フォーカスのあるツール ウィンドウのみを閉じることを指定します。 既定では、このチェック ボックスはオンになっています。  
  
**[[自動的に隠す] ボタンを、アクティブになっているタブに対してのみ実行する]**  
このチェック ボックスがオンになっている場合は、ドッキングしたセット内のすべてのツール ウィンドウではなく、現在フォーカスのあるツール ウィンドウのみが自動的に非表示になることを指定します。 既定では、このチェック ボックスはオフに設定されます。  
  
## <a name="display"></a>表示  
**[最近使用したファイルの一覧: n ファイルまで表示する]**  
**[ファイル]** メニューに表示される最新プロジェクトおよび最新ファイルの数をカスタマイズします。 1 ～ 24 の範囲の数値を入力します。 既定値は 4 です。 最近使用したスクリプト プロジェクトやファイル、その他のスクリプト プロジェクトを簡単に表示できます。  
  
