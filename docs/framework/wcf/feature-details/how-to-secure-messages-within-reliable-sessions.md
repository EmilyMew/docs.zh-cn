---
title: 如何：可靠会话内保护消息
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: ee35f2a36ca08814423b5a3d0b1432bacd28c2e5
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/16/2019
ms.locfileid: "56333048"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>如何：可靠会话内保护消息

本主题概述了使用系统提供的绑定之一来启用在可靠会话内交换的消息的消息级安全所需的步骤。这些绑定支持这种会话，但默认情况下不支持。 使用代码以强制方式或配置文件中以声明方式，请启用安全的可靠会话。 此过程使用客户端和服务配置文件来启用安全的可靠会话。

此过程由以下三个关键任务组成：

1. 指定客户端和服务在可靠会话内交换消息。

1. 在可靠会话内要求消息级安全。

1. 指定客户端必须用来向服务进行身份验证的客户端凭据类型。

它是在终结点配置元素包含的第一个任务中重要`bindingConfiguration`引用 （在此示例中） 名为的绑定配置的属性`MessageSecurity`。 [ **\<绑定 >** ](../../../../docs/framework/misc/binding.md)配置元素然后引用此名称来启用可靠会话通过设置`enabled`属性的[  **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))元素`true`。 通过将 `ordered` 属性设置为 `true`，可以要求可靠会话内的有序传送保证。

基于此配置过程的示例的源副本，请参阅[WS 可靠会话](../../../../docs/framework/wcf/samples/ws-reliable-session.md)。

项的第二个任务的基本项通过设置来实现 `mode` 的属性 **\<安全>** 元素中包含 **\<绑定>** 元素的客户端和服务将 `Message`。

项的第三个任务的基本项通过设置来实现 `clientCredentialType` 的属性 **\<消息>** 元素中包含 **\<安全>** 元素的客户端和服务将 `Certificate`。

> [!NOTE]
> 当使用可靠会话消息安全性，可靠消息传递尝试对未经身份验证的客户端进行身份验证，直到发生超时，而不是引发异常后第一次失败。

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>将服务配置为使用 WSHttpBinding 使用可靠会话

此过程所述[如何：在可靠会话内交换消息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)。

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>使用 WSHttpBinding 使用可靠会话配置客户端

此过程所述[如何：在可靠会话内交换消息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)。

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>在配置中设置 mode 和 ClientCredentialType

1. 添加到相应的绑定元素[ **\<绑定 >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)配置文件元素。 以下示例将添加[  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)元素。

1. 添加 **\<绑定>** 元素，并设置其 `name` 属性为适当的值。 该示例使用名称`MessageSecurity`。

1. 添加 **\<安全>** 元素，并设置 `mode` 归于 `Message`。

1. 内 **\<安全>** 元素中，添加 **\<消息>** 元素，并设置 `clientCredentialType` 归于 `Certificate`。

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
