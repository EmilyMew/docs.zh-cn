---
title: Byref
description: 了解有关 byref 和类似 byref 类型在F#，用于低级编程。
ms.date: 09/02/2018
ms.openlocfilehash: c0bad26672fbb9eb315eee1c3e275183ddeb9297
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59055360"
---
# <a name="byrefs"></a>Byref

F#有两个处理低级别编程的空间中的主要功能区域：

* `byref` / `inref` / `outref`类型，它们是托管的指针。 必须对使用情况的限制，以便不能编译的程序在运行时无效。
* 一个`byref`-如结构，即[结构](structures.md)具有类似语义和相同的编译时限制`byref<'T>`。 一个示例是<xref:System.Span%601>。

## <a name="syntax"></a>语法

```fsharp
// Byref types as parameters
let f (x: byref<'T>) = ()
let g (x: inref<'T>) = ()
let h (x: outref<'T>) = ()

// Calling a function with a byref parameter
let mutable x = 3
f &x

// Declaring a byref-like struct
open System.Runtime.CompilerServices

[<Struct; IsByRefLike>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

## <a name="byref-inref-and-outref"></a>Byref、 inref 和 outref

有三种形式的`byref`:

* `inref<'T>`用于读取的基础值的托管的指针。
* `outref<'T>`用于将写入的基础值的托管的指针。
* `byref<'T>`用于读取和写入的基础值的托管的指针。

一个`byref<'T>`可以在其中传递`inref<'T>`预期。 同样，`byref<'T>`可以在其中传递`outref<'T>`预期。

## <a name="using-byrefs"></a>使用 byref

若要使用`inref<'T>`，您需要先获取一个指针值与`&`:

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    
let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

若要使用写入指针`outref<'T>`或`byref<'T>`，你还必须对获取指向指针的值`mutable`。

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

如果你仅编写读取它，而是指针，请考虑使用`outref<'T>`而不是`byref<'T>`。

### <a name="inref-semantics"></a>Inref 语义

考虑下列代码：

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

在语义上，这意味着以下内容：

* 持有者`x`指针只能使用它来读取值。
* 获取到的任何指针`struct`字段中嵌套`SomeStruct`给定类型`inref<_>`。

以下也是如此：

* 没有任何含义的其他线程或别名不具有写访问权限`x`。
* 没有任何含义，`SomeStruct`是固定不变，凭借`x`正在`inref`。

但是，对于F#的值类型**都**不可变的`this`指针将被推断`inref`。

所有这些规则组合在一起表示的持有者`inref`指针不能修改所指向的内存的直接内容。

### <a name="outref-semantics"></a>Outref 语义

用途`outref<'T>`是指示指针应仅在从读取。 意外，`outref<'T>`允许读取基础值，尽管其名称。 这是为了实现兼容性。 在语义上，`outref<'T>`没有什么不同`byref<'T>`。

### <a name="interop-with-c"></a>与 C 进行互操作\#

C# 支持`in ref`并`out ref`关键字，除了`ref`返回。 下表显示了如何F#解释什么C#发出：

|C# 构造|F#推断|
|------------|---------|
|`ref` 返回值|`outref<'T>`|
|`ref readonly` 返回值|`inref<'T>`|
|`in ref` 参数|`inref<'T>`|
|`out ref` 参数|`outref<'T>`|

下表显示了什么F#发出：

|F#构造|发出的构造|
|------------|-----------------|
|`inref<'T>` argument（参数）|`[In]` 在参数上的属性|
|`inref<'T>` return|`modreq` 属性值|
|`inref<'T>` 在抽象槽或实现|`modreq` 在自变量或返回|
|`outref<'T>` argument（参数）|`[Out]` 在参数上的属性|

### <a name="type-inference-and-overloading-rules"></a>类型推理和重载规则

`inref<'T>`推断类型F#编译器在以下情况下：

1. .NET 参数或返回类型具有`IsReadOnly`属性。
2. `this`没有可变字段的结构类型的指针。
3. 内存位置的地址派生自另一个`inref<_>`指针。

时隐式的地址`inref`被采用，用类型自变量的重载`SomeType`优于使用类型的自变量的重载`inref<SomeType>`。 例如：

```fsharp
type C() =
    static member M(x: System.DateTime) = x.AddDays(1.0)
    static member M(x: inref<System.DateTime>) = x.AddDays(2.0)
    static member M2(x: System.DateTime, y: int) = x.AddDays(1.0)
    static member M2(x: inref<System.DateTime>, y: int) = x.AddDays(2.0)

let res = System.DateTime.Now
let v =  C.M(res)
let v2 =  C.M2(res, 4)
```

在这两种情况下，重载采用`System.DateTime`而不是重载采用解决`inref<System.DateTime>`。

## <a name="byref-like-structs"></a>Byref 类似结构

除了`byref` / `inref` / `outref`三个，你可以定义自己的结构，可以遵循`byref`-等语义。 此操作通过 <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> 属性实现：

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` 并不意味着`Struct`。 必须同时出现在类型上。

一个"`byref`-如"结构中的F#是绑定堆栈的值类型。 它永远不会分配托管堆上。 一个`byref`-像结构可用于高效的编程中，因为它强制实施强检查有关生存期和非捕获组。 中的规则：

* 它们可用作函数参数、 方法参数、 局部变量、 方法返回。
* 它们不能是静态或实例的类或常规结构的成员。
* 不能通过任何闭包构造捕获它们 (`async`方法或 lambda 表达式)。
* 它们不能用作泛型参数。

最后这一点非常重要的F#管道样式编程中，作为`|>`是对其输入的类型进行参数化的泛型函数。 可能的放宽此限制`|>`将来，因为它是内联的不会不调用任何非内联泛型函数在其主体中。

尽管这些规则非常强限制使用，但它们这样做是为了满足这一承诺的高性能计算以安全方式。

## <a name="byref-returns"></a>Byref 返回

Byref 返回从F#函数或成员可以产生和使用。 使用时`byref`-返回方法，则这是隐式取消引用。 例如：

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

若要避免隐式取消引用，例如传递一个引用多个链接的调用，通过使用`&x`(其中`x`是值)。

您可以直接将分配给返回`byref`。 请考虑以下 （高度命令性） 程序：

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override __.ToString() = String.Join(' ', nums)

    member __.FindLargestSmallerThan(target: int) =
        let mutable ctr = nums.Length - 1

        while ctr > 0 && nums.[ctr] >= target do ctr <- ctr - 1

        if ctr > 0 then &nums.[ctr] else &nums.[0]

[<EntryPoint>]
let main argv =
    let c = C()
    printfn "Original sequence: %s" (c.ToString())

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn "New sequence:      %s" (c.ToString())

    0 // return an integer exit code
```

以下是输出：

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a>范围，将 byref

一个`let`-绑定的值不能具有超过在其中定义的作用域的引用。 例如，以下是不允许：

```fsharp
let test2 () =
    let x = 12
    &x // Error: 'x' exceeds its defined scope!

let test () =
    let x =
        let y = 1
        &y // Error: `y` exceeds its defined scope!
    ()
```

这会阻止您获取具体取决于不同的结果，如果使用打开或关闭优化进行编译。
