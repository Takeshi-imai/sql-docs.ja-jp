---
title: "sp_add_log_shipping_secondary_database (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_secondary_database
- sp_add_log_shipping_secondary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_secondary_database
ms.assetid: d29e1c24-3a3c-47a4-a726-4584afa6038a
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 965f2191ba9dbdbba5be91412c1459064972c22c
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="spaddlogshippingsecondarydatabase-transact-sql"></a>sp_add_log_shipping_secondary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ログ配布のセカンダリ データベースを設定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_log_shipping_secondary_database  
[ @secondary_database = ] 'secondary_database',  
[ @primary_server = ] 'primary_server',   
[ @primary_database = ] 'primary_database',  
[, [ @restore_delay = ] 'restore_delay']  
[, [ @restore_all = ] 'restore_all']  
[, [ @restore_mode = ] 'restore_mode']  
[, [ @disconnect_users = ] 'disconnect_users']  
[, [ @block_size = ] 'block_size']  
[, [ @buffer_count = ] 'buffer_count']  
[, [ @max_transfer_size = ] 'max_transfer_size']  
[, [ @restore_threshold = ] 'restore_threshold']   
[, [ @threshold_alert = ] 'threshold_alert']   
[, [ @threshold_alert_enabled = ] 'threshold_alert_enabled']   
[, [ @history_retention_period = ] 'history_retention_period']  
```  
  
## <a name="arguments"></a>引数  
 [  **@secondary_database**  =] '*secondary_database*'  
 セカンダリ データベースの名前を指定します。 *secondary_database*は**sysname**、既定値はありません。  
  
 [  **@primary_server**  =] '*primary_server*'  
 プライマリ インスタンスの名前、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ログ配布構成にします。 *primary_server*は**sysname** NULL にすることはできません。  
  
 [  **@primary_database**  =] '*primary_database*'  
 プライマリ サーバー上のデータベースの名前を指定します。 *primary_database*は**sysname**、既定値はありません。  
  
 [  **@restore_delay**  =] '*restore_delay*'  
 セカンダリ サーバーは、指定されたバックアップ ファイルを復元する前に待機を分単位での時間数。 *restore_delay*は**int** NULL にすることはできません。 既定値は 0 です。  
  
 [  **@restore_all**  =] '*restore_all*'  
 1 に設定すると、セカンダリ サーバーでは復元ジョブの実行時にすべてのトランザクション ログ バックアップが復元されます。 1 以外の場合は、1 つのファイルが復元された後セカンダリ サーバーは停止します。 *restore_all*は**ビット**NULL にすることはできません。  
  
 [  **@restore_mode**  =] '*restore_mode*'  
 セカンダリ データベースの復元モードを指定します。  
  
 0 = NORECOVERY でログを復元します。  
  
 1 = STANDBY でログを復元。  
  
 *復元*は**ビット**NULL にすることはできません。  
  
 [  **@disconnect_users**  =] '*disconnect_users*'  
 1 に設定すると、復元操作の実行時、ユーザーはセカンダリ データベースから切断されます。 既定値 0 を = です。 *切断*users は**ビット**NULL にすることはできません。  
  
 [  **@block_size**  =] '*block_size*'  
 バックアップ デバイスのブロック サイズに使用されるサイズ (バイト単位)。 *block_size*は**int**で既定値は-1。  
  
 [  **@buffer_count**  =] '*buffer_count*'  
 バックアップまたは復元操作で使用されるバッファーの総数。 *buffer_count*は**int**で既定値は-1。  
  
 [ **@max_transfer_size** = ] '*max_transfer_size*'  
 サイズをバイト単位の最大入力または出力要求によって発行されたで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バックアップ デバイスにします。 *max_transfersize*は**int** NULL にすることができます。  
  
 [  **@restore_threshold**  =] '*restore_threshold*'  
 復元操作が始まってから警告が生成されるまでの許容経過時間 (分単位)。 *restore_threshold*は**int** NULL にすることはできません。  
  
 [  **@threshold_alert**  =] '*threshold_alert*'  
 バックアップのしきい値を超過したときに生成する警告を指定します。 *threshold_alert*は**int**の既定値は 14,420 です。  
  
 [  **@threshold_alert_enabled**  =] '*threshold_alert_enabled*'  
 アラートが発生するかどうかを指定と*backup_threshold*を超過します。 値 1 (既定値) では、警告が発生します。 *threshold_alert_enabled*は**ビット**です。  
  
 [  **@history_retention_period**  =] '*ヒストリは削除*'  
 分の履歴を保持する時間の長さです。 *ヒストリは削除*は**int**、既定値は NULL です。 何も指定しない場合は、値 14420 が使用されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **sp_add_log_shipping_secondary_database**から実行する必要があります、**マスター**セカンダリ サーバー上のデータベースです。 このストアド プロシージャでは次の処理が行われます。  
  
1.  **sp_add_log_shipping_secondary_primary** should be called prior to this stored procedure to initialize the primary log shipping database information on the secondary server.  
  
2.  内のセカンダリ データベースのエントリを追加**log_shipping_secondary_databases**指定された引数を使用します。  
  
3.  ローカル監視レコードを追加**log_shipping_monitor_secondary**セカンダリ サーバーを使用して指定された引数。  
  
4.  監視サーバーがセカンダリ サーバーと異なる場合は、追加の監視レコード**log_shipping_monitor_secondary**モニターでサーバーを使用して指定された引数。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールは、この手順を実行できます。  
  
## <a name="examples"></a>使用例  
 この例を使用して、 **sp_add_log_shipping_secondary_database**ストアド プロシージャをデータベースに追加する**LogShipAdventureWorks**ログ配布構成におけるセカンダリ データベースとしてプライマリ データベースと[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]プライマリ サーバー TRIBECA に搭載されています。  
  
```  
EXEC master.dbo.sp_add_log_shipping_secondary_database   
@secondary_database = N'LogShipAdventureWorks'   
,@primary_server = N'TRIBECA'   
,@primary_database = N'AdventureWorks2012'   
,@restore_delay = 0   
,@restore_mode = 1   
,@disconnect_users = 0   
,@restore_threshold = 45     
,@threshold_alert_enabled = 0   
,@history_retention_period = 1440 ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ログ配布 &#40; についてSQL Server &#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
