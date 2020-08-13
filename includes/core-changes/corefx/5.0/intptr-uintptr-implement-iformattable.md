---
ms.openlocfilehash: 3d29848e12d496d2d53c204e00ef8604831495e1
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024689"
---
### <a name="intptr-and-uintptr-implement-iformattable"></a>IntPtr 和 UIntPtr 实现 IFormattable

<xref:System.IntPtr> 和 <xref:System.UIntPtr> 现在实现 <xref:System.IFormattable>。 检查 <xref:System.IFormattable> 支持的功能现在可能返回这些类型的不同结果，因为它们可能以格式说明符和区域性的形式传递。

#### <a name="change-description"></a>更改描述

在早期版本的 .NET 中，<xref:System.IntPtr> 和 <xref:System.UIntPtr> 不实现 <xref:System.IFormattable>。 检查 <xref:System.IFormattable> 的函数可回退到仅调用 <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> 或 <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType>，这意味着不会遵循格式说明符和区域性。

在 .NET 5.0 和更高版本中，<xref:System.IntPtr> 和 <xref:System.UIntPtr> 实现 <xref:System.IFormattable>。 检查 <xref:System.IFormattable> 支持的功能现在可能返回这些类型的不同结果，因为它们可能以格式说明符和区域性的形式传递。

此更改会影响内插字符串和 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> 等方案。

#### <a name="reason-for-change"></a>更改原因

<xref:System.IntPtr> 和 <xref:System.UIntPtr> 现在通过 `nint` 和 `nuint` 关键字获得 C# 语言支持。 更新了后备类型，以通过其他基元类型（例如 <xref:System.Int32?displayProperty=nameWithType>）公开的功能提供接近奇偶校验（如果可能）。

#### <a name="version-introduced"></a>引入的版本

5.0 预览版 4

#### <a name="recommended-action"></a>建议操作

如果不希望在显示这些类型的值时使用格式说明符或自定义区域性，则可以调用 `ToString()` 的 <xref:System.IntPtr.ToString?displayProperty=nameWithType> 和 <xref:System.UIntPtr.ToString?displayProperty=nameWithType> 重载。

#### <a name="category"></a>类别

Core .NET 库

#### <a name="affected-apis"></a>受影响的 API

无法通过 API 分析检测到。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
