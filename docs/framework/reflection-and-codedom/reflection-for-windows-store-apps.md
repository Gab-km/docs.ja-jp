---
title: "Windows ストア アプリのための .NET Framework のリフレクション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection, Windows Store apps
- .NET for Windows Store apps, TypeInfo class
ms.assetid: 0d07090c-9b47-4ecc-81d1-29d539603c9b
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f015a8323079b4c63cc217826769316c44fa986d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Windows ストア アプリのための .NET Framework のリフレクション
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降、.NET Framework には、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリで使用される一連の使用のリフレクション型およびメンバーのセットが含まれます。 これらの型およびメンバーは、完全な .NET Framework だけでなく [Windows ストア アプリ用 .NET](http://go.microsoft.com/fwlink/?LinkID=225700) でも使用できます。 このドキュメントでは、これらと .NET Framework 4 以前のバージョンでの対応するものとの主な相違点について説明します。  
  
 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリを作成する場合は、[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] でリフレクション型とメンバーを使用する必要があります。 デスクトップ アプリを使用する場合もこれらの型およびメンバーを使用できますが、必須ではないため、両方のタイプのアプリに同じコードを使用できます。  
  
## <a name="typeinfo-and-assembly-loading"></a>TypeInfo およびアセンブリの読み込み  
 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] では、<xref:System.Reflection.TypeInfo> クラスに .NET Framework 4 <xref:System.Type> クラスの機能の一部が含まれます。 <xref:System.Type> オブジェクトは型定義への参照を表し、<xref:System.Reflection.TypeInfo> オブジェクトは型定義自体を表します。 これによって、参照するアセンブリをランタイムが必ずしも読み込まなくても、<xref:System.Type> オブジェクトを操作できるようになります。 関連付けられた <xref:System.Reflection.TypeInfo> オブジェクトを取得すると、アセンブリが強制的に読み込まれます。  
  
 <xref:System.Reflection.TypeInfo> には <xref:System.Type> で使用できるメンバーの多くが含まれ、[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] のリフレクションのプロパティの多くは <xref:System.Reflection.TypeInfo> オブジェクトのコレクションを返します。 <xref:System.Reflection.TypeInfo> オブジェクトから <xref:System.Type> オブジェクトを取得するには、<xref:System.Reflection.IReflectableType.GetTypeInfo%2A> メソッドを使用します。  
  
## <a name="query-methods"></a>クエリ メソッド  
 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] では、配列を返すメソッドではなく、<xref:System.Collections.Generic.IEnumerable%601> コレクションを返すリフレクション プロパティを使用します。 リフレクション コンテキストは、大型のアセンブリまたは型用に、これらのコレクションの限定的な走査を実装できます。  
  
 リフレクション プロパティは、継承ツリーを走査する代わりに、特定オブジェクトの宣言されたメソッドのみを返します。 また、フィルター処理に <xref:System.Reflection.BindingFlags> パラメーターを使用しません。 代わりに、返されるコレクションで LINQ クエリを使用することにより、フィルター処理をユーザー コード内で発生させます。 (`typeof(Object)` の結果などにより) ランタイムから始まるリフレクション オブジェクトの場合、継承ツリーを走査するには <xref:System.Reflection.RuntimeReflectionExtensions> クラスのヘルパー メソッドを使用するのが最も適切です。 カスタマイズされたリフレクション コンテキストのオブジェクトのコンシューマーは、これらのメソッドを使用できず、独自に継承ツリーを走査する必要があります。  
  
## <a name="restrictions"></a>制約  
 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリでは、.NET Framework の一部の型とメンバーへのアクセスが制限されます。 たとえば、[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] オブジェクトを使用して、<xref:System.Reflection.MethodInfo> に含まれない .NET Framework のメソッドを呼び出すことはできません。 また、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] メンバーおよび <xref:System.Runtime.InteropServices.Marshal> メンバーと同様に、<xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal> アプリにおいて安全とは見なされない特定の型およびメンバーはブロックされます。 この制限は、.NET Framework の型とメンバーにのみ適用されます。ユーザー コードやサードパーティ コードは通常どおり呼び出すことができます。  
  
## <a name="example"></a>例  
 この例は、[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] のリフレクション型とメンバーを使用して、<xref:System.Globalization.Calendar> 型のメソッドとプロパティを、継承されたメソッドとプロパティも含めて取得します。 このコードを実行するには、Reflection という名前のプロジェクトの `textblock1` という名前の [Windows.UI.Xaml.Controls.Textblock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) コントロールを含む [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ページ用のコード ファイルにこのコードを貼り付けます。 別の名前のプロジェクトにこのコードを張り付ける場合は、名前空間の名前をプロジェクトに一致するように変更してください。  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>参照  
 [リフレクション](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [Windows ストア アプリ用 .NET – サポートされている API](http://go.microsoft.com/fwlink/?LinkID=225700)
