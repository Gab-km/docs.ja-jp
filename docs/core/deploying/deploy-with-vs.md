---
title: "Visual Studio で .NET Core アプリを展開する | Microsoft Docs"
description: "Visual Studio で .NET Core アプリを展開する方法を説明します。"
keywords: ".NET, .NET Core, .NET Core 展開"
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 01049a21-fd50-4419-9ab2-0e4a2e091050
ms.translationtype: Human Translation
ms.sourcegitcommit: 3ffe3909902659a22cb25bac6dc5aaa4f5b9fde2
ms.openlocfilehash: c6fe1813f0d09207c6730fc5dce682647e25eb03
ms.contentlocale: ja-jp
ms.lasthandoff: 05/13/2017

---

# <a name="deploying-net-core-apps-with-visual-studio"></a>Visual Studio で .NET Core アプリを展開する

.NET Core アプリケーションは、アプリケーション バイナリは含むが、対象のシステムに .NET Core があるかどうかに依存する*フレームワークに依存する展開*、またはアプリケーションと .NET Core バイナリの両方を含む*自己完結型の展開*のいずれかで展開できます。 .NET Core アプリケーションの展開の概要については、「[.NET Core アプリケーションの展開](index.md)」を参照してください。

次のセクションでは、Microsoft Visual Studio を使用して、次のような展開を作成する方法を示します。

- フレームワークに依存する展開
- サードパーティの依存関係を含む、フレームワークに依存する展開
- 自己完結型の展開
- サードパーティの依存関係を含む、自己完結型の展開

Visual Studio を使用して、.NET Core アプリケーションを開発する方法の詳細については、「[Windows における .NET Core の前提条件](../windows-prerequisites.md#prerequisites-with-visual-studio-2017)」を参照してください。

## <a name="framework-dependent-deployment"></a>フレームワークに依存する展開

サードパーティの依存関係を含まない、フレームワークに依存する展開を展開するプロセスには、アプリのビルド、テスト、および発行が含まれます。 C# で記述された次の単純な例は、このプロセスを示しています。  

1. プロジェクトを作成します。

   [**ファイル**] > [**新規作成**] > [**プロジェクト**] を順に選択します。 [**新しいプロジェクト**] ダイアログの [**インストール済み**] プロジェクトの種類ウィンドウで、[**.NET Core**] を選択し、中央のウィンドウで [**コンソール アプリケーション (.NET Core)**] テンプレートを選択します。 [**名前**] テキスト ボックスに、"FDD" などのプロジェクト名を入力します。 [**OK**] ボタンを選択します。

1. アプリケーションのソース コードを追加します。

   エディターで *Program.cs* ファイルを開き、自動生成されたコードを次のコードに置き換えます。 テキストの入力を求めるプロンプトが表示されてから、ユーザーが入力した個々の単語が表示されます。 正規表現 `\w+` を使用して、入力テキストの単語を分離します。

   [!code-cs[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. アプリのデバッグ ビルドを作成します。

   [**ビルド**] > [**ソリューションのビルド**] を順に選択します。 [**デバッグ**] > [**デバッグ開始**] を選択して、アプリケーションのデバッグ ビルドをコンパイルして、実行することも可能です。

1. アプリを展開します。

   プログラムをデバッグしてテストしたら、アプリと共に配置するファイルを作成します。 Visual Studio から発行するには、次の操作を行います。

      1. アプリの (デバッグではなく) リリース バージョンを構築するために、ツールバーでソリューションの構成を [**デバッグ**] から [**リリース**] に変更します。

      1. **ソリューション エクスプローラー**で (ソリューションではなく) プロジェクトを右クリックし、[**発行**] を選択します。

      1. [**発行**] タブで [**発行**] を選択します。 Visual Studio が、アプリケーションを構成するファイルをローカル ファイル システムに書き込みます。

      1. これで [**発行**] タブには、[**FolderProfile**] という 1 つのプロファイルが表示されます。 プロファイルの構成設定が、タブの [**概要**] セクションに表示されます。

   作成されたファイルは、プロジェクトの *.\bin\release* サブディレクトリのサブディレクトリ内にある、`PublishOutput` という名前のディレクトリに配置されます。

アプリケーションのファイルと共に、発行プロセスは、アプリに関するデバッグ情報を含むプログラム データベース (.pdb) ファイルを出力します。 このファイルは、主に例外のデバッグに役立ちます。 これを、アプリケーションのファイルにはパッケージ化しないよう選択できます。 ただし、アプリのリリース ビルドをデバッグする場合のために、保存しておくことをお勧めします。

アプリケーション ファイルの完全なセットは、任意の方法で展開できます。 たとえば、Zip ファイルにパッケージ化したり、単純な `copy` コマンドを使用したり、任意のインストール パッケージで展開したりできます。 インストールしたら、ユーザーはアプリケーションを、`dotnet` コマンドを使用し、`dotnet fdd.dll` などのアプリケーションのファイル名を提供して実行できます。

また、アプリケーション インストールの一環として、インストーラーはアプリケーション バイナリに加えて、共有フレームワーク インストーラーをバンドルするか、または前提条件として共有フレームワークがあるか確認する必要があります。  共有フレームワークのインストールは、コンピューター全体が対象なので、管理者/ルート アクセスを必要とします。

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>サードパーティの依存関係を含む、フレームワークに依存する展開

1 つ以上のサードパーティの依存関係を備えたフレームワークに依存する展開を展開するには、すべての依存関係をプロジェクトに使用できる必要があります。 アプリをビルドする前に、次の追加手順が必要です。

1. **NuGet パッケージ マネージャー**を使用し、プロジェクトに NuGet パッケージへの参照を追加します。このとき、パッケージがシステムにまだない場合はそれをインストールします。 パッケージ マネージャーを開くには、[**ツール**] > [**NuGet パッケージ マネージャー**] > [**ソリューションの NuGet パッケージの管理**] を順に選択します。

1. `Newtonsoft.Json` がシステムにインストールされていることを確認します。されていない場合はインストールします。 [**インストール済み**] タブに、システムにインストールされた NuGet パッケージの一覧が表示されます。 `Newtonsoft.Json` がそこにない場合、[**参照**] タブを選択し、検索ボックスに "Newtonsoft.Json" と入力します。 `Newtonsoft.Json` を選択し、右側のウィンドウでプロジェクトを選択してから、[**インストール**] を選択します。

1. `Newtonsoft.Json` が既にシステムにインストールされている場合、[**ソリューション パッケージの管理**] タブの右のウィンドウから選択し、プロジェクトに追加します。

サードパーティの依存関係を含む、フレームワークに依存する展開は、サードパーティの依存関係と同じ移植性を持つことに注意してください。 たとえば、サードパーティ ライブラリが macOS のみをサポートする場合、そのアプリを Windows システムに移植することはできません。 この状況は、サードパーティの依存関係自体がネイティブ コードに依存する場合に生じる可能性があります。 これの良い例は、[libuv](https://github.com/libuv/libuv) に対してネイティブの依存関係が必要な [Kestrel サーバー](http://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel)です。 このようなサードパーティの依存関係を含むアプリケーションに対して FDD が作成されると、発行された出力には、ネイティブの依存関係がサポートする (そして、その NuGet パッケージ内に存在する) 各[ランタイム識別子 (RID)](../rid-catalog.md#what-are-rids) のフォルダーが含まれます。

## <a name="simpleSelf"></a> サードパーティの依存関係を含まない、自己完結型の展開

サードパーティの依存関係を含まない自己完結型の展開を展開するプロセスには、プロジェクトの作成、*csproj*ファイルの変更、アプリのビルド、テスト、および発行が含まれます。 C# で記述された次の単純な例は、このプロセスを示しています。 

1. プロジェクトを作成します。

   [**ファイル**] > [**新規作成**] > [**プロジェクト**] を順に選択します。 [**新しいプロジェクトの追加**] ダイアログの [**インストール済み**] プロジェクトの種類ウィンドウで、[**.NET Core**] を選択し、中央のウィンドウで [**コンソール アプリケーション (.NET Core)**] テンプレートを選択します。 [**名前**] テキスト ボックスに、"SCD" などのプロジェクト名を入力し、[**OK**] ボタンを選択します。

1. アプリケーションのソース コードを追加します。

   エディターで *Program.cs* ファイルを開き、自動生成されたコードを次のコードに置き換えます。 テキストの入力を求めるプロンプトが表示されてから、ユーザーが入力した個々の単語が表示されます。 正規表現 `\w+` を使用して、入力テキストの単語を分離します。

   [!code-cs[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. アプリの対象プラットフォームを定義します。

   1. **ソリューション エクスプローラー**で (ソリューションではなく) プロジェクトを右クリックし、[**編集**] を選択します。

   1. *csproj* ファイルの `<PropertyGroup>` セクションに、アプリの対象のプラットフォームを定義する `<RuntimeIdentifiers>` タグを作成し、対象とするプラットフォームごとにランタイム識別子 (RID) を指定します。 なお、RID の分離にはセミコロンを追加する必要があることに注意してください。 ランタイム識別子の一覧については、「[Runtime IDentifier catalog](../rid-catalog.md)」 (ランタイム識別子のカタログ) を参照してください。 

   たとえば、次の例は、アプリが 64 ビット Windows 10 オペレーティング システムおよび 64 ビット OS X バージョン 10.11 オペレーティング システムで実行されることを示します。

       ```xml
        <PropertyGroup>
          <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
        </PropertyGroup>
       ```
   なお、`<RuntimeIdentifiers>` 要素は、*csproj* ファイルの任意の `<PropertyGroup>` に入れることが可能です。 *csproj* ファイルの完全なサンプルは、このセクションの後の部分で示しています。

1. アプリのデバッグ ビルドを作成します。

   [**ビルド**] > [**ソリューションのビルド**] を順に選択します。 [**デバッグ**] > [**デバッグ開始**] を選択して、アプリケーションのデバッグ ビルドをコンパイルして、実行することも可能です。

1. アプリケーションを発行します。

   プログラムをデバッグしてテストしたら、アプリと共に展開するファイルをアプリの対象のプラットフォームごとに作成します。

   Visual Studio でアプリを発行するには、次の操作を行います。

      1. アプリの (デバッグではなく) リリース バージョンを構築するために、ツールバーでソリューションの構成を [**デバッグ**] から [**リリース**] に変更します。

      1. **ソリューション エクスプローラー**で (ソリューションではなく) プロジェクトを右クリックし、[**発行**] を選択します。 

      1. [**発行**] タブで [**発行**] を選択します。 Visual Studio が、アプリケーションを構成するファイルをローカル ファイル システムに書き込みます。

      1. これで [**発行**] タブには、[**FolderProfile**] という 1 つのプロファイルが表示されます。 プロファイルの構成設定が、タブの [**概要**] セクションに表示されます。 [**Target Runtime**]\(ターゲット ランタイム\) では、発行されたランタイムを識別し、[**対象の場所**] は自己完結型の展開が書き込まれた場所を識別します。

      1. Visual Studio は、発行されたすべてのファイルを、既定で 1 つのディレクトリに書き込みます。 ターゲット ランタイムごとに別のプロファイルを作成し、発行したファイルはプラットフォームごとのディレクトリに配置すると便利なのでお勧めします。 これを行う場合、対象のプラットフォームごとに別の発行プロファイルも作成します。 ここでは、次の手順でプラットフォームごとにアプリケーションを再構築します。

         1. [**発行**] ダイアログで、[**新しいプロファイルの作成**] を選択します。

         1. [**Pick a publish target**]\(発行する対象の選択)\ ダイアログで [**Choose a folder**]\(フォルダーを選択)\ の場所を *bin\Release\PublishOutput\win10-x64* に変更します。 **[OK]** を選択します。

         1. 新しいプロファイル (**FolderProfile1**) をプロファイルの一覧から選択し、[**Target Runtime**]\(ターゲット ランタイム\) が `win10-x64` であることを確認します。 違う場合は、[**設定**] を選択します。 [**プロファイルの設定**] ダイアログで、[**Target Runtime**]\(ターゲット ランタイム\) を `win10-x64` に変更して、[**保存**] を選択します。 それ以外の場合、[**キャンセル**] を選択します。

         1. 64 ビットの Windows 10 プラットフォーム用にアプリを発行するために、[**発行**] を選択します。

         1. 前の手順を繰り返して、`osx.10.11-x64` プラットフォームのプロファイルを作成します。 [**対象の場所**] が *bin\Release\PublishOutput\osx.10.11-x64* で、[**Target Runtime**]\(ターゲット ランタイム\) は [`osx.10.11-x64`] です。 Visual Studio がこのプロファイルに割り当てる名前は、**FolderProfile2** です。

      それぞれの対象の場所には、アプリの起動に必要なファイルの完全なセット (アプリ ファイルとすべての .NET Core ファイルの両方) が含まれています。

アプリケーションのファイルと共に、発行プロセスは、アプリに関するデバッグ情報を含むプログラム データベース (.pdb) ファイルを出力します。 このファイルは、主に例外のデバッグに役立ちます。 これを、アプリケーションのファイルにはパッケージ化しないよう選択できます。 ただし、アプリのリリース ビルドをデバッグする場合のために、保存しておくことをお勧めします。

発行したファイルは、任意の方法で展開できます。 たとえば、Zip ファイルにパッケージ化したり、単純な `copy` コマンドを使用したり、任意のインストール パッケージで展開したりできます。

このプロジェクトの完全な *csproj* ファイルを次に示します。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a>サードパーティの依存関係を含む、自己完結型の展開

1 つまたは複数のサードパーティの依存関係を含む自己完結型の展開を展開するプロセスには、依存関係の追加が含まれます。 アプリをビルドする前に、次の追加手順が必要です。

1. **NuGet パッケージ マネージャー**を使用し、プロジェクトに NuGet パッケージへの参照を追加します。このとき、パッケージがシステムにまだない場合はそれをインストールします。 パッケージ マネージャーを開くには、[**ツール**] > [**NuGet パッケージ マネージャー**] > [**ソリューションの NuGet パッケージの管理**] を順に選択します。

1. `Newtonsoft.Json` がシステムにインストールされていることを確認します。されていない場合はインストールします。 [**インストール済み**] タブに、システムにインストールされた NuGet パッケージの一覧が表示されます。 `Newtonsoft.Json` がそこにない場合、[**参照**] タブを選択し、検索ボックスに "Newtonsoft.Json" と入力します。 `Newtonsoft.Json` を選択し、右側のウィンドウでプロジェクトを選択してから、[**インストール**] を選択します。

1. `Newtonsoft.Json` が既にシステムにインストールされている場合、[**ソリューション パッケージの管理**] タブの右のウィンドウからプロジェクトを選択し、プロジェクトに追加します。

このプロジェクトの完全な *csproj* ファイルを次に示します。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

アプリケーションを展開すると、アプリで使用されるすべてのサードパーティの依存関係も、アプリケーション ファイルに含まれています。 アプリが実行されているシステムには、サードパーティ ライブラリは必要ありません。

サードパーティ ライブラリを含む自己完結型の展開は、そのライブラリでサポートされるプラットフォームにのみ展開できます。 これは、フレームワークに依存する展開にサード パーティの依存関係とネイティブの依存関係があり、ネイティブの依存関係は前にインストールしていた場合を除き、対象のプラットフォームにない場合と似ています。

# <a name="see-also"></a>関連項目
[.NET Core アプリケーションの展開](index.md)   
[.NET Core のランタイム識別子 (RID) のカタログ](../rid-catalog.md)   
