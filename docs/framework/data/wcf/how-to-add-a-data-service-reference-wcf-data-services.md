---
title: "方法: データ サービス参照を追加する (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fa20e9ed0cefbe587bba90ad25d5460592e3ecf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>方法: データ サービス参照を追加する (WCF Data Services)
使用することができます、**サービス参照の追加**への参照を追加する Visual Studio でのダイアログ[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]です。 参照をデータ サービスに追加すると、Visual Studio で開発したクライアント アプリケーションのデータ サービスに容易にアクセスできます。 この手順を完了すると、データ サービスから取得されたメタデータに基づいてデータ クラスが生成されます。 詳細については、次を参照してください。[データ サービス クライアント ライブラリを生成する](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)です。  
  
### <a name="to-add-a-data-service-reference"></a>データ サービス参照を追加するには  
  
1.  (オプション) データ サービスがソリューションの一部ではなく、実行していない場合は、データ サービスを開始して、データ サービスの URI を記録します。  
  
2.  クライアント プロジェクトを右クリックし、**サービス参照の追加**です。  
  
3.  データ サービスが、現在のソリューションの一部の場合は、クリックして**Discover**です。  
  
     - または -  
  
     **アドレス**ボックスに、データ サービスのベース URL を入力するように`http://localhost:1234/Northwind.svc`、クリックして**移動**です。  
  
4.  **[OK]**をクリックします。  
  
     新しいコード ファイルが追加されます。このコード ファイルには、データ サービス リソースにアクセスし、オブジェクトとしてデータ サービス リソースと対話するデータ クラスが含まれています。  
  
## <a name="see-also"></a>参照  
 [クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
