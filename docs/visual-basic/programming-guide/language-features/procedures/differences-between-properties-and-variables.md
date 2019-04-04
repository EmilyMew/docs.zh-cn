---
title: Visual Basic 中属性和变量的差异
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- variables [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- variables [Visual Basic], definition
- Visual Basic code, variables
- Visual Basic code, properties
- properties [Visual Basic], values
- properties [Visual Basic], defined
- variables [Visual Basic], and properties
- properties [Visual Basic], and variables
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
ms.openlocfilehash: de4800e23519c2cc1c8b2b219287b9fa018b9bbf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842897"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Visual Basic 中属性和变量的差异
变量和属性都表示可以访问的值。 但是，有存储和实现之间的差异。  
  
## <a name="variables"></a>变量  
 一个*变量*直接对应于内存位置。 定义具有单个声明语句的变量。 变量可以是*局部变量*，定义在过程内，可仅在该过程中，也可以是*成员变量*，而不是在任何中模块、 类或结构定义过程。 成员变量也称为*字段*。  
  
## <a name="properties"></a>属性  
 一个*属性*是模块、 类或结构上定义的数据元素。 定义属性的代码块之间`Property`和`End Property`语句。 代码块包含`Get`过程中，`Set`过程中，或两者。 这些过程称为*属性过程*或*属性访问器*。 除了检索或存储属性的值，它们还可以执行自定义操作，例如对访问计数器的更新。  
  
## <a name="differences"></a>差异  
 下表显示了变量和属性之间的一些重要差异。  
  
|差异点|变量|属性|  
|-------------------------|--------------|--------------|  
|声明|单个声明语句|系列中的代码块的语句|  
|实现|单个存储位置|可执行代码 （属性过程）|  
|存储|直接与变量的值相关联|通常具有内部存储之外的属性包含类或模块不可用<br /><br /> 属性的值可能会或可能不作为存储的元素存在<sup>1</sup>|  
|可执行代码|None|必须具有至少一个过程|  
|读取和写入访问权限|读/写或只读的|读/写、 只读的或只写|  
|自定义操作 （除了接受或返回值）|不可能|可以执行设置或检索属性值的一部分|  
  
 <sup>1</sup>和变量，不同的属性值可能不直接对应于存储的单个项。 存储可能会拆分成方便或安全性，部分或的值可能会以加密形式存储。 在这些情况下`Get`过程将汇编这些块或解密存储的值和`Set`过程会加密新值或将其拆分为构成的存储。 属性值可以是临时的如一天时间，在这种情况下`Get`过程会计算得出其值动态每次访问的属性。  
  
## <a name="see-also"></a>请参阅

- [属性过程](./property-procedures.md)
- [过程参数和自变量](./procedure-parameters-and-arguments.md)
- [Property 语句](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [如何：创建属性](./how-to-create-a-property.md)
- [如何：声明具有混合的访问级别的属性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：调用 Property 过程](./how-to-call-a-property-procedure.md)
- [如何：声明并在 Visual Basic 中调用默认属性](./how-to-declare-and-call-a-default-property.md)
- [如何：在属性中放置值](./how-to-put-a-value-in-a-property.md)
- [如何：从属性获取一个值](./how-to-get-a-value-from-a-property.md)
