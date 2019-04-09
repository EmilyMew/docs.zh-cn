---
title: IAssemblyName 接口
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d8d59ef282818dd9852d0ff8d2ec2abd40986d0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097130"
---
# <a name="iassemblyname-interface"></a>IAssemblyName 接口
提供用于描述和使用程序集的唯一标识的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Clone 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|创建的浅表副本`IAssemblyName`对象。|  
|[Finalize 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|允许此`IAssemblyName`对象释放资源并调用其析构函数之前执行其他清理操作。|  
|[GetDisplayName 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|获取此引用的程序集的用户可读名称`IAssemblyName`对象。|  
|[GetName 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|获取此引用的程序集的简单、 非加密名称`IAssemblyName`对象。|  
|[GetProperty 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|获取一个指针指向由指定引用的属性`PropertyId`。|  
|[GetVersion 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|获取此引用的程序集的版本信息`IAssemblyName`对象。|  
|[IsEqual 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|确定指定`IAssemblyName`对象是否等于此`IAssemblyName`、 根据指定的比较标志。|  
|[SetProperty 方法](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|设置由指定引用的属性的值`PropertyId`。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Fusion.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [合成接口](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IAssemblyEnum 接口](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
