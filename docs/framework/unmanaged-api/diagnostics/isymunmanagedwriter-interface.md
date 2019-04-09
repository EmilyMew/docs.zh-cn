---
title: ISymUnmanagedWriter 接口
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter
helpviewer_keywords:
- ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 7d6733ec-f081-4166-bc17-de09e16dc304
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ac95cd5b79a2e1762fa9adf29d4d7926ab4ab7a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150574"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter 接口
表示符号编写器，并提供方法用于定义文档、 序列点、 词法作用域和变量。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Abort 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|而不将符号提交到符号存储区关闭的符号编写器。|  
|[Close 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|将符号提交到符号存储区后关闭的符号编写器。|  
|[CloseMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|关闭当前方法。 一种方法关闭之后，可以在其中定义没有更多的符号。|  
|[CloseNamespace 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|关闭最近打开的命名空间。|  
|[CloseScope 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|关闭当前词法范围。|  
|[DefineConstant 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|定义常量值的名称。|  
|[DefineDocument 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|定义源文档。|  
|[DefineField 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|定义一个不在方法内的变量。|  
|[DefineGlobalVariable 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|定义单个全局变量。|  
|[DefineLocalVariable 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|在当前词法范围内定义单个变量。|  
|[DefineParameter 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|当前方法中定义的单个参数。|  
|[DefineSequencePoints 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|在当前方法内定义一组序列点。|  
|[GetDebugInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|返回编译器编写可移植可执行 (PE) 文件头中的调试目录项所需的信息。|  
|[Initialize 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|此编写器将与之关联的元数据发射器接口和设置输出文件将写入调试符号的名称。|  
|[Initialize2 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|设置此编写器将与之关联的元数据发射器接口，设置到的调试符号将被写入，并设置程序数据库 (PDB) 文件的最后一个位置的输出文件名称。|  
|[OpenMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|打开的符号信息发送到一个方法。|  
|[OpenNamespace 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|打开一个新的命名空间。|  
|[OpenScope 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|在当前方法中打开新的词法范围。|  
|[RemapToken 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|通知的符号编写器元数据标记在发出元数据已被重新映射。|  
|[SetMethodSourceRange 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|指定的真正开始和结束对源文件中的方法。|  
|[SetScopeRange 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|定义指定词法范围的偏移量范围。|  
|[SetSymAttribute 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|定义根据其名称的自定义属性。|  
|[SetUserEntryPoint 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|指定是此模块的入口点的用户定义的方法。|  
|[UsingNamespace 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|指定当前打开的词法范围内，使用给定的完全限定的命名空间名称。|  
  
## <a name="requirements"></a>要求  
 **标头：** CorSym.idl CorSym.h  
  
## <a name="see-also"></a>请参阅

- [诊断符号存储区接口](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2 接口](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3 接口](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
