---
title: IMetaDataTables 接口
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b2298e2d67e8a50e11d53d864f0e78f3b549e45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131412"
---
# <a name="imetadatatables-interface"></a>IMetaDataTables 接口
提供存储和检索表中元数据信息的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetBlob 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|获取一个指向二进制大型对象 (BLOB) 中的指定的列索引处。|  
|[GetBlobHeapSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|获取以字节为单位，在 BLOB 堆的大小。|  
|[GetCodedTokenInfo 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|获取与指定的行索引相关联的标记数组的指针。|  
|[GetColumn 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|获取一个指针指向包含在指定的列索引，在指定的表索引的表中的列中的值。|  
|[GetColumnInfo 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|指定表中获取有关指定的列的数据。|  
|[GetGuid 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|获取从指定索引处的行的 GUID。|  
|[GetGuidHeapSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|获取以字节为单位，GUID 堆的大小。|  
|[GetNextBlob 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|获取表中的下一个 BLOB 的索引。|  
|[GetNextGuid 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|获取当前表的列中的下一步的 GUID 值的索引。|  
|[GetNextString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|获取当前表的列中的下一个字符串的索引。|  
|[GetNextUserString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|获取包含在当前表列中的下一步的硬编码字符串的行的索引。|  
|[GetNumTables 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|获取在当前作用域中的表数`IMetaDataTables`实例。|  
|[GetRow 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|获取指定的行索引处，在指定的表索引的表中的行。|  
|[GetString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|获取当前引用作用域中从表的列的指定索引处的字符串。|  
|[GetStringHeapSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|获取以字节为单位的字符串堆的大小。|  
|[GetTableIndex 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|获取指定的标记所引用的表的索引。|  
|[GetTableInfo 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|获取指定的表索引处的名称、 行大小、 行数、 列数和表的键列索引。|  
|[GetUserString 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|获取在当前作用域中的字符串列中的指定索引处的硬编码的字符串。|  
|[GetUserStringHeapSize 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|获取以字节为单位的用户字符串堆的大小。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cor.h  
  
 **库：** 用作 MsCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据接口](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataTables2 接口](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
