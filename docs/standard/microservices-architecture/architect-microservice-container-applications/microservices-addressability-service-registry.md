---
title: 微服务可寻址性和服务注册表
description: 了解容器映像注册表在微服务体系结构中的角色。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 9bfd2a834039af9f71d263df3606d1b65a2d784f
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58466343"
---
# <a name="microservices-addressability-and-the-service-registry"></a>微服务可寻址性和服务注册表

每个微服务都有一个唯一名称 (URL)，用于解析其位置。 无论微服务在哪里运行，都需是可寻址的。 如果必须考虑哪一台计算机正在运行某个特定微服务，事情可能很快就不那么好办了。 按照 DNS 解析特定计算机 URL 的相同方式，微服务需要有唯一名称，以便可发现其当前位置。 微服务需要可寻址的名称，使其独立于运行于其中的基础结构。 这意味着服务部署方式与服务发现方式之间存在交互，因为此处需要一个[服务注册表](https://microservices.io/patterns/service-registry.html)。 同样，如果计算机出现故障，注册表服务须能够指出服务的运行位置。

[服务注册表模式](https://microservices.io/patterns/service-registry.html)是发现服务的一个关键部分。 注册表是包含服务实例的网络位置的数据库。 服务注册表需保持高度可用且是最新状态。 客户端可缓存从服务注册表获得的网络位置。 但是，该信息最终也会过时，客户端便无法再发现服务实例。 因此，服务注册表包含了一个服务器群集，使用复制协议来维护一致性。

在某些微服务部署环境中（称为集群，将在后面章节中介绍），服务发现是内置的。 例如，具有 Kubernetes (AKS) 环境的 Azure 容器服务可以处理服务实例注册和注销。 它还可在每个群集主机（充当服务器端发现路由器角色）上运行一个代理。 另一个示例是 Azure Service Fabric，它可通过其开箱即用的命名服务提供服务注册表。

请注意，服务注册表和 API 网关模式之间存在一定的重叠，这也有助于解决此问题。 例如，[Service Fabric 反向代理](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)是 API 网关的实现类型，该网关基于 Service Fabric 命名服务并且有助于解析内部服务的地址解析。

## <a name="additional-resources"></a>其他资源

- **Chris Richardson.模式：Service Registry（服务注册表）** \
  [https://microservices.io/patterns/service-registry.html](https://microservices.io/patterns/service-registry.html)

- **Auth0.The Service Registry**（服务注册表） \
  [https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)

- **Gabriel Schenker.Service discovery**（服务发现） \
  [https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)

>[!div class="step-by-step"]
>[上一页](maintain-microservice-apis.md)
>[下一页](microservice-based-composite-ui-shape-layout.md)