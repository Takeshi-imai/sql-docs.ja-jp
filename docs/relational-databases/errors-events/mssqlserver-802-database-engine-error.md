---
title: "MSSQLSERVER_802 - データベース エンジン エラー | Microsoft Docs"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 802 (Database Engine error)
ms.assetid: 5892ed24-4dcb-4bf9-a8a4-a7ca898832d5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 229bf928d06e606bb91332968f313202ab54d92b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver802---database-engine-error"></a>MSSQLSERVER_802 - データベース エンジン エラー
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|802|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|NO_BUFS|  
|メッセージ テキスト|バッファー プールで使用できるメモリが不足しています。|  
  
## <a name="explanation"></a>説明  
この問題は、バッファー プールがいっぱいになり、それ以上バッファー プールのサイズを大きくできない場合に発生します。  
  
## <a name="user-action"></a>ユーザーの操作  
メモリ エラーのトラブルシューティングに役立つ一般的な手順の概略を次に示します。  
  
1.  このサーバー上で、他のアプリケーションやサービスによってメモリが消費されていないか確認します。 重要度の低いアプリケーションやサービスのメモリ消費量が少なくなるように、構成を変更します。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Buffer Manager** および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Memory Manager** のパフォーマンス モニター カウンターを確認します。  
  
3.  次に示す [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ構成パラメーターを確認します。  
  
    -   **max server memory**  
  
    -   **min server memory**  
  
    -   **min memory per query**  
  
    通常とは異なる設定がないか確認し、必要に応じて修正します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で増加した必要なメモリの要件を把握しておきます。 既定の設定については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「サーバー構成オプションの設定」を参照してください。  
  
4.  DBCC MEMORYSTATUS 出力を監視し、エラー メッセージが表示された場合にどのように変化するかを調べます。  
  
5.  ワークロード (同時セッション数や現在実行中のクエリ数など) をチェックします。  
  
次のアクションを実行すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用できるメモリを増やせる可能性があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のアプリケーションがリソースを消費している場合は、そのアプリケーションを停止するか、別のサーバーで実行します。  
  
-   **max server memory** を構成した場合は、設定値を大きくします。  
  
次の DBCC コマンドを実行して、いくつかの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ キャッシュを解放します。  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
問題が解決しない場合は、さらに調査します。ワークロードの軽減が必要になる場合もあります。  
  
