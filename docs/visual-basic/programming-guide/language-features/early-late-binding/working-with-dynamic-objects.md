---
title: 使用动态对象 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: ea7d7aae1cd79a0243a9c721b5e3958fba82f84f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832068"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>使用动态对象 (Visual Basic)
动态对象提供另一种方法，而不`Object`类型，将在运行时的后期绑定到一个对象。 通过使用动态中定义的接口在运行时动态对象公开属性和方法等成员<xref:System.Dynamic>命名空间。 可以使用中的类<xref:System.Dynamic>命名空间创建的与静态类型或格式不匹配的数据结构处理的对象。 此外可以使用 IronPython 和 IronRuby 等动态语言中定义的动态对象。 有关演示如何创建动态对象，或使用动态语言中定义的动态对象的示例，请参阅[演练：创建和使用动态对象](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)， <xref:System.Dynamic.DynamicObject>，或<xref:System.Dynamic.ExpandoObject>。  
  
 Visual Basic 将绑定到对象中的动态语言运行时和 IronPython 和 IronRuby 等动态语言使用<xref:System.Dynamic.IDynamicMetaObjectProvider>接口。 类的实现示例`IDynamicMetaObjectProvider`接口是<xref:System.Dynamic.DynamicObject>和<xref:System.Dynamic.ExpandoObject>类。  
  
 如果对实现的对象进行后期绑定调用`IDynamicMetaObjectProvider`接口，Visual Basic 将绑定到使用该接口的动态对象。 如果对未实现的对象进行后期绑定调用`IDynamicMetaObjectProvider`接口，或者，如果在调用`IDynamicMetaObjectProvider`接口失败，则通过使用 Visual Basic 运行时的后期绑定功能，Visual Basic 将绑定到对象。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [演练：创建和使用动态对象](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [早期绑定和后期绑定](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
