---
ms.openlocfilehash: 975e331ad3e7bd7e0e8f49b62795c6acc7031ca9
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656325"
---
### <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a><span data-ttu-id="e1601-101">WinForms 和 WPF 应用使用 Microsoft.NET.Sdk</span><span class="sxs-lookup"><span data-stu-id="e1601-101">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>

<span data-ttu-id="e1601-102">Windows 窗体和 Windows Presentation Framework (WPF) 应用现在使用 .NET SDK (`Microsoft.NET.Sdk`)，而不使用 .NET Core WinForms 和 WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`)。</span><span class="sxs-lookup"><span data-stu-id="e1601-102">Windows Forms and Windows Presentation Framework (WPF) apps now use the .NET SDK (`Microsoft.NET.Sdk`) instead of the .NET Core WinForms and WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span>

#### <a name="change-description"></a><span data-ttu-id="e1601-103">更改说明</span><span class="sxs-lookup"><span data-stu-id="e1601-103">Change description</span></span>

<span data-ttu-id="e1601-104">在以前的 .NET Core 版本中，WinForms 和 WPF 应用使用单独的[项目 SDK](../../../../docs/core/project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`)。</span><span class="sxs-lookup"><span data-stu-id="e1601-104">In previous .NET Core versions, WinForms and WPF apps used a separate [project SDK](../../../../docs/core/project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span> <span data-ttu-id="e1601-105">从 .NET 5.0 开始，WinForms 和 WPF SDK 已与 .NET SDK (`Microsoft.NET.Sdk`) 统一。</span><span class="sxs-lookup"><span data-stu-id="e1601-105">Starting in .NET 5.0, the WinForms and WPF SDK has been unified with the .NET SDK (`Microsoft.NET.Sdk`).</span></span> <span data-ttu-id="e1601-106">此外，新的[目标框架名字对象 (TFM)](../../../../docs/standard/frameworks.md) 替换 .NET 5 中的 `netcoreapp` 和 `netstandard`。</span><span class="sxs-lookup"><span data-stu-id="e1601-106">In addition, new [target framework monikers (TFM)](../../../../docs/standard/frameworks.md) replace `netcoreapp` and `netstandard` in .NET 5.</span></span> <span data-ttu-id="e1601-107">下面的示例显示了在重新面向 .NET 5.0 或更高版本时，需要对 WPF 项目文件进行的更改。</span><span class="sxs-lookup"><span data-stu-id="e1601-107">The following example shows the changes you'd need to make for a WPF project file when retargeting to .NET 5.0 or later.</span></span>

<span data-ttu-id="e1601-108">在以前的 .NET Core 版本中：</span><span class="sxs-lookup"><span data-stu-id="e1601-108">In previous .NET Core versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="e1601-109">在 .NET 5.0 及更高版本中：</span><span class="sxs-lookup"><span data-stu-id="e1601-109">In .NET 5.0 and later versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

#### <a name="version-introduced"></a><span data-ttu-id="e1601-110">引入的版本</span><span class="sxs-lookup"><span data-stu-id="e1601-110">Version introduced</span></span>

<span data-ttu-id="e1601-111">.NET 5.0 预览版 8</span><span class="sxs-lookup"><span data-stu-id="e1601-111">.NET 5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e1601-112">建议操作</span><span class="sxs-lookup"><span data-stu-id="e1601-112">Recommended action</span></span>

<span data-ttu-id="e1601-113">在 WPF 或 Windows 窗体项目文件中：</span><span class="sxs-lookup"><span data-stu-id="e1601-113">In your WPF or Windows Forms project file:</span></span>

- <span data-ttu-id="e1601-114">将 `Sdk` 属性更新为 `Microsoft.NET.Sdk`。</span><span class="sxs-lookup"><span data-stu-id="e1601-114">Update the `Sdk` attribute  to `Microsoft.NET.Sdk`.</span></span>
- <span data-ttu-id="e1601-115">将 `TargetFramework` 属性更新为 `net5.0-windows`。</span><span class="sxs-lookup"><span data-stu-id="e1601-115">Update the `TargetFramework` property to `net5.0-windows`.</span></span>

#### <a name="category"></a><span data-ttu-id="e1601-116">类别</span><span class="sxs-lookup"><span data-stu-id="e1601-116">Category</span></span>

- <span data-ttu-id="e1601-117">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="e1601-117">Windows Forms</span></span>
- <span data-ttu-id="e1601-118">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="e1601-118">Windows Presentation Framework (WPF)</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e1601-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="e1601-119">Affected APIs</span></span>

<span data-ttu-id="e1601-120">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="e1601-120">Not detectable via API analysis.</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
