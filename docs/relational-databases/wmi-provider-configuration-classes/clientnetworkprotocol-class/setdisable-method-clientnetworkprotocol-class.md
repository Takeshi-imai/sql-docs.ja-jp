---
title: "SetDisable メソッド (ClientNetworkProtocol クラス) |Microsoft ドキュメント"
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
- SetDisable Method (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDisable method
ms.assetid: bce69ab9-ea5b-43fd-8114-08b1b5890755
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 992ffc91ef9782057764461b05fa0a977e8c6ad0
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="setdisable-method-clientnetworkprotocol-class"></a>SetDisable メソッド (ClientNetworkProtocol クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
指定されているクライアント ネットワーク プロトコルを無効になります、 [Configure Client Protocols](http://technet.microsoft.com/library/ms181035.aspx)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetDisable()  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 A [ClientNetworkProtocol クラス](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md)によって使用されるネットワーク プロトコルを表すオブジェクト、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]クライアント。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [クライアント ネットワーク プロトコルとネットワーク ライブラリの構成](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
