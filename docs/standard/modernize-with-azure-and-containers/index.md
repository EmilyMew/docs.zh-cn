---
title: 更新现有.NET 应用程序与 Azure 云和 Windows 容器 （第二版）
description: 了解如何迁移并更新现有应用程序对 Azure 云以及与此电子书的容器。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 68d5ce7ad71fae5ed3e1460c56581dd69c3925f3
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675921"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>更新现有.NET 应用程序使用 Azure 云和 Windows 容器 （第二版）

![实现现代化.NET 应用程序指南的封面图像。](./media/index/web-application-guide-cover-image.png)

发布者  
Microsoft Press 和 Microsoft DevDiv  
Microsoft Corporation 的部门  
One Microsoft Way  
Redmond, Washington 98052-6399  

版权所有 © 2018 Microsoft Corporation  

保留所有权利。 未经发布者书面许可，不得以任何形式或任何方式复制本书中的任何内容。

本书位于免费电子书 （电子图书） 可通过 microsoft 的多个通道的形式如 <https://dot.net/architecture> 。

若要了解本书的相关问题，请发送电子邮件至 [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)

本书“按原样”提供，表达作者的观点和看法。 视图、 观点和本书，包括 URL 和其他 Internet 网站参考中, 表达的信息可能会更改恕不另行通知。

本书中提及的一些示例仅用于说明，纯属虚构。 不存在任何实际关联或联系，请勿妄加推断。

Microsoft 和 <https://www.microsoft.com> 上“商标”网页列出的商标是 Microsoft 集团公司的商标。 所有其他标记均为其各自所有者的财产。

作者:
> **Cesar de la Torre**，Sr.PM，.NET 产品团队，Microsoft corp.

参与者和审阅者：
> **Scott Hunter**，Microsoft .NET 团队的合作伙伴总监项目经理  
> **Paul Yuknewicz**，Microsoft Visual Studio Tools 团队的主要项目经理  
> **Lisa Guthrie**，Sr.PM，Microsoft Visual Studio Tools 团队  
> **Ankit Asthana**，Microsoft .NET 团队的主要项目经理  
> **Unai Zorrilla**，Plain Concepts 的开发者领导  
> **Javier Valero**，Grupo Solutio 的首席运营官  

## <a name="introduction"></a>介绍

如果你决定要使 web 应用程序或服务实现现代化，并将它们移动到云，一定不必完全重新构建您的应用程序。 重构应用程序即可使用微服务之类的高级的方法并不总是一个选项，由于成本和时间约束。 根据应用程序的类型，重构应用程序也可能不需要。 为了优化组织云迁移策略的成本效益，必须考虑业务和应用的需求。 需要确定：

- 哪些应用需要转换或重新架构。

- 哪些应用只需部分更新。

- 哪些应用能直接“直接迁移”到云。

## <a name="about-this-guide"></a>关于本指南

本指南主要介绍初次更新的现有 Microsoft.NET Framework web 或面向服务的应用程序，这意味着将工作负荷移动到更高版本或更现代的环境，而不会显著改变应用程序的代码的操作和基本体系结构。 

本指南还强调您的应用程序迁移到云并部分更新应用使用一组特定的新技术和方法，如 Windows 容器和 Azure 支持 Windows 容器中的相关的计算平台的优势。

## <a name="path-to-the-cloud-for-existing-net-applications"></a>将现有 .NET 应用程序迁移到云的途径

组织通常选择移动到云来使其应用程序获得敏捷性和速度。 只需几分钟即可在云中设置数千台服务器 (VM)，而设置本地服务器通常需要数周。

将应用程序迁移到云没有普遍通用的策略。 合适的迁移方法由组织的需求和优先考虑事项，以及要迁移的应用程序种类决定。 并非所有应用程序都保证可以移动到平台即服务 ([PaaS](https://azure.microsoft.com/overview/what-is-paas/)) 模型或开发[云原生](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications)应用程序模型。 许多情况下都可根据业务需求采用阶段性或递增性方法将资产移动到云。

对于具有最佳长期敏捷性和为组织的值的现代应用程序，您可能会受益于投入*云原生*应用程序体系结构。 但是，对于现有的应用程序或遗留资产，关键是将其移动到云，从而实现显著的好处时花费最少的时间和金钱 （无重新架构或代码更改）。

图 1-1 显示了采用递增性方法将现有 .NET 应用程序移动到云时可能使用的途径。

 ![现有 .NET 应用程序和服务的更新途径](./media/image1-1.png)

> **图 1-1**。 现有 .NET 应用程序和服务的更新途径

每种迁移方法的优点和使用原因各不相同。 可以选择一种方法将应用迁移到云，也可以从多种方法中选择某些组件。 单个应用程序不限于单一的方法或成熟度状态。 例如，常见的混合方法将包含某些本地组件以及云中的其他组件。

定义和每个应用程序成熟度级别的简短说明如下所示：

**级别 1:云基础结构就绪**应用程序：您可以在此迁移方法，只需将迁移或重新托管基础结构即服务为你当前的本地应用程序 ([IaaS](https://azure.microsoft.com/overview/what-is-iaas/)) 平台。 应用的组成与之前基本一致，但现在可将它们部署到云中的 VM。
这种简单的迁移通常称为"提升和切换"。 在业界

**级别 2:云优化**应用程序：在此级别而仍无需重新架构或更改重要的代码，可以获得从使用现代技术，例如容器和其他云托管服务在云中运行您的应用程序的其他好处。 通过优化企业开发操作 (DevOps) 流程，可以提高应用程序的敏捷性，以实现更快交付。 通过使用 Windows 容器，基于 Docker 引擎等技术来实现此目的。 容器中删除时在多个阶段中部署应用程序依赖项导致的冲突。 在此成熟度模型中，你可以部署在 IaaS 上的容器或同时使用附加的 PaaS 云托管服务与数据库相关的缓存即服务、 监视和持续集成/持续部署 (CI/CD) 管道。

第三个成熟度级别是云中的最终目标，但对于很多应用它是可选的，并不是本指南的主要重点：

**级别 3:云原生**应用程序：此迁移方法通常是由业务需求和目标更新任务关键型应用程序驱动。 在此级别，使用 PaaS 服务将应用移动到 PaaS 计算平台。 实现[云原生](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications)应用程序和微服务体系结构，以改进应用程序，使其具有长期的敏捷性并扩展至新的限制。 此类更新通常需要专门针对云进行构建。 通常必须编写新代码，尤其是移动到基于云原生应用程序和微服务的模型时。 此方法有助于获得一些益处，这些益处在单片和本地应用程序环境中很难实现。

表 1-1 介绍了选择每种迁移或更新方法的主要优点和原因。

| **云基础结构就绪** <br /> *直接迁移* | **Cloud-Optimized** <br /> *实现现代化* | **Cloud-Native** <br /> *实现现代化、 重构和重写* |
|---|---|---|
| **应用程序的计算目标** |
| 部署到 Azure 中 VM 的应用程序 | 单体或 N 层应用程序部署到 Azure 应用服务、 Azure 容器实例 (ACI)、 虚拟机与容器、 Azure Service Fabric 或 AKS （Azure Kubernetes 服务） | Azure Kubernetes 服务 (AKS)、 Service Fabric 和/或基于 Azure Functions 的无服务器微服务上的容器化微服务。 |
| **数据目标** |
| VM 中的 SQL 或任何关系数据库 | Azure SQL 数据库托管实例或另一个在云中托管的数据库。 | 每个微服务，基于 Azure SQL 数据库、 Azure Cosmos DB 或在云中的另一个托管的数据库的细粒度数据库 |
| **优点**|
| <li>没有任何新的重构代码 <li> 需要的工作量最少，实现快速迁移 <li> Azure 中支持最小公分母 <li> 保证基本可用性 <li> 移动到云后，更容易更新 | <li> 不重新架构 <li> 更改最小代码/配置 <li> 由于容器的原因，改进了部署和 DevOps 发布敏捷性 <li> 增加了密度，降低了部署成本 <li> 应用的可移植性和依赖项 <li> 主机目标的灵活性：PaaS 方法或 IaaS | <li> 架构师的云，则获得最大的好处从云中，但需要新的代码 <li> 微服务云原生方法 <li> 新式任务关键型应用程序，云复原的可高度扩展 <li> 完全托管服务 <li> 优化了规模 <li> 通过子系统优化了自主敏捷性 <li> 基于部署和 DevOps |
| **挑战** |
| <li> 除了转移运营费用或关闭数据中心之外，云价值较小 <li> 少托管：无 OS 或中间件修补;可以使用基础结构解决方案，如 Terraform、 Spinnaker 或 Puppet | <li> 容器化是学习曲线，为开发人员和 IT 运营中一个额外的步骤 <li> DevOps 和 CI/CD 管道通常是必需的这种方法。 如果不是当前的区域性组织中存在，它可能是其他挑战| <li> 有关云本机应用程序和微服务体系结构需要体系结构重建而且通常需要大量的代码重构或重写现代化 （增加了的时间和预算） <li> DevOps 和 CI/CD 管道通常是必需的这种方法。 如果不是当前的区域性组织中存在，它可能是其他挑战|
> **表 1-1**。 现有 .NET 应用程序和服务的更新途径的优势和挑战

### <a name="key-technologies-and-architectures-by-maturity-level"></a>各成熟度级别使用的关键技术和体系结构

.NET Framework 应用程序的初始版本为 .NET Framework 1.0，该版本于 2001 年年底发布。 然后，公司发布了更新的版本（如 2.0、3.5 和 .NET 4.x）。 这些应用程序的大多数运行 Windows Server 和 Internet 信息服务器 (IIS) 上，使用关系数据库中的，如 SQL Server、 Oracle、 MySQL 或任何其他 rdbms 一样。

当今大部分现有 .NET 应用程序可能都基于 .NET Framework 4.x，甚至 .NET Framework 3.5，并使用 Web 框架，如 ASP.NET MVC、ASP.NET Web 窗体、ASP.NET Web API、Windows Communication Foundation (WCF)、ASP.NET SignalR 和 ASP.NET 网页。 这些既定的 .NET Framework 技术都依赖于 Windows。 如果只是简单地迁移旧版应用并希望对应用程序基础结构作出最少的更改，依赖项是一项重要的考虑因素。

图 1-2 显示了三个云成熟度级别中每一个级别所使用的主要技术和体系结构样式：

![用于更新现有 .NET Web 应用程序的每个成熟度级别的主要技术](./media/image1-2.png)

> **图 1-2**。 用于更新现有 .NET Web 应用程序的每个成熟度级别的主要技术

图 1-2 强调了最常见的方案，但在体系结构方面，可能存在许多混合变体。 例如，成熟度模型不仅适用于现有 Web 应用的单片体系结构，还适用于服务方向、N 层以及其他体系结构样式变体。 更高版本的焦点或上一个或另一个体系结构类型和相关的技术的百分比确定您的应用程序的整体成熟度级别。

更新流程中的每个成熟度级别与以下关键技术和方法相关：

- **云基础结构就绪**（重新托管或基本提升和切换）：第一步，许多组织只想快速执行云迁移策略。 在这种情况下，是重新承载的应用程序。 大多数重新托管均可使用 [Azure Migrate](https://aka.ms/azuremigrate) 自动完成，该服务提供指南、见解和机制，帮助迁移到基于 Azure 的云工具（如 [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/) 和 [Azure 数据库迁移服务](https://azure.microsoft.com/campaigns/database-migration/)）。 也可以手动设置重新托管，以便在将旧版应用移动到云时了解关于这些资产的基础结构详细信息。 例如，您可以将应用程序移到 Vm 在 Azure 中进行少量修改甚至修改可能与仅配置做出细微更改。 这种情况下的网络类似于本地环境，尤其是在 Azure 中创建虚拟网络时。

- **云计算得到优化**（托管服务和 Windows 容器）：此模型是有关进行几个重要部署优化，以获得部分显著好处从云，而无需更改应用程序的核心体系结构。 此处的基本步骤是对现有 .NET Framework 应用程序增加 [Windows 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/) 支持。 此重要步骤 （容器化） 不需要触及代码，因此总体的提升和转变工作量较轻。 可以使用 [Image2Docker](https://github.com/docker/communitytools-image2docker-win) 或 Visual Studio 之类的工具，Visual Studio 带有适用于 [Docker](https://www.docker.com/) 的工具。 Visual Studio 自动为 ASP.NET 应用程序和 Windows 容器映像选择智能默认值。 这些工具提供快速内部循环，并提供将容器迁移到 Azure 的快速途径。 部署到多个环境中时，敏捷性得到提高。 然后，转到生产环境，你可以部署到 Windows 容器[用于容器的 Azure Web 应用](https://azure.microsoft.com/services/app-service/containers/)，[Azure 容器实例 (ACI) 和 Windows Server 2016 和容器，如果偏好使用 IaaS 方案的 Azure Vm。 对于稍微复杂多容器应用程序，到业务流程协调程序，如[Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)或[Azure Kubernetes 服务 (AKS/ACS)](https://azure.microsoft.com/services/container-service/)。 在此初次更新期间你还可以添加资产从云中，例如使用之类的工具监视[Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview);使用你的应用程序生命周期的 CI/CD 管道[Azure DevOps 服务](https://visualstudio.microsoft.com/team-services/); 和许多其他数据资源服务在 Azure 中可用。 例如，可以修改单片 Web 应用，该应用最初使用传统 [ASP.NET Web 窗体](https://www.asp.net/web-forms)或 [ASP.NET MVC](https://www.asp.net/mvc) 开发，但现在使用 Windows 容器部署。 使用 Windows 容器时，还需要将数据迁移到 [Azure SQL 数据库托管实例](https://docs.microsoft.com/azure/sql-database/)中的数据库，但不需要更改应用程序的核心体系结构。

- **云原生**:中引入，你应该看待构建[云原生](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications)时你面向的大型复杂应用程序与多个独立的开发团队致力于不同的微服务，可以是应用程序开发和自主部署。 此外，由于每个微服务 granularized 和独立可伸缩性。 这些体系结构方法面临的非常重要的挑战和复杂性，但可以大大简化了云 PaaS 和业务流程协调程序喜欢[Azure Kubernetes 服务 (AKS/ACS)](https://azure.microsoft.com/services/container-service/) （托管 Kubernetes） [Azure 服务Fabric 中，并[Azure Functions](https://azure.microsoft.com/services/functions/)使用无服务器的方法。 所有这些方法 （如微服务和无服务器） 通常要求您针对云构建和编写新代码，经过调整以适应特定的 PaaS 平台的代码或符合特定的体系结构，例如微服务的代码。

图 1-3 显示了每个成熟度级别可使用的内部技术：

![每个更新成熟度级别可使用的内部技术](./media/image1-3.png)

> **图 1-3**。 每个更新成熟度级别可使用的内部技术

## <a name="lift-and-shift-scenario"></a>提升和迁移方案

对于直接迁移，请记住，在应用程序方案中可以使用很多不同的直接迁移变体。 如果仅重新托管应用程序，则可能拥有类似于图 1-4 中所示的方案，在此方案中，仅对应用程序和数据库服务器使用云中的 VM。

![云中纯 IaaS 方案的示例](./media/image1-4.png)

> **图 1-4**。 云中纯 IaaS 方案的示例

## <a name="modernization-scenarios"></a>现代化方案

对于现代化方案中，您可能必须纯云优化应用程序，使用仅从该成熟度级别的元素。 或者，你可能具有某些元素的中间状态应用程序从云基础结构准备就绪并从云计算得到优化的其他元素 (一个"挑选"或混合的模型)，如图 1-5。

![“挑选”方案示例，使用 IaaS 数据库、DevOps 和容器化资产](./media/image1-5.png)

> **图 1-5**。 “挑选”方案示例，使用 IaaS 数据库、DevOps 和容器化资产

接下来，理想的方案的多个现有.NET Framework 应用程序迁移，则无法迁移到云优化应用程序，若要获得一些工作显著的好处。 此方法还设置了云原生，作为可能的未来发展。 图 1-6 显示了一个示例。

![云优化的应用程序方案示例，使用 Windows 容器和托管的服务](./media/image1-6.png)

> **图 1-6**。 云优化的应用程序方案示例，使用 Windows 容器和托管的服务

再进一步，可以通过添加适用于特定方案的几个微服务来扩展现有的云优化应用程序。 这会将您部分推向云原生模型，这不是，当前指南的重点的级别。


## <a name="what-this-guide-does-not-cover"></a>本指南未涵盖的内容

本指南涵盖了一小部分特定的示例方案，如图 1-7 所示。 本指南主要仅在直接迁移方案和从根本上讲，云计算得到优化模型。 在云计算得到优化模型中，.NET Framework 应用程序现代化通过使用 Windows 容器，以及其他组件，如监视和 CI/CD 管道。 每个组件都是确保将应用程序更快地、敏捷地部署到云的基础。

![本指南未介绍云原生](./media/image1-7.png)

> **图 1-7** 本指南未介绍云原生

本指南的重点具有一定的针对性。 它将显示可用于实现的提升和转变现有.NET 应用程序，而无需重新架构，且无需更改代码的路径。 从根本上讲，它演示如何使应用程序云计算得到优化。

本指南不演示如何创建云本机应用程序，如如何改进到微服务体系结构。 若要重新构建您的应用程序或创建基于微服务的全新应用程序，请参阅电子书[.NET 微服务：容器化.NET 应用程序体系结构](https://aka.ms/microservicesebook)。

### <a name="additional-resources"></a>其他资源

- **适用于容器化 Docker 应用程序生命周期使用 Microsoft 平台和工具**（可下载电子书） \
  [https://aka.ms/dockerlifecycleebook](https://aka.ms/dockerlifecycleebook)

- **.NET 微服务：容器化.NET 应用程序体系结构**（可下载电子书） \
  [https://aka.ms/microservicesebook](https://aka.ms/microservicesebook)

- **构建现代 web 应用程序使用 ASP.NET Core 和 Azure** （可下载电子书） \
  [https://aka.ms/webappebook](https://aka.ms/webappebook)

## <a name="who-should-use-this-guide"></a>本指南的目标读者

本指南专为开发人员和解决方案架构师想要使现有的 ASP.NET web 应用程序或基于.NET Framework 中，为交付和发布应用程序灵活性的提高的 WCF 服务实现现代化。

本指南可能也对技术决策者有帮助，例如希望大概了解使用 Windows 容器和使用 Microsoft Azure 部署到云可以获得哪些好处的企业架构师或开发负责人/主管。

## <a name="how-to-use-this-guide"></a>如何使用本指南

本指南解释了需要更新现有应用程序的原因，以及使用 Windows 容器将应用移动到云能获得的具体好处。 本指南前几章的内容适用于架构师和技术决策者，他们只需大概了解，不需要实现和技术分步细节。

本指南最后一章介绍重点针对特定部署方案的多个演练。 本指南提供较短版本的演练，概况各种方案，并突出显示其权益。 完整演练深入到了设置和实现细节，并作为一组 [Wiki 文章](https://github.com/dotnet-architecture/eShopModernizing/wiki)在相同的公共 [GitHub 存储库](https://github.com/dotnet-architecture/eShopModernizing)中发布，该存储库中还存放着相关示例应用（将在下一节讨论）。 关注实现细节的开发者和架构师将对最后一章以及 GitHub 上的分步 Wiki 演练更感兴趣。

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>用于更新旧版应用的示例应用：eShopModernizing

GitHub 上的 [EShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) 存储库提供了两个示例应用程序，用以模拟旧版单片 Web 应用程序。 通过使用 ASP.NET MVC; 开发一个 web 应用通过使用 ASP.NET Web 窗体开发第二个 web 应用和第三个应用程序是具有 WinForms 客户端桌面应用程序使用 WCF 服务后端的 N 层应用。 所有这些应用基于传统.NET Framework。 这些示例应用不使用 .NET Core 或 ASP.NET Core，它们是要更新的现有/旧版 .NET Framework 应用程序。

这些示例应用都有第二个版本，使用新式代码，哪些是非常简单。 两个应用版本之间最重要的差异是第二个版本使用 Windows 容器作为部署选项。 第二个版本中还新增了一些组件，如用于管理映像的 Azure 存储 Blobs、管理安全的 Azure Active Directory，以及用于监视和审核应用程序的 Azure Application Insights。

## <a name="send-your-feedback"></a>提供你的反馈

本指南旨在帮助你了解改进和更新现有.NET web 应用程序的选项。 本指南以及相关示例应用程序不断更新。 你的反馈是欢迎使用 ！ 如有关于本指南的改进建议，请将其发送到 [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)。

>[!div class="step-by-step"]
>[下一页](lift-and-shift-existing-apps-azure-iaas.md)
