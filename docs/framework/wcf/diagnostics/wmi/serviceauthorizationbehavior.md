---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: 51555e3357b8c33a53261c4894d97798b0a05656
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102929"
---
# <a name="serviceauthorizationbehavior"></a>ServiceAuthorizationBehavior
ServiceAuthorizationBehavior  
  
## <a name="syntax"></a>语法  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a>方法  
 ServiceAuthorizationBehavior 类未定义任何方法。  
  
## <a name="properties"></a>属性  
 ServiceAuthorizationBehavior 类具有下列属性：  
  
### <a name="impersonatecallerforalloperations"></a>ImpersonateCallerForAllOperations  
 数据类型：Boolean  
  
 访问类型：只读  
  
 一个值，控制服务是否尝试使用传入消息所提供的凭据进行模拟。  
  
### <a name="principalpermissionmode"></a>PrincipalPermissionMode  
 数据类型：String  
  
 访问类型：只读  
  
 用于在服务器上执行操作的主体。  
  
### <a name="roleprovider"></a>RoleProvider  
 数据类型：String  
  
 访问类型：只读  
  
 ASP.NET 角色提供程序的名称。  
  
### <a name="serviceauthorizationmanager"></a>ServiceAuthorizationManager  
 数据类型：String  
  
 访问类型：只读  
  
 用于自定义授权的授权管理器。  
  
## <a name="requirements"></a>要求  
  
|MOF|已在 Servicemodel.mof 中声明。|  
|---------|-----------------------------------|  
|命名空间|已在 root\ServiceModel 中定义|  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
