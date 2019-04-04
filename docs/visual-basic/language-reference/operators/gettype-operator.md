---
title: GetType 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 34ab192814583db5cdc0d0183c73cc22b8633e9c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840311"
---
# <a name="gettype-operator-visual-basic"></a>GetType 运算符 (Visual Basic)
返回<xref:System.Type>指定类型的对象。 <xref:System.Type>对象提供有关其属性、 方法和事件等类型的信息。  
  
## <a name="syntax"></a>语法  
  
```  
GetType(typename)  
```  
  
## <a name="parameters"></a>参数  
  
|参数|描述|  
|---|---|  
|`typename`|为其所需的信息类型的名称。|  
  
## <a name="remarks"></a>备注  
 `GetType`运算符将返回<xref:System.Type>的指定对象的`typename`。 可以在任何已定义类型的名称将传递`typename`。 这包括：  
  
-   任何 Visual Basic 数据类型，如`Boolean`或`Date`。  
  
-   任何.NET Framework 类、 结构、 模块或接口，如<xref:System.ArgumentException?displayProperty=nameWithType>或<xref:System.Double?displayProperty=nameWithType>。  
  
-   任何类、 结构、 模块或接口定义的应用程序。  
  
-   任何由你的应用程序定义的数组。  
  
-   任何由你的应用程序定义的委托。  
  
-   任何由 Visual Basic、.NET Framework 中或你的应用程序定义的枚举。  
  
 如果你想要获取的对象变量的类型对象，使用<xref:System.Type.GetType%2A?displayProperty=nameWithType>方法。  
  
 `GetType`运算符只能在以下情况下有用：  
  
-   必须在运行时访问类型的元数据。 <xref:System.Type>对象提供元数据，例如类型成员和部署信息。 您需要它，例如，在程序集上进行反射。 有关详细信息，请参阅 <xref:System.Reflection?displayProperty=nameWithType>。  
  
-   你想要比较两个对象引用引用相同类型的实例。 如果是这样，`GetType`返回对相同的引用<xref:System.Type>对象。  
  
## <a name="example"></a>示例  
 下面的示例演示`GetType`中使用的运算符。  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [运算符和表达式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
