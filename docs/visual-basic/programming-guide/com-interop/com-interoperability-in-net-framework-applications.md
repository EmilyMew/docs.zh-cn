---
title: .NET Framework 应用程序中的 COM 互操作性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: 6e8b4eba40cc1872cb289ca120679bb951f2652a
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920800"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>.NET Framework 应用程序中的 COM 互操作性 (Visual Basic)

当你想要在同一个应用程序中使用 COM 对象和.NET Framework 对象时，您需要解决对象存在于内存中的差异。 .NET Framework 对象位于托管内存中 — 由公共语言运行时控制的内存，并根据需要运行时可能会移动。 COM 对象位于非托管内存中，不应将移动到另一个内存位置。 Visual Studio 和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]提供工具来控制这些交互托管和非托管组件。 有关托管代码的详细信息，请参阅[公共语言运行时](../../../standard/clr.md)。

除了.NET 应用程序中使用 COM 对象，您可能还想要使用 Visual Basic 开发从 com。 通过非托管代码可访问的对象

此页面上的链接提供有关 COM 和.NET Framework 对象之间的交互的详细信息。

## <a name="related-sections"></a>相关章节

| | |
|---------|---------|
| [COM 互操作](../../../visual-basic/programming-guide/com-interop/index.md) | 提供指向介绍在 Visual Basic 中，包括 COM 对象、 ActiveX 控件、 Win32 Dll，托管的对象和继承的 COM 对象的 COM 互操作性的主题。 |
| [与非托管代码交互操作](../../../framework/interop/index.md) | 简要介绍了一些托管和非托管代码之间的交互问题并提供进一步研究的链接。 |
| [COM 包装](../../../framework/interop/com-wrappers.md) | 讨论运行时可调用包装器，它允许托管的代码调用 COM 方法，以及 COM 可调用包装，允许 COM 客户端调用.NET 对象的方法。 |
| [高级 COM 互操作性](../../../framework/interop/index.md) | 提供指向介绍 COM 互操作性方面包装、 异常、 继承、 线程、 事件、 转换和封送处理主题。 |
| [Tlbimp.exe（类型库导入程序）](../../../framework/tools/tlbimp-exe-type-library-importer.md) | 讨论的工具，可用于将转换为公共语言运行时程序集中的等效定义 COM 类型库中找到的类型定义。 |