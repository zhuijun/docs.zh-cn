---
ms.openlocfilehash: 975e331ad3e7bd7e0e8f49b62795c6acc7031ca9
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656325"
---
### <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a>WinForms 和 WPF 应用使用 Microsoft.NET.Sdk

Windows 窗体和 Windows Presentation Framework (WPF) 应用现在使用 .NET SDK (`Microsoft.NET.Sdk`)，而不使用 .NET Core WinForms 和 WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`)。

#### <a name="change-description"></a>更改说明

在以前的 .NET Core 版本中，WinForms 和 WPF 应用使用单独的[项目 SDK](../../../../docs/core/project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`)。 从 .NET 5.0 开始，WinForms 和 WPF SDK 已与 .NET SDK (`Microsoft.NET.Sdk`) 统一。 此外，新的[目标框架名字对象 (TFM)](../../../../docs/standard/frameworks.md) 替换 .NET 5 中的 `netcoreapp` 和 `netstandard`。 下面的示例显示了在重新面向 .NET 5.0 或更高版本时，需要对 WPF 项目文件进行的更改。

在以前的 .NET Core 版本中：

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

在 .NET 5.0 及更高版本中：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

#### <a name="version-introduced"></a>引入的版本

.NET 5.0 预览版 8

#### <a name="recommended-action"></a>建议操作

在 WPF 或 Windows 窗体项目文件中：

- 将 `Sdk` 属性更新为 `Microsoft.NET.Sdk`。
- 将 `TargetFramework` 属性更新为 `net5.0-windows`。

#### <a name="category"></a>类别

- Windows 窗体
- Windows Presentation Foundation (WPF)

#### <a name="affected-apis"></a>受影响的 API

无法通过 API 分析检测到。

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
