---
title: "Odbc 入力元を使用して、データを抽出 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10f25703-49a2-4d45-abab-6b4da2a57ba5
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 236c2b7caf1ec3ade0a140bfabfc32f3a21a9ea1
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="extract-data-by-using-the-odbc-source"></a>ODBC 入力元を使用したデータ抽出
  この手順では、ODBC 入力元を使用してデータを抽出する方法について説明します。 ODBC 入力元を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクがあらかじめ含まれている必要があります。  
  
### <a name="to-extract-data-using-an-odbc-source"></a>ODBC 入力元を使用してデータを抽出するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、使用する [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] パッケージを開きます。  
  
2.  **[データ フロー]** タブをクリックし、次に **[ツールボックス]**で、ODBC 入力元をデザイン画面にドラッグします。  
  
3.  ODBC 入力元をダブルクリックします。  
  
4.  **[ODBC 入力元エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで、既存の ODBC 接続マネージャーを選択するか、 **[新規作成]** をクリックして新しい接続マネージャーを作成します。  
  
5.  データのアクセス方法を選択します。  
  
    -   **[テーブル名]**: データベースのテーブルまたはビューを選択するか、正規表現を入力して、ODBC 接続マネージャーの接続先のテーブルを指定します。  
  
         この一覧には、最初の 1,000 個のテーブルのみが含まれます。 データベースに 1,000 を超えるテーブルがある場合、テーブル名の最初の文字を入力するか、名前の一部の入力にワイルドカード (*) を使用すると、目的のテーブルが表示されます。  
  
    -   **[SQLコマンド]**: SQLコマンドを入力するか、 **[参照]** をクリックしてテキスト ファイルから SQL クエリを読み込みます。  
  
6.  **[プレビュー]** をクリックすると、ODBC 入力元によって抽出されるデータを最大 200 行表示できます。  
  
7.  外部列と出力列間のマッピングを更新するには、 **[列]** をクリックし、 **[外部列]** 一覧にある別の列を選択します。  
  
8.  必要に応じて、 **[出力列]** 一覧の値を編集し、出力列の名前を更新します。  
  
9. エラー出力を構成するには、 **[エラー出力]**をクリックします。  
  
10. **[OK]**をクリックします。  
  
11. 更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [Odbc 入力元エディター & #40 です。接続マネージャー ページ &#41;](../../integration-services/data-flow/odbc-source-editor-connection-manager-page.md)   
 [Odbc 入力元エディター & #40 です。[列] ページ &#41;](../../integration-services/data-flow/odbc-source-editor-columns-page.md)   
 [[ODBC ソース エディター] &#40;[エラー出力] ページ&#41;](../../integration-services/data-flow/odbc-source-editor-error-output-page.md)  
  
  