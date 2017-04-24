---
title: "方法 : カスタム セキュリティ トークン認証システムを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF, 認証"
ms.assetid: 10e245f7-d31e-42e7-82a2-d5780325d372
caps.latest.revision: 12
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 12
---
# 方法 : カスタム セキュリティ トークン認証システムを作成する
ここでは、カスタム セキュリティ トークン認証システムの作成方法と、これをカスタム セキュリティ トークン マネージャーに統合する方法を示します。セキュリティ トークン認証システムは受信メッセージと共に提出されるセキュリティ トークンの内容を検証します。検証に成功すると、認証システムは <xref:System.IdentityModel.Policy.IAuthorizationPolicy> インスタンスのコレクションを返します。これが評価されるとクレーム セットが返されます。  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] でカスタム セキュリティ トークン認証システムを使用するには、カスタム資格情報とセキュリティ トークンマネージャーの実装をあらかじめ作成しておく必要があります。カスタム資格情報とセキュリティ トークン マネージャーの作成の詳細については、「[チュートリアル: カスタム クライアントおよびサービスの資格情報を作成する](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)」を参照してください。資格情報、セキュリティ トークン マネージャー、およびプロバイダー クラスと認証システム クラスの詳細については、「[Security Architecture](http://msdn.microsoft.com/ja-jp/16593476-d36a-408d-808c-ae6fd483e28f)」を参照してください。  
  
## 手順  
  
#### カスタム セキュリティ トークン認証システムを作成するには  
  
1.  <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> クラスから派生する新しいクラスを定義します。  
  
2.  <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateTokenCore%2A> メソッドをオーバーライドします。カスタム認証システムが受信トークンの種類を検証できるかどうかによって、メソッドから `true` または `false` が返されます。  
  
3.  <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> メソッドをオーバーライドします。このメソッドでは、トークンの内容を適切に検証する必要があります。トークンが検証手順をパスすると、<xref:System.IdentityModel.Policy.IAuthorizationPolicy> インスタンスのコレクションが返されます。下記の例では、次の手順で作成するカスタム承認ポリシーの実装を使用します。  
  
     [!code-csharp[C_CustomTokenAuthenticator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#1)]
     [!code-vb[C_CustomTokenAuthenticator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#1)]  
  
 上記のコードでは、<xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateToken%28System.IdentityModel.Tokens.SecurityToken%29> メソッドに承認ポリシーのコレクションが返されます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、このインターフェイスのパブリックな実装は用意されていません。以下の手順では、これを独自の要件について実行する方法を示します。  
  
#### カスタム承認ポリシーを作成するには  
  
1.  <xref:System.IdentityModel.Policy.IAuthorizationPolicy> インターフェイスを実装する新しいクラスを定義します。  
  
2.  <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> の読み取り専用プロパティを実装します。このプロパティを実装する方法の 1 つは、クラスのコンストラクターでグローバル一意識別子 \(GUID\) を生成し、この値をプロパティの値が求められるたびに返すことです。  
  
3.  <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> の読み取り専用プロパティを実装します。このプロパティは、トークンから取得されるクレーム セットの発行者を返す必要があります。この発行者は、トークンの発行者、またはトークンの内容を検証する証明機関に対応している必要があります。次の例では、前の手順で作成したカスタム セキュリティ トークン認証システムから、このクラスに渡された発行者クレームを使用します。カスタム セキュリティ トークン認証システムでは、\(<xref:System.IdentityModel.Claims.ClaimSet.System%2A> プロパティから返される\) システム提供のクレーム セットを使用して、ユーザー名トークンの発行者を表します。  
  
4.  <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> メソッドを実装します。このメソッドは \(引数として渡される\) <xref:System.IdentityModel.Policy.EvaluationContext> クラスのインスタンスに、受信セキュリティ トークンの内容に基づいたクレームを設定します。評価が完了したら、メソッドは `true` を返します。実装が、評価コンテキストに追加情報を提供する他の承認ポリシーの存在に依存している場合、必要な情報が評価コンテキスト内に存在していないと、このメソッドは `false` を返します。この場合、承認ポリシーによって評価コンテキストが 1 つでも変更されていると、この受信メッセージのために生成された他のすべての承認ポリシー評価の終了後に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、このメソッドを再び呼び出します。  
  
     [!code-csharp[c_CustomTokenAuthenticator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#2)]
     [!code-vb[c_CustomTokenAuthenticator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#2)]  
  
 カスタム資格情報とカスタム セキュリティ トークン マネージャーの作成方法については、「[チュートリアル: カスタム クライアントおよびサービスの資格情報を作成する](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)」を参照してください。ここで作成したカスタム セキュリティ トークン認証システムを使用するには、<xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> メソッドからカスタム認証システムを返すようにセキュリティ トークン マネージャーの実装を変更します。適切なセキュリティ トークン要件が渡されると、このメソッドは認証システムを返します。  
  
#### カスタム セキュリティ トークン マネージャーにカスタム セキュリティ トークン認証システムを統合するには  
  
1.  カスタム セキュリティ トークン マネージャーの実装の <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> メソッドをオーバーライドします。  
  
2.  <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> パラメーターに基づいてカスタム セキュリティ トークン認証システムを返すロジックをメソッドに追加します。次の例では、トークン要件のトークンの種類が \(<xref:System.IdentityModel.Tokens.SecurityTokenTypes.UserName%2A> プロパティで表される\) ユーザー名で、セキュリティ トークン認証システムで要求されているメッセージの方向 \(<xref:System.ServiceModel.Description.MessageDirection> フィールドで表される\) が入力である場合、カスタム セキュリティ トークン認証システムが返されます。  
  
     [!code-csharp[c_CustomTokenAuthenticator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#3)]
     [!code-vb[c_CustomTokenAuthenticator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#3)]  
  
## 参照  
 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>   
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>   
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>   
 <xref:System.IdentityModel.Tokens.UserNameSecurityToken>   
 [チュートリアル: カスタム クライアントおよびサービスの資格情報を作成する](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)   
 [方法 : カスタム セキュリティ トークン プロバイダーを作成する](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)   
 [Security Architecture](http://msdn.microsoft.com/ja-jp/16593476-d36a-408d-808c-ae6fd483e28f)