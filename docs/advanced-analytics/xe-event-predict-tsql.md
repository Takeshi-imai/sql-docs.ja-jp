---
title: "予測ステートメントを監視するイベントを拡張 |Microsoft ドキュメント"
titleSuffix: SQL Server
ms.custom: 
ms.date: 03/01/2018
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 0e2847690a8d63753c9246995211d0705128f7ab
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="extended-events-for-monitoring-predict-statements"></a>予測ステートメントを監視する拡張イベント

この記事は、SQL Server の監視し、分析に使用できるジョブで使用する指定した拡張イベントをについて説明します[PREDICT](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)を SQL Server でリアルタイムのスコアリングを実行します。

機械学習 SQL Server に格納されているモデルからスコアを生成するリアルタイム スコア付けします。 予測関数では、R、Python、特定のバイナリ形式を使用して作成されているモデルのみなどに外部の実行時間は必要ありません。 詳細については、次を参照してください。[リアルタイム スコアリング](https://docs.microsoft.com/sql/advanced-analytics/real-time-scoring)です。

## <a name="prerequisites"></a>前提条件

(XEvents とも呼ばれます)、拡張イベントをセッションにイベントを追跡する方法の詳細については、次の記事を参照してください。

+ [拡張イベントの概念とアーキテクチャ](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)
+ [SSMS でのイベント キャプチャを設定します。](https://docs.microsoft.com/sql/relational-databases/extended-events/quick-start-extended-events-in-sql-server)
+ [オブジェクト エクスプ ローラーで、イベント セッションを管理します。](https://docs.microsoft.com/sql/relational-databases/extended-events/manage-event-sessions-in-the-object-explorer)

## <a name="table-of-extended-events"></a>拡張イベントの表

次の拡張イベントでは使用をサポートするすべてのバージョンの SQL Server、 [T-SQL 予測](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)ステートメントでは、Linux、および Azure SQL データベースで SQL Server を含むです。 

予測の T-SQL ステートメントは、SQL Server 2017 に導入されました。 

|name |object_type|description| 
|----|----|----|
|predict_function_completed |イベント  |組み込みコマンドの実行時間の内訳|
|predict_model_cache_hit |イベント|予測関数のモデルのキャッシュからモデルを取得するときに発生します。 他の predict_model_cache_ * イベントと共に、このイベントを使用すると、予測関数のモデルのキャッシュによって引き起こされる問題をトラブルシューティングできます。|
|predict_model_cache_insert |イベント  |   モデルは、予測関数のモデルのキャッシュに挿入するときに発生します。 他の predict_model_cache_ * イベントと共に、このイベントを使用すると、予測関数のモデルのキャッシュによって引き起こされる問題をトラブルシューティングできます。    |
|predict_model_cache_miss   |イベント|モデルが予測関数のモデルのキャッシュに見つからなかった場合に発生します。 SQL Server がメモリを増やす必要があることには、このイベントが頻繁に発生がある可能性があります。 他の predict_model_cache_ * イベントと共に、このイベントを使用すると、予測関数のモデルのキャッシュによって引き起こされる問題をトラブルシューティングできます。|
|predict_model_cache_remove |イベント| モデルが予測関数のモデルのキャッシュから削除されたときに発生します。 他の predict_model_cache_ * イベントと共に、このイベントを使用すると、予測関数のモデルのキャッシュによって引き起こされる問題をトラブルシューティングできます。|

## <a name="query-for-related-events"></a>関連するイベントのクエリ

これらのイベントに対して返されるすべての列の一覧を表示するには、SQL Server Management Studio で、次のクエリを実行します。

```sql
SELECT * FROM sys.dm_xe_object_columns WHERE object_name LIKE `predict%'
```

## <a name="examples"></a>使用例

予測を使用してスコア付けのセッションのパフォーマンスに関する情報をキャプチャするには。

1. 拡張イベント セッション、Management Studio またはサポートされている別の使用を新規作成[ツール](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools)です。
2. イベントを追加`predict_function_completed`と`predict_model_cache_hit`セッションにします。
3. 拡張イベント セッションを開始します。
4. 予測を使用するクエリを実行します。

結果には、これらの列を確認します。

+ 値は、`predict_function_completed`示していますが、モデルの読み込みとスコアリングに費やされたクエリをどの程度時間します。
+ ブール値`predict_model_cache_hit`か、クエリがキャッシュされたモデルを使用するかどうかを示します。 

### <a name="native-scoring-model-cache"></a>ネイティブのスコア付けモデルのキャッシュ

予測するのに特定のイベントだけでなく、キャッシュされたモデルとキャッシュの使用状況に関する詳細情報を次のクエリを使用できます。

ネイティブのスコア付けモデルのキャッシュを参照してください。

```sql
SELECT *
FROM sys.dm_os_memory_clerks
WHERE type = 'CACHESTORE_NATIVESCORING';
```

モデル キャッシュでオブジェクトを参照してください。

```sql
SELECT *
FROM sys.dm_os_memory_objects
WHERE TYPE = 'MEMOBJ_NATIVESCORING';
```

