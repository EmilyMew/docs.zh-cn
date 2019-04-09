---
title: ICorProfilerInfo2::DoStackSnapshot 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12ef215253ca02048a5a3fc2c7c682823233929f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108077"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot 方法
对指定线程的堆栈上指导托管的帧，并将信息发送到通过回调探查器。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
## <a name="parameters"></a>参数  
 `thread`  
 [in]目标线程的 ID。  
  
 传递 null，在`thread`会生成当前线程的快照。 如果`ThreadID`的传递不同的线程，公共语言运行时 (CLR) 会挂起该线程、 执行快照，并继续。  
  
 `callback`  
 [in]实现的指针[StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)由 CLR 提供有关每个托管的帧和非托管帧的每次运行探查器调用的方法。  
  
 `StackSnapshotCallback`探查器编写器实现方法。  
  
 `infoFlags`  
 [in]值为[COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)枚举，指定要返回的每个框架中通过传递的数据量`StackSnapshotCallback`。  
  
 `clientData`  
 [in]指向客户端数据，直接通过传递给`StackSnapshotCallback`回调函数。  
  
 `context`  
 [in]一个指向 Win32`CONTEXT`结构，它用于设定种子堆栈遍历。 Win32`CONTEXT`结构包含的 CPU 寄存器的值，表示在特定时刻 CPU 的状态。  
  
 该种子可以帮助 CLR 确定从何处开始堆栈遍历，如果堆栈的顶部为非托管帮助器代码;否则，将忽略种子。 必须提供异步遍历的种子。 如果正在执行是同步遍历，没有种子是必需的。  
  
 `context`参数才有效，仅当传入的 COR_PRF_SNAPSHOT_CONTEXT 标志`infoFlags`参数。  
  
 `contextSize`  
 [in]大小`CONTEXT`结构，它引用的`context`参数。  
  
## <a name="remarks"></a>备注  
 传递 null`thread`会生成当前线程的快照。 目标线程挂起时，才可以拍摄快照的其他线程。  
  
 当探查器要遍历堆栈时，它将调用`DoStackSnapshot`。 CLR 从该调用返回之前，它将调用你`StackSnapshotCallback`几次，一次为每个托管帧 （或非托管帧） 在堆栈上。 遇到非托管的帧时，您必须自己遍历它们。  
  
 在其中堆栈被遍历的顺序是如何帧被推入到堆栈的相反： 最后一个叶 （上一次推送） 帧第一个、 主 （第一个推送） 框架。  
  
 有关如何对探查器以审核托管的堆栈的详细信息，请参阅[.NET Framework 2.0 中的 Profiler 堆栈审核：基础和超越](https://go.microsoft.com/fwlink/?LinkId=73638)。  
  
 以下各节中所述，可以同步或异步的堆栈遍历。  
  
## <a name="synchronous-stack-walk"></a>同步堆栈遍历  
 同步堆栈遍历涉及对回调的响应中遍历当前线程的堆栈。 它不需要种子设定或挂起。  
  
 进行同步时，调用以响应调用的探查器的一个 CLR [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (或[ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) 方法调用`DoStackSnapshot`要遍历的堆栈当前线程。 如果想要查看堆栈的外观在通知等，这是很有用[icorprofilercallback:: Objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)。 只需调用`DoStackSnapshot`从你`ICorProfilerCallback`方法，传递 null，在`context`和`thread`参数。  
  
## <a name="asynchronous-stack-walk"></a>异步堆栈遍历  
 异步堆栈遍历要求遍历不同线程的堆栈或不在响应回调，而通过截取当前线程的指令指针遍历当前线程的堆栈。 异步遍历需要种子如果堆栈的顶部是不是一个平台的一部分的非托管的代码调用 (PInvoke) 或 COM 调用，但在 CLR 自身中的帮助器代码。 例如，执行在实时 (JIT) 编译或垃圾收集的代码是帮助器代码。  
  
 通过直接挂起目标线程获取种子并自己，直到找到的最顶层的遍历其堆栈托管帧。 挂起目标线程后，获取目标线程的当前寄存器上下文。 接下来，确定是否寄存器上下文指向非托管代码通过调用[icorprofilerinfo:: Getfunctionfromip](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) -如果它返回`FunctionID`等于零，该框架是在非托管的代码。 现在，遍历堆栈，直到到达第一个托管的帧，然后计算种子上下文基于该范围中寄存器上下文。  
  
 调用`DoStackSnapshot`使用种子上下文开始异步堆栈遍历。 如果未提供种子，`DoStackSnapshot`可能会跳过堆栈顶部的托管的帧，因此，将为您提供完整的堆栈审核。 如果你提供种子，则必须指向 JIT 编译或本机映像生成器 (Ngen.exe)-生成的代码;否则为`DoStackSnapshot`返回故障代码，CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX。  
  
 异步堆栈遍历可轻松地会导致死锁或访问冲突，除非您遵循以下准则：  
  
-   当你直接暂停线程时，请记住只有从未运行过托管的代码的线程才可以挂起另一个线程。  
  
-   始终阻止您[icorprofilercallback:: Threaddestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)回调该线程的堆栈遍历直到完成。  
  
-   在分析器调用到可以触发垃圾回收的 CLR 函数时，则不持有锁。 即，如果拥有线程可能会使触发垃圾回收的调用并持有锁。  
  
 此外，还有的死锁风险如果调用`DoStackSnapshot`从您的探查器已创建，以便您可以放心离开，单独的目标线程的堆栈的线程。 第一次你创建的线程进入某些`ICorProfilerInfo*`方法 (包括`DoStackSnapshot`)，CLR 将执行每个线程，该线程上的特定于 CLR 的初始化。 如果您的探查器已挂起目标线程想要遍历，其堆栈，并且该目标线程恰巧拥有锁所需执行此每个线程初始化，将发生死锁。 若要避免这种死锁，进行初始调用到`DoStackSnapshot`单独从在探查器创建的线程以遍历目标线程，但不是先挂起目标线程。 此初始调用可确保每个线程初始化可以完成而无需死锁。 如果`DoStackSnapshot`成功，并且报告至少一个框架，该时间点后，将会挂起任何目标线程和调用该探查器创建线程安全`DoStackSnapshot`来遍历该目标线程的堆栈。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerInfo 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
