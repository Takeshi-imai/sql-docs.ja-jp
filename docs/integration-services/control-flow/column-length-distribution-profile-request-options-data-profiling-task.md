---
title: "列長分布プロファイル要求オプション (データ プロファイル タスク) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 1a4de41f-f38d-40ea-ba1b-6c0ef67ea52a
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5799a96f092b7277bdeb5e7e49ca998d17f12020
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="column-length-distribution-profile-request-options-data-profiling-task"></a>[列長分布プロファイル要求] のオプション (データ プロファイル タスク)
  **[プロファイル要求]** ページの **[要求プロパティ]** ペインを使用すると、要求ペインで選択した **[列長分布プロファイル要求]** のオプションを設定できます。 列長分布プロファイルは、選択された列に含まれる文字列値の長さごとに、その長さと、テーブル内におけるその長さの行の比率を報告します。 このプロファイルを使用すると、無効な値などのデータの問題を特定できます。 たとえば、2 文字の米国州コードの列をプロファイルし、3 文字以上の値を検出できます。  
  
> [!NOTE]  
>  このトピックで説明するオプションは、 **[データ プロファイル タスク エディター]** の **[プロファイル要求]**ページに表示されます。 エディターのこのページの詳細については、「[Data Profiling Task Editor &#40;Profile Requests Page&#41;](../../integration-services/control-flow/data-profiling-task-editor-profile-requests-page.md)」(データ プロファイル タスク エディター &#40;[プロファイル要求] ページ&#41;)を参照してください。  
  
 データ プロファイル タスクの使用方法の詳細については、「[データ プロファイル タスクのセットアップ](../../integration-services/control-flow/setup-of-the-data-profiling-task.md)」を参照してください。 Data Profile Viewer を使用してデータ プロファイル タスクの出力を分析する方法の詳細については、「 [Data Profile Viewer (Data Profile Viewer)](../../integration-services/control-flow/data-profile-viewer.md)」を参照してください。  
  
## <a name="request-properties-options"></a>[要求プロパティ] のオプション  
 **[要求プロパティ]**ペインに表示される **[列長分布プロファイル要求]** のオプション グループは次のとおりです。  
  
-   **[データ]**( **[TableOrView]** オプション、 **[Column]** オプションなど)  
  
-   **全般**  
  
-   **Options**  
  
### <a name="data-options"></a>[データ] のオプション  
 **[ConnectionManager]**  
 プロファイル対象のテーブルまたはビューを含む [!INCLUDE[vstecado](../../includes/vstecado-md.md)] データベースに接続するには、.NET Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) を使用する既存の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続マネージャーを選択します。  
  
 **[TableOrView]**  
 プロファイル対象の列を含む既存のテーブルまたはビューを選択します。  
  
 詳細については、このトピックの「[TableorView] のオプション」を参照してください。  
  
 **[Column]**  
 プロファイル対象の既存の列を選択します。 すべての列をプロファイルするには、**[(\*)]** を選択します。  
  
 詳細については、このトピックの「[列] のオプション」を参照してください。  
  
#### <a name="tableorview-options"></a>[TableOrView] のオプション  
 **スキーマ**  
 選択したテーブルが属するスキーマを指定します。 このオプションは読み取り専用です。  
  
 **Table**  
 選択したテーブルの名前を表示します。 このオプションは読み取り専用です。  
  
#### <a name="column-options"></a>[列] のオプション  
 **IsWildCard**  
 **[(\*)]** ワイルドカードが選択されているかどうかを示します。 **[(\*)]** を選択してすべての列をプロファイルする場合、このオプションは **[True]** に設定されます。 個々の列をプロファイル対象として選択した場合、このオプションは **[False]** になります。 このオプションは読み取り専用です。  
  
 **[ColumnName]**  
 選択した列の名前を表示します。 **[(\*)]** を選択してすべての列をプロファイルする場合、このオプションは空白になります。 このオプションは読み取り専用です。  
  
 **[StringCompareOptions]**  
 このオプションは、列長分布プロファイルには適用されません。  
  
### <a name="general-options"></a>[全般] のオプション  
 **RequestID**  
 このプロファイル要求を識別するわかりやすい名前を入力します。 通常、自動生成された値を変更する必要はありません。  
  
### <a name="options"></a>オプションなど)  
 **[IgnoreLeadingSpaces]**  
 プロファイルが文字列値を比較する際に、先頭の空白を無視するかどうかを指定します。 このオプションの既定値は **[False]**です。  
  
 **[IgnoreTrailingSpaces]**  
 プロファイルが文字列値を比較する際に、末尾の空白を無視するかどうかを指定します。 このオプションの既定値は **[true]**です。  
  
## <a name="see-also"></a>参照  
 [データ プロファイル タスク エディターと &#40; です。「全般」 ページと &#41; です。](../../integration-services/control-flow/data-profiling-task-editor-general-page.md)   
 [単一テーブル クイック プロファイル フォーム &#40; のデータ プロファイル タスクと &#41; です。](../../integration-services/control-flow/single-table-quick-profile-form-data-profiling-task.md)  
  
  