---
title: 强命名（非托管 API 参考）
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32e74a76b6b1bedee4efc5715d0710c8efce2455
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120752"
---
# <a name="strong-naming-unmanaged-api-reference"></a>强命名（非托管 API 参考）
强命名 API 允许客户端管理程序集的强名称签名。  
  
 使用强名称对程序集进行签名将向包含程序集清单的文件添加公钥加密。 强名称签名帮助验证名称的唯一性，避免名称欺骗，并在解析引用时向调用方提供唯一标识。 但是，任何信任级别都不会与强名称关联。  
  
## <a name="in-this-section"></a>本节内容  
  
> [!NOTE]
>  从 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] 开始，所有这些函数都已弃用。 有关建议的替代方案，请参阅 [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) 接口。  
  
 [GetHashFromAssemblyFile 函数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 使用指定的哈希算法获取指定程序集文件的哈希。 从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [GetHashFromAssemblyFileW 函数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 使用指定的哈希算法获取指定为 Unicode 字符串的程序集文件的哈希。 从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [GetHashFromBlob 函数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 使用指定的哈希算法获取指定内存地址处的程序集的哈希。 从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [GetHashFromFile 函数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 生成指定文件内容的哈希。  从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [GetHashFromFileW 函数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 生成由 Unicode 字符串指定的文件内容的哈希。 从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [GetHashFromHandle 函数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 使用指定的哈希算法，生成具有指定文件句柄的文件内容的哈希。  从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameCompareAssemblies 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 确定两个程序集是否仅是强名称签名不同。 从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameErrorInfo 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 获取由其中一个强名称函数引发的最后一个错误代码。  
  
 [StrongNameFreeBuffer 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 释放先前调用 [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)、[StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md) 或 [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md) 强名称函数分配的内存。   从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameGetBlob 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 使用指定地址处可执行文件的二进制表示形式填充指定的缓冲区。 从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameGetBlobFromImage 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 获取指定内存地址处程序集映像的二进制表示形式。 从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameGetPublicKey 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 从私钥/公钥对中获取公钥。 从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameHashSize 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 使用指定的哈希算法获取哈希所需的缓冲区大小。  从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameKeyDelete 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 删除指定的密钥容器。 从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameKeyGen 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 创建新的公钥/私钥对，以便强名称使用。  从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameKeyGenEx 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 生成具有指定密钥大小的新公钥/私钥对，以便强名称使用。 从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameKeyInstall 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 将公钥/私钥对导入容器。  从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameSignatureGeneration 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 为指定的程序集生成强名称签名。   从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameSignatureGenerationEx 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 根据指定标志为指定的程序集生成强名称签名。    从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameSignatureSize 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 返回强名称签名的大小。 从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameSignatureVerification 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 获取一个值，该值指示提供的路径中的程序集清单是否包含根据指定标志验证的强名称签名。 从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameSignatureVerificationEx 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 获取一个值，该值指示提供的路径中的程序集清单是否包含强名称签名。  从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameSignatureVerificationFromImage 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 验证已映射到内存的程序集对关联的公钥是否有效。 从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameTokenFromAssembly 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 从指定的程序集文件创建强名称令牌。  从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameTokenFromAssemblyEx 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 从指定的程序集文件创建强名称令牌并返回公钥。 从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [StrongNameTokenFromPublicKey 函数](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 获取表示公钥的令牌。 从 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 开始，该函数已弃用。  
  
 [PublicKeyBlob 结构](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 表示二进制格式的公钥/私钥对中的公钥。  
  
## <a name="see-also"></a>请参阅

- [ICLRStrongName 接口](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [非托管 API 参考](../../../../docs/framework/unmanaged-api/index.md)
