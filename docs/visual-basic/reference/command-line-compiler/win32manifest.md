---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: bd9a708b99d11b90e47c3413bb0003ce2def13a1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833708"
---
# <a name="-win32manifest-visual-basic"></a>-win32manifest (Visual Basic)
标识用户定义的 Win32 应用程序清单文件要嵌入到项目的可移植可执行 (PE) 文件。  
  
## <a name="syntax"></a>语法  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`fileName`|自定义清单文件的路径。|  
  
## <a name="remarks"></a>备注  
 默认情况下，Visual Basic 编译器嵌入指定 asInvoker 的请求的执行级别的应用程序清单。 它在其中可执行文件生成，通常使用 Visual Studio 时的 bin\Debug 或 bin\Release 文件夹位于同一文件夹中创建清单。 如果你想要提供自定义清单，例如若要指定请求的执行级别的最高可用性或 requireAdministrator，使用此选项以指定的文件的名称。  
  
> [!NOTE]
>  此选项和[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)是互斥的选项。 如果尝试在同一命令行中使用这两个选项，则会生成错误。  
  
 如果应用程序没有用于指定请求执行级别的应用程序清单，将受到 Windows Vista 的用户帐户控制功能下的文件/注册表虚拟化的影响。 有关虚拟化的详细信息，请参阅 [Windows Vista 上的 ClickOnce 部署](/visualstudio/deployment/clickonce-deployment-on-windows-vista)。  
  
 如果以下条件之一为 true，你的应用程序会受到虚拟化：  
  
1.  您使用`-nowin32manifest`选项，并且不提供清单，在更高版本的生成步骤中或者在 Windows 资源 (.res) 文件通过使用`-win32resource`选项。  
  
2.  提供的自定义清单未指定请求执行级别。  
  
 Visual Studio 创建默认 .manifest 文件，并将它与可执行文件一起存储在“调试”和“发布”目录中。 您可以查看或编辑默认应用程序清单文件，方法是单击**查看 UAC 设置**上**应用程序**项目设计器中的选项卡。 有关详细信息，请参阅 [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)（应用程序页、项目设计器 (Visual Basic)。  
  
 您可以通过使用提供的应用程序清单作为自定义后期生成步骤或作为 Win32 资源文件的一部分`-nowin32manifest`选项。 如果希望应用程序受到 Windows Vista 的文件或注册表虚拟化的影响，请使用该选项。 这将阻止编译器创建并在 PE 文件中嵌入默认清单。  
  
## <a name="example"></a>示例  
 下面的示例演示了 Visual Basic 编译器插入到 PE 默认清单。  
  
> [!NOTE]
>  编译器将插入到清单 XML 的标准应用程序名称 MyApplication.app。 这是一种使应用程序可以在 Windows Server 2003 Service Pack 3 上运行的解决方法。  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
