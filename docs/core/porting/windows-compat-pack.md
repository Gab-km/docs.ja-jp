---
title: ".NET Core に移植する - Windows 互換機能パックの使用"
description: "Windows 互換機能パックとそれを使用して既存の .NET Framework コードを .NET Core に移植する方法について紹介します。"
keywords: ".NET, .NET Core, Windows, 互換機能"
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 3b1fe02aad4f78499158ecb7fa9b8521cb7d992e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="using-the-windows-compatibility-pack"></a>Windows 互換機能パックの使用

既存のコードを .NET Core に移植するとき、開発者が直面する最も一般的な問題の 1 つが、.NET Framework にのみ存在する API とテクノロジに対する依存性です。 *Windows 互換機能パック*はそのようなテクノロジを各種提供します。既存コードの実行可能性を上げるような方法で .NET Core アプリケーションと .NET Standard ライブラリをビルドできます。

このパッケージは論理 [.NET Standard 2.0 の拡張](../whats-new/index.md#api-changes-and-library-support)であり、API セットを大幅に増やします。ほとんど変更なしで既存コードがコンパイルされます。 ただし、.NET Standard の約束 ("これはあらゆる .NET 実装の API を集めたものである") を守る目的で、レジストリ、Windows Management Instrumentation (WMI)、リフレクション出力 API など、すべてのプラットフォームで動作しないテクノロジは含まれていません。

*Windows 互換機能パック*は .NET Standard を基盤とし、Windows 専用のテクノロジを利用できます。 .NET Core に移行したいが、最初の手順が Windows に留まることである顧客にとって特に便利です。 そのようなシナリオでは、Windows 専用テクノロジを利用できないことが移行における唯一のハードルとなります。アーキテクチャ上の利点がありません。

## <a name="package-contents"></a>パッケージの内容

*Windows 互換機能パック*は NuGet パッケージ [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) 経由で提供され、.NET Core または .NET Standard を対象とするプロジェクトから参照できます。

Windows 専用 API やプラットフォーム非依存 API など、約 20,000 の API を提供します。テクノロジ領域には次のものがあります。

* コード ページ
* CodeDom
* 構成
* ディレクトリ サービス
* 描画
* ODBC
* アクセス許可
* ポート
* Windows アクセス制御リスト (ACL)
* Windows Communication Foundation (WCF)
* Windows 暗号化
* Windows EventLog
* WMI (Windows Management Instrumentation)
* Windows パフォーマンス カウンター
* Windows レジストリ
* Windows ランタイム キャッシュ
* Windows サービス

詳細については、[互換機能パックの仕様](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md)をご覧ください。

## <a name="get-started"></a>作業開始

1. 移植の前に、[移植プロセス](index.md)を確認してください。

2. .NET Core または .NET Standard に既存のポートを移植するとき、NuGet パッケージ [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) をインストールします。

3. Windows に留まる場合、すでに用意はできています。

4. .NET Core アプリケーションまたは .NET Standard ライブラリを Linux または macOS で実行する場合、[API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) を使用し、プラットフォーム非依存で機能しない API の使用を見つけます。

5. そのような API の使用を取り除くか、プラットフォーム非依存の代替で置換するか、プラットフォーム チェックで保護します (以下参照)。

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

デモについては、[Windows 互換機能パックの Channel 9 動画](https://channel9.msdn.com/Events/Connect/2017/T123)をご覧ください。

