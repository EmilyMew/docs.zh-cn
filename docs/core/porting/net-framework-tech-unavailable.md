---
title: .NET Framework 技术在 .NET Core 上不可用
description: 了解在 .NET Core 上不可用的 .NET Framework 技术
author: cartermp
ms.author: mairaw
ms.date: 12/07/2018
ms.openlocfilehash: be55cd1d1c67b0542c8474d1b2e47f6752f658a2
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185800"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>.NET Framework 技术在 .NET Core 上不可用

一些适用于 .NET Framework 库的技术不可用于 .NET Core，例如 AppDomains、远程处理、代码访问安全性 (CAS) 和安全透明度。 如果库依赖于这些技术中的一个或多个，请考虑使用下面所述的替代方法。 有关 API 兼容性的详细信息，CoreFX 团队在 GitHub 上列出了[行为更改/兼容性破坏和弃用的/旧 API 列表](https://github.com/dotnet/corefx/wiki/ApiCompat)。

当前未实现某个 API 或技术并不因此意味着有意不对其提供支持。 应该首先在 GitHub 存储库中搜索 .NET Core，以确定遇到的特定问题是否为有意设计，但是如果找不到这样的指示符，请在 GitHub 的 [dotnet/corefx 存储库问题](https://github.com/dotnet/corefx/issues)中提交问题，以请求特定 API 和技术。 [问题中的移植请求](https://github.com/dotnet/corefx/labels/port-to-core)已标有 `port-to-core` 标签。

## <a name="appdomains"></a>AppDomain

应用程序域 (AppDomain) 可将应用相互隔离。 AppDomain 需要运行时支持并且通常价格昂贵。 不支持创建额外应用程序域... 我们不计划在将来添加此功能。 对于代码隔离，建议将流程分隔开来或将容器用作一种替代方法。 对于动态加载的程序集，我们建议使用新的 <xref:System.Runtime.Loader.AssemblyLoadContext> 类。

.NET Core 公开了一些 <xref:System.AppDomain> API 曲面，以便可以更轻松地从 .NET Framework 进行代码迁移。 一些 API 可正常工作（例如 <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>），一些成员不会执行任何操作（例如 <xref:System.AppDomain.SetCachePath%2A>），也有一些会引发 <xref:System.PlatformNotSupportedException>（例如 <xref:System.AppDomain.CreateDomain%2A>）。 对照 [dotnet/corefx GitHub 存储库](https://github.com/dotnet/corefx)中的 [`System.AppDomain` 引用源](https://github.com/dotnet/corefx/blob/master/src/Common/src/CoreLib/System/AppDomain.cs)检查所使用的类型，确保选择与已实现的版本相匹配的分支。

## <a name="remoting"></a>远程处理

.NET 远程处理被认为是存在问题的体系结构。 它用于进行跨 AppDomain 的通信，该通信现已不再受支持。 同样，远程处理也需要运行时支持，进行维护的成本较高。 出于这些原因，.NET Core 不支持 .NET 远程处理，并且我们不计划在将来添加对它的支持。

对于跨进程通信，可将进程间通信 (IPC) 机制视为远程处理的备用方案，如 <xref:System.IO.Pipes> 或 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 类。

对于跨计算机的通信，可将基于网络的解决方案用作备用方案。 最好使用低开销纯文本协议，例如 HTTP。 此处，ASP.NET Core 使用的 Web 服务器 [Kestrel Web 服务器](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel)是一个选择。 也可考虑将 <xref:System.Net.Sockets> 用于基于网络的跨计算机的方案。 有关更多选项，请参阅 [.NET 开放源代码开发人员项目：消息传送](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging)。

## <a name="code-access-security-cas"></a>代码访问安全性 (CAS)

沙盒依赖为托管应用程序或库使用或运行提供资源的运行时或框架进行限制，其[在 .NET Framework 上不受支持](~/docs/framework/misc/code-access-security.md)，因此在 .NET Core 上也不受支持。 .NET Framework 和运行时中存在太多发生特权提升以继续将 CAS 视为安全边界的情况。 此外，CAS 使实现更加复杂，通常会对无意使用它的应用程序造成正确性-性能影响。

可使用操作系统提供的安全边界，例如虚拟化、容器或具有最少特权集的用于运行进程的用户帐户。

## <a name="security-transparency"></a>安全透明度

与 CAS 相似，借助安全透明度可以以声明性方式将沙盒代码与安全关键代码隔离，但是[不再支持将它作为安全边界](~/docs/framework/misc/security-transparent-code.md)。 Silverlight 大规模使用了此功能。 

可使用操作系统提供的安全边界，例如虚拟化、容器或用于运行进程的用户帐户具有最少的一组特权。

>[!div class="step-by-step"]
>[下一页](third-party-deps.md)
