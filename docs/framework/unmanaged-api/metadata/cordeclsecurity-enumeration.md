---
title: CorDeclSecurity 枚举
ms.date: 03/30/2017
api_name:
- CorDeclSecurity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeclSecurity
helpviewer_keywords:
- CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5409d1b89ba3e50c4ae17ed5aa6bf063cf6c93cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136963"
---
# <a name="cordeclsecurity-enumeration"></a>CorDeclSecurity 枚举
指定可以使用声明性安全执行的安全操作。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`dclActionMask`|保留。|  
|`dclActionNil`|保留。|  
|`dclRequest`|保留。|  
|`dclDemand`|要求调用堆栈中的所有高级调用方已被授予当前权限对象所指定的权限。|  
|`dclAssert`|调用代码可以访问当前权限对象所标识的资源，即使堆栈中的高级调用方不具备访问该资源的权限|  
|`dclDeny`|即使它们已被授予权限来访问它，将向调用方，拒绝访问当前权限对象指定的资源的能力。|  
|`dclPermitOnly`|仅可以访问此权限对象所指定的资源，即使代码已被授予访问其他资源的权限。|  
|`dclLinktimeCheck`|需要已被授予指定的权限在给定时间内直接调用方。|  
|`dclInheritanceCheck`|需要已被授予指定的权限派生的类继承另一个类或重写方法。|  
|`dclRequestMinimum`|调用方可以请求的代码运行所需的最小权限。 此操作仅可以在程序集的作用域内使用。|  
|`dclRequestOptional`|调用方可以请求是可选的 （无需运行） 的其他权限。 此请求隐式拒绝所有未明确请求的其他权限。 此操作仅可以在程序集的作用域内使用。|  
|`dclRequestRefuse`|将不授予调用方的请求可能被误用的权限。 此操作仅可以在程序集的作用域内使用。|  
|`dclPrejitGrant`|保留。|  
|`dclPrejitDenied`|保留。|  
|`dclNonCasDemand`|保留。|  
|`dclNonCasLinkDemand`|要求直接调用方已被授予指定的权限。|  
|`dclNonCasInheritance`|保留。|  
|`dclLinkDemandChoice`|保留。|  
|`dclInheritanceDemandChoice`|保留。|  
|`dclDemandChoice`|保留。|  
|`dclMaximumValue`|保留。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorHdr.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据枚举](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
