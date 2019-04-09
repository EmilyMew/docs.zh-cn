---
title: LoggingLevelEnum 枚举
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fe8e1355382273a681e927897f4a8ff5814b8de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086502"
---
# <a name="logginglevelenum-enumeration"></a>LoggingLevelEnum 枚举
指示在托管线程记录事件时写入事件日志的描述性消息的严重级别。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`LTraceLevel0`|该消息是跟踪级别 0。|  
|`LTraceLevel1`|该消息是跟踪级别 1。|  
|`LTraceLevel2`|该消息是跟踪级别 2。|  
|`LTraceLevel3`|该消息是跟踪级别 3。|  
|`LTraceLevel4`|该消息是跟踪级别 4。|  
|`LStatusLevel0`|该消息为状态级别 0。|  
|`LStatusLevel1`|该消息是状态级别 1。|  
|`LStatusLevel2`|该消息是状态级别 2。|  
|`LStatusLevel3`|该消息是状态级别 3。|  
|`LStatusLevel4`|该消息是状态级别 4。|  
|`LWarningLevel`|该消息是警告级别。|  
|`LErrorLevel`|该消息是错误级别。|  
|`LPanicLevel`|该消息是 panic 级别。|  
  
## <a name="remarks"></a>备注  
 公共语言运行时 (CLR) 调用[icordebugmanagedcallback:: Logmessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)方法以通知调试器托管的线程记录事件。 CLR 将传递的值为`LoggingLevelEnum`枚举来指示托管的线程已写入到事件日志的消息的严重性级别。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Diagnostics.EventLog>
- [调试枚举](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
