---
title: 编译项目中的 XML 架构时发生错误
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 337fc1fb4dfc83c9b4814d3e45eb0cbe0758f7ce
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842520"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>编译项目中的 XML 架构时发生错误
编译项目中的 XML 架构时发生错误。 因此，XML IntelliSense 不可用。  
  
 在项目中包含的 XML 架构定义 (XSD) 架构中没有错误。 添加与现有的 XSD 架构冲突设置项目的 XSD 架构 (.xsd) 文件时，将发生此错误。  
  
 **错误 ID:** BC36810  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   双击中的警告**错误列表**窗口。 Visual Basic 将转到源的警告的 XSD 文件中的位置。 更正的 XSD 架构中的错误。  
  
-   请确保所有必需的 XSD 架构 (.xsd) 文件都包括在项目中。 可能需要单击**显示所有文件**上**项目**中的下拉菜单，看看您.xsd 文件**解决方案资源管理器**。 右键单击一个.xsd 文件，然后单击**包括在项目**将该文件包括在项目中。  
  
-   如果使用 XML 到架构向导时，如果从同一源推断架构不止一次可以发生此错误。 在这种情况下，您可以从项目中，删除现有的 XSD 架构文件将添加新的 XML 到架构项模板，然后提供 XML 到架构向导使用所有适用的 XML 源为您的项目。  
  
-   如果在 XSD 架构中不标识任何错误，则 XML 编译器可能没有足够的信息来提供详细的错误消息。 你可以获取更详细的错误信息，如果您确保.xsd 文件的 XML 命名空间包含的项目匹配项标识为 Visual Studio 中设置 XML 架构的 XML 命名空间。  
  
## <a name="see-also"></a>请参阅

- [“错误列表”窗口](/visualstudio/ide/reference/error-list-window)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
