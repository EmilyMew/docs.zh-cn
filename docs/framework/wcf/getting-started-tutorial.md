---
title: 教程：开始使用 Windows Communication Foundation 应用程序
description: 这些教程介绍了用于创建 WCF 应用程序。
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: d4613edefeb8db2c0d1e11e925f8ac41329efb0d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137918"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>教程：开始使用 Windows Communication Foundation 应用程序
以下一系列教程向您介绍了为 Windows Communication Foundation (WCF) 编程体验。 通过按顺序这些教程将提供初步了解创建 WCF 应用程序所需的步骤。 完成后，你必须正在运行的 WCF 服务和 WCF 客户端调用服务。 

本教程假定你正在使用 Visual Studio 作为开发环境。 如果你使用的另一个开发环境，忽略的 Visual Studio 的特定说明。 

对于示例 WCF 应用程序可以下载并运行，请参阅[Windows Communication Foundation 示例](samples/index.md)。 有关示例，请参阅[入门示例](samples/getting-started-sample.md)。

有关创建服务和客户端的更多详细信息，请参阅[基本 WCF 编程](basic-wcf-programming.md)。

## <a name="wcf-tutorials"></a>WCF 教程

前三个教程介绍如何定义 WCF 服务协定、 如何实现它，以及如何承载它。 在创建该服务是自承载在控制台应用程序。 此外可以托管在 Microsoft Internet Information Services (IIS) 服务。 有关详细信息，请参阅[如何：承载在 IIS 中的 WCF 服务](feature-details/how-to-host-a-wcf-service-in-iis.md)。 尽管您可以使用代码服务配置为在本教程中，还可以[配置配置文件中的服务](configuring-services-using-configuration-files.md)。 

- [教程：定义服务协定](how-to-define-a-wcf-service-contract.md)

    使用用户定义的接口创建 WCF 协定。 此协定定义服务所公开的功能。

- [教程：实现服务协定](how-to-implement-a-wcf-contract.md)

    定义协定后，您必须与服务类实现它。

- [教程：托管并运行基本服务](how-to-host-and-run-a-basic-wcf-service.md)

    配置服务的终结点，并将服务托管在一个控制台应用程序。 变为活动状态的服务，必须对其进行配置和运行时环境中托管它。 此运行时环境中创建服务并控制其上下文和生存期。

接下来两个教程介绍如何创建、 配置，并使用客户端应用程序调用该服务的操作公开。 服务发布定义客户端应用程序与服务进行通信所需信息的元数据。 Visual Studio 自动化访问此元数据的过程，并使用它来构造服务的客户端应用程序。 如果你决定不使用 Visual Studio，则可以使用[ServiceModel 元数据实用工具 (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md)相反。

- [教程：创建客户端](how-to-create-a-wcf-client.md)

    检索用于创建 WCF 客户端代理从 WCF 服务的元数据。 使用 Visual Studio 添加服务引用检索元数据，或者可以使用 ServiceModel 元数据实用工具的工具。 指定客户端用于访问服务的终结点。

- [教程：使用客户端](how-to-use-a-wcf-client.md)

    使用 WCF 客户端代理调用服务操作。

## <a name="reference"></a>参考

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>请参阅

- [概念性概述](conceptual-overview.md)
- [文档指南](guide-to-the-documentation.md)
- [什么是 Windows Communication Foundation](whats-wcf.md)
- [WCF 功能详细信息](feature-details/index.md)
- [基本编程生命周期](basic-programming-lifecycle.md)
- [生成客户端](building-clients.md)
- [基本 WCF 编程](basic-wcf-programming.md)
- [如何：创建双工协定](feature-details/how-to-create-a-duplex-contract.md)
- [如何：使用双工协定访问服务](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [ServiceModel 元数据实用工具工具 (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [如何：使用 Svcutil.exe 下载元数据文档](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [如何：发布使用配置文件服务的元数据](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [使用绑定配置服务和客户端](using-bindings-to-configure-services-and-clients.md)
- [入门示例](samples/getting-started-sample.md)
- [Windows Communication Foundation 示例](samples/index.md)
- [自承载](samples/self-host.md)
