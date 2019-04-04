---
title: 程序集内容
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- single-file assemblies
- multifile assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2be1aad4d222917364a57abc93b414af40b1e9ae
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675648"
---
# <a name="assembly-contents"></a>程序集内容
通常，静态程序集可能由以下四个元素组成：  
  
-   [程序集清单](../../../docs/framework/app-domains/assembly-manifest.md)，包含程序集元数据。  
  
-   类型元数据。  
  
-   实现这些类型的 Microsoft 中间语言 (MSIL) 代码。  
  
-   资源集。  
  
 只有程序集清单是必需的，但也需要类型或资源来向程序集提供任何有意义的功能。  
  
 程序集中的这些元素有分组几种方法。 您可以将所有元素分组到单个物理文件中，如下图所示。  
  
 ![显示名为 MyAssembly.dll 的单文件程序集的图表。](./media/assembly-contents/single-file-assembly.gif)  
  
 或者，可以将一个程序集的元素包含在几个文件中。 这些文件可以是应用程序所需的编译代码 (.netmodule)、资源（例如，.bmp 或 .jpg 文件）或其他文件的模块。 在您希望组合以不同语言编写的模块并优化应用程序的下载过程时，可创建一个多文件程序集，优化下载过程的方法是将很少使用的类型放入只在需要时才下载的模块中。  
  
 在下图中，一个假想应用程序的开发人员已选择将一些实用工具代码单独放入另一个模块中，同时在其原文件中保留一个较大的资源文件（在此例中为一个 .bmp 图像）。 .NET Framework 只在文件被引用时下载该文件；通过将很少引用的代码保留在独立于应用程序的文件中来优化代码下载。  
  
 ![显示多文件程序集的图表。](./media/assembly-contents/multifile-assembly-diagram.gif) 
  
> [!NOTE]
>  构成多文件程序集的那些文件实际上并非由文件系统来链接。 它们而是通过程序集清单进行链接，公共语言运行时将这些文件作为一个单元来管理。  
  
 在此插图中，所有三个文件均属于一个程序集，如 MyAssembly.dll 所包含的程序集清单文件中所述。 对于该文件系统，这三个文件是三个独立的文件。 请注意，文件 Util.netmodule 被编译为一个模块，因为它不包含任何程序集信息。 创建程序集之后，已将该程序集清单添加到指示程序集与 Util.netmodule 和 Graphic.bmp 之间关系的 MyAssembly.dll 中。  
  
 现在设计源代码时，你会作出有关如何将应用程序的功能划分到一个或多个文件的明确的决定。 在设计 .NET Framework 代码时，你也将作出类似的决定，即如何将应用程序的功能划分到一个或多个程序集中。  
  
## <a name="see-also"></a>请参阅
- [Assemblies in the Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)（公共语言运行时中的程序集）
- [程序集清单](../../../docs/framework/app-domains/assembly-manifest.md)
- [程序集安全注意事项](../../../docs/framework/app-domains/assembly-security-considerations.md)
