---
title: 其他数据类型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 4808d87322d5b21b70ec38e2eb31b2b204938745
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821760"
---
# <a name="miscellaneous-data-types-visual-basic"></a>其他数据类型 (Visual Basic)
Visual Basic 提供几种数据类型不是针对数字或字符。 相反，它们处理专用数据如是/否值、 日期/时间值和对象地址。  
  
 显示 Visual Basic 数据类型的并排比较的表，请参阅[数据类型](../../../../visual-basic/language-reference/data-types/index.md)。  
  
## <a name="boolean-type"></a>布尔值类型  
 [布尔数据类型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)是一个无符号的值，将被解释为任一`True`或`False`。 其数据宽度取决于实现的平台。 如果一个变量可以包含仅两个状态如 true/false 的值是/否或开/关，将其声明为`Boolean`。  
  
## <a name="date-type"></a>日期类型  
 [日期数据类型](../../../../visual-basic/language-reference/data-types/date-data-type.md)是一个 64 位值，包含日期和时间信息。 每个增量表示自 （上午 12:00） 开始后所用时间的 100 纳秒为单位的 1 公历日历中每 1 年月 1 日。 如果一个变量可以包含日期值、 时间值，或同时，将其声明为`Date`。  
  
## <a name="object-type"></a>对象类型  
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)是指向你的应用程序或通过在其他一些应用程序中的对象实例的 32 位地址。 `Object`变量可以是指你的应用程序识别的任何对象或任何数据类型的数据。 这包括*值类型*，如`Integer`， `Boolean`，和结构实例，并*引用类型*，这是实例创建的对象的类如`String`和<xref:System.Windows.Forms.Form>，以及数组实例。  
  
 如果一个变量存储指向你在编译时，不知道类的实例或者它可以指向不同的数据类型的数据，将其声明为`Object`。  
  
 利用`Object`数据类型是，可以使用它来存储任何数据类型的数据。 缺点是会产生额外的操作，需要更多的执行时间并提高执行速度慢的应用程序。 如果您使用`Object`对于值类型变量，则会产生*装箱*并*取消装箱*。 如果将其用于引用类型，则会产生*后期绑定*。  
  
## <a name="see-also"></a>请参阅

- [类型字符](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [基本数据类型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [数值数据类型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [字符数据类型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [数据类型疑难解答](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [早期绑定和后期绑定](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
