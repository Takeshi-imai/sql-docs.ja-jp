---
title: "Microsoft Azure ストレージへの接続 | Microsoft Docs"
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-f1
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.windowsazurestorage.connect.f1
- SQL13.SWB.WINDOWSAZURESTORAGE.CONNECT.F1
ms.assetid: 
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f6948e2719018550a07b9b20087bcfc255ef72cb
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="connect-to-microsoft-azure-storage"></a>Microsoft Azure Storage への接続
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] **[Microsoft Azure Storage 接続]** ダイアログを使用して、ストレージ アカウントを指定したり、Microsoft Azure への接続を検証したりします。  
  
## <a name="options"></a>および  
Microsoft Azure のアカウントに関する次の情報を指定し、 **[次へ]** をクリックして続行します。  
  
1.  **[ストレージ アカウント]** : ストレージ アカウント名を指定します。

   >[!NOTE]
   > [汎用のストレージ アカウント](https://docs.microsoft.com/en-us/azure/storage/storage-introduction#introducing-the-azure-storage-services)にのみ接続できます。 他の種類のストレージ アカウントに接続すると、次のようなエラーが発生することがあります。
   >
   >  HTTP ヘッダーのいずれか 1 つの値が正しい形式になっていません。 (Microsoft.SqlServer.StorageClient)
   >
   >  リモート サーバーがエラーを返しました: (400) 無効な要求。 (System)

2.  **[アカウント キー]** : 指定したストレージ アカウントのアカウント キーを指定します。  
  
3.  **[セキュリティ保護されたエンドポイントを使用する (HTTPS)]** : 暗号化された通信とネットワーク Web サーバーのセキュア ID を利用します。  
  
4.  **[アカウント キーを保存する]** : 暗号化されたファイルにパスワードが保存されます。  
  
