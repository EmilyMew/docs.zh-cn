---
title: CreateHistoryReader 函数
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e438006d6424866514e73119c05e8fd69d7ba62e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132257"
---
# <a name="createhistoryreader-function"></a>CreateHistoryReader 函数
创建指定的文件的历史记录读取。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a>参数  
 `wzFilePath`  
 [in]文件路径中。  
  
 `ppHistoryReader`  
 [out]成功完成后，将包含历史记录读取器指向的指针。  
  
## <a name="return-value"></a>返回值  
 定义在 WinError.h，除了下表中描述的值之外，此方法将返回标准 COM 错误代码。  
  
|返回代码|描述|  
|-----------------|-----------------|  
|S_OK|指示该方法已成功完成。|  
|E_INVALIDARG|指示`wzFilePath`或`ppHistoryReader`设置为 null 引用。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **库：** Fusion.dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [合成全局静态函数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
