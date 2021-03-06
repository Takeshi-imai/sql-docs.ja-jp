---
title: "srv_paraminfo (拡張ストアド プロシージャ API) | Microsoft Docs"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- srv_paraminfo
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paraminfo
ms.assetid: ee2afd4e-0d91-462b-9403-98d481546330
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 16ca2d41922461768b8edba1e12724e4bc852b15
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="srvparaminfo-extended-stored-procedure-api"></a>srv_paraminfo (拡張ストアド プロシージャ API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] CLR 統合を使用してください。  
  
 パラメーターに関する情報を返します。 この関数は、[srv_paramtype](../../relational-databases/extended-stored-procedures-reference/srv-paramtype-extended-stored-procedure-api.md)、[srv_paramlen](../../relational-databases/extended-stored-procedures-reference/srv-paramlen-extended-stored-procedure-api.md)、[srv_parammaxlen](../../relational-databases/extended-stored-procedures-reference/srv-parammaxlen-extended-stored-procedure-api.md)、および [srv_paramdata](../../relational-databases/extended-stored-procedures-reference/srv-paramdata-extended-stored-procedure-api.md) に代わる関数です。 **srv_paraminfo** では、「[データ型 (拡張ストアド プロシージャ API)](../../relational-databases/extended-stored-procedures-reference/data-types-extended-stored-procedure-api.md)」に記載されているデータ型、および長さがゼロのデータをサポートします。  
  
## <a name="syntax"></a>構文  
  
```  
  
int srv_paraminfo (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbType  
,  
ULONG *  
pcbMaxLen  
,  
ULONG *  
pcbActualLen  
,  
BYTE *  
pbData  
,  
BOOL *  
pfNull  
);  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 クライアント接続のためのハンドルです。  
  
 *n*  
 設定するパラメーターの序数です。 最初のパラメーターは 1 です。  
  
 *pbType*  
 パラメーターのデータ型です。  
  
 *pcbMaxLen*  
 パラメーターの最大長へのポインターです。  
  
 *pcbActualLen*  
 パラメーターの実際の長さへのポインターです。 **pfNull* が FALSE に設定されている場合、値 0 (\**pcbActualLen* == 0) はデータの長さがゼロであることを示します。  
  
 *pbData*  
 パラメーター データのバッファーへのポインターです。 *pbData* が NULL でない場合、拡張ストアド プロシージャ API により \**pbData* に \**pcbActualLen* バイトのデータが書き込まれます。 *pbData* が NULL の場合、\**pbData* にデータは書き込まれませんが、関数により \**pbType*、\**pcbMaxLen*、\**pcbActualLen*、**pfNull* が返されます。 このバッファーのメモリは、アプリケーションで管理する必要があります。  
  
 *pfNull*  
 NULL フラグへのポインターです。このパラメーターの値が NULL である場合、 **pfNull* は TRUE に設定されます。  
  
## <a name="returns"></a>返します。  
 パラメーター情報が正常に取得された場合は SUCCEED を返し、それ以外の場合は FAIL を返します。 FAIL が返されるのは、現在のリモート ストアド プロシージャがない場合と、*n* 番目のリモート ストアド プロシージャ パラメーターがない場合です。  
  
## <a name="remarks"></a>解説  
 **セキュリティに関する注意** 拡張ストアド プロシージャのソース コードを十分に確認し、コンパイルした DLL をテストしたうえで実稼働サーバーにインストールしてください。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)をご覧ください。  
  
## <a name="see-also"></a>参照  
 [拡張ストアド プロシージャのプログラマーズ リファレンス](../../relational-databases/extended-stored-procedures-reference/database-engine-extended-stored-procedures-reference.md)  
  
  
