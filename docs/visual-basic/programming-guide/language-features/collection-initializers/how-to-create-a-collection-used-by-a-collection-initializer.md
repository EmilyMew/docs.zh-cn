---
title: 如何：创建集合使用集合初始值设定项 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 75c280b57df03bde173c740123cccda278536dc1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820303"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>如何：创建集合使用集合初始值设定项 (Visual Basic)
当使用集合初始值设定项创建集合时，Visual Basic 编译器中搜索`Add`为其集合类型的方法的参数`Add`方法与集合初始值设定项中的值的类型匹配。 这`Add`方法用于填充集合初始值设定项中的值的集合。  
  
## <a name="example"></a>示例  
 下面的示例演示`OrderCollection`集合，其中包含一个公共`Add`方法，可以使用集合初始值设定项类型的对象添加`Order`。 `Add`方法，可使用缩短了的集合初始值设定项语法。  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>请参阅

- [集合初始值设定项](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [如何：创建 Add 扩展方法使用集合初始值设定项](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
