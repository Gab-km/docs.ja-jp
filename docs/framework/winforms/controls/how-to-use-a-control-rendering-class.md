---
title: "方法 : コントロールの描画クラスを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- visual themes [Windows Forms], applying to Windows Forms controls
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbf17ea84cb24d167975e6b918a0410a38c8ed3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-control-rendering-class"></a>方法 : コントロールの描画クラスを使用する
この例で使用する方法、<xref:System.Windows.Forms.ComboBoxRenderer>をコンボ ボックスの矢印ボックス コントロールをレンダリングします。 例から成る、<xref:System.Windows.Forms.Control.OnPaint%2A>単純なカスタム コントロールのメソッドです。 <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType>プロパティを使用して、アプリケーション ウィンドウのクライアント領域で visual スタイルが有効かどうかを確認します。 Visual スタイルが、アクティブな場合、<xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType>メソッドは、visual スタイル; で、ドロップダウン矢印をレンダリングするそれ以外の場合、<xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType>メソッドは従来の Windows スタイルでのドロップダウン矢印を表示します。  
  
## <a name="example"></a>例  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   派生したカスタム コントロール、<xref:System.Windows.Forms.Control>クラスです。  
  
-   A<xref:System.Windows.Forms.Form>カスタム コントロールをホストします。  
  
-   参照、 <xref:System?displayProperty=nameWithType>、 <xref:System.Drawing?displayProperty=nameWithType>、 <xref:System.Windows.Forms?displayProperty=nameWithType>、および<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType>名前空間。  
  
## <a name="see-also"></a>参照  
 [visual スタイルが使用されているコントロールのレンダリング](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)
