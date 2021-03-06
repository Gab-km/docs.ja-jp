---
title: "例外: failwith 関数 (F#)"
description: "'Failwith' 関数が f# の例外を生成する方法について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2e0c1f28-cc6c-4ecd-bb93-3816c4dd7cd3
ms.openlocfilehash: 295a4d754e0df015ba67daa9cf80d7df5b40199c
ms.sourcegitcommit: ffb9aa26cd5211dc6d96ebb42968d8357048880e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="exceptions-the-failwith-function"></a>例外: failwith 関数

`failwith`関数には、f# の例外が生成されます。


## <a name="syntax"></a>構文

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>コメント
*エラー メッセージ文字列*リテラル文字列または型の値は、前の構文で`string`です。 なったら、`Message`例外のプロパティです。

によって生成される例外`failwith`は、`System.Exception`名前を持つ参照である例外`Failure`f# コードでします。 次のコードの使用例`failwith`は例外をスローします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]
    
## <a name="see-also"></a>関連項目
[例外処理](index.md)

[例外の種類](exception-types.md)

[例外: `try...with` 式](the-try-with-expression.md)

[例外: `try...finally` 式](the-try-finally-expression.md)

[例外: `raise` 関数](the-raise-function.md)
