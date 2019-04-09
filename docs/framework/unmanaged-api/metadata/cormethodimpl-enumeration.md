---
title: CorMethodImpl 枚举
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2138dd32cf39db7b7c8989ba5827178d1a1e46c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117230"
---
# <a name="cormethodimpl-enumeration"></a>CorMethodImpl 枚举
包含一些值，用于描述方法实现功能。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`miCodeTypeMask`|描述代码类型的标志。|  
|`miIL`|指定方法实现为 Microsoft 中间语言 (MSIL)。|  
|`miNative`|指定方法实现为本机。|  
|`miOPTIL`|指定该方法的实现是 OPTIL。|  
|`miRuntime`|指定该方法的实现由公共语言运行时提供。|  
|`miManagedMask`|指示是否是托管或非托管代码的标志。|  
|`miUnmanaged`|指定该方法的实现不受管理。|  
|`miManaged`|指定管理方法实现。|  
|`miForwardRef`|指定该方法定义。 主要在合并方案中使用此标志。|  
|`miPreserveSig`|指定方法签名不能将出错的 HRESULT 转换。|  
|`miInternalCall`|公共语言运行时，保留供内部使用。|  
|`miSynchronized`|指定的方法是单线程通过其主体。|  
|`miNoInlining`|指定方法不能内联。|  
|`miAggressiveInlining`|指定的方法应是内联在可能的情况。|  
|`miNoOptimization`|指定该方法不应进行优化。|  
|`miMaxMethodImplVal`|有效的最大值`CorMethodImpl`。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorHdr.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据枚举](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
