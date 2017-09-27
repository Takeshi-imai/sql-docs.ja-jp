---
title: "SQL Server 2016 をインストール ウィザードからインストールする (セットアップ) | Microsoft Docs"
ms.custom: 
ms.date: 09/06/2016
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing SQL Server, steps
- Setup [SQL Server], steps
- SQL Server, installing
ms.assetid: 6ad23de1-2bab-4933-9122-c09f5565028d
caps.latest.revision: 91
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 05976158e43d7dfafaf02289462d1537f5beeb36
ms.openlocfilehash: b97afc1f7fd9464e5ef5074e9e2b3d1ccb98d4b0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/08/2017

---
# <a name="install-sql-server-from-the-installation-wizard-setup"></a>SQL Server をインストール ウィザードからインストールする (セットアップ)

 > この記事では、インストール ウィザードを使用して SQL Server をインストールする方法について説明します。 これは [!INCLUDE[SQLServer2016](../../includes/sssql15-md.md)] および [!INCLUDE[SQLServer2017](../../includes/sssqlv14-md.md)] に適用されます。 以前のバージョンの SQL Server に関連するコンテンツについては、「[インストール ウィザードからの SQL Server 2014 のインストール (セットアップ)](http://msdn.microsoft.com/library/ms143219(SQL.120).aspx)」を参照してください。

ここでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ インストール ウィザードを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新しいインスタンスをインストールする手順について詳しく説明します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードでは、1 つの機能ツリーを使用してすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントをインストールできるため、それらを個別にインストールする必要はありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントの個別のインストール方法の詳細については、「[SQL Server をインストールする](../../database-engine/install-windows/install-sql-server.md#how-to-install-individual-components)」を参照してください。  

 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をインストールする他の方法については、次のトピックに記載されています。  

-   [コマンド プロンプトからの SQL Server のインストール](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)  
  
-   [構成ファイルを使用した SQL Server のインストール](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md)  
  
-   [SysPrep を使用して SQL Server をインストールする](../../database-engine/install-windows/install-sql-server-using-sysprep.md)  
  
-   [新しい SQL Server フェールオーバー クラスターの作成 &#40;セットアップ&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)  
  
-   [インストール ウィザードを使用した SQL Server のアップグレード &#40;セットアップ&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md) 

## <a name="get-the-installation-media"></a>インストール メディアを入手する

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]
  
## <a name="prerequisites"></a>前提条件  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をインストールする前に、「 [SQL サーバーのインストール計画](../../sql-server/install/planning-a-sql-server-installation.md)」のトピックを参照してください。  
  
> [!NOTE]  
>  ローカル インストールの場合は、セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。  
 
 ###  <a name="bkmk_ga_instalpatch"></a> インストールのパッチ要件 

SQL Server の前提条件としてインストールされる特定のバージョンの Microsoft VC++ 2013 ランタイム バイナリに問題が見つかりました。 VC ランタイム バイナリに対するこの更新プログラムをインストールしないと、特定のシナリオにおいて、SQL Server で安定性の問題が発生する可能性があります。 SQL Server をインストールする前に、「[SQL Server リリース ノート](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch)」にある手順に従って、ご使用のコンピューターに VC ランタイム バイナリのパッチが必要かどうかを確認してください。  
  
## <a name="to-install-includessnoversionincludesssnoversion-mdmd"></a>インストール方法: [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール メディアを挿入します。 ルート フォルダーの Setup.exe をダブルクリックします。 ネットワーク共有からインストールするには、ネットワーク共有上のルート フォルダーに移動し、Setup.exe をダブルクリックします。  
  
1.  インストール ウィザードで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール センターが実行されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新しいインストールを作成するには、左側のナビゲーション領域の **[インストール]** をクリックし、**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [の新規スタンドアロン インストールを実行するか、既存のインストールに機能を追加します]** をクリックします。  

1.  [プロダクト キー] ページで、オプションを選択して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の無償のエディション、または PID キーを持つ製品版のどちらをインストールするかを指定します。 詳細については、「[SQL Server 2017 の各エディションとサポートされている機能](../../sql-server/editions-and-components-of-sql-server-2017.md)」を参照してください。  
  
     続行するには、 **[次へ]**をクリックします。  

1.  [ライセンス条項] ページで使用許諾契約書を確認し、同意する場合は **[ライセンス条項に同意する]** チェック ボックスをオンにして、 **[次へ]**をクリックします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の機能向上に役立てるため、機能の使用状況オプションを有効にしてレポートを [!INCLUDE[msCoName](../../includes/msconame-md.md)]に送信することもできます。  
  
1.  [グローバル ルール] ウィンドウ内で、ルール エラーが存在していない場合は、セットアップ手順は自動的に [製品の更新プログラム] ページに進みます。  
  
1.  [ [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update] ページは、コントロール パネルの [すべてのコントロール パネル項目] で [Windows Update]、[設定の変更] の順にクリックし、[ [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update] のチェック ボックスがオフになっている場合、次に表示されます。 [ [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update] ページでチェック マークを付けると、Windows Update を調べるときに最新の更新プログラムが含まれるようにコンピューターの設定が変更されます。  

1.  [製品の更新プログラム] ページに、使用できる最新の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 製品の更新プログラムが表示されます。 製品の更新プログラムが検出されない場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップではこのページは表示されず、 **[セットアップ ファイルのインストール]** ページに自動的に移動します。  

1.  [セットアップ ファイルのインストール] ページのセットアップには、セットアップ ファイルのダウンロード、抽出、およびインストールの進行状況が表示されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップの更新プログラムが検出され、含まれるように指定されている場合は、その更新プログラムもインストールされます。 更新プログラムが見つからない場合、セットアップが自動的に進行します。 
  
1. **[インストール ルール]** で、SQL Server セットアップはセットアップの実行中に発生する可能性がある潜在的な問題を特定するためのチェックを行います。 エラーが発生した場合は、詳細な情報を得るため、**[状態]** 列をクリックします。 それ以外の場合は、**[次へ]** をクリックします。 

1. **[インストールの種類]** で、新しいインストールの実行、または既存のインストールへの機能の追加のいずれかを選択します。 **[次へ]**をクリックします。 
  
1. [機能の選択] ページで、インストールするコンポーネントを選択します。 たとえば、SQL Server データベース エンジンの新しいインスタンスをインストールするには、**[データベース エンジン サービス]** を選択します。

    機能名を選択すると、 **[機能の説明]** ペインに各コンポーネント グループの説明が表示されます。 チェック ボックスはいくつでもオンにできます。 詳細については、[SQL Server 2016 のエディションとコンポーネント](../../sql-server/editions-and-components-of-sql-server-2016.md)に関するセクションと「[SQL Server 2016 の各エディションとサポートされている機能](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。
  
     選択した機能の必須コンポーネントが、 **[選択した機能に必要なコンポーネント]** ペインに表示されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップでは、この手順の後半で説明するインストール手順の間に、まだインストールされていない必須コンポーネントをインストールします。  
  
     [機能の選択] ページの下部にあるフィールドを使用して、共有コンポーネントのカスタム ディレクトリを指定することもできます。 共有コンポーネントのインストール パスを変更するには、ダイアログ ボックスの下部にあるフィールドのパスを更新するか、 **[参照]** をクリックしてインストール ディレクトリに移動します。 既定のインストール パスは [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]です。  
  
     共有コンポーネントには絶対パスを指定する必要があります。 フォルダーを圧縮または暗号化しないでください。 マップされたドライブはサポートされていません。  
  
     SQL Server は、共有機能の 2 つのディレクトリを使用します。
  
     * 共有機能ディレクトリ  
  
     * 共有機能ディレクトリ (x86)  
  
     前の各オプションには異なるパスを指定する必要があります。  
  
11. すべてのルールに合格した場合は、[機能ルール] ウィンドウは自動的に進行します。  
  
12. [インスタンスの構成] ページで、既定のインスタンスまたは名前付きインスタンスをインストールするかどうかを指定します。 詳細については、「 [Instance Configuration](../../sql-server/install/instance-configuration.md#instance-configuration)」を参照してください。  
  
     **[インスタンス ID]** : 既定では、インスタンス名がインスタンス ID として使用されます。 これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスのインストール ディレクトリとレジストリ キーを識別するために使用されます。 これは、既定のインスタンスの場合も名前付きインスタンスの場合も同様です。 既定のインスタンスの場合、インスタンス名とインスタンス ID は、MSSQLSERVER になります。 既定以外のインスタンス ID を使用するには、 **[インスタンス ID]** ボックスで異なる値を指定します。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]の標準的なスタンドアロン インスタンスでは、既定のインスタンスの場合も名前付きインスタンスの場合も、 **[インスタンス ID]**の値として既定値以外は使用しません。  
  
     すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Pack とアップグレードは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの各コンポーネントに適用されます。  
  
     **[インストール済みのインスタンス]** : セットアップを実行中のコンピューター上にある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがグリッドに表示されます。 既定のインスタンスが既にコンピューターにインストールされている場合、 [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]の名前付きインスタンスをインストールする必要があります。  
  
     インストールの残りの部分のワーク フローは、インストールするように指定した機能に応じて異なります。 選択した機能によっては、表示されないページもあります。  
  
13. [サーバーの構成 - サービス アカウント] ページを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスのログイン アカウントを指定します。 このページで構成する実際のサービスは、インストール時に選択した機能によって異なります。  
  
     すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスに同じログイン アカウントを割り当てることも、各サービス アカウントを個々に構成することもできます。 サービスを自動的に開始するか、手動で開始するか、または無効にするかを指定することもできます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、各サービスに最小の権限を与えるためにはサービス アカウントを個別に構成することをお勧めします。サービス アカウントを個別に構成すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスには、サービスでのタスクの実行に必要な最小権限が付与されます。 詳細については、「 [Windows サービス アカウントと権限の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のこのインスタンスに含まれるすべてのサービス アカウントに同じログオン アカウントを指定する場合は、ページの下部にあるフィールドに資格情報を指定します。  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
     [サーバーの構成 - 照合順序] ページを使用して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]に既定以外の照合順序を指定します。 詳細については、「[照合順序と Unicode のサポート](../../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。  
  
14. [!INCLUDE[ssDE](../../includes/ssde-md.md)] [の構成 - サーバーの構成] ページを使用して、次の項目を指定します。  
  
    -   [セキュリティ モード]: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス用に Windows 認証または混合モード認証を選択します。 混合モード認証を選択した場合は、組み込みの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者アカウントの強力なパスワードを入力する必要があります。  
  
         デバイスが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]との接続を正常に確立した後のセキュリティ メカニズムは Windows 認証モード、混合モードのどちらの場合も同じです。 詳細については、「 [データベース エンジンの構成 - サーバー構成](../../sql-server/install/instance-configuration.md#database-engine-configuration---server-configuration)」を参照してください。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [管理者] - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの 1 人以上のシステム管理者を指定する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを実行しているアカウントを追加するには、 **[現在のユーザーの追加]**をクリックします。 システム管理者の一覧に対してアカウントを追加または削除するには、 **[追加]** または **[削除]**をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスについて管理者特権を持っているユーザー、グループ、またはコンピューターの一覧を編集します。  
  
     [!INCLUDE[ssDE](../../includes/ssde-md.md)] [の構成 - データ ディレクトリ] ページを使用して、既定以外のインストール ディレクトリを指定します。 既定のディレクトリにインストールする場合は、 **[次へ]**をクリックします。  
  
    > [!IMPORTANT]  
    >  既定以外のインストール ディレクトリを指定する場合は、インストール フォルダーがこの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに対して一意であることを確認します。 このダイアログ ボックスのディレクトリは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の他のインスタンスのディレクトリと共有できません。  
  
     詳細については、「 [データベース エンジンの構成 - データ ディレクトリ](../../sql-server/install/instance-configuration.md#database-engine-configuration---data-directories)」を参照してください。  
  
     [!INCLUDE[ssDE](../../includes/ssde-md.md)] [の構成 - FILESTREAM] ページを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに対する FILESTREAM を有効にします。 詳細については、「 [データベース エンジンの構成 - Filestream](../../sql-server/install/instance-configuration.md#database-engine-configuration---filestream)」を参照してください。  
  
     [!INCLUDE[ssDE](../../includes/ssde-md.md)] [の構成 - TempDB] ページを使用して、ファイル サイズ、ファイルの数、既定以外のインストール ディレクトリ、および TempDB のファイル拡張設定を構成します。 詳細については、「 [データベース エンジンの構成- TempDB](../../sql-server/install/instance-configuration.md#database-engine-configuration---tempdb)」を参照してください。  
  
15. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [の構成 - アカウントの準備] ページを使用して、サーバー モードと [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の管理者権限を持つユーザーまたはアカウントを指定します。 サーバー モードによって、サーバーで使用されるメモリとストレージ サブシステムが決まります。 サーバー モードによって、実行されるソリューションの種類も異なります。 サーバーで多次元キューブ データベースを実行する場合は、既定の [多次元データおよびデータ マイニング] サーバー モード オプションを選択します。 管理者権限に関しては、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のシステム管理者を少なくとも 1 人指定する必要があります。 SQL Server セットアップを実行しているアカウントを追加するには、 **[現在のユーザーの追加]**をクリックします。 システム管理者の一覧に対してアカウントを追加または削除するには、 **[追加]** または **[削除]**をクリックし、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の管理者権限を持つユーザー、グループ、またはコンピューターの一覧を編集します。 サーバー モードと管理者権限の詳細については、「 [Analysis Services の構成 - アカウントの準備](../../sql-server/install/instance-configuration.md#analysis-services-configuration---account-provisioning)」を参照してください。  

   一覧の編集が完了したら、 **[OK]**をクリックします。 構成ダイアログ ボックスの管理者の一覧を確認します。 一覧が完成したら、 **[次へ]**をクリックします。
   
   [ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の構成 - データ ディレクトリ] ページを使用して、既定以外のインストール ディレクトリを指定します。 既定のディレクトリにインストールする場合は、 **[次へ]**をクリックします。  
   
   >[!IMPORTANT]  
   >[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をインストールするときに、INSTANCEDIR と SQLUSERDBDIR と同じディレクトリ パスを指定した場合、SQL Server エージェントとフルテキスト検索は、アクセス許可がないために開始されません。  
   >  
   >既定以外のインストール ディレクトリを指定する場合は、インストール フォルダーがこの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに対して一意であることを確認します。 このダイアログ ボックスのディレクトリは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の他のインスタンスのディレクトリと共有できません。  
   
   詳細については、「 [Analysis Service の構成 - データ ディレクトリ](../../sql-server/install/instance-configuration.md#analysis-services-configuration---data-directories)」を参照してください。  
   
17. [分散再生コントローラーの構成] ページを使用して、分散再生コントローラー サービスに対する管理権限を付与するユーザーを指定します。 管理権限を持つユーザーには、分散再生コントローラー サービスへの無制限のアクセス許可が与えられます。  
  
     分散再生コントローラー サービスに対するアクセス許可を付与するユーザーを追加するには、 **[現在のユーザーの追加]** をクリックします。 分散再生コントローラー サービスのアクセス許可を追加するには、 **[追加]** をクリックします。 Distributed Replay Controller サービスからアクセス許可を削除するには、 **[削除]** をクリックします。  
  
     続行するには、 **[次へ]**をクリックします。  
  
18. [分散再生クライアントの構成] ページを使用して、分散再生クライアント サービスに対する管理権限を付与するユーザーを指定します。 管理権限を持つユーザーには、分散再生クライアント サービスへの無制限のアクセス許可が与えられます。  
  
     **[コントローラー名]** は、省略可能なパラメーターで、既定値は \<*blank*> です。 分散再生クライアント サービスと通信するクライアント コンピューターであるコントローラーの名前を入力します。 次のことを考慮してください。  
  
    -   コントローラーを既にセットアップしてある場合は、各クライアントを構成するときにコントローラーの名前を入力します。  
  
    -   コントローラーをまだセットアップしていない場合は、コントローラー名を空白にしておくことができます。 ただし、コントローラー名を **クライアント構成** ファイルに手動で入力する必要があります。  
  
     分散再生クライアント サービス用の **[作業ディレクトリ]** を指定します。 既定の作業ディレクトリは、\<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\ です。  
  
     分散再生クライアント サービス用の **[結果ディレクトリ]** を指定します。 既定の結果ディレクトリは、\<*drive letter*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\ です。  
  
     続行するには、 **[次へ]**をクリックします。  
  
19. [インストールの準備完了] ページには、セットアップで指定したインストール オプションのツリー ビューが表示されます。 このページで、セットアップは製品の更新プログラム機能が有効/無効であるか、および最終バージョンの更新プログラムであるかどうかを示します。  
  
     続行するには、 **[インストール]**をクリックします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップは、選択した機能の必須コンポーネントを最初にインストールし、その後で機能をインストールします。  
  
20. インストール中は、セットアップの進行に合わせてインストールの進行状況を監視できるように、[インストールの進行状況] ページに状態が表示されます。  
  
21. インストールが終了すると、[完了] ページにインストールの概要ログ ファイルへのリンクと、その他の重要な注意事項が表示されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール プロセスを完了するには、 **[閉じる]**をクリックします。  
  
22. コンピューターの再起動を求めるメッセージが表示されたら、再起動してください。 セットアップが完了した時点で、インストール ウィザードによるメッセージを確認することが重要です。 詳細については、「 [SQL Server セットアップ ログ ファイルの表示と読み取り](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)」を参照してください。  
  
## <a name="next-steps"></a>次の手順  
 新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストールを構成します。  
  
 システムのセキュリティを向上させるため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、主要なサービスと機能を個別にインストールし、有効化できるようになっています。 詳細については、「 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server のインストールの検証](../../database-engine/install-windows/validate-a-sql-server-installation.md)   
 [失敗した SQL Server 2016 のインストールの修復](../../database-engine/install-windows/repair-a-failed-sql-server-installation.md)   
 [SQL Server セットアップ ログ ファイルの表示と読み取り](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)   
 [インストール ウィザードを使用した SQL Server 2016 へのアップグレード &#40;セットアップ&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)   
 [コマンド プロンプトからの SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)  
  
  
