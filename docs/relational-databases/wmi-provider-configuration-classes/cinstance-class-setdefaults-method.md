---
title: "SetDefaults メソッド (CInstance クラス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- SetDefaults Method (CInstance Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDefaults method
ms.assetid: ed9e99c2-3e28-4ee8-bc20-61ca05984973
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ea75930319239ca7e14a1f840b4cfad3b04226b3
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="cinstance-class---setdefaults-method"></a>CInstance クラス - SetDefaults メソッド
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
インスタンスのすべての既定値を設定、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既存のデータを上書きするオプションを使用するクライアント。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 [クライアント インスタンスを表す](../../relational-databases/wmi-provider-configuration-classes/cinstance-class.md) CInstance クラス [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|Description|  
|---------------|-----------------|  
|*OverwriteAll*|インスタンス上の既存の値を上書きするかどうかを指定するブール値、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント: **true**既存のデータを上書きするか、 **false**既存のデータを上書きしない場合。|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [クライアント プロトコルの構成](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
