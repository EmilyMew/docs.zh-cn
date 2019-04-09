---
title: Oracle 数据类型映射
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: c1fb3a6838e6a1b242255d4035c10ab0ec07d536
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104567"
---
# <a name="oracle-data-type-mappings"></a>Oracle 数据类型映射
下表列出 Oracle 数据类型及其与 <xref:System.Data.OracleClient.OracleDataReader> 的映射。  
  
|Oracle 数据类型|由 OracleDataReader.GetValue 返回的 .NET Framework 数据类型|由 OracleDataReader.GetOracleValue 返回的 OracleClient 数据类型|备注|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BFILE**|**Byte[]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte[]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**十进制**|<xref:System.Data.OracleClient.OracleNumber>|此数据类型是其别名**数量**数据类型，而是，以便<xref:System.Data.OracleClient.OracleDataReader>返回**System.Decimal**或<xref:System.Data.OracleClient.OracleNumber>而不是浮点值。 使用该 .NET Framework 数据类型可能导致溢出。|  
|**INTEGER**|**十进制**|<xref:System.Data.OracleClient.OracleNumber>|此数据类型是其别名**NUMBER(38)** 数据类型，而是，以便<xref:System.Data.OracleClient.OracleDataReader>返回**System.Decimal**或<xref:System.Data.OracleClient.OracleNumber>而不是一个整数值。 使用该 .NET Framework 数据类型可能导致溢出。|  
|**INTERVAL YEAR TO MONTH**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**INTERVAL DAY TO SECOND**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**LONG RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**NUMBER**|**十进制**|<xref:System.Data.OracleClient.OracleNumber>|使用该 .NET Framework 数据类型可能导致溢出。|  
|**NVARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||Oracle **REF CURSOR**数据类型不受<xref:System.Data.OracleClient.OracleDataReader>对象。|  
|**ROWID**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**TIMESTAMP WITH LOCAL TIME ZONE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**TIMESTAMP WITH TIME ZONE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**UNSIGNED INTEGER**|**数字**|<xref:System.Data.OracleClient.OracleNumber>|此数据类型是其别名**NUMBER(38)** 数据类型，而是，以便<xref:System.Data.OracleClient.OracleDataReader>返回**System.Decimal**或<xref:System.Data.OracleClient.OracleNumber>而不是无符号的整数值。 使用该 .NET Framework 数据类型可能导致溢出。|  
|**VARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
  
 下表列出 Oracle 数据类型和.NET Framework 数据类型 (**System.Data.DbType**和<xref:System.Data.OracleClient.OracleType>) 作为参数绑定时使用。  
  
|Oracle 数据类型|要绑定为参数的 DbType 枚举|要绑定为参数的 OracleType 枚举|备注|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle 只允许绑定**BFILE**作为**BFILE**参数。 Oracle.NET 数据提供程序不会不会自动为您构造如果您尝试绑定一个非**BFILE**值，例如**byte []** 或<xref:System.Data.OracleClient.OracleBinary>。|  
|**BLOB**||**Blob**|Oracle 只允许绑定**BLOB**作为**BLOB**参数。 Oracle.NET 数据提供程序不会不会自动为您构造如果您尝试绑定一个非**BLOB**值，例如**byte []** 或<xref:System.Data.OracleClient.OracleBinary>。|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**Clob**|Oracle 只允许绑定**CLOB**作为**CLOB**参数。 Oracle.NET 数据提供程序不会不会自动为您构造如果您尝试绑定一个非**CLOB**值，例如**System.String**或<xref:System.Data.OracleClient.OracleString>。|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Single、Double、Decimal**|**Float、Double、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 确定**System.Data.DBType**和<xref:System.Data.OracleClient.OracleType>。|  
|**INTEGER**|**SByte、Int16、Int32、Int64、Decimal**|**SByte、Int16、Int32、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 确定**System.Data.DBType**和<xref:System.Data.OracleClient.OracleType>。|  
|**INTERVAL YEAR TO MONTH**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> 使用这两个 Oracle 9i 客户端和服务器软件时才可用。|  
|**INTERVAL DAY TO SECOND**|**对象**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> 使用这两个 Oracle 9i 客户端和服务器软件时才可用。|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**LONG RAW**|**二进制**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle 只允许绑定**NCLOB**作为**NCLOB**参数。 Oracle.NET 数据提供程序不会不会自动为您构造如果您尝试绑定一个非**NCLOB**值，例如**System.String**或<xref:System.Data.OracleClient.OracleString>。|  
|**NUMBER**|**VarNumeric**|**数字**||  
|**NVARCHAR2**|**String**|**NVarChar**||  
|**RAW**|**二进制**|**Raw**||  
|**REF CURSOR**||**Cursor**|有关详细信息，请参阅[Oracle REF Cursor](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)。|  
|**ROWID**|**AnsiString**|**Rowid**||  
|**TIMESTAMP**|**DateTime**|**时间戳**|<xref:System.Data.OracleClient.OracleType> 使用这两个 Oracle 9i 客户端和服务器软件时才可用。|  
|**TIMESTAMP WITH LOCAL TIME ZONE**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> 使用这两个 Oracle 9i 客户端和服务器软件时才可用。|  
|**TIMESTAMP WITH TIME ZONE**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> 使用这两个 Oracle 9i 客户端和服务器软件时才可用。|  
|**UNSIGNED INTEGER**|**Byte、UInt16、UInt32、UInt64、Decimal**|**Byte、UInt16、Uint32、Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> 确定**System.Data.DBType**和<xref:System.Data.OracleClient.OracleType>。|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **InputOutput**，**输出**，并**ReturnValue** **ParameterDirection**所使用的值<xref:System.Data.OracleClient.OracleParameter.Value%2A>属性<xref:System.Data.OracleClient.OracleParameter>对象是.NET Framework 数据类型，除非输入的值为 Oracle 数据类型 (例如，<xref:System.Data.OracleClient.OracleNumber>或<xref:System.Data.OracleClient.OracleString>)。 这不适用于**REF CURSOR**， **BFILE**，或**LOB**数据类型。  
  
## <a name="see-also"></a>请参阅

- [Oracle 和 ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET 托管提供程序和 DataSet 开发人员中心](https://go.microsoft.com/fwlink/?LinkId=217917)
