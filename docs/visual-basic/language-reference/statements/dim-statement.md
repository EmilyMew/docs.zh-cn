---
title: Dim 语句 (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: cab1cc07d23a44e57bdb0962a323b014308cb1e5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836553"
---
# <a name="dim-statement-visual-basic"></a>Dim 语句 (Visual Basic)
声明，并为一个或多个变量分配存储空间。  
  
## <a name="syntax"></a>语法  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a>部件  
  
-   `attributelist`  
  
     可选。 请参阅[属性列表](../../../visual-basic/language-reference/statements/attribute-list.md)。  
  
-   `accessmodifier`  
  
     可选。 可以是以下各项之一：  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [Protected Friend](../../language-reference/modifiers/protected-friend.md)
    
    - [Private Protected](../../language-reference/modifiers/private-protected.md)

     请参阅 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
-   `Shared`  
  
     可选。 请参阅[共享](../../../visual-basic/language-reference/modifiers/shared.md)。  
  
-   `Shadows`  
  
     可选。 请参阅[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。  
  
-   `Static`  
  
     可选。 请参阅[静态](../../../visual-basic/language-reference/modifiers/static.md)。  
  
-   `ReadOnly`  
  
     可选。 请参阅[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
-   `WithEvents`  
  
     可选。 指定这些引用可以引发事件的类的实例的对象变量。 请参阅[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)。  
  
-   `variablelist`  
  
     必需。 此语句中声明的变量的列表。  
  
     `variable [ , variable ... ]`  
  
     每个 `variable` 都具有以下语法和部件：  
  
     `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`  
  
    |部件|描述|  
    |---|---|  
    |`variablename`|必需。 变量的名称。 请参阅 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
    |`boundslist`|可选。 一个数组变量的每个维度的边界的列表。|  
    |`New`|可选。 创建类的新实例时`Dim`语句在运行时。|  
    |`datatype`|可选。 变量的数据类型。|  
    |`With`|可选。 引入了对象初始值设定项列表。|  
    |`propertyname`|可选。 在类中属性的名称要进行的实例。|  
    |`propinitializer`|之后需要`propertyname`=。 一个表达式，计算并分配给属性名。|  
    |`initializer`|可选如果`New`未指定。 计算并将在创建时分配给变量的表达式。|  
  
## <a name="remarks"></a>备注  
 Visual Basic 编译器使用`Dim`语句来确定变量的数据类型和其他信息，如哪些代码可以访问该变量。 下面的示例声明一个变量来保存`Integer`值。  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 您可以指定任何数据类型或枚举、 结构、 类或接口的名称。  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 对于引用类型，你使用`New`关键字来创建类的新实例或结构的指定数据类型。 如果使用`New`，不使用初始值设定项表达式。 相反，你提供参数，如有必要，创建该变量的类的构造函数。  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 您可以声明过程、 块、 类、 结构或模块中的变量。 不能声明的源文件、 命名空间或接口中的变量。 有关详细信息，请参阅[声明上下文和默认访问级别](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 在模块级别，在任何过程中，外部声明的变量是*成员变量*或*字段*。 成员变量是在整个其类、 结构或模块范围内。 在过程级别声明的变量是*局部变量*。 本地变量是仅在它们的过程或块的作用域中。  
  
 以下访问修饰符用于声明变量的过程之外： `Public`， `Protected`， `Friend`， `Protected Friend`，和`Private`。 有关详细信息，请参阅[访问 Visual Basic 中的级别](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `Dim`关键字是可选的如果指定任何下列修饰符通常省略： `Public`， `Protected`， `Friend`， `Protected Friend`， `Private`， `Shared`， `Shadows`， `Static`，`ReadOnly`，或`WithEvents`。  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 如果`Option Explicit`是启用 （默认值），编译器需要的声明为使用每个变量。 有关详细信息，请参阅[Option Explicit 语句](../../../visual-basic/language-reference/statements/option-explicit-statement.md)。  
  
## <a name="specifying-an-initial-value"></a>指定一个初始值  
 在创建时，可以将值分配给一个变量。 对于值类型，你使用*初始值设定项*来提供要分配给该变量的表达式。 该表达式的计算结果必须为一个常量，它可以在编译时计算。  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 如果指定一个初始值设定项，并且在未指定数据类型`As`子句中，*类型推理*用于推断从初始值设定项的数据类型。 在以下示例中，同时`num1`和`num2`强类型为整数。 在第二个声明中，类型推理来推断值 3 中的类型。  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 在过程级别应用类型推断。 它不适用于类、 结构、 模块或接口中的过程之外。 类型推理的详细信息，请参阅[Option Infer 语句](../../../visual-basic/language-reference/statements/option-infer-statement.md)并[本地类型推断](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。  
  
 如果未指定数据类型或初始值设定项，则会发生什么情况的信息，请参阅[默认数据类型和值](../../../visual-basic/language-reference/statements/dim-statement.md#default)本主题中更高版本。  
  
 可以使用*对象初始值设定项*声明命名和匿名类型的实例。 下面的代码创建的实例`Student`类，并使用对象初始值设定项来初始化属性。  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 有关对象初始值设定项的详细信息，请参阅[如何：使用对象初始值设定项声明对象](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)，[对象初始值设定项：命名和匿名类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)，并[匿名类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
## <a name="declaring-multiple-variables"></a>声明多个变量  
 您可以声明多个变量在一个声明语句中，使用括号指定每个，并在每个数组名的变量名称。 以逗号分隔多个变量。  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 如果要声明多个变量与一个`As`子句，不能提供该组的变量的初始值设定项。  
  
 可以通过使用单独指定不同的数据类型为不同的变量`As`子句为每个声明的变量。 每个变量将在第一个指定的数据类型`As`子句后遇到其`variablename`一部分。  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a>数组  
 您可以声明一个变量来保存*数组*，后者可以包含多个值。 若要指定该变量包含一个数组，请遵循其`variablename`立即使用括号。 有关数组的详细信息，请参阅[数组](../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
 您可以指定上限和每个维度的数组的下限。 若要执行此操作，包括`boundslist`在括号内。 为每个维度`boundslist`指定上限和下限 （可选）。 下限始终为零，或不指定它是否。 每个索引可能会不同于为 0 到其上界值。  
  
 以下两个语句是等效的。 每个语句声明数组 21`Integer`元素。 在访问数组时，索引可能会不同于 0 到 20。  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 下面的语句声明的类型的二维数组`Double`。 数组具有 6 列 (5 + 1) 每个 4 行 (3 + 1)。 请注意，上限表示索引不维的长度的最大可能值。 维的长度是上边界加 1。  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 数组可以包含 1 到 32 维数。  
  
 您可以将所有边界的数组声明中留空。 如果执行此操作时，数组具有您指定的维数，但不会被初始化。 它的值为`Nothing`直到至少初始化的某些元素。 `Dim`语句必须指定所有维度或任何维度的边界。  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 如果数组具有多个维度，必须包含以逗号分隔括号来表示的维度数。  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 您可以声明*零长度数组*通过声明一个数组的维数是-1。 包含一个零长度数组的变量不具有值`Nothing`。 零长度数组所需的某些公共语言运行时函数。 如果您尝试访问此类数组，则会发生运行时异常。 有关详细信息，请参阅[数组](../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
 可以通过使用数组文本初始化数组的值。 若要这样做，括起来与大括号初始化值 (`{}`)。  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 对于多维数组，每个单独的维度的初始化括在大括号外部的维度中。 按行优先的顺序指定了元素。  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 有关数组文本的详细信息，请参阅[数组](../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="default"></a> 默认数据类型和值  
 下表描述了指定 `Dim` 语句中数据类型和初始值设定项的各种组合的结果。  
  
|是否指定数据类型？|是否指定初始值设定项？|示例|结果|  
|---|---|---|---|  
|否|否|`Dim qty`|如果[Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)是 off （默认），将变量设置为`Nothing`。<br /><br /> 如果 `Option Strict` 处于打开状态，则发生编译时错误。|  
|否|是|`Dim qty = 5`|如果[Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)是启用 （默认值），则变量采用数据类型的初始值设定项。 请参阅[局部类型推理](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。<br /><br /> 如果 `Option Infer` 和 `Option Strict` 均处于关闭状态，则变量采用 `Object` 的数据类型。<br /><br /> 如果 `Option Infer` 处于关闭状态但 `Option Strict` 处于打开状态，则发生编译时错误。|  
|是|否|`Dim qty As Integer`|将变量初始化为数据类型的默认值。 请参阅本节后面的表。|  
|是|是|`Dim qty  As Integer = 5`|如果初始值设定项的数据类型不可转换为指定数据类型，则会发生编译时错误。|  
  
 如果你指定的数据类型，但不是指定初始值设定项，Visual Basic 将变量初始化为其数据类型的默认值。 下表显示的默认初始化值。  
  
|数据类型|默认值|  
|---|---|  
|所有数值类型 (包括`Byte`和`SByte`)|0|  
|`Char`|二进制 0|  
|所有的引用类型 (包括`Object`， `String`，和所有数组)|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|12:00 AM 的 1 年 1 月 1 日 (0001 年 01 月 01 日上午 12:00:00)|  
  
 就像一个单独的变量初始化结构的每个元素。 如果声明数组的长度，但不是初始化它的元素，每个元素将初始化，就好像单独的变量。  
  
## <a name="static-local-variable-lifetime"></a>静态本地变量的生存期  
 一个`Static`本地变量的生存期比在其中声明该过程的生存期更长。 边界的变量的生存期取决于声明该过程以及它是否`Shared`。  
  
|过程声明|初始化变量|变量会停止现有|  
|---|---|---|  
|在模块中|第一次调用该过程|当您的程序停止执行|  
|过程是在类或结构中， `Shared`|第一次调用该过程的特定实例上或在类或结构本身上|当您的程序停止执行|  
|过程不是在类或结构中， `Shared`|第一次特定实例上调用该过程|该实例进行垃圾回收 (GC) 的发布时|  
  
## <a name="attributes-and-modifiers"></a>特性和修饰符  
 可以将特性应用仅到成员变量上，而不是本地变量。 属性提供信息对程序集的元数据，这并不用于临时存储 （如本地变量） 有意义。  
  
 在模块级别不能使用`Static`修饰符来声明变量的成员。 在过程级别不能使用`Shared`， `Shadows`， `ReadOnly`， `WithEvents`，或任何访问修饰符来声明本地变量。  
  
 您可以指定哪些代码可以访问的变量通过提供`accessmodifier`。 类和模块成员变量 （任何过程之外） 默认为私有访问和结构成员变量默认为公共访问权限。 您可以调整其访问级别和访问修饰符。 （过程） 中的本地变量上，不能使用访问修饰符。  
  
 您可以指定`WithEvents`仅在成员变量上，而不是上一个过程中本地变量。 如果指定`WithEvents`，该变量的数据类型必须是特定的类类型，不`Object`。 不能声明具有数组`WithEvents`。 有关事件的详细信息，请参阅[事件](../../../visual-basic/programming-guide/language-features/events/index.md)。  
  
> [!NOTE]
>  代码类之外，结构或模块必须限定成员变量的名称，并且该类、 结构或模块的名称。 过程或块不能引用任何本地变量在该过程或块之外的代码。  
  
## <a name="releasing-managed-resources"></a>释放托管的资源  
 .NET Framework 垃圾回收器释放托管资源而无需您采取任何额外的编码。 但是，您可以强制而不是等待垃圾回收器托管的资源可供使用。  
  
 如果一个类保存到的特别有价值且稀缺资源 （例如数据库连接或文件句柄） 上，可能不希望等到下一步的垃圾回收，以清理不再使用的类实例。 一个类可以实现<xref:System.IDisposable>接口，以提供一种方法来释放垃圾回收之前的资源。 实现该接口的类公开`Dispose`可以调用来强制立即释放资源有价值的方法。  
  
 `Using`语句可获取资源、 执行一组语句，然后释放资源的过程进行自动化。 但是，资源必须实现<xref:System.IDisposable>接口。 有关详细信息，请参阅 [Using 语句](../../../visual-basic/language-reference/statements/using-statement.md)。  
  
## <a name="example"></a>示例  
 下面的示例通过使用声明变量`Dim`语句使用各种选项。  
  
 [!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]  
  
## <a name="example"></a>示例  
 以下示例列出 1 到 30 之间的素数。 本地变量的作用域是在代码注释中所述。  
  
 [!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]  
  
## <a name="example"></a>示例  
 在以下示例中，`speedValue`在类级别声明变量。 `Private`关键字用于声明变量。 中的任何过程可以访问该变量`Car`类。  
  
 [!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]  
  
 [!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]  
  
## <a name="see-also"></a>请参阅

- [Const 语句](../../../visual-basic/language-reference/statements/const-statement.md)
- [ReDim 语句](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Option Explicit 语句](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Infer 语句](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [“项目设计器”->“编译”页 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [变量声明](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [数组](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [对象初始值设定项：命名和匿名类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [匿名类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [对象初始值设定项：命名和匿名类型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [如何：使用对象初始值设定项声明对象](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [局部类型推理](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
