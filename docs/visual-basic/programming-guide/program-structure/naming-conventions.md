---
title: Visual Basic 命名约定
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: 46f59403feced4baafef4662065cb7daedbeaa7b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837073"
---
# <a name="visual-basic-naming-conventions"></a>Visual Basic 命名约定
当在 Visual Basic 应用程序中命名元素时，该名称的第一个字符必须是字母字符或下划线。 但请注意，以下划线开头的名称不符合[语言独立性和与语言无关的组件](../../../standard/language-independence-and-language-independent-components.md)(CLS)。  
  
 以下建议适用于命名。  
  
-   在开始使用一个大写字母，名称中每个单独的分词`FindLastRecord`和`RedrawMyForm`。  
  
-   开始函数和方法名称以动词，如`InitNameArray`或`CloseDialog`。  
  
-   开始类、 结构、 模块和属性名称使用名词，如`EmployeeName`或`CarAccessory`。  
  
-   开始接口名称以前缀"I"后, 跟名词或名词短语，如`IComponent`，或使用形容词描述接口的行为，如`IPersistable`。 不使用下划线字符，并且请慎用缩写词，因为缩写可能会造成混淆。  
  
-   名词描述类型的事件，随后开始事件处理程序名称"`EventHandler`"后缀，如下所示:"`MouseEventHandler`"。  
  
-   在事件参数类的名称，包括"`EventArgs`"后缀。  
  
-   如果"before"或"after"事件的概念，请在现在时或过去时，使用后缀，如"`ControlAdd`"或"`ControlAdded`"。  
  
-   有关长或经常使用术语，使用缩写保留名称长度合理的例如，"HTML"，而不是"超文本标记语言"。 一般情况下，变量名称多于 32 个字符难以读取到较低分辨率的监视器上。 此外，请确保你的缩写词是在整个应用程序保持一致。 在项目中"HTML"和"超文本标记语言"之间随机切换可能会导致混淆。  
  
-   避免使用内层作用域的外部作用域中的名称相同的名称。 如果访问错误变量时，会导致错误。 如果变量和具有相同名称的关键字之间发生冲突，则必须标识关键字的前面添加相应的类型库。 例如，如果有一个名为变量`Date`，可以使用内部函数`Date`只是在调用函数<xref:System.DateTime.Date%2A?displayProperty=nameWithType>。  
  
## <a name="see-also"></a>请参阅

- [代码中用作元素名称的关键字](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [Me、My、MyBase 和 MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [已声明的元素名称](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [程序结构和代码约定](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Visual Basic 语言参考](../../../visual-basic/language-reference/index.md)
