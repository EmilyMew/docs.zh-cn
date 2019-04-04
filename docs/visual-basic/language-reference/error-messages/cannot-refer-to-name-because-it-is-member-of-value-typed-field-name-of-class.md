---
title: “<name>”是使用“System.MarshalByRefObject”作为基类的类“<name>”的值类型字段“<classname>”的成员，无法引用
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: aac190119ced74496c4dd012d200fca6d895ff28
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826764"
---
# <a name="cannot-refer-to-name-because-it-is-a-member-of-the-value-typed-field-name-of-class-classname-which-has-systemmarshalbyrefobject-as-a-base-class"></a>不能引用的 '\<名称 > 因为它是值类型字段的成员\<名称 > 的类的\<类名 >' system.marshalbyrefobject 作为基类
`System.MarshalByRefObject`类可让应用程序支持跨应用程序域边界对对象的远程访问。 类型必须继承自`MarshalByRejectObject`类时跨应用程序域边界使用的类型。 不得复制对象的状态，因为对象的成员不是可在其中创建应用程序域之外使用。  
  
 **错误 ID:** BC30310  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  检查以确保所引用的成员的引用有效。  
  
2.  显式限定的成员`Me`关键字。  
  
## <a name="see-also"></a>请参阅

- <xref:System.MarshalByRefObject>
- [Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)
