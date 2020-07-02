---
ms.openlocfilehash: d21b2e092d460fdfc367d0f490228ed44ad5c6cc
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365634"
---
### <a name="built-in-support-for-winrt-is-removed-from-net"></a>已从 .NET 中删除对 WinRT 的内置支持

已删除对使用 .NET 中的 [Windows 运行时 (WinRT)](/uwp/winrt-cref/winrt-type-system) API 的内置支持。

#### <a name="version-introduced"></a>引入的版本

5.0 预览版 6

#### <a name="change-description"></a>更改描述

以前，CoreCLR 可能会使用 [Windows 元数据 (WinMD) 文件](/uwp/winrt-cref/winmd-files)来激活和使用 WinRT 类型。 从 .NET 5.0 开始，CoreCLR 不再能够直接使用 WinMD 文件。

如果尝试引用不受支持的程序集，则会收到 <xref:System.IO.FileNotFoundException>。 如果激活 WinRT 类，则会收到 <xref:System.PlatformNotSupportedException>。

做出此中断性变更的原因如下：

- 便于独立于 .NET 运行时单独开发和改进 WinRT。
- 为了与为其他操作系统（例如 iOS 和 Android）提供的互操作系统对称。
- 为了利用其他 .NET 功能，例如 C# 功能、中间语言 (IL) 链接和预先 (AOT) 编译。
- 为了简化 .NET 运行时基本代码。

#### <a name="recommended-action"></a>建议操作

- 删除对 [Microsoft.Windows.SDK.Contracts 包](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts)的引用，并将其替换为对 [Microsoft.Windows.SDK.NET 包](https://www.nuget.org/packages/microsoft.windows.sdk.net)的引用。

- 使用 [C#/WinRT](/windows/uwp/csharp-winrt/) 工具链在 .NET 5.0 及更高版本中生成或自定义 WinRT API 和类型。

#### <a name="category"></a>类别

Interop

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

-->
