---
title: IMetaDataInfo::GetFileMapping 方法
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4c6a9473a698e4635c8b5cc9fb58963334dfd65e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081783"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping 方法
获取内存区域的映射的文件和映射的类型。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a>参数  
 `ppvData`  
 [out]指向映射文件开头的指针。  
  
 `pcbData`  
 [out]映射区域的大小。 如果`pdwMappingType`是`fmFlat`，这是文件的大小。  
  
 `pdwMappingType`  
 [out]一个[CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)值，该值指示映射的类型。 公共语言运行时 (CLR) 的当前实现总是返回`fmFlat`。 其他值保留供将来使用。 但是，你应当始终验证返回的值，因为其他值可能在将来版本中启用或服务版本。  
  
## <a name="return-value"></a>返回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|填充所有输出。|  
|`E_INVALIDARG`|作为参数值传递 NULL。|  
|`COR_E_NOTSUPPORTED`|CLR 实现不能提供有关内存区域的信息。 这可能由于以下原因：<br /><br /> 通过打开的元数据范围`ofWrite`或`ofCopyMemory`标志。<br />无需打开元数据范围`ofReadOnly`标志。<br />- [Imetadatadispenser:: Openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)方法用来打开该文件的元数据部分。<br />-文件不是可移植可执行 (PE) 文件。 **注意：** 这些条件依赖于 CLR 实现，并可能降低在将来版本的 CLR。|  
  
## <a name="remarks"></a>备注  
 内存的`ppvData`指向无效，将仅当基础元数据范围处于打开状态。  
  
 为了使此方法时的调用的磁盘上文件的元数据映射到内存中工作[imetadatadispenser:: Openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法，必须指定`ofReadOnly`标志，必须指定`ofWrite`或`ofCopyMemory`标志。  
  
 每个作用域的文件映射类型的选择是特定于给定的 clr 实现。 它不能由用户设置。 CLR 的当前实现始终返回`fmFlat`在`pdwMappingType`，但这可能会更改在将来的 CLR 版本或将来的给定版本的 service release。 您应始终检查返回的值`pdwMappingType`，因为不同类型将具有不同的布局和偏移量。  
  
 不支持传递的任何三个参数为 NULL。 该方法将返回`E_INVALIDARG`，并无输出来填充。 忽略映射类型或区域的大小可能会导致不正常程序终止。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 用作 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataInfo 接口](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping 枚举](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
