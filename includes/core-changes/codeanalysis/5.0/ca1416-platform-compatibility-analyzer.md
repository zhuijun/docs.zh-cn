---
ms.openlocfilehash: 4a7616d2ffaabab5279342ebc1082c93a174a52d
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406163"
---
### <a name="ca1416-platform-compatibility"></a><span data-ttu-id="eceea-101">CA1416：平台兼容性</span><span class="sxs-lookup"><span data-stu-id="eceea-101">CA1416: Platform compatibility</span></span>

<span data-ttu-id="eceea-102">从 .NET 5.0 开始，默认启用 .NET 代码分析器规则 [CA1416](/visualstudio/code-quality/ca1416)。</span><span class="sxs-lookup"><span data-stu-id="eceea-102">.NET code analyzer rule [CA1416](/visualstudio/code-quality/ca1416) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="eceea-103">它会针对从未验证操作系统的调用站点调用特定于平台的 API 生成一个生成警告。</span><span class="sxs-lookup"><span data-stu-id="eceea-103">It produces a build warning for calls to platform-specific APIs from call sites that don't verify the operating system.</span></span>

#### <a name="change-description"></a><span data-ttu-id="eceea-104">更改说明</span><span class="sxs-lookup"><span data-stu-id="eceea-104">Change description</span></span>

<span data-ttu-id="eceea-105">从 .NET 5.0 开始，.NET SDK 包括 [.NET 源代码分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="eceea-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="eceea-106">其中一些规则会默认启用，包括 [CA1416](/visualstudio/code-quality/ca1416)。</span><span class="sxs-lookup"><span data-stu-id="eceea-106">Several of these rules are enabled, by default, including [CA1416](/visualstudio/code-quality/ca1416).</span></span> <span data-ttu-id="eceea-107">如果项目包含违反此规则的代码，并已被配置为将警告视为错误，则此更改可能会中断生成。</span><span class="sxs-lookup"><span data-stu-id="eceea-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span> <span data-ttu-id="eceea-108">当你在平台上下文未验证的位置使用特定于平台的 API 时，规则 CA1416 会通知你。</span><span class="sxs-lookup"><span data-stu-id="eceea-108">Rule CA1416 informs you when you're using platform-specific APIs from places where the platform context isn't verified.</span></span>

<span data-ttu-id="eceea-109">规则 [CA1416](/visualstudio/code-quality/ca1416)（平台兼容性分析器）与 .NET 5.0 中新增的一些其他功能配合工作。</span><span class="sxs-lookup"><span data-stu-id="eceea-109">Rule [CA1416](/visualstudio/code-quality/ca1416), the platform compatibility analyzer, works hand-in-hand with some other features that are new in .NET 5.0.</span></span> <span data-ttu-id="eceea-110">.NET 5.0 引入了 <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> 和 <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>，可用于指定支持或不支持 API 的平台 。</span><span class="sxs-lookup"><span data-stu-id="eceea-110">.NET 5.0 introduces the <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> and <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>, which let you specify the platforms that an API *is* or *isn't* supported on.</span></span> <span data-ttu-id="eceea-111">如果没有这些属性，则假定所有平台都支持 API。</span><span class="sxs-lookup"><span data-stu-id="eceea-111">In the absence of these attributes, an API is assumed to be supported on all platforms.</span></span> <span data-ttu-id="eceea-112">这些属性已应用于核心 .NET 库中特定于平台的 API。</span><span class="sxs-lookup"><span data-stu-id="eceea-112">These attributes have been applied to platform-specific APIs in the core .NET libraries.</span></span>

<span data-ttu-id="eceea-113">在针对其所使用的 API 不可用的平台的项目中，规则 [CA1416](/visualstudio/code-quality/ca1416) 会标记任何未验证平台上下文的特定于平台的 API 调用。</span><span class="sxs-lookup"><span data-stu-id="eceea-113">In projects that target platforms for which APIs that they use aren't available, rule [CA1416](/visualstudio/code-quality/ca1416) flags any platform-specific API call where the platform context isn't verified.</span></span> <span data-ttu-id="eceea-114">现在，在不受支持的操作系统上调用 API 时，大多数用 <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> 和 <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> 属性修饰的 API 都会引发 <xref:System.PlatformNotSupportedException> 异常。</span><span class="sxs-lookup"><span data-stu-id="eceea-114">Most of the APIs that are now decorated with the <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> and <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> attributes throw <xref:System.PlatformNotSupportedException> exceptions when they're invoked on an unsupported operating system.</span></span> <span data-ttu-id="eceea-115">这些 API 被标记为特定于平台的 API 之后，规则 [CA1416](/visualstudio/code-quality/ca1416) 可以通过将 OS 检查添加到调用站点来帮助防止运行时 <xref:System.PlatformNotSupportedException> 异常。</span><span class="sxs-lookup"><span data-stu-id="eceea-115">Now that these APIs are marked as platform-specific, rule [CA1416](/visualstudio/code-quality/ca1416) helps you prevent run-time <xref:System.PlatformNotSupportedException> exceptions by adding OS checks to your call sites.</span></span>

#### <a name="examples"></a><span data-ttu-id="eceea-116">示例</span><span class="sxs-lookup"><span data-stu-id="eceea-116">Examples</span></span>

- <span data-ttu-id="eceea-117"><xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType> 方法仅在 Windows 上受支持，并且该方法修饰有 `[SupportedOSPlatform("windows")]`。</span><span class="sxs-lookup"><span data-stu-id="eceea-117">The <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType> method is only supported on Windows and is decorated with `[SupportedOSPlatform("windows")]`.</span></span> <span data-ttu-id="eceea-118">如果项目[目标](../../../../docs/standard/frameworks.md)是 `net5.0`（但不是 `net5.0-windows`），则以下代码将在生成时生成 CA1416 警告。</span><span class="sxs-lookup"><span data-stu-id="eceea-118">The following code will produce a CA1416 warning at build time if the project [targets](../../../../docs/standard/frameworks.md) `net5.0` (but not `net5.0-windows`).</span></span> <span data-ttu-id="eceea-119">有关为避免该警告可以执行的操作，请参阅[建议的操作](#recommended-action)。</span><span class="sxs-lookup"><span data-stu-id="eceea-119">For actions you can take to avoid the warning, see [Recommended action](#recommended-action).</span></span>

  ```csharp
  public void PlayCMajor()
  {
      Console.Beep(261, 1000);
  }
  ```

- <span data-ttu-id="eceea-120">浏览器不支持 <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> 方法，并且该方法修饰有 `[UnsupportedOSPlatform("browser")]`。</span><span class="sxs-lookup"><span data-stu-id="eceea-120">The <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> method is not supported in the browser and is decorated with `[UnsupportedOSPlatform("browser")]`.</span></span> <span data-ttu-id="eceea-121">如果项目支持浏览器平台，则以下代码将在生成时生成 CA1416 警告。</span><span class="sxs-lookup"><span data-stu-id="eceea-121">The following code will produce a CA1416 warning at build time if the project supports the browser platform.</span></span>

  ```csharp
  public void CreateImage()
  {
      Image newImage = Image.FromFile("SampImag.jpg");
  }
  ```

  > [!TIP]
  >
  > - <span data-ttu-id="eceea-122">Blazor WebAssembly 项目和 Razor 类库项目自动提供浏览器支持。</span><span class="sxs-lookup"><span data-stu-id="eceea-122">Blazor WebAssembly projects and Razor class library projects include browser support automatically.</span></span>
  > - <span data-ttu-id="eceea-123">若要手动添加浏览器作为项目的支持平台，请将以下项添加到项目文件中：</span><span class="sxs-lookup"><span data-stu-id="eceea-123">To manually add the browser as a supported platform for your project, add the following entry to your project file:</span></span>
  >
  >  ```xml
  >  <ItemGroup>
  >    <SupportedPlatform Include="browser" />
  >  </ItemGroup>
  >  ```

#### <a name="version-introduced"></a><span data-ttu-id="eceea-124">引入的版本</span><span class="sxs-lookup"><span data-stu-id="eceea-124">Version introduced</span></span>

<span data-ttu-id="eceea-125">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="eceea-125">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eceea-126">建议操作</span><span class="sxs-lookup"><span data-stu-id="eceea-126">Recommended action</span></span>

<span data-ttu-id="eceea-127">确保仅当代码在适当的平台上运行时，才调用特定于平台的 API。</span><span class="sxs-lookup"><span data-stu-id="eceea-127">Ensure that platform-specific APIs are only called when the code is running on an appropriate platform.</span></span> <span data-ttu-id="eceea-128">在调用特定于平台的 API 之前，可以使用 <xref:System.OperatingSystem?displayProperty=nameWithType> 类中的 `Is<Platform>` 方法之一（例如 <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType>）检查当前操作系统。</span><span class="sxs-lookup"><span data-stu-id="eceea-128">You can check the current operating system using one of the `Is<Platform>` methods in the <xref:System.OperatingSystem?displayProperty=nameWithType> class, for example, <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType>, before calling a platform-specific API.</span></span>

<span data-ttu-id="eceea-129">可以在 `if` 语句条件下使用 `Is<Platform>` 方法之一：</span><span class="sxs-lookup"><span data-stu-id="eceea-129">You can use one of the `Is<Platform>` methods in the condition of an `if` statement:</span></span>

```csharp
public void PlayCMajor()
{
    if (OperatingSystem.IsWindows())
    {
        Console.Beep(261, 1000);
    }
}
```

<span data-ttu-id="eceea-130">或者，如果不希望在运行时增加额外的 `if` 语句，请改为调用 <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>：</span><span class="sxs-lookup"><span data-stu-id="eceea-130">Or, if you don't want the overhead of an additional `if` statement at run time, call <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> instead:</span></span>

```csharp
public void PlayCMajor()
{
    Debug.Assert(OperatingSystem.IsWindows());
    Console.Beep(261, 1000);
}
```

<span data-ttu-id="eceea-131">如果你正在创作库，可以将 API 标记为平台专用。</span><span class="sxs-lookup"><span data-stu-id="eceea-131">If you're authoring a library, you can mark your API as platform-specific.</span></span> <span data-ttu-id="eceea-132">在这种情况下，检查要求的负担就落在了调用方身上。</span><span class="sxs-lookup"><span data-stu-id="eceea-132">In this case, the burden of checking requirements falls on your callers.</span></span> <span data-ttu-id="eceea-133">可以标记特定方法或类型，也可以标记整个程序集。</span><span class="sxs-lookup"><span data-stu-id="eceea-133">You can mark specific methods or types or an entire assembly.</span></span>

```csharp
[SupportedOSPlatform("windows")]
public void PlayCMajor()
{
    Console.Beep(261, 1000);
}
```

<span data-ttu-id="eceea-134">如果不想修复所有调用站点，则可以选择以下某个选项以禁止显示警告：</span><span class="sxs-lookup"><span data-stu-id="eceea-134">If you don't want to fix all your call sites, you can choose one of the following options to suppress the warning:</span></span>

- <span data-ttu-id="eceea-135">若要禁止显示规则 CA1416，可以使用 `#pragma` 或 [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) 编译器标志来实现此目的，也可以通过在 .editorconfig 文件中[设置规则的严重性](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations)，将值设置为 `none` 来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="eceea-135">To suppress rule CA1416, you can do so using `#pragma` or the [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) compiler flag, or by [setting the rule's severity](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations) to `none` in an .editorconfig file.</span></span>

  ```csharp
  public void PlayCMajor()
  {
  #pragma warning disable CA1416
      Console.Beep(261, 1000);
  #pragma warning restore CA1416
  }
  ```

- <span data-ttu-id="eceea-136">若要完全禁用代码分析，请在项目文件中将 `EnableNETAnalyzers` 设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="eceea-136">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="eceea-137">有关详细信息，请参阅 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="eceea-137">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="eceea-138">类别</span><span class="sxs-lookup"><span data-stu-id="eceea-138">Category</span></span>

- <span data-ttu-id="eceea-139">代码分析</span><span class="sxs-lookup"><span data-stu-id="eceea-139">Code analysis</span></span>
- <span data-ttu-id="eceea-140">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="eceea-140">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eceea-141">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="eceea-141">Affected APIs</span></span>

<span data-ttu-id="eceea-142">对于 Windows 平台：</span><span class="sxs-lookup"><span data-stu-id="eceea-142">For Windows platform:</span></span>

- <span data-ttu-id="eceea-143"><https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md> 上列出的所有 API。</span><span class="sxs-lookup"><span data-stu-id="eceea-143">All APIs listed at <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md>.</span></span>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>

<span data-ttu-id="eceea-144">对于 Blazor WebAssembly 平台：</span><span class="sxs-lookup"><span data-stu-id="eceea-144">For Blazor WebAssembly platform:</span></span>

- <span data-ttu-id="eceea-145"><https://github.com/dotnet/runtime/issues/41087> 上列出的所有 API。</span><span class="sxs-lookup"><span data-stu-id="eceea-145">All APIs listed at <https://github.com/dotnet/runtime/issues/41087>.</span></span>

<!--

#### Affected APIs

- ``

-->

#### <a name="see-also"></a><span data-ttu-id="eceea-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eceea-146">See also</span></span>

- [<span data-ttu-id="eceea-147">CA1416：验证平台兼容性</span><span class="sxs-lookup"><span data-stu-id="eceea-147">CA1416: Validate platform compatibility</span></span>](/visualstudio/code-quality/ca1416)
- [<span data-ttu-id="eceea-148">.NET API 分析器</span><span class="sxs-lookup"><span data-stu-id="eceea-148">.NET API analyzer</span></span>](../../../../docs/standard/analyzers/api-analyzer.md)
