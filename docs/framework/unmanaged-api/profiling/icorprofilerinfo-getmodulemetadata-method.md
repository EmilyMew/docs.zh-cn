---
title: ICorProfilerInfo::GetModuleMetaData 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89a2424548bb577e3580d6eaa72f61e5cf9ccc7d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111210"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>ICorProfilerInfo::GetModuleMetaData 方法
获取将映射到指定的模块的元数据接口实例。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a>参数  
 `moduleId`  
 [in]接口实例将映射到该模块的 ID。  
  
 `dwOpenFlags`  
 [in]值为[CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)枚举，用于指定打开清单文件的模式。 仅`ofRead`，`ofWrite`和`ofNoTransform`位均有效。  
  
 `riid`  
 [in]引用 ID (GUID) 将检索其实例的元数据接口。 请参阅[元数据接口](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)有关接口的列表。  
  
 `ppOut`  
 [out]指向元数据接口实例的地址的指针。  
  
## <a name="remarks"></a>备注  
 可能会要求提供要在读/写模式下打开的元数据，但这将导致该程序的元数据执行速度变慢，因为对更改就像从编译器，不能优化元数据。  
  
 一些模块 （如资源模块） 有任何元数据。 在这些情况下，`GetModuleMetaData`将返回 S_FALSE 和中的 null 的 HRESULT 值 *`ppOut`。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerInfo 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
