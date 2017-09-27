---
title: "更新 - リレーショナル データベース ドキュメント | Microsoft Docs"
description: "最近変更されたリレーショナル データベースに関するドキュメントで更新されたコンテンツのスニペットを示します。"
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: relational-databases
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.translationtype: HT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: ee7d66bcd8720234f4aec97d24ce16ed21888a3c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-relational-databases-docs"></a>新規または最近の更新: リレーショナル データベース ドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新日の範囲:* &nbsp; **2017 年 7 月 18 日**&nbsp;から&nbsp;**2017 年 9 月 11 日**
- *対象領域:* &nbsp; **リレーショナル データベース**。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [Excel から SQL Server または Azure SQL Database にデータをインポートする](import-export/import-data-from-excel-to-sql.md)
2. [PolyBase Kerberos の接続性のトラブルシューティング](polybase/polybase-troubleshoot-connectivity.md)
3. [透過的なデータ暗号化 (TDE)](security/encryption/transparent-data-encryption.md)
4. [Azure SQL Database と Data Warehouse 用の Transparent Data Encryption](security/encryption/transparent-data-encryption-azure-sql.md)
5. [Azure SQL Database および Data Warehouse 用の Bring Your Own Key サポートによる Transparent Data Encryption](security/encryption/transparent-data-encryption-byok-azure-sql.md)
6. [PowerShell: Azure Key Vault の自分のキーを使用して Transparent Data Encryption を有効にする](security/encryption/transparent-data-encryption-byok-azure-sql-configure.md)
7. [PowerShell を使用して Transparent Data Encryption (TDE) プロテクターをローテーションする](security/encryption/transparent-data-encryption-byok-azure-sql-key-rotation.md)
8. [PowerShell を使用して Transparent Data Encryption (TDE) プロテクターを削除する](security/encryption/transparent-data-encryption-byok-azure-sql-remove-tde-protector.md)
9. [SQL Server 共有管理オブジェクト (SMO) ライセンス条項](server-management-objects-smo/smo-license-terms.md)
10. [sys.external_libraries (Transact-SQL)](system-catalog-views/sys-external-libraries-transact-sql.md)
11. [sys.external_library_files (Transact-SQL)](system-catalog-views/sys-external-library-files-transact-sql.md)
12. [sp_rxPredict](system-stored-procedures/sp-rxpredict-transact-sql.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [自動調整](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-automatic-tuningautomatic-tuningautomatic-tuningmd"></a>1.&nbsp; [自動調整](automatic-tuning/automatic-tuning.md)

*更新日: 2017 年 8 月 16 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 64.  ms.author= "jovanpop".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 be765a1acf9bdfd5485520d16160677583e81f8e 135d926227094374e6ec5484e7babee625b44bb2  (PR=2860  ,  Filename=automatic-tuning.md  ,  Dirpath=docs\relational-databases\automatic-tuning\  ,  MergeCommitSha40=e4a6157cb56c6db911406585f841046a431eef99) -->



**自動プラン選択の修正**


..!NCLUDE-NotShown--ssde_md--../../includes/ssde_md.md)] は、プラン選択の機能低下が検出されると常に、最後の既知の正常なプランに自動的に切り替えることができます。

![SQL plan choice correction--media/force-last-good-plan.png "SQL プラン選択修正")

..!NCLUDE-NotShown--ssde_md--../../includes/ssde_md.md)] は、正しくないプランの代わりに使う必要があるプランなど、プラン選択機能低下の可能性を自動的に検出します。
..!NCLUDE-NotShown--ssde_md--../../includes/ssde_md.md)] は、最後の既知の正常なプランを適用するとき、適用されたプランのパフォーマンスを自動的に監視します。 適用されたプランが機能低下したプランよりよくない場合、新しいプランは適用されなくなり、..!NCLUDE-NotShown--ssde_md--../../includes/ssde_md.md)] は新しいプランをコンパイルします。 適用されたプランが機能低下したプランよりよい場合は、適用されたプランが再コンパイルまで維持されます (たとえば、次の統計またはスキーマ変更時)。

**自動プラン選択修正の有効化**


データベースごとに自動調整を有効にし、プラン変更の機能低下が検出されたときは最後の正常なプランを適用することを指定できます。 自動調整は、次のコマンドを使って有効にします。

```
ALTER DATABASE current
SET AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = ON );
```
このオプションを有効にすると、..!NCLUDE-NotShown--ssde_md--../../includes/ssde_md.md)] は、予想される CPU ゲインが 10 秒より大きいか、新しいプランのエラー数が推奨プランのエラー数より多い場合は、推奨を自動的に適用し、適用されたプランが現在のプランよりよいことを検証します。

**代替 - 手動プラン選択修正**


自動調整しないときは、ユーザーが定期的にシステムを監視し、機能低下したクエリを検索する必要があります。 プランの機能が低下した場合、ユーザーが見つける必要があります。







## <a name="similar-articles"></a>類似した記事

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新規 + 更新 (3 + 12): **SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (5 + 0): **SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (5 + 1): **SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (19 + 82): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (1 + 8): **SQL 用の Linux** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (12 + 1): **SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (0 + 1): **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (7 + 1): **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (1 + 1): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (0 + 2): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (1 + 4): **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (4 + 1): **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)
- [新規 + 更新 (0 + 1): **SQL 用のツール**に関するドキュメント](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)


