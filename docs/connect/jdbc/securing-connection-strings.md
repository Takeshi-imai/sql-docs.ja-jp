---
title: "接続文字列を保護する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69ce8557-5260-4ea4-81b8-d0c5481f0868
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 588166b41e7a66a442b1b5b49fbdcaf0d6d13320
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="securing-connection-strings"></a>接続文字列のセキュリティ保護
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  セキュリティで保護されたアプリケーションを実現する上で、データ ソースへのアクセスを保護することは、最も重要な目的の 1 つです。 データ ソースへのアクセスを制限するには、ユーザー ID、パスワード、データ ソース名などの接続情報をセキュリティで保護して安全策を講じる必要があります。 ソース コードにおいて、ユーザー ID やパスワードをプレーンテキストで保存するのはセキュリティ上の深刻な問題となります。 ユーザー ID やパスワード情報が含まれているコードをコンパイルしてから外部ソースに提供する場合でも、コンパイル済みのコードを逆アセンブルされる可能性があるため、ユーザー ID とパスワードは特定されてしまいます。 そのため、ユーザー ID やパスワードなどの重要な情報は、絶対にコードに入れないようにする必要があります。  
  
 接続 URL とパスワードをアプリケーションのソース コードに一緒に保存しないことを強くお勧めします。 代わりに、アクセスが制限されている別のファイルにパスワードを保存することをお勧めします。 実行されているアプリケーションのコンテキストに対して、そのファイルへのアクセスを許可することもできます。  
  
 また、暗号化したパスワードをファイルに保存する方法もあります。 暗号化 API は、キーをどこかに保存する必要がなく、ユーザーのパスワードから生成していないものを使用してください。 たとえば、証明書に基づく公開キーと秘密キーのペアを使用すること、または両方の当事者がキーの承諾プロトコルを使用して、秘密キーを送信せずに暗号化のための同じ秘密キーを生成する方法 (Diffie-Hellman アルゴリズム) の使用を検討することができます。  
  
 外部ソースからの接続文字列情報 (ユーザーが入力するユーザー ID やパスワードなど) を受け取る場合は、ソースからの入力をすべて検証して、正しい書式に従っていること、接続に影響を及ぼすパラメータが追加されていないことを確認する必要があります。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバー アプリケーションのセキュリティ保護](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
