---
title: CoInitializeEE 函数
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18f1a4ede1a362860df1271835600e7b867eac00
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127759"
---
# <a name="coinitializeee-function"></a>CoInitializeEE 函数
确保公共语言运行时执行引擎已加载到进程。 此函数已弃用在[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。 使用[iclrruntimehost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法相反。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a>参数  
 `fFlags`  
 [in]之一[COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md)枚举常量。  
  
## <a name="return-value"></a>返回值  
 Winerror.h 和下表中的值中定义，此方法将返回标准 COM 错误代码。  
  
|返回代码|描述|  
|-----------------|-----------------|  
|S_OK|执行引擎已成功加载。|  
|S_FALSE|执行引擎已加载。|  
|E_FAIL|无法加载执行引擎。|  
  
## <a name="remarks"></a>备注  
 如果它先前加载，则此方法加载的执行引擎。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 包含为 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据全局静态函数](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
