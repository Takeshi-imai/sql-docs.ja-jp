---
title: "メモリのプロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/23/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- LowMemoryLimit property
- MinimumAllocatedMemory property
- MidMemoryPrice property
- MemoryHeapType property
- memory [Analysis Services]
- DefaultPagesCountToReuse property
- TotalMemoryLimit property
- SessionMemoryLimit property
- VirtualMemoryLimit property
- WaitCountIfHighMemory property
- HighMemoryPrice property
- HeapTypeForObjects property
ms.assetid: 085f5195-7b2c-411a-9813-0ff5c6066d13
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 15e0fc6fa123fd4d9ca71f35804d2f06d0342b5a
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="memory-properties"></a>メモリのプロパティ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、要求をすぐに処理できるように、開始時に少量のメモリを事前に割り当てます。 追加のメモリがクエリに割り当てられ、処理のワークロードが増大します。 
  
  構成設定を指定すると、メモリが解放されるしきい値を制御することができます。 たとえば、 **HardMemoryLimit** 設定では、メモリ不足の条件を自分で指定します (既定では、このしきい値は有効ではありません)。ここでは、新しい要求は追加のリソースが有効になるまで完全に拒否されます。

エディションで使用される Analysis Services インスタンスあたり最大メモリの詳細については、次を参照してください。[エディションと SQL Server のサポートされる機能](../../sql-server/editions-and-components-of-sql-server-2017.md#Cross-BoxScaleLimits)します。
  
 次の設定は、特に明記しない限り、多次元と表形式サーバー モード モードの両方に適用されます。  
 
## <a name="default-memory-configuration"></a>既定のメモリ構成

既定の構成では、インスタンスがアイドル状態の場合でも、起動時に各 Analysis Services インスタンスが少量の RAM (40 ～ 50 MB) を割り当てます。 

構成設定はインスタンスごとであることに注意してください。 同じハードウェアのテーブルと多次元インスタンスなど、Analysis Services の複数のインスタンスを実行している場合、他のインスタンスとは関係なく、各インスタンスで固有のメモリを割り当てます。

次の表では、(リファレンス セクションの詳細情報と共に) 一般的に使用されるメモリの設定について簡単に説明します。 同じサーバー上の他のアプリケーションでメモリを消費している場合、構成する必要がある設定を次に示します。

設定 | Description
--------|------------
LowMemoryLimit | 多次元インスタンスで、最初にサーバーが、使用されるオブジェクトと関係なく割り当てられたメモリを解放し始める下限のしきい値。
VertiPaqMemoryLimit | テーブルインスタンスで、最初にサーバーが、使用されるオブジェクトと関係なく割り当てられたメモリを解放し始める下限のしきい値。
TotalMemoryLimit | 実行中の要求および新しい優先度の高い要求に対してスペースを作るために、Analysis Services が積極的にさらにメモリを解放し始める上限のしきい値。 
HardMemoryLimit | Analysis Services がメモリ不足のために、完全に要求を拒否し始める別のしきい値。 
 
## <a name="property-reference"></a>プロパティ リファレンス

次のプロパティは、それ以外に指定されない限り、テーブルと多次元の両方のモードに適用されます。

 1 ～ 100 の値は、 **[物理メモリの合計]** または **[仮想アドレス領域]**のどちらか少ない方に対する割合を示します。 100 を超える値はメモリ制限を示します (単位: バイト)。
  
 **LowMemoryLimit**  
 64 ビットの符号付き倍精度浮動小数点数のプロパティです。Analysis Services が優先度の低いオブジェクトのメモリ (使用頻度の低いキャッシュなど) を解放し始める最初のしきい値を定義します。 メモリを割り当てると、サーバーはこの制限より下のメモリを解放することはありません。 既定値は 65 です。これは、物理メモリまたは仮想アドレス空間の 65% (どちらか少ない方) を超えたらメモリ不足とすることを示します。  
  
 **TotalMemoryLimit**  
 他の要求用にスペースを作るために、サーバーがメモリの割り当てを解除し始めるしきい値を定義します。 この制限に達すると、インスタンスは、期限切れのセッションを終了したり、使用されていない計算をアンロードしたりすることによって、徐々にキャッシュ内のメモリを解放し始めます。 既定値は、物理メモリまたは仮想アドレス空間の 80% です (どちらか少ない方)。 **TotalMemoryLimit** は常に、 **HardMemoryLimit**より小さくする必要があります。  
  
 **HardMemoryLimit**  
 インスタンスが、メモリ使用量を減らすために、アクティブなユーザー セッションを積極的に終了し始めるメモリのしきい値を指定します。 終了されたすべてのセッションには、メモリ不足によって使用中止となった旨のエラーが送信されます。 既定値 (0) は、 **HardMemoryLimit** が **TotalMemoryLimit** とシステムの物理メモリ合計の間の値に設定されることを意味します。システムの物理メモリがプロセスの仮想アドレス領域を超える場合は、 **HardMemoryLimit**を計算せずに、仮想アドレス空間が使用されます。  
  
 **VirtualMemoryLimit**  
  詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **VertiPaqPagingPolicy**  
  テーブル インスタンスのみの場合、サーバーのメモリが不足したときのページングの動作を指定します。 有効な値は次のとおりです。  
  
  

設定  |Description  
---------|---------
**0**     |  ページングを無効にします。 メモリが足りなくなると、メモリ不足エラーが発生し、処理は失敗します。 ページングを無効にする場合は、サービス アカウントに Windows 特権を付与する必要があります。 手順については、「[サービス アカウントの構成 (Analysis Services)](../../analysis-services/instances/configure-service-accounts-analysis-services.md)」を参照してください。 
**1**     |  (既定値) このプロパティを指定した場合、オペレーティング システムのページング ファイル (pagefile.sys) を使用してディスクへのページングが行われます。   
  
1 に設定された場合、指定された方法を使用してサーバーがディスクへのページングを試行するので、メモリ制約によって処理が失敗する可能性は低くなります。 **VertiPaqPagingPolicy** プロパティを設定しても、メモリ エラーが発生しないことが保証されるわけではありません。 以下の状況では、メモリ不足エラーが発生する可能性があります。  
  
-   すべての辞書のための十分なメモリがない。 処理中に、Analysis Services は各列の辞書をメモリにロックします。それらすべての合計が、 **VertiPaqMemoryLimit**で指定されている値を超えることはできません。  
  
-   処理に対応するための十分な仮想アドレス空間がない。  
  
 繰り返し発生するメモリ不足エラーを解決するには、処理を要するデータの量を減らすようにモデルを設計し直すか、コンピューターに物理メモリを追加します。  
  
 **VertiPaqMemoryLimit**  
 テーブル インスタンスのみの場合、ディスクへのページングを許可していれば、ページングが開始されるメモリ消費レベル (メモリの合計に対する割合) をこのプロパティで指定します。 既定値は 60 です。 メモリ消費量が 60% 未満の場合、ディスクへのページングは実行されません。 このプロパティは、 **VertiPaqPagingPolicyProperty**に依存します (ページングを有効にするには 1 に設定する必要があります)。  
  
 **HighMemoryPrice**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MemoryHeapType**  
  詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。 SQL Server 2016 SP1 とそれ以降の Analysis Services で有効な値は次のとおりです。
  
  設定 | Description
--------|------------
**-1** | (既定値) 自動。 エンジンがどれを使用するかを決定します。
**1** | Analysis Services ヒープ。
**2** | Windows LFH。
**5** | ハイブリッド アロケーター。 このアロケーターを使用の Windows LFH \<= 16 KB の割り当てと AS のヒープ > 16 KB の割り当て。 
**6** | Intel TBB アロケーター。 SQL Server 2016 SP1 (およびそれ以降) の Analysis Services で使用できます。
  
  
 **HeapTypeForObjects**  
  詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。 有効な値は次のとおりです。
  
   設定 | Description
--------|------------
**0** | Windows LFH ヒープ。
**1** | Analysis Services スロット アロケーター。
**3** | 各オブジェクトには独自の Analysis Services ヒープがあります。

 
 **DefaultPagesCountToReuse**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **HandleIA64AlignmentFaults**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MidMemoryPrice**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MinimumAllocatedMemory**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **PreAllocate**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **SessionMemoryLimit**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **WaitCountIfHighMemory**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Analysis Services インスタンスのサーバー モードの決定](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
