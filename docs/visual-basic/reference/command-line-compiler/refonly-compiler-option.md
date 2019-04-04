---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: 4093e98738cf6e41cd450229d82e3672fe9687ec
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819450"
---
# <a name="-refonly-visual-basic"></a>-refonly (Visual Basic)

**-Refonly**选项表示编译的主输出应引用程序集而不是实现程序集。 `-refonly` 参数以无提示方式禁用输出 PDB，因为无法执行引用程序集。

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>语法

```console
-refonly
```

## <a name="remarks"></a>备注

Visual Basic 支持`-refout`切换从版本 15.3 开始。

引用程序集是包含元数据，但没有实现代码的仅限元数据的程序集。 它们包括匿名类型以外的所有内容的类型和成员信息。 使用 `throw null` 主体（而非不使用主体）的原因在于，这样做可以运行和传递 PEVerify（从而验证元数据的完整性）。

引用程序集包括程序集级别[ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute)属性。 可以在源中指定此属性（之后编译器就不需要进行合成）。 由于有此属性中，运行时会拒绝加载用于执行引用程序集 （但仍可在仅限反射上下文中加载）。 在程序集反映的工具需要确保它们的加载为仅反射; 的引用程序集否则，运行时会引发<xref:System.BadImageFormatException>。

`-refonly` 和 [`-refout`](refout-compiler-option.md) 选项互斥。

## <a name="see-also"></a>请参阅

- [/refout](refout-compiler-option.md)
- [Visual Basic 命令行编译器](index.md)
- [示例编译命令行](sample-compilation-command-lines.md)
