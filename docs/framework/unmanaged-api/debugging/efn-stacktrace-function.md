---
title: _EFN_StackTrace 函数
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfbdbb389f9945ffeea649bcddd45bee8caf2496
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119985"
---
# <a name="efnstacktrace-function"></a>_EFN_StackTrace 函数
提供托管堆栈跟踪的文本表示形式以及 `CONTEXT` 记录的数组，其中每项对应非托管代码和托管代码之间的每个转换。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
## <a name="parameters"></a>参数  
 `Client`  
 [in]正在调试客户端。  
  
 `wszTextOut`  
 [out]堆栈跟踪的文本表示形式。  
  
 `puiTextLength`  
 [out]指向中的字符数的`wszTextOut`。  
  
 `pTransitionContexts`  
 [out]转换上下文的数组。  
  
 `puiTransitionContextCount`  
 [out]一个指向数组中的转换上下文的数目。  
  
 `uiSizeOfContext`  
 [in]上下文结构的大小。  
  
 `Flags`  
 [in]设置为 0 或 SOS_STACKTRACE_SHOWADDRESSES (0x01) 以显示 EBP 寄存器和 enter 堆栈指针 (ESP) 前面每个`module!functionname`行。  
  
## <a name="remarks"></a>备注  
 `_EFN_StackTrace`结构可从 WinDbg 编程接口调用。 使用参数，如下所示：  
  
-   如果`wszTextOut`为 null，`puiTextLength`是不为 null，该函数将返回的字符串长度以`puiTextLength`。  
  
-   如果`wszTextOut`是不为 null，函数将存储中的文本`wszTextOut`最多所指示的位置`puiTextLength`。 成功返回是否有足够的空间中的缓冲区，则返回 E_OUTOFMEMORY 如果缓冲区不够长。  
  
-   如果该函数的转换部分则将忽略`pTransitionContexts`和`puiTransitionContextCount`都为 null。 在这种情况下，该函数提供了只有函数名称的文本输出的调用方。  
  
-   如果`pTransitionContexts`为 null，`puiTransitionContextCount`是不为 null，则该函数将返回所需数量的上下文中的条目`puiTransitionContextCount`。  
  
-   如果`pTransitionContexts`是不为 null，则该函数将它作为数组的长度结构`puiTransitionContextCount`。 通过给定结构大小`uiSizeOfContext`，并且必须是大小[SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)或`CONTEXT`体系结构。  
  
-   `wszTextOut` 采用以下格式：  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   如果以十六进制表示的偏移量为 0x0，写入没有偏移量。  
  
-   如果没有任何托管的代码的线程上当前上下文中，该函数将返回 SOS_E_NOMANAGEDCODE。  
  
-   `Flags`参数为 0 或 SOS_STACKTRACE_SHOWADDRESSES 若要查看每个前面的 EBP 和 ESP`module!functionname`行。 默认情况下，它为 0。  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** SOS_Stacktrace.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [调试全局静态函数](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
