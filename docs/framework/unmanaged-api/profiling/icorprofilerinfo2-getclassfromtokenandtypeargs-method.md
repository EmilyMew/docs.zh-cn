---
title: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d4d5ec9119cdcf89e507f133288f569e6fb37ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072514"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs 方法
获取`ClassID`通过使用指定的元数据标记的类型和`ClassID`的任何值类型参数。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a>参数  
 `moduleID`  
 [in]该类型所在的模块的 ID。  
  
 `typeDef`  
 [in]`mdTypeDef`元数据标记所引用的类型。  
  
 `cTypeArgs`  
 [in]为给定类型的类型参数的数目。 此值必须为零的非泛型类型。  
  
 `typeArgs`  
 [in]一个数组`ClassID`值，其中每个类型的自变量。 值`typeArgs`可以为 NULL，如果`cTypeArgs`设置为零。  
  
 `pClassID`  
 [out]一个指向`ClassID`的指定类型。  
  
## <a name="remarks"></a>备注  
 调用`GetClassFromTokenAndTypeArgs`方法替换`mdTypeRef`而不是`mdTypeDef`元数据标记可以具有不可预知的结果; 调用方应解决`mdTypeRef`到`mdTypeDef`时将其传递。  
  
 如果尚未加载该类型，则调用`GetClassFromTokenAndTypeArgs`将触发加载，这是一种危险操作在多种上下文中的。 例如，在模块或其他类型的加载过程中调用此方法在运行时尝试循环加载某些内容导致无限循环。  
  
 一般情况下，使用`GetClassFromTokenAndTypeArgs`不建议这样做。 如果探查器感兴趣的特定类型的事件，它们应存储`ModuleID`并`mdTypeDef`的该类型，以及使用[ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)若要检查是否给定`ClassID`是所需的类型。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerInfo 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
