---
title: "ASSEMBLYPROPERTY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ASSEMBLYPROPERTY_TSQL
- ASSEMBLYPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- ASSEMBLYPROPERTY statement
- assemblies [CLR integration], properties
ms.assetid: cf03d1b1-724c-48bf-a8df-3fe2586b150a
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a38d9f773e010ab779204d7c92b351d88c0d08f7
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="assemblyproperty-transact-sql"></a>ASSEMBLYPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

アセンブリのプロパティに関する情報を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
ASSEMBLYPROPERTY('assembly_name', 'property_name')  
```  
  
## <a name="arguments"></a>引数  
*assembly_name*  
アセンブリの名前を指定します。
  
*property_name*  
情報を取得するプロパティの名前を指定します。 *property_name*値は次のいずれかになります。
  
|[値]|Description|  
|---|---|
|**CultureInfo**|アセンブリのロケール。|  
|**PublicKey**|アセンブリの公開キーまたは公開キー トークン。|  
|**MvID**|コンパイラによって生成された、アセンブリの完全なバージョン識別番号。|  
|**VersionMajor**|4 部構成のアセンブリ バージョン識別番号のメジャー部分 (最初の部分)。|  
|**VersionMinor**|4 部構成のアセンブリ バージョン識別番号のマイナー部分 (2 番目の部分)。|  
|**VersionBuild**|4 部構成のアセンブリ バージョン識別番号のビルド部分 (3 番目の部分)。|  
|**VersionRevision**|4 部構成のアセンブリ バージョン識別番号のリビジョン部分 (4 番目の部分)。|  
|**SimpleName**|アセンブリの単純な名前。|  
|**アーキテクチャ**|アセンブリのプロセッサ アーキテクチャ。|  
|**CLRName**|アセンブリの簡単な名前、バージョン番号、カルチャ、公開キー、およびアーキテクチャをエンコードする正規文字列。 この値は、共通言語ランタイム (CLR) 側でアセンブリを一意に識別する値です。|  
  
## <a name="return-type"></a>戻り値の型
**sql_variant**
  
## <a name="examples"></a>使用例  
次の例で、`HelloWorld`にアセンブリを登録、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。 詳細については、次を参照してください。 [Hello World サンプル](http://msdn.microsoft.com/library/fed6c358-f5ee-4d4c-9ad6-089778383ba7)です。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT ASSEMBLYPROPERTY ('HelloWorld' , 'PublicKey');  
```  
  
## <a name="see-also"></a>参照
[アセンブリ &#40; です。Transact SQL と &#41; です。](../../t-sql/statements/create-assembly-transact-sql.md)  
[アセンブリと &#40; を削除します。Transact SQL と &#41; です。](../../t-sql/statements/drop-assembly-transact-sql.md)
  
  
