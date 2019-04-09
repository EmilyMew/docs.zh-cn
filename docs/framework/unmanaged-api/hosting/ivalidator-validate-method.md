---
title: IValidator::Validate 方法
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1fba06360a0c31e0a7fa3e61de9793bad14650fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127499"
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate 方法
验证指定的可移植可执行 (PE) 或 Microsoft 中间语言 (MSIL) 文件。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a>参数  
 `veh`  
 [in]一个指向`IVEHandler`处理验证错误的实例。  
  
 `pAppDomain`  
 [in]指向在其中加载的文件的应用程序域的指针。  
  
 `ulFlags`  
 [in]按位组合[ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)值，指示应执行的验证。  
  
 `ulMaxError`  
 [in]最大允许在退出验证之前的错误数。  
  
 `token`  
 [in]不使用。  
  
 `fileName`  
 [in]一个字符串，指定要验证的文件的名称。  
  
 `pe`  
 [in]指向在其中存储文件的内存缓冲区的指针。  
  
 `ulSize`  
 [in]以字节为单位，要验证的文件的大小。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** IValidator.idl, IValidator.h  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
