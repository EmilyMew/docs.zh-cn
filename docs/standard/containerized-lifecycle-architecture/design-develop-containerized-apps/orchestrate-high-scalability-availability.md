---
title: 协调安排微服务和多容器应用程序，实现高可伸缩性和高可用性
description: 实际的生产应用程序必须部署和使用业务流程协调程序处理的运行状况、 工作负荷和所有容器的生命周期管理。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 834e0b91a596f489c10e4eb11b0de2b5eaeb9f1c
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58466395"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>协调安排微服务和多容器应用程序，实现高可伸缩性和高可用性

使用业务流程协调程序的生产就绪应用程序至关重要如果基于微服务应用程序或将其拆分到多个容器的不同而不同。 如前所述，在基于微服务的方法中，每个微服务均拥有其模型和数据，如此从开发和部署的角度来看，它便是具有自主性。 但即使拥有由多个服务组成的更传统的应用程序（如 SOA），也将拥有多个容器或服务，这些容器或服务中包含需要作为分布式系统部署的单个业务应用程序。 这类系统的扩展和管理非常复杂；因此，如果想要拥有生产就绪且可缩放的多容器应用程序，则必须使用业务流程协调程序。

图 4-6 说明了部署到多个微服务 （容器） 组成的应用程序的群集。

![群集中的组合 Docker 应用程序：为每个服务实例使用一个容器。 Docker 容器是“部署单元”，一个容器是 Docker 的一个实例。一个主机会处理许多容器](./media/image6.png)

**图 4-6**。 容器群集

它看上去类似于逻辑方法。 但是，您怎样处理负载平衡、 路由和安排这些组合式应用程序？

Docker 命令行接口 (CLI) 满足需求的管理一台主机上的一个容器，但管理多个容器的更复杂的分布式应用程序的多个主机上部署时，这个过程很短。 在大多数情况下，需要一个管理平台，将自动启动容器、 扩展具有多个实例，每个映像的容器、 挂起，或需要并且在理想情况下还控制访问资源，如网络和数据的方式时关闭它们存储。

超过单个容器或简单的组合式的应用和推动与微服务的大型企业应用程序的管理，则必须转向业务流程和群集平台。

从体系结构和开发的角度看，如果你是构建大型企业，基于微服务的应用程序，务必了解以下平台和产品的支持高级的方案：

- **群集和业务流程协调程序。** 当您需要向外扩展应用程序跨多个 Docker 主机，如使用大型基于微服务的应用程序，很重要，以便能够管理所有这些主机作为单个群集通过抽象化基础平台的复杂性。 这就是容器群集和业务流程协调程序所提供的功能。 业务流程协调程序的示例包括 Azure Service Fabric 和 Kubernetes。 Kubernetes 通过 Azure Kubernetes 服务在 Azure 中提供。

- **计划程序。** *计划*意味着管理员能够启动容器在群集中，因此，计划程序还提供用于执行此操作的用户界面的功能。 群集计划程序具有多个职责：高效使用群集资源、设置用户提供的约束、有效负载均衡节点或主机间的容器，以及在提供高可用性的同时强力解决错误。

群集和计划程序的概念密切相关，因此不同供应商提供的产品通常具有这两套功能。 下面的部分显示的最重要的平台和软件可供选择群集和计划程序。 在 Azure 等公有云中广泛提供这些业务流程协调程序。

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>适用于容器群集、业务流程和计划的软件平台

| Platform | 注释 |
|:---:|:---|
| **Kubernetes** <br/> ![Kubernetes 徽标](./media/kubernetes-logo.png) | [*Kubernetes*](https://kubernetes.io/) 是一款开源产品，提供各种功能，从群集基础结构和容器计划到安排功能均涵盖在内。 它能实现跨主机群集自动部署、缩放以及执行各种应用程序容器操作。 <br/> <br/> Kubernetes 提供以容器为中心的基础结构，将应用程序容器分组为逻辑单元，以便管理和发现。 <br/> <br/> Kubernetes 在 Linux 中的运用已发展成熟，但在 Windows 中相对较弱。 |
| **Azure Kubernetes Service (AKS)** <br/> ![Azure Kubernetes 服务徽标](./media/aks-logo.png) | [Azure Kubernetes 服务 (AKS)](https://azure.microsoft.com/services/kubernetes-service/) 是 Azure 中的托管 Kubernetes 容器业务流程服务，简化了 Kubernetes 群集的管理、部署和操作。 |
| **Azure Service Fabric** <br/> ![Azure Service Fabric 徽标](./media/service-fabric-logo.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) 是用于生成应用程序的 Microsoft 微服务平台。 它是服务的[业务流程协调程序](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction)，可创建计算机群集。 Service Fabric 可将服务作为容器或纯进程进行部署。 它甚至可以在同一应用程序和群集中将进程中的服务与容器中的服务进行组合。 <br/> <br/> Service Fabric 群集可以在 Azure 中、本地或任意云中部署。 但是，Azure 中的部署使用托管方法进行了简化。 <br/> <br/> Service Fabric 提供其他可选的规定 [Service Fabric 编程模型](https://azure.microsoft.com/documentation/articles/service-fabric-choose-framework/)（如[有状态服务](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-services-introduction/)和 [Reliable Actors](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-actors-introduction/)）。 <br/> <br/> Service Fabric 在 Windows 中的运用已经成熟（已在 Windows 中发展多年），但在 Linux 中相对较弱。 <br/> <br/> 自 2017 年以来，Service Fabric 同时支持 Linux 和 Windows 容器。 |
| **Azure Service Fabric Mesh** <br/> ![Azure Service Fabric 网格徽标](./media/azure-service-fabric-mesh-logo.png) | [*Azure Service Fabric Mesh* ](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview)提供相同的可靠性、 关键任务性能和可扩展性是 Service Fabric 中，但还提供完全托管且无服务器平台。 无需管理群集、虚拟机、存储或网络配置。 只需专注于应用程序的开发。 <br/> <br/> *Service Fabric Mesh*支持 Windows 和 Linux 容器，您可以使用任何编程语言和框架所选的开发。

## <a name="using-container-based-orchestrators-in-azure"></a>在 Azure 中使用基于容器的业务流程协调程序

多个云供应商提供 Docker 容器支持以及 Docker 群集和业务流程支持，包括 Azure、 Amazon EC2 容器服务和 Google 容器引擎。 Azure 提供 Docker 群集和业务流程协调程序支持通过 Azure Kubernetes 服务 (AKS)、 Azure Service Fabric 和 Azure Service Fabric 网格。

## <a name="using-azure-kubernetes-service"></a>使用 Azure Kubernetes 服务

Kubernetes 群集汇集多个 Docker 主机，并将它们作为单个虚拟 Docker 主机公开，因此可将多个容器部署到群集和横向扩展与任意数量的容器实例。 该群集将处理可伸缩性、运行状况等所有复杂的管理任务。

AKS 提供了一种方法，可在 Azure 中简化虚拟机（预配置为运行容器化应用程序）群集的创建、配置和管理。 通过使用常用开源计划和业务流程工具的优化配置，AKS 能够利用现有技能或大量不断增长的社区专业知识，在 Microsoft Azure 上部署和管理基于容器的应用程序。

Azure Kubernetes 服务优化了专门针对 Azure 的常用 Docker 群集开源和技术的配置。 可以获得一个开放的解决方案，该解决方案为容器和应用程序配置提供可移植性。 用户选择主机的大小和数量以及业务流程协调程序工具，然后 AKS 可处理其他操作。

![Kubernetes 群集结构：有一个处理 DNS、计划程序、代理等的主节点，以及多个托管容器的工作节点。](media/image36.png)

图 4-7。 Kubernetes 群集的简化结构和拓扑

图 4-7 显示了其中一个主节点 (VM) 控制大部分协调的群集，并可以将容器部署到其他节点作为从应用程序角度来看一个池管理的 Kubernetes 群集结构。 这样，你可以扩展到数千或甚至数万个容器。

## <a name="development-environment-for-kubernetes"></a>Kubernetes 的开发环境

在开发环境中的[Docker 在 2018 年 7 月宣布](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/)，Kubernetes 还可以运行在单个开发计算机 （Windows 10 或 macOS） 中通过仅安装[Docker 桌面](https://www.docker.com/community-edition)。 可以在稍后部署到云 (AKS) 进行进一步集成测试，如图 4-8 中所示。

![Docker 于 2018 年 7 月宣布通过 Docker 桌面对 Kubernetes 群集进行开发计算机支持。](media/kubernetes-development-environment.png)

**图 4-8**。 在开发计算机和云中运行 Kubernetes

## <a name="get-started-with-azure-kubernetes-service-aks"></a>开始使用 Azure Kubernetes 服务 (AKS)

若要开始使用 AKS，你部署 AKS 群集从 Azure 门户或通过使用 CLI。 有关部署 Azure 容器服务群集的详细信息，请参阅[部署 Azure Kubernetes 服务 (AKS) 群集](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)。

作为 AKS 的一部分，默认安装的任何软件都不收费。 所有默认选项都通过开源软件实现。 AKS 可用于 Azure 中的多个虚拟机。 仅针对所选的计算实例以及使用的其他基础结构资源（如存储和网络）收取费用。 AKS 本身不会以增量方式收费。

对于进一步实现部署到 Kubernetes 信息基于`kubectl`和原始`.yaml`文件，请参阅上的文章[AKS （Azure Kubernetes 服务） 中设置 eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service))。

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>使用 Helm 图表部署到 Kubernetes 群集

当应用程序部署到 Kubernetes 群集，可以使用原始`kubectl.exe`CLI 工具，使用部署文件基于本机格式 (`.yaml`文件)，如前面在上一节中所述。 但是，对于更复杂的 Kubernetes 应用程序（如部署基于微服务的复杂应用程序时），建议使用 [Helm](https://helm.sh/)。

Helm 图表可帮助你定义，版本、 安装、 共享、 升级过程中或即使最复杂 Kubernetes 应用程序回滚。

更进一步，也建议使用 Helm 用法，因为 Azure 中的其他 Kubernetes 环境（如 [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces)）也基于 Helm 图表。

由维护 helm[云本机计算基础 (CNCF)](https://www.cncf.io/)与 Microsoft、 Google、 Bitnami 和 Helm 参与者社区协作。

有关进一步实现信息 Helm 图表和 Kubernetes，请参阅文章上[使用 Helm 图表，以便部署到 AKS eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts)。

## <a name="use-azure-dev-spaces-for-you-kubernetes-application-lifecycle"></a>为您 Kubernetes 应用程序生命周期中使用 Azure 开发人员空格

[Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) 为团队提供快速的迭代 Kubernetes 开发体验。 通过尽可能少的开发计算机设置，便可以直接在 Azure Kubernetes 服务 (AKS) 中以迭代方式运行和调试容器。 你可以开发在 Windows、 Mac 或 Linux 使用 Visual Studio、 Visual Studio Code 中或在命令行等熟悉的工具。

如前文所述，Azure 开发人员空格部署基于容器的应用程序时使用 Helm 图表。

Azure 开发人员空间可帮助开发团队会在 Kubernetes 上提高工作效率，因为它允许您快速迭代，而只需使用 Visual Studio 2017 或 Visual Studio Code 调试直接在 Azure 中的全局 Kubernetes 群集中的代码。 Azure 中的这一 Kubernetes 群集是共享的托管 Kubernetes 群集，因此团队可以通过协作方式一起工作。 可以独立开发代码，然后部署到全局群集并对其他组件进行端到端测试，无需复制或模拟依赖项。

图 4-9、 中所示中 Azure 开发人员空间的最区别性功能是创建可以运行集成到群集中的全局部署的其余部分的空间的功能。

![Azure Dev Spaces 可以通过透明方式混合搭配生产微服务与开发容器实例，以便简化新版本的测试。](media/image38.png)

**图 4-9**. 在 Azure Dev Spaces 中使用多个空间

基本上，可以设置共享的开发空间在 Azure 中。 每个开发人员可以专注于只是其一部分应用程序，并可以以迭代方式开发已包含所有其他服务的开发空间中的"预已提交的"代码和云资源依赖于其方案。 依赖项始终保持最新，开发者能够以真实反映生产的方式进行工作。

Azure 开发人员空间提供了一个空格，可用于处理隔离，无需担心会干扰你的团队成员的概念。 此功能基于 URL 前缀;如果容器的请求 URL 中使用适用于开发人员空间前缀，Azure 开发人员空格将运行的容器的部署了该空间的特殊版本，如果存在。 否则，会运行全局/合并版本。

您可以看到[eShopOnContainers Azure 开发人员空间上的 wiki 页](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.2-Using-Azure-Dev-Spaces-and-AKS)若要获取上一个具体示例的实际视图。

详细信息，请参阅文章在[使用 Azure 开发人员空格进行团队开发](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore)。

## <a name="additional-resources"></a>其他资源

- **Azure Kubernetes 服务 (AKS) 入门** \
  [https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)

- **Azure Dev Spaces** \
  [https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces)

- **Kubernetes。** 官方网站。 \
  [https://kubernetes.io/](https://kubernetes.io/)

## <a name="using-azure-service-fabric"></a>使用 Azure Service Fabric

Azure Service Fabric 源于从提供的服务交付"盒子"产品，通常是单一式样式中，Microsoft 的转换。 构建和运营大型服务规模，如 Azure SQL 数据库、 Azure Cosmos DB、 Azure 服务总线或 Cortana 的后端的体验成就了 Service Fabric。 越来越多的服务采用了该平台，它随着时间不断演变。 Service Fabric 不仅需要在 Azure 上运行，还需在独立的 Windows Server 部署上运行，这一点十分重要。

Service Fabric 旨在解决如何构建和运行服务，并有效利用基础结构资源等难题，让团队能够使用微服务方法来解决业务问题。

Service Fabric 提供了两个宽广区域，可帮助构建使用微服务方法的应用程序：

- 提供各种系统服务的平台，可用于部署、缩放、升级、检测、重新启动失败的服务、发现服务位置、管理状态和监视健康状况。 实际上，这些服务具备了很多前面介绍的微服务的特征。

- 有助于将应用程序构建为微服务的编程 API 或框架：[Reliable Actors 和 Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)。 开发人员可选择任何代码来构建微服务，但这些 API 可简化构建工作，且更深入地与平台集成。 这样开发人员就可获得运行状况信息和诊断信息，也可利用可靠的状态管理。

Service Fabric 未指定服务构建方式，开发人员可使用任何技术。 但它内置了编程 API，可简化微服务的构建。

所示图 4-10，您可以创建和运行 Service Fabric 中的微服务，作为简单进程也作为 Docker 容器。 此外还可在同一 Service Fabric 群集中混合基于容器的微服务与基于进程的微服务。

![比较 Azure service Fabric 群集：为每个节点在其中运行的每个微服务; 一个进程的进程的微服务微服务作为容器的每个节点在 Docker 运行使用多个容器，每个微服务的一个容器。](./media/azure-service-fabric-cluster-types.png)

**图 4-10**。 在 Azure Service Fabric 中将微服务部署为进程或容器

基于 Linux 和 Windows 主机的 Service Fabric 群集可分别运行 Docker Linux 容器和 Windows 容器。

有关 Azure Service Fabric 中容器支持的最新信息，请参阅 [Service Fabric 和容器](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)。

Service Fabric 是一个平台，一个很好示例，您可以在其中定义的不同逻辑体系结构 （业务微服务或界定的上下文） 与物理实现。 例如，如果您实现[有状态 Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)中[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)，在下一部分介绍"[无状态与有状态微服务](#stateless-versus-stateful-microservices)，"有多个物理服务具有一个业务微服务概念。

如图 4-10，并从逻辑/业务微服务角度看，实现 Service Fabric 有状态可靠服务时的考虑中所示，您通常需要实现两个层的服务。 第一层是后端有状态可靠服务，用于处理多个分区（每个分区均为一项有状态服务）。 第二层是前端服务或网关服务，负责跨多个分区或有状态服务实例进行路由，聚合数据。 该网关服务还处理访问后端服务的客户端通信，通信带有重试循环。 如果实现自定义服务，则其称为网关服务；或者，还可使用现成的 Service Fabric [反向代理](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)。

![Service Fabric 具有规定在容器中支持多个有状态 reliable services。](./media/service-fabric-stateful-business-microservice.png)

**图 4-11**。 具有多个有状态服务实例和自定义网关的前端业务微服务

在任何情况下，当你使用 Service Fabric 有状态 Reliable Services 时，也可以逻辑或业务微服务 （边界上下文） 的多个物理服务组成。 每个这些、 网关服务和分区服务就可以实现为 ASP.NET Web API 服务，图 4-11 所示。

在 Service Fabric 中，可对成组服务进行分组，并将其部署为 [Service Fabric 应用程序](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model)，即业务流程协调程序或群集的打包和部署单元。 因此，Service Fabric 应用程序同样可映射到该自治业务和逻辑微服务边界或边界上下文，这样开发人员就可以自主部署这些服务。

### <a name="service-fabric-and-containers"></a>Service Fabric 和容器

对于 Service Fabric 中的容器，开发人员也可在 Service Fabric 群集中的容器映像内部署服务。 如图 4-12 所示，大多数情况下将仅有一个容器，每个服务。

![Service Fabric 应用程序可以运行访问外部数据库的多个容器，并且整个集将是业务微服务的逻辑边界](./media/azure-service-fabric-business-microservice.png)

图 4-12。 Service Fabric 中具有多个服务（容器）的业务微服务

但是，Service Fabric 中也可能有所谓的“sidecar”容器（两个容器必须一同部署为逻辑服务）。 重要的是，业务微服务是多个内聚元素的逻辑边界。 在许多情况下，它可能是具有单个数据模型的单个服务，但在其他一些情况下，也可能具有多个物理服务。

图 4-13 中所示，请注意，可以混合使用进程中的服务和容器，在同一 Service Fabric 应用程序的服务。

![在同一个节点中运行服务和容器 service fabric 应用程序。](./media/business-microservice-mapped-to-service-fabric-application.png)

图 4-13。 映射到含容器和有状态服务的 Service Fabric 应用程序的业务微服务

有关 Azure Service Fabric 中容器支持的详细信息，请参阅 [Service Fabric 和容器](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)。

## <a name="stateless-versus-stateful-microservices"></a>无状态微服务与有状态微服务

如前所述，每个微服务（逻辑边界上下文）必须有其域模型（数据和逻辑）。 对于无状态微服务，数据库来自外部，采用 SQL Server 等关系选项，或 Azure Cosmos DB 或 MongoDB 等 NoSQL 选项。

但在 Service Fabric 中，服务本身可以是有状态的，也就是说数据驻留在微服务中。 此数据不仅能存在于同一服务器中，还可以存在于微服务进程中、内存中、硬盘驱动器中，并能复制到其他节点。 图 4-30 显示了不同的方法。

![无状态服务中 （持久性和数据库） 的状态是不在微服务进行的。 有状态服务中状态保存在微服务。](./media/stateless-vs-stateful-microservices.png)

图 4-14。 无状态微服务与有状态微服务

无状态方法是完全有效的，相比有状态微服务，它更易实现，因为这种方法类似于用户熟悉的传统模式。 但无状态微服务会在进程和数据源之间产生延迟。 若要试图增加缓存和队列来提高性能，该方法会涉及更多要移动的内容。 结果就是，最终会得到具有许多层级的复杂体系结构。

相反，[有状态微服务](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)采用的方案更高级，因为域逻辑和数据之间没有延迟。 有状态服务有利于处理繁重数据、游戏后端、数据库即服务和其他低延迟方案，因为它能启用本地状态，提高访问速度。

无状态服务和有状态服务相辅相成。 例如，您可以看到在右边的图中图 4-31，有状态服务可以拆分为多个分区。 若要访问这些分区，可能需要无状态服务充当网关服务，该服务了解如何基于分区键处理每个分区。

有状态服务确实存在缺点。 它们对设置了某一高的复杂性级别，以便向外扩展。完成跨有状态微服务和数据分区复制数据等任务时，必须解决通常由外部数据库系统实现的功能。 但这正是含[有状态可靠服务](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)的 [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) 等业务流程协调程序可发挥重要作用的一方面，它可使用 [Reliable Services API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) 和 [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction) 简化有状态微服务的开发过程和生命周期。

其他允许有状态微服务，支持 Actor 模式，提高业务逻辑和数据之间的容错、缩短延迟的微服务框架有来自 Microsoft Research 的 Microsoft [Orleans](https://github.com/dotnet/orleans) 和 [Akka.NET](https://getakka.net/)。 这两个框架目前都在改善其对 Docker 的支持。

请记住，Docker 容器本身是无状态。 若要实现有状态服务，需到前面提到的某个级别更高的规范框架。

## <a name="using-azure-service-fabric-mesh"></a>使用 Azure Service Fabric 网格

Azure Service Fabric Mesh 是完全托管的服务，开发人员可生成和部署任务关键型应用程序而无需管理任何基础结构。 使用 Service Fabric 网格可构建并运行按需缩放的安全的分布式微服务应用程序。

图 4-15 中所示在 Service Fabric 网格上托管的应用程序运行和缩放，而你不担心基础结构增强它。

![在 Docker desktop 中运行的多容器应用程序可以部署到 Azure Service Fabric 网格中，而无需担心基础结构。](media/image39.png)

**图 4-15**。 将微服务/容器应用程序部署到 Service Fabric 网格

事实上，Service Fabric 网格由包含数千台计算机的群集组成。 所有群集操作都向开发人员隐藏。 只需上传容器并指定所需资源、可用性要求和资源限制。 Service Fabric 网格会自动分配应用程序部署所请求的基础结构，还会处理基础结构故障，从而确保应用程序高度可用。 只需关心应用程序的运行状况和响应能力，而不是基础结构。

有关详细信息，请参阅[Service Fabric Mesh 文档](https://docs.microsoft.com/azure/service-fabric-mesh/)。

## <a name="choosing-orchestrators-in-azure"></a>在 Azure 中选择业务流程协调程序

下表提供有关根据工作负荷和 OS 焦点使用哪个业务流程协调程序的指南。

![Azure Kubernetes 服务是更成熟比在 Windows 中的 Linux 中，主要用于部署基于容器的微服务。 Azure Service Fabric（群集和网格）在 Windows 中比在 Linux 中更成熟，通常用于基于容器的微服务、基于普通进程的微服务和有状态服务。](media/image40.png)

**图 4-16**。 Azure 指南中的业务流程协调程序选择

>[!div class="step-by-step"]
>[上一页](soa-applications.md)
>[下一页](deploy-azure-kubernetes-service.md)
