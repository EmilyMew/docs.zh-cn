---
title: ICLRDataTarget 接口
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ed3cb62b56e80a7fe4ea54b43ac9f4a28b8d102
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100244"
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget 接口
提供与公共语言运行时 (CLR) 的目标项进行交互的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetCurrentThreadID 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|获取当前线程的操作系统识别符。|  
|[GetImageBase 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|获取指定的图像的基础内存地址。|  
|[GetMachineType 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|获取目标进程正在使用的指令集的类型的标识符。|  
|[GetPointerSize 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|获取以字节为单位，指向当前目标的指针的大小。|  
|[GetThreadContext 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|获取一个指向线程的上下文具有指定标识符。|  
|[GetTLSValue 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|线程本地存储区 (TLS) 中获取一个值，指定线程的指定索引处。|  
|[ReadVirtual 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|从指定的虚拟内存地址数据读入指定的缓冲区。|  
|[Request 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|调用由公共语言运行时 (CLR) 数据访问服务以请求操作，如由实现定义。|  
|[SetThreadContext 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|目标进程中设置指定线程的当前的上下文。|  
|[SetTLSValue 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|设置中指定目标进程中线程的线程本地存储 (TLS) 的值。|  
|[WriteVirtual 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|将数据从指定的缓冲区写入到指定的虚拟内存地址。|  
  
## <a name="remarks"></a>备注  
 API 客户端 （即调试器） 必须实现此接口作为适用于特定的目标项。 例如，活动进程的实现将不同于内存转储的。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** ClrData.idl, ClrData.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRDataTarget2 接口](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
