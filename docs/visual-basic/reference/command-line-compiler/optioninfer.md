---
title: /optioninfer
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2df7fa743e72d12dcef1aa9be5ea43d24ef43cee
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="optioninfer"></a>/optioninfer
変数宣言でローカル型推論を使用できるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
/optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`+` &#124; `-`|任意。 `/optioninfer+` を指定してローカル型推論を有効にするか、または `/optioninfer-` を指定してローカル型推論をブロックします。 `/optioninfer` オプションは、何も値を指定しない場合、`/optioninfer+` と同じです。 `/optioninfer` スイッチが存在しない場合の既定値も `/optioninfer+` です。 既定値は、Vbc.rsp 応答ファイル内に設定されています。|  
  
> [!NOTE]
>  `/noconfig` オプションを使用すると、vbc.rsp に指定するのではなく、コンパイラの内部既定値を保持できます。 このオプションのコンパイラの既定値は `/optioninfer-` です。  
  
## <a name="remarks"></a>コメント  
 ソース コード ファイルが含まれている場合、 [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)、ステートメントよりも優先、`/optioninfer`コマンド ライン コンパイラ設定します。  
  
### <a name="to-set-optioninfer-in-the-visual-studio-ide"></a>Visual Studio IDE で /optioninfer を設定するには  
  
1.  プロジェクトを選択**ソリューション エクスプ ローラー**です。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **コンパイル** タブの値を変更、 **Option infer**ボックス。  
  
## <a name="example"></a>例  
 次のコードは、ローカル型推論を有効にした状態で `test.vb` をコンパイルします。  
  
```  
vbc /optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>参照  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [ローカル型の推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [コマンド ラインからのビルド](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
