---
title: 属性
description: 了解如何F#是表示与对象相关联的值的成员的属性。
ms.date: 05/16/2016
ms.openlocfilehash: bf605ee1135bd3b3561bde9a8ae66353497931b0
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675687"
---
# <a name="properties"></a>属性

*属性*是表示与对象相关联的值的成员。

## <a name="syntax"></a>语法

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a>备注

属性表示"具有"在面向对象的编程中，表示与对象实例，或对于静态属性，与类型相关联的数据的关系。

您可以声明两种方法，具体取决于是否想要显式指定 （也称为后备存储） 的基础值的属性，或如果想要允许编译器自动生成你的后备存储中的属性。 通常情况下，您应使用更明确的方式在该属性具有重要的实现和自动的方式，只需为值或变量的简单包装器属性时。 若要显式声明的属性，使用`member`关键字。 此声明性语法后跟指定的语法`get`并`set`方法，也称为*访问器*。 将各种形式的语法部分中所示的显式语法用于读/写和只读的只写属性。 对于只读属性，只需定义`get`方法; 因此，对于只写属性，定义仅`set`方法。 请注意，当属性同时具有`get`和`set`访问器中，替代语法，可指定属性和是不同的每个访问器，如下面的代码中所示的可访问性修饰符。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

对于读/写属性，同时具有`get`并`set`方法，则的顺序`get`和`set`可以反转。 或者，可以提供有关所示的语法`get`仅为所示的语法和`set`仅而不是使用组合的语法。 执行此操作可以更轻松地注释掉单个`get`或`set`方法时，如果这是你可能需要执行操作。 以下方法来使用组合的语法如以下代码所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

私有值属性的数据调用该保留*后备存储*。 若要让编译器自动创建的后备存储，请使用关键字`member val`，省略自我标识符，然后提供用于初始化该属性的表达式。 如果该属性是可变的包括`with get, set`。 例如，以下类类型包括两个自动实现的属性。 `Property1` 是只读的同时初始化为提供给主构造函数的参数和`Property2`是初始化为空字符串可设置属性：

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

自动实现的属性是一种类型，初始化的一部分，因此它们必须包含在任何其他成员定义之前就像`let`绑定和`do`类型定义中的绑定。 请注意在初始化时和每次访问该属性时不仅计算初始化自动实现的属性表达式。 此行为是属性的与显式实现的行为不同。 这实际上意味着，用于初始化这些属性的代码将添加到类的构造函数。 请考虑下面显示了这种差异的代码：

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
```

**输出**

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

上述代码的输出显示，AutoProperty 的值是不变时重复调用而 ExplicitProperty 更改每次调用它。 本示例演示自动实现属性的表达式不计算每个时间，是因为是显式的属性的 getter 方法。

>[!WARNING]
>有一些库，如实体框架 (`System.Data.Entity`)，可以在不很好地配合初始化自动实现的属性的基类构造函数中执行自定义操作。 在这些情况下，请尝试使用显式属性。

属性可以是类、 结构、 可区分的联合、 记录、 接口和类型扩展的成员，也可以在对象表达式中定义。

特性可以应用于属性。 若要将属性应用于属性，请在单独的行的属性前面写入属性。 有关更多信息，请参阅[特性](../attributes.md)。

默认情况下，属性是公共的。 可访问性修饰符还可以应用于属性。 若要应用可访问性修饰符，如果将其添加的属性名称之前它旨在应用于两个`get`和`set`方法; 将其之前添加`get`和`set`如果不同的可访问性是关键字所需的每个访问器。 *可访问性修饰符*可以是以下之一： `public`， `private`， `internal`。 有关详细信息，请参阅[访问控制](../access-control.md)。

每次访问属性时都会执行属性实现。

## <a name="static-and-instance-properties"></a>静态和实例属性

属性可以是静态或实例属性。 静态属性可以调用没有实例和用于与不具有单个对象的类型相关联的值。 对于静态属性，省略自我标识符。 对于实例属性需要自我标识符。

以下的静态属性定义基于一个方案使用的静态字段`myStaticValue`，它是属性的后备存储。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

属性也可以是数组一样，在这种情况下调用它们*索引属性*。 有关详细信息，请参阅[索引化属性](indexed-properties.md)。

## <a name="type-annotation-for-properties"></a>属性的类型批注

在许多情况下，编译器有足够的信息来推断从后备存储的类型属性的类型，但您可以通过添加类型注释来显式设置的类型。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>使用属性 set 访问器

您可以设置提供的属性`set`访问器使用`<-`运算符。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

输出是**20**。

## <a name="abstract-properties"></a>抽象属性

属性可以是抽象的。 与方法一样，`abstract`只是与属性关联的虚拟调度意味着。 抽象属性可以是真正抽象的也就是说，无需在同一个类中定义。 因此，包含此类属性的类是一个抽象类。 或者，抽象可能只是意味着一个属性是虚拟的并在这种情况下，定义必须位于同一个类。 请注意，抽象属性不能为私有，并且有一个访问器是抽象的其他必须也是抽象的。 有关抽象类的详细信息，请参阅[抽象类](../abstract-classes.md)。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>请参阅

- [成员](index.md)
- [方法](methods.md)
