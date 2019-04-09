---
title: IHostAssemblyStore::ProvideAssembly 方法
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62a8be1e330338043df50bd80576b5aa65447b9c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111899"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly 方法
获取未被引用程序集的引用[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) ，则返回从[ihostassemblymanager:: Getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)。 公共语言运行时 (CLR) 调用`ProvideAssembly`每个程序集未显示在列表中。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>参数  
 `pBindInfo`  
 [in]一个指向[AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)主机用于确定是否存在任何版本控制策略，包括某些绑定特征的实例和要绑定到的程序集。  
  
 `pAssemblyId`  
 [out]指向此请求的程序集的唯一标识符的`IStream`。  
  
 `pHostContext`  
 [out]用于确定无需使用一个平台，请求的程序集的证据的特定于宿主的数据的指针调用来调用。 `pHostContext` 对应于<xref:System.Reflection.Assembly.HostContext%2A>的托管属性<xref:System.Reflection.Assembly>类。  
  
 `ppStmAssemblyImage`  
 [out]指向的地址的指针`IStream`，其中包含要加载，或者如果找不到程序集，则为 null 的可移植可执行 (PE) 映像。  
  
 `ppStmPDB`  
 [out]指向的地址的指针`IStream`如果找不到.pdb 文件包含的程序调试 (PDB) 的信息或为 null。  
  
## <a name="return-value"></a>返回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly` 已成功返回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。|  
|HOST_E_TIMEOUT|呼叫已超时。|  
|HOST_E_NOT_OWNER|调用方不拥有该锁。|  
|HOST_E_ABANDONED|事件已取消时被阻塞的线程或纤程正在等待它。|  
|E_FAIL|发生未知的灾难性故障。 如果某方法返回 E_FAIL，CLR 不再在进程内可用。 对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。|  
|COR_E_FILENOTFOUND (0x80070002)|找不到请求的程序集。|  
|E_NOT_SUFFICIENT_BUFFER|指定的缓冲区大小`pAssemblyId`不足够大以保存宿主希望返回的标识符。|  
  
## <a name="remarks"></a>备注  
 返回标识值`pAssemblyId`host 所指定。 标识符在进程生存期内必须是唯一的。 CLR 使用此值将流作为唯一标识符。 它会检查每个值的值与`pAssemblyId`返回的其他调用`ProvideAssembly`。 如果主机返回相同`pAssemblyId`值的另一个`IStream`，CLR 将检查是否已映射了该流的内容。 如果是这样，在运行时加载而不是映射新映像的现有副本。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRAssemblyReferenceList 接口](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 接口](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore 接口](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
