---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: 44bc619c489fdff36f0b595f7d8934689b859adb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819424"
---
# <a name="-noconfig"></a>-noconfig
指定，编译器不应该自动引用常用[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]程序集或导入`System`和`Microsoft.VisualBasic`命名空间。  
  
## <a name="syntax"></a>语法  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>备注  
 `-noconfig`选项告知编译器不使用 Vbc.rsp 文件，位于 Vbc.exe 文件所在的同一目录中进行编译。 Vbc.rsp 文件引用常用[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]程序集和导入`System`和`Microsoft.VisualBasic`命名空间。 编译器隐式引用 System.dll 程序集，除非`-nostdlib`指定选项。 `-nostdlib`选项告知编译器不能使用 vbc.rsp 进行编译或自动引用 System.dll 程序集。  
  
> [!NOTE]
>  始终引用 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的程序集。  
  
 你可以修改 Vbc.rsp 文件以指定应包含每个 Vbc.exe 编译中的其他编译器选项 (除非指定`-noconfig`选项)。 有关详细信息，请参阅 [@（指定响应文件）](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)。  
  
 编译器选项传递给处理`vbc`最后一个命令。 因此，命令行上的任何选项将替代的 Vbc.rsp 文件中的相同选项的设置。  
  
> [!NOTE]
>  `-noconfig`选项不适用于从 Visual Studio 开发环境中，仅当从命令行编译时便可。  
  
## <a name="see-also"></a>请参阅

- [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [@（指定响应文件）](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [-参考 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
