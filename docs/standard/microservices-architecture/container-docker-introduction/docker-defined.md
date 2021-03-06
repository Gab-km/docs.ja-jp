---
title: "Docker とは何ですか。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Docker とは何ですか。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: aa9cb379628fa91e5dc5b1b529f92db98fa59305
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="what-is-docker"></a>Docker とは何ですか。

[Docker](https://www.docker.com/)は、[オープン ソース プロジェクト](https://github.com/docker/docker)クラウドまたはオンプレミスで実行できるポータブル、自分のコンテナーとしてのアプリケーションの展開を自動化するためです。 Docker はでも、[会社](https://www.docker.com/)を昇格し、このテクノロジは進化します。 Docker は、クラウド、Linux、およびなどの Microsoft Windows ベンダーと共同で動作します。

![](./media/image2.png)

**図 2-2**です。 Docker は、ハイブリッド クラウドのすべてのレイヤーでコンテナーを展開します。

Docker イメージ コンテナーは、Linux と Windows 上でネイティブに実行します。 Windows イメージを Windows ホストでのみ実行して、Linux のイメージが Linux ホストでのみ実行します。 ホストは、サーバーまたは VM です。

Windows、Linux、または macOS を開発することができます。 開発用コンピューターには、アプリとその依存関係を含めて、Docker のイメージが展開されている Docker ホストが実行されます。 Linux または macOS では、Linux ベースと Linux コンテナーにのみイメージを作成できます Docker ホストを使用します。(Macos には、コードを編集または Docker CLI を実行することができますがこの記事の執筆時点で、コンテナー上で実行しないで直接 macOS)。Windows では、Linux または Windows コンテナーのいずれかのイメージを作成できます。

Windows または macOS、 [Docker Community Edition (CE)](https://www.docker.com/community-edition)開発環境でコンテナーをホストし、その他の開発者ツールを提供します。 [Docker の Enterprise Edition (EE)](https://www.docker.com/enterprise-edition)ビルド、出荷、および大規模な基幹業務アプリケーションを実行する IT チームが使用されます。 ~ 両方の製品が必要な VM のコンテナーをホストする (、Docker ホスト) をインストールします ~。 

[Windows コンテナー](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)ランタイムの 2 つの種類で機能します。

-   Windows Server コンテナーは、プロセスと名前空間の分離テクノロジを使用してアプリケーションの分離を提供します。 Windows Server コンテナーは、コンテナー ホストとホストで実行されているすべてのコンテナーに、カーネルを共有します。

-   HYPER-V コンテナーは、各コンテナーを大幅に最適化された仮想マシンで実行して Windows Server コンテナーによって提供される分離に展開されます。 コンテナーでは、HYPER-V、分離性を提供することは、この構成では、コンテナー ホストのカーネルを共有されません。 HYPER-V コンテナーでは、信頼されていないと*悪意のあるマルチ テナント*アプリケーションを同じホストで実行します。 HYPER-V コンテナーでは、スタートアップに時間と Windows Server コンテナーより密度の節約の効率性があります。

これらのコンテナーのイメージが作成され、同じように機能します。 コンテナーの作成方法が異なります。 詳細については、「 [Hyper-v コンテナー](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)です。

## <a name="comparing-docker-containers-with-virtual-machines"></a>仮想マシンでの Docker コンテナーの比較

図 2-3 は、Vm と Docker の比較を示しています。 コンテナーです。

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **仮想マシン****Docker コンテナー** 
                                                                                                                                                                                        
  ![](./media/image3.png)                                                                                                                                ![](./media/image4.png)
                                                                                                                                                                                        
  仮想マシンには、アプリケーション、必要なライブラリまたはバイナリ、および完全ゲスト オペレーティング システムが含まれます。 完全な仮想化では、コンテナリゼーションより多くのリソースが必要です。 コンテナーには、アプリケーションとそのすべての依存関係が含まれます。 ただし、コンテナーは、他のコンテナーを OS カーネルを共有します。 コンテナーは、ホスト オペレーティング システムでのユーザー領域の分離のプロセスとして実行します。 コンテナーごとに特別な仮想マシン内では、各コンテナーが実行されている HYPER-V コンテナーでは可します。
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**図 2-3**です。 Docker コンテナーへの従来の仮想マシンの比較

コンテナーがはるかに少ないリソースを必要とするため (たとえば、する必要はありません、完全な OS)、高速に起動され、簡単に配置します。 低いリソース使用率は、高密度を使用できます。 同じハードウェア単位でより多くのサービスを実行し、コストを削減できます。

カーネルで同じ結果 Vm よりも少ない分離で実行します。

イメージの主な目的は、することが環境 (依存関係) 同じ上でさまざまな展開です。 つまり、コンピューターにデバッグおよび保証同じ環境内の別のコンピューターに展開できます。

コンテナー イメージは、アプリやサービスをパッケージ化し、信頼性が高く、再現可能な方法で展開する方法です。 Docker ではあるだけでなく、技術方針やもプロセスとする可能性があります。

Docker 開発者しないと、「動作私のコンピューターでは、なぜ実稼働環境で?」 よく言わ「で実行される Docker」です。 Docker にパッケージされたアプリは、Docker のサポートされているどの環境で実行することができます。 Docker は、一貫してすべて配置ターゲットを実行 (Dev、QA、ステージング、実稼働) アプリをパッケージ化されます。

>[!div class="step-by-step"]
[前](index.md) [次へ] (docker terminology.md)
