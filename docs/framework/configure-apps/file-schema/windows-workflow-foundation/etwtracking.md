---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: 12589ab7c6cb65618a5f53a3e4be49d85a2ffbb7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358959"
---
# <a name="etwtracking"></a>\<etwTracking>
一种服务行为，允许服务来利用 ETW 跟踪使用<xref:System.Activities.Tracking.EtwTrackingParticipant>。  
  
\<system.ServiceModel>  
\<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<etwTracking>  
  
## <a name="syntax"></a>语法  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|profileName|一个字符串，指定与此行为关联的跟踪配置文件的名称。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<行为 > 的\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|指定行为元素。|  
  
## <a name="remarks"></a>备注  
 在添加到服务的行为配置后，此配置元素对工作流服务配置跟踪参与者。  
  
 跟踪参与者用于获取从工作流发出的跟踪数据并将其存储在不同的媒体中。 同样，也可以在跟踪参与者中执行对跟踪记录的任何后续处理。  
  
## <a name="example"></a>示例  
 下面的配置示例演示在 Web.config 文件中配置的标准 ETW 跟踪参与者。  
  
 中定义 ETW 跟踪参与者使用跟踪记录写入 ETW 的提供程序 Id **\<诊断 >** 部分。 跟踪参与者具有一个与其关联的配置文件，用来指定跟踪参与者已订阅的跟踪记录。 这由 **profileName** 的属性 **\<添加>** 元素。 这些定义后，跟踪参与者添加到 **\<etwTracking >** 服务行为。 这会将所选跟踪参与者添加到工作流实例的扩展中，以便它们开始接收跟踪记录。  
  
```xml  
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## <a name="see-also"></a>请参阅
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [工作流跟踪](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [跟踪参与者](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
