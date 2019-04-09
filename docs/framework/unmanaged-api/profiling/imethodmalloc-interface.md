---
title: IMethodMalloc 接口
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee825da1f3f0fd72a3b47b48783f0f344af99b65
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077763"
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc 接口
提供用于新的 Microsoft 中间语言 (MSIL) 函数主体分配内存的方法。  
  
> [!NOTE]
>  `IMethodMalloc`接口是一个简单的内存分配器。 它可以分配内存，但不是能将其释放。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Alloc 方法](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|尝试为新的 MSIL 函数体分配指定的内存量。|  
  
## <a name="remarks"></a>备注  
 每个分配器是特定于模块的并确保函数体，将从该模块的基的正偏移位置。 因此，应使用分配器分配内存来存放函数体仅，十分宝贵，模块的基以上的内存。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [分析接口](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
