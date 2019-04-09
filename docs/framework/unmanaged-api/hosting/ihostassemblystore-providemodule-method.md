---
title: IHostAssemblyStore::ProvideModule 方法
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e07e2c3f2c6000f5a081b13316c269f322b1ef8a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078333"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule 方法
解析程序集或链接 （而不是嵌入） 中的模块资源文件。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>参数  
 `pBindInfo`  
 [in]一个指向[ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)实例，它描述请求的模块<xref:System.AppDomain>，程序集和模块名称。  
  
 `pdwModuleId`  
 [out]指向的唯一标识符的`IStream`包含已加载的模块。  
  
 `ppStmModuleImage`  
 [out]指向的地址的指针`IStream`对象，其中包含要加载的可移植可执行 (PE) 映像，或者如果找不到该模块，则为 null。  
  
 `ppStmPDB`  
 [out]指向的地址的指针`IStream`对象，其中包含请求的模块，与程序调试 (PDB) 信息，或者如果找不到.pdb 文件，则为 null。  
  
## <a name="return-value"></a>返回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`ProvideModule` 已成功返回。|  
|HOST_E_CLRNOTAVAILABLE|公共语言运行时 (CLR) 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。|  
|HOST_E_TIMEOUT|呼叫已超时。|  
|HOST_E_NOT_OWNER|调用方不拥有该锁。|  
|HOST_E_ABANDONED|事件已取消时被阻塞的线程或纤程正在等待它。|  
|E_FAIL|发生未知的灾难性故障。 如果某方法返回 E_FAIL，CLR 不再在进程内可用。 对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。|  
|COR_E_FILENOTFOUND (0x80070002)|无法找到请求的程序集或链接的资源。|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId` 不足够大以包含宿主希望返回的标识符。|  
  
## <a name="remarks"></a>备注  
 返回标识值`pdwModuleId`host 所指定。 标识符在进程生存期内必须是唯一的。 CLR 使用此值关联的流作为唯一标识符。 它会检查每个值的值与`pAssemblyId`返回通过调用[ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)和的值针对`pdwModuleId`返回的其他调用`ProvideModule`。 如果主机的另一个返回相同的标识符值`IStream`，CLR 将检查是否已映射了该流的内容。 如果是这样，CLR 加载而不是映射新映像的现有副本。 因此，标识符必须不重叠，从返回的程序集标识符`ProvideAssembly`。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRAssemblyReferenceList 接口](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 接口](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore 接口](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
