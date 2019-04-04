---
title: 平台 (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: 9657d9ec23b0e67625521ee595bc693eb7b992a4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843118"
---
# <a name="-platform-visual-basic"></a>平台 (Visual Basic)
指定公共语言运行时 (CLR) 的哪个平台版本可以运行输出文件。  
  
## <a name="syntax"></a>语法  
  
```  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`x86`|将程序集编译成可由 32 位、x86 可兼容 CLR 运行。|  
|`x64`|将程序集编译成可由支持 AMD64 或 EM64T 指令集的计算机上的 64 位 CLR 运行。|  
|`Itanium`|将程序集编译成可由配有 Itanium 处理器的计算机上的 64 位 CLR 运行。|  
|`arm`|将程序集编译成可在配有高级 RISC 计算机 (ARM) 处理器的计算机上运行。|  
|`anycpu`|将程序集编译成可在任意平台上运行。 应用程序将作为 32 位应用程序在 Windows 的 32 位版本上运行，作为 64 位应用程序在 Windows 的 64 位版本上运行。 此标志为默认值。|  
|`anycpu32bitpreferred`|将程序集编译成可在任意平台上运行。 应用程序将作为 32 位 应用程序在 Windows 的 32 位版本和 64 位版本上运行。 此标志仅对可执行文件 (.EXE) 有效且需要 [!INCLUDE[net_v45](~/includes/net-v45-md.md)]。|  
  
## <a name="remarks"></a>备注  
 使用 `-platform` 选项来指定输出文件所面向的处理器类型。  
  
 通常，无论平台如何，Visual Basic 内编写的 .NET Framework 程序集将运行相同内容。 但是，存在一些不同平台行为不同的情况。 这些常见的情况是：  
  
-   结构中包含大小随平台而改变的成员，如任何指针类型。  
  
-   指针算术包含固定大小。  
  
-   平台调用错误，或使用句柄的 `Integer` 而非 <xref:System.IntPtr> 的 COM 声明不正确。  
  
-   将 <xref:System.IntPtr> 强制转换为 `Integer`。  
  
-   将平台调用或 COM 互操作与不存在于任何平台的组件一起使用。  
  
 **-平台**选项将会减少一些问题，如果您知道您的代码将在运行的体系结构做出判定。 尤其是在下列情况下：  
  
-   如果你针对 64 位平台且应用程序在 32 位计算机上运行，则相对于不使用此开关而出现的错误，此错误消息更早出现且更加针对问题。  
  
-   如果你在选项上设置 `x86` 标志且之后应用程序在 64 位计算机上运行，则应用程序将在 WOW 子系统中运行而不是在本机上运行。  
  
 在 64 位 Windows 操作系统上：  
  
-   用 `-platform:x86` 编译的程序集将在 WOW64 下运行的 32 位 CLR 上执行。  
  
-   用 `-platform:anycpu` 编译的可执行文件将在 64 位 CLR 上执行。  
  
-   用 `-platform:anycpu` 编译的 DLL 将在加载它的进程所在的同一 CLR 上执行。  
  
-   用 `-platform:anycpu32bitpreferred` 编译的可执行文件将在 32 位 CLR 上执行。  
  
 有关如何开发 Windows 64 位版本上运行的应用程序的详细信息，请参阅[64 位应用程序](../../../framework/64-bit-apps.md)。  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a>若要设置的 Visual Studio IDE 中的平台  
  
1.  在中**解决方案资源管理器**，选择项目，打开**项目**菜单，并单击**属性**。  
  
2.  上**编译**选项卡上，选中或清除**首选 32 位**复选框，或者，在**目标 CPU**列表中，选择一个值。  
  
     有关详细信息，请参阅[编译页，项目设计器 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)。  
  
## <a name="example"></a>示例  
 下例阐释使用 `-platform` 编译器选项的方式。  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a>请参阅

- [/target (Visual Basic)](target.md)
- [Visual Basic 命令行编译器](index.md)
- [示例编译命令行](sample-compilation-command-lines.md)
