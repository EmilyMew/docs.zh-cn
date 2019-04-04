---
title: Null 值
description: 了解如何在中使用 null 值F#编程语言。
ms.date: 03/22/2019
ms.openlocfilehash: 93ac48eddf36981b9df550e76405c3175ae92e0a
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409635"
---
# <a name="null-values"></a>Null 值

本主题介绍如何在中使用 null 值F#。

## <a name="null-value"></a>Null 值

Null 值通常不使用在F#的值或变量。 但是，null 将显示异常值在某些情况下。 如果类型在定义F#，null 不允许作为常规的值，除非[AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f)特性应用于类型。 如果某些其他.NET 语言中定义了一个类型，null 是一个可能的值，并进行互操作与此类类型时在F#代码可能会遇到 null 值。

中定义的类型为F#和使用严格地根据F#，只能创建一个 null 值使用F#库直接将使用[Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977)或[Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)。 但是，对于F#类型用于从其他.NET 语言，或者如果正在使用一个 API，编写时未使用该类型F#，如.NET Framework 中，可以出现 null 值。

可以使用`option`中键入F#时可能会使用引用变量与另一种.NET 语言中可能的 null 值。 而不是 null，与F#`option`类型，使用该选项的值`None`如果没有对象。 使用选项值`Some(obj)`与对象`obj`对象时。 有关详细信息，请参阅[选项](../options.md)。 请注意，仍能够打包`null`成选项值如果为`Some x`，`x`恰好是`null`。 因此，务必使用`None`值时`null`。

`null`关键字是中的有效关键字F#语言中，并且你必须使用.NET Framework Api 或其他用其他.NET 语言编写的 Api 时使用它。 两种情况中，您可能需要一个 null 值是和解释的返回值或输出参数从.NET 方法调用时调用.NET API 和作为参数传递 null 值。

要将 null 值传递给.NET 方法，只需使用`null`调用代码中的关键字。 下面的代码示例阐释了这一点。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

若要解释从.NET 方法获取一个 null 值，使用模式匹配，如果你知道如何操作。 下面的代码示例演示如何使用模式匹配来解释从返回的 null 值`ReadLine`当其尝试读取超出输入流的末尾。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

为空值F#还可以在其他方面，例如在使用生成类型`Array.zeroCreate`，它调用`Unchecked.defaultof`。 您必须要注意此类的代码来跟封装的 null 值。 仅适用于库中F#，不需要检查每个函数中的 null 值。 如果你正在编写用于与其他.NET 语言的互操作的库，您可能需要添加 null 检查输入参数，并引发`ArgumentNullException`，就像您在 C# 或 Visual Basic 代码中执行操作。

下面的代码可用于检查任意值是否为 null。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>请参阅

- [值](index.md)
- [match 表达式](../match-expressions.md)
