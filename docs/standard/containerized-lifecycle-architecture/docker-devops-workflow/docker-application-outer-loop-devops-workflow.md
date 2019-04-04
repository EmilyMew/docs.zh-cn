---
title: Docker 应用程序的外部循环 DevOps 工作流中的步骤
description: 了解 DevOps 工作流的"外部循环"的步骤
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 95664e20269f68a2eea5111b6c12ec7f108dc77b
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58462976"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Docker 应用程序的外部循环 DevOps 工作流中的步骤

图 5-1 提供了端到端描述的组成 DevOps 外部循环工作流的步骤。

![下图显示了 DevOps 的"外部循环"。 代码推送到存储库，CI 管道已启动，然后开始部署应用程序获取在 CD 管道。 从已部署应用程序收集的指标反馈到开发工作负载，出现"内部循环"的位置，因此开发团队必须对用户和业务需求作出响应的实际数据。](./media/image1.png)

**图 5-1**。 使用 Microsoft 工具的 Docker 应用程序的 DevOps 外部循环工作流

现在，让我们检查每个中更详细地介绍这些步骤。

## <a name="step-1-inner-loop-development-workflow"></a>步骤 1：内部循环开发工作流

第 4 章中详细介绍了此步骤，但概括来说，下面是其中外部循环开始时，开发人员将推送到源控件管理系统 （如 Git) 的代码启动 CI 管道操作的时刻。

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>步骤 2：源代码管理集成和使用 Azure DevOps 服务和 Git 管理

在此步骤中，您需要有了要收集来自不同的开发人员团队中的所有代码的合并的版本的版本控制系统。

即使源代码管理 (SCC) 和源代码管理可能看起来得心应手周期的对大多数开发人员，开发运营生命周期中创建 Docker 应用程序时，务必强调必须提交与应用程序的 Docker 映像直接对全局 Docker 注册表 （如 Azure 容器注册表或 Docker Hub） 从开发人员的计算机。 相反，必须全局生成或基于源代码存储库 （如 Git) 的 CI 管道中仅对集成的源代码创建 Docker 映像的发布和部署到生产环境。

通过它们应只使用本地映像，生成的开发人员，他们自己的计算机中测试时。 这就是为什么很重要已从源代码管理代码激活在 DevOps 管道。

Azure DevOps 服务和 Team Foundation Server 支持 Git 和 Team Foundation 版本控制。 可以选择它们，并将其用于端到端 Microsoft 体验。 但是，还可以管理外部存储库 （如 GitHub、 本地 Git 存储库或 Subversion） 中的代码和仍将能够连接到它并获取你的 DevOps CI 管道作为起始点的代码。

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>步骤 3：构建 CI，集成和测试 Azure DevOps 服务和 Docker

CI 已成为新式软件测试和交付的标准。 Docker 解决方案维护开发和运营团队之间明确地分离。 Docker 映像的不变性可确保内容已开发、 CI 使用，请通过测试和生产环境中运行之间的可重复部署。 在开发人员的便携式计算机中部署 docker 引擎，测试基础结构，使容器可移植跨环境。

在此情况下，使用正确的代码提交的版本控制系统后，你需要*构建的服务*选取代码并运行的全局生成和测试。

此步骤中 （CI、 生成、 测试） 的内部工作流是构造的 CI 管道包含的代码存储库 （Git 等），您的生成服务器 （Azure DevOps 服务）、 Docker 引擎和 Docker 注册表。

您可以使用 Azure DevOps 服务为基础构建您的应用程序和设置 CI 管道，也会发布已生成的"项目"到"项目存储库，"下一步中进行介绍。

使用 Docker 进行部署，"最后一个项目"时要部署应用程序或服务的 Docker 映像中嵌入它们。 这些映像都推送或发布到*Docker 注册表*（私有等存储库可在 Azure 容器注册表中拥有的或公共 Docker 中心注册表，通常用于官方基础映像类似）。

下面是一个基本概念：CI 管道将启动的情况下关闭状态提交到 Git 等源代码管理存储库。 提交会导致 Azure DevOps 服务运行 Docker 容器中的生成作业，并该作业的成功完成后，将 Docker 映像推送到 Docker 注册表中，在图 5-2 所示。

![外部循环的第一部分涉及到步骤 1 到 3，从代码中运行、 调试和验证，然后生成和测试 CI 步骤的代码存储库](./media/image2.png)

**图 5-2**。 在 CI 中所涉及的步骤

下面是使用 Docker 和 Azure DevOps 服务的基本 CI 工作流步骤：

1. 开发人员将提交推送到源代码管理存储库 （Git/Azure DevOps 服务、 GitHub 等）。

2. 如果您使用的 Azure DevOps 服务或 Git，CI 生成中，这意味着它非常简单，Azure DevOps 服务中选择一个复选框。 如果使用的外部 （如 GitHub)，SCC`webhook`将通知更新的 Azure DevOps 服务或推送到 Git/GitHub。

3. Azure DevOps 服务拉取源代码管理存储库，包括描述图像，以及应用程序和测试代码的 Dockerfile。

4. Azure DevOps 服务生成 Docker 映像并使用生成号对其进行标记。

5. Azure DevOps 服务实例化中预配 Docker 主机的 Docker 容器，并运行适当的测试。

6. 如果测试成功，将映像首先重新标记为有意义的名称，以便您知道它是"blessed 的生成"(如"/ 1.0.0"或任何其他标签)，然后推送到 Docker 注册表 （Docker 中心、 Azure 容器注册表、 DTR 等） 和

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>适用于 Azure DevOps 服务实施 CI 管道中的使用 Azure DevOps 服务和 Docker 扩展

Visual Studio Azure DevOps 服务包含生成和发布模板，可在 CI/CD 管道与可生成 Docker 映像，将 Docker 映像推送到经过身份验证的 Docker 注册表、 运行 Docker 映像，或运行提供的其他操作Docker CLI。 它还添加了 Docker Compose，可用于生成、 推送和运行多容器 Docker 应用程序，或在图 5-3 所示运行提供的 Docker Compose CLI 其他操作的任务。

![Azure DevOps 中的 Docker CI 管道的浏览器视图](./media/image3.png)

**图 5-3**。 Azure DevOps 服务，包括生成和发布模板和相关联的任务中的 Docker CI 管道。

可以使用这些模板和任务来构造你的 CI/CD 的项目生成 / 测试和部署 Azure Service Fabric、 Azure Kubernetes 服务和类似的产品/服务中。

这些 Visual Studio Team Services 任务，生成 Linux Docker 主机/VM 在 Azure 中设置和您首选的 Docker 注册表 （Azure 容器注册表、 Docker 中心、 私有 Docker DTR 或任何其他 Docker 注册表） 来组合 Docker CI 管道中的非常一致的方式。

***要求：***

- Azure DevOps 服务，或对于在本地安装，Team Foundation Server 2015 Update 3 或更高版本。

- Azure DevOps 服务代理具有 Docker 二进制文件。

  创建一个这些代理的简单方法是使用 Docker 来运行基于 Azure DevOps 服务代理 Docker 映像的容器。

> [!信息] 若要阅读更多有关组成 Azure DevOps 服务 Docker CI 管道和查看演练，请访问这些站点：
>
> - 作为 Docker 容器中运行 Visual Studio Team Services （现在 Azure DevOps 服务） 代理: \
>   [https://hub.docker.com/r/microsoft/vsts-agent/](https://hub.docker.com/r/microsoft/vsts-agent/)
>
> - 构建使用 Azure DevOps 服务的.NET Core Linux Docker 映像: \
>   [https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/](https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/)
>
> - 构建基于 Linux 的 Visual Studio Team Service 生成具有 Docker 支持的计算机: \
>   [http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support](http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support)

### <a name="integrate-test-and-validate-multi-container-docker-applications"></a>将集成、 测试和验证多容器 Docker 应用程序

通常情况下，大多数 Docker 应用程序组成的多个容器而不是单个容器。 一个很好示例是一个面向微服务的应用程序，您将有每个微服务的一个容器。 但是，即使没有严格遵循微服务方法模式，很可能 Docker 应用程序将构成多个容器或服务。

因此，生成后 CI 管道中的应用程序容器，您还需要部署、 集成和测试应用程序作为一个整体与所有其容器内集成 Docker 主机或甚至到你的容器是一个测试群集分发。

如果你使用单个主机，可以使用 Docker 命令，如 docker-compose 来生成和部署相关的容器来测试和验证单个 VM 中的 Docker 环境。 但是，如果您正在使用如 DC/OS、 Kubernetes 或 Docker Swarm 的业务流程协调程序群集，则需要将通过不同的机制或业务流程协调程序，具体取决于你所选群集/计划程序将容器部署。

以下是几种可以针对 Docker 容器运行的测试类型：

- Docker 容器的单元测试

- 测试组又彼此相关的应用程序或微服务

- 在生产环境和"canary，"版本中测试

重要的一点是，运行时集成和功能测试，必须运行从容器外部这些测试。 不包含或因为容器基于应与您要部署到生产环境的完全相同的静态图像在要部署的容器中运行的测试。

将映像发布到注册表，以便可以在不同群集中对其进行测试时测试更高级的方案，如包括多个群集 （群集、 临时群集和生产群集测试） 的可行选项。

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>将自定义应用程序 Docker 映像推送到全局 Docker 注册表

Docker 映像已测试并验证后，你将想要标记并将其发布到 Docker 注册表。 Docker 注册表是 Docker 应用程序生命周期中一项重要，因为它是你在其中存储自定义测试 （也称为"blessed 映像"） 以便将部署到 QA 和生产环境的中心位置。

与存储在源代码管理存储库 （Git 等） 的应用程序代码的"事实来源"的方式类似，Docker 注册表是"事实来源"二进制应用程序或 bits 要部署到 QA 或生产环境。

通常情况下，你可能想要自定义映像的专用存储库在专用存储库中 Azure 容器注册表或 Docker 受信任注册表，如在本地注册表中或在具有受限访问权限 （如公共云注册表中Docker 中心），尽管在此最后一个的情况下，如果你的代码不是开放源代码，您必须信任很多供应商的安全。 无论哪种方式，所使用的方法类似，并且基于`docker push`命令，在图 5-4 所示。

![步骤 3 中，为构建集成和测试 (CI) 中可能会将生成的 docker 映像发布到专用或公共注册表。](./media/image4.png)

**图 5-4**。 正在自定义映像发布到 Docker 注册表

有多个产品/服务的 Azure 容器注册表、 Amazon Web 服务容器注册表、 Google 容器注册表、 Quay 注册表等云供应商提供 Docker 注册表。

使用 Docker 任务，可以请求服务映像由定义一组`docker-compose.yml`文件，使用多个标记，向一个已经过身份验证的 Docker 注册表 （如 Azure 容器注册表），在图 5-5 所示。

![要从 Azure DevOps 发布到注册表的映像的步骤的浏览器视图。](./media/image5.png)

**图 5-5**。 使用 Azure DevOps 服务为发布到 Docker 注册表的自定义映像

> [!信息] 了解 Azure 容器注册表的详细信息，请参阅<https://aka.ms/azurecontainerregistry>。

## <a name="step-4-cd-deploy"></a>步骤 4：CD，部署

Docker 映像的不可变性可以确保具有什么开发、 CI 使用，请通过测试并在生产环境中运行的可重复部署。 在 Docker 注册表 （专用或公用） 中发布的应用程序 Docker 映像后，您可以将其部署到你可能有多个环境 (生产、 QA、 暂存、 等) 从 CD 管道通过使用 Azure DevOps 服务管道任务或 Azure DevOps 服务版本管理。

但是，现在它取决于要部署哪些类型的 Docker 应用程序。 部署简单的应用程序 （组合和部署的角度来看） 等一个单片包含几个容器或服务应用程序和已部署到少量服务器或 Vm 是不同于部署等更复杂的应用程序面向微服务的应用程序与超大规模的功能。 以下各节中介绍了这两种方案。

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>部署包含 Docker 应用程序到多个 Docker 环境

让我们来看第一个在不太复杂方案： 部署到单个环境或多个环境中的简单 Docker 主机 （Vm 或服务器） (QA、 过渡和生产)。 在此方案中，在内部 CD 管道可以使用 docker-compose （从 Azure DevOps 服务部署任务） 来部署 Docker 应用程序使用其相关的一组的容器或服务，如图 5-6 所示。

![CD 部署步骤 (4) 可以将发布到不同的环境，如 q & a、 过渡和生产。](./media/image6.png)

**图 5-6**。 将应用程序的容器部署到简单的 Docker 主机环境注册表

图 5-7 突出显示了如何连接生成 CI QA/测试环境，通过 Azure DevOps 服务通过单击添加任务对话框中的 Docker Compose。 但是，部署到过渡或生产环境时，你通常将处理多个环境的发布管理功能 (如 QA、 过渡和生产)。 如果你正在部署到单个 Docker 主机，它使用 Azure DevOps 服务"Docker Compose"任务 (这调用`docker-compose up`命令实质上)。 如果你正在部署到 Azure 容器服务，它使用 Docker 部署任务，如后面的部分中所述。

![添加 Docker Compose 的任务的浏览器视图。](./media/image7.png)

**图 5-7**。 Azure DevOps 服务管道中添加 Docker Compose 任务

当在 Azure DevOps 服务中创建发布时，花了一套输入项目。 这些项目旨在是固定不变的版本中，生存期内所有环境中。 在引入容器时，输入的项目标识注册表部署中的映像。 具体取决于如何标识这些映像，它们不保证能够保持不变的版本中，最明显事例被引用时期间`myimage:latest`从`docker-compose`文件。

Azure DevOps 服务模板，您生成包含特定的注册表的映像的生成项目的功能摘要，可保证能唯一标识同一图像二进制文件。 这些是你确实要用作输入到发行版。

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>通过使用 Azure DevOps 服务 Release Management 管理发布到 Docker 环境

通过 Azure DevOps 服务模板，可以生成新映像、 将其发布到 Docker 注册表、 Linux 或 Windows 主机上运行和使用如下所示命令`docker-compose`将多个容器部署为整个应用程序，作为 Azure DevOps 后盾服务的多个环境的发布管理功能，在图 5-8 所示。

![浏览器视图的 Azure DevOps，配置 Docker compose 版本。](./media/image8.png)

**图 5-8**。 Azure DevOps 服务 Docker Compose 通过 Azure DevOps 服务版本管理的任务的配置

但是，请记住在图 5-6 所示和实现图 5-8 中的方案是一个简单 （它部署到单个 Docker 主机和虚拟机，并且将单个容器或每个映像的实例） 和可能应仅用于开发或测试 scenarios。 在大多数企业生产方案中，你会想要情况下跨多个节点、 服务器和 Vm，以及"智能故障转移"负载平衡，具有高可用性 (HA) 和易于管理的可伸缩性，如果服务器或节点发生故障，其服务和容器将移动到另一个主机服务器或 VM。 在这种情况下，您需要更高级的技术，例如容器群集、 业务流程协调程序和计划程序。 因此，将部署到这些群集的方法是通过处理的高级的方案中所述在下一节。

### <a name="deploying-docker-applications-to-docker-clusters"></a>Docker 应用程序部署到 Docker 群集

分布式应用程序的性质要求，还将分散的计算资源。 若要让生产规模的功能，需要具有群集提供高可伸缩性和高可用性根据共用资源的功能。

您可以将容器部署手动到这些群集从 CLI 工具或 web UI，但应保留这种手动找出部署测试工作或管理目的，例如向外扩展或监视。

从 CD 的角度来看，Azure DevOps 服务具体而言，您可以运行和精心制作的部署任务从你将部署容器化应用程序在容器中的分布式群集的 Azure DevOps 服务发布管理环境服务，如图 5-9 所示。

![CD 部署步骤 (4) 还可以发布到通过业务流程协调程序群集。](./media/image9.png)

**图 5-9**。 分布式应用程序部署到容器服务

最初，部署到特定群集或业务流程协调程序时，您将传统上使用特定的部署脚本和每个每个业务流程协调程序 （即 Kubernetes 和 Service Fabric 具有不同的部署机制） 的机制而不是更简单和易于使用`docker-compose`工具基于`docker-compose.yml`定义文件。 但是，借助 Azure DevOps 服务 Docker 部署任务中，显示在图 5-10，你现在还可以部署到受支持的业务流程协调程序通过只使用你熟悉`docker-compose.yml`文件为您，因为该工具执行该"转换"(从你`docker-compose.yml`业务流程协调程序所需的格式的文件)。

![浏览器视图中的任务目录中 Azure DevOps，以显示 Docker 的部署任务。](./media/image10.png)

**图 5-10**。 将 Docker 部署任务添加到环境 RM

图 5-11 演示了如何编辑 Docker 部署任务和指定目标类型 (Azure 容器服务 DC/OS，在此情况下)、 在 Docker Compose 文件，以及 （如 Azure 容器注册表或 Docker 中心） 的 Docker 注册表连接。 这是将检索随时可用自定义 Docker 映像部署为群集中容器的任务。

![Azure DevOps 的浏览器视图将部署到业务流程协调程序任务定义。](./media/image11.png)

**图 5-11**。 Docker 部署任务定义部署到 Azure 容器服务 DC/OS

> [!信息] 若要了解更多有关使用 Azure DevOps 服务和 Docker 在 CD 管道，请访问 <https://azure.microsoft.com/services/devops/pipelines>

## <a name="step-5-run-and-manage"></a>步骤 5：运行和管理

因为运行和管理应用程序在企业生产级别是主要使用者在和的本身，并由于操作的类型和在该级别 （IT 操作） 以及此区域的大范围的人员，整个的下一章专门介绍解释了它。

## <a name="step-6-monitor-and-diagnose"></a>步骤 6：监视和诊断

本主题还介绍了在接下来的任务的一章它执行在生产系统;但是，务必要突出显示在此步骤中获得的见解必须馈送回到开发团队，以便应用程序不断得到改进。 从该角度来看，它也是一部分的 DevOps，尽管通常执行的任务和操作 IT。

仅监视和诊断在 DevOps 领域中的 100%时，监视进程和由开发团队针对测试或 beta 环境执行的分析。 这是通过执行负载测试或通过监视 beta 或 QA 环境，beta 版测试人员正在新版本。

>[!div class="step-by-step"]
>[上一页](index.md)
>[下一页](create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)
