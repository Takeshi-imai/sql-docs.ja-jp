---
title: MSSQLSERVER_7308 | Microsoft Docs
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
- 7308 (Database Engine error)
- single-threaded apartment mode
ms.assetid: cca9eab9-afb9-463d-abfd-0802257e2c99
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5cf8216f916b6dbfe501f85fe18a5c6990a03762
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver7308"></a>MSSQLSERVER_7308
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|7308|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|RMT_STA_DISABLED|  
|メッセージ テキスト|OLE DB プロバイダー '%ls' を分散クエリに使用することはできません。このプロバイダーは、シングル スレッド アパートメント モードで実行するように構成されています。|  
  
## <a name="explanation"></a>説明  
シングル スレッド アパートメント (STA) モードで実行するように構成されている OLE DB プロバイダーを使用しました。 シングル スレッド アパートメント (STA) モードで実行する OLE DB プロバイダーを分散クエリに使用することはできません。  
  
## <a name="user-action"></a>ユーザーの操作  
このエラーを解決するには、プロバイダーをマルチスレッド アパートメント (MTA) モードで実行するように構成します。 プロバイダーが MTA をサポートしておらず、MTA をサポートするバージョンにアップグレードできない場合は、プロバイダーをプロセス外で実行するように構成することを検討してください。 プロバイダーが MTA またはプロセス外での実行をサポートしているかどうかは、プロバイダーの製造元に問い合わせてください。  
  
