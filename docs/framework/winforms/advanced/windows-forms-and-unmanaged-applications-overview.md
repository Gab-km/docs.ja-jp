---
title: "Windows フォームおよびアンマネージ アプリケーションの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop
- ActiveX controls [Windows Forms], about ActiveX controls
- Windows Forms, interop
ms.assetid: 0a26d99d-8135-4895-8760-c9a2b5f67f14
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ad64588727584a9b3de0a95e9bad252a3fb0581
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="windows-forms-and-unmanaged-applications-overview"></a>Windows フォームおよびアンマネージ アプリケーションの概要
Windows フォーム アプリケーションとコントロールは、いくつかの注意事項がありますが、アンマネージ アプリケーションと相互運用できます。 次のセクションでは、Windows フォーム アプリケーションとコントロールがサポートするシナリオと構成、および、サポートしないシナリオと構成について説明します。  
  
## <a name="windows-forms-controls-and-activex-applications"></a>Windows フォーム コントロールおよび ActiveX アプリケーション  
 Microsoft Internet Explorer と Microsoft Foundation Classes (MFC) を除いて、Windows フォーム コントロールは、ActiveX コントロールをホストするように設計されたアプリケーションではサポートされません。 Visual Studio .NET 2003 より前のバージョンの Visual Studio からの ActiveX テスト コンテナーなど、ActiveX コントロールをホストできるその他のアプリケーションと開発ツールは、Windows Forms コントロールでサポートされるホストではありません。  
  
 これらの制約は、コンポーネント オブジェクト モデルの COM 相互運用機能を通じて、Windows フォーム コントロールの使用にも適用されます。 COM 呼び出し可能ラッパー (CCW) を通じた Windows フォーム コントロールの使用は、Internet Explorer でのみサポートされます。 COM 相互運用の詳細については、  
  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)。  
  
 Windows フォーム コントロールのサポートをホストしている、使用できる ActiveX を次の表に示します。  
  
|Windows フォームのバージョン|Support|  
|---------------------------|-------------|  
|.NET Framework version 1.0|Internet Explorer 5.01 以降のバージョン|  
|.NET Framework version 1.1 以降|Internet Explorer 5.01 以降のバージョン<br /><br /> Microsoft Foundation Classes (MFC) 7.0 以降|  
  
## <a name="hosting-windows-forms-components-as-activex-controls"></a>ActiveX コントロールとして Windows フォームのコンポーネントをホストする  
 .NET Framework 1.1 では、MFC 7.0 以降のバージョンを含めるようサポートが拡張されました。 このサポートには、MFC 7.0 以降の ActiveX コントロール コンテナーと完全に互換性があるすべてのコンテナーが含まれています。  
  
 ただし、Windows フォーム コントロールの ActiveX コントロールとしての登録はサポートされません。 また、Windows フォーム コントロールの `com.ms.win32.Ole32.CoCreateInstance` メソッドの呼び出しはサポートされていません。 Windows フォーム コントロールのマネージ アクティベーションだけがサポートされます。 Windows フォーム コントロールを作成すると、ActiveX コントロールの場合と同様に MFC アプリケーションでホストできます。  
  
 アンマネージ アプリケーションで Windows フォーム コントロールを使用するには、アンマネージ CLR ホスティング API を使用して CLR をホストするか、C++ interop 機能を使用する必要があります。 C++ interop 機能の使用が、推奨されるソリューションです。  
  
## <a name="windows-forms-in-com-client-applications"></a>COM クライアント アプリケーションでの Windows フォーム  
 Windows フォームを Visual Basic 6.0 アプリケーションや MFC アプリケーションなどの COM クライアント アプリケーションから開くと、フォームが予期しない動作をすることがあります。 たとえば、TAB キーを押した時に、フォーカスが 1 つのコントロールから別のコントロールに変更されません。 コマンド ボタンにフォーカスがあるときに ENTER キーを押すと、ボタンの <xref:System.Windows.Forms.Control.Click> イベントは発生しません。 また、キー ストロークやマウスのアクティビティで、予期しない動作が発生することもあります。  
  
 この動作は、Windows フォームが正常に動作するために必要なメッセージ ループ サポートを、アンマネージ アプリケーションが実装していないために発生します。 COM クライアント アプリケーションによって提供されるメッセージ ループは、Windows フォームのメッセージ ループと基本的に異なります。  
  
 アプリケーションのメッセージ ループは、スレッドのメッセージ キューのメッセージを取得して変換し、処理のためにアプリケーションに送信する内部プログラム ループです。 Windows フォームのメッセージ ループは、Visual Basic 6.0 アプリケーションや MFC アプリケーションなど、以前のアプリケーションが提供するメッセージ ループと同じアーキテクチャを持っていません。 メッセージ ループにポストされたウィンドウのメッセージは、Windows フォームの要求とは異なる処理を実行することがあります。 そのため、予期しない動作が発生する可能性があります。 一部のキーストロークの組み合わせ、一部のマウスのアクティビティが動作せず、一部のイベントが想定どおりに発生しないことがあります。  
  
## <a name="resolving-interoperability-issues"></a>相互運用性の問題の解決  
 これらの問題は、<xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> メソッドを使用して作成された [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] メッセージ ループでフォームを表示することで解決できます。  
  
 Windows フォームが COM クライアント アプリケーションから正しく動作するには、Windows フォームのメッセージ ループ上で実行する必要があります。 そのためには、次の方法のいずれかを使用します。  
  
-   <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> メソッドを使用して、Windows フォームを表示します。 詳細については、「 [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)」を参照してください。  
  
-   各 Windows フォームを新しいスレッドで表示します。 詳細については、「[方法 : 独自のスレッドで各 Windows フォームを表示して COM 相互運用機能をサポートする](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Windows フォームとアンマネージ アプリケーション](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 [COM 相互運用](../../../visual-basic/programming-guide/com-interop/index.md)  
 [.NET Framework アプリケーションにおける COM 相互運用性](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [COM 相互運用性サンプル](http://msdn.microsoft.com/library/09c38567-6380-4d70-848a-e896a4ca05f4)  
 [Aximp.exe (Windows フォーム ActiveX コントロール インポーター)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)  
 [COM への .NET Framework コンポーネントの公開](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [COM 用のアセンブリのパッケージ化](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [COM へのアセンブリの登録](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [方法: ShowDialog メソッドで Windows フォームを表示して COM 相互運用機能をサポートする](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [方法: 独自のスレッドで各 Windows フォームを表示して COM 相互運用機能をサポートする](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
