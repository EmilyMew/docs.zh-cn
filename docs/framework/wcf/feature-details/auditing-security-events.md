---
title: 审核安全事件
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: 7d19c32994fdfc5587c06b979886f20ab2a04508
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101285"
---
# <a name="auditing-security-events"></a>审核安全事件
创建使用 Windows Communication Foundation (WCF) 的应用程序可以利用审核功能记录安全事件 （成功、 失败，或两者）。 这些事件被写入 Windows 系统事件日志，并且可以使用事件查看器进行检查。  
  
 审核为管理员提供了一种检测已经发生或正在发生的攻击的方式。 此外，审核有助于开发人员调试与安全相关的问题。 例如，如果授权或检查策略配置中的错误意外拒绝授权用户进行访问，开发人员可以通过检查事件日志迅速发现并隔离此错误的原因。  
  
 有关 WCF 安全性的详细信息，请参阅[安全性概述](../../../../docs/framework/wcf/feature-details/security-overview.md)。 有关 WCF 编程的详细信息，请参阅[基本 WCF 编程](../../../../docs/framework/wcf/basic-wcf-programming.md)。  
  
## <a name="audit-level-and-behavior"></a>审核级别和行为  
 存在两个安全审核级别：  
  
-   服务授权级别，在该级别对调用方进行授权。  
  
-   消息级别，在其中 WCF 消息的有效性检查，并对调用方进行身份验证。  
  
 你可以检查这两个审核级别的成功或失败，这被称为*审核行为*。  
  
## <a name="audit-log-location"></a>审核日志位置  
 一旦确定审核级别和行为，您（或管理员）就可指定审核日志的位置。 三个选项包括：默认值、 应用程序中，和安全。 当指定“默认值”时，实际日志取决于所使用的系统以及该系统是否支持写入安全日志。 有关详细信息，请参阅本主题后面的"操作系统"部分。  
  
 写入 Security 日志要求具有 `SeAuditPrivilege`。 默认情况下，只有“本地系统”和“网络服务”帐户具有此特权。 管理 Security 日志功能 `read` 和 `delete` 要求具有 `SeSecurityPrivilege`。 默认情况下，只有管理员具有此特权。  
  
 与此相反，经过身份验证的用户可以读取和写入应用程序日志。 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 默认情况下，审核写入到应用程序日志的事件。 该日志还包含对所有通过身份验证的用户可见的个人信息。  
  
## <a name="suppressing-audit-failures"></a>禁止显示审核失败  
 审核过程中的另一个选择为是否禁止显示任何审核失败。 默认情况下，审核失败不会影响应用程序。 但是，如若需要，可将此选项设置为 `false`，这将导致引发异常。  
  
## <a name="programming-auditing"></a>审核编程  
 可以通过编程或通过配置来指定审核行为。  
  
### <a name="auditing-classes"></a>审核类  
 下表描述了用于对审核行为进行编程的类和属性。  
  
|类|描述|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|将设置审核选项作为服务行为启用。|  
|<xref:System.ServiceModel.AuditLogLocation>|枚举值，用于指定要写入的日志。 可能的值为 Default、Application 和 Security。 选择 Default 时，操作系统将确定实际日志位置。 请参见本主题后面的“Application 或 Security 事件日志选择”部分。|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|指定在消息级别审核哪些类型的消息身份验证事件。 选择包括 `None`、`Failure`、`Success` 和 `SuccessOrFailure`。|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|指定在服务级别审核哪些类型的服务授权事件。 选择包括 `None`、`Failure`、`Success` 和 `SuccessOrFailure`。|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|指定在审核失败时如何处理客户端请求。 例如，当服务尝试写入 Security 日志但不具有 `SeAuditPrivilege` 时。 默认值 `true` 指示忽略失败，因此将正常处理客户端请求。|  
  
 设置应用程序日志审核事件的示例，请参阅[如何：审核安全事件](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)。  
  
### <a name="configuration"></a>配置  
 此外可以使用配置来指定审核行为，通过添加[ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)下[\<行为 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)。 必须添加下的元素[\<行为 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)如下面的代码中所示。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <behavior>  
        <!-- auditLogLocation="Application" or "Security" -->  
        <serviceSecurityAudit  
                  auditLogLocation="Application"  
                  suppressAuditFailure="true"  
                  serviceAuthorizationAuditLevel="Failure"  
                  messageAuthenticationAuditLevel="SuccessOrFailure" />   
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 如果启用了审核但未指定 `auditLogLocation`，则对于支持写入 Security 日志的平台来说，默认日志名称为“Security”日志；否则为“Application”日志。 仅 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wv](../../../../includes/wv-md.md)] 操作系统支持写入安全日志。 有关详细信息，请参阅本主题后面的"操作系统"部分。  
  
## <a name="security-considerations"></a>安全注意事项  
 如果恶意用户了解到审核功能处于启用状态，攻击者可能会发送将导致写入审核项的无效消息。 如果以这种方式填充审核日志，则审核系统会出现故障。 为了缓解此问题，请将 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> 属性设置为 `true`，然后使用事件查看器的属性来控制审核行为。 详细信息，请参阅 Microsoft 支持文章的查看和管理事件日志可在 Windows XP 中使用事件查看器[如何查看和管理 Windows XP 中的事件查看器中的事件日志](https://go.microsoft.com/fwlink/?LinkId=89150)。  
  
 在 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上写入 Application 日志的审核事件对任何通过身份验证的用户都是可见的。  
  
## <a name="choosing-between-application-and-security-event-logs"></a>选择 Application 或 Security 事件日志  
 下表提供的信息有助于您选择是记录到 Application 事件日志中还是记录到 Security 事件日志中。  
  
#### <a name="operating-system"></a>操作系统  
  
|系统|Application 日志|Security 日志|  
|------------|---------------------|------------------|  
|[!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] 或更高版本|支持|不支持|  
|[!INCLUDE[ws2003sp1](../../../../includes/ws2003sp1-md.md)] 和 [!INCLUDE[wv](../../../../includes/wv-md.md)]|支持|线程上下文必须具有 `SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>其他因素  
 除操作系统以外，下表描述了其他用于控制是否启用日志记录的设置。  
  
|因素|Application 日志|Security 日志|  
|------------|---------------------|------------------|  
|审核策略管理|不适用。|除配置以外，Security 日志还受到本地安全机构 (LSA) 策略的控制。 还必须启用“审核对象访问”类别。|  
|默认用户体验|所有通过身份验证的用户都可以写入 Application 日志，因此对于应用程序进程，不需要执行其他权限步骤。|应用程序进程（上下文）必须具有 `SeAuditPrivilege`。|  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [安全性概述](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [基本 WCF 编程](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [如何：审核安全事件](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
- [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)
- [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [Windows Server App Fabric 的安全模型](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
