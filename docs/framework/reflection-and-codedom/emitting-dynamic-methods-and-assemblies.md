---
title: "動的メソッドおよびアセンブリの出力"
ms.custom: 
ms.date: 08/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c724620c987b2ee871dc282bca0dd3da1a5031bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>動的メソッドおよびアセンブリの出力
ここでは、<xref:System.Reflection.Emit> 名前空間のマネージ型のセットについて説明します。これらのマネージ型を使用すると、コンパイラやツールでメタデータおよび Microsoft Intermediate Language (MSIL) を実行時に出力できます。また、ポータブル実行可能 (PE) ファイルをディスク上に生成することもできます。 この名前空間を使用する主な機能は、スクリプト エンジンとコンパイラです。 ここでは、リフレクション出力と呼ばれる <xref:System.Reflection.Emit> 名前空間の機能について説明します。  
  
 リフレクション出力は、以下の機能を提供します。  
  
-   実行時に <xref:System.Reflection.Emit.DynamicMethod> クラスを使用して軽量のグローバル メソッドを定義し、デリゲートを使用してそのメソッドを実行します。  
  
-   実行時にアセンブリを定義し、次に、それらを実行するか、ディスクに保存します。  
  
-   実行時にアセンブリを定義し、それらを実行した後、それらをアンロードし、ガベージ コレクションがリソースを再利用できるようにします。  
  
-   実行時に新しいアセンブリのモジュールを定義し、次に、モジュールを実行するか、ディスクに保存します。  
  
-   実行時にモジュール内の型を定義し、その型のインスタンスを作成してメソッドを呼び出します。  
  
-   デバッガーまたはコード プロファイラなどのツールで使用できる、定義されたモジュールのシンボリック情報を定義します。  
  
 <xref:System.Reflection.Emit> 名前空間のマネージ型に加えて、アンマネージ メタデータ インターフェイスもあります。これについては、[メタデータ インターフェイス](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)に関するリファレンス ドキュメントを参照してください。 マネージ リフレクション出力は、アンマネージ メタデータ インターフェイスよりも強力なセマンティック エラー チェック機能、より高水準なメタデータの抽象化クラスを提供します。  
  
 メタデータと MSIL を使用する際に役立つリソースとしては、他に、共通言語基盤 (CLI: Common Language Infrastructure) のドキュメント、特に「Partition II: Metadata Definition and Semantics」と「Partition III: CIL Instruction Set」などもあります。 このドキュメントは、オンラインの [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) と [Ecma の Web サイト](http://go.microsoft.com/fwlink/?LinkId=116487)で参照できます。  
  
## <a name="in-this-section"></a>このセクションの内容
  
[リフレクション出力のセキュリティ関連事項](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
リフレクション出力を使用した動的アセンブリの作成時のセキュリティ関連事項について説明します。  

[方法: 動的メソッドを定義および実行する](how-to-define-and-execute-dynamic-methods.md)   
単純な動的メソッドおよびクラスのインスタンスにバインドされる動的メソッドを実行する方法を示します。

[方法: リフレクション出力を使用してジェネリック型を定義する](how-to-define-a-generic-type-with-reflection-emit.md)   
2 つの型パラメーターを持つ単純なジェネリック型を作成する方法、クラス制約、インターフェイス制約、特殊な制約を型パラメーターに適用する方法、パラメーターの型や戻り値の型としてクラスの型パラメーターを使用するメンバーを作成する方法を紹介します。

[方法: リフレクション出力を使用してジェネリック メソッドを定義する](how-to-define-a-generic-method-with-reflection-emit.md)   
単純なジェネリック メソッドを作成、出力および呼び出す方法を示します。

[動的な型生成のための収集可能なアセンブリ](collectible-assemblies.md)   
そのアセンブリが作成されたアプリケーション ドメインをアンロードせずにアンロードできる動的アセンブリである、収集可能なアセンブリについて説明します。
  
## <a name="reference"></a>参照  
 <xref:System.Reflection.Emit.OpCodes>  
 メソッド本体の構築に使用できる MSIL 命令コードのカタログを作成します。  
  
 <xref:System.Reflection.Emit>  
 動的メソッド、アセンブリ、および型の出力に使用するマネージ クラスが含まれます。  
  
 <xref:System.Type>  
 <xref:System.Type> クラスについて説明します。このクラスは、マネージ リフレクションとリフレクション出力の型を表し、これらのテクノロジを使用するうえで重要なクラスです。  
  
 <xref:System.Reflection>  
 メタデータとマネージ コードの探索に使用するマネージ クラスが含まれます。  
  
## <a name="related-sections"></a>関連項目  
 [リフレクション](../../../docs/framework/reflection-and-codedom/reflection.md)  
 メタデータとマネージ コードの探索方法について説明します。  
  
 [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 .NET 実装のアセンブリの概要を説明します。
