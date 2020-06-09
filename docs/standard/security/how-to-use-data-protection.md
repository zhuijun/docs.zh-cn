---
title: 如何：使用数据保护
description: 了解如何通过访问 .NET 中的数据保护 API （DPAPI）来使用数据保护。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DPAPI
- encryption [.NET Framework], data protection API
- data [.NET Framework], decryption
- ProtectedMemory class, about ProtectedMemory class
- ProtectedData class, about ProtectedData class
- cryptography [.NET Framework], data protection API
- data protection API [.NET Framework]
- decryption
- data [.NET Framework], encryption
ms.assetid: 606698b0-cb1a-42ca-beeb-0bea34205d20
ms.openlocfilehash: c7f88105727dfd33c87a815054aa317ac2052e83
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598588"
---
# <a name="how-to-use-data-protection"></a>如何：使用数据保护
.NET Framework 提供对数据保护 API (DPAPI) 的访问，这允许你使用来自当前用户帐户或计算机的信息对数据进行加密。  当使用 DPAPI 时，你会使显式生成和存储加密密钥的困难问题得到缓解。  
  
 使用 <xref:System.Security.Cryptography.ProtectedMemory> 类加密内存中的字节数组。  此功能在 Microsoft Windows XP 和更高版本操作系统中可用。  你可以指定由当前进程加密的内存只能由当前进程、由所有进程、或从相同的用户上下文解密。  请参阅 <xref:System.Security.Cryptography.MemoryProtectionScope> 枚举以获取 <xref:System.Security.Cryptography.ProtectedMemory> 选项的详细说明。  
  
 使用 <xref:System.Security.Cryptography.ProtectedData> 类来加密字节数组的副本。 此功能在 Microsoft Windows 2000 和更高版本操作系统中可用。  你可以指定由当前用户帐户加密的数据仅能通过相同的用户帐户解密，也可以指定由当前用户帐户加密的数据可以通过计算机上的任何帐户进行解密。  请参阅 <xref:System.Security.Cryptography.DataProtectionScope> 枚举以获取 <xref:System.Security.Cryptography.ProtectedData> 选项的详细说明。  
  
### <a name="to-encrypt-in-memory-data-using-data-protection"></a>若要使用数据保护对内存中数据进行加密  
  
1. 调用静态 <xref:System.Security.Cryptography.ProtectedMemory.Protect%2A> 方法，同时传递要加密的字节数组、平均信息量和内存保护范围。  
  
### <a name="to-decrypt-in-memory-data-using-data-protection"></a>若要使用数据保护对内存中数据进行解密  
  
1. 调用静态 <xref:System.Security.Cryptography.ProtectedMemory.Unprotect%2A> 方法，同时传递要解密的字节数组和内存保护范围。  
  
### <a name="to-encrypt-data-to-a-file-or-stream-using-data-protection"></a>若要使用数据保护将数据加密到文件或流  
  
1. 创建随机平均信息量。  
  
2. 调用静态 <xref:System.Security.Cryptography.ProtectedData.Protect%2A> 方法，同时传递要加密的字节数组、平均信息量和数据保护范围。  
  
3. 将加密的数据写入文件或流。  
  
### <a name="to-decrypt-data-from-a-file-or-stream-using-data-protection"></a>若要使用数据保护从文件或流解密数据  
  
1. 从文件或流中读取加密的数据。  
  
2. 调用静态 <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A> 方法，同时传递要解密的字节数组和数据保护范围。  
  
## <a name="example"></a>示例  
 下面的代码示例演示加密和解密的两种形式。  首先，该代码示例对内存中的字节数组进行加密，然后将其解密。  接下来，该代码示例对字节数组的副本进行加密、将其保存到文件、从文件加载回数据，然后对数据进行解密。  此示例显示原始数据、加密的数据和已解密的数据。  
  
 [!code-csharp[DPAPI-HowTO#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DPAPI-HowTO/cs/sample.cs#1)]
 [!code-vb[DPAPI-HowTO#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DPAPI-HowTO/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
  
- 包括对 `System.Security.dll` 的引用。  
  
- 包括 <xref:System>、<xref:System.IO>、<xref:System.Security.Cryptography> 和 <xref:System.Text> 命名空间。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Security.Cryptography.ProtectedMemory>
- <xref:System.Security.Cryptography.ProtectedData>
