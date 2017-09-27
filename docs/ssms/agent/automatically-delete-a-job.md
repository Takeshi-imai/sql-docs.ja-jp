---
title: "ジョブを自動的に削除する | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dropping jobs
- SQL Server Agent jobs, removing
- automatic job removal
- jobs [SQL Server Agent], deleting
- deleting jobs
- removing jobs
ms.assetid: 92dbb6da-5919-4bde-9354-d454e9ea3da0
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: a8f3813b1a04cde1ce2d48d1859292f97519aabf
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="automatically-delete-a-job"></a>Automatically Delete a Job
このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] または SQL Server 管理オブジェクトを使用して、ジョブの成功時、失敗時、または完了時に自動的にそのジョブが削除されるように [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントを構成する方法について説明します。  
  
ジョブ応答により、データベース管理者はジョブの完了日時や実行頻度を確認できます。 以下に、一般的なジョブ応答を示します。  
  
-   電子メール、ポケットベル、または **net send** メッセージによってオペレーターに通知します。  
  
    オペレーターが事後の作業を実行する必要がある場合に、これらのジョブ応答のいずれかを使用します。 たとえば、バックアップ ジョブが正常に終了した場合、オペレーターは、バックアップ テープを取り出して、安全な場所に保管するように通知を受ける必要があります。  
  
-   Windows アプリケーション ログにイベント メッセージを書き込みます。  
  
    この応答は、失敗したジョブに対してのみ使用できます。  
  
-   ジョブを自動的に削除します。  
  
    このジョブを再実行する必要がないことが明らかな場合に、このジョブ応答を使用します。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [Security](#Security)  
  
-   **ジョブ応答を指定する方法:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [SQL Server 管理オブジェクト](#SMO)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Security"></a>Security  
詳細については、「 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  
  
## <a name="SSMS"></a>SQL Server Management Studio の使用  
  
#### <a name="to-automatically-delete-a-job"></a>ジョブを自動的に削除するには  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]**を展開し、 **[ジョブ]**を展開します。次に、編集するジョブを右クリックし、 **[プロパティ]**をクリックします。  
  
3.  **[通知]** ページをクリックします。  
  
4.  **[自動的にジョブを削除]**チェック ボックスをオンにし、次のいずれかを選択します。  
  
    -   ジョブが正常に完了したときにジョブの状態を削除する場合は、 **[ジョブ成功時]** をクリックします。  
  
    -   ジョブが正常に完了しなかったときにジョブを削除する場合は、 **[ジョブ失敗時]** をクリックします。  
  
    -   完了時の状態にかかわらずジョブを削除する場合は、 **[ジョブ完了時]** をクリックします。  
  
## <a name="SMO"></a>SQL Server 管理オブジェクトの使用  
**ジョブを自動的に削除するには**  
  
Visual Basic、Visual C#、PowerShell など、選択したプログラミング言語で **Job** クラスの **DeleteLevel** プロパティを使用します。 詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](http://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。  
  
