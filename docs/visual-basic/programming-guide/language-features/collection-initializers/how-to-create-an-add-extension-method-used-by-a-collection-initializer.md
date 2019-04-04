---
title: 如何：创建 Add 扩展方法使用集合初始值设定项 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: a5af41e25b8f82aa173e2df28cc41b313c8d68dd
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825399"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>如何：创建 Add 扩展方法使用集合初始值设定项 (Visual Basic)
当使用集合初始值设定项创建集合时，Visual Basic 编译器中搜索`Add`为其集合类型的方法的参数`Add`方法与集合初始值设定项中的值的类型匹配。 这`Add`方法用于填充集合初始值设定项中的值的集合。  
  
 如果没有匹配`Add`存在方法并不能修改集合的代码，你可以添加扩展方法调用`Add`采用所需的集合初始值设定项的参数。 这通常是需要对泛型集合使用集合初始值设定项时执行的操作。  
  
## <a name="example"></a>示例  
 下面的示例演示如何将扩展方法添加到泛型<xref:System.Collections.Generic.List%601>类型，以便可以使用集合初始值设定项来添加类型的对象`Employee`。 扩展方法，可使用缩短了的集合初始值设定项语法。  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>请参阅

- [集合初始值设定项](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [如何：创建使用集合初始值设定项的集合](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
