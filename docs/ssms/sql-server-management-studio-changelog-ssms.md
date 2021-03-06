---
title: SQL Server Management Studio - Changelog (SSMS) | Microsoft Docs
ms.custom: 
ms.date: 02/15/2018
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms
ms.reviewer: 
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3dc76cc1-3b4c-4719-8296-f69ec1b476f9
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: a87476c668bcbf8226348349d6886c39ce8563bf
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="sql-server-management-studio---changelog-ssms"></a>SQL Server Management Studio - Changelog (SSMS)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
この記事では、SSMS の現在と以前のバージョンの更新、機能強化、およびバグの修正に関する詳細を提供します。 [SSMS の以前のバージョン](#previous-ssms-releases)は以下でダウンロードできます。



## <a name="ssms-175download-sql-server-management-studio-ssmsmd"></a>[SSMS 17.5](download-sql-server-management-studio-ssms.md)

一般公開 | ビルド番号: 14.0.17224.0

### <a name="whats-new"></a>新機能

**SSMS 全般**

データの検出と分類:

- データベース内の機密データの検出、分類、ラベル付けとレポート作成を行うための新しい SQL データの検出と分類機能が追加されました。 
- 最も機密性の高いデータ (ビジネス、財務、医療、PII など) の自動検出と分類は、組織の情報保護の達成において極めて重要な役割を果たすことができます。
- 詳細については、「[SQL データの検出と分類](../relational-databases/security/sql-data-discovery-and-classification.md)」を参照してください。

クエリ エディター:

- Azure SQL DW の区切られたテキストの外部ファイル形式に SkipRows オプションのサポートが追加されました。 この機能では、ユーザーは区切られたテキスト ファイルを SQL DW に読み込む際に指定した数の行をスキップすることができます。 また、FIRST_ROW キーワードの対応する intellisense/SMO サポートも追加されました。 

Showplan:

- SQL Data Warehouse の推定プラン ボタンを表示できるようになりました。
- 新しい Showplan 属性 *EstimateRowsWithoutRowGoal* が追加され、新しい Showplan 属性 (*UdfCpuTime* と *UdfElapsedTime*) が *QueryTimeStats* に追加されました。 詳細については、「[Optimizer row goal information in query execution plan added in SQL Server 2017 CU3](http://support.microsoft.com/help/4051361)」 (SQL Server 2017 CU3 で追加されたクエリ実行プランのオプティマイザー行の目標情報) を参照してください。



### <a name="bug-fixes"></a>バグの修正

**SSMS 全般**

Showplan:

- LQS 接続の経過時間ではなく、エンジンの実行時間を表示するように、ライブ クエリ統計経過時間が修正されました。
- Showplan で GbApply や InnerApply などの Apply 論理演算子を認識できないという問題が修正されました。
- ExchangeSpill に関する問題が修正されました。

クエリ エディター:

- 先頭に "SET SHOWPLAN_ALL ON" が付いた単純なクエリを実行する際に SSMS が "入力文字列の形式が正しくありません。 (mscorlib)" というようなエラーをスローするという SPID に関する問題が修正されました。 


SMO:

- サーバーの照合順序で大文字と小文字が区別される場合に SMO が AvailabilityReplica プロパティをフェッチできない (その結果、SSMS で "マルチパート識別子 "a.delimited" をバインドできませんでした" というようなエラー メッセージが表示される場合がある) という問題が修正されました。
- 照合順序が処理されない (その結果、照合順序の大文字と小文字が区別されるサーバーで実行されているデータベースで右クリックしたときに、トルコ語のロケールの ma マシン上で実行されている SSMS で "レガシ基数推定が有効なスコープ構成ではありません" というようなエラーが表示される場合がある) という、DatabaseScopedConfigurationCollection クラスの問題が修正されました。
- SMO が SQL 2005 サーバーで SQL エージェント プロパティをフェッチできない (その結果、SSMS が "ローカル変数に既定値を代入できません。 スカラー変数 "@ServiceStartMode" を宣言してください" というようなエラーをスローし、最終的にオブジェクト エクスプローラーで SQL エージェント ノードが表示されない) という、JobServer クラスの問題が修正されました。

テンプレート: 

- "データベース メール": いくつかのタイプミスが修正されました [(https://feedback.azure.com/forums/908035/suggestions/33143512)](https://feedback.azure.com/forums/908035/suggestions/33143512)。  

オブジェクト エクスプローラー:
- インデックスの管理圧縮が失敗する問題が修正されました (https://feedback.azure.com/forums/908035-sql-server/suggestions/32610058-ssms-17-4-error-when-enabling-page-compression-o)。

監査: 
- *監査ファイルの統合*機能に関する問題が修正されました。
<br>

### <a name="known-issues"></a>既知の問題

データ分類:
- 分類を削除してから、同じ列の新しい分類を手動で追加すると、古い情報の種類と機密ラベルがメイン ビューの列に割り当てられます。<br>
*回避策*: 分類をメイン ビューに戻した後、保存する前に新しい情報の種類と機密ラベルを割り当てます。



## <a name="previous-ssms-releases"></a>以前のリリースの SSMS

以前のバージョンの SSMS をダウンロードするには、次のセクションのタイトル リンクをクリックします。




## <a name="downloadssdtmediadownloadpng-ssms-174httpsgomicrosoftcomfwlinklinkid864329"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 17.4](https://go.microsoft.com/fwlink/?linkid=864329)
一般公開 | ビルド番号: 14.0.17213.0

[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x40a)


### <a name="whats-new"></a>新機能

**SSMS 全般**

脆弱性評価:
- データベースをスキャンして潜在的な脆弱性およびベスト プラクティスからの逸脱 (構成の不備、過剰なアクセス許可、公開された機密データなど) がないかを確認できるように新しい SQL 脆弱性評価サービスが追加されました。 
- 評価の結果には、各々の問題を解決する実践的な手順が含まれ、カスタマイズした修復スクリプトが適宜提供されます。 評価レポートは環境ごとにカスタマイズし、特定の要件に合わせて調整することができます。 詳細については、「[SQL 脆弱性評価](https://docs.microsoft.com/sql/relational-databases/security/sql-vulnerability-assessment)」を参照してください。

SMO:
- Azure 上で *HasMemoryOptimizedObjects* が例外をスローするという問題を修正しました。
- 新しい CATALOG_COLLATION 機能のサポートが追加されました。

Always On ダッシュボード:
- 可用性グループでの待機時間の分析の機能強化。
- 次の 2 つの新しいレポートが追加されました: *AlwaysOn\_Latency\_Primary* および *AlwaysOn\_Latency\_Secondary*

Showplan:
- 適切なドキュメントを指すようにリンクが更新されました。
- 実際に作成されたプランから直接、単一プラン分析を実行できます。
- 新しいアイコンのセット。
- GbApply や InnerApply などの "Apply 論理演算子" を認識するためのサポートが追加されました。
        
XE プロファイラー:
- XEvent プロファイラーに名前が変更になりました。
- 既定で、[停止] / [開始] メニュー コマンドによってセッションが停止/開始されるようになりました。
- キーボード ショートカットが有効になりました (たとえば、検索する場合は CTRL + F キー)。
- XEvent プロファイラー セッションの適切なイベントに database\_name アクションと client\_hostname アクションが追加されました。 変更を有効にするために、サーバー上で既存の QuickSessionStandard セッション インスタンスまたは QuickSessionTSQL セッション インスタンスを削除することが必要な場合があります - [Connect 3142981](https://connect.microsoft.com/SQLServer/feedback/details/3142981)

コマンド ライン:
- 新しいコマンド ライン オプション ("-G") が追加されました。このオプションを指定すると、Active Directory 認証 ('統合' または 'パスワード' のいずれか) を使用してサーバー/データベースへの SSMS の自動接続を行うことができます。 詳細については、「[Ssms ユーティリティ](ssms-utility.md)」を参照してください。

フラット ファイルのインポート ウィザード:
- テーブルの作成時に既定値 ("dbo") 以外のスキーマの名前を選択する方法が追加されました。

クエリ ストア:
- クエリ ストアで使用可能なレポート リストを展開するときの "低下したクエリ" レポートが復元されました。

**Integration Services (IS)**
- 展開ウィザードにパッケージ検証機能が追加されました。これにより、ユーザーは、Azure SSIS IR でサポートされていない SSIS パッケージ内のコンポーネントを容易に確認することができます。

### <a name="bug-fixes"></a>バグの修正

**SSMS 全般**

- オブジェクト エクスプローラー:
    - データベース スナップショットでテーブル値関数ノードが表示されないという問題を修正しました - [Connect 3140161](https://connect.microsoft.com/SQLServer/feedback/details/3140161)です。
    - サーバーが autoclose データベースがある場合に、"*データベース*" ノードを展開する際のパフォーマンスが向上しました。
- クエリ エディター:
    - マスター データベースへのアクセス権をユーザーが持っていない場合に IntelliSense が失敗するという問題を修正しました。
    - リモート コンピューターへの接続を終了するときに、場合によって SSMS をクラッシュさせていた問題を修正しました - [Connect 3142557](https://connect.microsoft.com/SQLServer/feedback/details/3142557)。
- XEvent ビューアー:
    - XEL へのエクスポート機能が再び有効になりました。
    - 場合によって、ユーザーが XEL ファイル全体を読み込めないという問題を修正しました。
- XEvent プロファイラー:
    - ユーザーが *VIEW SERVER STATE* アクセス許可を持っていない場合に SSMS のクラッシュの原因となっていた問題を修正しました。
    - XE プロファイラー ライブ データ ウィンドウを閉じても基になるセッションが停止しないという問題を修正しました。
- 登録済みサーバー:
    - "移動先…" コマンドが機能しなくなるという問題を修正しました -  [Connect 3142862](https://connect.microsoft.com/SQLServer/feedback/details/3142862) および [Connect 3144359](https://connect.microsoft.com/SQLServer/feedback/details/3144359/)。
- SMO:
    - 転送オブジェクトの TransferData メソッドが動作していないという問題を修正しました。
    - SQL DW データベースが一時停止した場合に Server データベースが例外をスローするという問題を修正しました。
    - SQL DW に対して SQL データベースをスクリプト化すると、不適切な T-SQL パラメーター値が生成されるという問題を修正しました。
    - DB の拡張をスクリプト化したときに *DATA\_COMPRESSION* オプションが正しく送信されないという問題を修正しました。
- ジョブの利用状況モニター:
    - ユーザーがカテゴリによるフィルター処理を試みているときに "インデックスが範囲を超えています。 負でない値で、コレクションのサイズよりも小さくなければなりません。 
        パラメーター名: インデックス (System.Windows.Forms)" というエラーが発生するという問題を修正しました - [Connect 3138691](https://connect.microsoft.com/SQLServer/feedback/details/3138691)。
- 接続ダイアログ:
    - 読み取り/書き込みドメイン コント ローラーへのアクセス権を持たないドメイン ユーザーは SQL 認証を使用して SQL Server にログインできないという問題を修正しました - [Connect 2373381](https://connect.microsoft.com/SQLServer/feedback/details/2373381)。
- レプリケーション:
    - SQL Server でプル サブスクリプションのプロパティを参照するときに、エラー "値 'null' をプロパティ ServerInstance に適用できません" が表示されるという問題を修正しました。
- SSMS セットアップ:
    - SSMS セットアップが原因で、コンピューター上にインストールされている一部の製品が正しく再構成されないという問題を修正しました。
- ユーザー設定:
   - この修正プログラムにより、米国政府機関向けソブリン クラウド ユーザーは、ユニバーサル認証と Azure Active Directory ログインを介して SSMS で Azure SQL Database および ARM リソースへのアクセスを中断なく継続できるようになります。  SSMS の以前のバージョンのユーザーの場合は、[ツール]、[オプション]、[Azure サービス] の順に開き、[リソース管理] で "Active Directory Authority" プロパティの構成を https://login.microsoftonline.us に変更する必要があります。

**Analysis Services (AS)**

- プロファイラー: Window 認証を使用して Azure AS に対する接続を試みるときに発生する問題を修正しました。
- 1400 モデル上で接続の詳細をキャンセルするときにクラッシュを引き起こす可能性のある問題を修正しました。
- 資格情報を更新するときに、接続プロパティ ダイアログで Azure BLOB キーを設定すると、それが視覚的にマスクされるようになります。
- Azure Analysis Services のユーザー選択ダイアログで、検索時にオブジェクト ID ではなくアプリケーション ID guid が表示される問題を修正しました。
- データベース\MDX クエリ デザイナー ツールバーで、いくつかのボタンにアイコンが正しくマップされない原因となっていた問題を修正しました。
- msmdpump IIS http/https アドレスを使用した SSAS への接続を妨げる問題を修正しました。
- Azure Analysis Services の[ユーザー ピッカー] ダイアログ内の複数の文字列が新たに他の言語にも翻訳されました。
- MaxConnections プロパティが表形式モデルのデータ ソースに表示されるようになりました。
- 配置ウィザードで、Azure AS ロール メンバーに対する適切な JSON 定義が生成されるようになります。
- Azure AS に対して Windows 認証を選択した場合にログインを求めるメッセージが引き続き表示されるという SQL Profiler での問題を修正しました。



## <a name="downloadssdtmediadownloadpng-ssms-173httpsgomicrosoftcomfwlinklinkid858904"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 17.3](https://go.microsoft.com/fwlink/?linkid=858904)
一般公開 | ビルド番号: 14.0.17199.0

[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40a)


### <a name="enhancements"></a>機能強化

- インテリジェントなフレームワークを使用して、CSV ファイルのインポート エクスペリエンスを効率化するための新しい "フラット ファイルのインポート" ウィザードが追加されました。これは最小限のユーザーの介入または特殊なドメインの知識で使用できます。 詳細については、「[Import Flat File to SQL Wizard](../relational-databases/import-export/import-flat-file-wizard.md)」 (フラット ファイルを SQL ウィザードにインポートする) を参照してください。
- オブジェクト エクスプローラーに "XEvent プロファイラー" ノードが追加されました。 詳細については、「[SSMS XEvent プロファイラーの使用](../relational-databases/extended-events/use-the-ssms-xe-profiler.md)」を参照してください。
- パフォーマンス ダッシュボードでの待機の履歴レポートの待機のフィルター処理と分類を更新しました。
- "Predict" 関数の構文チェックを追加しました。
- 外部ライブラリ管理のクエリの構文チェックを追加しました。
- 外部ライブラリ管理の SMO サポートを追加しました。
- [登録済みサーバー] ウィンドウに [PowerShell の起動] のサポートを追加しました (新しい SQL PowerShell モジュールが必要)。
- Always On: 可用性グループに[読み取り専用ルーティングのサポート](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)を追加しました。
- [Active Directory - MFA で汎用のサポート] ログインの出力ウィンドウにトレースの詳細を送信するオプションを追加しました (既定ではオフになっているため、[ツール] > [オプション] > [Azure サービス] > [Azure クラウド] > [ADAL 出力ウィンドウのトレース レベル] の下にあるユーザー設定で有効にする必要があります)。 
- クエリ ストア: 
  - クエリ ストア UI は、QDS が何らかのデータを記録している限り、QDS がオフになっている場合でもアクセスできます。
  - クエリ ストア UI で、既存レポートのすべての待機の分類法が公開されるようになりました。 これにより、顧客が上位の待機中のクエリのシナリオのロック解除などができるようになります。
- [スクリプト パラメーター ヘッダーを含める] がオプションになりました (既定で無効になっており、[ツール] > [オプション] > [SQL Server オブジェクト エクスプローラー] > [スクリプト] > [スクリプト パラメーター ヘッダーを含める] の下のユーザー設定で有効にすることができます) - [Connect アイテム 3139199](https://connect.microsoft.com/SQLServer/feedback/details/3139199)。
- "RC" ブランド化を削除しました。

### <a name="bug-fixes"></a>バグの修正

**SSMS 全般**

- XEvent: 
   - SSMS が .xel ファイル内のイベントの一部だけを開く問題を修正しました。
   - 既定のデータベースが 'マスター' でない場合の "ライブ データの監視" のエクスペリエンスが向上しました。[Connect アイテム 1222582](https://connect.microsoft.com/SQLServer/feedback/details/1222582)
- Always On: ログ バックアップの復元がエラー "このバックアップ セットのログは LSN x で終了します。これはデータベースに適用するには古すぎます" で失敗する可能性がある問題を修正しました。
- ジョブの利用状況モニター: 一貫性のないアイコンを修正しました。[Connect アイテム 3133100](https://connect.microsoft.com/SQLServer/feedback/details/3133100)
- クエリ ストア: クエリ ストア レポートでユーザーが "カスタム" の日付範囲を選択できない問題を修正しました。 以下の Connect アイテムにリンクされています。
   - [Connect アイテム 3139842](https://connect.microsoft.com/SQLServer/feedback/details/3139842)
   - [Connect アイテム 3139399](http://connect.microsoft.com/SQLServer/feedback/details/3139399)
- 保存されている情報に指定したデータベースがあり、ユーザーが <default> を選択した場合に、接続ダイアログで最近使用したデータベースが "クリア" されない問題を修正しました。
- オブジェクト スクリプト作成:
    - ユーザーが DW データベースをサーバー上で一時停止したが、別の非 DW データベースを選択してそれをスクリプト作成しようとした場合に、"データベース スクリプトの生成" が機能せず、エラーがスローされる問題を修正しました。
    - スクリプト作成したストアド プロシージャのヘッダーがスクリプトの設定と一致せず、誤解を招くスクリプトになる問題を修正しました。[Connect アイテム 3139784](http://connect.microsoft.com/SQLServer/feedback/details/3139784)
    - SQL Azure オブジェクトをターゲットにしたときに、"スクリプト ボタン" が再度有効になります。
    - Azure SQL データベースに接続しているときに、一部のオブジェクト (UDF、ビュー、SP、トリガー) で "Alter" または "Execute" のスクリプト作成が許可されない SSMS の問題を修正しました。[Connect アイテム 3136386](https://connect.microsoft.com/SQLServer/feedback/details/3136386)
- クエリ エディター:
  - Azure SQL Database をターゲットにする際の IntelliSense が向上しました。
  - 有効期限が切れた認証トークン (ユニバーサル認証) によりクエリが失敗する問題を修正しました。
  - Azure SQL Database に対して作業を行うときの IntelliSense が向上しました (特に、Azure SQL Database の接続時には、最新の T-SQL 文法 (140) が使用されます)。
  - サーバー上の DataWarehouse 以外のデータベースへの接続でクエリ ウィンドウを開くと、そのサーバーの DataWarehouse データベースへの後続のクエリ ウィンドウのすべてで、サポートされない型/オプションに関するさまざまなエラーがスローされます。
- Always On:
   - Always On ダッシュボードと AG プロパティ ページにシード処理モード列が追加されました。
   - プライマリが Windows にある場合に、Linux AG が作成できない問題を修正しました。[Connect アイテム 3139856](https://connect.microsoft.com/SQLServer/feedback/details/3139856)
- クエリ実行時の SSMS での複数の "メモリ不足" 問題を修正しました。[Connect アイテム 2845190](https://connect.microsoft.com/SQLServer/feedback/details/2845190)、[Connect アイテム 3123864](https://connect.microsoft.com/SQLServer/feedback/details/3123864)
- Profiler: 
   - SQL 2005 をターゲットとしたときに、Profiler が機能しない問題を修正しました。
   - Profiler が [サーバー証明書を信頼する] 接続オプションを受け入れない問題を修正しました。
- 利用状況モニター: Linux で実行されている SQL Server がポイントされた場合に利用状況モニターが機能しない問題を修正しました。
- 外部データ ソースまたは外部ファイル形式のオブジェクトを転送しない SMO 転送クラスの問題を修正しました。これらの種類のオブジェクトは、正しく転送に含まれるようになりました。
- 登録済みサーバー:
   - UA サーバーに対してマルチサーバー クエリが有効になりました (グループ内のすべての UA サーバーに対して同じトークンを使用しようとします)。
- AD ユニバーサル認証:
   - Azure AD 認証がサポートされない問題を修正しました。
   - テーブル/ビュー デザイナーが機能しない問題を修正しました。
   - "上位 1000 行を選択" と "上位 200 行を編集" が機能しない問題を修正しました。
- データベースの復元: ファイルを別の場所に移動したときに、パスの最後のフォルダーが復元で除外される問題を修正しました。
- 圧縮ウィザード:
   - インデックスの圧縮ウィザードの管理問題を修正しました。SQL 2016 以前のバージョンでデータの圧縮ウィザードが破損する問題を修正しました。
        https://connect.microsoft.com/SQLServer/feedback/details/3139342
   - Azure のテーブルとインデックスに圧縮ウィザードが追加されました。
- Showplan: 
   - PDW 演算子が認識されない問題を修正しました。
- サーバー プロパティ : 
   - サーバー プロセッサのアフィニティを変更できない問題を修正しました。


**Analysis Services (AS)**

- 1400 互換性レベルのテーブル モデルと Power Query データ ソースをサポートする展開ウィザードの多くの問題を修正しました。
- コマンドラインから実行する際に、展開ウィザードで AS Azure に展開できるようになりました。
- AS Azure で Windows 認証を使用する際に、ユーザーがオブジェクト エクスプローラーでユーザー アカウントの名前を正しく確認できるようになりました。


### <a name="known-issues-in-this-173-release"></a>この 17.3 リリースの既知の問題:

**SSMS 全般**

- MFA を使用した UA を使用する Azure AD 認証では、次の SSMS 機能はサポートされていません。
   - データベース エンジン チューニング アドバイザーは Azure AD の認証ではサポートされていません。ユーザーに表示されるエラー メッセージが少し曖昧だという既知の問題があります。"Could not load file or assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory,…" (ファイルまたはアセンブリ 'Microsoft.IdentityModel.Clients.ActiveDirectory を読み込めませんでした…) が、正常なメッセージである "Database Engine Tuning Advisor does not support Microsoft Azure SQL Database. (DTAClient) (Database Engine Tuning Advisor は Microsoft Azure SQL Database をサポートしていません(DTAClient)) の代わりに表示されます。
- DTA でクエリを分析しようとすると、次のエラーが発生します。"Object must implement IConvertible. (mscorlib)" (オブジェクトで IConvertible を実装する必要があります (mscorlib))。
- *[低下したクエリ]* がオブジェクト エクスプローラーのレポートのクエリ ストアのリストにありません。
   - 回避策: **[クエリ ストア]** ノードを右クリックし、**[View Regressed Queries]\(低下したクエリを表示します\)** を選択します。

**Integration Services (IS)**

- [catalog].[event_messagea] の [Execution_path] は、Scale Out でのパッケージの実行には正しくありません。[execution_path] は、パッケージの実行可能ファイルのオブジェクト名ではなく、"\Package" で開始します。 SSMS でパッケージ実行の概要レポートを表示すると、実行の概要の "実行パス" のリンクが機能しません。 回避策として、概要レポートの [メッセージの表示] をクリックして、すべてのイベント メッセージを確認します。


## <a name="downloadssdtmediadownloadpng-ssms-172httpsgomicrosoftcomfwlinklinkid854085"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 17.2](https://go.microsoft.com/fwlink/?linkid=854085)
一般公開 | ビルド番号: 14.0.17177.0

[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40a)

### <a name="enhancements"></a>機能強化

- Multi-Factor Authentication (MFA)
  - 多要素認証を使用したユニバーサル認証 (UA with MFA) 向けの複数ユーザーの Azure AD 認証
  - 複数ユーザーの認証をサポートするため、MFA を使用したユニバーサル認証用に新しいユーザー資格情報の入力フィールドが追加されました。
- 接続ダイアログ ボックスで、次の 5 つの認証方法がサポートされるようになりました。
  - [Windows 認証]
  - SQL Server 認証 (SQL Server Authentication)
  - Active Directory - Universal with MFA のサポート
  - Active Directory - パスワード
  - Active Directory - 統合

- MFA を使用したユニバーサル認証を使用する DacFx のデータベースのインポート/エクスポート ウィザード。
- API のサポートについては、「[IUniversalAuthProvider インターフェイス](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx)」を参照してください。
- MFA を使用した Azure AD ユニバーサル認証で使用される ADAL マネージ ライブラリは、バージョン 3.13.9 にアップグレードされました。
- SQL Database および SQL Data Warehouse の Azure AD 管理者設定のサポートが実現された新しい CLI インターフェイスの追加。

 Active Directory の認証方法の詳細については、「[SQL Database と SQL Data Warehouse でのユニバーサル認証 (MFA 対応の SSMS サポート)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication)」と「[SQL Server Management Studio 用に Azure SQL Database の多要素認証を構成する](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure)」を参照してください。

- 出力ウィンドウには、オブジェクト エクスプローラー ノードの展開時に実行されるクエリのエントリがあります。
- Azure SQL Databases のビュー デザイナーの有効化
- SSMS でのオブジェクトのスクリプト作成の既定のスクリプト作成オプションが、オブジェクト エクスプローラーから変更されました。
  - 以前は、新しいインストールには既定で、 SQL Server の最新バージョン (現時点では SQL Server 2017) を対象に生成されたスクリプトがありました。
  - SSMS 17.2 では、新しいオプション [*スクリプト設定をソースに一致させる*] が追加されました。 *True* に設定すると、生成されるスクリプトは、オブジェクトがスクリプト化されるサーバーと同じバージョン、エンジンの種類、およびエンジンのエディションを対象にします。
  - [*スクリプト設定をソースに一致させる*] の値は既定で *True* に設定されているため、SSMS の新しいインストールは、オブジェクトのスクリプト作成を常に元のサーバーと同じターゲットにすることが自動的に既定値に設定されます。
  - [*スクリプト設定をソースに一致させる*] の値を *False* に設定すると、通常のスクリプトのターゲット オプションが有効になり、従来どおりに機能します。
    - さらに、すべてのスクリプト作成オプションが、独自のセクションの [*バージョン オプション*] に移動されました。 これらは [*全般スクリプト作成オプション*] の下にはありません。

- "Restore from URL" に National Clouds のサポートが追加されました。
- QueryStoreUI レポートで、sys.query_store_runtime_stats からの追加のメトリック (RowCount、DOP、CLR Time など) がサポートされるようになりました。
- Azure SQL Database で IntelliSense がサポートされるようになりました。
    - https://connect.microsoft.com/SQLServer/feedback/details/3100677/ssms-2016-would-be-nice-to-have-intellisense-on-azure-sql-databases
- セキュリティ: 接続ダイアログの既定値が、サーバー証明書を信頼せず、Azure SQL DB 接続の暗号化を要求することになります。
- SQL Server on Linux のサポートに関する全般的な改良点:
 - データベース メール ノードの復帰
 - パスに関連するいくつかの問題への対処
 - 利用状況モニターの安定性の向上
 - [接続プロパティ] ダイアログでの正しいプラットフォームの表示
- パフォーマンス ダッシュボード サーバー レポートを既定のレポートとして使用できるようになりました。
  - SQL Server 2008 以降のバージョンに接続できます。
  - 欠落したインデックスのサブレポートは、最も有用なインデックスを特定しやすくするため、スコアリングを使用します。
  - 履歴待機統計サブレポートで、待機の集計がカテゴリ別になりました。 アイドル状態とスリープの待機は既定で除外されます。
  - 新しい履歴ラッチ サブレポート。
- Showplan ノードの検索では、プランのプロパティを検索できます。 テーブル名などの任意の演算子プロパティを簡単に検索できます。 プランを表示しているときに、このオプションを使用するには、次の手順を実行します。
  - プランを右クリックし、コンテキスト メニューで [ノードの検索] オプションをクリックします。
  - CTRL + F キーを使用します。


**Analysis Services (AS)**

- SSMS の AS Azure モデルにメール アドレスがないユーザーに対する新しい AAD ロール メンバー選択

**Integration Services (IS)**

- SSIS の実行レポートに追加された新しい列 ([実行数])

### <a name="known-issues-in-this-release"></a>このリリースの既知の問題:

- "Active Directory - MFA を使用したユニバーサルのサポート" を使用するクエリ ウィンドウを 1 時間開いた後でクエリを実行しようとすると、次のようなエラーが発生する場合があります。

   `Msg 0, Level 11, State 0, Line 0
The connection is broken and recovery is not possible. The client driver attempted to recover the connection one or more times and all attempts failed. Increase the value of ConnectRetryCount to increase the number of recovery attempts.`

   クエリを再実行すると、エラーを克服して成功します。

- MFA を使用したユニバーサル認証を使用する Azure AD 認証では、次の SSMS 機能はサポートされていません。
  - **新しいテーブル/ビュー** デザイナーが古いスタイルのログイン プロンプトを表示して、Azure AD の認証で機能しません。
  - **[上位 200 行を編集]** 機能は、Azure AD 認証をサポートしません。
  - **登録済みサーバー** コンポーネントは、Azure AD 認証をサポートしません。
  - **データベース エンジン チューニング アドバイザー**は、Azure AD 認証でサポートされていません。 ユーザーに表示されるエラー メッセージが有益ではないという既知の問題があります。*Could not load file or assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory,…* (ファイルまたはアセンブリ 'Microsoft.IdentityModel.Clients.ActiveDirectory を読み込めませんでした…) が、正常なメッセージである *Database Engine Tuning Advisor does not support Microsoft Azure SQL Database.(DTAClient)* (Database Engine Tuning Advisor は Microsoft Azure SQL Database をサポートしていません(DTAClient)) の代わりに表示されます。

**Analysis Services (AS)**

- SSAS のオブジェクト エクスプローラーは、AS Azure の接続プロパティに Windows 認証のユーザー名を表示しません。

### <a name="bug-fixes"></a>バグの修正

- クエリの結果を (テキストとして) 印刷しようとすると発生する問題を修正しました。  https://connect.microsoft.com/SQLServer/feedback/details/3055225/
- SQL Azure データベースでテーブルとその他のオブジェクトの削除をスクリプト化したときに、SSMS が不正にこれらを破棄する問題を修正しました。
- 次のようなエラーが表示され、SSMS が時々起動しない問題を修正しました。"1 つ以上のコンポーネントが見つかりません。 アプリケーションを再インストールしてください。"
- SSMS UI の SPID が古くなって同期されない問題を修正しました。 https://connect.microsoft.com/SQLServer/feedback/details/1898875
- /passive 引数が /quiet として扱われる SSMS (サイレント) セットアップでの問題を修正しました。
- SSMS が起動時に時々、"オブジェクト参照がオブジェクト インスタンスに設定されていません" というエラーをスローする問題を修正しました。 http://connect.microsoft.com/SQLServer/feedback/details/3134698
- グラフ テーブルで [計算] を押すと、SSMS がクラッシュするデータ圧縮ウィザードの問題を修正しました。
- (低速なインターネット接続を介して) テーブルのインデックスを右クリックしたときのパフォーマンスの問題に対処しました。 https://connect.microsoft.com/SQLServer/feedback/details/3120783
- 大文字と小文字を区別する照合順序を持つサーバーで、SSMS がバックアップ ファイルを列挙できない問題を修正しました。 http://connect.microsoft.com/SQLServer/feedback/details/3134787 と https://connect.microsoft.com/SQLServer/feedback/details/3137000
- Showplan と showplan 比較のさまざまな修正
- SSMS を実行しているコンピューターに SQL Server がインストールされていないと、[接続] ダイアログで接続に使用する [ネットワーク プロトコル] をユーザーが指定できない問題を修正しました。 https://connect.microsoft.com/SQLServer/feedback/details/3134997
- 一部の SSMS ダイアログが "ランダム" な場所に表示されるマルチ モニター構成のサポートを強化しました。 タスク ダイアログやプロパティ シートを閉じたときにその位置を記憶できるように、[SQL Server オブジェクト エクスプローラー | コマンド] ユーザー設定の下に、新しいオプション [タスク ダイアログ] が追加されました。 https://connect.microsoft.com/SQLServer/feedback/details/889169、https://connect.microsoft.com/SQLServer/feedback/details/1158271、https://connect.microsoft.com/SQLServer/feedback/details/3135260 
- SSMS が暗号化された Azure SQL DB の DB プロパティを変更できない問題を修正しました。
- [実行後に結果を破棄する] オプションを強化しました。 https://connect.microsoft.com/SQLServer/feedback/details/1196581
- ユーザーが自分が管理者ではない Azure サブスクリプションにアクセスできない問題を改善または修正しました。
- ソース データベースの選択に関係なく、OE で選択したターゲット データベースを維持するようにデータベースの復元ウィザードを改善しました。 https://connect.microsoft.com/SQLServer/feedback/details/3118581
- オブジェクト エクスプローラーが、新しく追加された "ネイティブ コンパイル ストアド プロシージャ" を正しく並べ替えない問題を修正しました。 http://connect.microsoft.com/SQLServer/feedback/details/3133365
- "SELECT TOP n ROWS" に "TOP" 句が含まれない問題を修正しました。 Azure SQLDW の場合。 https://connect.microsoft.com/SQLServer/feedback/details/3133551 と https://connect.microsoft.com/SQLServer/feedback/details/3135874
- QueryStoreUI: すべてのレポートで非カスタム時間間隔が正しく動作しない問題を修正しました。
- Always Encrypted:
    - 新しい CMK ダイアログでの AKV アクセス許可状態のメッセージングが改善されました。
    - 長い名前の CEK を区別しやすくするため、CEK ドロップダウンにツールヒントが追加されました。
    - 一部の CNG キー ストア プロバイダーが Always Encrypted の [新しい列マスター キー] ダイアログに表示されない問題を修正しました。
- SSMS 接続の一貫性のない "Application Name" を修正しました。 http://connect.microsoft.com/SQLServer/feedback/details/3135115
- SSMS が SQL Azure に対して正しいスクリプトを生成しない (DATA_COMPRESSIONS オプションを使用したテーブルとインデックス) 問題を修正しました。 https://connect.microsoft.com/SQLServer/feedback/details/3133148
- ユーザーが CTRL + Q のショートカット キーを使用してクイック起動できない問題を修正しました (注: クエリ エディターで [IntelliSense が有効] オプションを切り替える新しいキー バインディングは、CTRL + B と CTRL + I になりました)。 https://connect.microsoft.com/SQLServer/feedback/details/3131968
- カスタム ドメインが定義されたアカウントを持つサブスクリプションからストレージ アカウントを選択しようとすると、SSMS が例外をスローする "データベースの復元" での問題を修正しました。
- SSMS が "インデックスが配列の境界外です" エラーをスローし、ユーザーが "テーブル ビュー" を標準以外のものに変更できない "データベース ダイアグラム" での問題を修正しました。 https://connect.microsoft.com/SQLServer/feedback/details/3133792 と http://connect.microsoft.com/SQLServer/feedback/details/3135326
- SSMS が従来のストレージ アカウントを列挙しない "URL へのバックアップ/復元" での問題を修正しました。
- データベース ロールにスキーマ バインドのセキュリティ保護可能を追加しようとすると、例外がスローされる問題を修正しました。 https://connect.microsoft.com/SQLServer/feedback/details/3118143
- テーブル ノードの展開時に、SSMS が断続的に次のエラーを表示する問題を修正しました。"データが NULL です。 このメソッド、またはプロパティは Null 値で呼び出せません。" http://connect.microsoft.com/SQLServer/feedback/details/3136283
- DTA: 特定の境界値を持つパーティション関数を評価するときに、ヒープの破損により DTAEngine.exe が終了する問題を修正しました。


**Analysis Services (AS)**

- データベースに ID とは異なる名前が含まれていると、AS データベースの復元がエラーにより失敗する問題を修正しました。
- DAX クエリ ウィンドウで [IntelliSense が有効] を切り替えるメニュー オプションが無視される問題を修正しました。
- msmdpump IIS http/https アドレスを介した SSAS への接続を妨げる問題を修正しました。
- セミコロンが含まれているパスワードを使用して AS Azure に接続できるようになりました。
- [メンバーシップのスキップ] オプションを使用して AS データベースの復元コマンドのスクリプトを作成すると、SQL Server 2017 AS サーバーまたは AS Azure で使用するときに対応する新しい JSON オプションが含まれます。
- 読み込み時にデータベースの削除ダイアログにエラーを引き起こす非常にまれな問題を修正しました。
- SQL クエリと M のパーティション定義が混在する 1400 互換性レベル モデルでパーティションを表示しようとするときに発生する可能性のある問題を修正しました。

**Integration Services (IS)**
- SSISDB カタログの実行情報レポートを表示できない問題を修正しました。
- 多数のプロジェクトまたはパッケージによるパフォーマンス低下に関する SSMS の問題に対処しました。

## <a name="downloadssdtmediadownloadpng-ssms-171httpsgomicrosoftcomfwlinklinkid799832"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 17.1](https://go.microsoft.com/fwlink/?linkid=799832)
一般公開 | ビルド番号: 14.0.17119.0

[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x40a)

### <a name="enhancements"></a>機能強化

- プロファイラー: [ヘルプ] > [バージョン情報] でリリース バージョン番号 (例: 17.1) が表示されるようになりました
- Analysis Service のユーザーは、データ ソースのコンテキスト メニューから 1200 TM モデル以降のデータ ソースの資格情報を更新できます
- 組み込み SSIS レポートで、CTP 2.1 での SSIS スケールアウト実行からのログが表示されるようになりました
- SSIS スケールアウト管理アプリケーション
  - スケールアウト マスターに関する基本的な情報を表示します。
  - スケールアウトの配置に worker を簡単に追加します。
  - すべてのスケールアウト worker とそれらに関する基本情報を表示し、それらを簡単に有効化または無効化することもできます。

### <a name="bug-fixes"></a>バグの修正
- Always On:
  - 可用性レプリカのプロパティが WSFC AG に対して常に "自動フェールオーバー" モードと表示された問題を修正しました。
  - 可用性グループを更新すると読み取り専用ルーティング リストが上書きされた問題を修正しました
- Always Encrypted: 生成されたログ ファイルに DacFx によって生成された情報が含まれない問題を修正しました。
- プラン表示: 適応型結合ではない演算子に対して UI に常に 実際の結合の種類属性が表示されていた問題を修正しました。
- セットアップ:
  - SSMS 17.0 が Visual Studio 2013 の SSDT を壊していた問題を修正しました [Connect アイテム 3133479]
  - セットアップの最後で [再起動] をクリックしてもコンピューターが再起動しなかった問題を修正しました
- スクリプト: 削除スクリプトを作成しようとするときに SSMS が誤って Azure データベース オブジェクトを削除しないようにそのオプションを無効にすることで一時的に防止しています。  適切な修正は SSMS の今後のリリースで行われます。
- オブジェクト エクスプローラー: "AS COPY" を使って作成された Azure データベースに接続したときに "データベース" ノードが展開されなかった問題を修正しました

## <a name="downloadssdtmediadownloadpng-ssms-170httpgomicrosoftcomfwlinklinkid799832"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 17.0](http://go.microsoft.com/fwlink/?LinkID=799832)
一般公開 | ビルド番号: 14.0.17099.0

[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x40a)

### <a name="enhancements"></a>機能強化 

- アップグレード パッケージと Windows Software Update Services (WSUS) 
    - 将来の 17.X のリリースには、小さい累積更新プログラム パッケージが含まれます 
  - 更新プログラム パッケージは、WSUS カタログにも公開されます  
- アイコンの更新
    - アイコンは、VS シェル提供のアイコンと一致するように更新され、高 DPI 解像度をサポートするようになりました
    - 16.X バージョンと 17.X バージョンを区別する新しい SSMS とプロファイラー プログラムのアイコンに更新します。
- SQL PowerShell モジュール
  - SQL Server PowerShell モジュールは、SSMS から削除され、PowerShell ギャラリーを介してリリースされます (モジュールのバージョン管理をサポートするには PowerShell 5.0 が必要です)
  - 一部の SMO オブジェクトの "プレゼンテーション" (書式設定) に関連するその他の改善 (たとえば、データベースでサイズと使用可能領域が、テーブルで行数と領域の使用状況が表示されるようになりました)
  - OE で PowerShell コマンド プロンプトが [PowerShell の起動] メニューから呼び出されたときのカラー化が追加されました
  - AG コマンドレットに (New-SqlAvailabilityGroup、Join-SqlAvailabilityGroup、および Set-SqlAvailabilityGroup) に -ClusterType パラメーターと -RequiredCopiesToCommit パラメーターを追加しました。
  - Add-SqlAzureAuthenticationContext コマンドレットに -ActiveDirectoryAuthority パラメーターと -AzureKeyVaultResourceId パラメーターを追加しました。
  - Revoke-SqlAvailabilityGroupCreateAnyDatabase、Grant-SqlAvailabilityGroupCreateAnyDatabase、Set-SqlAvailabilityReplicaRoleToSecondary の各コマンドレットが追加されました
  - Set-SqlAvailabilityReplica および New-SqlAvailabilityReplica コマンドレットに -SeedingMode パラメーターが追加されました
  - -ConnectionString パラメーターが Get-SqlDatabase に追加されました
- SQL Server on Linux
    - ログ配布に対する一般的な機能強化と修正を行いました。
  - ネイティブ Linux パスの Attach、Restore、Backup データベースのサポートが追加されました
  - 監査ログ宛先フォルダーのネイティブ Linux パスのサポートが追加されました
- Analysis Services
  - DAX クエリ ウィンドウ:
    - エディターでのかっこの照合
    - DEFINE MEASURE と DEFINE VAR の構文のサポート
    - さまざまな Intellisense の機能強化
  - ユニバーサル認証
    - ユーザーはパスワードを指定しないでユーザー名を指定することができ、Azure ログイン ダイアログが接続を処理します
  - SSMS PQ 統合: 
    - 構造化されたデータ ソースのスクリプトが機能します 
    - PQ UI で構造化されたデータ ソースの表示と編集
- 新しい [一意制約の追加] テンプレート
- Showplan
    - プロパティ ウィンドウにスレッド全体の経過時間の合計ではなく最大値を表示します。
    - 新しい mem grant 演算子のプロパティを公開します。
    - ライブ クエリ統計の [クエリの編集] ボタンが有効になりました。
    - インターリーブ実行のサポート
  - [実際の実行プランの分析] の新しいオプション
  - プラン表示の比較に対する全般的改良
  - プラン表示の比較機能に、2 つのクエリ プランの一致するノード間の基数推定での大きな違いを見つけて、考えられる根本原因の基本分析を実行する機能が導入されました。
- 登録済みサーバー エクスプローラーから Configuration Manager を削除しました。
- Azure Blob ストレージから監査ログを読み取り可能
- Always Encrypted にパラメーター化機能が追加されました。詳細については、[このページ](https://blogs.msdn.microsoft.com/sqlsecurity/2016/12/13/parameterization-for-always-encrypted-using-ssms-to-insert-into-update-and-filter-by-encrypted-columns/)を参照してください。 
- Azure SQL DB への AAD ユニバーサル認証接続でカスタム テナント ID がサポートされるようになりました。 
- Azure SQL Database のスクリプト生成で、テキスト、ルール、およびデータベースが完全にスクリプト化されるようになりました。
- スプラッシュ スクリーンでの SSMS と Profiler のブランド化が修正されました。
- SSMS からユーティリティ コントロール ポイントの UI が削除されました。
- SSMS は "PremiumRS" エディションの SQL Azure データベースを作成できるようになりました
- Always On 可用性グループ
  - 新しいクラスターの種類 EXTERNAL と NONE のサポートが追加されます
    - Linux での SQL Server 2000 のサポートが追加されます
    - 初期データ同期のためのオプションとして自動シード処理が追加されます
    - エンドポイント URL の処理、DB の更新、UI のレイアウトなど、いくつかの欠陥を修正しました
    - Azure レプリカ関連の機能を削除しました
  - いくつかの可用性グループ キーワードについて IntelliSense を改善しました
- 利用状況モニター
  - SSMS 出力ウィンドウに新しい [利用状況モニター] ウィンドウを追加しました
  - ポップアップ メッセージではなく出力ウィンドウに情報を記録するように、接続エラー/タイムアウト メッセージを変更しました
  - [概要] セクションで空グラフ (5 番目のグラフ) を削除しました
  - 利用状況モニターのデータ収集が一時停止した場合の [(一時停止)] を [概要] タイトルに追加しました
  - SQL Server のグラフの強化 
    - グラフ ノードとエッジ テーブルの新しいアイコン
    - グラフ ノードとエッジ テーブルを [グラフ テーブル] フォルダーに表示
    - グラフ ノードとエッジ テーブルを作成するためのテンプレートを使用可能
- プレゼンテーション モード
    - クイック起動 (Ctr+Q) で 3 つの新しいタスクを使用できます。
    - PresentOn: プレゼンテーション モードをオンにします。
    - PresentEdit: プレゼンテーション モードでのプレゼンテーションのフォント サイズを編集します。  クエリ エディター用の "テキスト エディター フォント"。  その他のコンポーネント用の "環境フォント"。
    - RestoreDefaultFonts: 既定の設定に戻ります。
    - *注: 現時点では、PresentOff コマンドは存在しません。プレゼンテーション モードをオフにするには、RestoreDefaultFonts を使用します。*

### <a name="bug-fixes"></a>バグの修正

- surfacebook タッチパッドでプラン表示をスクロールしたときに SSMS がクラッシュする問題を修正しました
- 復元中またはオフライン中のデータベースのプロパティを取得するときに SSMS が長時間ハングする問題を修正しました 
- RC ビルドで "ヘルプ ビューアー" が開かない問題を修正しました
- "メンテナンス プラン タスク ツールボックス" アイテムが SSMS にない問題を修正しました。
- データベースの名前に中かっこが含まれている場合にデータベースを圧縮できない SSMS の問題を修正しました。 [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3122618)を参照)。
- SSMS が Azure データベースの削除をスクリプト化しようとして実際にはデータベース自体を削除していた問題を修正しました。 [Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3131458/)を参照)。
- ユーザー定義テーブル型で既定値がスクリプト化されない問題を修正しました ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3119027)を参照)。
- インデックスのコンテキスト メニューに関するパフォーマンスの改善を再度実行しました ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3120783)を参照)。
- 実行プランで欠落インデックスの上にマウスを置いたときに過剰なちらつきを発生させる問題を修正しました ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3118510)を参照)。
- スクリプト作成時に SSMS の DB オフラインがオンラインになる問題を修正しました ([Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3118550)を参照)。
- SSMS のローカライズされた (英語以外の) バージョンで、さまざまな UI の修正を実行しました。
- SQL 2016 SP1 Standard Edition をターゲットとした場合に [Always Encrypted キー] ノードが欠落する問題を修正しました。
- Always Encrypted
    - SQL 2016 RTM Standard Edition または SQL 2014 (またはそれより前) のサーバーをターゲットとした場合に、[常に暗号化] メニューが間違って有効化されていました。
    - CREATE または ALTER 構文を使用すると、IntelliSense でエラーが報告される問題を修正しました。
    - CMK/CEK にエスケープする必要がある (角かっこで囲まれた) 文字が含まれていた場合、暗号化が失敗する問題を修正しました。
    - SSMS でメモリ不足例外が発生すると、代わりにネイティブ (64 ビット) の PowerShell を使用することを提案するエラーがユーザーに表示されます。
    - ユーザーが従来の Azure サブスクリプションではなく Resource Group Manager サブスクリプションを使用した場合に AE ウィザードが失敗する問題を修正しました。
    - ユーザーがいずれのサブスクリプションにもアクセス許可がないか Azure Key Vault を持っていない場合に、AE ウィザードに適切でないエラーが表示される問題を修正しました。
    - 複数の AAD があるときに Azure Key Vault のサインイン ページに Azure サブスクリプションが表示されないという AE ウィザードの問題を修正しました。
    - Azure Key Vault のサインイン ページに、ユーザーが閲覧者アクセス許可を持っている Azure サブスクリプションが表示されないという AE ウィザードの問題を修正しました。
  - リソース ファイルを正しく読み込めず、不正確なエラー メッセージを表示していた問題を修正しました
- SSMS の [セットアップ] ページ上のハイパーリンクのコントラストを改善しました。
- SQL Server Express (2016 SP1) に接続したときに Polybase ノードが表示されない問題を修正しました。
- SSMS が Azure DB の互換性レベルを v140 に変更できない問題を修正しました
- Azure データベースの一覧を展開するときのオブジェクト エクスプローラーのパフォーマンスを強化しました ([Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3100675)を参照)。
- リレーショナル サーバー以外の種類のサーバー (AS\RS\IS) で [SQL Server ログの表示] コンテキスト メニュー項目が間違って表示される問題を修正しました。 
- SQL 認証を使用する Analysis Services のパーティション クエリの構文チェックで、ログイン失敗メッセージが表示される問題を修正しました。
- SSMS で、プレビュー 1400 コンパクト レベルの AS 表形式モデルの名前を変更するとエラーが発生する問題を修正しました。
- まれな状況で、AS サーバー上で無効な操作を試行した後で発生する可能性がある "モデルの操作に失敗する" 問題を修正しました。モデルの保存に失敗した後、ローカルの変更は元に戻ります。
- Analysis Services 同期データベースのポップアップ ダイアログの文字の間違いを修正しました。
- コンテナーのバックアップ/復元ダイアログが、複数のモニター セットアップで画面の表示領域を超えて表示される。 
- 対象オブジェクトの名前に "]" が含まれている場合、SecurityPolicy を作成できない。
- SSMS 2016 の [最近使用した項目を開く] メニューに、最近保存したファイルが表示されない ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)を参照)。
- VS Shell の更新時のユーザー設定のリセットが削除されました。
- ユーザーが SQL Server 2017 のデータベースの互換性レベルを変更できないという問題を修正しました。
- AAD ユニバーサル認証を使用するクエリ ウィンドウで、1 時間後にクエリを更新できなくなる。
- SSMS からユーティリティ コントロール ポイントの UI が削除されました。
- トークンの初期の有効期限が切れると、AD ユニバーサル認証接続でデータを照会できない。
- Azure SQL DB 間のルールをスクリプト化できない。
- SQL PowerShell が以前の SQL インスタンス (2014 以前) に接続できないという問題が修正されました ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/1138754/sql-server-sqlps-powershell-module-fails-connection-to-sql-2012-instance)を参照)。
- 登録済みサーバーのインポートに失敗すると SSMS がクラッシュする原因となる問題が修正されました。
- ユーザーにデータベースに対する特定のアクセス許可がある場合に SSMS がクラッシュする原因となる問題が修正されました。 
- SSMS - ビューの確認時にデザイン画面にテーブルが表示されなくなる ( [Connect アイテム](https://connect.microsoft.com/SQLServer/feedback/details/2946125/ssms-tables-disappears-from-design-surface-while-reviewing-views)を参照)。 
- テーブルのスクロール バーでテーブルの内容をスクロールできない。上下の方向キーでのみスクロールできる。 バグがあるスクロール バーを使用してスクロールを試した後でテーブルの内容をスクロールできる場合もある ( [Connect アイテム](
http://connect.microsoft.com/SQLServer/feedback/details/3106561/sql-server-manager-2016-bug-in-design-view)を参照)。 
- ルート ノードを更新した後、登録済みサーバーにアイコンが表示されない。
- Azure v12 サーバーで [データベースの作成] のスクリプト ボタンを使用してスクリプトを実行すると、"スクリプトを作成するアクションはありません" というメッセージが表示される。
- SSMS の [サーバーに接続] ダイアログで、新しい接続ごとの [追加のプロパティ] タブがクリアされない。
- タスクの生成スクリプトで、Azure SQL DB のデータベースの生成スクリプトが生成されない。
- ビュー デザイナーのスクロール バーが無効になっているように表示される。
- Always Encrypted AVK キーのパスにバージョン ID が含まれていない。
- クエリ ウィンドウ内のエンジン エディション クエリの数が削減されました ( [Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3113387)を参照)。
- 暗号化が正しく処理されていない状態でモジュールを更新すると、Always Encrypted でエラーが発生する。
- OLTP と OLAP の既定の接続タイムアウト値が 15 秒から 30 秒に変更され、無視された接続エラーのクラスが修正されました。 
- カスタム レポートの起動時の SSMS のクラッシュが修正されました ( [Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3118856)を参照)。
- Azure SQL データベースで [スクリプトの生成] が 実行できないという問題が修正されました。
- [スクリプト化] と [スクリプトの生成] ウィザードが修正され、ストアド プロシージャなどのオブジェクトのスクリプト化の際に余分な改行が追加されないようになります ( [Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3115850)を参照)。
- SQLAS PowerShell プロバイダー: Dimension フォルダーと MeasureGroup フォルダーに LastProcessed プロパティが追加されます ( [Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3111879)を参照)。
- ライブ クエリ統計: バッチの最初のクエリしか表示されないという問題が修正されました ( [Connect アイテム] (http://connect.microsoft.com/SQLServer/feedback/details/3114221)  
- プラン表示: プロパティ ウィンドウにスレッド全体の合計ではなく、最大値が表示される。
- クエリ ストア: 豊富な実行バリエーションの新しいレポートがクエリに追加される。
- オブジェクト エクスプローラーのパフォーマンスの問題 ([Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3114074)を参照):
    - テーブルのコンテキスト メニューがすぐにハングする。
    - テーブルのインデックスを右クリックすると SSMS の動作が遅くなる (リモート (インターネット) 接続経由の場合)。 
    - サーバーでのテーブルの並べ替えクエリの発行を避ける。
- SSMS から (Azure VM にデータベースを展開するための) Azure 展開ウィザードが削除されました。
- SSMS の実行プランに不足しているインデックスが表示されないという問題が修正されました ([Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3114194)を参照)。
- SSMS での一般的なシャットダウン時のクラッシュの問題が修正されました。
- オブジェクト エクスプローラーで、PolyBase|スケールアウト グループ ノードのコンテキスト メニューを表示したときにエラーが発生する問題が修正されました ([Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3115128)を参照)。
- データベースに対するアクセス許可を表示しようとすると SSMS がクラッシュする場合があるという問題が修正されました。
- クエリ ストア: クエリ ストア レポートの結果グリッドのコンテキスト メニュー項目が全体的に改善されました。
- 関連付けられていないオブジェクトで既存のテーブルに対して Always Encrypted を構成すると、エラーが発生して実行できない ( [Connect アイテム](http://connect.microsoft.com/SQLServer/feedback/details/3103181)を参照)。
- 複数のスキーマを持つ既存のデータベースに対して Always Encrypted を構成できない ( [Connect アイテム] (http://connect.microsoft.com/SQLServer/feedback/details/3109591)
- データベースにシステム ビューを参照するビューが含まれているため、Always Encrypted の暗号化された列ウィザードでエラーが発生する ( [Connect アイテム] (http://connect.microsoft.com/SQLServer/feedback/details/3111925)
- Always Encrypted を使用して暗号化する場合、暗号化が正しく処理されていない状態でモジュールを更新するとエラーが発生する。
- [新規サーバーの登録] ダイアログで UI が切り捨てられる問題が修正されました。
- 引用符で囲まれた文字列定数値を含む式が DMF 条件 UI で正しく更新されない問題が修正されます。
- カスタム レポートの実行時に SSMS がクラッシュする原因と思われる問題が修正されました。
- [Scale Out で実行] メニュー項目が フォルダー ノードに追加されます。
- Azure SQL DB ファイアウォール ホワイト リスト IP アドレス機能の問題を修正しました
- AS 多次元パーティションのソースの編集時にオブジェクト参照が例外を設定しない原因であった SSMS の問題を修正しました
- 多次元 AS サーバーから顧客アセンブリを削除するときにオブジェクト参照が例外を設定しない原因であった SSMS の問題を修正しました
- AS テーブル 1400 db の名前変更が失敗した問題を修正しました
- 接続プロパティ ダイアログからの 1400 互換性レベル AS テーブル データソースのスクリプト化に関する問題を修正しました
- 1400 互換性レベル モデル内のテーブルが少なくとも 1 つのパーティションを持つという前提を削除しました
- Ctrl + R キーで SSMS DAX クエリ エディターの結果ウィンドウが切り替わるようになりました


## <a name="downloadssdtmediadownloadpng-ssms-1653httpgomicrosoftcomfwlinklinkid840946"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 16.5.3](http://go.microsoft.com/fwlink/?LinkID=840946)
一般公開 | ビルド番号: 13.0.16106.4

[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40a)

このリリースでは次の問題が修正されました。

* SSMS 16.5.2 で、テーブルに複数のスパース列がある場合に 'Table' ノードが拡張される原因となっていた問題が修正されました。

* ユーザーは、SSIS カタログに、Microsoft Dynamics AX/CRM Online のリソースに接続される OData 接続マネージャーを含む SSIS パッケージを展開できます。 詳細については、「[OData 接続マネージャー](../integration-services/connection-manager/odata-connection-manager.md)」を参照してください。

* 関連付けられていないオブジェクトで既存のテーブルに対して Always Encrypted を構成すると、エラーが発生して実行できない ( [Connect ID 3103181](https://connect.microsoft.com/SQLServer/feedback/details/3103181/setting-up-always-encrypted-on-an-existing-table-fails-with-errors-on-unrelated-objects) を参照)。

* 複数のスキーマを持つ既存のデータベースに対して Always Encrypted を構成できない ( [Connect ID 3109591](https://connect.microsoft.com/SQLServer/feedback/details/3109591/sql-server-2016-always-encrypted-against-existing-database-with-multiple-schemas-doesnt-work) を参照)。

* データベースにシステム ビューを参照するビューが含まれているため、Always Encrypted の暗号化された列ウィザードでエラーが発生する ( [Connect ID 3111925](https://connect.microsoft.com/SQLServer/feedback/details/3111925/sql-server-2016-always-encrypted-encrypted-column-wizard-failed-task-failed-due-to-following-error-cannot-save-package-to-file-the-model-has-build-blocking-errors) を参照)。

* Always Encrypted を使用して暗号化する場合、暗号化が正しく処理されていない状態でモジュールを更新するとエラーが発生する。

* *[最近使用した項目を開く]* メニューに、最近保存したファイルが表示されない ( [Connect ID 3113288](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files) を参照)。

* テーブルのインデックスを右クリックすると SSMS の動作が遅くなる (リモート (インターネット) 接続経由の場合)。 [Connect ID 3114074](https://connect.microsoft.com/SQLServer/feedback/details/3114074/ssms-slow-when-right-clicking-an-index-for-a-table-over-a-remote-internet-connection) を参照)。
 
* SQL デザイナーのスクロール バーの問題が修正されました ( [Connect ID 3114856](http://connect.microsoft.com/SQLServer/feedback/details/3114856/bug-in-scrollbar-on-sql-desginer-in-ssms-2016) を参照)。

* テーブルのコンテキスト メニューがすぐにハングする。 
 
* SSMS で利用状況モニターの例外がスローされ、クラッシュする場合がある ( [Connect ID 697527](https://connect.microsoft.com/SQLServer/feedback/details/697527/) を参照)。

* ".NET ランタイムの内部エラーにより、処理が中止されました。IP 71AF8579 (71AE0000)、終了コード 80131506" という内容のエラーで SSMS 2016 がクラッシュする。


## <a name="ssms-1651"></a>SSMS 16.5.1
一般公開 | ビルド番号: 13.0.16100.1

* 制約の確認時に Invoke-Sqlcmd で誤って複数の行が挿入されるという問題を修正しました。 [Microsoft Connect アイテム: 811560](https://connect.microsoft.com/SQLServer/feedback/details/811560)

* 可用性グループの作成時に ENU 以外の言語バージョンが完全に動作しないという問題を修正しました。

* クエリ プラン XML をクリックしたときに適切な SSMS UI が開かないという問題を修正しました。


## <a name="downloadssdtmediadownloadpng-ssms-165httpgomicrosoftcomfwlinklinkid799832"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 16.5](http://go.microsoft.com/fwlink/?LinkID=799832)
一般公開 | ビルド番号: 13.0.16000.28


[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x40a)

* テーブル名に ";:" が含まれるデータベースをクリックするとクラッシュすることがあるという問題を修正しました。
* [AS Tabular Database Properties] (AS 表形式データベースのプロパティ) ウィンドウの [モデル] ページに変更を加えると、元の定義がスクリプト出力されるという問題を修正しました。 
[Microsoft Connect アイテム: 3080744](https://connect.microsoft.com/SQLServer/feedback/details/3080744) 
* [最近使ったファイル] の一覧に一時ファイルが追加されるという問題を修正しました。  
[Microsoft Connect アイテム: 2558789](https://connect.microsoft.com/SQLServer/feedback/details/2558789)
* オブジェクト エクスプローラー ツリーのユーザー テーブル ノードで、[圧縮の管理] メニュー項目が無効になるという問題を解決しました。  
[Microsoft Connect アイテム: 3104616](https://connect.microsoft.com/SQLServer/feedback/details/3104616)

* オブジェクト エクスプローラー、登録済みサーバー エクスプローラー、およびテンプレート エクスプローラーのフォントサイズ、およびエクスプ ローラーの詳細をユーザーが設定できないという問題を解決しました。 エクスプローラーのフォントには、環境フォントが使用されます。  
[Microsoft Connect アイテム: 691432](https://connect.microsoft.com/SQLServer/feedback/details/691432)

* 接続が失われると、SSMS は常に既定のデータベースに再接続するという問題を解決しました。  
[Microsoft Connect アイテム: 3102337](https://connect.microsoft.com/SQLServer/feedback/details/3102337)

* 実行プラン アイコンを含む、ポリシー管理およびクエリ エディター ウィンドウで、多くの高 DPI 問題を修正しました。

* 拡張イベントのフォントと色を構成するためのオプションが見つからないという問題を修正しました。

* アプリケーションを閉じるとき、またはエラー ダイアログ ボックスが表示されるときに発生する SSMS のクラッシュの問題を修正しました。


## <a name="downloadssdtmediadownloadpng-ssms-1641-september-2016httpgomicrosoftcomfwlinklinkid799832"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 16.4.1 (2016 年 9 月)](http://go.microsoft.com/fwlink/?LinkID=799832)
一般公開 | ビルド番号: 13.0.15900.1

[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x40a)

*  ストアド プロシージャの ALTER/変更を実行しようとすると失敗するという問題を修正しました。  
[Microsoft Connect アイテム #3103831](https://connect.microsoft.com/SQLServer/feedback/details/3103831)

* PowerShell でデータの表示や書き込みを行うための新しいコマンドレット 'Read-SqlTableData'、'Read-SqlViewData'、'Write-SqlTableData'。  
[Trello Read-SqlTableData カード](https://trello.com/c/FXVUNJ8x/131-read-sqltabledata)  
[Microsoft Connect アイテム #2685363](https://connect.microsoft.com/SQLServer/feedback/details/2685363)
    
* 新しい 'Add-SqlLogin' コマンドレット。PowerShell を使った新しいログイン管理シナリオを可能にします。  
[Microsoft Connect アイテム #2588952](https://connect.microsoft.com/SQLServer/feedback/details/2588952)
    
*  さまざまな国のクラウドに接続するユーザーのためのサポートと使いやすさが向上しています。
    
    
*  メモリ不足例外がスローされるという問題を修正しました。  
[Microsoft Connect アイテム #3062914](https://connect.microsoft.com/SQLServer/feedback/details/3062914)  
[Microsoft Connect アイテム #3074856](https://connect.microsoft.com/SQLServer/feedback/details/3074856)
    
*  スキーマによるフィルター処理というフィルター オプションを選択できないという問題を修正しました。  
[Microsoft Connect アイテム #3058105](https://connect.microsoft.com/SQLServer/feedback/details/3058105)  
[Microsoft Connect アイテム #3101136](https://connect.microsoft.com/SQLServer/feedback/details/3101136)
    
*  ストレッチ データベースのモニター ウィンドウにアクセスできないという問題を修正しました。
    
*  F1 ヘルプで常にオンライン コンテンツが開くという問題を修正しました。 オンラインとオフラインのどちらのヘルプを参照するかを、[ヘルプ] メニューの "ヘルプ設定の設定" で選べるようになりました。   
[Microsoft Connect アイテム #2826366](https://connect.microsoft.com/SQLServer/feedback/details/2826366)
    
*  1200 レベルの Analysis Services 表形式モデルをスクリプト化するときに、パスワードがスクリプト用に除去されない (サーバー バージョンでは除去されていても) という問題を解決しました (クライアント モデル オブジェクトはスクリプト化の前に同期されるようになりました)。
    
*  'SELECT TOP N ROWS' オプションを選択すると、TOP 演算子について非推奨の構文が生成されるという問題を修正しました。  
[Microsoft Connect アイテム #3065435](https://connect.microsoft.com/SQLServer/feedback/details/3065435)
    
*  SSMS のさまざまなレイアウトの問題を修正しました。たとえば、[ログインのプロパティ] ページや詳細設定クエリ実行オプションです。   
[Microsoft Connect アイテム #3058199](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Microsoft Connect アイテム #3079122](https://connect.microsoft.com/SQLServer/feedback/details/3058199)  
[Microsoft Connect アイテム #3071384](https://connect.microsoft.com/SQLServer/feedback/details/3071384)
    
*  ユーザーが新しいクエリ ウィンドウを開くたびにソリューションが自動的に作成されるという問題を修正しました。   
[Microsoft Connect アイテム #2924667](https://connect.microsoft.com/SQLServer/feedback/details/2924667)    
[Microsoft Connect アイテム #2917742](https://connect.microsoft.com/SQLServer/feedback/details/2917742)   
[Microsoft Connect アイテム #2612635](https://connect.microsoft.com/SQLServer/feedback/details/2612635)
    
*  オブジェクト エクスプローラーでシステム データベースの中のテンポラル テーブルを拡張できないという問題を修正しました。  
[Microsoft Connect アイテム #2551649](https://connect.microsoft.com/SQLServer/feedback/details/2551649)
    
*  SSMS が SELECT @@trancount というクエリをバッチ実行後に実行するという問題を修正しました。    
[Microsoft Connect アイテム #3042364](https://connect.microsoft.com/SQLServer/feedback/details/3042364)
    
*  Analysis Services でスクリプトをサーバーのプロパティ ページから作成すると接続ダイアログが非表示になるという問題を修正しました。
    
*  Ctrl + Q キーを押してもクイック起動ツール バーが選択されないという問題を修正しました。
    
*  データベースの MaxSize を [サーバーのプロパティ] ダイアログで変更するときにデータベースが 2 TB を超えていると中断されるという問題を修正しました。  
[Microsoft Connect アイテム #1231091](https://connect.microsoft.com/SQLServer/feedback/details/1231091)
    
*  データベースの復元ウィザードで、先頭にホワイトスペースのあるファイル名が受け付けられないという問題を修正しました。   
[Microsoft Connect アイテム #2395147](https://connect.microsoft.com/SQLServer/feedback/details/2395147)



## <a name="downloadssdtmediadownloadpng-ssms-163-august-2016httpgomicrosoftcomfwlinklinkid799832"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 16.3 (2016 年 8 月)](http://go.microsoft.com/fwlink/?LinkID=799832)
一般公開 |バージョン番号: 13.0.15700.28


[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x40a)

* SSMS の毎月のリリースは番号が付けられるようになりました。

* [新しい認証オプション **「Active Directory ユニバーサル認証」**](https://azure.microsoft.com/documentation/articles/sql-database-ssms-mfa-authentication/)。 これは、多要素、パスワード、および統合認証メカニズムをサポートする Azure Active Directory によって実行されるトークン ベースの認証メカニズムです。

* SQL Server Profiler テンプレートの機能に適した新しい拡張イベント テンプレート [(Microsoft Connect アイテム #2543925)](../tools/sql-server-profiler/sql-server-profiler-templates.md)。

* Azure SQL データベースの新しい [データベースの作成] と [データベースのプロパティ] ダイアログ ボックス。

* PowerShell を使用して SQL Server ログインの管理を実行するための新しい ’Get SqlLogin’ コマンドレットと 'Remove-SqlLogin’ コマンドレット。  
*リンクされている、顧客のバグ要求:*   
[Microsoft Connect アイテム #2588952。](https://connect.microsoft.com/SQLServer/feedback/details/2588952/)

* 任意のプロバイダーとキー パスの列マスター キーの作成のサポートを追加する新しい PowerShell コマンドレット ’New-SqlColumnMasterKeySettings’。

* SSMS での Azure SQL データベースの作成を効率化する新しい [データベースの作成] ダイアログ ボックス。

* SSMS オブジェクト エクスプ ローラーの 'データベース' のノードでのフィルタリングのサポート。 データベースの一覧をフィルター処理するには、オブジェクト エクスプ ローラーで 'データベース' ノードに移動し、オブジェクト エクスプ ローラーのツールバーでフィルター アイコンをクリックします。

* [バックアップと復元] ウィザードでの Azure Resource Manager (ARM) タイプのストレージ アカウントのサポート。

* [高解像度表示の初期ベータ版のサポート](https://blogs.msdn.microsoft.com/sqlreleaseservices/ssms-highdpi-support/)。  
*リンクされている、顧客のバグ要求:*   
[Microsoft Connect アイテム #1129301](https://connect.microsoft.com/SQLServer/feedback/details/1129301/management-studio-is-unusable-on-a-4k-display)、 [Microsoft Connect アイテム #1858763](https://connect.microsoft.com/SQLServer/feedback/details/1858763/)、 [Microsoft Connect アイテム #1852671](https://connect.microsoft.com/SQLServer/feedback/details/1852671/)、 [Microsoft Connect アイテム #1487643](https://connect.microsoft.com/SQLServer/feedback/details/1487643/)、  [Microsoft Connect アイテム #1355641](https://connect.microsoft.com/SQLServer/feedback/details/1355641/)、 [Microsoft Connect アイテム #2161595](https://connect.microsoft.com/SQLServer/feedback/details/2161595/)、 [Microsoft Connect アイテム #1854041](https://connect.microsoft.com/SQLServer/feedback/details/1854041/)、 [Microsoft Connect アイテム #1055617](https://connect.microsoft.com/SQLServer/feedback/details/1055617/)、 [Microsoft Connect アイテム #2448774](https://connect.microsoft.com/SQLServer/feedback/details/2448774/)、 [Microsoft Connect アイテム #1521405](https://connect.microsoft.com/SQLServer/feedback/details/1521405/)、 [Microsoft Connect アイテム #2117853](https://connect.microsoft.com/SQLServer/feedback/details/2117853/)、 [Microsoft Connect アイテム #2014256](https://connect.microsoft.com/SQLServer/feedback/details/2014256/)、 [Microsoft Connect アイテム #2162218](https://connect.microsoft.com/SQLServer/feedback/details/2162218/)、 [Microsoft Connect アイテム #2344551](https://connect.microsoft.com/SQLServer/feedback/details/2344551/)、 [Microsoft Connect アイテム #1664436](https://connect.microsoft.com/SQLServer/feedback/details/1664436/)、 [Microsoft Connect アイテム #2554043](https://connect.microsoft.com/SQLServer/feedback/details/2554043/)、 [Microsoft Connect アイテム #2983216](https://connect.microsoft.com/SQLServer/feedback/details/2983216/)、 [Microsoft Connect アイテム #2021706](https://connect.microsoft.com/SQLServer/feedback/details/2021706/)

* SQL Server クエリ ストアからのワークロードの自動読み取りをサポートするためのデータベース エンジン チューニング アドバイザー (DTA) を機能強化。

* クラスター化列ストア インデックス、非クラスター化列ストア インデックス、および行ストア インデックスに関するインデックスの推奨事項を表示するよう、データベース エンジン チューニング アドバイザー (DTA) を機能強化。

* SQL Server Analysis Services PowerShell コマンドレットを使用したデータベース コンソール (DBCC) コマンドの送信のサポート。

* SSMS で、復号化された AlwaysEncrypted ラージ オブジェクト (LOB) 列のクリア テキストを表示するようバグを修正。  
*リンクされている、顧客のバグ要求:*   
[Microsoft Connect アイテム #2413024](https://connect.microsoft.com/SQLServer/feedback/details/2413024/cannot-view-cleartext-of-alwaysencrypted-lob-columns-in-ssms)

* Windows の視覚スタイルが有効でない場合のクラッシュを解決するよう [Always Encrypted] ダイアログボックスのバグを修正。

* SQL Server インスタンスへの接続を妨げる 'メソッドが見つかりませんでした' エラーのバグを修正。

* datetimeoffset を含むパーティション関数を作成するときの SSMS クラッシュのバグを修正。

* Distributed Replay 管理ツール (DReplay.exe) を起動するための Microsoft .NET 3.5 の削除要件を追加するようバグを修正。

* サーバーの完全修飾名をサポートするよう [Analysis Services 配置] ウィザードのバグを修正。

* 2016 互換性モデルの Analysis Services 表形式モデルでパーティションを表示するよう SSMS のバグを修正。  
*リンクされている、顧客のバグ要求:*   
[Microsoft Connect アイテム #2845053](https://connect.microsoft.com/SQLServer/feedback/details/2845053/ssms-cannot-display-partitions-in-tabular-models-in-2016-compatibility-level) 

* Analysis Services 表形式モデルおよび SQL Server 共有管理オブジェクト (SMO) におけるパフォーマンスの改善およびバグの修正。 


---
## <a name="downloadssdtmediadownloadpng-ssms-july-2016-hotfix-updatehttpgomicrosoftcomfwlinklinkid799832"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 2016 年 7 月の修正プログラム](http://go.microsoft.com/fwlink/?LinkID=799832)
一般公開 |バージョン番号: 13.0.15600.2

[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x40a)

* **不足している右クリック メニュー項目を有効にするよう SSMS のバグを修正**。  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2883440](https://connect.microsoft.com/SQLServer/feedback/details/2883440/lost-table-design-and-edit-top-n-rows-in-tables-context-menu)  
[Microsoft Connect アイテム #2909644](https://connect.microsoft.com/SQLServer/feedback/details/2909644/ssms-2016-is-missing-edit-options-against-sql-express-2014)  
[Microsoft Connect アイテム #2924345](https://connect.microsoft.com/SQLServer/feedback/details/2924345/some-ssms-object-explorer-right-click-menu-options-missing-in-july-update)

---
## <a name="ssms-july-2016"></a>SSMS 2016 年 7 月 
一般公開 |バージョン番号: 13.0.15500.91

* *7 月 5 日編集:* Analysis Services プロセス ダイアログと Analysis Services の配置ウィザードの、表形式データベース向けの SQL Server 2016 (互換性レベル 1200) のサポートを強化。

* *7 月 5 日編集:* 'XACT_ABORT' を設定する SSMS の [クエリ実行オプション] ダイアログ ボックスの新しいオプション。 このオプションは、この SSMS リリースでは既定で有効になっています。実行時エラーが発生した場合に、SQL Server にトランザクション全体をロールバックし、バッチを中止する指示をします。

* SSMS での Azure SQL Data Warehouse のサポート。

* SQL Server PowerShell モジュールの大幅な更新。 これには、新しい [SQL PowerShell モジュールと、Always Encrypted の新しいコマンドレット、SQL エージェント、SQL エラー ログ](https://blogs.technet.microsoft.com/dataplatforminsider/2016/06/30/sql-powershell-july-2016-update)が含まれます。

* Always Encrypted ウィザードでの PowerShell スクリプトの生成のサポート。

* Azure SQL データベースへの接続時間を大幅に短縮。

* 新しい 'Backup to URL' ダイアログによって、SQL Server 2016 データベースのバックアップ向けの Azure Storage の資格情報の作成をサポート。 このダイアログにより、データベースのバックアップを Azure ストレージ アカウントにより効率的に格納できます。
 
* 新しい復元ダイアログによって、Microsoft Azure Storage サービスからの SQL Server 2016 データベース バックアップの復元を効率化。
 
* ユーザーが SELECT 権限を持っていない場合に、SSMS クエリ デザイナーにテーブルを追加できるようバグを修正。

* 'TRY_CAST()' と 'TRY_CONVERT()' 関数の IntelliSense サポートを追加するためのバグを修正。  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2453461](https://connect.microsoft.com/SQLServer/feedback/details/2453461/sql-server-2012-issue-with-try-cast)。

* 'SQLAS' Analysis Services 拡張機能の読み込みを有効にするための PowerShell モジュールのバグを修正。  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2544902](https://connect.microsoft.com/SQLServer/feedback/details/2544902/ssms-march-2016-refresh-sqlps-failed-to-load-the-sqlas-extension)。

* ドラッグ アンド ドロップで Sql ファイルを開くことができるよう、SSMS のエディター ウィンドウのバグを修正。  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2690658](https://connect.microsoft.com/SQLServer/feedback/details/2690658/cannot-drag-sql-files-into-management-studios)。

* 終了時のプロファイラーのクラッシュを修正するようプロファイラーのバグを修正  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2616550](https://connect.microsoft.com/SQLServer/feedback/details/2616550/sql-server-2016-rc2-profiler-version-13-0-1300-275-wont-close-after-trace-is-started-even-after-trace-is-stopped)。  
[Microsoft Connect アイテム #2319968](https://connect.microsoft.com/SQLServer/Feedback/Details/2319968)。

* SSMS テーブル デザイナーでの結合のリンクを編集しようとする際のクラッシュを防ぐよう、SSMS のバグを修正。  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2721052](https://connect.microsoft.com/SQLServer/feedback/details/2721052/ssms-view-design-mode-right-click-on-join-crashes-ssms)。

* Db_owner ロールのメンバーのデータベース スクリプトの生成を有効にするよう SSMS のバグを修正  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2869241](https://connect.microsoft.com/SQLServer/feedback/details/2869241/error-with-script-database-as-create-to-in-ssms-2008r2-and-ssms-2016-june)。

* サーバーがオフラインになった場合、[クエリ] タブを閉じるときの遅延を回避するよう SSMS エディターのバグを修正。  
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2656058](https://connect.microsoft.com/SQLServer/feedback/details/2656058/ssms-2014-2016-query-tab-takes-significantly-longer-to-close-if-the-instance-it-was-connected-to-is-now-offline)。

* SQL Server Express データベースのバックアップ オプションを有効にするようバグを修正。 
*リンクされている、顧客のバグ要求:*  
[Microsoft Connect アイテム #2801910](https://connect.microsoft.com/SQLServer/feedback/details/2801910/ssms-2016-backup-option-not-appearing-in-tasks)。  
[Microsoft Connect アイテム #2874434](https://connect.microsoft.com/SQLServer/feedback/details/2874434/backup-missing-from-tasks-context-menu-in-ssms-2016-when-you-are-connected-to-an-express-instance)。

* 多次元の Analysis Services モデルのデータ フィード プロバイダーが正しく示されるよう、Analysis Services のバグを修正。

----
## <a name="downloadssdtmediadownloadpng-ssms-june-2016httpgomicrosoftcomfwlinklinkid799832"></a>![ダウンロード](../ssdt/media/download.png) [SSMS 2016 年 6 月](http://go.microsoft.com/fwlink/?LinkID=799832)
一般公開 |バージョン番号: 13.0.15000.23

[中国語 (中華人民共和国)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x804) | [中国語 (台湾)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x404) | [英語 (米国)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x409) | [フランス語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x40c) | [ドイツ語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x407) | [イタリア語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x410) | [日本語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x411) | [韓国語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x412) | [ポルトガル語 (ブラジル)](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x416) | [ロシア語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x419) | [スペイン語](https://go.microsoft.com/fwlink/?linkid=799832&clcid=0x40a)

* SSMS を 2016年 6 月リリースから一般公開。

* 現在のドキュメントへの統合が強化され、正規表現を使用した検索が可能な SSMS の新しいクイック検索ダイアログ。 
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/2735513/quick-find-replace-in-ssms-2016-rc3/>

* スクリプトを使用した無人インストールのインストール進行状況とプロセス終了コードを追跡できるよう、SSMS インストーラーを機能強化。

* ヘルプ ドキュメントおよび記事を正しく表示できるよう、SSMS の状況依存の F1 ヘルプのバグを修正。

* スクロール時に SSMS のクラッシュの原因となるクエリ データ ストア '低下したクエリ' ビューのバグを修正。

* Excel 2016 から SQL Server Analysis Services への接続を許可するよう、Excel Analysis Services OLEDB コネクタのバグを修正。

* マルチ モニター システムで、SSMS のメイン ウィンドウと同じのモニターに [接続] ダイアログ ボックスを表示するよう、SSMS の [接続] ダイアログ ボックスのバグを修正。  
*リンクされている、顧客のバグ要求:*  
<https://connect.microsoft.com/SQLServer/feedback/details/724909/connection-dialog-appears-off-screen/>
<https://connect.microsoft.com/SQLServer/feedback/details/755689/sql-server-management-studio-connect-to-server-popup-dialog/>  
<https://connect.microsoft.com/SQLServer/feedback/details/389165/sql-server-management-studio-gets-confused-dealing-with-multiple-displays/>

* Always Encrypted エクスペリエンスのバグを修正。 Always Encrypted メニュー オプションが Stretch Database に対して正しく有効にならないバグを修正しました。 また、SafeNet (Luna SA) HSM プロバイダーを正しく使用しない Always Encrypted ウィザードのバグも修正しました。


## <a name="additional-downloads"></a>追加のダウンロード  
すべての SQL Server Management Studio ダウンロードの一覧については、「[Microsoft ダウンロード センター](https://www.microsoft.com/en-us/download/search.aspx?q=sql%20server%20management%20studio&p=0&r=10&t=&s=Relevancy~Descending)」を検索してください。  
  
SQL Server Management Studio の最新リリースについては、「[SQL Server Management Studio &#40;SSMS&#41; のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)」をご覧ください。  
