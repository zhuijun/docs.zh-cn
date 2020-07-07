---
title: 平台调用示例
description: 请参阅平台调用示例，该示例演示如何定义和调用 User32.dll 中的 MessageBox 函数。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [.NET Framework], platform invoke
- unmanaged functions
- COM interop, platform invoke
- platform invoke, examples
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 15926806-f0b7-487e-93a6-4e9367ec689f
ms.openlocfilehash: 97b0720b8954bc24a4058e6a03c32d32bd9e3180
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620802"
---
# <a name="platform-invoke-examples"></a>平台调用示例
以下示例演示如何定义和调用 User32.dll 中的 MessageBox 函数，并将简单字符串作为参数传递。 在这些示例中，<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> 字段设置为 Auto，以让目标平台确定字符宽度和字符串封送处理。  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)]
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)]
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 有关其他示例，请参阅[通过平台调用封送处理数据](marshaling-data-with-platform-invoke.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [在托管代码中创建原型](creating-prototypes-in-managed-code.md)
- [指定字符集](specifying-a-character-set.md)
