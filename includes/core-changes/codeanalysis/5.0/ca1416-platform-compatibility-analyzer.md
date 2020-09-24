---
ms.openlocfilehash: cd7860a5dfff1eb595625665382689733cffc94a
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90721278"
---
### <a name="ca1416-platform-compatibility"></a>CA1416：平台兼容性

从 .NET 5.0 开始，默认启用 .NET 代码分析器规则 [CA1416](/visualstudio/code-quality/ca1416)。 它会针对从未验证操作系统的调用站点调用特定于平台的 API 生成一个生成警告。

#### <a name="change-description"></a>更改说明

从 .NET 5.0 开始，.NET SDK 包括 [.NET 源代码分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。 其中一些规则会默认启用，包括 [CA1416](/visualstudio/code-quality/ca1416)。 如果项目包含违反此规则的代码，并已被配置为将警告视为错误，则此更改可能会中断生成。 当你在平台上下文未验证的位置使用特定于平台的 API 时，规则 CA1416 会通知你。

规则 [CA1416](/visualstudio/code-quality/ca1416)（平台兼容性分析器）与 .NET 5.0 中新增的一些其他功能配合工作。 .NET 5.0 引入了 <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> 和 <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>，可用于指定支持或不支持 API 的平台 。 如果没有这些属性，则假定所有平台都支持 API。 这些属性已应用于核心 .NET 库中特定于平台的 API。

在针对其所使用的 API 不可用的平台的项目中，规则 [CA1416](/visualstudio/code-quality/ca1416) 会标记任何未验证平台上下文的特定于平台的 API 调用。 现在，在不受支持的操作系统上调用 API 时，大多数用 <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> 和 <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> 属性修饰的 API 都会引发 <xref:System.PlatformNotSupportedException> 异常。 这些 API 被标记为特定于平台的 API 之后，规则 [CA1416](/visualstudio/code-quality/ca1416) 可以通过将 OS 检查添加到调用站点来帮助防止运行时 <xref:System.PlatformNotSupportedException> 异常。

#### <a name="examples"></a>示例

- <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType> 方法仅在 Windows 上受支持（该方法是用 `[SupportedOSPlatform("windows")]` 修饰的）。 如果项目[目标](../../../../docs/standard/frameworks.md)是 `net5.0`（但不是 `net5.0-windows`），则以下代码将在生成时生成 CA1416 警告。 有关为避免该警告可以执行的操作，请参阅[建议的操作](#recommended-action)。

  ```csharp
  public void PlayCMajor()
  {
      Console.Beep(261, 1000);
  }
  ```

- 浏览器不支持 <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> 方法（该方法是用 `[UnsupportedOSPlatform("browser")]` 修饰的）。 如果项目使用 Blazor WebAssembly SDK (`<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">`) 或在项目文件中包含 `browser` 作为受支持的平台 (`<SupportedPlatform Include="browser" />`)，则以下代码将在生成时生成 CA1416 警告。

  ```csharp
  public void CreateImage()
  {
      Image newImage = Image.FromFile("SampImag.jpg");
  }
  ```

#### <a name="version-introduced"></a>引入的版本

5.0 RC1

#### <a name="recommended-action"></a>建议操作

确保仅当代码在适当的平台上运行时，才调用特定于平台的 API。 在调用特定于平台的 API 之前，可以使用 <xref:System.OperatingSystem?displayProperty=nameWithType> 类中的 `Is<Platform>` 方法之一（例如 <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType>）检查当前操作系统。

可以在 `if` 语句条件下使用 `Is<Platform>` 方法之一：

```csharp
public void PlayCMajor()
{
    if (OperatingSystem.IsWindows())
    {
        Console.Beep(261, 1000);
    }
}
```

或者，如果不希望在运行时增加额外的 `if` 语句，请改为调用 <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>：

```csharp
public void PlayCMajor()
{
    Debug.Assert(OperatingSystem.IsWindows());
    Console.Beep(261, 1000);
}
```

还可以将 API 标记为特定于平台的 API，在这种情况下，检查要求的重担就落在了调用方身上。 可以标记特定方法或类型，也可以标记整个程序集。

```csharp
[SupportedOSPlatform("windows")]
public void PlayCMajor()
{
    Console.Beep(261, 1000);
}
```

如果不想修复所有调用站点，则可以选择以下某个选项以禁止显示警告：

- 若要禁止显示规则 CA1416，可以使用 `#pragma` 或 [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) 编译器标志来实现此目的，也可以通过在 .editorconfig 文件中[设置规则的严重性](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations)，将值设置为 `none` 来实现此目的。

  ```csharp
  public void PlayCMajor()
  {
  #pragma warning disable CA1416
      Console.Beep(261, 1000);
  #pragma warning restore CA1416
  }
  ```

- 若要完全禁用代码分析，请在项目文件中将 `EnableNETAnalyzers` 设置为 `false`。 有关详细信息，请参阅 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。

#### <a name="category"></a>类别

- 代码分析
- Core .NET 库

#### <a name="affected-apis"></a>受影响的 API

对于 Windows 平台：

- <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md> 上列出的所有 API。
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>

对于 Blazor WebAssembly 平台：

- <https://github.com/dotnet/runtime/issues/41087> 上列出的所有 API。

<!--

#### Affected APIs

- ``

-->

#### <a name="see-also"></a>另请参阅

- [CA1416：验证平台兼容性](/visualstudio/code-quality/ca1416)
- [.NET API 分析器](../../../../docs/standard/analyzers/api-analyzer.md)
