---
title: "探索プロキシの実装"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2996eb07c883947210c48471a2c60ba49495566d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-a-discovery-proxy"></a>探索プロキシの実装
ここでは、探索プロキシの実装に必要な手順について説明します。 探索プロキシは、サービスのリポジトリを格納するスタンドアロンのサービスです。 クライアントは探索プロキシに対し、そのプロキシで認識される探索可能なサービスを問い合わせることができます。 プロキシにサービスを登録する方法は、実装手段によって異なります。 たとえば、探索プロキシが既存のサービス リポジトリに接続でき、その情報を探索可能にできる場合、管理者は管理 API を使用して探索可能なサービスをプロキシに追加することができます。または、探索プロキシにアナウンス機能を使用し、内部キャッシュを更新できます。  
  
 WCF 実装は、プロキシを簡単にビルドできる基本クラスを提供します。 これらの API を利用して、既存のリポジトリの上に探索プロキシをビルドできます。  
  
 ここで実装される探索プロキシは、探索可能にしてクライアントからエンドポイントを検索できるという点で、他の WCF サービスと似ています。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [探索プロキシを実装する方法](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 探索プロキシを実装する方法について説明します。  
  
 [探索プロキシで登録される探索可能なサービスの実装方法](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 探索プロキシに登録する、探索可能な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの実装方法について説明します。  
  
 [探索プロキシを使用してサービスを検索するクライアント アプリケーションの実装方法](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 探索プロキシを使用してサービスを検索する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アプリケーションの実装方法について説明します。  
  
 [探索プロキシをテストする方法](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 前の 3 つのトピックに記述されたコードのテスト方法について説明します。  
  
## <a name="see-also"></a>参照  
 [WCF Discovery](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [プログラムを使用して探索可能性に WCF サービスとクライアントを追加する方法](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
