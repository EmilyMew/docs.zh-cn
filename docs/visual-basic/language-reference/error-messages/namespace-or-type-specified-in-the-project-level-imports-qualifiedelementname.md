---
title: 在项目级 Imports“<qualifiedelementname>”中指定的命名空间或类型不包含任何公共成员，或者找不到该命名空间或类型
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 554300f87dbfca351ebcd2d544051968e84880ab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816795"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>项目级 Imports 中指定的 Namespace 或类型\<qualifiedelementname > 不包含任何公共成员，或者找不到
项目级 Imports 中指定的 Namespace 或类型\<qualifiedelementname > 不包含任何公共成员，或者找不到。 请确保该命名空间或类型定义，其中包含至少一个公共成员。 请确保别名名称中不包含其他别名。  
  
 一个项目的导入属性所指定的包含元素不能为找到或未定义任何`Public`成员。  
  
 一个*包含元素*可以是命名空间、 类、 结构、 模块、 接口或枚举。 包含元素包含成员，例如变量、 过程或其他包含的元素。  
  
 导入的目的是允许你访问命名空间或类型成员的代码而无需限定它们。 你的项目可能还需要添加对命名空间或类型的引用。 详细信息，请参阅"导入包含元素"中[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
 如果编译器找不到指定的包含元素，它无法解析使用它的引用。 如果它找到的元素，但该元素不会公开任何`Public`成员，则任何引用都不会成功。 在任一情况下是没有意义的 import 元素。  
  
 您使用**项目设计器**来指定要导入元素。 使用**导入命名空间**一部分**引用**页。 你可以获取**项目设计器**通过双击**我的项目**中的图标**解决方案资源管理器**。  
  
 **错误 ID:** BC40057  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  打开**项目设计器**，并切换到**引用**页。  
  
2.  在中**导入命名空间**部分中，验证包含的元素是否可从你的项目进行访问。  
  
3.  验证包含的元素公开至少一个`Public`成员。  
  
## <a name="see-also"></a>请参阅

- [项目设计器 ->“引用”页 (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [管理项目和解决方案属性](/visualstudio/ide/managing-project-and-solution-properties)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [在 Visual Basic 中的命名空间](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [对已声明元素的引用](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
