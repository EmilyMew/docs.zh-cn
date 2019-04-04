---
title: Visual Basic 程序的结构
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: 5817d4d37610c87bb7e4ade407421ddce7a3a862
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828116"
---
# <a name="structure-of-a-visual-basic-program"></a>Visual Basic 程序的结构
从标准构建基块是构建 Visual Basic 程序。 一个*解决方案*由一个或多个项目组成。 一个*项目*又可以包含一个或多个程序集。 每个*程序集*从一个或多个源代码文件编译。 一个*源文件*提供定义和实现的类、 结构、 模块和接口，它们最终包含了所有代码。  
  
 有关这些构建基块的 Visual Basic 程序的详细信息，请参阅[解决方案和项目](/visualstudio/ide/solutions-and-projects-in-visual-studio)并[.NET 中的程序集](../../../standard/assembly/index.md)。  
  
## <a name="file-level-programming-elements"></a>文件级别的编程元素  
 当您启动项目或文件，并打开代码编辑器中时，您将看到一些代码已存在并按正确的顺序。 您编写任何代码都应遵循以下顺序：  
  
1.  `Option` 语句  
  
2.  `Imports` 语句  
  
3.  `Namespace` 语句和命名空间级别的元素  
  
 如果按不同顺序输入语句，可以产生编译错误。  
  
 程序还可以包含条件编译语句。 您可以单引号分隔文件中的上述顺序语句之间的源文件。  
  
### <a name="option-statements"></a>选项语句  
 `Option` 语句建立基本为后续的代码，以防止语法和逻辑错误的规则。 [Option Explicit 语句](../../../visual-basic/language-reference/statements/option-explicit-statement.md)可确保所有变量声明和拼写正确，这可以减少调试时间。 [Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)帮助不同的数据类型的变量之间工作时可能发生的逻辑错误和数据丢失降到最低。 [Option 比较语句](../../../visual-basic/language-reference/statements/option-compare-statement.md)指定字符串的方式相互进行比较，基于其`Binary`或`Text`值。  
  
### <a name="imports-statements"></a>Imports 语句  
 可以包括[Imports 语句 （.NET Namespace 和类型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)导入在项目外部定义的名称。 `Imports`语句允许您的代码来指代类和其他类型定义中导入命名空间，而无需限定它们。 可以使用任意多个`Imports`根据语句。 有关详细信息，请参阅[引用和 Imports 语句](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)。  
  
### <a name="namespace-statements"></a>Namespace 语句  
 命名空间可帮助组织和分类以便于分组和访问编程元素。 您使用[Namespace 语句](../../../visual-basic/language-reference/statements/namespace-statement.md)进行分类在特定的命名空间中的以下语句。 有关详细信息，请参阅 [Visual Basic 中的命名空间](../../../visual-basic/programming-guide/program-structure/namespaces.md)。  
  
### <a name="conditional-compilation-statements"></a>条件编译语句  
 条件编译语句可以出现在源文件中的几乎任何位置。 它们会导致您的代码以包括或排除在编译时根据特定条件的部分。 您可以将它们用于调试应用程序中，因为在调试模式下仅在运行的条件代码。 有关详细信息，请参阅[条件编译](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)。  
  
## <a name="namespace-level-programming-elements"></a>Namespace 级别的编程元素  
 类、 结构和模块包含在源文件中的所有代码。 它们是*命名空间级别*元素可出现在命名空间或文件级别的源的文件。 它们具有所有其他编程元素的声明。 接口，它们定义元素签名，但不提供实现，也出现在模块级别。 模块级别元素的详细信息，请参阅：  
  
-   [Class 语句](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Structure 语句](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Module 语句](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Interface 语句](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 在命名空间级别的数据元素是枚举和委托。  
  
## <a name="module-level-programming-elements"></a>模块级的编程元素  
 过程、 运算符、 属性和事件是可以保存可执行代码 （在运行时执行操作的语句） 的唯一编程元素。 它们是*模块级*的程序元素。 过程级别元素的详细信息，请参阅：  
  
-   [Function 语句](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Sub 语句](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Declare 语句](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Event 语句](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 在模块级别的数据元素是变量、 常量、 枚举和委托。  
  
## <a name="procedure-level-programming-elements"></a>过程级别的编程元素  
 大多数的内容*过程级别*元素都是可执行语句，它们构成您的程序的运行时代码。 所有可执行代码必须是在一些过程 (`Function`， `Sub`， `Operator`， `Get`， `Set`， `AddHandler`， `RemoveHandler`， `RaiseEvent`)。 有关详细信息，请参阅[语句](../../../visual-basic/programming-guide/language-features/statements.md)。  
  
 在过程级别的数据元素仅限于本地变量和常量。  
  
## <a name="the-main-procedure"></a>主要过程  
 `Main`过程是用于运行时应用程序已加载的第一个代码。 `Main` 可作为起始点和应用程序的总体控制。 有四种`Main`:  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 此过程的最常见类型是`Sub Main()`。 有关详细信息，请参阅[在 Visual Basic 中的 Main 过程](../../../visual-basic/programming-guide/program-structure/main-procedure.md)。  
  
## <a name="see-also"></a>请参阅

- [在 Visual Basic 中的主要过程](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
- [Visual Basic 命名约定](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Visual Basic 限制](../../../visual-basic/programming-guide/program-structure/limitations.md)
