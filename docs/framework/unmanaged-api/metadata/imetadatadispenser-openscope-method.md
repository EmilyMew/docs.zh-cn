---
title: IMetaDataDispenser::OpenScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5b94987631f7dbbe39e585a8ea2c2252b9427613
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079599"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope 方法
打开一个现有的磁盘上的文件并将其元数据映射到内存中。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>参数  
 `szScope`  
 [in]要打开的文件的名称。 该文件必须包含公共语言运行时 (CLR) 元数据。  
  
 `dwOpenFlags`  
 [in]值为[CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)枚举，用于打开指定的模式 （读取、 写入和其他操作）。  
  
 `riid`  
 [in]要返回; 所需的元数据接口的 IID调用方将使用该接口导入 （读取） 或发出 （写入） 元数据。  
  
 值`riid`必须指定一个"导入"发出"接口。 有效值为 IID_IMetaDataEmit、 IID_IMetaDataImport、 IID_IMetaDataAssemblyEmit、 IID_IMetaDataAssemblyImport、 IID_IMetaDataEmit2 或 IID_IMetaDataImport2。  
  
 `ppIUnk`  
 [out]对返回的接口指针。  
  
## <a name="remarks"></a>备注  
 方法使用从一个"导入"接口，或添加到使用从"发出"界面中的一个方法，可以查询的元数据的内存中副本。  
  
 如果目标文件不包含 CLR 元数据，`OpenScope`方法将失败。  
  
 在.NET Framework 版本 1.0 和 1.1 版中，如果作用域以打开`dwOpenFlags`设置为 ofRead，有资格享受共享。 也就是说，如果后续调用`OpenScope`传入以前打开的文件的名称，重用现有的范围，且不会创建一组新的数据结构。 但是，由于这种共享会出现问题。  
  
 在.NET Framework 2.0 版中，作用域以打开`dwOpenFlags`不再共享设置为 ofRead。 使用 ofReadOnly 值以允许要共享的作用域。 共享作用域后，使用"读/写"元数据接口的查询将失败。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 用作 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataDispenser 接口](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx 接口](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
