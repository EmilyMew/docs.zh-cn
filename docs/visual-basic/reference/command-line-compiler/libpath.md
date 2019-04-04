---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: b8e28b821f6536ddb5c7612e8706e024dd79a0bd
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833294"
---
# <a name="-libpath"></a>-libpath
指定引用的程序集的位置。  
  
## <a name="syntax"></a>语法  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`dirList`|必需。 以分号分隔的编译器进行查找的引用的程序集目录的列表中找不到当前工作目录 （调用编译器的目录） 或公共语言运行时的系统目录。 如果目录名称包含空格，将名称括在引号 ("")。|  
  
## <a name="remarks"></a>备注  
 `-libpath`选项指定引用的程序集的位置[-引用](../../../visual-basic/reference/command-line-compiler/reference.md)选项。  
  
 编译器按以下顺序搜索未完全限定的程序集引用：  
  
1.  当前工作目录。 该目录为从其调用编译器的目录。  
  
2.  公共语言运行时系统目录。  
  
3.  由指定的目录`/libpath`。  
  
4.  由 LIB 环境变量指定的目录。  
  
 `-libpath`选项是累加的; 指定一次追加到以前的值。  
  
 使用`-reference`来指定程序集引用。  
  
|若要在 Visual Studio 中设置 /libpath 集成开发环境|  
|---|  
|1.在 **“解决方案资源管理器”** 中选择一个项目。 在“项目”菜单上，单击“属性”。 <br />2.单击“引用”选项卡。<br />3.单击**引用路径...** 按钮。<br />4.在中**引用路径**对话框框中，输入中的目录名称**文件夹：** 框。<br />5.单击**将文件夹添加**。|  
  
## <a name="example"></a>示例  
 下面的代码编译`T2.vb`创建.exe 文件。 编译器和所呈现的工作目录中，c： 驱动器的根目录中的 c： 驱动器的新程序集目录中的程序集引用。  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>请参阅

- [.NET 中的程序集](../../../standard/assembly/index.md)
- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
