---
title: 类型“<typename1>”的值无法转换为“<typename2>”（多个文件引用）
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 58b334eb5e6db443bcfaba72729d59cb1d798e70
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833524"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a>类型的值\<typename1 > 无法转换为\<typename2 > （多个文件引用）
类型的值\<typename1 > 无法转换为\<typename2 >。 类型不匹配可能是由于为的文件引用混合使用 '\<filepath1 > 项目中\<projectname1 > 对的文件引用\<filepath2 > 项目中\<项目名称 2> >。 如果两个程序集完全相同，请尝试更换这些引用，以确保两个引用都来自相同的位置。  
  
 在其中一个项目会对程序集的多个文件引用的情况下，编译器无法保证一个类型可转换为另一个。  
  
 每个文件引用指定文件路径和项目 （通常为 DLL 文件） 的输出文件的名称。 编译器无法保证输出文件来自同一源，或它们表示相同的程序集的相同版本。 因此，它不能保证在不同的引用类型具有相同的类型，或甚至一个可以转换为其他。  
  
 如果你知道引用的程序集具有相同的程序集标识，可以使用单个文件引用。 *程序集标识* 包括程序集的名称、版本、公钥（如果有）和区域性。 此信息唯一地标识该程序集。  
  
 **错误 ID:** BC30961  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   如果引用的程序集具有相同的程序集标识，然后删除或替换其中一个文件的引用，以便只有单个文件引用。  
  
-   如果引用的程序集不具有相同的程序集标识，则更改你的代码，以便它不会尝试转换为类型在另一个中的类型。  
  
## <a name="see-also"></a>请参阅

- [在 Visual Basic 中的类型转换](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [管理项目中的引用](/visualstudio/ide/managing-references-in-a-project)
