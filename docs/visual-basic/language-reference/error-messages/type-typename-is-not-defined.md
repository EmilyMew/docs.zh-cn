---
title: 未定义类型“<typename>”
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: c2675d61307d92da1710368668f43af3559060a3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825031"
---
# <a name="type-typename-is-not-defined"></a>类型\<类型名称 > 未定义
该语句进行了对未定义的类型引用。 您可以如声明语句中定义的类型`Enum`， `Structure`， `Class`，或`Interface`。  
  
 **错误 ID:** BC30002  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   请确保该类型定义和它的引用都使用相同的拼写。  
  
-   确保该类型定义为引用可访问。 例如，如果类型是另一个模块中，已声明`Private`、 将类型定义移动到引用的模块，或将其声明`Public`。  
  
-   请确保类型的命名空间不会重新定义你的项目中。 如果是，使用`Global`关键字来完全限定类型名称。 例如，如果一个项目定义名为命名空间`System`，则<xref:System.Object?displayProperty=nameWithType>不能访问类型，除非它是使用完全限定`Global`关键字： `Global.System.Object`。  
  
-   如果定义的类型，但在 Visual Basic 中，单击未注册的对象库或在其中定义的类型库**添加引用**上**项目**菜单，并选择适当的对象库或类型库。  
  
-   请确保该类型所在的目标.NET Framework 配置文件的一部分的程序集。 有关详细信息，请参阅 [.NET Framework 目标错误疑难解答](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)。  
  
## <a name="see-also"></a>请参阅

- [在 Visual Basic 中的命名空间](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Enum 语句](../../../visual-basic/language-reference/statements/enum-statement.md)
- [Structure 语句](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Class 语句](../../../visual-basic/language-reference/statements/class-statement.md)
- [Interface 语句](../../../visual-basic/language-reference/statements/interface-statement.md)
- [管理项目中的引用](/visualstudio/ide/managing-references-in-a-project)
