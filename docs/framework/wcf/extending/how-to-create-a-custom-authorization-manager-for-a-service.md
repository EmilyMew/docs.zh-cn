---
title: 如何：创建自定义授权管理器服务
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
ms.openlocfilehash: 571c1d66bcf1ea62972eb1be3fd694964581db38
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465134"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a>如何：创建自定义授权管理器服务
标识模型基础结构在 Windows Communication Foundation (WCF) 支持可扩展的基于声明的授权模型。 声明是从令牌中提取的，自定义授权策略将有选择地对其进行处理，然后放入 <xref:System.IdentityModel.Policy.AuthorizationContext> 中。 授权管理器检查 <xref:System.IdentityModel.Policy.AuthorizationContext> 中的声明，从而作出授权决策。  
  
 默认情况下，授权决策由 <xref:System.ServiceModel.ServiceAuthorizationManager> 类作出；但是，可通过创建自定义授权管理器来覆盖这些决策。 若要创建自定义授权管理器，请创建一个从 <xref:System.ServiceModel.ServiceAuthorizationManager> 派生的类，并实现 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 方法。 授权决策是在 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 方法中作出的，如果允许访问，该方法返回 `true`，如果拒绝访问，则返回 `false`。  
  
 如果授权决策取决于消息正文的内容，请使用 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法。  
  
 由于性能问题，如有可能，应重新设计应用程序，使授权决策不需要访问消息正文。  
  
 在代码或配置中，可以进行服务的自定义授权管理器注册。  
  
### <a name="to-create-a-custom-authorization-manager"></a>创建自定义授权管理器  
  
1.  从 <xref:System.ServiceModel.ServiceAuthorizationManager> 类派生一个类。  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2.  重写 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> 方法。  
  
     使用传给 <xref:System.ServiceModel.OperationContext> 方法的 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> 进行授权决策。  
  
     下面的代码示例使用 <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> 方法查找自定义声明 `http://www.contoso.com/claims/allowedoperation`，从而做出授权决策。  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a>使用代码注册自定义授权管理器  
  
1.  创建自定义授权管理器的一个实例，然后将其分配给 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> 属性。  
  
     使用 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 属性可以访问 <xref:System.ServiceModel.ServiceHostBase.Authorization%2A>。  
  
     下面的代码示例注册 `MyServiceAuthorizationManager` 自定义授权管理器。  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a>使用配置注册自定义授权管理器  
  
1.  打开服务的配置文件。  
  
2.  添加[ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)到[\<行为 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)。  
  
     向[ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)，添加`serviceAuthorizationManagerType`属性并将其值设置为表示自定义授权管理器的类型。  
  
3.  添加一个保护客户端和服务之间的通信的绑定。  
  
     为此通信选择的绑定决定了添加到 <xref:System.IdentityModel.Policy.AuthorizationContext> 的声明，自定义授权管理器使用这些声明来进行授权决策。 有关系统提供的绑定的更多详细信息，请参阅[System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md)。  
  
4.  添加到服务终结点，行为将相关联[\<服务 >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)元素和设置的值`behaviorConfiguration`属性的 name 属性的值设[\<行为>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)元素。  
  
     有关配置服务终结点的详细信息，请参阅[如何：在配置中创建的服务终结点](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)。  
  
     下面的代码示例注册自定义授权管理器 `Samples.MyServiceAuthorizationManager`。  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service   
              name="Microsoft.ServiceModel.Samples.CalculatorService"  
              behaviorConfiguration="CalculatorServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
            <endpoint address=""  
                      binding="wsHttpBinding_Calculator"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <WSHttpBinding>  
           <binding name = "wsHttpBinding_Calculator">  
             <security mode="Message">  
               <message clientCredentialType="Windows"/>  
             </security>  
            </binding>  
          </WSHttpBinding>  
    </bindings>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="CalculatorServiceBehavior">  
              <serviceAuthorization serviceAuthorizationManagerType="Samples.MyServiceAuthorizationManager,MyAssembly" />  
             </behavior>  
         </serviceBehaviors>  
       </behaviors>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
    > [!WARNING]
    >  请注意，当您指定了 serviceAuthorizationManagerType 时，字符串必须包含完全限定的类型名称、 一个逗号，以及在其中定义类型的程序集的名称。 如果您忽略了程序集名称，WCF 会尝试从 System.ServiceModel.dll 加载类型。  
  
## <a name="example"></a>示例  
 下面的代码示例演示 <xref:System.ServiceModel.ServiceAuthorizationManager> 类的一个基本实现，包括重写 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 方法。 该示例代码检查某个自定义声明的 <xref:System.IdentityModel.Policy.AuthorizationContext>，如果该自定义声明的资源与 `true` 中的操作值匹配，则返回 <xref:System.ServiceModel.OperationContext>。 有关更完整的实现<xref:System.ServiceModel.ServiceAuthorizationManager>类，请参阅[授权策略](../../../../docs/framework/wcf/samples/authorization-policy.md)。  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a>请参阅
- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [授权策略](../../../../docs/framework/wcf/samples/authorization-policy.md)
