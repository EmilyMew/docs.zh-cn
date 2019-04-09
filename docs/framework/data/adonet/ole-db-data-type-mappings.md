---
title: OLE DB 数据类型映射
ms.date: 03/30/2017
ms.assetid: 04bcb259-59d3-4fd7-894d-4f0dd0c68069
ms.openlocfilehash: 09fab7c5df99ffdb0aef6d32a8ad5ca1ed446d42
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100582"
---
# <a name="ole-db-data-type-mappings"></a>OLE DB 数据类型映射
下表显示了针对适用于 ADO 和 OLE DB 的 .NET Framework 数据提供程序 ([!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]) 中的数据类型推断出的 <xref:System.Data.OleDb> 类型。 另外，还列出了 <xref:System.Data.OleDb.OleDbDataReader> 的类型化访问器方法。  
  
|ADO 类型|OLE DB 类型|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 类型|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 类型化取值函数|  
|--------------|-----------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|adBigInt|DBTYPE_I8|Int64|GetInt64()|  
|adBinary|DBTYPE_BYTES|Byte[]|GetBytes()|  
|adBoolean|DBTYPE_BOOL|Boolean|GetBoolean()|  
|adBSTR|DBTYPE_BSTR|String|GetString()|  
|adChapter|DBTYPE_HCHAPTER|通过 `DataReader` 支持。 请参阅[使用 DataReader 检索数据](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)。|GetValue()|  
|adChar|DBTYPE_STR|String|GetString()|  
|adCurrency|DBTYPE_CY|十进制|GetDecimal()|  
|adDate|DBTYPE_DATE|DateTime|GetDateTime()|  
|adDBDate|DBTYPE_DBDATE|DateTime|GetDateTime()|  
|adDBTime|DBTYPE_DBTIME|DateTime|GetDateTime()|  
|adDBTimeStamp|DBTYPE_DBTIMESTAMP|DateTime|GetDateTime()|  
|adDecimal|DBTYPE_DECIMAL|十进制|GetDecimal()|  
|adDouble|DBTYPE_R8|Double|GetDouble()|  
|adError|DBTYPE_ERROR|ExternalException|GetValue()|  
|adFileTime|DBTYPE_FILETIME|DateTime|GetDateTime()|  
|adGUID|DBTYPE_GUID|GUID|GetGuid()|  
|adIDispatch|DBTYPE_IDISPATCH *|对象|GetValue()|  
|adInteger|DBTYPE_I4|Int32|GetInt32()|  
|adIUnknown|DBTYPE_IUNKNOWN *|对象|GetValue()|  
|adNumeric|DBTYPE_NUMERIC|十进制|GetDecimal()|  
|adPropVariant|DBTYPE_PROPVARIANT|对象|GetValue()|  
|adSingle|DBTYPE_R4|Single|GetFloat()|  
|adSmallInt|DBTYPE_I2|Int16|GetInt16()|  
|adTinyInt|DBTYPE_I1|Byte|GetByte()|  
|adUnsignedBigInt|DBTYPE_UI8|UInt64|GetValue()|  
|adUnsignedInt|DBTYPE_UI4|UInt32|GetValue()|  
|adUnsignedSmallInt|DBTYPE_UI2|UInt16|GetValue()|  
|adUnsignedTinyInt|DBTYPE_UI1|Byte|GetByte()|  
|adVariant|DBTYPE_VARIANT|对象|GetValue()|  
|adWChar|DBTYPE_WSTR|String|GetString()|  
|adUserDefined|DBTYPE_UDT|不受支持||  
|adVarNumeric|DBTYPE_VARNUMERIC|不受支持||  
  
 \* 对于 OLE DB 类型`DBTYPE_IUNKNOWN`和`DBTYPE_IDISPATCH`，对象引用是指针的封送表示形式。  
  
## <a name="see-also"></a>请参阅

- [在 ADO.NET 中检索和修改数据](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
