---
title: 开发 Windows 服务应用程序
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
author: ghogen
ms.openlocfilehash: 32aa2c1c4cd31e4591c9fa30c05ebe61058f94c5
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442628"
---
# <a name="develop-windows-service-apps"></a>开发 Windows 服务应用

使用 Visual Studio 或 .NET Framework SDK，可以通过创建作为服务安装的应用程序来轻松创建服务。 这种类型的应用程序称为 Windows 服务。 借助框架功能，可以创建、安装服务，启动、停止服务并及控制服务的行为。

> [!NOTE]
> 在 Visual Studio 中，可以使用 Visual C# 或 Visual Basic 在托管代码中创建服务，如果需要，可以与现有的 C++ 代码进行互操作。 或者，可以通过使用 [ATL 项目向导](/cpp/atl/reference/atl-project-wizard)在本机 C++ 中创建 Windows 服务。

## <a name="in-this-section"></a>本节内容

[Windows 服务应用程序介绍](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)

提供 Windows 服务应用程序、服务生存期以及服务应用程序与其他常见项目类型的区别的概述。

[演练：在组件设计器中创建 Windows 服务应用程序](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

提供在 Visual Basic 和 Visual C# 中创建服务的示例。

[服务应用程序编程体系结构](../../../docs/framework/windows-services/service-application-programming-architecture.md)

介绍服务编程中使用的语言元素。

[如何：创建 Windows 服务](../../../docs/framework/windows-services/how-to-create-windows-services.md)

介绍使用 Windows 服务项目模板创建和配置 Windows 服务的过程。

## <a name="related-sections"></a>相关章节

<xref:System.ServiceProcess.ServiceBase> - 介绍用于创建服务的 <xref:System.ServiceProcess.ServiceBase> 类的主要功能。

<xref:System.ServiceProcess.ServiceProcessInstaller> - 介绍 <xref:System.ServiceProcess.ServiceProcessInstaller> 类的功能，该类与 <xref:System.ServiceProcess.ServiceInstaller> 类一起用于安装和卸载服务。

<xref:System.ServiceProcess.ServiceInstaller> - 介绍 <xref:System.ServiceProcess.ServiceInstaller> 类的功能，该类与 <xref:System.ServiceProcess.ServiceProcessInstaller> 类一起用于安装和卸载服务。

[从模板创建项目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) - 介绍本章中使用的项目类型以及如何从中进行选择。
