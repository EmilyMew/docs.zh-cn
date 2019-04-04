---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: c1824e4a086ecdd4b6a776bd6894f6e003d02867
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822552"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
在编译期间取消显示版权标志和信息性消息。  
  
## <a name="syntax"></a>语法  
  
```  
-nologo  
```  
  
## <a name="remarks"></a>备注  
 如果指定`-nologo`，编译器不会显示版权标志。 默认情况，`-nologo` 是无效的。  
  
> [!NOTE]
>  `-nologo`选项不适用于从 Visual Studio 开发环境中，仅当从命令行编译时便可。  
  
## <a name="example"></a>示例  
 下面的代码编译`T2.vb`，并且不显示版权标志。  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
