---
title: "Red Hat Enterprise Linux に SQL Server 2017 の概要 |Microsoft ドキュメント"
description: "このクイック スタート チュートリアルでは、Red Hat Enterprise Linux に SQL Server 2017 をインストールし、作成し、sqlcmd によるデータベースのクエリを実行する方法を示します。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 09/07/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.translationtype: MT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 5309c2884fa4bf46a4c9c7224f4c1f21be23e7e6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="install-sql-server-and-create-a-database-on-red-hat"></a>SQL Server をインストールし、Red hat でデータベースを作成

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このクイック スタート チュートリアルの最初をインストールする SQL Server 2017 RC2 Red Hat Enterprise Linux (RHEL) 7.3 にします。 接続し、 **sqlcmd**を最初にデータベースを作成し、クエリを実行します。

> [!TIP]
> このチュートリアルでは、ユーザー入力と、インターネット接続が必要です。 興味のある場合、[無人](sql-server-linux-setup.md#unattended)または[オフライン](sql-server-linux-setup.md#offline)インストール手順を参照してください[Linux 上の SQL Server のインストールのガイダンス](sql-server-linux-setup.md)です。

## <a name="prerequisites"></a>前提条件

RHEL 7.3 コンピューターにする必要があります**3.25 GB 以上**メモリです。

自分のコンピューター上の Red Hat Enterprise Linux をインストールするに移動[http://access.redhat.com/products/red-hat-enterprise-linux/evaluation](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)です。 Azure で RHEL 仮想マシンを作成することもできます。 参照してください[作成と Azure CLI を使用して Linux Vm の管理](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)、および使用`--image RHEL`への呼び出しで`az vm create`です。

その他のシステム要件については、次を参照してください。 [Linux に SQL Server のシステム要件](sql-server-linux-setup.md#system)です。

## <a id="install"></a>SQL Server をインストールします。

RHEL で SQL Server を構成するをインストールするターミナルで次のコマンドを実行、 **mssql サーバー**パッケージ。

1. Microsoft SQL Server の Red Hat リポジトリの構成ファイルをダウンロードするには。

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server.repo
   ```

1. SQL Server をインストールするには、次のコマンドを実行します。

   ```bash
   sudo yum update
   sudo yum install -y mssql-server
   ```

1. パッケージのインストールが完了すると、実行後に**mssql conf セットアップ**SA パスワードを設定しのエディションを選択する指示に従います。

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```
   > [!TIP]
   > (最小長さが 8 文字で、大文字と小文字のアルファベット、基本 10 桁の数字や英数字以外の記号) は、SA アカウントの強力なパスワードを指定することを確認してください。

   > [!TIP]
   > RC2 をインストールするときに、各エディションのいずれかを購入したライセンスは必要ありません。 リリース候補になっているために、選択したエディションに関係なく、次のメッセージが表示されます。
   >
   > `This is an evaluation version.  There are [175] days left in the evaluation period.`
   >
   > このメッセージは、選択したエディションには反映されません。 RC2 のプレビューの期間に関連します。

1. 構成を完了すると、サービスが実行されていることを確認します。

   ```bash
   systemctl status mssql-server
   ```
   
1. リモート接続を許可するのには、RHEL 上のファイアウォールで SQL Server のポートを開きます。 SQL Server の既定ポートは、TCP 1433 です。 使用している場合**FirewallD**ファイアウォールの次のコマンドを使用することができます。

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

この時点では、SQL Server では、RHEL コンピューター上で実行しを使用する準備ができました!

## <a id="tools"></a>SQL Server コマンド ライン ツールをインストールします。

データベースを作成するには、SQL Server で TRANSACT-SQL ステートメントを実行できるツールを使用して接続する必要があります。 次の手順は、SQL Server コマンド ライン ツールをインストール: [sqlcmd](../tools/sqlcmd-utility.md)と[bcp](../tools/bcp-utility.md)です。

1. Microsoft Red Hat リポジトリの構成ファイルをダウンロードします。

   ```bash
   sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```

1. 以前のバージョンがあれば**mssql ツール**インストールされている、古い unixODBC パッケージを削除します。

   ```bash
   sudo yum update
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. インストールする次のコマンド実行**mssql ツール**unixODBC 開発者パッケージにします。

   ```bash
   sudo yum update
   sudo yum install -y mssql-tools unixODBC-devel
   ```

1. 便宜上、次のように追加します。`/opt/mssql-tools/bin/`を、**パス**環境変数。 これにより、完全なパスを指定せず、ツールを実行することができます。 変更するのには、次のコマンドを実行、**パス**ログイン セッションと対話型/以外のログイン セッションの両方の。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

> [!TIP]
> **Sqlcmd**クエリの実行し、管理と開発タスクを実行する SQL Server に接続するためのツールの 1 つだけです。 その他のツールが含まれます[SQL Server Management Studio](sql-server-linux-develop-use-ssms.md)と[Visual Studio Code](sql-server-linux-develop-use-vscode.md)です。

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
