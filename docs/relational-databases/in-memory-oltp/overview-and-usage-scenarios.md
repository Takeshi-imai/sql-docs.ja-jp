---
title: "概要と使用シナリオ | Microsoft Docs"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62c964c5-eae4-4cf1-9024-d5a19adbd652
caps.latest.revision: 5
author: jodebrui
ms.author: jodebrui
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: edf397a4e4922167ae2eafd2c8e78ac97858bd37
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="overview-and-usage-scenarios"></a>概要と使用シナリオ
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

インメモリ OLTP は、トランザクション処理のパフォーマンスの最適化、データの取り込み、データの読み込み、および一時的なデータのシナリオに SQL Server と Azure SQL Database で使用できる高度な技術です。 ここでは、インメモリ OLTP のテクノロジと使用シナリオの概要について説明します。 この情報を参照して、インメモリ OLTP が用途に合っているかどうかを判断してください。 このトピックの最後には、インメモリ OLTP オブジェクトを表示する例、パフォーマンス デモの参照、次のステップに使用できるリソースの参照を掲載しています。

この記事では、SQL Server と Azure SQL Database の両方のインメモリ OLTP テクノロジについて説明します。 次のブログ記事では、Azure SQL Database でのパフォーマンスとリソース活用における利点について、詳細に説明しています。 
- [In-Memory OLTP in Azure SQL Database](https://azure.microsoft.com/blog/in-memory-oltp-in-azure-sql-database/) (Azure SQL Database のインメモリ OLTP)

## <a name="in-memory-oltp-overview"></a>インメモリ OLTP の概要

インメモリ OLTP は、適切なワークロードの場合にパフォーマンスが大きく向上します。 お客様の bwin は、インメモリ OLTP を利用して、SQL Server 2016 を実行する 1 台のコンピューターで [毎秒 120 万要求を達成](https://blogs.msdn.microsoft.com/sqlcat/2016/10/26/how-bwin-is-using-sql-server-2016-in-memory-oltp-to-achieve-unprecedented-performance-and-scale/) しました。 また、Quorum は、Azure SQL Database でインメモリ OLTP を利用して、 [リソース使用率を 70% 下げ](https://customers.microsoft.com/en-US/story/quorum-doubles-key-databases-workload-while-lowering-dtu-with-sql-database)、ワークロードを 2 倍にしました。 一部の事例では、最大 30 倍のパフォーマンス向上が見られていますが、向上率はワークロードによって変わります。

それでは、このパフォーマンス向上は何に由来するのでしょうか。 基本的に、インメモリ OLTP は、データ アクセスとトランザクションの実行を効率化し、同時に実行されるトランザクション間のロックとラッチの競合を取り除くことで、トランザクション プロセスのパフォーマンスを改善します。高速化の理由はデータがメモリ内にあるからではなく、メモリ内のデータを中心にして最適化しているためです。 メモリ内の同時処理が多い計算に関する最新の機能強化を利用するように、データ ストレージ、アクセス、処理アルゴリズムはゼロから再設計されました。

現在では、データがメモリ内にあるからというだけで、障害が発生したときにデータが失われることを意味しなくなりました。 既定で、すべてのトランザクションは完全に持続可能になりました。つまり、SQL Server の他のテーブルと同じ持続可能性の保証があります。トランザクション コミットの一部として、すべての変更はディスク上のトランザクション ログに書き込まれます。 トランザクション コミット後のどこかの時点で障害が発生すると、データベースがオンラインに戻ったときに、コミットされたデータを利用できます。 さらに、インメモリ OLTP は、SQL Server の高可用性と障害復旧機能 (AlwaysOn、バックアップ/復元など) と連携します。

データベースでインメモリ OLTP を利用するには、次に示すオブジェクトの種類から 1 つまたは複数使用します。

- *メモリ最適化テーブル* は、ユーザー データの格納に使用されます。 テーブルは、作成時にメモリが最適化されるように宣言します。
- *非持続的テーブル* は、キャッシュまたは中間の結果セット用の一時的なデータに使用されます (従来の一時テーブルは置き換えられます)。 非持続的テーブルは、DURABILITY=SCHEMA_ONLY を使用して宣言されるメモリ最適化テーブルです。つまり、これらのテーブルを変更しても、IO は発生しません。 そのため、持続性が重要ではない場合、ログ IO リソースの消費を回避することができます。
- *メモリ最適化テーブル型* は、テーブル値パラメーター (TVP) だけでなく、ストアド プロシージャの中間結果セットにも使用されます。 メモリ最適化テーブル型は、従来のテーブル型の代わりに使用できます。 メモリ最適化テーブル型を使用して宣言したテーブル変数と TVP は、非持続的メモリ最適化テーブルの利点 (効率的なデータ アクセス、IO なし) を継承します。
- *ネイティブ コンパイル T-SQL モジュール* は、操作の処理に必要な CPU サイクルを減らして、個々のトランザクションにかかる時間をさらに短縮するために使用されます。 Transact-SQL モジュールは、作成時にネイティブでコンパイルするように宣言します。 このとき、ストアド プロシージャ、トリガー、スカラー ユーザー定義関数という T-SQL モジュールをネイティブでコンパイルできます。

インメモリ OLTP は SQL Server と Azure SQL Database に組み込まれています。 また、これらのオブジェクトは、従来の対応するオブジェクトにとても似た動作なので、多くの場合、データベースとアプリケーションの変更を最小限に抑えながら、パフォーマンスを向上できます。 さらに、同じデータベースにメモリ最適化テーブルと従来のディスクベースのテーブルの両方を持ち、2 つのテーブルに対してクエリを実行することができます。 このトピックの末尾には、これらの種類の各オブジェクトについて、Transact-SQL スクリプト例を掲載しています。

## <a name="usage-scenarios-for-in-memory-oltp"></a>インメモリ OLTP の使用シナリオ

インメモリ OLTP は魔法の高速化ボタンではなく、あらゆるワークロードに適しているわけではありません。 たとえば、ほとんどのクエリが広範囲に及ぶデータに対する集計を行う場合、メモリ最適化テーブルで CPU 使用率は下がりません。このようなシナリオには、列ストア インデックスが役立ちます。

次に、お客様がインメモリ OLTP で成功したシナリオとアプリケーション パターンの一覧を紹介します。

### <a name="high-throughput-and-low-latency-transaction-processing"></a>高スループット、低遅延トランザクションの処理

これはインメモリ OLTP を構築する中核となるシナリオです。個々のトランザクションの低遅延を保ちながら、大量のトランザクションに対応します。

一般的なワークロード シナリオとして、金融商品の取引、スポーツくじ、モバイル ゲーム、広告配信などがあります。 また、一般的なパターンとして、読み取りや更新が頻繁な "カタログ" もあります。 たとえば、大きなファイルが複数ある場合、各ファイルはクラスターの複数のノードに分散され、メモリ最適化テーブル内にある各ファイルの各シャードの場所を分類します。

#### <a name="implementation-considerations"></a>実装に関する注意点

中核となるトランザクション テーブル (つまり、最もパフォーマンスが重要なトランザクションがあるテーブル) にメモリ最適化テーブルを使用します。 ネイティブでコンパイルされたストアド プロシージャを使用して、ビジネス トランザクションに関連付けられたロジックの実行を最適化します。 データベースのストアド プロシージャに組み込むことができるロジック数が多いほど、インメモリ OLTP の利点も大きくなります。

既存のアプリケーションで開始するには:
1. [トランザクション パフォーマンス分析レポート](https://msdn.microsoft.com/library/dn205133.aspx) を使用して移行するオブジェクトを特定し、 
2. 移行に [メモリ最適化](https://msdn.microsoft.com/library/dn284308.aspx) および [ネイティブ コンパイル](https://msdn.microsoft.com/library/dn358355.aspx) アドバイザーを利用します。

#### <a name="customer-case-studies"></a>お客様の導入事例

- CMC Markets は SQL Server 2016 でインメモリ OLTP を利用し、継続的な低遅延を達成しました (「 [Because a second is too long to wait, this financial services firm is updating its trading software now](https://customers.microsoft.com/en-us/story/because-a-second-is-too-long-to-wait-this-financial-services-firm-is-updating-its-trading-software)」(1 秒の待機時間は長すぎるので、今、この金融サービス企業は取引ソフトウェアを更新しています))。
- Derivco は SQL Server 2016 でインメモリ OLTP を利用して、増加したスループットに対応し、ワークロードの急増を処理しています (「 [When an online gaming company doesn’t want to risk its future, it bets on SQL Server 2016](https://customers.microsoft.com/en-us/story/when-an-online-gaming-company-doesnt-want-to-risk-its-future-it-bets-on-sql-server-2016)」(オンライン ゲーム会社は将来を危険にさらしたくない場合、SQL Server 2016 に賭けます))。


### <a name="data-ingestion-including-iot-internet-of-things"></a>IoT (モノのインターネット) などのデータ統合

インメモリ OLTP は、同時にさまざまなソースから大量のデータを取り込む処理が特に得意です。 また、多くの場合、他の取り込み先と比較して、SQL Server データベースにデータを取り込む方が利点があります。これは、SQL ではデータに対するクエリの実行速度がとても速く、リアルタイムで洞察できるためです。

一般的なアプリケーションのパターンは、センサーの読み取りとイベントを取り込み、通知だけでなく履歴分析を可能にする方法です。 複数のソースからでも、一括更新を管理し、同時読み取りのワークロードに対する影響を最小限に抑えることができます。

#### <a name="implementation-considerations"></a>実装に関する注意点

データの取り込みにメモリ最適化テーブルを使用します。 取り込みの大部分が (更新ではなく) 挿入で構成され、データのインメモリ OLTP ストレージの占有領域が重要な場合、次のいずれかを行います。

- [を実行するジョブを使用して、](https://msdn.microsoft.com/library/gg492088.aspx)クラスター化列ストア インデックス `INSERT INTO <disk-based table> SELECT FROM <memory-optimized table>`が指定されたディスクベースのテーブルに定期的にデータを一括オフロードします。または、
- [一時メモリ最適化テーブル](https://msdn.microsoft.com/library/mt590207.aspx) を使用して、履歴データを管理します。このモードでは、履歴データはディスクに保存され、データの移動はシステムによって管理されます。

SQL Server サンプル リポジトリに一時メモリ最適化テーブル、メモリ最適化テーブル型、およびネイティブ コンパイル ストアド プロシージャを使用するスマート グリッド アプリケーション含めることでデータの取り込みを高速化し、センサー データのインメモリ OLTP ストレージの占有領域を管理しています。 

 - [smart-grid-release](https://github.com/Microsoft/sql-server-samples/releases/tag/iot-smart-grid-v1.0) 
 - [smart-grid-source-code](https://github.com/Microsoft/sql-server-samples/tree/master/samples/applications/iot-smart-grid)
 
#### <a name="customer-case-studies"></a>お客様の導入事例

- [Quorum は、Azure SQL Database でインメモリ OLTP を利用することで、主要なデータベースのワークロードを 2 倍にしながら、使用率を 70% 削減しました](http://customers.microsoft.com/story/quorum-doubles-key-databases-workload-while-lowering-dtu-with-sql-database)
- EdgeNet は、SQL Server 2014 のインメモリ OLTP で一括データ読み込みのパフォーマンスを改善し、中間層キャッシュを維持する必要がなくなりました (「 [Data Services Firm Gains Real-Time Access to Product Data with In-Memory Technology](https://customers.microsoft.com/en-us/story/data-services-firm-gains-real-time-access-to-product-d)」(データ サービス会社がインメモリ テクノロジで運用データにリアルタイムにアクセス))
- Beth Israel Deaconess Medical Center は、SQL Server 2014 のインメモリ OLTP でデータ取り込み率を大幅に改善し、ワークロードの急増を処理できました ([https://customers.microsoft.com/en-us/story/strengthening-data-security-and-creating-more-time-for])

### <a name="caching-and-session-state"></a>キャッシュとセッションの状態

インメモリ OLTP テクノロジは、SQL でセッションの状態 (ASP.NET アプリケーションの状態など) を維持する場合におよびキャッシュの場合に特に推奨されます。

ASP.NET セッションの状態は、インメモリ OLTP で特に成功している使用事例です。 SQL Server では、あるお客様が毎秒約 120 万要求を達成しました。 一方、社内のすべての中間層アプリケーションのキャッシュ ニーズにインメモリ OLTP を使用し始めました。 詳細については、「 [How bwin is using SQL Server 2016 In-Memory OLTP to achieve unprecedented performance and scale](https://blogs.msdn.microsoft.com/sqlcat/2016/10/26/how-bwin-is-using-sql-server-2016-in-memory-oltp-to-achieve-unprecedented-performance-and-scale/)」(bwin が SQL Server 2016 のインメモリ OLTP を使用して前例のないパフォーマンスとスケールを達成した方法) を参照してください。

#### <a name="implementation-considerations"></a>実装に関する注意点

varbinary(max) 列に BLOB を格納することで、簡易なキーと値のストアとして非持続的メモリ最適化テーブルを使用できます。 または、SQL Server および Azure SQL Database で [JSON のサポート](https://azure.microsoft.com/blog/json-support-is-generally-available-in-azure-sql-database/) で半構造化キャッシュを実装できます。 最後に、多様なデータ型と制約を含み、完全なリレーショナル スキーマを使用する非持続的なテーブルで、完全なリレーショナル キャッシュを作成できます。

ASP.NET セッションの状態のメモリ最適化を始めるには、GitHub で公開されているスクリプトを利用して、組み込みの SQL Server セッションの状態プロバイダーで作成されるオブジェクトを置き換えます。

- [aspnet-session-state](https://github.com/Microsoft/sql-server-samples/tree/master/samples/applications/aspnet-session-state)

#### <a name="customer-case-studies"></a>お客様の導入事例

- bwin は、SQL Server 2014 のインメモリ OLTP で、ループットを大幅に増やし、ASP.NET セッションの状態のハードウェアの占有領域を減らすことができました (「 [Gaming Site Can Scale to 250,000 Requests Per Second and Improve Player Experience](https://customers.microsoft.com/en-us/story/gaming-site-can-scale-to-250000-requests-per-second-an)」(ゲーム サイトを毎秒 250,000 要求に拡張し、プレーヤーのエクスペリエンスを改善することができました))。
- bwin は、SQL Server 2016 でインメモリ OLTP を使用して、ASP.NET セッションの状態を使用してスループットをさらに増加し、会社全体の中間層キャッシュ システムを実装しました (「 [How bwin is using SQL Server 2016 In-Memory OLTP to achieve unprecedented performance and scale](https://blogs.msdn.microsoft.com/sqlcat/2016/10/26/how-bwin-is-using-sql-server-2016-in-memory-oltp-to-achieve-unprecedented-performance-and-scale/)」(bwin が SQL Server 2016 のインメモリ OLTP を使用して前例のないパフォーマンスとスケールを達成している方法))

### <a name="tempdb-object-replacement"></a>tempdb オブジェクトの置き換え

非持続的テーブルとメモリ最適化テーブル型を利用して、従来の tempdb #temp テーブル、テーブル変数、テーブル値パラメーター (TVP) を置き換えます。

メモリ最適化テーブル変数と非持続的テーブルは、従来のテーブル変数と #temp テーブルと比較すると、一般的に CPU が減り、ログの IO が完全になくなります。



#### <a name="implementation-considerations"></a>実装に関する注意点

概要については、「 [Improving temp table and table variable performance using memory optimization](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/)」(メモリ最適化を使用した一時テーブルとテーブル変数のパフォーマンスの向上) を参照してください。

#### <a name="customer-case-studies"></a>お客様の導入事例

- あるお客様は、従来の TVP をメモリ最適化 TVP に置き換えるだけでパフォーマンスを 40% 改善できました (「 [High Speed IoT Data Ingestion Using In-Memory OLTP in Azure](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/04/07/a-technical-case-study-high-speed-iot-data-ingestion-using-in-memory-oltp-in-azure/)」(Azure でのインメモリ OLTP を使用した高速 IoT 取り込み))。


### <a name="etl-extract-transform-load"></a>ETL (抽出、変換、読み込み)

多くの場合、ETL ワークフローには、データのステージング テーブルへの読み込み、データの変換、最終的なテーブルへの読み込みが含まれています。

#### <a name="implementation-considerations"></a>実装に関する注意点

データのステージングには非持続的メモリ最適化テーブルを使用します。 すべての IO が完全になくなり、データ アクセスがより効率的になります。

ワークフローの一部としてステージング テーブルで変換を実行する場合、ネイティブ コンパイル ストアド プロシージャを使用すると、変換を高速化できます。 このような変換を並列して実行できると、メモリ最適化からさらにスケール メリットが得られます。

## <a name="sample-script"></a>サンプル スクリプト

インメモリ OLTP の使用を開始する前に、MEMORY_OPTIMIZED_DATA ファイルグループを作成する必要があります。 さらに、データベース互換性レベル 130 (以上) を使用し、データベース オプション MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT をオンに設定することをお勧めします。

次の場所のスクリプトを使用して、既定のデータ フォルダーにファイルグループを作成し、推奨される設定を構成できます。

- [enable-in-memory-oltp.sql](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql)

次に、データベースで作成できるインメモリ OLTP オブジェクトを説明するためのスクリプトを示します。
  
     -- configure recommended DB option
     ALTER DATABASE CURRENT SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON
     GO
     -- memory-optimized table
     CREATE TABLE dbo.table1
     ( c1 INT IDENTITY PRIMARY KEY NONCLUSTERED,
       c2 NVARCHAR(MAX))
     WITH (MEMORY_OPTIMIZED=ON)
     GO
     -- non-durable table
     CREATE TABLE dbo.temp_table1
     ( c1 INT IDENTITY PRIMARY KEY NONCLUSTERED,
       c2 NVARCHAR(MAX))
     WITH (MEMORY_OPTIMIZED=ON,
           DURABILITY=SCHEMA_ONLY)
     GO
     -- memory-optimized table type
     CREATE TYPE dbo.tt_table1 AS TABLE
     ( c1 INT IDENTITY,
       c2 NVARCHAR(MAX),
       is_transient BIT NOT NULL DEFAULT (0),
       INDEX ix_c1 HASH (c1) WITH (BUCKET_COUNT=1024))
     WITH (MEMORY_OPTIMIZED=ON)
     GO
     -- natively compiled stored procedure
     CREATE PROCEDURE dbo.usp_ingest_table1
       @table1 dbo.tt_table1 READONLY
     WITH NATIVE_COMPILATION, SCHEMABINDING
     AS
     BEGIN ATOMIC
         WITH (TRANSACTION ISOLATION LEVEL=SNAPSHOT,
               LANGUAGE=N'us_english')
     
       DECLARE @i INT = 1
     
       WHILE @i > 0
       BEGIN
         INSERT dbo.table1
         SELECT c2
         FROM @table1
         WHERE c1 = @i AND is_transient=0
     
         IF @@ROWCOUNT > 0
           SET @i += 1
         ELSE
         BEGIN
           INSERT dbo.temp_table1
           SELECT c2
           FROM @table1
           WHERE c1 = @i AND is_transient=1
     
           IF @@ROWCOUNT > 0
             SET @i += 1
           ELSE
             SET @i = 0
         END
       END
     
     END
     GO
     -- sample execution of the proc
     DECLARE @table1 dbo.tt_table1
     INSERT @table1 (c2, is_transient) VALUES (N'sample durable', 0)
     INSERT @table1 (c2, is_transient) VALUES (N'sample non-durable', 1)
     EXECUTE dbo.usp_ingest_table1 @table1=@table1
     SELECT c1, c2 from dbo.table1
     SELECT c1, c2 from dbo.temp_table1
     GO
   

## <a name="resources-to-learn-more"></a>詳細情報:

- [クイック スタート 1: Transact-SQL のパフォーマンスを向上させるインメモリ OLTP テクノロジ](http://msdn.microsoft.com/library/mt694156.aspx)
- インメモリ OLTP を使用したパフォーマンス デモ: [in-memory-oltp-perf-demo-v1.0](https://github.com/Microsoft/sql-server-samples/releases/tag/in-memory-oltp-demo-v1.0)
- [インメモリ OLTP の説明とデモを紹介する 17 分のビデオ](https://www.youtube.com/watch?v=l5l5eophmK4) (デモは 8:25 から)
- [インメモリ OLTP を有効にして推奨されるオプションを設定するスクリプト](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql)
- [主なインメモリ OLTP ドキュメント](https://msdn.microsoft.com/library/dn133186.aspx)
- [インメモリ OLTP が Azure SQL Database のパフォーマンスとリソース活用にもたらす利点](https://azure.microsoft.com/blog/in-memory-oltp-in-azure-sql-database/)
- [メモリ最適化を使用して一時テーブルとテーブル変数のパフォーマンスを改善する](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/)
[SQL Database でインメモリ テクノロジを使用してパフォーマンスを最適化する](https://docs.microsoft.com/azure/sql-database/sql-database-in-memory)
- [メモリ最適化テーブルでのシステム バージョン管理された一時テーブル](https://msdn.microsoft.com/library/mt590207.aspx)
- [インメモリ OLTP - 一般的なワークロード パターンと移行に関する考慮事項](http://msdn.microsoft.com/library/dn673538.aspx) 
