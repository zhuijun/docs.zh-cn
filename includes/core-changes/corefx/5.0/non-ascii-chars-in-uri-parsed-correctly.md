---
ms.openlocfilehash: faf9459ab9002e6149560e2a3452265fa246bf6b
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720176"
---
### <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a>在 Unix 上正确分析包含非 ASCII 字符的 URI 路径

在 <xref:System.Uri?displayProperty=fullName> 类中修复了一个 bug，包含非 ASCII 字符的绝对 URI 路径现在可以在 Unix 平台上正确分析。

#### <a name="change-description"></a>更改描述

在早期版本的 .NET 中，不能在 Unix 平台上正确分析包含非 ASCII 字符的绝对 URI 路径，并且会复制该路径的段。 （绝对路径是以“/”开头的路径。）.NET 5.0 的分析问题已得以修复。 如果从早期版本的 .NET 迁移到 .NET 5.0 或更高版本，则会获得由 <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>、<xref:System.Uri.ToString?displayProperty=nameWithType> 和其他 <xref:System.Uri> 成员生成的不同的值。

在 Unix 上运行时，请考虑以下代码的输出。

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

先前 .NET 版本的输出：

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

.NET 5.0 或更高版本的输出：

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

#### <a name="version-introduced"></a>引入的版本

5.0

#### <a name="recommended-action"></a>建议操作

如果你具有需要和说明重复路径段的代码，则可以删除该代码。

#### <a name="category"></a>类别

Core .NET 库

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
