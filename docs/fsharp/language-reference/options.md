---
title: 选项
description: 了解如何使用F#选项时的实际值可能不存在为命名的值或变量的类型。
ms.date: 05/16/2016
ms.openlocfilehash: 6d32693bccc74c2cab642e4f626c9463092e8a39
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634097"
---
# <a name="options"></a>选项

中的选项类型F#的实际值可能不存在为命名的值或变量时使用。 选项有一个基础类型，并可以保存该类型的值或它可能不具有值。

## <a name="remarks"></a>备注

以下代码演示了一个函数，它生成的选项类型。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

您可以看到，如果输入`a`为大于 0，`Some(a)`生成。  否则为`None`生成。

值`None`选项不包含实际值时使用。 否则为该表达式`Some( ... )`为提供的选项值。 值`Some`并`None`可在模式匹配，如下面的函数中所示`exists`，它将返回`true`如果选项的值和`false`如果不是。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>使用选项

选项时，通常使用搜索未返回匹配的结果，如下面的代码中所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

在上面的代码列表是以递归方式搜索。 该函数`tryFindMatch`会将一个谓词函数`pred`，返回一个布尔值，以及要搜索的列表。 如果找到满足谓词的元素，则递归将结束并且该函数返回值作为表达式中的一个选项`Some(head)`。 递归过程结束时匹配空列表。 在该点的值`head`未找到，和`None`返回。

许多F#可能会或可能不存在返回的值在集合中搜索的库函数`option`类型。 按照约定，这些函数开头`try`前缀，例如， [ `Seq.tryFindIndex` ](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)。

值可能不存在，例如，它是否可以尝试构造值时，将引发异常时，选项也会有用。 下面的代码示例阐释了这一点。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

`openFile`上一示例中的函数具有类型`string -> File option`因为它将返回`File`对象如果成功打开该文件和`None`如果发生异常。 根据具体情况，可能不会捕获异常，而不是允许其传播一个适当的设计选择。

此外，就仍然可以将传递`null`或为 null 值`Some`事例的某个选项。 这通常是为了避免使用，并且通常在例程F#进行编程，但可能是由于在.NET 中的引用类型的特性。

## <a name="option-properties-and-methods"></a>选项属性和方法

选项类型支持以下属性和方法。

|属性或方法|类型|描述|
|------------------|----|-----------|
|[无](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|静态属性，可用于创建具有的选项值`None`值。|
|[IsNone](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|返回`true`如果该选项有`None`值。|
|[IsSome](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|返回`true`如果该选项有一个值，不是`None`。|
|[一些](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|创建一个选项的静态成员的值，则不`None`。|
|[值](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|返回基础值，则引发`System.NullReferenceException`如果值为`None`。|

## <a name="option-module"></a>Option 模块

将某个模块[选项](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c)，其中包含对选项执行操作的有用函数。 某些函数重复属性的功能，但可在上下文中需要一个函数的位置。 [Option.isSome](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79)并[Option.isNone](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819)是测试是否选项包含一个值，这两个模块函数。 [Option.get](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea)获取值，如果有的话。 如果不存在值，则会引发`System.ArgumentException`。

[Option.bind](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0)函数值，执行的函数，如果一个值。 该函数必须正好带一个参数，并且其参数类型必须是选项类型。 该函数的返回值是另一个选项类型。

Option 模块还包括可用于列表、 数组、 序列和其他集合类型的功能相对应的函数。 这些函数包括[ `Option.map` ](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622)， [ `Option.iter` ](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191)， [ `Option.forall` ](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428)， [ `Option.exists` ](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99)， [ `Option.foldBack` ](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb)， [ `Option.fold` ](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8)，和[ `Option.count` ](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876)。 使用这些功能，类似于零个或一个元素的集合使用的选项。 有关详细信息和示例，请参阅集合中的函数的讨论[列出了](lists.md)。

## <a name="converting-to-other-types"></a>将转换为其他类型

选项可以转换为列表或数组。 当一个选项，转换这些数据结构的任意一个时，生成的数据结构具有零个或一个元素。 若要将转换为数组的一个选项，请使用[ `Option.toArray` ](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64)。 若要将选项转换为列表，请使用[ `Option.toList` ](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1)。

## <a name="see-also"></a>请参阅

- [F# 语言参考](index.md)
- [F# 类型](fsharp-types.md)
