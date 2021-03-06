---
title: "方法 : コードを使用してイベント ハンドラーを追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3abcd441219e58df2e5a0d4b66447e255c6aabd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-event-handler-using-code"></a>方法 : コードを使用してイベント ハンドラーを追加する
この例では、コードを使用して要素をイベント ハンドラーを追加する方法を示します。  
  
 イベント ハンドラーを追加する場合、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]要素、および要素を含むマークアップ ページがまだ読み込まれて、コードを使用してハンドラーを追加する必要があります。 また、コードをまったく使用してを使用して任意の要素が宣言されていないアプリケーションの要素ツリーを構築するかどうか[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、構築される要素ツリーにイベント ハンドラーを追加する特定のメソッドを呼び出すことができます。  
  
## <a name="example"></a>例  
 次の例は、新しく追加<xref:System.Windows.Controls.Button>で最初に定義されている既存のページに[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。 分離コード ファイルが、イベント ハンドラー メソッドを実装しで新しいイベント ハンドラーとしてメソッドを追加、<xref:System.Windows.Controls.Button>です。  
  
 [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)]の例では、`+=`演算子をイベントにハンドラーを割り当てます。 これは、ハンドラーを割り当てるために使用する演算子と同じ、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]イベント モデルを処理します。 [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)]イベント ハンドラーを追加するための手段としてこの演算子はサポートされません。 代わりに、2 つの手法の 1 つ必要です。  
  
-   使用して、<xref:System.Windows.UIElement.AddHandler%2A>と連携して、メソッド、`AddressOf`演算子、イベント ハンドラーの実装を参照します。  
  
-   使用して、`Handles`イベント ハンドラーの定義の一部としてキーワード。 この手法はここでは表示されません。参照してください[Visual Basic およびイベント処理の WPF](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)です。  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  最初に解析済みのイベント ハンドラーを追加する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページがはるかに簡単です。 イベント ハンドラーを追加するオブジェクトの要素内で処理するイベントの名前に一致する属性を追加します。 分離コード ファイルで定義されているイベント ハンドラー メソッドの名前とその属性の値を指定、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページ。 詳細については、次を参照してください。 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)または[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)です。  
  
## <a name="see-also"></a>参照  
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
