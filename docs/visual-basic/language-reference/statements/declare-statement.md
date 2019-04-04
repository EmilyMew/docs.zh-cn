---
title: 声明语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Declare
- vb.Lib
- vb.Any
helpviewer_keywords:
- Lib keyword [Visual Basic]
- declaring procedures [Visual Basic], Declare statement
- functions [Visual Basic], function procedures
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- procedures [Visual Basic], external
- Alias keyword [Visual Basic]
- external references [Visual Basic], Visual Basic
- DLLs, declaring procedures
- Declare statement [Visual Basic]
- declarations [Visual Basic], external
- Visual Basic code, Function procedures
- As keyword [Visual Basic], in Declare statement
- resources [Visual Basic], declaring
- Public keyword [Visual Basic], Declare statement
- platform invoke, Visual Basic external references
- Sub procedures [Visual Basic], declarations
- APIs, declaring API functions
- Visual Basic code, Sub procedures
- Function procedures [Visual Basic], declaring
ms.assetid: d3f21fb0-b804-4c99-97ed-583b23894cf1
ms.openlocfilehash: fbb7b4e118598157e2005469f89831df50de6576
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838334"
---
# <a name="declare-statement"></a>Declare Statement
声明对外部文件中实现的过程的引用。  
  
## <a name="syntax"></a>语法  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _  
Declare [ charsetmodifier ] [ Sub ] name Lib "libname" _  
[ Alias "aliasname" ] [ ([ parameterlist ]) ]  
' -or-  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _  
Declare [ charsetmodifier ] [ Function ] name Lib "libname" _  
[ Alias "aliasname" ] [ ([ parameterlist ]) ] [ As returntype ]  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`attributelist`|可选。 请参阅[属性列表](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|可选。 可以是以下各项之一：<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [受保护](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [友元](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [专用](../../../visual-basic/language-reference/modifiers/private.md)<br />- [受保护的友元](../../language-reference/modifiers/protected-friend.md)<br />- [专用受保护](../../language-reference/modifiers/private-protected.md)<br /><br /> 请参阅 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|可选。 请参阅[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`charsetmodifier`|可选。 指定字符集和文件搜索信息。 可以是以下各项之一：<br /><br /> -   [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) （默认值）<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [自动](../../../visual-basic/language-reference/modifiers/auto.md)|  
|`Sub`|（可选），但`Sub`或`Function`必须出现。 指示外部过程不返回值。|  
|`Function`|（可选），但`Sub`或`Function`必须出现。 指示外部过程返回一个值。|  
|`name`|必需。 此外部引用的名称。 有关详细信息，请参阅[声明的元素名称](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Lib`|必需。 引入了`Lib`子句，用于标识包含外部过程的外部文件 （DLL 或代码资源）。|  
|`libname`|必需。 包含声明的过程的文件的名称。|  
|`Alias`|可选。 指示所声明的过程，不能通过中指定的名称在其文件中进行标识`name`。 指定在其标识`aliasname`。|  
|`aliasname`|如果在使用需要`Alias`关键字。 标识过程的两种方式之一的字符串：<br /><br /> 在其文件中，用引号括起来的过程的入口点名称 (`""`)<br /><br /> 或<br /><br /> 数字符号 (`#`) 后跟一个整数，指定在其文件内的过程的入口点的序号|  
|`parameterlist`|所需的过程如果采用参数。 请参阅[参数列表](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`returntype`|需要`Function`指定并`Option Strict`是`On`。 该过程返回的值的数据类型。|  
  
## <a name="remarks"></a>备注  
 有时您需要调用在文件中 （如 DLL 或代码资源） 在项目外部定义的过程。 执行此操作时，Visual Basic 编译器不能正确调用该过程所需的信息，如该过程所在的位置、 如何标识、 其调用的序列和返回类型和字符串字符集，它使用的访问。 `Declare`语句创建对外部过程的引用，并提供这些必需的信息。  
  
 只能在模块级别使用 `Declare`。 这意味着*声明上下文*的外部引用必须是类、 结构或模块，并且不能为源文件、 命名空间、 接口、 过程或块。 有关详细信息，请参阅[声明上下文和默认访问级别](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 外部引用默认为[公共](../../../visual-basic/language-reference/modifiers/public.md)访问。 您可以调整其访问级别和访问修饰符。  
  
## <a name="rules"></a>规则  
  
-   **特性。** 可以将特性应用于外部引用。 在应用任何特性都有效，仅在你的项目中，不是外部文件中。  
  
-   **修饰符。** 外部过程是隐式[共享](../../../visual-basic/language-reference/modifiers/shared.md)。 不能使用`Shared`关键字声明的外部引用，并且您不能更改它的共享的状态时。  
  
     外部过程不能参与重写、 实现接口成员，或处理事件。 因此，不能使用`Overrides`， `Overridable`， `NotOverridable`， `MustOverride`， `Implements`，或`Handles`中的关键字`Declare`语句。  
  
-   **外部过程的名称。** 不需要此外部引用指定相同的名称 (在`name`) 作为其外部文件中的过程的入口点名称 (`aliasname`)。 可以使用`Alias`子句来指定入口点名称。 这可以是外部的过程相同的作用域中具有与 Visual Basic 保留的修饰符或变量、 过程或任何其他编程元素同名的情况下很有用。  
  
    > [!NOTE]
    >  大多数 Dll 中的入口点名称是区分大小写。  
  
-   **外部过程号。** 或者，可以使用`Alias`子句来指定外部文件的入口点的导出表内的序号。 若要执行此操作，应先`aliasname`以数字符号 (`#`)。 这可以是很有用，如果在 Visual Basic 中不允许外部过程的名称中的任何字符或外部文件导出不带名称的过程。  
  
## <a name="data-type-rules"></a>数据类型的规则  
  
-   **参数数据类型。** 如果`Option Strict`是`On`，必须指定每个参数中的数据类型`parameterlist`。 这可以是任何数据类型或枚举、 结构、 类或接口的名称。 内`parameterlist`，则使用`As`子句来指定要传递给每个参数的自变量的数据类型。  
  
    > [!NOTE]
    >  如果外部过程不针对.NET Framework 编写的您必须采取措施的数据类型相对应。 例如，如果声明到 Visual Basic 6.0 过程使用的外部引用`Integer`参数 （在 Visual Basic 6.0 中为 16 位），必须标识相应的参数作为`Short`中`Declare`语句，因为这是 16 位在 Visual Basic 中的位的整数类型。 同样，`Long`在 Visual Basic 6.0 中，具有不同的数据宽度和`Date`的实现方式不同。  
  
-   **返回的数据类型。** 如果外部过程`Function`并`Option Strict`是`On`，必须指定返回给调用代码的值的数据类型。 这可以是任何数据类型或枚举、 结构、 类或接口的名称。  
  
    > [!NOTE]
    >  Visual Basic 编译器不验证您的数据类型是与这些外部过程兼容。 如果存在不匹配，公共语言运行时将生成<xref:System.Runtime.InteropServices.MarshalDirectiveException>运行时异常。  
  
-   **默认数据类型。** 如果`Option Strict`是`Off`而且未指定参数中的数据类型`parameterlist`，Visual Basic 编译器将转换为相应的参数[Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)。 同样，如果未指定`returntype`，编译器采用返回数据类型为`Object`。  
  
    > [!NOTE]
    >  处理可能在不同平台上编写的外部过程，因为它是危险做出任何关于数据类型假设或允许它们采用默认设置。 如果有的话，它会更安全，以指定每个参数和返回值的数据类型。 这还可以提高代码的可读性。  
  
## <a name="behavior"></a>行为  
  
-   **作用域。** 在其类、 结构或模块的作用域中是外部引用。  
  
-   **生存期。** 外部引用具有相同的生存期类、 结构或在其中声明的模块。  
  
-   **调用外部过程。** 调用外部过程调用的相同方式`Function`或`Sub`过程 — 通过在表达式中使用它，如果它返回一个值，或通过指定其[Call 语句](../../../visual-basic/language-reference/statements/call-statement.md)如果它不返回值。  
  
     将参数传递到完全按照指定的外部过程`parameterlist`在`Declare`语句。 不会考虑外部文件中最初声明参数的方式。 同样，如果没有返回值，使用它完全按照指定的`returntype`在`Declare`语句。  
  
-   **字符集。** 可以指定在`charsetmodifier`如何 Visual Basic 应封送字符串时调用的外部过程。 `Ansi`修饰符指示 Visual Basic 进行封送为 ANSI 值的所有字符串和`Unicode`修饰符将指示该封都送为 Unicode 值的所有字符串。 `Auto`修饰符将定向到封送字符串，根据.NET Framework 的 Visual Basic 规则基于外部引用`name`，或`aliasname`如果指定。 默认值为 `Ansi`。  
  
     `charsetmodifier` 此外可以指定 Visual Basic 应如何查找其外部文件中的外部过程。 `Ansi` 和`Unicode`直接 Visual Basic，而无需在搜索过程中修改其名称进行查找。 `Auto` 指示 Visual Basic，若要确定运行时平台的基字符集和可能修改外部过程的名称，按如下所示：  
  
    -   ANSI 平台，如 Windows 95、 Windows 98 或 Windows Millennium Edition 上首先查找与没有名称的修改的外部过程。 如果失败，将"A"追加到外部过程名称的末尾，并再次查找。  
  
    -   在 Unicode 平台上，如 Windows NT、 Windows 2000 或 Windows XP 中，首先查找与没有名称的修改的外部过程。 如果该操作失败，则将追加"W"到末尾的外部过程的名称，并再次查找。  
  
-   **机制。** Visual Basic 使用.NET Framework*平台调用*(PInvoke) 机制来解析和访问外部过程。 `Declare`语句和<xref:System.Runtime.InteropServices.DllImportAttribute>这两个类使用此机制自动，并且不需要任何知识的 PInvoke。 有关详细信息，请参见[演练：调用 Windows Api](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)。  
  
> [!IMPORTANT]
>  如果外部过程外部公共语言运行时 (CLR) 运行，则*非托管代码*。 当调用此类过程，例如 Windows API 函数或 COM 方法，可能会使你的应用程序的安全风险。 有关详细信息，请参阅[用于非托管代码安全编码准则](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md)。  
  
## <a name="example"></a>示例  
 下面的示例声明的外部引用`Function`返回当前用户名称的过程。 然后，它调用外部过程`GetUserNameA`作为的一部分`getUser`过程。  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="example"></a>示例  
 <xref:System.Runtime.InteropServices.DllImportAttribute>提供非托管代码中使用函数的替代方法。 下面的示例声明导入的函数，而无需使用`Declare`语句。  
  
 [!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Imports 语句（.NET 命名空间和类型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [AddressOf 运算符](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)
- [参数列表](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Call 语句](../../../visual-basic/language-reference/statements/call-statement.md)
- [演练：调用 Windows API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
