---
ms.openlocfilehash: 17a167e5245914329195d61ab45ae2d8ecb617d6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416247"
---
### <a name="blazor-target-framework-of-nuget-packages-changed"></a>Blazor：NuGet 包的目标框架已更改

Blazor 3.2 WebAssembly 项目编译为面向 .NET Standard 2.1 (`<TargetFramework>netstandard2.1</TargetFramework>`)。 在 ASP.NET Core 5.0 中，Blazor Server 和 Blazor WebAssembly 项目都面向 .NET 5.0 (`<TargetFramework>net5.0</TargetFramework>`)。 为了更好地适应目标框架更改，以下 Blazor 包不再面向 .NET Standard 2.1：

* [Microsoft.AspNetCore.Components](https://www.nuget.org/packages/Microsoft.AspNetCore.Components)
* [Microsoft.AspNetCore.Components.Authorization](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Authorization)
* [Microsoft.AspNetCore.Components.Forms](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Forms)
* [Microsoft.AspNetCore.Components.Web](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web)
* [Microsoft.AspNetCore.Components.WebAssembly](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly)
* [Microsoft.AspNetCore.Components.WebAssembly.Authentication](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication)
* [Microsoft.JSInterop](https://www.nuget.org/packages/Microsoft.JSInterop)
* [Microsoft.JSInterop.WebAssembly](https://www.nuget.org/packages/Microsoft.JSInterop.WebAssembly)
* [Microsoft.Authentication.WebAssembly.Msal](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal)

有关讨论，请参阅 GitHub 问题 [dotnet/aspnetcore#23424](https://github.com/dotnet/aspnetcore/issues/23424)。

#### <a name="version-introduced"></a>引入的版本

5.0 预览版 7

#### <a name="old-behavior"></a>旧行为

在 Blazor 3.1 和 3.2 中，包面向 .NET Standard 2.1 和 .NET Core 3.1。

#### <a name="new-behavior"></a>新行为

在 ASP.NET Core 5.0 中，包面向 .NET 5.0。

#### <a name="reason-for-change"></a>更改原因

进行此更改是为了更好地符合 .NET 目标框架要求。

#### <a name="recommended-action"></a>建议操作

Blazor 3.2 WebAssembly 项目应在将其包引用更新为 5.x.x 的过程中以 .NET 5.0 为目标。 引用其中一个包的库可以根据这些包的要求面向 .NET 5.0 或多个目标。

#### <a name="category"></a>类别

ASP.NET Core

#### <a name="affected-apis"></a>受影响的 API

None

<!--

#### Affected APIs

Not detectable via API analysis

-->
