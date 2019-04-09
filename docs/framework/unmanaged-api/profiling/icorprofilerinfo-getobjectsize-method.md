---
title: ICorProfilerInfo::GetObjectSize 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d366a0093ca82d2e5b3c40729777a1b6c0766bda
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092196"
---
# <a name="icorprofilerinfogetobjectsize-method"></a>ICorProfilerInfo::GetObjectSize 方法
获取指定对象的大小。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a>参数  
 `objectId`  
 [in]对象的 ID。  
  
 `pcSize`  
 [out]指向对象的大小，以字节为单位的指针。  
  
## <a name="remarks"></a>备注  
  
> [!IMPORTANT]
>  此方法已过时。 它返回 COR_E_OVERFLOW 对象大于 4 GB 64 位平台上。 使用[ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)方法相反。  
  
 相同类型的不同对象通常具有相同的大小。 但是，某些类型，如数组或字符串，可能具有不同大小的每个对象。  
  
 返回的大小`GetObjectSize`方法不包括任何可能出现在垃圾回收堆上对象后的对齐方式填充。 如果使用`GetObjectSize`方法上垃圾回收堆，提前对象之间添加根据需要手动填充的对齐方式。  
  
-   在 32 位 Windows 上 COR_PRF_GC_GEN_0、 COR_PRF_GC_GEN_1 和 COR_PRF_GC_GEN_2 使用 4 字节对齐方式，并 COR_PRF_GC_LARGE_OBJECT_HEAP 使用 8 字节对齐方式。  
  
-   在 64 位 Windows 上的对齐方式始终是 8 个字节。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerInfo 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
