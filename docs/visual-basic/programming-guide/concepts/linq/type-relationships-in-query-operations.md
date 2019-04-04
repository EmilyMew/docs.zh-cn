---
title: 查询操作中的类型关系 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: fd2bcfad0ae24288887500ae6286e6ac73fddac5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822331"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>查询操作中的类型关系 (Visual Basic)
中使用的变量[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]查询操作为强类型，必须相互兼容。 数据源中、 查询本身，以及在查询执行过程中，使用强类型化。 下图标识术语用于描述[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查询。 有关查询的部分的详细信息，请参阅[基本查询操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)。  
  
 ![显示与突出显示的元素的伪代码查询屏幕截图。](./media/type-relationships-in-query-operations/linq-query-description-terms.png)  
  
 在查询中范围变量的类型必须与数据源中的元素的类型兼容。 查询变量的类型必须与在中定义的序列元素兼容`Select`子句。 最后，序列元素的类型还必须与兼容的类型中使用循环控制变量`For Each`执行查询的语句。 此强类型化便于在编译时识别类型错误。  
  
 Visual Basic 使强类型方便通过也称为实现局部类型推理*隐式类型化*。 在上一示例中，使用功能，您将看到在所有[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]示例和文档。 在 Visual Basic 中，局部类型推理是只需通过实现`Dim`语句不带`As`子句。 在以下示例中，`city`强类型化为字符串。  
  
 [!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]  
  
> [!NOTE]
>  局部类型推理时才起作用`Option Infer`设置为`On`。 有关详细信息，请参阅[Option Infer 语句](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。  
  
 但是，即使在查询中使用局部类型推理，是在数据源中的变量、 查询变量和查询执行循环之间存在相同的类型关系。 最好在编写时已基本了解对这些类型关系[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查询或使用的示例和文档中的代码示例。  
  
 您可能需要指定显式类型从数据源返回的类型不匹配的范围变量。 可以通过使用指定的范围变量的类型`As`子句。 但是，这会导致错误如果转换[收缩转换](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)并`Option Strict`设置为`On`。 因此，我们建议在从数据源检索的值上执行转换。 您可以将值转换从数据源为显式的范围变量类型使用<xref:System.Linq.Enumerable.Cast%2A>方法。 此外可以强制转换中所选值`Select`范围变量的类型不同的显式类型的子句。 在下面的代码说明了这些点。  
  
 [!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>返回源数据的整个元素的查询  
 下面的示例演示[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查询返回的源数据中的选定元素的序列的操作。 源`names`，包含数组的字符串，并将查询输出是包含以字母 M 开头的字符串序列。  
  
 [!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]  
  
 这等效于下面的代码，但它更简短、 更轻松地编写。 依赖于在查询中的局部类型推理是在 Visual Basic 中的首选的样式。  
  
 [!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]  
  
 以下关系存在于这两个前面的代码示例，是否隐式或显式确定类型。  
  
1.  数据源中的元素的类型`names`，是范围变量的类型`name`，在查询中。  
  
2.  选择后，该对象的类型`name`，确定查询变量的类型`mNames`。 此处`name`是一个字符串，因此查询变量是在 Visual Basic 中的 IEnumerable (Of String)。  
  
3.  中定义的查询`mNames`中执行`For Each`循环。 循环将循环执行查询的结果。 因为`mNames`，在执行时将返回一个字符串，循环迭代变量序列`nm`，也是一个字符串。  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>返回从所选元素的一个字段的查询  
 下面的示例演示[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]查询返回的序列包含仅选择数据源中的每个元素的一部分的操作。 查询采用一系列`Customer`对象作为其数据源，并仅适用于项目`Name`结果中的属性。 客户名称是一个字符串，因为查询将生成一个字符串序列作为输出。  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim custNames = From cust In customers   
                Where cust.City = "London"   
                Select cust.Name  
  
For Each custName In custNames  
    Console.WriteLine(custName)  
Next  
```  
  
 变量之间的关系是类似于更简单的示例中。  
  
1.  数据源中的元素的类型`customers`，是范围变量的类型`cust`，在查询中。 在此示例中，类型为`Customer`。  
  
2.  `Select`语句返回`Name`每个属性`Customer`对象而不是整个对象。 因为`Name`是一个字符串，查询变量`custNames`，再次将 IEnumerable (Of String)，不属于`Customer`。  
  
3.  因为`custNames`表示一个字符串，序列`For Each`循环的迭代变量`custName`，必须为字符串。  
  
 而无需本地类型推断，前面的示例将很难编写和理解，如以下示例所示。  
  
```vb  
' Method GetTable returns a table of Customer objects.  
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()  
 Dim custNames As IEnumerable(Of String) =  
     From cust As Customer In customers   
     Where cust.City = "London"   
     Select cust.Name  
  
 For Each custName As String In custNames  
     Console.WriteLine(custName)  
 Next  
```  
  
## <a name="queries-that-require-anonymous-types"></a>需要匿名类型的查询  
 下面的示例显示了更复杂的情况。 在上一示例中，不便于显式指定所有变量的类型。 在此示例中，是不可能。 而不是选择整个`Customer`数据源或从每个元素的单个字段中的元素`Select`子句在此查询将返回两个属性的原始`Customer`对象：`Name`和`City`。 在响应`Select`子句中，编译器会定义包含这两个属性的匿名类型。 执行的结果`nameCityQuery`在`For Each`循环是一系列新的匿名类型的实例。 因为匿名类型具有没有可用的名称，不能指定的类型`nameCityQuery`或`custInfo`显式。 也就是说，与匿名类型，有没有类型名称来代替`String`在`IEnumerable(Of String)`。 有关详细信息，请参阅[匿名类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim nameCityQuery = From cust In customers   
                    Where cust.City = "London"   
                    Select cust.Name, cust.City  
  
For Each custInfo In nameCityQuery  
    Console.WriteLine(custInfo.Name)  
Next  
```  
  
 尽管不能为指定类型的变量上一示例中，关系保持不变。  
  
1.  数据源中的元素的类型同样是在查询中范围变量的类型。 在此示例中，`cust`的一个实例`Customer`。  
  
2.  因为`Select`语句生成匿名类型，查询变量`nameCityQuery`，必须为匿名类型隐式类型。 匿名类型没有可用的名称，并因此不能显式指定。  
  
3.  中的迭代变量的类型`For Each`循环是在步骤 2 中创建的匿名类型。 该类型具有没有可用的名称，因为必须隐式确定循环迭代变量的类型。  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的 LINQ 入门](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [匿名类型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [局部类型推理](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Visual Basic 中的 LINQ 简介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [查询](../../../../visual-basic/language-reference/queries/index.md)
