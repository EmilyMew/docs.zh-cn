---
title: ClrCreateManagedInstance 函数
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f82303a3d38e7a5baaf1c3edcc41518228360d34
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088452"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance 函数
创建指定的托管类型的实例。  
  
 此函数中不推荐[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。 使用 COM 激活来创建的托管类型的实例或使用托管 (请参阅[CLR 承载接口中添加.NET Framework 4 和 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md))。  
  
## <a name="syntax"></a>语法  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a>参数  
 `pTypeName`  
 [in]指向所请求的实例类型的名称的指针。  
  
 `riid`  
 [in]`IID`的所请求的实例类型。  
  
 `ppObject`  
 [out]指向由调用方请求的托管类型的实例的指针指向的指针。  
  
## <a name="remarks"></a>备注  
 公共语言运行时应该已经加载到进程。 例如，它可以通过调用由加载[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)函数之前`ClrCreateManagedInstance`调用函数。 如果未加载运行时，`ClrCreateManagedInstance`首次尝试加载 v1.0.3705 的运行时。 如果失败，它尝试加载运行时的最新版本。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** MSCorEE.dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [弃用的 CLR 承载函数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [宿主](../../../../docs/framework/unmanaged-api/hosting/index.md)
