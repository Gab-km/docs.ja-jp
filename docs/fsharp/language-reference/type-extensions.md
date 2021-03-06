---
title: "型拡張 (F#)"
description: "F# 型の拡張機能が新しいメンバーの種類を追加する、定義済みのオブジェクトを許可する方法について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c9d7ce27-f5ad-4766-b9e9-34187da5bc24
ms.openlocfilehash: f78f8689e95fc1547f1a2b17c615592c00051f7c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="type-extensions"></a>型拡張

型拡張を使用すると、定義済みのオブジェクト型に新しいメンバーを追加できます。

## <a name="syntax"></a>構文

```fsharp
// Intrinsic extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]

// Optional extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]
```

## <a name="remarks"></a>コメント
型拡張には 2 つの形式があり、それぞれで構文と動作が若干異なります。 *固有拡張*は同じ名前空間またはモジュールで、同じソース ファイル、および同じアセンブリ (DLL または実行可能ファイル) に表示される、拡張対象の型とします。 *省略可能な拡張*拡張で元のモジュール、名前空間、または拡張する型をアセンブリの外側に表示されます。 リフレクションで型をチェックするときは、その型に対して固有拡張が使用されますが、任意拡張は使用されません。 任意拡張はモジュール内で使用する必要があり、拡張を含むモジュールが開いている場合のスコープ内でのみ使用できます。

前の構文で*typename*拡張されている型を表します。 アクセスできる型はいずれも拡張できますが、型の名前が、型略称ではなく、実際の型の名前である必要があります。 1 つの型拡張に複数のメンバーを定義できます。 *自己識別子*通常のメンバーと同様、呼び出されるオブジェクトのインスタンスを表します。

軽量構文では、`end` キーワードを省略できます。

型拡張で定義されたメンバーは、クラス型の他のメンバーと同じように使用できます。 他のメンバーと同様に、これらのメンバーは静的メンバーまたはインスタンス メンバーになることができます。 これらのメソッドとも呼ばれます*拡張メソッド*; プロパティと呼ばれます*拡張機能プロパティ*のようにします。 任意拡張のメンバーはコンパイルされると、静的メンバーになります。このメンバーに対する最初のパラメーターとして、オブジェクト インスタンスが暗黙で渡されます。 ただし、これらのメンバーは、宣言された方法に応じてインスタンス メンバーまたは静的メンバーと同じように動作します。 暗黙の拡張メンバーは型のメンバーとして含まれるため、無制限に使用できます。

拡張メソッドは、仮想メソッドまたは抽象メソッドになることができません。 拡張メソッドで同じ名前の他のメソッドをオーバーロードできますが、コンパイラは、あいまいな呼び出しの場合は非拡張メソッドを優先します。

1 つの型に対して複数の組み込み型拡張が存在する場合、すべてのメンバーが一意である必要があります。 オプション型拡張の場合は、1 つの型に対する複数の型拡張が存在する場合でも、各メンバーに同じ名前を付けることができます。 クライアント コードで同じメンバー名が定義されている 2 つの異なるスコープを開いている場合にのみ、あいまいさに対するエラーが発生します。

次の例では、モジュール内の型に対して組み込み型拡張を使用しています。 モジュールの外部のクライアント コードでは、型の通常のメンバーとまったく同様に型拡張が使用されます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3701.fs)]

組み込み型拡張を使用すると、型の定義を複数のセクションに分割できます。 この機能は、コンパイラが生成したコードとユーザーが作成したコードを別にしておく場合、複数のユーザーが作成したコードをグループ化する場合、複数の機能に関連付けられているコードをグループ化する場合など、大規模な型定義を管理する場合に便利です。

次の例では、オプション型拡張を使用して `System.Int32` 型を拡張し、`FromString` 拡張メソッドで静的メンバーの `Parse` を呼び出します。 `testFromString` メソッドで、新しいメンバーがインスタンス メンバーと同じように呼び出されているのがわかります。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3702.fs)]

IntelliSense で新しいインスタンス メンバーを `Int32` 型の他のメソッドと同じように使用できるのは、拡張を含むモジュールが開いている場合、または、拡張を含むモジュールは開いていないがスコープ内にある場合だけです。

## <a name="generic-extension-methods"></a>ジェネリック拡張メソッド
F# 3.1 で前に、f# コンパイラが (C#) の使用をサポートしていませんでした-ジェネリック型の変数、配列型、タプル型、または「この」パラメーターとして f# 関数型の拡張メソッドのスタイルを設定します。 F# 3.1 ではこれらの拡張メンバーの使用をサポートします。

たとえば、F# 3.1 コードでは、次の C# の構文に似ているシグネチャを使用する拡張メソッドを使用できます。

```csharp
static member Method<T>(this T input, T other)
```

この方法はジェネリック型パラメーターが制約される場合に特に役立ちます。 さらに、F# コードでこのような拡張メンバーを宣言し、追加の、意味的に豊富な一連の拡張メソッドを定義できます。 F# では、通常、次の例に示すように拡張メンバーを定義します。

```fsharp
open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq { for x in xs do for i in 1 .. n do yield x }
```

ただし、ジェネリック型の場合、型変数は、制約されない可能性があります。 この制限を回避するために、F# で C# スタイル拡張メンバーを宣言できます。 この種の宣言と F# のインライン機能を組み合わせると、拡張機能メンバーとしてジェネリックなアルゴリズムを示すことができます。

次の宣言を検討します。

```fsharp
[<Extension>]
type ExtraCSharpStyleExtensionMethodsInFSharp () =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

この宣言を使用すると、次の例のようなコードを記述できます。

```fsharp
let listOfIntegers = [ 1 .. 100 ]
let listOfBigIntegers = [ 1I to 100I ]
let sum1 = listOfIntegers.Sum()
let sum2 = listOfBigIntegers.Sum()
```

このコードでは、同じジェネリックな算術コードが単一の拡張メンバーを定義することによって、オーバーロードすることなく 2 種類のリストに適用されます。


## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[メンバー](members/index.md)
