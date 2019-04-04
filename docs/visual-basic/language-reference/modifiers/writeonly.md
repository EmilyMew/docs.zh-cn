---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: 1b8de27e872914ba59d73126d2a9a7c42609165e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829015"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
指定可写入但无法读取属性。  
  
## <a name="remarks"></a>备注  
  
## <a name="rules"></a>规则  
 **声明上下文。** 只能在模块级别使用 `WriteOnly`。 这意味着声明上下文`WriteOnly`属性必须是类、 结构或模块，并且不能是源文件、 命名空间或过程。  
  
 您可以将属性声明为`WriteOnly`，但不是变量。  
  
## <a name="when-to-use-writeonly"></a>何时使用 WriteOnly  
 有时您希望使用的代码，以便能够设置一个值，但不是会发现它是什么。 例如，敏感数据，如身份证号或密码，需要从访问由未设置任何组件进行保护。 在这些情况下，你可以使用`WriteOnly`属性设置的值。  
  
> [!IMPORTANT]
>  当你定义并使用`WriteOnly`属性，请考虑以下附加保护措施：  
  
-   **重写。** 如果该属性是类的成员，允许其默认为[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)，并不声明`Overridable`或`MustOverride`。 这可以防止不需要访问通过重写派生的类。  
  
-   **访问级别。** 如果在一个或多个变量中保存该属性的敏感数据，将其声明[专用](../../../visual-basic/language-reference/modifiers/private.md)以便没有其他代码可以访问它们。  
  
-   **加密。** 将所有敏感数据存储以加密形式，而不是以纯文本。 如果恶意代码以某种方式获得该内存区域的访问权，则更难以进行使用的数据。 加密也是很有用，如有必要进行序列化的敏感数据。  
  
-   **正在重置。** 类、 结构或将属性定义的模块时被终止，默认值或其他无意义的值重置的敏感数据。 这提供额外的保护时进行常规访问时释放该内存区域。  
  
-   **持久性。** 如果可以避免，则不保留任何敏感数据，例如在磁盘上。 此外，任何敏感数据写入剪贴板。  
  
 `WriteOnly`修饰符可用于在此上下文中：  
  
 [Property 语句](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>请参阅

- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [关键字](../../../visual-basic/language-reference/keywords/index.md)
