---
title: "sys.dm_fts_parser (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_parser_TSQL
- dm_fts_parser
- dm_fts_parser_TSQL
- sys.dm_fts_parser
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_parser dynamic management function
- troubleshooting [SQL Server], full-text search
ms.assetid: 2736d376-fb9d-4b28-93ef-472b7a27623a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 97e1eb8f7c4b37e8f1d3bb84ff7b1607712f729c
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmftsparser-transact-sql"></a>sys.dm_fts_parser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  適用した後に最終的なトークン化の結果を返します、指定された[ワード ブレーカー](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)、[類義語辞典](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)、および[ストップ リスト](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)の組み合わせをクエリ文字列入力をします。 トークン化の結果は、指定したクエリ文字列についての Full-Text Engine の出力と同じです。  
  
 sys.dm_fts_parser は動的管理関数です。  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.dm_fts_parser('query_string', lcid, stoplist_id, accent_sensitivity)  
```  
  
## <a name="arguments"></a>引数  
 *query_string*  
 解析対象のクエリです。 *query_string*される文字列チェーンを指定できます[CONTAINS](../../t-sql/queries/contains-transact-sql.md)構文でサポートされます。 たとえば、変化形、類義語辞典、および論理演算子を含めることができます。  
  
 *lcid*  
 解析に使用されるワード ブレーカーのロケール識別子 (LCID) *query_string*です。  
  
 *stoplist_id*  
 いずれかで識別されるワード ブレーカーが使用する場合は、ストップ リストの ID *lcid*です。 *stoplist_id*は**int**です。'NULL' を指定した場合、ストップリストは使用されません。 0 を指定すると、システム ストップリストが使用されます。  
  
 ストップリスト ID は、データベースで一意の値です。 指定されたテーブルの使用上のフルテキスト インデックスのストップ リスト ID を取得する、 [sys.fulltext_indexes](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)カタログ ビューです。  
  
 *accent_sensitivity*  
 フルテキスト検索で分音文字を区別するかしないかを制御するブール値です。 *accent_sensitivity*は**ビット**、次の値のいずれか。  
  
|[値]|アクセントの区別|  
|-----------|----------------------------|  
|0|区別しない<br /><br /> "Café"と"café"などの単語が同一に扱われます。|  
|1|区別する<br /><br /> "Café"と"café"などの単語は異なる方法で扱われます。|  
  
> [!NOTE]  
>  フルテキスト カタログのこの値の現在の設定を表示するには、次を実行[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント: `SELECT fulltextcatalogproperty('` *catalog_name*`', 'AccentSensitivity');`です。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|キーワード (keyword)|**varbinary (128)**|ワード ブレーカーによって返される、特定のキーワードの 16 進数表記です。 この表記は、フルテキスト インデックスにキーワードを格納するために使用します。 この値は人間が判読できるなど、フルテキスト インデックスの内容を返す他の動的管理ビューによって返される関連する特定のキーワードを出力するため便利ですが[sys.dm_fts_index_keywords](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)と[sys.dm_fts_index_keywords_by_document](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)です。<br /><br /> **注:** 0 Xff は、ファイルまたはデータセットの終了を示す特殊文字を表します。|  
|group_id|**int**|特定の用語の生成元になった論理グループを区別する際に役立つ整数値を格納します。 たとえば、英語の場合、'`Server AND DB OR FORMSOF(THESAURUS, DB)"`' で次の group_id 値が生成されます。<br /><br /> 1: サーバー<br />2: DB<br />3: DB|  
|phrase_id|**int**|フルテキストなどの複合語の代替形式がワード ブレーカーによって発行されているかどうかを区別する際に役立つ整数値を格納します。 複合語 ('multi-million' など) が存在する場合、ワード ブレーカーによって代替形式が発行されることがあります。 このような代替形式 (語句) は区別が必要になる場合があります。<br /><br /> たとえば、英語の場合、'`multi-million`' で次の phrase_id 値が生成されます。<br /><br /> 場合は 1`multi`<br />場合は 1`million`<br />2`multimillion`|  
|occurrence|**int**|解析結果の各用語の順序を示します。 たとえば、英語の "`SQL Server query processor`" という語句の場合、occurrence には語句内の用語に対する次のオカレンス値が格納されます。<br /><br /> 場合は 1`SQL`<br />2`Server`<br />3`query`<br />4`processor`|  
|special_term|**nvarchar (4000)**|ワード ブレーカーによって発行されている用語の特性に関する情報を格納します。次のいずれかになります。<br /><br /> 完全一致<br /><br /> ノイズ ワード<br /><br /> 文の末尾<br /><br /> 段落の末尾<br /><br /> 章の末尾|  
|display_term|**nvarchar (4000)**|人間が判読できる形式のキーワードを格納します。 フルテキスト インデックスのコンテンツにアクセスするように設計されている関数と同様に、ここに表示される用語は、非正規化の制限のため元の用語と同一とは限りません。 ただし、元の入力から特定できるだけの十分な精度は確保されます。|  
|expansion_type|**int**|特定の用語の拡張の特性に関する情報を格納します。次のいずれかになります。<br /><br /> 0 = 1 つの単語の場合<br /><br /> 2 = 変化形の拡張<br /><br /> 4 = 類義語辞典の拡張と置換<br /><br /> たとえば、類義語辞典で run が `jog` の拡張として定義されている場合を考えてみます。<br /><br /> `<expansion>`<br /><br /> `<sub>run</sub>`<br /><br /> `<sub>jog</sub>`<br /><br /> `</expansion>`<br /><br /> 用語`FORMSOF (FREETEXT, run)`次の出力が生成されます。<br /><br /> `run` : expansion_type=0<br /><br /> `runs` : expansion_type=2<br /><br /> `running` : expansion_type=2<br /><br /> `ran` : expansion_type=2<br /><br /> `jog` : expansion_type=4|  
|source_term|**nvarchar (4000)**|特定の用語の生成元または解析元になった用語または語句です。 たとえば、英語の場合、`word breakers" AND stemmers'` に対するクエリで次の source_term 値が生成されます。<br /><br /> `word breakers`display_term の`word`<br />`word breakers`display_term の`breakers`<br />`stemmers`display_term の`stemmers`|  
  
## <a name="remarks"></a>解説  
 **sys.dm_fts_parser**など構文と、フルテキスト述語の機能をサポートしている[CONTAINS](../../t-sql/queries/contains-transact-sql.md)と[FREETEXT](../../t-sql/queries/freetext-transact-sql.md)、関数、およびなど[CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)と[FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md)です。  
  
## <a name="using-unicode-for-parsing-special-characters"></a>特殊文字の解析での Unicode の使用  
 クエリ文字列を解析するときに**sys.dm_fts_parser** Unicode として、クエリ文字列を指定しない限り、これには、次の接続は、データベースの照合順序を使用します。 したがって、ü や ç などの特殊文字を含む Unicode 以外の文字列を出力できない可能性があります、データベースの照合順序によって、予期されます。 データベースの照合順序とは関係なくクエリ文字列を処理するで文字列をプレフィックス`N`,、つまり`N'` *query_string*`'`です。  
  
 詳細については、このトピックの後の方にある「C.  特殊文字を含む文字列の出力を表示する」を参照してください。  
  
## <a name="when-to-use-sysdmftsparser"></a>sys.dm_fts_parser を使用する場合  
 **sys.dm_fts_parser**デバッグのために非常に強力にすることができます。 主な使用シナリオには、次のようなものがあります。  
  
-   特定のワード ブレーカーによる特定の入力の処理方法を理解するには  
  
     クエリによって予期しない結果が返された場合、その主な原因として、ワード ブレーカーによるデータの解析方法と区切り方法が挙げられます。 sys.dm_fts_parser を使用すると、ワード ブレーカーからフルテキスト インデックスに渡される結果を検出できます。 また、フルテキスト インデックスで検索されないストップワードである用語も確認できます。 用語が特定の言語によって異なりますで指定されたストップ リスト内にあるかどうかにストップ ワードをどのようにがかどうか、 *stoplist_id*関数で宣言されている値。  
  
     ユーザーがワード ブレーカーによる入力の解析方法を確認できるようにするアクセントの区別フラグには、アクセントの区別に関する情報が格納されているので、これも確認してください。  
  
-   特定の入力に対するステミング機能の動作のしくみを理解するには  
  
     ワード ブレーカーとステミング機能によるクエリ用語とそのステミング形式の解析方法を調べるには、次の FORMSOF 句を含む CONTAINS または CONTAINSTABLE クエリを指定します。  
  
    ```  
    FORMSOF( INFLECTIONAL, query_term )  
    ```  
  
     この結果から、フルテキスト インデックスに渡されている用語がわかります。  
  
-   類義語辞典による入力の全体または一部の拡張方法や置換方法を理解するには  
  
     次のように指定することもできます。  
  
    ```  
    FORMSOF( THESAURUS, query_term )  
    ```  
  
     このクエリの結果から、クエリ用語に対するワード ブレーカーと類義語辞典の相互作用のしくみがわかります。 類義語辞典から拡張または置換を確認し、フルテキスト インデックスに対して実際に発行されているクエリを特定することができます。  
  
     ユーザーが次のように発行したとします。  
  
    ```  
    FORMSOF( FREETEXT, query_term )  
    ```  
  
     この場合、変化形および類義語辞典の機能が自動的に実行されます。  
  
 上記の使用シナリオに加え、sys.dm_fts_parser は、フルテキスト クエリに関する他の多くの問題の理解やトラブルシューティングに大きく役立ちます。  
  
## <a name="permissions"></a>権限  
 メンバーシップが必要、 **sysadmin**の指定したストップ リストに対するサーバーの役割とアクセス権を固定します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-displaying-the-output-of-a-given-word-breaker-for-a-keyword-or-phrase"></a>A. キーワードまたは語句に関する特定のワード ブレーカーの出力を表示する  
 次の例では、以下のクエリ文字列に対して LCID が 1033 の英語のワード ブレーカーを使用し、ストップリストを使用しない場合の出力が返されます。  
  
 `The Microsoft business analysis`  
  
 アクセントの区別は無効になっています。  
  
```  
SELECT * FROM sys.dm_fts_parser (' "The Microsoft business analysis" ', 1033, 0, 0);  
```  
  
### <a name="b-displaying-the-output-of-a-given-word-breaker-in-the-context-of-stoplist-filtering"></a>B. ストップリスト フィルターを使用する場合の特定のワード ブレーカーの出力を表示する  
 次の例では、下記のクエリ文字列に対して LCID が 1033 の英語のワード ブレーカーと ID が 77 の英語のストップリストを使用する場合の出力が返されます。  
  
 `"The Microsoft business analysis" OR "MS revenue"`  
  
 アクセントの区別は無効になっています。  
  
```  
SELECT * FROM sys.dm_fts_parser (' "The Microsoft business analysis"  OR " MS revenue" ', 1033, 77, 0);  
```  
  
### <a name="c-displaying-the-output-of-a-string-that-contains-special-characters"></a>C. 特殊文字を含む文字列の出力を表示する  
 次の例では、Unicode を使用して次のフランス語の文字列を解析します。  
  
 `français`  
  
 この例では、フランス語の LCID として `1036` と、ユーザー定義のストップリストの ID として `5` を指定します。 アクセントの区別は有効になっています。  
  
```  
SELECT * FROM sys.dm_fts_parser(N'français', 1036, 5, 1);  
```  
  
## <a name="see-also"></a>参照  
 [フルテキスト検索およびセマンティック検索の動的管理ビューおよび関数 &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [フル テキスト検索](../../relational-databases/search/full-text-search.md)   
 [検索用のワード ブレーカーとステミング機能の構成と管理](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [構成して、フルテキスト検索の類義語辞典ファイルの管理](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)   
 [構成およびストップ ワードとストップ リストをフルテキスト検索の管理](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [フルテキスト検索でのクエリ](../../relational-databases/search/query-with-full-text-search.md)   
 [フルテキスト検索でのクエリ](../../relational-databases/search/query-with-full-text-search.md)   
 [セキュリティ保護可能](../../relational-databases/security/securables.md)  
  
  
