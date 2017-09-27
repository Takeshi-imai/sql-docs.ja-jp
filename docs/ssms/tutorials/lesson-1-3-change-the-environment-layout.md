---
title: "環境レイアウトの変更 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: ce118ee5-70e2-472e-8e09-7ed3bfed59fa
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 5db067d5a2fe5bbf9953484c9a999ed7b1fcddae
ms.openlocfilehash: b09f254256c4b9a01b99bfe77768a28185f5ffd9
ms.contentlocale: ja-jp
ms.lasthandoff: 07/31/2017

---
# <a name="lesson-1-3---change-the-environment-layout"></a>レッスン 1-3 - 環境レイアウトの変更
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の各コンポーネントは画面スペースを共有しています。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] コンポーネントを閉じる、非表示にする、または移動することにより、画面スペースをさらに確保できます。 このページの実習では、コンポーネントを別の場所に移動します。  
  
## <a name="closing-and-hiding-components"></a>コンポーネントを閉じる、または非表示にする  
  
#### <a name="to-practice-closing-hiding-and-reopening-component-windows"></a>コンポーネント ウィンドウを閉じる、非表示にする、または再表示するには  
  
1.  登録済みサーバーを非表示にするには、[登録済みサーバー] の右上にある **閉じる** ボタンをクリックします。 [登録済みサーバー] が閉じます。  
  
2.  オブジェクト エクスプローラーで、 **[自動的に隠す]** (押しピン型のボタン) をクリックします。 オブジェクト エクスプローラーが画面左側に最小化されます。  
  
3.  [オブジェクト エクスプローラー] のタイトル バーの上にマウス カーソルを移動します。 オブジェクト エクスプローラーが再び表示されます。  
  
4.  押しピンボタンをもう一度クリックすると、オブジェクト エクスプローラーが開いたまま固定されます。  
  
5.  **[表示]** メニューの **[登録済みサーバー]** をクリックすると、[登録済みサーバー] が再び表示されます。  
  
## <a name="moving-components"></a>コンポーネントの移動  
[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] のコンポーネントは移動が可能です。また、さまざまな構成でドッキングすることができます。  
  
#### <a name="to-practice-moving-components"></a>コンポーネントを実際に移動するには  
  
1.  [登録済みサーバー] のタイトル バーをクリックし、ドキュメント ウィンドウの中央にドラッグします。 コンポーネントのドッキングが解除され、マウスを離すまでフローティング状態になります。  
  
2.  [登録済みサーバー] を画面上のさまざまな場所にドラッグしてみましょう。 ドッキングできる場所は複数あり、その場所に移動すると青色のドッキング情報が表示されます。 各矢印は、その場所にコンポーネントをドロップするとウィンドウがドッキングされることを示します。矢印の向きに応じて、フレームの上部、下部、または左右にドッキングできます。 いずれかの矢印の上にカーソルを移動すると、ドッキング先の領域が暗色表示されます。 中央の円は、コンポーネントが他のコンポーネントとスペースを共有することを示します。 中央部分にドロップすると、使用可能なコンポーネントがタブとしてフレームに表示されます。  
  
## <a name="undocking-components"></a>コンポーネントのドッキング解除  
[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] コンポーネントの表示をカスタマイズできます。  
  
#### <a name="to-dock-and-undock-components"></a>コンポーネントのドッキングとドッキング解除を行うには  
  
1.  [オブジェクト エクスプローラー] のタイトル バーを右クリックすると、次のメニュー オプションが表示されます。  
  
    -   Float  
  
    -   ドッキング  
  
    -   タブ付きドキュメントとしてドッキング  
  
    -   [自動的に隠す]  
  
    -   [非表示]  
  
    これらのオプションは、 **[ウィンドウ]** メニューまたはツール バーの下矢印からも選択できます。  
  
2.  オブジェクト エクスプローラーのドッキングを解除するには、[オブジェクト エクスプローラー] のタイトル バーをダブルクリックします。  
  
3.  オブジェクト エクスプローラーをドッキングするには、Ctrl キーを押しながらタイトル バーをもう一度ダブルクリックします。  
  
4.  [オブジェクト エクスプローラー] のタイトル バーをクリックし、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]の右端までドラッグします。 オブジェクト エクスプローラーをドラッグすると、ウィンドウをドッキングできる場所を示すガイドのひし形が表示されます。 オブジェクト エクスプローラーをガイドのひし形の上にドラッグし、ウィンドウがどのように配置されるかを確認します。 ガイドのひし形の上にあるオブジェクト エクスプローラーを [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]の右端までドラッグします。 ツール ウィンドウをドラッグする場合、ドッキングの効果を確認するかウィンドウをドッキングするには、カーソルをガイドのひし形の上に配置する必要があります。  
  
5.  オブジェクト エクスプローラーは Management Studio の上下にも移動できます。 オブジェクト エクスプローラーをウィンドウの元の位置、つまり左端にあるガイドのひし形にドラッグ アンド ドロップします。  
  
6.  [オブジェクト エクスプローラー] のタイトル バーを右クリックし、 **[非表示]**をクリックします。  
  
7.  **[表示]** メニューの **[オブジェクト エクスプローラー]** をクリックすると、ウィンドウが再び表示されます。  
  
8.  オブジェクト エクスプローラーのドッキングを解除するには、オブジェクト エクスプローラーのタイトル バーを右クリックし、 **[フローティング]** をクリックします。  
  
9. 既定の構成に戻すには、 **[ウィンドウ]** メニューの **[ウィンドウ レイアウトのリセット]**をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[クエリ ウィンドウの表示](../../tools/sql-server-management-studio/lesson-1-4-display-the-query-window.md)  
  
  
  
