---
title: IMetaDataAssemblyImport::FindAssembliesByName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b388dae0f109ff366f83c92de99b00b80bcc01a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108714"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName 方法
获取具有指定的程序集的数组`szAssemblyName`参数，并使用公共语言运行时 (CLR) 解析引用的标准规则。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a>参数  
 `szAppBase`  
 [in]要在其中搜索给定的程序集的根目录。 如果此值设置为`null`，`FindAssembliesByName`将仅在全局程序集缓存中查找程序集。  
  
 `szPrivateBin`  
 [in]以分号分隔的子目录 （例如，"bin; bin2"），在其中搜索程序集的根目录下的列表。 除了默认探测规则中指定的探测这些目录。  
  
 `szAssemblyName`  
 [in]要查找的程序集的名称。 此字符串的格式定义的类参考页中<xref:System.Reflection.AssemblyName>。  
  
 `ppIUnk`  
 [in]类型的数组[IUnknown](/cpp/atl/iunknown)所要放入`IMetadataAssemblyImport`接口指针。  
  
 `cMax`  
 [out]可将中的接口指针的最大数目`ppIUnk`。  
  
 `pcAssemblies`  
 [out]返回接口指针的数。 也就是说，数量的接口指针实际放置在`ppIUnk`。  
  
## <a name="return-value"></a>返回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` 已成功返回。|  
|`S_FALSE`|没有程序集。|  
  
## <a name="remarks"></a>备注  
 指定程序集名称，`FindAssembliesByName`方法按照解析程序集引用的标准规则找到该程序集。 (有关详细信息，请参阅[运行时如何定位程序集](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。)`FindAssembliesByName`允许调用方配置的程序集冲突解决程序上下文，例如，应用程序基和专用搜索路径的各个方面。  
  
 `FindAssembliesByName`方法需要 CLR 初始化过程中，以便调用程序集的解析逻辑。 因此，您必须调用[CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) （传递 COINITEE_DEFAULT） 之前，调用`FindAssembliesByName`，然后按照通过调用[CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)。  
  
 `FindAssembliesByName` 返回[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)指针，指向包含程序集名称的程序集清单中传递的文件。 如果给定的程序集名称未完全指定 （例如，如果它不包含版本），可能返回多个程序集。  
  
 `FindAssembliesByName` 通常使用由编译器会尝试查找在编译时引用的程序集。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 用作 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [运行时如何定位程序集](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
