---
title: 授予对服务操作的访问权限
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: 50b6ab528aaebabbe709104632e269dfa68072a5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842364"
---
# <a name="authorizing-access-to-service-operations"></a>授予对服务操作的访问权限
此示例演示如何使用[ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)若要启用使用<xref:System.Security.Permissions.PrincipalPermissionAttribute>属性来授予对服务操作的访问。 此示例基于[Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)示例。 使用配置了服务和客户端[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。 `mode`的属性[\<安全 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)已设置为`Message`并`clientCredentialType`已设置为`Windows`。 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 应用到每个服务方法并用于限制对每个操作的访问。 调用方必须是 Windows 管理员才能访问每项操作。  
  
 在此示例中，客户端是一个控制台应用程序 (.exe)，服务是由 Internet 信息服务 (IIS) 承载的。  
  
> [!NOTE]
>  本主题的最后介绍了此示例的设置过程和生成说明。  
  
 服务配置文件使用[ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)若要设置`principalPermissionMode`属性：  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>   
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 将 `principalPermissionMode` 设置为 `UseWindowsGroups` 可使用基于 Windows 组名的 <xref:System.Security.Permissions.PrincipalPermissionAttribute>。  
  
 将 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 应用于每个操作以要求调用方是 Windows 管理员组的成员，如下面的示例代码所示。  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 运行示例时，操作请求和响应将显示在客户端控制台窗口中。 如果客户端在管理员组成员的账户下运行，客户端可与每个操作成功通信；否则访问被拒绝。 若要体验授权失败，请在不是管理员组成员的账户下运行客户端。 在控制台窗口中按 Enter 可以关闭客户端。  
  
 通过实现 <xref:System.ServiceModel.Dispatcher.IErrorHandler> 可以通知服务授权失败。 请参阅[扩展控件上的错误处理和报告](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)有关如何实现信息`IErrorHandler`。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1.  请确保您具有执行[的 Windows Communication Foundation 示例的一次性安装过程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的说明进行操作。  
  
3.  若要在单或跨计算机配置中运行示例，请按照中的说明[运行 Windows Communication Foundation 示例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
