---
title: "IPv6 の自動構成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
caps.latest.revision: 5
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 5
---
# IPv6 の自動構成
IPv6 の 1 種類の重要な目的は、ノードのプラグ アンド プレイをサポートするためです。  つまり、ノードを IPv6 のネットワークに差し込み、自動的にその影響介在なしでコンフィギュレーションすることは可能なはずです。  
  
## 自動型の設定  
 IPv6 の設定が自動次の型をサポートしています:  
  
-   **Stateful auto\-configuration**。  この種の設定はノードのインストールや管理、IPv6 \(DHCPv6\) サーバーの構成プロトコルをホストで必要なそのための介在の特定のレベルが必要です。  DHCPv6 サーバーは、コンフィギュレーション情報が提供されるノード リストを維持します。  また、ステータス情報を管理します。各アドレスを使用した頻度である場合や、再割当に使用可能な場合があります\) サーバーはわかっています。  
  
-   **Stateless auto\-configuration**。  この種の設定が小規模な組織と個人に適しています。  この場合、各ホストは入庫済ルーター広告の内容の住所が決まります。  住所のネットワーク ID の一部を定義する IEEE EUI\-64 の標準を使用してリンク ホストの住所の独自性とすることができますです。  
  
 住所の決定方法に関係なく、ノードであるか、潜在的な住所が保管場所のリンクに固有であることを確認する必要があります。  これは、潜在的な住所に横願いメッセージの送信に使用されます。  ノードが応答を受信すると、アドレスが既に使用中で、別の住所を決定することに気づきます。  
  
## IPv6 の移動性  
 モバイル デバイスに拡散は、新しい条件をもたらしました: デバイスは、必要に応じて IPv6 のインターネット場所を変更または既存の接続を維持必要があります。  この機能を提供するには、携帯電話ノードは常に到達できる自宅住所が割り当てられます。  携帯電話ノードは家庭の場合は、自宅のリンクに接続し、自宅住所を使用します。  携帯電話ノードが自宅、通常の通信の携帯電話ルーター、入念ノード間の通信文およびノードである自宅のエージェントといういるとき。  
  
## 参照  
 [インターネット プロトコル バージョン 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)   
 [ソケット](../../../docs/framework/network-programming/sockets.md)