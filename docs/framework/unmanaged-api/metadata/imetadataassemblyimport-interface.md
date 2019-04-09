---
title: IMetaDataAssemblyImport 接口
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 373ff0470e2403f91534df0c0ffe4039dbb0f832
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112627"
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport 接口
提供访问和检查程序集清单内容的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CloseEnum 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|释放句柄指定的枚举器。|  
|[EnumAssemblyRefs 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|获取对包含枚举器的接口指针`mdAssemblyRef`令牌中当前元数据范围的程序集引用的程序集。|  
|[EnumExportedTypes 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|获取对包含枚举器的接口指针`mdExportedType`所引用的当前元数据范围中的程序集的 COM 类型的令牌。|  
|[EnumFiles 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|获取对包含枚举器的接口指针`mdFile`令牌中当前元数据范围的程序集引用的文件。|  
|[EnumManifestResources 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|获取对包含枚举器的接口指针`mdManifestResource`由当前的元数据范围中的程序集引用的资源的令牌。|  
|[FindAssembliesByName 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|获取一个数组`mdAssemblyRef`具有指定名称的程序集的令牌。|  
|[FindExportedTypeByName 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|获取`mdExportedType`标记，表示具有指定名称的 COM 类型。|  
|[FindManifestResourceByName 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|获取`mdManifestResource`标记，表示具有指定名称的资源。|  
|[GetAssemblyFromScope 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|获取程序集在当前元数据范围内的标记。|  
|[GetAssemblyProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|获取指定的程序集的属性设置。|  
|[GetAssemblyRefProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|获取指定的属性设置`mdAssemblyRef`令牌。|  
|[GetExportedTypeProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|获取指定的 COM 类型的属性设置。|  
|[GetFileProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|获取指定的文件的属性设置。|  
|[GetManifestResourceProps 方法](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|获取指定的清单资源的属性设置。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 用作 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据接口](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataAssemblyEmit 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
