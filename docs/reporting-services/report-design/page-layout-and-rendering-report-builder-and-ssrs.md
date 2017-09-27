---
title: "ページ レイアウトとレンダリング (レポート ビルダーおよび SSRS) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2358653-35bc-4496-810a-d3ccf02f229f
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d688ed124a419017e97d405d7f5bd80e6e3bf530
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="page-layout-and-rendering-report-builder-and-ssrs"></a>ページ レイアウトとレンダリング (レポート ビルダーおよび SSRS)
ページ レイアウト、改ページ、用紙サイズなど、意図したとおりのレポートを作成できるように、ページ分割されたレポートに関する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の表示拡張機能について説明します。 

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート ビルダーやレポート デザイナーのプレビュー ペインでレポートを表示すると、レポートは最初に HTML レンダラーによってレンダリングされます。 その後は、Excel ファイルや CSV (コンマ区切り) ファイルなどの別の形式にレポートをエクスポートできます。 エクスポートしたレポートは、Excel での詳細な分析や、CSV ファイルをインポートして使用できるアプリケーションのデータ ソースに使用できます。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、レポートをさまざまな形式にエクスポートするための一連のレンダラーが含まれています。 各レンダラーには、レポートのレンダリング時の適用ルールがあります。 レポートを別のファイル形式にエクスポートする場合、Adobe Acrobat (PDF) レンダラーなど、特に物理的なページ サイズに基づくページ割り付けを使用するレンダラーの場合、レンダリング ルールの適用後、レポートのレイアウトを変更しないと、エクスポートしたレポートを正しい体裁で表示、印刷できない場合があります。  
  
 エクスポートしたレポートが最適な外観になるまでには、反復的な作業が伴うことも少なくありません。つまり、レポート ビルダーやレポート デザイナーでレポートを作成、プレビューした後、必要な形式にエクスポートし、エクスポートしたレポートを見直してから、レポートに変更を加えるという作業です。  
    
##  <a name="PageLayout"></a> レポート アイテム  
 レポート アイテムとは、さまざまな種類のレポート データに関連付けられたレイアウト要素のことです。 
 
* テーブル、マトリックス、一覧、グラフ、およびゲージは、それぞれレポート データセットにリンクするデータ領域のレポート アイテムです。 レポートの処理時、データ領域はレポート ページの横と下方に拡大され、データを表示します。 

その他のレポート アイテムは 1 つの項目にリンクし、これを表示します。 
* **画像** レポート アイテムは画像にリンクします。 
* **テキスト ボックス** レポート アイテムには、タイトルなどの単純なテキストか、埋め込みフィールド、レポート パラメーター、またはデータセット フィールドに対する参照を格納できる式のいずれかが含まれます。 
* **線** および **四角形** レポート アイテムは、レポート ページ上に簡単なグラフィカル要素を表示します。 また、 **四角形** は、他のレポート アイテムのコンテナーとしても使用できます。 

レポートにはサブレポートを含めることもできます。  
  
## <a name="page-layout"></a>ページ レイアウト

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]では、レポート アイテムをデザイン画面の任意の場所に配置できます。 スナップ線とサイズ変更ハンドルを使用すると、レポート アイテムを対話形式で配置したり、その初期形状の拡大および縮小を行ったりできます。 データ領域にさまざまなデータ セットを配置したり、異なる形式の同じデータを並べて配置したりすることもできます。 デザイン画面にレポート アイテムを配置すると、レポート アイテムのサイズと形状は既定で設定され、その他のすべてのレポート アイテムとの初期関係も既定で設定されます。 
 
 他のレポート アイテムの内部にレポート アイテムを配置して、より複雑なレポートのデザインを作成できます。 たとえば、テーブル セル内のグラフや画像、テーブル セル内の表、四角形内の複数の画像などです。 レポートに目的の編成と外観を提供することに加えて、四角形などのレポート アイテムをコンテナーに配置することにより、レポート アイテムをレポート ページにどのように表示するかを制御します。  
  
 レポートは、各ページに同じヘッダーとフッターを付けて複数のページにわたって表示できます。 また、画像や線などのグラフィック要素を使用することも、式に基づいて複数のフォント、色、およびスタイルを設定することもできます。  
  
##  <a name="ReportSections"></a> レポート セクション  
 レポートは、3 つの主要なセクションである " *ページ* " ヘッダーと " *ページ* " フッター (いずれも任意)、およびレポート本文で構成されます。 " *レポート* " のヘッダーとフッターはレポートの個別のセクションではなく、レポート本文の上部および下部に配置されるレポート アイテムで構成されます。 ページ ヘッダーとページ フッターは、レポートの各ページの上部と下部に同じ内容を繰り返し配置します。 ヘッダーとフッターには、画像、テキスト ボックス、直線などのレポート アイテムを配置できます。 レポート本文には、すべての種類のレポート アイテムを配置できます。  
  
 レポート アイテムのプロパティを設定して、ページ上でのレポート アイテムの表示および非表示を初期設定できます。 データ領域の行、列、またはグループの表示プロパティを設定したり、ユーザーがレポート データの表示と非表示を対話形式で設定するための切り替えボタンを配置したりできます。 表示の設定や表示の初期設定は、レポート パラメーターに基づく式などを使用することで設定できます。  
  
 レポートの処理時、レポート データはレポート レイアウト要素と結合し、この結合したデータがレポート レンダラーに送信されます。 レポート レンダラーは、定義済みのレポート アイテム拡張規則に従い、各ページにどのくらいの量のデータを配置できるかを判断します。 使用するレンダラーに最適化された見やすいレポートをデザインするには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]におけるページ割り付けの制御規則を理解しておく必要があります。 詳細については、「 [Reporting Services の改ページ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)」を参照してください。  
  
##  <a name="RenderingExtensions"></a> レンダラー  
 Reporting Services には、表示拡張機能とも呼ばれる一連のレンダラーが付属しています。レンダラーを使用して、レポートをさまざまな形式にエクスポートできます。 レンダラーには、次の 3 種類があります。  
  
-   **データ レンダラー** データ レンダラーは、すべての書式設定とレイアウト情報をレポートから取り除いたうえで、データのみを表示します。 生成されたファイルを使用して、生のレポート データを別のファイル形式 (Excel、他のデータベース、XML データ メッセージ、カスタム アプリケーションなど) にインポートできます。 利用可能なデータ レンダラーとしては CSV と XML があります。  
  
    > [!NOTE]  
    >  異なる形式に直接エクスポートすることはできませんが、Atom 表示拡張機能によってレポートからデータ ファイルを生成できます。  
  
-   **ソフト改ページ レンダラー** : ソフト改ページ レンダラーでは、レポートのレイアウトと書式設定が維持されます。 生成されたファイルは、Web ページなど、画面上での閲覧や配信に最適化されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word、Web アーカイブ (MHTML)、HTML などのソフト改ページ レンダラーがあります。  
  
-   **ハード改ページ レンダラー** : ハード改ページ レンダラーでは、レポートのレイアウトと書式設定が維持されます。 生成されたファイルは、一貫した印刷結果を提供すること、または、レポートを印刷物のような形でオンライン配信する際の見やすさを優先して最適化されます。 TIFF と PDF のハード改ページ レンダラーが利用できます。  
  
 レポートをレポート ビルダーまたはレポート デザイナーでプレビューすると、または [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーでレポートを実行すると、レポートは常にまず HTML で表示されます。 レポートを実行した後、そのレポートを別のファイル形式にエクスポートすることができます。 詳しくは、「 [レポートのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)におけるページ割り付けの制御規則を理解しておく必要があります。  
  
##  <a name="RenderingBehaviors"></a> レンダリングの動作  
 選択したレンダラーによっては、レポートをレンダリングする際に、特定のルールが適用されます。 レポート アイテムが 1 ページにまとめられる際の方法は、次に示す要因の組み合わせによって決まります。  
  
-   レンダリングの規則。  
-   レポート アイテムの幅と高さ。  
-   レポート本文のサイズ。  
-   ページの幅と高さ。  
-   レンダラー固有の改ページ調整。  
  
 たとえば、HTML 形式や MHTML 形式としてレンダリングされたレポートは、コンピューター画面での操作性を重視して最適化され、ページの長さは固定的ではありません。  
  
 詳細については、「[レンダリングの動作 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md)」を参照してください。  
   
##  <a name="Pagination"></a> ページ割り付け  
 ページ割り付けとは、レポートに含まれるページ数と、ページ上でのレポート アイテムの配置方法をいいます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] でのページ割り付けは、レポートの閲覧と作成に使用する表示拡張機能のほか、レポートに使用する改ページのオプションと同一ページ表示のオプションによって異なります。  
  
 レポート作成に使用するレンダラーに最適化された、ユーザーにとって見やすいレポートをデザインするには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]における改ページの制御規則を理解しておく必要があります。 **データ** 表示拡張機能および **ソフト ページ** 表示拡張機能を使ってエクスポートされたレポートは、通常、改ページの影響を受けません。 データ表示拡張機能を使用した場合、レポートは、XML 形式または CSV 形式の表形式の行セットとしてレンダリングされます。 レポート データを使用可能な形でエクスポートするには、レンダリング時に、レポートからフラットな表形式の行セットに適用されるルールを理解しておく必要があります。  
  
 **ソフト ページ** 表示拡張機能 (HTML 表示拡張機能など) を使用するとき、レポートがどのような体裁で印刷されるか、また、PDF などのハード ページ レンダラーを使用した場合はどのように表示されるかを確認したい場合があります。 レポート ビルダーおよびレポート デザイナーでは、レポートの作成時や更新時にレポートをプレビューしたりエクスポートしたりできます。  
  
 レポートのレイアウトや物理的なページ サイズに最も大きく影響するのは、**ハード ページ** レンダラーです。 詳しくは、「[Reporting Services の改ページ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)」をご覧ください。  
   
##  <a name="HowTo"></a> 操作方法に関するトピック  
 レポートでページ割り付けを扱う際の詳細な手順を紹介しているトピックの一覧を次に示します。  
  
-   [改ページの追加 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/add-a-page-break-report-builder-and-ssrs.md)  
  
-   [複数のページへの行および列ヘッダーの表示 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)  
  
-   [ページ ヘッダーまたはページ フッターの追加および削除 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/add-or-remove-a-page-header-or-footer-report-builder-and-ssrs.md)  
  
-   [レポートのスクロール時にヘッダーを表示したままにする &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md)  
  
-   [ページ番号またはその他のレポート プロパティの表示 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/display-page-numbers-or-other-report-properties-report-builder-and-ssrs.md)  
  
-   [最初のページまたは最後のページでページ ヘッダーまたはページ フッターを非表示にする &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/hide-a-page-header-or-footer-on-the-first-or-last-page-report-builder-and-ssrs.md)  
  
##  <a name="InThisSection"></a> このセクションの内容  
 以下のトピックでは、ページ レイアウトとレンダリングに関する詳細情報について説明します。  
  
 [ページ ヘッダーとページ フッター &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/page-headers-and-footers-report-builder-and-ssrs.md)  
 レポート ヘッダーおよびレポート フッターに関する情報のほか、レポート ヘッダーおよびレポート フッターを使用してページ割り付けを制御する方法について説明します。  
  
 [改ページ、見出し、列、および行の制御 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs.md)  
 改ページの使用に関する情報を提供します。  
  
## <a name="see-also"></a>参照  
 [さまざまなレポート表示拡張機能の対話機能 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-builder/interactive-functionality-different-report-rendering-extensions.md)   
 [レポートのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)  
  
  