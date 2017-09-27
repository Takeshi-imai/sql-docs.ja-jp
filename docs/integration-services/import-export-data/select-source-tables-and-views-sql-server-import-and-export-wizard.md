---
title: "ソース テーブルとビュー (SQL Server インポートおよびエクスポート ウィザード) 選択 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.selectsourcetablesandviews.f1
ms.assetid: f60e1a19-2ea6-403c-89ab-3e60ac533ea0
caps.latest.revision: 96
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9a0c3c4fc8d41206ea077498dafb755e7b433a78
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="select-source-tables-and-views-sql-server-import-and-export-wizard"></a>[コピー元のテーブルおよびビューを選択] (SQL Server インポートおよびエクスポート ウィザード)
  テーブル全体をコピーするか、クエリを入力するかを指定した後に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードには **[コピー元のテーブルおよびビューを選択]**が表示されます。 このページでは、コピーする既存のテーブルとビューを選択します。 それから、新規または既存のコピー先テーブルにコピー元テーブルをマッピングします。 必要に応じて、個々の列のマッピングも確認し、サンプル データをプレビューします。

> [!TIP]
> 1 つ以上の SQL Server データベースまたはテーブルとビュー以外の SQL Server データベース オブジェクトをコピーした場合は、データベース コピー ウィザードを使用して、インポートおよびエクスポート ウィザードではなく。 詳細については、「 [データベース コピー ウィザードの使用](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
## <a name="screen-shot---if-youre-going-to-copy-tables"></a>スクリーン ショットのテーブルをコピーしようとしている場合  
 スクリーン ショットを次の例を示しています、 **[ソース テーブルおよびビュー**以前に選択したときに、ウィザードのページ、 **1 つまたは複数のテーブルまたはビューからデータをコピー** ] オプションを選択、 **テーブルのコピーまたはクエリの指定**ページ。 この一覧には、データ ソースで使用可能なすべてのテーブルとビューが表示されます。
 
この例では、**ソース**一覧には、AdventureWorks サンプル データベース内のすべてのテーブルが含まれています。 選択した行は、ユーザーがコピーすることを示しています、 **Sales.Customer**を新しいソースからテーブル**Sales.CustomerNew**先のテーブルです。 
   
 ![インポートおよびエクスポート ウィザードのテーブルの選択」ページ](../../integration-services/import-export-data/media/select-tables1.png "インポートおよびエクスポート ウィザードのテーブルの選択 ページ")
  
## <a name="screen-shot---if-you-provided-a-query"></a>クエリを指定した場合のスクリーン ショット  
 スクリーン ショットを次の例を示しています、 **ソース テーブルおよびビュー**以前に選択したときに、ウィザードのページ、**を転送するデータを指定するクエリを記述**オプション、で**テーブルのコピーを指定またはクエリ**ページ。 **ソース**一覧には、1 行だけ、項目がという名前が含まれています。`[Query]`で指定したクエリを表す、**ソース クエリを指定する**ページ。
 
この例では、ユーザーがクエリ結果を **Sales.CustomerNew** テーブルにコピーします。  
    
 ![インポートおよびエクスポート ウィザードのテーブルの選択」ページ](../../integration-services/import-export-data/media/select-tables2.png "インポートおよびエクスポート ウィザードのテーブルの選択 ページ")  

## <a name="select-source-and-destination-tables"></a>変換元のテーブルと変換先のテーブルの選択 
**変換元**  
チェック ボックスを使用して、コピー先にコピーできるテーブルとビューを一覧から選択します。 既定では、データ ソースのデータが変更なくコピーされます。 新しいレプリケーション先テーブルを作成する場合も、データ ソースからの変更なし - は、列とそのプロパティの一覧に新しいテーブルのスキーマがコピーされます。

クエリを指定した場合は、名前の項目が 1 つだけが一覧に`[Query]`です。 

**変換先**  
 変換元の各テーブルまたはクエリの一覧で変換先テーブルを選択するか、ウィザードで作成する新しいテーブルの名前を入力します。 既存の変換先テーブルを選択する場合、そのテーブルの列とデータ型は変換元テーブルと互換性がある必要があります。  

> [!NOTE]
> この時点でウィザードを一時停止し、外部ツール (  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]など) を使用して変換先データベースに新しいテーブルを手動で作成した場合、新しいテーブルは使用可能な変換先テーブルの一覧にすぐには表示されません。 変換先テーブルの一覧を最新の情報に更新するには、 **[変換先の選択]** ページに戻り、変換先データベースを再度選択して、使用可能なテーブルとビューの一覧を最新の情報に更新してから、もう一度 **[コピー元のテーブルおよびビューを選択]** ページに進みます。  

## <a name="optionally-review-column-mappings-and-preview-data"></a>必要に応じて、列マッピングを確認し、データをプレビュー
**マッピングの編集**   
必要に応じて、をクリックして**マッピングを編集する**を表示する、**列マッピング**選択したテーブルのダイアログ ボックス。 **[列マッピング]** ダイアログ ボックスを使用して、次のことを行います。
-   変換元と変換先の間の個々の列のマッピングを確認します。
-   列のサブセットのみをコピーするには、コピーしない列について **[無視]** を選択します。

詳細については、「 [列マッピング](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md)」を参照してください。  

**プレビュー**  
必要に応じて、をクリックして**プレビュー**サンプル内のデータを最大 200 行をプレビューする、**データのプレビュー**  ダイアログ ボックス。 プレビューで、コピーしたいデータがウィザードによってコピーされることを確認します。 詳細については、 [データのプレビュー](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md)に関するページを参照してください。  
  
データをプレビューした後で、ウィザードの前のページで選択したオプションを変更してもかまいません。 これらの変更を行うには、 **[コピー元のテーブルおよびビューを選択]** ページに戻り、 **[戻る]** をクリックし、選択の変更が可能な前のページに戻ります。  

## <a name="select-source-and-destination-tables-for-excel"></a>Excel の変換元のテーブルと変換先のテーブルの選択

### <a name="excel-source-tables"></a>Excel の変換元テーブル
Excel データ ソースの変換元テーブルとビューの一覧には、2 種類の Excel オブジェクトがあります。
-   **ワークシート**。 ワークシート名の末尾にはドル記号 ($) が付きます (例: **'Sheet1$'**)。
-   **名前付き範囲** 名前付き範囲 (ある場合) は名前別に表示されます。

特定の名前のない範囲のセル (たとえば、 **[Sheet1$A1:B4]**) との間でデータの読み込みを行う場合、クエリを記述する必要があります。 **[テーブルのコピーまたはクエリの指定]** ページに戻り、 **[転送するデータを指定するためのクエリを記述する]**を選択します。

#### <a name="prepare-the-excel-source-data"></a>Excel ソースのデータを準備します。
ソース テーブルとしてワークシートまたは範囲を指定した場合、ドライバーは、ワークシートまたは範囲の左上の空でない最初のセルから、 *連続した* セルのブロックを読み取ります。 その結果、ソース データに空行を含めることはできなくなります。 たとえば、列ヘッダーとデータ行の間に空行を含めることはできません。 ワークシートの一番上にタイトル行と空行があり、その後にデータ行がある場合、そのワークシートをクエリできません。 Excel では、データの範囲に名前を割り当て、ワークシートではなく名前付き範囲をクエリする必要があります。

### <a name="excel-destination-tables"></a>Excel 変換先テーブル
Excel にデータをエクスポートする場合、変換先として、次の 3 つのうちいずれかを指定できます。
-   **ワークシート。** ワークシートを指定するには、シート名の末尾に $ 文字を付加し、文字列を区切り文字で囲みます (例: **[Sheet1$]**)。
-   **名前付き範囲。** 名前付き範囲を指定するには、範囲名をそのまま使用します (例: **MyDataRange**)。
-   **名前のない範囲。** 名前のないセルの範囲を指定するには、シート名の末尾に $ 文字を付加し、範囲の指定を追加し、文字列を区切り文字で囲みます (例: **[Sheet1$A1:B4]**)。

## <a name="special-considerations-for-excel-sources-and-destinations"></a>Excel の変換元と変換先に関する特別な考慮事項
変換元または変換先として Excel を使用する場合、 **[列マッピング]** ページで **[マッピングの編集]** をクリックし、データ型マッピングを確認することをお勧めします。 

**Excel ブックのデータ型**。 Excel は一般的なデータベースではありません。 列に固定のデータ型がありません。 ウィザードで認識できる Excel のデータ型は、数値、通貨、ブール値、日時、文字列 (255 文字以下)、およびメモ (256 文字以上) のみです。 ウィザードでは、数 (既定では、最初の 8 行) の各列のデータ型を推測する既存の Excel データ ソース内の行をサンプリングします。

ウィザードで Excel との読み込み処理で明示的なデータ型変換を実行する必要がある場合、一般的に **[データ型マッピングの確認]** ページが表示されます。このページで、変換内容を確認できます。 これらの変換には次が含まれる可能性があります。
-   倍精度の Excel 数値列と他の型の数値列の列間の変換
-   255 文字の Excel 文字列の列と異なる長さの文字列の列間の変換
-   Unicode Excel 文字列の列と特定のコードページを使用して非 Unicode 文字列の列の間で変換します。

### <a name="special-considerations-for-excel-sources"></a>Excel の変換元に関する特別な考慮事項
**インポートされるデータの値が Null になります (値がなくなります)**。 ウィザード - によってサンプリングされた最初の 8 行でさまざまなデータ型を格納する Excel の列が表示されたらなど、数値と文字列値 - 混在ウィザード、列のデータ型として、ほとんどのデータ型を取得およびその contai セルに null 値を返しますその他の種類の n データです。 ウィザードのこの動作を変更する方法はありません。

**インポートされるデータの文字列が切り捨てられます**。 ウィザードで Excel の列にテキスト データが含まれていると判断されると、先頭 8 行でサンプリングされる最も長い値に基づいて列のデータ型 (文字列またはメモ) が選択されます。 ウィザードがサンプリングした行で 255 文字より長い値が検出されなかった場合、その列はメモ列ではなく、255 文字の文字列の列として扱われ、255 文字を超える値は切り捨てられます。 切り詰めなしのメモ列からデータをインポートするにはメモ列に、ウィザードによってサンプリングされたを含む最初の 8 行で 255 文字より長い、少なくとも 1 つの値が含まれているかどうかを確認する必要があります。

### <a name="special-considerations-for-excel-destinations"></a>Excel の変換先に関する特別な考慮事項
**既存の範囲を指定します**。 エラーが発生した範囲がある少ない場合、変換先として既存の範囲を指定すると*列*ソース データよりもします。 ただし、指定した範囲がある少ない場合*行*ソース データよりも、ウィザードが行の書き込みが続行し、新しい行の数と一致する範囲の定義を拡張します。

**メモ (ntext) データの保存**。 255 文字を超える文字列を Excel 列に正常に保存するには、変換先の列のデータ型を **文字列型** ではなく **メモ型**としてウィザードが認識する必要があります。
-   既にコピー先のテーブルに行のデータがある場合、ウィザードによってサンプリングされた最初の 8 つの行はメモ列に 255 文字より長い値を含む、少なくとも 1 つの行を含める必要です。
-   コピー先のテーブルは、ウィザードによって作成された場合、 **CREATE TABLE**ステートメントを使用する必要があります**LONGTEXT** (またはそのシノニムのいずれか) のデータ型として、メモ列です。 チェック、 **CREATE TABLE**ステートメント をクリックして、必要に応じて、修正および**SQL の編集** の横に、**変換先テーブルを作成する** オプションを選択、**列マッピング**ページ。

## <a name="whats-next"></a>次の操作  
 変換先テーブルにコピーおよびマップする既存のテーブルおよびビューを選択した後に表示されるのは、 **[パッケージの保存および実行]**ページです。 このページでは、コピー操作をすぐに実行するかどうかを指定します。 構成によっては、ウィザードによって作成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを保存して、それをカスタマイズし、後から再利用することができます。 詳細については、 [パッケージの保存および実行](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md)に関するページを参照してください。
 
 ## <a name="see-also"></a>参照
[簡単な例によるインポートおよびエクスポート ウィザードの概要](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)


