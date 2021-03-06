---
title: "高度なエラー処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7771b9a4d5a6c0fb4349894afd348e9dece27fd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-error-handling"></a>高度なエラー処理
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ルーティング サービスを示します。 ルーティング サービスは、コンテンツ ベースのルーターをアプリケーションに簡単に追加できるようにする [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] コンポーネントです。 このサンプルでは、トランザクションやその他のより複雑なメッセージ概念 (マルチキャストなど) を使用して、ルーティング サービスをエラーから自動的に回復する方法を示します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a>サンプルの詳細  
 このサンプルのルーティング サービスは、MSMQ キューからメッセージを読み取り、そのメッセージを 2 つのキュー リストにマルチキャストするように構成されています。 サービス キューに使用されるリストとログ キューに使用されるリストです。  
  
 既定では、ルーティング サービスで使用するように構成された MSMQ バインディングによってトランザクションの使用がサポートされるため、メッセージはトランザクション メッセージとなり、それぞれのリストの少なくとも 1 つのキューで受信されないと、ルーティング サービスから受信キュー (`InQ`) に、メッセージが正常にルーティングされたとは報告されません。 しがたって、両方のサービス キューまたは両方のログ キューが使用できない場合は、メッセージをルーティングできなかったこと、および受信キューで何らかの処理が必要であることが報告されます。 この処理には、メッセージをシステム配信不能キューに移動することが含まれます。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  > [!IMPORTANT]
    >  このサンプルを実行する前に、MSMQ をインストールしてください。 MSMQ がインストールされていないと、サンプルの実行中に例外メッセージが返されます。 MSMQ をインストールする手順についてはあります[をインストールするメッセージ キュー (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437)です。  
  
     [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して AdvancedErrorHandling.sln を開きます。  
  
2.  キーを押して**f5 キーを押して**または**CTRL + SHIFT + B**で[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]です。  
  
    1.  Ctrl キーと Shift キーを押しながら B キーを押してアプリケーションをビルドする場合は、./RoutingService/bin/debug/RoutingService.exe にあるアプリケーションを開始する必要があります。  
  
3.  コンソール ウィンドウで、Enter キーを押してクライアントを起動します。  
  
4.  クライアントから、ケースごとに、キューに関するさまざまな統計情報が返されます。  
  
    1.  ケース 1 (エラーなし) の場合は、次の出力が返されます。  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  ケース 3 (プライマリ サービス キューとプライマリ ログ キューのエラー) の場合は、次の出力が返されます。  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  ケース 4 (プライマリ サービス キューとプライマリおよびバックアップ ログ キューのエラー) の場合は、次の出力が返されます。  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  ケース 2 (プライマリ サービス キューのエラー) の場合は、次の出力が返されます。  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a>コードまたは App.config で構成可能  
 サンプルは、提供された時点では、App.config ファイルを使用してルーターの動作を定義するように構成されています。 RoutingService\App.config ファイルの名前を別の名前に変更して認識されないようにし、RoutingService\Program.cs の `configDriven` フィールドの値を `false` に変更して、コードで定義された構成を使用することもできます。 どちらの方法でも、ルーターの動作は同じになります。  
  
### <a name="scenario"></a>シナリオ  
 このサンプルは、ルーティング サービスで高度なメッセージング機能 (トランザクションや受信コンテキストなど) を処理できること、およびそれらの機能を適切なエラー処理シナリオの一部として利用できることを示しています。  
  
### <a name="real-world-scenario"></a>実際のシナリオ  
 Contoso では、ルーティング サービスを介したトランザクションの受信を利用して、エラー状態のときでも、必要なすべてのサービスで情報を受信できるようにしたいと考えています。 さらに、エラーを自動的に適切に処理し、エラー処理ロジックを利用してもメッセージを配信できない場合にはエラーが報告されるようにしたいと考えています。 そのために、計画的に特定のエンドポイントにフェールオーバーするようにルーティング サービスを構成し、必要に応じてトランザクションや受信コンテキストの作成、完了、ロールバック、中止などを行うことで、エラー状態をルーティング サービスで処理するようにしています。  
  
## <a name="see-also"></a>参照  
 [AppFabric ホスティングと永続性のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)
