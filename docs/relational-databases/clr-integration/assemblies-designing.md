---
title: "アセンブリのデザイン |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- designing assemblies [SQL Server]
- assemblies [CLR integration], designing
ms.assetid: 9c07f706-6508-41aa-a4d7-56ce354f9061
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d5e491f922a034a55cb65e432e0c005f6cc18fc0
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="assemblies---designing"></a>アセンブリの設計
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
このトピックでは、アセンブリをデザインするときに考慮する必要がある次の項目について説明します。  
  
-   アセンブリのパッケージ化  
  
-   アセンブリのセキュリティを管理します。  
  
-   アセンブリに関する制限事項  
  
## <a name="packaging-assemblies"></a>アセンブリのパッケージ化  
 アセンブリのクラスやメソッドには、複数の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ルーチンまたは型の機能を含めることができます。 ほとんどの場合、関連する機能を実行するルーチンの機能を 1 つのアセンブリ内にパッケージ化することが適切です。これは特に、このようなルーチンで、メソッドが相互に呼び出しを行うクラスが共有される場合に当てはまります。 たとえば、CLR (共通言語ランタイム) トリガーと CLR ストアド プロシージャのデータ エントリ管理タスクを実行するクラスを 1 つのアセンブリにパッケージ化することがあります。 これは、これらのクラスのメソッドは、関連性の低いタスクを実行するクラスのメソッドよりも相互に呼び出しを行う可能性が高いためです。  
  
 コードをアセンブリにパッケージ化しているときは、次のことを考慮する必要があります。  
  
-   CLR ユーザー定義関数に依存する CLR ユーザー定義型とインデックスにより、アセンブリに依存する持続データがデータベースに格納される可能性があります。 多くの場合、アセンブリに依存する持続データがデータベースに存在すると、アセンブリのコードを変更することが複雑になることがあります。 そのため、一般に、持続データの依存関係があるコード (ユーザー定義関数を使用するユーザー定義型やインデックスなど) とそのような持続データの依存関係がないコードは切り離した方が適切です。 詳細については、次を参照してください。[を実装するアセンブリ](../../relational-databases/clr-integration/assemblies-implementing.md)と[ALTER ASSEMBLY &#40;です。TRANSACT-SQL と #41 です](../../t-sql/statements/alter-assembly-transact-sql.md)。  
  
-   マネージ コードの一部分で上位の権限が必要な場合、そのコードは、上位の権限を必要としないコードとは別のアセンブリにパッケージ化することをお勧めします。  
  
## <a name="managing-assembly-security"></a>アセンブリのセキュリティ管理  
 アセンブリでマネージ コードが実行されるときに、.NET コード アクセス セキュリティによって保護されているリソースにアセンブリがアクセスできる程度を制御できます。 この制御は、アセンブリを作成または変更するときに、SAFE、EXTERNAL_ACCESS、または UNSAFE の 3 つの中のいずれかの権限セットを指定して行います。  
  
### <a name="safe"></a>SAFE  
 SAFE は既定の権限セットであり、最も強い制限です。 SAFE 権限を指定したアセンブリによって実行されるコードでは、ファイル、ネットワーク、環境変数、またはレジストリなどの外部システム リソースにアクセスできません。 SAFE コードでは、ローカルの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのデータにアクセスしたり、ローカル データベースの外部にあるリソースへのアクセスを必要としない計算やビジネス ロジックを実行したりすることができます。  
  
 ほとんどのアセンブリでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の外部にあるリソースにアクセスしなくても計算やデータ管理タスクを実行できます。 そのため、アセンブリの権限セットとして SAFE を使用することをお勧めします。  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 EXTERNAL_ACCESS を使用すると、アセンブリでファイル、ネットワーク、Web サービス、環境変数、およびレジストリなどの特定の外部システム リソースにアクセスできます。 EXTERNAL ACCESS 権限を持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインだけが EXTERNAL_ACCESS アセンブリを作成できます。  
  
 SAFE アセンブリおよび EXTERNAL_ACCESS アセンブリには検証可能なタイプ セーフのコードしか格納できません。 つまり、これらのアセンブリでクラスにアクセスするには、型定義で有効な整形式のエントリ ポイントを使用する必要があります。 そのため、これらのアセンブリでは、コードによって所有されていないメモリ バッファーに自由にアクセスすることはできません。 また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスの堅牢性に悪影響を与える可能性がある操作を実行することもできません。  
  
### <a name="unsafe"></a>UNSAFE  
 UNSAFE を使用すると、アセンブリでは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の内外を問わずどちらのリソースにも無制限にアクセスできます。 UNSAFE アセンブリの内部で実行されているコードで、アンマネージ コードを呼び出すことができます。  
  
 また、UNSAFE を指定すると、CLR 検証機能によってタイプ セーフではないと見なされる操作をアセンブリのコードで実行できます。 これらの操作により、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセス空間のメモリ バッファーに制御なしにアクセスされる可能性があります。 UNSAFE アセンブリは、いずれかのセキュリティ システムを覆すも可能性があることができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または共通言語ランタイム。 UNSAFE 権限は、経験豊かな開発者や管理者によって信頼性の高いアセンブリにのみ与えるようにする必要があります。 メンバーにのみ、 **sysadmin**固定サーバー ロールは、UNSAFE アセンブリを作成できます。  
  
## <a name="restrictions-on-assemblies"></a>アセンブリに関する制限事項  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 信頼性の高い、スケーラブルな方法で実行できることを確認するアセンブリ内のマネージ コードを特定の制限を設定します。 つまり、SAFE アセンブリと EXTERNAL_ACCESS アセンブリでは、サーバーの堅牢性を侵害する可能性のある操作を実行できません。  
  
### <a name="disallowed-custom-attributes"></a>禁止されているカスタム属性  
 アセンブリには次のカスタム属性で注釈を付けることができません。  
  
```  
System.ContextStaticAttribute  
System.MTAThreadAttribute  
System.Runtime.CompilerServices.MethodImplAttribute  
System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
System.Runtime.Remoting.Contexts.ContextAttribute  
System.Runtime.Remoting.Contexts.SynchronizationAttribute  
System.Runtime.InteropServices.DllImportAttribute   
System.Security.Permissions.CodeAccessSecurityAttribute  
System.STAThreadAttribute  
System.ThreadStaticAttribute  
```  
  
 また、SAFE アセンブリと EXTERNAL_ACCESS アセンブリには、次のカスタム属性で注釈を付けることができません。  
  
```  
System.Security.SuppressUnmanagedCodeSecurityAttribute  
System.Security.UnverifiableCodeAttribute  
```  
  
### <a name="disallowed-net-framework-apis"></a>禁止されている .NET Framework API  
 どの[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 、許可されていないのいずれかの注釈が付けられる API **HostProtectionAttributes** SAFE と EXTERNAL_ACCESS アセンブリから呼び出すことができません。  
  
```  
eSelfAffectingProcessMgmt  
eSelfAffectingThreading  
eSynchronization  
eSharedState   
eExternalProcessMgmt  
eExternalThreading  
eSecurityInfrastructure  
eMayLeakOnAbort  
eUI  
```  
  
### <a name="supported-net-framework-assemblies"></a>サポートされている .NET Framework アセンブリ  
 カスタム アセンブリで参照されているアセンブリは、CREATE ASSEMBLY を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に読み込む必要があります。 次の [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] アセンブリは既に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に読み込まれているため、CREATE ASSEMBLY を使用しなくてもカスタム アセンブリで参照できます。  
  
```  
custommarshallers.dll  
Microsoft.visualbasic.dll  
Microsoft.visualc.dll  
mscorlib.dll  
system.data.dll  
System.Data.SqlXml.dll  
system.dll  
system.security.dll  
system.web.services.dll  
system.xml.dll  
System.Transactions  
System.Data.OracleClient  
System.Configuration  
```  
  
## <a name="see-also"></a>参照  
 [アセンブリ &#40;データベース エンジン&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)   
 [CLR 統合のセキュリティ](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
