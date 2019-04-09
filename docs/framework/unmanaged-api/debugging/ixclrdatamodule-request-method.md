---
title: IXCLRDataModule::Request 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a02a60668ae6caaad1940395822758331b93f550
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119790"
---
# <a name="ixclrdatamodulerequest-method"></a>IXCLRDataModule::Request 方法

若要填充缓冲区中提供了模块的数据的请求。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>语法
```
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a>参数

`reqCode`\
[in]请求类型发送。

`inBufferSize`\
[in] 要传入的输入缓冲区的大小。

`inBuffer`\
[in，size_is(inBufferSize)]要在请求中发送的原始数据的缓冲区指针。

`outBufferSize`\
[in]输出缓冲区的大小。

`outBuffer`\
[out，size_is(outBufferSize)]要用于存储请求响应的缓冲区指针。

## <a name="remarks"></a>备注

提供的方法属于`IXCLRDataModule`接口，并对应于虚拟方法表 36th 槽。

## <a name="requirements"></a>要求

**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
**标头：** None   
**库：** None  
**.NET Framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>请参阅

- [调试](index.md)
- [IXCLRDataModule 接口](ixclrdatamodule-interface.md)