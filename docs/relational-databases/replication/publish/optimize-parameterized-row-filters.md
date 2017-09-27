---
title: "パラメーター化された行フィルターの最適化 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- precomputed partitions [SQL Server replication]
- filters [SQL Server replication], parameterized
- merge replication precomputed partitions [SQL Server replication], SQL Server Management Studio
- parameterized filters [SQL Server replication], optimizing
ms.assetid: 49349605-ebd0-4757-95be-c0447f30ba13
caps.latest.revision: 44
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 891399921dc50cc1a5463f9735462c94ce442df4
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="optimize-parameterized-row-filters"></a>パラメーター化された行フィルターの最適化
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、パラメーター化された行フィルターを最適化する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [推奨事項](#Recommendations)  
  
-   **パラメーター化された行フィルターを最適化するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   パラメーター化されたフィルターを使用する場合、パブリケーションを作成する際に **@use_partition_groups** オプションまたは **@keep_partition_changes** オプションを指定して、マージ レプリケーションでのフィルターの処理方法を制御できます。 この 2 つのオプションを使用し、パブリケーション データベースに追加のメタデータを格納することで、アーティクルをフィルター選択し、パブリケーションの同期パフォーマンスを向上できます。 アーティクルを作成する際に **@partition_options** を設定することで、サブスクライバー間でデータを共有する方法を制御できます。 これらの要件の詳細については、「 [パラメーター化された行フィルター](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)」をご覧ください。  
  
     [!INCLUDE[ssEW](../../../includes/ssew-md.md)]SQL Server Compact サブスクライバーを使用して、keep_partition_changes を true に設定し、削除を正しく反映する必要があります。 false に設定すると、サブスクライバーに予想よりも多くの行が含まれる場合があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 次の設定を使用して、パラメーター化された行フィルターを最適化できます。  
  
 **Partition Options**  
 このオプションは、**[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスの **[プロパティ]** ページ、または **[フィルターの追加]** ダイアログ ボックスで設定します。 どちらのダイアログ ボックスも、パブリケーションの新規作成ウィザードおよび **[パブリケーションのプロパティ - \<Publication>]**ダイアログ ボックスからアクセスできます。 **[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスでは、**[フィルターの追加]** ダイアログ ボックスでは使用できない、このオプションに対する追加の値も指定できます。  
  
 **[パーティションの事前計算]**  
 このオプションは、パブリケーションのアーティクルが一連の要件を満たしている場合に、既定で **[True]** に設定されています。 これらの要件の詳細については、「[事前計算済みパーティションによるパラメーター化されたフィルターのパフォーマンス最適化](../../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md)」を参照してください。 このオプションは、**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで変更します。  
  
 **[同期の最適化]**  
 このオプションは、 **[パーティションの事前計算]** が **[False]** に設定されている場合にのみ、 **[True]**に設定されています。 このオプションは、**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで設定します。  
  
 パブリケーションの新規作成ウィザードの使用および **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスへのアクセスの詳細については、「[Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)」 (パブリケーションの作成) および「[View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」 (パブリケーション プロパティの表示および変更) を参照してください。  
  
#### <a name="to-set-partition-options-in-the-add-filter-or-edit-filter-dialog-box"></a>[フィルターの追加] または [フィルターの編集] ダイアログ ボックスでパーティションのオプションを設定するには  
  
1.  パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[行のフィルター選択]** ページで、**[追加]** をクリックし、**[フィルターの追加]** をクリックします。  
  
2.  パラメーター化されたフィルターを作成します。 詳しくは、「 [マージ アーティクルのパラメーター化された行フィルターの定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)」をご覧ください。  
  
3.  複数のサブスクライバー間でのデータの共有方法に一致するオプションを選択します。  
  
    -   **[このテーブルの 1 行を複数のサブスクリプションに移動する]**  
  
    -   **[このテーブルの 1 行を 1 つのサブスクリプションのみに移動する]**  
  
     **[このテーブルの 1 行を 1 つのサブスクリプションのみに移動する]**を選択すると、マージ レプリケーションは、格納および処理するメタデータを減らすことにより、パフォーマンスを最適化できます。 ただし、データのパーティション分割によって、1 つの行が複数のサブスクライバーにレプリケートされないことを確認する必要があります。 詳細については、「 [パラメーター化された行フィルター](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)」トピックの「[パーティションのオプション] の設定」をご覧ください。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスが表示されている場合は、**[OK]** をクリックして保存し、ダイアログ ボックスを閉じます。  
  
#### <a name="to-set-partition-options-in-the-article-properties---article-dialog-box"></a>[アーティクルのプロパティ - \<Article>] ダイアログ ボックスで [パーティションのオプション] を設定するには  
  
1.  パブリケーションの新規作成ウィザードの **[アーティクル]** ページ、または **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスでテーブルを選択し、**[アーティクルのプロパティ]** をクリックします。  
  
2.  **[反転表示されたテーブル アーティクルのプロパティを設定]** または **[すべてのテーブル アーティクルのプロパティを設定]**をクリックします。  
  
3.  **[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスの **[プロパティ]** タブの **[対象オブジェクト]** セクションで、**[パーティションのオプション]** に対して以下のいずれかの値を指定します。  
  
    -   **[重複する]**  
  
    -   **[重複する (パーティション外のデータ変更を禁止)]**  
  
    -   **[重複しない (単一のサブスクリプション)]**  
  
    -   **[重複しない (複数のサブスクリプションで共有)]**  
  
     これらのオプションの詳細、および **[フィルターの追加]** および **[フィルターの編集]** ダイアログ ボックスで使用できるオプションとこれらのオプションを関連付ける方法の詳細については、「 [パラメーター化された行フィルター](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)」の「[パーティションのオプション] の設定」を参照してください。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスが表示されている場合は、**[OK]** をクリックして保存し、ダイアログ ボックスを閉じます。  
  
#### <a name="to-set-precompute-partitions"></a>[パーティションの事前計算] を設定するには  
  
1.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで、**[パーティションの事前計算]** オプションに対する値を選択します。 このプロパティは、以下の場合に読み取り専用になります。  
  
    -   パブリケーションが、事前計算済みパーティションの要件を満たさない場合。  
  
    -   スナップショットが、パブリケーションに対して生成されていない場合。 この場合、 **[スナップショットの作成時に自動的に設定する]**の値が表示されます。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-set-optimize-synchronization"></a>[同期の最適化] を設定するには  
  
1.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで、**[同期の最適化]** オプションに対して **[True]** の値を選択します。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 **@keep_partition_changes** と **@use_partition_groups** のフィルタ オプションの定義については「[sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)」を参照してください。  
  
#### <a name="to-specify-merge-filter-optimizations-when-creating-a-new-publication"></a>新しいパブリケーションを作成するときにマージ フィルターの最適化を指定するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)を実行します。 以下のパラメーターのいずれかに、**@publication** と **true** の値を指定します。  
  
    -   **@use_partition_groups**- アーティクルが事前計算済みパーティションの要件を満たしている場合、パフォーマンスが最も最適化されます。 詳細については、「[事前計算済みパーティションによるパラメーター化されたフィルターのパフォーマンス最適化](../../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md)」を参照してください。  
  
    -   **@keep_partition_changes** - 事前計算済みパーティションを使用できない場合、この最適化を使用します。  
  
2.  パブリケーション用のスナップショット ジョブを追加します。 詳細については、「[Publisher で文書を作成するには](../../../relational-databases/replication/publish/create-a-publication.md)」を参照してください。  
  
3.  パブリッシャー側のパブリケーション データベースに対して、 [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)を実行します。次のパラメーターを指定します。  
  
    -   **@publication** - 手順 1. で指定したパブリケーション名  
  
    -   **@article** - アーティクルの名前  
  
    -   **@source_object** - パブリッシュするデータベース オブジェクト  
  
    -   **@subset_filterclause** - アーティクルを行方向にフィルター選択するために使用する、オプションのパラメーター化されたフィルター句  
  
    -   **@partition_options** - フィルター選択されるアーティクルのパーティション オプション  
  
4.  パブリケーションの各アーティクルに対し、手順 3. を実行します。  
  
5.  (省略可) パブリッシャー側のパブリケーション データベースに対して [sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) を実行し、2 つのアーティクル間に結合フィルターを定義します。 詳しくは、「 [マージ アーティクル間の結合フィルターの定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)」をご覧ください。  
  
#### <a name="to-view-and-modify-merge-filter-behaviors-for-an-existing-publication"></a>既存のパブリケーションに対するマージ フィルターの動作を表示して変更するには  
  
1.  (省略可) パブリッシャー側のパブリケーション データベースに対して [@publication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)を指定して **@publication**を使用して、パラメーター化された行フィルターを最適化する方法について説明します。 結果セットの **keep_partition_changes** および **use_partition_groups** の値を調べます。  
  
2.  (省略可) パブリッシャー側のパブリケーション データベースに対して、 [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)を実行します。 **@property** には **use_partition_groups** を指定し、**@value** には **true** または **false** を指定します。  
  
3.  (省略可) パブリッシャー側のパブリケーション データベースに対して、 [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)を実行します。 **@property** には **keep_partition_changes** を指定し、**@value** には **true** または **false** を指定します。  
  
    > [!NOTE]  
    >  **keep_partition_changes** を有効にする場合、まず **use_partition_groups** を無効にして、**@force_reinit_subscription** に **1** を指定します。  
  
4.  (省略可) パブリッシャー側のパブリケーション データベースに対して、 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)を実行します。 **@property** に **partition_options** を指定し、**@value** に適切な値を指定します。 このフィルター選択オプションの定義については、「 [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) 」を参照してください。  
  
5.  (省略可) 必要に応じてスナップショット エージェントを開始し、スナップショットを再生成してください。 新しいスナップショットの生成が必要な変更の詳細については、「[Change Publication and Article Properties](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)」 (パブリケーションおよびアーティクルのプロパティの変更) を参照してください。  
  
## <a name="see-also"></a>参照  
 [マージ アーティクル間の一連の結合フィルターを自動的に生成する &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/publish/automatically-generate-join-filters-between-merge-articles.md)   
 [マージ アーティクルのパラメーター化された行フィルターの定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [パラメーター化された行フィルター](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)  
  
  