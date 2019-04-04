---
title: 类型“<typename1>”的值无法转换为“<typename2>”
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: 5f313a43bc3a2f983dabbd45477d120fdb80d063
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829014"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a>类型的值\<typename1 > 无法转换为\<typename2 >
类型的值\<typename1 > 无法转换为\<typename2 >。 类型不匹配可能是由于的文件引用的程序集的项目引用混合使用\<程序集名称 >。 请尝试更换的文件引用\<文件路径 > 项目中\<projectname1 > 项目引用\<项目名称 2> >。  
  
 在其中一个项目会的项目引用和文件引用的情况下，编译器无法保证一个类型可转换为另一个。  
  
 下面的伪代码说明了可能会生成此错误的情况。  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 项目`P1`完成项目间接的项目引用`P2`到项目`P3`，同时还对直接文件引用`P3`。 声明`commonObject`使用的文件引用`P3`，而在调用`P2.getCommonClass`将使用到的项目引用`P3`。  
  
 在此情况下的问题是文件引用指定的文件路径和名称的输出文件`P3`(通常为 p3.dll)，而项目引用标识源项目 (`P3`) 按项目名称。 因此，编译器无法保证该类型`P3.commonClass`来自通过两个不同的引用相同的源代码。  
  
 这种情况通常发生在项目引用和文件引用混合。 在上图中，会出现问题如果`P1`进行直接的项目引用到`P3`而不是文件引用。  
  
 **错误 ID:** BC30955  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   更改的项目引用的文件引用。  
  
## <a name="see-also"></a>请参阅

- [在 Visual Basic 中的类型转换](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [管理项目中的引用](/visualstudio/ide/managing-references-in-a-project)
