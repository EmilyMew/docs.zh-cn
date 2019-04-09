---
title: Visual Basic 中的数组
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
ms.openlocfilehash: 6b131d073e10f99feaf770fe5fd3c393551fa5a3
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675960"
---
# <a name="arrays-in-visual-basic"></a>Visual Basic 中的数组

数组是一组值，术语上称之为*元素*，逻辑上彼此相关的。 例如，数组可能包含的语法学校; 中的每个年级的学生数量数组的每个元素是单个年级的学生数量。 同样，数组可能包含的一个类; 的学生的成绩数组的每个元素是一个单一的等级。

它是可能的各个变量来存储每个数据项。 例如，如果我们的应用程序分析学生成绩，我们可以使用一个单独的变量的每个学生的等级，如`englishGrade1`， `englishGrade2`，等等。此方法具有三个主要的限制：

- 我们必须知道在设计时我们需要处理完全数目的成绩。
- 快速处理大量的成绩变得难以处理。 反过来，这使得应用程序更有可能有严重的 bug。
- 很难维护。 我们添加的每个新级别要求应用程序进行修改、 重新编译和重新部署。

通过使用一个数组，可以通过相同的名称，请参阅这些相关的值并使用一个数字，称为*索引*或*下标*用于标识各个元素根据其数组中的位置。 数组范围从 0 到数组中元素的总数减 1 所得的索引。 当您使用 Visual Basic 语法来定义数组的大小时，指定其最高的索引，不在数组中元素的总数。 您可以使用数组作为一个单元，并循环访问其元素的功能使您无需了解它包含在设计时完全多少个元素。

在进行说明之前，请看几个简单的示例：

```vb
' Declare a single-dimension array of 5 numbers.
Dim numbers(4) As Integer

'Declare a single-dimension array and set its 4 values.
Dim numbers = New Integer() {1, 2, 4, 8}

' Change the size of an existing array to 16 elements and retain the current values.
ReDim Preserve numbers(15)

' Redefine the size of an existing array and reset the values.
ReDim numbers(15)

' Declare a 6 x 6 multidimensional array.
Dim matrix(5, 5) As Double

' Declare a 4 x 3 multidimensional array and set array element values.
Dim matrix = New Integer(3, 2) {{1, 2, 3}, {2, 3, 4}, {3, 4, 5}, {4, 5, 6}}

' Declare a jagged array
Dim sales()() As Double = New Double(11)() {}
```

## <a name="array-elements-in-a-simple-array"></a>简单数组中的数组元素

让我们创建一个名为数组`students`存储语法学校中每个年级的学生数量。 这些元素的索引范围为 0 到 6。 使用此数组是比声明七个变量更简单。

下图显示`students`数组。 对于数组的每个元素：

- 元素索引表示年级（索引 0 表示幼儿园）。

- 元素中包含的值表示每个年级的学生数量。

![显示学生人数的数组的关系图](./media/index/students-array-elements.gif)

下面的示例包含用于创建和使用数组的 Visual Basic 代码：

[!code-vb[simple-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]

该示例执行三项操作：

- 它声明了`students`具有七个元素的数组。 数`6`声明数组中表示数组中的最后一个索引; 它是一个小于数组中的元素数。
- 它将值分配给数组中的每个元素。 通过使用数组名称并在括号中包含单个元素的索引访问数组元素。
- 它列出了数组的每个值。 该示例使用[ `For` ](../../../language-reference/statements/for-next-statement.md)语句来访问数组的每个元素按索引号。

`students`前面的示例中的数组是一维数组，因为它使用一个索引。 使用多个索引或下标的数组称为*多维*。 有关详细信息，请参阅本文的其余部分和[在 Visual Basic 中的数组维数](../../language-features/arrays/array-dimensions.md)。

## <a name="creating-an-array"></a>创建数组

以下几种方式，可以定义数组的大小：

- 当声明数组时，可以指定大小：

  [!code-vb[creating1](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]

- 可以使用`New`子句提供数组大小，在创建时：

  [!code-vb[creating2](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]

如果具有现有数组，您可以通过使用来重新定义其大小[ `ReDim` ](../../../language-reference/statements/redim-statement.md)语句。 您可以指定`ReDim`语句保留数组中的值，也可以指定它创建一个空数组。 下面的示例演示了用 `ReDim` 语句来修改现有数组的大小的不同用法。

[!code-vb[redimensioning](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]

有关详细信息，请参阅[ReDim 语句](../../../language-reference/statements/redim-statement.md)。

## <a name="storing-values-in-an-array"></a>将值存储在数组

你可以通过使用类型 `Integer`的索引访问数组中的每个位置。 你可以使用括号内的索引来引用每个数组位置，从而存储和检索数组中的值。 对于多维数组的索引用逗号 （，） 分隔。 每个数组维度都需要一个索引。

下面的示例演示用于存储和检索值在数组中的一些语句。

[!code-vb[store-and-retrieve](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]

## <a name="populating-an-array-with-array-literals"></a>使用数组文本填充数组

通过使用数组文本，可以创建它时填充具有一组初始的值的数组。 数组文本包含用逗号分隔的值列表，这些值被括在括号内 (`{}`)。

通过使用数组文本创建数组时，可以提供数组类型或使用类型推理功能来确定数组类型。 下面的示例显示了这两个选项。

[!code-vb[create-with-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]

使用类型推理时，该数组的类型由*基准类型*中的文本值列表。 基准类型是数组中的所有其他类型可以扩大到的类型。 如果无法确定此唯一类型，基准类型是数组中所有其他类型可以缩小到的唯一类型。 如果无法确定为这两种唯一类型之一，则基准类型是 `Object`。 例如，如果提供给数组文本的值的列表包含 `Integer`、 `Long`和 `Double`类型的值，则生成的数组类型是 `Double`。 因为`Integer`并`Long`仅扩大到`Double`，`Double`是基准类型。 有关详细信息，请参阅 [Widening and Narrowing Conversions](../../language-features/data-types/widening-and-narrowing-conversions.md)。

> [!NOTE]
> 仅对定义为本地变量的类型成员的数组，可以使用类型推理。 如果缺少显式类型定义，则数组使用数组文本在类级别定义的类型是`Object[]`。 有关详细信息，请参阅[局部类型推理](../variables/local-type-inference.md)。

请注意，上面的示例定义`values`作为类型的数组`Double`即使所有数组文本都属于类型`Integer`。 您可以创建此数组，因为数组文本中的值可以扩大到`Double`值。

此外可以创建并使用填充多维数组*嵌套数组文本*。 嵌套的数组文本必须具有与生成的数组保持一致维度的数。 下面的示例使用嵌套的数组文本创建一个二维整数的数组。

[!code-vb[nested-array-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]

在使用嵌套的数组文本创建并填充数组，如果嵌套的数组文本中的元素数不匹配，就会出错。 如果显式声明数组变量具有不同数量的维度比数组文本，也会发生错误。

正如您可以对一维数组，可以使用嵌套的数组文本创建多维数组时依赖类型推断。 推断出的类型是所有的嵌套级别的所有数组文本中的所有值的基准类型。 下面的示例创建类型的一个二维数组`Double[,]`属于类型的值从`Integer`和`Double`。

[!code-vb[nested-type-inference](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]

有关其他示例，请参阅[如何：初始化数组变量在 Visual Basic 中的](../../language-features/arrays/how-to-initialize-an-array-variable.md)。

## <a name="iterating-through-an-array"></a>循环访问数组

当循环访问数组时，访问数组中的每个元素，从最低到最高或从最高到低的顺序。 通常情况下，使用两种[为...下一条语句](../../../language-reference/statements/for-next-statement.md)或[为每个...下一条语句](../../../language-reference/statements/for-each-next-statement.md)循环访问数组的元素。 如果不知道数组的上限，您可以调用<xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType>方法以获取索引的最高的值。 尽管最小索引值是几乎始终为 0，可以调用<xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType>方法以获取索引的最小值。

下面的示例循环访问一维数组，通过使用[ `For...Next` ](../../../language-reference/statements/for-next-statement.md)语句。

[!code-vb[iterate-one-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]

下面的示例循环访问通过使用多维数组[ `For...Next` ](../../../language-reference/statements/for-next-statement.md)语句。 <xref:System.Array.GetUpperBound%2A> 方法具有用于指定维度的参数。 `GetUpperBound(0)` 返回的最高的第一个维的索引和`GetUpperBound(1)`返回第二个维度的最高的索引。

[!code-vb[iterate-two-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]

下面的示例使用[为每个...下一条语句](../../../language-reference/statements/for-each-next-statement.md)循环访问一个一维数组和一个二维数组。

[!code-vb[iterate-for-each-next](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]

## <a name="array-size"></a>数组大小

数组的大小是数组所有维度的长度的产物。 它表示数组中当前所包含的元素总数。  例如，下面的示例声明包含每个维度中的四个元素的二维数组。 如示例输出所示，该数组的大小为 16 (或 (3 + 1) * (3 + 1)。

[!code-vb[array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]

> [!NOTE]
> 数组大小的这一讨论不适用于交错数组。 交错的数组并确定交错数组的大小的信息，请参阅[交错数组](#jagged-arrays)部分。

可以通过使用 <xref:System.Array.Length%2A?displayProperty=nameWithType> 属性查找数组大小。 你可以通过使用查找多维数组中的每个维的长度<xref:System.Array.GetLength%2A?displayProperty=nameWithType>方法。

通过将分配给它一个新数组对象，或可以调整大小的数组变量[`ReDim`语句](../../../language-reference/statements/redim-statement.md)语句。 下面的示例使用`ReDim`语句更改为 51 元素数组的一个 100 元素的数组。

[!code-vb[resize-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]

当处理数组大小时，需要记住几件事情。

|||
|---|---|
|维度长度|每个维度的索引是基于 0 的这意味着其范围为 0 到其上限之间。 因此，给定维度的长度为一个大于该维度的声明的上限。|
|长度限制|每一维数组的长度限制为的最大值`Integer`数据类型，即<xref:System.Int32.MaxValue?displayProperty=nameWithType>或 (2 ^31)-1。 但是，数组的总大小还受到系统上可用的内存限制。 如果尝试初始化数组超出可用内存量，则运行时会引发<xref:System.OutOfMemoryException>。|
|大小和元素大小|数组的大小独立于其元素的数据类型。 大小始终表示元素 （不所占用的内存的字节数） 的总数。|
|内存消耗|做出关于数组如何存储在内存中的假设是不可靠的。 由于不同数据宽度的平台上的存储会有所变化，因此同一数组在 64 位系统上可以占用比在 32 位系统上更多的内存。 具体取决于数组初始化时的系统配置，公共语言运行时 (CLR) 可以尽可能地将存储分配到靠近包元素的地方，或者将它们全部在自然硬件边界上对齐。 此外，数组需要存储开销的控制信息，而且每添加一个维度，这种开销随之增加。|

## <a name="the-array-type"></a>数组类型

每个数组具有不同于它的元素的数据类型的数据类型。 没有一种数据类型能用于所有数组。 相反，数组的数据类型由数组的维度数量或 *“排名”*，以及数组中元素的数据类型确定。 两个数组变量属于相同的数据，仅当它们具有相同的排名并且其元素具有相同的数据类型。 数组的维度的长度不会影响数组数据类型。

每个数组都继承自 <xref:System.Array?displayProperty=nameWithType> 类，并且你可以声明一个类型为 `Array` 的变量，但不能创建一个类型为 `Array` 的数组。 例如，虽然下面的代码声明`arr`变量的类型为`Array`，并调用<xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>方法可实例化的数组，该数组类型的事实证明，Object []。

[!code-vb[array-class](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)]

此外，[ReDim 语句](../../../language-reference/statements/redim-statement.md)无法对声明为类型 `Array` 的变量执行运算。 出于这些原因，以及为类型安全，则最好声明为特定类型的每个数组。

你可以通过几种方式了解到数组及其元素的数据类型。

- 您可以调用<xref:System.Object.GetType%2A>方法以获取对变量<xref:System.Type>表示变量的运行时类型的对象。 <xref:System.Type> 对象可在其属性和方法中保存大量信息。
- 您可以将该变量传递到<xref:Microsoft.VisualBasic.Information.TypeName%2A>函数以获取`String`与运行时类型的名称。

下面的示例调用两`GetType`方法和`TypeName`函数来确定数组的类型。 数组类型是`Byte(,)`。 请注意，<xref:System.Type.BaseType%2A?displayProperty=nameWithType>属性还指示字节数组的基类型是<xref:System.Array>类。

[!code-vb[array-type](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]

## <a name="arrays-as-return-values-and-parameters"></a>作为返回值和参数的数组

若要通过 `Function` 过程返回数组，请将数组数据类型和维度数指定为 [Function 语句](../../../language-reference/statements/function-statement.md)的返回类型。 在函数内，声明一个具有相同数据类型和维度数的本地数组变量。 在 [Return 语句](../../../language-reference/statements/return-statement.md)中，添加不带括号的局部数组变量。

若要将作为参数的数组指定到 `Sub` 或 `Function` 步骤中，可将此参数定义为具有指定数据类型和维度数量的数组。 在过程调用中，将传递一个数组变量具有相同的数据类型和维度数。

在以下示例中，`GetNumbers`函数返回`Integer()`，类型的一维数组`Integer`。 `ShowNumbers` 过程接受 `Integer()` 参数。

[!code-vb[return-value-and-params](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]

在以下示例中，`GetNumbersMultiDim`函数返回`Integer(,)`，类型的二维数组`Integer`。  `ShowNumbersMultiDim` 过程接受 `Integer(,)` 参数。

[!code-vb[multidimensional-return-value](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]

## <a name="jagged-arrays"></a>交错数组

有时应用程序中的数据结构是二维而不是矩形。 例如，可能会使用数组来存储有关每一天的月份的高温度数据。 数组的第一个维度表示月份，但第二个维度表示的天数，并在一个月的天数不均匀。 一个*交错的数组*，这也称为*数组的数组*，专为此类方案。 交错的数组是一个数组，其元素也是数组。 交错数组和交错数组中的每个元素都可以具有一个或多个维度。

以下示例使用月份数组，其中每个元素是天数数组。 该示例使用交错的数组，因为不同月份有不同的天数。  示例演示如何创建交错的数组，将值分配给它，并检索和显示它的值。

[!code-vb[jagged-arrays](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]

前面的示例通过将值分配给交错数组元素的元素按`For...Next`循环。 通过使用嵌套的数组文本，还可以将值分配到交错数组的元素。 但是，尝试使用嵌套数组文本 (例如， `Dim valuesjagged = {{1, 2}, {2, 3, 4}}`) 会生成编译器错误[BC30568](../../../,,/../misc/bc30568.md)。 若要更正此错误，请用括号括起来将内部数组文本。 圆括号会强制进行计算的数组文本表达式和生成的值用于外部数组文本，如以下示例所示。

[!code-vb[jagged-array-initialization](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)]

交错的数组是一维数组，其元素包含的数组。 因此，<xref:System.Array.Length%2A?displayProperty=nameWithType>属性和`Array.GetLength(0)`方法返回的元素数中的一维数组，并`Array.GetLength(1)`引发<xref:System.IndexOutOfRangeException>因为交错的数组不是多维。 检索的每个子数组的值来确定每个子数组中的元素数<xref:System.Array.Length%2A?displayProperty=nameWithType>属性。 下面的示例说明了如何确定交错数组中的元素数。

[!code-vb[jagged-array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)]

## <a name="zero-length-arrays"></a>零长度数组

Visual Basic 区分未初始化的数组 (其值是一个数组`Nothing`) 和一个*零长度数组*或空数组 （不包含任何元素的数组。）未初始化的数组是不确定维度或向其分配任何值。 例如：

```vb
Dim arr() As String
```

声明为-1 维的长度为零的数组。 例如：

```vb
Dim arrZ(-1) As String
```

在下列情况下，你可能需要创建一个零长度数组：

- 不会有风险的情况下<xref:System.NullReferenceException>异常，你的代码必须访问的成员<xref:System.Array>类，如<xref:System.Array.Length%2A>或<xref:System.Array.Rank%2A>，或调用 Visual Basic 函数，例如<xref:Microsoft.VisualBasic.Information.UBound%2A>。

- 你想要保留您的代码，而不必检查简单`Nothing`作为一种特殊情况。

- 你的代码与应用程序编程接口 (API) 交互，该接口要求你将一个零长度数组传递到一个或多个过程，或将一个零长度数组返回到一个或多个过程。

## <a name="splitting-an-array"></a>拆分数组

在某些情况下，可能需要拆分为多个数组的单个数组。 这涉及到确定的点或点的数组将被拆分，并为两个或多个单独的数组，然后快速数组。

> [!NOTE]
> 本部分不讨论如何将单个字符串拆分为基于某些分隔符的字符串数组。 有关将字符串拆分的信息，请参阅<xref:System.String.Split%2A?displayProperty=nameWithType>方法。

用于拆分数组的最常见条件是：

- 数组中的元素数。 例如，您可能想要为多个相等部分大约拆分数超过了指定的元素的数组。 为此，可以使用通过以下任一方法返回的值<xref:System.Array.Length%2A?displayProperty=nameWithType>或<xref:System.Array.GetLength%2A?displayProperty=nameWithType>方法。

- 用作分隔符，该值指示应在何处拆分数组的元素的值。 您可以通过调用来搜索特定值<xref:System.Array.FindIndex%2A?displayProperty=nameWithType>和<xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType>方法。

一旦确定了应在其中拆分数组的索引，然后可以通过调用创建个人数组<xref:System.Array.Copy%2A?displayProperty=nameWithType>方法。

下面的示例将数组拆分成两个数组大小大致相等。 （如果数组元素的总数为奇数，第一个数组具有多个元素的第二个。）

[!code-vb[splitting-an-array-by-length](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)]

下面的示例将一个字符串数组拆分成两个数组根据其值为"zzz"，可作为数组分隔符的元素存在。 新数组不包括包含分隔符的元素。

[!code-vb[splitting-an-array-by-delimiter](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)]

## <a name="joining-arrays"></a>加入数组

此外可以组合多个数组合并为一个更大数组。 若要执行此操作，还使用<xref:System.Array.Copy%2A?displayProperty=nameWithType>方法。

> [!NOTE]
> 本部分不讨论联接成单个字符串的字符串数组。 有关联接的字符串数组的信息，请参阅<xref:System.String.Join%2A?displayProperty=nameWithType>方法。

然后再将每个数组的元素复制到新数组，您首先必须确保，这样就足够大以容纳新的数组初始化数组。 可以通过两种方法执行此操作：

- 使用[ `ReDim Preserve` ](../../../language-reference/statements/redim-statement.md)语句，以便动态地将新元素添加到它之前展开数组。 这是最简单的技术，但它可能会导致性能下降并占用过多内存时要复制大型数组。
- 计算所需的新的大型数组的元素的总数，然后将每个源数组的元素添加到它。

以下示例使用第二种方法将具有 10 个元素的四个数组添加到单个数组。

[!code-vb[joining-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)]

因为在这种情况下源数组也是所有小型，我们还可以动态地可以展开数组，我们将每个新数组的元素添加到它。 以下示例执行该操作。

[!code-vb[joining-an-array-dynamically](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)]

## <a name="collections-as-an-alternative-to-arrays"></a>作为数组的替代方法的集合

数组最适用于创建和使用固定数量的强类型化对象。 集合提供更灵活的方式来使用对象组。 与数组不同，这需要明确地更改与数组的大小[`ReDim`语句](../../../language-reference/statements/redim-statement.md)，集合增加和减少动态随着需求的应用程序更改。

当你使用`ReDim`来重新设置其维数的数组，Visual Basic 创建一个新数组，并释放上一个。 这需要执行时间。 因此，如果你正在使用频繁变化，或者您的项目数不能预测所需的最大项数，您通常将使用集合来获得更好的性能。

对于某些集合，你可以为放入集合中的任何对象分配一个密钥，这样你便可以使用该密钥快速检索此对象。

如果你的集合中只包含一种数据类型的元素，你可以使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空间中的一个类。 泛型集合强制类型安全，因此无法向其添加任何其他数据类型。

有关集合的详细信息，请参阅[集合](../../concepts/collections.md)。

## <a name="related-topics"></a>相关主题

|术语|定义|
|----------|----------------|
|[Array Dimensions in Visual Basic](../../language-features/arrays/array-dimensions.md)|在数组中解释级别和维度。|
|[如何：初始化数组变量在 Visual Basic 中](../../language-features/arrays/how-to-initialize-an-array-variable.md)|说明如何用初始值填充数组。|
|[如何：在 Visual Basic 中的对数组进行排序](../../language-features/arrays/how-to-sort-an-array.md)|显示如何按字母先后顺序对数组元素进行排序。|
|[如何：将一个数组赋给另一个数组](../../language-features/arrays/how-to-assign-one-array-to-another-array.md)|说明将数组分配到另一个数组变量的规则和步骤。|
|[数组疑难解答](../../language-features/arrays/troubleshooting-arrays.md)|讨论在使用数组时出现的一些常见问题。|

## <a name="see-also"></a>请参阅

- <xref:System.Array?displayProperty=nameWithType>
- [Dim 语句](../../../language-reference/statements/dim-statement.md)
- [ReDim 语句](../../../language-reference/statements/redim-statement.md)
