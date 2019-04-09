---
title: IMetaDataEmit::DefineMethod 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a67e8ce19a2acf5b4ee1d114858e00d93cb183b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115578"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod 方法
使用指定的签名中，创建方法或全局函数的定义，并将令牌返回到该方法定义。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT DefineMethod (      
    [in]  mdTypeDef         td,   
    [in]  LPCWSTR           szName,   
    [in]  DWORD             dwMethodFlags,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [in]  ULONG             ulCodeRVA,   
    [in]  DWORD             dwImplFlags,   
    [out] mdMethodDef      *pmd  
);  
```  
  
## <a name="parameters"></a>参数  
 `td`  
 [in]`mdTypedef`父类或父接口的方法的令牌。 设置`td`到`mdTokenNil`，如果您要定义全局函数。  
  
 `szName`  
 [in]Unicode 中的成员名称。  
  
 `dwMethodFlags`  
 [in]值为[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)枚举，用于指定方法或全局函数的属性。  
  
 `pvSigBlob`  
 [in]方法签名中。 保存签名中提供。 如果您需要指定任何参数的其他信息，请使用[imetadataemit:: Setparamprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)方法。  
  
 `cbSigBlob`  
 [in]中的字节计数`pvSigBlob`。  
  
 `ulCodeRVA`  
 [in]代码的地址。  
  
 `dwImplFlags`  
 [in]值为[CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)枚举，用于指定该方法的实现功能。  
  
 `pmd`  
 [out]成员标记中。  
  
## <a name="remarks"></a>备注  
 元数据 API 可保证按给定的封闭类或接口中指定的调用方发出这些方法的相同顺序保留`td`参数。  
  
 有关使用的其他信息`DefineMethod`和特定参数设置如下。  
  
## <a name="slots-in-the-v-table"></a>V-表中的槽  
 运行时使用的方法定义以设置 v 表槽。 在一个或多个槽需要是已跳过、 此类情况下并保持与 COM 接口布局相同的虚拟方法定义为采用槽或 v-表; 中的槽设置`dwMethodFlags`到`mdRTSpecialName`的值[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)枚举和名称指定为：  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>
  
 其中*SequenceNumber*是方法的序列号和*槽数*是要跳过 v 表中的槽数。 如果*槽数*是省略，则假定为 1。 这些虚拟方法不能从托管或非托管代码调用，任何尝试从托管或非托管代码中调用它们，将引发异常。 其唯一用途是占用空间为 COM 集成运行时生成的 v 表中。  
  
## <a name="duplicate-methods"></a>重复的方法  
 不应定义重复的方法。 也就是说，不应调用`DefineMethod`中的值重复一`td`， `wzName`，和`pvSig`参数。 (这三个参数组合在一起唯一地定义的方法。)。 但是，可以使用重复三次，前提是，对于其中一个方法定义，您将设置`mdPrivateScope`位`dwMethodFlags`参数。 (`mdPrivateScope`位意味着编译器将发出对此方法定义的引用。)  
  
## <a name="method-implementation-information"></a>方法的实施信息  
 声明的方法时通常不知道有关方法实现的信息。 因此，不需要传递中的值`ulCodeRVA`并`dwImplFlags`参数调用时`DefineMethod`。 可以通过更高版本提供的值[imetadataemit:: Setmethodimplflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)或[imetadataemit:: Setrva](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)根据。  
  
 在某些情况下，如平台调用 (PInvoke) 或 COM 互操作方案中，未将提供方法正文，和`ulCodeRVA`应设置为零。 在这些情况下，该方法不应将标记为抽象，因为运行时将查找其实现。  
  
## <a name="defining-a-method-for-pinvoke"></a>定义一个方法的 PInvoke  
 若要通过 PInvoke 调用每个非托管函数，必须定义表示目标的非托管函数的托管的方法。 若要定义的托管的方法，请使用`DefineMethod`某些设置为特定值，具体取决于 PInvoke 的使用方式的参数：  
  
-   True PInvoke-涉及到驻留在非托管 DLL 的外部的非托管方法的调用。  
  
-   本地 PInvoke-涉及到在当前托管模块中嵌入本机非托管方法的调用。  
  
 下表中提供的参数设置。  
  
|参数|值为 true 的 PInvoke 的|值为本地 PInvoke 的|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||设置`mdStatic`; 清除`mdSynchronized`和`mdAbstract`。|  
|`pvSigBlob`|一个有效的公共语言运行时 (CLR) 方法签名，使用有效的参数将托管类型。|使用有效的参数有效的 CLR 方法签名的托管类型。|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|设置`miCil`和`miManaged`。|设置`miNative`和`miUnmanaged`。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 用作 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataEmit 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
