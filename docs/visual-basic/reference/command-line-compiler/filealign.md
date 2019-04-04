---
title: -filealign
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
ms.openlocfilehash: 9a844515a4596064937762ac05b850463f1b5e14
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819172"
---
# <a name="-filealign"></a>-filealign
指定输出文件各节的对齐位置。  
  
## <a name="syntax"></a>语法  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a>自变量  
 `number`  
 必需。 一个值，输出文件中指定的节的对齐方式。 有效值为 512、1024、2048、4096 和 8192。 这些值以字节为单位。  
  
## <a name="remarks"></a>备注  
 可以使用`-filealign`选项以在输出文件中指定的节的对齐方式。 节是包含代码或数据的可移植可执行文件 (PE) 文件中的连续内存块。 `-filealign`选项，可以编译应用程序时使用了非标准的对齐方式; 大多数开发人员不需要使用此选项。  
  
 每一节对齐的倍数的边界上`-filealign`值。 没有固定的默认值。 如果`-filealign`未指定，则编译器在编译时会选取默认值。  
  
 通过指定节的大小，可以更改输出文件的大小。 修改节的大小可能对将在较小设备上运行的程序有用。  
  
> [!NOTE]
>  `-filealign`选项不适用于从 Visual Studio 开发环境中，仅当从命令行编译时便可。  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
