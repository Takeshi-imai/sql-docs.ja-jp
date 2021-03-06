---
title: "ウイルス対策ソフトウェア (Analytics Platform System)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 60ab9a88-d339-4917-a38b-f9481aef38fd
caps.latest.revision: "29"
ms.openlocfilehash: 1733ec6be50d839284fa147eb1cf5c1660b77190
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="antivirus-software"></a>ウイルス対策ソフトウェア
データ センターには、ウイルス対策ソフトウェアが必要とする場合は、次のガイドラインを使用して、Analytics Platform System にウイルス対策ソフトウェアをインストールします。 会社のデータ センターの要件である場合を除き、ウイルス対策ソフトウェアをインストールしないことをお勧めします。  
  
> [!WARNING]  
> コンピューターごとおよび分析プラットフォーム システム全体のセキュリティ上のリスクを個別に評価して、各コンピューターのセキュリティ上のリスク レベルに適しているツールを選択することを強くお勧めします。 さらに、すべてのウイルス対策プロジェクトをロールアウトする前に、システム安定性とパフォーマンスのすべての変更を測定する完全読み込みで全体をテストすることをお勧めします。  
>   
> ウイルス対策ソフトウェアでは、一部のシステム リソースを実行する必要があります。 分析プラットフォーム システム上のパフォーマンスに影響があるかどうかを判断するウイルス対策ソフトウェアをインストールした後と前にテストを実行する必要があります。  
  
このトピックの内容が記載されているガイダンスに基づいて[SQL Server を実行しているコンピューター上で実行するウイルス対策ソフトウェアの選び方](http://support.microsoft.com/kb/309422)と[サポート技術情報の記事 961804](http://support.microsoft.com/kb/961804/en-us)です。  
  
## <a name="exclusion-list-for-physical-hosts"></a>物理ホストの除外リスト  
物理ホスト上のウイルス対策ソフトウェアをインストールするには、ディレクトリとプロセスの次のリストを除外します。 これらは、ウイルス対策ソフトウェアによってスキャンする必要がありますされません。  
  
**これらのディレクトリを除外するには。**  
  
-   C:\ProgramData\Microsoft\Windows\Hyper-V - 仮想マシンの構成ディレクトリ  
  
-   C:\Users\Public\Documents\Hyper-V\Virtual ハード_ディスク - 既定の仮想ハード ディスク ドライブのディレクトリ  
  
-   仮想ハード ディスク ドライブのディレクトリにある C:\clusterStorage  
  
**これらのプロセスを除外するには。**  
  
-   仮想マシンの管理 (Vmms.exe)  
  
-   仮想マシン ワーカー プロセス (Vmwp.exe)  
  
## <a name="exclusion-list-for-virtual-machines-vms"></a>仮想マシン (Vm) の除外リスト  
Vm にウイルス対策ソフトウェアをインストールするには、ディレクトリおよびファイルの次の一覧を除外します。 これらは、ウイルス対策ソフトウェアによってスキャンする必要がありますされません。  
  
***PDW_region*-CTL01**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
***appliance_domain*-AD01**と ***appliance_domain*-AD02**  
  
-   制限はありません。  
  
**コンピューティング ノード Vm**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
***appliance_domain*VMM**  
  
-   制限はありません。  
  
***appliance_domain*-WDS**  
  
-   制限はありません。  
  
***appliance_domain*-ISCSI01**  
  
-   C:\iscsitarget  
  
## <a name="see-also"></a>参照  
[アプライアンスの管理タスクと #40 です。Analytics Platform System &#41;](appliance-management-tasks.md)  
  
