---
title: -参考 (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 21efca701eb16898dd291d73bf0431641ba75d12
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826114"
---
# <a name="-reference-visual-basic"></a>-参考 (Visual Basic)
使编译器让指定程序集中的类型信息供当前正在编译的项目。  
  
## <a name="syntax"></a>语法  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`fileList`|必需。 程序集文件名的逗号分隔列表。 如果文件名包含空格，则将名称括在引号内。|  
  
## <a name="remarks"></a>备注  
 导入的文件必须包含程序集元数据。 仅公共类型都是程序集外部可见的。 [/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)选项从模块导入元数据。  
  
 如果引用的程序集 （程序集 A） 本身引用了另一个程序集 (程序集 B)，则在下列情况下需要引用程序集 B:  
  
-   程序集 A 中的类型继承自程序集 B 中的类型或实现程序集 B 中的接口。  
  
-   调用具有程序集 B 中的返回类型或参数类型的字段、属性、事件或方法。  
  
 使用[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)指定一个或多个程序集引用所在的目录。  
  
 为使编译器可以识别的程序集 （而不是模块） 中的类型，必须强制其解析的类型。 如何执行此操作的一个示例是定义类型的实例。 其他方法都可以解析为编译器的程序集中的类型名称。 例如，如果您从程序集中的类型继承，类型名称然后将成为编译器已知。  
  
 Vbc.rsp 响应文件引用常用[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]程序集，默认情况下使用。 使用`-noconfig`如果不希望编译器使用 Vbc.rsp。  
  
 `-reference` 的缩写形式是 `/r`。  
  
## <a name="example"></a>示例  
 下面的命令编译源文件`Input.vb`和引用程序集从`Metad1.dll`并`Metad2.dll`以生成`Out.exe`。  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [-目标 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
