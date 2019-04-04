---
title: 如何：调用命令行编译器 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 78bf5b1f19db3a4f39e263cfd71283f0f7718631
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817175"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>如何：调用命令行编译器 (Visual Basic)
可以通过在命令行中，也称为 MS-DOS 提示符中键入可执行文件的名称来调用命令行编译器。 如果从默认 Windows 命令提示符下进行编译，你必须键入的可执行文件的完全限定的路径。 若要替代此默认行为，可以使用用于 Visual Studio，开发人员命令提示或修改 PATH 环境变量。 同时，可从任何目录编译只需键入编译器名称。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a>若要调用编译器使用针对 Visual Studio 开发人员命令提示  
  
1.  打开 Microsoft Visual Studio 程序组中的 Visual Studio Tools 程序文件夹。  
  
2.  可以使用 Visual Studio 开发人员命令提示若要从任何目录访问编译器，在你的计算机，如果安装了 Visual Studio。  
  
3.  用于 Visual Studio 调用开发人员命令提示。  
  
4.  在命令行中，键入`vbc.exe` *sourceFileName* ，然后按 ENTER。  
  
     例如，如果在名为的目录中存储你的源代码`SourceFiles`，将打开命令提示符并键入`cd SourceFiles`更改为该目录。 如果该目录包含名为源文件`Source.vb`，则可以通过键入来对其进行编译`vbc.exe Source.vb`。  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>若要设置为编译器的 Windows 命令提示符下的 PATH 环境变量  
  
1.  使用 Windows Search 功能在本地磁盘上查找 Vbc.exe。  
  
     编译器的目录的确切名称取决于 Windows 目录的位置和安装了".NET Framework"的版本。 如果有多个版本的安装".NET Framework"，您必须确定要使用 （通常使用最新版本） 的版本。  
  
2.  从你**启动**菜单中，右键单击**我的电脑**，然后单击**属性**从快捷菜单。  
  
3.  单击**高级**选项卡，然后依次**环境变量**。  
  
4.  在中**系统**变量窗格中，选择**路径**从列表中单击**编辑**。  
  
5.  在**编辑系统**变量的对话框中，将插入点移动到中字符串的末尾**变量值**字段并键入分号 （;） 后接在步骤 1 中找到完整的目录名称。  
  
6.  单击**确定**以确认所做的编辑，然后关闭对话框。  
  
     更改 PATH 环境变量后，你可以运行 Visual Basic 编译器在 Windows 命令提示符从任何目录的计算机上。  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>若要调用编译器使用 Windows 命令提示符  
  
1.  从**启动**菜单上单击**附件**文件夹，，然后打开**Windows 命令提示符下**。  
  
2.  在命令行中，键入`vbc.exe` *sourceFileName* ，然后按 ENTER。  
  
     例如，如果在名为的目录中存储你的源代码`SourceFiles`，将打开命令提示符并键入`cd SourceFiles`更改为该目录。 如果该目录包含名为源文件`Source.vb`，则可以通过键入来对其进行编译`vbc.exe Source.vb`。  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [条件编译](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
