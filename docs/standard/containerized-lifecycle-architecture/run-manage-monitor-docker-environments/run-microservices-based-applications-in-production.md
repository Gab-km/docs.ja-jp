---
title: "実稼働環境で構成される microservices ベースのアプリケーションを実行します。"
description: "Microsoft プラットフォームとツールが、Docker のコンテナー化アプリケーションのライフ サイクル"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: e7a2788098aa731699cbb201c7177e7578907673
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>実稼働環境で構成される microservices ベースのアプリケーションを実行します。

複数 microservices で構成されたアプリケーションは展開の複雑性を容易にし、IT の観点から実行可能なためするために orchestrator クラスターをデプロイする必要があります。 Orchestrator クラスターでは、それができなければを展開およびスケール アウト microservices の複雑なアプリケーションは非常に困難。

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>クラスターの orchestrators、スケジューラ、およびコンテナーの概要

この電子書籍の前半紹介*クラスター*と*スケジューラ*ソフトウェア アーキテクチャと開発のディスカッションの一部として。 Docker のクラスターには、Docker Swarm と続き Datacenter オペレーティング システム (DC/OS) があります。 Microsoft Azure のコンテナー サービスによって提供されるインフラストラクチャの一部としてこれらの両方を実行できます。

アプリケーションはスケール アウトされた複数のホスト システムで、ときに各ホスト システムを管理し、基になるプラットフォームの複雑さを抽象化する機能は魅力的なになります。 Orchestrators およびスケジューラが提供するものは正確です。 ここで見て簡単なを見てみましょう。

-   **スケジューラ*** *「スケジュール」とは、特定のコンテナーを実行する方法を規定するホスト システムにサービス ファイルの読み込みに管理者の能力です。 Docker クラスター内のコンテナーの起動は、スケジュール設定と呼ばれる傾向があります。 一般的な意味で、サービス定義の読み込みの特定の動作を指しますスケジュールがスケジューラは必要なすべての容量にサービスを管理するホストの init システムにフックをします。

クラスター スケジューラは、複数の目標: クラスターのリソースを効率的に使用して、ユーザーが指定した配置制約、スケジューリング「公平性を」エラーに堅牢な中の程度を持つ、すぐに保留状態のままにしないアプリケーションの使用と常に使用できます。

-   **オーケストレーション*** *プラットフォームが multicontainer、複雑なワークロードをホストのクラスターに展開されているライフ サイクル管理機能を拡張します。 ホスト インフラストラクチャを抽象化して、によってオーケストレーション ツールは、1 つの配置ターゲットとしてクラスター全体を処理する方法のユーザーを付けます。

オーケストレーションの処理には、ツールと初期配置またはコンテナー; ごとの配置からのアプリケーション管理のすべての側面を自動化できるプラットフォームが含まれます。コンテナーをそのホストの正常性アドインまたはパフォーマンス; に応じて異なるホストに移動バージョン管理とローリング更新プログラムおよび正常性のスケーリングと; のフェールオーバーをサポートする関数の監視さらに多くします。

オーケストレーションは、コンテナーのスケジュール設定、クラスター管理、および他のホストのプロビジョニング可能性のあるを参照する広範な用語です。

Orchestrators およびスケジューラによって提供される機能は、開発し、最初から作成する非常に複雑なしたがって通常はようにするベンダーにより提供されるオーケストレーション ソリューションを使用します。


>[!div class="step-by-step"]
[前](index.md) [次へ] (管理、運用の docker-environments.md)
