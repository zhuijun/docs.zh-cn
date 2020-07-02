---
ms.openlocfilehash: c20d5fb3d700ba7649e423a79e4598b327c50a00
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622224"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>传递和比较 UInt16 值时，代码生成不正确

#### <a name="details"></a>详细信息

由于 .NET Framework 4.7 中引入了更改，在某些情况下，.NET Framework 4.7 上运行的应用程序中由 JIT 编译器生成的代码错误地比较了两个 <code>T:System.UInt16</code> 值。 有关详细信息，请参阅 GitHub.com 上的[问题 #11508：传递和比较 ushort 参数时不提示错误 codegen](https://github.com/dotnet/coreclr/issues/11508)。

#### <a name="suggestion"></a>建议

如果在 .NET Framework 4.7 中比较 16 位无符号值时遇到问题，请升级到 .NET Framework 4.7.1。

| “属性”    | 值       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.7|
|类型|运行时|
